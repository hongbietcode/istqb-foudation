# MODULE 1.1: TESTING LÀ GÌ?

**Giai đoạn**: 1 - Nền tảng
**Thời lượng học**: 3-4 giờ
**Độ khó**: ⭐ Dễ (Beginner)

---

## MỤC TIÊU HỌC TẬP (Learning Objectives)

Sau khi hoàn thành module này, bạn sẽ có thể:

### FL-1.1.1 (K1) - Identify typical test objectives
**Nhận diện được các mục tiêu điển hình của testing**

### FL-1.1.2 (K2) - Differentiate testing from debugging
**Phân biệt được testing và debugging**

**Business Outcome**: FL-BO1 (Hiểu testing là gì và tại sao có lợi)

---

## 1. TESTING LÀ GÌ? (What is Testing?)

### 1.1. Định nghĩa

**Testing** (Kiểm thử phần mềm) là:

> "Một tập hợp các hoạt động để **lập kế hoạch**, **chuẩn bị** và **đánh giá** các sản phẩm phần mềm và các work products liên quan nhằm xác định rằng chúng đáp ứng các yêu cầu đã nêu, chứng minh rằng chúng phù hợp với mục đích, và phát hiện các defects."

**Giải thích đơn giản**:
Testing là quá trình kiểm tra phần mềm để:
1. Xem nó có hoạt động đúng như mong đợi không
2. Tìm ra lỗi (bugs/defects)
3. Đảm bảo chất lượng trước khi giao cho khách hàng

### 1.2. Ví dụ thực tế

**Ví dụ 1: Testing app Grab**
```
Tình huống: Bạn order Grab từ điểm A đến điểm B

Testing sẽ kiểm tra:
✓ App có tính đúng khoảng cách không?
✓ Giá cước có chính xác không?
✓ Thông báo có đến driver không?
✓ Thanh toán có thành công không?
✓ App có crash khi mất mạng không?
✓ App có chạy mượt trên điện thoại cũ không?
```

**Ví dụ 2: Testing tính năng login website Shopee**
```
Testing sẽ kiểm tra:
✓ Login bằng email/password có thành công không?
✓ Login bằng Facebook/Google có work không?
✓ Nhập sai password 5 lần có bị khóa tài khoản không?
✓ Có hiện thông báo lỗi rõ ràng không?
✓ Thời gian login có dưới 2 giây không?
✓ Mật khẩu có được mã hóa không?
```

### 1.3. Testing KHÔNG chỉ là "tìm lỗi"

Nhiều người nghĩ testing = tìm bugs. Nhưng thực tế, testing còn nhiều việc hơn thế:

| Hoạt động | Mô tả | Ví dụ |
|-----------|-------|-------|
| **Planning** | Lập kế hoạch testing | Quyết định test gì, khi nào, ai test |
| **Analysis** | Phân tích yêu cầu | Đọc requirements để hiểu cần test gì |
| **Design** | Thiết kế test cases | Viết các bước test cụ thể |
| **Implementation** | Chuẩn bị môi trường | Setup test data, test environment |
| **Execution** | Chạy tests | Thực hiện các test cases |
| **Reporting** | Báo cáo kết quả | Viết test report, defect report |

---

## 2. MỤC TIÊU CỦA TESTING (Test Objectives)

### 2.1. Các mục tiêu điển hình

Testing có **7 mục tiêu chính**:

#### 1. Evaluate work products (Đánh giá sản phẩm)
**Mục đích**: Kiểm tra requirements, user stories, designs, code có đáp ứng yêu cầu không.

**Ví dụ**:
- Review requirement document để tìm ambiguity (mơ hồ)
- Review design để đảm bảo feasible (khả thi)
- Review code để tìm logic errors

#### 2. Trigger failures and find defects (Phát hiện lỗi)
**Mục đích**: Làm cho phần mềm lỗi để tìm ra defects.

**Ví dụ**:
- Nhập email không hợp lệ vào form đăng ký
- Upload file 100MB vào hệ thống giới hạn 10MB
- Click button "Submit" 10 lần liên tục (double-click issue)

