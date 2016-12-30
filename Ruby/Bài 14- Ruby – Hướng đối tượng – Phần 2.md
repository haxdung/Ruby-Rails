# Ruby – Hướng đối tượng – Phần 2

Trong phần này chúng ta tiếp tục tìm hiểu về hướng đối tượng trong Ruby.

# Truy xuất thuộc tính

Như đã nói ở bài trước, mặc định tất cả các thuộc tính trong Ruby đều là **private**, tức là chúng ta chỉ có thể truy xuất được thông qua phương thức của đối tượng. Trong thực tế thì khi thiết kế lớp, với mỗi thuộc tính chúng ta sẽ định nghĩa 2 phương thức là **getter** và **setter**, mục đích của 2 phương thức này là để truy xuất dữ liệu và chỉnh sửa chúng, việc định nghĩa 2 phương thức trên hầu như là công việc tuy không bắt buộc nhưng nhất định phải làm. Do đó trong một số IDE có sẵn chức năng tự tạo các phương thức **getter** và **setter** luôn. Đối với Ruby thì có sẵn 3 phương thức tương tự là **attr_reader**, **attr_writer** và **attr_accessor**.

Phương thức **attr_reader** sẽ tạo các phương thức **getter** trong khi phương thức **attr_writer** sẽ tạo các phương thức **setter**. Phương thức **attr_accessor** sẽ tạo cả **getter**, **setter** và các biến **instance**.

Ví dụ 1:
example1.rb
```ruby
class Car
  
    attr_reader :name, :price
    attr_writer :name, :price
  
    def to_s
        "#{@name}: #{@price}"
    end
 
end
 
 
c1 = Car.new
c2 = Car.new
 
c1.name = "Porsche"
c1.price = 23500
 
c2.name = "Volkswagen"
c2.price = 9500
 
puts "#{c1.name}: #{c1.price}"
 
p c1
p c2
```
Trong ví dụ này chúng ta định nghĩa lớp Car. Trong lớp này chúng ta định nghĩa các phương thức **getter** và **setter** bằng cách sử dụng phương thức **attr_reader** và **attr_writer**.
```ruby
attr_reader :name, :price
```
Để tạo các phương thức **getter** thì chúng ta ghi tên phương thức đó dưới dạng **Symbol** phía sau phương thức **attr_reader**.
```ruby
attr_writer :name, :price 
```
Tương tự với các phương thức **setter**, chúng ta cũng ghi sau phương thức **attr_writer**.
```ruby
c1.name = "Porsche"
c1.price = 23500
```
Chúng ta gọi các phương thức **setter** như gọi các phương thức bình thường, rồi dùng toán tử gán **"="** để thiết lập dữ liệu.
```ruby
puts "#{c1.name}: #{c1.price}"
```
Tương tự, các phương thức **getter** cũng vậy.
Output
```
Porsche: 23500
#<Car:0x2517d98 @name="Porsche", @price=23500>
#<Car:0x2517d80 @name="Volkswagen", @price=9500>
```
Ví dụ 2:
example2.rb
```ruby
class Book
   attr_accessor :title, :pages   
end
 
b1 = Book.new
b1.title = "Hidden motives"
b1.pages = 255
 
p "The book #{b1.title} has #{b1.pages} pages"
```
Như đã nói ở trên, phương thức **attr_accessor** sẽ tạo luôn cả phương thức **getter** và **setter**.
Output
```
"The book Hidden motives has 255 pages"
```

# Hằng số lớp

constant_class.rb
```ruby
class MMath
 
    PI = 3.141592
end
 
 
puts MMath::PI
```
Các hằng số được định nghĩa bên trong một lớp có tác dụng giống như biến **class** vậy, tức là chúng được dùng chung bởi tất cả các đối tượng thuộc lớp đó, chứ không có lớp nào có biến riêng cả. Trong ví dụ trên chúng ta định nghĩa lớp **NMath** có hằng **PI**.
```ruby
PI = 3.141592
```
Hằng số được đặt tên bắt đầu bằng chữ cái in hoa.
```ruby
puts MMath::PI
```
Để truy xuất giá trị của hằng số thì chúng ta dùng toán tử **::** theo sau tên lớp.
Output
```
3.141592
```

