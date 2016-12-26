# Ruby – Mảng

Mảng là một tập hợp các phần tử có thứ tự. Khác với biến thông thường là mỗi biến chỉ lưu một giá trị tại một thời điểm, mảng lưu nhiều giá trị khác nhau tại một thời điểm. Kiểu dữ liệu của mảng cũng là kiểu dữ liệu động, tức là một mảng có thể lưu cùng lúc một chuỗi string, một số nguyên hoặc cả một đối tượng khác. Các phần tử trong mảng ngoài giá trị ra còn được đánh số thứ tự, số thứ tự trong mảng được bắt đầu từ 0 giống như các ngôn ngữ khác.

Ví dụ:
example.rb
```
arr = [1, 2, 3, 4, 5]
 
arr.each do |num|
    puts num
end
```
Chúng ta có một mảng tên là arr có 5 phần tử là 5 số nguyên. Chúng ta dùng phương thức each duyệt qua mỗi phần tử trong mảng rồi in giá trị ra màn hình.
Output
```
1
2
3
4
5
```

Khởi tạo mảng

Mảng là một đối tượng, do đó chúng ta có thể sử dụng phương thức new để tạo mảng.

Ví dụ 1:
array_init1.rb
```
arr = Array.new
 
arr.push 1
arr.push 2
arr.push 3
arr.push 4
arr.push 5
 
puts arr
```
Trong đoạn code trên chúng ta tạo một mảng có 5 số nguyên.
```
arr = Array.new
```
Để tạo một mảng thì chúng ta dùng phương thức new của lớp Array.
```
arr.push 1
```
Phương thức push sẽ thêm một phần tử vào cuối mảng.

Ví dụ 2:
array_init2.rb
```
a1 = Array.new
a2 = Array.new 3
a3 = Array.new 6, "coin"
a4 = Array.new [11]
 
puts [a1, a2, a3, a4].inspect
```
Phương thức new có thể nhận một vài tham số khi khởi tạo.
```
a1 = Array.new
```
Nếu chúng ta chỉ gọi phương thức new thì Ruby sẽ tạo một mảng rỗng.
```
a2 = Array.new 3
```
Tham số đầu tiên mà phương thức này nhận là số lượng phần tử mảng, dòng code trên sẽ tạo một mảng có 3 phần tử là các đối tượng nil.
```
a3 = Array.new 6, "coin"
```
Tham số thứ 2 là giá trị mặc định, dòng code trên sẽ tạo một mảng có 6 phần tử với mỗi phần tử là một string có giá trị là “coin”.
```
a4 = Array.new [11]
```
Hoặc chúng ta có thể khởi tạo các phần tử và giá trị luôn bằng cặp dấu ngoặc vuông []. Dòng code trên tạo một mảng có một phần tử là số 11.
```
puts [a1, a2, a3, a4].inspect
```
Một mảng cũng có thể chứa các mảng khác, trong dòng trên chúng ta đưa 4 mảng a1, a2, a3 và a4 vào một mảng. Phương thức inspect sẽ trả về một chuỗi mô tả các phần tử của mảng nằm trong cặp dấu [].
Output
```
[[], [nil, nil, nil], ["coin", "coin", "coin", "coin", "coin", "coin"], [11]]
```
Ví dụ 3:

Mỗi phần tử trong Ruby có thể mang bất kì kiểu dữ liệu nào, các phần tử cũng không cần phải có kiểu dữ liệu giống nhau.
array_init3.rb
```
class Empty
   
end
 
arr1 = [1, 2, 3, 4, 5]
 
arr2 = [1, -1, "big", 3.4, Empty.new, arr1, :two]
 
puts arr2.inspect
```
Trong ví dụ này chúng ta có mảng arr2 chứa số nguyên, chuỗi, số thực, một đối tượng lớp, một symbol và một mảng khác.
Output
```
[1, -1, "big", 3.4, #<Empty:0x2591868>, [1, 2, 3, 4, 5], :two]
```
Ví dụ 4:

