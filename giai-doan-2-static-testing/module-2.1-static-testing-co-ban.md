# MODULE 2.1: STATIC TESTING CƠ BẢN

**Thời lượng**: 2-3 giờ | **Độ khó**: ⭐⭐

---

## MỤC TIÊU HỌC TẬP (Learning Objectives)

Sau khi hoàn thành module này, bạn sẽ:

| ID | Mục tiêu | Level |
|----|----------|-------|
| FL-3.1.1 | Nhận biết các work products có thể được kiểm tra bằng static testing | K1 |
| FL-3.1.2 | Giải thích giá trị của static testing | K2 |
| FL-3.1.3 | So sánh static testing với dynamic testing | K2 |

---

## 1. STATIC TESTING LÀ GÌ?

### 1.1. Định Nghĩa

> **Static Testing (Kiểm thử tĩnh)** là kỹ thuật kiểm thử phần mềm **KHÔNG thực thi code**. Thay vào đó, chúng ta kiểm tra các "work products" (sản phẩm công việc) bằng cách **đọc, xem xét, phân tích**.

```
STATIC TESTING = Kiểm tra mà KHÔNG chạy phần mềm
                 ↓
         Đọc và phân tích documents, code, designs
```

### 1.2. So Sánh: Static Testing vs Dynamic Testing

| Khía cạnh | Static Testing | Dynamic Testing |
|-----------|----------------|-----------------|
| **Thực thi code** | ❌ KHÔNG | ✅ CÓ |
| **Đối tượng** | Documents, code, designs | Phần mềm đang chạy |
| **Thời điểm** | Sớm (trước khi code xong) | Muộn hơn (sau khi code) |
| **Công cụ** | Reviews, static analyzers | Test tools, test scripts |
| **Tìm defects** | Defects trong documents/code | Failures khi chạy |
| **Chi phí sửa** | Thấp (phát hiện sớm) | Cao hơn (phát hiện muộn) |

### 1.3. Ví Dụ Minh Họa

**Tình huống: Phát triển app đặt xe (như Grab)**

```
📋 STATIC TESTING (Trước khi code):
├── Review requirement document
│   → Phát hiện: "Thiếu yêu cầu về cancel booking"
│
├── Review UI mockups
│   → Phát hiện: "Nút thanh toán quá nhỏ trên mobile"
│
└── Review source code (code review)
    → Phát hiện: "Lỗ hổng SQL injection ở function login"

🖥️ DYNAMIC TESTING (Sau khi code):
├── Test login feature
│   → Phát hiện: "Login fails với password có ký tự đặc biệt"
│
├── Test booking flow
│   → Phát hiện: "App crash khi GPS bị tắt"
│
└── Performance testing
    → Phát hiện: "Response time > 5s khi 1000 users"
```

---

## 2. GIÁ TRỊ CỦA STATIC TESTING

### 2.1. Tại Sao Static Testing Quan Trọng?

```
    ┌─────────────────────────────────────────────────────────────┐
    │                    CHI PHÍ SỬA DEFECT                       │
    │                                                             │
    │   $$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$$  Production       │
    │   $$$$$$$$$$$$$$$$$$$$$$$$              System Testing      │
    │   $$$$$$$$$$$$$                         Integration         │
    │   $$$$$$                                 Unit Testing       │
    │   $                                      Requirements ← STATIC │
    │                                                             │
    │   Càng phát hiện SỚM → Chi phí sửa càng THẤP               │
    └─────────────────────────────────────────────────────────────┘
```

### 2.2. Lợi Ích Chính

| Lợi ích | Giải thích | Ví dụ |
|---------|------------|-------|
| **1. Phát hiện defects SỚM** | Tìm lỗi trước khi code, tiết kiệm chi phí | Review requirement phát hiện logic sai |
| **2. Chi phí thấp** | Sửa document dễ hơn sửa code đã deploy | Sửa 1 dòng trong spec vs refactor code |
| **3. Cải thiện chất lượng** | Documents rõ ràng → Code tốt hơn | Requirements đầy đủ → Ít bugs |
| **4. Tìm defects mà dynamic testing khó tìm** | Một số lỗi không thể hiện khi chạy | Code standards violations, security holes |
| **5. Tăng giao tiếp** | Review = Discussion giữa team members | Hiểu rõ requirements hơn |
| **6. Giảm testing effort** | Ít bugs → Ít test cycles | Tiết kiệm thời gian regression |

