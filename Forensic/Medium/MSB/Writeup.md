## 🕵️‍♂️ Challenge:
### This image passes LSB statistical analysis, but we can't help but think there must be something to the visual artifacts present in this image...
Download the image **here**
### Hint:
1. What's causing the 'corruption' of the image?
## 📝 Solution:
Đề cho 1 tấm ảnh **`Ninja-and-Prince-Genji-Ukiyoe-Utagawa-Kunisada.flag.png`**  

![Ninja-and-Prince-Genji-Ukiyoe-Utagawa-Kunisada flag](https://github.com/user-attachments/assets/603467f2-66ab-4a71-83f0-e13c112473da)

Đọc qua miêu tả của bài thì bài này ko phải phân tích bit LSB, tuy nhiên gợi ý nhắc rằng **tấm ảnh bị nhiễu do đâu?**, kết hợp với đề bài là MSB, ta có thể đoán rằng dữ liệu được ẩn chứa trong các bit MSB, do LSB là các bit mà khi sửa đổi ít gây ra khác biệt nhất, còn MSB thì ngược lại, cụ thể trong trường hợp này nó gây nhiễu tấm ảnh.  
Qua nhiều cách không khả quan cho lắm, sau 1 hồi lần mò thì mình tìm được công cụ này: `https://github.com/Pulho/sigBits`  
Cài đặt và chạy lệnh:
```bash
python3 sigBits.py -t=MSB Ninja-and-Prince-Genji-Ukiyoe-Utagawa-Kunisada.flag.png
```
Ta được 1 file **`outputSB.txt`** rất dài, tìm cụm từ **`pico`**, ta thấy flag xuất hiện:  

![image](https://github.com/user-attachments/assets/2b6fc0dd-89af-47cc-a7de-efd1220c7883)

> ### 🎯 Flag: `picoCTF{15_y0ur_que57_qu1x071c_0r_h3r01c_ee3cb4d8}`
