## 🕵️‍♂️ Challenge:
### I thought that my password was super-secret, but it turns out that passwords passed over the AIR can be CRACKED, especially if I used the same wireless network password as one in the rockyou.txt credential dump.
Use this '***pcap file***' and the rockyou wordlist. The flag should be entered in the picoCTF{XXXXXX} format.

### Hint:
1. Finding the IEEE 802.11 wireless protocol used in the wireless traffic packet capture is easier with wireshark, the JAWS of the network.
2. Aircrack-ng can make a pcap file catch big air...and crack a password.
## 📝 Solution:  

Mở file pcap đề cho bằng wireshark để kiểm tra SSID, BSSID, handshake:  

<img width="1491" height="934" alt="image" src="https://github.com/user-attachments/assets/f502b332-46e9-4d7e-9334-609fabf9d474" />

Ở đây có SSID: "Gone_Surfing", BSSID: `TPLink_4f:6a:1a` và `CenturyXinya_17:b0:be`.  
Bây giờ tìm xem có Handshake ko bằng cách lọc:
```bash
eapol
```
<img width="912" height="487" alt="image" src="https://github.com/user-attachments/assets/d70f7d22-0276-4626-95e3-47e706f13015" />
<br>
<br>
<br>
Vậy là có nhé, giờ cài đặt công cụ ***Aircrack-ng*** và tiến hành bẻ khóa bằng wordlist ***rockyou.txt***:  

```bash
aircrack-ng -w rockyou.txt -e "Gone_Surfing" wpa-ing_out.pcap
```
<br>
<img width="1015" height="796" alt="image" src="https://github.com/user-attachments/assets/c804fe1a-1537-4b26-ae85-1441a057430b" />

Rồi, key là ***mickeymouse*** nha, nhét vào flag thôi!

>### 🎯 Flag: ***picoCTF{mickeymouse}***
