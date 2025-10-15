## 🕵️‍♂️ Challenge:
### Can you get the flag?  
Go to **this** website and see what you can discover.  
### Hint:
1. How is the password checked on this website?  
## 📝 Solution:

<img width="1125" height="512" alt="image" src="https://github.com/user-attachments/assets/c12584b9-5d94-44c2-81a4-084a0cc6cbf0" />

Đề cho 1 trang web yêu cầu đăng nhập.  

Mình kiểm tra source code thì ko thấy gì.  

Dựa vào gợi ý, mình vào devtool, vào tab Source, thử đăng nhập bừa rồi quan sát.  

Sau khi nhấn đăng nhập thì web báo đăng nhập sai, đồng thời trong tab source xuất hiện 1 file **secure.js**, có nội dung là nguyên lý check đăng nhập.  

<img width="1617" height="632" alt="image" src="https://github.com/user-attachments/assets/c0dd5b03-754e-469f-97ad-79016ad2ec95" />

Vậy tài khoản mật khẩu cần nhập là:  
> admin  
> strongPassword098765

Đăng nhập thử:  

<img width="660" height="291" alt="image" src="https://github.com/user-attachments/assets/c5d2c268-29e8-4ea5-8c6b-8866b4e17d8c" />

Xong...  


> ### 🎯 Flag: **`picoCTF{j5_15_7r4n5p4r3n7_a8788e61}`**
