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
