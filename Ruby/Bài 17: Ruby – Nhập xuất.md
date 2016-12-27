# Ruby – Nhập xuất

Trong phần này chúng ta sẽ tìm hiểu về hệ thống nhập xuất trong Ruby. Khi chạy một chương trình thì chương trình có thể nhận các dòng dữ liệu đi vào, có thể là từ bàn phím, file hoặc từ chính một chương trình khác. Tương tự, chương trình cũng có thể xuất các dòng dữ liệu đi ra ngoài, thường là sẽ đi đến màn hình, đi vào một file hoặc đi vào một chương trình khác.

# Xuất dữ liệu ra

Xuyên suốt series này chúng ta đã thực hiện việc xuất dữ liệu rất nhiều lần bằng các phương thức có trong Ruby. Các phương thức này tồn tại trong **module Kernel**.

Ví dụ 1:
output1.rb
```
print "Apple "
print "Apple\n"
 
puts "Orange"
puts "Orange"
```
Hai phương thức **print** và **puts** là 2 phương thức xuất dữ liệu là các chuỗi text ra màn hình, trong đó phương thức **puts** sẽ in chuỗi rồi xuống dòng còn phương thức **print** thì không.
```
print "Apple\n"
```
Nếu muốn phương thức **print** có xuống dòng thì chúng ta thêm kí tự **\n** vào.
Output
```
Apple Apple
Orange
Orange
```
Ví dụ 2:
output2.rb
```
p "Lemon"
p "Lemon"
 
printf "There are %d apples\n", 3

putc 'K'
putc 0xA
```
Chúng ta tiếp tục tìm hiểu một số phương thức in dữ liệu khác.
```
p "Lemon"
```
Phương thức **p** sẽ gọi phương thức **inspect** của đối tượng. Phương thức **inspect** là một phương thức của lớp **Object**, thường thì phương thức này sẽ in ra tên lớp cùng các thông tin liên quan.
```
printf "There are %d apples\n", 3
```
Phương thức **printf** in chuỗi và cho phép truyền tham số vào trong chuỗi.
```
putc 'K'
putc 0xA
```
Phương thức putc chỉ đơn giản là in một kí tự ra màn hình. Giá trị 0xA là giá trị của kí tự xuống dòng trong bảng mã **ASCII**. Tức thay vì ở đây chúng ta dùng **putc** **"\n"** thì chúng ta có thể in 0xA thay thế.
Output
```
"Lemon"
"Lemon"
There are 3 apples
K
```

# Đọc dữ liệu vào

Ví dụ 1:
input1.rb
```
print "Enter your name: "
name = gets
puts "Hello #{name}"
```
Để đọc dữ liệu vào thì chúng ta dùng phương thức **gets**.
```
name = gets
```
Phương thức **gets** sẽ nhận một chuỗi nhập vào từ bàn phím. Khi chạy chương trình, đến đoạn gọi phương thức **gets** thì chương trình sẽ dừng lại chờ chúng ta gõ một chuỗi nào đó rồi bấm **ENTER** thì chuỗi đó sẽ được truyền vào biến name.
Output
```
Enter your name: Hoang
Hello Hoang
```
Ví dụ 2:
input2.rb
```
print "Enter a string: "
str = gets
 
puts "String size: #{str.size}"
```
Phương thức **size** sẽ trả về số lượng kí tự có trong chuỗi
Output
```
Enter a string: abc
String size: 4
```
Kết quả in ra là 4 trong khi chuỗi của chúng ta nhập vào chỉ là "abc" tức là chỉ có 3 chữ cái thôi, lý do là vì phương thức **gets** tính luôn cả kí tự **ENTER** mà chúng ta gõ phía sau nữa nên thành 4.

Để loại bỏ kí tự **ENTER** này ra khỏi chuỗithì chúng ta dùng phương thức **chomp**.
input2.rb
```
print "Enter a string: "
str = gets.chomp
 
puts "String size: #{str.size}"
```
Như thế phương thức **size** sẽ cho ra đúng số lượng kí tự đã được nhập vào.
Output
```
Enter a string: abc
String size: 3
```

