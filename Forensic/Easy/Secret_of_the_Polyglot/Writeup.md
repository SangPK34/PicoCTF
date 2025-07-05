## 🕵️‍♂️ Challenge:
### The Network Operations Center (NOC) of your local institution picked up a suspicious file, they're getting conflicting information on what type of file it is. They've brought you in as an external expert to examine the file. Can you extract all the information from this strange file?
Download the suspicious file **here**.
### Hint:
1. This problem can be solved by just opening the file in different ways.
## 📝 Solution:
Đề cho 1 file đuôi PDF, mở lên thì thấy 1 phần flag.  

![image](https://github.com/user-attachments/assets/bf052974-c5fc-4997-b994-ace8a69b1210)

Dựa vào gợi ý rằng ta có thể giải quyết vấn đề khi mở file bằng nhiều cách khác nhau, mình sẽ kiểm tra dạng file đề cho:

```bash
pswsl@PS16:~/sangdz$ file flag2of2-final.pdf
flag2of2-final.pdf: PNG image data, 50 x 50, 8-bit/color RGBA, non-interlaced
```

→ Ta thấy nó báo file này là PNG, vậy tiến hành đổi đuôi file về PNG và mở.  

![image](https://github.com/user-attachments/assets/ce660c49-d92b-4051-b3b4-57716682ae44)

Vậy là có phần còn lại của flag.  

> 🎯 Flag: **`picoCTF{F1u3n7_1n_pn9_&_pdf_1f991f77}`**
