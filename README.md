# Docker - những lệnh cơ bản 

# Mục Lục
1. [KHỞI ĐẦU VỚI DOCKER](#1.-KHỞI-ĐẦU-VỚI-DOCKER)
   - [Kiểm tra phiên bản Docker](#Kiểm-tra-phiên-bản-Docker)
   - [Xem thông tin chi tiết về Docker trên hệ thống](#Xem-thông-tin-chi-tiết-về-Docker-trên-hệ-thống)
   - [Xem các container đang chạy](#Xem-các-container-đang-chạy)
   - [Xem tất cả container (cả đang chạy và đã dừng)](#Xem-tất-cả-container---cả-đang-chạy-và-đã-dừng)
2. [QUẢN LÝ CONTAINER](#2.-QUẢN-LÝ-CONTAINER)
   - [Chạy một container mới](#Chạy-một-container-mới)
   - [Chạy container ở chế độ nền](#Chạy-container-ở-chế-độ-nền)
   - [Khởi động-dừng container](#Khởi-động---dừng-container)
   - [Khởi động lại container](#Khởi-động-lại-container)
   - [Xóa container](#Xóa-container)
   - [Truy cập vào terminal của container](#Truy-cập-vào-terminal-của-container)
3. [LÀM VIỆC VỚI IMAGES](#3.-LÀM-VIỆC-VỚI-IMAGES)
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
# 2. QUẢN LÝ CONTAINER
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
# 3. LÀM VIỆC VỚI IMAGES
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
