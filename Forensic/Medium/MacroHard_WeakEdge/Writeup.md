## 🕵️‍♂️ Challenge:
### I've hidden a flag in this file. Can you find it? 
***Forensics is fun.pptm***
### Hint:
(None)
## 📝 Solution:
File `.pptm` là file powerpoint có chứa macro, vậy thì chúng ta thử kiểm tra macro của nó trong công cụ ***Visual Basic*** tích hợp sẵn trong PPT:  

<img width="1334" height="443" alt="image" src="https://github.com/user-attachments/assets/6e3837b4-4f6a-4aa3-9d9b-843cbe62a139" />

<img width="844" height="373" alt="image" src="https://github.com/user-attachments/assets/a779f069-8989-446b-8f99-315d2ba57f7b" />
<br>
<br>
Với cái tên bài thì mình tưởng nó có gì đó trong phần macro, nhưng khi mở lên thì có vẻ là mấy dòng vô nghĩa thôi...  
Mình thử strings file pptm này thì thấy được cả cấu tạo bên trong file, gồm rất nhiều file nhỏ:  

<img width="636" height="702" alt="image" src="https://github.com/user-attachments/assets/aaf0e6c8-7141-4bec-b32b-0012074c6d8e" />
<br>
<br>
Mình đổi đuôi file thành `.zip` rồi giải nén.  

<img width="817" height="359" alt="image" src="https://github.com/user-attachments/assets/cba67cbf-deee-4781-9c16-d854433803d6" />
<br>
<br>
Sau khi còng lưng ra mò từng ngóc ngách thì mình phát hiện có file `\Forensics is fun\ppt\slideMasters\hidden"` khá đáng nghi, kiểm tra thì nó là 1 dãy kí tự:  

> Z m x h Z z o g c G l j b 0 N U R n t E M W R f d V 9 r b j B 3 X 3 B w d H N f c l 9 6 M X A 1 f Q

Khả năng đây là Base64, thử giải mã thì được flag thật :))  

<img width="781" height="620" alt="image" src="https://github.com/user-attachments/assets/9bafcf68-3f19-48dc-a592-c95ec7a9c8b4" />

Okla!!  

>### 🎯 Flag: ***picoCTF{D1d_u_kn0w_ppts_r_z1p5}***
