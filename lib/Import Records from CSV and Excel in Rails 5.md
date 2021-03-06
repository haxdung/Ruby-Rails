We will continue working on the project we created in Exporting Records in CSV and Excel Formats in Rails 5. Add:
```ruby
gem 'roo'
```
to Gemfile and run bundle. In products/index.html.erb, add file upload field:
```ruby
<h2>Import Products</h2>
<%= form_tag import_products_path, multipart: true do %>
  <%= file_field_tag :file %>
  <%= submit_tag "Import" %>
<% end %>
```
Define route to import data from the uploaded file.
```ruby
resources :products do
  collection do
    post :import
  end
end
```
This defines the following route.
```ruby
import_products POST   /products/import(.:format)   products#import
```
Implement import action in products controller.
```ruby
def import
  Product.import(params[:file])

  redirect_to root_url, notice: 'Products imported.'
end
```
This gives the error:
```ruby
uninitialized constant Roo::Csv
```
Change:
```ruby
Roo::Csv
```
to
```ruby
Roo::CSV
```
In product model, change:
```ruby
spreadsheet = Roo::Spreadsheet.open(file.path)
```
We get the error, ActiveRecord::NotFound exception. Change the import line that finds a record like this:
```ruby
product = find_by(id: row["id"]) || new
```
The entire method now looks like this:
```ruby
def self.import(file)
  spreadsheet = Roo::Spreadsheet.open(file.path)
  header = spreadsheet.row(1)
  (2..spreadsheet.last_row).each do |i|
    row = Hash[[header, spreadsheet.row(i)].transpose]
    product = find_by(id: row["id"]) || new
    product.attributes = row.to_hash
    product.save!
  end
end  
```
Make sure to name the headers have the same value as the column name in the database, so the header should be id, name and released_on. Delete this:
```ruby
def self.open_spreadsheet(file)
  case File.extname(file.original_filename)
  when ".csv" then Roo::CSV.new(file.path, nil, :ignore)
  when ".xls" then Roo::Excel.new(file.path, nil, :ignore)
  when ".xlsx" then Roo::Excelx.new(file.path, nil, :ignore)
  else raise "Unknown file type: #{file.original_filename}"
  end
end
```
