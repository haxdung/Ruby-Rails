# Ruby – Hướng đối tượng – Phần 1

Chúng ta đã tìm hiểu sơ qua về đối tượng trong các bài trước, trong bài này chúng ta sẽ tìm hiểu sâu hơn.

Ngôn ngữ lập trình được phân ra làm nhiều loại mô hình như mô hình lập trình hướng thủ tục, lập trình hướng hàm, lập trình hướng đối tượng… Ruby là ngôn ngữ lập trình hướng đối tượng.

Lập trình hướng đối tượng (Object-oriented programming – OOP) là mô hình lập trình sử dụng các đối tượng để thiết kế nên kiến trúc của chương trình ứng dụng.

OOP có các khái niệm cơ bản sau đây:
```
    Trừu tượng (Abstraction)
    Đa hình (Polymorphism)
    Đóng gói (Encapsulation)
    Thừa kế (Inheritance)
```
Khái niệm đối tượng

Đây là các thành phần cấu tạo nên một chương trình hướng đối tượng. Một đối tượng trong OOP chứa 2 thành phần là thuộc tính và phương thức, trong đó thuộc tính đơn giản chỉ là các biến chứa dữ liệu, phương thức chỉ là các hàm/thủ tục. Các đối tượng sẽ giao tiếp với nhau thông qua phương thức của chúng. Mỗi đối tượng có thể nhận/gửi thông điệp cho nhau và xử lý dữ liệu của chúng.

Để tạo một đối tượng thì chúng ta phải có lớp, lớp chính là một cái khuôn/bản vẽ/bản thiết kế… để tạo nên các đối tượng.

Ví dụ khi nói lớp Người thì chúng ta biết rằng một người bao gồm tên, tuổi, màu da, giới tính… có thể ăn, nói, nhảy múa… Còn khi nói đối tượng người thì chúng ta có đối tượng Jack, 23 tuổi, quốc tịch Mỹ, biết hát, đối tượng Jennifer 19 tuổi, quốc tịch Nauy, biết nấu ăn…

Ví dụ:
object_creation.rb
```
class Being
   
end
 
b = Being.new
puts b
```
Trong đoạn code trên chúng ta định nghĩa lớp và tạo một đối tượng từ lớp đó.
```
class Being
   
end
```
Để định nghĩa lớp thì chúng ta dùng cặp từ khóa class...end với tên lớp mà chúng ta muốn đặt sau từ khóa class. Hiện tại lớp này là lớp rỗng, không có gì cả.
```
b = Being.new
```
Để tạo một đối tượng thuộc lớp Being thì chúng ta ghi tên lớp rồi dùng phương thức new. Phương thức này sẽ trả về địa chỉ tham chiếu đến đối tượng vừa tạo, ở trên chúng ta lưu lại đối tượng này vào biến b.
```
puts b
```
Khi chúng ta gọi phương thức puts lên một đối tượng, phương thức này sẽ gọi phương thức to_s có trong mỗi đối tượng. Trong trường hợp của chúng ta thì do chưa định nghĩa phương thức to_s nên phương thức puts sẽ trả về địa chỉ tham chiếu đến đối tượng.
Output
```
#<Being:0x9f3c290>
```

Phương thức khởi tạo

Phương thức khởi tạo là một phương thức đặc biệt, phương thức này từ động được gọi khi chúng ta tạo một đối tượng. Phương thức khởi tạo không trả về một giá trị nào cả. Mục đích chính của phương thức khởi tạo chỉ là thiết lập trạng thái cho đối tượng. Tất cả các phương thức khởi tạo trong Ruby đều có tên là initialize.

Ví dụ 1:
constructor1.rb
```
class Being
 
    def initialize
        puts "Being is created"
    end
 
end
 
Being.new
```
Trong ví dụ trên chúng ta định nghĩa phương thức initialize. Trong phương thức này chúng ta in một chuỗi string ra màn hình. Khi chúng ta gọi phương thức new, phương thức này sẽ tự động gọi phương thức initialize.

