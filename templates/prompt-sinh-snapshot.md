# Prompt mẫu: nhờ AI sinh snapshot

Sao chép nội dung dưới đây, thay các chỗ trong `<...>`, rồi gửi cho AI cùng diff đã staged.

Lấy diff:

```bash
git diff --staged
```

Danh sách file:

```bash
git diff --staged --name-status
```

## Prompt

````
Hãy viết một snapshot cho commit sắp tạo, bằng tiếng Việt có dấu, theo đúng mẫu
trong templates/snapshot.md của repo.

Thông tin commit:
- Ngày: <DD/MM/YYYY>
- Tác giả: <tên>
- Nhánh: <tên nhánh>
- Thẻ Trello: <mã thẻ / link và mô tả ngắn yêu cầu>
- Tiêu đề commit dự kiến: <loại>(<phạm vi>): <mô tả> (<mã thẻ>)
- Hash commit trước: <hash ngắn hoặc "không có">

Diff đã staged:
<dán kết quả git diff --staged>

Danh sách file:
<dán kết quả git diff --staged --name-status>

Yêu cầu:
1. Chỉ ghi những gì **thấy được trong diff** và thông tin thẻ Trello ở trên.
   Không suy diễn mục đích, không bịa số liệu. Chỗ không biết ghi "Chưa xác nhận".
2. Viết phần Tóm tắt để người không đọc code cũng hiểu.
3. Điền đủ các mục của mẫu: Tóm tắt, Lý do, File thay đổi, Ảnh hưởng,
   Cách kiểm tra, Rủi ro và điểm chưa xác nhận, Việc tiếp theo.
4. **Không đưa** khoá API, mật khẩu, SĐT, tên khách hàng, số liệu ngân sách thật
   vào snapshot. Nếu diff chứa thứ giống bí mật hoặc dữ liệu thật, hãy cảnh báo
   tôi ở đầu câu trả lời và không chép lại giá trị đó.
5. Đề xuất tên file theo mẫu snapshot_<DDMMYYYY>_<nội-dung-commit>.md
   (chữ thường, không dấu, nối bằng gạch ngang).
6. Chỉ trả về nội dung file markdown, kèm dòng đầu là tên file đề xuất.
````

## Sau khi AI trả lời

- [ ] Đọc kỹ, sửa chỗ sai hoặc suy diễn.
- [ ] Kiểm tra không có dữ liệu thật hoặc bí mật.
- [ ] Lưu file vào thư mục snapshot của repo, đúng tên.
- [ ] `git add` file snapshot rồi commit cùng thay đổi.
