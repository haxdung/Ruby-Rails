# Ruby – Biểu thức
Biểu thức bao gồm toán tử và toán hạng. Toán tử là một kí tự đặc biệt thực hiện các phép tính toán trên các toán hạng và trả về một giá trị nào đó. Hầu hết các toán tử trong lập trình đều bắt nguồn từ toán học. Các toán tử khác nhau có các mức độ ưu tiên khác nhau. Toán hạng là các tham số đầu vào cho toán tử, trong lập trình thì toán hạng chính là các biến hoặc các giá trị.

Đây là bảng danh sách các toán tử của Ruby:
Tên 	Kí hiệu
Lấy thuộc tính, phương thức 	:: .
Thao tác mảng 	[ ] [ ]=
Lấy lũy thừa 	**
Toán tử phủ định, đảo bit, tăng, giảm 	! ~ + -
Toán tử nhân, chia, chia lấy phần dư 	* / %
Toán tử cộng, trừ 	+ -
Toán tử dịch bit 	<< >>
Toán tử thao tác bit AND 	&
Toán tử thao tác bit OR 	^ |
Toán tử so sánh hơn kém 	> >= < <=
Toán tử so sánh bằng 	<=> == === != =~ !~
Toán tử logic AND 	&&
Toán tử logic OR 	||
Toán tử tạo phạm vi 	.. ...
Toán tử điều kiện 	?:
Toán tử gán 	= += -= *= **= /= %= &= |= ^= <<= >>= ||= &&=
Phủ định 	not
Toán tử logic OR, AND 	or and

Các toán tử trong cùng một dòng có độ ưu tiên như nhau. Các toán tử ở các hàng trên có độ ưu tiên cao hơn các hàng dưới. Các toán tử có thể làm việc với một, hai hoặc ba toán hạng. Tùy vào từng trường hợp mà Ruby sẽ chọn toán tử nào để dùng vì có một số toán tử có kí hiệu giống nhau nhưng có ý nghĩa khác nhau.
Dấu của số

Chúng ta có 2 toán tử thay đổi dấu của số là + và -. Ví dụ:
1
2
	
puts +2
puts -2

Dấu cộng chỉ định số đó là số nguyên dương, dấu trừ là số nguyên âm, nhưng cũng giống như trong toán hocj, dấu + có thể bỏ.
sign1.rb
1
2
3
4
5
	
a = 1
 
puts a
puts -(a)
puts -(-(a))

Cũng giống như toán học, 2 dấu trừ sẽ chuyển thành dấu cộng.
Output
1
2
3
	
1
-1
1
Toán tử gán

Toán tử gán sẽ gán giá trị cho biến, như chúng ta đã biết biến có nhiệm vụ lưu trữ giá trị. Toán hạng nằm phía bên phải sẽ được gán cho toán hạng nằm bên trái.
1
2
	
x = 1
puts x 

Chúng ta gán biến x có giá trị 1.
1
2
	
x = x + 1
puts x # prints 2

Trong lập trình toán hạng cũng có thể là một phép toán khác, trong ví dụ trên biến x được gán giá trị là x + 1.
1
	
1 = x; # Error

Chúng ta không thể gán một biến vào một giá trị, như thế là không hợp lệ, dòng code trên sẽ báo lỗi.
Toán tử lấy thuộc tính, phương thức

Đây là các toán tử có mức độ ưu tiên cao nhất, tức là trong một biểu thức thì chúng sẽ được thực hiện đầu tiên.

Toán tử :: có ý nghĩa là lấy hằng số, module hoặc một lớp được định nghĩa bên trong một lớp khác:
member_access_operators1.rb
1
2
3
4
5
6
7
8
9
10
	
class MyMath
    Pi = 3.1415926535   
end
 
module People
    Name = "People"
end
 
puts MyMath::Pi
puts People::Name

Trong đoạn code trên chúng ta có một lớp và một module, để lấy hằng số từ một lớp (hoặc module) thì chúng ta ghi tên lớp, sau đó là dấu :: rồi tên hằng, như thế các hằng số có tên giống nhau nhưng được đặt trong các lớp khác nhau sẽ không bị xung đột.
Output
1
2
	
3.1415926535
People

Toán tử . truy xuất thuộc tính và phương thức của một đối tượng:
member_access_operators2.rb
1
2
3
4
5
6
7
8
9
10
11
12
13
14
15
	
class Person
     
   def initialize name, age
       @name = name
       @age = age       
   end
    
   def info
       "#{@name} is #{@age} years old"
   end
     