Để định nghĩa một phương thức thì chúng ta dùng cặp từ khóa def...end với tên phương thức nằm phía sau từ khóa def.
Output
```
Being is created
```
Ví dụ 2:
constructor2.rb
```
class Person
 
    def initialize name
        @name = name
    end
 
    def get_name
        @name
    end
 
end
 
p1 = Person.new "Jane"
p2 = Person.new "Beky"
 
puts p1.get_name
puts p2.get_name
```
Thuộc tính của một đối tượng là các biến lưu trữ giá trị của đối tượng đó. Các biến này còn được gọi là biến instance. Mỗi đối tượng đều có thuộc tính của riêng nó, tức là các đối tượng thuộc cùng một lớp thì có các biến instance khác nhau.
```
class Person
 
    def initialize name
        @name = name
    end
```
Trong đoạn code trên, hàm khởi tạo initialize nhận vào một biến tham số có tên là name, chúng ta gán giá trị của tham số đó vào biến instance @name.
```
def get_name
    @name
end
```
Chúng ta định nghĩa phương thức get_name, phương thức này trả về giá trị của biến @name. Trong Ruby các biến instance chỉ có thể truy xuất trong các phương thức.
```
p1 = Person.new "Jane"
p2 = Person.new "Beky"
```
Để truyền tham số thì chúng ta ghi phía sau tên phương thức khi gọi. Trong đoạn code trên các chuỗi “Jane”, “Beky” sẽ được truyền vào hàm initialize.
Output
```
Jane
Beky
```

Phương thức thành phần

Phương thức thành phần (hay gọi ngắn gọn là phương thức) là các hàm được định nghĩa bên trong một lớp, mục đích của phương thức là thực hiện một công việc nào đó. Thường thì phương thức sẽ làm việc với các thuộc tính của đối tượng. Phương thức rất quan trọng với tính năng đóng gói trong lập trình hướng đối tượng, đóng gói tức là chúng ta không quan tâm phương thức làm những gì mà chỉ quan tâm đến kết quả cuối cùng của phương thức mà thôi.

Ví dụ 1:
method1.rb
```
class Person
 
    def initialize name
        @name = name
    end
 
    def get_name
        @name
    end
 
end
 
per = Person.new "Jane"
 
puts per.get_name
puts per.send :get_name
```
Để gọi một phương thức thì chúng ta có 2 cách.
```
puts per.get_name
```
Cách đầu tiên và cũng là phổ biến nhất là ghi tên đối tượng, dấu chấm rồi đến tên phương thức.
```
puts per.send :get_name
```
Cách thứ hai là gọi phương thức send, theo sau là tên phương thức nhưng viết dưới dạng một Symbol, tức là thêm dấu 2 chấm ":" vào trước tên phương thức.

Ví dụ 2:
method2.rb
```
class Circle
    
    @@PI = 3.141592
 
    def initialize
        @radius = 0
    end
 
    def set_radius radius
        @radius = radius
    end
 
    def area
        @radius * @radius * @@PI
    end
 
end
 
 
c = Circle.new
c.set_radius 5
puts c.area
```
Trong đoạn code trên chúng ta định nghĩa lớp Circle có 2 phương thức.
```
@@PI = 3.141592
```
Trong lớp Circle chúng ta định nghĩa một biến class là @@PI, biến class là biến dùng chung cho tất cả các đối tượng.
```
def initialize
    @radius = 0
end
```
Chúng ta định nghĩa một biến instance là @radius.
```
def set_radius radius
    @radius = radius
end
```
Phương thức set_radius sẽ nhận một tham số đầu vào và gán giá trị đó cho biến @radius.
```
def area
    @radius * @radius * @@PI
end
```
Phương thức area sẽ tính diện tích hình tròn với biến @radius và @@PI.
```
c = Circle.new
c.set_radius 5
puts c.area
```
Nếu như trong các ngôn ngữ khác, chúng ta có từ khóa return để trả về một giá trị của một phương thức thì trong Ruby giá trị này sẽ tự động được trả về ngầm bằng giá trị của câu lệnh cuối cùng được thực hiện trong phương thức. Trong đoạn code trên, phương thức puts c.area sẽ in ra giá trị được trả về là diện tích được tính bên trong phương thức area.
Output
```
78.5398
```