#### 3. Ensure required coverage (Đảm bảo độ bao phủ)
**Mục đích**: Đảm bảo đã test đủ requirements và code.

**Ví dụ**:
- Test 100% use cases trong spec
- Execute 90% lines of code
- Test tất cả browsers (Chrome, Firefox, Safari, Edge)

#### 4. Reduce risk (Giảm rủi ro)
**Mục đích**: Giảm nguy cơ phần mềm fail khi production.

**Ví dụ**:
- Test thoroughly tính năng payment (vì rủi ro cao)
- Test security để avoid data breach
- Test performance để avoid server crash khi nhiều users

#### 5. Verify requirements (Xác minh yêu cầu)
**Mục đích**: Confirm phần mềm đáp ứng specified requirements.

**Ví dụ**:
- Requirement: "User có thể reset password qua email"
- Test: Verify email reset password có gửi đến không

#### 6. Validate completeness (Xác nhận hoàn thiện)
**Mục đích**: Ensure test object work như stakeholders mong đợi và cần.

**Ví dụ**:
- UAT (User Acceptance Testing): User thật test xem app có đáp ứng nhu cầu công việc không
- Beta testing: Release cho một nhóm users thử nghiệm trước

#### 7. Build confidence (Tạo niềm tin)
**Mục đích**: Tăng confidence về chất lượng của test object.

**Ví dụ**:
- Chạy regression tests → Confirm changes không break existing features
- Performance tests pass → Confident hệ thống handle được traffic cao

### 2.2. Mục tiêu thay đổi theo Context

Mục tiêu của testing **khác nhau** tùy vào:

#### Component Testing (Unit Testing)
**Mục tiêu chính**:
- Find defects
- Verify functions work correctly
- Build confidence in code quality

**Ví dụ**: Test function `calculateDiscount(price, percentage)` với các inputs khác nhau

#### Acceptance Testing
**Mục tiêu chính**:
- Validate system meets business needs
- Build confidence for deployment
- Verify requirements fulfilled

**Ví dụ**: Business users test hệ thống quản lý kho để xem có đáp ứng quy trình thực tế không

#### Performance Testing
**Mục tiêu chính**:
- Verify performance requirements met
- Reduce risk of slow response
- Ensure system handles expected load

**Ví dụ**: Test website có load được trong 2 giây với 1000 concurrent users không

---

## 3. TESTING vs DEBUGGING

### 3.1. Sự khác biệt

| Aspect | **TESTING** | **DEBUGGING** |
|--------|-------------|---------------|
| **Mục đích** | **Tìm defects** | **Fix defects** |
| **Người thực hiện** | **Testers** | **Developers** |
| **Khi nào** | **Trong suốt SDLC** | **Sau khi tìm thấy defect** |
| **Hoạt động** | Execute tests, Compare results | Analyze root cause, Modify code |
| **Kết quả** | Defect reports | Fixed code |
| **Approach** | Destructive (cố làm fail) | Constructive (cố fix) |

### 3.2. Workflow: Testing → Debugging

```
┌─────────────────────────────────────────────────────┐
│                  TESTING PROCESS                    │
└─────────────────────────────────────────────────────┘
                        │
                        ↓
         1. Tester execute test case
                        │
                        ↓
         2. Actual result ≠ Expected result
                        │
                        ↓
         3. Tester log defect report
                        │
                        ↓
┌─────────────────────────────────────────────────────┐
│                 DEBUGGING PROCESS                   │
└─────────────────────────────────────────────────────┘
                        │
                        ↓
         4. Developer analyze defect
                        │
                        ↓
         5. Developer find root cause
                        │
                        ↓
         6. Developer fix code
                        │
                        ↓
         7. Developer run unit tests
                        │
                        ↓
┌─────────────────────────────────────────────────────┐
│             CONFIRMATION TESTING                    │
└─────────────────────────────────────────────────────┘
                        │
                        ↓
         8. Tester verify fix
                        │
                        ↓
         9. PASS → Close defect
            FAIL → Return to step 4
```

### 3.3. Ví dụ thực tế

