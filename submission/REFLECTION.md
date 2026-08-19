# Reflection — Lab 19

**Tên:** Nguyễn Minh Phương
**Cohort:** A20-K3
**Path đã chạy:** lite

---

## Câu hỏi (≤ 200 chữ)

> Trên golden set 50 queries, mode nào thắng ở loại query nào (`exact` /
> `paraphrase` / `mixed`), và tại sao? Khi nào bạn **không** dùng hybrid
> (i.e. khi nào pure BM25 hoặc pure vector là lựa chọn đúng)?

Trên 50 truy vấn, hybrid đạt Precision@10 cao nhất (78,6%), hơn BM25
(77,8%) và vector (73,2%). Với `exact`, BM25 và hybrid cùng đạt 96,7%. Với
`mixed`, hybrid thắng ở 100%, so với vector 98,5% và BM25 97,0%. Riêng
`paraphrase`, BM25 đạt 33,3%, hybrid 32,0% và vector 24,0%. Vector yếu vì Lite
dùng `bge-small-en-v1.5`,
model thiên tiếng Anh nên hiểu paraphrase tiếng Việt còn yếu.

Tôi không dùng hybrid khi cần exact match hoặc ưu tiên latency: NB3 đo P99
keyword 4,3 ms, thấp hơn nhiều so với hybrid 112,9 ms. Pure BM25 phù hợp cho mã,
tên và cụm từ chính xác. Pure vector phù hợp khi lexical mismatch là vấn đề chính
và đã có model đa ngữ tốt. Hybrid phù hợp khi dữ liệu có cả tín hiệu từ khóa lẫn
ngữ nghĩa và chất lượng quan trọng hơn chi phí suy luận.

---

## Điều ngạc nhiên nhất khi làm lab này

Vector không tự động thắng paraphrase: chất lượng phụ thuộc mạnh vào ngôn ngữ
của embedding model. Hybrid vẫn thắng trung bình dù chỉ hơn BM25 0,8 điểm phần trăm.

---

## Bonus challenge

- [ ] Đã làm bonus (xem `bonus/`)
- [ ] Pair work với: _<tên đồng đội nếu có>_
