## 🕵️‍♂️ Challenge:
### I don't like scrolling down to read the code of my website, so I've squished it. As a bonus, my pages load faster!  
Browse **here**, and find the flag!  
### Hint:
1. Try CTRL+U / ⌘+U in your browser to view the page source. You can also add 'view-source:' before the URL, or try curl <URL> in your shell.
2. Minification reduces the size of code, but does not change its functionality.
3. What tools do developers use when working on a website? Many text editors and browsers include formatting.  
## 📝 Solution:
Đề cho 1 trang web:  

<img width="1580" height="757" alt="image" src="https://github.com/user-attachments/assets/2dfbcbd5-c0a0-4fb9-b856-4eb3b0744270" />

Thử ctrl+U để xem source code:  

<img width="1919" height="673" alt="image" src="https://github.com/user-attachments/assets/fbcec36b-77e6-40bf-ac85-216b34b507b4" />

Ta thấy nó viết theo hàng ngang rất khó đọc và tìm.  

Vào devtool bằng F12, kiểm tra file index trong tab Source:  

<img width="1001" height="732" alt="image" src="https://github.com/user-attachments/assets/f5a4cfc0-d01b-4760-9f17-d7c6e448f7c3" />

Dễ thấy flag lộ ra.  

> ###🎯 Flag: **`picoCTF{pr3tty_c0d3_d9c45a0b}`**