**Scenario**: Testing tính năng đặt hàng trên Tiki

**TESTING**:
```
Test Case: TC_001 - Đặt hàng thành công

Preconditions:
- User đã login
- Giỏ hàng có 1 sản phẩm

Steps:
1. Click button "Thanh toán"
2. Chọn địa chỉ giao hàng
3. Chọn phương thức thanh toán "COD"
4. Click "Đặt hàng"

Expected Result:
- Hiện thông báo "Đặt hàng thành công"
- Nhận email xác nhận
- Order status = "Đang xử lý"

Actual Result:
- Hiện lỗi "Hệ thống bận, vui lòng thử lại"  ❌
- KHÔNG nhận email
- KHÔNG tạo order mới

Status: FAILED
```

**Tester → Log defect**: "Cannot place order, error message shows 'System busy'"

---

**DEBUGGING** (Developer thực hiện):
```
1. Reproduce lỗi trong dev environment
2. Check logs → Thấy lỗi: "Database connection timeout"
3. Analyze code → Tìm thấy:
   - Connection pool size = 10
   - Current connections = 10 (full!)
4. Root cause: Connection pool quá nhỏ
5. Fix: Tăng connection pool size lên 50
6. Run unit tests → PASS
7. Deploy fix to test environment
```

---

**CONFIRMATION TESTING** (Tester verify):
```
1. Tester chạy lại TC_001
2. Actual Result:
   - Hiện "Đặt hàng thành công" ✓
   - Nhận email xác nhận ✓
   - Order status = "Đang xử lý" ✓

Status: PASSED → Close defect
```

### 3.4. Testing và Debugging bổ trợ nhau

```
Good Testing + Good Debugging = High Quality Software

- Testing: Tìm ra defects càng nhiều càng tốt
- Debugging: Fix defects càng nhanh càng tốt
- Cả hai cùng mục tiêu: Improve software quality
```

---

## 4. VÍ DỤ THỰC TẾ TỪ VIỆT NAM

### 4.1. Case Study: Lỗi app Momo (Giả định)

**Tình huống**: Tháng 12 mùa sale, app Momo bị crash hàng loạt

**Nếu đã testing kỹ**:
```
✓ Load Testing: Simulate 100,000 concurrent users
  → Phát hiện server cannot handle > 50,000 users
  → Upgrade server trước mùa sale

✓ Stress Testing: Push system beyond limits
  → Phát hiện database slow queries
  → Optimize queries trước release

✓ Spike Testing: Sudden traffic surge (12h trưa)
  → Phát hiện auto-scaling không kịp
  → Configure better auto-scaling rules
```

**Kết quả**: App chạy smooth ngay cả khi triệu users truy cập

### 4.2. Case Study: Lỗi thanh toán Shopee (Giả định)

**Tình huống**: User complain thanh toán bị trừ tiền 2 lần

**Nếu đã testing kỹ**:
```
✓ Functional Testing: Test double-click button "Thanh toán"
  → Phát hiện không có debounce mechanism
  → Add debounce 3 seconds

✓ Integration Testing: Test payment gateway integration
  → Phát hiện không có idempotency check
  → Add transaction ID validation

✓ Error Guessing: Tester thử các scenarios bất thường
  → Phát hiện lỗi khi network lag
  → Add proper timeout handling
```

**Kết quả**: Không còn trường hợp charge twice

---

## 5. COMMON MISCONCEPTIONS (Hiểu lầm phổ biến)

### Hiểu lầm #1: "Testing là công việc đơn giản"
**Sự thật**: Testing đòi hỏi:
- Analytical thinking (tư duy phân tích)
- Attention to detail (chú ý chi tiết)
- Communication skills (kỹ năng giao tiếp)
- Technical knowledge (kiến thức kỹ thuật)
- Domain knowledge (hiểu biết về nghiệp vụ)

### Hiểu lầm #2: "Testing chỉ là click click"
**Sự thật**: Testing bao gồm:
- Đọc và phân tích requirements
- Thiết kế test cases (cần suy nghĩ)
- Lập kế hoạch testing
- Quản lý risks
- Automation testing (cần code)
- Performance testing (cần hiểu architecture)