### 2.3. Defects Mà CHỈ Static Testing Mới Tìm Được

```
╔══════════════════════════════════════════════════════════════╗
║  DEFECTS CHỈ STATIC TESTING TÌM ĐƯỢC:                        ║
╠══════════════════════════════════════════════════════════════╣
║                                                              ║
║  📄 Requirements:                                            ║
║     • Mâu thuẫn giữa requirements                            ║
║     • Requirements mơ hồ, không rõ ràng                      ║
║     • Thiếu requirements quan trọng                          ║
║                                                              ║
║  🎨 Design:                                                  ║
║     • Design không phù hợp với requirements                  ║
║     • Missing error handling                                 ║
║     • Inefficient algorithms                                 ║
║                                                              ║
║  💻 Code:                                                    ║
║     • Coding standards violations                            ║
║     • Dead code (code không bao giờ được chạy)              ║
║     • Security vulnerabilities                               ║
║     • Maintainability issues                                 ║
║                                                              ║
║  📝 Test artifacts:                                          ║
║     • Test cases thiếu coverage                              ║
║     • Incorrect expected results                             ║
║                                                              ║
╚══════════════════════════════════════════════════════════════╝
```

### 2.4. Ví Dụ Thực Tế Việt Nam

**Case Study: VNPay - Mobile Payment App**

```
SCENARIO: Phát triển tính năng "Chuyển tiền liên ngân hàng"

📋 STATIC TESTING (Review Requirements):
─────────────────────────────────────────
Requirement ban đầu:
"User có thể chuyển tiền đến tài khoản ngân hàng khác"

Static Review phát hiện:
├── ❌ Thiếu: Giới hạn số tiền chuyển/ngày?
├── ❌ Thiếu: Xử lý khi số dư không đủ?
├── ❌ Thiếu: Confirm OTP trước khi chuyển?
├── ❌ Thiếu: Thông báo cho người nhận?
└── ❌ Mơ hồ: "Ngân hàng khác" - danh sách cụ thể?

Sau review, requirements được bổ sung:
├── ✅ Giới hạn: 500 triệu/giao dịch, 2 tỷ/ngày
├── ✅ Validate số dư trước khi xử lý
├── ✅ Yêu cầu OTP cho giao dịch > 10 triệu
├── ✅ Push notification cho người nhận
└── ✅ Support 45 ngân hàng theo danh sách NAPAS

KẾT QUẢ:
→ Phát hiện 5 defects TRƯỚC khi code
→ Tiết kiệm ước tính: 2 tuần development
→ Tránh được lỗi security nghiêm trọng (missing OTP)
```

---

## 3. CÁC KỸ THUẬT STATIC TESTING

### 3.1. Tổng Quan

```
                    STATIC TESTING
                         │
            ┌────────────┴────────────┐
            ▼                         ▼
       REVIEWS                  STATIC ANALYSIS
     (Manual)                   (Tool-based)
            │                         │
    ┌───────┼───────┐                 │
    ▼       ▼       ▼                 ▼
Informal  Formal  Technical    Static analyzers
review    review  review       (SonarQube, etc.)
```

### 3.2. Reviews (Manual Examination)

**Định nghĩa**: Kiểm tra work products bằng mắt người

| Loại Review | Mô tả | Ví dụ |
|-------------|-------|-------|
| **Informal Review** | Không có process formal, buddy check | Developer nhờ đồng nghiệp xem code |
| **Walkthrough** | Author trình bày work product | Designer walkthrough UI mockups |
| **Technical Review** | Experts đánh giá technical quality | Architecture review |
| **Inspection** | Formal nhất, có metrics | Code inspection với checklist |

### 3.3. Static Analysis (Tool-based)

**Định nghĩa**: Sử dụng tools để tự động phân tích code/documents

