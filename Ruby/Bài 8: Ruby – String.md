# Ruby – String
Trong phần này chúng ta sẽ tìm hiểu kỹ hơn về kiểu dữ liệu **String**.

**String** là một chuỗi các kí tự được bọc trong cặp dấu nháy đơn hoặc nháy kép.
quotes.rb
```
puts 'Python'
puts "Ruby"
```
Trong ví dụ trên chúng ta sử dụng cả 2 loại dấu nháy để tạo string.
Output
```
Python
Ruby
```
Nếu bạn muốn in ra cả ký tự dấu nháy thì có 2 cách:
quotes2.rb
```
puts "There are many stars"
puts "He said, \"Which one is your favourite?\""
 
puts 'There are many stars'
puts 'He said, "Which one is your favourite?"'
```
Cách thứ nhất là đặt trước dấu nháy ký tự **\** và Ruby sẽ in ra dấu nháy đó. Cách thứ 2 là trộn dấu nháy đơn với dấu nháy kép, chẳng hạn như chúng ta bọc string bằng cặp dấu nháy đơn và bên trong chúng ta cho in ra dấu nháy kép.
Output
```	
There are many stars.
He said, "Which one is your favourite?"
```

# Ký tự thoát

Ký tự thoát là các ký tự đặc biệt dùng để điều khiển string chứ không được in ra màn hình.
escape.rb
```	
puts "one\ntwo\nthree\nfour"
puts "bbb\raaa"
puts "Joan\b\b\bane"
puts "Towering\tinferno"
```
Kí tự **\n** có nghĩa là xuống dòng, bất kì kí tự nào nằm sau **\n** đều được xuống dòng. Kí tự **\r** đưa dấu nháy trên màn hình về vị trí đầu dòng.  Kí tự **\t** cách một đoạn dài bằng một dấu tab giống như khi chúng ta gõ nút tab, kí tự **\b** xóa một kí tự đứng trước nó.
Output
```	
one
two
three
four
aabbb
Jane
Towering      inferno
```
Nếu muốn in ra cả ký tự **\** thì chúng ta đưa vào là **\\**.
escape1.rb
```	
puts "Escape character \\"
```
Output
```	
Escape character \
```
Lấy từng phần tử của string

Chúng ta có thể lấy từng phần tử của string.
string_element.rb
```
msg = "Ruby language"
 
puts msg["Ruby"]
puts msg["Python"]
 
puts msg[0]
puts msg[-1]
 
puts msg[0, 3]
puts msg[0..9]
puts msg[0, msg.length]
```
Để có thể lấy các phần tử của string thì chúng ta sử dụng cặp dấu ngoặc vuông **[]** vừa đưa vào bên trong đó chỉ số, khoảng hoặc một string khác.
```	
puts msg["Ruby"]
```
Khi đưa vào một string bên trong cặp dấu **[]** thì Ruby sẽ tìm chuỗi đó trong chuỗi gốc, nếu tìm thấy thì in ra chuỗi, nếu không thì in ra chuỗi rỗng.
```	
puts msg[0]
```
Nếu đưa vào một con số nào thì chúng ta được kí tự tại vị trí đó, chuỗi trong Ruby được đánh số từ 0.
```
puts msg[-1]
```
Ruby cũng hỗ trợ chỉ số âm, đưa vào số âm thì sẽ được kí tự từ cuối string.
```	
puts msg[0, 3]
```
Khi đưa vào 2 chữ số cách nhau bởi dấu phẩy, ví dụ [i, n] thì chúng ta lấy được n kí tự từ vị trí i.
```
puts msg[0..9]
```
Chúng ta cũng có thể đưa vào một khoảng giá trị, [0..9] sẽ lấy về chuỗi kí tự từ vị trí 0 đến vị trí 9.
```
puts msg[0, msg.length]
```
Phương thức **length** trả về độ lớn của chuỗi nên dòng trên có nghĩa là lấy toàn bộ chuỗi.
Output
```
Ruby
 
R
e
Rub
Ruby langu
Ruby language
```