# Phương thức to_s

Tất cả các đối tượng trong Ruby đều có phương thức **to_s**, phương thức này được kế thừa từ lớp **Object** gốc trong Ruby. Phương thức trả về một chuỗi string mô tả về đối tượng đó, khi chúng ta dùng phương thức **puts** để in ra một đối tượng thì phương thức **puts** sẽ gọi đến phương thức **to_s** của đối tượng đó.
to_s_method.rb
```ruby
class Being
 
    def to_s
        "This is Being class"
    end
end
 
b = Being.new
puts b.to_s
puts b
```
Trong ví dụ này chúng ta định nghĩa lớp Being có phương thức **to_s**.
```ruby
def to_s
    "This is Being class"
end
```
Nếu chúng ta không định nghĩa lại phương thức **to_s** thì phương thức **puts** sẽ gọi phương thức **to_s** của lớp **Object** gốc, mà phương thức **to_s** gốc sẽ in ra địa chỉ bộ nhớ của đối tượng.
```ruby
b = Being.new
puts b.to_s
puts b
```
Khi dùng chúng ta có thể gọi ra một cách rõ ràng hoặc không gọi cũng được.
Output
```
This is Being class
This is Being class
```

# Quá tải toán tử

Quá tải toán tử tức là một toán tử có thể dùng cho nhiều kiểu dữ liệu khác nhau, giống như chúng ta có nhiều phương thức và mỗi phương thức nhận nhiều tham số khác nhau vậy.
overload_operator.rb
```ruby
class Circle
    
    attr_accessor :radius
     
    def initialize r
        @radius = r
    end
 
    def +(other)
        Circle.new @radius + other.radius
    end
     
    def to_s
        "Circle with radius: #{@radius}"
    end
end
 
 
c1 = Circle.new 5
c2 = Circle.new 6
c3 = c1 + c2
 
p c3
```
Trong ví dụ này chúng ta định nghĩa lớp Circle có toán tử **+**.
```ruby
def +(other)
    Circle.new @radius + other.radius
end
```
Để định nghĩa một toán tử thì chúng ta cũng dùng cặp từ khóa **def...end** giống như định nghĩa một phương thức với tên toán tử phía sau từ khóa **def**, sau đó đặt tham số trong cặp dấu **()**.

Ở đây lớp Circle có nghĩa là hình tròn, thuộc tính radius là bán kính. Toán tử **+** có chức năng cộng 2 bán kính của 2 hình tròn.
```ruby
c1 = Circle.new 5
c2 = Circle.new 6
c3 = c1 + c2
```
Toán tử được dùng như cách dùng với các kiểu dữ liệu bình thường
Output
```
Circle with radius: 11
```

# Phương thức class

Các phương thức trong Ruby có 2 loại là phương thức **class** và phương thức **instance**, giống như biến cũng có biến **class** và biến **instance** vậy. Và chức năng của 2 loại phương thức này cũng giống hệt như đối với biến. Tức là phương thức **instance** là phương thức của riêng từng đối tượng, trong khi phương thức **class** là phương thức dùng chung, tất cả các đối tượng được tạo từ cùng một lớp sẽ dùng chung một phương thức **class**.

Phương thức **class** không thể truy xuất các biến **instance** mà chỉ có thể truy xuất các biến **class**.

