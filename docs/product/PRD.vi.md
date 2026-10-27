# Work Performance — Tài liệu Yêu cầu Sản phẩm (PRD)

> **Task:** WP-001 | **Phiên bản:** 1.0-draft | **Ngày:** 27/10/2026 | **Trạng thái:** Bản nháp — chờ phê duyệt  
> **Sản phẩm:** Web Application / PWA | **Định hướng:** Cá nhân trước, sẵn sàng mở rộng đội nhóm  
> **Tương ứng:** [PRD.md (English)](./PRD.md). Hai bản phải có cùng phạm vi, ID yêu cầu và quyết định.

## 1. Tóm tắt sản phẩm

Work Performance giúp cá nhân lập kế hoạch, thực hiện, theo dõi và đánh giá công việc, dự án, mục tiêu và thời gian bằng các báo cáo tuần, tháng, quý. Bản đầu tiên tối ưu quản lý cá nhân nhưng thiết kế phân quyền và dữ liệu đủ để mở rộng đội nhóm.

**Giá trị cốt lõi:** biết việc cần làm, mức ưu tiên, việc quá hạn, chênh lệch kế hoạch–thực tế và xu hướng cải thiện mà không phải nhập thông tin trùng lặp.

## 2. Vấn đề và kết quả mong muốn

### Vấn đề
- Công việc, deadline, mục tiêu và ước tính thời gian bị phân tán.
- Hoàn thành nhiều task chưa chắc mang lại kết quả quan trọng.
- Đánh giá cuối tuần chủ yếu dựa vào trí nhớ, khó so sánh kế hoạch và thực tế.
- Thiết kế chỉ dành cho cá nhân thường khó nâng cấp thành hệ thống nhóm.

### Kết quả
1. Ghi nhận và ưu tiên công việc nhanh chóng.
2. Theo dõi dự án, thời hạn và trở ngại minh bạch.
3. Liên kết công việc với mục tiêu.
4. Đo tiến độ, đúng hạn và sai lệch ước tính theo công thức rõ ràng.
5. Đánh giá tuần và lưu báo cáo lịch sử.
6. Mở rộng nhóm mà không làm lộ dữ liệu cá nhân.

### Tín hiệu nghiệm thu sơ bộ (cần xác nhận sau thử nghiệm)
- Tạo task chỉ cần nhập tiêu đề.
- Đánh giá tuần không phải nhập lại dữ liệu đã có.
- Có thể truy vết KPI tới tập dữ liệu, mẫu số và kỳ tính.
- Không thể đọc hoặc sửa dữ liệu từ workspace không được cấp quyền.

## 3. Đối tượng người dùng

| Đối tượng | Giai đoạn | Nhu cầu |
|---|---|---|
| Cá nhân quản lý công việc | MVP | Lập kế hoạch ngày/tuần, ưu tiên, hoàn thành, nhìn lại |
| Người làm nhiều dự án | MVP | Milestone, thời gian dự kiến/thực tế, mục tiêu |
| Thành viên nhóm | Sau MVP | Nhận việc, cập nhật và phối hợp |
| Quản lý nhóm | Sau MVP | Phân bổ workload và đánh giá kết quả nhóm |

**Bối cảnh ban đầu:** người dùng tại Việt Nam, giao diện desktop/mobile, đề xuất timezone mặc định Asia/Ho_Chi_Minh nhưng phải thay đổi được; thiết kế sẵn sàng đa ngôn ngữ.

## 4. Nguyên tắc sản phẩm

