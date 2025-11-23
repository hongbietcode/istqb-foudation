# BÀI TẬP GIAI ĐOẠN 5: OTHER TECHNIQUES

**Thời lượng**: 2-3 giờ | **Độ quan trọng**: ⭐⭐⭐

---

## MỤC TIÊU

- Củng cố kiến thức White-Box Testing
- Thực hành Experience-Based Techniques
- Áp dụng Collaboration-Based Approaches

---

## CÂU HỎI TRẮC NGHIỆM (30 CÂU)

### NHÓM 1: WHITE-BOX TESTING (10 câu)

**Câu 1** (K2)
White-box testing technique nào focus vào executing mỗi statement ít nhất 1 lần?

A. Branch coverage
B. Statement coverage
C. Path coverage
D. Condition coverage

<details>
<summary>Đáp án</summary>

**B. Statement coverage**

Giải thích: Statement coverage đo % statements được executed.
</details>

---

**Câu 2** (K3)
Code có 20 statements, test suite execute 16 statements. Statement coverage?

A. 16%
B. 20%
C. 80%
D. 100%

<details>
<summary>Đáp án</summary>

**C. 80%**

16/20 × 100% = 80%
</details>

---

**Câu 3** (K3)
```javascript
function check(x) {
    if (x > 0) {     // Decision 1
        return "Positive";
    }
    return "Non-positive";
}
```

Test case: `x = 5`. Branch coverage?

A. 0%
B. 50%
C. 100%
D. 75%

<details>
<summary>Đáp án</summary>

**B. 50%**

Decision 1 có 2 branches (True, False). Test case chỉ cover True branch.
1/2 = 50%
</details>

---

**Câu 4** (K2)
Statement nào ĐÚNG về relationship giữa Statement và Branch coverage?

A. Statement coverage mạnh hơn Branch coverage
B. 100% Statement coverage guarantees 100% Branch coverage
C. 100% Branch coverage guarantees 100% Statement coverage
D. Hai metrics không liên quan

<details>
<summary>Đáp án</summary>

**C. 100% Branch coverage guarantees 100% Statement coverage**

Branch coverage subsumes Statement coverage.
</details>

---

**Câu 5** (K3)
```python
def grade(score):
    if score >= 60:     # D1
        return "Pass"
    return "Fail"
```

Minimum test cases để đạt 100% Branch coverage?

A. 1
B. 2
C. 3
D. 4

<details>
<summary>Đáp án</summary>

**B. 2**

Decision 1 có 2 branches:
- TC1: score=70 → True branch
- TC2: score=50 → False branch
</details>

---

**Câu 6** (K3)
Code có 3 decisions, mỗi decision có 2 branches. Total branches?

A. 3
B. 5
C. 6
D. 8

<details>
<summary>Đáp án</summary>

**C. 6**

3 decisions × 2 branches each = 6 branches
</details>

---

**Câu 7** (K2)
White-box testing phù hợp nhất ở test level nào?

A. System testing
B. Acceptance testing
C. Component (Unit) testing
D. Exploratory testing

<details>
<summary>Đáp án</summary>

**C. Component (Unit) testing**

White-box requires code access, most commonly used in unit testing by developers.
</details>

---

**Câu 8** (K2)
Value chính của measuring code coverage là gì?

A. Replace functional testing
B. Guarantee bug-free code
C. Identify untested parts of code
D. Reduce test execution time

<details>
<summary>Đáp án</summary>

**C. Identify untested parts of code**

Coverage shows which code has/hasn't been executed, helping identify gaps.
</details>

---

**Câu 9** (K3)
```javascript
function max(a, b, c) {
    let max = a;          // S1
    if (b > max) {        // D1
        max = b;          // S2
    }
    if (c > max) {        // D2
        max = c;          // S3
    }
    return max;           // S4
}
```

Test case: `max(5, 3, 2)`. Executed statements?

A. S1, S4
B. S1, S2, S4
C. S1, S2, S3, S4
D. All statements

<details>
<summary>Đáp án</summary>

**A. S1, S4**

- S1 executed (max = 5)
- D1: b(3) > max(5)? False → S2 NOT executed
- D2: c(2) > max(5)? False → S3 NOT executed
- S4 executed (return 5)

Only S1 and S4.
</details>

---

**Câu 10** (K2)
Tool nào dùng để measure code coverage cho JavaScript?

