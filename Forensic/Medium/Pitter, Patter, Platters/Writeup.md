## 🕵️‍♂️ Challenge:
### 'Suspicious' is written all over this disk image.  
Download ***suspicious.dd.sda1***

### Hint:
1. It may help to analyze this image in multiple ways: as a blob, and as an actual mounted disk.  
2. Have you heard of slack space? There is a certain set of tools that now come with Ubuntu that I'd recommend for examining that disk space phenomenon...  
## 📝 Solution:
File đề cho là một volume ext3 chứ không phải là "disk image" chứa nhiều phân vùng.  
Mở bằng công cụ Autopsy để phân tích, ở tab "***file analysis***" ta thấy có file "**`suspicious-file.txt`"**:  

<img width="1808" height="712" alt="image" src="https://github.com/user-attachments/assets/36b749f5-9798-4330-8ab9-06c58249422d" />
<br>
<br>

Nội dung bên trong file txt:  

<img width="437" height="244" alt="image" src="https://github.com/user-attachments/assets/185ef154-6203-4912-a140-3556139b314f" />

<br>
<br>
Có vẻ đây là 1 gợi ý, và chúng ta hãy chú ý tới gợi ý đề bài cho là "Slack space".  
Slack space là phần dung lượng còn thừa trong cluster (khối lưu trữ nhỏ nhất trên ổ đĩa) khi một file không dùng hết.  

📦 Ví dụ:  

Ổ đĩa của chúng ta dùng cluster 4 KB. Ta lưu 1 file dung lượng 6 KB.  
-> File này sẽ chiếm 2 cluster:  

Cluster 1: 4 KB đầy đủ dữ liệu file.  

Cluster 2: chỉ dùng 2 KB cho dữ liệu file, 2 KB còn lại trống → đây chính là slack space.  

<img width="325" height="144" alt="download" src="https://github.com/user-attachments/assets/6e3e7462-34a7-49c1-a61c-adcb838ace30" />
<br>
<br>
Chọn tab Meta của file txt này:  

<img width="1507" height="466" alt="image" src="https://github.com/user-attachments/assets/3f873ed9-a0dc-4134-854d-be6eec4e774f" />
<br>
<br>
Sau đó click vào trị số 2049 của mục Direct Blocks.  

<img width="1387" height="709" alt="image" src="https://github.com/user-attachments/assets/1b04c8d6-fca5-4cb9-89f3-27e242259d72" />
<br>
<br>
Lúc này phần slack space đã được hiển thị:  

<img width="1029" height="417" alt="image" src="https://github.com/user-attachments/assets/5552fcad-d233-4c36-b505-f4fbeb19202d" />
<br>
<br>
Chỉ việc đảo ngược chuỗi và loại bỏ dấu chấm, ta được flag :D  

>### 🎯 Flag: ***picoCTF{b3_5t111_mL|_<3_ce709d16}***
