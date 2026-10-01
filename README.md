# Bài 1: Khởi tạo Droplet trên DigitalOcean

- **Học viên:** Đỗ Gia Hưng
- **Mục tiêu:** Cấu hình cặp khóa SSH Ed25519, khởi tạo máy chủ Ubuntu Server trên DigitalOcean và thực hiện kết nối an toàn không dùng mật khẩu.

---

## 1. Thông số cấu hình Droplet

| Tiêu chí | Cấu hình lựa chọn |
| :--- | :--- |
| **Hệ điều hành** | Ubuntu 22.04 LTS x64 |
| **Khu vực (Region)** | Singapore (SGP1) |
| **Gói tài nguyên** | Basic Plan - Regular SSD ($4 hoặc $6/mo) |
| **Xác thực** | SSH Key (`id_ed25519.pub`) |
| **Địa chỉ IP Public** | `<IP_ADDRESS_CỦA_BẠN>` |

---

## 2. Các bước thực hiện

### Bước 1: Khởi tạo SSH Keypair
Chạy lệnh tạo khóa Ed25519 tại máy cá nhân:
```bash
ssh-keygen -t ed25519 -C "your_email@example.com"
Lấy chuỗi Public Key từ tệp ~/.ssh/id_ed25519.pub để đưa lên DigitalOcean.

Bước 2: Tạo Droplet
Vào console DigitalOcean chọn tạo Droplet với các thông số tại bảng trên.

Tại mục Authentication Method, dán Public Key vừa tạo và chọn gán vào Droplet.

Bước 3: Xác thực kết nối SSH
Thực hiện kết nối từ terminal cá nhân:

Bash
ssh -i ~/.ssh/id_ed25519 root@<IP_ADDRESS_CỦA_BẠN>
3. Kết quả xác thực
Log kết nối Terminal
Plaintext
The authenticity of host '<IP_ADDRESS_CỦA_BẠN> (<IP_ADDRESS_CỦA_BẠN>)' can't be established.
ED25519 key fingerprint is SHA256:xxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx.
This key is not known by any other names.
Are you sure you want to continue connecting (yes/no/[fingerprint])? yes
Warning: Permanently added '<IP_ADDRESS_CỦA_BẠN>' (ED25519) to the list of known hosts.
Welcome to Ubuntu 22.04.4 LTS (GNU/Linux 5.15.0-xx-generic x86_64)

 * Documentation:  [https://help.ubuntu.com](https://help.ubuntu.com)
 * Management:     [https://landscape.canonical.com](https://landscape.canonical.com)
 * Support:        [https://ubuntu.com/pro](https://ubuntu.com/pro)

root@devops-lab-ubuntu:~# uname -a
Linux devops-lab-ubuntu 5.15.0-xx-generic #xx-Ubuntu SMP x86_64 x86_64 x86_64 GNU/Linux