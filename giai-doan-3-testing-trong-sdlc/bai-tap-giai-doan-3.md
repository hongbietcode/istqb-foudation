# BÀI TẬP GIAI ĐOẠN 3: TESTING TRONG SDLC

**Thời lượng**: 2-3 giờ
**Tiêu chuẩn đạt**: ≥80% (≥24/30 câu hỏi trắc nghiệm)

---

## PHẦN 1: BÀI TẬP THỰC HÀNH (5 bài)

### Bài tập 1: Áp Dụng Test Levels

**Scenario**: Bạn là QA Lead cho dự án phát triển app **Grab Food Clone**. App có các tính năng chính:
- User registration/login
- Browse restaurants
- Order food
- Payment (VNPay, MoMo)
- Order tracking
- Rating & reviews

**Yêu cầu**: Xác định test activities cho MỖI test level.

| Test Level | Test Activity | Test Object | Performer |
|------------|--------------|-------------|-----------|
| Component Testing | ? | ? | ? |
| Component Integration | ? | ? | ? |
| System Testing | ? | ? | ? |
| System Integration | ? | ? | ? |
| Acceptance Testing | ? | ? | ? |

<details>
<summary>Đáp án mẫu</summary>

| Test Level | Test Activity | Test Object | Performer |
|------------|--------------|-------------|-----------|
| Component Testing | Test `calculateDeliveryFee()` function, Test `validatePromoCode()` | Individual functions, classes | Developers |
| Component Integration | Test OrderService ↔ InventoryService, Test CartService ↔ PaymentService | APIs, module interfaces | Developers/QA |
| System Testing | Test complete order flow from browse to payment confirmation, Performance test với 1000 users | Complete integrated app | QA Team |
| System Integration | Test với VNPay/MoMo gateway, Test với restaurant POS systems | External APIs | QA Team |
| Acceptance Testing | UAT: Restaurant owners test order management, Beta: 500 users test full app | Business processes | Business users |

</details>

---

### Bài tập 2: Xác Định Test Types

**Scenario**: Cho các yêu cầu sau của hệ thống Banking App:

```
REQ-001: User can transfer money to another account
REQ-002: Transfer must complete within 3 seconds
REQ-003: All transfers require OTP verification
REQ-004: App must work on iOS 15+ and Android 10+
REQ-005: User can view transaction history
REQ-006: System must handle 10,000 concurrent users
REQ-007: 90% of users should be able to complete transfer without help
REQ-008: App must be accessible for visually impaired users
```

**Yêu cầu**: Phân loại mỗi requirement thuộc Functional hay Non-functional, và xác định loại test cụ thể.

| REQ | Type | Specific Test Type | Giải thích |
|-----|------|-------------------|------------|
| REQ-001 | ? | ? | ? |
| REQ-002 | ? | ? | ? |
| REQ-003 | ? | ? | ? |
| REQ-004 | ? | ? | ? |
| REQ-005 | ? | ? | ? |
| REQ-006 | ? | ? | ? |
| REQ-007 | ? | ? | ? |
| REQ-008 | ? | ? | ? |

<details>
<summary>Đáp án</summary>

| REQ | Type | Specific Test Type | Giải thích |
|-----|------|-------------------|------------|
| REQ-001 | Functional | Functional Testing | "What" system does - transfer function |
| REQ-002 | Non-functional | Performance Testing | "How well" - response time |
| REQ-003 | Functional | Security/Functional | Function requirement về OTP |
| REQ-004 | Non-functional | Compatibility Testing | Multi-platform support |
| REQ-005 | Functional | Functional Testing | Feature - view history |
| REQ-006 | Non-functional | Load/Scalability Testing | Capacity requirement |
| REQ-007 | Non-functional | Usability Testing | User experience metric |
| REQ-008 | Non-functional | Accessibility Testing | WCAG compliance |

</details>

---

### Bài tập 3: Confirmation vs Regression Testing

