# Hướng dẫn đóng góp

Áp dụng cho mọi thành viên, kể cả người không quen Git.

## Quy trình ngắn gọn

1. **Nhận thẻ** trên Trello (cột *To Do*), chuyển sang *Doing*.
2. **Tạo nhánh** từ `main`, tên theo mẫu `docs/<mã-thẻ>-mo-ta-ngan`, ví dụ `docs/FO-12-quy-tac-gan-nguon`.
3. **Sửa tài liệu**, commit theo [quy ước commit](00-quy-dinh/quy-uoc-commit.md).
4. **Mở Pull Request** vào `main`, điền đủ mẫu PR (có link thẻ Trello). Chuyển thẻ sang *Review*.
5. **Chờ duyệt:** cần ít nhất 1 người khác duyệt.
6. **Merge**, rồi chuyển thẻ sang *Done*.

Chi tiết xem [`00-quy-dinh/flow-lam-viec.md`](00-quy-dinh/flow-lam-viec.md).

## Cách sửa trực tiếp trên web GitHub (không cần cài Git)

1. Mở file cần sửa, bấm biểu tượng bút chì (Edit).
2. Sửa nội dung.
3. Bấm **Commit changes**, chọn **Create a new branch for this commit and start a pull request**, đặt tên nhánh theo quy ước.
4. Điền mẫu PR và bấm **Create pull request**.

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
- Không có dữ liệu thật hay thông tin nhạy cảm.
- Đúng chính tả và đúng thuật ngữ.