A. JUnit
B. Istanbul (nyc)
C. PyTest
D. JaCoCo

<details>
<summary>Đáp án</summary>

**B. Istanbul (nyc)**

Istanbul/nyc là coverage tool cho JavaScript. JUnit (Java), PyTest (Python), JaCoCo (Java).
</details>

---

### NHÓM 2: EXPERIENCE-BASED TECHNIQUES (10 câu)

**Câu 11** (K2)
Error guessing dựa trên gì?

A. Formal specifications
B. Code structure
C. Tester's experience và past defects
D. Coverage metrics

<details>
<summary>Đáp án</summary>

**C. Tester's experience và past defects**

Error guessing = anticipate errors based on experience.
</details>

---

**Câu 12** (K2)
Exploratory testing được định nghĩa là gì?

A. Testing without any planning
B. Simultaneous learning, test design, và execution
C. Only ad-hoc testing
D. Automated testing

<details>
<summary>Đáp án</summary>

**B. Simultaneous learning, test design, và execution**

Definition by James Bach.
</details>

---

**Câu 13** (K2)
Session-based exploratory testing thường kéo dài bao lâu?

A. 15-30 minutes
B. 60-120 minutes
C. 4-6 hours
D. 1-2 days

<details>
<summary>Đáp án</summary>

**B. 60-120 minutes**

Typical session length: 60-120 mins, time-boxed.
</details>

---

**Câu 14** (K2)
Charter trong exploratory testing là gì?

A. Contract với client
B. Test plan document
C. Mission/goal for testing session
D. Test case template

<details>
<summary>Đáp án</summary>

**C. Mission/goal for testing session**

Charter defines what to explore in the session.
</details>

---

**Câu 15** (K1)
Error guessing cũng được gọi là gì?

A. Fault injection
B. Fault attack
C. Mutation testing
D. Fuzz testing

<details>
<summary>Đáp án</summary>

**B. Fault attack**

Error guessing = Fault attack (target specific fault types).
</details>

---

**Câu 16** (K2)
Checklist-based testing khác test cases ở điểm nào?

A. Checklist có expected results chi tiết
B. Checklist là high-level, không có detailed steps
C. Checklist formal hơn test cases
D. Checklist không reusable

<details>
<summary>Đáp án</summary>

**B. Checklist là high-level, không có detailed steps**

Checklist provides items to check, not detailed step-by-step instructions.
</details>

---

**Câu 17** (K2)
Khi nào NÊN dùng exploratory testing?

A. Regulatory compliance testing
B. When specs unclear, need quick feedback
C. Only for regression testing
D. When automation is not possible

<details>
<summary>Đáp án</summary>

**B. When specs unclear, need quick feedback**

Exploratory good for unclear requirements, time constraints, early testing.
</details>

---

**Câu 18** (K2)
Common error category nào dưới đây thường được target bởi error guessing?

A. Division by zero
B. Successful transactions only
C. Normal user behavior
D. Positive test cases

<details>
<summary>Đáp án</summary>

**A. Division by zero**

Division by zero là common error often targeted by error guessing.
</details>

---

**Câu 19** (K2)
Checklist-based testing lấy từ nguồn nào?

A. Only requirements
B. Past experience, standards, common issues
C. Only code coverage
D. Only user feedback

<details>
<summary>Đáp án</summary>

**B. Past experience, standards, common issues**

Checklists built from experience, industry standards (OWASP, WCAG), common defects.
</details>

---

**Câu 20** (K2)
Experience-based techniques bị hạn chế vì sao?

A. Too formal
B. Require expensive tools
C. Results depend on tester skill, hard to measure coverage
D. Only work for unit testing

<details>
<summary>Đáp án</summary>

**C. Results depend on tester skill, hard to measure coverage**

Experience-based không có quantifiable coverage, results vary by tester.
</details>

---

### NHÓM 3: COLLABORATION-BASED APPROACHES (10 câu)

**Câu 21** (K2)
3 C's của user stories là gì?

A. Code, Compile, Check
B. Card, Conversation, Confirmation
C. Create, Collaborate, Complete
D. Component, Container, Context

<details>
<summary>Đáp án</summary>

**B. Card, Conversation, Confirmation**

Card (written story), Conversation (discussion), Confirmation (AC).
</details>

---

**Câu 22** (K3)
User story format đúng là gì?

A. Given-When-Then
B. As a [role], I want [feature], So that [benefit]
C. Test case format
D. Epic structure

