# Ruby – Module và Exception

Trong phần này chúng ta sẽ tìm hiểu về **module** và **exception** trong Ruby.

# Module

Một **module** là một tập các phương thức, lớp, hằng số, do đó **module** cũng gần giống như lớp vậy, chỉ khác là **module** không thể tạo các đối tượng và không thể thừa kế.

Thường thì chúng ta sẽ gộp các lớp, phương thức và hằng số có liên quan với nhau vào một **module** để tránh xung đột tên. Nếu bạn đã từng làm việc với C# và Java thì có thể nói **module** trong Ruby tương đương với **namespace** trong C# và **package** trong Java vậy.

Ngoài ra chúng ta còn có thể sử dụng **module** trong Ruby để thực hiện đa thừa kế nữa.

Ví dụ 1:
```ruby
puts Math::PI
puts Math.sin 2
```
Math là một **module** có sẵn trong Ruby, **module** này chứa các hằng số và phương thức hỗ trợ thực hiện các phép tính toán học. Ở đoạn code trên chúng ta in ra hằng số PI và dùng phương thức sin.
```ruby
include Math

puts PI
puts sin 2
```
Nếu không muốn ghi tên **module** ra trực tiếp thì chúng ta có thể sử dụng từ khóa **include** Math để báo cho Ruby biết là chúng ta sẽ dùng **module** Math.
```
3.141592653589793
0.9092974268256817
```
Ví dụ 2:
```ruby
module Forest
 
    class Rock ; end
    class Tree ; end
    class Animal ; end    
    
end

module Town
    
   class Pool ; end
   class Cinema ; end
   class Square ; end
   class Animal ; end
        
end


p Forest::Tree.new
p Forest::Rock.new
p Town::Cinema.new

p Forest::Animal.new
p Town::Animal.new
```
Để định nghĩa một **module** thì chúng ta dùng cặp từ khóa **module…end**, tên **module** được đặt sau từ khóa **module**.
```ruby
module Forest
 
    class Rock ; end
    class Tree ; end
    class Animal ; end    
    
end
```
Thường thì chúng ta sẽ nhóm những thứ có liên quan với nhau lại vào trong một **module**. Như trong đoạn code trên chúng ta định nghĩa các lớp Rock (đá), Tree (cây) và Animal (động vật) vào trong **module** Forest (rừng).
```ruby
p Forest::Tree.new
p Forest::Rock.new
p Town::Cinema.new
```
Để truy xuất một đối tượng trong một **module** thì chúng ta dùng toán tử **::**
```ruby
p Forest::Animal.new
p Town::Animal.new
```
Như bình thường thì chúng ta không thể định nghĩa 2 lớp có tên giống nhau trong một file được. Nhưng ở đây chúng ta sử dụng thêm cả **module** nữa nên có thể định nghĩa 2 lớp có tên giống nhau trong một file.
```
#<Forest::Tree:0x97f35ec>
#<Forest::Rock:0x97f35b0>
#<Town::Cinema:0x97f3588>
#<Forest::Animal:0x97f3560>
#<Town::Animal:0x97f3538>
```
Ví dụ 3:

Hướng đối tượng trong C++ có hỗ trợ đa thừa kế, trong Java cũng hỗ trợ đa thừa kế thông qua **Interface**, còn Ruby hỗ trợ đa thừa kế thông qua **module**.
```ruby
module Device
    def switch_on ; puts "on" end    
    def switch_off ; puts "off" end
end

module Volume
    def volume_up ; puts "volume up" end    
    def vodule_down ; puts "volume down" end
end

module Pluggable
    def plug_in ; puts "plug in" end    
    def plug_out ; puts "plug out" end
end

class CellPhone
    include Device, Volume, Pluggable
   
    def ring
        puts "ringing"
    end    
end

cph = CellPhone.new
cph.switch_on
cph.volume_up
cph.ring
```
Đa thừa kế tức là một lớp có thể thừa kế từ nhiều lớp khác, chúng ta có thể sử dụng **module** của Ruby để thực hiện đa thừa kế.

Ở đây chúng ta định nghĩa một lớp, sau đó **include** các **module** bên trong lớp này và lớp đó sẽ có thể sử dụng những phương thức, hằng số… của các **module** đã được **include**.
```ruby
class CellPhone
    include Device, Volume, Pluggable
   
    def ring
        puts "ringing"
    end    
end
```
Trong ví dụ này chúng ta có 3 **module** Device, Volume và Pluggable, mỗi **module** có một số phương thức in chuỗi. Chúng ta cũng định nghĩa lớp CellPhone và **include** cả 3 **module** trên vào.
```ruby
cph = CellPhone.new
cph.switch_on
cph.volume_up
cph.ring
```
Như thế khi tạo đối tượng lớp CellPhone, chúng ta có thể gọi luôn cả các phương thức của những **module** mà lớp đó đã **include** chứ không cần gọi đến tên **module** nữa.
```
on
volume up
ringing
```

# Exception

