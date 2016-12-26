# Ruby – Kiểu dữ liệu – Phần 1
Trong phần này chúng ta sẽ tìm hiểu về các kiểu dữ liệu.

Tất cả các chương trình máy tính trên thế giới đều sử dụng dữ liệu, từ trình soạn thảo văn bản, máy tính, game… dữ liệu cũng được chia làm nhiều loại khác nhau chẳng hạn như số, kí tự, hình ảnh, âm thanh… Kiểu dữ liệu là một tập các giá trị và các thao tác có thể có trên các giá trị đó.

Tất cả các kiểu dữ liệu trong Ruby đều là lớp. Ruby hỗ trợ một số kiểu dữ liệu cơ bản sau đây:
```
    Boolean – kiểu luận lý
    Symbol
    Number – số
    String – chuỗi kí tự
    Array – mảng
    Hashe – bảng băm
```
Ví dụ:
types.rb
```
h = { :name => "Jane", :age => 17 }
 
p true.class, false.class
p "Ruby".class
p 1.class
p 4.5.class
p 3_463_456_457.class
p :age.class
p [1, 2, 3].class
p h.class
```
Trong đoạn code trên chúng ta in tên lớp của từng kiểu dữ liệu khác nhau.
```
p true.class, false.class
```
Kiểu boolean có 2 giá trị là True hoặc False.
```
p "Ruby".class
```
Kiểu string, chúng ta đã làm việc với kiểu này trong các bài trước.
```
p 1.class
p 4.5.class
p 3_463_456_457.class
```
Kiểu số, gồm số nguyên và số thực.
```
p :age.class
```

# Kiểu Symbol.

```
p [1, 2, 3].class
p h.class
```
Ở đây chúng ta có một đối tượng mảng và một đối tượng bảng băm.
Output
```
TrueClass
FalseClass
String
Fixnum
Float
Bignum
Symbol
Array
Hash
```

# Kiểu Boolean

Nói một cách “triết lý” thì trên thế giới này có một số thứ tồn tại theo 2 trạng thái/thái cực khác nhau… chẳng hạn như có Thiên đàng và Địa ngục, Nước và Lửa, Nam và Nữ… kiểu dữ liệu boolean cũng vậy, đối tượng thuộc kiểu này có một trong 2 trạng thái là True (đúng) hoặc False (sai). Đây là một kiểu dữ liệu quan trọng mà hầu hết ngôn ngữ lập trình nào cũng có.

Ví dụ:
kid.rb
```
bool = [true, false]
 
male = bool[rand(2)]
 
 
if male
    puts "We will use name John"
else
    puts "We will use name Victoria"
end
```
Trong đoạn code trên chúng ta sử dụng phương thức rand() để lấy giá trị ngẫu nhiên từ 0→1.
```
bool = [true, false]
```
Chúng ta có một biến tên là bool, đây là một mảng có 2 giá trị là true hoặc false. Một mảng được tạo bằng cách sử dụng cặp dấu [].
```
male = bool[rand(2)]
```
Khi phương thức rand() trả về 0 hoặc 1, chúng ta dùng kết quả đó để lấy giá trị tương ứng trong mảng bool, tức là nếu 0 thì biến male có giá tri là true, nếu 1 thì male là false.
```
if male
    puts "We will use name John"
else
    puts "We will use name Victoria"
end
```
Tùy vào giá trị của male mà chúng ta in ra câu lệnh tương ứng với từ khóa if..else..end.
Output
```
We will use name Victoria
```

# Kiểu Symbol

Nếu bạn biết kiểu enum trong C++, Java… thì trong Ruby chúng được gọi là Symbol. Symbol được dùng để biểu diễn các đối tượng khác. Dùng symbol sẽ tiết kiệm được nhiều tài nguyên hơn so với dùng biến thông thường. Tất cả các biến symbol đều là một đối tượng từ lớp Symbol. Để định nghĩa một symbol thì chúng ta thêm dấu hai chấm ":" vào trước giá trị, ví dụ :name. Hầu hết các đối tượng trong Ruby đều có phương thức to_sym để chuyển một đối tượng thành một symbol.

