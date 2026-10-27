# Quy ước ngôn ngữ tài liệu

> Phạm vi: repository Work Performance | Trạng thái: Áp dụng | Ngày: 27/10/2026

## Bắt buộc hai phiên bản
Mọi tài liệu Markdown do dự án viết phải có hai bản tương ứng:
- **Tiếng Anh (dành cho agent):** `TEN.md` (ví dụ `docs/product/PRD.md`).
- **Tiếng Việt (dành cho người dùng):** `TEN.vi.md` (ví dụ `docs/product/PRD.vi.md`).

Ngoại lệ: các file có tên bắt buộc do công cụ quy định (ví dụ `README.md`, `AGENTS.md`, GitHub issue/PR templates) giữ tên tiếng Anh chuẩn và vẫn bổ sung file `.vi.md` tương ứng khi có nội dung tài liệu dành cho người dùng. Định dạng máy đọc (JSON, YAML, OpenAPI) không phải Markdown và không bắt buộc nhân đôi nếu chưa được yêu cầu.

## Quy tắc đồng bộ
1. Tạo hoặc cập nhật đồng thời hai ngôn ngữ trong cùng task hoặc PR.
2. Giữ nguyên mã yêu cầu, task ID, tên trạng thái, công thức, phiên bản, mốc roadmap và acceptance criteria.
3. Dịch phần giải thích; không dịch mã định danh, code, tên API hoặc đường dẫn.
4. Không để bản tiếng Việt cũ hơn mà không thông báo; nếu thiếu một bản thì không đánh dấu tài liệu đã hoàn tất.
5. Tiếng Anh là tài liệu agent dùng thao tác; tiếng Việt để người dùng nghiệm thu. **Không bản nào được tự ý thay đổi yêu cầu đã chốt của bản kia.** Có mâu thuẫn phải đồng bộ trước khi phê duyệt.
6. Người dùng đánh giá phạm vi qua bản tiếng Việt; các quyết định cuối cùng phải phản ánh nhất quán ở bản tiếng Anh.

## Checklist nghiệm thu
- [ ] Đủ hai file.
- [ ] Phiên bản và trạng thái tương ứng.
- [ ] Đầy đủ mục, requirements, acceptance criteria và quyết định.
- [ ] Link tương đối hoạt động.
- [ ] Nội dung thay đổi được cập nhật đồng thời.
- [ ] Có nghiệm thu của người dùng trước khi merge.

Áp dụng với PRD, roadmap, báo cáo task, kiến trúc, tài liệu API, kiểm thử, deployment và handoff.