<details>
<summary>Đáp án</summary>

**B. As a [role], I want [feature], So that [benefit]**

Standard user story format.
</details>

---

**Câu 23** (K2)
INVEST trong user stories, "I" stands for?

A. Integrated
B. Independent
C. Investigated
D. Incremental

<details>
<summary>Đáp án</summary>

**B. Independent**

Independent, Negotiable, Valuable, Estimable, Small, Testable
</details>

---

**Câu 24** (K2)
INVEST "V" có nghĩa là gì?

A. Verified
B. Validated
C. Valuable (to user)
D. Variable

<details>
<summary>Đáp án</summary>

**C. Valuable (to user)**

Story phải deliver value cho user/customer.
</details>

---

**Câu 25** (K3)
User story nào vi phạm INVEST "V"?

A. As a customer, I want to track my order
B. As a developer, I want to refactor database code
C. As an admin, I want to manage users
D. As a user, I want to reset password

<details>
<summary>Đáp án</summary>

**B. As a developer, I want to refactor database code**

Không valuable cho user - chỉ technical benefit.
</details>

---

**Câu 26** (K3)
Given-When-Then format, "When" represents gì?

A. Expected result
B. Precondition
C. Action/event
D. Test data

<details>
<summary>Đáp án</summary>

**C. Action/event**

GIVEN (context) → WHEN (action) → THEN (outcome)
</details>

---

**Câu 27** (K2)
Acceptance criteria nên được written khi nào?

A. After implementation complete
B. During testing phase
C. Before implementation starts
D. After deployment

<details>
<summary>Đáp án</summary>

**C. Before implementation starts**

AC define "Done", should be written upfront for shared understanding.
</details>

---

**Câu 28** (K2)
ATDD stands for gì?

A. Automated Test-Driven Development
B. Acceptance Test-Driven Development
C. Agile Test Design Deployment
D. Advanced Testing Development Discipline

<details>
<summary>Đáp án</summary>

**B. Acceptance Test-Driven Development**

Define acceptance tests first, then develop code to pass them.
</details>

---

**Câu 29** (K2)
ATDD process bắt đầu với activity nào?

A. Write code
B. Write unit tests
C. Specification workshop với team
D. Deploy to production

<details>
<summary>Đáp án</summary>

**C. Specification workshop với team**

ATDD starts with collaboration - PO, Dev, Tester define AC together.
</details>

---

**Câu 30** (K2)
Ai tham gia Specification Workshop trong ATDD?

A. Only testers
B. Only developers
C. Product Owner, Developers, Testers (whole team)
D. Only Product Owner

<details>
<summary>Đáp án</summary>

**C. Product Owner, Developers, Testers (whole team)**

Three Amigos: PO (what), Dev (how), Tester (what if).
</details>

---

## ĐÁP ÁN TỔNG HỢP

### Bảng Đáp Án Nhanh

| Câu | Đáp án | Câu | Đáp án | Câu | Đáp án |
|-----|--------|-----|--------|-----|--------|
| 1 | B | 11 | C | 21 | B |
| 2 | C | 12 | B | 22 | B |
| 3 | B | 13 | B | 23 | B |
| 4 | C | 14 | C | 24 | C |
| 5 | B | 15 | B | 25 | B |
| 6 | C | 16 | B | 26 | C |
| 7 | C | 17 | B | 27 | C |
| 8 | C | 18 | A | 28 | B |
| 9 | A | 19 | B | 29 | C |
| 10 | B | 20 | C | 30 | C |

---

## PHẦN B: BÀI TẬP THỰC HÀNH

### BÀI TẬP 1: Calculate Coverage

**Code:**
```python
def calculate_shipping(weight, distance):
    cost = 0                              # S1

    if weight > 0 and distance > 0:       # D1
        cost = weight * 5 + distance * 2  # S2

        if weight > 10:                   # D2
            cost = cost * 0.9             # S3 (10% discount)

    return cost                           # S4
```

**Câu hỏi:**
1. Có bao nhiêu statements?
2. Có bao nhiêu decisions và branches?
3. Test case: `weight=15, distance=100`. Statement coverage?
4. Thiết kế test suite để đạt 100% Branch coverage

<details>
<summary>Đáp án</summary>

**1. Statements:** 4 (S1, S2, S3, S4)

**2. Decisions và Branches:**
- Decisions: 2 (D1, D2)
- Branches: 4 (D1-T, D1-F, D2-T, D2-F)

