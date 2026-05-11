# 03 — Product ROI Dashboard

**Day 23 Lab — Product ROI Dashboard**
**Tên:**
- Nguyễn Thành Đại Khánh - 2A202600404

**Ngày:** 2026-05-11

---

## Part A — Adoption Context

### A.1 Thách Thức Chọn

| Trường | Trả lời |
|---|---|
| Thách thức áp dụng AI | Sinh viên đọc tài liệu học tập (PDF, slide) mất nhiều thời gian nhưng không nhớ được trọng tâm, không biết mình hiểu đến đâu, và không có lộ trình học rõ ràng |
| Tình huống xuất phát từ ai / ở đâu? | Sinh viên đại học đang ôn thi hoặc tự học môn mới, không có giảng viên hướng dẫn trực tiếp |
| Dấu hiệu bị kẹt | Đọc xong tài liệu nhưng không tổng hợp được; không biết câu nào sẽ ra thi; bỏ học giữa chừng vì không thấy tiến bộ |
| Vì sao thách thức này đáng giải quyết? | Retention rate của sinh viên tự học online thấp (~10-15% hoàn thành khoá); AI có thể cá nhân hoá lộ trình học và tăng hiệu quả đáng kể nếu đo đúng |

### A.2 Sản Phẩm / Công Cụ AI

| Trường | Trả lời |
|---|---|
| Tên sản phẩm / công cụ AI | **StudyMate AI** — AI Learning Assistant cho sinh viên đọc tài liệu |
| Người dùng chính | Sinh viên đại học (18-24 tuổi) tự học hoặc ôn thi, không có gia sư |
| Bối cảnh sử dụng | Sinh viên upload PDF / slide bài giảng → AI tóm tắt, tạo quiz, gợi ý học tiếp, theo dõi tiến độ |
| Mục tiêu kinh doanh / học tập / vận hành | Tăng tỷ lệ hoàn thành tài liệu lên ≥60%; cải thiện điểm kiểm tra trung bình ≥15%; giữ người dùng quay lại ≥3 buổi/tuần |
| Không nằm trong phạm vi | Dạy trực tiếp (live tutoring), chấm bài thi chính thức, quản lý lớp học của giảng viên |

### A.3 4 Quy Trình Chính

| # | Tên quy trình | Vai trò AI | Điểm người kiểm tra | Khi AI sai thì xử lý thế nào? |
|---|---|---|---|---|
| 1 | Upload PDF → Tóm tắt | Summarize — AI đọc toàn bộ tài liệu, trích trọng tâm, tóm tắt theo chương | Sinh viên review bản tóm tắt trước khi lưu; có nút "Báo sai / Thiếu" | Sinh viên gắn flag → system log lại → sinh viên tự edit hoặc đọc lại tài liệu gốc |
| 2 | Tạo quiz tự động | Generate — AI tạo câu hỏi trắc nghiệm + tự luận từ nội dung tóm tắt | Sinh viên làm quiz, hệ thống ghi nhận câu trả lời; không có giảng viên review real-time | Nếu câu hỏi sai logic → sinh viên report → câu hỏi đó bị loại khỏi pool; team content review hàng tuần |
| 3 | Gợi ý phần học tiếp theo | Recommend — AI phân tích điểm quiz, xác định gap, gợi ý chương/tài liệu nên đọc tiếp | Sinh viên xem gợi ý và chọn follow hoặc skip; có thể tắt tính năng này | Nếu gợi ý không phù hợp → sinh viên skip → system ghi nhận pattern để cải thiện model |
| 4 | Theo dõi tiến độ học | Track — AI tổng hợp % tài liệu đã đọc, điểm quiz theo thời gian, streak học tập | Sinh viên xem dashboard tiến độ; không có human review | Nếu data sai (vd: tính sai % đọc) → sinh viên report → Product Owner kiểm tra log trong 24h |

### A.4 Chẩn Đoán Nhanh ADKAR

| Stage | Câu hỏi | Nhận định |
|---|---|---|
| Awareness | Người dùng có biết AI này giúp gì không? | Biết — sinh viên tìm app vì nghe bạn bè / thấy quảng cáo |
| Desire | Người dùng có muốn dùng không? | **CÓ** nhưng yếu — muốn dùng khi gần thi, không duy trì thói quen |
| Knowledge | Người dùng có biết dùng đúng không? | Chưa — nhiều người chỉ dùng tóm tắt, bỏ qua quiz và gợi ý |
| Ability | Người dùng có đủ access, thời gian, kỹ năng không? | Đủ — app mobile, miễn phí cơ bản |
| Reinforcement | Có cơ chế khiến họ quay lại dùng không? | **YẾU nhất** — không có streak reward, không có reminder đủ mạnh |