1. **Cá nhân trước:** tạo personal workspace khi đăng ký, không buộc dùng chức năng đội nhóm.
2. **Sẵn sàng cho nhóm:** dữ liệu nghiệp vụ thuộc workspace và kiểm tra quyền ở backend.
3. **Ít thao tác:** Quick Add, mặc định hợp lý, KPI tính tự động.
4. **Đo lường minh bạch:** thể hiện tử số, mẫu số, kỳ tính, trường hợp loại trừ/thiếu dữ liệu.
5. **Đánh giá công bằng:** điểm tổng hợp chỉ là tín hiệu tham khảo, không phải kết luận hiệu suất.
6. **Giữ lịch sử:** snapshot kỳ đã chốt không bị sửa ngầm.
7. **Responsive và dễ tiếp cận:** PWA mobile-first, hỗ trợ bàn phím.
8. **Bảo mật từ đầu:** phân quyền tối thiểu và audit những thay đổi quan trọng.

## 5. Phạm vi phiên bản

### MVP — bắt buộc
- Đăng nhập/đăng xuất và khởi tạo personal workspace.
- Dashboard: việc sắp đến hạn, quá hạn, ưu tiên, tiến độ và KPI.
- Tasks: Quick Add, CRUD, status, priority, deadline, tags, subtask, gắn project, List/Kanban/Calendar, lọc/sắp xếp.
- Projects: CRUD, trạng thái, thời hạn, milestone, task và tiến độ tính từ dữ liệu.
- Time tracking: ước tính, ghi thời gian thủ công, tổng thời gian thực tế; timer nên có nếu khả thi.
- Goals và Key Results đo được, check-in, chu kỳ tháng/quý.
- Analytics theo tuần/tháng/quý, nguồn gốc phép tính, tình trạng dữ liệu và snapshot.
- Weekly Review: kết quả, việc trễ, blockers, cải tiến và ưu tiên tuần tới.
- Settings: timezone, theme sáng/tối, ngày đầu tuần, trọng số KPI.
- Authorization theo workspace, lịch sử thay đổi quan trọng, API có thể kiểm thử.

### Giai đoạn 2
Nhắc việc, recurring tasks, đồng bộ lịch, GitHub, VS Code qua API độc lập, xuất CSV và analytics nâng cao.

### Giai đoạn 3
Team workspace, mời thành viên, vai trò, phân công, workload, team goals, performance review, dashboard quản lý.

### Ngoài phạm vi MVP
Microservices, Kubernetes, thanh toán, chat, native mobile, chấm điểm tự động bằng AI, đánh giá nhân sự toàn công ty, chỉnh trực tiếp VS Extends, đồng bộ offline phức tạp, tự nhập toàn bộ dữ liệu GitHub.

## 6. Luồng nghiệp vụ đầu-cuối

**WF-01 — Lần đầu sử dụng:** đăng ký/đăng nhập → tạo personal workspace → thiết lập timezone/ngày bắt đầu tuần → dashboard trống → Quick Add.

**WF-02 — Công việc hằng ngày:** mở dashboard → xem ưu tiên/hạn/quá hạn → tạo hoặc sắp ưu tiên → đổi trạng thái → ghi thời gian khi cần → hoàn thành → dashboard cập nhật.

**WF-03 — Lập kế hoạch dự án:** tạo project → milestone/task → deadline và ước tính (tùy chọn) → thực hiện → tiến độ dự án được tính từ task.

**WF-04 — Chu kỳ mục tiêu:** tạo goal có kỳ hạn → khai báo Key Results đo được → check-in → xem tiến độ → đánh giá cuối tháng/quý.

**WF-05 — Đánh giá tuần:** chọn tuần → xem số liệu và mẫu số → ghi nhận kết quả/trở ngại → lập ưu tiên tuần sau → chốt review để tạo snapshot.

**WF-06 — Chỉnh sửa sau khi chốt:** dữ liệu task có thể được điều chỉnh theo quyền; snapshot đã công bố không thay đổi; báo cáo tính lại và audit phải giải thích chênh lệch.

## 7. Yêu cầu chức năng

**MUST:** bắt buộc để phát hành MVP. **SHOULD:** ưu tiên nếu khả thi. **LATER:** sau MVP.

