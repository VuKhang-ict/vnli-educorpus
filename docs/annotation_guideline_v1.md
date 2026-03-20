# Annotation Guideline v1 — VNLI-EduCorpus

## 1. Mục tiêu
Tài liệu này hướng dẫn gán nhãn cho các cặp câu Premise–Hypothesis trong bộ dữ liệu VNLI-EduCorpus thuộc lĩnh vực giáo dục.

Nhiệm vụ của người gán nhãn:
- đọc Premise
- đọc Hypothesis
- xác định quan hệ suy luận giữa hai câu
- chọn đúng 1 nhãn:
  - ENT = Entailment
  - CON = Contradiction
  - NEU = Neutral

## 2. Nguyên tắc cốt lõi
Người gán nhãn chỉ được dựa vào thông tin có trong Premise để đánh giá Hypothesis.

Không dùng:
- kiến thức ngoài văn bản
- suy đoán theo kinh nghiệm cá nhân
- giả định xã hội phổ biến
- ý định ngầm mà Premise không hỗ trợ rõ ràng

Câu hỏi cần tự hỏi:
“Dựa riêng vào Premise, tôi có đủ căn cứ để kết luận Hypothesis đúng, sai, hay chưa đủ thông tin?”

## 3. Định nghĩa nhãn

### 3.1. ENT — Entailment (Kéo theo)
Chọn ENT khi Premise đủ thông tin để kết luận Hypothesis đúng hoặc gần như chắc chắn đúng.

Dấu hiệu thường gặp:
- diễn đạt lại cùng ý
- thay đổi cách nói nhưng không đổi nghĩa cốt lõi
- khái quát hợp lý từ thông tin đã nêu
- quan hệ bao hàm trực tiếp

Ví dụ:
Premise: Giáo viên yêu cầu học sinh nêu luận điểm ở phần mở đầu.
Hypothesis: Phần mở đầu cần nêu luận điểm chính.
Label: ENT

### 3.2. CON — Contradiction (Mâu thuẫn)
Chọn CON khi Hypothesis trái với Premise hoặc không thể đồng thời đúng với Premise trong cùng ngữ cảnh.

Dấu hiệu thường gặp:
- phủ định trực tiếp
- đảo ngược ý nghĩa
- thay đổi thông tin thời gian, nơi chốn, đối tượng, số lượng theo hướng xung đột
- Premise nói “không”, Hypothesis nói “có” hoặc ngược lại

Ví dụ:
Premise: Học sinh không nên học tủ trước kì kiểm tra.
Hypothesis: Học tủ là cách học được khuyến khích.
Label: CON

### 3.3. NEU — Neutral (Trung tính)
Chọn NEU khi Premise không đủ thông tin để kết luận Hypothesis đúng hay sai.

Dấu hiệu thường gặp:
- Hypothesis thêm chi tiết mới mà Premise không nói tới
- Premise chỉ nói một phần nhưng Hypothesis kết luận quá mức
- không có bằng chứng đủ mạnh để chọn ENT
- cũng không có mâu thuẫn đủ rõ để chọn CON

Ví dụ:
Premise: Đoạn trích nói về tình bạn thời học sinh.
Hypothesis: Tác giả của đoạn trích sinh ra ở Huế.
Label: NEU

## 4. Quy tắc ra quyết định nhanh
Ưu tiên dùng chuỗi quyết định sau:

1. Hypothesis có được Premise hỗ trợ trực tiếp không?
- Có -> ENT

2. Hypothesis có mâu thuẫn trực tiếp với Premise không?
- Có -> CON

3. Nếu không rơi vào 1 hoặc 2:
- Chọn NEU

## 5. Quy tắc chi tiết để tránh gán nhãn sai

### 5.1. Không dùng kiến thức nền ngoài câu
Nếu Premise không nói, không được tự bổ sung bằng hiểu biết phổ thông.

### 5.2. Thêm chi tiết mới thường là NEU
Nếu Hypothesis thêm:
- địa điểm
- thời gian
- nguyên nhân
- số lượng
- chủ thể cụ thể
mà Premise không nêu, đa số là NEU.