Symbol không thể thay đổi được giá trị. Thường thì symbol được dùng để làm khóa trong bảng băm.
symbols.rb
```
p :name
p :name.class
p :name.methods.size
p "Jane".methods.size
 
p :name.object_id
p :name.object_id
p "name".object_id
p "name".object_id
```
Trong đoạn code trên chúng ta thực hiện một số thao tác với symbol.
```
p :name
p :name.class
```
Chúng ta in symbol và tên của chúng ra màn hình.
```
p :name.methods.size
p "Jane".methods.size
```
Chúng ta so sánh kích thước dữ liệu của một symbol và một string. Rõ ràng là một string có kích thước lớn hơn một symbol.
```
p :name.object_id
p :name.object_id
p "name".object_id
p "name".object_id
```
Symbol giống nhau thì có id giống nhau, string giống nhau thì lại có id khác nhau.
Output
```
:name
Symbol
79
162
10328
10328
77344750
77344730
```
Ngoài ra Symbol cũng thường được dùng để dánh dấu, chẳng hạn như thay vì khai báo biến number = 1 rồi thực hiện if number == 1... thì ở đây chúng ta dùng symbol sẽ tiết kiệm được bộ nhớ cũng như dễ code hơn.
light.rb
```
light = :on
 
if light == :on
    puts "The light is on"
else
    puts "The light is off"
end
 
light = :off
 
if light == :on
    puts "The light is on"
else
    puts "The light is off"
end
```
Trong đoạn code trên chúng ta in các đoạn text khác nhau tùy theo giá trị của biến light.

Symbol còn được dùng để làm khóa trong bảng băm.
symbol_hash.rb
```
domains = {:sk => "Slovakia", :no => "Norway", :hu => "Hungary"}
 
puts domains[:sk]
puts domains[:no]
puts domains[:hu]
```
Trong đoạn code trên chúng ta có một đối tượng bảng băm là domains, đối tượng này dùng khóa là các Symbol.
```
puts domains[:sk]
puts domains[:no]
puts domains[:hu]
```
Chúng ta lấy giá trị của từng phần tử trong bảng băm bằng khóa.
Output
```
Slovakia
Norway
Hungary
```

# Kiểu số nguyên – Integer

Trong lập trình thì thì integer là một kiểu dữ liệu cơ bản, mặc dù trong toán thì số nguyên là  tập hợp Z, một tập hợp vô hạn, nhưng trong máy tính thì không có cái gì vô hạn cả, chúng ta có thể có tập hợp các số nguyên nhưng tập hợp này chỉ trong một phạm vi nhất định.

Trong Ruby thì số nguyên là các đối tượng thuộc lớp Fixnum hoặc Bignum, 2 lớp này có độ lớn khác nhau, độ lớn là khoảng giá trị của một đối tượng, ví dụ như trong C++, Java thì một số nguyên thường có độ lớn từ -2^32 đến 2^32, trong Ruby thì độ lớn của Fixnum tùy thuộc vào hệ điều hành, nếu một số nguyên có giá trị lớn hơn ngưỡng cho phép thì sẽ tự động được chuyển thành kiểu Bignum nên chúng ta cũng không cần phải quan tâm lắm đến vấn đề này.
integers.rb
```
p -2
p 121
p 123265
p -34253464356
p 34867367893463476
 
p 1.class
p 23453246.class
p 234532423563456346.class
p 2345324235632363463456456346.class
 
p 5 / 2
p 5.div 2
```
Đoạn code trên thực hiện một số thao tác với số nguyên.
```
p -2
p 121
p 123265
p -34253464356
p 34867367893463476
```
Trên đây là các con số cả âm lẫn không âm với các độ lớn khác nhau.
```
p 1.class
p 23453246.class
p 234532423563456346.class
p 2345324235632363463456456346.class
```
Chúng ta in ra tên lớp của các số nguyên. Hai số đầu tiên có kiểu Fixnum trong khi 2 số sau có kiểu Bignum.
```
p 5 / 2
p 5.div 2
```
Chúng ta thực hiện phép chia 2 số nguyên bằng toán tử / và phương thức div. Phép chia một số nguyên cũng sẽ trả về một số nguyên.
Output
```
-2
121
123265
-34253464356
34867367893463476
Fixnum
Fixnum
Bignum
Bignum
2
2
```
Số nguyên còn có thể được biểu diễn trong nhiều hệ cơ số khác nhau như hệ thập phân (10), hệ thập lục phân (16), hệ bát phân (8), và hệ nhị phân (2). Hệ thập phân là hệ cơ số mà chúng ta thường dùng nhất, hệ thập lục phân được biểu diễn với kí tự 0x ở đầu, hệ bát phân dùng kí tự 0 và hệ nhị phân dùng kí tự 0b.
notations.rb
```
puts 122
puts 0x7a
puts 0172
puts 0b1111010
```
Đoạn code trên in số 122 ở bốn hệ cơ số khác nhau.
Output
```
122
122
122
122
```
Bignum hay “số nguyên lớn” là các con số có số lượng chữ số rất lớn, thường là vài trăm chữ số, đọc số nguyên lớn cũng rất khó chịu, chẳng hạn như số 936758346345906394… do đó Ruby cho phép số nguyên lớn có thể có dấu gạch dưới “_” để chúng ta dễ đọc hơn, khi dịch thì trình thông dịch Ruby sẽ bỏ qua các dấu gạch dưới đó.
underscore.rb
```
p 23482345629
p 23_482_345_629
 
p 23482345629 == 23_482_345_629
```
Đoạn code trên sử dụng dấu gạch dưới cho số nguyên lớn.
```
23482345629
23482345629
true
```

