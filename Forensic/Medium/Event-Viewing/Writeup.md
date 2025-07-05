## 🕵️‍♂️ Challenge:
### One of the employees at your company has their computer infected by malware! Turns out every time they try to switch on the computer, it shuts down right after they log in. The story given by the employee is as follows:
1. They installed software using an installer they downloaded online  
2. They ran the installed software but it seemed to do nothing  
3. Now every time they bootup and login to their computer, a black command prompt screen quickly opens and closes and their computer shuts down instantly.

See if you can find evidence for the each of these events and retrieve the flag (split into 3 pieces) from the correct logs!
Download the Windows Log file **here**
### Hint:
1. Try to filter the logs with the right event ID
2. What could the software have done when it was ran that causes the shutdowns every time the system starts up?
## 📝 Solution:
Đề cho 1 file log của window: **`Windows_Logs.evtx`**  
Dựa vào gợi ý 1, mình thử tra các event ID của các sự kiện **`Install, Registry change, Shutdown`**  
thì thu được tương ứng là **`1033, 4657, 1077`**.  

Nhấn đúp vào từng sự kiện có ID như trên để kiểm tra, ta thu được các mảnh **Base64**:  

![image](https://github.com/user-attachments/assets/20f9c6ec-f91a-4186-a9da-59fb9e37610a)

![image](https://github.com/user-attachments/assets/2551734d-e0ac-4f77-9917-f3069d2ea606)

![image](https://github.com/user-attachments/assets/5faefbff-ef76-4539-9370-eede91bb3c4b)

Đem đi decode, ta thu được flag:

> 🎯 Flag: **`picoCTF{Ev3nt_vi3wv3r_1s_a_pr3tty_us3ful_t00l_81ba3fe9}`**
