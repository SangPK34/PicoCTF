## 🕵️‍♂️ Challenge:
### Can you find the flag in this disk image? This time, its not as plain as you think it is!
Download the disk image ***here***.

### Hint:
1. How will you search and extract files in a partition?
## 📝 Solution:
Downfile về và giải nén, ta được file **`disko-3.dd`**  
Thử mount thẳng file để kiểm tra:
```bash
sudo mount -o loop disko-3.dd /mnt
ls /mnt
```
<img width="652" height="76" alt="image" src="https://github.com/user-attachments/assets/bd1c3aba-0e92-4d50-b7d3-4c4296cfbf02" />

Ta thấy có thư mục ***log***, tiến hành kiểm tra bên trong nó:  
```bash
 ls -l /mnt/log
```
<img width="687" height="878" alt="image" src="https://github.com/user-attachments/assets/61a35888-5e5b-4746-adcf-b600970ce44e" />

Bên trong có khá nhiều file, và như mọi khi, file gây chú ý đầu tiên là file có kí tự **Flag**, cụ thể là ***`flag.gz`***, tiến hành giải nén và mở file:  
```bash
cp /mnt/log/flag.gz .
gunzip flag.gz
cat flag
```
<img width="398" height="100" alt="image" src="https://github.com/user-attachments/assets/f2f09e7e-3b1a-4a05-9457-139d67d384bc" />

Yah, xong zòi~  

>## 🎯 Flag: ***`picoCTF{n3v3r_z1p_2_h1d3_26d4f233}`***
