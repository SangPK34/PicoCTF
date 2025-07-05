## 🕵️‍♂️ Challenge:
### Download this disk image and find the flag.
Note: if you are using the webshell, download and extract the disk image into **/tmp** not your home directory.
***Download compressed disk image***
### Hint:
(None)
## 📝 Solution:
Đề cho 1 file nén, giải nén ta được file **`disk.flag.img`**  
Kiểm tra file, ta được thông tin:  

![image](https://github.com/user-attachments/assets/deada2b0-4f38-48d2-858e-d2f92348faf1)  

Phân vùng 1 và 3 là Linux, có thể chứa flag, còn phân vùng 2 là Swap, thường không quan trọng.  
Tiến hành tạo device mapper cho từng phân vùng bằng lệnh:  
```bash
sudo kpartx -av disk.flag.img
```
![image](https://github.com/user-attachments/assets/61c5ee35-ce80-460d-b0d4-73a6bf5b45c0)

Bây giờ kiểm tra partition 1:  
Mount partition 1:
```bash
sudo mkdir -p /mnt/part1
sudo mount /dev/mapper/loop0p1 /mnt/part1
```
Thử tìm tất cả các file có trong P1:
```bash
find /mnt/part1
```
![image](https://github.com/user-attachments/assets/14306556-d2de-4761-8989-2a94a478e42c)

Kết quả thấy ko có gì đặc biệt. Thử tìm ở P3 xem sao:
```bash
sudo mkdir -p /mnt/part3
sudo mount /dev/mapper/loop0p3 /mnt/part3
sudo find /mnt/part3
```
Ta thấy quá nhiều file được liệt kê, vậy nên ta thử lọc tìm các file có từ ***flag*** trong tên:  
```bash
sudo find /mnt/part3 -type f -iname '*flag*'
```
![image](https://github.com/user-attachments/assets/260bfab7-a66a-434a-a4cb-e999ef103773)

Ố, có file rồi, copy file này ra ngoài để giải mã thử:
```bash
sudo cp /mnt/part3/root/flag.txt.enc ./
```
Kiểm tra thử định dạng file, ta thấy file này đã bị mã hóa bằng openssl, cần mật khẩu để giải.  

![image](https://github.com/user-attachments/assets/cb0b2666-53c9-4fbf-81d4-32d9e7a382b7)

Ta chạy lệnh sau để tìm trong P3 các file có nội dung chứa từ ***flag***:
```bash
sudo grep -Ri --color 'flag' /mnt/part3 2>/dev/null
```
![image](https://github.com/user-attachments/assets/c9f4e20d-f62e-44d6-b2c3-10b94a003e6c)

Ôi chà, trong cái file chứa lịch sử dòng lệnh, ta thấy có người đã chạy lệnh này, và mật khẩu họ dùng là: **`unbreakablepassword1234567`**

Giờ ta chỉ cần decrypt file flag.txt.enc:
```bash
openssl enc -aes256 -d -salt -in flag.txt.enc -k unbreakablepassword1234567 -nopad
```
![image](https://github.com/user-attachments/assets/3cc5fb5b-3923-4f0a-b893-ec0aabb01bbe)
Mệt quá...
> ### 🎯 Flag: `picoCTF{h4un71ng_p457_0a710765}`