**Scenario**: Developer vừa fix bug **BUG-456**: "Checkout fails khi cart có hơn 10 items"

**Test Suite hiện tại**:
- TC-CART-001: Add single item to cart
- TC-CART-002: Add multiple items (5 items)
- TC-CART-003: Add 10+ items to cart ← Test này found BUG-456
- TC-CART-004: Remove item from cart
- TC-CHECKOUT-001: Checkout with 1 item
- TC-CHECKOUT-002: Checkout with promo code
- TC-CHECKOUT-003: Checkout with 10+ items ← Related to BUG-456
- TC-PAYMENT-001: Pay with credit card
- TC-PAYMENT-002: Pay with VNPay
- TC-ORDER-001: View order history

**Yêu cầu**:
1. Xác định tests nào là Confirmation Testing
2. Xác định tests nào là Regression Testing
3. Giải thích lý do

<details>
<summary>Đáp án</summary>

**CONFIRMATION TESTING** (verify bug is fixed):
- TC-CART-003: Add 10+ items to cart
- TC-CHECKOUT-003: Checkout with 10+ items

Lý do: Đây là tests đã tìm ra bug và tests liên quan trực tiếp đến bug.

**REGRESSION TESTING** (verify no new bugs):
- TC-CART-001: Add single item to cart
- TC-CART-002: Add multiple items (5 items)
- TC-CART-004: Remove item from cart
- TC-CHECKOUT-001: Checkout with 1 item
- TC-CHECKOUT-002: Checkout with promo code
- TC-PAYMENT-001: Pay with credit card
- TC-PAYMENT-002: Pay with VNPay
- TC-ORDER-001: View order history

Lý do: Đây là tests cho các features khác để đảm bảo fix không break existing functionality.

</details>

---

### Bài tập 4: SDLC Model Selection

**Scenario**: Cho các dự án sau, recommend SDLC model phù hợp và giải thích cách testing sẽ được thực hiện.

| Project | Description | Recommended SDLC | Testing Approach |
|---------|-------------|------------------|------------------|
| A | Government tax system với requirements rõ ràng, không thay đổi | ? | ? |
| B | Startup app với idea mới, requirements chưa rõ, cần feedback nhanh | ? | ? |
| C | Medical device software cần compliance và documentation đầy đủ | ? | ? |
| D | E-commerce website cần release features liên tục | ? | ? |

<details>
<summary>Đáp án</summary>

| Project | Recommended SDLC | Testing Approach |
|---------|------------------|------------------|
| A - Tax System | **Waterfall** hoặc **V-Model** | Sequential testing phases, formal documentation, extensive system testing, regulatory acceptance testing |
| B - Startup App | **Agile (Scrum)** | Testing throughout sprints, continuous testing, test automation, fast feedback, exploratory testing |
| C - Medical Device | **V-Model** | Parallel test planning, full traceability, formal verification & validation, regulatory compliance testing |
| D - E-commerce | **Agile với CI/CD** | Continuous testing, automated regression, DevOps pipeline, frequent releases, feature flags |

</details>

---

### Bài tập 5: White-box Coverage Calculation

**Scenario**: Cho đoạn code sau:

```javascript
function calculateShipping(weight, distance, express) {
  let baseCost = 10000;           // Line 1

  if (weight > 5) {               // Line 2 - Branch A
    baseCost = baseCost * 2;      // Line 3
  }

  if (distance > 100) {           // Line 4 - Branch B
    baseCost = baseCost + 50000;  // Line 5
  }

  if (express) {                  // Line 6 - Branch C
    baseCost = baseCost * 1.5;    // Line 7
  }

  return baseCost;                // Line 8
}
```

**Test Cases**:
- TC1: calculateShipping(3, 50, false)
- TC2: calculateShipping(10, 150, true)