# File

Tất cả các công việc nhập dữ liệu vào và xuất dữ liệu ra đều được quản lý bởi một lớp có tên là **IO**, ngoài ra Ruby còn có các lớp con khác kế thừa từ lớp **IO** nhằm mục đích thực hiện việc nhập xuất trên các dòng dữ liệu khác nhau, trong đó có lớp **File** dùng để nhập xuất file.

Ví dụ 1:
file_io1.rb
```
f = File.open('C:\\output.txt', 'w')
f.puts "The Ruby tutorial"
f.close
```
Trong ví dụ này chúng ta thực hiện ghi dữ liệu lên file.
```
f = File.open('C:\\output.txt', 'w')
```
Để ghi dữ liệu vào file thì trước tiên chúng ta phải mở file đó đã bằng phương thức **File.open()**, phương thức này nhận vào tham số là đường dẫn đến file và chế độ mở, ở đây tên file là output.txt và chế độ mở là **w** (write) tức là mở file để ghi.
```
f.puts "The Ruby tutorial"
```
Phương thức **open** sẽ trả về một đối tượng **stream**, nói cho đơn giản thì bạn cứ hình dung **stream** chính là những thứ như **Kernel** vậy, nếu bạn đã từng làm việc với C++ thì **stream** ở đây giống như đối tượng **std::cout** ấy. Và ở đây chúng ta có thể dùng đối tượng **stream** đó để ghi dữ liệu lên file bằng phương thức **puts**. 
```
f.close
```
Sau khi đã làm việc với file xong thì chúng ta đóng file lại bằng phương thức **close**.

Ví dụ 2:
file_io2.rb
```
File.open('C:\\output.txt', 'w') do |f|
    
    f.puts "Ruby"
    f.write "Java\n"
    f << "Python\n"
     
end
```
Nếu chúng ta mở file trong khối lệnh **File.open()...end** thì sau khi kết thúc chúng ta không cần phải đóng file nữa mà Ruby sẽ tự đóng cho chúng ta.
```
f.puts "Ruby"
f.write "Java\n"
f << "Python\n"
```
Ngoài ra ở đây chúng ta dùng thêm phương thức **write** và toán tử **<<** để in chuỗi ra màn hình.

Ví dụ 3:
file_io3.rb
```
puts File.exists? 'C:\\tempfile'
 
f = File.new 'C:\\tempfile', 'w'
puts File.mtime 'C:\\tempfile'
puts f.size
 
File.rename 'C:\\tempfile', 'C:\\tempfile2'
 
f.close
```
Lớp **File** ngoài việc hỗ trợ nhập xuất còn có một số phương thức khác.
```
puts File.exists? 'C:\\tempfile'
```
Phương thức **exists?** kiểm tra xem một file có tồn tại hay không.
```
f = File.new 'C:\\tempfile', 'w'
```
Phương thức **new** sẽ tạo một file mới trên đĩa cứng.
```
puts File.mtime 'C:\\tempfile'
```
Phương thức **mtime** lấy thời gian chỉnh sửa file lần cuối cùng.
```
puts f.size
```
Phương thức **size** trả về kích thước của file.
```
File.rename 'C:\\tempfile', 'C:\\tempfile2'
```
Phương thức **rename** sẽ đổi tên file.
Output
```
false
2011-11-05 16:19:36 +0100
0
```
Ví dụ 4:
file_io4.rb
```
f = File.open("C:\\input.txt")
 
while line = f.gets do
    puts line
end
 
f.close
```
Trong ví dụ này chúng ta sẽ đọc một file.
```
f = File.open("C:\\input")
```
Để đọc một file thì trước tiên chúng ta cũng phải mở file đó đã, ở đây chúng ta không đưa vào tham số chế độ mở là vì mặc định Ruby sẽ mở file theo chế độ đọc.
```
while line = f.gets do
    puts line
end
```
Phương thức **gets** sẽ đọc từng dòng dữ liệu trong file, chúng ta lưu dữ liệu đó trong biến line, vòng lặp **while** có tác dụng kiểm tra xem biến line có rỗng hay không, tức là trong khi file vẫn còn dữ liệu để đọc thì chúng ta thực hiện đoạn code bên trong vòng lặp.
Output
```
Ruby
Java
Python
```
Ngoài phương thức **gets** có chức năng đọc từng dòng thì còn có phương thức **readlines** sẽ đọc tất cả các dòng trong file và lưu vào một mảng. Cũng vì thế nên bạn **lưu ý đối với các file có kích thước lớn**.
```
file = 'C:\\input'
 
File.readlines(file).each do |line|
    puts line
end
```
Output
```
Ruby
Java
Python
```