**Barrier chính:**

```
Reinforcement — sinh viên dùng 1-2 lần rồi bỏ vì không có cơ chế nhắc nhở và phần thưởng
đủ để tạo thói quen. Desire có nhưng yếu, không đủ tự duy trì nếu không có Reinforcement.
```

### A.5 3 Tactic Tăng Adoption

| Tactic | Nhắm vào barrier nào? | Áp dụng cho quy trình nào? | Người phụ trách | Khi nào hoàn thành? |
|---|---|---|---|---|
| 1. Streak + reminder thông minh: thông báo push vào đúng giờ sinh viên thường học (dựa trên lịch sử dùng app), kèm progress so với hôm qua | Reinforcement | Workflow 4 — Theo dõi tiến độ | Product Manager | Tuần 3 sau launch |
| 2. Quiz challenge hàng tuần: mỗi tuần có 1 "challenge quiz" từ tài liệu sinh viên đã upload, có leaderboard nhỏ trong nhóm bạn bè | Desire + Reinforcement | Workflow 2 — Tạo quiz | Growth Lead | Tuần 5 sau launch |
| 3. Onboarding có hướng dẫn "dùng đúng cách": flow 3 bước đầu tiên chỉ rõ: upload → quiz → xem gợi ý, có ví dụ mẫu trước khi sinh viên upload file thật | Knowledge | Workflow 1, 2, 3 | UX Designer | Tuần 1 sau launch |

---

## Part B — ROI Dashboard

### B.1 Chỉ Số Toàn Sản Phẩm

| Lớp đo | Chỉ số | Mốc hiện tại | Mục tiêu | Nguồn dữ liệu | Người phụ trách | Rủi ro từ phản biện | Sửa ở v2 |
|---|---|---:|---:|---|---|---|---|
| Activation | % người dùng hoàn thành session đầu tiên (upload + xem tóm tắt + làm ≥1 quiz) | 34% | 60% | App event log (Mixpanel) | Product Manager | Sinh viên upload rồi đóng app ngay — activation quá dễ tính | v2: Thêm điều kiện "làm ≥1 quiz" mới tính activated |
| Retention / Value | % người dùng quay lại ≥3 buổi trong 7 ngày | 18% | 45% | App session log (Amplitude) | Growth Lead | 3 buổi/7 ngày có thể bị inflate nếu buổi = mở app <1 phút | v2: Định nghĩa buổi = ≥5 phút active trong app |
| Trust / Quality | % quiz câu hỏi không bị report lỗi sau khi sinh viên làm | 82% | 95% | Quiz report log (internal DB) | Content Lead | Sinh viên lười report dù câu hỏi sai → số này bị underestimate | v2: Thêm micro-survey sau mỗi quiz "Câu hỏi này có hợp lý không?" |

### B.2 Chỉ Số Theo Từng Quy Trình

#### Quy trình 1 — Upload PDF → Tóm tắt

