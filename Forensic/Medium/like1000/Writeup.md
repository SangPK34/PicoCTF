## 🕵️‍♂️ Challenge:
### This *.tar file* got tarred a lot.
### Hint:
1. Try and script this, it'll save you a lot of time 
## 📝 Solution:
Đề cho file ***1000.tar***, sau khi giải nén thử thì mình được file ***999.tar***, bóc tiếp thì đến ***998.tar*** :D  
Có vẻ đúng như đề bài, nó được nén rất nhiều lần, và bóc củ hành 1000 lớp này bằng tay thì chắc hỏng mắt mất :D  
Đúng, như gợi ý, ta cần viết script giải nén đến tận lõi thì thôi, và đây, của bạn đây:
```bash
#!/bin/bash

mkdir -p unpack_temp
cp "$1" unpack_temp/
cd unpack_temp

while true; do
    progress=0
    for f in *.tar; do
        [ -f "$f" ] || continue
        tar -xf "$f" && rm "$f"
        echo "📂 Giải nén: $f"
        progress=1
    done
    [ $progress -eq 0 ] && break
done

cd ..
mv unpack_temp untar
echo "✅ Đã lưu kết quả vào: untar"
```
Một số trình soạn script sẽ bị lỗi, dòng xuống dòng là CRLF, cần chuyển về Linux:

```bash
dos2unix untar.sh
```
Bây giờ kiểm tra trong thư mục **`untar`** vừa được tạo, sẽ có file `flag.png`  

![image](https://github.com/user-attachments/assets/e1e95105-15b1-46c0-8bbd-e7e9ae0b2632)


Ngon rồi...  

> ## 🎯 Flag: ***picoCTF{l0t5_0f_TAR5}***
