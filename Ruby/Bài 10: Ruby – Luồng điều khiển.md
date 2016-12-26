# Ruby – Luồng điều khiển

Các câu lệnh điều khiển chịu trách nhiệm điều khiển luồng chương trình chạy trong Ruby. Các câu lệnh điều khiển bao gồm 2 loại câu lệnh cơ bản là câu **lệnh điều kiện** và **vòng lặp**. Câu lệnh điều kiện là các câu lệnh có tác dụng thực hiện các câu lệnh khác nhau tùy theo từng điều kiện khác nhau. Vòng lặp là khối lệnh có tác dụng thực hiện các câu lệnh lặp đi lặp lại nhiều lần.

Khi một chương trình chạy thì các câu lệnh sẽ được thực hiện tuần tự từ trên xuống dưới.
Câu lệnh điều kiện **if**

Từ khóa **if** được dùng để kiểm tra xem một biểu thức có đúng hay không. Nếu đúng thì thực thi một câu lệnh hoặc một khối lệnh, một khối lệnh phải được đặt trước từ khóa end.
if_keyword.rb
```
puts "Enter a number: "
num = gets.to_i
 
if num > 0 then
 
    puts "num variable is positive"
    puts "num variable equals to #{num}"
end
```
Phương thức **gets.to_i** sẽ đọc một chuỗi được nhập từ bàn phím và chuyển thành số nguyên rồi gán vào biến num, sau đó câu lệnh **if** kiểm tra xem nếu biến num lớn hơn 0 thì in các chuỗi text ra màn hình.
Output
```
Enter a number: 4
num variable is positive
num variable equals to 4
```
Chúng ta có thể sử dụng từ khóa **else** để thực thi một khối lệnh khác nếu biểu thức trong **if** là sai:
if_else_keyword.rb
```
age = 17
 
if age > 18
    puts "Adult"
else
    puts "Not Adult"
end
```
Trong ví dụ trên chúng ta có biến age là 17, câu lệnh **if** kiểm tra xem nếu biến age > 18 thì in ra chuỗi “Adult”, ngược lại thì in ra chuỗi "Not Adult".
Output
```
Not Adult
```
Ngoài ra chúng ta còn có thể dùng từ khóa **elseif** để thực hiện kiểm tra nhiều biểu thức khác nhau:
if_elseif_else_keyword.rb
```
print "Enter a number: "
 
num = gets.to_i
 
if num < 0
    puts "#{num} is negative"
elsif
    num == 0 puts "#{num} is zero"
elsif num > 0
   puts "#{num} is positive"
end
```
Trong ví dụ trên chúng ta cho nhận một số được nhập từ bàn phím và in ra chuỗi string tương ứng với từng trường hợp số đó bé hơn 0, bằng 0 hoặc lớn hớn 0.

# Câu lệnh điều kiện case

Câu lệnh **case** có tác dụng lựa chọn các câu lệnh để thực thi dựa vào điều kiện đặt ra, do đó câu lệnh **case** cũng có tác dụng tương tự như câu lệnh **if..elseif** vậy. Cú pháp:
```
case <biến>
when <giátrị>
else  
end
```
Bên trong khối lệnh **case..end** là các từ khóa **when** và **else**, theo sau các từ khóa **when** là các giá trị, Khi chạy, Ruby sẽ so sánh biến theo sau từ khóa **case** với từng giá trị ở từng từ khóa **when**, nếu trùng tại đâu thì chạy câu lệnh phía sau từ khóa **when** đó, nếu không có từ khóa **when** nào khớp thì chạy câu lệnh mặc định sau từ khóa **else**.
case_keyword.rb
```
print "Enter a domain: "
 
domain = gets.chomp
 
case domain
    when "us"
        puts "United States"
    when "de"
        puts "Germany"
    when "no"
        puts "Norway"
    when "hu"
        puts "Hungary"
    else
        puts "Unknown"
end
```
Trong đoạn code trên chúng ta nhận một chuỗi được nhập từ bàn phím và gán vào biến domain, sau đó kiểm tra với từng giá trị trong câu lệnh **case**, nếu domain trùng với giá trị nào thì in một chuỗi string ra màn hình tương ứng với gái trị đó, nếu không trùng với giá trị nào thì in chuỗi “Unknown”.
```
domain = gets.chomp
```
Phương thức **chomp** sẽ nhận một chuỗi từ bàn phím, kể cá kí tự ENTER nhưng sau đó phương thức này sẽ tự loại bỏ kí tự ENTER ra khỏi chuỗi.
Output
```
Enter a domain: no
Norway
```

# Câu lệnh lặp while và until

Câu lệnh **while** cho phép một câu lệnh hoặc một khối lệnh được thực hiện lặp đi lặp lại nhiều lần trong điều kiện cho trước.

Theo sau từ khóa **while** là một biểu thức, nếu biểu thức này trả về **true** thì thực hiện câu lệnh theo sau nó rồi lặp lại biểu thức **cho đến khi biểu thức trả về false** thì thôi.
while_keyword.rb
```
i = 0
sum = 0
 
while i < 10  do
   i = i + 1
   sum = sum + i
end
 
puts "Sum of 0..9 is #{sum}"
```
Đoạn code trên sẽ tính tổng của các số từ 0 đến 9.

