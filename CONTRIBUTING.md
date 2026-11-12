# Hướng dẫn đóng góp

Áp dụng cho mọi thành viên, kể cả người không quen Git.

## Quy trình ngắn gọn

1. **Nhận thẻ** trên Trello (cột *To Do*), chuyển sang *Doing*.
2. **Tạo nhánh từ `dev`**, tên theo [quy ước nhánh](00-quy-dinh/quy-uoc-nhanh.md), ví dụ `docs/FO-12-quy-tac-gan-nguon`.
3. **Sửa tài liệu**, commit theo [quy ước commit](00-quy-dinh/quy-uoc-commit.md).
4. **Mỗi commit kèm một snapshot** do AI sinh, theo [quy định snapshot](00-quy-dinh/quy-dinh-snapshot.md).
5. **Mở Pull Request vào `dev`**, điền đủ mẫu PR (có link thẻ Trello). Chuyển thẻ sang *Review*.
6. **Chờ duyệt:** cần ít nhất 1 người khác duyệt.
7. **Merge vào `dev`** (môi trường beta). Khi đủ ổn định, người phụ trách mở PR release `dev` → `main` (production).

Chi tiết xem [`00-quy-dinh/flow-lam-viec.md`](00-quy-dinh/flow-lam-viec.md).

## Hai nhánh chính

| Nhánh | Ý nghĩa |
|---|---|
| `main` | Production, bản ổn định |
| `dev` | Beta, bản tích hợp để kiểm thử |

**Không commit trực tiếp** vào hai nhánh này. Luôn đi qua PR.

## Cách sửa trực tiếp trên web GitHub (không cần cài Git)

1. Ở góc trên bên trái, đổi nhánh sang `dev`.
2. Mở file cần sửa, bấm biểu tượng bút chì (Edit).
3. Sửa nội dung.
4. Bấm **Commit changes**, chọn **Create a new branch for this commit and start a pull request**, đặt tên nhánh theo quy ước.
5. Thêm file snapshot cho commit này (xem [quy định snapshot](00-quy-dinh/quy-dinh-snapshot.md)). Trên web, bấm **Add file → Create new file** trên cùng nhánh đó.
6. Điền mẫu PR, chọn nhánh đích là `dev` và bấm **Create pull request**.

## Quy tắc viết tài liệu

- Viết bằng **tiếng Việt có dấu**, câu ngắn, dùng đúng thuật ngữ trong [`glossary.md`](glossary.md).
- Định dạng **Markdown**. Mỗi tài liệu bắt đầu bằng tiêu đề cấp 1 và phần thông tin (người viết, ngày, trạng thái).
- Quy tắc nghiệp vụ dùng mẫu [`templates/quy-tac-nghiep-vu.md`](templates/quy-tac-nghiep-vu.md). Yêu cầu dùng mẫu [`templates/user-story.md`](templates/user-story.md).
- Số liệu và ví dụ phải **giả hoặc đã ẩn danh**. Repo này công khai.
- Điều chưa chắc chắn ghi rõ là **Chưa xác nhận**, kèm người cần xác nhận.
- Nếu một quy tắc cần được code đọc (ngưỡng, danh sách bước phễu), cập nhật cả file `rules.yaml` trong `02-quy-tac/` và báo dev qua thẻ Trello.

## Duyệt PR

Người duyệt kiểm tra:

- Nội dung rõ, không mâu thuẫn với tài liệu khác.
- Có nguồn và ngày cập nhật cho quy tắc.
- Không có dữ liệu thật hoặc thông tin nhạy cảm, kể cả trong snapshot.
- Đúng chính tả và đúng thuật ngữ.
- Tên nhánh, tiêu đề commit đúng quy ước. Mỗi commit có snapshot.
- PR đang trỏ đúng nhánh đích (`dev`, hoặc `main` nếu là release và hotfix).
