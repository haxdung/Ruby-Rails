# Ruby – Giới thiệu về ngôn ngữ Ruby

# Ruby

Ruby là một ngôn ngữ lập trình động, phản xạ, hướng đối tượng. Tác giả của ngôn ngữ Ruby là một lập trình viên người Nhật tên là Yukihiro Matsumoto. Ruby được giới thiệu lần đầu vào năm 1995.

Ruby hỗ trợ hầu hết các mô hình lập trình truyền thống, bao gồm lập trình hướng đối tượng, lập trình phản xạ, lập trình mệnh lệnh… Ruby được lấy cảm hứng từ Perl, Smalltalk, Effiel và Lisp.

Website chính thức của Ruby có địa chỉ ruby-lang.org.

# Trình thông dịch Ruby

Trong series này mình dùng Ruby phiên bản 2.2.4 trên Windows. Bạn có thể tải và cài đặt Ruby cho Windows tại địa chỉ http://rubyinstaller.org/, Khi cài bạn nhớ check lựa chọn cho trình cài đặt tự động gán đường dẫn đến thư mục bin trong biến PATH luôn cho tiện.

Sau khi cài xong, bạn mở Command Prompt (cmd) lên và chạy lệnh **irb** để mở trình thông dịch Ruby, màn hình cùng với dấu nhắc lệnh của Ruby có dạng như sau:

```
C:\User\xRuby> irb
irb(main):001:0>
```

Từ đây bạn có thể gõ các lệnh trong Ruby.

```
irb(main):001:0> puts RUBY_VERSION
2.2.4 => nil
```


Ở trên chúng ta chạy lệnh puts, lệnh này sẽ in một đoạn text ra màn hình, ở đây chúng ta in hằng số RUBY_VERSION, hằng số này cho biết phiên bản Ruby mà chúng ta sử dụng.

# Viết code Ruby trong file

Ngoài cách chạy Ruby trực tiếp từ trình thông dịch thì chúng ta có thể viết code Ruby trong các file script riêng rồi trình thông dịch sẽ chạy đoạn code trong file đó. Bạn chỉ cần tạo một file text, viết code Ruby trong đó rồi lưu lại với phần mở rộng là **.rb**.
hello.rb
puts "Hello world"

Đoạn code trên sẽ in chuỗi Hello world ra màn hình.

```
C:\Project\Ruby>first.rb 
Hello world
```

Để chạy file **.rb** thì bạn mở cmd lên rồi trỏ đến thư mục chứa file này (bằng lệnh cd) sau đó gõ vào tên file là xong.
