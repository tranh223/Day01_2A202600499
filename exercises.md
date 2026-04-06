# Ngày 1 — Bài Tập & Phản Ánh
## Nền Tảng LLM API | Phiếu Thực Hành

**Thời lượng:** 1:30 giờ  
**Cấu trúc:** Lập trình cốt lõi (60 phút) → Bài tập mở rộng (30 phút)

---

## Phần 1 — Lập Trình Cốt Lõi (0:00–1:00)

Chạy các ví dụ trong Google Colab tại: https://colab.research.google.com/drive/172zCiXpLr1FEXMRCAbmZoqTrKiSkUERm?usp=sharing

Triển khai tất cả TODO trong `template.py`. Chạy `pytest tests/` để kiểm tra tiến độ.

**Điểm kiểm tra:** Sau khi hoàn thành 4 nhiệm vụ, chạy:
```bash
python template.py
```
Bạn sẽ thấy output so sánh phản hồi của GPT-4o và GPT-4o-mini.

---

## Phần 2 — Bài Tập Mở Rộng (1:00–1:30)

### Bài tập 2.1 — Độ Nhạy Của Temperature
Gọi `call_openai` với các giá trị temperature 0.0, 0.5, 1.0 và 1.5 sử dụng prompt **"Hãy kể cho tôi một sự thật thú vị về Việt Nam."**

**Bạn nhận thấy quy luật gì qua bốn phản hồi?** (2–3 câu)
> *Khi temperature tăng dần, câu trả lời chuyển từ trạng thái ổn định/lặp lại sang sáng tạo/ngẫu hứng. Ở mức 0.0, mô hình luôn chọn từ có xác suất cao nhất nên nội dung rất súc tích và giống nhau giữa các lần chạy; ngược lại, ở mức 1.5, câu chữ bắt đầu trở nên bay bổng quá mức, đôi khi bị lặp từ hoặc thiếu logic (hallucination).*

**Bạn sẽ đặt temperature bao nhiêu cho chatbot hỗ trợ khách hàng, và tại sao?**
> *em sẽ đặt temperature thấp, khoảng 0.0 đến 0.3. Lý do: Chatbot hỗ trợ khách hàng cần sự chính xác, nhất quán và đáng tin cậy, và không muốn chatbot tự tạotạo ra các chính sách hoàn tiền hoặc cung cấp thông tin sai lệch chỉ vì muốn trả lời một cách thú vị hơn*

---

### Bài tập 2.2 — Đánh Đổi Chi Phí
Xem xét kịch bản: 10.000 người dùng hoạt động mỗi ngày, mỗi người thực hiện 3 lần gọi API, mỗi lần trung bình ~350 token.

**Ước tính xem GPT-4o đắt hơn GPT-4o-mini bao nhiêu lần cho workload này:**
> *sấp xỉ 16,67 lần*

**Mô tả một trường hợp mà chi phí cao hơn của GPT-4o là xứng đáng, và một trường hợp GPT-4o-mini là lựa chọn tốt hơn:**
> *Nên dùng GPT-4o: Khi cần xử lý các tác vụ phức tạp đòi hỏi khả năng suy luận logic cao, chẳng hạn như viết mã nguồn (coding) phức tạp, phân tích hợp đồng pháp lý hoặc giải quyết các bài toán đa bước mà sai số nhỏ cũng gây hậu quả lớn. Nên dùng GPT-4o-mini: Khi thực hiện các tác vụ đơn giản, lặp đi lặp lại với khối lượng lớn như phân loại cảm xúc khách hàng (sentiment analysis), tóm tắt tin nhắn ngắn hoặc trả lời các câu hỏi FAQ cơ bản.*

---

### Bài tập 2.3 — Trải Nghiệm Người Dùng với Streaming
**Streaming quan trọng nhất trong trường hợp nào, và khi nào thì non-streaming lại phù hợp hơn?** (1 đoạn văn)
> *Streaming là hỗ trợ cho trải nghiệm người dùng (UX) khi mô hình cần tạo ra các phản hồi dài (như viết bài blog hoặc giải thích chi tiết). Nó giúp giảm độ trễ cảm nhận (perceived latency) vì người dùng thấy chữ xuất hiện ngay lập tức thay vì phải nhìn màn hình trống trong 10-15 giây. Ngược lại, non-streaming phù hợp hơn cho các tác vụ backend (xử lý ngầm) mà người dùng không trực tiếp quan sát quá trình tạo chữ, ví dụ như trích xuất dữ liệu từ văn bản sang định dạng JSON, dịch thuật tự động theo lô (batch), hoặc khi hệ thống cần kiểm tra toàn bộ câu trả lời trước khi gửi đi để đảm bảo an toàn.*


## Danh Sách Kiểm Tra Nộp Bài
- [v] Tất cả tests pass: `pytest tests/ -v`
- [v] `call_openai` đã triển khai và kiểm thử
- [v] `call_openai_mini` đã triển khai và kiểm thử
- [v] `compare_models` đã triển khai và kiểm thử
- [v] `streaming_chatbot` đã triển khai và kiểm thử
- [v] `retry_with_backoff` đã triển khai và kiểm thử
- [v] `batch_compare` đã triển khai và kiểm thử
- [v] `format_comparison_table` đã triển khai và kiểm thử
- [v] `exercises.md` đã điền đầy đủ
- [v] Sao chép bài làm vào folder `solution` và đặt tên theo quy định 
