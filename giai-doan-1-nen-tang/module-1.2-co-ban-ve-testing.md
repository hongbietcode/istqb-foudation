# MODULE 1.2: Cơ BẢN VỀ TESTING

**Giai đoạn**: 1 - Nền tảng
**Thời lượng học**: 4-5 giờ
**Độ khó**: ⭐⭐ Trung bình

---

## MỤC TIÊU HỌC TẬP (Learning Objectives)

Sau khi hoàn thành module này, bạn sẽ có thể:

### FL-1.2.1 (K2) - Distinguish errors, defects, and failures
**Phân biệt được errors, defects và failures**

### FL-1.2.2 (K2) - Distinguish root cause of defects from effects
**Phân biệt được nguyên nhân gốc rễ của defects và tác động của chúng**

### FL-1.2.3 (K2) - Explain how testing contributes to success
**Giải thích được testing đóng góp vào thành công như thế nào**

### FL-1.2.4 (K2) - Explain relationship between testing and QA
**Giải thích được mối quan hệ giữa testing và QA**

**Business Outcomes**: FL-BO1, FL-BO2

---

## 1. ERRORS, DEFECTS VÀ FAILURES

### 1.1. Ba khái niệm cơ bản

#### Error (Lỗi sai, Sai sót)
**Định nghĩa**: Hành động của con người tạo ra kết quả không đúng.

**Ví dụ**:
- Developer **viết nhầm** công thức: `total = price - discount` (đúng là `price * (1 - discount/100)`)
- BA **hiểu nhầm** requirement và viết spec sai
- Designer **thiết kế nhầm** user flow

**Nguyên nhân**:
- Thiếu kiến thức
- Áp lực thời gian
- Miscommunication
- Fatigue (mệt mỏi)
- Complexity của hệ thống

---

#### Defect (Khuyết tật, Bug, Fault)
**Định nghĩa**: Imperfection trong work product (code, document, design) do error gây ra.

**Ví dụ**:
```javascript
// DEFECT trong code
function calculateDiscount(price, percentage) {
  return price - percentage;  // ❌ DEFECT: Sai công thức
  // Đúng phải là: price * (percentage / 100)
}
```

```sql
-- DEFECT trong database query
SELECT * FROM orders WHERE user_id = 123 OR 1=1;
-- ❌ DEFECT: SQL injection vulnerability
```

**Đồng nghĩa**: Bug, Fault, Issue, Problem

---

#### Failure (Hỏng hóc, Lỗi phát sinh)
**Định nghĩa**: Sự kiện test object không thực hiện đúng function như yêu cầu, do defect được execute.

**Ví dụ**:
```
User Story: "Áp dụng mã giảm giá 20% cho đơn hàng 1,000,000đ"

Expected: 1,000,000 - 200,000 = 800,000đ
Actual:   1,000,000 - 20       = 999,980đ  ❌ FAILURE!
```

**Hậu quả**:
- User không thể hoàn thành task
- Sản phẩm không đáp ứng requirements
- Loss of trust, revenue, reputation

---

### 1.2. Mối quan hệ: Error → Defect → Failure

```
┌─────────────────────────────────────────────────────────────┐
│                        FLOW CHART                           │
└─────────────────────────────────────────────────────────────┘

   ERROR (Sai sót)
   Developer viết sai công thức
          │
          ↓
   DEFECT (Bug trong code)
   Công thức tính giảm giá sai
          │
          ↓
   Code được EXECUTE
          │
          ↓
   FAILURE (Hỏng hóc)
   User thấy giá sai trên màn hình
```

**Ví dụ thực tế**:

```
1. ERROR (Human mistake)
   └─ Developer nghĩ 20% discount = trừ đi 20

2. DEFECT (Flaw in code)
   └─ Code: return price - percentage;

3. EXECUTION
   └─ User apply mã giảm 20% cho đơn 1tr

4. FAILURE (Incorrect behavior)
   └─ Giá hiện: 999,980đ thay vì 800,000đ
   └─ User complain!
```

---

### 1.3. Quan trọng: Không phải Defect nào cũng gây Failure

