## 🕵️‍♂️ Challenge:
### Figure out how they moved the ***flag***.

### Hint:
1. What are some other ways to hide data?
## 📝 Solution:
Đề cho 1 file Pcap, mở bằng wireshark.  
Sau khi lướt qua vài gói tin và ko thấy có gì đặc biệt, ta để ý tới đề bài, đó là **TFTP** - **Giao thức truyền tệp đơn giản**.

![Screenshot 2025-07-06 064346](https://github.com/user-attachments/assets/bc8bdf92-9eb9-4d10-9530-0f6c63e2948f)

Thực hiện export file ra TFTP, ta thấy nó có các file:  

![image](https://github.com/user-attachments/assets/9efb9599-4e84-4267-9d45-f1a1e85d34a8)

Chọn save all để lưu hết chỗ file trên, sau đó kiểm tra các file.  

Trong file `Instructions.txt` là 1 chuỗi:
> GSGCQBRFAGRAPELCGBHEGENSSVPFBJRZHFGQVFTHVFRBHESYNTGENAFSRE.SVTHERBHGNJNLGBUVQRGURSYNTNAQVJVYYPURPXONPXSBEGURCYNA

Đây là 1 chuỗi ROT 13, đem giải mã ta thu được:
> TFTPDOESNTENCRYPTOURTRAFFICSOWEMUSTDISGUISEOURFLAGTRANSFER.FIGUREOUTAWAYTOHIDETHEFLAGANDIWILLCHECKBACKFORTHEPLAN  

Tức là **"TFTP DOESN'T ENCRYPT OUR TRAFFIC, SO WE MUST DISGUISE OUR FLAG TRANSFER. FIGURE OUT A WAY TO HIDE THE FLAG AND I WILL CHECK BACK FOR THE PLAN."**  

Tạm dịch: ***"TFTP không mã hóa lưu lượng của chúng ta, vì vậy chúng ta phải che giấu việc truyền cờ. Hãy tìm cách để giấu cờ và tôi sẽ quay lại để kiểm tra kế hoạch."***  

Tiếp đến file `plan`, ta mở bằng notepad và cũng thu được chuỗi ROT13:  
> VHFRQGURCEBTENZNAQUVQVGJVGU-QHRQVYVTRAPR.PURPXBHGGURCUBGBF

Đi giải mã, ta được: 
> IUSEDTHEPROGRAMANDHIDITWITH-DUEDILIGENCE.CHECKOUTTHEPHOTOS

Tức là: **"I USED THE PROGRAM AND HID IT WITH-DUE DILIGENCE. CHECK OUT THE PHOTOS."**  
Tạm dịch: ***"Tôi đã sử dụng chương trình và giấu nó một cách cẩn trọng. Hãy xem các bức ảnh."***

Còn file `Program.deb`, ta kiểm tra thì thấy nó chứa các mục con: Debian binary package, with control.tar.gz , data compression xz, giải nén nó:
```bash
ar x program.deb
```

![image](https://github.com/user-attachments/assets/761a32b4-bf47-4370-9d40-5a43b9b41c98)
  
Tiến hành giải nén từng lớp, ta thấy bên trong gồm khá nhiều file hoặc thư mục có tên **`Steghide`**  
Mình tìm thử thì nó là 1 công cụ steganography giúp ẩn, xuất dữ liệu ẩn từ file.  
Chạy thử:
```bash
steghide extract -sf picture1.bmp
steghide extract -sf picture2.bmp
steghide extract -sf picture3.bmp
```
Mỗi lệnh nó sẽ yêu cầu nhập ***passphrase***.  

Ở lời nhắn trên:  
`IUSEDTHEPROGRAMANDHIDITWITH-DUEDILIGENCE.CHECKOUTTHEPHOTOS` ta thấy cụm từ ***DUEDILIGENCE*** khá đáng nghi, thử dùng làm mật khẩu thì pass cái ảnh `picture3.bmp`

![image](https://github.com/user-attachments/assets/55334353-1290-4e89-b951-35753c94a080)

Yeah!!!
> ## 🎯 Flag: ***picoCTF{h1dd3n_1n_pLa1n_51GHT_18375919}***
