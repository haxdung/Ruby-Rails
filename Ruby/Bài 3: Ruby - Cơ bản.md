# Ruby – Cơ bản

Trong phần này chúng ta sẽ học cách làm việc với ngôn ngữ Ruby.

Ví dụ một đoạn code Ruby:
first.rb

```
puts "This is Ruby"
```

Đoạn code trên rất đơn giản, chỉ là in chuỗi “This is Ruby” ra màn hình console. Từ khóa puts nhận vào một tham số phía sau nó là một chuỗi text, chuỗi text được bọc trong cặp dấu nháy kép "".
Output

```
This is Ruby
``

Đọc dữ liệu vào từ terminal (trong Windows là Command Prompt – cmd):

```
print "What is your name? "
name = gets
puts "Hello #{name}"
```

Đoạn code trên sẽ nhận một chuỗi do chúng ta nhập vào từ bàn phím rồi in ra màn hình.

```
print "What is your name? "
```

Từ khóa print cũng có tác dụng in một chuỗi text lên màn hình nhưng không xuống dòng như từ khóa puts.

```
name = gets
```

Dòng code trên sẽ đọc một đoạn text từ người dùng và lưu vào biến name bằng cách sử dụng phương thức gets,

```
puts "Hello #{name}"
```

#{name} sẽ thay bằng giá trị của biến name, bằng cách đó chúng ta có thể đưa giá trị của biến vào trong chuỗi.
Output

```
What is your name? Hoang
Hello Hoang
```

Ngoài cách chạy code Ruby từ file script thì chúng ta cũng có thể chạy code từng dòng trong terminal:

```
C:\User\PhoCode>ruby -e "puts RUBY_VERSION"
2.2.4
```

Khi chúng ta chạy code Ruby từ file script, chẳng hạn như ruby hello.rb thì trình thông dịch Ruby sẽ đọc và dịch code trong file hello.rb, còn nếu chúng ta đưa vào tham số -e thì Ruby sẽ thực thi đoạn lệnh phía sau chứ không tìm file để chạy.

Ngoài ra trình thông dịch Ruby còn có tham số -c, khi dùng tham số này thì trình thông dịch Ruby sẽ thực hiện kiểm tra lỗi cú pháp của đoạn code chứ không thực hiện đoạn code bên trong, nếu không có lỗi thì sẽ in đoạn text “Syntax OK” ra màn hình.
syntax_check.rb

```
puts "This is Ruby
```

Đoạn có trên có lỗi cú pháp là thiếu dấu " kết thúc chuỗi.

```
C:\User\PhoCode>ruby -c syntax_check.rb 
syntax_check.rb:1: unterminated string meets end of file
```

Trình thông dịch sẽ báo lỗi nếu có lỗi.
Đưa tham số vào chương trình

Khi chúng ta chạy một file script Ruby thì có thể đưa các tham số vào chương trình để sử dụng.

```
puts ARGV
```

Trong Ruby biến toàn cục ARGV là biến lưu các tham số được truyền vào chương trình, đây là một mảng, mỗi phần tử trong mảng là một tham số.
args.rb

```
puts ARGV
```

Chúng ta in toàn bộ tham số được đưa vào chương trình.

```
C:\User\PhoCode>ruby args.rb 1 2 3
```

Chúng ta truyền tham số vào bằng cách gõ các giá trị vào sau tên file script. Trong đoạn code trên chúng ta truyền vào 3 con số.

Ngoài ra chúng ta có thể lấy từng tham số đơn lẻ:
args2.rb

```
puts $0
puts $*
```

Trong Ruby các biến toàn cục có tên bắt đầu bằng kí tự $ theo sau là tên biến. Ngoài ra Ruby còn có sẵn một số biến đặc biệt, chẳng hạn như $0 lưu tên file script được thực thi, $* cũng lưu các tham số truyền vào như ARGV.

```
C:\User\PhoCode>ruby args2.rb Ruby Python Perl
Ruby
Python
Perl
```

Biến và hằng số

Biến là nơi để lưu trữ dữ liệu. Biến gồm có tên và kiểu dữ liệu, kiểu dữ liệu là các loại giá trị khác nhau, ví dụ như số nguyên, chuỗi, số thực… là các loại kiểu dữ liệu khác nhau. Không giống các ngôn ngữ như C++, Java… bạn phải khai báo rõ ràng kiểu dữ liệu cùng tên biến như int a, Ruby là ngôn ngữ động, tức là bạn chỉ cần khai báo tên biến và gán giá trị cho nó là Ruby sẽ tự quy định kiểu dữ liệu, ngoài ra bạn cũng có thể thay đổi giá trị và Ruby cũng sẽ tự động thay đổi kiểu dữ liệu cho bạn luôn.

Hằng số trong Ruby cũng khác với các ngôn ngữ khác, trong các ngôn ngữ như C++, Java… thì hằng số là không thể thay đổi được giá trị, còn hằng số trong Ruby thì có thể thay đổi được, khi dịch thì Ruby không báo lỗi mà chỉ đưa ra các lời cảnh báo.
variables.rb

```
city = "New York"
name = "Paul"; age = 35
nationality = "American"
 
puts city
puts name
puts age
puts nationality
 
city = "London"
 
puts city
```

Trong đoạn code trên chúng ta làm việc với 4 biến.

```	
city = "New York"
```

Biến city lưu trữ một chuỗi text, Ruby tự động nhận diện kiểu dữ liệu.

```
name = "Paul"; age = 35
```

Khi khai báo nhiều biến trên cùng một dòng thì chúng ta phải ngăn cách chúng bằng dấu chấm phẩy. Trong thực tế thì tốt hơn hết là chúng ta khai báo trên nhiều dòng khác nhau.

```	
puts city
puts name
puts age
puts nationality
```

Chúng ta in các biến ra màn hình

```
city = "London"
```

Đoạn code trên sẽ gán lại giá trị mới cho biến city.

```
C:\User\PhoCode>ruby variables.rb 
New York
Paul
35
American
London
```

Trong đoạn code dưới đây chúng ta sẽ làm việc với hằng số.
constants.rb

```
WIDTH = 100
HEIGHT = 150
 
var = 40
puts var
 
var = 50
puts var
 
puts WIDTH
WIDTH = 110
puts WIDTH
```

Chúng ta khai báo 2 hằng và một biến.

```
WIDTH = 100
HEIGHT = 150
```

Chúng ta chỉ cần đặt tên với chữ cái đầu viết hoa thì biến đó sẽ là hằng số. Trong thực tế thì chúng ta nên viết hoa toàn bộ các chữ cái trong tên hằng.

```
C:\User\PhoCode>ruby constants.rb 
40
50
100
constants.rb:13: warning: already initialized constant WIDTH
110
```