#### Case 1: Defect nhưng không Failure (Dead code)
```javascript
function processOrder(order) {
  // ... main logic ...

  // DEFECT: Code này sai nhưng không bao giờ chạy
  if (false) {  // Dead code
    let x = 10 / 0;  // ❌ DEFECT nhưng không gây FAILURE
  }

  return order;
}
```

#### Case 2: Defect nhưng Failure chỉ xảy ra trong điều kiện đặc biệt
```javascript
function divide(a, b) {
  return a / b;  // ❌ DEFECT: Không check b = 0
}

divide(10, 2);  // ✓ OK: No failure
divide(10, 0);  // ❌ FAILURE: NaN or Infinity
```

#### Case 3: Failure không do Defect (Environmental issues)
```
FAILURE: Website chậm, timeout
NGUYÊN NHÂN: Server hết RAM (không phải do code bug)
```

---

### 1.4. Ví dụ chi tiết: App Grab

**Scenario**: Tính tiền cước Grab

```
┌─────────────────────────────────────────────────────────────┐
│ STEP 1: ERROR (Human mistake)                               │
└─────────────────────────────────────────────────────────────┘

Developer A hiểu nhầm requirement:
- Requirement: "Phí = 10,000đ/km + 5,000đ phí khởi hành"
- Developer nghĩ: "Phí = 10,000đ × km + 5,000đ"
- Developer viết: "Phí = 15,000đ × km" (SKIP phí khởi hành)

┌─────────────────────────────────────────────────────────────┐
│ STEP 2: DEFECT (Bug in code)                                │
└─────────────────────────────────────────────────────────────┘

Code bị sai:
```javascript
function calculateFare(distance) {
  const BASE_FARE = 5000;
  const PER_KM = 10000;

  // ❌ DEFECT: Missing BASE_FARE
  return PER_KM * distance;

  // ✓ Correct: return BASE_FARE + (PER_KM * distance);
}
```

┌─────────────────────────────────────────────────────────────┐
│ STEP 3: EXECUTION                                            │
└─────────────────────────────────────────────────────────────┘

User đặt Grab đi 3km:

```javascript
calculateFare(3);  // Returns 30,000đ
```

┌─────────────────────────────────────────────────────────────┐
│ STEP 4: FAILURE (Incorrect result)                          │
└─────────────────────────────────────────────────────────────┘

Expected: 5,000 + (10,000 × 3) = 35,000đ
Actual:   10,000 × 3           = 30,000đ  ❌ FAILURE

User thấy giá: 30,000đ (rẻ hơn 5,000đ)
→ Grab bị lỗ tiền!
```

---

## 2. ROOT CAUSE ANALYSIS (Phân tích nguyên nhân gốc rễ)

### 2.1. Root Cause là gì?

**Định nghĩa**: Nguyên nhân cơ bản nhất dẫn đến defect. Fix root cause sẽ prevent similar defects trong tương lai.

### 2.2. 5 Whys Technique

**Kỹ thuật**: Hỏi "Tại sao?" 5 lần để tìm root cause.

**Ví dụ**: App Momo bị crash khi thanh toán

```
Failure: App crash khi user click "Thanh toán"

Why #1: Tại sao crash?
└─ Vì NullPointerException ở PaymentService

Why #2: Tại sao NullPointerException?
└─ Vì biến 'user.address' là null

Why #3: Tại sao user.address null?
└─ Vì code không check user có address chưa

Why #4: Tại sao code không check?
└─ Vì developer không biết address có thể null

Why #5: Tại sao developer không biết?
└─ Vì requirement không specify rõ điều này

ROOT CAUSE: Requirement không đầy đủ
```

**Giải pháp**:
- **Immediate fix**: Add null check trong code
- **Long-term fix**: Improve requirement review process

---

### 2.3. Phân biệt Root Cause và Effect

| Aspect | Root Cause (Nguyên nhân gốc) | Effect (Tác động) |
|--------|------------------------------|-------------------|
| **Là gì** | Nguyên nhân cơ bản nhất | Hậu quả của defect |
| **Ví dụ** | Requirement không rõ ràng | App crash |
| **Fix** | Improve requirement process | Add null check |
| **Prevent** | Ngăn defects tương tự | Chỉ fix symptom |