Các mảng có thể lồng vào nhau không giới hạn.
array_init4.rb
```
arr = [1, 2, 3, [2, 4, 6, [11, 12]]]
 
puts arr.length
puts arr[0], arr[1]
 
puts arr[3][0]
puts arr[3][1]
 
puts arr[3][3][0]
puts arr[3][3][1]
 
puts arr.flatten!.inspect
```
Trong ví dụ trên, mảng [11, 12] được lồng vào mảng [2, 4, 6], mảng [2, 4, 6] lại được lồng vào mảng [1, 2, 3].
```
puts arr.length
```
Phương thức length sẽ trả về 4 vì một mảng lồng trong một mảng khác cũng chỉ tính là một phần tử.
```
puts arr[0], arr[1]
```
Toán tử [] sẽ lấy giá trị của các phần tử mảng tương ứng. Trong dòng code trên chúng ta in ra giá trị của phần tử thứ 0 và thứ 1.
```
puts arr[3][0]
puts arr[3][1]
```
Để lấy giá trị của phần tử nằm trong mảng con bên trong thì chúng ta lại dùng thêm một toán tử [] khác nữa. Ở đây [3][0] tức là lấy phần tử đầu tiên của phần tử thứ 4 trong mảng [2, 4, 6, [11, 12]] (vì chỉ số được đánh từ 0).
```
puts arr[3][3][0]
puts arr[3][3][1]
```
Tương tự với các phần tử mảng nằm sâu bên trong, chúng ta chỉ cần dùng toán tử [] là lấy được.
```
puts arr.flatten!.inspect
```
Phương thức flatten! sẽ lấy các phần tử của mảng con nhập vào mảng cha và tạo thành một mảng mới.
Output
```
4
1
2
2
4
11
12
[1, 2, 3, 2, 4, 6, 11, 12]
```

Xuất mảng ra màn hình

Có rất nhiều cách để in các phần tử mảng ra màn hình.
print_array.rb
```
arr = [1, 2, 3, 4, 5]
 
puts arr
puts arr.inspect
 
arr.each do |e|
    puts e
end
```
Trong ví dụ trên chúng ta in mảng ra bằng 3 cách.
```
puts arr
```
Cách đơn giản nhất là dùng phương thức puts hoặc print, 2 phương thức này sẽ in các phần tử mảng trên từng dòng.
```
puts arr.inspect
```
Phương thức inspect sẽ in các phần tử mảng trong cặp dấu [], mỗi phần tử ngăn cách nhau bởi dấu phẩy.
```
arr.each do |e|
    puts e
end
```
Phương thức each sẽ duyệt qua từng phần tử trong mảng, mỗi lần duyệt sẽ thực hiện các câu lệnh phía sau từ khóa do.
Output
```
1
2
3
4
5
[1, 2, 3, 4, 5]
1
2
3
4
5
```

Tuy xuất các phần tử mảng

Các đối tượng mảng có một số phương thức dùng để lấy các phần tử tại bất kì vị trí nào.

Ví dụ:
read_array1.rb
```
alpha = %w{ a b c d e f g h}
puts alpha.first
puts alpha.last
puts alpha.at(3)
```
Trong ví dụ trên chúng ta dùng phương thức first để lấy phần tử đầu tiên, phương thức last lấy phần tử ở vị trí cuối cùng, phương thức at(i) lấy phần tử tại vị trí thứ i.
```
alpha = %w{a b c d e f g h}
```
Ngoài ra chúng ta còn có cách tạo nhanh một mảng chứa các phần tử là chuỗi theo cú pháp %w{}, theo cú pháp này %w{a b} tương đương với ['a', 'b'].
Output
```
a
h
d
```
Ví dụ 2:

Thông thường chúng ta sẽ dùng toán tử [] để truy xuất phần tử mảng.
read_array2.rb
```
alpha = %w{ a b c d e f g h }
 
puts alpha[0]
puts alpha[-1]
puts alpha[0, 3].inspect
puts alpha[2..6].inspect
puts alpha[2...6].inspect
```
Trong ví dụ trên chúng ta có 5 cách sử dụng toán tử [] để truy xuất phần tử mảng.
```
puts alpha[0]
puts alpha[-1]
```
Để lấy từng phần tử thì chúng ta có thể đưa vào chỉ số mảng, chỉ số mảng trong Ruby được đánh số từ 0 và chúng ta cũng có thể đưa vào chỉ số âm để lấy phần tử từ cuối mảng.
```
puts alpha[0, 3].inspect
```
Chúng ta có thể sử dụng toán tử [] theo cú pháp [i, n] và Ruby sẽ lấy n phần tử từ vị trí i. Phương thức inspect chẳng qua là để in các phần tử mảng trong cặp dấu [] trên một dòng ngăn cách bằng dấu phẩy cho dễ đọc.
```
puts alpha[2..6].inspect
puts alpha[2...6].inspect
```
Như chúng ta đã biết, [n..i] sẽ lấy các phần tử từ vị trí n đến vị trí i, [n...i] sẽ lấy các phần tử từ vị trí n đến vị trí i - 1.