| Lớp đo | Chỉ số | Mốc hiện tại | Mục tiêu | Nguồn dữ liệu | Người phụ trách | Rủi ro từ phản biện | Sửa ở v2 |
|---|---|---:|---:|---|---|---|---|
| Activation | % file upload được xử lý thành công (không lỗi parse) | 78% | 95% | Pipeline error log | Backend Engineer | PDF scan / hình ảnh không parse được → tính vào fail | v2: Phân loại lỗi: parse fail vs. định dạng không hỗ trợ |
| Engagement | % sinh viên đọc tóm tắt >30 giây trước khi đóng | 55% | 75% | Session time log (Mixpanel) | Product Manager | Để tab mở không = đọc thật | v2: Scroll depth tracking thay cho time-on-page |
| Productivity | Thời gian trung bình từ upload đến đọc xong tóm tắt so với đọc tài liệu gốc | 8 phút (tóm tắt) vs ~45 phút (gốc) | Giữ ≤10 phút | Timed session log | Product Manager | Chưa đo chất lượng hiểu — nhanh hơn không = hiểu tốt hơn | v2: Ghép với quiz score để kiểm chứng |
| Quality | % tóm tắt bị sinh viên gắn flag "sai / thiếu quan trọng" | 14% | ≤5% | Flag log (internal DB) | Content Lead | Sinh viên không biết nội dung gốc cũng không flag → số bị underestimate | v2: Thêm A/B test so sánh tóm tắt AI vs. tóm tắt giảng viên trên 20 tài liệu mẫu |
| Trust | % sinh viên dùng tóm tắt làm tài liệu ôn thi (không mở lại file gốc) | 38% | 60% | Follow-up survey sau kỳ thi | Growth Lead | Survey recall bias — sinh viên không nhớ chính xác | v2: Track hành vi: sau khi xem tóm tắt, có mở file gốc không? |
| Value | Điểm quiz trung bình của sinh viên đọc tóm tắt AI vs. không dùng | Tóm tắt AI: 68/100 vs. không dùng: 61/100 | Tóm tắt AI ≥75/100 | Quiz score DB + cohort split | Data Analyst | Cohort không randomized — nhóm dùng AI có thể chăm hơn vốn dĩ | v2: Randomized cohort test trong 1 kỳ học |

#### Quy trình 2 — Tạo quiz tự động

| Lớp đo | Chỉ số | Mốc hiện tại | Mục tiêu | Nguồn dữ liệu | Người phụ trách | Rủi ro từ phản biện | Sửa ở v2 |
|---|---|---:|---:|---|---|---|---|
| Activation | % sinh viên làm ≥1 quiz sau khi xem tóm tắt | 42% | 70% | App event log | Product Manager | Activation cao không = học được — có thể làm qua loa | v2: Tính activation khi score ≥50% (chứng tỏ đọc nội dung) |
| Engagement | Số quiz trung bình sinh viên làm per tài liệu | 1.3 | 3.0 | Quiz attempt log | Product Manager | Số lần làm nhiều có thể do quiz quá khó, không phải engaged | v2: Tách: lần đầu vs. retry để phân biệt struggle vs. engagement |
| Productivity | Thời gian ôn tập trung bình với quiz AI vs. tự đặt câu hỏi tay | 12 phút/chương (quiz AI) vs. ~35 phút (tự ôn) | Giữ ≤15 phút | Timed session + survey | UX Designer | Chưa đo hiệu quả nhớ sau 1 tuần | v2: Thêm delayed recall test sau 7 ngày |
| Quality | % câu hỏi quiz được sinh viên đánh giá "phù hợp / có ích" | 71% | 90% | In-app rating sau quiz | Content Lead | Rating bias: sinh viên dễ cho điểm cao nếu câu hỏi quen | v2: Thêm giảng viên review sample 50 câu/tuần để benchmark |
| Trust | % sinh viên accept gợi ý quiz tiếp theo mà không skip | 58% | 75% | Recommendation accept log | Data Analyst | Skip không = không tin — có thể đã đủ kiến thức | v2: Thêm exit survey khi skip "Tại sao bỏ qua?" |
| Value | Chênh lệch điểm kiểm tra giữa sinh viên dùng quiz AI ≥5 lần vs. không dùng | +9 điểm (68 vs. 59) | +15 điểm | Exam score + usage DB | Data Analyst | Confounding: sinh viên chăm thì cả dùng quiz nhiều lẫn điểm cao | v2: Kiểm soát biến "số giờ học tổng" trong phân tích |

#### Quy trình 3 — Gợi ý phần học tiếp theo

