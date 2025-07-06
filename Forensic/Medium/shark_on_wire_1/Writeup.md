## 🕵️‍♂️ Challenge:
### We found this *packet capture*. Recover the flag.
### Hint:
1. Try using a tool like Wireshark
2. What are streams?
## 📝 Solution:
Đề cho 1 file **`capture.pcap`**, ta mở bằng wireshark và tiến hành follow các gói tin bên trong.  
Mình thử sort ip rồi follow thì thấy giữa 2 ip `10.0.0.2` và `10.0.0.12` có 1 thông điệp rất khả nghi:  

![image](https://github.com/user-attachments/assets/1c0f15b3-53f7-45b2-9843-b394538b5d2a)

Nghi cái gì nữa, flag đó -.-

> ## 🎯 Flag: ***picoCTF{StaT31355_636f6e6e}***