```
SOURCE CODE
    │
    ▼
┌─────────────────────────────────────────┐
│         STATIC ANALYSIS TOOL            │
│         (SonarQube, ESLint)             │
├─────────────────────────────────────────┤
│ Phân tích:                              │
│ • Coding standards                      │
│ • Security vulnerabilities              │
│ • Code complexity                       │
│ • Potential bugs                        │
│ • Code duplication                      │
└─────────────────────────────────────────┘
    │
    ▼
REPORT: Danh sách issues
```

**Ví dụ Output từ SonarQube:**

```
╔═══════════════════════════════════════════════════════════════╗
║ FILE: PaymentService.java                                     ║
╠═══════════════════════════════════════════════════════════════╣
║ 🔴 CRITICAL: SQL Injection vulnerability (Line 45)            ║
║    → String query = "SELECT * FROM users WHERE id=" + userId; ║
║    → FIX: Use prepared statements                             ║
║                                                               ║
║ 🟠 MAJOR: Method too complex (Cyclomatic complexity: 25)      ║
║    → processPayment() should be refactored                    ║
║                                                               ║
║ 🟡 MINOR: Magic number detected (Line 78)                     ║
║    → Replace 86400 with named constant SECONDS_PER_DAY        ║
║                                                               ║
║ 📊 Code Coverage: 45% (Target: 80%)                           ║
║ 📊 Duplication: 12%                                           ║
╚═══════════════════════════════════════════════════════════════╝
```

---

## 4. WORK PRODUCTS CÓ THỂ STATIC TEST

### 4.1. Danh Sách Work Products

```
╔════════════════════════════════════════════════════════════════╗
║               WORK PRODUCTS EXAMINABLE BY STATIC TESTING       ║
╠════════════════════════════════════════════════════════════════╣
║                                                                ║
║  📄 REQUIREMENTS PHASE:                                        ║
║     • Business requirements document                           ║
║     • User stories và acceptance criteria                      ║
║     • Use cases                                                ║
║     • Functional specifications                                ║
║                                                                ║
║  🎨 DESIGN PHASE:                                              ║
║     • System architecture document                             ║
║     • Database design (ERD)                                    ║
║     • UI/UX mockups và wireframes                             ║
║     • API specifications                                       ║
║                                                                ║
║  💻 DEVELOPMENT PHASE:                                         ║
║     • Source code                                              ║
║     • Database scripts                                         ║
║     • Configuration files                                      ║
║                                                                ║
║  🧪 TESTING PHASE:                                             ║
║     • Test plans                                               ║
║     • Test cases                                               ║
║     • Test data                                                ║
║     • Test scripts                                             ║
║                                                                ║
║  📚 OTHER:                                                     ║
║     • User manuals                                             ║
║     • Release notes                                            ║
║     • Contracts                                                ║
║     • Project plans                                            ║
║                                                                ║
╚════════════════════════════════════════════════════════════════╝
```

### 4.2. Ví Dụ: Static Testing Ở Mỗi Phase

**Dự án: Xây dựng app Shopee Food**

```
PHASE               WORK PRODUCT              STATIC TEST ACTIVITY
─────────────────────────────────────────────────────────────────
Requirements   →    User Stories         →    Review by BA, Tester
                    "Là user, tôi muốn       Checklist:
                    order food từ             □ Story rõ ràng?
                    restaurant gần nhất"      □ Acceptance criteria đủ?
                                             □ Testable?

Design         →    API Specification    →    Technical Review
                    POST /orders              Checklist:
                    {restaurant_id,           □ Request/Response format?
                     items[],                 □ Error handling?
                     delivery_address}        □ Authentication?

Code           →    OrderService.java    →    Code Review + Static Analysis
                                             SonarQube scan:
                                             □ Security issues?
                                             □ Code complexity?
                                             □ Test coverage?

Test           →    Test Cases           →    Peer Review
                    TC-ORDER-001              Checklist:
                    "Test order flow"         □ Steps đủ chi tiết?
                                             □ Expected results rõ?
                                             □ Edge cases covered?
```

---

## 5. DEFECTS TÌM ĐƯỢC BỞI STATIC TESTING

### 5.1. Phân Loại Defects

#### 5.1.1. Requirement Defects

