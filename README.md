# Lục Viên — Website cửa hàng cây cảnh

Dự án gồm **hai website độc lập**, mỗi website nằm trong một thư mục riêng:

| Thư mục | Website |
|---|---|
| `web-ban-hang/` | Web bán hàng dành cho khách (trang chủ, cửa hàng, giỏ hàng, thanh toán…) |
| `admin/` | Trang quản trị cửa hàng (tổng quan, đơn hàng, sản phẩm, khách hàng…) |

Cả hai viết **hoàn toàn bằng HTML và CSS** (không có JavaScript). Toàn bộ nội dung — sản phẩm,
giá, đánh giá, số liệu, số thứ tự — được viết cố định (hardcode) trong các file HTML. Ảnh và
font được lưu ngay trong thư mục của từng website, nên chạy được **hoàn toàn offline**, không
gọi tới bất kỳ dịch vụ bên ngoài nào.

## Cách chạy

Không cần cài đặt, không cần build, không cần mạng. Mở trực tiếp bằng trình duyệt
(Chrome, Edge, Firefox, Safari bản mới):

- Web bán hàng: `web-ban-hang/index.html`
- Trang quản trị: `admin/index.html` (Tổng quan), từ đó chuyển sang Đơn hàng, Sản phẩm, Khách hàng
  bằng thanh bên

Mỗi thư mục tự chứa đủ `css/`, `fonts/`, `images/` cần dùng nên có thể sao chép hoặc triển khai
riêng từng website. Chỗ duy nhất hai site trỏ sang nhau là các liên kết “Về cửa hàng” và
“Bài viết” trong trang quản trị (`../web-ban-hang/...`); nếu tách hẳn hai site khỏi nhau, chỉ
cần sửa các liên kết đó.

## Cấu trúc thư mục

```
├── README.md
│
├── web-ban-hang/                  Website bán hàng
│   ├── index.html                 Trang chủ
│   ├── san-pham.html              Cửa hàng – trang 1 (sản phẩm 1–12)
│   ├── san-pham-2.html            Cửa hàng – trang 2 (sản phẩm 13–24)
│   ├── san-pham-3.html            Cửa hàng – trang 3 (sản phẩm 25–28)
│   ├── chi-tiet.html              Chi tiết sản phẩm (Monstera)
│   ├── gio-hang.html              Giỏ hàng
│   ├── thanh-toan.html            Thanh toán
│   ├── dat-hang-thanh-cong.html   Xác nhận đặt hàng
│   ├── gioi-thieu.html            Về chúng tôi
│   ├── cham-soc.html              Cẩm nang chăm cây (danh sách bài viết)
│   ├── bai-viet.html              Bài viết chi tiết
│   ├── lien-he.html               Liên hệ (sơ đồ vị trí vẽ bằng CSS)
│   ├── dang-nhap.html             Đăng nhập
│   ├── dang-ky.html               Tạo tài khoản
│   ├── css/
│   │   ├── fonts.css              Khai báo @font-face cho font lưu cục bộ
│   │   ├── style.css              Design tokens, header, footer, nút, form, thẻ sản phẩm
│   │   └── pages.css              Giao diện riêng cho từng trang + responsive
│   ├── fonts/                     Be Vietnam Pro, Fraunces (.woff2, có bộ ký tự tiếng Việt)
│   └── images/                    43 ảnh cây cảnh (.jpg)
│
└── admin/                         Website quản trị
    ├── index.html                 Tổng quan (bảng điều khiển)
    ├── don-hang.html              Đơn hàng
    ├── san-pham.html              Sản phẩm
    ├── khach-hang.html            Khách hàng
    ├── css/
    │   ├── fonts.css              Bản sao từ web-ban-hang
    │   ├── style.css              Bản sao từ web-ban-hang (design tokens, nút, form…)
    │   └── admin.css              Bố cục quản trị, biểu đồ CSS, bảng dữ liệu
    ├── fonts/                     Bản sao font của web-ban-hang
    └── images/                    10 ảnh dùng trong trang quản trị
```

`fonts.css`, `style.css` và thư mục `fonts/` có mặt ở cả hai site (bản sao) để mỗi site chạy
độc lập. Khi sửa design tokens hoặc font, cần cập nhật ở cả hai nơi.

## Các hiệu ứng giao diện làm bằng CSS

| Hiệu ứng | Kỹ thuật |
|---|---|
| Menu điện thoại, bảng bộ lọc trượt ra | `checkbox` ẩn + `label` + selector `:checked ~` |
| Mega menu “Cửa hàng” | `:hover` và `:focus-within` |
| Tabs sản phẩm, tabs mô tả/đánh giá | `radio` ẩn + `label` |
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

## Yêu cầu đăng nhập trước khi thanh toán

Hai nút dẫn tới thanh toán (“Tiến hành thanh toán” ở giỏ hàng, “Mua ngay” ở trang chi tiết)
đều trỏ tới `dang-nhap.html#thanh-toan` chứ không tới `thanh-toan.html`. Thẻ `<body>` của
`dang-nhap.html` và `dang-ky.html` có `id="thanh-toan"`, nên khi địa chỉ có `#thanh-toan`, CSS
`body:target` hiện dòng nhắc và bật bộ nút trỏ tới `thanh-toan.html` (bộ nút mặc định trỏ tới
`index.html` bị ẩn). Nhờ vậy đăng nhập hoặc tạo tài khoản xong mới sang được trang thanh toán.

Đây chỉ là luồng chuyển trang; vì không có JavaScript hay máy chủ, website không thật sự kiểm tra
phiên đăng nhập — gõ thẳng `thanh-toan.html` vẫn mở được.

## Ghi chú

- Dữ liệu sản phẩm, giá, đánh giá, địa chỉ… là dữ liệu mẫu.
- Ảnh minh họa lấy từ [Unsplash](https://unsplash.com) (Unsplash License).
- Font Be Vietnam Pro và Fraunces theo giấy phép SIL Open Font License.
- Giao diện responsive cho desktop, tablet và điện thoại; tôn trọng
  `prefers-reduced-motion` để tắt hiệu ứng chuyển động khi người dùng yêu cầu.
