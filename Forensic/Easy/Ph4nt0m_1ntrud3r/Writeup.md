## 🕵️‍♂️ Challenge:
### A digital ghost has breached my defenses, and my sensitive data has been stolen! 😱💻 Your mission is to uncover how this phantom intruder infiltrated my system and retrieve the hidden flag.
To solve this challenge, you'll need to analyze the provided PCAP file and track down the attack method. The attacker has cleverly concealed his moves in well timely manner. Dive into the network traffic, apply the right filters and show off your forensic prowess and unmask the digital intruder!
Find the PCAP file here **Network Traffic PCAP file** and try to get the flag.
### Hint:
1. Filter your packets to narrow down your search.  
2. Attacks were done in timely manner.  
3. Time is essential.  
## 📝 Solution:
Đề cho 1 file Pcap, ta mở bằng wireshark.    
Dựa vào gợi ý, ta chú ý tới yếu tố thời gian, tiến hành sort các gói tin theo thời gian tăng dần, ta thấy từ gói tin 22 xuống, đều chứa 1 chuỗi base64:    

![image](https://github.com/user-attachments/assets/c53e64e7-0bb8-42ff-a084-22103f1e4cec)

Thu thập và decode tất cả.  
![image](https://github.com/user-attachments/assets/08b5c816-e3b1-40ca-a443-38b5e9bf3900)

Và thế là có cờ!
> 🎯 Flag: **`picoCTF{1t_w4snt_th4t _34sy_tbh_4r_d4b57909}`**
