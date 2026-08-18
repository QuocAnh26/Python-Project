# 🏆 World Cup Data Analytics & Web App

Dự án phân tích dữ liệu chuyên sâu bóng đá World Cup (FBref Mini) tích hợp các mô hình Machine Learning để khám phá cấu trúc dữ liệu, tìm kiếm cầu thủ tương đồng, phân cụm lối chơi và định giá chuyển nhượng.

---

## 🛠️ Hướng dẫn cài đặt & Thiết lập môi trường (Setup)

Đối với các thành viên trong nhóm sau khi `clone` hoặc `pull` code mới nhất từ GitHub về máy, hãy thực hiện theo các bước dưới đây để chạy dự án:

### Bước 1: Kéo code mới nhất từ Git
Mở Terminal / Command Prompt tại thư mục dự án và chạy:
```bash
git pull origin main
```

### Bước 2: Tạo và kích hoạt môi trường ảo (venv)
Trên Windows:
```bash
python -m venv venv
venv\Scripts\activate
```
Trên macOS / Linux:
```bash
python3 -m venv venv
source venv/bin/activate
```

### Bước 3: Cài đặt các thư viện phụ thuộc (Dependencies)
Sau khi đã kích hoạt môi trường ảo, chạy lệnh sau để cài đặt toàn bộ thư viện cần thiết từ file `requirements.txt`:
```bash
pip install -r requirements.txt
```

> Chỉ làm BƯỚC 2 & 3 ĐÚNG 1 LẦN DUY NHẤT (Khi mới clone/setup dự án):
> - Bước 2 (Tạo venv): Chỉ cần tạo môi trường ảo một lần duy nhất trên máy.
> - Bước 3 (pip install): Chỉ cần cài đặt gói thư viện một lần duy nhất.