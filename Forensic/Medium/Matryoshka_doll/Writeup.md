## 🕵️‍♂️ Challenge:
### Matryoshka dolls are a set of wooden dolls of decreasing size placed one inside another.  
What's the final one? Image: **this**
### Hint:
1. Wait, you can hide files inside files? But how do you find them?
2. Make sure to submit the flag as picoCTF{XXXXX}
## 📝 Solution:
Đề cho 1 file **`dolls.jpg`**:  

<img width="297" alt="dolls" src="https://github.com/user-attachments/assets/cc7e2147-aef8-4b60-adf9-af2ca05a5e42" />  

Mình kiểm tra thì thấy đây là file PNG nên đổi lại đuôi thành **`.png`**  

Dựa vào gợi ý 1:  
`You can hide files inside files? `  

Mình đoán file ảnh này đang chứa 1 file nào đó bên trong, chạy thử `zsteg` thì thấy kết quả báo:  

![Screenshot 2025-07-06 032005](https://github.com/user-attachments/assets/0c5a4db5-0fb3-444a-98d6-6ffa2363815a)

Tức là đang có 379142 bytes dữ liệu ZIP bị giấu phía sau ảnh. Mình dùng `binwalk` để kiểm tra thêm:  

![image](https://github.com/user-attachments/assets/4d8a2ebb-3661-49ac-864c-5f788072409b)


Đây là vị trí phần zip trong file 

Lấy file zip ra và giải nén:  
```bash
dd if=dolls.png bs=1 skip=272492 of=hidden.zip
```
![image](https://github.com/user-attachments/assets/3812f1d4-98ec-4cc2-aa3e-b072531c374a)

Di chuyển vào trong thư mục **`base_images`** để kiểm tra file 2_c.jpg, ta thấy nó cũng là file ảnh bình thường, thử `zsteg` tiếp, ta được:  

![image](https://github.com/user-attachments/assets/4e23a075-6f47-4b0c-adb6-8262ce9b81ba)

Tiếp tục binwalk để lấy vị trí zip.  

![image](https://github.com/user-attachments/assets/c0ab4742-cd58-45a9-99d1-9add05fe9860)

Làm tương tự như trên, ta vào được folder chứa file `3_c.jpg`:  

![image](https://github.com/user-attachments/assets/e7b9d832-cb29-4bde-bc0e-0bc8c4523872)

`Binwalk` lần nữa và thấy vẫn còn zip:  

![image](https://github.com/user-attachments/assets/191f1b11-1481-441d-8084-769baaa76b35)

Tiếp tục cách trên, ta có `4_c.jpg`:  

![image](https://github.com/user-attachments/assets/6aa56ff7-d96b-461d-970f-f312fb825db8)

Làn này ta đã thấy được bên trong nó có thứ cần tìm:  

![image](https://github.com/user-attachments/assets/cdf9cda5-7f1f-43bf-ad31-5d3bb11a0c75)

Tiến hành giải nén và đọc file **`flag.txt`**:  

![image](https://github.com/user-attachments/assets/501a0de6-9865-4e88-897a-2801d8fe6db9)

Xong!  

> ## 🎯 Flag: ***picoCTF{bf6acf878dcbd752f4721e41b1b1b66b}***
