## 🕵️‍♂️ Challenge:
### Download this packet capture and find the flag.
***Download packet capture***

### Hint:
1. All we know is that this packet capture includes a chat conversation and a file transfer. 
## 📝 Solution:
Đề cho 1 file pcap, mở bằng wireshark và follow thử các gói tin, ta thấy một cuộc hội thoại giữa 2 ip `10.0.2.4` và `10.0.2.15`:

![image](https://github.com/user-attachments/assets/c18bad21-bf1d-4d80-8b68-d0beed53f35c)

Ở đây ta thấy được luôn 1 lệnh decrypt file `file.des3`:
```bash
openssl des3 -d -salt -in file.des3 -out file.txt -k supersecretpassword123
```
Nhưng file `file.des3` ở đâu?  
Cuộc hội thoại đã tiết lộ rằng họ sẽ truyền file đó qua cổng **9002**  
Lọc các cổng 9002 trong wireshark:
```markdown
tcp.port == 9002
```
Follow tcp stream một gói tin, xuất ở định dạng raw ta sẽ có được file `file.des3` với nội dung:  
> 53616c7465645f5f0c160de825c4925b6543fa6c52dc91b4487b8252966d9de6aec8508b95522f879232bf89e3066440  

Chạy lệnh giải nén đã có, ta được:  

![image](https://github.com/user-attachments/assets/187bc12e-f80f-4f3a-a004-1624daf9866e)

Và thế là xong...  

> ## 🎯 Flag: ***picoCTF{nc_73115_411_dd54ab67}***
