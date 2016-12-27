# Ruby – Bảng băm
Bảng băm là một kiểu dữ liệu lưu trữ theo dạng tập hợp giống như mảng, nhưng các phần tử không được lưu chỉ số mà lưu theo khóa, tức là các phần tử của bảng băm có 2 thành phần là khóa và giá trị.
Khởi tạo bảng băm

Ví dụ 1:

Để tạo một đối tượng bảng băm thì chúng ta có thể dùng phương thức **new** với lớp **Hash**.
create_hash1.rb
```
hash = Hash.new
hash[1] = "Jane"
hash.store(2, "Thomas")
 
puts hash
```
Trong đoạn code trên chúng ta tạo một bảng băm từ lớp Hash với phương thức **new**.
```
hash[1] = "Jane"
hash.store(2, "Thomas")
```
Để tạo các phần tử trong bảng băm thì chúng ta có thể dùng toán tử **[]** với tên khóa bên trong. Ở trên chúng ta dùng khóa là các số nguyên, nhưng nếu muốn chúng ta có thể dùng khóa là các kí tự. Ngoài ra lớp **Hash** còn có phương thức **store** để tạo các phần tử của bảng băm tương tự như toán tử **[]**.
```
puts hash
```
Phương thức puts sẽ in các phần tử của bảng băm ra trong cặp dấu **{}**. Các phần tử của bảng băm sẽ được in theo dạng **<khóa> => <giá trị>**.
Output
```
{1=>"Jane", 2=>"Thomas"}
```
Ví dụ 2:
create_hash2.rb
```
hash = { "de" => "Germany",
    "sk" => "Slovakia",
    "hu" => "Hungary",
    "us" => "United States",
    "no" => "Norway"
}
 
puts hash["de"]
puts hash["no"]
```
Chúng ta có thể tạo nhanh các phần tử của bảng băm bằng theo cú pháp {<khóa>=><giá trị>}.
```
hash = { "de" => "Germany",
    "sk" => "Slovakia",
    "hu" => "Hungary",
    "us" => "United States",
    "no" => "Norway"
}
```
Trong ví dụ này chúng ta tạo các khóa và giá trị là các chuỗi string.
```
puts hash["de"]
```
Chúng ta có thể in từng giá trị của từng phần tử nhất định thông qua khóa của chúng với toán tử **[]**.
Output
```
Germany
Norway
```

# Các thao tác trên bảng băm

Ví dụ 1:
hash_methods1.rb
```
hash = Hash.new
 
hash[1] = "Jane"
hash[2] = "Thomas"
hash[3] = "Robert"
hash[4] = "Julia"
hash[5] = "Rebecca"
 
puts "Hash size: #{hash.size}"
 
puts hash.keys.inspect
puts hash.values.inspect
```
Trong ví dụ này chúng ta sử dụng một số phương thức cơ bản của bảng băm.
```
puts "Hash size: #{names.size}"
```
Phương thưc size sẽ trả về số lượng phần tử của bảng băm.
```
puts hash.keys.inspect
puts hash.values.inspect
```
Phương thức keys sẽ trả về danh sách các khóa trong khi phương thức **values** sẽ trả về danh sách các giá trị có trong bảng băm.
Output
```
Hash size: 5
[1, 2, 3, 4, 5]
["Jane", "Thomas", "Robert", "Julia", "Rebecca"]
```
Ví dụ 2:
hash_methods2.rb
```
hash = Hash.new
 
hash[1] = "Jane"
hash[2] = "Thomas"
hash[3] = "Robert"
hash[4] = "Julia"
hash[5] = "Rebecca"
 
hash2 = hash.dup
 
puts hash.eql? hash2
 
puts hash.empty?
hash.clear
puts hash.empty?
```
Trong ví dụ này chúng ta sử dụng một số phương thức khác của bảng băm.
```
hash2 = hash.dup
```
Phương thức **dup** sẽ tạo một bảng băm khác có các phần tử giống như bảng băm gốc.
```
puts hash.eql? hash2
```
Phương thức **eql?** cho biết 2 bảng băm có các cặp khóa-giá trị giống nhau hay không.
```
puts hash.empty?
```
Phương thức **empty?** cho biết bảng băm có rỗng hay không, dòng code trên sẽ trả về **false**.
```
hash.clear
puts hash.empty?
```
Phương thức **clear** sẽ xóa toàn bộ bảng băm, do đó phương thức **empty?** ở sau sẽ trả về **True**.
Output
```
true
false
true
```
Ví dụ 3:
hash_methods3.rb
```
hash = { :de => "Germany", 
    :sk => "Slovakia",
    :no => "Norway", 
    :us => "United States"
 }
 
puts hash.has_key? :de
puts hash.include? :no
puts hash.key? :me
puts hash.member? :sk
 
puts hash.has_value? "Slovakia"
puts hash.value? "Germany"
```
Trong ví dụ này chúng ta kiểm tra sự tồn tại của các phần tử. Ngoài ra ở đây chúng ta sử dụng các đối tượng **Symbol** để làm khóa vì **Symbol dễ dùng hơn và cũng tốn ít bộ nhớ hơn**.
```
puts hash.has_key? :de
puts hash.include? :no
puts hash.key? :me
puts hash.member? :sk
```
Phương thức **has_key?**, **include?**, **key?** và **member?** đều kiểm tra xem một khóa nào đó có tồn tại trong bảng băm hay không.
```
puts hash.has_value? "Slovakia"
puts hash.value? "Germany"
```
Phương thức **has_value?** và **value?** cho biết giá trị nào đó có tồn tại trong bảng băm hay không.
Output
```
true
true
false
true
true
true
```
Ví dụ 4:
hash_methods4.rb
```
hash = { 1 => "Germany", 
    2 => "Norway", 
    3 => "United Kingdom", 
    4 => "United States"
 }
 
puts hash.fetch 1
puts hash[2]
puts hash.values_at 1, 2, 3
```
Trong ví dụ này chúng ta sử dụng các phương thức đọc dữ liệu từ bảng băm.
```
puts hash.fetch 1
```
Phương thức **fetch** nhận vào khóa và trả về giá trị.
```
puts hash[2]
```
Như chúng ta đã biết, toán tử **[]** sẽ trả về giá trị với khóa được chỉ định.
```
puts hash.values_at 1, 2, 3
```
Phương thức **values_at** sẽ trả về các phần tử có khóa được chỉ định.
Output
```
Germany
Norway
Germany
Norway
United Kingdom
```

