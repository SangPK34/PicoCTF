## 🕵️‍♂️ Challenge:
### Can you find the flag in this disk image? The right one is Linux! One wrong step and its all gone!
Download the disk image ***here***.
### Hint:
1. How can you extract/isolate a partition?
## 📝 Solution:
Đề cho 1 file **`disko-2.dd`**, kiểm tra thì nó đúng là file disk với nhiều phân vùng khác nhau, và theo đề bài thì chúng ta nên tập trung phân tích vào phân vùng Linux.  
Nhưng trước khi đi vào phân tích từng ngóc ngách trong đó, sao chúng ta ko thử các cách đơn giản, và cụ thể ở đây là dò strings.  
Mình sẽ thử tìm các chuỗi có kí tự ***picoCTF{*** bằng lệnh:  
```bash
strings disko-2.dd | grep 'picoCTF{'
```
![image](https://github.com/user-attachments/assets/fd6e2ba7-a5d0-4535-9abd-3bcb7759d545)
<br>
<br>
Ròi, ra 1 nồi luôn :D, thử tới bao giờ đây...
Với gợi ý từ đề bài, ta đoán nó ở phân vùng linux. Bây giờ hãy kiểm tra xem nó có những phân vùng nào: 
```bash
fdisk -l disko-2.dd
```
<br>
<br>

![image](https://github.com/user-attachments/assets/8ec0baa5-29f5-4dc9-85b8-bcc7a02ec995)
<br>
<br>
Vậy là chỉ có duy nhất P1 là Linux, bây giờ hãy trích nguyên cái P1 thành 1 disk mới rồi dò string lại lần nữa nhé!  
```bash
dd if=disko-2.dd of=p1.img bs=512 skip=2048 count=51200
strings -a p1.img | grep picoCTF{
```
<br>
<br>

![image](https://github.com/user-attachments/assets/3714ae96-f445-4e46-82df-50d6224aef09)

Chỉ có duy nhất 1 flag lòi ra, và đúng rồi đó, là nó, đáp án đó!
> ## 🎯 Flag: ***picoCTF{4_P4Rt_1t_i5_a93c3ba0}***