**3. Test case weight=15, distance=100:**
- Path: S1 → D1(T) → S2 → D2(T) → S3 → S4
- Executed: All statements (S1, S2, S3, S4)
- **Statement Coverage: 4/4 = 100%**

**4. Test Suite cho 100% Branch Coverage:**

| TC | weight | distance | D1 | D2 | Branches Covered |
|----|--------|----------|----|----|------------------|
| 1 | 15 | 100 | T | T | D1-T, D2-T |
| 2 | 5 | 50 | T | F | D1-T, D2-F |
| 3 | 0 | 100 | F | - | D1-F |

**3 test cases cover all 4 branches → 100% Branch Coverage**

</details>

---

### BÀI TẬP 2: Exploratory Testing Charter

**Scenario:** Bạn là tester cho ứng dụng Momo. Hãy tạo charter cho exploratory testing session.

**Câu hỏi:**
1. Viết charter cho session testing payment flow
2. List các areas bạn sẽ explore
3. Tạo template session notes

<details>
<summary>Đáp án Mẫu</summary>

**1. Charter:**
```
CHARTER: Explore payment flow to find transaction-related bugs

FOCUS AREAS:
- Payment method selection
- Insufficient balance handling
- Network interruption scenarios
- Receipt generation
- Transaction history

TIME: 90 minutes
TESTER: [Your name]
```

**2. Areas to Explore:**
- Payment methods: Momo wallet, linked cards, bank transfer
- Edge cases: Minimum amount (1,000 VND), maximum amount
- Insufficient balance scenarios
- Network: WiFi, 4G, offline
- Interruptions: Incoming call, app backgrounded
- Security: Transaction PIN, biometric auth
- Error handling: Timeout, failed transactions
- Concurrent transactions
- Receipt and transaction history

**3. Session Notes Template:**
```
SESSION START: [Time]
APP VERSION: [Version]
DEVICE: [Model, OS]
CHARTER: [Charter text]

SETUP ([Time range]):
- Test account balance: X VND
- Payment methods configured
- Network: WiFi

EXPLORATION ([Time range]):
[Timestamp] - [Activity/Observation]
- ✅ [What worked]
- 🐛 BUG #N: [Bug description]
- 🔍 OBSERVATION: [Interesting finding]
- 💡 QUESTION: [Question raised]

BUGS FOUND:
1. [Bug 1] - Priority: [H/M/L]
2. [Bug 2] - Priority: [H/M/L]

COVERAGE:
- [Areas tested]
- [Not covered]

FOLLOW-UP:
- [Questions to ask]
- [Areas need more testing]

SESSION END: [Time]
```

</details>

---

### BÀI TẬP 3: Write User Story với INVEST

**Scenario:** E-commerce app cần feature "Save for later" trong cart.

**Câu hỏi:**
1. Viết user story
2. Đánh giá theo INVEST
3. Viết acceptance criteria (Given-When-Then)

<details>
<summary>Đáp án</summary>

**1. User Story:**
```
US-456: Save Items for Later

As a Shopee customer,
I want to move cart items to "Save for later" list,
So that I can purchase them later without losing them.
```

**2. INVEST Evaluation:**

| Criterion | ✅/❌ | Explanation |
|-----------|-------|-------------|
| **I**ndependent | ✅ | Không depend on other stories |
| **N**egotiable | ✅ | Details flexible (max items, UI, etc.) |
| **V**aluable | ✅ | Value: Keep items without buying now |
| **E**stimable | ✅ | Team có thể estimate (3-5 SP) |
| **S**mall | ✅ | Fit trong 1 sprint |
| **T**estable | ✅ | Có thể write clear AC |

**VERDICT: Good story!** ✅

**3. Acceptance Criteria:**

```gherkin
AC1: Move item to "Save for later"
  GIVEN customer has "iPhone 15" in cart
  WHEN customer clicks "Save for later" on that item
  THEN item is removed from cart
    AND item appears in "Saved items" section
    AND cart total is updated

AC2: Move saved item back to cart
  GIVEN customer has "iPhone 15" in "Saved items"
  WHEN customer clicks "Move to cart"
  THEN item is added to cart
    AND item is removed from "Saved items"
    AND cart total includes the item

AC3: View saved items
  GIVEN customer has saved items
  WHEN customer goes to cart page
  THEN "Saved items" section is visible
    AND shows all saved items with images, names, prices

AC4: Saved items persist across sessions
  GIVEN customer saved items and logged out
  WHEN customer logs back in
  THEN saved items are still there

AC5: Maximum limit
  GIVEN customer has 50 saved items (max limit)
  WHEN customer tries to save another item
  THEN error message "Maximum 50 saved items" is shown
    AND item remains in cart
```

