# Kiểm tra skill AI Hackathon

Mục tiêu: đánh giá đường thực hiện từ một prompt hoặc file plan đến sản phẩm, database/ERD và hai Markdown bổ trợ cho thuyết trình; sửa các thiếu sót được chứng minh. Đây là kiểm tra skill và các bài thử cô lập, không phải kết quả của đề thi thật sắp tới.

## Cách kiểm tra

- Đọc toàn bộ bản skill đang cài và các reference; so với bản trong workspace và các yêu cầu người dùng đã chốt.
- Forward-test độc lập trong thư mục tạm, không truy cập mạng hoặc sửa dự án thật.
- Bài FULL: CLI Python/SQLite đăng ký workshop, sức chứa, hủy/đăng ký lại, cạnh tranh chỗ cuối, database bền vững và seed chạy lại được; nhóm 3 người, nói/demo 9 phút, Q&A riêng.
- Bài chỉ tài liệu: plan quản lý mượn thiết bị chưa triển khai, có email chưa chọn dịch vụ/key; cần hai Markdown, không code hoặc gửi email.
- Bài file Word: đọc DOCX có đoạn văn và bảng chứa riêng một rule nghiệp vụ; dùng bản skill sửa, không cung cấp lại nội dung file bằng prompt.
- Bài FULL web: UI tiếng Việt + HTTP API + SQLite quản lý dự án/công việc, tham chiếu bắt buộc/tùy chọn, status, seed, restart; repo trống và thư viện chuẩn, không CDN.
- Kiểm tra artifact và bằng chứng thực tế; không lấy validator YAML làm bằng chứng đủ cho hành vi toàn quy trình.

## Thiếu sót thấy trong bản đầu và hướng sửa

| Phát hiện | Bằng chứng bản đầu | Sửa |
| --- | --- | --- |
| Chưa ghi mặc định nhóm của người dùng có 3 người | presentation-docs chỉ nói dùng người nói nếu biết; chưa có mặc định số người hay vai trò/chuyển lượt/Q&A | Bổ sung mặc định 3 người trong entrypoint/full-run, bảng chia vai và đồng bộ lời nói, demo, Q&A trong hai Markdown |
| Phân tích/đặc tả trước code chưa có yêu cầu lưu bền vững rõ | Có yêu cầu trình bày trước sửa mã, nhưng chưa buộc ghi vào A–Z trước code để tiếp tục/đối chiếu | Ghi yêu cầu/rule/đặc tả trước code, cập nhật theo giai đoạn và kiểm tra trạng thái thực tế khi nối tiếp |
| Đọc DOCX dễ phụ thuộc thư viện dù text/bảng có thể đọc bằng thư viện chuẩn | full-run yêu cầu đọc đủ nhưng chưa chỉ đường dự phòng khi không có thư viện; môi trường thử không cài python-docx | Thêm fallback đọc OOXML trong ZIP, bảo toàn đoạn/bảng; phân biệt phần hình/comment/changes chưa kiểm tra |
| Một câu tham chiếu ngữ cảnh sửa skill có thể gây hiểu sai cho lần dùng sau | presentation-docs nói “Việc cập nhật skill này chưa cung cấp đề/sản phẩm cụ thể” như trạng thái cố định | Đổi thành điều kiện chỉ áp dụng khi thật sự đang chỉnh skill hoặc xin template |
| Nhánh minh họa có thể dùng sai snapshot dù con số riêng lẻ đúng | Lượt DOCX: sau trả L01 tồn E1=1; nhánh U2 cần tồn E1=0 sau duyệt L02, nhưng phối hợp nói “về bảng ban đầu” nơi tồn là 2 | Bổ sung đối chiếu trước/thao tác/sau và mốc snapshot khi rẽ nhánh; sửa đồng bộ tình huống rồi kiểm tra lại |
| Chưa có gate riêng để tránh lẫn API pass với UI đã chạy | Lượt web HTTP chạy được nhưng CUA không có browser provider và getApp Chrome timeout, nên không có bằng chứng click/UI | Tách kết quả UI/API/DB và yêu cầu công khai UI chưa kiểm chứng khi công cụ lỗi; giữ kiểm tra còn chạy được và bước tái hiện |

## Ma trận yêu cầu và bằng chứng

Phân biệt kiểm chứng hành vi của các bài thử với cấu trúc gói skill. Các bài thử không có yêu cầu xuất Office/PDF nên không dùng việc thiếu các file đó làm lỗi; hai Markdown và ERD vẫn được đối chiếu.

