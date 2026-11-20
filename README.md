# Theo dõi chi phí BHXH – BHYT – BHTN

**Chạy thử ngay:** https://eng072291.github.io/nous-bhxh-tracker/ (chế độ xem thử, dữ liệu mẫu, không lưu)

Công cụ web một trang (HTML + JavaScript thuần, không cần cài đặt) giúp phòng Hành chính – Nhân sự:

- tính số BHXH, BHYT, BHTN phải đóng của từng người theo tháng (tỷ lệ 32%, sàn/trần lương, quy tắc 14 ngày, BHYT tháng báo giảm, người nước ngoài, người hưởng lương hưu);
- ghi sự kiện tăng, giảm, thai sản, ốm dài ngày, nghỉ không lương, điều chỉnh lương bằng **một form**; tool tự cập nhật bảng tính, biến động và danh sách nhân sự;
- đối chiếu với **danh sách chi tiết** và **thông báo C12-TS** của cơ quan BHXH: chênh lệch theo từng người, theo tháng, lũy kế cả năm;
- kiểm tra số đã nộp (Đ = A + B − C), tiền chậm đóng (0,03%/ngày) và nguyên nhân phát sinh.

## Hai phiên bản trong cùng một trang

| Bản | Mở bằng | Dành cho |
|---|---|---|
| **Bản gọn** (mặc định) | `index.html` hoặc `#thang` | Làm việc hằng tháng: Tháng này · Nhân sự · Đối chiếu cả năm · Nhập số cơ quan |
| **Bản đầy đủ** | `#nhap-lieu` | Tra cứu chi tiết: bảng tính, biến động, đối chiếu từng người, C12, tiền chậm đóng, tham số, quy định |

## Chạy thử

Mở `index.html` bằng trình duyệt. Khi không có kho dữ liệu, trang tự chạy **chế độ xem thử** với 10 nhân sự mẫu (không lưu).

Trang được viết để chạy như một artifact trên claude.ai, nơi dữ liệu được lưu và chia sẻ qua `window.claude.use("db")`. Muốn chạy với kho dữ liệu khác, thay phần `boot()` cuối file bằng lớp lưu trữ của bạn (Firebase, Supabase, API nội bộ…) theo cùng cấu trúc:

| Tài liệu | Nội dung |
|---|---|
| `app/thamso` | tỷ lệ đóng, mức lương tối thiểu vùng, lương cơ sở, tuỳ chọn |
| `app/nhansu` | `{ list: [ {ma, ten, bhxh, pb, cd, dt, ngayVao, ngayNghi, luong} ] }` |
| `ky/YYYY-MM` | `{ cp: [...bảng tính], bd: [...biến động], cq: [...DS cơ quan], c12: {...thông báo C12} }` |
| `app/nguyennhan` | nguyên nhân chênh lệch và tiền lãi theo tháng |
| `app/laicham` | sổ theo dõi tiền chậm đóng |

## Căn cứ pháp lý đã đưa vào tool

Luật BHXH 2024 (41/2024/QH15) · NĐ 158/2025, 188/2025, 274/2025 · NĐ 293/2025 (lương tối thiểu vùng từ 01/01/2026) · NĐ 161/2026 (lương cơ sở 2.530.000 từ 01/07/2026) · QĐ 366/QĐ-BHXH (thay QĐ 595 từ 01/05/2026).

Mức lương và tỷ lệ chỉnh được trong mục **Tỷ lệ & mức lương**. Kiểm tra lại khi có văn bản mới.

## Bảo mật dữ liệu

Kho mã này **không chứa dữ liệu thật**. Không commit file lương, danh sách nhân sự, mã số BHXH hay thông báo C12 vào kho công khai.

## Giấy phép

MIT
