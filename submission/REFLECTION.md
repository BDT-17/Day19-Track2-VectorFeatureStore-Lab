# Reflection - Lab 19

**Tên:** Bùi Đức Thắng  
**MSSV:** 2A202600002  
**Cohort:** Cohort 1 - Track 2: Data & Infrastructure  
**Path đã chạy:** `lite`

---

## Câu hỏi (<= 200 chữ)

Trên golden set 50 queries, `hybrid` thắng tổng thể với Precision@10 = `78.6%`,
cao hơn `keyword = 77.8%` và `semantic = 73.2%`. Ở nhóm `exact`, BM25 và hybrid
gần như ngang nhau vì query chứa từ khóa kỹ thuật xuất hiện trực tiếp trong
corpus. Ở nhóm `mixed`, hybrid thắng rõ nhất (`100.0%`) vì RRF kết hợp được
tín hiệu keyword và semantic. Ở nhóm `paraphrase`, kết quả giảm cho cả 3 mode
do lite path dùng `bge-small-en`, chưa tối ưu cho paraphrase tiếng Việt.

Tôi không dùng hybrid khi ưu tiên chi phí và độ trễ, hoặc khi bài toán chỉ cần
một loại tín hiệu rõ ràng. BM25 thuần phù hợp cho exact match, mã lỗi, mã sản
phẩm, và truy vấn có từ khóa đặc thù. Vector thuần phù hợp khi cần tìm gần
nghĩa, cross-lingual, hoặc khi exact keyword không quan trọng.

---

## Điều ngạc nhiên nhất khi làm lab này

Điều làm tôi ấn tượng nhất là RRF rất đơn giản nhưng lại hiệu quả: không cần
chuẩn hóa score giữa BM25 và vector vẫn hợp nhất được hai bảng xếp hạng. Tôi
cũng gặp một vấn đề thực tế trên Windows với Feast metrics, cho thấy phần
environment và reproducibility quan trọng không kém thuật toán.

---

## Bonus challenge

- [ ] Đã làm bonus (xem `bonus/`)
- [ ] Pair work với: `N/A`