</details>

---

### BÀI TẬP 4: Error Guessing Checklist

**Scenario:** Testing login form.

**Câu hỏi:** List 15 potential errors/attacks để test bằng error guessing.

<details>
<summary>Đáp án</summary>

**Error Guessing List for Login:**

| # | Potential Error/Attack | Test Input |
|---|------------------------|------------|
| 1 | Empty username | username="", password="any" |
| 2 | Empty password | username="valid", password="" |
| 3 | Both empty | username="", password="" |
| 4 | SQL Injection | username="admin'--", password="any" |
| 5 | XSS attack | username="<script>alert(1)</script>" |
| 6 | Very long inputs | username=1000 chars, password=1000 chars |
| 7 | Special characters | username="!@#$%^&*()", password="^&*()_+" |
| 8 | Leading spaces | username=" admin", password="pass" |
| 9 | Trailing spaces | username="admin ", password="pass" |
| 10 | Case sensitivity | "Admin" vs "admin" |
| 11 | Brute force | Try 100 login attempts rapidly |
| 12 | Account enumeration | Try various usernames, observe responses |
| 13 | Concurrent logins | Same user login from 2 browsers |
| 14 | Session timeout | Login, wait 30 mins, try action |
| 15 | CSRF attack | Craft malicious login request |

**Nguồn:**
- ✅ OWASP Top 10 (Security vulnerabilities)
- ✅ Past bugs in similar systems
- ✅ Common input validation issues
- ✅ Authentication best practices

</details>

---

### BÀI TẬP 5: ATDD Workflow

**Scenario:** Implement "Apply promo code" feature for Shopee.

**Câu hỏi:**
1. Viết user story
2. Viết acceptance criteria (Given-When-Then)
3. Mô tả ATDD workflow (5 steps)

<details>
<summary>Đáp án</summary>

**1. User Story:**
```
As a Shopee customer,
I want to apply promo codes to my order,
So that I can get discounts.
```

**2. Acceptance Criteria:**

```gherkin
Scenario 1: Apply valid promo code
  GIVEN customer has items worth 500,000 VND in cart
    AND valid promo code "SALE20" exists (20% off)
  WHEN customer enters "SALE20" in promo code field
    AND clicks "Apply"
  THEN discount of 100,000 VND is applied
    AND order total becomes 400,000 VND
    AND message "Promo code applied successfully" is shown

Scenario 2: Invalid promo code
  GIVEN customer has items in cart
  WHEN customer enters invalid code "INVALID123"
    AND clicks "Apply"
  THEN error message "Invalid promo code" is shown
    AND no discount is applied

Scenario 3: Expired promo code
  GIVEN promo code "EXPIRED" has expired yesterday
  WHEN customer tries to apply "EXPIRED"
  THEN error "Promo code expired" is shown

Scenario 4: Minimum order requirement
  GIVEN promo code "MIN500" requires minimum 500K order
    AND customer has 300K in cart
  WHEN customer tries to apply "MIN500"
  THEN error "Minimum order 500,000 VND required" is shown
```

**3. ATDD Workflow:**

**Step 1: Specification Workshop**
```
PARTICIPANTS: PO, Developer, Tester

DISCUSSION:
- PO: Users want to apply promo codes for discounts
- Dev: Where to store promo codes? Database?
- Tester: What about multiple codes? Stacking allowed?
- PO: Only 1 code per order. Codes in database with:
  * Code, Discount %, Expiry date, Min order amount

OUTCOME: User story + 4 acceptance criteria (above)
```

**Step 2: Create Acceptance Tests**
```gherkin
Feature: Promo Code Application

  Scenario: Apply valid promo code
    Given I have items worth "500000" VND in cart
    And promo code "SALE20" is valid with "20%" discount
    When I apply promo code "SALE20"
    Then I should see discount of "100000" VND
    And order total should be "400000" VND
    And I should see message "Promo code applied successfully"

  # ... (other scenarios)
```

