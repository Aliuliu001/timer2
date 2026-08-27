# 📋 KẾ HOẠCH TỔNG — Thêm chế độ "Timer" & gọn hóa Magic Realm Battle

> Tài liệu này là bản "brainstorm" (nghĩ ra + sắp xếp ý tưởng) tổng thể.
> Đọc hiểu trước khi bắt tay vào làm. Chi tiết từng bước nằm ở `TASKS.md`.
> Nhật ký thực hiện nằm ở `process.md`.

---

## 1. Mục tiêu (viết bằng tiếng người)
Biến game hiện tại thành **gọn hơn** (bỏ hẳn chế độ Team) và thêm một chế độ chơi **MỚI tên là Timer** — đơn giản hóa tối đa:
- Quản trò (người cầm máy) chỉ bấm **Đúng (✓)** hoặc **Sai (✗)**.
- Boss tự động đi tới về phía Hero.
- Hết giờ tổng mà Boss chưa chạm tới Hero → **WIN**.
- Boss chạm Hero trước khi hết giờ → **LOSE**.

---

## 2. Sau khi đổi, game có 3 chế độ
| Chế độ | Trạng thái | Mô tả ngắn |
|--------|-----------|-----------|
| **Solo** | Giữ nguyên | 1 người đấu Boss, có flashcard/quiz |
| **PvP** | Giữ nguyên | 2 người đua trên 1 bàn phím |
| **Timer** | 🆕 MỚI | Quản trò bấm Đúng/Sai, không hiện thẻ câu hỏi |

→ **Xóa hoàn toàn Team mode** (nhẹ code, dễ bảo trì).

---

## 3. Chế độ Timer chi tiết

### 3.1. Màn hình (UI)
- **Arena (sàn đấu) chiếm toàn bộ màn hình** — vì không hiện flashcard/quiz nữa nên rất rộng.
- **Boss nằm bên TRÁI**, đi từ trái sang phải về phía Hero.
- **Hero nằm bên PHẢI**, **đứng yên (cố định)**, được thiết kế **giống hệt Boss** (thả link ảnh từ Pinterest/Google, KHÔNG dùng vòng tròn ảnh học sinh).
- Trên màn hình có **2 thứ HIỂN THỊ KHÁC NHAU** (đã chốt Giả định A2):
  1. 🔢 **⏰ Thời Gian Còn Lại** — số đếm ngược `02:00 → 00:00`. Về 0 = HẾT GIỜ = THẮNG.
  2. 📊 **👹 Boss Đang Tiến Lại** — thanh chạy trái→phải, đo KHOẢNG CÁCH Boss còn cách Hero (đầy = thua). Dùng skill làm chậm Boss thì thanh lùi lại.
  → Một cái là THỜI GIAN, một cái là KHOẢNG CÁCH. Cả 2 chạy cùng lúc tạo kịch tính, học sinh phân biệt ngay.

### 3.2. Cách chơi (luật)
- Boss ban đầu đứng ở trái, sẽ đi tới bên phải với tốc độ nhất định.
- Nếu không ai cản, Boss sẽ chạm Hero đúng lúc hết giờ.
- Quản trò bấm **✓ Đúng** → Hero được **+1 mana** (tối đa 10, giữ nguyên cơ chế cũ).
- Quản trò bấm **✗ Sai** → không cộng mana (có thể reset chuỗi combo).
- Dùng mana để **tung kỹ năng làm chậm/dừng/đẩy lùi Boss** → kéo dài sự sống tới khi hết giờ.

### 3.3. Hai dạng dùng kỹ năng (chọn 1 trong Cài đặt)
| Dạng | Tên | Cách hoạt động |
|------|-----|---------------|
| A | **Random (cũ)** | Hệ thống tự chia ngẫu nhiên thẻ kỹ năng vào tay Hero. Đủ chuỗi 5 lần Đúng → bùng nổ **Combo Pha Lê**. |
| B | **Buffet (tự mua)** | Toàn bộ kỹ năng hiện sẵn ở **thanh dưới màn hình**. Có đủ mana thì click chọn kỹ năng nào tuỳ thích. |

---

## 4. NGUYÊN TẮC BẮT BUỘC (không được phá)
Bạn dặn kỹ: **Giữ nguyên toàn bộ cách nạp input trong Settings, Skills, Controls… KHÔNG được xóa.**
→ Nghĩa là tôi chỉ được:
- ✅ Xóa những gì thuộc riêng về **Team mode**.
- ✅ Thêm mới code cho Timer.
- ✅ Sửa UI của riêng Timer.
- ❌ **KHÔNG** đụng vào: tab Cards (ngân hàng câu hỏi), tab Hero Skills, tab Boss Skills, tab Controls, tab Students (dành cho Solo), và các hàm xử lý chung.

---