**Ví dụ thực tế**:

```
┌─────────────────────────────────────────────────────────────┐
│ Symptom (Effect): Website bị hack, data leak                │
└─────────────────────────────────────────────────────────────┘
        ↑
        │
┌─────────────────────────────────────────────────────────────┐
│ Immediate Cause: SQL Injection vulnerability                │
└─────────────────────────────────────────────────────────────┘
        ↑
        │
┌─────────────────────────────────────────────────────────────┐
│ Root Cause: No security training for developers             │
└─────────────────────────────────────────────────────────────┘

Quick Fix: Patch SQL injection
Root Fix: Implement security training + code review process
```

---

## 3. TESTING ĐÓ GÓP VÀO THÀNH CÔNG NHƯ THẾ NÀO?

### 3.1. Các đóng góp chính của Testing

#### 1. Find Defects Early (Tìm lỗi sớm)
**Giá trị**: Giảm chi phí fix bugs

```
Cost to fix bug:
- Requirements phase:   $1      (Edit document)
- Design phase:         $5      (Update design)
- Coding phase:        $10      (Change code)
- Testing phase:       $50      (Fix + Regression test)
- Production:         $100+     (Hotfix + Customer support)

→ Sớm tìm bug = Tiết kiệm tiền!
```

**Ví dụ**:
- Review requirement → Tìm ambiguity → Clarify ngay → Cost: 30 phút
- Bug found in production → Emergency meeting → Hotfix → Customer complaints → Cost: 2 ngày + reputation damage

---

#### 2. Reduce Risk of Failures (Giảm rủi ro)
**Giá trị**: Avoid production incidents

**Ví dụ**: Testing e-commerce checkout
```
Without Testing:
- Bug: Double charge khách hàng
- Result: Customer complaints, refunds, bad reviews
- Cost: Lost revenue + reputation damage

With Testing:
- Test: Verify no double charge
- Find bug: Before production
- Fix: Before any customer affected
- Result: No incidents, happy customers
```

---

#### 3. Verify Requirements Met (Kiểm chứng yêu cầu)
**Giá trị**: Ensure product meets stakeholder needs

**Ví dụ**: Banking app security requirement
```
Requirement: "App phải logout sau 5 phút idle"

Testing verify:
✓ Idle 4:59 → App vẫn active
✓ Idle 5:00 → App auto logout
✓ After logout → Require re-login
✓ Session cleared → No data leak

→ Requirement MET!
```

---

#### 4. Build Confidence (Tạo niềm tin)
**Giá trị**: Stakeholders có confidence để release

```
Before Testing: "Code xong rồi, nhưng không biết có bug không?"
After Testing:  "Đã test 500 test cases, 95% pass, 5% minor bugs đã fix"

→ Team confident để release!
```

---

#### 5. Provide Information (Cung cấp thông tin)
**Giá trị**: Support decision making

**Ví dụ**: Test report cho stakeholders
```
Test Metrics:
- Test cases executed: 500
- Pass: 475 (95%)
- Fail: 25 (5%)
  ├─ Critical: 0
  ├─ Major: 2 (being fixed)
  └─ Minor: 23 (can defer)

Quality Assessment: GOOD - Ready for release
```

---

#### 6. Comply with Standards (Tuân thủ chuẩn)
**Giá trị**: Meet regulatory requirements

**Ví dụ**: Medical device software
```
Standard ISO 13485 requires:
✓ Test plan documented
✓ Test cases traceability to requirements
✓ Test results recorded
✓ Defects tracked and resolved

→ Testing provides compliance evidence
```

---

### 3.2. Testing Success Stories (Việt Nam)

#### Case Study 1: VNPay
**Context**: Upgrade payment gateway

**Testing contribution**:
```
✓ Load Testing: Simulate 50,000 transactions/hour
  → Found bottleneck in database
  → Optimized queries before go-live

✓ Security Testing: Penetration testing
  → Found 3 critical vulnerabilities
  → Fixed before hackers could exploit

✓ Integration Testing: Test with 20+ banks
  → Found API incompatibility with 2 banks
  → Resolved before launch

Result: Smooth launch, zero downtime, no security breach
```

