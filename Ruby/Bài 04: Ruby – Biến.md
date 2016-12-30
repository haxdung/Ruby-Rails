# Ruby – Biến

Biến là nơi lưu trữ dữ liệu. Mỗi biến có một tên riêng, tên biến được đặt theo một số quy luật riêng. Mỗi biến có một kiểu dữ liệu riêng. Ruby có rất nhiều kiểu dữ liệu có sẵn. Kiểu dữ liệu trong Ruby là kiểu dữ liệu động, tức là khi chúng ta khai báo biến và gán giá trị thì Ruby sẽ tự động gán kiểu dữ liệu cho biến dựa trên giá trị đó chứ chúng ta không cần phải khai báo trước kiểu dữ liệu như trong các ngôn ngữ như C++, Java…
```ruby
i = 5
puts i
i = 7
puts i
```
Giá trị của biến có thể thay đổi được. Trong đoạn code trên chúng ta có biến i có giá trị ban đầu là 5, sau đó thay bằng 7.
Quy tắc đặt tên biến

Tên biến là có phân biệt HOA-thường. Tức là biến age và biến Age là 2 biến khác nhau.
case.rb
```ruby
i = 5
p i
I = 7
p I
```
Trong đoạn code trên chúng ta có biến i và biến I mang các giá trị khác nhau.
Output
```
5
7
```
Biến được đặt tên bằng các kí tự chữ cái, chữ số và dấu gạch dưới “_”, nhưng không thể bắt đầu bằng chữ số và chữ cái in hoa.
```ruby
name = "Jane"
placeOfBirth = "Bratislava"
placeOfBirth = "Kosice"
favorite_season = "autumn"
 
n1 = 2
n2 = 4
n3 = 7
 
p name, placeOfBirth, favorite_season
p n1, n2, n3
```
Trong đoạn code trên n1, n2 và n3 là các tên biến hợp lệ.

Khi đặt tên biến chúng ta nên đặt tên sao cho dễ nhớ và dễ sử dụng.

# Sigil

Biến trong Ruby có thể bắt đầu bằng một số kí tự đặc biệt và được gọi là **sigil**, các kí tự sigil dùng để chỉ ra **phạm vi hoạt động của biến**.
sigils.rb
```ruby
tree_name = "pine"
$car_name = "Peugeot"
@sea_name = "Black sea"
@@species = "Cat"
 
p local_variables
p global_variables.include? :$car_name
p self.instance_variables
p Object.class_variables
```
Trong đoạn code trên chúng ta có 4 biến với 4 phạm vi hoạt động khác nhau tùy theo từng kí hiệu sigil.
```ruby
tree_name = "pine"
```
Biến không có kí tự đặc biệt nào được gọi là biến cục bộ, tức là chỉ có hiệu lực ở phạm vi trong từng phương thức, lớp… nhất định.
```ruby
$car_name = "Peugeot"
```
Kí tự **$** cho biết biến đó là biến toàn cục, biến toàn cục có hiệu lực trong toàn bộ code Ruby.
```ruby
@sea_name = "Black sea"
```
Kí tự **@** cho biết biến đó là biến **instance**, biến này chỉ có hiệu lực trong một đối tượng.
```ruby
@@species = "Cat"
```
Cuối cùng là kí tự **@@** tức biến **class**, tất cả các đối tượng của một class đều có thể truy xuất biến này.

Chúng ta sẽ tìm hiểu thêm về các loại biến này ở dưới và trong các bài sau.
```ruby
p local_variables
```
Biến **local_variables** là một mảng lưu trữ toàn bộ các biến cục bộ hiện có.
```ruby
p global_variables.include? :$car_name
```
Tương tự, chúng ta có biến **global_variables** lưu toàn bộ các biến toàn cục, nhưng ở đây chúng ta không cho in ra toàn bộ vì số lượng biến toàn cục có sẵn rất nhiều, thay vào đó chúng ta dùng phương thức **include?** để kiểm tra xem biến $car_name của chúng ta có nằm trong danh sách đó hay không.
```ruby
p self.instance_variables
```
Ở trên chúng ta tham chiếu đến biến **instance_variables**, biến này lưu trữ toàn bộ biến **instance** trong đối tượng hiện tại, ở đây là những biến **instance** được khai báo trong chương trình – tức là **@sea_name**.

