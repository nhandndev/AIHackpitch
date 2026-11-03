# Khung làm bài và bảo vệ

Đọc phần phù hợp với nhiệm vụ hiện tại. Các mốc thời gian và mẫu dưới đây là đề xuất hỗ trợ thi, không phải tiêu chí chấm chính thức từ bản chép lời.

## Phân bổ 180 phút

| Phút tính từ lúc bắt đầu | Kết quả cần đạt |
| --- | --- |
| 0–15 | Hiểu đề, tác nhân, yêu cầu bắt buộc, giả định và phạm vi MVP |
| 15–35 | Luồng nghiệp vụ, quy tắc, kiến trúc, database/ERD và đặc tả MVP đủ để triển khai |
| 35–115 | Xây dựng luồng xuyên suốt, tích hợp module, kiểm tra từng phần |
| 115–145 | Kiểm chứng tiêu chí chấp nhận, lỗi và nhánh biên; sửa lỗi quan trọng |
| 145–165 | Ổn định bản demo, hướng dẫn chạy, báo cáo/slide; đồng bộ ERD với schema cuối |
| 165–180 | Tập demo, phản biện, kiểm tra gói nộp theo thể lệ |

Điều chỉnh theo thời gian còn lại, repo và độ khó; không đợi hết giai đoạn code mới bắt đầu kiểm tra. Đây là ngân sách thời gian, không phải lời hứa mọi đề đều làm xong trong 3 giờ. Theo bản chép lời, thuyết trình diễn ra sau thời gian làm bài; phần cuối lịch trên dùng để chuẩn bị. Nếu thể lệ mới tính cả pitch trong tổng giờ, chừa thời lượng đó trước.

Nếu còn ít thời gian, rà lại yêu cầu bắt buộc, làm rõ phần chưa đáp ứng và bảo vệ luồng cốt lõi. Cắt hiệu ứng, tính năng phụ hoặc mở rộng chưa cần; không thay đổi âm thầm phạm vi đề. Ưu tiên bản có thể chạy và kiểm tra được, vẫn ghi tối thiểu nghiệp vụ, thiết kế và tiêu chí cho phần đang làm.

## Khung phân tích ngắn

1. **Đề và nguồn:** yêu cầu nguyên gốc hoặc vị trí trong tài liệu; rubric nếu có.
2. **Vấn đề:** ai gặp khó khăn gì, hiện làm thế nào, vì sao cần giải pháp.
3. **Mục tiêu:** đầu ra hoặc hành vi có thể kiểm chứng.
4. **Phạm vi:** bắt buộc, nâng cao, ngoài phạm vi.
5. **Điểm chưa rõ:** giả định nào có thể làm thay đổi thiết kế; cách xác minh.

| ID | Yêu cầu | Nguồn / giả định | Mức ưu tiên | Tiêu chí chấp nhận |
| --- | --- | --- | --- | --- |
| R1 | Nội dung cụ thể | Đề mục tương ứng hoặc “giả định” | Bắt buộc / nâng cao | Hành vi quan sát được |

Không tự đặt “95% chính xác”, “1.000 người dùng đồng thời” hoặc mục tiêu tương tự nếu chưa có yêu cầu hay phép đo. Nếu đề xuất mục tiêu, gắn nhãn và nêu cách đo khả thi.

## Khung nghiệp vụ, dữ liệu và tích hợp

Với luồng chính, ghi tác nhân → điều kiện → thao tác → rule → trạng thái/đầu ra → kết thúc. Thêm nhánh từ chối hoặc lỗi ngay tại bước có thể phát sinh. Chọn flowchart, activity hoặc bảng trạng thái theo bài; không cần tất cả.

| Dữ liệu | Trường / kiểu quan trọng | Định danh / quan hệ | Validation | Lưu ở đâu / thời gian tồn tại |
| --- | --- | --- | --- | --- |
| Thực thể của bài | Các trường thật sự dùng | Khóa và liên kết cần thiết | Luật từ nghiệp vụ | Bộ nhớ, file hoặc DB theo nhu cầu |

