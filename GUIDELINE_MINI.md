# Mini guideline — bài làm cá nhân

> Điền nội dung này trước khi bắt đầu gán nhãn. Giữ lại các quyết định sau khi self-QC.

## Định nghĩa lớp

| Lớp | Định nghĩa của bạn | Ví dụ/điểm phân biệt |
| --- | --- | --- |
| `car` |Xe ô tô con, chủ yếu dùng để chở người, thường có 4–7 chỗ ngồi.| Sedan, hatchback, SUV, taxi, xe bán tải (pickup/cabin nhỏ). Phân biệt với van dựa vào thiết kế thân xe và mục đích sử dụng.|
| `truck` | Xe tải dùng để vận chuyển hàng hóa, thường có cabin và thùng hàng hoặc khu vực chở hàng riêng.| Xe tải thùng, xe ben, xe đầu kéo. Xe bán tải (pickup) không thuộc lớp này mà thuộc `car`. Phân biệt với van ở kết cấu và kiểu thân xe.|
| `bus` | Xe được thiết kế để vận chuyển nhiều hành khách, thường có nhiều hàng ghế và kích thước lớn.| Xe buýt công cộng, xe khách, xe đưa đón học sinh. Phân biệt với van dựa vào thiết kế và chức năng chở khách.|
| `van` | Xe dạng thân hộp, khoang cabin và khoang chở người/hàng thường nằm trong một thân xe liền khối| Xe tải van, xe giao hàng dạng van, xe minivan. Phân biệt với truck ở thiết kế thân xe và với bus ở cấu trúc, quy mô chở khách.|

## Quy tắc chung

- Box bám sát vật thể nghĩa là: Bounding Box phải bao quanh toàn bộ phần nhìn thấy của phương tiện, sát các điểm ngoài cùng của xe, hạn chế chứa vùng nền không cần thiết. Không bao gồm bóng đổ của xe.
- Vật thể bị che khuất: Vẫn gán nhãn nếu có đủ đặc điểm nhận dạng loại phương tiện. Bounding Box bao quanh phần nhìn thấy, không tự suy đoán phần bị che khuất.
- Vật thể bị cắt bởi rìa ảnh: Vẫn gán nhãn nếu xác định được loại xe. Bounding Box chỉ bao quanh phần xe nằm trong ảnh và không vượt ra ngoài ranh giới ảnh.
- Vật thể rất nhỏ/mơ hồ: Chỉ gán nhãn khi có thể xác định loại phương tiện một cách tương đối chắc chắn. Không gán nhãn nếu vật thể quá nhỏ, mờ hoặc không đủ đặc điểm để phân biệt giữa các lớp. Áp dụng nhất quán cho toàn bộ dataset.

## Ghi lại quyết định cho ít nhất ba ca mơ hồ

| Ảnh | Tình huống | Quyết định cuối | Lý do theo schema |
| --- | --- | --- | --- |
| `drive_009` | Một xe ô tô bị phương tiện phía trước che khuất một phần.| Vẫn gán nhãn car, box bao quanh phần nhìn thấy.| Xe vẫn có đặc điểm nhận dạng của car, áp dụng quy tắc vật thể bị che khuất.|
| `drive_014` | Một xe ô tô chỉ xuất hiện một phần ở rìa phải ảnh.| Gán nhãn car, Bounding Box chỉ bao quanh phần xe xuất hiện trong ảnh.| Vẫn nhận dạng được loại xe qua phần thân và kính xe, áp dụng quy tắc vật thể bị cắt bởi rìa ảnh.|
| `drive_019` | Một phương tiện ở rất xa, kích thước nhỏ và không rõ là car hay van.| Không gán nhãn nếu không thể phân biệt chắc chắn.| Áp dụng quy tắc vật thể rất nhỏ/mơ hồ, tránh gán sai lớp.|
