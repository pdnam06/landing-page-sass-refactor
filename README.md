# Tái cấu trúc Landing Page MyBrand bằng Sass

## Trang nguồn
Đề bài không kèm hình hoặc file thiết kế Template. Bài này sử dụng Landing Page MyBrand đã làm trước đó trong thư mục responsive-landing-page. Phần nổi bật là ba thẻ dịch vụ có sẵn; số liệu thống kê nằm trong hero-stats. Giữ nguyên nội dung HTML, thiết kế và các breakpoint của trang nguồn.

Bản trước khi tái cấu trúc được lưu trong original/index.html và original/style.css để đối chiếu.

## Cấu trúc SCSS
```text
scss/
  abstracts/
    _variables.scss
    _mixins.scss
  base/
    _global.scss
  layout/
    _header.scss
    _hero.scss
    _sections.scss
    _footer.scss
    _responsive.scss
  components/
    _buttons.scss
    _statistics.scss
    _dashboard.scss
    _products.scss
    _process.scss
    _testimonials.scss
    _contact.scss
  main.scss
index.html
style.css
original/
package.json
package-lock.json
```

## Kiến thức Sass áp dụng
- Variables: bảng màu và các breakpoint 900px, 768px, 520px trong _variables.scss.
- Nesting: nhóm quy tắc con dưới logo, nav, hero, thống kê, service và footer; các selector đầu ra giữ nguyên độ ưu tiên.
- Mixins: flex-between tái sử dụng bố cục header/footer; shadow tái sử dụng cách khai báo bóng đổ; at-most nhận breakpoint và nội dung qua @content.
- Partials và @use: từng phần giao diện được quản lý độc lập, nạp theo thứ tự gốc trong main.scss để giữ nguyên cascade.
- Các CSS custom properties trong :root cũng được sinh từ biến Sass để giữ bảng màu có sẵn.

## Chạy bài
Mở terminal trong thư mục dự án:
```powershell
npm.cmd ci
npm.cmd run build
```
Mở index.html bằng trình duyệt.

Biên dịch trực tiếp nếu đã cài Sass toàn cục:
```powershell
sass.cmd scss/main.scss style.css --no-source-map
```

Tự biên dịch khi sửa SCSS:
```powershell
npm.cmd run watch
```
Sửa biến hoặc partial rồi lưu, tải lại trang để xem kết quả. Dừng bằng Ctrl+C. style.css là đầu ra biên dịch.

## Kiểm tra
So sánh vị trí, kích thước và các thuộc tính CSS tính toán của toàn bộ phần tử với trang nguồn tại 1440px, 901px, 900px, 769px, 768px, 521px, 520px, 390px và 320px. Kết quả trong verification.txt. Có ảnh desktop.png, tablet.png, mobile.png.

Node.js v22.19.0, Dart Sass 1.105.1. node_modules được bỏ qua khi đưa mã nguồn lên GitHub.

Lưu ý về mẫu nguồn: tại độ rộng 901px, trang gốc có chiều rộng nội dung 906px (tràn 5px). Bản chuyển SCSS giữ nguyên hành vi này để đối chiếu đúng giao diện gốc.
