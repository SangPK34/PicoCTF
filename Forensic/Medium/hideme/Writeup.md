## 🕵️‍♂️ Challenge:
### Every file gets a flag.
The SOC analyst saw one image been sent back and forth between two people. They decided to investigate and found out that there was more than what meets the eye **here**.
### Hint:
(None)
## 📝 Solution:
Đề cho 1 tấm ảnh **`flag.png`**

![flag](https://github.com/user-attachments/assets/6a31ad47-d141-479d-bd5b-2aaff82e2d8b)

Thử chạy `zsteg`và quan sát:  

![image](https://github.com/user-attachments/assets/7e02d3b4-2d2c-4954-8aa9-95df162be51b)

Ta thấy Ảnh này có nhúng thêm ZIP sau đoạn IEND, trong ZIP đó có folder `secret` chứa file `flag.png.`  
Giải nén bằng **Binwalk**, sau đó liệt kê các file trong thư mục binwalk đã xuất, ta thấy có file **`9B3B`**, kiểm tra thử thì đúng là file zip.  
Giải nén nó, ta được folder **`Secret`** chứa flag.

![image](https://github.com/user-attachments/assets/92b927c7-7dbe-43dc-8d1e-78cdfd560c39)

Mở file **`Flag.png`** lên ta được:  

![image](https://github.com/user-attachments/assets/d9663f29-17cb-4bd3-b022-1cc8ea3e46ae)

> ### 🎯 Flag: `picoCTF{Hiddinng_An_imag3_within_@n_ima9e_82101824}`