| ID | Mức | Yêu cầu |
|---|---|---|
| FR-AUTH-01 | MUST | Chỉ được truy cập tài nguyên của workspace có quyền |
| FR-AUTH-02 | MUST | Tài khoản mới có personal workspace |
| FR-TASK-01 | MUST | Tạo task chỉ với tiêu đề và giá trị mặc định |
| FR-TASK-02 | MUST | Cập nhật trạng thái, ưu tiên, hạn, project, tags; sửa/xóa theo chính sách |
| FR-TASK-03 | MUST | Subtask, tiến độ cha/con, không tạo vòng lặp |
| FR-TASK-04 | MUST | Lọc/sắp xếp; List, Kanban, Calendar |
| FR-TASK-05 | MUST | Lưu sự kiện đổi trạng thái và deadline |
| FR-TASK-06 | SHOULD | Blocker/dependency; chặn chu trình phụ thuộc |
| FR-PROJ-01 | MUST | CRUD project/milestone, tiến độ suy ra từ task |
| FR-TIME-01 | MUST | Ước tính, ghi thời gian thủ công, tính tổng |
| FR-TIME-02 | SHOULD | Timer bắt đầu/dừng, không chạy trùng |
| FR-GOAL-01 | MUST | Goal tháng/quý, Key Results đo lường được |
| FR-GOAL-02 | MUST | Check-in theo ngày và giá trị/đích |
| FR-DASH-01 | MUST | Dashboard hạn, quá hạn, ưu tiên, tiến độ và KPI |
| FR-AN-01 | MUST | KPI có định nghĩa theo tuần/tháng/quý |
| FR-AN-02 | MUST | Hiện thiếu dữ liệu/N/A thay vì coi là 0% |
| FR-AN-03 | MUST | Snapshot chốt kỳ và phiên bản định nghĩa metric |
| FR-REV-01 | MUST | Weekly Review có kết quả, đánh giá và ưu tiên |
| FR-REV-02 | MUST | Chốt review lưu snapshot, người và thời gian |
| FR-SET-01 | MUST | Thiết lập timezone, ngày đầu tuần, theme, trọng số KPI |
| FR-AUD-01 | MUST | Audit thay đổi quan trọng kèm actor và thời điểm |
| FR-INT-01 | LATER | Tích hợp Calendar/GitHub/VS Code độc lập |
| FR-TEAM-01 | LATER | Vai trò nhóm, mời thành viên, giao việc, team analytics |

**Màn hình chính:** Auth/Onboarding; Dashboard; My Tasks (List/Kanban/Calendar); danh sách/chi tiết Project; Goals & OKRs; Time Entries; Performance Analytics; Weekly Review; Settings. Desktop dùng sidebar, mobile dùng bottom navigation, Quick Add truy cập toàn cục.

## 8. Vòng đời nghiệp vụ (đề xuất; WP-002 sẽ chốt)

- **Task:** Todo → In Progress → Done; Blocked tùy chọn; Cancelled kết thúc; Reopened là chuyển trạng thái có audit từ Done. Cho phép quay lại bước trước, ghi lịch sử. Đổi deadline phải giữ cả giá trị cũ và mới. Xóa không được âm thầm phá dữ liệu báo cáo.
- **Project:** Planned → Active → Completed/Archived; có thể thêm Paused. Ưu tiên tiến độ suy ra từ task.
- **Goal:** Draft → Active → Completed/Closed; có thể Cancelled. Check-in cũ không bị ghi đè.
- **Cần chốt:** Blocked là trạng thái riêng hay thuộc In Progress; task hủy, parent/subtask, cách cố định deadline, tác động của reopen tới tỷ lệ đúng hạn.

## 9. KPI và quy tắc tính (sơ bộ; WP-003 sẽ chốt)

