## 🕵️‍♂️ Challenge:
### We found this ***packet capture*** and ***key***. Recover the flag.
### Hint:
1. Try using a tool like Wireshark.
2. How can you decrypt the TLS stream?
## 📝 Solution:
Đề cho 2 file: **`picopico.key`**, **`capture.pcap`**.  
Mở gói Pcap lên và phân tích  .

![image](https://github.com/user-attachments/assets/1323c2b4-6702-4c0c-8786-df8693f10937)

Dựa vào gợi ý 2, ta cần chú ý đến những gói tin TLS, ở đây mình thử follow TLS 1 gói nhưng ko được, nó chưa được giải mã, và giờ là lúc cần dùng đến file key kia.  
Đọc file key thì mình thấy đây có vẻ là loại RSA:  

![image](https://github.com/user-attachments/assets/6e9f4077-d972-411b-8806-5f7db466c32e)

Bây giờ click chuột phải vào 1 gói tin TLS và chọn như mình:  

![image](https://github.com/user-attachments/assets/a33d5b90-62a6-4545-b61b-1d27e6e43ea1)

Một cửa sổ được mở lên và chúng ta hãy add key file vào, cùng các giá trị liên quan:  

![image](https://github.com/user-attachments/assets/a8fde197-dcc4-43ca-8f9c-f8cdc87b7788)


> IP address: Của sever  
> Port: 443 (xem trong gói tin)  
> Protocol: http  
> Key file: chọn đường dẫn đến key file  
> pass: bỏ trống  

Rồi ok, sau đó follow TLS stream lại gói đó, và ta đã có thể đọc được:  

![image](https://github.com/user-attachments/assets/469d8862-0cf5-4f57-9192-1984fa435059)

Xong!!
> ## 🎯 Flag: ***picoCTF{honey.roasted.peanuts}***
