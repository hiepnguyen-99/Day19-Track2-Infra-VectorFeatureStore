# Reflection - Lab 19

**Tên:** Nguyễn Xuân Hiệp  
**Lớp:** Cohort 2  

---

## Câu hỏi (<= 200 chữ)

Trên tập mẫu (golden set) gồm 50 truy vấn, phương pháp Hybrid đạt kết quả tốt nhất: BM25 đạt 77.8%, Vector đạt 73.2%, và Hybrid đạt 78.6%. 

Với các truy vấn dạng `exact`, BM25 thể hiện sức mạnh vượt trội do truy vấn chứa chính xác các thuật ngữ trong kho dữ liệu; lúc này kết quả Hybrid gần như tương đương BM25 vì tín hiệu từ từ khóa đã đủ rõ ràng. Với dạng `mixed`, Hybrid thể hiện ưu thế rõ rệt nhất nhờ thuật toán RRF đã kết hợp thành công cả hai nguồn tín hiệu: thuật ngữ chính xác và ngữ nghĩa diễn đạt lại (paraphrase). Ở dạng `paraphrase`, do sử dụng mô hình `BAAI/bge-small-en-v1.5` (vốn được huấn luyện chủ yếu bằng tiếng Anh), kết quả Vector không vượt qua được BM25 như kỳ vọng vì chưa tối ưu cho việc hiểu ngữ nghĩa tiếng Việt.

Tôi sẽ không dùng Hybrid khi khối lượng công việc (workload) chủ yếu là các từ khóa chính xác, khi cần tối ưu chi phí/độ trễ (latency), hoặc khi kết quả tìm kiếm cần được giải thích rõ ràng dựa trên khớp từ vựng. Ngược lại, Pure Vector sẽ phù hợp hơn khi truy vấn là ngôn ngữ tự nhiên, đa ngôn ngữ hoặc ít chứa các thuật ngữ kỹ thuật đặc thù.

---

## Điều ngạc nhiên nhất khi làm lab này

Đó là phương pháp Hybrid không nhất thiết phải chiến thắng áp đảo ở mọi phân khúc (slice) dữ liệu; nó chỉ cần hoạt động ổn định (robust) trên các truy vấn dạng hỗn hợp (mixed queries) là đã đủ giá trị để triển khai trong thực tế (production).

---

## Bonus challenge

- [v] Đã làm bonus (xem `bonus/`)
- [ ] Làm việc nhóm cùng: _<tên đồng đội nếu có>_