Quyền truy cập

Quyền truy cập tức là phạm vi truy xuất các thuộc tính và phương thức của mỗi đối tượng. Ruby có 3 loại quyền truy cập là public, protected và private. Trong Ruby, tất cả các thuộc tính đều có quyền truy cập là private và không thể thay đổi được, còn các phương thức thì mặc định có quyền truy cập là public nhưng có thể thay đổi được.

Quyền truy cập loại public cho phép chúng ta truy cập thành phần của đối tượng ở bên trong lẫn bên ngoài lớp. Quyền protected và private giống nhau ở chỗ đều không cho phép truy cập thành phần của đối tượng ở bên ngoài lớp, khác nhau ở chỗ private không gọi được với từ khóa self, còn protected thì được.

Quyền truy cập đảm bảo an toàn cho dữ liệu không bị thay đổi cho dù là cố ý hay vô ý.

Ví dụ 1:
access_modifier1.rb
```
class Some
         
     def method1
         puts "public method1 called"
     end
 
    public
     
     def method2
         puts "public method2 called" 
     end
      
     def method3
         puts "public method3 called"
         method1
         self.method1
     end         
end
 
s = Some.new
s.method1
s.method2
s.method3
```
Trong ví dụ này chúng ta sử dụng quyền truy cập public.
```
def method1
    puts "public method1 called"
end
```
Phương thức method1 có quyền truy cập mặc định là public.
```
public
 
  def method2
      puts "public method2 called" 
  end
 
  ...
```
Ngoài ra chúng ta có thể chỉ rõ cho Ruby biết là phương thức nào có quyền public bằng cách ghi từ khóa public lên trước phần định nghĩa phương thức đó, trong trường hợp này cả method2 và method3 đều có quyền truy cập là public.
```
s = Some.new
s.method1
s.method2
s.method3
```
Chỉ có các phương thức public mới có thể truy cập ở bên ngoài phần định nghĩa lớp.
Output
```
public method1 called
public method2 called
public method3 called
public method1 called
public method1 called
```
Ví dụ 2:
access_modifier2.rb
```
class Some
     
    def initialize
        method1
        # self.method1
    end
 
    private
     
     def method1
         puts "private method1 called" 
     end
            
end
 
 
s = Some.new
# s.method1
```
Để chỉ định phương thức nào là private thì chúng ta đặt từ khóa private lên trước định nghĩa phương thức đó. Các phương thức private chỉ có thể gọi được trong phần định nghĩa lớp nhưng không được sử dụng từ khóa self.
Output
```
private method called
```
Ví dụ 3:
access_modifier3.rb
```
class Some
     
    def initialize
        method1
        self.method1
    end
 
    protected
     
     def method1
         puts "protected method1 called" 
     end
            
end
 
 
s = Some.new
# s.method1
```
Tương tự như private, để chỉ định phương thức protected thì chúng ta đặt từ khóa protected lên trước định nghĩa phương thức. Phương thức protected khác private ở chỗ là chúng có thể truy cập với từ khóa self, giống private ở chỗ là không thể truy cập được ở bên ngoài phần định nghĩa lớp.
Thừa kế

