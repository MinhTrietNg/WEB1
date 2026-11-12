# Lục Viên — Website cửa hàng cây cảnh

Website bán cây cảnh viết **hoàn toàn bằng HTML và CSS** (không có JavaScript).
Toàn bộ nội dung — sản phẩm, giá, đánh giá, số liệu, số thứ tự — được viết cố định
(hardcode) trong các file HTML. Ảnh và font được lưu ngay trong thư mục dự án, nên
website chạy được **hoàn toàn offline**, không gọi tới bất kỳ dịch vụ bên ngoài nào.

## Cách chạy

Mở trực tiếp file `index.html` bằng trình duyệt (Chrome, Edge, Firefox, Safari bản mới).
Không cần cài đặt, không cần build, không cần mạng.

## Cấu trúc thư mục

```
├── index.html                 Trang chủ
├── san-pham.html              Cửa hàng – trang 1 (sản phẩm 1–12)
├── san-pham-2.html            Cửa hàng – trang 2 (sản phẩm 13–24)
├── san-pham-3.html            Cửa hàng – trang 3 (sản phẩm 25–28)
├── chi-tiet.html              Chi tiết sản phẩm (Monstera)
├── gio-hang.html              Giỏ hàng
├── thanh-toan.html            Thanh toán
├── dat-hang-thanh-cong.html   Xác nhận đặt hàng
├── gioi-thieu.html            Về chúng tôi
├── cham-soc.html              Cẩm nang chăm cây (danh sách bài viết)
├── bai-viet.html              Bài viết chi tiết
├── lien-he.html               Liên hệ (sơ đồ vị trí vẽ bằng CSS)
├── dang-nhap.html             Đăng nhập / Đăng ký
├── css/
│   ├── fonts.css              Khai báo @font-face cho font lưu cục bộ
│   ├── style.css              Design tokens, header, footer, nút, form, thẻ sản phẩm
│   └── pages.css              Giao diện riêng cho từng trang + responsive
├── fonts/                     Be Vietnam Pro, Fraunces (.woff2, có bộ ký tự tiếng Việt)
└── images/                    43 ảnh cây cảnh (.jpg)
```

## Các hiệu ứng giao diện làm bằng CSS

| Hiệu ứng | Kỹ thuật |
|---|---|
| Menu điện thoại, bảng bộ lọc trượt ra | `checkbox` ẩn + `label` + selector `:checked ~` |
| Mega menu “Cửa hàng” | `:hover` và `:focus-within` |
| Tabs sản phẩm, tabs mô tả/đánh giá, đăng nhập/đăng ký | `radio` ẩn + `label` |
| Gallery ảnh sản phẩm | `radio` + hiệu ứng `opacity` |
| Hiện chi tiết phương thức thanh toán | `.pay:has(input:checked)` |
| Thông báo “Đã thêm vào giỏ hàng” | nút là `<label>` của `radio` ẩn + `body:has(#cart-added:checked)` |
| FAQ / accordion | thẻ `<details>` / `<summary>` |
| Thanh tiến độ đọc bài viết | `animation-timeline: scroll()` |
| Hiệu ứng xuất hiện khi cuộn | `animation-timeline: view()` |
| Tô màu sao đánh giá theo điểm | `background-clip: text` + biến `--rating` |
| Dải thông báo chạy ngang | `@keyframes` |

Các phần sau chỉ là giao diện minh họa, không tính toán hay thay đổi dữ liệu:

- Bộ lọc, nút sắp xếp ở trang Cửa hàng và các chủ đề ở trang Cẩm nang: danh sách sản phẩm,
  bài viết luôn cố định như trong HTML.
- Lựa chọn kích thước, chậu, số lượng ở trang chi tiết: giá luôn hiển thị cố định.
- Lựa chọn hình thức giao hàng, mã giảm giá ở giỏ hàng: phí giao và tổng tiền luôn cố định.
- Nút “Thêm vào giỏ” chỉ hiện thông báo đã thêm; giỏ hàng luôn gồm các sản phẩm viết sẵn
  trong `gio-hang.html`. Chỉ khi bấm “Tiến hành thanh toán” mới sang trang thanh toán.

Website không có thẻ `<form>` gửi dữ liệu: các ô nhập liệu không có ràng buộc kiểm tra, và
những nút cần chuyển trang (Đăng nhập, Tạo tài khoản, Đặt hàng…) là liên kết thông thường.

## Ghi chú

- Dữ liệu sản phẩm, giá, đánh giá, địa chỉ… là dữ liệu mẫu.
- Ảnh minh họa lấy từ [Unsplash](https://unsplash.com) (Unsplash License).
- Font Be Vietnam Pro và Fraunces theo giấy phép SIL Open Font License.
- Giao diện responsive cho desktop, tablet và điện thoại; tôn trọng
  `prefers-reduced-motion` để tắt hiệu ứng chuyển động khi người dùng yêu cầu.
