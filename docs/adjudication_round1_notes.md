# Adjudication Round 1 Notes

## Phạm vi
Pilot round 2 balanced gồm 15 mẫu:
- 5 ENT
- 5 CON
- 5 NEU

## Kết quả so sánh
- Không có case nào lệch nhãn giữa hai lượt gán.
- Tất cả 15/15 mẫu đều trùng nhãn.
- Đây là bằng chứng tốt cho độ ổn định giữa hai lượt gán nhãn.

## Lưu ý phương pháp
- Cả hai file export hiện đều mang completed_by = 1.
- Vì vậy, kết quả hiện tại nên diễn giải là intra-annotator consistency / test-retest consistency.
- Chưa thể xem đây là inter-annotator agreement đúng nghĩa nếu chưa có annotator thứ hai độc lập.

## Case cần lưu ý
### VNLI_DEMO_0026
- Lượt 1: NEU + ambiguous_hypothesis
- Lượt 2: NEU, không gắn quality flag
- Quyết định cuối: giữ final_label = NEU
- Ghi chú: cần làm rõ hơn trong guideline khi nào dùng quality_flag cho các giả thuyết thêm thông tin ngoài premise.

## Kết luận
Pilot round 2 đã hoàn thành tốt mục tiêu:
- kiểm tra độ ổn định của guideline
- kiểm tra tính nhất quán của labeling interface
- tạo được một mini gold set 15 mẫu để làm mốc tham chiếu
