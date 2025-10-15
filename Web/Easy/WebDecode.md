## 🕵️‍♂️ Challenge:
### Do you know how to use the web inspector?  
Start searching **here** to find the flag

### Hint:
1. Use the web inspector on other files included by the web page.
2. The flag may or may not be encoded.  
## 📝 Solution:
Đề cho 1 trang web có giao diện:  

Đầu tiên là tab HOME:  

<img width="1890" height="972" alt="image" src="https://github.com/user-attachments/assets/1aeefce1-c6a5-4dcd-8841-705d12607e5a" />

Tiếp theo là tab ABOUT:  

<img width="1752" height="899" alt="image" src="https://github.com/user-attachments/assets/c88b09cc-49cf-47bc-9e3d-3c1eec9b72c8" />
 
Tab CONTACT:  

<img width="1615" height="769" alt="image" src="https://github.com/user-attachments/assets/8e2bc57e-bb5e-4d3f-860a-568156e06d4c" />

Với các thông điệp hiển thị, khả nghi nhất là tab ABOUT, kiểm tra source code của trang đó bằng ctrl U:  

<img width="1027" height="882" alt="image" src="https://github.com/user-attachments/assets/707be96e-3f2c-417b-9a6e-6a2bf798b68d" />

Vậy là 1 chuỗi Base64, đem decode:  

<img width="840" height="649" alt="image" src="https://github.com/user-attachments/assets/cf899cbf-aaab-4c80-9dc7-d0bae349a577" />

Xong...  

> ###🎯 Flag: **`picoCTF{web_succ3ssfully_d3c0ded_df0da727}`**
