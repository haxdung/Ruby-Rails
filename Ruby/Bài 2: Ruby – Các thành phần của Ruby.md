# Ruby – Các thành phần của Ruby

Một ngôn ngữ lập trình bao gồm nhiều thành phần cấu thành nên nó. Trong phần này chúng ta sẽ tìm hiểu các thành phần cấu tạo nên ngôn ngữ lập trình Ruby.

# Bình luận – Comment

Các đoạn comment được dùng để ghi chú mã nguồn. Cú pháp comment của Ruby có 2 loại là comment cho một dòng và comment cho nhiều dòng. Comment trên một dòng được bắt đầu bởi dấu **#**, comment trên nhiều dòng được bọc bởi cặp kí hiệu **=begin** và **=end**.
comments.rb

```
=begin
  comments.rb
  Pho Code
=end
 
puts "Comments example"
```

Các dòng comment sẽ không được dịch bởi trình thông dịch.

```
=begin
  comments.rb
  Pho Code
=end
```

# Biến – Variable

Biến chỉ là một cái tên, đại diện cho một thứ gì đó có công việc là lưu trữ một giá trị nào đó. Trong lập trình thì chúng ta nói là “gán giá trị cho biến”, giá trị ở đây có thể là một đoạn text, một con số hay một đối tượng nào đó.

Tên của các biến được đặt bằng các kí tự trong bảng chữ cái và dấu gạch dưới, nhưng không được bắt đầu bằng kí tự số, cũng không được bắt đầu bằng kí tự viết HOA, nếu dùng chữ HOA thì Ruby sẽ gọi đây là “hằng số”.

```
Value
value2
company_name
```

Value là một hằng số, value2 và company_name là biến.

```
12Val
exx$
first-name
```

Ở trên là các tên biến không hợp lệ.

Tên biến có thể được bắt đầu bởi 2 kí tự đặc biệt là @ và $, chúng ta sẽ tìm hiểu thêm sau.

Biến trong Ruby là có phân biệt HOA-thường, tức là price và pRice là 2 biến khác nhau.

# Hằng số – Constant

Trong các ngôn ngữ khác thì hằng số cũng là các biến thôi nhưng chỉ lưu một giá trị trong suốt chương trình, không thể thay đổi được. Nhưng không giống với các ngôn ngữ khác, giá trị của các hằng số trong Ruby là có thể thay đổi được, khi chúng ta thay đổi giá trị hằng thì Ruby không báo lỗi mà chỉ đưa ra mấy dòng cảnh báo.

Tên hằng số được bắt đầu bởi một kí tự viết HOA, thường thì khi đặt tên hằng chúng ta luôn viết hoa toàn bộ các kí tự trong tên.
constants.rb

```
Name = "Robert"
AGE = 23
 
Name = "Juliet"
```

Trong ví dụ trên chúng ta định nghĩa hằng Name và AGE, sau đó thay đổi giá trị của Name và Ruby sẽ báo lỗi tương tự như sau.
Output

```
C:\Project\Ruby>irb constants.rb
constants.rb:4: warning: already initialized constant Name
```

# Giá trị – Literal

Giá trị là các kí tự mô tả một giá trị của một kiểu dữ liệu nào đó, có thể là một con số, một đoạn text… dùng để gán cho các biến. Chúng ta sẽ tìm hiểu về kiểu dữ liệu sau.

```
age = 29
nationality = "Hungarian"
```

Trong ví dụ trên thì 29 và “Hungarian” là giá trị, age và nationality là biến.
literals.rb

```
require 'date'
 
sng = true
name = "James"
job = nil
weight = 68.5
born = Date.parse("November 12, 1986")
 
puts "His name is #{name}"
 
if sng == true
    puts "He is single"
else
    puts "He is in a relationship"
end
 
puts "His job is #{job}"
puts "He weighs #{weight} kilograms"
puts "He was born in #{born}"
```

Trong đoạn code trên thì chúng ta có các giá trị có kiểu dữ liệu boolean, kiểu string, kiểu float, kiểu nil – có thể hiểu là kiểu rỗng, kiểu Date.
Output

```
His name is James
He is single
His job is 
He weighs 68.5 kilograms
He was born in 1986-11-12
```

# Khối lệnh – Block

Khối lệnh là cách để chúng ta gộp nhóm các lênh lại với nhau, bạn sẽ hiểu về khối lệnh nhiều hơn khi thực hành. Khối lệnh trong Ruby được bắt đầu và kết thúc bởi cặp dấu **{}** hoặc cặp từ khóa **do-end**.

```
puts [2, -1, -4, 0].delete_if { |x| x < 0 }
     
[1, 2, 3].each do |e|
    puts e
end
```

Trong ví dụ trên chúng ta sử dụng cả 2 loại khối lệnh.

Ngoài các câu lệnh tính toán bình thường thì trong lập trình còn có các câu lệnh điều khiển, ví dụ như câu lệnh **if**, đây là câu lệnh điều kiện, theo sau **if** là một biểu thức rồi tới một khối lệnh nằm trong cặp từ khóa **then-end**. Chúng ta sẽ tìm hiểu thêm về các câu lệnh điều kiện sau.

```
if true then
    puts "Ruby language"
    puts "Ruby script"
end
```

# Sigil

Sigil là các kí tự $ và @ dùng để khai báo phạm vi hoạt động của biến. Trong đó **$** cho biết biến đó là một biến toàn cục, **@** cho biết đó là biến instance, **@@** là biến class. Chúng ta sẽ tìm hiểu thêm trong bài lập trình hướng đối tượng.

```
$car_name = "Peugeot"
@sea_name = "Black sea"
@@species = "Cat"
```

Sigil luôn được đặt trước tên biến.

# Toán tử

Toán tử là các kí tự thực hiện các hành động nào đó trên một giá trị nào đó.

```
!    +    -    ~    *    **    /    %
<< >>    &    |    ^
==    ===    !=    <=>    >=    >
<    <=    =    %=    /=    -=
+=    *=    **=    ..    ...    not
and    or    ?:    &&    || 
```

Chúng ta sẽ tìm hiểu thêm về toán tử sau.

# Từ khóa

Từ khóa là các từ ưu tiên trong Ruby, thường dùng làm các câu lệnh thực hiện hành động nào đó, chẳng hạn như in giá trị ra màn hình, thực hiện các công việc lặp đi lặp lại hay thực hiện tính toán. Khi đặt tên biến chúng ta không được đặt tên trùng với từ khóa.

```
alias    and      BEGIN      begin    break    case
class    def      defined?   do       else     elsif
END      end      ensure     false    for      if
in       module   next       nil      not      or
redo     rescue   retry      return   self     super
then     true     undef      unless   until    when
while    yield
```

Ở trên là danh sách các từ khóa có trong Ruby.