Ngoài ra ở đây chúng ta còn dùng thêm biến **self** nữa, biến **self** tham chiếu đến đối tượng hiện tại đang được sử dụng, ở đây là chương trình chính, nếu bạn đã từng làm việc với con trỏ this trong C++, Java… thì **self** cũng giống như con trỏ **this** vậy. Thực ra ở đây bạn cũng không cần dùng đến **self** vì chúng ta đang gọi hàm ngay trong chương trình chính chứ không phải bên trong một phương thức hay lớp nào đó.
```ruby
p Object.class_variables
```
Cuối cùng là biến **class_variables**,  biến này lưu trữ toàn bộ biến **class** có trong chương trình.
Output
```
[:tree_name]
true
[:@sea_name]
[:@@species]
```

# Biến cục bộ

Biến cục bộ là biến chỉ có hiệu lực trong một phạm vi nhất định trong toàn bộ code Ruby, cụ thể là biến nằm bên trong hàm, phương thức, class.
locals.rb
```ruby
def method1
   x = 5
   p x    
end
 
method1 
 
p x
```
Trong đoạn code trên chúng ta có phương thức method1 có một biến là x, biến này là biến cục bộ, chúng ta chỉ có thể sử dụng biến này giữa cặp từ khóa **def...end**.
```
method1 
```
Chúng ta gọi phương thức bằng cách ghi rõ tên phương thức ra.
```
p x
```
Nếu chúng ta truy xuất biến ở ngoài phạm vi phương thức thì Ruby sẽ báo lỗi NameError vì Ruby không tìm thấy biến đó.
Output
```
5
./locals.rb:11:in `<main>': undefined local variable 
or method `x' for main:Object (NameError)
```
Đoạn code dưới đây chỉnh sửa lại từ đoạn code trên một tí.
locals2.rb
```ruby
x = 5
 
def method1
    x = 10
    p x
end
 
method1
 
p x
```
Trong đoạn code trên chúng ta có 2 biến tên là x, một biến nằm trong phương thức method1 và một biến nằm ở ngoài, mặc dù chúng có cùng tên nhưng đây là 2 biến khác nhau hoàn toàn.
```ruby
x = 5
```
Biến x đầu tiên được gán giá trị là 5, biến này có phạm vi trong toàn đoạn code nhưng không thể truy cập ở bên trong phương thức method1.
```ruby
def method1
    x = 10
    p x
end
```
Bên trong phương thức method1 lại có một biến x khác nữa được gán giá trị là 10. Biến này chỉ có hiệu lực bên trong cặp từ khóa **def...end**.
Output
```
10
5
```
Phương thức có thể nhận vào các tham số, các tham số khi truyền vào phương thức sẽ có hiệu lực như một biến cục bộ bên trong phương thức đó:
parameters.rb
```ruby
def rectangle_area a, b
    puts local_variables
    return a * b
end
 
puts rectangle_area 5, 6
```
Ở trên chúng ta có phương thức **rectangle_area** nhận vào 2 tham số a và b. Phương thức này tính và trả về diện tích hình chữ nhật.
```
puts rectangle_area 5, 6
```
Để truyền tham số vào phương thức thì chúng ta ghi giá trị hoặc biến vào sau lời gọi phương thức.
Output
```
a
b
30
```
Một phương thức có thể được định nghĩa bên trong một phương thức khác, phương thức đó gọi là phương thức nội, phương thức nội cũng có biến cục bộ của riêng nó.
inner_methods.rb
```ruby
def method1
     
    def method2
                 
        def method3
            m5, m6 = 3
            puts "Level 3"
            puts local_variables
        end           
         
        m3, m4 = 3
        puts "Level 2"
        puts local_variables
        method3    
    end       
     
    m1, m2 = 3
    puts "Level 1"
    puts local_variables
    method2
             
end
 
method1
```
Trong đoạn code trên chúng ta định nghĩa 3 phương thức là method1, method2 và method3, trong đó method2 và method3 là các phương thức nội. Phương thức method2 nằm bên trong method1 và method3 lại nằm bên trong method2. Các biến nằm ở phương thức nào thì chỉ có hiệu lực ở phạm vi phương thức đó.
Output
```
Level 1
m1
m2
Level 2
m3
m4
Level 3
m5
m6
```

# Biến toàn cục

