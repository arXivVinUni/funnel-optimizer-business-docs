## Thẻ Trello

<!-- Bắt buộc. Dán link thẻ Trello -->

## Loại PR và nhánh đích

- [ ] Nhánh làm việc → `dev`
- [ ] Release: `dev` → `main`
- [ ] Hotfix: `hotfix/*` → `main` (nhớ merge ngược `main` → `dev`)

## Thay đổi gì

<!-- Mô tả ngắn gọn bạn đã thêm hoặc sửa gì -->

## Vì sao

<!-- Lý do, bối cảnh -->

## Checklist

- [ ] Tên nhánh theo quy ước (`<loại>/<mã-thẻ>-...`), tách từ `dev`
- [ ] Tiêu đề PR và các commit theo quy ước (`<loại>(<phạm vi>): ... (<mã-thẻ>)`)
- [ ] **Mỗi commit có snapshot** trong thư mục snapshot, đã đọc lại sau khi AI sinh
- [ ] Có người viết, ngày cập nhật, trạng thái (với tài liệu)
- [ ] Có nguồn hoặc căn cứ, chỗ chưa chắc ghi **Chưa xác nhận**
- [ ] Dùng đúng thuật ngữ trong `glossary.md`
- [ ] **Không có dữ liệu thật hay khoá API** (SĐT, tên khách, ngân sách), kể cả trong snapshot
- [ ] Nếu đổi quy tắc mà code cần đọc: đã cập nhật `rules.yaml` và tạo thẻ cho dev
- [ ] Đã chuyển thẻ Trello sang **Review** và dán link PR vào thẻ

## Cách kiểm tra

<!-- Người duyệt kiểm tra thế nào? Với repo code: lệnh chạy test, cách thử trên beta -->