**Yêu cầu**:
1. Tính Statement Coverage với TC1 và TC2
2. Tính Branch Coverage với TC1 và TC2
3. Nếu chưa đạt 100% branch coverage, đề xuất thêm test case

<details>
<summary>Đáp án</summary>

**TC1: calculateShipping(3, 50, false)**
- weight=3, distance=50, express=false
- Line 1: ✓ Executed
- Line 2: ✓ Executed (condition FALSE, weight 3 ≤ 5)
- Line 3: ✗ NOT executed (branch not taken)
- Line 4: ✓ Executed (condition FALSE, distance 50 ≤ 100)
- Line 5: ✗ NOT executed
- Line 6: ✓ Executed (condition FALSE)
- Line 7: ✗ NOT executed
- Line 8: ✓ Executed

**TC2: calculateShipping(10, 150, true)**
- weight=10, distance=150, express=true
- Line 1: ✓ Executed
- Line 2: ✓ Executed (condition TRUE, weight 10 > 5)
- Line 3: ✓ Executed
- Line 4: ✓ Executed (condition TRUE, distance 150 > 100)
- Line 5: ✓ Executed
- Line 6: ✓ Executed (condition TRUE)
- Line 7: ✓ Executed
- Line 8: ✓ Executed

**STATEMENT COVERAGE:**
With TC1 + TC2: Lines executed = {1, 2, 3, 4, 5, 6, 7, 8} = 8/8 = **100%**

**BRANCH COVERAGE:**
| Branch | True | False |
|--------|------|-------|
| A (weight > 5) | TC2 ✓ | TC1 ✓ |
| B (distance > 100) | TC2 ✓ | TC1 ✓ |
| C (express) | TC2 ✓ | TC1 ✓ |

Branch coverage = 6/6 = **100%**

**Kết luận**: TC1 và TC2 đạt 100% cả Statement và Branch coverage.

</details>

---

## PHẦN 2: CÂU HỎI TRẮC NGHIỆM (30 câu)

**Thời gian**: 45 phút
**Yêu cầu đạt**: ≥80% (24/30 câu)

---

### Câu 1 (K2)
Trong Waterfall model, testing phase được thực hiện khi nào?

A. Song song với development
B. Sau khi development phase hoàn thành
C. Trước design phase
D. Liên tục trong suốt project

<details>
<summary>Đáp án</summary>

**B. Sau khi development phase hoàn thành**

Giải thích: Waterfall là sequential model, testing là phase riêng biệt sau development.
</details>

---

### Câu 2 (K1)
V-Model còn được gọi là gì?

A. Agile Model
B. Verification and Validation Model
C. Vertical Model
D. Variable Model

<details>
<summary>Đáp án</summary>

**B. Verification and Validation Model**

Giải thích: V-Model = Verification (building right) and Validation (building the right thing).
</details>

---

### Câu 3 (K2)
Trong Agile, testing được thực hiện như thế nào?

A. Sau mỗi sprint
B. Cuối project
C. Throughout the sprint (liên tục)
D. Chỉ khi có bugs

<details>
<summary>Đáp án</summary>

**C. Throughout the sprint (liên tục)**

Giải thích: Agile testing là continuous, không có separate testing phase.
</details>

---

### Câu 4 (K1)
TDD là viết tắt của?

A. Technical Design Document
B. Test-Driven Development
C. Testing During Development
D. Test Data Definition

<details>
<summary>Đáp án</summary>

**B. Test-Driven Development**
</details>

---

### Câu 5 (K2)
Trong TDD, thứ tự đúng là gì?

A. Code → Test → Refactor
B. Test → Code → Refactor
C. Refactor → Code → Test
D. Design → Code → Test

<details>
<summary>Đáp án</summary>

**B. Test → Code → Refactor**

Giải thích: TDD cycle: RED (write failing test) → GREEN (write code to pass) → REFACTOR
</details>

---

### Câu 6 (K1)
BDD sử dụng format nào?

A. If-Then-Else
B. Given-When-Then
C. Input-Output
D. Setup-Execute-Assert