# Truyền biến vào string

Chúng ta có thể truyền giá trị của các biến khác vào string để hiển thị, biến được truyền vào có dạng **#{<tên biến>}**. Ví dụ:
interpolation.rb

```
#!/usr/bin/ruby
 
name = "Jane"
age = 17
```
puts "#{name} is #{age} years old"

Giá trị của biến name và age sẽ được hiển thị tương ứng.
Output
```
Jane is 17 years old
```
Chúng ta cũng có thể thực hiện các biểu thức với các biến được truyền vào:
interpolation2.rb
```
x = 5
y = 6
 
puts "#{x} x #{y} = #{x*y}"
```
Output
```
5 x 6 = 30
```
Nối chuỗi

Nối chuỗi tức là tạo một chuỗi từ các chuỗi con.
concat.rb
```
lang = "Ruby" + " programming" + " languge"
puts lang
 
lang = "Python" " programming" " language"
puts lang
 
lang = "Perl" << " programming" << " language"
puts lang
 
lang = "Java".concat(" programming").concat(" language")
puts lang
```
Có rất nhiều cách để nối một chuỗi. Để nối một chuỗi thì chúng ta có thể dùng toán tử cộng +, viết 2 chuỗi đứng liền nhau, dùng toán tử <<,  hoặc dùng phương thức **concat()**.
Output
```
Ruby programming languge
Python programming language
Perl programming language
Java programming language
```

# So sánh chuỗi

Ruby hỗ trợ một số toán tử và phương thức giúp so sánh chuỗi một cách dễ dàng.
string_comparison.rb
```
puts "12" == "12"
puts "aa" == "ab"
puts "Ruby".eql? "Jan"
```
Chúng ta có thể so sánh chuỗi bằng toán tử == hoặc phương thức **eql?**. Kết quả trả về True nếu 2 chuỗi giống nhau và ngược lại.
Output
```
true
false
false
```
Ngoài ra Ruby còn có toán tử <==> dùng để so sánh chuỗi, toán tử này không trả về **True** hay **False** mà trả về 1, 0, -1:
```
    1: chuỗi bên trái lớn hơn chuỗi bên phải
    -1: chuỗi bên trái bé hơn chuỗi bên phải
    0: hai chuỗi bằng nhau
```
Chuỗi a được gọi là bé hơn chuỗi b nếu kí tự tương ứng của chuỗi a có thứ tự cao hơn kí tự tương ứng bên chuỗi b trong bảng mã ASCII. Ví dụ, khi so sánh "a" <==> "b" thì kí tự a nằm trước kí tự b trong bảng mã ASCII nên a sẽ lớn hơn b. Nếu 2 kí tự bằng nhau thì Ruby sẽ tiếp tục so sánh kí tự tiếp theo của 2 chuỗi cho đến hết.
string_comparison2.rb
```
puts "a" <==> "b"
puts "b" <==> "a"
puts "a" <==> "a"
```
Output
```
-1
1
0
```
# Các phương thức trong String

String cũng là một đối tượng trong Ruby do đó các đối tượng string có các phương thức hữu ích mà chúng ta có thể sử dụng.

