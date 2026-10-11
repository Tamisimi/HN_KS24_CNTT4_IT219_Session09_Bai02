# Bài 2 — Khởi chạy Web Server Nginx với Port Mapping

## Mục tiêu
Chạy Nginx dạng container ngầm (`-d`), ánh xạ cổng (`-p 8080:80`), kiểm tra bằng curl, rồi dọn dẹp.

## Các lệnh đã thực hiện

```bash
# 1. Khởi chạy container
docker run -d -p 8080:80 --name my-web nginx:alpine

# 2. Kiểm tra container đang chạy
docker ps

# 3. Kiểm tra trang web
curl http://localhost:8080

# 4. Dọn dẹp
docker stop my-web && docker rm my-web
```

## Giải thích nhanh

| Tham số | Ý nghĩa |
|---------|--------|
| `-d` | Chạy ngầm (detached) |
| `-p 8080:80` | Map cổng máy host 8080 → cổng 80 trong container |
| `--name my-web` | Đặt tên container |
| `nginx:alpine` | Image Nginx bản nhẹ |

## Kết quả mong đợi

### `docker ps`
Container `my-web` trạng thái Up, ports `0.0.0.0:8080->80/tcp`.

### `curl http://localhost:8080`
Trả về HTML có dòng **Welcome to nginx!**.

### Sau dọn dẹp
`docker ps -a` không còn container `my-web`.
