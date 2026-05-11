# 02 — Case Comparison

**Day 23 Lab — Product ROI Dashboard**  
**Nhóm:** 
- Nguyễn Thành Đại Khánh - 2A202600404
- Bùi Trọng Anh - 2A202600010
- Nguyễn Tiến Thành - 2A202600487 

**Ngày:** 2026-05-11

---

## So sánh case thành công và cảnh báo

| Trường | Case thành công — Morgan Stanley | Case thất bại / cảnh báo — Klarna |
|---|---|---|
| **Case** | Morgan Stanley AI @ Work — triển khai AI assistant nội bộ cho ~16.000 financial advisors toàn cầu (2023) | Klarna AI customer service — thay thế 700 agent bằng AI chatbot, xử lý ~2/3 tổng lượng ticket (2024) |
| **AI được dùng trong workflow nào?** | Advisor tra cứu tài liệu nghiên cứu, quy định nội bộ, sản phẩm tài chính trong lúc gặp client — AI trả lời ngay thay vì advisor phải thoát ra tìm kiếm thủ công | Khách hàng liên hệ hỗ trợ → chatbot AI xử lý toàn bộ: tra cứu đơn hàng, giải quyết khiếu nại, hoàn tiền — thay thế gần như hoàn toàn con người ở tầng đầu |
| **Người dùng chính là ai?** | ~16.000 financial advisors nội bộ của Morgan Stanley | Khách hàng cuối (end users) liên hệ hỗ trợ của Klarna |
| **Họ đo metric gì?** | **Efficiency:** Thời gian tìm kiếm tài liệu; số lần tra cứu thành công; tỷ lệ adoption trong đội advisor; thời gian onboard advisor mới | **Volume:** Số ticket AI tự xử lý; tỷ lệ resolution không cần human; thời gian xử lý trung bình; chi phí nhân sự tiết kiệm được |
| **Metric đó chứng minh được gì?** | Giảm ~30% thời gian tìm kiếm thông tin; advisor dành thêm thời gian thật sự tư vấn client thay vì research; rút ngắn onboarding advisor mới từ nhiều tháng xuống vài tuần | AI xử lý 2/3 tổng ticket; resolution time giảm từ ~11 phút xuống ~2 phút; tiết kiệm chi phí tương đương ~700 headcount trong ngắn hạn |
| **Metric đó chưa chứng minh được gì?** | Chất lượng tư vấn tổng thể của advisor có thực sự tốt hơn không; portfolio performance của client có cải thiện không; advisor có thực sự tin và dùng output AI để ra quyết định hay chỉ để tham khảo | Customer satisfaction thật sự — CSAT ban đầu được đo trên tập ticket đơn giản, loại trừ các case phức tạp; long-term retention và customer lifetime value sau khi trải nghiệm hỗ trợ bị "AI hóa" |
| **Thiếu metric nào?** | Metric về trust calibration của advisor (họ có biết khi nào AI sai không?); client satisfaction sau khi advisor dùng AI; tần suất advisor override lại gợi ý của AI | CSAT đo đầy đủ kể cả complex case; churn rate của khách hàng so sánh pre/post; số case leo thang (escalation) lên human do AI thất bại; Net Promoter Score dài hạn |
| **Bài học cho dashboard nhóm** | AI hiệu quả nhất khi hỗ trợ knowledge retrieval trong domain chuyên biệt — không thay thế judgment. Metric nên đo thời gian giải phóng được (advisor làm được gì thêm?), không chỉ đo tốc độ AI. | Metric volume (số ticket giải quyết) và metric value (khách có hài lòng, có ở lại không) là hai thứ khác nhau hoàn toàn. Klarna sau đó phải tuyển lại agent. Đo sai metric = quyết định sai. |

---

## Bài học nhóm sẽ áp dụng vào dashboard

```
1. ĐỪNG chỉ đo volume / usage
   → Thêm ít nhất 1 metric Quality, Trust hoặc Value vào mỗi workflow.
   → Lý do: Klarna đo ticket count thay vì CSAT thật sự → quyết định sai → phải tuyển lại người.

2. ĐO "thời gian giải phóng được" thay vì chỉ đo tốc độ AI
   → Metric nên là: "Người dùng làm được gì thêm với thời gian tiết kiệm?"
   → Lý do: Morgan Stanley thành công vì đo thêm advisor dành thêm time cho client, không chỉ đo search speed.

3. CÓ human-check và failure path rõ ràng trong từng workflow
   → Klarna thiếu escalation metric → không biết AI thất bại ở đâu và bao nhiêu lần.
   → Dashboard của nhóm phải ghi rõ: AI sai thì ai xử lý? Dữ liệu lưu ở đâu?

4. ĐO trust calibration của người dùng AI
   → Metric: tần suất override / chỉnh sửa output AI; tỷ lệ advisor/agent tin vào kết quả AI.
   → Không đo trust = không biết khi nào cần can thiệp.

5. BASELINE và TARGET phải thực tế, có data source rõ
   → Không ghi chung chung "tăng hiệu quả" — phải ghi: baseline = X, target = Y, đo bằng công cụ Z.
```

---

## Phân tích nhanh: Tại sao Morgan Stanley thành công, Klarna thất bại?

| Chiều so sánh | Morgan Stanley ✅ | Klarna ❌ |
|---|---|---|
| **Scope AI** | Hỗ trợ → con người vẫn quyết định | Thay thế → AI quyết định toàn bộ |
| **Người dùng chính** | Internal (advisor) — kiểm soát được | External (khách hàng) — không kiểm soát được kỳ vọng |
| **Metric đo** | Efficiency + adoption (gần với value) | Volume + cost savings (xa với value thật) |
| **Human oversight** | Advisor vẫn review và chịu trách nhiệm | AI tự xử lý, human chỉ xử lý escalation |
| **Kết quả dài hạn** | Adoption tốt, advisor hài lòng | Phải tuyển lại 700 agent vì CSAT thật giảm |

---

