---
name: ai-hackathon
description: "Làm trọn bài thi hackathon từ prompt hoặc plan nhóm: phân tích, đặc tả, kiến trúc, database/ERD, code, kiểm thử; tạo Markdown tổng hợp A–Z và Markdown sinh slide đồng bộ để thuyết trình/bảo vệ. Dùng khi nhận đề, làm full, chuẩn bị tài liệu hoặc luyện thi; không dùng cho lập trình thông thường ngoài cuộc thi."
---

# AI Hackathon

Nhận một prompt hoặc một file kế hoạch của nhóm và thực hiện đến bộ kết quả có thể chạy, kiểm chứng, nộp và bảo vệ. Mặc định làm FULL khi người dùng không giới hạn phạm vi: không chỉ viết plan, prompt cho AI khác hoặc tài liệu rồi dừng. Giao tiếp, tài liệu và lời thuyết trình bằng tiếng Việt; giữ tên kỹ thuật trong mã nguồn khi phù hợp.

## Chế độ một đầu vào → bộ kết quả đầy đủ

- `$ai-hackathon [mô tả đề]` hoặc `$ai-hackathon [file plan]` đủ để bắt đầu. Đọc đầu vào và repo, tự rút yêu cầu, ghi giả định hợp lý, lập kế hoạch thực hiện rồi tiếp tục làm. Người dùng không cần gõ lại yêu cầu tạo ERD, code, test hay slide ở mỗi bước.
- Trong chế độ FULL, đọc [full-run.md](references/full-run.md) để tiếp nhận file, tổ chức đầu ra và kiểm tra hoàn tất; đọc [database-erd.md](references/database-erd.md) để thiết kế, triển khai và kiểm chứng database/ERD. Database và ERD là một phần riêng phải được xử lý, không gộp thành câu “có cơ sở dữ liệu” rồi bỏ qua.
- FULL hoặc yêu cầu bộ tài liệu thuyết trình phải có hai Markdown chính: `docs/PROJECT_A_TO_Z.md` để hiểu, tập nói và bảo vệ toàn bộ bài; `docs/SLIDE_GEN.md` để đưa cho AI/công cụ sinh slide. Đọc [presentation-docs.md](references/presentation-docs.md) khi tạo/cập nhật chúng. Hai file bổ trợ nhau, giữ riêng và đồng bộ; file A–Z là nguồn nội dung chuẩn, file sinh slide là bản chuyển thể để trình bày.
- Có plan nhóm: giữ mục tiêu, stack, phạm vi và ràng buộc đã chọn. Nếu có mâu thuẫn hoặc lựa chọn không chạy được, chỉ rõ, ưu tiên yêu cầu chính thức của đề và sửa ít nhất có thể. Không coi các đề xuất tùy chọn trong plan là yêu cầu bắt buộc.
- Không chờ duyệt lại sau mỗi giai đoạn. Tự chọn chi tiết triển khai có thể đảo ngược và ghi lý do. Chỉ hỏi khi thiếu đầu vào thiết yếu hoặc quyết định không thể suy ra có thể làm sai bài; tiếp tục việc độc lập trong lúc chờ.
- Với nhóm của người dùng này, mặc định có **3 người** nếu đầu vào mới không nói khác. Hai Markdown phải phân vai, phần nói, câu chuyển lượt, phối hợp demo và câu hỏi phản biện cho Người 1/2/3; dùng tên thật khi được cung cấp, còn thiếu tên thì ghi vai trò đề xuất. Cách chia cụ thể xem presentation-docs.
- Khi thiếu tài khoản/API key/dịch vụ ngoài, hoàn thành phần local và phần độc lập, cung cấp cấu hình cần điền và đánh dấu tích hợp bị chặn; mock phải được ghi rõ. Không báo FULL đã hoàn thành khi còn đầu ra bắt buộc chưa có hoặc chưa chạy được.
- Nếu chỉ yêu cầu ERD, phân tích, review hoặc luyện bảo vệ thì làm đúng phần đó. Việc dùng skill để chỉnh chính skill này không phải yêu cầu khởi tạo một ứng dụng thi mới.