Ví dụ:
class_methods1.rb
```v
class Circle
     
    def initialize x
        @r = x
    end
    
    def self.info
       "This is a Circle class"
    end
     
    def area
        @r * @r * 3.141592
    end
 
end
 
 
p Circle.info
c = Circle.new 3
p c.area
```
Trong ví dụ này chúng ta định nghĩa lớp Circle có một phương thức **class**.
```ruby
def self.info
    "This is a Circle class"
end
```
Phương thức **class** được định nghĩa bằng cách thêm từ khóa **self** vào trước tên phương thức.
```ruby
def area
    "Circle, radius: #{@r}"
end
```
Phương thức area là phương thức **instance** vì không chứa từ khóa **self**, vậy tức là các phương thức mà chúng ta đã định nghĩa từ trước tới giờ đều là phương thức **instance**.
```ruby
p Circle.info
```
Để gọi phương thức **class** thì chúng ta gọi từ tên lớp chứ không gọi từ tên đối tượng.
```ruby
c = Circle.new 3
p c.area
```
Để gọi phương thức **instance** thì chúng ta phải tạo một đối tượng rồi gọi từ tên đối tượng đó như trước giờ chúng ta vẫn làm. Ở đoạn code trên chúng ta tạo một đối tượng Circle có tên là c và gọi phương thức **instance** area của đối tượng đó.
Output
```
"This is a Circle class"
28.274328
```
Ví dụ 2:

Ngoài cách định nghĩa như trên chúng ta còn có 2 cách định nghĩa phương thức **class** khác.
class_methods2.rb
```ruby
class Wood
      
    def self.info
       "This is a Wood class"
    end
end
 
class Brick
      
    class << self
        def info
           "This is a Brick class"
        end
    end
end
 
class Rock
      
end
 
def Rock.info
   "This is a Rock class"
end
 
p Wood.info
p Brick.info
p Rock.info
```
Trong ví dụ này chúng ta dùng 3 cách định nghĩa phương thức **class** khác nhau.
```ruby
def self.info
    "This is a Wood class"
end
```
Cách đầu tiên đã giới thiệu ở trên là dùng từ khóa **self**.
```ruby
class << self
    def info
        "This is a Brick class"
    end
end
```
Cách thứ 2 là khai báo phần định nghĩa trong khối **class << self...end**.
```ruby
def Rock.info
   "This is a Rock class"
end
```
Cách thứ 3 là hay vì dùng từ khóa **self** thì chúng ta dùng luôn tên lớp.
Output
```
"This is a Wood class"
"This is a Brick class"
"This is a Rock class"
```

# Đa hình

Tính đa hình là tính năng cho phép chúng ta thực thi toán tử hay phương thức với nhiều kiểu dữ liệu khác nhau. Khi một lớp thừa kế từ một lớp khác thì lớp con ngoài việc kế thừa lại những gì có ở lớp cha thì có thể định nghĩa lại hoặc mở rộng thêm nữa. Nói một cách tổng quát thì **đa hình là tính năng cho phép định nghĩa lại các phương thức ở lớp con**.

Ví dụ:
polymorphism.rb
```ruby
class Animal
     
    def make_noise 
        "Some noise"
    end
 
    def sleep 
        puts "#{self.class.name} is sleeping."
    end
   
end
 
class Dog < Animal
     
    def make_noise 
        'Woof!'        
    end
     
end
 
class Cat < Animal 
     
    def make_noise 
        'Meow!'
    end
end
 
[Animal.new, Dog.new, Cat.new].each do |animal|
  puts animal.make_noise
  animal.sleep
end
```
Trong ví dụ trên chúng ta có lớp cơ sở Animal, lớp dẫn xuất Dog và Cat kế thừa từ lớp Animal. Cả 3 lớp này đều có phương thức make_noise nhưng kết quả của phương thức này ở 3 lớp là khác nhau.
```ruby
[Animal.new, Dog.new, Cat.new].each do |animal|
  puts animal.make_noise
  animal.sleep
end
```
Việc định nghĩa lại phương thức được kế thừa ở lớp cha còn được gọi là **override**. Ở đây phương thức make_noise được **override** lại ở 2 lớp Dog và Cat, trong khi ở lớp cơ sở có phương thức sleep nữa nhưng không được **override** lại.

Khi chúng ta gọi phương thức make_noise ở lớp con thì Ruby sẽ tìm trong lớp con đó có phương thức đó hay không, nếu có thì dùng phương thức ở lớp con, nếu không thì gọi lên phương thức đó ở lớp cha.
Output
```
Some noise
Animal is sleeping.
Woof!
Dog is sleeping.
Meow!
Cat is sleeping.
```
