# Khai báo dùng AI — Hồ Trung Kiên · G05

| # | Công cụ | Câu hỏi tóm tắt | Cách dùng kết quả | Cách đối chiếu |
|---|---|---|---|---|
| 1 | Codex | Thêm `occupied=yes` cho `child_seat` khi checkpoint A báo lỗi. | Sửa schema của script và cấu hình nhãn CVAT, cập nhật mục tương ứng trong guideline của repo. | Chạy lại checkpoint A trên S01 và S02. |
| 2 | Codex | Viết phần `ir_log` của Task 1b cho S03–S08. | Đưa số liệu RGB và IR-sim tính tại máy vào mẫu CSV, sau đó đối chiếu thêm dữ liệu nhãn trong bản cuối. | Đối chiếu mã khung, thống kê độ sáng và nhãn CVAT đã xuất. |
| 3 | Codex | Gộp hai bản CVAT, rồi gộp lại sau khi sửa nhãn DMS. | Giữ một bản xuất gồm 16 ảnh OMS và 6 ảnh DMS, cập nhật kết quả kiểm tra cuối. | Kiểm tra danh sách khung, nội dung nhãn và kết quả `cabin_check`. |
| 4 | Codex | Review các bất đồng và điền `disagreement_log.csv`. | Ghi kết quả đối chiếu checkpoint với bản cuối và sự khác lớp giữa cặp S06 RGB/IR-sim. | Đối chiếu số điểm D02, khung bao S06 và mục guideline liên quan. |
| 5 | Codex | Kiểm tra hồ sơ nộp cá nhân và bổ sung file còn thiếu. | Soạn danh sách lớp, bản tự đánh giá và đáp án gợi ý cho exit ticket. Bổ sung hai dòng IR thật từ dữ liệu nhãn và đóng gói bài. | Chạy lại các bộ kiểm tra, đọc CSV theo mẫu và kiểm tra nội dung gói ZIP. |
| 6 | Codex | Gộp bản export sau khi sửa S06 và cập nhật báo cáo liên quan. | Lấy nhãn S06 RGB mới từ CVAT, tạo bản v2 và cập nhật các ghi chú về S06 cùng gói nộp. | So các nhãn của hai bản, kiểm tra cặp S06 cùng lớp và hướng ghế, rồi chạy `cabin_check` trên 22 khung. |
| 7 | Codex | Kiểm tra gói nộp, ghi nhận coach đã chấp nhận `occupied=yes` và đóng gói theo hình thức cá nhân. | Bổ sung xác nhận của coach vào báo cáo kiểm tra và bản tự đánh giá. | Kiểm tra danh sách giá trị trong schema, bốn khung có `occupied=yes` và kết quả `cabin_check` trên cả hai bản xuất. |

Dữ liệu dùng để hỗ trợ review gồm nhãn XML xuất từ CVAT, file hướng dẫn và số liệu tổng hợp tính tại máy.
