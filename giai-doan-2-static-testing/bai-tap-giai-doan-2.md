# BÀI TẬP GIAI ĐOẠN 2: STATIC TESTING

**Thời lượng**: 2-3 giờ
**Tiêu chuẩn đạt**: ≥80% (≥16/20 câu hỏi trắc nghiệm)

---

## PHẦN 1: BÀI TẬP THỰC HÀNH (6 bài)

### Bài tập 1: Xác định Static Testing Opportunities

**Scenario**: Bạn là QA Lead trong dự án phát triển app Momo (ví điện tử). Project timeline như sau:

```
Week 1-2:  Requirements gathering và documentation
Week 3-4:  UI/UX Design
Week 5-8:  Development
Week 9-10: Testing
Week 11:   UAT và Release
```

**Yêu cầu**: Xác định các work products có thể được static test ở mỗi phase và loại review phù hợp.

**Điền vào bảng:**

| Phase | Work Product | Static Test Activity | Review Type |
|-------|-------------|---------------------|-------------|
| Week 1-2 | ? | ? | ? |
| Week 3-4 | ? | ? | ? |
| Week 5-8 | ? | ? | ? |
| Week 9-10 | ? | ? | ? |

<details>
<summary>Đáp án mẫu</summary>

| Phase | Work Product | Static Test Activity | Review Type |
|-------|-------------|---------------------|-------------|
| Week 1-2 | Business Requirements Document | Review cho completeness, consistency | Inspection (formal) |
| Week 1-2 | User Stories | Review acceptance criteria | Walkthrough |
| Week 1-2 | Use Cases | Scenario-based review | Technical Review |
| Week 3-4 | UI Mockups | Review với stakeholders | Walkthrough |
| Week 3-4 | API Specifications | Technical review | Technical Review |
| Week 3-4 | Database Design (ERD) | Expert review | Technical Review |
| Week 5-8 | Source Code | Code review + Static analysis | Informal/Technical |
| Week 5-8 | Configuration Files | Security review | Checklist-based |
| Week 9-10 | Test Plan | Peer review | Walkthrough |
| Week 9-10 | Test Cases | Review coverage | Checklist-based |

</details>

---

### Bài tập 2: Chọn Review Type Phù Hợp

**Scenario**: Cho các tình huống sau, chọn loại review phù hợp nhất và giải thích lý do.

| # | Tình huống | Review Type | Lý do |
|---|-----------|-------------|-------|
| 1 | Junior developer vừa viết xong function tính lãi suất, muốn senior check trước khi commit | ? | ? |
| 2 | BA muốn present user stories cho team để mọi người hiểu requirements | ? | ? |
| 3 | Security team cần đánh giá authentication module | ? | ? |
| 4 | Requirements document cho banking system cần được verify trước khi dev | ? | ? |
| 5 | Designer muốn demo UI flow cho checkout feature | ? | ? |

<details>
<summary>Đáp án</summary>

| # | Review Type | Lý do |
|---|-------------|-------|
| 1 | **Informal Review** | Quick feedback từ senior, không cần formal process |
| 2 | **Walkthrough** | Author (BA) leads, mục đích là share knowledge với team |
| 3 | **Technical Review** | Cần security experts đánh giá, focus on technical quality |
| 4 | **Inspection** | Critical document, cần formal process, metrics, và trained reviewers |
| 5 | **Walkthrough** | Designer leads, demo scenarios cho team |

</details>

---

### Bài tập 3: Conduct Mock Review

**Scenario**: Review đoạn requirements sau cho tính năng "Chuyển tiền" của ứng dụng VietQR.

```
REQUIREMENTS DOCUMENT: TRANSFER FEATURE
=======================================

REQ-001: User can transfer money to other bank accounts.

REQ-002: System should process transfers quickly.

REQ-003: Minimum transfer amount is 1,000 VND.

REQ-004: Maximum transfer amount is 500,000,000 VND per transaction.

REQ-005: User must enter correct account number.

REQ-006: Transfer fee is 0.05% of transfer amount.

REQ-007: Maximum transfer limit is 1,000,000,000 VND per day.

REQ-008: User receives notification after transfer.

REQ-009: Transfer history is stored for 6 months.

REQ-010: Maximum transfer per day is 300,000,000 VND.
```

