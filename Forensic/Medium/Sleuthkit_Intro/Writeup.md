## 🕵️‍♂️ Challenge:
### Download the disk image and use *mmls* on it to find the size of the Linux partition. Connect to the remote checker service to check your answer and get the flag.
Note: if you are using the webshell, download and extract the disk image into `/tmp` not your home directory.
***Download disk image***
Additional details will be available after launching your challenge instance.
### Hint:
(None)
## 📝 Solution:
Tải về và giải nén, ta được file `disk.img`, theo đề bài, ta kiểm tra file này bằng ***mmls***, trước tiên phải cài đặt bộ công cụ **sleuthkit**   
```bash
sudo apt install sleuthkit
```
Sau khi cài đặt, chạy:  
```bash
mmls disk.img
```
<img width="886" height="238" alt="Screenshot 2025-07-23 190222" src="https://github.com/user-attachments/assets/1f1eef3d-6075-4f38-a161-bafe83d314a9" />

Với đề bài, ta chú ý đến giá trị **Length** của phân vùng **Linux** là ***0000202752***.  

Đề cho 1 địa chỉ netcat, truy cập thì nó đòi giá trị length đó, chỉ cần nhập vô là xong:  

<img width="794" height="157" alt="Screenshot 2025-07-23 190159" src="https://github.com/user-attachments/assets/3d878e27-267d-4e0b-acf6-87fef820418e" />

Rồi đó!
>### 🎯 Flag: ***picoCTF{mm15_f7w!}***