```
╔══════════════════════════════════════════════════════════════╗
║  REQUIREMENT DEFECTS                                          ║
╠══════════════════════════════════════════════════════════════╣
║                                                              ║
║  🔴 AMBIGUITY (Mơ hồ):                                       ║
║     ❌ "System should respond quickly"                        ║
║     ✅ "System should respond within 2 seconds"               ║
║                                                              ║
║  🔴 INCONSISTENCY (Mâu thuẫn):                               ║
║     ❌ Requirement A: "Max 10 items per order"                ║
║     ❌ Requirement B: "Unlimited items allowed"               ║
║                                                              ║
║  🔴 INCOMPLETENESS (Thiếu):                                  ║
║     ❌ Không có requirement cho error handling                ║
║     ❌ Missing non-functional requirements                    ║
║                                                              ║
║  🔴 INCORRECT (Sai logic):                                   ║
║     ❌ "If age < 18, allow alcohol purchase"                  ║
║        (Logic ngược!)                                        ║
║                                                              ║
╚══════════════════════════════════════════════════════════════╝
```

#### 5.1.2. Design Defects

```
╔══════════════════════════════════════════════════════════════╗
║  DESIGN DEFECTS                                               ║
╠══════════════════════════════════════════════════════════════╣
║                                                              ║
║  🔴 INEFFICIENT ALGORITHMS:                                  ║
║     → Design sử dụng O(n²) khi có thể O(n log n)            ║
║                                                              ║
║  🔴 MISSING ERROR HANDLING:                                  ║
║     → Không có design cho trường hợp network failure        ║
║                                                              ║
║  🔴 SECURITY GAPS:                                           ║
║     → API không có authentication design                     ║
║                                                              ║
║  🔴 SCALABILITY ISSUES:                                      ║
║     → Design không support horizontal scaling               ║
║                                                              ║
║  🔴 MISALIGNMENT WITH REQUIREMENTS:                          ║
║     → Design thiếu feature so với requirements               ║
║                                                              ║
╚══════════════════════════════════════════════════════════════╝
```

#### 5.1.3. Code Defects

```
╔══════════════════════════════════════════════════════════════╗
║  CODE DEFECTS (Tìm bởi Static Analysis)                       ║
╠══════════════════════════════════════════════════════════════╣
║                                                              ║
║  🔴 SECURITY VULNERABILITIES:                                ║
║     • SQL Injection                                          ║
║     • XSS (Cross-Site Scripting)                             ║
║     • Hardcoded passwords                                    ║
║                                                              ║
║  🔴 CODING STANDARDS VIOLATIONS:                             ║
║     • Naming conventions                                     ║
║     • Code formatting                                        ║
║     • Missing comments                                       ║
║                                                              ║
║  🔴 MAINTAINABILITY ISSUES:                                  ║
║     • High cyclomatic complexity                             ║
║     • Code duplication                                       ║
║     • Long methods (>100 lines)                              ║
║                                                              ║
║  🔴 POTENTIAL BUGS:                                          ║
║     • Null pointer dereference                               ║
║     • Resource leaks                                         ║
║     • Dead code (unreachable)                                ║
║                                                              ║
╚══════════════════════════════════════════════════════════════╝
```

#### 5.1.4. Test Defects

```
╔══════════════════════════════════════════════════════════════╗
║  TEST ARTIFACT DEFECTS                                        ║
╠══════════════════════════════════════════════════════════════╣
║                                                              ║
║  🔴 INCORRECT TEST LOGIC:                                    ║
║     → Expected result sai so với requirement                 ║
║                                                              ║
║  🔴 MISSING TEST COVERAGE:                                   ║
║     → Không có test case cho negative scenarios              ║
║                                                              ║
║  🔴 INCOMPLETE TEST DATA:                                    ║
║     → Test data không cover boundary values                  ║
║                                                              ║
║  🔴 AMBIGUOUS TEST STEPS:                                    ║
║     → Người khác không thể follow test steps                 ║
║                                                              ║
╚══════════════════════════════════════════════════════════════╝
```

---

## 6. STATIC TESTING TOOLS PHỔ BIẾN

### 6.1. Công Cụ Theo Ngôn Ngữ

