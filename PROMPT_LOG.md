# NHẬT KÝ PROMPT ENGINEERING (VIBE CODING LOG)

- **Họ và tên:** Lê Cao Duy Khang
- **MSSV:** 125000847
- **Tên đề tài Website:** Website Sản phẩm & Tin tức Công nghệ Đột phá (NexTech Landing Page)
- **Công cụ AI đã sử dụng:** Gemini 2.5 Flash / Advanced Agentic Assistant (Vibe Coding)

---

## 1. Yêu cầu ban đầu (System/Initial Prompt)

> **Prompt khởi tạo:**  
> "Bạn là một Chuyên gia Lập trình Web Senior (Senior Front-End Developer & UI/UX Designer). Hãy giúp tôi xây dựng dự án website cho bài thi Giữa kỳ môn Thiết kế Web với thông tin: Sinh viên Lê Cao Duy Khang, MSSV: 125000847. Đề tài: Landing Page Sản phẩm & Tin tức Công nghệ (NexTech).  
> Yêu cầu bắt buộc:  
> 1. Chuẩn Semantic HTML5: tối thiểu 5 thành phần `<header>`, `<nav>`, `<main>`, `<section>`/`<article>`, `<footer>`, tuyệt đối không lạm dụng thẻ `<div>`.  
> 2. Kỹ thuật CSS & CSS Variables: khai báo hệ thống `:root` màu Dark Tech/Cyberpunk, font chữ, spacing; sử dụng layout CSS Flexbox/Grid; tự viết hiệu ứng `:hover`, `:focus` mượt mà cho button và cards.  
> 3. Tích hợp thư viện hiệu ứng: Animate.css (cho Hero banner, tiêu đề) và AOS (Animate On Scroll) khi cuộn trang, kèm `AOS.init()`.  
> Hãy xuất ra cấu trúc file gồm `index.html` và `style.css`."

---

## 2. Quá trình tinh chỉnh & Giải quyết sự cố (Iteration Iterations)

### Lần 1: Dựng khung Semantic HTML & Hệ thống CSS Variables
- **Prompt đã dùng:**  
  *"Kiểm tra lại cấu trúc HTML. Đảm bảo cấu trúc trang không bị lạm dụng thẻ `<div>` bọc lung tung. Các khối danh mục sản phẩm và bài viết tin tức phải dùng thẻ `<article>`, khối thông tin liên hệ dùng `<address>`, ngày tháng dùng thẻ `<time>`. Khai báo bảng màu Dark Tech vào biến CSS `:root` gồm màu chủ đạo Cyber Cyan (`#00f2fe`), Cyber Violet (`#7928ca`), cùng hệ thống spacing và bo góc chuẩn."*
- **Kết quả AI tạo ra:**  
  AI đã thay thế các thẻ container bằng `<header>`, `<nav>`, `<main>`, `<section>`, `<article>`, `<figure>`, `<footer>`, `<address>`. File `style.css` định nghĩa toàn bộ biến CSS trong `:root` với gradient và neon shadow sắc sảo.
- **Nhận xét & Tinh chỉnh của SV:**  
  Cấu trúc HTML rất sạch và chuẩn ngữ nghĩa W3C. Tuy nhiên, tôi nhận thấy trên giao diện di động (dưới 768px), thanh menu navbar bị tràn màn hình. Tôi đã yêu cầu AI bổ sung nút hamburger menu (`#menuToggle`) với thuộc tính trợ năng `aria-expanded`, đồng thời ẩn/hiện navbar mượt mà bằng CSS Flexbox `column` và JavaScript toggling class `.is-open`.

---

### Lần 2: Tích hợp thư viện Animate.css & AOS (Animate On Scroll)
- **Prompt đã dùng:**  
  *"Nhúng CDN của Animate.css v4 và AOS v2 vào thẻ `<head>`. Áp dụng các class `animate__animated animate__fadeInDown`, `animate__fadeInLeft`, `animate__zoomIn` vào Hero Section. Với các section Sản phẩm, Tính năng và Tin tức, gắn thuộc tính `data-aos="fade-up"` và `data-aos-delay`. Viết mã kích hoạt `AOS.init()` ở cuối thẻ `<body>`."*