#### Case Study 2: Shopee
**Context**: Mùa sale 9.9

**Testing contribution**:
```
✓ Performance Testing: 2 triệu concurrent users
  → Server config adjusted
  → Auto-scaling configured

✓ Stress Testing: Push to breaking point
  → Found memory leak
  → Fixed before sale event

Result: Handled 5 triệu orders, app stable
```

---

## 4. TESTING VÀ QUALITY ASSURANCE (QA)

### 4.1. Phân biệt Testing và QA

| Aspect | **Testing (QC)** | **Quality Assurance (QA)** |
|--------|------------------|----------------------------|
| **Focus** | **Product** | **Process** |
| **Goal** | Tìm defects trong product | Prevent defects bằng good process |
| **When** | Sau khi có product | Xuyên suốt project |
| **Activities** | Execute tests, Find bugs | Define standards, Process improvement |
| **Approach** | **Detective** (phát hiện) | **Preventive** (phòng ngừa) |
| **Responsibility** | Testers | Whole team |

### 4.2. Ví dụ minh họa

#### Testing (QC) Activities:
```
✓ Execute test cases
✓ Compare actual vs expected results
✓ Log defects
✓ Verify bug fixes
✓ Measure test coverage
✓ Report quality status
```

#### QA Activities:
```
✓ Define coding standards
✓ Establish review process
✓ Implement CI/CD pipeline
✓ Conduct training
✓ Process improvement (retrospectives)
✓ Audit compliance
```

### 4.3. QA và Testing bổ trợ nhau

```
Good QA Process + Good Testing = High Quality Product

QA (Prevent):
├─ Define standards
├─ Code review process
├─ Automated CI/CD
└─ Team training
        ↓
    Fewer defects created
        ↓
Testing (Detect):
├─ Find remaining defects
├─ Verify quality
├─ Provide metrics
└─ Build confidence
        ↓
    High quality release
```

**Ví dụ thực tế**:

```
PROJECT: Develop mobile banking app

QA Activities (Prevent defects):
✓ Week 1: Define security coding standards
✓ Week 2: Setup code review checklist
✓ Week 3: Configure automated security scan
✓ Ongoing: Daily code reviews

→ Result: Fewer security bugs created

Testing Activities (Find defects):
✓ Week 4: Security testing
✓ Week 5: Penetration testing
✓ Week 6: Vulnerability scan

→ Result: Find and fix remaining security issues

COMBINED RESULT: Secure app ready for production
```

---

## 5. ISTQB 7 TESTING PRINCIPLES

### Principle 1: Testing shows presence of defects, not their absence
**"Kiểm thử chứng minh CÓ lỗi, không chứng minh KHÔNG CÓ lỗi"**

**Giải thích**:
- Testing có thể tìm ra defects
- Nhưng không thể chứng minh software hoàn toàn bug-free
- Ngay cả khi pass all tests, vẫn có thể có hidden bugs

**Ví dụ**:
```
Test 1000 scenarios → All PASS
→ Không có nghĩa là scenario 1001 sẽ PASS
→ Vẫn có thể có bugs chưa được test
```

**Thực tế**: Phần mềm phức tạp có vô số combinations, không thể test hết.

---

### Principle 2: Exhaustive testing is impossible
**"Kiểm thử toàn diện là không thể"**

**Giải thích**:
- Không thể test tất cả combinations của inputs, preconditions, postconditions
- Phải prioritize testing dựa trên risk và importance

**Ví dụ**:
```
Form đăng ký có 10 fields:
- Mỗi field có trung bình 5 test cases
- Total combinations: 5^10 = 9,765,625 test cases!

→ Không thể test hết → Phải prioritize
```

**Giải pháp**:
- Risk-based testing: Test high-risk areas nhiều hơn
- Test design techniques: EP, BVA để reduce test cases

---

### Principle 3: Early testing saves time and money
**"Kiểm thử sớm tiết kiệm thời gian và tiền bạc"**

**Giải thích**:
- Static testing (reviews) bắt đầu sớm trong SDLC
- Dynamic testing bắt đầu sớm nhất có thể
- Defects found early = Cheaper to fix

