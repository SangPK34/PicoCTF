## 🕵️‍♂️ Challenge:
### Can you find the flag in this disk image?
Download the disk image here.
### Hint:
1. Maybe Strings could help? If only there was a way to do that?
## 📝 Solution:
Đề cho 1 file `disko-1.dd.gz`  
Giải nén, ta được 1 file `disko-1.dd`  
Dựa vào gợi ý:  

`Maybe Strings could help? If only there was a way to do that?`  

Mình chạy thử lệnh string để tìm chuỗi có dạng flag:
```bash
strings disko-1.dd | grep -i picoCTF{
```
![image](https://github.com/user-attachments/assets/0826f8f6-eee8-4431-b67c-0b4b305af23b)

Và thế là hết...
> 🎯 Flag: **`picoCTF{1t5_ju5t_4_5tr1n9_e3408eef}`**
