# Báo cáo thực hành Day 3 — điền trực tiếp trong fork của bạn

**Cách dùng:** Thay mọi dấu `…` bằng bài làm thật của bạn trước khi nộp link fork trên [LMS](https://aithucchien.vinuni.edu.vn). Giữ nguyên bốn mục và bảng để coach đọc nhanh. Viết ngắn, cụ thể theo ảnh/vùng; không cần thuật ngữ chuyên sâu. Ví dụ trong [hướng dẫn mẫu](../../reports/REPORT_TEMPLATE.md) chỉ giúp hiểu cách điền, không phải câu trả lời để chép lại.

- Mã học viên theo lớp: 2A202603339
- Ngày / CVAT local: 12-11-2026 / CVAT local
- Công cụ đã dùng: brush/polygon

Mã học viên là mã lớp cấp; không cần ghi họ tên trong report nếu kênh [LMS](https://aithucchien.vinuni.edu.vn) đã nhận diện bạn. Chỉ ghi công cụ thật sự đã dùng; không có SAM vẫn làm bài bình thường.

## 1. Bài đã nộp

Ghi tên ZIP đúng như file trong `submissions/` và số ảnh đã vẽ, Save. Chưa làm hoặc export lỗi thì ghi `chưa có`, không tạo ZIP rỗng. Cột điểm là điểm tối đa của task, **không phải điểm tự chấm**.

| Task | File ZIP đúng tên | Hoàn thành mấy ảnh | Điểm tối đa (coach chấm sau) |
| --- | --- | ---: | ---: |
| easy_semantic | easy_semantic.zip | 3 / 3 | 20 |
| medium_instance | medium_instance.zip | 3 / 3 | 32 |
| hard_panoptic | hard_panoptic.zip | 2 / 2 | 30 |
| cp1_holes | cp1_holes.zip | 1 / 1 | 3 |
| cp2_slice | cp2_slice.zip | 1 / 1 | 3 |
| cp5_occlusion | cp5_occlusion.zip | 1 / 1 | 3 |
| cp3_thin | cp3_thin.zip | 1 / 1 | 3 |
| cp4_curb | cp4_curb.zip | 1 / 1 | 3 |
| cp6_coverage | cp6_coverage.zip | 1 / 1 | 3 |
| **Tổng tối đa** | | | **100** |

Nếu export lỗi, ghi task, dữ liệu đã Save đến đâu và lỗi đã báo coach.

## 2. Một quyết định trước khi dùng gợi ý

Chọn object đầu tiên bạn tự vẽ ở `medium_instance`, trước khi xem bất kỳ đề xuất tự động nào cho object đó. Ghi ảnh/vị trí đủ để tìm lại; “quy tắc biên” là lý do bạn chọn hoặc dừng mask ở ranh đó.

- Ảnh, vị trí và object Medium đầu tiên tự vẽ: 000000181542.jpg, vị trí: bà lão mặc áo dài trắng đang đi bộ trên vạch qua đường
- Class và quy tắc tôi dùng để chọn biên: Class person. Áp dụng quy tắc gắn nhãn phần nhìn thấy (visible-only): vẽ đường biên bám sát toàn bộ cơ thể, mái tóc, hai tà áo dài trắng, quần, dép và quai túi xách đeo trên vai phải.
- Nếu dùng gợi ý sau đó: vùng gợi ý sai/đúng, hành động sửa/giữ và lý do: không dùng
- Nếu không dùng gợi ý: Tôi gộp trọn phần tà áo dài đang bay rộng và quai túi xách vào chung một mask person thay vì cắt thẳng theo khung người, đồng thời đặt object này ở layer cao hơn chiếc xe máy phía sau để bảo đảm đúng thứ tự che khuất thực tế.

## 3. Một lỗi tôi tìm thấy và sửa

Chọn một lỗi **có thật** trong bài. Nếu công cụ lỗi khiến bạn chưa sửa được, ghi rõ đã thử gì và cần coach hỗ trợ gì; không ghi “đã sửa” khi chưa sửa.

- Task/ảnh/vùng: medium_instance/000000181542.jpg/vùng vỉa hè hậu cảnh phía sau xe bán tải và góc dưới bên trái khung hình
- Lỗi thuộc loại: sai lớp / thiếu-thừa vật / gộp-tách / biên / phủ vùng / khác: thiếu-thừa vật
- Bằng chứng tôi nhìn thấy: Dữ liệu ban đầu bỏ sót nhóm người đi bộ đứng trên vỉa hè ở hậu cảnh (khu vực phía sau xe bán tải, trước cửa hàng Chanel) và phần bánh trước của chiếc xe máy lọt vào mép dưới bên trái ảnh.
- Quy tắc và hành động sửa: Áp dụng quy tắc gắn nhãn đầy đủ các đối tượng thuộc class mục tiêu nhìn thấy được trong khung hình
- Sau sửa đã Save và export lại chưa? Đã sửa và export lại

Nếu bạn **đã xem Summary tự đánh giá trên GitHub Actions hoặc tự chạy script**, ghi ngắn một kết quả liên quan lỗi vừa sửa (ví dụ task, metric trước/sau nếu có): … / chưa có điểm. Scorecard ba tier tối đa **82**, không phải điểm cuối trên 100. Không tự ghi PASS/top 3/bonus; người phụ trách xác nhận theo tiêu chí lớp. Không đưa file ground truth vào fork.

## 4. Ba ca chưa chắc hoặc đã cân nhắc

Mỗi ca là một **vùng cụ thể** khiến bạn phải cân nhắc hai cách hiểu. Ghi dấu hiệu nhìn thấy hoặc quy tắc đã dùng, rồi nêu quyết định hoặc câu hỏi cho coach. Không cần ba lỗi; ca đã quyết định được cũng hợp lệ.

| Ảnh/vị trí | Hai cách hiểu có thể | Quy tắc/chứng cứ | Quyết định hoặc câu hỏi cho coach |
| --- | --- | --- | --- |
| 000000460147.jpg — Vùng trung tâm: Xe tải chuyên dụng chở nhiều ô tô trên 2 tầng thùng xe. | (1) Gộp cả xe tải mẹ và các xe con bên trên thành 1 đối tượng truck duy nhất.
(2) Tách riêng khung/cabin xe tải là truck, còn từng ô tô nằm trên 2 sàn chở hàng là các instance car độc lập. | Mắt thường nhìn rõ 3 chiếc ô tô con tách biệt trên 2 tầng sàn chở | Hỏi coach: Với xe tải chở ô tô, các xe trên thùng luôn tách thành car riêng hay gộp chung vào truck? |
| 000000460147.jpg — Vùng bên trái: Trụ biển quảng cáo ENEOS, bảng quảng cáo vàng lớn và dãy nhà thấp tầng phía sau. | (1) Gộp cả trụ biển hiệu/bảng quảng cáo khung thép cỡ lớn cùng dãy nhà phía sau vào class building.
(2) Loại trừ các trụ/bảng quảng cáo độc lập (để trống), chỉ gán building cho phần tường và mái nhà phía sau. | Dấu hiệu thị giác cho thấy các biển quảng cáo dựng trên khung cột thép tách rời khỏi nhà dân phía sau | Hỏi coach: Các trụ/bảng quảng cáo cỡ lớn dọc đường (như trụ ENEOS và bảng vàng bên trái) có tính vào building không hay xếp vào nền bỏ qua? |
| 000000460147.jpg — Vùng dưới trung tâm: Phần mặt đường nhựa có vạch sơn trắng nằm giữa đuôi xe tải chở ô tô và dải cây xanh phân cách. | (1) Tính là road vì đây là bề mặt trải nhựa liên thông với mặt đường, chỉ ngăn cách với làn bên trái bằng vạch sơn kẻ đường.   
(2) Không gán nhãn road (để trống/nền) vì đây là vùng lề đệm/đảo mềm ngăn cách xe với dải phân cách cứng | Dấu hiệu thị giác cho thấy bề mặt nhựa đường đồng chất có sơn ký hiệu giao thông trên mặt đường | Hỏi coach: Vùng mặt đường có vạch sơn đệm sát dải phân cách giữa có tính vào road hay để trống? |