<details>
<summary>Đáp án</summary>

**B. Given-When-Then**

Giải thích: BDD dùng Gherkin syntax: Given (precondition), When (action), Then (expected outcome)
</details>

---

### Câu 7 (K2)
Shift-Left testing có nghĩa là gì?

A. Move testing sang team khác
B. Move testing sớm hơn trong SDLC
C. Giảm số lượng tests
D. Test chỉ ở production

<details>
<summary>Đáp án</summary>

**B. Move testing sớm hơn trong SDLC**

Giải thích: Shift-Left = Di chuyển activities sang "trái" (sớm hơn) trên timeline.
</details>

---

### Câu 8 (K2)
Lợi ích chính của CI/CD đối với testing là gì?

A. Không cần testers
B. Fast feedback on code quality
C. Giảm số lượng bugs
D. Không cần automation

<details>
<summary>Đáp án</summary>

**B. Fast feedback on code quality**

Giải thích: CI/CD chạy tests automatically, cho feedback nhanh khi code có vấn đề.
</details>

---

### Câu 9 (K1)
Component Testing còn được gọi là gì?

A. Integration Testing
B. Unit Testing
C. System Testing
D. Acceptance Testing

<details>
<summary>Đáp án</summary>

**B. Unit Testing**
</details>

---

### Câu 10 (K2)
Ai thường thực hiện Component Testing?

A. End users
B. Business analysts
C. Developers
D. Project managers

<details>
<summary>Đáp án</summary>

**C. Developers**

Giải thích: Unit testing thường do developers thực hiện vì họ hiểu code.
</details>

---

### Câu 11 (K2)
Component Integration Testing focus vào gì?

A. Complete system functionality
B. Interfaces between components
C. User acceptance
D. Performance metrics

<details>
<summary>Đáp án</summary>

**B. Interfaces between components**

Giải thích: Component Integration Testing kiểm tra interactions và interfaces giữa components.
</details>

---

### Câu 12 (K2)
System Testing được thực hiện trên môi trường nào?

A. Developer's machine
B. Production environment
C. Production-like (staging) environment
D. Customer's site

<details>
<summary>Đáp án</summary>

**C. Production-like (staging) environment**

Giải thích: System Testing cần môi trường giống production để có kết quả chính xác.
</details>

---

### Câu 13 (K1)
User Acceptance Testing (UAT) được thực hiện bởi ai?

A. QA Team
B. Developers
C. Business users / Customers
D. Database administrators

<details>
<summary>Đáp án</summary>

**C. Business users / Customers**
</details>

---

### Câu 14 (K2)
Operational Acceptance Testing (OAT) focus vào gì?

A. Business functionality
B. User experience
C. Backup, recovery, system administration
D. Payment processing

<details>
<summary>Đáp án</summary>

**C. Backup, recovery, system administration**

Giải thích: OAT verify system có thể được maintained và operated.
</details>

---

### Câu 15 (K2)
Alpha testing khác Beta testing ở điểm nào?

A. Alpha test ở customer site, Beta test ở developer site
B. Alpha test ở developer site, Beta test ở customer site
C. Không có sự khác biệt
D. Alpha chỉ test functional, Beta test non-functional

<details>
<summary>Đáp án</summary>

**B. Alpha test ở developer site, Beta test ở customer site**
</details>

---

### Câu 16 (K2)
Functional testing focus vào gì?

A. How fast system responds
B. What the system does
C. How secure the system is
D. How many users can access

<details>
<summary>Đáp án</summary>

**B. What the system does**
</details>

---

### Câu 17 (K1)
Theo ISO 25010, Performance Efficiency bao gồm gì?

A. Security và reliability
B. Time behavior, resource utilization, capacity
C. Usability và accessibility
D. Maintainability và portability

<details>
<summary>Đáp án</summary>

**B. Time behavior, resource utilization, capacity**
</details>