| Ngôn ngữ | Static Analysis Tools |
|----------|----------------------|
| **Java** | SonarQube, FindBugs, PMD, Checkstyle |
| **JavaScript/TypeScript** | ESLint, TSLint, SonarQube |
| **Python** | Pylint, Flake8, Bandit (security) |
| **C/C++** | Cppcheck, Coverity, PC-lint |
| **C#/.NET** | SonarQube, ReSharper, StyleCop |
| **All languages** | SonarQube (multi-language) |

### 6.2. Ví Dụ: ESLint cho JavaScript

```javascript
// File: paymentService.js

// ❌ ESLint sẽ báo lỗi:
var amount = 100;              // Prefer 'const' or 'let'
if(amount = 100) {             // Assignment instead of comparison
    console.log(password);      // Undefined variable
}

// ✅ Sau khi fix theo ESLint:
const amount = 100;
if (amount === 100) {
    console.log('Amount is 100');
}
```

---

## 7. TỔNG KẾT SO SÁNH

### Static vs Dynamic Testing - Khi Nào Dùng?

```
┌─────────────────────────────────────────────────────────────────┐
│                    KHI NÀO DÙNG STATIC vs DYNAMIC?              │
├─────────────────────────────────────────────────────────────────┤
│                                                                 │
│  📋 DÙNG STATIC TESTING KHI:                                    │
│     ✓ Sớm trong project (requirements, design phase)            │
│     ✓ Kiểm tra documents, specifications                        │
│     ✓ Code review trước khi merge                               │
│     ✓ Tìm security vulnerabilities                              │
│     ✓ Đảm bảo coding standards                                  │
│     ✓ Cải thiện maintainability                                 │
│                                                                 │
│  🖥️ DÙNG DYNAMIC TESTING KHI:                                   │
│     ✓ Kiểm tra functional behavior                              │
│     ✓ Test user workflows end-to-end                            │
│     ✓ Performance testing                                       │
│     ✓ Test runtime behavior                                     │
│     ✓ Integration testing                                       │
│                                                                 │
│  💡 BEST PRACTICE:                                               │
│     → Kết hợp CẢ HAI để đạt hiệu quả tối đa!                   │
│     → Static testing TRƯỚC, Dynamic testing SAU                 │
│                                                                 │
└─────────────────────────────────────────────────────────────────┘
```

---

## 8. CÂU HỎI ÔN TẬP

### Câu 1 (K1)
Điều nào sau đây có thể được kiểm tra bằng static testing?

A. Response time của API
B. Requirements document
C. User interface behavior
D. Memory usage khi chạy application

<details>
<summary>Đáp án</summary>

**B. Requirements document**

Giải thích:
- A, C, D đều cần chạy phần mềm → Dynamic testing
- Requirements document được kiểm tra bằng review (Static testing)
</details>

---

### Câu 2 (K2)
Tại sao static testing có thể phát hiện defects sớm hơn dynamic testing?

A. Vì static testing tools chạy nhanh hơn
B. Vì static testing không cần code được compile
C. Vì static testing có thể áp dụng cho requirements và designs trước khi code xong
D. Vì static testing do machines thực hiện

<details>
<summary>Đáp án</summary>

**C. Vì static testing có thể áp dụng cho requirements và designs trước khi code xong**

Giải thích:
- Static testing review được requirements/designs từ đầu project
- Dynamic testing phải đợi có executable code
</details>

---

### Câu 3 (K2)
Defect nào sau đây CHỈ có thể được tìm bằng static testing?

A. Application crash khi network timeout
B. Mâu thuẫn giữa hai requirements
C. Button không hoạt động khi click
D. Performance chậm khi có nhiều users

<details>
<summary>Đáp án</summary>

**B. Mâu thuẫn giữa hai requirements**

Giải thích:
- A, C, D là runtime behaviors → Dynamic testing
- Mâu thuẫn requirements chỉ phát hiện qua review documents
</details>

---

### Câu 4 (K1)
Công cụ nào sau đây là static analysis tool?

A. Selenium
B. JMeter
C. SonarQube
D. Postman

<details>
<summary>Đáp án</summary>

**C. SonarQube**

