# Báo cáo thực hành Day 3 — điền trực tiếp trong fork của bạn

**Cách dùng:** Thay mọi dấu `…` bằng bài làm thật của bạn trước khi nộp link fork trên [LMS](https://aithucchien.vinuni.edu.vn). Giữ nguyên bốn mục và bảng để coach đọc nhanh. Viết ngắn, cụ thể theo ảnh/vùng; không cần thuật ngữ chuyên sâu. Ví dụ trong [hướng dẫn mẫu](../../reports/REPORT_TEMPLATE.md) chỉ giúp hiểu cách điền, không phải câu trả lời để chép lại.

- Mã học viên theo lớp: 2A202603220
- Ngày / CVAT local: 11/11/2026
- Công cụ đã dùng: CVAT local (SAM3 trong CVAT cho cp4, cp5, cp6, Vẽ thử công cho các data còn lại)

Mã học viên là mã lớp cấp; không cần ghi họ tên trong report nếu kênh [LMS](https://aithucchien.vinuni.edu.vn) đã nhận diện bạn. Chỉ ghi công cụ thật sự đã dùng; không có SAM vẫn làm bài bình thường.

## 1. Bài đã nộp

Ghi tên ZIP đúng như file trong `submissions/` và số ảnh đã vẽ, Save. Chưa làm hoặc export lỗi thì ghi `chưa có`, không tạo ZIP rỗng. Cột điểm là điểm tối đa của task, **không phải điểm tự chấm**.

| Task | File ZIP đúng tên | Hoàn thành mấy ảnh | Điểm tối đa (coach chấm sau) |
| --- | --- | ---: | ---: |
| easy_semantic | submissions/easy_semantic.zip | 3 / 3 | 20 |
| medium_instance | submissions/medium_instance.zip | 3 / 3 | 32 |
| hard_panoptic | submissions/hard_panoptic.zip | 2 / 2 | 30 |
| cp1_holes | submissions/cp1_holes.zip | 3 / 3 | 3 |
| cp2_slice | submissions/cp2_slice.zip | 1 / 1 | 3 |
| cp5_occlusion | submissions/cp5_occlusion.zip | 1 / 1 | 3 |
| cp3_thin | submissions/cp3_thin.zip | 1 / 1 | 3 |
| cp4_curb | submissions/cp4_curb.zip | 1 / 1 | 3 |
| cp6_coverage | submissions/cp6_coverage.zip | 1 / 1 | 3 |
| **Tổng tối đa** | | | **100** |


## 2. Một quyết định trước khi dùng gợi ý


- Ảnh, vị trí và object Medium đầu tiên tự vẽ: ảnh `000000181542.jpg`, người phụ nữ mặc áo dài trắng đang đi qua đường.
- Class và quy tắc tôi dùng để chọn biên: xác định vật thể, nhãn vẽ sát vật. Người này là một object riêng, tách khỏi người lái và xe máy xung quanh.
- Nếu dùng gợi ý sau đó: Quá trình dùng tool với cp4, cpp5, cp6 sau khi tôi trích hợp được SAM. kiểm lại class và số object trong danh sách Objects. Giữ người lái và xe máy là hai object riêng vì quy tắc instance tính mỗi vật là một mask.

## 3. Một lỗi tôi tìm thấy và sửa

Chọn một lỗi **có thật** trong bài. Nếu công cụ lỗi khiến bạn chưa sửa được, ghi rõ đã thử gì và cần coach hỗ trợ gì; không ghi “đã sửa” khi chưa sửa.

- Task/ảnh/vùng: `000000350023.jpg`
- Lỗi thuộc loại: thừa vật
- Bằng chứng tôi nhìn thấy: ở phía bên phải ảnh, giữa vegetion và building, tôi thấy thừa một vật.
- Quy tắc và hành động sửa: chỉ gán nhãn cho vật nhìn thấy
- Sau sửa đã Save và export lại chưa? đã save và export

Nếu bạn **đã xem Summary tự đánh giá trên GitHub Actions hoặc tự chạy script**, ghi ngắn một kết quả liên quan lỗi vừa sửa (ví dụ task, metric trước/sau nếu có): … / chưa có điểm. Scorecard ba tier tối đa **82**, không phải điểm cuối trên 100. Không tự ghi PASS/top 3/bonus; người phụ trách xác nhận theo tiêu chí lớp. Không đưa file ground truth vào fork.

## 4. Ba ca chưa chắc hoặc đã cân nhắc

Mỗi ca là một **vùng cụ thể** khiến bạn phải cân nhắc hai cách hiểu. Ghi dấu hiệu nhìn thấy hoặc quy tắc đã dùng, rồi nêu quyết định hoặc câu hỏi cho coach. Không cần ba lỗi; ca đã quyết định được cũng hợp lệ.

| Ảnh/vị trí | Hai cách hiểu có thể | Quy tắc/chứng cứ | Quyết định hoặc câu hỏi cho coach |
| --- | --- | --- | --- |
| cp1_holes / 000000144300.jpg: nhà caravan trắng bên trái và xe van xanh phía sau xe máy | (a) gán bus vì là phương tiện lớn có bánh và có thể trở khách; (b) caravan là nhà kéo  | Trạm chỉ có 6 class person/bicycle/car/motorcycle/bus/truck; không có class trailer/van riêng | Gán là bus (2 object). Hỏi coach: caravan không có đầu kéo có nên để bus không? |