**Yêu cầu**:
1. Identify ít nhất 5 defects trong requirements này
2. Classify mỗi defect: Ambiguity, Inconsistency, Incompleteness, Incorrect
3. Suggest fix cho mỗi defect

<details>
<summary>Đáp án mẫu</summary>

**DEFECT #1**
- Location: REQ-002
- Type: **Ambiguity**
- Description: "Quickly" không định nghĩa rõ
- Suggestion: "System should process transfers within 3 seconds"

**DEFECT #2**
- Location: REQ-004 vs REQ-007 vs REQ-010
- Type: **Inconsistency**
- Description:
  - REQ-004: Max 500M/transaction
  - REQ-007: Max 1B/day
  - REQ-010: Max 300M/day
  - REQ-007 và REQ-010 mâu thuẫn (1B vs 300M per day)
- Suggestion: Confirm với business, keep only one daily limit

**DEFECT #3**
- Location: REQ-005
- Type: **Ambiguity**
- Description: "Correct account number" - không rõ validation rules
- Suggestion: "Account number must be valid (9-14 digits, bank code prefix, checksum validation)"

**DEFECT #4**
- Location: Missing
- Type: **Incompleteness**
- Description: Thiếu requirement về OTP/authentication cho transfers
- Suggestion: Add "REQ-011: OTP verification required for transfers > 10,000,000 VND"

**DEFECT #5**
- Location: REQ-006
- Type: **Incompleteness**
- Description: Không có min/max transfer fee
- Suggestion: "Transfer fee is 0.05%, minimum 5,000 VND, maximum 50,000 VND"

**DEFECT #6**
- Location: REQ-008
- Type: **Ambiguity**
- Description: "Notification" không rõ loại nào (SMS, push, email?)
- Suggestion: "User receives push notification and SMS for transfers > 1,000,000 VND"

**DEFECT #7**
- Location: Missing
- Type: **Incompleteness**
- Description: Thiếu requirement về error handling (insufficient balance, invalid account, etc.)
- Suggestion: Add requirements for all error scenarios

</details>

---

### Bài tập 4: Write Review Checklist

**Yêu cầu**: Tạo checklist cho code review của Payment Module (e-commerce).

Checklist cần cover:
1. Functionality
2. Security
3. Performance
4. Maintainability
5. Error handling

<details>
<summary>Đáp án mẫu</summary>

```
PAYMENT MODULE CODE REVIEW CHECKLIST
====================================

□ FUNCTIONALITY
  □ All requirements implemented correctly?
  □ Business logic matches specifications?
  □ Calculations (tax, discounts) accurate?
  □ Edge cases handled (zero amount, max amount)?
  □ Currency handling correct?

□ SECURITY
  □ No hardcoded credentials/API keys?
  □ Input validation implemented?
  □ SQL injection prevented (parameterized queries)?
  □ XSS vulnerabilities addressed?
  □ Sensitive data encrypted?
  □ PCI-DSS compliance for card data?
  □ Logging doesn't expose sensitive data?

□ PERFORMANCE
  □ Database queries optimized?
  □ No N+1 query problems?
  □ Appropriate indexes used?
  □ Connection pooling implemented?
  □ Caching where appropriate?
  □ Async processing for non-critical operations?

□ MAINTAINABILITY
  □ Code follows team standards/conventions?
  □ Functions have single responsibility?
  □ Magic numbers replaced with constants?
  □ Clear naming (variables, functions)?
  □ Comments for complex logic?
  □ No code duplication?
  □ Cyclomatic complexity reasonable (<10)?

□ ERROR HANDLING
  □ All exceptions handled appropriately?
  □ Meaningful error messages for users?
  □ Detailed logs for debugging?
  □ Graceful degradation?
  □ Transaction rollback on failure?
  □ Timeout handling for external calls?

□ TESTING
  □ Unit tests written?
  □ Edge cases tested?
  □ Test coverage acceptable (>80%)?
  □ Integration tests for payment flow?
```

</details>

---

### Bài tập 5: Static Analysis Findings

**Scenario**: SonarQube analysis của OrderService.java trả về kết quả:

