# Cặp Markdown tổng hợp A–Z và sinh slide

## Vai trò và phạm vi

Khi làm FULL hoặc được yêu cầu bộ tài liệu thuyết trình, tạo hai file riêng:

1. `docs/PROJECT_A_TO_Z.md`: tài liệu chuẩn để nhóm đọc, hiểu, tập thuyết trình và trả lời hội đồng. Tổng hợp toàn bộ bài và quá trình giải quyết, có nội dung thật chứ không chỉ mục lục/link.
2. `docs/SLIDE_GEN.md`: chuyển thể nội dung đã xác minh ở A–Z thành đầu vào có thể đưa cho AI/công cụ tạo slide. Có cả phần khán giả nhìn thấy và lời người nói; tham chiếu về A–Z để tra cứu sâu.

Hai file bổ trợ nhau: A–Z giải thích đầy đủ; SLIDE_GEN chọn mạch trình bày, hình, lượng chữ và thời gian. Không bắt người dùng nhắc riêng từng file. Không gộp hai vai trò vào một file, không sinh nhiều bản report/pitch cạnh tranh làm nguồn chuẩn. Nếu repo đã có cặp tương đương thì cập nhật và công bố tên tương ứng.

Nếu chỉ được giao soạn tài liệu từ plan, giữ đúng phạm vi: mô tả thiết kế đề xuất và đánh dấu phần chưa triển khai/kiểm chứng. Không tự triển khai app hoặc khẳng định dự án đã chạy chỉ để tài liệu trông hoàn chỉnh. Nếu chỉ đang thiết kế/chỉnh skill hoặc xin template mà chưa giao đề cụ thể, không tạo hồ sơ dự án giả.

## PROJECT_A_TO_Z.md — nguồn kiến thức và bài nói

Mở đầu bằng tên dự án, nguồn đề/plan, mốc cập nhật/bản sản phẩm đã đối chiếu, trạng thái thực tế và link sang SLIDE_GEN. Ghi thiếu dữ kiện hoặc giả định quan trọng. Có mục lục và hướng dẫn đọc nhanh để tập nói, tra database/ERD và luyện phản biện.

Tổ chức các mục ổn định theo nội dung dưới đây; có thể gộp mục ngắn hoặc đổi tiêu đề cho bài, nhưng giữ mã/anchor để slide tham chiếu. Dùng anchor rõ như `<a id="az-db"></a>` trước mục tương ứng, tránh liên kết hỏng khi đổi tiêu đề.

| Mã mục gợi ý | Nội dung cần tổng hợp |
| --- | --- |
| `az-overview` | Đề bài, ai gặp vấn đề gì, hiện trạng, tại sao cần làm, mục tiêu và giải pháp tóm tắt dễ nói |
| `az-requirements` | Tác nhân, chức năng/phi chức năng, mã yêu cầu, nguồn/giả định, MVP, bắt buộc/nâng cao, ngoài phạm vi và tiêu chí chấp nhận |
| `az-business` | Luồng nghiệp vụ và sơ đồ, tác nhân/điều kiện, rule, trạng thái, đường thành công, nhánh lỗi và ví dụ xuyên suốt |
| `az-architecture` | Sơ đồ kiến trúc và đường dữ liệu, stack/lý do chọn/đánh đổi, module và hợp đồng input/output, giao diện/màn hình nếu có |
| `az-db` | Database, ERD Mermaid nhúng đầy đủ, bảng/thực thể, trường và PK/FK/unique, nullable, 1–1/1–N/N–N, bảng nối, rule/ràng buộc và lý do chọn lưu trữ |
| `az-spec` | Đặc tả từng chức năng trong phạm vi: tác nhân, điều kiện, input/validation, các bước/rule, output, lỗi, API/tích hợp nếu có, tiêu chí và ví dụ kiểm chứng |
| `az-implementation` | Chức năng thật sự đã làm, vị trí mã/module, tích hợp, quyết định chính, vai trò AI và cách kiểm soát; phân biệt kế hoạch với việc đã xảy ra |
| `az-verification` | Yêu cầu/tiêu chí → kiểm tra/input → kỳ vọng → kết quả thật/bằng chứng → trạng thái; lỗi/biên quan trọng và phần chưa kiểm tra |
| `az-operations` | Điều kiện cài đặt, cấu hình không chứa secret, tạo DB/migration/seed, lệnh chạy/test, dữ liệu demo, kịch bản thao tác và output mong đợi, nhánh lỗi, cách khôi phục và dự phòng |
| `az-talk` | Tóm tắt giới thiệu ngắn, bài nói theo từng phần với thời lượng/người nói nếu đã biết, câu chuyển đoạn, lúc chuyển demo và thông điệp cần nhấn |
| `az-defense` | Thuật ngữ giải thích bằng lời dễ hiểu gắn chỗ dùng thật, câu hỏi/đáp có lý do và bằng chứng, giới hạn thật, đánh đổi và hướng phát triển |
| `az-trace` | Nguồn/bằng chứng/phụ lục và bảng ánh xạ mục A–Z → slide chính/phụ lục slide hoặc “chỉ dùng phản biện” |