## Cơ sở và phạm vi

Skill được chắt lọc từ bản chép lời buổi hướng dẫn do người dùng cung cấp: ban tổ chức giao bài toán; đội cần thể hiện cả quá trình phân tích, thiết kế, đặc tả, xây dựng, kiểm thử và báo cáo. Bản chép lời nói thời gian làm bài là 3 giờ rồi thuyết trình/demo. Đây là ngữ cảnh ban đầu, không phải thang điểm hoặc lịch thi chính thức cho mọi cuộc thi. Không suy ra ngày thi từ những cụm như “thứ ba tuần sau”.

Khi có đề, thể lệ, thời lượng hoặc tiêu chí chấm mới, dùng chúng làm nguồn ưu tiên. Kiểm tra quy định về AI, thư viện, dữ liệu và nộp bài nếu đã được cung cấp; không tự giả định cuộc thi cấm hoặc cho phép một hình thức sử dụng cụ thể.

## Bắt đầu và chọn chế độ

- Đọc toàn bộ đề/plan liên quan, gồm bảng, sơ đồ, ghi chú và rubric; đọc mã nguồn hiện có trước khi hỏi lại. Phân biệt yêu cầu được nêu rõ, suy luận và giả định; dẫn vị trí nguồn cho yêu cầu quan trọng.
- Nếu chưa có đề, đề nghị gửi đề hoặc chọn luyện tập; có thể chuẩn bị khung làm bài, nhưng không tự bịa đề rồi coi là đề chính thức.
- Nếu thiếu thông tin làm thay đổi nghiệp vụ cốt lõi, hỏi gọn câu cần giải quyết; tiếp tục phần độc lập. Với chi tiết có thể đảo ngược, ghi giả định và tiến hành.
- Mặc định 180 phút làm bài nếu chưa có thời lượng khác, nói rõ đây là giả định. Đọc [playbook.md](references/playbook.md) khi cần chia thời gian, soạn đặc tả, slide hoặc luyện phản biện.
- Nhận đề mới: thực hiện quy trình dưới đây. Bài đang làm: tìm chỗ thiếu và nối tiếp, không bắt đội viết lại toàn bộ. Yêu cầu riêng một phần: chỉ xử lý phần đó cùng các phụ thuộc thật sự cần thiết.
- Luyện bảo vệ: dùng sản phẩm và tài liệu thực tế để đặt câu hỏi, mỗi lượt một câu khi người dùng muốn luyện tương tác. Nếu chưa có sản phẩm, ghi rõ tình huống giả định.

## Quy trình từ đề đến sản phẩm

### 1. Hiểu vấn đề và yêu cầu

Tóm tắt ai đang gặp vấn đề gì, quy trình hiện tại, lý do cần giải quyết và kết quả mong đợi. Xác định tác nhân, dữ liệu đầu vào, đầu ra và phạm vi ngoài bài làm.

Gắn mã ngắn cho yêu cầu quan trọng, ví dụ `R1`. Tách chức năng và yêu cầu phi chức năng có liên quan thực tế như thời gian phản hồi, quyền truy cập, độ chính xác hoặc khả năng chạy trên máy demo. Chỉ dùng ngưỡng có trong đề hoặc đánh dấu là mục tiêu đề xuất.

Chốt MVP nhỏ nhất đáp ứng yêu cầu bắt buộc và chứng minh một luồng nghiệp vụ xuyên suốt. Ghi riêng phần nâng cao; khi thiếu giờ, giảm phần nâng cao trước. Không tự bỏ yêu cầu bắt buộc để chạy kịp; báo rõ nếu có yêu cầu chưa thể hoàn thành.

### 2. Phân tích nghiệp vụ

Mô tả ai khởi tạo, điều kiện bắt đầu, các bước xử lý, quy tắc quyết định, thay đổi trạng thái và điều kiện kết thúc. Phân biệt luật nghiệp vụ với lựa chọn công nghệ.