```
╔═══════════════════════════════════════════════════════════════╗
║ FILE: OrderService.java                                       ║
╠═══════════════════════════════════════════════════════════════╣
║ 🔴 CRITICAL (2):                                              ║
║    Line 45: SQL Injection vulnerability                       ║
║    Line 112: Hardcoded password in code                       ║
║                                                               ║
║ 🟠 MAJOR (3):                                                 ║
║    Line 78: Cognitive complexity of 25 (threshold: 15)        ║
║    Line 156: Potential null pointer dereference               ║
║    Line 203: Resource not closed (database connection)        ║
║                                                               ║
║ 🟡 MINOR (4):                                                 ║
║    Line 34: Magic number "86400"                              ║
║    Line 89: Unused variable "temp"                            ║
║    Line 145: Missing Javadoc for public method                ║
║    Line 178: Inconsistent naming convention                   ║
║                                                               ║
║ 📊 Code Coverage: 42% (Target: 80%)                           ║
║ 📊 Duplication: 18% (Threshold: 5%)                           ║
╚═══════════════════════════════════════════════════════════════╝
```

**Yêu cầu**:
1. Prioritize các issues (cái nào fix trước?)
2. Đề xuất cách fix cho mỗi issue
3. Estimate effort (Low/Medium/High)

<details>
<summary>Đáp án mẫu</summary>

**PRIORITY 1: CRITICAL (Fix immediately)**

| Issue | Fix | Effort |
|-------|-----|--------|
| SQL Injection (Line 45) | Use PreparedStatement instead of string concatenation | Medium |
| Hardcoded password (Line 112) | Move to environment variables or secrets manager | Low |

**PRIORITY 2: MAJOR (Fix in current sprint)**

| Issue | Fix | Effort |
|-------|-----|--------|
| High complexity (Line 78) | Refactor into smaller functions | High |
| Null pointer (Line 156) | Add null check or use Optional | Low |
| Resource leak (Line 203) | Use try-with-resources | Low |

**PRIORITY 3: MINOR (Fix when time permits)**

| Issue | Fix | Effort |
|-------|-----|--------|
| Magic number (Line 34) | Create constant: SECONDS_PER_DAY = 86400 | Low |
| Unused variable (Line 89) | Remove variable | Low |
| Missing Javadoc (Line 145) | Add documentation | Low |
| Naming convention (Line 178) | Rename following standards | Low |

**PRIORITY 4: METRICS (Plan improvements)**

| Metric | Current | Target | Action |
|--------|---------|--------|--------|
| Code Coverage | 42% | 80% | Write more unit tests (+38%) |
| Duplication | 18% | <5% | Extract common code to utilities |

</details>

---

### Bài tập 6: Role-Based Review Exercise

**Scenario**: Bạn được assign review User Story sau từ perspective của TESTER:

```
USER STORY: Online Payment
==========================
AS A customer
I WANT TO pay for my order using credit card
SO THAT I can complete my purchase

ACCEPTANCE CRITERIA:
1. User can enter credit card details
2. System validates card number format
3. Payment is processed through payment gateway
4. User receives confirmation email
```

**Yêu cầu**: Từ góc độ Tester, identify issues và đặt questions.

<details>
<summary>Đáp án mẫu</summary>

**ISSUES IDENTIFIED (Tester Perspective):**

**Issue #1: Incomplete Acceptance Criteria**
- Missing: What happens when payment fails?
- Missing: What happens when card is declined?
- Missing: Timeout scenarios?

**Issue #2: Not Testable**
- AC#1: "Enter credit card details" - which fields exactly?
  - Card number, Expiry, CVV, Name on card?
- AC#3: "Processed through gateway" - how to verify success?

**Issue #3: Missing Test Data Info**
- What test card numbers should I use?
- Test environment for payment gateway?

**Issue #4: Missing Non-Functional Requirements**
- Response time for payment processing?
- Security requirements (PCI compliance)?

**QUESTIONS FOR BA/PO:**

1. "What error message should show when card is declined?"
2. "What is the expected response time for payment processing?"
3. "Should we support Save Card for future purchases?"
4. "What currencies are supported?"
5. "Is 3D Secure required?"
6. "What's the retry logic if gateway times out?"
7. "How do I test this - do we have sandbox credentials?"