Ví dụ 3:
read_array3.rb
```
alpha = %w{ a b c d e f g h}
 
puts alpha.values_at(1..5).inspect
puts alpha.values_at(1, 3, 5).inspect
puts alpha.values_at(1, 3, 5, 6, 8).inspect
puts alpha.values_at(-1, -3).inspect
```
Chúng ta có thể sử dụng phương thức values_at để lấy nhiều phần tử tại những vị trí riêng biệt. Giá trị trả về của phương thức values_at là một mảng chứa các phần tử được lấy ra..
```
puts alpha.values_at(1..5).inspect
```
Dòng trên sẽ trả về các phần tử từ vị trí 1 đến vị trí 5.
```
puts alpha.values_at(1, 3, 5).inspect
```
Dòng trên lấy các phần tử ở vị trí 1, 3, và 5.
```
puts alpha.values_at(-1, -3).inspect
```
Chúng ta cũng có thể đưa vào các chỉ số âm như với toán tử [].
Output
```
["b", "c", "d", "e", "f"]
["b", "d", "f"]
["b", "d", "f", "g", nil]
["h", "f"]
```
Ví dụ 4:
read_array4.rb
```
alpha = %w{ a b c d e f g h}
 
puts alpha.slice(0)
puts alpha.slice(-1)
puts alpha.slice(0, 3).inspect
puts alpha.slice(2..6).inspect
puts alpha.slice(2...6).inspect
```
Mảng trong Ruby có phương thức slice có chức năng và cách dùng y hệt như toán tử [].
Output
```
a
h
["a", "b", "c"]
["c", "d", "e", "f", "g"]
["c", "d", "e", "f"]
```
Ví dụ 6:
read_array6.rb
```
alpha = %w{ a b c d e f g h}
 
puts alpha.sample
puts alpha.sample(3).inspect
```
Phương thức sample có tác dụng lấy một hoặc một số phần tử tại vị trí bất kì.
Output
```
b
["c", "f", "d"]
```

Một số thao tác trên mảng

Ví dụ 1:
array_methods1.rb
```
arr1 = [1, 2, 3, 4, 5]
arr2 = [6, 7, 8, 9, 10]
 
puts arr1 + arr2
puts arr1.concat arr2
```
Chúng ta có thể nối 2 mảng vào nhau bằng toán tử + hoặc dùng phương thức concat.

Ví dụ 2:
array_methods2.rb
```
alpha = %w{ a b c d e f}
 
puts alpha.inspect
puts "Array size: #{alpha.length}"
puts "First element: #{alpha.first}"
puts "Last element: #{alpha.last}"
 
puts alpha.eql? alpha.dup
puts alpha.eql? alpha.dup.delete_at(0)
 
alpha.clear
puts alpha.inspect
puts alpha.empty?
```
Trong ví dụ trên chúng ta làm việc với một số phương thức mới.
```
puts "Array size: #{alpha.length}"
```
Chúng ta đã biết, phương thức length cho biết số lượng phần tử trong mảng.
```
puts "First element: #{alpha.first}"
puts "Last element: #{alpha.last}"
```
Phương thức first và last lấy phần tử đầu tiên và phần tử cuối cùng.
```
puts alpha.eql? alpha.dup
```
Phương thức eql! so sánh 2 mảng và trả về True nếu 2 mảng bằng nhau. Trong đoạn code trên là trả về True vì ở đây chúng ta dùng phương thức dup để tạo ra một mảng mới copy từ mảng gốc.
```
puts alpha.eql? alpha.dup.delete_at(0)
```
Phương thức delete_at(i) sẽ xóa phần tử tại vị trí thứ i. Dòng trên sẽ trả về False vì 2 mảng không giống nhau.
```
alpha.clear
```
Phương thức clear sẽ xóa toàn bộ mảng.
```
puts alpha.empty?
```
Phương thức empty? cho biết mảng có rỗng hay không.
Output
```
["a", "b", "c", "d", "e", "f"]
Array size: 6
First element: a
Last element: f
true
false
[]
true
```
Ví dụ 3:
array_methods3.rb
```
alpha = %w{a b c d e}
 
alpha1 = alpha.reverse
puts alpha1.inspect
puts alpha.inspect
 
alpha1 = alpha.reverse!
puts alpha1.inspect
puts alpha.inspect
```
Khi sử dụng các phương thức mà có thay đổi giá trị phần tử mảng thì chúng ta phải thêm dấu chấm ! vào cuối tên phương thức.