### Hiểu lầm #3: "Chỉ test khi code xong"
**Sự thật**: Testing bắt đầu từ đầu:
- Review requirements → Tìm ambiguity
- Review designs → Tìm logical flaws
- Test during development → Unit testing
- Test sau release → Maintenance testing

### Hiểu lầm #4: "Testing có thể đảm bảo software 100% bug-free"
**Sự thật**:
- Testing có thể chứng minh **có** bugs, không thể chứng minh **không có** bugs
- Testing giảm risk, không loại bỏ hoàn toàn risk
- "Testing shows the presence of defects, not their absence" (Testing Principle #1)

### Hiểu lầm #5: "Tester và Developer là enemies"
**Sự thật**:
- Tester và Developer cùng mục tiêu: Quality software
- Tester tìm defects để protect end users
- Developer fix defects để improve product
- Cần collaboration, not confrontation

---

## 6. TẠI SAO TESTING QUAN TRỌNG?

### 6.1. Consequences của Poor Testing

**Ví dụ ngoài đời thực** (quốc tế):

#### Case 1: Therac-25 (1985-1987)
- **Sản phẩm**: Medical radiation therapy machine
- **Lỗi**: Software bug dẫn đến overdose radiation
- **Hậu quả**: 3 người chết, nhiều người bị thương nghiêm trọng
- **Nguyên nhân**: Insufficient testing, poor error handling

#### Case 2: Knight Capital Group (2012)
- **Sản phẩm**: Trading software
- **Lỗi**: Deployment bug (software cũ và mới conflict)
- **Hậu quả**: Mất $440 triệu USD trong 45 phút
- **Nguyên nhân**: Inadequate testing, poor deployment process

#### Case 3: Boeing 737 MAX (2018-2019)
- **Sản phẩm**: Flight control system
- **Lỗi**: MCAS system malfunction
- **Hậu quả**: 2 vụ tai nạn, 346 người chết
- **Nguyên nhân**: Insufficient testing, inadequate training

### 6.2. Cost of Bugs

**Cost tăng theo thời gian phát hiện**:

```
Requirements Phase:    $1
Design Phase:         $5
Coding Phase:        $10
Testing Phase:       $50
Production:        $100+

→ Sớm tìm ra bug, CHI PHÍ thấp hơn!
```

**Ví dụ**:
- Bug tìm thấy khi review requirement: Sửa trong 5 phút (edit doc)
- Bug tìm thấy khi production: Cần hotfix, rollback, customer support, reputation damage

---

## 7. KEY TAKEAWAYS (Điểm chính cần nhớ)

### 7 điểm quan trọng nhất:

1. **Testing ≠ Chỉ tìm bugs**
   - Testing là quá trình toàn diện: Planning → Execution → Reporting

2. **Testing có nhiều mục tiêu**
   - Find defects, Reduce risk, Verify requirements, Build confidence, etc.

3. **Testing ≠ Debugging**
   - Testing: Testers tìm defects
   - Debugging: Developers fix defects

4. **Testing bắt đầu sớm**
   - Review requirements, Review designs
   - Không chờ đến khi có code

5. **Testing không thể chứng minh "no bugs"**
   - Chỉ có thể chứng minh "có bugs"
   - Giảm risk, không loại bỏ hoàn toàn

6. **Test objectives phụ thuộc context**
   - Component testing: Find defects
   - Acceptance testing: Validate business needs
   - Performance testing: Verify performance

7. **Good testing saves money**
   - Tìm bugs sớm → Chi phí fix thấp
   - Prevent production issues → Avoid reputation damage

---

## 8. SELF-ASSESSMENT CHECKLIST

Đánh dấu ✓ nếu bạn có thể làm được:

- [ ] Tôi có thể giải thích testing là gì cho người không biết IT
- [ ] Tôi có thể liệt kê ít nhất 5 mục tiêu của testing
- [ ] Tôi có thể phân biệt testing và debugging
- [ ] Tôi có thể cho ví dụ về test objectives trong context khác nhau
- [ ] Tôi hiểu tại sao testing quan trọng
- [ ] Tôi hiểu testing không thể đảm bảo 100% bug-free
- [ ] Tôi có thể giải thích tại sao nên test sớm

**Nếu đánh dấu được ≥6/7** → Bạn đã nắm vững module này!

---

## 9. PRACTICE QUESTIONS (Câu hỏi thực hành)

### Question 1 (K1)
Which of the following is a typical test objective?

A. Ensuring all code is executed
B. Finding as many failures as possible so that defects are identified and fixed
C. Ensuring that all identified defects are fixed
D. Preventing the occurrence of defects through development

**Đáp án**: B
**Giải thích**:
- A: Sai - Code coverage là metric, không phải objective
- B: **Đúng** - Tìm failures để identify defects là typical objective
- C: Sai - Fixing defects là responsibility của developers, không phải testers
- D: Sai - Prevention là QA activity, testing là detection

---

### Question 2 (K2)
Which of the following statements correctly describes the difference between testing and debugging?

A. Testing identifies defects, debugging analyzes and removes the causes of failures
B. Testing removes faults, debugging identifies defects
C. Testing prevents defects, debugging removes defects
D. Testing is performed by developers, debugging by testers

**Đáp án**: A
**Giải thích**:
- A: **Đúng** - Testing tìm defects (by testers), debugging analyze and fix (by developers)
- B: Sai - Ngược lại
- C: Sai - Testing detect defects, không prevent
- D: Sai - Ngược lại

---

### Question 3 (K2)
Which test objectives are typically more important in acceptance testing than in component testing?

A. Finding defects
B. Verifying that requirements are fulfilled
C. Building confidence in the quality of the component
D. Gaining confidence that the system will work in the production environment

**Đáp án**: D
**Giải thích**:
- Acceptance testing focus on validating system meets business needs and ready for production
- Component testing focus on finding defects in individual components

---

### Question 4 (K1)
Which of the following is NOT a typical test objective?

A. To find defects and failures
B. To prevent defects
C. To build confidence in the level of quality
D. To provide information for debugging activities

**Đáp án**: B
**Giải thích**: Prevention of defects là part của Quality Assurance (QA), không phải testing objectives

---

### Question 5 (K2)
During which phase is it MOST cost-effective to find and fix defects?

A. Requirements phase
B. Design phase
C. Coding phase
D. Production phase

**Đáp án**: A
**Giải thích**: Càng sớm tìm defects, cost càng thấp. Requirements phase là earliest phase.

---

## 10. THUẬT NGỮ QUAN TRỌNG (Key Terms)

| English | Tiếng Việt | Định nghĩa ngắn |
|---------|------------|-----------------|
| **Testing** | Kiểm thử | Process để đánh giá quality và find defects |
| **Test Objective** | Mục tiêu kiểm thử | Reason/purpose để conduct testing |
| **Debugging** | Gỡ lỗi | Activity để find, analyze và remove defects |
| **Defect** | Khuyết tật, lỗi | Flaw trong work product |
| **Failure** | Hỏng hóc | Deviation từ expected behavior |
| **Quality** | Chất lượng | Degree product meets requirements |
| **Verification** | Kiểm chứng | Confirm product built RIGHT |
| **Validation** | Xác nhận | Confirm built the RIGHT product |

---

## NEXT STEPS

Bạn đã hoàn thành Module 1.1! 🎉

**Tiếp theo**:
- 📚 [Module 1.2: Cơ bản về Testing](module-1.2-co-ban-ve-testing.md) - Tìm hiểu về Errors, Defects, Failures và 7 Testing Principles
- 💪 Làm [Bài tập Giai đoạn 1](bai-tap-giai-doan-1.md) (sau khi học xong cả 4 modules)

**Ôn tập**:
- Review 7 test objectives
- Review differences giữa Testing và Debugging
- Làm lại 5 practice questions

---

**Thời gian học đề xuất**: 3-4 giờ
**Thời gian ôn lại**: 30 phút (sau 2-3 ngày)

*Hẹn gặp bạn ở Module 1.2!*