| ID | Chỉ số | Công thức/nguyên tắc ban đầu | Ngoại lệ |
|---|---|---|---|
| KPI-01 | Task Completion Rate | Task hoàn thành / task thuộc tập tính | Cần định nghĩa tập theo kỳ |
| KPI-02 | On-time Completion Rate | Task hoàn thành trước hạn cam kết / task hoàn thành có hạn | Không có deadline là N/A/loại trừ |
| KPI-03 | Estimate Accuracy | Thời gian thực tế so với dự kiến; chênh lệch % | Thiếu estimate/actual không tính bằng 0 |
| KPI-04 | Overdue Tasks | Task chưa hoàn thành quá hạn tại thời điểm chốt | Phụ thuộc timezone, hạn dạng ngày |
| KPI-05 | Goal Progress | Tiến độ KR theo baseline/target/chiều tăng giảm | Xử lý target bằng 0 và trọng số |
| KPI-06 | Project Progress | Task hoàn thành / tổng task hợp lệ (ban đầu) | Độ lớn task có thể khác nhau |
| KPI-07 | Workload | Thời gian dự kiến và đã ghi theo kỳ | Task chưa ước tính tách riêng |
| KPI-08 | Performance Trend | So sánh chỉ số các kỳ chốt tương đương | Không đủ tính tương đương: N/A |

**Bốn chiều hiệu suất đề xuất:** Goal Achievement 35%, Delivery Performance 30%, Planning Accuracy 20%, Continuous Improvement 15%. Đây **chưa phải quy tắc được phê duyệt**. Tổng trọng số cấu hình phải là 100%; mặc định không dùng điểm tổng hợp để kết luận hiệu suất.

**Trước khi code KPI cần chốt:** tập task/mẫu số, thiếu dữ liệu, ngày deadline và timezone, task mở lại/hủy, thay đổi deadline, thời điểm chốt, snapshot, cách tính lại và version công thức.

## 10. Quyền sở hữu và toàn vẹn dữ liệu

- Mỗi bản ghi nghiệp vụ thuộc đúng một workspace; các quan hệ cần bảo đảm không liên kết chéo workspace.
- Backend kiểm tra quyền tại truy vấn/service/policy, không tin vào bộ lọc frontend.
- Thiết kế hỗ trợ một người tham gia nhiều workspace trong tương lai; MVP chỉ hiển thị personal workspace.
- Thời điểm lưu UTC; hạn theo ngày và kỳ báo cáo phải dùng timezone rõ ràng.
- Ghi sự kiện thay đổi task (status, deadline, hoàn thành, đổi project) và nguồn gốc snapshot.
- Audit không ghi mật khẩu, token hoặc nội dung cá nhân quá mức. Chính sách lưu/xóa cần chốt.
- Không bắt buộc giao diện phân quyền nhóm trong MVP.

## 11. Yêu cầu phi chức năng

| ID | Yêu cầu / cách nghiệm thu đề xuất |
|---|---|
| NFR-SEC-01 | Kiểm thử tự động từ chối truy cập/sửa workspace khác; API có bảo vệ xác thực |
| NFR-SEC-02 | Quản lý phiên/token an toàn, validate đầu vào, rate limit, không lưu secret lên Git |
| NFR-PERF-01 | Đo trên tập dữ liệu đại diện; mục tiêu thử nghiệm p95 API thường dưới 500ms trên staging được kiểm soát, cần xác thực |
| NFR-UX-01 | Responsive từ 360px tới desktop, không tràn ngang ngoài ý muốn |
| NFR-ACC-01 | Hướng tới WCAG 2.2 AA; kiểm tra bàn phím, focus và contrast |
| NFR-REL-01 | Có tài liệu và kiểm thử backup/restore, migration an toàn trước production |
| NFR-OBS-01 | Log lỗi có cấu trúc, request correlation, health check; không log credentials |
| NFR-TEST-01 | Backend PHPUnit/Pest, frontend Vitest, luồng quan trọng Playwright; CI lint/typecheck/build |
| NFR-DATA-01 | Snapshot đã chốt bất biến; lịch sử giải thích thay đổi nguồn |
| NFR-PWA-01 | PWA có thể cài đặt, xử lý mất mạng thân thiện; chưa hứa chỉnh offline ở MVP |