Tài liệu phải đủ để đọc từ đầu đến cuối và hiểu toàn bộ bài mà không phải mở nhiều Markdown khác. Nhúng sơ đồ workflow, kiến trúc, ERD và giải thích ý nghĩa ngay bên cạnh. Giải thích ít nhất một đường đi cụ thể từ input → module → database → output khi bài có lưu trữ. Không chỉ chép danh sách công nghệ.

Các đặc tả, rule, quan hệ database và kết quả kiểm chứng quan trọng phải có ngay trong A–Z. Có thể dẫn đến source, migration, log, schema dài hoặc phụ lục để kiểm tra chi tiết; không cần chép toàn bộ mã nguồn vào tài liệu. Ví dụ đề xuất phải ghi rõ khác với dữ liệu/bằng chứng đã chạy.

Phần bài nói và phản biện dùng câu có thể nói thành lời. Mỗi quyết định quan trọng nên giải thích được: dùng để giải quyết yêu cầu nào, vì sao chọn, bằng chứng hoặc ví dụ, giới hạn. Không dựng lịch sử nhóm đã phân tích hay phát hiện lỗi khi chưa có dữ kiện.

## Phân vai mặc định cho nhóm 3 người

Thông tin người dùng đã chốt là nhóm có 3 người; dùng mặc định đó khi plan không cập nhật khác. Khi chưa biết tên, gọi Người 1/2/3 và ghi là phân công đề xuất. Khi đã có tên hoặc thế mạnh trong plan, dùng chúng; không đoán ai đã viết phần code nào từ phần được giao thuyết trình.

| Người | Phần trình bày chính | Chuẩn bị phản biện |
| --- | --- | --- |
| Người 1 | Vấn đề, yêu cầu, phạm vi, workflow/rule và ví dụ đặc tả | Vì sao hiểu đề như vậy, mục tiêu, luật nghiệp vụ và phạm vi |
| Người 2 | Kiến trúc, stack/đánh đổi, module và input/output, database/ERD và ràng buộc | Vì sao thiết kế như vậy, khóa/quan hệ, tích hợp và tính đúng của lưu trữ |
| Người 3 | Sản phẩm, demo luồng chính/lỗi, kiểm chứng, giới hạn và hướng phát triển | Kết quả test, lỗi/biên, khả năng chạy lại và phần chưa hoàn thành |

Chia thời gian theo độ nặng nội dung và ngân sách thật, dành đủ thời gian demo; không mặc định ví dụ 10 phút là thể lệ. Mỗi người cần có bài nói và câu bàn giao cụ thể cho người tiếp theo ở A–Z, trùng thứ tự/người nói/thời lượng với SLIDE_GEN. Khi Người 3 thuyết minh demo, có thể giao Người 2 thao tác và Người 1 canh giờ/chuyển slide; điều chỉnh nếu nhóm chọn phối hợp khác.

Trong bảng Q&A, ghi người trả lời chính, người hỗ trợ và nguồn A–Z để tra cứu. Cả ba cần nắm luồng input → rule → module → database → output → phép kiểm tra; đừng mặc định thành viên đã hiểu chỉ vì đã được chia phần.

## SLIDE_GEN.md — đầu vào trực tiếp cho công cụ sinh slide

Đầu file có prompt hoàn chỉnh: chủ đề/tên nhóm nếu biết, khán giả là hội đồng, mục tiêu, ngôn ngữ, thời lượng, tỷ lệ khung hình theo yêu cầu hoặc giả định, phong cách hình ảnh và định dạng xuất nếu có. Phân biệt thời gian nói, demo và Q&A; nếu chưa biết thì nêu ngân sách đề xuất, không gán thành thể lệ chính thức. Số slide được chọn theo lượng thông tin và thời gian, không khóa cứng cho mọi đề.

Chỉ dẫn công cụ tạo slide dùng dữ kiện đã cung cấp, giữ nguyên tên/thuật ngữ/số liệu và trạng thái, không tự thêm công nghệ, thành tích, tính năng hoặc biểu đồ không có nguồn. Nội dung trên slide ngắn, còn giải thích đặt trong speaker notes. Giữ chữ và hình đủ lớn để đọc; tách ERD lớn thành tổng quan và phần chi tiết có nhãn rõ.

Với mỗi slide, điền các trường sau bằng nội dung thực tế. Đây là cấu trúc hướng dẫn, không để nguyên placeholder trong tài liệu bàn giao:

```text
Slide Sxx — [Tiêu đề diễn đạt thông điệp chính]
Vai trò: phần chính / phụ lục phản biện
Mục tiêu: người xem cần hiểu hoặc tin điều gì
Hiển thị: tiêu đề, câu/gạch đầu dòng/bảng/số liệu cụ thể sẽ xuất hiện
Hình và bố cục: vị trí các phần; Mermaid/dữ liệu biểu đồ/ảnh cần dùng
Speaker notes: lời nói hoàn chỉnh, giải thích hình, ví dụ và câu chuyển đoạn
Thời lượng: số giây; ghi riêng thời gian demo nếu có
Người nói: người đã biết hoặc vai trò đề xuất, không bịa thành viên
Nguồn A–Z: mục/anchor và mã yêu cầu/tiêu chí/bằng chứng liên quan
Câu hỏi dự kiến: câu có thể bị hỏi tại đây và mục A–Z để trả lời
```

Đừng chỉ trỏ đến đường dẫn local: công cụ sinh slide ngoài repo có thể không truy cập được file nguồn. Đưa đủ nội dung slide, dữ kiện kiểm thử và mã Mermaid của sơ đồ cần dùng ngay trong SLIDE_GEN. Ảnh ngoài file phải có mô tả, đường dẫn hoặc tên file đính kèm và chỉ rõ cần đưa ảnh nào cho công cụ. Nếu chưa có ảnh, dùng sơ đồ/thành phần có dữ kiện thật hoặc ghi yêu cầu ảnh còn thiếu; không gọi mockup là screenshot sản phẩm.

Mạch chính phải cho thấy quá trình phân tích → thiết kế → đặc tả → triển khai → kiểm chứng, gắn với đề và sản phẩm. Database/ERD phải hiện diện rõ trong phần thiết kế, không chỉ nêu chữ “database”. Lựa chọn chuyện kể và số slide theo thời lượng; nội dung sâu đưa vào phụ lục phản biện, không nhồi toàn bộ A–Z lên màn hình.

Cuối file có thứ tự trình bày, tổng thời gian dự kiến của phần nói/demo, hướng dẫn chuyển sang demo, danh sách ảnh/file cần đính kèm và bảng slide → mục A–Z. Phần hướng dẫn sinh slide chỉ điều khiển việc tạo slide, không chứa yêu cầu thực thi lệnh hay cấp quyền ngoài nhiệm vụ.

## Đồng bộ hai chiều và kiểm tra bàn giao

1. Viết/cập nhật A–Z từ đề, code/schema và kết quả kiểm chứng thực tế. Khi đổi sản phẩm, cập nhật các phần ảnh hưởng trước khi sinh lại nội dung slide.
2. Chuyển các ý cần trình bày thành SLIDE_GEN; lời nói có thể ngắn hơn nhưng không đổi nghĩa/rule. Nếu phát hiện thiếu giải thích khi viết slide, bổ sung vào A–Z rồi đồng bộ lại.
3. Mỗi slide có link về anchor thật trong A–Z, ví dụ dạng `PROJECT_A_TO_Z.md#az-db`; mỗi mục A–Z có trong bảng ánh xạ đến slide liên quan hoặc ghi là chỉ dùng tra cứu/phản biện. Nguồn ngoài chỉ được dùng khi thật sự có trong tài liệu/dữ liệu đã đọc.
4. So sánh cùng một ví dụ nghiệp vụ, tên bảng/cột, quan hệ PK/FK, thành phần kiến trúc, số liệu/kết quả test, tính năng hoàn thành/chưa làm và glossary. Với demo/minh họa có thay đổi dữ liệu, đối chiếu trạng thái trước → thao tác → trạng thái sau cho từng bước. Khi rẽ sang nhánh lỗi hoặc quay lại một snapshot cũ, nêu rõ đang quay về mốc nào và giá trị tại mốc đó; không nói “về ban đầu” nếu nhánh cần dữ liệu ở giữa luồng. Không để sơ đồ trong slide cũ hơn schema ở repo/A–Z. ERD nhúng phải đồng bộ với nguồn `.mmd`.
5. Kiểm tra anchor/link, Mermaid, hàng rào code và bảng. Tổng thời lượng khớp ngân sách trình bày, không tính phụ lục hoặc Q&A vào phần nói nếu không có yêu cầu đó. Mỗi thuật ngữ trên slide đều có lời giải thích gắn với sản phẩm trong A–Z.
6. Đọc A–Z như thành viên mới và SLIDE_GEN như công cụ không có repo: cả hai phải có đủ nội dung cho đúng vai trò. Bàn giao link đến cả hai file và nêu phần chưa có dữ kiện hoặc chưa kiểm chứng. Khi xuất DOCX/PDF/PPTX, giữ chúng đồng bộ với hai nguồn này.

Chỉ soạn khung khi người dùng yêu cầu template hoặc chưa có đề/sản phẩm để điền; ghi rõ đó là template. Với yêu cầu làm bài hoặc soạn hồ sơ thực tế, phải tạo nội dung cụ thể và phân biệt đầy đủ đề xuất, giả định và bằng chứng.