| Module | Trách nhiệm | Input | Output | Lỗi | Nơi nhận output |
| --- | --- | --- | --- | --- | --- |
| Tên module thực tế | Một trách nhiệm rõ | Cấu trúc, kiểu | Cấu trúc, kiểu | Hành vi khi thất bại | Module hoặc giao diện kế tiếp |

Rà tên trường, kiểu, đơn vị, giá trị rỗng và mã lỗi ở ranh giới module; đây là những chỗ dễ ghép sai dù từng phần chạy riêng. Bảng dữ liệu trên không thay thế thiết kế database: xem [database-erd.md](database-erd.md) để làm ERD, schema, migration và seed.

## Mẫu đặc tả chức năng

Chỉ giữ các mục có tác dụng với chức năng thực tế:

```text
F1 — Tên chức năng
Liên quan: R1; luật nghiệp vụ BR1 nếu cần định danh riêng
Mục đích / tác nhân:
Điều kiện bắt đầu / quyền truy cập nếu có:
Input: trường, kiểu, bắt buộc, giới hạn, ví dụ
Xử lý: các bước và quy tắc quyết định
Output: cấu trúc hoặc hành vi hiển thị, thay đổi dữ liệu/trạng thái
Nhánh lỗi: điều kiện → phản hồi → dữ liệu có bị thay đổi không
Tích hợp: module gọi / được gọi; hợp đồng dữ liệu
AC1: Với [dữ liệu cụ thể], khi [thao tác], kết quả phải [kỳ vọng quan sát được]
AC2: Với [trường hợp lỗi cụ thể], hệ thống phải [kỳ vọng]
Cách kiểm tra: thao tác/lệnh và dữ liệu dùng
```

Tránh tiêu chí “chạy tốt”, “giao diện đẹp” hoặc “xử lý đúng”. Thay bằng kết quả cụ thể có thể quan sát và đối chiếu. Với đầu ra AI có tính biến thiên, dùng tiêu chí đánh giá phù hợp nhiệm vụ và ghi rõ bộ mẫu, thay vì mặc định so khớp nguyên văn.

## Mẫu giao một việc triển khai cho AI

```text
Bối cảnh: [vấn đề, stack hiện có, đường dẫn tài liệu]
Nhiệm vụ: triển khai F1 theo [đặc tả hoặc phần trích cần thiết]
Phạm vi thay đổi: [module/chức năng], giữ các hợp đồng tích hợp đã nêu
Input/output và quy tắc: [dẫn chiếu rõ hoặc ghi trực tiếp nếu ngắn]
Tiêu chí đạt: AC1, AC2; [lệnh hoặc thao tác kiểm chứng]
Khi thiếu dữ kiện: báo điểm ảnh hưởng nghiệp vụ; ghi giả định cho chi tiết nhỏ
Bàn giao: thay đổi, cách chạy, kết quả kiểm chứng thật, phần chưa hoàn thành
```

Chỉ giao việc đủ nhỏ để có thể xem xét kết quả và tích hợp. Không dùng câu “xây toàn bộ app này” khi chưa có nghiệp vụ và đặc tả.

## Bằng chứng kiểm chứng

| Yêu cầu | Chức năng / tiêu chí | Cách kiểm tra và input | Kỳ vọng | Kết quả thực tế / bằng chứng | Trạng thái |
| --- | --- | --- | --- | --- | --- |
| R1 | F1 / AC1 | Lệnh hoặc thao tác cụ thể | Điều phải xảy ra | Log, đường dẫn test, ảnh hoặc kết quả quan sát thật | Đạt / không đạt / chưa kiểm tra |

Giữ tham chiếu đến mã và dữ liệu đủ để lặp lại. Không đưa token, mật khẩu hay dữ liệu riêng vào ảnh/log báo cáo. Nếu dùng dữ liệu tổng hợp, ghi nguồn là dữ liệu mẫu do đội tạo. Với lỗi đã sửa có ảnh hưởng lớn, kiểm tra lại luồng bị lỗi và điểm tích hợp liên quan.