# Số chấm động

Số chấm động tức là số thực, số thực thường được dùng để đo các giá trị liên tục như trọng lượng, tốc độ, chiều dài… Trong Ruby thì số thực được biểu diễn bởi lớp Float hoặc BigDecimal.
floating_point.rb
```
p 15.4
p 0.3455
p -343.4563
 
p 12.5.class
p -12.5.class
p (5.0 / 2).class
 
p 5.fdiv 2
p 12.to_f
```
Đoạn code trên thực hiện một số thao tác với số chấm động.
```
p 15.4
p 0.3455
p -343.4563
```
Chúng ta in 3 số chấm động, số chấm động có phần thập phân nằm phía sau dấu chấm.
```
p 12.5.class
p -12.5.class
p (5.0 / 2).class
```
Chúng ta in tên lớp biểu diễn số chấm động. Ngoài ra nếu chúng ta thực hiện tính toán một số nguyên với một số chấm động thì kết quả sẽ cho ra một số chấm động.
```
p 5.fdiv 2
p 12.to_f
```
Chúng ta tạo các số chấm động bằng phương thức fdiv và phương thức to_f. Phương thức fdiv chẳng qua là thực hiện phép chia nhưng trả về số chấm động mặc dù phép chia đó thực hiện trên 2 số nguyên, còn phương thức to_f sẽ chuyển đổi một số bất kì thành số thực.
Output
```
15.4
0.3455
-343.4563
Float
Float
Float
2.5
12.0
```
Mặc định thì phần thập phân chỉ hiển thị tối đa 16 chữ số nhưng chúng ta có thể định dạng kiểu hiển thị theo ý chúng ta với phương thức sprintf hoặc printf.
format_float.rb
```
p 1/3.0
p 1.fdiv 2
 
puts sprintf "%.4f" % (1/3.0)
puts sprintf "%.7f" % (5/3.0)
```
Đoạn code trên sẽ định dạng hiển thị số chấm động.
```
p 1/3.0
p 13.fdiv 4
p 1.fdiv 2
```
Phương thức p sẽ in các số chấm động một cách mặc định.
```
puts sprintf "%.4f" % (1/3.0)
puts sprintf "%.7f" % (5/3.0)
```
Chúng ta định dạng lại số chấm động bằng phương thức sprintf, phương thức này nhận vào một chuỗi định dạng, chuỗi này có dạng %... ở đây %.4f tức là hiển thị 4 chữ số phía sau dấu chấm, tương tự %.7f là hiển thị 7 chữ số, kí tự f cho Ruby biết kiểu định dạng này được sử dụng với số chấm động.
Output
```
0.3333333333333333
3.25
0.5
0.3333
1.6666667
```
