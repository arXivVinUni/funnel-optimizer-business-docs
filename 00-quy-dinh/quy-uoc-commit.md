# Quy ước commit

Dùng [Conventional Commits](https://www.conventionalcommits.org), viết bằng tiếng Việt, ngắn gọn.

## Mẫu

```
<loại>(<phạm vi>): <mô tả ngắn> (<mã-thẻ>)

<nội dung chi tiết, tuỳ chọn>

<chân trang, tuỳ chọn>
```

- **Loại**: bắt buộc, xem bảng dưới.
- **Phạm vi**: tuỳ chọn, cho biết phần nào bị ảnh hưởng (xem bảng phạm vi).
- **Mô tả ngắn**: bắt buộc, tiếng Việt, **tối đa 72 ký tự**, bắt đầu bằng động từ, không dấu chấm cuối.
- **Mã thẻ Trello**: bắt buộc, trong ngoặc ở cuối dòng đầu.
- **Nội dung chi tiết**: giải thích **vì sao** thay đổi. Cách làm tự thấy qua diff. Cách dòng trống với dòng đầu.
- **Chân trang**: breaking change, liên kết, đồng tác giả.

Ví dụ:

```
feat(ai): thêm độ tin cậy cho kết quả gán nguồn đơn (FO-12)

Mỗi đơn được gán nguồn đều có điểm tin cậy từ 0 đến 1. Đơn dưới ngưỡng
trong rules.yaml đưa vào hàng đợi duyệt HITL thay vì tự áp dụng.
```

## Các loại commit

| Loại | Ý nghĩa | Ví dụ |
|---|---|---|
| `feat` | Tính năng hoặc nội dung mới | `feat(fe): thêm trang duyệt đơn gán nguồn (FO-12)` |
| `fix` | Sửa lỗi | `fix(finance): sửa làm tròn khi quy đổi VND sang USD (FO-15)` |
| `docs` | Chỉ thay đổi tài liệu | `docs: bổ sung quy tắc gán nguồn theo SĐT (FO-20)` |
| `style` | Định dạng, không đổi logic | `style(be): format code theo ruff (FO-28)` |
| `refactor` | Tổ chức lại code, không đổi hành vi | `refactor(ai): tách module attribution (FO-22)` |
| `perf` | Cải thiện hiệu năng | `perf(ai): đối chiếu SĐT bằng chỉ mục băm (FO-25)` |
| `test` | Thêm hoặc sửa test | `test(finance): thêm ca biên cho % chi phí/doanh thu (FO-27)` |
| `build` | Build, thư viện phụ thuộc | `build(be): nâng cấp FastAPI lên bản mới (FO-30)` |
| `ci` | CI/CD, GitHub Actions | `ci: thêm workflow chạy test khi mở PR (FO-31)` |
| `chore` | Việc phụ trợ, cấu hình | `chore: thêm mục data/real vào .gitignore (FO-32)` |
| `revert` | Hoàn tác commit trước | `revert: hoàn tác "feat(ai): đổi ngưỡng tin cậy" (FO-33)` |
| `data` | Dữ liệu mẫu, schema, script ẩn danh | `data(ai): sinh dữ liệu giả cho 500 đơn hàng (FO-40)` |
| `prompt` | Prompt hoặc luồng suy luận của agent | `prompt(agent): thêm yêu cầu trích dẫn căn cứ (FO-41)` |
| `eval` | Đánh giá, calibration, backtest | `eval(calibration): thêm đo ECE theo từng kênh (FO-42)` |
| `rules` | Quy tắc nghiệp vụ máy đọc được | `rules: nâng ngưỡng tin cậy HITL lên 0.7 (FO-43)` |
| `snapshot` | Chỉ thêm hoặc sửa snapshot (hiếm khi cần) | `snapshot: bổ sung snapshot còn thiếu (FO-12)` |
| `release` | Phát hành phiên bản | `release: v1.2.0` |
| `hotfix` | Sửa gấp trên production | `hotfix(finance): sửa sai tỷ giá production (FO-50)` |

## Các phạm vi gợi ý

| Phạm vi | Dùng cho |
|---|---|
| `fe`, `be`, `ai`, `docs` | Phần lớn của từng repo |
| `finance` | Hàm tài chính xác định (quy đổi tiền tệ, % chi phí) |
| `attribution` | Gán nguồn đơn |
| `agent` | Luồng LangGraph, nodes, prompt |
| `calibration` | Đánh giá độ hiệu chuẩn của dự báo |
| `hitl` | Hàng đợi và màn hình duyệt |
| `anonymize` | Ẩn danh dữ liệu |
| `auth`, `api`, `db` | Hạ tầng Backend |
| `ui`, `chart` | Giao diện, biểu đồ |

Phạm vi có thể thêm theo nhu cầu. Một repo dùng thống nhất một tên cho một phần.

## Breaking change

Đánh dấu bằng `!` sau loại và ghi chân trang `BREAKING CHANGE:`:

```
feat(api)!: đổi định dạng trả về của /funnel (FO-60)

BREAKING CHANGE: trường "drop_rate" đổi từ phần trăm sang số thập phân 0..1.
Frontend cần cập nhật trước khi lên production.
```

## Chân trang thường dùng

- `Refs: <link thẻ Trello>`: liên kết thêm.
- `Co-Authored-By: <tên> <email>`: khi làm chung hoặc có AI hỗ trợ.
- `BREAKING CHANGE: ...`: xem trên.

## Quy tắc

- **Một commit làm một việc.** Việc nhỏ, commit nhỏ.
- Mỗi commit đều **kèm một snapshot** theo [quy định snapshot](quy-dinh-snapshot.md).
- Mô tả nói rõ **làm gì**. Không viết "sửa lỗi", "cập nhật", "fix", "update" chung chung.
- **Không commit** dữ liệu thật, khoá API, file `.env`.
- Commit `merge` do GitHub tạo khi merge PR vào `main` hoặc `dev` được miễn quy ước và miễn snapshot.
- Khi squash and merge, **tiêu đề PR trở thành commit** nên cũng phải theo quy ước này.

## Kiểm tra tự động (khuyến nghị)

Từng repo code nên thêm công cụ kiểm tra commit (ví dụ `commitlint`) trong CI để chặn commit sai quy ước.