Chỉ tiêu số là giả định cần benchmark trên môi trường thực tế trước khi chốt.

## 12. Acceptance Criteria theo module

### AC-01 — Onboarding và phân quyền
- Khi đăng ký thành công, tài khoản có personal workspace sử dụng được.
- Tài khoản chỉ có quyền workspace A không thể đọc/sửa dữ liệu workspace B và API không làm lộ thông tin.
- API bảo vệ phải từ chối truy cập chưa đăng nhập.

### AC-02 — Tasks
- Quick Add với tiêu đề tạo task đúng workspace và trạng thái mặc định.
- Kéo task trên Kanban và lưu: List, Calendar, Dashboard hiển thị thống nhất.
- Đổi deadline/status: truy vết giá trị cũ/mới.
- Subtask: ngăn vòng lặp và không đếm trùng.

### AC-03 — Projects
- Hoàn thành task: tiến độ project cập nhật theo mẫu số rõ ràng.
- Project không có task: hiển thị trạng thái trống rõ ràng.

### AC-04 — Time
- Nhiều time entry: tổng thời gian thực tế đúng; không tự suy đoán phần chồng lấn.
- Không có estimate: Estimate Accuracy là N/A, không phải 0%.

### AC-05 — Goals
- KR có baseline/current/target: tiến độ theo chiều và giới hạn đã định nghĩa.
- Check-in: truy vết giá trị, người cập nhật, ngày.

### AC-06 — Performance
- Báo cáo kỳ hiển thị giá trị KPI, tập dữ liệu/mẫu số và version công thức.
- Thiếu dữ liệu: hiển thị giải thích, không bịa kết quả.
- Task sửa sau khi chốt không thay đổi snapshot cũ.

### AC-07 — Weekly Review
- Review tuần tham chiếu KPI, blockers và ưu tiên tuần tới.
- Nếu mở lại/sửa review đã chốt, phải tuân thủ chính sách riêng và vẫn giữ snapshot gốc.

### AC-08 — Desktop/mobile
- Ở độ rộng 360px, task/Quick Add/review sử dụng được, không tràn ngang ngoài ý muốn.
- Core dialogs/menus/forms có thể thao tác chỉ bằng bàn phím.

## 13. Kiểm thử và điều kiện phát hành

Mọi yêu cầu **MUST** phải có liên kết tới ít nhất một automated test và review UI thủ công nếu phù hợp. CI phải chặn merge khi unit/integration, lint, typecheck hoặc build fail; E2E luồng trọng yếu là điều kiện release.

Mục tiêu tham khảo: coverage tối thiểu 80% phần business logic quan trọng, **không thay thế** kiểm thử kịch bản. Bắt buộc kiểm thử phân quyền workspace, state transitions, ngoại lệ KPI, tính bất biến snapshot, ranh giới timezone và luồng mobile.

Báo cáo phải có câu lệnh, môi trường, commit SHA, PASS/FAIL/SKIP và phần chưa kiểm thử. Không ghi PASS nếu chưa chạy thực tế. Release cần kiểm tra migration, backup/restore, rollback, security, staging và người dùng nghiệm thu.

## 14. Phụ thuộc và giới hạn

- Stack đề xuất (kiểm tra tương thích ở S0): Vue 3, TypeScript, Vite, Tailwind CSS, shadcn-vue, Pinia, Laravel 13, PHP 8.3+, Sanctum, PostgreSQL 17, Redis, Nginx, Docker Compose, REST `/api/v1`.
- Modular Monolith/PWA; không triển khai microservices/Kubernetes trong MVP.
- Repository riêng `hoangthongpham/work-performance`; tuyệt đối không thay đổi `hoangthongpham/vs_extends` hay dự án khác.
- Branch: `main` stable, `dev` integration, `feature/*` theo task; chỉ merge sau nghiệm thu.
- Không tự suy đoán đường dẫn máy, credentials, tên miền/host production.

