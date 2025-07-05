## 🕵️‍♂️ Challenge:
### Download this disk image, find the key and log into the remote machine.
Note: if you are using the webshell, download and extract the disk image into **/tmp** not your home directory.  
***Download disk image***  
***`Remote machine: ssh -i key_file -p 59682 ctf-player@saturn.picoctf.net`***  
### Hint:
(None)
## 📝 Solution:
Đề cho 1 file nén và 1 link ssh, ở link ssh có ***`key_file`***, vậy chúng ta phải tìm key từ file kia.  
Giải nén file ta được file **`disk.img`**
Kiểm tra file, ta có thông tin:  

![image](https://github.com/user-attachments/assets/7b1d2201-1575-49ad-8161-b18319cabb51)

Vậy ổ này có 2 phân vùng.  
Trước tiên, tạo mapping để mount:
```bash
sudo kpartx -av disk.img
```
Tạo 2 thư mục mount point:
```bash
sudo mkdir -p /mnt/part1 /mnt/part2
```
Mount phân vùng 1 và 2
```bash
sudo mount /dev/mapper/loop0p1 /mnt/part1
sudo mount /dev/mapper/loop0p2 /mnt/part2
```
Liệt kê các file trong P1 bằng lệnh:
```bash
ls -laR /mnt/part1
```
![image](https://github.com/user-attachments/assets/1239d4d4-abbf-4906-ac0d-fb13318d25dc)  

Có vẻ ko có gì lạ lắm.  
Nhập lệnh trên với P2, ta thấy có rất nhiều file, nên ta sẽ thử tìm các file có chứa từ ***key*** trong bên trong: 
```bash
sudo find /mnt/part2 -iname '*key*'
```
![image](https://github.com/user-attachments/assets/fbec2d50-a865-46f9-b9fc-9a327000536b)

Ta thấy file **`/usr/bin/ssh-keygen`** chính là công cụ để tạo SSH key.

Nếu p2 này có ssh-keygen, rất có thể trong đây có private key hoặc public key cũ đã tạo, có thể dùng key này để đăng nhập SSH không cần password.
Tìm tất cả file trong P2 có chứa key SSH:  
```bash
sudo find /mnt/part2 -type f \( -name "id_rsa" -o -name "id_ecdsa" -o -name "id_ed25519" -o -name "
```
![image](https://github.com/user-attachments/assets/01e181cf-06b3-4ae3-8d6a-30a7d2af73a6)

Và nó là file này:
> **/mnt/part2/root/.ssh/id_ed25519**

Copy về và cấp quyền cho key rồi chạy ssh thôi:
```bash
sudo cp /mnt/part2/root/.ssh/id_ed25519 ~/  
sudo chmod 600 ~/id_ed25519
ssh -i ~/id_ed25519 -p 65301 ctf-player@saturn.picoctf.net
```

![image](https://github.com/user-attachments/assets/6cbd40a2-de08-4f5e-828f-b1a5f0a9051a)

Và BÙMMM...  

> ## 🎯 Flag: ***picoCTF{k3y_5l3u7h_b5066e83}***