| Yêu cầu | Bằng chứng cần kiểm tra | Trạng thái |
| --- | --- | --- |
| Nhận một prompt, làm đến sản phẩm | CLI có source/schema/seed/README và 20 test đạt. Web có source HTML/CSS/JS/API/DB và 20 test đạt | Đạt cho CLI và backend web; tương tác UI chưa kiểm chứng |
| Nhận file plan Word, gồm bảng | Đọc 7 đoạn + bảng 2×2 qua OOXML; BR-TABLE tối đa 2 phiếu được đưa vào R4, F3, AC8, sơ đồ và slide | Đạt trong fixture DOCX text/bảng |
| Database thật, lưu bền vững, seed an toàn | CLI test qua tiến trình riêng; web test restart tiến trình server; seed lặp; FK/PK/unique/check và metadata thật | Đạt trong hai bài có triển khai |
| ERD khớp schema cuối | CLI và web: nguồn `.mmd` khớp A–Z, đúng ba bảng/cột thật mỗi bài; PK/FK/unique/nullable và quan hệ đã đối chiếu schema | Đạt phạm vi source/schema; chưa render Mermaid |
| A–Z đầy đủ, đọc độc lập | Đã đọc phần chính cả bốn bài: phân tích, nghiệp vụ, kiến trúc, database/ERD, đặc tả, kiểm chứng, bài nói/phản biện; web tách rõ UI chưa kiểm | Đạt trong bốn lượt thử |
| SLIDE_GEN tự đủ nội dung và đồng bộ | CLI/web: 7 slide chính/540s; docs-only/DOCX: 8 slide chính/480s. Sơ đồ, notes, người nói, bảng ánh xạ và nguồn/anchor đã kiểm; nhánh snapshot DOCX đã sửa | Đạt trong bốn lượt thử, gồm một lượt sửa snapshot |
| Chia lời nói/demo/Q&A cho 3 người | DOCX không nêu số người nhưng dùng mặc định 3: 150/170/160 giây, chuyển lượt, phối hợp minh họa và bảng chính/hỗ trợ Q&A | Đạt với bản sửa |
| Tài liệu từ plan chưa triển khai không bịa kết quả | Hai lượt docs-only chỉ tạo Markdown; test sản phẩm ghi chưa chạy, email chưa tích hợp, sơ đồ là đề xuất | Đạt |
| Không tự chạy dịch vụ/email/deploy ngoài phạm vi | Không network ra ngoài/email/tài khoản/deploy. Web chỉ server loopback cho kiểm thử được phép | Đạt trong các lượt thử |
| Không dừng chỉ ở plan; tôn trọng chế độ giới hạn | FULL có code/database/test; docs-only không tự sinh app. Web ghi A–Z/spec trước code, đã quan sát khi chưa có source | Đạt |
| Gói skill đúng cấu trúc, reference hợp lệ | quick_validate + YAML/link/fence đạt; 6 file bản cài khớp byte và SHA-256 với source | Đạt; xem evidence/installed-skill.json |

## Bằng chứng chạy và đối chiếu

- `evidence/full-tests.txt`: root tự chạy lại 20 unittest của CLI; tất cả đạt, gồm 10 vòng cạnh tranh chỗ cuối và đăng ký trùng đồng thời.
- `evidence/baseline-artifacts.json`: root kiểm link/anchor (44 cho CLI, 45 cho docs-only), ERD nhúng và schema; có hash artifact/source tại lúc kiểm tra.
- `evidence/web-http-root.json`: root chạy 15 request HTTP thật trên server loopback/DB tạm mới, gồm static asset, tạo/lọc, validation, optional assignee, update DONE và tham chiếu sai; sau khi đóng server đọc SQLite vẫn DONE và chỉ có hai task hợp lệ.
- `evidence/web-tests.txt` và `evidence/web-demo.txt`: suite web có 20 test (12 Store/DB + 8 HTTP); demo HTTP tạo, cập nhật, dừng/khởi động tiến trình mới trên cùng DB đã đạt. Source test nằm ở `/private/tmp/ai-hackathon-web-test/tests/test_app.py`.
- `evidence/final-artifacts.json`: kiểm tra cuối đủ bốn bộ artifact, hash source/tài liệu; link local/anchor hợp lệ là 44 (CLI), 45 (docs-only), 46 (DOCX), 43 (web). Đây là số link trong hai Markdown chính theo bộ kiểm của root, không bao gồm mọi file README/phụ lục.
- Kiểm tra đối chiếu được thử bằng ba lỗi cài có chủ đích trên bản sao tạm: anchor không tồn tại, ERD A–Z khác nguồn và schema có cột không nằm trong ERD. Cả ba đều bị phát hiện; artifact thật không bị thay đổi.
- Các thư mục `/private/tmp/ai-hackathon-*-test` là bài thử tổng hợp, không phải dự án thật của nhóm; hệ điều hành có thể dọn chúng. Log/manifest trong thư mục audit này được giữ cùng workspace.
- Đã dừng server web do bài thử tạo bằng Ctrl+C, exit 0 theo lượt chạy; root kiểm tra handle 21730 không còn tồn tại. Không để server kiểm thử chạy sau bàn giao.

## Phạm vi kết luận

Các phần chưa được chứng minh:

- Click, tương tác và bố cục UI trong browser: CUA không có browser provider/IAB, gọi native Chrome timeout. Đã kiểm API/DB/static asset/cú pháp JS, chưa gọi chúng là UI pass.
- Render/parse Mermaid bằng công cụ Mermaid thực tế: không có `mmdc`; đã kiểm source, quan hệ và sự đồng bộ với schema, chưa khẳng định ảnh render đọc được.
- DOC cũ, PDF scan/OCR, DOCX có ảnh/comment/tracked changes và đường nạp từ tài liệu online chưa được forward-test. Fixture Word lần này chỉ text và bảng.
- Word/PDF/PPTX đầu ra, tích hợp email/model thật, production hosting, tải lớn và hoạt động của đội người thật chưa được thử; không suy từ log local thành kết quả các phần này.

Bộ skill đã có quy trình và đầu ra bao phủ yêu cầu hiện tại, đồng thời được sửa theo lỗi quan sát được. Đây không phải bảo đảm mọi đề bất kỳ sẽ xong không cần thông tin bổ sung, tài khoản, quyền hoặc kiểm thử tiếp. Không có thang điểm chính thức trong transcript để gán điểm cho skill hoặc dự đoán điểm thi.
