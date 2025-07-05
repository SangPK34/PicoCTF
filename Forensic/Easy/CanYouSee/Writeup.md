## 🕵️‍♂️ Challenge:
### How about some hide and seek?
Download this file **here**.
### Hint:
1. How can you view the information about the picture?
2. If something isn't in the expected form, maybe it deserves attention?
## 📝 Solution:
Đề cho 1 file `unkown.zip`, giải nén ta được 1 file `ukn_reality.jpg`.  
Quan sát ko có gì bất thường ở tấm ảnh, chú ý tới các gợi ý, ta kiểm tra metadata của nó bằng `exiftool`:  

![Screenshot 2025-07-05 144155](https://github.com/user-attachments/assets/63c4fb13-5a51-41d0-9f3d-5549bedd87f1)

Ta thấy xuất hiện 1 chuỗi base64, đem đi giải mã ta thu được flag.

> 🎯 Flag: **`picoCTF{ME74D47A_HIDD3N_b32040b8}`**
