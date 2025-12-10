# Challenge CTF Forensics
Name challenge: Bitlocker-1
Link: https://play.picoctf.org/practice/challenge/453?category=4&difficulty=2&page=1.
Đầu tiên mình tải file về máy ảo kali để tiện cho việc phân tích và giải mã.
Sau khi tải mình được 1 file tên bitlocker-1.dd, xác định được đây là 1 file ổ đĩa, dựa vào tên bài thì mình đoán được 90% file đang bị khóa dưới dạng bitlocker.
Để chắc ăn mình xài lệnh
```bash
file  bitlocker-1.dd
```
Ta có kết quả 
<img width="1907" height="95" alt="image" src="https://github.com/user-attachments/assets/e000b7a7-c3dd-4c5a-9beb-2bfa141ce2dc" />
Mình nhận ra dạng bài yêu cầu giải mã phân vùng BitLocker. 
Mình bắt đầu dùng công cụ bitlocker2john dể trích xuất hash của file 
```bash
bitlocker2john -i bitlocker-1.dd > hash.txt
```
Khi trích xuất xong mình được 1 file ma.txt chứa toàn bộ mã băm của file gốc.
<img width="1679" height="355" alt="image" src="https://github.com/user-attachments/assets/a524b586-452c-4a91-a7ef-f50417f88829" />
Sau đó mình dùng tiếp công cụ thứ 2 là john để crack file đó bằng data password khổng lồ từ file rockyou mình có sẵn.
```bash
john ma.txt --wordlist=rockyou.txt
```
Sau 1 lúc thì mình có kết quả






