# Quy định snapshot

**Mỗi commit đều kèm một snapshot** do AI sinh, đặt trong thư mục tài liệu của chính repo chứa commit đó. Snapshot là bản ghi ngắn gọn "commit này làm gì, vì sao, ảnh hưởng gì", giúp người sau (và AI sau) nắm bối cảnh mà không phải đọc toàn bộ diff.

## Vị trí

| Repo | Thư mục snapshot |
|---|---|
| `funnel-optimizer-business-docs` | `snapshots/` (ở thư mục gốc) |
| `funnel-optimizer-backend` | `docs/snapshots/` |
| `funnel-optimizer-ai` | `docs/snapshots/` |
| `funnel-optimizer-frontend` | `app/docs/snapshots/` (hoặc `docs/snapshots/`, chốt khi dựng repo) |

Vị trí có thể điều chỉnh theo cấu trúc từng repo. Khi đổi, cập nhật bảng này trong cùng PR.

## Đặt tên file

```
snapshot_<NgàyThángNăm>_<nội-dung-commit>.md
```

- `NgàyThángNăm` theo dạng **DDMMYYYY**, lấy ngày commit. Ví dụ `12112026`.
- `nội-dung-commit` lấy từ mô tả ngắn của commit: chữ thường, không dấu, nối bằng gạch ngang, tối đa khoảng 60 ký tự.
- Nếu một ngày có hai commit trùng nội dung, thêm hậu tố `-02`, `-03`.

Ví dụ:

```
snapshot_12112026_cap-nhat-flow-2-nhanh.md
snapshot_13112026_them-do-tin-cay-gan-nguon.md
snapshot_13112026_them-do-tin-cay-gan-nguon-02.md
```

## Quy trình cho mỗi commit

1. Hoàn thành thay đổi, `git add` các file.
2. Nhờ AI sinh snapshot bằng [prompt mẫu](../templates/prompt-sinh-snapshot.md), đưa vào diff đã staged và thông tin thẻ Trello.
3. **Đọc lại** snapshot do AI sinh: sửa chỗ sai, bỏ chỗ suy diễn, xoá mọi thông tin nhạy cảm.
4. Lưu file theo quy ước đặt tên vào thư mục snapshot, `git add` file đó.
5. Commit **cùng lúc** thay đổi và snapshot (một commit, hai phần).

## Nội dung snapshot

Dùng mẫu [`templates/snapshot.md`](../templates/snapshot.md). Các mục chính:

- Thông tin: ngày, tác giả, nhánh, thẻ Trello, loại và tiêu đề commit.
- **Tóm tắt**: 2 đến 4 câu về thay đổi.
- **Lý do**: vì sao cần thay đổi.
- **File thay đổi**: danh sách và vai trò.
- **Ảnh hưởng**: ảnh hưởng tới phần khác (API, quy tắc, schema, người dùng).
- **Cách kiểm tra**: cách xác nhận thay đổi đúng.
- **Rủi ro và điểm chưa xác nhận**.
- **Việc tiếp theo**.

## Quy tắc quan trọng

- **AI chỉ soạn nháp, người commit chịu trách nhiệm.** Người commit phải đọc và xác nhận.
- Snapshot ghi **sự thật từ diff và thẻ Trello**. Không suy diễn mục đích, không bịa số liệu. Chỗ không biết ghi **Chưa xác nhận**.
- **Không đưa dữ liệu thật, khoá API, SĐT khách, số liệu ngân sách** vào snapshot. Repo có thể công khai.
- **Hash của chính commit** không thể ghi trong snapshot (chưa tồn tại lúc viết). Ghi hash của commit **trước đó** nếu cần, hoặc bỏ qua.
- Snapshot là bản ghi **tại thời điểm commit**, **không sửa lại** về sau. Nếu phát hiện sai, thêm mục "Đính chính" ở snapshot của commit kế tiếp.
- **Miễn snapshot:** commit merge do GitHub tạo khi merge PR vào `dev` hoặc `main`, commit khởi tạo repo, và commit kiểu `snapshot:` (để bổ sung snapshot còn thiếu).
- Khi **squash and merge**, các snapshot của từng commit trong nhánh vẫn được giữ trong cây file, không gộp thành một.

## Vì sao vẫn lưu cả khi đã có git log

- Git log ghi **cái gì thay đổi**. Snapshot ghi thêm **vì sao và ảnh hưởng gì**, ở mức người không đọc code cũng hiểu.
- Bạn marketing và người duyệt nghiệp vụ đọc snapshot thay vì diff.
- AI đọc snapshot để lấy bối cảnh nhanh khi hỗ trợ các phiên làm việc sau.

## Kiểm tra tự động (khuyến nghị, làm sau)

Từng repo code nên thêm bước CI kiểm tra: mỗi PR có ít nhất một snapshot mới, tên file đúng mẫu, và không chứa chuỗi dạng khoá API.