Giải thích:
- Selenium: UI automation (Dynamic)
- JMeter: Performance testing (Dynamic)
- SonarQube: Static code analysis
- Postman: API testing (Dynamic)
</details>

---

### Câu 5 (K2)
Lợi ích CHÍNH của static testing là gì?

A. Có thể thay thế hoàn toàn dynamic testing
B. Không cần involvement của testers
C. Phát hiện defects sớm với chi phí sửa thấp
D. Tự động generate test cases

<details>
<summary>Đáp án</summary>

**C. Phát hiện defects sớm với chi phí sửa thấp**

Giải thích:
- A: Sai - Static và Dynamic bổ sung cho nhau
- B: Sai - Testers tham gia reviews
- C: Đúng - Early defect detection = Lower cost
- D: Sai - Static testing không generate test cases
</details>

---

### Câu 6 (K2)
Trong context của e-commerce website, defect nào sau đây được tìm bởi static testing?

A. Checkout process fails khi cart có 100+ items
B. Security vulnerability: SQL injection trong login function
C. Page load time > 5 seconds
D. Payment gateway timeout

<details>
<summary>Đáp án</summary>

**B. Security vulnerability: SQL injection trong login function**

Giải thích:
- A, C, D cần chạy hệ thống mới detect được
- SQL injection được phát hiện bởi static code analysis (SonarQube, etc.)
</details>

---

### Câu 7 (K1)
Work product nào KHÔNG phù hợp cho static testing?

A. Test plan document
B. Application response time
C. Source code
D. User manual

<details>
<summary>Đáp án</summary>

**B. Application response time**

Giải thích:
- Response time là runtime behavior
- Cần dynamic testing (performance testing) để đo
</details>

---

### Câu 8 (K2)
Static testing và dynamic testing có điểm chung gì?

A. Đều cần executable code
B. Đều nhằm mục đích tìm defects
C. Đều sử dụng test automation tools
D. Đều được thực hiện bởi developers

<details>
<summary>Đáp án</summary>

**B. Đều nhằm mục đích tìm defects**

Giải thích:
- A: Sai - Static testing không cần executable
- B: Đúng - Cả hai đều tìm defects
- C: Sai - Static có thể manual (reviews)
- D: Sai - Testers cũng tham gia cả hai
</details>

---

### Câu 9 (K2)
Review requirements document có thể phát hiện defect nào?

A. Runtime error
B. Memory leak
C. Missing acceptance criteria
D. UI không responsive

<details>
<summary>Đáp án</summary>

**C. Missing acceptance criteria**

Giải thích:
- A, B, D là runtime issues → Dynamic testing
- Missing acceptance criteria được tìm khi review requirements
</details>

---

### Câu 10 (K2)
Tại sao nên kết hợp static và dynamic testing?

A. Vì static testing quá tốn thời gian
B. Vì dynamic testing không tìm được defects
C. Vì mỗi loại tìm được các types of defects khác nhau
D. Vì khách hàng yêu cầu

<details>
<summary>Đáp án</summary>

**C. Vì mỗi loại tìm được các types of defects khác nhau**

Giải thích:
- Static: Document defects, coding standards, security issues in code
- Dynamic: Functional failures, performance issues, integration problems
- Kết hợp = Coverage tốt hơn
</details>

---

## 9. CHECKLIST TỰ ĐÁNH GIÁ

Đánh dấu ✅ khi bạn đã hiểu:

- [ ] Định nghĩa được static testing
- [ ] Phân biệt được static testing và dynamic testing
- [ ] Liệt kê được ít nhất 5 work products có thể static test
- [ ] Giải thích được 3 lợi ích chính của static testing
- [ ] Nêu được 3 loại defects mà chỉ static testing mới tìm được
- [ ] Biết được 2 kỹ thuật static testing (Reviews và Static Analysis)
- [ ] Kể tên được ít nhất 2 static analysis tools

---

## TÀI LIỆU THAM KHẢO

- ISTQB CTFL Syllabus v4.0.1 - Chapter 3: Static Testing
- ISTQB Glossary
- SonarQube Documentation

---

**Tiếp theo**: [Module 2.2: Review Process](./module-2.2-review-process.md)

---

**Version**: 1.0.0
**Last Updated**: November 2025
