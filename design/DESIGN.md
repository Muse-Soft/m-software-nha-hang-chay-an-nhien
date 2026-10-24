# Thiết kế giao diện — Nhà hàng chay An Nhiên (TEC-68)

> Bản bàn giao cho Dev triển khai. Thuộc Epic TEC-67, yêu cầu web MSR-10.
> LƯU Ý NỘI DUNG: địa chỉ và số điện thoại thật CHƯA có trong issue nên bản này dùng
> placeholder rõ ràng (xem mục 7). Thực đơn và giá dưới đây là NỘI DUNG MẪU để duyệt
> bố cục — chủ quán/PO xác nhận lại trước khi public. Không tự ý coi giá mẫu là giá thật.

## 1. Tông & cảm giác
- Tông: nâu gỗ + xanh rêu, thanh tịnh, ấm, nhẹ.
- Cảm giác cần đạt trong 3 giây đầu: yên tĩnh, sạch, nhiều cây xanh, đồ chay ngon.
- Tránh: màu chói, chữ dày đặc, ảnh tối, hiệu ứng nhấp nháy.

## 2. Design tokens (Dev dùng đúng mã này)
| Token | Giá trị | Dùng cho |
|---|---|---|
| `--wood` | `#7B5B3A` (nâu gỗ) | Tiêu đề, nút chính, viền nhấn |
| `--wood-dark` | `#5C4226` | Header, footer, chữ nhấn đậm |
| `--moss` | `#5F7A5A` (xanh rêu) | Nhãn, badge chay, link, nút phụ |
| `--moss-light` | `#E7EDE3` | Nền section xen kẽ |
| `--cream` | `#FAF6EF` | Nền chính |
| `--paper` | `#FFFFFF` | Thẻ món, thẻ combo |
| `--ink` | `#2E2A24` | Chữ chính |
| `--muted` | `#7A7166` | Chữ phụ, giá cũ |
| `--gold` | `#C9A86A` | Đường viền mỏng trang trí, giá nổi bật |

- Font: tiêu đề — serif thanh lịch (ví dụ "Playfair Display" hoặc serif hệ thống);
  thân bài — sans dễ đọc (ví dụ "Be Vietnam Pro" / sans hệ thống). Dự phòng font hệ thống
  nếu không tải được webfont, không được vỡ bố cục.
- Bo góc: thẻ 16px, nút 999px (pill). Bóng thẻ nhẹ, không bóng đậm.
- Khoảng cách: section cách nhau 56px (mobile) / 80px (desktop); thẻ cách nhau 16px.

## 3. Bố cục trang chủ (theo thứ tự từ trên xuống)
1. **Header dính (sticky):** logo "An Nhiên — Ẩm thực chay", menu: Thực đơn | Combo |
   Đặt bàn | Không gian | Liên hệ. Nút chính: "Đặt bàn".
2. **Hero:** ảnh không gian xanh (placeholder), tiêu đề "Ăn chay, lòng an nhiên",
   dòng phụ 1 câu về rau tươi nấu mỗi ngày, 2 nút: "Xem thực đơn hôm nay" + "Đặt bàn".
   Dưới hero: dải tin nhanh — "Mở cửa 10:00–22:00 hằng ngày" + "Gọi điện" (placeholder, mục 7).
3. **Thực đơn theo ngày:** tiêu đề + chọn ngày (7 nút Thứ 2–Chủ nhật, mặc định hôm nay).
   Trong mỗi ngày, 3 nhóm có tiêu đề riêng: Khai vị | Món chính | Tráng miệng.
   Mỗi món = 1 dòng/thẻ: tên món, mô tả ngắn 1 dòng, giá, badge (ví dụ "Món chay",
   "Cay nhẹ", "Bán chạy") khi cần. Xem mẫu đầy đủ trong `index.html`.
4. **Combo gia đình:** 3 thẻ ngang hàng (mobile xếp dọc): Combo 2 người / 4 người /
   6 người, mỗi thẻ ghi: giá, số món, món gồm những gì, nút "Đặt combo này"
   (dẫn tới form đặt bàn, tự điền sẵn combo đã chọn).
5. **Mục đặt bàn:** form gồm: họ tên, số điện thoại, ngày, giờ (giới hạn 10:00–22:00),
   số khách, chọn combo (không bắt buộc), ghi chú (ăn kiêng/dị ứng). Nút gửi:
   "Gửi yêu cầu đặt bàn". Dưới form ghi rõ: "Nhà hàng sẽ gọi lại xác nhận.
   Giờ mở cửa 10:00–22:00." (Chưa có backend: Dev lưu form ở giai đoạn sau theo
   task backend riêng; bản này chỉ bàn giao giao diện + validation phía trình duyệt.)
