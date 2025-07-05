## 🕵️‍♂️ Challenge:
### A group of underground hackers might be using this legit site to communicate. Use your forensic techniques to uncover their message.Additional details will be available after launching your challenge instance.

## 📝 Solution:
### Sau khi khởi chạy thử thách, ta sẽ có một trang web với rất nhiều lá cờ.
Dựa vào gợi ý:  
`In the country that doesn't exist, the flag persists`  

→ Ta để ý có một lá cờ lạ, là 1 quốc gia không tồn tại **"Upanzi, Republic The"**.

![upz](https://github.com/user-attachments/assets/ca95134d-bbdf-4dd1-ad75-b689cb98a51d)

Chuột phải vào lá cờ → chọn **Kiểm tra phần tử** → phát hiện hình ảnh có kích thước cực lớn **14173 × 10630 px** nhưng dung lượng chỉ **1.8 MB**  
→ Rất đáng nghi, tiến hành tải về để phân tích.  
Sau khi thử 7749 cách với nhiều công cụ khác nhau nhưng không thu được gì do kích thước ảnh khá lớn.  
Mình để ý tên của challenge có từ **"Stepic"**, thử tìm trên web thì thấy một công cụ Python cùng tên.  

Cài đặt công cụ trên linux và chạy lệnh:
```bash
stepic -d -i upz.png
```
Và BÙMMM...
```markdown
🎯 FLAG: picoCTF{fl4g_h45_fl4g16aa94cf}