## Pitch và demo

Khi tạo bộ tài liệu, áp dụng [presentation-docs.md](presentation-docs.md): A–Z là bản giải thích đầy đủ và bài nói để nhóm nắm; SLIDE_GEN là bản chuyển thể có nội dung slide, lời nói và tham chiếu về A–Z. Dàn ý dưới đây giúp chọn mạch kể, không thay thế nội dung hoàn chỉnh của hai file.

Nếu chưa biết thời lượng, chuẩn bị dàn ý co giãn và nói rõ giả định; không khẳng định số slide là yêu cầu của hội đồng. Một dàn ý ngắn có thể gồm:

1. Người dùng, vấn đề, mục tiêu và phạm vi thực hiện.
2. Yêu cầu và luồng nghiệp vụ chính, kèm rule quyết định quan trọng.
3. Kiến trúc, database/ERD và lý do chọn giải pháp; phóng rõ PK/FK, quan hệ quan trọng trên hình.
4. Ví dụ đặc tả và cách đội dùng AI để triển khai, kiểm tra.
5. Demo xuyên suốt và bằng chứng đáp ứng yêu cầu.
6. Phần còn thiếu, đánh đổi và bước phát triển tiếp theo.

Kịch bản demo: trạng thái ban đầu → input mẫu → thao tác → output mong đợi → dữ liệu/trạng thái thay đổi → một nhánh lỗi có ý nghĩa. Ghi thời gian ước lượng từng đoạn; tập một lần với đúng dữ liệu và môi trường dùng để báo cáo. Chuẩn bị khôi phục dữ liệu nếu thao tác làm thay đổi trạng thái.

Phương án dự phòng có thể là chạy local, ảnh hoặc video đã quay nếu phù hợp thể lệ. Nêu rõ khi đang dùng bản ghi hoặc mock; không trình bày chúng như hệ thống live đang chạy.

## Câu hỏi hội đồng và cách luyện

Chọn câu hỏi phù hợp sản phẩm thực tế, không biến danh sách thành đáp án học thuộc:

- Ai cần sản phẩm này, và luồng nào chứng minh đã giải quyết vấn đề trong đề?
- Rule nghiệp vụ này lấy từ đâu? Khi dữ liệu không hợp lệ thì điều gì xảy ra?
- Vì sao chọn kiến trúc/công nghệ này? Trong 3 giờ, đánh đổi nào có chủ đích?
- Dữ liệu nào cần lưu, liên kết bằng gì, và khi nào bị thay đổi?
- Giải thích một quan hệ trong ERD: vì sao 1–N hoặc N–N, FK nằm ở đâu, và DB ngăn dữ liệu sai như thế nào?
- Output module này đi đâu? Nếu kiểu dữ liệu hoặc dịch vụ ngoài thay đổi thì sao?
- Nhóm biết kết quả đúng bằng cách nào? Cho xem một tiêu chí và phép kiểm tra.
- Phần nào do AI hỗ trợ? Nhóm đã phát hiện và sửa một kết quả sai như thế nào, nếu có?
- Thuật ngữ trên slide nghĩa là gì, và nó nằm ở đâu trong sản phẩm?
- Nếu model/dịch vụ không phản hồi hoặc trả kết quả sai, người dùng thấy gì?
- Hiện giới hạn lớn nhất là gì? Cải tiến tiếp theo giải quyết giới hạn đó ra sao?

Cấu trúc trả lời gợi ý: quyết định/hành vi → lý do theo đề → ví dụ hoặc bằng chứng → giới hạn thực tế. Nếu chưa làm, nói rõ chưa làm và cách dự định kiểm chứng. Không bịa một lỗi AI từng gây ra chỉ để trả lời trôi chảy.

Khi luyện tương tác, đợi người dùng trả lời rồi nhận xét độ đúng, bằng chứng và cách diễn đạt; hỏi tiếp từ điểm họ chưa giải thích được. Có thể soạn lời đáp mẫu nếu được yêu cầu, nhưng không lấy lời mẫu làm bằng chứng người dùng đã hiểu.
