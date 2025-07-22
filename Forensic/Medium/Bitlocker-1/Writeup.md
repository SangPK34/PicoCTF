## 🕵️‍♂️ Challenge:
### Jacky is not very knowledgable about the best security passwords and used a simple password to encrypt their BitLocker drive. See if you can break through the encryption!
Download the disk image ***here***
### Hint:
1. Hash cracking  
## 📝 Solution:
Downfile về và giải nén, ta được file `bitlocker-1.dd`    
Theo đề bài và gợi ý thì bài này chúng ta dùng brute-force để dò mật khẩu của Jacky.  
Ở đây mình dùng công cụ John, mình clone về và build nó:  
> https://github.com/openwall/john.git

Bắt đầu bằng việc tạo phân vùng mount:
```bash
sudo mkdir -p /mnt/bitlocker
sudo mkdir -p /mnt/bitlocker-mount
```
Bây giờ trong công cụ John, ta tới vị trí: ***`john/run`***, sẽ có file `bitlocker2john.py`  
Chạy file python này để tạo file hash:
```bash
python3 bitlocker2john.py ~/bitlocker-1.dd > ~/bitlocker.hash
```
Ta sẽ thấy nó tìm được một số hash như:
`The following hashes were found:  
$bitlocker$2$16$2b71884a0ef66f0b9de049a82a39d15b$1048576$12$00be8a46ead6da0106000000$60$a28f1a60db3e3fe4049a821c3aea5e4ba1957baea68cd29488c0f3f6efcd4689e43f8ba3120a33048b2ef2c9702e298e4c260743126ec8bd29bc6d58  
...`
Bây giờ để brute-force, ta phải có file wordlist, phổ biến nhất đó là file ***`rockyou.txt`***, ta cần tải nó:  
```bash
wget https://github.com/brannondorsey/naive-hashcat/releases/download/data/rockyou.txt
```
Sau khi có wordlist, tiến hành brute force:  
```bash
./john/run/john --format=bitlocker --wordlist=rockyou.txt bitlocker.hash
```
Tốc độ khá chậm, nhưng cuối cùng cũng có kết quả, mật khẩu là: "**jacqueline**"
Bây giờ cần giải mã file bitlocker sang file trung gian:  
```bash
sudo dislocker -V ~/CTF/bitlocker-1.dd -ujacqueline -- /mnt/bitlocker
```
Mount file vừa giải mã:  
```bash
sudo mount -o ro,loop /mnt/bitlocker/dislocker-file /mnt/bitlocker-mount
```
Kiểm tra bên trong, ta thấy có file `flag.txt`, mở nó và lấy cờ thui:  
<img width="662" height="119" alt="image" src="https://github.com/user-attachments/assets/54318f56-8850-4871-af4a-abc28a7e0136" />

>### 🎯 Flag: ***picoCTF{us3_b3tt3r_p4ssw0rd5_pl5!_3242adb1}***
