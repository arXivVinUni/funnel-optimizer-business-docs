# Quy ước đặt tên nhánh

## Mẫu

```
<loại>/<mã-thẻ>-<mô-tả-ngắn>
```

- Chữ thường, **không dấu**, nối bằng dấu gạch ngang.
- Mã thẻ là mã trên Trello, ví dụ `FO-12`. Việc không có thẻ thì **không làm**, trừ hotfix khẩn (tạo thẻ bổ sung ngay sau đó).
- Mô tả ngắn 2 đến 5 từ, nói rõ làm gì.
- Tổng độ dài tên nhánh nên dưới 60 ký tự.

## Các loại nhánh

### Nhánh làm việc thông dụng (tách từ `dev`)

| Loại | Dùng cho | Ví dụ |
|---|---|---|
| `feat` | Thêm tính năng hoặc nội dung mới | `feat/FO-12-man-hinh-duyet-hitl` |
| `fix` | Sửa lỗi (không gấp) | `fix/FO-15-sai-quy-doi-tien-te` |
| `docs` | Chỉ thay đổi tài liệu | `docs/FO-20-quy-tac-gan-nguon` |
| `refactor` | Tổ chức lại code, không đổi hành vi | `refactor/FO-22-tach-module-finance` |
| `perf` | Cải thiện hiệu năng | `perf/FO-25-tang-toc-doi-chieu-sdt` |
| `test` | Thêm hoặc sửa test | `test/FO-27-test-ham-ty-le-chi-phi` |
| `style` | Định dạng, không đổi logic (format, lint) | `style/FO-28-format-theo-prettier` |
| `build` | Hệ thống build, thư viện phụ thuộc | `build/FO-30-nang-cap-fastapi` |
| `ci` | Pipeline CI/CD, GitHub Actions | `ci/FO-31-them-workflow-test` |
| `chore` | Việc phụ trợ, cấu hình, dọn dẹp | `chore/FO-32-cap-nhat-gitignore` |
| `revert` | Hoàn tác một thay đổi trước đó | `revert/FO-33-hoan-tac-quy-tac-gan-nguon-02` |

### Nhánh đặc thù cho đề tài

| Loại | Dùng cho | Ví dụ |
|---|---|---|
| `data` | Dữ liệu mẫu, script ẩn danh, schema | `data/FO-40-sinh-du-lieu-gia-don-hang` |
| `prompt` | Sửa prompt hoặc luồng suy luận của agent | `prompt/FO-41-chinh-prompt-gan-nguon` |
| `eval` | Đánh giá, calibration, backtest | `eval/FO-42-do-ece-tren-du-lieu-that` |
| `rules` | Thay đổi quy tắc nghiệp vụ máy đọc được (`rules.yaml`) | `rules/FO-43-doi-nguong-tin-cay` |
| `spike` | Thử nghiệm ngắn tìm hiểu giải pháp, **không merge thẳng** | `spike/FO-44-thu-langgraph-checkpoint` |
| `demo` | Chuẩn bị demo, slide, kịch bản | `demo/FO-45-kich-ban-demo-cuoi-ky` |

### Nhánh quy trình đặc biệt

| Loại | Tách từ | Vào | Ví dụ |
|---|---|---|---|
| `hotfix` | `main` | `main`, sau đó merge ngược về `dev` | `hotfix/FO-50-loi-tinh-tien-production` |
| `release` | `dev` | `main` (và merge ngược `dev` nếu có chỉnh) | `release/v1.2.0` |

Nhánh `release/*` không có mã thẻ, dùng số phiên bản theo SemVer.

## Quy tắc thêm

- **Nhánh `spike`** là để học hỏi. Kết quả đưa vào tài liệu hoặc thẻ Trello, sau đó mở nhánh `feat/*` mới nếu quyết định làm thật. Không merge nhánh `spike` vào `dev`.
- Nhánh **không có loại hợp lệ** sẽ bị người duyệt yêu cầu đổi tên.
- Nếu một việc đi kèm nhiều loại (vừa `feat` vừa `refactor`), chọn loại **chính** hoặc tách thành hai PR.
- Không dùng tên cá nhân hay tên chung chung làm tên nhánh: `tien-test`, `new-branch`, `fix-bug`, `update`.
- Không đặt nhánh ngang hàng với nhánh chính như `main-2`, `dev-new`.
