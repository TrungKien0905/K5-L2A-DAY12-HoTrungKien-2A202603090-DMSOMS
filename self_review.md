# Tự đánh giá — Hồ Trung Kiên · G05

## 1. Rà soát bốn cảnh

| Ảnh | Đối tượng | Loại lỗi | Ghi chú | Đã sửa? |
|---|---|---|---|---|
| S02_ir.png / S02_rgb.png | `child_seat.occupied` | Quy tắc kiểm tra | Coach đã xác nhận `occupied=yes` hợp lệ cho bài G05. Cặp S02 giữ giá trị đã gán. | Đã kiểm tra schema và chạy lại trên cả hai bản export. |
| S06_ir.png / S06_rgb.png | Ghế ở `rear_right` | `wrong_class` trên RGB ở bản trước | Bản trước gán `infant_seat` trên IR-sim và `child_seat` trên RGB cho cùng vị trí. | Đã sửa RGB thành `infant_seat`, `facing=front` trong bản v2. |
| D02.png | `face13` | `missing` ở checkpoint B | Bản checkpoint thiếu skeleton. Bản cuối có đủ 13 điểm nằm trong box mặt rộng 229,56 px. | Đã bổ sung. Vị trí từng điểm cần đối chiếu trên CVAT. |
| D04.png | `face13` | `extra` ở bản trước | Bộ kiểm tra báo skeleton không có điểm nào hiện. Bản cuối giữ box mặt và đã bỏ skeleton đó. | Đã sửa. |

## 2. Lỗi lặp lại và cách tránh

Ở bản export đầu, bộ kiểm tra báo cả D01 và D04 đều có `face13` nhưng không có điểm nào hiện. Trước khi thêm skeleton, kiểm tra box mặt có rộng ít nhất 60 px và xác định được mốc nào trong khung. Trước khi export, xem lại các skeleton mà mọi điểm đều bị đánh dấu `outside`.

## 3. Ghi chú về log bất đồng

D02 cho thấy cùng một khung có thể khác giữa checkpoint và bản cuối do phần 13 điểm được làm sau. Ở S06, đối chiếu cặp RGB/IR-sim phát hiện lớp ghế chưa nhất quán. Bản v2 dùng cùng lớp và cùng hướng ghế trên hai ảnh. Hai dòng này đến từ so sánh các bản và các khung của G05.
