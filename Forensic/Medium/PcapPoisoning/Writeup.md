## 🕵️‍♂️ Challenge:
### How about some hide and seek heh?
Download this **file** and find the flag.

### Hint:
(None)
## 📝 Solution:
Đề cho 1 file pcap, tiến hành mở bằng wireshark và quan sát.  
Ở đây mình thấy gói thứ 4 có info chứa **username root, password toor** rất đáng chú ý.  
Mình lọc các gói tin tương tác giữa 2 ip này thì được gói **507**, có thể thấy ngay nó chứa flag:  

![image](https://github.com/user-attachments/assets/51805b79-43cf-4671-ac6b-124e0f15ae9b)


> ### 🎯 Flag: `picoCTF{P64P_4N4L7S1S_SU55355FUL_5b6a6061}`
