# Danh sách lớp v0 — Hồ Trung Kiên · G05

## DMS

| # | Lớp / thuộc tính | Giá trị | Để làm gì (chức năng DMS) | Nhìn thấy được trên IR? |
|---|---|---|---|---|
| 1 | `person` | Box người, `seat=driver` | Xác định tài xế để gắn tín hiệu mặt, tay và dây an toàn đúng người. | Có khi thấy đường viền cơ thể. |
| 2 | `face` | Box mặt | Khoanh vùng đầu vào để ước lượng hướng đầu và theo dõi mắt. | Có khi đủ thấy mặt. |
| 3 | `face.eye_left`, `face.eye_right` | `open`, `closed`, `unknown` | Theo dõi thời gian nhắm mắt qua nhiều khung để hỗ trợ cảnh báo buồn ngủ. | Có khi phân biệt được hai mí. |
| 4 | `face.glasses` | `none`, `clear`, `sun`, `unknown` | Nhận biết khi kính làm giảm độ tin cậy của ước lượng mắt và hướng nhìn. | Có thể thấy gọng và tròng. Phản xạ hoặc đặc tính của tròng trên NIR làm việc phân loại khó hơn. |
| 5 | `face.gaze_zone` | `road`, `mirror_l`, `mirror_r`, `mirror_c`, `cluster`, `center`, `lap`, `other` | Ước lượng khoảng thời gian tài xế nhìn ra ngoài vùng đường. | Có khi đủ dấu hiệu từ mắt và hướng đầu. |
| 6 | `face13` | 13 điểm, có cờ `occluded` và `outside` | Dùng vị trí mắt, mũi và miệng để ước lượng tư thế đầu và trạng thái mí. | Có với mặt đủ lớn và các mốc nhìn thấy được. |
| 7 | `hand.on_wheel` | `yes`, `no`, `unknown` | Xác định tay nào đang chạm vô lăng khi hệ thống cần kiểm tra khả năng tiếp quản. | Có khi thấy rõ tay và điểm tiếp xúc với vô lăng. |
| 8 | `phone.state` | `held`, `mounted`, `lap` | Phân biệt điện thoại đang cầm với điện thoại trên giá hoặc trên đùi. | Có khi thấy cạnh, góc hoặc màn hình. |
| 9 | `person.seatbelt` | `worn_correct`, `worn_incorrect`, `not_worn`, `unknown` | Hỗ trợ nhắc thắt dây và kiểm tra đường đi của dây qua cơ thể. | Có khi thấy dải dây và vị trí qua vai, hông. |

## OMS

| # | Lớp / thuộc tính | Giá trị | Để làm gì (chức năng OMS) | Nhìn thấy được trên IR? |
|---|---|---|---|---|
| 1 | `person` | Box người | Đếm hành khách và phân biệt người với đồ vật ở hàng ghế sau. | Có khi thấy đủ hình dạng người. |
| 2 | `seat` | `rear_left`, `rear_middle`, `rear_right` trong bộ G05 | Gắn từng người hoặc vật với đúng ghế để hệ thống chỉ ra vị trí cần kiểm tra. | Có nếu xác định được vị trí ghế theo hướng của xe. |
| 3 | `person.seatbelt` | `not_worn`, `unknown` trong SVIRO | Ghi nhận trường hợp thấy rõ hành khách không thắt dây và trường hợp vùng dây không đủ rõ. | Có khi thân người và vùng dây nhìn rõ. |
| 4 | `child_seat.occupied` | `yes`, `no`, `unknown` | Phân biệt ghế trẻ em đang có người ngồi, đang trống hoặc chưa xác định. | Có khi nhìn rõ bên trong ghế. |
| 5 | `infant_seat.facing` | `rear`, `front` | Xác định hướng lắp của ghế em bé để hỗ trợ kiểm tra bố trí ghế. | Có nếu thấy được đường viền và hướng của ghế. |
| 6 | `object.type` | `bag`, `box`, `cup`, `other` | Phân biệt đồ vật đặt trên ghế với hành khách và ghế trẻ em. | Có khi hình dạng đủ rõ. |
| 7 | `frame_meta.camera_blocked` | `yes`, `no` | Báo suy giảm khả năng quan sát khi camera bị che. | Có khi vật che cản rõ trường nhìn. |

## Hai câu hỏi cần coach làm rõ

1. **S06_ir.png và S06_rgb.png.** Khi chỉ thấy một phần ghế ở `rear_right`, dấu hiệu hình dạng nào đủ để phân biệt `infant_seat` với `child_seat`? Hai ảnh từng được gán khác lớp ở cùng vị trí. Bản v2 gán cả hai là `infant_seat`, `facing=front`. Câu hỏi nhằm làm rõ tiêu chí áp dụng nhất quán cho các khung tương tự.
2. **D04.png.** Khi box mặt rộng hơn 60 px nhưng chưa xác định được các mốc, guideline cần tối thiểu bao nhiêu mốc xác định được để giữ `face13`? Bản cuối giữ box `face` và bỏ skeleton mà bản kiểm tra trước báo không có điểm nào hiện.