**SUGGESTED IMPROVED AC:**

```
ACCEPTANCE CRITERIA (Revised):
1. User enters: Card Number (16 digits), Expiry (MM/YY),
   CVV (3-4 digits), Name on Card
2. Real-time validation:
   - Card number: Luhn algorithm check
   - Expiry: Future date
   - CVV: 3 digits (Visa/MC) or 4 digits (Amex)
3. On valid card, payment processed within 5 seconds
4. Success: Confirmation email sent within 1 minute
5. Failure: Clear error message displayed
   - "Card declined - please try another card"
   - "Network error - please try again"
6. 3D Secure authentication for cards requiring it
```

</details>

---

## PHẦN 2: CÂU HỎI TRẮC NGHIỆM (20 câu)

**Thời gian**: 30 phút
**Yêu cầu đạt**: ≥80% (16/20 câu)

---

### Câu 1 (K1)
Static testing là gì?

A. Testing phần mềm bằng cách chạy code
B. Testing phần mềm bằng cách kiểm tra work products mà không chạy code
C. Testing performance của application
D. Testing với automated tools

<details>
<summary>Đáp án</summary>

**B. Testing phần mềm bằng cách kiểm tra work products mà không chạy code**

Giải thích: Static testing = Kiểm tra mà không execute code (đọc, review, analyze documents/code).
</details>

---

### Câu 2 (K2)
Lợi ích chính của static testing so với dynamic testing là gì?

A. Static testing nhanh hơn
B. Static testing tìm được nhiều bugs hơn
C. Static testing có thể phát hiện defects sớm hơn với chi phí sửa thấp hơn
D. Static testing không cần người tham gia

<details>
<summary>Đáp án</summary>

**C. Static testing có thể phát hiện defects sớm hơn với chi phí sửa thấp hơn**

Giải thích: Static testing có thể áp dụng từ requirements phase, khi chi phí fix còn thấp.
</details>

---

### Câu 3 (K1)
Work product nào KHÔNG thể được kiểm tra bằng static testing?

A. Requirements document
B. Source code
C. Application response time
D. Test cases

<details>
<summary>Đáp án</summary>

**C. Application response time**

Giải thích: Response time là runtime behavior, cần dynamic testing (performance testing) để đo.
</details>

---

### Câu 4 (K2)
Loại defect nào CHỈ có thể được tìm bằng static testing?

A. System crash khi submit form
B. Login timeout sau 30 phút
C. Mâu thuẫn giữa hai requirements
D. Button không click được

<details>
<summary>Đáp án</summary>

**C. Mâu thuẫn giữa hai requirements**

Giải thích: Inconsistency trong requirements chỉ phát hiện khi review documents, không thể hiện khi chạy code.
</details>

---

### Câu 5 (K1)
Trong review process, activity nào thực hiện TRƯỚC TIÊN?

A. Individual review
B. Issue communication
C. Planning
D. Fixing

<details>
<summary>Đáp án</summary>

**C. Planning**

Giải thích: Review process: Planning → Initiation → Individual Review → Issue Communication → Fixing & Reporting.
</details>

---

### Câu 6 (K1)
Role nào responsible cho việc FIX defects sau review?

A. Moderator
B. Scribe
C. Author
D. Reviewer

<details>
<summary>Đáp án</summary>

**C. Author**

Giải thích: Author là người tạo work product, nên chịu trách nhiệm fix defects.
</details>

---

### Câu 7 (K2)
Trong walkthrough, ai là người LEAD review?

A. Moderator
B. Manager
C. Author
D. Senior reviewer

<details>
<summary>Đáp án</summary>

**C. Author**

Giải thích: Walkthrough = Author-led review. Author "walks through" work product cho participants.
</details>

---

### Câu 8 (K1)
Loại review nào có formality level CAO NHẤT?

A. Informal review
B. Walkthrough
C. Technical review
D. Inspection

<details>
<summary>Đáp án</summary>

**D. Inspection**

Giải thích: Inspection là most formal với defined process, required roles, và metrics collection.
</details>

---

