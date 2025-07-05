🕵️‍♂️ Challenge:
### We found this file. Recover the *flag*.
### Hint:
1. Weird that it won't display right...
## 📝 Solution:
Đề cho 1 file **`tunn3l_v1s10n`**, kiểm tra thì không rõ thuộc loại file nào, giải tệp ẩn cũng ko thấy gì...  
Mình mở thử trình soạn thảo hex để xem có gì bất thường ko:  

![image](https://github.com/user-attachments/assets/968cf91e-0ae9-4f56-892f-64192ec5f674)

Nhìn header thì đây có vẻ là file BMP, mình thử thêm đuôi file **.BMP** nhưng vẫn ko mở được.
Mình sử dụng web này để tham khảo về cấu trúc BMP Hex:  
> https://www.donwalizerjr.com/understanding-bmp/

Để ý tới **0x0E ~ 0x11** đại diện cho **header size**, ta thấy **`B8 D0 00 00`** là quá lớn, nên đổi về **`28 00 00 00`**  

![image](https://github.com/user-attachments/assets/ca6cc577-9edd-4b44-924a-86e4264fd1c6)

Giờ thì đã hiển thị được ảnh, nhưng trông hơi sai sai, cùng với đó là dòng chữ: `notaflag{sorry}`.  

Thử đổi **0x0A ~ 0x0D** từ **`B8 D0 00 00`** thành **`36 00 00 00`** - tương ứng với 54 bytes: Kích thước tối thiểu của file BMP chuẩn.

![image](https://github.com/user-attachments/assets/e2d9fec7-704c-4706-8106-645795897ace)

Lần này ảnh đã chuẩn hơn, nhưng vẫn chưa thấy flag.  
Mình đoán ảnh bị hiển thị thiếu nên thử thay đổi chiều rộng và cao của ảnh:
Đổi chiều rộng trước (tăng nhẹ 1 byte): đổi **`6E 04 00 00`** ở offset **0x12 – 0x15** thành **`6F 04 00 00`**  
Đổi xong ta thấy ảnh bị biến dạng, hỏng màu, có vẻ ko khả quan:  

![image](https://github.com/user-attachments/assets/8e0c5b4a-92c7-48e8-ab83-32cbd2454ed4)

Vậy đổi thử chiều , cũng tăng nhẹ 1 byte: đổi **`33 01 00 00`** ở offset **0x16 – 0x19** thành **`34 01 00 00`**  
Thì bức ảnh vẫn rất bình thường vậy tăng chiều cao là khả quan.  
Bây giờ cần tính chiều cao tối đa có thể tăng:  
> ***`Số byte chiều cao  = (Tổng bytes - 54 byte header) / (Số pixel rộng * Số byte trên 1 pixel )`***

Ở đây cụ thể là :  
Tổng bytes: 0x2C268E = 28934548 bytes
Ở vị trí offset 0x1C và 0x1D là số bit/pixel, **`18 00`** ứng với **`24`** -> Số byte trên 1 pixel: 24/8 = 3 bytes  
Chiều rộng được thể hiện bằng 4 bytes tại offset 0x12 - 0x15: **`6E 04 00 00`** = 1134 pixels

=> Chiều cao tối đa = (2893454-54) / (1134*3) = 850 bytes  

Quy 850 về Hex, ta được **`52 03 00 00`**.  

Sửa lại chiều cao trong Hex editor:  

![image](https://github.com/user-attachments/assets/249b513b-fe24-4841-92e4-811051224993)  

Ta được tấm ảnh hoàn chỉnh:  

![tunn3l_v1s10n](https://github.com/user-attachments/assets/4b99477f-eca8-42ba-a6fb-6690eaa6c7ac)

Và vậy thôi, hẹ hẹ hẹ...  

> ## 🎯 Flag: ***picoCTF{qu1t3_a_v13w_2020}***