## 5. Brainstorm — các lựa chọn đã cân nhắc
- **Có nên gộp Timer vào Solo luôn không?** → Không. Bạn muốn Timer là chế độ riêng (card thứ 3 ở màn hình chọn). Giữ Solo tách biệt để Solo vẫn có flashcard/quiz bình thường.
- **Mana có mở giới hạn không?** → Bạn đã chốt: **Giữ nguyên 10**. Nên Timer dùng lại y hệt cơ chế mana cũ.
- **Hero Timer dùng ảnh học sinh (1.png) hay link?** → Bạn chốt: **dùng link giống Boss**. Nên tôi copy lại cơ chế hiển thị Avatar của Boss sang Hero.
- **Có giữ được code cũ của Solo không?** → Có. Timer sẽ "mượn" lại vòng lặp Solo (Boss đi, Hero dùng skill) rồi sửa vị trí + bỏ câu hỏi. Đỡ phải viết lại từ đầu.

---

## 6. CÁC GIẢ ĐỊNH của Hermes (bạn đọc và sửa nếu sai)
- **A1 — Ảnh Hero:** Giữ tab **Students** (dùng cho Solo). Thêm **1 ô link riêng "Timer Hero"** trong Cài đặt để nhập ảnh Boss-style cho Hero của Timer.
- **A2 — 2 đồng hồ (ĐÃ CHỐT):** Tách thành 2 thông tin KHÁC NHAU để học sinh dễ phân biệt:
  - 🔢 **Số đếm ngược = "⏰ Thời Gian Còn Lại"**: `02:00 → 00:00`. Về 0 = HẾT GIỜ = THẮNG.
  - 📊 **Thanh tiến trình = "👹 Boss Đang Tiến Lại"**: thanh chạy trái→phải, đầy = Boss chạm Hero. Đo KHOẢNG CÁCH Boss còn cách Hero. Dùng skill làm chậm Boss = thanh lùi lại.
  → Một cái là THỜI GIAN, một cái là KHOẢNG CÁCH. Cả 2 chạy cùng lúc.
- **A3 — Tick/cross là duy nhất:** Trong Timer, phần "trả lời" CHỈ dùng tick/cross (không hiện flashcard/quiz). Hai dạng (Random/Buffet) chỉ áp dụng cho **CÁCH DÙNG KỸ NĂNG**, không phải cho câu hỏi.
- **A6 — Giữ phím Quản Trò:** Phím bấm Đúng/Sai của người cầm máy (Controls → "Team Mode (Quản Trò)": Correct=`→`, Wrong=`←`) **PHẢI GIỮ LẠI**, chỉ đổi tên nhóm thành "⌨️ Quản Trò (dùng cho Timer)". Timer sẽ dùng lại 2 phím này. Tuyệt đối không xóa nhầm.
- **A4 — Thắng/Thua:** WIN khi `thời gian còn lại = 0` VÀ Boss chưa chạm Hero. LOSE khi Boss chạm Hero trước khi hết giờ.
- **A5 — Git:** Tôi sẽ commit từng task và **push thẳng lên nhánh `main`** (khớp với cách bạn đang làm trên GitHub), mỗi commit ghi rõ task. Bạn có thể "Back to Menu" chơi ngay sau mỗi lần push.

---

## 7. Thuật ngữ (dành cho bạn, không cần nhớ)
- **Mana (năng lượng):** điểm dùng để tung chiêu, tối đa 10.
- **Combo Pha Lê:** hiệu ứng đặc biệt khi trả lời Đúng liền 5 lần.
- **Layout:** cách bố trí các khối trên màn hình.
- **CSS:** "phần trang điểm" — màu sắc, vị trí, hiệu ứng.
- **Commit / Push:** lưu code lên GitHub.
- **Hardcode:** ghi cứng 1 giá trị vào code (xấu, nên tránh — lấy từ Cài đặt thì tốt hơn).

---

## 8. Thứ tự thực hiện (chi tiết ở TASKS.md)
1. T1 — Gỡ Team mode (UI + logic + cài đặt + css)
2. T2 — Thêm card Timer + nối nút
3. T3 — Layout Timer (arena, đồng hồ, timer)
4. T4 — Hero kiểu Boss (link, phải, trường cài đặt)
5. T5 — Lật / đảo chiều Boss (trái → phải)
6. T6 — Tick/cross cho Timer (+mana)
7. T7 — Kỹ năng Timer: Random + Buffet (thanh dưới tự mua)
8. T8 — Luật thắng/thua + màn hình kết quả
9. T9 — Cập nhật Cài đặt (xóa Team, thêm Timer Hero link + dạng kỹ năng + thời gian)
10. T10 — Chạy thử, sửa lỗi, dọn code, push GitHub

> Làm **từng task một**. Xong task nào, tôi báo cáo + push, bạn xem/thử rồi mới sang task sau.