- **Thách thức gặp phải:**  
  Khi chạy thử nghiệm, một số phần tử có gắn `data-aos` bị ẩn hoàn toàn hoặc khi cuộn nhanh thì hiệu ứng bị giật cục, không kích hoạt đúng thời điểm. Đồng thời, Animate.css nếu chạy liên tục sẽ gây xao nhãng trải nghiệm người dùng (UX).
- **Cách sửa prompt (Debug prompt):**  
  *"Hãy tối ưu script khởi tạo AOS với tham số `{ duration: 800, once: true, offset: 100, easing: 'ease-out-cubic' }` để hiệu ứng cuộn mượt và chỉ chạy một lần, tránh render lại gây lag. Thêm thuộc tính `overflow-x: hidden` cho thẻ `body` và `html` trong `style.css` để tránh lỗi xuất hiện thanh cuộn ngang khi AOS thực hiện animation dịch chuyển tọa độ X. Ngoài ra, thêm nút Back-To-Top tự động hiển thị khi cuộn quá 300px."*
- **Kết quả sau sửa đổi:**  
  Hiệu ứng cuộn hoạt động cực kỳ mượt mà, không giật lag, không sinh lỗi tràn thanh cuộn ngang, giao diện toát lên vẻ cao cấp và hiện đại đúng chuẩn Vibe Coding.

---

## 3. Đánh giá cá nhân về quá trình Vibe Coding

### 1. AI đã giúp bạn tiết kiệm thời gian ở phần nào nhất?
- **Khởi tạo Boilerplate & CSS Variables:** AI sinh ra toàn bộ bảng mã màu, font typography và spacing trong `:root` chỉ trong vài giây, giúp tiết kiệm ít nhất 40-50 phút so với việc ngồi gõ tay và tra cứu mã màu HEX/RGBA.
- **Cấu trúc Semantic HTML chuẩn chỉ:** Việc sinh sẵn các thẻ ngữ nghĩa `<article>`, `<figure>`, `<time>`, `<address>` cùng hệ thống class BEM rõ ràng giúp việc phân chia layout diễn ra ngay lập tức.
- **Tích hợp thư viện CDN chính xác:** AI cung cấp đường dẫn CDN phiên bản mới nhất, tương thích tốt và kèm sẵn cấu hình khởi tạo JavaScript tiêu chuẩn.

### 2. Bài học rút ra khi đặt câu hỏi (Prompt) cho AI trong thiết kế web?
- **Đặt câu hỏi có ngữ cảnh & vai trò rõ ràng (Role-based Prompting):** Khi yêu cầu AI đóng vai "Senior Front-End Developer & UI/UX Designer", chất lượng mã nguồn tạo ra có tư duy tổ chức cao hơn hẳn, code sạch và có chú thích chi tiết.
- **Đưa ra các ràng buộc kỹ thuật khắt khe (Negative Constraints):** Việc nêu rõ *"Tuyệt đối KHÔNG lạm dụng thẻ `<div>` vô nghĩa"* và *"Bắt buộc dùng Semantic HTML5, CSS Variables trong `:root`"* giúp AI tuân thủ đúng barem điểm chấm thi của Giảng viên mà không tự ý viết tắt hay dùng framework ngoài ý muốn.
- **Tư duy tinh chỉnh từng bước (Iterative Refinement):** Không nên mong đợi AI hoàn hảo 100% trong một lượt prompt duy nhất. Cần kiểm tra mã nguồn thực tế, phát hiện các điểm nghẽn (như menu responsive trên mobile, lỗi thanh cuộn ngang khi dùng AOS) và đưa ra prompt điều chỉnh cụ thể để đạt kết quả xuất sắc nhất.
