# Quy ước commit

Dùng [Conventional Commits](https://www.conventionalcommits.org), viết ngắn gọn.

## Mẫu

```
<loại>: <mô tả ngắn> (<mã-thẻ>)
```

Ví dụ:

```
docs: bổ sung quy tắc gán nguồn theo số điện thoại (FO-12)
fix: sửa sai định nghĩa bước "Giao nhận" (FO-15)
chore: thêm khung thư mục 05-demo (FO-3)
```

## Các loại

| Loại | Ý nghĩa |
|---|---|
| `docs` | Thêm hoặc sửa tài liệu |
| `feat` | Thêm mục nội dung hoặc quy tắc mới |
| `fix` | Sửa sai nội dung, lỗi chính tả quan trọng |
| `refactor` | Sắp xếp lại cấu trúc, không đổi ý nghĩa |
| `chore` | Cấu hình, template, việc phụ trợ |

## Quy tắc

- Mô tả viết bằng tiếng Việt, **không quá 72 ký tự**, không có dấu chấm cuối.
- Mô tả nói rõ **làm gì**, không viết "sửa lỗi", "cập nhật" chung chung.
- Luôn kèm **mã thẻ Trello** trong ngoặc ở cuối.
- Một commit làm một việc.
