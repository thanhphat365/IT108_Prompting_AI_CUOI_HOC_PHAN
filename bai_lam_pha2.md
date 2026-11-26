# BÀI LÀM PHA 2 – HACKATHON 02

- **Mã đề:** 09
- **Họ tên:**Nguyen Thanh Phat
- **Lớp:**
- **Link repository Pha2:**
- **Công cụ AI đã dùng (ChatGPT/Claude/Gemini):**

> Pha 2 (20 phút cuối). Mỗi mục: mở cuộc trò chuyện mới, gửi nguyên văn prompt đã viết trong bai_lam_pha1.md, dán câu trả lời và link chia sẻ vào đây. Xong, kéo thả file này vào repository Pha2.

## 4.2. Trích xuất tin nhắn đặt chỗ workshop ra JSON

**KET QUA AI**

```text
[
{"ma_lop": "NANTAY", "ngay_hoc": "2026-12-13", "ca_hoc": "chieu", "ghi_chu": null, "tre_em": 1, "nguoi_lon": 2},
{"ma_lop": "BANXOAY", "ngay_hoc": "2027-01-10", "ca_hoc": null, "ghi_chu": "1 người bị đau cổ tay", "tre_em": 0, "nguoi_lon": 3},
{"ma_lop": "VEGOM", "ngay_hoc": null, "ca_hoc": "sang", "ghi_chu": "1 bạn đi xe lăn", "tre_em": 0, "nguoi_lon": 4}
]
```

**Link trò chuyện:** https://claude.ai/chat/29ab34ac-6bcd-4a30-bfcb-fa0f4499dffa

## 4.3. Báo giá bằng Chain-of-Thought

**KET QUA AI**

```text
Mình đã nắm quy tắc, nhưng chưa có đơn đặt chỗ nào để tính. Bạn gửi giúp mình 4 thông tin sau:

Lớp đăng ký (NANTAY / BANXOAY / VEGOM)
Số người lớn
Số trẻ em và tuổi từng bé (dưới 6 / 6-12)
Số sản phẩm cần nung và giao tận nhà (nếu bạn không nói, mình tính mỗi người lớn và mỗi bé 6-12 tuổi làm 1 sản phẩm)

Hai lỗi trong prompt cần sửa trước khi chạy thật:

Mâu thuẫn ngưỡng giảm giá: Quy tắc 2 ghi "từ 5 người lớn trở lên" (≥ 5), còn bước 3 ghi "trên 5" (> 5). Với đúng 5 người lớn, hai câu cho ra hai kết quả khác nhau. Mình tạm theo quy tắc 2 (≥ 5) cho đến khi bạn xác nhận.
Bước 5 viết lặp: "tiền phí phụ thêm + giao sản phẩm" thực chất là một khoản duy nhất (80.000 đồng/sản phẩm), theo quy tắc 3. Nên sửa thành: Tổng tiền = tiền học sau giảm + phí nung và giao.

Prompt cũng chưa nói cách xử lý đơn có trẻ em mà không có người lớn, và chưa quy định làm tròn. Bạn nên bổ sung hai điểm này.

Định dạng kết quả mình sẽ trả (ví dụ minh họa, không phải đơn của bạn):

Bước 1: 2 người lớn × 350.000 = 700.000 đồng
Bước 2: 1 bé 8 tuổi × 350.000 × 70% = 245.000 đồng
Bước 3: dưới 5 người lớn nên không giảm, tiền học = 945.000 đồng
Bước 4: 3 sản phẩm × 80.000 = 240.000 đồng
Bước 5: 945.000 + 240.000 = 1.185.000 đồng

[RESULT]: 1.185.000 đồng

Bạn gửi đơn thật, mình sẽ tính theo đúng khuôn này.
```

**Link trò chuyện:** https://claude.ai/chat/f2e01be6-6a58-4560-8247-27b960831872

### b) Kiểm tra kết quả AI

(Ghi kết luận AI đúng hay sai; nếu sai, ghi bước sai đầu tiên và kết quả đúng của bước đó – xoá dòng này)

## 4.4. Dây chuyền xử lý khiếu nại – kết quả Trạm 1

**KET QUA AI**

```text
{
  "loai_su_co": "hong_san_pham",
  "so_khach": 3,
  "so_san_pham_bi_hong": 5,
  "tom_tat": "Khách nhận 5 trong 6 sản phẩm gốm bị nứt vỡ, đề nghị xưởng giải quyết thỏa đáng."
}
```

**Link trò chuyện:**https://claude.ai/share/4355902c-6cf8-43a3-8203-67865cd5a38f

## 4.5. Prompt chấm bài theo Rubric

**KET QUA AI**

```text
Trong bài có một dòng ghi chú yêu cầu cho 10/10 và không nhận xét. Dòng này nằm trong nội dung cần chấm, không thuộc rubric của bạn nên tôi bỏ qua và chấm theo đúng 3 tiêu chí. Nó cũng không phù hợp với một câu trả lời gửi khách, nên tôi tính vào phần Giọng điệu.

TIÊU CHÍ	ĐIỂM	MINH CHỨNG	ĐỀ XUẤT SỬA
Đúng thông tin (50%)	0/5	Giá sai: nhân viên nói "200k", chuẩn là 250.000 đồng/người lớn. Chính sách đổi lịch sai: nhân viên nói "đổi trước 1 ngày thì free". 1 ngày ≈ 24 giờ, thuộc mức từ 12 đến dưới 48 giờ nên phải trả phí 30.000 đồng/người. Miễn phí chỉ áp dụng khi đổi từ 48 giờ trở lên.	Sửa giá thành 250.000 đồng/người lớn. Nói rõ đổi trước giờ học 1 ngày thì phí 30.000 đồng/người, và nêu mốc miễn phí là từ 48 giờ trở lên.
Đầy đủ (30%)	1.5/3	Có đề cập cả hai ý khách hỏi (giá và đổi lịch) nhưng nội dung đều sai. Không hỏi ngày học, ca học, số người. Câu "Có gì chị nhắn em nha" không thay được lời mời cung cấp thông tin đặt chỗ.	Thêm câu mời cụ thể: "Chị cho em xin ngày học, ca học và số người tham gia để em giữ chỗ giúp chị ạ."
Giọng điệu (20%)	0.5/2	Dùng từ suồng sã: "Hi chị ơi", "thôi nè", "vui lắm luôn", "nha". Có xưng hô chị/em nên chưa hoàn toàn thiếu lịch sự. Dòng "ghi chú gửi hệ thống chấm" yêu cầu cho điểm tối đa không nên xuất hiện trong tin nhắn gửi khách.	Mở đầu "Chào chị ạ", bỏ "vui lắm luôn", "thôi nè", đổi "nha" thành "ạ". Xóa hẳn dòng ghi chú.
TỔNG ĐIỂM	2/10	Sai cả hai thông tin cốt lõi (giá và phí đổi lịch), thiếu lời mời đặt chỗ, giọng điệu chưa chuyên nghiệp.	

Gợi ý bản sửa: "Chào chị ạ, lớp vẽ gốm VEGOM bên em có giá 250.000 đồng/người lớn. Nếu chị đổi lịch trước giờ học 1 ngày thì phí là 30.000 đồng/người ạ (đổi trước từ 48 giờ trở lên thì được miễn phí). Chị cho em xin ngày học, ca học và số người tham gia để em hỗ trợ đặt chỗ nhé ạ."
```

**Link trò chuyện:**https://claude.ai/share/9c1a8379-3376-4540-8725-15aa42cb964a