Mỗi luồng chính cần đường thành công và các nhánh lỗi có ảnh hưởng: đầu vào không hợp lệ, thiếu dữ liệu, thao tác không được phép, hoặc lỗi dịch vụ nếu có. Dùng sơ đồ Mermaid đơn giản khi giúp nhìn rõ luồng; không ép UML phức tạp.

### 3. Thiết kế kiến trúc và module

Chọn thiết kế vừa đủ cho quy mô và thời gian thi, giải thích lý do cùng một đánh đổi đáng kể. Nếu đã có stack chạy được, ưu tiên tiếp tục trừ khi có bằng chứng nó không đáp ứng đề.

Tạo sơ đồ kiến trúc và luồng dữ liệu input → xử lý → output, chỉ gồm thành phần có trong giải pháp. Với ứng dụng có giao diện, xác định màn hình và hành trình chính; triển khai đủ trạng thái tải, rỗng, lỗi và thành công liên quan đến demo. Không ép mọi đề thành web app hoặc microservice.

Chia module theo chức năng. Nêu trách nhiệm, đầu vào/đầu ra, lỗi và nơi tích hợp; kiểm tra output của module trước khớp input của module sau. Chỉ đặc tả API, schema hoặc thuật toán đến mức cần để xây dựng và kiểm chứng.

Việc dùng AI để lập trình không đồng nghĩa sản phẩm phải tích hợp AI. Nếu sản phẩm có AI, xác định nhiệm vụ của model, dữ liệu gửi/nhận, tiêu chí đánh giá, cách xử lý kết quả sai hoặc lỗi. Phân biệt rõ kết quả model và quy tắc xác định.

### 4. Database và sơ đồ ERD

Trước khi code phần lưu trữ, đọc [database-erd.md](references/database-erd.md). Từ nghiệp vụ xác định thực thể, thuộc tính, kiểu, PK/FK/unique, tính bắt buộc, quan hệ và lực lượng quan hệ 1–1, 1–N, N–N. Quan hệ N–N trong mô hình quan hệ phải có bảng nối và ràng buộc phù hợp.

Trong FULL, bàn giao phần Database/ERD đầy đủ trong `docs/PROJECT_A_TO_Z.md`, ERD Mermaid có thể chỉnh sửa ở `docs/diagrams/erd.mmd`, schema/migration chạy được theo stack và dữ liệu seed cho demo. Có thể giữ `docs/database.md` làm phụ lục kỹ thuật nếu hữu ích; tài liệu A–Z vẫn phải có sơ đồ và lời giải thích đủ để nhóm trình bày. Database phải được kết nối với luồng ứng dụng thật; dữ liệu chỉ nằm trong mảng mock không chứng minh đã có database.

ERD phải khớp schema/ORM/migration cuối cùng: cùng tên bảng/cột, PK/FK, nullable, unique và quan hệ. Kiểm tra tạo DB mới, seed, đọc/ghi qua ứng dụng và ràng buộc có ảnh hưởng nghiệp vụ. Có công cụ render thì xuất thêm SVG/PNG cho báo cáo/slide và kiểm tra hình; luôn giữ bản nguồn Mermaid. Không vẽ ERD bằng ảnh AI.

Không bỏ database/ERD vì plan chưa viết phần này: tự thiết kế phần còn thiếu từ nghiệp vụ và ghi giả định. Nếu đề hoặc người dùng yêu cầu không lưu dữ liệu, hoặc bài thực sự không có thực thể lưu trữ, ghi rõ ngoại lệ và mô hình dữ liệu phù hợp; không tạo bảng/tính năng giả để đủ hồ sơ. Phân biệt mô hình khái niệm với database đã triển khai.

### 5. Viết đặc tả trước khi giao AI xây dựng

Với mỗi chức năng MVP, ghi: yêu cầu liên quan; mục đích; tác nhân và điều kiện; input và validation; xử lý và luật; output; lỗi; tiêu chí chấp nhận có ví dụ kiểm chứng. Dùng mẫu trong playbook khi hữu ích.

