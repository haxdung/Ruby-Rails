# Ruby – Kiểu dữ liệu – Phần 2
Trong phần này chúng ta tiếp tục tìm hiểu về các kiểu dữ liệu của Ruby.

# Số hữu tỉ – Rational

Số hữu tỉ là số có thể biểu diễn dưới dạng phân số. Sử dụng số hữu tỉ sẽ giúp tránh các lỗi về làm tròn số vì chúng ta có thể biểu diễn chúng dưới dạng phân số. Ruby có lớp Rational hỗ trợ làm việc với số hữu tỉ. Một số đối tượng trong Ruby có phương thức to_r để chuyển một số thành số hữu tỉ.
rational_number.rb
```
puts 5.to_r
puts "43".to_r
puts 1.5.to_r
 
p Rational 0
p Rational 2/5.0
p Rational 1.5
```
Trong đoạn code trên chúng ta thực hiện một số thao tác với số hữu tỉ.
```
puts 5.to_r
```
Chúng ta có thể chuyển số nguyên 5 sang 5/1 bằng phương thức to_r.
```
p Rational 1.5
```
Hoặc chúng ta có thể tạo ra từ lớp Rational.
Output
```
5/1
43/1
3/2
(0/1)
(3602879701896397/9007199254740992)
(3/2)
```

# Đối tượng nil

Trong C++, Java… có đối tượng NULL thì trong Ruby chúng được gọi là nil. Đây là một đối tượng mô tả giá trị “không có”, ý nói một biến không có giá trị gì cả. nil là một đối tượng tĩnh, tức là trong Ruby chỉ có một đối tượng nil duy nhất giống như đối tượng true hay false vậy, nil được tạo ra từ lớp NilClass.
nil_object.rb
```
puts nil
p nil
 
p $val
 
p $val1 == $val2
```
Đoạn code trên thực hiện một số thao tác với nil.
```
puts nil
p nil
```
Phương thức puts sẽ in chuỗi rỗng của đối tượng nil, trong khi phương thức p lại in chuỗi "nil" ra màn hình.
```
p $val
```
Nếu chúng ta in một biến chưa có giá trị thì Ruby sẽ hiển thị là nil.
```
p $val1 == $val2
```
Dòng code trên sẽ trả về true vì đối tượng nil là một đối tượng tĩnh và nó chỉ có 1.
Output
```
nil
nil
true
```

# Kiểu chuỗi – String

Một string là một dãy các kí tự liên tiếp nhau. Trong Ruby chúng là các đối tượng thuộc lớp String. Các chuỗi string được bọc trong cặp dấu nháy đơn hoặc nháy kép.

String là một kiểu dữ liệu quan trọng, trong phần sau chúng ta sẽ tìm hiểu kĩ hơn về kiểu dữ liệu này.
string_example.rb
```
p "Hello"
p 'Ruby'
 
p "Ruby".size
p "Ruby".upcase
 
p 2.to_s
```
Trong đoạn code trên chúng ta in một số string và các tính chất của chúng ra màn hình.
```
p "Hello"
p 'Ruby'
```
String có thể được bọc trong cặp dấu nháy đơn hoặc nháy kép.
```
p "Ruby".size
p "Ruby".upcase
```
Ở 2 dòng trên chúng ta gọi đến phương thức size và phương thức upcase, phương thức size trả về độ lớn của string còn phương thức upcase chuyển một string thành dạng chữ in hoa.
```
p 2.to_s
```
Trong dòng trên phương thức to_s chuyển một số thành một string.
Output
```
"Hello"
"Ruby"
4
"RUBY"
"2"
```

# Mảng và bảng băm

Mảng và bảng băm lưu dữ liệu theo dạng tập hợp, tức là chúng không lưu từng giá trị cụ thể mà lưu một nhóm các phần tử có giá trị khác nhau.

Mảng lưu các phần tử theo một thứ tự trong khi bảng băm lưu phần tử theo các cặp khóa-giá trị. Chúng ta sẽ tìm hiểu thêm về 2 kiểu dữ liệu này trong các bài sau.
array_hash.rb
```
nums = [1, 2, 3, 4]
 
puts "There are #{nums.size} items in the array"
 
nums.each do |num|
    puts num
end
 
 
domains = { :de => "Germany", :sk => "Slovakia",
            :us => "United States", :no => "Norway" }
 
puts domains.keys
puts domains.values
```
Đoạn code trên ví dụ về mảng và bảng băm trong Ruby.
```
nums = [1, 2, 3, 4]
 
puts "There are #{nums.size} items in the array"
 
nums.each do |num|
    puts num
end
```
Trong đoạn code trên, dòng đầu tiên tạo một mảng có 4 phần tử. Dòng thứ hai sẽ in số lượng phần tử trong mảng ra màn hình. Các dòng sau duyệt qua mảng để lấy từng phần tử của mảng và in ra màn hình.
```
domains = { :de => "Germany", :sk => "Slovakia",
            :us => "United States", :no => "Norway" }
 
puts domains.keys
puts domains.values
```
Ở đây chúng ta tạo một đối tượng bảng băm và in danh sách khóa và giá trị ra màn hình.
Output
```
There are 4 items in the array
1
2
3
4
de
sk
us
no
Germany
Slovakia
United States
Norway
```
# Chuyển đổi kiểu dữ liệu

Ruby có các phương thức hỗ trợ chuyển đổi kiểu dữ liệu như to_i, to_s hay to_f. Ngoài trong module Kernel còn có các phương thức như Integer, String hoặc Float cũng làm công việc tương tự.
kernel_conversion.rb
```
p Array(1..6)
p Complex 6
p Float 12
p Integer "34"
p Rational 6
p String 22
```
Đoạn code trên chuyển đổi kiểu dữ liệu bằng các phương thức của module Kernel.
Output
```
[1, 2, 3, 4, 5, 6]
(6+0i)
12.0
34
(6/1)
"22"
```
Đoạn code dưới đây chuyển đổi đối tượng sang kiểu số nguyên và số chấm động.
number_conversion.rb
```
p "12".to_i
p 12.5.to_i
p nil.to_i
 
p 12.to_f
p "11".to_f
p nil.to_f
```
Một số đối tượng trong Ruby chứa phương thức to_i và to_f giúp chuyển đổi sang kiểu số nguyên và số chấm động tương ứng.
Output
```
12
12
0
12.0
11.0
0.0
```
Chúng ta có thể chuyển một string sang khá nhiều kiểu dữ liệu khác nhau:
string_conversion.rb
```
p "12".to_i
p "13".to_f
p "12".to_r
p "13".to_c
 
p "Jane".to_sym
 
v = "Ruby Python Tcl PHP Perl".split
p v.class
```
Trong đoạn code trên chúng ta chuyển string sang số nguyên, số thực, số hữu tỉ, số phức, mảng và thậm chí là thành một symbol.
```
v = "Ruby Python Tcl PHP Perl".split
p v.class
```
Phương thức split sẽ tách từng kí tự trong string và lưu trong một mảng.
Output
```
12
13.0
(12/1)
(13+0i)
:Jane
Array
```