| Lớp đo | Chỉ số | Mốc hiện tại | Mục tiêu | Nguồn dữ liệu | Người phụ trách | Rủi ro từ phản biện | Sửa ở v2 |
|---|---|---:|---:|---|---|---|---|
| Activation | % sinh viên xem gợi ý (không đóng ngay) | 61% | 80% | Click event log | Product Manager | Xem ≠ follow — cần đo follow rate | v2: Đo cả "xem" và "bắt đầu học theo gợi ý" riêng |
| Engagement | % gợi ý được sinh viên follow (bắt đầu học phần được gợi ý trong session đó) | 29% | 50% | Navigation log | Product Manager | Follow rate thấp có thể do gợi ý chưa cá nhân hoá đủ | v2: Phân tích follow rate theo loại gap (gap nhỏ vs. gap lớn) |
| Productivity | Số "learning gap" được đóng trong 1 tuần (quiz cũ đạt ≥80% sau khi học theo gợi ý) | 1.1 gap/tuần | 3.0 gap/tuần | Quiz re-attempt log | Data Analyst | Gap "closed" có thể do quiz quá dễ, không phải học được | v2: Thêm delayed test sau 3 ngày để kiểm tra retention |
| Quality | % gợi ý phù hợp với gap thực sự của sinh viên (đo bằng post-quiz accuracy) | 64% | 85% | Quiz score before/after recommendation | Data Analyst | Model chưa tốt với tài liệu ngoài curriculum chuẩn | v2: Giới hạn gợi ý trong tài liệu đã có accuracy data tốt |
| Trust | % sinh viên tắt tính năng gợi ý (opt-out) | 22% | ≤10% | Feature toggle log | Product Manager | Opt-out cao = không tin hoặc không thấy giá trị | v2: Thêm exit survey khi opt-out để phân loại lý do |
| Value | Tỷ lệ hoàn thành tài liệu của sinh viên dùng gợi ý vs. không dùng | 41% (dùng) vs. 27% (không dùng) | ≥60% (dùng gợi ý) | Completion log + feature flag DB | Data Analyst | Sinh viên follow gợi ý có thể chăm hơn vốn dĩ | v2: Randomized experiment trong cohort mới |

#### Quy trình 4 — Theo dõi tiến độ học

| Lớp đo | Chỉ số | Mốc hiện tại | Mục tiêu | Nguồn dữ liệu | Người phụ trách | Rủi ro từ phản biện | Sửa ở v2 |
|---|---|---:|---:|---|---|---|---|
| Activation | % sinh viên mở dashboard tiến độ ≥1 lần/tuần | 33% | 60% | Page view log | Product Manager | Mở = xem nhanh rồi đóng, không = hành động | v2: Đo thêm "time on dashboard" ≥30 giây |
| Engagement | Streak dài nhất trung bình của sinh viên active (ngày liên tiếp có ≥1 learning session) | 4.2 ngày | 10 ngày | Session log (streak algorithm) | Growth Lead | Streak bị break do app crash hoặc lỗi kỹ thuật, không phải bỏ học | v2: Exclude streak break do lỗi kỹ thuật (từ error log) |
| Productivity | Số giờ học tracking được per tuần per user active | 2.1h | 4.0h | Session time log | Product Manager | Sinh viên để app chạy nền → inflate số giờ | v2: Chỉ tính giờ có interaction (scroll, click, answer) |
| Quality | % data tiến độ được sinh viên xác nhận là chính xác (qua prompt "Tiến độ này đúng không?") | 79% | 95% | In-app confirmation log | Backend Engineer | Sinh viên xác nhận qua loa để tắt thông báo | v2: Thêm 1 câu hỏi cụ thể "Còn chương nào bạn đã học mà app chưa ghi nhận?" |
| Trust | % sinh viên dùng dashboard để lập kế hoạch ôn thi (feature "Lập lịch từ tiến độ") | 19% | 40% | Feature usage log | Product Manager | Feature mới, chưa được biết đến → cần onboarding | v2: Thêm tooltip khi sinh viên gần ngày thi (lấy từ academic calendar) |
| Value | Tỷ lệ hoàn thành khoá học của sinh viên có streak ≥7 ngày so với không có streak | 67% (có streak) vs. 28% (không) | ≥70% (có streak ≥7 ngày) | Completion log + streak DB | Data Analyst | Correlation không phải causation — sinh viên chăm thì cả streak dài lẫn hoàn thành cao | v2: Phân tích với cohort matched (tương đồng về baseline engagement) |

---

## Part C — Dashboard Mock