Phương thức reverse sẽ đảo ngược các phần tử trong mảng, ví dụ phần tử đầu tiên đổi chỗ cho phần tử cuối cùng…
Output
```
["e", "d", "c", "b", "a"]
["a", "b", "c", "d", "e"]
["e", "d", "c", "b", "a"]
["e", "d", "c", "b", "a"]
```
Ví dụ 4:
array_methods4.rb
```
arr = [1, 2, 2, 2, 3, 4, 5, 8, 11]
 
puts arr.index 2
puts arr.index 11
puts arr.rindex 2
 
puts arr.include? 3
puts arr.include? 10
 
puts arr.join '-'
puts arr.uniq!.inspect
```
Trong ví dụ này chúng ta có thêm một số phương thức thao tác với mảng khác.
```
puts arr.index 2
puts arr.index 11
```
Phương thức index i trả về chỉ số của phần tử đầu tiên có giá trị i, ví dụ chúng ta có 3 phần tử có giá trị là 2 thì index 2 sẽ trả về phần tử đầu tiên có giá trị 2 là phần tử thứ 1.
```
puts arr.rindex 2
```
Phương thức rindex cũng có tác dụng như phương thức index nhưng tìm các phần tử từ phải qua trái.
```
puts arr.include? 3
puts arr.include? 10
```
Phương thức include? cho biết một giá trị có tồn tại trong mảng hay không, phương thức này trả về True nếu có và False nếu ngược lại.
```
puts arr.join '-'
```
Phương thức join sẽ tạo một chuỗi string có các phần tử ngăn cách nhau bởi kí tự được truyền vào, trong ví dụ trên là kí tự "-".
```
puts arr.uniq!.inspect
```
Phương thức uniq! sẽ loại bỏ các phần tử có giá trị giống nhau.
Output
```
1
8
3
true
false
1-2-2-2-3-4-5-8-11
[1, 2, 3, 4, 5, 8, 11]
```

Thêm bớt phần tử

Ví dụ 1:
insert_array.rb
```
alpha = []
 
alpha.insert 0, 'E', 'F', 'G'
alpha.push 'H'
alpha.push 'I', 'J', 'K'
alpha << 'L' << 'M'
alpha.unshift 'A', 'B', 'C'
alpha.insert(3, 'D')
  
puts alpha.inspect
```
Để thêm một phần tử vào mảng thì có rất nhiều cách.
```
alpha.insert 0, 'E', 'F', 'G'
```
Phương thức insert sẽ thêm các phần tử vào vị trí được chỉ định, trong đoạn code trên chúng ta thêm 3 kí tự E, F, G vào vị trí 0 nhưng vì mỗi vị trí chỉ có một phần tử nên F, G sẽ ở vị trí 1 và 2.
```
alpha.push 'H'
alpha.push 'I', 'J', 'K'
```
Phương thức push sẽ thêm phần tử vào cuối mảng. Chúng ta có thể thêm một lúc nhiều phần tử bằng ngăn cách nhau bởi dấu phẩy.
```
alpha << 'L' << 'M'
```
Toán tử << cũng có tác dụng như phương thức push.
```
alpha.unshift 'A', 'B', 'C'
```
Phương thức unshift ngược lại với phương thức push là chèn các phần tử mới vào đầu mảng.
```
alpha.insert(3, 'D')
```
Phương thức insert() sẽ chèn phần tử vào vị trí được chỉ định.
Output
```
["A", "B", "C", "D", "E", "F", "G", "H", "I", "J", "K", "L", "M"]
```
Ví dụ 2:
delete_array.rb
```
alpha = %w{ a b c d e f g h}
 
alpha.pop
alpha.pop
 
puts alpha.inspect
 
alpha.shift
alpha.shift
 
puts alpha.inspect
 
alpha.delete_at(0)
alpha.delete('d')
 
puts alpha.inspect
 
puts alpha.clear
puts alpha.inspect
```
Để xóa các phần tử ra khỏi mảng cũng có nhiều cách.
```
alpha.pop
```
Phương thức pop xóa phần tử cuối cùng của mảng.
```
alpha.shift
```
Phương thức shift xóa phần tử đầu tiên của mảng.
```
alpha.delete_at(0)
```
Phương thức delete_at(i) xóa phần tử tại vị trí thứ i.
```
puts alpha.clear
```
Phương thức clear xóa toàn bộ mảng.
```
alpha.delete('d')
```
Phương thức delete(i) xóa phần tử có giá tị là i.
Output
```
["a", "b", "c", "d", "e", "f"]
["c", "d", "e", "f"]
["e", "f"]
[]
```