Trong lập trình **có 3 loại lỗi là lỗi biên dịch, lỗi ngữ nghĩa và lỗi exception – lỗi ngoại lệ**. Lỗi **exception** là lỗi xảy ra trong quá trình chương trình chạy (tiếng anh là **run time error**). Ví dụ như bạn viết một chương trình máy tính bỏ túi gồm các chức năng cộng trừ nhân chia. Thoạt nhìn có vẻ như rất đơn giản, chỉ cần yêu cầu người dùng nhập vào 2 số và phép tính, thực hiện phép tính rồi trả lại kết quả cho người dùng. Nhưng chương trình này sẽ báo lỗi nếu người dùng thực hiện một phép tính chia với số chia là 0. Đó là loại lỗi chỉ xảy ra trong khi chương trình chạy, để phòng ngừa loại lỗi này thì chỉ có một cách là các lập trình viên phải đoán trước các trường hợp lỗi ngoại lệ có thể xảy ra và xử lý chúng trước trong code của mình. Nhưng vì bạn chẳng phải nhà tiên tri, bạn không thể nào đoán trước tất cả mọi thứ được ? nên trên thực tế thì các phần mềm lớn vẫn thường có lỗi chứ không có phần mềm nào không có lỗi cả, công việc của chúng ta là cố gắng phát hiện lỗi và sửa lỗi thôi.

Trong Ruby các lỗi **exception** thường gặp được định nghĩa thành một lớp riêng, và tất cả chúng đều được kế thừa từ lớp **Exception**. Ngoài ra chúng ta cũng có thể định nghĩa lớp **exception** của riêng chúng ta.

Ví dụ 1:
```ruby
x = 35
y = 0

begin
    z = x / y
    puts z
rescue => e
    puts "Error: #{e}"
end
```
Trong ví dụ này chúng ta sẽ thử thực hiện một phép chia với mẫu số là 0.
```ruby
begin
    z = x / y
    puts z
```
Những câu lệnh mà có khả năng giải phóng **exception** sẽ được đặt trong cặp từ khóa **begin...end**.
```ruby
rescue => e
    puts "Error: #{e}"
end
```
Để có thể bắt lỗi thì chúng ta dùng từ khóa **rescue** theo sau là dấu **=>** rồi đến tên tham số đối tượng **exception**. Các đối tượng **exception** sẽ chứa một chuỗi mô tả về tên lỗi **exception** đã xảy ra. Chúng ta có thể dùng phương thức **puts** để in đoạn chuỗi đó ra.
```
Error: divided by 0
```
Ví dụ 2:
```ruby
age = 17
begin
    if age < 18 
        raise "Under 18 is not allowed" 
    end 

    puts "Allowed" 
rescue => e
    puts e
    p e    
end
```
Chúng ta có thể tự giải phóng một lỗi **exception** bằng cách dùng từ khóa **raise**.
```ruby
begin
    if age < 18
        raise "Under 18 is not allowed"
    end
 
    puts "Allowed"
```
Theo sau từ khóa **raise** chúng ta đưa vào tham số là một chuỗi, Ruby sẽ tạo một đối tượng **RuntimeException** và truyền vào đó chuỗi này. **Khi một exception được giải phóng, chương trình sẽ bị ngắt ngay tại đó**.
```ruby
rescue => e
    puts e
    p e    
end
```
Nếu không có câu lệnh **rescue** để bắt lỗi thì chương trình sẽ thoát luôn, còn ở đây chúng ta có câu lệnh bắt lỗi nên chương trình sẽ tiếp tục thực thi những gì có trong câu lệnh này.

Nếu như phương thức **puts** chỉ in đoạn chuỗi mô tả lỗi thì phương thức p sẽ in cả tên lớp **exception** và đoạn chuỗi mô tả.
```
Under 18 is not allowed
#<RuntimeError: Under 18 is not allowed>
```
Ví dụ 3:
```ruby
age = 17

begin
    if age < 18 
        raise "Under 18 is not allowed" 
    end 
    puts "Entry allowed" 
rescue => e
    puts e
    p e
ensure
    exit 0
end
```
Ruby còn có từ khóa **ensure**, **những câu lệnh nằm sau từ khóa ensure sẽ được thực thi cho dù có xảy ra lỗi hay không**. Từ khóa **ensure** có tác dụng **giống như từ khóa finally trong các ngôn ngữ như C#, Java…**
```ruby
ensure
    exit 0
end
```
Chúng ta thực thi câu lệnh **exit** để thoát chương trình trong từ khóa **ensure**, khi chương trình chạy, cho dù có lỗi xảy ra hay không thì câu lệnh exit cũng sẽ được thực thi, mặc dù ở đây câu lệnh này cũng không có ý nghĩa mấy vì dù gì chương trình cũng tự thoát.

Ví dụ 4:
```ruby
age = 17

class NotOver18Exception < StandardError
end

begin
    if age < 18 
        raise NotOver18Exception, "Under 18 is not allowed" 
    end 
    puts "Entry allowed" 
rescue => e
    puts e
    p e
ensure
    exit 0
end
```
Chúng ta có thể định nghĩa lớp **exception** của riêng chúng ta và giải phóng đối tượng thuộc lớp đó.
```ruby
class NotOver18Exception < StandardError
end
```
Một lớp **exception** phải được kế thừa từ lớp **StandardError**, trong ví dụ này chúng ta định nghĩa lớp **NotOver18Exception** kế thừa từ lớp **StandardError**.
```ruby
if age < 18
    raise NotOver18Exception, "Under 18 is not allowed"
end
```
Để giải phóng lỗi thì chúng ta đưa thêm tên lớp vào sau từ khóa **raise**, rồi đến đoạn chuỗi mô tả lỗi.
```
Under 18 is not allowed
#<NotOver18Exception: Under 18 is not allowed>
```