end
 
p = Person.new "Jane", 17
puts p.info

Trong ví dụ trên chúng ta định nghĩa lớp Person có 2 phương thức do chúng ta định nghĩa. Chúng ta sử dụng toán tử . để truy xuất 2 phương thức này.
1
2
	
p = Person.new "Jane", 17
puts p.info

Chúng ta gọi phương thức new và phương thức info, phương thức new sẽ gọi đến phương thức initialize mà chúng ta đã viết, phương thức info sẽ trả về một chuỗi.
Output
1
	
Jane is 17 years old
Toán tử toán học

Bao gồm các toán tử sau đây.
Kí hiệu 	Tên
+ 	Cộng
- 	Trừ
* 	Nhân
/ 	Chia
% 	Chia lấy phần dư
** 	Lũy thừa

Ví dụ:
math_operators1.rb
1
2
3
4
5
6
7
8
9
10
	
a = 1
b = 2
c = 3
 
puts a + b + c
puts c - a
puts a * b
puts c / 3
puts c % a
puts c ** a

Các toán tử toán học giống y hệt như các phép toán trong toán học vậy.
1
	
puts c % a

Toán tử % chia hai số rồi lấy phần dư, ví dụ 9 chia 4 được 2 dư 1 thì toán tử này trả về 1.
Output
1
2
3
4
5
6
	
6
2
2
1
0
3

Ví dụ 2:
math_operators2.rb
1
2
3
4
5
	
puts 5 / 2
 
puts 5 / 2.0
puts 5.0 / 2
puts 5.to_f / 2

Trong ví dụ này chúng ta thực hiện phép chia trên số nguyên và số thực.
1
	
puts 5 / 2

Khi chúng ta thực hiện phép chia 2 số nguyên thì kết quả trả về là số nguyên.
1
2
3
	
puts 5 / 2.0
puts 5.0 / 2
puts 5.to_f / 2

Nếu một trong 2 toán hạng là số thực thì kết quả trả về là một số thực, ngoài ra chúng ta có thể dùng phương thức to_f để chuyển một số nguyên thành một số thực.
Output
1
2
3
4
	
2
2.5
2.5
2.5

Ví dụ 3:
math_operators3.rb
1
2
3
4
	
puts 5.div 2.0
puts 5.fdiv 2
puts 5.quo 2
puts 5.0.quo 2.0

Ngoài toán tử / thì chúng ta còn có các phương thức div, fdiv và quo cũng thực hiện phép chia.
1
	
puts 5.div 2.0

Phương thức div thực hiện phép chia số nguyên và trả về số nguyên cho dù toán hạng có là số thực.
1
	
puts 5.fdiv 2

Phương thức fdiv thì lại trả về số thực mặc dù toán hạng có là số nguyên.
1
2
	
puts 5.quo 2
puts 5.0.quo 2.0

Phương thức quo sẽ thực hiện phép chia và trả về số hữu tỉ dưới dạng phân số nếu các toán hạng là số nguyên, nếu một trong hai toán hạng là số thực thì trả về số thực.
Output
1
2
3
4
	
2
2.5
5/2
2.5
Toán tử logic

Ruby có các toán tử logic sau:
Kí hiệu 	Tên
&& 	AND
|| 	OR
! 	negation

Toán tử logic sẽ trả kết quả về là một đối tượng boolean, tức là chỉ có true hoặc false. Ngoài 3 toán tử &&, || và ! thì còn có 3 toán tử có tác dụng tương tự nhưng độ ưu tiên thấp hơn là and, or và not.

Ngoài ra các toán tử so sánh hay quan hệ cũng trả về một giá trị boolean:
1
2
3
4
5
6
7
8
9
	
x = 1
y = 2
 
puts x == y
puts y > x
 
if y > x then
    puts "y is greater than x"
end

Trong đoạn code trên chúng ta sử dụng toán tử so sánh == và toán tử quan hệ >.
1
2
	
puts x == y
puts y > x

Cả 2 dòng trên sẽ trả về kết quả là một giá trị boolean.
1
2
3
	
if y > x then
    puts "y is greater than x"
end

Các toán tử quan hệ thường được dùng trong câu lệnh điều kiện if, trong đoạn code trên phương thức puts sẽ được thực thi nếu biểu thức trong if trả về true.

Ví dụ 1:
logic_operators1.rb
1
2
3
4
	
puts true && true
puts true && false
puts false && true
puts false && false

