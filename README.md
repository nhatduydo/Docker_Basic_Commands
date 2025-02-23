# Docker - những lệnh cơ bản 

# Mục Lục
1. [KHỞI ĐẦU VỚI DOCKER](#KHỞI-ĐẦU-VỚI-DOCKER)
   - [Kiểm tra phiên bản Docker](#Kiểm-tra-phiên-bản-Docker)
   - [Xem thông tin chi tiết về Docker trên hệ thống](#Xem-thông-tin-chi-tiết-về-Docker-trên-hệ-thống)
   - [Xem các container đang chạy](#Xem-các-container-đang-chạy)
   - [Xem tất cả container (cả đang chạy và đã dừng)](#Xem-tất-cả-container---cả-đang-chạy-và-đã-dừng)
2. [QUẢN LÝ CONTAINER](#QUẢN-LÝ-CONTAINER)
   - [Chạy một container mới](#Chạy-một-container-mới)
   - [Chạy container ở chế độ nền](#Chạy-container-ở-chế-độ-nền)
   - [Khởi động-dừng container](#Khởi-động---dừng-container)
   - [Khởi động lại container](#Khởi-động-lại-container)
   - [Xóa container](#Xóa-container)
   - [Truy cập vào terminal của container](#Truy-cập-vào-terminal-của-container)
3. [LÀM VIỆC VỚI IMAGES](#LÀM-VIỆC-VỚI-IMAGES)
   - [Xem danh sách images](#Xem-danh-sách-images)
   - [Tải image từ Docker Hub](#Tải-image-từ-Docker-Hub)
   - [Build image từ Dockerfile](#Build-image-từ-Dockerfile)
   - [Đẩy image lên registry](#Đẩy-image-lên-registry)
4. [MẠNG VÀ VOLUME](#MẠNG-VÀ-VOLUME)
   - [Xem danh sách networks](#Xem-danh-sách-networks)
   - [Tạo network mới](#Tạo-network-mới)
   - [Tạo volume mới](#Tạo-volume-mới)
   - [Xem danh sách volumes](#Xem-danh-sách-volumes)
5. [ DOCKER COMPOSE](#DOCKER-COMPOSE)
   - [Khởi động các services](#Khởi-động-các-services)
   - [Dừng và xóa các services](#Dừng-và-xóa-các-services)
   - [Xem logs của các services](#Xem-logs-của-các-services)
6. [DỌN DẸP HỆ THỐNG](#DỌN-DẸP-HỆ-THỐNG)
   - [Xóa tất cả dữ liệu không sử dụng](#Xóa-tất-cả-dữ-liệu-không-sử-dụng)
   - [Xóa các container đã dừng](#Xóa-các-container-đã-dừng)
   - [Xóa các image không sử dụng](#Xóa-các-image-không-sử-dụng)
  
7. [tạo linux server](#tạo-linux-server)
  ## LỜI KHUYÊN:
- Luôn nhớ kiểm tra trước khi xóa container/image
- Sử dụng tags để quản lý versions
- Backup dữ liệu quan trọng trước khi thao tác
   
# 1. KHỞI ĐẦU VỚI DOCKER
### Kiểm tra phiên bản Docker
```
docker --version
```
### Xem thông tin chi tiết về Docker trên hệ thống
```
docker info
```
### Xem các container đang chạy
```
docker ps
```
### Xem tất cả container - cả đang chạy và đã dừng
```
docker ps -a
```
# QUẢN LÝ CONTAINER
### Chạy một container mới
```
docker run <image>
```
### Chạy container ở chế độ nền
```
docker run -d <image>
```
### Khởi động - dừng container
```
docker start/stop <container>
```
### Khởi động lại container
```
docker restart <container>
```
### Xóa container
```
docker rm <container>
```
### Truy cập vào terminal của container
```
docker exec -it <container> /bin/bash
```
# LÀM VIỆC VỚI IMAGES
###  Xem danh sách images
```
docker images
```
### Tải image từ Docker Hub
```
docker pull <image>
```
### Build image từ Dockerfile
```
docker build -t <name>:<tag> <path>
```
### Đẩy image lên registry
```
docker push <name>:<tag>
```
# MẠNG VÀ VOLUME
### Xem danh sách networks
```
docker network ls
```
### Tạo network mới
```
docker network create <name>
```
### Tạo volume mới
```
docker volume create <name>
```
### Xem danh sách volumes
```
docker volume ls
```
# DOCKER COMPOSE
### Khởi động các services
```
docker-compose up
```
### Dừng và xóa các services
```
docker-compose down
```
### Xem logs của các services
```
docker-compose logs
```
# DỌN DẸP HỆ THỐNG
### Xóa tất cả dữ liệu không sử dụng
```
docker system prune
```
### Xóa các container đã dừng
```
docker container prune
```
### Xóa các image không sử dụng
```
docker image prune
```
# test-server
Chạy một container Ubuntu giả lập server
```
docker run -dit --name test-server -p 2222:22 ubuntu
```
-d: Chạy container ở chế độ nền.
-i -t: Cho phép tương tác với container.
--name test-server: Đặt tên container.
-p 2222:22: Chuyển tiếp cổng SSH từ container ra máy host (cổng 2222 trên host sẽ kết nối tới cổng 22 trong container).

Sau đó, vào container để cấu hình SSH:
```
docker exec -it test-server bash
```
Cài đặt OpenSSH Server
```
apt update && apt install -y openssh-server
service ssh start
passwd  # Đặt mật khẩu cho user root
```
cài đặt trình soạn thảo nano
```
apt update && apt install -y nano
```
Mở file cấu hình SSH:
```
nano /etc/ssh/sshd_config
```
Tìm dòng: PermitRootLogin prohibit-password
sửa thành 
```
PermitRootLogin yes
```
Lưu lại (Ctrl + X → Y → Enter), rồi khởi động lại SSH
```
service ssh restart
```
Kết nối SSH từ máy host
```
exit
```
```
docker inspect -f "{{range .NetworkSettings.Networks}}{{.IPAddress}}{{end}}" test-server
```
lấy được ip 
```
172.17.0.2
```
Sau đó, thử kết nối SSH:
```
ssh root@localhost -p 2222
```
```
ssh root@172.17.0.2
```
Nếu không kết nối được, hãy kiểm tra xem cổng SSH có mở không bằng:
```
docker exec -it test-server netstat -tlnp | grep sshd
```
Hoặc thử restart SSH trong container:
```
docker exec -it test-server service ssh restart
```


# login ssh docker 
Khởi động Docker và kiểm tra container
```
docker start test-server
```
Vào container:
```
docker exec -it test-server bash
```
Sau đó, kiểm tra SSH:
```
service ssh status
```
Nếu SSH chưa chạy, bật nó lên
```
service ssh start
```
Nếu chưa cài OpenSSH, cài đặt bằng
```
apt update && apt install -y openssh-server
service ssh start
```
Thoát khỏi container (exit), rồi thử SSH từ cmd Windows:
```
ssh root@localhost -p 2222
```
## đổi tên: 
```
nano ~/.bashrc
```
Thêm dòng này vào cuối file: đổi tên khác nếu muốn
```
export PS1="root@myserver:~# "
```
Sau đó, chạy lệnh:
```
source ~/.bashrc
```
# thực hiện cài plask test api, postman, post,python 
Bạn đang chạy container Ubuntu (test-server), vào container này:
```
docker exec -it test-server bash
```
```
apt update && apt install -y python3-flask
```
kiểm tra phiên bản flask 
```
python3 -c "import importlib.metadata; print(importlib.metadata.version('flask'))"
```
 Tạo một API Flask trong Docker
 ```
nano /app.py
```
Thêm đoạn code API đơn giản:
```
from flask import Flask, request, jsonify

app = Flask(__name__)

@app.route('/post-data', methods=['POST'])
def post_data():
    data = request.get_json()
    return jsonify({"message": "Dữ liệu đã nhận", "data": data}), 200

if __name__ == '__main__':
    app.run(debug=True, host='0.0.0.0', port=5000)
```
Chạy API trong container:
```
python3 /app.py
```
Gửi request đến API trong Docker
Từ máy Windows, mở một cửa sổ terminal mới và chạy lệnh này để lấy IP của container
```
docker inspect -f "{{range .NetworkSettings.Networks}}{{.IPAddress}}{{end}}" test-server
```
```
172.17.0.2
```
# tạo linux server
```
docker version
```
```
docker pull ubuntu:latest
```
Chạy container Ubuntu
```
docker run -it --name my-linux-server ubuntu:latest /bin/bash
```
Cập nhật danh sách package
```
apt update && apt upgrade -y
```
Lệnh ping chưa được cài đặt trong container Ubuntu. Bạn có thể cài đặt nó bằng cách chạy
```
apt install iputils-ping -y
```
Sau khi cài đặt xong, thử lại lệnh
```
ping -c 4 google.com
```
 Cài đặt các công cụ cần thiết
 ```
apt install curl wget nano net-tools htop -y
```
Kiểm tra thông tin hệ thống
```
cat /etc/os-release && uname -r
```
Kiểm tra địa chỉ IP của container
```
ifconfig
```
Chạy một server đơn giản trong container
```
apt install python3 -y
```
 Chạy server HTTP
```
python3 -m http.server 8080 --bind 0.0.0.0
```
Đổi hostname
```
echo "nhatduy" > /etc/hostname
```
```
python3 -m http.server 8080 --bind 0.0.0.0
```
Kiểm tra truy cập từ Windows
```
apt update && apt install -y curl
```


# tạo ubuntu server
```
docker --version
```
Chạy lệnh sau để tạo một container Ubuntu
```
docker run -dit --name ubuntu-server ubuntu:latest
```
Sau đó, kết nối vào container:
```
docker exec -it ubuntu-server bash
```
Cập nhật hệ thống
```
apt update && apt upgrade -y
```
Cài đặt SSH Server
```
apt install openssh-server -y
```
```
service ssh start
```
Cài đặt giao diện 
Tên GUI	Nhẹ hay Nặng	Lệnh cài đặt
GNOME (Mặc định của Ubuntu Desktop)	Nặng	apt install ubuntu-desktop -y
Xfce (Nhẹ hơn GNOME)	Trung bình	apt install xfce4 -y
LXDE (Rất nhẹ)	Nhẹ nhất	apt install lxde -y
KDE Plasma (Đẹp nhưng nặng)	Nặng	apt install kde-plasma-desktop -y

ở đây sẽ thử cài giao diện mặc đinh 
```
apt install ubuntu-desktop -y
```

