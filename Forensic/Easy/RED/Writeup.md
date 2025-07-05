## 🕵️‍♂️ Challenge:
### RED, RED, RED, RED
Download the image: red.png
### Hint:
1. The picture seems pure, but is it though?
2. Red?Ged?Bed?Aed?
3. Check whatever Facebook is called now.
## 📝 Solution:
Đề cho 1 tấm ảnh màu đỏ, và gợi ý 1 mình thấy hơi vô dụng.  
Dựa vào gợi ý 2:  

`Red?Ged?Bed?Aed?`  

Ta chú ý và các chữ cái đầu sẽ được 1 gợi ý mới là **RGBA** - các thang màu của 1 tấm ảnh (red, green, blue, alpha).  
Ở đây mình chọn 1 trang web phân tích: **`https://georgeom.net/StegOnline/image`**

Dựa vào gợi ý 3:  
`Check whatever Facebook is called now.`  

→ Ta nghĩ tới cái tên công ty của FB là **"META"**.
→ Lục lọi trong đống metadata của bức ảnh, ta thấy được đoạn tin:  

![image](https://github.com/user-attachments/assets/783e5ed7-f89e-4c8f-81a4-499905933da0)

Để ý các chữ cái đầu mỗi  của đoạn tin, chúng ta có thông điệp:
```markdown
CHECKLSB
```
Quay lại trang web trên, upload ảnh và chọn **Show RGBA values**, ta có thể thấy giá trị các bit màu:

![image](https://github.com/user-attachments/assets/bbae90ff-78dc-4145-8943-e683061755e0)

Từ gợi ý đã có, ta phải xử lí các bit LSB của đống bit này, và nhìn sơ qua thì chúng chỉ có các giá trị là 0 và 1.  
Mình sẽ gộp 8 bit lại rồi đổi sang kí tự đọc được, code Python:  
```python
with open('RGBA.txt', 'r') as f:
    content = f.read()

numbers = [int(x.strip()) for x in content.replace(',', ' ').split()]

lsb_bits = [n & 1 for n in numbers]

chars = []
for i in range(0, len(lsb_bits), 8):
    byte = lsb_bits[i:i+8]
    if len(byte) < 8:
        continue
    value = 0
    for bit in byte:
        value = (value << 1) | bit
    chars.append(chr(value))

message = ''.join(chars)
print(message)

```
Và sau khi runcode, chúng ta thu được:  

![image](https://github.com/user-attachments/assets/5ddfbb50-ff87-4168-b605-083b6bb17d0a)

Nhìn qua thì đây là 1 chuỗi Base64 được lặp lại nhiều lần, ta tiến hành decode chuỗi **`cGljb0NURntyM2RfMXNfdGgzX3VsdDFtNHQzX2N1cjNfZjByXzU0ZG4zNTVffQ==`**.  

Và BÙMMM...  

> 🎯 Flag: **`picoCTF{r3d_1s_th3_ult1m4t3_cur3_f0r_54dn355_}`**
