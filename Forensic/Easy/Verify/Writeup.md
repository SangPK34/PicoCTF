## 🕵️‍♂️ Challenge:
### People keep trying to trick my players with imitation flags. I want to make sure they get the real thing! I'm going to provide the SHA-256 hash and a decrypt script to help you know that my flags are legitimate.
***`ssh -p 53039 ctf-player@rhea.picoctf.net`***  
Using the password ***`83dcefb7`***.  
Accept the fingerprint with ***yes***, and ***ls*** once connected to begin. Remember, in a shell, passwords are hidden!  
Checksum: ***467a10447deb3d4e17634cacc2a68ba6c2bb62a6637dad9145ea673bf0be5e02***  
To decrypt the file once you've verified the hash, run ***`./decrypt.sh files/<file>.`***
### Hint:
1. Checksums let you tell if a file is complete and from the original distributor. If the hash doesn't match, it's a different file.  
2. You can create a SHA checksum of a file with ***`sha256sum <file>`*** or all files in a directory with ***`sha256sum <directory>/*`***.
3. Remember you can pipe the output of one command to another with **`|`**. Try practicing with the 'First Grep' challenge if you're stuck!  
## 📝 Solution:
Chạy ssh bài cho, nhập mật khẩu và kiểm tra các file đang có trên ssh, ta thấy có 3 file:  

<img width="1184" height="655" alt="image" src="https://github.com/user-attachments/assets/499852e2-cb6a-41b4-8391-90a107c2126f" />
<br>
<br>
<br>
Kiểm tra từng file đang có:  
<br>
<br>
<img width="1463" height="653" alt="image" src="https://github.com/user-attachments/assets/6cf0300e-7f77-49ed-a754-f6eb3edd3bf4" />

Kiểm tra trong thư mục ***Files***, ta thấy có rất nhiều file ascii text:  

<img width="1442" height="653" alt="image" src="https://github.com/user-attachments/assets/4a6b776e-febc-4b30-86f5-d0639e5859b2" />

Từ các gợi ý đề cho, với file txt chứa mã hash, ta sẽ đi đối chiếu với các file có trong thư mục ***Files***, bằng lệnh:  
```bash
sha256sum files/* | grep "$(cat checksum.txt)"
```
<img width="979" height="82" alt="image" src="https://github.com/user-attachments/assets/90fcaeba-9313-4222-91a7-f9820e4df828" />

File cho kết quả khớp là file **`c6c8b911`**  
Bây giờ đi giải mã nó bằng file **`decrypt.sh`**  
```bash
./decrypt.sh files/c6c8b911
```
<img width="611" height="72" alt="image" src="https://github.com/user-attachments/assets/c1211dc8-4e0c-4824-8cfd-93cf952b0a08" />

Vậy là xong!  

>## 🎯 Flag: ***`picoCTF{trust_but_verify_c6c8b911}`***