Toán tử tập hợp

Tập hợp cũng là một danh sách các phần tử nhưng các phần tử không được phép trùng nhau.
set.rb
```
A = [1, 2, 3, 4, 5]
B = [4, 5, 6, 7, 8]
 
union = A | B
isect = A & B
diff1  = A - B
diff2  = B - A
sdiff = (A - B) | (B - A)
 
puts "Union: #{union}"
puts "Intersection: #{isect}"
puts "Difference of A - B: #{diff1}"
puts "Difference of B - A: #{diff2}"   
puts "Symmetric: #{sdiff}"
```
Ruby có các toán tử có chức năng thực hiện các phép toán tập hợp trên mảng.
```
union = A | B
```
Toán tử | sẽ thực hiện phép hợp, phần tử nào cũng được lấy.
```
isect = A & B
```
Toán tử ^ thực hiện phép giao, chỉ có các phần tử cùng nằm chung 2 mảng mới được lấy.
```
diff1  = A - B
diff2  = B - A
```
Toán tử "-" thực hiện phép hiệu, phép hiệu A – B sẽ lấy các phần tử thuộc tập A và các phần tử trong tập B mà cũng có trong tập A.
```
sdiff = (A - B) | (B - A)
```
Phép hiệu đối xứng sẽ lấy các phần tử của riêng từng tập hợp, phần tử nào có mặt trong cả 2 tập hợp thì không lấy. Thực ra trong toán học không có phép toán này, ở đây mình chỉ kết hợp phép hiệu với phép giao lại thôi.
Output
```
Union of arrays: [1, 2, 3, 4, 5, 6, 7, 8]
Intersection of arrays: [4, 5]
Difference of arrays A - B: [1, 2, 3]
Difference of arrays B - A: [6, 7, 8]
Symmetric difference of arrays: [1, 2, 3, 6, 7, 8]
```

Sắp xếp mảng

Ruby có một số phương thức sắp xếp các phần tử mảng rất mạnh.
sorting.rb
```
arr = %w{ Mercury Venus Earth Mars Jupiter
                Saturn Uranus Neptune Pluto }
                
puts "#{arr.sort}"               
puts "#{arr.reverse}"
puts "#{arr.shuffle}"
```
Phương thức sort sắp xếp các phần tử từ bé đến lớn, hoặc theo thứ thự bảng chữ cái nếu các phần tử là kiểu chuỗi.

Phương thức reverse thì sắp xếp theo thứ tự ngược lại.

Phương thức shuffle sẽ xáo trộn vị trí các phần tử một cách ngẫu nhiên.
Output
```
["Earth", "Jupiter", "Mars", "Mercury", "Neptune", "Pluto", "Saturn", "Uranus", "Venus"]
["Pluto", "Neptune", "Uranus", "Saturn", "Jupiter", "Mars", "Earth", "Venus", "Mercury"]
["Venus", "Mercury", "Uranus", "Mars", "Neptune", "Earth", "Jupiter", "Pluto", "Saturn"]
```
