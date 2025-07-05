## 🕵️‍♂️ Challenge:
### This `garden` contains more than it seems.
### Hint:
1. What is a hex editor?
## 📝 Solution:
Đề cho 1 tấm ảnh `garden.jpg`  

Mình thử exiftool thấy ko có gì bất thường, sau đó thử lệnh:
```bash
strings garden.jpg
```
thì kết quả thu được:

![image](https://github.com/user-attachments/assets/3ce8a89b-7810-4b99-ad56-e0a1e192a924)

Như vậy là chưa cần tới gợi ý :(

> 🎯 Flag: **`picoCTF{more_than_m33ts_the_3y33dd2eEF5}`**
