# BÀI THỰC HÀNH 1: TRÍCH XUẤT VÀ ĐỊNH DẠNG THÔNG TIN TUYỂN DỤNG

## 1 .PROMPT TRÍCH XUẤT THÔNG TIN TUYỂN DỤNG

C – Context : Bạn là chuyên viên xử lý dữ liệu nhân sự cấp cao của một công ty công nghệ.

R – Request : Đọc email ứng tuyển và trích xuất 6 thông tin: Họ tên, Số điện thoại, Email, Vị trí ứng tuyển, Năm kinh nghiệm và Kỹ năng chính.

E – Explanation : Thông tin được dùng để nhập vào database tuyển dụng nên phải chính xác, không được tự suy đoán.

A – Action :
- Chuẩn hóa họ tên, viết hoa chữ cái đầu.
- Loại bỏ khoảng trắng thừa trong số điện thoại và chuẩn hóa định dạng nếu có đủ thông tin.
- Chuyển năm kinh nghiệm thành số.
- Đưa kỹ năng vào danh sách, không để trùng lặp.
- Thông tin không có trong email ghi null, riêng kỹ năng ghi [].
- Xuất kết quả thành bảng Markdown và JSON.

T – Tone : Ngắn gọn, chính xác, khách quan.

E – Extras ví dụ Few-shot :

**VÍ DỤ 1**

Input email:

"Tôi tên NGUYỄN VĂN AN, ứng tuyển Backend Developer. Tôi có 2 năm kinh nghiệm, sử dụng Python, SQL, FastAPI. SĐT 0912345678, email an@gmail.com."

Output:

Bảng Markdown:

| Thông tin | Kết quả |
|---|---|
| Họ tên | Nguyễn Văn An |
| Số điện thoại | 0912345678 |
| Email | an@gmail.com |
| Vị trí ứng tuyển | Backend Developer |
| Năm kinh nghiệm | 2 |
| Kỹ năng chính | Python, SQL, FastAPI |

Json:

{
  "name": "Nguyễn Văn An",
  "phone": "0912345678",
  "email": "an@gmail.com",
  "position": "Backend Developer",
  "experience_years": 2,
  "skills": ["Python", "SQL", "FastAPI"]
}

**VÍ DỤ 2**

Input email:

"Tôi là trần thị mai, muốn ứng tuyển Tester. Tôi có 1 năm kinh nghiệm kiểm thử phần mềm, biết Selenium, SQL và Jira. Email: mai@gmail.com."

Output:

Bảng Markdown:

| Thông tin | Kết quả |
|---|---|
| Họ tên | Trần Thị Mai |
| Số điện thoại | null |
| Email | mai@gmail.com |
| Vị trí ứng tuyển | Tester |
| Năm kinh nghiệm | 1 |
| Kỹ năng chính | Selenium, SQL, Jira |

Json:

{"name": "Trần Thị Mai","phone": null,"email": "mai@gmail.com","position": "Tester","experience_years": 1,"skills": ["Selenium", "SQL", "Jira"]}

## Yêu cầu khi xử lý email mới:

Chỉ xuất bảng Markdown và một đối tượng JSON theo đúng cấu trúc sau:

{
  "name": null,
  "phone": null,
  "email": null,
  "position": null,
  "experience_years": null,
  "skills": []
}

Không tự thêm thông tin, không suy đoán dữ liệu còn thiếu và không viết giải thích ngoài kết quả

## 2 .KIỂM TRA JSON
Sử dụng công cụ JSONLint để kiểm tra cú pháp JSON :

-Không thiếu dấu ngoặc hoặc dấu phẩy

-Đúng tên các trường dữ liệu

-experience_years là kiểu số

-skills là kiểu mảng

-Thông tin thiếu được ghi null
