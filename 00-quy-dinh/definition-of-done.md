# Definition of Done

Một thẻ Trello chỉ được chuyển sang **Done** khi đáp ứng đủ các điều kiện dưới đây.

## Chung cho mọi thẻ

- [ ] Nội dung đúng với yêu cầu trong thẻ Trello.
- [ ] Nhánh làm việc tách từ `dev`, tên đúng [quy ước nhánh](quy-uoc-nhanh.md).
- [ ] Commit đúng [quy ước commit](quy-uoc-commit.md) và **mỗi commit có snapshot** theo [quy định snapshot](quy-dinh-snapshot.md).
- [ ] Snapshot đã được người commit đọc lại, không có dữ liệu thật hay bí mật.
- [ ] PR đã được **ít nhất 1 người khác** duyệt và merge vào `dev`.
- [ ] Link PR nằm trong thẻ Trello.
- [ ] Đã kiểm thử trên **beta** (với repo code). Việc lên `main` (production) được người phụ trách quyết định qua PR release.

## Với tài liệu nghiệp vụ

- [ ] Dùng đúng mẫu trong `templates/` (nếu có mẫu phù hợp).
- [ ] Có **người viết, ngày cập nhật, trạng thái**.
- [ ] Có **nguồn hoặc căn cứ** cho số liệu và quy tắc. Chỗ chưa chắc được đánh dấu **Chưa xác nhận**.
- [ ] Dùng đúng thuật ngữ trong `glossary.md`. Thuật ngữ mới đã được thêm vào đó.
- [ ] Không chứa dữ liệu thật (SĐT, tên khách, số liệu ngân sách).
- [ ] Không mâu thuẫn với tài liệu hiện có, hoặc đã sửa các tài liệu liên quan.

## Với quy tắc cần code đọc (`rules.yaml`)

- [ ] Các mục chung và mục tài liệu đã đạt.
- [ ] Đã cập nhật `rules.yaml` khớp với văn bản.
- [ ] Đã tạo thẻ Trello cho dev để đồng bộ vào code.

## Với kịch bản báo cáo và demo

- [ ] Ví dụ dùng dữ liệu giả hoặc đã ẩn danh.
- [ ] Có người đọc thử và chạy thử kịch bản từ đầu đến cuối.

## Với repo code (backend, AI, frontend)

- [ ] Test liên quan đã viết và chạy xanh. Hàm tài chính có test cho các ca biên.
- [ ] Không có phần tính toán tài chính nằm trong prompt hoặc do LLM tính.
- [ ] Với thay đổi dự báo: đã kiểm chứng calibration trên dữ liệu thật hoặc ghi rõ lý do chưa kiểm.
- [ ] Không có khoá API, file `.env` hay dữ liệu thật trong commit.