Biến toàn cục khác biến cục bộ ở chỗ là có hiệu lực trên toàn code. Biến toàn cục có tên bắt đầu bằng ký tự $.
globals.rb
```ruby
$gb = 6
 
 
module ModuleM        
    puts "Inside module"
    puts $gb
end
 
 
def method1
    puts "Inside method"
    puts $gb
end
 
 
class Some
    puts "Inside class"
    puts $gb
end
 
method1
 
puts "Inside toplevel"
puts $gb
puts global_variables.include? :$gb
```
Trong đoạn code trên chúng ta có biến toàn cục $gb. Biến toàn cục có thể sử dụng được trong cả module, phương thức, lớp…
```ruby
$gb = 6
```
Chúng ta khai báo biến toàn cục $gb và gán giá trị là 6.
```ruby
module ModuleM        
    puts "Inside module"
    puts $gb
end
```
Trong module ModuleM chúng ta in giá trị của biến toàn cục.
```ruby
def method1
    puts "Inside method"
    puts $gb
end
```
Trong phương thức method1 cũng vậy.
```ruby
class Some
    puts "Inside class"
    puts $gb
end
```
Và cả bên trong class cũng vậy.
```ruby
puts $gb
puts global_variables.include? :$gb
```
Ở ngoài các phương thức, class… chúng ta cũng có thể gọi đến biến toàn cục $gb.
Output
```
Inside module
6
Inside class
6
Inside method
6
Inside toplevel
6
true
```
Ngoài các biến toàn cục do chúng ta định nghĩa, Ruby còn có sẵn các biến được định nghĩa sẵn.
```ruby
p $LOAD_PATH
p $:
```
Ở trên chúng ta dùng 2 biến $LOAD_PATH và $:, đây đều là các biến lưu trữ thông tin về các đường dẫn thư mục có trong biến môi trường Path của Windows.

# Biến instance và biến class

Ở đây chúng ta sẽ tìm hiểu sơ qua về biến **instance** và biến **class**. Chúng ta sẽ tìm hiểu thêm trong bài hướng đối tượng.

Biến **instance** là biến nằm trong một đối tượng cụ thể. Mỗi đối tượng có những biến **instance** riêng của chúng, biến **instance** có tên bắt đầu bằng kí tự **@**.

Biến **class** là biến nằm trong một lớp. Những đối tượng được tạo ra từ lớp đó sẽ dùng chung biến **class**, biến **class** có tên bắt đầu bằng kí tự **@@**.
instance_class.rb
```ruby
class Being
     
    @@is = true
        
    def initialize nm
        @name = nm
    end
     
    def to_s
        "This is #{@name}"
    end   
     
    def does_exist?
        @@is
    end
end
 
b1 = Being.new "Being 1"
b2 = Being.new "Being 2"
b3 = Being.new "Being 3"
 
puts b1, b2, b3
 
p b1.does_exist?
p b2.does_exist?
p b3.does_exist?
```
Trong đoạn code trên chúng ta định nghĩa lớp Being. Lớp này có một biến **instance** và một biến **class**.
```ruby
class Being
     
    @@is = true
```
Biến **@@is** là một biến class, tất cả các đối tượng thuộc lớp Being đều dùng chung một biến **@@is**.
```ruby
def initialize nm
    @name = nm
end
```
Phương thức **initialize** là phương thức khởi tạo. Phương thức này tự động được gọi khi chúng ta khai báo đối tượng. Mỗi đối tượng thuộc lớp Being có biến instance **@name** khác nhau.
```ruby
def to_s
    "This is #{@name}"
end      
```
Phương thức **to_s** tự động được gọi khi dùng với hàm như **p** hay **puts**. Ở đây phương thức này trả về một chuỗi.
```ruby
def does_exist?
    @@is
end
```
Phương thức **does_exist?** trả về biến **class** của lớp đó.
```ruby
b1 = Being.new "Being 1"
b2 = Being.new "Being 2"
b3 = Being.new "Being 3"
```
Sau khi đã định nghĩa lớp, chúng ta khai báo 3 đối tượng thuộc lớp Being là b1, b2 và b3. Mỗi đối tượng khi khởi tạo được nhận một tham số dùng cho biến **@name** của riêng chúng.
```ruby
puts b1, b2, b3
```
Phương thức **puts** sẽ tự động gọi đến phương thức **to_s** tương ứng với từng đối tượng.
```ruby
p b1.does_exist?
p b2.does_exist?
p b3.does_exist?
```
Phương thức **does_exist?** sẽ trả về giá trị của biến **@@is**, do cả 3 đối tượng này đều dùng chung biến class **@@is** nên kết quả trả về là như nhau.
Output
```
This is Being 1
This is Being 2
This is Being 3
true
true
true
```
