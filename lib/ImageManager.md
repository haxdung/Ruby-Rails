Images are a crucial part of any application. From a social network to a simple bug tracker, images play an important role. However, managing images is not a trivial task and requires a lot of planning ahead.

In this article allow me to demonstrate how to achieve this in Rails. I’m going to show you how to process your images and create multiple versions in the backend. We’ll also see how to improve the performance of the page by compressing these images without losing quality.
Getting Started

The examples in this tutorial run on Rails 4.2, with a MongoDb database, and HAML to render the views. However the snippets used here should be compatible with any version of Rails, albeit minor config differences.
Setting up the Stage

ImageMagick is the go to library for image processing on POSIX systems. If you don’t have ImageMagick installed on your system, it can be installed with the package manager for your OS. On Ubuntu:
```
sudo apt-get -y install imagemagick
sudo apt-get -y install libmagic-dev
sudo apt-get -y install libmagickwand-dev
```
On Mac OS X, I recommend using Homebrew:
```
brew install imagemagick
```
Now, we need a Ruby adapter to connect to the native ImageMagick library. I personally prefer MiniMagick, as it is lightweight and does pretty much everything a typical application requires:

# Gemfile
```
gem 'mini_magick'
```
## Playground

Let’s play around with some of the MiniMagick’s features before building anything serious. Open up the Rails console (rails c) and run the following:
```ruby
# Open an image from a website

image = MiniMagick::Image.open("https://s3.amazonaws.com/StartupStockPhotos/20140808_StartupStockPhotos/85.jpg")

# Get the Image's width
image.width # 4928

# Get the image's height
image.height #3264
```
Holy moly, that’s huge. Let’s see if we can resize this to fit our iPad:
```ruby
image.resize "2048x1536"

# Now get the image's new width and height

p "Width is => #{image.width} and height is => #{image.height}"
```
Well, that did it. Wait a second, where is this changed file stored?
```ruby
image.path # temp path
```
The manipulated image is stored in a temp path and will be washed away. To persist it to disk, simply call the write method:
```ruby
image.write "public/uploads/test.jpg"
```
## Converting Image

One of the most frequent operations you’ll do is convert images to different formats. MiniMagick makes this very simple:
```ruby
image.format "png"
image.write "public/uploads/test.png"
```
## Going Crazy

You can also combine multiple operations in a single block:
```ruby
image.combine_options do |i|
  i.resize "2048x1536"
  i.flip
  i.rotate "-45"
  i.blur "0x15"
end
image.write "public/uploads/blur.png"

![Some weird result](blur.png)
```
OK, I went a little overboard here. In my defense, I’m just trying to show all the cool stuff that you can do with MiniMagick :).

Now, let’s see how we can tie this up with our Rails app.

# Uploading Files

Carrierwave is a wonderful gem which simplifies file uploads in Ruby. It also interacts nicely with MiniMagick, making our lives much simpler.

## Gemfile
```ruby
gem 'carrierwave'
gem 'carrierwave-mongoid', :require => 'carrierwave/mongoid'
```
NOTE: If you’re on ActiveRecord or DataMapper, the configurations would be slightly different and the official Carrierwave documentation will show you the way.

Bundle to fetch all these gems:
```
bundle install
```
Create our first uploader:
```ruby
#app/uploaders/image_uploader.rb

class ImageUploader < CarrierWave::Uploader::Base
  # Include RMagick or MiniMagick support:
  include CarrierWave::MiniMagick

  # Choose what kind of storage to use for this Uploader:
  storage :file
  # Override the directory where uploaded files will be stored.
  # This is a sensible default for uploaders that are meant to be mounted:
  def store_dir
    "uploads/images"
  end
end
```
The code here is self explanatory. storage :file instructs the server to store the image on the local server and the store_dir specifies the location.

Since, the files are sent over the Internet, as a best practice, always filter the incoming files:
```ruby
# app/uploaders/image_uploader.rb
...
# Add a white list of extensions which are allowed to be uploaded.
# For images you might use something like this:
def extension_white_list
  %w(jpg jpeg png gif)
end
...
```
This snippet filters out file types other than the ones specified here. This is by no means foolproof, but it serves as a first level filter against any impediment attack.

Mount this uploader to our image model:
```ruby
# app/models/image.rb

class Image
  include Mongoid::Document
  include Mongoid::Timestamps
  include Mongoid::Paranoia
  include Mongoid::Attributes::Dynamic
  include Rails.application.routes.url_helpers

  mount_uploader :media, ImageUploader, mount_on: :media_filename
end
```
Edit the image_uploader.rb to process the uploaded image:
```ruby
# app/uploaders/image_uploader.rb

#.....
process :resize_to_fill => [200, 200]
process :convert => 'png'
#.....
```
Try creating a new image from the Rails console:
```ruby
media = File.open("/Users/test/Desktop/image/jpg")
img = Image.new(:media => media)
img.save
```
The uploaded image is available under the store_dir. However, the uploaded image is immediately processed and overwritten with the 200×200 image. We won’t have a copy of the original file for any future edits. To avoid this, create multiple versions of the file.
```ruby
# app/uploaders/image_uploader.rb

#.....
version :thumb do
  process :resize_to_fit => [100, 100]
  process :convert => 'jpg'
end

version :cover   do
  process :resize_to_fit => [240, 180]
  process :convert => 'jpg'
end

#.....
```
This creates 2 new versions, along with the original image. Check the versions created by Carrierwave:
```ruby
img.media.versions[:thumb] # returns the thumb image instance
img.media.versions[:cover] # returns the cover image instance
```
Did you notice that these images are generated instantaneously? This means that the image conversion happens in the same thread and execution is blocked until it completes. In a production application, it would be undesirable to create multiple versions of an image in the same thread. Instead, we should be handling this conditionally.
```ruby
# app/uploaders/image_uploader/rb

#....
version :cover, :if => :is_live? do
  process :resize_to_fit => [240, 180]
  process :convert => 'jpg'
end

def is_live?(img = nil)
  @is_live
end

def is_live=(value)
  @is_live = value
end
#....
```
Now, when we try creating a new image, the cover version won’t be generated. We can manually trigger this when needed by simply running:
```ruby
img.media.is_live = true
img.save
img.media.recreate_versions! :cover
```
This code also runs in the foreground and is a blocking operation, but at least it’s deferred till the last moment possible. We can take this a step further by running this in the background with Resque:
```ruby
# lib/resque/image_queue.rb
class ImageQueue
  @queue = :image_queue
  def self.perform(image_id)
    image = Image.find image_id
    img.media.is_live= true
    img.save
    img.media.recreate_versions! :cover
  end
end
```
and, enqueue it:
```ruby
Resque.enqueue(ImageQueue, img.id.to_s)
```
## Improving Performance

Images are heavy and tend to slow down the website. One way to reduce the page weight is to compress these images. Carrierwave Image Optimizer helps us compress our images on the fly without any hassles.

Add this to your Gemfile:
```ruby
gem 'carrierwave-imageoptimizer'
```
And edit the image_uploader
```ruby
# app/uploaders/image_uploader.rd

#.....

include CarrierWave::ImageOptimizer
process :optimize
process :quality => 100
#....
```
This compresses all the images without any visual loss. The way this works is all the meta information about the image is stripped out. On average, this reduces the size around 20-30%.