---

### Câu 18 (K2)
Load Testing thuộc loại testing nào?

A. Functional Testing
B. Usability Testing
C. Performance Testing
D. Security Testing

<details>
<summary>Đáp án</summary>

**C. Performance Testing**
</details>

---

### Câu 19 (K2)
Black-box testing không cần biết gì?

A. Requirements
B. User stories
C. Internal code structure
D. Expected outputs

<details>
<summary>Đáp án</summary>

**C. Internal code structure**

Giải thích: Black-box test based on specifications, không cần biết code implementation.
</details>

---

### Câu 20 (K2)
White-box testing thường do ai thực hiện?

A. End users
B. Business analysts
C. Developers hoặc technical testers
D. Project managers

<details>
<summary>Đáp án</summary>

**C. Developers hoặc technical testers**

Giải thích: White-box testing cần coding skills để hiểu code structure.
</details>

---

### Câu 21 (K2)
Statement Coverage đo lường gì?

A. Số branches được test
B. Số statements được execute
C. Số test cases được chạy
D. Số bugs được tìm

<details>
<summary>Đáp án</summary>

**B. Số statements được execute**
</details>

---

### Câu 22 (K2)
Branch Coverage yêu cầu gì?

A. Execute mỗi statement 1 lần
B. Execute mỗi branch (true/false) ít nhất 1 lần
C. Execute mỗi path qua code
D. Execute mỗi function

<details>
<summary>Đáp án</summary>

**B. Execute mỗi branch (true/false) ít nhất 1 lần**
</details>

---

### Câu 23 (K2)
Confirmation Testing verify gì?

A. System performance
B. Defect đã được fix
C. New features work
D. No regression issues

<details>
<summary>Đáp án</summary>

**B. Defect đã được fix**
</details>

---

### Câu 24 (K2)
Regression Testing verify gì?

A. Defect được fix
B. Changes không break existing functionality
C. New requirements
D. User acceptance

<details>
<summary>Đáp án</summary>

**B. Changes không break existing functionality**
</details>

---

### Câu 25 (K2)
Regression testing nên được automate vì?

A. Manual testing không thể thực hiện
B. Tests chạy frequently và repetitively
C. Automation rẻ hơn
D. Users yêu cầu

<details>
<summary>Đáp án</summary>

**B. Tests chạy frequently và repetitively**

Giải thích: Regression tests chạy mỗi khi có change, manual execution không practical.
</details>

---

### Câu 26 (K2)
Maintenance Testing được trigger bởi?

A. Chỉ khi có new requirements
B. Modifications, migrations, hoặc retirement
C. Chỉ khi system crash
D. Chỉ cuối năm

<details>
<summary>Đáp án</summary>

**B. Modifications, migrations, hoặc retirement**
</details>

---

### Câu 27 (K2)
Impact Analysis trong maintenance testing giúp gì?

A. Estimate project cost
B. Determine testing scope based on changes
C. Find all bugs
D. Train new team members

<details>
<summary>Đáp án</summary>

**B. Determine testing scope based on changes**

Giải thích: Impact analysis xác định areas bị ảnh hưởng để decide test scope.
</details>

---

### Câu 28 (K1)
Good testing practice nào áp dụng cho mọi SDLC?

A. Testing chỉ ở cuối project
B. Early tester involvement
C. Không cần documentation
D. Chỉ developer test

<details>
<summary>Đáp án</summary>

**B. Early tester involvement**
</details>

---

### Câu 29 (K2)
Retrospective trong Agile giúp testing như thế nào?

A. Không liên quan đến testing
B. Identify improvements cho test process
C. Replace testing
D. Reduce test coverage

<details>
<summary>Đáp án</summary>

**B. Identify improvements cho test process**

Giải thích: Retrospectives review what went well/wrong, giúp improve testing process.
</details>

---

### Câu 30 (K2)
Trong DevOps pipeline, automated tests đóng vai trò gì?