Ví dụ 1:
string_methods1.rb
```
word = "Methods"
 
puts "Size of #{word}: #{word.size}"
 
puts word.include? "tho"
puts word.include? "od"
 
puts
 
puts word.empty?
word.clear
puts word.empty?
```
Trong đoạn code trên chúng ta sử dụng 4 phương thức của đối tượng string.
```
puts "Size of #{word}: #{word.size}"
```
Phương thức **size** lấy số lượng kí tự có trong string.
```
puts word.include? "tho"
```
Đoạn code trên dùng phương thức **include?**, phương thức này cho biết chuỗi “tho” có nằm trong chuỗi “Methods” hay không.
```
puts word.empty?
word.clear
```
Phương thức **empty?** cho biết string có rỗng hay không, phương thức **clear** sẽ xóa toàn bộ string.
Output
```
Size of Methods: 7
true
true
 
false
true
```
Ví dụ 2:
string_methods2.rb
```
ruby = "Ruby"
 
puts ruby.upcase
puts ruby.downcase
puts ruby.capitalize
puts ruby.swapcase
```
Ruby có 4 phương thức để chuyển kí tự qua lại giữa chữ hoa với chữ thường. Phương thức **upcase** chuyển toàn bộ string thành in hoa. Phương thức **downcase** là chuyển thành chữ in thường. Phương thức **capitalize** viết hoa chữ cái đầu trong string, còn lại viết thường. Phương thức **swapcase** chuyển kí tự hoa thành thường và ngược lại.
Output
```
RUBY
ruby
Ruby
rUBY
```
Ví dụ 3:
string_methods3.rb
```
str1 = "ruby.com"
str2 = "python.com"
 
puts str1.start_with? "ruby"
puts str2.start_with? "ruby."
 
puts str1.end_with? ".com"
puts str2.end_with? ".com"
```
Trong ví dụ trên, phương thức **start_with?** cho biết chuỗi str1 và str2 có bắt đầu bằng chuỗi “ruby” hay không. Ngược lại, phương thức **end_with?** cho biết chuỗi có kết thúc bằng chuỗi “.com” hay không.
Output
```
true
false
true
true
```
Ví dụ 4:
string_method4.rb
```
msg = "Ruby\nPython"
 
puts msg
puts msg.inspect
```
Phương thức **inspect** sẽ in các ký tự thoát ra luôn chứ không dùng để điều khiển chuỗi nữa.
Output
```
Ruby
Python
"Ruby\nPython"
```

# Định dạng chuỗi

Định dạng chuỗi là hiển thị chuỗi theo nhiều cách khác nhau bằng cách chèn các chuỗi đặc tả. Chuỗi đặc tả có kí tự bắt đầu là kí tự % được đặt bên trong cặp dấu nháy đơn hoặc nháy kép cùng với chuỗi gốc.

Chuỗi đặc tả có dạng sau đây:
Cú pháp
```
%[cờ][độ lớn][độ chính xác]<tên đặc tả>
```
Trong đó cờ, độ lớn và độ chính xác là các tham số tùy chọn, không có cũng được. Tên đặc tả là kiểu hiển thị của dữ liệu. Chúng ta sẽ xem các ví dụ dưới đây.

Ví dụ 1:
string_format1.rb
```
puts "There are %d oranges in the basket." % 12
puts "There are %d oranges and %d apples in the basket." % [12, 10]
puts "Speed: %f km/h" % 62.1
puts "Name: %s" % "iPhone 5"
```
Khi chúng ta đặt %d bên trong chuỗi thì khi dịch Ruby sẽ hiểu là phải đưa một số nguyên vào vị trí đó thay thế cho chuỗi **%d**. Các tham số sẽ được đưa vào sau dấu **%** phía sau chuỗi. Ngoài ra chúng ta cũng có thể đưa vào nhiều tham số bằng cách đặt chúng trong cặp dấu **[]** và ngăn cách nhau bởi dấu phẩy.

Đặc tả **%d** hiển thị số nguyên, **%f** là số chấm động, **%s** là hiển thị một chuỗi.
Output
```
There are 12 oranges in the basket.
There are 12 oranges and 10 apples in the basket.
Speed: 62.100000 km/h
Name: iPhone 5
```
Ví dụ 2:
string_format2.rb
```
puts "%d" % 300
puts "%x" % 300
puts "%o" % 300
puts "%b" % 300
puts "%e" % (5/3.0)
```
Kiểu số nguyên có thể được hiển thị trên nhiều hệ cơ số khác nhau. Chẳng hạn **%d** là hệ 10, **%x** là hệ 16, **%o** là hệ 8, **%b** là hệ nhị phân (hệ 2), **%e** là hiển thị theo kiểu số mũ.
Output
```
300
12c
454
100101100
1.666667e+00
```
Tham số độ chính xác là một con số đứng giữa kí tự **%** và kí tự đặc tả, tham số này có nhiều ý nghĩa khác nhau với từng kiểu dữ liệu khác nhau.