Cứ mỗi lần lặp, các biến i và sum sẽ được tính lại giá trị mới cho đến khi điều kiện i < 10 sai thì dừng vòng lặp.
```
while i < 10  do
   ...
end
```
Từ khóa **do** là tùy chọn, **không có cũng được**.
Output
```
Sum of 0..9 is 55
```
Câu lệnh **until** thì cũng có cấu trúc cú pháp giống như câu lệnh **while**, chỉ khác là **until** sẽ thực hiện các câu lệnh nếu điều kiện sai (**false**), nếu biểu thức sau **until** trả về **true** thì dừng vòng lặp.
until_keyword.rb
```
hours_left = 12
 
until hours_left == 0
     
    if hours_left == 1
        puts "#{hours_left} hour left"
    else
        puts " #{hours_left} hours left"
    end
 
    hours_left -= 1
end
```
Trong ví dụ trên chúng ta có biến hours_left, biến này sẽ giảm dần theo từng vòng lặp và cứ mỗi lần lặp chúng ta in một đoạn string ra màn hình, vòng lặp sẽ dừng khi biến hours_left = 0.
Output
```
12 hours left
11 hours left
10 hours left
9 hours left
8 hours left
7 hours left
6 hours left
5 hours left
4 hours left
3 hours left
2 hours left
1 hour left
```

# Câu lệnh lặp for

Khác với câu lệnh **while** và **until** là số lần lặp không được biết trước, câu lệnh **for** sẽ chạy vòng lặp với số lần nhất định. Cũng giống các câu lệnh trên, câu lệnh **for** cũng kết thúc với từ khóa **end** và có thể có từ khóa **do** nếu muốn.
for_keyword.rb
```
for i in 0..9 do
 
    puts "#{i}"
end
```
Đoạn code trên sẽ in các con số từ 0 đến 9. Biến i trong vòng lặp sẽ được thay thế bởi các số trong đoạn 0..9, toán tử .. sẽ tạo một biến danh sách các số nguyên từ 0 đến 9.
Output
```
0
1
2
3
4
5
6
7
8
9
```
Thường chúng ta dùng vòng lặp **for** để duyệt qua một danh sách các phần tử.
for_keyword2.rb
```
planets = ["Mercury", "Venus", "Earth", "Mars", "Jupiter",
    "Saturn", "Uranus", "Neptune"]
 
for i in 0...planets.length
 
    puts planets[i]
end
```
Trong ví dụ trên chúng ta có một biến mảng, chúng ta duyệt qua mảng này bằng vòng lặp **for** với số lần lặp được lấy từ phương thức **length**, phương thức này cho biết số phần tử có trong mảng.
```
for i in 0...planets.length
```
Mảng được đánh số từ 0 nên biến i sẽ có giá trị từ 0 đến n-1, với n là số phần tử của mảng. Do dó chúng ta sử dụng toán tử ... để tạo một danh sách các con số từ 0 đến length-1.
Output
```
Mercury
Venus
Earth
Mars
Jupiter
Saturn
Uranus
Neptune
```

# Phương thức each

Mảng trong Ruby có phương thức each cho phép chúng ta duyệt qua mảng một cách dễ dàng.
each_method.rb
```
planets = ["Mercury", "Venus", "Earth", "Mars", "Jupiter",
    "Saturn", "Uranus", "Neptune"]
 
planets.each do |iter| 
 
    puts iter
end
```
Phương thức này nhận vào 2 tham số là tên mảng và một khối lệnh, khối lệnh sẽ thực hiện các câu lệnh trong mỗi lần duyệt qua mảng.
```
planets.each do |iter| 
 
    puts iter
end
```
Phía sau phương thức each là khối lệnh nằm trong cặp từ khóa **do..end**, sau từ khóa do là tên của biến lặp, mỗi lần lặp, biến này sẽ tham chiếu đến từng phần tử của mảng. Cặp từ khóa **do..end** cũng có thể được thay thế bằng cặp dấu **{}**.
Câu lệnh **break, next**

Câu lệnh **break** có tác dụng kết thúc vòng lặp **while**, **for** hoặc **case** cho dù vòng lặp đó có chạy xong hay chưa.
break_keyword.rb
```
while true
 
    r = 1 + rand(30)
    print "#{r} "
 
    if r == 22
        break
    end
end
```
Trong ví dụ trên chúng ta có một vòng lặp chạy vô thời hạn vì điều kiện sau while luôn luôn là **true**, do đó bên trong vòng lặp này chúng ta đặt một câu lệnh if để kiểm tra điều kiện, ở đây trong mỗi lần lặp chúng ta tạo một số ngẫu nhiên rồi gán vào biến r, sau đó chúng ta kiểm tra nếu r = 22 thì dừng vòng lặp bằng câu lệnh **break**.
```
r = 1 + rand(30)
print "#{r} "
```
Phương thức **rand(n)** sẽ cho ra một số ngẫu nhiên từ 0..n.
Output
```
27 30 9 8 27 25 29 30 24 17 16 20 27 13 7 5 13 28 22
```
Câu lệnh next có tác dụng bỏ qua vòng lặp hiện tại và thực hiện vòng lặp tiếp theo, các câu lệnh sau từ khóa next sẽ không được thực thi.
next_keyword.rb
```
num = 0
 
while num < 100
 
    num += 1
 
    if (num % 2 == 0)
        next
    end
 
    print "#{num} "
end   
```
Trong ví dụ trên chúng ta in ra những số lẻ từ 1 đến 99.
```
if (num % 2 == 0)
    next
end
```
Biểu thức num % 2 == 0 sẽ trả về true nếu biến num là số chẵn, ngược lại là true, nếu num là số chẵn thì câu lệnh next sẽ bỏ qua vòng lặp hiện tại, tức là câu lệnh print ở dưới sẽ không được thực hiện mà nhảy đến vòng lặp tiếp theo.
Output
```
1 3 5 7 9 11 13 15 17 19 21 23 25 27 29 31 33 35 37 39 41 43 45 47 49 51 53 55 57 59 61 63 65 67 69 71 73 75 77 79 81 83 85 87 89 91 93 95 97 99
```