Toán tử && trả về true nếu cả 2 toán hạng đều có giá trị là true.
Output
1
2
3
4
	
true
false
false
false

Ví dụ 2:
logic_operators2.rb
1
2
3
4
	
puts true || true
puts true || false
puts false || true
puts false || false

Toán tử || trả về true nếu một trong 2 toán hạng là true, ngược lại trả về false.
Output
1
2
3
4
	
true
true
true
false

Ví dụ 3:
logic_operators3.rb
1
2
3
4
5
6
7
	
puts !0
puts !1
puts !true
puts !false
 
puts ! (4<3)
puts ! "Ruby".include?("a")

Toán tử ! sẽ đảo ngược giá trị true thành false và ngược lại.
Output
1
2
3
4
5
6
	
false
false
false
true
true
true

Khi Ruby thực hiện toán tử || và && thì các toán hạng sẽ lần lượt được đánh giá, nếu toán hạng đầu tiên đủ điều kiện để đưa ra kết quả thì dừng lại chứ không xem xét tới các toán hạng phía sau nữa. Ví dụ trong biểu thức true || false thì Ruby chỉ cần nhìn thấy toán hạng đầu tiên là true thì sẽ trả về true luôn chứ không xem xét toán hạng thứ hai là true hay false.
Toán tử so sánh

Đây là các toán tử so sánh lớn hơn, bé hơn:
Kí hiệu 	tên
< 	bé hơn
<= 	bé hơn hoặc bằng
> 	lớn hơn
>= 	lớn hơn hoặc bằng

Ví dụ:
1
2
	
p 1 < 2 p 2 > 3
p 3 >= 3

Trong đoạn code trên, phép toán 1 < 2 trả về true, phép toán 2 > 3 trả về false. Phép toán 3 >= 3 trả về true.
Toán tử thao tác bit

Con người chúng ta thường làm việc với hệ cơ số 10 vì mặc nhiên chúng ta có 10 ngón tay, 10 ngón chân nên rất dễ tính toán, máy tính thì lại không như vậy, máy tính chỉ hiểu được hệ cơ số 2 – tức hệ nhị phân. Bạn cần nắm rõ cách hoạt động của các phép toán thao tác trên bit trước khi đi vào tìm hiểu thêm vì ở đây mình sẽ chỉ giải thích sơ lược qua các ví dụ.

Trong Ruby có các toán tử thao tác bit sau:
Kí hiệu 	ý nghĩa
~ 	Đảo ngược bit
^ 	Phép XOR
& 	Phép AND
| 	Phép OR
<< 	Dịch trái 1 bit
>> 	Dịch phải 1 bit

Thường thì chúng ta cũng ít khi dùng các toán tử này.

Ví dụ:
1
2
3
4
5
6
7
8
9
10
11
12
13
14
15
	
puts ~ 7   # prints -8 
puts ~ -8  # prints 7
 
puts 6 & 3  # prints 2
puts 3 & 6  # prints 2
 
puts 6 ^ 3  # prints 5
puts 3 ^ 6  # prints 5
 
puts 6 | 3  # prints 7
puts 3 | 6  # prints 7
 
puts 6 << 1  # prints 12
puts 1 << 6 # prints 64 puts 6 >> 1  # prints 3
puts 1 >> 6  # prints 0

Phép đảo ngược bit ~ sẽ chuyển tất cả các bit từ 0 sang 1 và ngược lại. Trong ví dụ này, 7 trong hệ 10 là 0111 trong hệ 2,  đảo ngược lại sẽ là 1000, mặc định Ruby làm việc với số nguyên có dấu, mà bit đầu tiên là bit xác định có dấu hay không nên 1000 trong hệ 2 sẽ là -8 trong hệ 10.
1
2
	
puts ~ 7   # prints -8 
puts ~ -8  # prints 7

Toán tử & sẽ thực hiện phép AND 2 số, trong đó nếu có cả 2 bit đều là 1 thì kết quả là 1, ngược lại là 0. Trong ví dụ này 6 & 3 là 0110 & 0011 = 0010, tức là số 2 trong hệ 10.
1
2
	
puts 6 & 3  # prints 2
puts 3 & 6  # prints 2

Toán tử ^ thực hiện phép XOR, nếu 2 bit giống nhau thì kết quả là 0, khác nhau thì là 1. Trong ví dụ này 6 ^ 3 tương đương 0110 ^ 0011 = 0101 là 5 trong hệ 10.
1
2
	
