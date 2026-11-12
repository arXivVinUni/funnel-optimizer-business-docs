# Flow làm việc

Công việc được **giao và theo dõi trên Trello**. GitHub chỉ chứa nội dung và code, không dùng Issues song song.

Flow này áp dụng cho **mọi repo** của tổ chức (docs, backend, AI, frontend).

## 1. Hai nhánh chính

| Nhánh | Môi trường | Ý nghĩa | Ai được đẩy vào |
|---|---|---|---|
| `main` | **Production** | Bản ổn định, đã qua beta, là bản được hosting phục vụ người dùng thật | Chỉ qua PR từ `dev` (hoặc `hotfix/*`) |
| `dev` | **Beta (staging)** | Bản tích hợp, dùng để kiểm thử trước khi lên production | Chỉ qua PR từ nhánh làm việc |

Quy tắc cứng:

- **Không commit trực tiếp** vào `main` hay `dev` (trừ commit khởi tạo repo).
- `main` và `dev` phải bật **branch protection**: bắt buộc PR, bắt buộc duyệt, không force push.
- Khi có hosting: `dev` tự động deploy lên môi trường **beta**, `main` tự động deploy lên **production**.
- `main` luôn là tập con "đã kiểm chứng" của `dev`. Không để `main` chứa thứ chưa từng qua `dev`, trừ hotfix.

```
feature/*  ──PR──►  dev (beta)  ──PR release──►  main (production)
                      ▲                              │
                      └──── hotfix/* ◄───────────────┘
                      (hotfix tách từ main, merge về main rồi merge ngược về dev)
```

## 2. Luồng làm việc bình thường

1. Nhận thẻ Trello (cột **To Do**), chuyển sang **Doing**, gán tên mình.
2. Cập nhật `dev` mới nhất, **tạo nhánh làm việc từ `dev`** theo [quy ước đặt tên](quy-uoc-nhanh.md).
3. Làm việc, commit nhỏ theo [quy ước commit](quy-uoc-commit.md). **Mỗi commit kèm một snapshot** theo [quy định snapshot](quy-dinh-snapshot.md).
4. Đẩy nhánh, mở **PR vào `dev`**, điền mẫu PR (có link thẻ Trello). Chuyển thẻ sang **Review**.
5. Có **ít nhất 1 người khác** duyệt và các kiểm tra tự động (nếu có) đều xanh.
6. Merge vào `dev`. Thẻ sang **Beta** (nếu bảng có cột này) hoặc **Done** theo quy định của nhóm.
7. Kiểm thử trên beta. Khi đủ ổn định, mở **PR release** từ `dev` vào `main`.
8. Merge vào `main` tạo bản production. Gắn tag phiên bản (xem mục 5). Thẻ sang **Done**.

## 3. Vòng đời thẻ Trello

| Cột | Khi nào | Việc cần làm |
|---|---|---|
| **To Do** | Thẻ được giao | Đọc yêu cầu, hỏi lại nếu chưa rõ |
| **Doing** | Bắt đầu làm | Tạo nhánh từ `dev`, tự gán tên vào thẻ |
| **Review** | Đã mở PR vào `dev` | Dán link PR vào thẻ, báo người duyệt |
| **Beta** | PR đã merge vào `dev` | Kiểm thử trên môi trường beta |
| **Done** | Đã lên `main` (production) hoặc tài liệu đã duyệt xong | Kiểm tra theo [Definition of Done](definition-of-done.md) |

Nếu bị chặn, ghi rõ lý do vào thẻ và gắn nhãn **Blocked**.

## 4. Pull Request

- Một PR chỉ làm **một việc**, gắn với **một thẻ Trello**.
- **Đích PR:**
  - Nhánh làm việc → `dev`.
  - `dev` → `main` (PR release).
  - `hotfix/*` → `main`, sau đó merge ngược `main` → `dev`.
- Điền đủ mẫu PR, bắt buộc có **link thẻ Trello**.
- Cần **ít nhất 1 người khác** duyệt. Không tự duyệt PR của mình. PR release vào `main` cần **người phụ trách repo** duyệt.
- Người duyệt phản hồi trong **1 ngày làm việc**. Quá hạn thì nhắc trên thẻ Trello.
- **Cách merge:**
  - Nhánh làm việc → `dev`: **Squash and merge**, tiêu đề PR theo [quy ước commit](quy-uoc-commit.md). Giữ lại các snapshot đã sinh (xem [quy định snapshot](quy-dinh-snapshot.md)).
  - `dev` → `main`: **Create a merge commit** để giữ lịch sử release.
  - `main` → `dev` (đồng bộ sau hotfix): **Create a merge commit**.
- Xóa nhánh làm việc sau khi merge. Không xóa `main` và `dev`.

## 5. Phát hành và gắn phiên bản

- Mỗi lần merge `dev` → `main` gắn tag theo [Semantic Versioning](https://semver.org): `vMAJOR.MINOR.PATCH`, ví dụ `v1.2.0`.
- Nhánh `release/vX.Y.Z` (tuỳ chọn) dùng khi cần "đóng băng" `dev` để chỉnh lần cuối trước khi lên `main`.
- Ghi các thay đổi chính vào `CHANGELOG.md` theo [Keep a Changelog](https://keepachangelog.com) khi phát hành.

## 6. Hotfix (sửa gấp trên production)

1. Tạo nhánh `hotfix/<mã-thẻ>-mo-ta` **từ `main`**.
2. Sửa tối thiểu, có snapshot, mở PR vào `main`, duyệt khẩn (vẫn cần 1 người).
3. Sau khi merge và gắn tag PATCH (ví dụ `v1.2.1`), **merge ngược `main` vào `dev`** để `dev` không mất bản sửa.
4. Ghi rõ nguyên nhân vào thẻ Trello và snapshot.

## 7. Giữ nhánh sạch

- Mỗi sáng hoặc trước khi làm tiếp, kéo `dev` mới nhất và rebase hoặc merge vào nhánh của bạn nếu nhánh sống quá 2 ngày.
- Nhánh làm việc nên sống **ngắn** (tối đa khoảng 3 ngày). Việc lớn thì chia thẻ nhỏ.
- Nhánh không hoạt động quá 14 ngày: hỏi người phụ trách rồi xóa hoặc hoàn thành.

## 8. Quy tắc ứng xử khi làm chung

- Mâu thuẫn nghiệp vụ giữa hai tài liệu: dừng lại, ghi vào thẻ Trello, hỏi người phụ trách nghiệp vụ. Không tự chọn một bên.
- Thay đổi quy tắc đã **Đã duyệt** phải có thẻ Trello riêng và lý do thay đổi.
- Thay đổi ảnh hưởng tới code (ngưỡng, định nghĩa bước phễu, công thức): tạo thẻ Trello cho dev và dán link PR.
- **Bí mật và dữ liệu thật** (API key, SĐT khách, số liệu ngân sách) tuyệt đối không commit, kể cả trong snapshot. Phát hiện lỡ commit thì báo ngay trên Trello, xử lý theo hướng thu hồi khoá, không chỉ xoá commit.