# Thư mục

Ruby có lớp **Dir** hỗ trợ làm việc với thư mục.
directory.rb
```
Dir.mkdir "tmp"
puts Dir.exists? "tmp"
 
puts Dir.pwd
Dir.chdir "tmp"
puts Dir.pwd
 
Dir.chdir '..'
puts Dir.pwd
Dir.rmdir "tmp"
puts Dir.exists? "tmp"
```
Trong ví dụ trên chúng ta làm việc với 4 phương thức của lớp **Dir**.
```
Dir.mkdir "tmp"
```
Phương thức **mkdir** sẽ tạo một thư mục mới.
```
puts Dir.exists? "tmp"
```
Phương thức **exists?** kiểm tra xem một thư mục có tồn tại hay không.
```
puts Dir.pwd
```
Phương thức **pwd** in ra đường dẫn đến thư mục hiện tại. Đây là thư mục chứa file code Ruby mà chúng ta đang viết.
```
Dir.chdir '..'
```
Phương thức **chdir** thay đổi thư mục hiện tại thành thư mục khác. Ở đây dấu **".."** tức là lùi về thư mục cha.
```
Dir.rmdir "tmp"
puts Dir.exists? "tmp"
```

Phương thức **rmdir** sẽ xóa một thư mục.
Output
```
true
C:/Program Files (x86)/Notepad++
C:/Program Files (x86)/Notepad++/tmp
C:/Program Files (x86)/Notepad++
false
```

# Chuyển hướng dòng nhập xuất

Như bình thường chúng ta dùng phương thức **puts, print...** để in dữ liệu lên màn hình. Trong các bài trước chúng ta đã biết phương thức puts là phương thức của **module Kernel**, tức là gọi **Kernel.puts** "Ruby" sẽ tương đương với puts "Ruby". Ngoài ra Ruby còn có một số biến toàn cục tham chiếu tới các module đó nữa, biến $stdout là một ví dụ, đây là biến tham chiếu tới **module Kernel**, tức là bây giờ chúng ta có 3 cách dùng phương thức **puts** khác nhau là **Kernel.puts** “”, **$stdout.puts** "" hoặc **puts** "".

Chính vì biến $stdout tham chiếu tới **module Kernel** nên phương thức **puts** gọi từ biến này sẽ xuất dữ liệu lên màn hình nhưng chúng ta cũng có thể chuyển hướng để biến này xuất dữ liệu ra nơi khác.
```
$stdout = File.open "C:\\output.log", "a"
 
puts "Ruby"
puts "Java"
 
$stdout.close
$stdout = STDOUT
 
puts "Python"
```
Trong ví dụ trên chúng ta chuyển hướng dòng dữ liệu xuất ra từ màn hình sang file output.log.
```
$stdout = File.open "C:\\output.log", "a"
```
Như chúng ta đã biết, phương thức **File.open** sẽ trả về một đối tượng **stream**, chúng ta gán **stream** đó vào biến $stdout.
```
puts "Ruby"
puts "Java"
```
Khi chúng ta gọi phương thức **puts**, dữ liệu xuất ra sẽ được tự động ghi vào file thay vì ghi lên màn hình như trước.
```
$stdout = STDOUT
 
puts "Python"
```
Nếu chúng ta chuyển hướng lại vào hằng số **STDOUT** thì dòng dữ liệu xuất ra từ các phương thức **puts, print...** sẽ lại đi vào màn hình chứ không đi vào file nữa.
