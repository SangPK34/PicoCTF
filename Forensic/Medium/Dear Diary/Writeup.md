## 🕵️‍♂️ Challenge:
### If you can find the flag on this disk image, we can close the case for good!
Download the disk image ***here***.
### Hint:
1. If you're observing binary data raw in the terminal you may be misled about the contents of a block.  
## 📝 Solution:
Tải file về và giải nén, ta được một file disk image với MBR và có 3 phân vùng.  

<img width="831" height="116" alt="image" src="https://github.com/user-attachments/assets/ec6ea13a-58e6-4ad7-9242-e3fb15c9bef0" />

Bài này mình sẽ dùng công cụ Autopsy để phân tích file đĩa nhé.  

Sau khi nhập file vào autopsy:  
<img width="703" height="444" alt="image" src="https://github.com/user-attachments/assets/95d80ebe-a602-43ac-abfc-b201a5eb1c6d" />

Ta chọn tùy chọn đầu tiên là cả file disk với dữ liệu dạng raw thay vì chọn từng phân vùng. Sau đó chọn Analyze, chọn keyword search, nhập ".txt" để tìm thử các file txt đang có.  
<img width="882" height="631" alt="image" src="https://github.com/user-attachments/assets/dde0a6e9-de0e-40db-9385-4be08288d637" />

Tìm từ trên xuống thì ta thấy Unit 1423344 xuất hiện chuỗi "***pic***":  
<img width="1483" height="672" alt="image" src="https://github.com/user-attachments/assets/122ba941-d627-45c1-a31c-9c2910261e95" />

Xem thử cái tiếp theo thì xuất hiện "***oCT***":  
<img width="1177" height="438" alt="image" src="https://github.com/user-attachments/assets/aa34c458-728e-4966-8571-4eef13718857" />

Và các Unit tiếp theo cũng chứa các phần của flag, chỉ cần ghép lại là được flag:  

>### 🎯 Flag: ***picoCTF{1_533_n4m35_80d24b30}***
