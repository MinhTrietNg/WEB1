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
- Trang quản trị: `admin/dang-nhap.html` (đăng nhập, URL riêng so với web bán hàng). Tài khoản mẫu
  `admin` / `admin123` đã điền sẵn, bấm Đăng nhập để vào `admin/index.html`; thanh bên chuyển sang
  Đơn hàng, Sản phẩm, Người dùng, Thống kê; nút Đăng xuất quay lại trang đăng nhập.

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
│   ├── gioi-thieu.html            Về chúng tôi
│   ├── cham-soc.html              Cẩm nang chăm cây (danh sách bài viết)
│   ├── bai-viet.html              Bài viết chi tiết
│   ├── lien-he.html               Liên hệ (sơ đồ vị trí vẽ bằng CSS)
│   ├── dang-nhap.html             Đăng nhập (đích đến đổi theo #gio-hang, #thanh-toan, #lich-su)
│   ├── dang-ky.html               Tạo tài khoản
│   ├── da-dang-nhap/              Khu đã đăng nhập (bản sao các trang bán hàng + trang riêng)
│   │   ├── tai-khoan.html         Thông tin khách hàng (hiện sau khi đăng nhập)
│   │   ├── chinh-sua-thong-tin.html  Chỉnh sửa thông tin (giả lập, không lưu thật)
│   │   ├── gio-hang.html          Giỏ hàng
│   │   ├── thanh-toan.html        Thanh toán (điền sẵn thông tin, chọn địa chỉ, ràng buộc SĐT)
│   │   ├── dat-hang-thanh-cong.html  Xác nhận đặt hàng
│   │   ├── lich-su.html           Lịch sử mua hàng, nhóm theo từng đơn
│   │   └── index, san-pham*, chi-tiet, gioi-thieu, cham-soc, bai-viet, lien-he (.html)
│   ├── css/
│   │   ├── fonts.css              Khai báo @font-face cho font lưu cục bộ
│   │   ├── style.css              Design tokens, header, footer, nút, form, thẻ sản phẩm
│   │   └── pages.css              Giao diện riêng cho từng trang + responsive
│   ├── fonts/                     Be Vietnam Pro, Fraunces (.woff2, có bộ ký tự tiếng Việt)
│   └── images/                    43 ảnh cây cảnh (.jpg)
│
└── admin/                         Website quản trị
    ├── dang-nhap.html             Đăng nhập quản trị (đăng xuất cũng quay về đây)
    ├── index.html                 Tổng quan (bảng điều khiển)
    ├── don-hang.html              Quản lý đơn hàng: bộ lọc + cập nhật tình trạng xuôi
    ├── don-hang-loc.html          Ví dụ kết quả lọc đơn hàng
    ├── don-hang-chi-tiet-*.html   Chi tiết từng đơn hàng (15 trang)
    ├── san-pham.html              Quản lý sản phẩm – trang 1 (san-pham-2, san-pham-3: trang 2, 3)
    ├── san-pham-them.html         Thêm sản phẩm (chọn phân loại, tải ảnh, khung xem trước)
    ├── san-pham-sua-*.html        Sửa sản phẩm, điền sẵn thông tin (28 trang)
    ├── khach-hang.html            Quản lý người dùng: khóa / mở khóa
    ├── khach-hang-them.html       Thêm người dùng
    ├── khach-hang-sua-*.html      Sửa người dùng (10 trang)
    ├── thong-ke.html              Thống kê 5 khách mua nhiều nhất theo khoảng ngày
    ├── css/
    │   ├── fonts.css              Bản sao từ web-ban-hang
    │   ├── style.css              Bản sao từ web-ban-hang (design tokens, nút, form…)
    │   └── admin.css              Bố cục quản trị, biểu đồ CSS, bảng dữ liệu
    ├── fonts/                     Bản sao font của web-ban-hang
    └── images/                    10 ảnh dùng ở trang Tổng quan
                                   (ảnh sản phẩm trong các trang khác lấy từ ../web-ban-hang/images)
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
- Nút “Thêm vào giỏ” (khu đã đăng nhập) chỉ hiện thông báo đã thêm; giỏ hàng luôn gồm các sản
  phẩm viết sẵn trong `da-dang-nhap/gio-hang.html`.

Phần lớn nút chuyển trang (Đăng nhập, Tạo tài khoản…) là liên kết thông thường. Chỉ một số
`<form>` dùng để tận dụng kiểm tra của HTML (vẫn không có JavaScript, không gửi hay lưu dữ liệu):

- Trang Thanh toán (`da-dang-nhap/thanh-toan.html`): ô số điện thoại bắt buộc, đúng 10 chữ số và bắt đầu bằng 03, 05, 07, 08
  hoặc 09 (`required` + `pattern`); nhập sai thì CSS `:invalid` đổi viền đỏ và hiện dòng báo lỗi,
  nút Đặt hàng không chuyển trang.
- Trang quản trị: biểu mẫu đăng nhập, thêm/sửa người dùng, thêm/sửa sản phẩm, bộ lọc đơn hàng
  và thống kê. Sau khi gửi biểu mẫu chỉ chuyển sang trang kết quả mẫu viết sẵn.

## Lịch sử mua hàng

`web-ban-hang/da-dang-nhap/lich-su.html` hiển thị các đơn của tài khoản mẫu “Thu Hà”, mỗi đơn là
một khối riêng (mã đơn, ngày đặt, thanh toán, tình trạng, danh sách sản phẩm, địa chỉ giao, tổng
tiền). Vào từ chân trang (“Tra cứu đơn hàng”), trang thông tin khách hàng hoặc nút “Xem lịch sử
mua hàng” ở trang xác nhận đơn. Đơn
#LV-261112-0428 khớp với giỏ hàng, trang thanh toán và trang quản trị.

## Trang quản trị: các chức năng theo tiêu chí

Toàn bộ là giao diện hardcode, thao tác không lưu lại sau khi tải lại trang:

| Chức năng | Cách thể hiện |
|---|---|
| Đăng nhập, đăng xuất | `admin/dang-nhap.html`, URL khác web bán hàng |
| Người dùng: thêm, sửa, khóa/mở | Danh sách có công tắc; CSS `:has()` đổi nhãn “Đang hoạt động” / “Đã khóa”; trang thêm và sửa riêng |
| Thêm sản phẩm | Chọn phân loại bắt buộc, ô tải ảnh, khung xem trước ảnh (ảnh cố định, vì chỉ HTML/CSS không đọc được file vừa chọn) |
| Sửa sản phẩm | Mỗi sản phẩm một trang, điền sẵn thông tin, phân loại và ảnh hiện tại |
| Xóa sản phẩm | Hộp thoại bằng `:target`: sản phẩm đã bán thì báo “sẽ ẩn”, chưa bán thì hỏi lại trước khi xóa |
| Cập nhật tình trạng đơn | Hộp chọn chỉ có tình trạng hiện tại và các bước tiếp theo; đơn đã giao/đã hủy không đổi được |
| Lọc đơn hàng | Tình trạng, từ ngày – đến ngày, thành phố, quận/huyện; `don-hang-loc.html` là kết quả mẫu |
| Thống kê | Chọn khoảng ngày; 5 khách mua nhiều nhất, giảm dần theo tổng tiền, mỗi đơn có liên kết xem chi tiết |

Đăng nhập quản trị không kiểm tra tài khoản: trang quản trị không thật sự bị khóa với người
chưa đăng nhập.

## Đăng nhập: khu khách và khu đã đăng nhập

Không có JavaScript hay máy chủ nên không có “phiên đăng nhập” thật. Thay vào đó website có hai
bộ trang:

- **Khu khách** (`web-ban-hang/`): xem sản phẩm, bài viết thoải mái. “Thêm vào giỏ”, “Mua ngay”,
  biểu tượng giỏ hàng và “Tra cứu đơn hàng” đều dẫn tới `dang-nhap.html` kèm `#gio-hang`,
  `#thanh-toan` hoặc `#lich-su`. Khu này không có trang giỏ hàng hay thanh toán.
- **Khu đã đăng nhập** (`web-ban-hang/da-dang-nhap/`): bản sao của các trang bán hàng, header có
  tên khách và nút đăng xuất. Chỉ ở đây mới thêm giỏ hàng được (thông báo “Đã thêm vào giỏ hàng”),
  và mới có giỏ hàng, thanh toán, xác nhận đơn, lịch sử mua hàng, thông tin khách hàng.
  Đăng xuất quay về trang chủ của khu khách.

Trang đăng nhập và tạo tài khoản biết bạn đến từ đâu nhờ địa chỉ có `#`: các phần tử rỗng
`<span id="gio-hang">`, `<span id="thanh-toan">`, `<span id="lich-su">` khớp `:target`, CSS
`body:has(#gio-hang:target)`… hiện lời nhắc và đổi nút “Đăng nhập” sang đúng trang đích. Đăng nhập
bình thường (không có `#`) thì vào `da-dang-nhap/tai-khoan.html`.

Tài khoản mẫu đã điền sẵn ở trang đăng nhập: **Nguyễn Thu Hà**, `thuha@example.com`. Trang
thông tin khách hàng hiển thị họ tên, email, số điện thoại, ngày sinh, hạng thành viên, điểm và sổ
địa chỉ (dữ liệu giả, khớp với đơn hàng và trang quản trị). Trang thanh toán tự điền sẵn thông tin
này, cho chọn một trong hai địa chỉ của tài khoản hoặc “Nhập địa chỉ mới” (các ô địa chỉ chỉ hiện
khi chọn mục này), và chỉ còn hai hình thức thanh toán: tiền mặt hoặc trực tuyến.

Từ trang thông tin khách hàng có thể vào `da-dang-nhap/chinh-sua-thong-tin.html` để “giả bộ” đổi
thông tin: biểu mẫu điền sẵn họ tên, email, số điện thoại (có ràng buộc `pattern`), ngày sinh,
giới tính, hai địa chỉ và phần đổi mật khẩu. Bấm “Lưu thay đổi” sẽ quay về `tai-khoan.html#da-luu`,
nơi CSS `:target` hiện thông báo “Đã lưu thay đổi”. Dữ liệu hiển thị vẫn là dữ liệu viết cứng,
không thay đổi thật.

Vì chỉ là luồng chuyển trang, gõ thẳng địa chỉ một trang trong `da-dang-nhap/` vẫn mở được.

## Ghi chú

- Dữ liệu sản phẩm, giá, đánh giá, địa chỉ… là dữ liệu mẫu.
- Ảnh minh họa lấy từ [Unsplash](https://unsplash.com) (Unsplash License).
- Font Be Vietnam Pro và Fraunces theo giấy phép SIL Open Font License.
- Giao diện responsive cho desktop, tablet và điện thoại; tôn trọng
  `prefers-reduced-motion` để tắt hiệu ứng chuyển động khi người dùng yêu cầu.