Duyệt bảng băm

Có rất nhiều cách để duyệt qua từng phần tử trong bảng băm.
browse_hash.rb
```
hash = { 1 => "Germany", 
    2 => "Norway", 
    3 => "United Kingdom", 
    4 => "United States"
 }
 
hash.each { |k, v| puts "Key: #{k}, Value: #{v}" }
hash.each_key { |key| puts "#{key}" }
hash.each_value { |val| puts "#{val}" }
hash.each_pair { |k, v| puts "Key: #{k}, Value: #{v}" }
```
Trong ví dụ này chúng ta sử dụng 4 phương thức khác nhau để duyệt qua bảng băm.
```
hash.each { |k, v| puts "Key: #{k}, Value: #{v}" }
```
Phương thức each sẽ duyệt qua toàn bộ từng phần tử trong bảng băm, mỗi lần duyệt chúng ta thực thi đoạn lênh bên trong cặp dấu **{}**. Trong đó |k, v| đại diện cho khóa và giá trị, k và v chỉ là những cái tên thay thế, chúng ta có thể dùng tên bất kì do chúng ta đặt như |key, value|...
```
hash.each_key { |key| puts "#{key}" }
```
Tương tự, phương thức **each_key** sẽ duyệt qua từng phần tử nhưng chỉ lấy khóa chứ không thể lấy được giá trị của từng khóa.
```
hash.each_value { |val| puts "#{val}" }
```
Phương thức **each_value** sẽ duyệt qua từng phần tử và lấy giá trị, không lấy khóa.
```
hash.each_pair { |k, v| puts "Key: #{k}, Value: #{v}" }
```
Phương thức **each_pair** duyệt qua từng phần tử giống hệt như phương thức **each**.
Output
```
Key: 1, Value: Germany
Key: 2, Value: Norway
Key: 3, Value: United Kingdom
Key: 4, Value: United States
1
2
3
4
Germany
Norway
United Kingdom
United States
Key: 1, Value: Germany
Key: 2, Value: Norway
Key: 3, Value: United Kingdom
Key: 4, Value: United States
```

# Xóa phần tử trong bảng băm

delete_hash.rb
```
hash = Hash.new
 
hash[1] = "Jane"
hash[2] = "Thomas"
hash[3] = "Robert"
hash[4] = "Julia"
hash[5] = "Rebecca"
 
hash.delete 4
hash.shift
 
puts hash
```
Lớp **Hash** có một số phương thức để xóa các phần tử ra khỏi bảng băm.
```
hash.delete 4
```
Phương thức **delete** sẽ xóa phần tử có khóa được chỉ định.
```
hash.shift
```
Phương thức **shift** sẽ xóa phần tử ở vị trí đầu tiên.
Output
```
{2=>"Thomas", 3=>"Robert", 5=>"Rebecca"}
```

Trộn bảng băm vào nhau

Chúng ta có thể trộn các bảng băm vào nhau để tạo thành một bảng băm mới.
mix_hashes.rb
```
hash1 = Hash.new
 
hash1[1] = "Jane"
hash1[2] = "Thomas"
 
hash2 = Hash.new
 
hash2[3] = "Robert"
hash2[4] = "Julia"
 
hash = hash1.merge hash2
puts hash
 
hash = hash1.update hash2
puts hash
```
Trong ví dụ này chúng ta sử dụng 2 phương thức là **merge** và **update**.
```
hash = hash1.merge hash2
puts hash
```
Cả 2 phương thức **merge** và **update** sẽ trộn 2 bảng băm vào nhau để tạo thành một bảng băm mới.
Output
```
{1=>"Jane", 2=>"Thomas", 3=>"Robert", 4=>"Julia"}
{1=>"Jane", 2=>"Thomas", 3=>"Robert", 4=>"Julia"}
```