### Câu 9 (K2)
Khi nào nên sử dụng Technical Review?

A. Khi cần quick feedback
B. Khi cần đánh giá technical quality bởi experts
C. Khi author muốn explain approach
D. Khi không có thời gian cho formal review

<details>
<summary>Đáp án</summary>

**B. Khi cần đánh giá technical quality bởi experts**

Giải thích: Technical Review = Expert-led, focus on technical correctness và quality.
</details>

---

### Câu 10 (K2)
Checklist-based review technique có ưu điểm gì?

A. Không cần preparation
B. Nhanh hơn ad hoc review
C. Đảm bảo consistent coverage
D. Tìm được tất cả defects

<details>
<summary>Đáp án</summary>

**C. Đảm bảo consistent coverage**

Giải thích: Checklist giúp reviewers check systematic, không bỏ sót items, đảm bảo consistency.
</details>

---

### Câu 11 (K2)
Role-based review technique yêu cầu gì?

A. Mỗi reviewer đọc từ perspective của một role (User, Developer, Tester...)
B. Chỉ có managers review
C. Review theo thứ tự roles
D. Mỗi role review một phần document

<details>
<summary>Đáp án</summary>

**A. Mỗi reviewer đọc từ perspective của một role (User, Developer, Tester...)**

Giải thích: Role-based = Perspective-based. Different roles find different types of defects.
</details>

---

### Câu 12 (K1)
SonarQube là loại tool gì?

A. Test automation tool
B. Performance testing tool
C. Static analysis tool
D. Defect tracking tool

<details>
<summary>Đáp án</summary>

**C. Static analysis tool**

Giải thích: SonarQube phân tích code mà không chạy nó, tìm code quality issues, vulnerabilities.
</details>

---

### Câu 13 (K2)
Success factor nào QUAN TRỌNG NHẤT cho reviews?

A. Sử dụng expensive tools
B. Có nhiều reviewers
C. Focus on defects, not people
D. Review meetings dài

<details>
<summary>Đáp án</summary>

**C. Focus on defects, not people**

Giải thích: Constructive atmosphere rất quan trọng. Criticize work product, không criticize author.
</details>

---

### Câu 14 (K2)
Defect nào được tìm bởi static analysis tools?

A. UI không responsive trên mobile
B. SQL injection vulnerability trong code
C. Application crash khi network mất
D. Performance chậm khi có nhiều users

<details>
<summary>Đáp án</summary>

**B. SQL injection vulnerability trong code**

Giải thích: Static analysis tools scan code để tìm security vulnerabilities như SQL injection mà không cần chạy code.
</details>

---

### Câu 15 (K2)
Tại sao nên kết hợp static và dynamic testing?

A. Vì static testing quá đắt
B. Vì dynamic testing không tìm được bugs
C. Vì mỗi loại tìm được các types of defects khác nhau
D. Vì khách hàng yêu cầu

<details>
<summary>Đáp án</summary>

**C. Vì mỗi loại tìm được các types of defects khác nhau**

Giải thích: Static và Dynamic testing complement nhau - together give better coverage.
</details>

---

### Câu 16 (K1)
Activity nào KHÔNG thuộc review process?

A. Planning
B. Individual review
C. Test execution
D. Issue communication

<details>
<summary>Đáp án</summary>

**C. Test execution**

Giải thích: Test execution là dynamic testing, không phải review activity.
</details>

---

### Câu 17 (K2)
Inspection khác với walkthrough ở điểm nào?

A. Inspection có author, walkthrough không có
B. Inspection led by moderator, walkthrough led by author
C. Inspection nhanh hơn walkthrough
D. Walkthrough formal hơn inspection

<details>
<summary>Đáp án</summary>

**B. Inspection led by moderator, walkthrough led by author**

Giải thích:
- Inspection: Moderator leads, formal process
- Walkthrough: Author leads, less formal
</details>

---

### Câu 18 (K2)
Scenario-based review phù hợp nhất cho loại work product nào?

A. Source code
B. Requirements document
C. Test scripts
D. User manual

<details>
<summary>Đáp án</summary>

**B. Requirements document**

Giải thích: Scenario-based review "dry runs" real-world scenarios qua requirements để tìm gaps.
</details>