## 15. Roadmap dự kiến

| Phase | Thời gian dự kiến | Deliverable / điều kiện |
|---|---|---|
| P0 — Planning | Tuần 1 | PRD được duyệt; danh sách quyết định |
| P1 — Architecture & UX | Tuần 2 | ERD, API, security design, UI prototype được duyệt |
| S0 — Foundation | Tuần 3 | Repo structure, Docker, auth, migrations, CI chạy tốt |
| S1 — Work Management | Tuần 4–5 | Task/Project và tests |
| S2 — Goals & Time | Tuần 6 | Goal, check-ins, time tracking và tests |
| S3 — Analytics | Tuần 7–8 | Metric versioning, scenarios, snapshots và tests |
| S4 — Reviews & QA | Tuần 9 | Weekly Review, regression |
| S5 — Release | Tuần 10 | Staging, production readiness, rollback, nghiệm thu |

Ước tính sẽ điều chỉnh theo phạm vi và bằng chứng kiểm thử.

## 16. Rủi ro và biện pháp

- **KPI dễ bị chạy theo số lượng:** không đánh giá chỉ qua số task; công khai chất lượng dữ liệu và các chiều hiệu suất.
- **Dời hạn làm sai tỷ lệ đúng hạn:** lưu lịch sử deadline và chốt quy tắc cố định hạn cam kết.
- **MVP phình to:** để integrations, team và automation nâng cao cho các giai đoạn sau.
- **Nhập time entry gây nặng:** hỗ trợ nhập nhanh, không đồng nhất dữ liệu thiếu với 0.
- **Rò rỉ dữ liệu khi mở rộng nhóm:** workspace authorization và tests từ S0.
- **Báo cáo lịch sử sai lệch:** version định nghĩa KPI, đóng băng snapshot.

## 17. Những quyết định cần người dùng phê duyệt

| ID | Cần quyết định | Mặc định đề xuất |
|---|---|---|
| D-01 | Task nào thuộc tập cam kết của tuần? | Task hạn trong tuần + task được đưa rõ vào kế hoạch tuần; không trộn mẫu số |
| D-02 | Tính đúng hạn khi deadline thay đổi? | Theo deadline cam kết đã đóng băng, lưu lịch sử |
| D-03 | Có dùng điểm độ phức tạp/trọng số task ở MVP? | Trước tiên hiển thị priority; trọng số nâng cao để sau |
| D-04 | Có mở lại task đã Done? | Có, ghi audit; snapshot cũ không thay đổi |
| D-05 | Xóa hẳn hay lưu trữ task? | Archive/soft delete với retention policy |
| D-06 | MVP có bắt buộc timer? | Manual time entry bắt buộc, timer nên có |
| D-07 | Có bật điểm hiệu suất tổng hợp mặc định? | Không; hiển thị bốn chiều riêng |
| D-08 | Tuần bắt đầu và timezone? | Thứ Hai; timezone cấu hình được |
| D-09 | Mẫu số bằng 0 hoặc chưa đủ dữ liệu? | N/A và giải thích |
| D-10 | Host/domain deploy và phương án đăng nhập? | Chốt trong S0, không suy đoán |

## 18. Definition of Done — WP-001

- [x] Bản PRD nháp có phiên bản, mục tiêu, giới hạn MVP, personas và workflows.
- [x] Yêu cầu chức năng và acceptance criteria có thể kiểm thử.
- [x] NFR, giả định KPI, phân tách dữ liệu, rủi ro.
- [x] Roadmap, quality gates, open decisions.
- [x] Có bản tiếng Việt để người dùng đọc và bản tiếng Anh cho agent.
- [ ] Người dùng review và phê duyệt PRD v1.0.
- [ ] WP-002 và WP-003 chốt lifecycle và công thức KPI.

**Trạng thái: Bản nháp sẵn sàng review, chưa được phê duyệt.**