**Ví dụ**:
```
Bug trong requirement (Week 1):
- Find: 30 minutes review
- Fix: 15 minutes update document
- Cost: 1 hour

Same bug found in production (Week 20):
- Find: User complaint
- Analyze: 2 hours
- Fix: 4 hours code change
- Test: 4 hours regression
- Deploy: 2 hours hotfix
- Support: 3 hours customer service
- Cost: 15+ hours + reputation damage
```

**Shift Left**: Di chuyển testing sang trái (sớm hơn) trong timeline.

---

### Principle 4: Defects cluster together
**"Lỗi thường tập trung lại với nhau"**

**Giải thích**:
- Một số modules có nhiều defects hơn các modules khác
- Thường theo Pareto Principle: 80% defects nằm trong 20% modules

**Ví dụ**:
```
E-commerce website modules:
- Product catalog:    5 bugs (10%)
- Shopping cart:      8 bugs (16%)
- Payment processing: 35 bugs (70%)  ← CLUSTER!
- User profile:       2 bugs (4%)

→ Focus testing on Payment module
```

**Tại sao?**:
- Module phức tạp hơn
- Nhiều dependencies
- Code mới hoặc code được modify nhiều
- Developer ít kinh nghiệm

**Hành động**: Prioritize testing cho high-defect areas.

---

### Principle 5: Tests wear out (Pesticide Paradox)
**"Tests cũng sẽ mòn (Nghịch lý thuốc trừ sâu)"**

**Giải thích**:
- Chạy đi chạy lại same tests → Không tìm được defects mới
- Giống thuốc trừ sâu: Dùng lâu → Sâu kháng thuốc
- Phải regularly review và update tests

**Ví dụ**:
```
Regression test suite ban đầu: 100 tests
- Month 1: Found 20 new bugs
- Month 2: Found 5 new bugs
- Month 3: Found 1 new bug
- Month 4: Found 0 bugs  ← Tests wear out!

Action: Add new test cases for new features/scenarios
```

**Giải pháp**:
- Add tests cho new functionalities
- Update tests khi requirements change
- Use exploratory testing để find new bugs

---

### Principle 6: Testing is context dependent
**"Kiểm thử phụ thuộc vào ngữ cảnh"**

**Giải thích**:
- Different types of systems = Different testing approaches
- Safety-critical system ≠ E-commerce website

**Ví dụ**:

```
┌─────────────────────────────────────────────────────────────┐
│ Medical Device Software (Life-critical)                     │
└─────────────────────────────────────────────────────────────┘
✓ 100% code coverage required
✓ Formal verification
✓ Extensive documentation
✓ Regulatory compliance testing
✓ Zero tolerance for critical bugs

┌─────────────────────────────────────────────────────────────┐
│ Mobile Game (Entertainment)                                 │
└─────────────────────────────────────────────────────────────┘
✓ Focus on UX and performance
✓ Exploratory testing
✓ Beta testing with real users
✓ Minor bugs acceptable if not game-breaking
```

**Agile vs Waterfall**:
- Agile: Continuous testing, short iterations
- Waterfall: Testing phase sau coding phase

---

### Principle 7: Absence-of-defects fallacy
**"Ngụy biện không có lỗi"**

**Giải thích**:
- Phần mềm không có bugs ≠ Phần mềm tốt
- Nếu software không đáp ứng user needs → Vẫn thất bại

**Ví dụ**:
```
Scenario: E-wallet app perfect, zero bugs

BUT:
- User muốn: Chuyển tiền đơn giản trong 3 clicks
- App requires: 10 clicks + OTP + confirmation email

→ Perfect but USELESS!
→ Product fails despite zero bugs
```

**Lesson**: Testing phải verify cả:
1. **Verification**: Building product RIGHT (no bugs)
2. **Validation**: Building the RIGHT product (meets user needs)

---

## 6. TÓM TẮT 7 PRINCIPLES

