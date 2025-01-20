# Docker - những lệnh cơ bản 

# Mục Lục
1. [1. KHỞI ĐẦU VỚI DOCKER](#1-.-KHỞI-ĐẦU-VỚI-DOCKER)
   - [Kiểm tra phiên bản Docker](#Kiểm-tra-phiên-bản-Docker)
   - [Xem thông tin chi tiết về Docker trên hệ thống](#Xem-thông-tin-chi-tiết-về-Docker-trên-hệ-thống)
   - [Xem các container đang chạy](#Xem-các-container-đang-chạy)
   - [Xem tất cả container (cả đang chạy và đã dừng)](#Xem-tất-cả-container---cả-đang-chạy-và-đã-dừng)
2. [2. QUẢN LÝ CONTAINER](#2-.-QUẢN-LÝ-CONTAINER)
   - [Chạy một container mới](#Chạy-một-container-mới)
   - [Chạy container ở chế độ nền](#Chạy-container-ở-chế-độ-nền)
   - [Khởi động-dừng container](#Khởi-động---dừng-container)
   - [Khởi động lại container](#Khởi-động-lại-container)
   - [Xóa container](#Xóa-container)
   - [Truy cập vào terminal của container](#Truy-cập-vào-terminal-của-container)
   - 
   
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
