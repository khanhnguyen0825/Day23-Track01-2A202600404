# 04 — Reflection Cá Nhân

**Tên:** Nguyễn Thành Đại Khánh - 2A202600404
**Ngày:** 2026-05-11

---

## Một metric hoặc một giả định tôi sẽ sửa

Trong quá trình xây dựng dashboard cho StudyMate AI, giả định em muốn sửa nhất là cách đo **Retention**.

Ban đầu, em định nghĩa Retention là "% người dùng mở app ít nhất 1 lần trong 7 ngày". Nhìn lại, đây là một metric yếu vì nó đo sự hiện diện thụ động, không đo học tập thật sự. Một sinh viên mở app rồi đóng ngay sau 10 giây vẫn được tính là "retained" — điều đó hoàn toàn sai về bản chất.

Sau khi phân tích case Klarna và Morgan Stanley, em nhận ra sai lầm cốt lõi: **đo hành vi dễ quan sát thay vì đo kết quả thật**. Klarna đo số ticket xử lý được, bỏ qua việc khách hàng có thực sự hài lòng không — kết quả là phải tuyển lại 700 người.

Nếu làm lại, em sẽ sửa thành: Retention = % người dùng có ít nhất 3 phiên học trong 7 ngày, mỗi phiên có tương tác thật (scroll, trả lời quiz, ghi chú) tối thiểu 5 phút — đo bằng session log có lọc interaction event. Metric này khó đạt hơn, nhưng nếu đạt được thì mới thật sự chứng minh sản phẩm tạo ra thói quen học, không chỉ tạo ra lượt mở app.

---