Trình bày bản phân tích và đặc tả ngắn trước lượt sửa mã đầu tiên. Khi đã được giao triển khai, tiếp tục làm theo đặc tả mà không biến bước này thành yêu cầu xin xác nhận. Nếu người dùng chỉ yêu cầu phân tích thì dừng đúng phạm vi đó.

Ghi các yêu cầu/rule, giả định và đặc tả này vào A–Z trước khi code, rồi cập nhật qua từng giai đoạn. Khi tiếp tục sau gián đoạn, đọc trạng thái file và kiểm tra sản phẩm hiện tại để nối tiếp; không tạo lại từ đầu hoặc dựa vào lời hứa/kết quả cũ chưa xác minh.

### 6. Triển khai và tích hợp theo đặc tả

Làm trước một luồng từ đầu đến cuối có thể demo, sau đó hoàn thành các yêu cầu bắt buộc còn lại trong phạm vi. Khi trực tiếp triển khai, viết và sửa mã, cài phụ thuộc cần thiết, nối giao diện/API/database nếu có, rồi chạy sản phẩm; không chỉ bàn giao các prompt yêu cầu người dùng tự làm tiếp. Khi giao một phần cho công cụ AI, dùng hợp đồng rõ: bối cảnh, phạm vi, input/output, quy tắc, tiêu chí chấp nhận và cách kiểm tra. Việc chia module không tự yêu cầu hay cho phép mở thêm agent.

Khi hành vi mong muốn thay đổi, cập nhật đặc tả và mã cùng nhau. Ghi lại quyết định quan trọng và lý do đủ để đội có thể trình bày; tránh nhật ký dài cho mọi thao tác. Không thêm công nghệ chỉ để slide trông phức tạp.

### 7. Kiểm chứng và chuẩn bị demo

Đối chiếu sản phẩm với từng tiêu chí chấp nhận. Chạy luồng xuyên suốt, trường hợp lỗi và trường hợp biên có khả năng làm hỏng demo. Chọn kiểm thử tự động hay kiểm tra thủ công theo rủi ro và thời gian; ghi input, kỳ vọng, kết quả thật và phần chưa kiểm tra.

Với sản phẩm có giao diện, kiểm tra thao tác từ UI qua xử lý/API đến dữ liệu bằng browser/công cụ UI khi khả dụng. Tách kết quả kiểm chứng UI, API và database; nếu công cụ UI lỗi hoặc không có, vẫn chạy kiểm tra độc lập còn làm được và ghi UI chưa kiểm chứng. HTTP 200, build, cú pháp JS hay đọc source không đủ để đánh dấu luồng tương tác UI đã đạt.

Phân biệt “đã viết”, “đã chạy” và “đã kiểm chứng”. Không kết luận đạt từ việc build thành công hoặc chỉ xem mã; không bịa kết quả test, số người dùng hay chỉ số cải thiện. Nếu không chạy được, ghi nguyên nhân và hướng tái hiện.

Chuẩn bị dữ liệu demo, lệnh chạy, đường đi demo và phương án dự phòng phù hợp. Nếu dùng mock hoặc dữ liệu mẫu, ghi rõ; chúng không chứng minh tích hợp thật đã hoạt động. Chỉ triển khai lên hosting hoặc nộp bài khi nằm trong yêu cầu đã được giao, không tự công bố sản phẩm.

### 8. Báo cáo và bảo vệ

Xây dựng phần trình bày từ bằng chứng: vấn đề → yêu cầu → nghiệp vụ → kiến trúc → database/ERD → đặc tả → demo/kiểm thử → giới hạn và hướng phát triển. Viết `docs/PROJECT_A_TO_Z.md` hoàn chỉnh trước, rồi chuyển thành `docs/SLIDE_GEN.md` theo [presentation-docs.md](references/presentation-docs.md). Mỗi slide có nội dung hiển thị, hình/sơ đồ, lời nói, thời lượng và tham chiếu đúng mục A–Z; có bảng ánh xạ hai chiều để tra khi bị hỏi. Điều chỉnh số slide/kịch bản theo thời lượng thực tế.

