

  
**Bài 6 : Sự cố tài liệu dự án trên GitHub
PHẦN 1: PHÂN TÍCH SAI LẦM VÀ LỢI THẾ CỦA MARKDOWN**

1. Hai sai lầm cốt lõi trong tư duy của Nam khi dùng file Rich Text (`.docx`)

-   **Sai lầm 1: Nhầm lẫn về bản chất tệp tin lưu trữ mã nguồn:** File Word (`.docx`) bản chất là định dạng **Rich Text** (văn bản mã hóa nhị phân phức tạp bao gồm siêu dữ liệu cấu hình font chữ, layout, style...). Nó không phải là văn bản thuần túy nên trình duyệt web và GitHub không thể đọc/hiển thị trực tiếp nội dung văn bản bên trong nếu không có trình đọc chuyên dụng.
-   **Sai lầm 2: Phá vỡ cơ chế theo dõi phiên bản (Git Diff & Conflict):** Do là file nhị phân, hệ thống Git quản lý mã nguồn không thể bóc tách cấu trúc theo từng dòng chữ. Khi Nam sửa dù chỉ một dấu phẩy, Git buộc phải ghi nhận toàn bộ cấu trúc nhị phân của file đã bị thay đổi, dẫn đến việc báo lỗi xung đột (**Conflict**) toàn bộ tệp tin, gây ác mộng cho việc làm việc nhóm.

2. Tại sao Markdown an toàn, nhẹ hơn và chống hư hại file tốt hơn?

-   **Siêu nhẹ:** Markdown thuộc loại **Plain Text** (văn bản thô). Nó chỉ lưu các ký tự chữ và ký hiệu định dạng cơ bản (`#`, `*`), hoàn toàn không chứa mã nhị phân phụ trợ nên dung lượng file nhẹ hơn Word gấp hàng trăm lần.
-   **Tối ưu cho Git:** Git có thể dễ dàng so sánh cấu trúc Plain Text theo từng dòng chữ đơn lẻ (**Git Diff**). Ai sửa dòng nào, hệ thống chỉ cập nhật chính xác dòng đó, loại bỏ hoàn toàn lỗi xung đột file diện rộng.
-   **Chống hư hại file (Bẫy dữ liệu):** Nếu file `.docx` bị mất hoặc lỗi 1 byte dữ liệu khi truyền qua mạng, toàn bộ cấu trúc định dạng nhị phân sẽ bị sụp đổ, khiến file **bị hỏng hoàn toàn và không thể mở được**. Ngược lại, nếu file Markdown `.md` bị mất 1 byte, hệ thống **chỉ bị mất hoặc sai lệch đúng 1 ký tự tại vị trí đó**, toàn bộ phần nội dung văn bản thô còn lại vẫn an toàn tuyệt đối và đọc được bình thường.

----------

PHẦN 2: CHUYỂN ĐỔI ĐOẠN GIỚI THIỆU SANG MARKDOWN (`.md`)

markdown

```
# 🌿 Dự án Nông nghiệp Thông minh - GreenTech

*Hệ thống quản lý chuỗi cung ứng nông sản sạch ứng dụng công nghệ IoT toàn diện.*

## 1. Giới thiệu chung
Dự án **GreenTech** ra đời nhằm mục đích giải quyết bài toán tối ưu hóa quy trình tưới tiêu và giám sát chất lượng đất cho các nông trại thông minh tại Việt Nam.

## 2. Các tính năng cốt lõi
Hệ thống cung cấp bộ giải pháp quản lý khép kín bao gồm:
- [x] Tự động đo đạc độ ẩm và kích hoạt máy bơm nước qua vi xử lý SoC.
- [x] Lọc và hiển thị dữ liệu lỗi hệ thống trực tiếp qua giao diện dòng lệnh.
- [ ] Gửi báo cáo phân tích định kỳ hàng ngày về tình trạng sức khỏe cây trồng.

> **GreenTech — Mang công nghệ số đến từng luống rau xanh!**
```
