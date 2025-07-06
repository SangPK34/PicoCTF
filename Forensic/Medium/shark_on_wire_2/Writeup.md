## 🕵️‍♂️ Challenge:
### We found this *packet capture*. Recover the flag that was pilfered from the network.
### Hint:
(None)
## 📝 Solution:
Đề cho file Pcap, mở bằng wireshark để phân tích các gói tin.  
Sau 7749 cách thử và bị lừa bởi khá nhiều mảnh flag giả, mình mới để ý tới gói tin thứ `1104`  

Thông điệp của nó là **start**  

![image](https://github.com/user-attachments/assets/af26a490-51ef-4381-a341-cddf188dc24f)
<br>
<br>
<br>
Và gói tin thứ `1303` với thông điệp là **end**  

![image](https://github.com/user-attachments/assets/31da6f74-72a7-4cdb-a48f-5983c17cd88e)

Với thông điệp **start** và **end** thì mình nghĩ là giữa 2 gói tin này sẽ có những gói tin khác ẩn chứa điều gì đó có ích.  
Quan sát điểm chung giữa 2 gói này, thì mình thấy là chung IP đích, chung cổng nguồn, cổng đích.  
Nhưng lục lọi lại thì mình thấy cổng đích `10.0.0.1`  xuất hiện khá nhiều ngoài khoảng giữa 2 gói này và cũng chứa nhiều nội dung rác  
Còn cổng nguồn thì mình lọc bằng lệnh:
```bash
tcp.srcport == 5000 || udp.srcport == 5000
```
Quan sát thấy cũng gần như cũng toàn là gói rác nên mình lọc tiếp các gói có cổng đích là 22:
```bash
tcp.dstport == 22 || udp.dstport == 22
```
![image](https://github.com/user-attachments/assets/7a6bb2f0-3957-4f1e-a007-67af24d2baa3)

Trông cũng khá gọn gàng ấy chứ, hầu như có mỗi cổng nguồn là khác nhau.  
Để ý kĩ các cổng nguồn thì đều xuất phát bằng 5, còn các vế sau thì ko có quy luật nào.  
Vậy nếu bỏ đi các số 5 ở đầu thì sao ? Trừ 2 gói `start` và `end` thì ta có các số  

> **112, 105, 99, 111, 67, 84, ...**

Chà, hình như là ASCII, đem giải mã thử mấy số đầu:

![image](https://github.com/user-attachments/assets/17ac6826-998b-4e0f-aa70-792fee116c15)

Vậy là chúng ta biết phải làm gì tiếp rồi đấy :D  
Đem giải mã nốt các số còn lại, ta sẽ được flag:  

![image](https://github.com/user-attachments/assets/c05dc572-e9d9-4417-9f0b-e9118f271b46)

Done!! 

> ## 🎯 Flag: ***picoCTF{p1LLf3r3d_data_v1a_st3g0}***
