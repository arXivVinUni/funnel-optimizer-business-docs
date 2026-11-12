# FunnelOptimizer – Tài liệu nghiệp vụ

Repo này chứa toàn bộ tài liệu nghiệp vụ của đề tài **FunnelOptimizer AI Agent**: trợ lý phân tích và tối ưu phễu chuyển đổi đa kênh (Quảng cáo → Hội thoại → Đơn hàng → Giao nhận) cho bán lẻ.

Đây là **nguồn sự thật chung** cho các repo code (backend, AI, frontend). Quy tắc nghiệp vụ được viết ở đây trước, code bám theo sau.

## Cấu trúc

| Thư mục | Nội dung |
|---|---|
| [`00-quy-dinh/`](00-quy-dinh/) | Quy định làm việc: flow 2 nhánh `main`/`dev`, quy ước nhánh, quy ước commit, quy định snapshot, Definition of Done |
| [`snapshots/`](snapshots/) | Snapshot do AI sinh cho mỗi commit |
| [`01-nghiep-vu/`](01-nghiep-vu/) | Bài toán, định nghĩa phễu, các kênh |
| [`02-quy-tac/`](02-quy-tac/) | Quy tắc gán nguồn đơn, ngưỡng tin cậy, quy tắc HITL |
| [`03-kich-ban-bao-cao/`](03-kich-ban-bao-cao/) | Script và mẫu báo cáo, mẫu đề xuất hành động |
| [`04-du-lieu/`](04-du-lieu/) | Mô tả schema dữ liệu, quy tắc ẩn danh (không chứa dữ liệu thật) |
| [`05-demo/`](05-demo/) | Kịch bản demo, slide |
| [`templates/`](templates/) | Mẫu user story, mẫu quy tắc nghiệp vụ |
| [`glossary.md`](glossary.md) | Từ điển thuật ngữ dùng chung |

## Bắt đầu

1. Đọc [`CONTRIBUTING.md`](CONTRIBUTING.md) để biết cách đóng góp.
2. Nhận việc trên Trello, rồi làm theo [`00-quy-dinh/flow-lam-viec.md`](00-quy-dinh/flow-lam-viec.md).
3. Có hai nhánh chính: `main` (production) và `dev` (beta). Làm việc trên nhánh tách từ `dev`, mọi thay đổi vào `dev` hoặc `main` đều qua Pull Request.
4. Mỗi commit kèm một snapshot, xem [`00-quy-dinh/quy-dinh-snapshot.md`](00-quy-dinh/quy-dinh-snapshot.md).

## Nguyên tắc nội dung

- **Không đưa dữ liệu thật lên repo** (SĐT khách, số liệu ngân sách, tên khách hàng). Repo này công khai. Ví dụ phải là dữ liệu giả hoặc đã ẩn danh.
- **Mỗi quy tắc nghiệp vụ ghi rõ** người viết, ngày cập nhật và trạng thái (Nháp / Đã duyệt).
- **Tách tính toán và diễn giải:** công thức tài chính (quy đổi tiền tệ, % chi phí/doanh thu) viết dạng xác định, không mơ hồ, vì sẽ được cài thành hàm code, không giao cho LLM.
- **Không suy diễn thiếu căn cứ:** điều gì chưa chắc thì ghi "Chưa xác nhận" thay vì viết như đã chắc.
