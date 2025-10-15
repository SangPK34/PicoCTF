## 🕵️‍♂️ Challenge:
### My dog-sitter's brother made this website but I can't get in; can you help?  
***login.mars.picoctf.net***
### Hint:
(None)
## 📝 Solution:

<img width="1315" height="846" alt="image" src="https://github.com/user-attachments/assets/44c2a380-b1b5-4c4e-a4e1-8812c2fe8fe2" />

Đề cho 1 web yêu cầu đăng nhập, mình thử nhập bừa thì nó chỉ báo incorrect, thử SQL injection cũng ko được, nên mình thử tìm trong devtool xem sao.  

Thì ở tab Source, trong file `index.js`, mình thấy có chuỗi base64 trong 1 hàm gì đó.  

<img width="1007" height="633" alt="image" src="https://github.com/user-attachments/assets/6cce6a23-b5bc-4adf-9ad0-c5718ac74b0c" />

Chưa cần hiểu logic hàm, mình đem decode thì được flag:  

<img width="803" height="664" alt="image" src="https://github.com/user-attachments/assets/950a11ce-cd1e-4f5a-a936-2f365b2669b2" />

:D  

> ### 🎯 Flag: **`picoCTF{53rv3r_53rv3r_53rv3r_53rv3r_53rv3r}`**
