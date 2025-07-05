## 🕵️‍♂️ Challenge:
### Can you handle APKs?
Download the android apk **here**.
### Hint:
1. Did you know you can **unzip** APK files?
2. Now you have the whole host of shell tools for searching these files.
## 📝 Solution:
Đề cho 1 file `mobpsycho.apk`  
Dựa vào gợi ý 1, ta tiến hành đổi đuôi file thành `.zip` và giải nén như thường, được folder `mobpsycho`  
Dựa vào gợi ý 2, ta cần chạy lệnh tìm kiếm 1 file nào đó trong folder, ở đây mình nghĩ là các tệp chứa từ khóa liên quan như: `"flag", "CTF", "Pico", ...`  

Chạy thử lệnh:  

```bash
find mobpsycho -type f -iname "*flag*"
```
![image](https://github.com/user-attachments/assets/05b754c6-373c-4dab-a9e3-12bc5340deab)

Vậy là có vị trí file cần tìm, mở thử nó:  

![image](https://github.com/user-attachments/assets/25c14a9a-dc40-4378-9c13-18002f2d316b)

Ta được đoạn mã Hex: `7069636f4354467b6178386d433052553676655f4e5838356c346178386d436c5f35326135653264657d`  
Đem decode ta thu được flag:


> ### 🎯 Flag: `picoCTF{ax8mC0RU6ve_NX85l4ax8mCl_52a5e2de}`