### 5.3. Từ mức độ và sắc thái phải đọc kỹ
Các cặp như:
- nên / phải
- có thể / chắc chắn
- một số / tất cả
- thường / luôn luôn
rất dễ gây sai nhãn.

Quy tắc:
- Premise yếu hơn, Hypothesis mạnh hơn -> thường là NEU hoặc CON
- Premise mạnh hơn, Hypothesis yếu hơn -> có thể là ENT nếu không đổi nghĩa cốt lõi

### 5.4. Phủ định không phải lúc nào cũng là CON
Có từ “không” chưa chắc là mâu thuẫn.
Phải xem toàn bộ nghĩa câu.

### 5.5. Diễn giải lại bằng từ đồng nghĩa có thể là ENT
Nếu chỉ đổi cách nói mà không thêm hoặc bớt nghĩa quan trọng, có thể gán ENT.

### 5.6. Phạm vi khái quát hóa
- Từ cụ thể -> tổng quát vừa phải: có thể ENT
- Từ cụ thể -> khẳng định quá rộng: thường NEU
- Từ cá biệt -> tất cả / luôn luôn: thường không phải ENT

## 6. Các trường hợp dễ nhầm trong miền giáo dục

### 6.1. Yêu cầu học tập vs khuyến nghị
Premise: Học sinh nên đọc kĩ đề trước khi làm.
Hypothesis: Học sinh bắt buộc phải đọc đề 3 lần.
=> NEU

### 6.2. Cấm vs không khuyến khích
Premise: Học sinh không nên học tủ.
Hypothesis: Học sinh bị cấm tuyệt đối học tủ.
=> NEU hoặc CON tùy ngữ cảnh; mặc định ưu tiên NEU nếu Premise chưa nêu mức cấm tuyệt đối.

### 6.3. Dẫn chứng văn bản vs suy diễn ngoài văn bản
Premise chỉ nói về nội dung văn bản.
Hypothesis thêm thông tin về tác giả, bối cảnh ngoài văn bản.
=> thường NEU

### 6.4. Hướng dẫn làm bài vs kết quả bài làm
Premise: Giáo viên yêu cầu nêu luận điểm ở mở bài.
Hypothesis: Học sinh chắc chắn đã làm đúng yêu cầu.
=> NEU

## 7. Rationale bắt buộc
Mỗi task phải có giải thích ngắn từ 1–3 câu:
- chỉ ra vì sao chọn nhãn
- nêu cụ thể chi tiết nào trong Premise hỗ trợ quyết định
- nếu NEU, phải ghi rõ “Premise không đủ thông tin để kết luận ...”

## 8. Confidence bắt buộc
Chọn 1 mức:
- high
- medium
- low

Gợi ý:
- high: quan hệ rất rõ
- medium: có chút phân vân nhưng vẫn quyết định được
- low: task mơ hồ, khó, hoặc cần review

## 9. Quality flags
Đánh dấu nếu có một trong các vấn đề sau:
- ambiguous_premise
- ambiguous_hypothesis
- needs_domain_review
- possible_source_issue
- typo_or_cleaning_issue

## 10. Khi nào cần chuyển review
Gắn cờ review nếu:
- rationale khó viết rõ
- có nhiều hơn 1 cách hiểu hợp lý
- câu có lỗi diễn đạt làm thay đổi nghĩa
- không chắc vì cần kiến thức chuyên môn

## 11. Chính sách adjudication sau này
- Nếu 2 người gán cùng nhãn -> tạm chấp nhận
- Nếu khác nhãn -> đưa vào danh sách adjudication
- Nếu confidence low hoặc có quality flag -> ưu tiên review trước

## 12. Ghi nhớ cuối cùng
Khi phân vân giữa ENT và NEU:
- nếu Premise không đủ mạnh để chứng minh -> chọn NEU

Khi phân vân giữa CON và NEU:
- nếu chưa có xung đột thật rõ -> chọn NEU