**Step Definitions (initially FAIL - RED):**
```javascript
Given('I have items worth {string} VND in cart', function(amount) {
  this.cart = new Cart();
  this.cart.addItem({ price: parseInt(amount) });
});

When('I apply promo code {string}', function(code) {
  this.result = this.cart.applyPromoCode(code);
});

Then('I should see discount of {string} VND', function(discount) {
  assert.equal(this.cart.discount, parseInt(discount));
});
```

**Step 3: Implement Feature**
```javascript
class Cart {
  constructor() {
    this.items = [];
    this.promoCode = null;
    this.discount = 0;
  }

  applyPromoCode(code) {
    const promo = PromoCodeService.getByCode(code);

    if (!promo) {
      throw new Error("Invalid promo code");
    }

    if (promo.isExpired()) {
      throw new Error("Promo code expired");
    }

    if (this.total() < promo.minOrderAmount) {
      throw new Error(`Minimum order ${promo.minOrderAmount} VND required`);
    }

    this.promoCode = promo;
    this.discount = this.total() * promo.discountPercent / 100;
    return "Promo code applied successfully";
  }

  total() {
    const subtotal = this.items.reduce((sum, item) => sum + item.price, 0);
    return subtotal - this.discount;
  }
}
```

**Step 4: Run Tests → PASS (GREEN)**
```
✓ Apply valid promo code
✓ Invalid promo code
✓ Expired promo code
✓ Minimum order requirement

4 scenarios passed
```

**Step 5: Refactor**
```javascript
// Refactor: Extract validation logic
class PromoCodeValidator {
  static validate(promo, cart) {
    if (!promo) throw new InvalidPromoCodeError();
    if (promo.isExpired()) throw new ExpiredPromoCodeError();
    if (cart.total() < promo.minOrderAmount) {
      throw new MinimumOrderNotMetError(promo.minOrderAmount);
    }
  }
}

// Tests still PASS after refactoring ✅
```

</details>

---

## CHECKLIST TỰ ĐÁNH GIÁ

### White-Box Testing
- [ ] Tính được Statement Coverage từ code và test cases
- [ ] Tính được Branch Coverage
- [ ] Hiểu difference và relationship giữa Statement vs Branch
- [ ] Thiết kế được test cases để đạt target coverage
- [ ] Biết khi nào dùng white-box testing

### Experience-Based
- [ ] List được common errors cho error guessing
- [ ] Viết được charter cho exploratory testing session
- [ ] Document được exploratory session notes
- [ ] Tạo được checklist cho testing
- [ ] Hiểu khi nào nên dùng experience-based techniques

### Collaboration-Based
- [ ] Viết được user story đúng format
- [ ] Đánh giá user story theo INVEST
- [ ] Viết được acceptance criteria (Given-When-Then)
- [ ] Hiểu ATDD workflow
- [ ] Biết vai trò của mỗi team member

---

## TÓM TẮT GIAI ĐOẠN 5

```
╔═══════════════════════════════════════════════════════════════╗
║                 GIAI ĐOẠN 5 - OTHER TECHNIQUES                ║
╠═══════════════════════════════════════════════════════════════╣
║                                                               ║
║  📊 WHITE-BOX TESTING:                                        ║
║     • Statement Coverage = % statements executed             ║
║     • Branch Coverage = % decision outcomes tested           ║
║     • Branch > Statement (stronger)                          ║
║     • Best for unit testing                                  ║
║                                                               ║
║  🎯 EXPERIENCE-BASED:                                         ║
║     • Error Guessing: Anticipate errors từ experience       ║
║     • Exploratory: Session-based, learning + testing        ║
║     • Checklist: High-level items, quick & consistent       ║
║                                                               ║
║  🤝 COLLABORATION-BASED:                                      ║
║     • User Stories: As a [role], I want [feature]...        ║
║     • INVEST: Independent, Negotiable, Valuable, etc.        ║
║     • AC: Given-When-Then format                             ║
║     • ATDD: Define tests → Implement → Pass → Refactor      ║
║                                                               ║
║  💡 KEY INSIGHT:                                              ║
║     Combine tất cả techniques để achieve best coverage:      ║
║     • Formal (Black-box, White-box) = Systematic            ║
║     • Experience-based = Creative bug finding                ║
║     • Collaboration = Clear requirements                     ║
║                                                               ║
╚═══════════════════════════════════════════════════════════════╝
```

---

**Version**: 1.0.0
**Last Updated**: November 2025
