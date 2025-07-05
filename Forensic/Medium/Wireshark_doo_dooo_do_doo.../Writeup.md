## 🕵️‍♂️ Challenge:
### Can you find the flag? 
***shark1.pcapng***

### Hint:
(None)
## 📝 Solution:
Mở file bằng wireshark, khi thử follow các gói tin, ta bắt gặp một chuỗi giống flag khi đang ở `tcp.stream eq 5`  
>cvpbPGS{c33xno00_1_f33_h_qrnqorrs}

![image](https://github.com/user-attachments/assets/7566bd40-fc79-4238-8602-94bd5bb1545b)

Có vẻ đây là loại mã hóa ROT13, đem đi decode thử. Và BÙMMM...  

![image](https://github.com/user-attachments/assets/6fe1efe8-2822-4b7e-b879-69f6e8a270cf)

> ## 🎯 Flag: ***picoCTF{p33kab00_1_s33_u_deadbeef}***