Đối với số nguyên thì độ chính xác là số lượng chữ số được hiển thị, nếu giá trị không đủ thì Ruby sẽ tự động chèn thêm các chữ số 0 vào trước, mặc định thì tham số này là 1 tức là không chèn thêm vào.

Đối với số thực thì là số lượng chữ số được hiển thị nằm sau phần thập phân.

Đối với kiểu chuỗi thì độ chính xác có nghĩa là số lượng kí tự cần được hiển thị.

Ví dụ 3:
string_format3.rb
```
puts 'Height: %f %s' % [177.3, 'cm']
puts 'Height: %.1f %s' % [177.3, 'cm']
 
puts "%d" % 16
puts "%.5d" % 16
 
puts "%s" % "Ruby"
puts "%.5s" % "Python"
```
Trong ví dụ trên, **%.1f** tức là hiển thị 1 chữ số sau phần thập phân. Mặc định Ruby hiển thị 6 chữ số sau phần thập phân nên nếu không đủ thì Ruby sẽ tự động chèn thêm các số 0 vào trước.

Tương tự, mặc định Ruby hiển thị độ chính xác là 1 với số nguyên, nhưng nếu chúng ta thiết lập là **%.5d** thì Ruby sẽ tự chèn thêm các số 0 vào trước cho đủ 5 chữ số.

**%.5s** cũng giống 2 kiểu trên ở chỗ là sẽ chỉ cho phép hiển thị 5 chữ cái, nếu số lượng chữ cái quá nhiều thì các chữ cái sau cùng sẽ bị lược bỏ, nhưng nếu không đủ số lượng thì Ruby cũng chẳng chèn thêm kí tự nào vào.
Output
```
Height: 177.300000 cm
Height: 177.3 cm
16
00016
Ruby
Pytho
```
Ví dụ 4: Tham số độ lớn quy định số lượng kí tự tối thiểu cần được hiển thị ra.
string_format4.rb
```
puts "%d" % 1
puts "%d" % 12
puts "%d" % 123
puts "%d" % 1234
puts "%d" % 12345
 
puts "%10d" % 1
puts "%10d" % 12
puts "%10d" % 123
puts "%10d" % 1234
puts "%10d" % 12345
```
Tham số độ lớn nằm trước dấu chấm trong chuỗi đặc tả. Nếu dữ liệu không đủ số lượng kí tự thì Ruby sẽ tự động chèn thêm các khoảng trống vào phía trước chuỗi, ngoài ra chúng ta cũng có thể ghi số âm và Ruby sẽ đưa các kí tự khoảng trống vào phía sau chuỗi.
Output
```
1
12
123
1234
12345
         1
        12
       123
      1234
     12345
```
Tham số cờ quy định một số kiểu hiển thị khác mà chúng ta sẽ xem sau đây.

Ví dụ 5:
string_format5.rb
```
puts "%010d" % 1
puts "%010d" % 12
puts "%010d" % 123
puts "%010d" % 1234
puts "%010d" % 12345
 
puts "%-10d" % 1
puts "%-10d" % 12
puts "%-10d" % 123
puts "%-10d" % 1234
puts "%-10d" % 12345
```
Cờ **0** sẽ chèn thêm một số lượng số 0 vào trước số thay vì chèn khoảng trống. Cờ dấu trừ **“-”** sẽ canh lề trái các chữ số.
Output
```
0000000001
0000000012
0000000123
0000001234
0000012345
1
12
123
1234
12345
```
Ngoài ra còn có các cờ khác như dấu ** *, +, #, b, d, u, x…**.
