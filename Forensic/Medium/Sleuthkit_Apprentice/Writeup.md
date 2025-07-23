## 🕵️‍♂️ Challenge:
### Download this disk image and find the flag.  
Note: if you are using the webshell, download and extract the disk image into **/tmp** not your home directory.  
***Download compressed disk image***
### Hint:  
(None)
## 📝 Solution:
Tải về và giải nén, ta được file `disk.flag.img`.  

Đem đi phân tích, bắt đầu bằng các lệnh đơn giản như dò string, với cụm "picoCTF" thì không thấy gì, nhưng "flag" thì lại trả về rất rất nhiều, hơi khó để tìm.  
Kiểm tra bằng lệnh:  
```bash
fdisk -l disk.flag.img
```
<br>
<img width="853" height="320" alt="image" src="https://github.com/user-attachments/assets/63befb99-9285-43b4-aab3-41fe6214daac" />
<br>
<br>
Ta thấy đĩa có 3 phân vùng, và thường thì ta phân vùng 1 chứa các file hệ thống, phân vùng 2 là swap nên ko cần quan tâm lắm, vậy nên chúng ta sẽ tiến hành phân tích phân vùng 3 trước.  
Tiến hành mount p3:  

```bash
mkdir -p /tmp/disk_mount
sudo losetup -P /dev/loop0 disk.flag.img
sudo mount /dev/loop0p3 /tmp/disk_mount
```
<img width="412" height="412" alt="image" src="https://github.com/user-attachments/assets/8699b9c6-4236-4098-b07d-a79e40cb8d09" />
<br>
<br>
Kiểm tra thì đây là 1 phân vùng root, đáng để kiểm tra.  
Ở đây mình kiểm tra lịch sử dòng lệnh của đĩa này bằng cách tìm file `.ash_history` nằm trong folder `root`:  

```bash
sudo ls -la /tmp/disk_mount/root
```
<img width="426" height="120" alt="image" src="https://github.com/user-attachments/assets/4234ac38-692c-4bf3-b10d-61e766256f1a" />
<br>
<br>
Kiểm tra nội dung file, ta thấy các lệnh khá quan trọng:  
<br>
<img width="380" height="273" alt="image" src="https://github.com/user-attachments/assets/f9cba4df-395a-4abf-988e-6aa097018c0e" />
<br>
<br>
Từ history này ta thấy:  
1. nano flag.txt - Tạo file flag.txt
2. iconv -f ascii -t utf16 flag.txt > flag.uni.txt - Convert sang UTF-16
3. shred -zu flag.txt - Xóa an toàn file flag.txt
<br>
Bây giờ ta kiểm tra xem file `flag.uni.txt` có còn tồn tại không trong thư mục **my_folder**:

```bash
sudo ls -la /tmp/disk_mount/root/my_folder
```
<img width="416" height="101" alt="image" src="https://github.com/user-attachments/assets/316eab1a-43c6-40b8-b2aa-ff79cde6b1ec" />

Như vậy là vẫn còn, giờ thì cat nó:  
```bash
sudo cat /tmp/disk_mount/root/my_folder/flag.uni.txt
```
Xong!  
<img width="418" height="54" alt="image" src="https://github.com/user-attachments/assets/ad0aed95-1a5c-4121-83c1-dd398ab11275" />
<br>
<br>
>### 🎯 Flag: ***picoCTF{by73_5urf3r_adac6cb4}***
