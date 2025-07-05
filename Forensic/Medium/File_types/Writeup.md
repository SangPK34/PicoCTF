## 🕵️‍♂️ Challenge:
### This file was found among some files marked confidential but my pdf reader cannot read it, maybe yours can.
You can download the file from **here**.
### Hint:
1. Remember that some file types can contain and nest other files
## 📝 Solution:
Đề cho file **`Flag.pdf`** nhưng có vẻ bị lỗi do ko đúng định dạng nên mình kiểm tra:  

![image](https://github.com/user-attachments/assets/b1cf73b4-8f22-4d51-a460-125d45ec0fee)

Vậy đây là 1 shell archive chứ ko phải pdf. Chạy thử lệnh sau để xem 30 dòng đầu của file:
```bash
cat Flag.pdf | head -n 30
```
![image](https://github.com/user-attachments/assets/af4700fb-c589-44fc-81d3-05c009fbd2aa)

Ta thấy có dòng
> 1092 -rw-r--r-- flag

Tức là khi chạy nó sẽ giải nén ra file flag. Vậy ta thử chạy nó:
```bash
sh Flag.pdf
```
![image](https://github.com/user-attachments/assets/4c9892cd-c311-4bee-aabd-cb1e18b95679)

Vậy là xong, bây giờ kiểm tra loại file `flag` vừa giải nén:
>pswsl@PS16:~/sangdz$ file flag  
>flag: current ar archive

Như vậy đây là 1 file bị nén dạng **ar**, giải nén nó:
```bash
ar x flag
```
Kiểm tra lại loại file:  

![image](https://github.com/user-attachments/assets/b613d86d-cadc-464d-8e0f-6cf80f154ac5)

Lần này là kiểu **cpio**, giải nén báo bị trùng file đang có nên mình đổi tên thành **flagg** rồi giải nén:  
```bash
cpio -id < flagg
```
![image](https://github.com/user-attachments/assets/bb75f3e0-7682-485c-abfa-739cbc9a5521)

Sau khi giải nén ta được file **flag** tiếp, và kiểm tra thì lần này là file **bzip2**. Lại giải nén:  
```bash
bunzip2 flag
```
![image](https://github.com/user-attachments/assets/6f12125e-4de5-4913-bad3-d51be42a7ca6)

Lần này là file **gzip**...Mệt vãiii. Nhưng ko sao, đổi tên thành **`flag.gz`** và tiếp tục giải nén:
```bash
gunzip flag.gz
```
![image](https://github.com/user-attachments/assets/55846f94-9138-4f0b-9ef4-c4be3b546dfc)

Lần này đến **Lzip** :)), thôi cố đi:
```bash
lzip -d flag
```
![image](https://github.com/user-attachments/assets/a573504d-4b69-47ec-a1fa-73071fb84ffa)

Đùa, lại **Lz4**
```bash
lz4 -d flag.out flag
```
![image](https://github.com/user-attachments/assets/5250edff-4233-4bad-adc1-23e88423687f)

Mé, **LZMA** j nữa, bóc hành từng lớp à :)). Mình lại thêm đuôi file thành **.lzma** rồi triển tiếp thôi. 
```bash
lzma -d flag.lzma
```
![image](https://github.com/user-attachments/assets/ec09f9c8-e193-47c3-af91-ca239b50b447)

Vãi dắm, nữa, **lzop** thưa quý vị, thêm đuôi file **.lzo** rồi lết tiếp thôi, hành quá trời hành, lớp quá trời lớp, bóc bóc cay cả mắt.
```bash
lzop -d flag.lzo
```
![image](https://github.com/user-attachments/assets/669d0d15-010b-4787-b252-b22be80b3134)

Thôi tịnh tâm, lần này là **lzip**, giải nén là ko ngừng bỏ cuộc... Thêm đuôi **.lz** và bóc tiếp.
```bash
lzip -d flag.lz
```
![image](https://github.com/user-attachments/assets/6e98c569-d635-4666-b55f-565783a422a0)

Đùa, đ nói nữa. Thêm đuôi **.xz** rồi bóc:
```bash
xz -d flag.xz
```
![image](https://github.com/user-attachments/assets/971d8f37-57ea-4eb4-9f19-52bf9cb05bd7)

Húuuuu, bóc tới rễ rồi. Cat thôiii:
![image](https://github.com/user-attachments/assets/8d1119a2-9225-42b6-93af-0f0f1b907793)

Là 1 chuỗi Hex!
>7069636f4354467b66316c656e406d335f6d406e3170756c407431306e5f
>6630725f3062326375723137795f37396230316332367d0a

Decode thôiii
Và BÙMMM...  

> ### 🎯 Flag: ***picoCTF{f1len@m3_m@n1pul@t10n_f0r_0b2cur17y_79b01c26}***
