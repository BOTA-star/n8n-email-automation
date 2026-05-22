# Email Summarization Workflow (n8n)

## 1. Giới thiệu

Đây là workflow được xây dựng trên nền tảng n8n nhằm tự động xử lý email, bao gồm đọc nội dung email, xử lý file đính kèm và tóm tắt nội dung bằng Gemini Chat Model.

Workflow được thiết kế để hoạt động hoàn toàn trên hệ thống n8n nội bộ của công ty, không bao gồm source code độc lập.

---

## 2. Chức năng chính

* Tự động lấy email mới từ Gmail Trigger
* Kiểm tra và xử lý file đính kèm (PDF, JSON, TXT)
* Trích xuất nội dung từ file attachment
* Chuẩn hóa dữ liệu đầu vào bằng Code Node
* Tóm tắt nội dung email bằng Gemini Chat Model
* Gửi kết quả qua Zalo Webhook

---

## 3. Cấu trúc Workflow

Workflow bao gồm các bước chính:

1. **Gmail Trigger** – Nhận email mới
2. **IF Node** – Kiểm tra email có attachment (Nếu không có sẽ đến thẳng bước 5)
3. **Extract File Node** – Trích xuất nội dung file đính kèm
4. **Code Node** – Chuẩn hóa dữ liệu email và file
5. **Gemini Chat Model** – Tóm tắt nội dung email
6. **Zalo Webhook Node** – Gửi kết quả tóm tắt

---

## 4. Cách sử dụng

### Import workflow vào n8n

1. Truy cập hệ thống n8n nội bộ
2. Chọn **Import Workflow**
3. Upload file `workflow.json`
4. Cấu hình lại credentials:

   * Gmail API
   * Gemini API
   * Zalo Webhook

---

## 5. Dữ liệu đầu ra

Workflow trả về kết quả dạng:

```json
{
    "file_name": "Tên file đính kèm (nếu có)",
    "sender": "Email người gửi",
    "subject": "Tiêu đề email",
    "email_body": "Nội dung email gốc",
    "text": "Nội dung tóm tắt của AI..."
}
```

---

## 6. Lưu ý

* Workflow hoạt động trên nền tảng n8n, không cần backend riêng
* Toàn bộ logic xử lý nằm trong các node của n8n
* Cần cấu hình đầy đủ credentials trước khi chạy

## 7. Tài liệu liên quan

* File workflow: `workflow.json`
* AI Model: Gemini Chat API
* Platform: n8n