6. **Giới thiệu không gian:** 3 khối: "Sân vườn nhiều cây", "Phòng riêng yên tĩnh",
   "Góc trà & đọc sách" — mỗi khối 1 ảnh placeholder + 2 câu mô tả. Kèm câu chuyện
   ngắn 3–4 câu về triết lý nấu chay của quán.
7. **Footer / Liên hệ:** địa chỉ (placeholder), giờ mở cửa 10:00–22:00 hằng ngày,
   nút "Gọi điện" nổi bật, link: Thực đơn | Đặt bàn | Không gian.
8. **Nút gọi điện nổi trên mobile:** thanh dính dưới cùng chỉ hiện ở mobile, gồm
   2 nút: "Gọi điện" và "Đặt bàn", để người dùng không phải cuộn lên đầu trang.

## 4. Thực đơn mẫu (để duyệt bố cục — xác nhận lại trước khi public)
Xem bản đầy đủ, theo từng ngày, trong `index.html` (tab Thứ 2–Chủ nhật).
Khung mẫu mỗi ngày: 2 khai vị, 3 món chính, 2 tráng miệng.
Ví dụ ngày mẫu: Gỏi cuốn rau củ (45.000đ), Súp bí đỏ (39.000đ); Cơm sen nấm
(75.000đ), Lẩu nấm An Nhiên (129.000đ/người), Đậu hũ sốt nấm (69.000đ);
Chè sen long nhãn (35.000đ), Rau câu dừa (29.000đ).
Combo mẫu: 2 người 299.000đ · 4 người 499.000đ · 6 người 699.000đ.

## 5. Responsive — ưu tiên mobile (mobile-first)
| Breakpoint | Bố cục |
|---|---|
| < 640px (mobile, mặc định) | 1 cột toàn trang; menu header thu thành nút ☰; thẻ món xếp dọc; form full chiều rộng; thanh Gọi/Đặt bàn dính dưới cùng; chữ thân bài tối thiểu 16px, tiêu đề section 24px |
| 640–1023px (tablet) | Lưới món 2 cột; combo 2 cột (thẻ thứ 3 xuống hàng); không gian 2 cột |
| ≥ 1024px (desktop) | Nội dung tối đa 1120px, căn giữa; lưới món 3 cột; combo 3 cột; không gian 3 cột; hero 2 cột (chữ + ảnh) |

- Ảnh: dùng `aspect-ratio` cố định, không để ảnh làm lệch bố cục khi tải chậm.
- Chạm: nút và ô nhập cao tối thiểu 44px; khoảng cách giữa các nút đủ để không bấm nhầm.
- Dễ đọc: độ tương phản chữ/nền đạt chuẩn đọc thường; không dùng chữ màu nhạt trên
  nền nhạt; giá luôn đứng riêng, không chìm trong mô tả.

## 6. Checklist Dev triển khai
- [ ] Đúng thứ tự 8 khối ở mục 3, đúng tokens ở mục 2.
- [ ] Mobile-first, kiểm tra ở 360px, 768px, 1280px.
- [ ] Tab ngày đổi được thực đơn; combo đã chọn tự điền vào form đặt bàn.
- [ ] Giờ đặt bàn chỉ cho 10:00–22:00; số điện thoại validate đủ số.
- [ ] Thay placeholder địa chỉ/số điện thoại (mục 7) bằng thông tin thật trước khi public.
- [ ] Thay ảnh placeholder bằng ảnh thật của quán trước khi public.

## 7. Placeholder bắt buộc thay trước khi public
- Địa chỉ: `[ĐỊA CHỈ — chờ PO/chủ quán cung cấp]` (trong `index.html` ghi là
  "Địa chỉ: đang cập nhật — vui lòng gọi điện xác nhận").
- Số điện thoại: `[SỐ ĐIỆN THOẠI — chờ PO cung cấp]` — nút "Gọi điện" hiện trỏ
  tới `#lien-he`, Dev thay bằng `tel:<số thật>` khi có số.
- Ảnh: toàn bộ ảnh trong prototype là ảnh placeholder (picsum) — thay bằng ảnh thật.
- Giá món/combo: nội dung mẫu, xác nhận lại với chủ quán.