| # | Principle | Ý nghĩa | Hành động |
|---|-----------|---------|-----------|
| 1 | Shows presence, not absence | Không thể chứng minh bug-free | Accept risk, test smart |
| 2 | Exhaustive testing impossible | Không test hết được | Prioritize by risk |
| 3 | Early testing saves money | Test sớm = Rẻ hơn | Shift Left, Reviews |
| 4 | Defects cluster | Bugs tập trung | Focus high-risk areas |
| 5 | Pesticide paradox | Tests mòn | Update tests regularly |
| 6 | Context dependent | Context khác nhau | Tailor approach |
| 7 | Absence-of-defects fallacy | Zero bugs ≠ Success | Validate user needs |

---

## 7. PRACTICE QUESTIONS

### Question 1 (K2)
Which of the following BEST describes the relationship between errors, defects and failures?

A. Errors lead to defects, which may lead to failures
B. Defects lead to errors, which may lead to failures
C. Failures lead to defects, which may lead to errors
D. Errors lead to failures, which may lead to defects

**Đáp án**: A
**Giải thích**: Error (human mistake) → Defect (in code) → Failure (when executed)

---

### Question 2 (K2)
Which testing principle states that the same tests repeated over and over again tend to find no new defects?

A. Testing shows presence of defects
B. Exhaustive testing is impossible
C. Defects cluster together
D. Pesticide paradox

**Đáp án**: D
**Giải thích**: Pesticide paradox = Tests wear out, need to update regularly

---

### Question 3 (K2)
How does testing contribute to higher quality?

A. By ensuring all defects are found and fixed
B. By providing information about defects to enable improvements
C. By preventing all defects through process improvements
D. By verifying that the system works correctly

**Đáp án**: B
**Giải thích**: Testing provides information → Enable improvements. A is impossible, C is QA, D is partial.

---

### Question 4 (K2)
What is the difference between Quality Assurance (QA) and Quality Control (QC)?

A. QA is concerned with proper testing process, QC is concerned with testing the product
B. QA is testing the product, QC is concerned with proper testing process
C. QA is performed by developers, QC is performed by testers
D. QA is for functional testing, QC is for non-functional testing

**Đáp án**: A
**Giải thích**: QA = Process-focused (proper process), QC/Testing = Product-focused (test product)

---

### Question 5 (K2)
Why is it impossible to achieve 100% testing coverage?

A. Because testing is too expensive
B. Because there are too many combinations of inputs and preconditions to test
C. Because testers don't have enough time
D. Because not all defects can be found

**Đáp án**: B
**Giải thích**: Exhaustive testing is impossible due to infinite combinations (Principle #2)

---

## 8. SELF-ASSESSMENT CHECKLIST

Đánh dấu ✓ nếu bạn có thể:

- [ ] Giải thích sự khác biệt giữa Error, Defect và Failure
- [ ] Vẽ được flow: Error → Defect → Failure
- [ ] Cho ví dụ về Root Cause Analysis
- [ ] Liệt kê 5 cách testing đóng góp vào success
- [ ] Phân biệt Testing (QC) và Quality Assurance (QA)
- [ ] Nhớ và giải thích được 7 Testing Principles
- [ ] Áp dụng 7 Principles vào ví dụ thực tế

**Đạt ≥6/7** → Bạn đã nắm vững module này!

---

## 9. KEY TAKEAWAYS

1. **Error → Defect → Failure**: Hiểu rõ flow và phân biệt 3 khái niệm
2. **Root Cause Analysis**: Tìm nguyên nhân gốc rễ, không chỉ fix symptom
3. **Testing đóng góp**: Find defects early, Reduce risk, Verify requirements, Build confidence
4. **QA ≠ Testing**: QA prevent (process), Testing detect (product)
5. **7 Principles**: Nền tảng của testing, cần nhớ và hiểu sâu
6. **Context matters**: Tailor testing approach theo loại project

---

## NEXT STEPS

📚 **Tiếp theo**: [Module 1.3: Quy trình Testing](module-1.3-quy-trinh-testing.md)

💪 **Ôn tập**:
- Vẽ lại flow Error → Defect → Failure
- Viết 1 example về mỗi Testing Principle
- Review QA vs Testing differences

---

**Thời gian học**: 4-5 giờ
**Thời gian ôn**: 45 phút (sau 2 ngày)
