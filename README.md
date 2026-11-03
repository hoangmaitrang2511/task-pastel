# Task Pastel

Trang theo dõi task theo dự án, có subtask và tiến độ. Theme Sáng (pastel) và Tối (đen, xám).
Mỗi tài khoản (Yin, Vedel) có dữ liệu riêng, lưu trên Firebase và đồng bộ giữa các máy.

Trang web: https://hoangmaitrang2511.github.io/task-pastel/

## Cấu trúc

- `index.html`: toàn bộ giao diện và logic.
- `firebase-config.js`: cấu hình Firebase và danh sách tài khoản (tên hiển thị → email trong Firebase).
- `firestore.rules`: quy tắc bảo mật, mỗi người chỉ đọc và ghi dữ liệu của chính mình.

## Cài Firebase

1. Tạo project tại https://console.firebase.google.com.
2. Authentication → Sign-in method → bật **Email/Password**.
3. Authentication → Users → Add user: `yin@taskpastel.app` và `vedel@taskpastel.app`, mỗi người một mật khẩu.
4. Authentication → Settings → Authorized domains → thêm `hoangmaitrang2511.github.io`.
5. Firestore Database → Create database (production mode), rồi dán nội dung `firestore.rules` vào tab Rules → Publish.
6. Project settings → Your apps → thêm Web app, copy `firebaseConfig` vào `firebase-config.js`.

## Thêm tài khoản

Tạo user mới trong Firebase Authentication, rồi thêm một dòng vào `ACCOUNTS` trong `firebase-config.js`.
Đổi mật khẩu: Firebase console → Authentication → Users → menu ⋮ của user → Reset password.

## Lộ trình

### Đồng bộ hai chiều với Google Calendar (chưa làm)

Hiện mỗi task có hạn chót đều có nút "Thêm vào Google Calendar". Nút này chỉ đẩy một chiều, và bạn phải tự bấm Lưu trên Google Calendar.

Bản đồng bộ hai chiều dự kiến làm như sau:
- Hiện sự kiện từ Google Calendar ngay trên lịch ở phần Tổng quan.
- Tự tạo, sửa và xoá sự kiện khi task được thêm, đổi hạn hoặc xoá.

Cần chuẩn bị trước:
1. Một project trên Google Cloud có bật Google Calendar API. Có thể dùng chính project Firebase `task-pastel`.
2. Cấu hình OAuth consent screen ở chế độ Testing, rồi thêm tài khoản Google của Yin và Vedel vào danh sách test user.
3. Tạo một OAuth Client ID loại Web, có Authorized JavaScript origin là `https://hoangmaitrang2511.github.io`.
4. Mỗi người bấm "Kết nối Google Calendar" một lần trên trang.
