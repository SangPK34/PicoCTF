## 🕵️‍♂️ Challenge:
### Decode this ***message*** from the moon.
### Hint:
1. How did pictures from the moon landing get sent back to Earth?
2. What is the CMU mascot?, that might help select a RX option.
## 📝 Solution:
Đề cho 1 file `message.wav`, mở lên nghe toàn tiếng bíp bíp váng hết cả đầu:))  
Mình đoán là mã Morse nhưng đem đi giải mã thì ko phải.  

Đọc gợi ý 1: 
> ***How did pictures from the moon landing get sent back to Earth?***  

Mình tìm kiếm thì nó là phương thức **SSTV**

![image](https://github.com/user-attachments/assets/c8b54b66-7b15-44a5-a66f-e9d7045dac9c)
<br>
<br>
Đọc tiếp gợi ý 2:
> ***What is the CMU mascot?***

Mình tìm kiếm thì biết được **CMU** là tên 1 trường đại học: **Carnegie Mellon University**, và linh vật của họ là chú chó ***Scotty***

![image](https://github.com/user-attachments/assets/faaa948e-4f30-4dce-b3c6-b5b03745c766)

Và gộp 2 gợi ý lại, thì việc bây giờ chúng ta cần làm là: **giải mã SSTV với mode Scottie 1** từ file WAV đã cho.
Mình thử khá nhiều công cụ và đa số khá khó dùng, thậm chí bị lỗi, và cái ổn nhất mình lấy từ nguồn này:
> https://github.com/colaclanth/sstv

Cài đặt nó:
```bash
git clone https://github.com/colaclanth/sstv.git
cd sstv
sudo python3 setup.py install
```
Bây giờ chuyển file **`message.wav`** vào trong folder `sstv`, rồi chạy:
```bash
 sstv -d message.wav -o result.png
```
Xong! Giờ mở ảnh lên thui...  

![result](https://github.com/user-attachments/assets/57a2406e-2ec6-4991-af3a-42f18d474a2a)
<br>
<br>
> ## 🎯 Flag: ***picoCTF{beep_boop_im_in_space}***
