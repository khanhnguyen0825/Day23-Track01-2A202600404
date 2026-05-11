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

## Tài liệu tham khảo (Citations)

1. Morgan Stanley. “Launch of AI @ Morgan Stanley Debrief.” Morgan Stanley Press Release, 2024.  
   - Dùng để chứng minh: AI @ Morgan Stanley Assistant được rollout từ 2023; 98% Financial Advisor teams adopted the Assistant; Debrief hỗ trợ ghi chú meeting, action items, draft email và lưu vào Salesforce.

2. OpenAI. “Morgan Stanley uses AI evals to shape the future of wealth management.” OpenAI Customer Story.  
   - Dùng để chứng minh: Morgan Stanley dùng AI để hỗ trợ financial advisors truy xuất insight nhanh hơn; document access tăng từ 20% lên 80%; advisors có thêm thời gian cho client relationships.

3. Morgan Stanley. “Artificial Intelligence: Firmwide Team.”  
   - Dùng để chứng minh: Morgan Stanley triển khai AI theo hướng human-centric, có controls và oversight.

4. Klarna. “Klarna AI assistant handles two-thirds of customer service chats in its first month.” Klarna Press Release, 2024.  
   - Dùng để chứng minh: AI assistant xử lý 2/3 customer service chats; tương đương workload của 700 full-time agents; resolution time giảm từ 11 phút xuống dưới 2 phút.

5. OpenAI. “Klarna’s AI assistant does the work of 700 full-time agents.” OpenAI Customer Story, 2024.  
   - Dùng để chứng minh: 2.3 triệu conversations trong tháng đầu; 2/3 customer service chats; tương đương 700 agents; CSAT ngang human agents theo công bố ban đầu; repeat inquiries giảm 25%; resolution time dưới 2 phút.

6. Bloomberg. “Klarna Slows AI-Driven Job Cuts With Call for Real People.” 2025.  
   - Dùng để chứng minh: Klarna thừa nhận cách tiếp cận cost-cutting bằng AI trong customer service đã đi quá xa và cần đưa con người trở lại.

7. Fortune. “As Klarna flips from AI-first to hiring people again...” 2025.  
   - Dùng để chứng minh: Klarna quay lại tuyển người và CEO nhấn mạnh khách hàng luôn cần lựa chọn gặp human support.

8. Customer Experience Dive. “Klarna changes its AI tune and again recruits humans for customer service.” 2025.  
   - Dùng để chứng minh: Sau hơn một năm quảng bá AI chatbot làm workload của 700 representatives, Klarna quay lại dùng người cho customer service.

9. AP News. “AI shakes up the call center industry, but some tasks are still better left to the humans.” 2025.  
   - Dùng để chứng minh: Trong ngành call center, AI phù hợp với tác vụ lặp lại nhưng human agents vẫn quan trọng với case phức tạp/sensitive; Klarna là ví dụ về việc đưa người trở lại.