Markdown là hai đầu ra chính bắt buộc cho phần tài liệu thuyết trình, kể cả khi không xuất Word/PowerPoint. Khi xuất báo cáo DOCX/PDF, lấy nguồn từ A–Z; khi tạo PPTX trong FULL hoặc theo yêu cầu, lấy nguồn từ SLIDE_GEN. Dùng skill/công cụ phù hợp và render/kiểm tra theo hướng dẫn của chúng. Nếu không xuất được, vẫn bàn giao đủ hai Markdown và nêu định dạng chưa tạo được; không nói đã có file xuất chỉ từ dàn ý.

Mọi thuật ngữ trên slide phải có lời giải thích đơn giản, gắn với chỗ dùng trong sản phẩm. Nếu đội chưa hiểu hoặc tính năng chưa có, sửa nội dung cho đúng thay vì dựng câu trả lời. Giúp đội hiểu quyết định; không khẳng định đội đã tự phân tích hay hiểu chỉ vì AI đã tạo tài liệu.

Chuẩn bị câu hỏi về lý do chọn giải pháp, rule, dữ liệu, tích hợp, cách biết hệ thống đúng, lỗi phát sinh và vai trò của AI. Câu trả lời phải dựa vào sản phẩm thật; phân biệt phần đã làm và dự kiến.

## Sản phẩm bàn giao

FULL cần sản phẩm chạy được, bằng chứng theo [full-run.md](references/full-run.md) và hai tài liệu chính:

- `docs/PROJECT_A_TO_Z.md`: một tài liệu có mục lục, tổng hợp toàn bộ từ đề, yêu cầu, nghiệp vụ, thiết kế, database/ERD, đặc tả đến triển khai, kiểm thử, cách chạy/demo, bài nói và phản biện. Phải đọc được độc lập, không chỉ làm trang liệt kê link đến file khác.
- `docs/SLIDE_GEN.md`: hướng dẫn sinh slide có thể đưa trực tiếp cho công cụ AI, kèm nội dung từng slide, sơ đồ/dữ kiện cần dùng, speaker notes, thời lượng và nguồn tham chiếu về A–Z. Không chỉ là danh sách tiêu đề.

Đầu ra kỹ thuật hỗ trợ:

- `README.md`: cài đặt, cấu hình, tạo database/seed, chạy, kiểm thử và xử lý lỗi thường gặp.
- Mã nguồn cùng cấu hình phụ thuộc, `.env.example` không chứa secret và dữ liệu demo phù hợp bài.
- `docs/diagrams/erd.mmd` và schema/migration/seed thực tế của stack; ảnh/sơ đồ và test cần thiết.
- Các tài liệu chuyên sâu sẵn có như solution/spec/database/verification/demo có thể giữ làm phụ lục; nội dung cần hiểu để bảo vệ vẫn tổng hợp vào A–Z. Không tạo thêm report/pitch độc lập trùng vai trò hai Markdown chính.
- File DOCX/PDF/PPTX xuất từ hai Markdown chính đặt trong `deliverables/` khi tạo được.

Tái sử dụng tài liệu đang có; chỉ gộp các phụ lục khi bài nhỏ, không gộp hai Markdown chính thành một. Nếu dự án đã có file tương đương, dùng tên hiện có và công bố rõ cặp tương ứng thay vì nhân đôi. Không tạo hàng loạt file rỗng. Khi chỉ luyện nói hoặc hỏi một phần, trả lời trực tiếp thay vì sinh cả bộ hồ sơ.

Trong lúc làm, cập nhật ngắn phần đã chứng minh, vướng mắc và bước tiếp theo. Trước khi kết thúc FULL, chạy lượt đối chiếu hoàn tất trong full-run: sửa được thì tiếp tục sửa; thiếu quyền/dữ kiện thiết yếu thì chỉ rõ chỗ bị chặn. Cuối lượt, đưa link sản phẩm/file, lệnh chạy, kết quả kiểm chứng thật, thiếu sót và việc đội cần nắm trước khi bảo vệ. Không chỉ trả về kế hoạch cho một yêu cầu FULL.
