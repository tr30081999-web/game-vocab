# ConfXP — Luyện từ vựng họp hành

Game luyện từ vựng tiếng Anh công sở, host miễn phí qua **GitHub Pages**, cập nhật từ mới trực tiếp trên GitHub (kể cả từ điện thoại) không cần code.

## 1. Cấu trúc repo

Repo cần đủ các file sau ở thư mục gốc:

```
index.html              ← toàn bộ app (UI, game logic, không cần sửa)
vocab.json               ← danh sách từ vựng, đây là file bạn sẽ cập nhật mỗi ngày
manifest.json             ← cấu hình để "Thêm vào Màn hình chính" có icon + chạy như app riêng
icon-192.png              ← icon app (Android)
icon-512.png              ← icon app (Android, độ phân giải cao)
apple-touch-icon.png      ← icon app (iOS)
README.md                 ← file hướng dẫn này (không bắt buộc nhưng nên có)
```

> Thiếu `manifest.json` / các file icon không sao — app vẫn chạy bình thường, chỉ là khi "Thêm vào Màn hình chính" sẽ không có icon đẹp + không mở full màn hình như app riêng.

## 2. Tạo repo & bật GitHub Pages (làm 1 lần)

1. Vào **github.com** → góc trên phải bấm dấu **+** → **New repository**.
2. Đặt tên ví dụ `confxp-vocab` → chọn **Public** → **Create repository**.
3. Trong repo trống vừa tạo, bấm **uploading an existing file** (hoặc **Add file → Upload files**).
4. Kéo thả TẤT CẢ các file: `index.html`, `vocab.json`, `manifest.json`, `icon-192.png`, `icon-512.png`, `apple-touch-icon.png`, `README.md` vào → **Commit changes**.
5. Vào tab **Settings** (của repo) → mục **Pages** ở sidebar trái.
6. Ở **Build and deployment → Source**, chọn **Deploy from a branch**.
7. **Branch** chọn `main`, thư mục chọn `/ (root)` → **Save**.
8. Đợi khoảng 1 phút, load lại trang Settings → Pages, sẽ thấy dòng:
   `Your site is live at https://<tên-bạn>.github.io/confxp-vocab/`
9. Mở link đó — app chạy y hệt bản offline, nhưng giờ **lưu dữ liệu ổn định** (vì URL cố định, không còn bị lỗi mất dữ liệu như khi mở qua Files app trên Android).
10. **Thêm vào Màn hình chính** trên điện thoại — nhờ có `manifest.json`, icon sẽ là logo tia sét ConfXP thật (không phải icon trình duyệt chung chung), và mở lên sẽ full màn hình như 1 app riêng, không có thanh địa chỉ.

## 3. Cập nhật từ vựng mỗi ngày (việc bạn sẽ làm thường xuyên)

Không cần máy tính, làm thẳng trên điện thoại qua trình duyệt:

1. Vào repo trên GitHub → bấm vào file **vocab.json**.
2. Bấm icon **cây bút chì (Edit)** ở góc phải.
3. Thêm 1 dòng mới vào cuối mảng, đúng định dạng (nhớ dấu `,` ở dòng phía trên nếu thêm vào giữa):
   ```
   "touch base | liên hệ trao đổi nhanh | Can we touch base tomorrow? | Chúng ta trao đổi nhanh được không? | ghi chú"
   ```
   → định dạng y hệt cách dán vào ô textarea trong app: `từ | nghĩa | câu ví dụ EN | dịch câu ví dụ | ghi chú`.
4. Bấm **Commit changes** (góc dưới hoặc trên).
5. Mở lại app (hoặc bấm nút **🔄 Đồng bộ từ GitHub** trong tab Từ vựng nếu app đang mở sẵn) — từ mới sẽ tự xuất hiện.

## 4. Cơ chế đồng bộ hoạt động ra sao

- App tự động fetch `vocab.json` mỗi lần mở trang, **gộp** (merge) vào dữ liệu đang có theo từ tiếng Anh — từ mới thì thêm, từ trùng tên thì cập nhật lại nghĩa/câu ví dụ mới nhất.
- Tiến độ chơi (điểm số, streak, XP, bảng xếp hạng, mức độ thuộc từng từ) **vẫn lưu riêng trên từng trình duyệt/thiết bị** (localStorage), KHÔNG đẩy lên GitHub — vì đây là dữ liệu cá nhân, không cần và không nên public.
- Nếu mở app trên nhiều thiết bị, từ vựng sẽ giống nhau (vì cùng đọc từ `vocab.json`), nhưng điểm số mỗi máy tính riêng.
- Nút **⬇️ Xuất dữ liệu** trong app vẫn dùng để backup tiến độ cá nhân (điểm, XP...) phòng khi đổi máy/đổi trình duyệt.

## 5. Lưu ý

- Repo đang để **Public** nên nội dung `vocab.json` (từ vựng) ai cũng xem được nếu có link — không sao vì không phải dữ liệu nhạy cảm. Muốn private thì cần GitHub Pro (Pages riêng tư không miễn phí với tài khoản cá nhân thường).
- Nếu gõ sai cú pháp JSON (quên dấu `,` hoặc dấu `"`) khi sửa `vocab.json`, app sẽ không đồng bộ được — nhưng dữ liệu local cũ vẫn an toàn, không bị mất, chỉ là không cập nhật từ mới cho tới khi bạn sửa lại đúng cú pháp.
