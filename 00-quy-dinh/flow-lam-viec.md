# Flow làm việc

Công việc được **giao và theo dõi trên Trello**. GitHub chỉ chứa nội dung và code, không dùng Issues song song.

## Quy trình nhánh: GitHub Flow

- `main` luôn ở trạng thái ổn định, đã được duyệt.
- Mọi thay đổi làm trên **nhánh riêng** tách từ `main`, rồi vào `main` qua **Pull Request**.
- Không commit trực tiếp vào `main` (trừ commit khởi tạo repo).

### Đặt tên nhánh

```
<loại>/<mã-thẻ>-mo-ta-ngan
```

| Loại | Dùng cho |
|---|---|
| `docs` | Thay đổi tài liệu |
| `feat` | Thêm nội dung hoặc tính năng mới |
| `fix` | Sửa lỗi, sửa sai nội dung |
| `chore` | Việc lặt vặt (cấu trúc thư mục, cấu hình) |

Ví dụ: `docs/FO-12-quy-tac-gan-nguon`. Dùng chữ thường, không dấu, nối bằng dấu gạch ngang.

## Vòng đời thẻ Trello

| Cột | Khi nào | Việc cần làm |
|---|---|---|
| **To Do** | Thẻ được giao | Đọc yêu cầu, hỏi lại nếu chưa rõ |
| **Doing** | Bắt đầu làm | Tạo nhánh theo quy ước, tự gán tên mình vào thẻ |
| **Review** | Đã mở PR | Dán link PR vào thẻ, báo người duyệt |
| **Done** | PR đã được duyệt và merge | Kiểm tra theo [Definition of Done](definition-of-done.md) |

Nếu bị chặn, ghi rõ lý do vào thẻ và gắn nhãn **Blocked**.

## Pull Request

- Một PR chỉ làm **một việc**, gắn với **một thẻ Trello**.
- Điền đủ mẫu PR, bắt buộc có **link thẻ Trello**.
- Cần **ít nhất 1 người khác** duyệt. Không tự duyệt PR của mình.
- Người duyệt phản hồi trong vòng **1 ngày làm việc**. Nếu quá hạn, nhắc trên thẻ Trello.
- Khi merge, chọn **Squash and merge** để lịch sử gọn, và đặt tiêu đề theo [quy ước commit](quy-uoc-commit.md).
- Xóa nhánh sau khi merge.

## Quy tắc ứng xử khi làm chung

- Mâu thuẫn nghiệp vụ giữa hai tài liệu: dừng lại, ghi vào thẻ Trello, hỏi người phụ trách nghiệp vụ. Không tự chọn một bên.
- Thay đổi quy tắc đã **Đã duyệt** phải có thẻ Trello riêng và lý do thay đổi.
- Thay đổi ảnh hưởng tới code (ngưỡng, định nghĩa bước phễu, công thức): tạo thẻ Trello cho dev và dán link PR.