A. Optional, không quan trọng
B. Quality gate - code không proceed nếu tests fail
C. Chỉ run ở production
D. Thay thế manual testing hoàn toàn

<details>
<summary>Đáp án</summary>

**B. Quality gate - code không proceed nếu tests fail**
</details>

---

## PHẦN 3: ĐÁP ÁN VÀ TÍNH ĐIỂM

### Bảng Đáp Án Trắc Nghiệm

| Câu | Đáp án | Câu | Đáp án | Câu | Đáp án |
|-----|--------|-----|--------|-----|--------|
| 1 | B | 11 | B | 21 | B |
| 2 | B | 12 | C | 22 | B |
| 3 | C | 13 | C | 23 | B |
| 4 | B | 14 | C | 24 | B |
| 5 | B | 15 | B | 25 | B |
| 6 | B | 16 | B | 26 | B |
| 7 | B | 17 | B | 27 | B |
| 8 | B | 18 | C | 28 | B |
| 9 | B | 19 | C | 29 | B |
| 10 | C | 20 | C | 30 | B |

### Thang Điểm

| Số câu đúng | Đánh giá | Khuyến nghị |
|-------------|----------|-------------|
| 27-30 | ⭐⭐⭐ Xuất sắc | Sẵn sàng chuyển sang Giai đoạn 4 |
| 24-26 | ⭐⭐ Đạt | Có thể tiến tiếp, review lại các câu sai |
| 20-23 | ⭐ Chưa đạt | Đọc lại Modules 3.1, 3.2, 3.3 |
| <20 | ❌ Cần ôn lại | Học lại toàn bộ Giai đoạn 3 |

---

## PHẦN 4: CHECKLIST TỰ ĐÁNH GIÁ

Hoàn thành checklist sau trước khi chuyển sang Giai đoạn 4:

### SDLC và Testing
- [ ] Phân biệt được Waterfall, V-Model, Agile
- [ ] Giải thích được testing trong mỗi SDLC model
- [ ] Nêu được good testing practices cho mọi SDLC
- [ ] Hiểu được TDD, ATDD, BDD
- [ ] Giải thích được DevOps và CI/CD
- [ ] Mô tả được Shift-Left approach

### Test Levels
- [ ] Phân biệt được 5 test levels
- [ ] Nêu được objectives, test basis, test objects của mỗi level
- [ ] Biết ai thường thực hiện mỗi level
- [ ] Phân biệt được các loại acceptance testing

### Test Types
- [ ] Phân biệt được Functional và Non-functional testing
- [ ] Nêu được các đặc tính ISO 25010
- [ ] Phân biệt được Black-box và White-box testing
- [ ] Hiểu được Statement và Branch coverage
- [ ] Phân biệt được Confirmation và Regression testing

---

## TỔNG KẾT GIAI ĐOẠN 3

Sau khi hoàn thành Giai đoạn 3, bạn đã học được:

```
✅ SDLC VÀ TESTING
   → Sequential models (Waterfall, V-Model)
   → Iterative/Incremental models
   → Agile (Scrum)
   → Test-first approaches (TDD, ATDD, BDD)
   → DevOps và CI/CD
   → Shift-Left testing
   → Retrospectives

✅ TEST LEVELS
   → Component Testing (Unit Testing)
   → Component Integration Testing
   → System Testing
   → System Integration Testing
   → Acceptance Testing (UAT, OAT, Alpha, Beta)

✅ TEST TYPES
   → Functional vs Non-functional Testing
   → ISO 25010 Quality Characteristics
   → Black-box vs White-box Testing
   → Confirmation vs Regression Testing
   → Maintenance Testing
```

---

**Tiếp theo**: [Giai đoạn 4: Black-Box Techniques](../giai-doan-4-black-box-techniques/module-4.1-test-techniques-overview.md)

---

**Version**: 1.0.0
**Last Updated**: November 2025