---

### Câu 19 (K1)
Role nào ghi chép defects trong review meeting?

A. Author
B. Moderator
C. Scribe
D. Review Leader

<details>
<summary>Đáp án</summary>

**C. Scribe**

Giải thích: Scribe (Recorder) responsible cho documenting defects và decisions.
</details>

---

### Câu 20 (K2)
Điều nào KHÔNG phải là lợi ích của static testing?

A. Phát hiện defects sớm
B. Chi phí sửa defects thấp
C. Có thể thay thế hoàn toàn dynamic testing
D. Tìm được defects mà dynamic testing khó tìm

<details>
<summary>Đáp án</summary>

**C. Có thể thay thế hoàn toàn dynamic testing**

Giải thích: Static và Dynamic testing bổ sung cho nhau, không thể thay thế. Mỗi loại có strengths riêng.
</details>

---

## PHẦN 3: ĐÁP ÁN VÀ TÍNH ĐIỂM

### Bảng Đáp Án Trắc Nghiệm

| Câu | Đáp án | Câu | Đáp án |
|-----|--------|-----|--------|
| 1 | B | 11 | A |
| 2 | C | 12 | C |
| 3 | C | 13 | C |
| 4 | C | 14 | B |
| 5 | C | 15 | C |
| 6 | C | 16 | C |
| 7 | C | 17 | B |
| 8 | D | 18 | B |
| 9 | B | 19 | C |
| 10 | C | 20 | C |

### Thang Điểm

| Số câu đúng | Đánh giá | Khuyến nghị |
|-------------|----------|-------------|
| 18-20 | ⭐⭐⭐ Xuất sắc | Sẵn sàng chuyển sang Giai đoạn 3 |
| 16-17 | ⭐⭐ Đạt | Có thể tiến tiếp, review lại các câu sai |
| 14-15 | ⭐ Chưa đạt | Đọc lại Module 2.1 và 2.2 |
| <14 | ❌ Cần ôn lại | Học lại toàn bộ Giai đoạn 2 |

---

## PHẦN 4: CHECKLIST TỰ ĐÁNH GIÁ

Hoàn thành checklist sau trước khi chuyển sang Giai đoạn 3:

### Kiến Thức Cơ Bản
- [ ] Định nghĩa được static testing
- [ ] Phân biệt được static testing và dynamic testing
- [ ] Nêu được ít nhất 3 lợi ích của static testing
- [ ] Liệt kê được 5+ work products có thể static test

### Review Process
- [ ] Nêu được 5 activities trong review process
- [ ] Mô tả vai trò của mỗi role trong review
- [ ] Phân biệt được 4 loại reviews
- [ ] Biết khi nào sử dụng loại review nào

### Review Techniques
- [ ] Giải thích được 4 review techniques
- [ ] Có thể tạo review checklist
- [ ] Có thể conduct mock review

### Static Analysis
- [ ] Hiểu được static analysis tools làm gì
- [ ] Kể tên được 2+ static analysis tools
- [ ] Biết cách interpret static analysis results

### Thực Hành
- [ ] Hoàn thành 6 bài tập thực hành
- [ ] Đạt ≥80% câu hỏi trắc nghiệm (≥16/20)

---

## TỔNG KẾT GIAI ĐOẠN 2

Sau khi hoàn thành Giai đoạn 2, bạn đã học được:

```
✅ STATIC TESTING FUNDAMENTALS
   → Definition và value
   → Static vs Dynamic testing
   → Work products examinable
   → Defects found by static testing

✅ REVIEW PROCESS
   → 5 review activities
   → 6 roles in reviews
   → 4 review types
   → 4 review techniques
   → Success factors

✅ STATIC ANALYSIS
   → Tool-based analysis
   → Types of issues detected
   → Popular tools (SonarQube, ESLint, etc.)

✅ PRACTICAL SKILLS
   → Conduct reviews
   → Write checklists
   → Interpret static analysis results
```

---

**Tiếp theo**: [Giai đoạn 3: Testing trong SDLC](../giai-doan-3-testing-trong-sdlc/module-3.1-sdlc-va-testing.md)

---

**Version**: 1.0.0
**Last Updated**: November 2025
