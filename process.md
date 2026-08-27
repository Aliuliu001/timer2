# 📓 PROCESS LOG — Nhật ký thực hiện

> Ghi chép từng bước làm việc. Mỗi task xong thì ghi: ngày, làm gì, kết quả, lệnh git.
> Mục đích: để bạn (và AI sau này) theo dõi được tiến độ mà không cần hỏi lại.

---

## 📌 Thông tin chung
- **Repo:** https://github.com/Aliuliu001/timer2.git
- **Cách chạy local:** mở `index.html` bằng Chrome/Edge (khuyên dùng).
- **Quy tắc git:** commit từng task, push nhánh `main` (khớp cách bạn đang làm).
- **Nguyên tắc:** KHÔNG xóa phần nhập liệu (Cards/Skills/Controls/Students).

---

## 🗓️ Session 1 — Lập kế hoạch (ngày 27/08/2026)
- [x] Tải repo từ GitHub về máy làm việc.
- [x] Đọc hiểu dự án: game "Magic Realm Battle", 3 chế độ (Solo/PvP/Team), web thuần (HTML/CSS/JS).
- [x] Kiểm tra: 10 file JS đều chạy không lỗi.
- [x] Làm rõ yêu cầu với bạn:
  - Mana giữ giới hạn 10.
  - Timer có 2 dạng kỹ năng: Random (cũ) & Buffet (tự mua thanh dưới).
  - Giữ Solo + PvP, bỏ Team.
- [x] Tạo 3 tài liệu: `PLAN.md` (kế hoạch tổng), `TASKS.md` (danh sách task), `process.md` (file này).
- [ ] **Chờ bạn duyệt kế hoạch** → bắt đầu **T1**.

### Ghi chú giả định (cần bạn xác nhận)
- A1: Giữ tab Students (Solo); Timer Hero dùng link riêng.
- A2: 2 đồng hồ = cùng 1 thời gian tổng, hiển thị 2 cách.
- A3: Timer chỉ tick/cross; 2 dạng chỉ cho CÁCH DÙNG KỸ NĂNG.
- A4: WIN = hết giờ & Boss chưa chạm; LOSE = Boss chạm trước.
- A5: commit + push thẳng `main`.

---

## 🗓️ Session 2 — T1: Gỡ Team mode  ✅ HOÀN THÀNH
- [x] **index.html:** xóa card Team, duckrace-screen, team-layout; đổi "Solo & Team Mode"→"Solo Mode"; xóa mục Team turn mode; đổi nhóm phím "Team Mode (Quản Trò)"→"⌨️ Quản Trò (dùng cho Timer)" — **GIỮ NGUYÊN 2 phím Đúng/Sai** (`key-team-correct`/`key-team-wrong`).
- [x] **js/game.js:** xóa hàm `startTeam`/`nextTeamTurn`/`handleTeamAnswer`/`showDuckrace`; xóa rẽ nhánh `mode==='team'` trong handleAnswer, renderCards, speech; xóa duckrace event listeners; đổi "Team keyboard" handler thành "Quản trò keyboard" gọi `handleManualTick` (cho Timer sau này).
- [x] **js/config.js:** xóa `teamTurnMode`; **GIỮ** `teamKeys` (Timer dùng) và `pvpKeys`/`numStudents` (thuộc PvP/Solo, KHÔNG xóa).
- [x] **js/ui.js:** bỏ rẽ nhánh `team` trong renderCards (gộp vào else solo) — tránh crash vì `#team-layout` đã xóa.
- [x] **Bảo vệ:** KHÔNG xóa tab Students/Cards/Skills/Controls. Chỉ xóa đúng code Team/Duckrace.
- [x] **Kiểm tra:** `node --check` 9/9 file OK; load thử toàn bộ game.js trong Node sandbox → không lỗi runtime; không còn gọi hàm team đã xóa.
- [x] **Push:** commit `T1 — remove Team mode, keep PvP/Solo + moderator keys` → main.
- [ ] **Chờ bạn test:** mở game → chỉ còn 2 card (Solo/PvP) → Solo & PvP vẫn chơi bình thường.

> 📌 **Lưu ý cho bạn:** 2 cái đồng hồ & Hero kiểu Boss sẽ làm ở T3/T4. Bây giờ Timer chưa có nút riêng, bấm vào đâu cũng chỉ Solo/PvP thôi — bình thường.

---

## 🗓️ Session 3 — T2: Thêm card Timer
> (sẽ điền)

---

## 🗓️ Session 4 — T3: Layout Timer
> (sẽ điền)

---

## 🗓️ Session 5 — T4: Hero kiểu Boss
> (sẽ điền)

---

## 🗓️ Session 6 — T5: Lật/đảo chiều Boss
> (sẽ điền)

---

## 🗓️ Session 7 — T6: Tick/Cross Timer
> (sẽ điền)

---

## 🗓️ Session 8 — T7: Kỹ năng Timer (Random + Buffet)
> (sẽ điền)

---

## 🗓️ Session 9 — T8: Luật thắng/thua
> (sẽ điền)

---

## 🗓️ Session 10 — T9: Cập nhật Cài đặt
> (sẽ điền)

---

## 🗓️ Session 11 — T10: Chạy thử & Push
> (sẽ điền)
