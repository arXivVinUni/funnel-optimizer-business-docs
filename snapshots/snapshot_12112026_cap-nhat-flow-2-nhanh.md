# Snapshot: cập nhật flow làm việc với 2 nhánh, quy ước nhánh và commit mở rộng, quy định snapshot

- **Ngày:** 12/11/2026
- **Tác giả:** buianhdung2kar5
- **Nhánh:** main (commit khởi tạo quy định, trước khi tạo `dev`)
- **Thẻ Trello:** Chưa xác nhận (chưa có mã thẻ)
- **Commit:** docs: cập nhật flow 2 nhánh, mở rộng quy ước nhánh và commit, thêm quy định snapshot
- **Commit trước đó:** 02fa47b

## Tóm tắt

Flow làm việc chuyển sang hai nhánh chính: `main` là production, `dev` là beta để dùng khi có hosting. Quy ước đặt tên nhánh và commit được mở rộng thêm nhiều loại, gồm các loại riêng cho đề tài (`data`, `prompt`, `eval`, `rules`, `spike`). Thêm quy định mỗi commit phải có một snapshot do AI sinh, cùng mẫu và prompt để sinh snapshot.

## Lý do

Theo yêu cầu của người phụ trách: cần flow chuẩn chỉ hơn, có tách production và beta, nhiều trường hợp hơn cho nhánh và commit, và có snapshot cho từng commit để nắm bối cảnh.

## File thay đổi

| File | Loại thay đổi | Vai trò |
|---|---|---|
| `00-quy-dinh/flow-lam-viec.md` | Sửa | Flow 2 nhánh, hotfix, release, quy tắc PR và merge |
| `00-quy-dinh/quy-uoc-nhanh.md` | Thêm | Quy ước đặt tên nhánh với nhiều loại |
| `00-quy-dinh/quy-uoc-commit.md` | Sửa | Mở rộng loại, phạm vi, breaking change |
| `00-quy-dinh/quy-dinh-snapshot.md` | Thêm | Quy định vị trí, đặt tên và quy trình snapshot |
| `00-quy-dinh/definition-of-done.md` | Sửa | Thêm điều kiện về nhánh, snapshot, beta |
| `templates/snapshot.md` | Thêm | Mẫu snapshot |
| `templates/prompt-sinh-snapshot.md` | Thêm | Prompt mẫu nhờ AI sinh snapshot |
| `.github/PULL_REQUEST_TEMPLATE.md` | Sửa | Thêm loại PR, nhánh đích, mục snapshot |
| `CONTRIBUTING.md`, `README.md` | Sửa | Cập nhật theo flow mới |
| `snapshots/` | Thêm | Thư mục chứa snapshot, kèm snapshot này |

## Ảnh hưởng

- **Phần khác bị ảnh hưởng:** Mọi repo của tổ chức sẽ áp dụng quy định này.
- **Breaking change:** Không.
- **Cần đồng bộ ở repo khác:** Có. Các repo backend, AI, frontend cần sao chép quy định và chốt thư mục snapshot khi dựng repo.

## Cách kiểm tra

1. Mở `00-quy-dinh/` và kiểm tra các liên kết giữa tài liệu mở được.
2. Đọc lại quy trình trong `flow-lam-viec.md` xem có khớp với `quy-uoc-nhanh.md` và `quy-dinh-snapshot.md`.

## Rủi ro và điểm chưa xác nhận

- Nhánh `dev` chưa tồn tại tại thời điểm commit, sẽ được tạo từ `main` ngay sau commit này.
- Branch protection chưa bật. Cần admin bật trong Settings.
- Cột "Beta" trên bảng Trello có hay không do nhóm quyết định (người xác nhận: người phụ trách).
- Thư mục snapshot của repo frontend (`app/docs/snapshots/` hay `docs/snapshots/`) chưa chốt.

## Việc tiếp theo

- Tạo nhánh `dev`, bật branch protection cho `main` và `dev`.
- Sao chép quy định sang các repo code khi dựng repo.
- Thêm bước CI kiểm tra commit và snapshot (làm sau).
