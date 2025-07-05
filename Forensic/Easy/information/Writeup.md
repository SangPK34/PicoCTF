## 🕵️‍♂️ Challenge:
### Files can always be changed in a secret way.
Can you find the flag? **cat.jpg**

### Hint:
1. Look at the details of the file
2. Make sure to submit the flag as picoCTF{XXXXX}
## 📝 Solution:
Đề cho 1 tấm ảnh `cat.jpg`  
Dựa vào gợi ý, ta kiểm tra metadata của nó:  

![image](https://github.com/user-attachments/assets/422f0526-5667-4fc9-bb8e-8134ada1d315)

→ Ta có đoạn mã base64: `cGljb0NURnt0aGVfbTN0YWRhdGFfMXNfbW9kaWZpZWR9`  
Đem đi decode, ta được flag:

> 🎯 Flag: **`picoCTF{the_m3tadata_1s_modified}`**
