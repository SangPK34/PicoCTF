## 🕵️‍♂️ Challenge:
### Can you find the flag?  
***shark2.pcapng.***
### Hint:
1. Did you really find _the_ flag?  
2. Look for traffic that seems suspicious.  
## 📝 Solution:
Tải file về và thử dò string:  
```bash
strings shark2.pcapng | grep picoCTF{
```
<img width="671" height="654" alt="image" src="https://github.com/user-attachments/assets/c80cbbe3-6f18-4c2b-92b6-a6cfdafca66f" />
<br>
<br>
Ra 1 đống luôn ạ, nhma chỗ này trông ko giống dạng flag mà chúng ta hay nộp, mình cứ để tạm đây và đi theo hướng khác xem sao...  

Thử mở file bằng wireshark, sau đó thử lọc các gói có nội dung chứa cụm từ: ***picoCTF{*** để kiểm tra các yếu tố khác bằng cách nhập vào bộ lọc:  
```bash
frame contains "picoCTF"
```
<br>
<br>
<img width="1631" height="878" alt="image" src="https://github.com/user-attachments/assets/ef0ce9a6-00c3-4def-99d5-9a569629ab8d" />
<br>
<br>
Cũng ko có gì lạ lắm, vậy đổi hướng thôi...  
Dựa vào gợi ý 2, chúng ta thử kiểm tra từng kiểm tra từng loại gói tin như http, tcp, dns, vv...  
Và ở mỗi gói DNS, mình thấy tên miền có các đoạn kí tự khá lạ ở đầu:  

<img width="1646" height="728" alt="image" src="https://github.com/user-attachments/assets/ac5fecd5-55f3-4dd7-a822-5f9f285475ec" />

Mình lọc các gói tin DNS có IP đích và gốc là 2 IP mà ban đầu mình tìm được các flag giả:  

```bash
dns && ip.src == 192.168.38.104 && ip.dst == 18.217.1.57
```
<img width="1587" height="525" alt="image" src="https://github.com/user-attachments/assets/38630dbf-3d8b-4236-bdac-c5fa59abdbf7" />
<br>

> cGljb0NURntkbnNfM3hmMWxfZnR3X2RlYWRiZWVmfQ==

Rất quen rất quen, đúng đúng, là base64 đó, gộp lại đem decode xem sao :D  

<img width="519" height="617" alt="image" src="https://github.com/user-attachments/assets/f9d29593-dbd5-4aeb-8235-38c3afe527f1" />

Thử nộp thì được rồi!  

>### 🎯 Flag: ***picoCTF{dns_3xf1l_ftw_deadbeef}***