```text
┌────────────────────────────────────┐ ┌────────────────────────────────────┐
│ TILE 1: PRODUCT HEALTH             │ │ TILE 2: WORKFLOW 1 — TÓM TẮT      │
│ Metric: Week-1 Retention Rate      │ │ Metric: % tóm tắt không bị flag   │
│ Current: 18%   Target: 45%         │ │ Current: 82%   Target: 95%         │
│ Status: RED                        │ │ Status: AMBER                      │
│ Action if red:                     │ │ Action if red:                     │
│  → Kích hoạt streak reminder       │ │  → Content Lead review 20 tóm tắt  │
│  → A/B test onboarding flow mới    │ │    bị flag trong tuần              │
└────────────────────────────────────┘ └────────────────────────────────────┘

┌────────────────────────────────────┐ ┌────────────────────────────────────┐
│ TILE 3: WORKFLOW 2 — QUIZ          │ │ TILE 4: TRUST / QUALITY            │
│ Metric: Quiz follow rate           │ │ Metric: Quiz rating "phù hợp"      │
│ Current: 42%   Target: 70%         │ │ Current: 71%   Target: 90%         │
│ Status: AMBER                      │ │ Status: AMBER                      │
│ Action if red:                     │ │ Action if red:                     │
│  → Thêm incentive (badge) quiz     │ │  → Giảng viên review 50 câu/tuần  │
│  → Giảm độ khó quiz đầu tiên       │ │  → Loại câu hỏi rating <3/5        │
└────────────────────────────────────┘ └────────────────────────────────────┘

┌────────────────────────────────────┐ ┌────────────────────────────────────┐
│ TILE 5: VALUE — LEARNING OUTCOME   │ │ TILE 6: DECISION                   │
│ Metric: Điểm exam: AI vs. no-AI    │ │ Continue / Pivot / Kill: CONTINUE  │
│ Current: +9pts  Target: +15pts     │ │ Metric mạnh nhất: Exam score delta │
│ Status: AMBER                      │ │ Before scale:                      │
│ Action if red:                     │ │  1. Fix retention (18% → 45%)      │
│  → Review quiz quality + gợi ý     │ │  2. Validate quiz quality ≥90%     │
│  → Chạy randomized cohort study    │ │  3. Randomized cohort study        │
└────────────────────────────────────┘ └────────────────────────────────────┘
```

---

## Part D — Decision Memo

```markdown
# Decision Memo — StudyMate AI (v2 sau red-team)

1. Tôi khuyến nghị: TIẾP TỤC (Continue) — nhưng không scale trước khi đạt retention ≥40%.

2. Chỉ số mạnh nhất để bảo vệ quyết định:
   Chênh lệch điểm kiểm tra: sinh viên dùng quiz AI ≥5 lần đạt 68/100 vs. 59/100 (không dùng)
   → Delta +9 điểm đo được từ actual exam score (không phải self-report).
   → Đây là evidence gần nhất với learning outcome thật — không chỉ đo hành vi trong app.

3. Chỉ số / giả định tôi đã sửa sau red-team:
   V1: Dùng "% sinh viên mở dashboard" để đo Retention.
       → CFO phản biện: mở app ≠ học được gì — dễ inflate bằng push notification.
   V2: Đổi thành "% người dùng quay lại ≥3 buổi trong 7 ngày với ≥5 phút active mỗi buổi"
       lấy từ session log (Amplitude), loại session <5 phút.
   Vì sao V2 tốt hơn: đo hành vi thật (thời gian active), không chỉ đo hiện diện.

   V1: Activation = sinh viên upload file thành công.
       → User phản biện: upload xong nhưng không đọc tóm tắt, không làm quiz = không activated.
   V2: Activation = upload + đọc tóm tắt + làm ≥1 quiz trong cùng session.
   Vì sao V2 tốt hơn: đảm bảo sinh viên trải qua đủ core value proposition.

4. Trước khi scale, tôi phải:
   1. Tăng Week-1 Retention từ 18% lên ≥40% — deadline: cuối Q3
   2. Validate quiz quality đạt ≥90% "phù hợp" — phối hợp giảng viên review — deadline: cuối Q2
   3. Chạy randomized cohort study (n≥200) để xác nhận causal link quiz AI → exam score — deadline: kết thúc 1 kỳ học
```

---

## Ghi chú Red-team (v1 → v2)

| # | V1 có vấn đề gì? | V2 sửa thành gì? | Vì sao sửa này tốt hơn? |
|---|---|---|---|
| 1 | Activation = upload file thành công | Activation = upload + xem tóm tắt + làm ≥1 quiz | Đo đủ core loop, không chỉ đo bước đầu tiên |
| 2 | Retention = % mở app ≥1 lần/tuần | Retention = ≥3 buổi/tuần với ≥5 phút active | Loại bỏ passive open, chỉ đo engagement thật |
| 3 | Quiz quality = số lần report lỗi | Quiz quality = in-app rating sau mỗi quiz + giảng viên review 50 câu/tuần | Giảm underreporting bias, thêm expert benchmark |

---