puts 6 ^ 3  # prints 5
puts 3 ^ 6  # prints 5

Toán tử | thực hiện phép OR, nếu một trong 2 bit là 1 thì kết quả là 1, ngược lại nếu cả 2 bit là 0 thì kết quả là 0. Ở đây 6 | 3 tương đương 0110 | 0011 = 0111 là 7 trong hệ 10.
1
2
	
puts 6 | 3  # prints 7
puts 3 | 6  # prints 7

Toán tử << dịch 1 bit sang trái, toán tử >> dịch 1 bit sang phải, ví dụ 6 << 1 tức là dịch 0110 sang 1 bit, thành 1100 tức 12 trong hệ 10, nếu tiếp tục dịch 12 << 1 thì được 11000 tức là 24 trong hệ 10. Nghĩa là phép dịch bit trái sẽ nhân số đó lên 2 lần. Tương tự phép dịch bit phải chia số đó cho 2.
1
2
3
	
puts 6 << 1  # 12
puts 1 << 6 # 64 puts 6 >> 1  # 3
puts 1 >> 6  # 0
Toán tử hợp

Toán tử hợp ở đây nghĩa là gộp các toán tử với toán tử gán = để thực hiện tính toán và gán giá trị luôn.

Ví dụ:
1
2
3
4
5
6
7
8
9
10
11
12
	
a = 0
 
a = a + 1
a += 1
puts a
 
 
b = 0
 
b = b - 8
b -= 8
puts b

Toán tử += có nghĩa là cộng rồi gán, chẳng hạn a += 1 tức là a + 1 rồi gán vào biến a, phép toán này tương đương với a = a + 1.

Đây là các toán tử hợp có trong Ruby:
1
	
-=   *=  **=  /=   %=   &=   |=   <<= >>= 
Mức độ ưu tiên của các toán tử

Mức độ ưu tiên toán tử cho biết trong một biểu thức thì toán tử nào sẽ được thực hiện trước.
1
	
3 + 5 * 5  # Result: 28

Ví dụ như trong biểu thức gồm có phép nhân và phép cộng thì phép nhân được thực hiện trước và phép cộng được thực hiện sau.
1
	
(3 + 5) * 5  # Result: 40

Để tăng độ ưu tiên thì chúng ta bọc biểu thức trong cặp dấu ngoặc tròn (). Các biểu thức trong cặp dấu ngoặc tròn sẽ được thực thi trước.
1
	
9 / 3 * 3   # Result: 9

Các toán tử có độ ưu tiên bằng nhau sẽ được thực hiện từ trái sang phải, giống hoàn toàn với toán học.
Toán tử phạm vi

Ruby có 2 toán tử phạm vi, dùng để tạo các đối tượng thuộc dạng danh sách trong một phạm vi nào đó, thường là phạm vi số hoặc kí tự.
range_operators.rb
1
2
3
4
	
p (1..3).to_a
p (1...3).to_a
 
p ('a' .. 'l').to_a

Toán tử i..j tạo danh sách các phần tử từ i tới j, bao gồm cả j, toán tử i...j tạo danh sách các phần tử từ i tới j nhưng không bao gồm j, tức là từ i tới j-1.
1
	
p ('a' .. 'l').to_a

Chúng ta có thể đưa vào dãy số hoặc dãy kí tự. Phương thức to_a sẽ chuyển danh sách này về kiểu mảng.
Output
1
2
3
	
[1, 2, 3]
[1, 2]
["a", "b", "c", "d", "e", "f", "g", "h", "i", "j", "k", "l"]
Toán tử điều kiện

Toán tử này trả về một trong 2 biểu thức tùy thuộc vào giá trị biểu thức điều kiện mà chúng ta đề ra. Cú pháp:
1
	
biểu thức điều kiện ? biểu thức 1 : biểu thức 2

Có pháp trên có nghĩa là nếu biểu thức điều kiện là true thì thực hiện biểu thức 1, nếu false thì thực hiện biểu thức 2. Ví dụ:
conditional_operators.rb
1
2
3
4
5
6
7
8
9
	
age = 32
 
adult = age >= 18 ? true : false
 
if adult then
    puts "Adult"
else
    puts "Not adult"
end

Trong ví dụ trên chúng ta in ra các string khác nhau tùy vào giá trị của biến adult.
1
	
adult = age >= 18 ? true : false

Biến adult sẽ có giá trị là true nếu biến age lớn hơn 18, ngược lại adult là false.
Output
```
Adult
```