Thừa kế là tính năng cho phép định nghĩa các lớp dựa trên các lớp đã có. Lớp thừa kế từ một lớp khác được gọi là lớp dẫn xuất, lớp được lớp khác thừa kế lại được gọi là lớp cơ sở. Lớp dẫn xuất thừa hưởng các thành phần của lớp cơ sở và có thể có thêm các thành phần của riêng chúng. Tính năng thừa kế cho phép lập trình viên giảm thiểu sự phức tạp của chương trình.

Ví dụ 1:
inheritance1.rb
```
class Being
 
    def initialize
        puts "Being class created"
    end
end
 
class Human < Being
 
   def initialize
       super
       puts "Human class created"
   end
end
 
Being.new
Human.new
```
Trong ví dụ trên chúng ta có 2 lớp là lớp Being và lớp Human, trong đó lớp Being là lớp cơ sở, lớp Human là lớp dẫn xuất. Tức là lớp Human kế thừa từ lớp Being.
```
class Human < Being
```
Để một lớp kế thừa từ một lớp khác thì chúng ta ghi dấu "<" vào sau tên lớp và ghi tên lớp dẫn xuất phía sau.
```
def initialize
    super
    puts "Human class created"
end
```
Phương thức super có tác dụng gọi đến hàm khởi tạo của lớp cha.
Output
```
Being class created
Being class created
Human class created
```
Ví dụ 2:

Một lớp có thể có nhiều lớp cơ sở. Mỗi lớp trong Ruby mặc định có phương thức ancestors, phương thức này trả về danh sách các lớp cơ sở của lớp đó. Và mặc định tất cả các lớp trong Ruby đều kế thừa từ một lớp gốc có tên là Object và BasicObject trong module Kernel.
inheritance2.rb
```
class Being 
end
 
class Living < Being 
end
 
class Mammal < Living 
end
 
class Human < Mammal 
end
     
     
p Human.ancestors
```
Trong ví dụ này chúng ta có bốn lớp là Human kế thừa từ Mammal, lớp Mammal lại kế thừa từ lớp Living và lớp Living kế thừa từ lớp Being.
```
p Human.ancestors
```
Phương thức ancestors sẽ in danh sách các lớp cơ sở.
Output
```
[Human, Mammal, Living, Being, Object, Kernel, BasicObject]
```
Lưu ý là tính năng thừa kế trong Ruby hơi khác so với các ngôn ngữ như C++, C#, Java… ở chỗ là trong các ngôn ngữ khác thì các thành phần public và protected đều được truyền lại từ lớp cha đến lớp con còn thành phần private thì không, nhưng trong Ruby thì cả 3 loại public, protected và private đều được truyền lại cho lớp con, tức là tính năng thừa kế trong Ruby không có liên quan gì đến quyền truy cập cả.
Phương thức super

Phương thức super có tác dụng gọi đến phương thức cùng tên ở lớp cha.
super_method.rb
```
class Base
    
    def show x=0, y=0
        p "Base class, x: #{x}, y: #{y}"
    end
end
 
class Derived < Base
 
    def show x, y
        super
        super x
        super x, y
        super()
    end
end
 
 
d = Derived.new
d.show 3, 3
```
Trong ví dụ trên chúng ta có lớp Base và lớp Derived, trong đó lớp Derived kế thừa từ lớp Base. Cả 2 lớp này đều có phương thức show.
```
def show x, y
    super
    super x
    super x, y
    super()
end
```
Việc gọi super trong phương thức show ở lớp con sẽ gọi đến phương thức show ở lớp cha. Nếu phương thức ở lớp cha có nhận tham số mà chúng ta không truyền vào phương thức super thì phương thức này sẽ tự động nhận tham số của phương thức con, tức là các tham số truyền vào phương thức con sẽ tự động truyền vào trong lời gọi phương thức super luôn. Hoặc chúng ta có thể gọi super() để không truyền vào một tham số nào cả.
Output
```
"Base class, x: 3, y: 3"
"Base class, x: 3, y: 0"
"Base class, x: 3, y: 3"
"Base class, x: 0, y: 0"
```
