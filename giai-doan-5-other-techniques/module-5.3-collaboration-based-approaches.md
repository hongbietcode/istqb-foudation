# MODULE 5.3: COLLABORATION-BASED APPROACHES

**Thời lượng**: 3-4 giờ | **Độ khó**: ⭐⭐

---

## MỤC TIÊU HỌC TẬP

Sau khi hoàn thành module này, bạn sẽ:

| ID | Mục tiêu | Level |
|----|----------|-------|
| FL-4.5.1 | Viết user story với 3 C's | K3 |
| FL-4.5.2 | Sử dụng INVEST criteria | K3 |
| FL-4.5.3 | Viết acceptance criteria (Given-When-Then) | K3 |
| FL-4.5.4 | Giải thích ATDD process | K2 |

---

## 1. COLLABORATION-BASED APPROACHES

### 1.1. Tổng Quan

```
╔═══════════════════════════════════════════════════════════════╗
║          COLLABORATION-BASED TEST APPROACHES                  ║
╠═══════════════════════════════════════════════════════════════╣
║                                                               ║
║  📖 ĐỊNH NGHĨA:                                               ║
║     Test approaches tập trung vào COLLABORATION giữa         ║
║     các stakeholders để tạo test conditions                  ║
║                                                               ║
║  👥 STAKEHOLDERS:                                             ║
║     • Business representatives (PO, BA)                      ║
║     • Developers                                             ║
║     • Testers                                                ║
║     • Users                                                  ║
║                                                               ║
║  🎯 MỤC ĐÍCH:                                                 ║
║     • SHARED UNDERSTANDING của requirements                  ║
║     • Define acceptance criteria TOGETHER                    ║
║     • Prevent misunderstandings                              ║
║     • Build quality in                                       ║
║                                                               ║
║  🔧 TECHNIQUES:                                               ║
║     1. User Stories (3 C's)                                  ║
║     2. INVEST Criteria                                       ║
║     3. Acceptance Criteria (Given-When-Then)                 ║
║     4. ATDD (Acceptance Test-Driven Development)             ║
║                                                               ║
║  ✅ LỢI ÍCH:                                                  ║
║     • Reduce defects (clear requirements)                    ║
║     • Faster feedback                                        ║
║     • Better team alignment                                  ║
║     • Living documentation                                   ║
║                                                               ║
╚═══════════════════════════════════════════════════════════════╝
```

---

## 2. USER STORIES

### 2.1. User Story Là Gì?

```
╔═══════════════════════════════════════════════════════════════╗
║                      USER STORY                               ║
╠═══════════════════════════════════════════════════════════════╣
║                                                               ║
║  📖 ĐỊNH NGHĨA:                                               ║
║     Short, simple description của feature từ USER PERSPECTIVE║
║                                                               ║
║  📝 FORMAT:                                                   ║
║                                                               ║
║     As a [role],                                             ║
║     I want [feature],                                        ║
║     So that [benefit].                                       ║
║                                                               ║
║  VÍ DỤ:                                                       ║
║     As a Shopee customer,                                    ║
║     I want to save items to wishlist,                        ║
║     So that I can purchase them later.                       ║
║                                                               ║
║  🎯 MỤC ĐÍCH:                                                 ║
║     • Capture WHAT user needs (not HOW to build)             ║
║     • Focus on value to user                                 ║
║     • Enable conversation                                    ║
║                                                               ║
╚═══════════════════════════════════════════════════════════════╝
```

### 2.2. The 3 C's

```
╔═══════════════════════════════════════════════════════════════╗
║                    THE 3 C's OF USER STORIES                  ║
╠═══════════════════════════════════════════════════════════════╣
║                                                               ║
║  📇 1. CARD                                                   ║
║     → User story written on physical/virtual card            ║
║     → SHORT format (As a... I want... So that...)           ║
║     → Placeholder for conversation                           ║
║     → NOT full specification                                 ║
║                                                               ║
║  💬 2. CONVERSATION                                           ║
║     → Discussion giữa team và stakeholders                   ║
║     → Clarify details, ask questions                         ║
║     → Explore edge cases                                     ║
║     → Happens throughout development                         ║
║                                                               ║
║  ✅ 3. CONFIRMATION                                           ║
║     → Acceptance criteria                                    ║
║     → HOW to confirm story is "Done"                         ║
║     → Written as testable conditions                         ║
║     → Basis for acceptance tests                             ║
║                                                               ║
╚═══════════════════════════════════════════════════════════════╝
```

**Ví dụ đầy đủ**:

**CARD**:
```
US-123: Wishlist Management

As a Shopee customer,
I want to save items to my wishlist,
So that I can purchase them later when I have budget.
```

**CONVERSATION** (meeting notes):
```
Q: How many items can be in wishlist?
A: Maximum 100 items

Q: What happens when item out of stock?
A: Show "Out of stock" badge, keep in wishlist

Q: Can user add same item twice?
A: No, show message "Already in wishlist"

Q: Wishlist synced across devices?
A: Yes, if user logged in
```

**CONFIRMATION** (Acceptance Criteria):
```
AC1: User can add item to wishlist from product page
AC2: User can view all wishlist items in "My Wishlist" page
AC3: User can remove item from wishlist
AC4: Wishlist limited to 100 items
AC5: Duplicate items not allowed
AC6: Wishlist persists across sessions (if logged in)
```

---

## 3. INVEST CRITERIA

### 3.1. INVEST Là Gì?

```
╔═══════════════════════════════════════════════════════════════╗
║                    INVEST CRITERIA                            ║
╠═══════════════════════════════════════════════════════════════╣
║                                                               ║
║  📖 ĐỊNH NGHĨA:                                               ║
║     6 characteristics của GOOD user story                    ║
║                                                               ║
║  🔤 I - INDEPENDENT                                           ║
║     → Story không depend on other stories                    ║
║     → Có thể develop theo bất kỳ order nào                  ║
║     → Giảm dependencies, tăng flexibility                    ║
║                                                               ║
║  📏 N - NEGOTIABLE                                            ║
║     → Details có thể negotiate với team                      ║
║     → Không phải fixed contract                              ║
║     → Encourage conversation                                 ║
║                                                               ║
║  💎 V - VALUABLE                                              ║
║     → Deliver value cho user/customer                        ║
║     → Focus on benefits, not technical tasks                 ║
║     → PO có thể explain value                                ║
║                                                               ║
║  📊 E - ESTIMABLE                                             ║
║     → Team có thể estimate effort                            ║
║     → Đủ rõ ràng để size story                              ║
║     → Nếu không estimable → cần refine                      ║
║                                                               ║
║  🐭 S - SMALL                                                 ║
║     → Fit trong 1 sprint/iteration                           ║
║     → Không quá lớn (epic)                                  ║
║     → Có thể complete và demo                                ║
║                                                               ║
║  🧪 T - TESTABLE                                              ║
║     → Có acceptance criteria rõ ràng                         ║
║     → Có thể verify "Done"                                   ║
║     → Pass/Fail criteria                                     ║
║                                                               ║
╚═══════════════════════════════════════════════════════════════╝
```

### 3.2. Ví Dụ: Đánh Giá User Story Theo INVEST

**User Story**:
```
As a Grab driver,
I want to see estimated earnings for each trip,
So that I can decide whether to accept the trip.
```

**Đánh giá INVEST**:

| Criterion | ✅/❌ | Giải thích |
|-----------|-------|------------|
| **I**ndependent | ✅ | Không depend on other stories, có thể develop độc lập |
| **N**egotiable | ✅ | Details (formula, UI) có thể discuss với team |
| **V**aluable | ✅ | Clear value: Driver biết income trước khi accept |
| **E**stimable | ✅ | Team có thể estimate (maybe 3-5 story points) |
| **S**mall | ✅ | Fit trong 1 sprint (2 weeks) |
| **T**estable | ✅ | Có thể write acceptance criteria và test |

**Verdict**: Good user story! ✅

---

**Bad Example**:
```
As a developer,
I want to refactor the database layer,
So that the code is cleaner.
```

**Đánh giá INVEST**:

| Criterion | ✅/❌ | Problem |
|-----------|-------|---------|
| **I**ndependent | ⚠️ | Might affect other features |
| **N**egotiable | ✅ | OK |
| **V**aluable | ❌ | No value to USER (only technical) |
| **E**stimable | ⚠️ | Refactoring scope unclear |
| **S**mall | ❌ | "Refactor database" too big |
| **T**estable | ❌ | How to verify "cleaner code"? |

**Problems**:
- ❌ Not valuable to user (technical task)
- ❌ Too big, unclear scope
- ❌ Not testable

**Better split**:
- Technical tasks nên là subtasks của user-facing stories
- Hoặc create Spike để investigate

---

## 4. ACCEPTANCE CRITERIA

### 4.1. Acceptance Criteria Là Gì?

```
╔═══════════════════════════════════════════════════════════════╗
║                  ACCEPTANCE CRITERIA (AC)                     ║
╠═══════════════════════════════════════════════════════════════╣
║                                                               ║
║  📖 ĐỊNH NGHĨA:                                               ║
║     Conditions mà user story phải satisfy để được "Done"     ║
║                                                               ║
║  🎯 MỤC ĐÍCH:                                                 ║
║     • Define scope của story                                 ║
║     • Shared understanding                                   ║
║     • Basis for testing                                      ║
║     • Definition of "Done"                                   ║
║                                                               ║
║  📝 FORMATS:                                                  ║
║     1. Scenario-based (Given-When-Then)                      ║
║     2. Rule-based (bullet points)                            ║
║                                                               ║
║  ✅ GOOD AC:                                                  ║
║     • Testable (có thể verify)                              ║
║     • Clear (không ambiguous)                                ║
║     • Concise (ngắn gọn)                                    ║
║     • Measurable (có criteria rõ ràng)                      ║
║                                                               ║
╚═══════════════════════════════════════════════════════════════╝
```

### 4.2. Given-When-Then Format

```
╔═══════════════════════════════════════════════════════════════╗
║                  GIVEN-WHEN-THEN FORMAT                       ║
╠═══════════════════════════════════════════════════════════════╣
║                                                               ║
║  📝 STRUCTURE:                                                ║
║                                                               ║
║     GIVEN [precondition/context]                             ║
║     WHEN [action/event]                                      ║
║     THEN [expected outcome]                                  ║
║                                                               ║
║  📖 MEANING:                                                  ║
║     • GIVEN: Initial context, setup                          ║
║     • WHEN: Action user takes                                ║
║     • THEN: Expected result                                  ║
║                                                               ║
║  ✅ LỢI ÍCH:                                                  ║
║     • Structured format                                      ║
║     • Easy to understand                                     ║
║     • Directly maps to test cases                            ║
║     • Supported by BDD tools (Cucumber, SpecFlow)           ║
║                                                               ║
╚═══════════════════════════════════════════════════════════════╝
```

### 4.3. Ví Dụ: Given-When-Then

**User Story**: Login functionality

**Acceptance Criteria**:

**AC1: Successful login**
```gherkin
GIVEN user is on login page
  AND user has valid account (username: "test@email.com", password: "Test@123")
WHEN user enters valid username and password
  AND clicks "Login" button
THEN user is redirected to dashboard
  AND welcome message "Welcome, Test User!" is displayed
```

**AC2: Failed login - Invalid credentials**
```gherkin
GIVEN user is on login page
WHEN user enters invalid username or password
  AND clicks "Login" button
THEN login fails
  AND error message "Invalid username or password" is displayed
  AND user remains on login page
```

**AC3: Account lockout**
```gherkin
GIVEN user has entered wrong password 2 times
WHEN user enters wrong password 3rd time
THEN account is locked for 30 minutes
  AND message "Account locked. Try again in 30 minutes." is displayed
```

**AC4: Password visibility toggle**
```gherkin
GIVEN user is on login page
WHEN user clicks "Show password" icon
THEN password is displayed in plain text
WHEN user clicks icon again
THEN password is hidden (shown as dots)
```

### 4.4. Ví Dụ: Rule-Based Format

**User Story**: Apply discount code

**Acceptance Criteria** (bullet points):

```
✓ User can enter discount code in "Promo code" field
✓ Valid discount code applies discount to order total
✓ Discount amount shown separately in order summary
✓ Invalid discount code shows error "Invalid code"
✓ Expired discount code shows error "Code expired"
✓ Only 1 discount code allowed per order
✓ Discount applies before tax calculation
✓ Discount cannot reduce total below 0
```

### 4.5. Ví Dụ Thực Tế: Grab Booking

**User Story**:
```
As a Grab passenger,
I want to book a ride,
So that I can travel from point A to point B.
```

**Acceptance Criteria (Given-When-Then)**:

**Scenario 1: Successful booking**
```gherkin
GIVEN passenger app is open
  AND passenger location is detected (Nguyen Hue, D1, HCMC)
WHEN passenger enters destination "Ben Thanh Market"
  AND selects "GrabCar" service
  AND confirms booking
THEN system finds nearest driver
  AND shows driver details (name, photo, vehicle, ETA)
  AND booking status is "Finding driver"
```

**Scenario 2: No drivers available**
```gherkin
GIVEN passenger app is open
WHEN passenger tries to book ride
  AND no drivers available in area
THEN message "No drivers available. Please try again." is displayed
  AND booking is not created
```

**Scenario 3: Estimate fare before booking**
```gherkin
GIVEN passenger has entered pickup and destination
WHEN passenger views booking screen
THEN estimated fare range is displayed (e.g., "50,000 - 60,000 VND")
  AND estimated time is displayed (e.g., "15-20 mins")
```

---

## 5. ACCEPTANCE TEST-DRIVEN DEVELOPMENT (ATDD)

### 5.1. ATDD Là Gì?

```
╔═══════════════════════════════════════════════════════════════╗
║        ACCEPTANCE TEST-DRIVEN DEVELOPMENT (ATDD)              ║
╠═══════════════════════════════════════════════════════════════╣
║                                                               ║
║  📖 ĐỊNH NGHĨA:                                               ║
║     Development approach:                                    ║
║     1. Define ACCEPTANCE TESTS trước                         ║
║     2. Develop code để pass tests                            ║
║     3. Acceptance tests = executable specifications          ║
║                                                               ║
║  🔄 ATDD PROCESS:                                             ║
║                                                               ║
║     1. SPECIFICATION WORKSHOP                                ║
║        → PO, Dev, Tester collaborate                         ║
║        → Write user story                                    ║
║        → Define acceptance criteria (Given-When-Then)        ║
║                                                               ║
║     2. CREATE ACCEPTANCE TESTS                               ║
║        → Turn AC into executable tests                       ║
║        → Initially FAIL (feature not built yet)              ║
║                                                               ║
║     3. IMPLEMENT FEATURE                                     ║
║        → Developers code feature                             ║
║        → Guided by acceptance tests                          ║
║                                                               ║
║     4. RUN TESTS                                             ║
║        → Execute acceptance tests                            ║
║        → Tests PASS when feature complete                    ║
║                                                               ║
║     5. REFACTOR                                              ║
║        → Improve code quality                                ║
║        → Tests ensure no regression                          ║
║                                                               ║
║  ✅ LỢI ÍCH:                                                  ║
║     • Clear requirements before coding                       ║
║     • Shared understanding                                   ║
║     • Automated regression suite                             ║
║     • Living documentation                                   ║
║                                                               ║
╚═══════════════════════════════════════════════════════════════╝
```

### 5.2. ATDD vs TDD vs BDD

| Aspect | TDD | ATDD | BDD |
|--------|-----|------|-----|
| **Level** | Unit (code) | Acceptance (feature) | Behavior (user) |
| **Who writes** | Developers | Devs + Testers + PO | Whole team |
| **Language** | Code (tests) | Given-When-Then | Given-When-Then (Gherkin) |
| **Focus** | Internal logic | External behavior | User behavior |
| **Tests** | Unit tests | Acceptance tests | Behavior specs |
| **Tools** | JUnit, pytest | FitNesse, Robot | Cucumber, SpecFlow |

**Relationship**:
- **TDD**: Developer writes unit test → code → refactor (Red-Green-Refactor)
- **ATDD**: Team defines acceptance tests → develop → pass tests
- **BDD**: ATDD + natural language (Gherkin) + focus on behavior

### 5.3. ATDD Workflow

```
┌─────────────────────────────────────────────────────────┐
│         ITERATION / SPRINT START                        │
└────────────────────┬────────────────────────────────────┘
                     │
        ┌────────────▼─────────────┐
        │  1. SPECIFICATION        │
        │     WORKSHOP             │
        │  • PO presents story     │
        │  • Team discusses        │
        │  • Write AC (GWT)        │
        └────────────┬─────────────┘
                     │
        ┌────────────▼─────────────┐
        │  2. CREATE ACCEPTANCE    │
        │     TESTS                │
        │  • Tester writes tests   │
        │  • Initially FAIL (RED)  │
        └────────────┬─────────────┘
                     │
        ┌────────────▼─────────────┐
        │  3. IMPLEMENT FEATURE    │
        │  • Developer codes       │
        │  • Guided by tests       │
        │  • Run tests frequently  │
        └────────────┬─────────────┘
                     │
        ┌────────────▼─────────────┐
        │  4. TESTS PASS (GREEN)   │
        │  • Feature complete      │
        │  • All AC satisfied      │
        └────────────┬─────────────┘
                     │
        ┌────────────▼─────────────┐
        │  5. REFACTOR             │
        │  • Improve code          │
        │  • Tests ensure no       │
        │    regression            │
        └────────────┬─────────────┘
                     │
        ┌────────────▼─────────────┐
        │  DEMO TO STAKEHOLDERS    │
        │  • Show working feature  │
        │  • AC as proof           │
        └──────────────────────────┘
```

### 5.4. Ví Dụ ATDD: Shopping Cart

**1. Specification Workshop**

**User Story**:
```
As a Shopee customer,
I want to add items to cart,
So that I can purchase multiple items together.
```

**Acceptance Criteria (Given-When-Then)**:
```gherkin
Scenario 1: Add item to empty cart
  GIVEN cart is empty
  WHEN customer adds "iPhone 15" to cart
  THEN cart contains 1 item
    AND cart total is 25,000,000 VND

Scenario 2: Add multiple quantities
  GIVEN cart is empty
  WHEN customer adds "iPhone 15" with quantity 2
  THEN cart contains 2 items
    AND cart total is 50,000,000 VND

Scenario 3: Maximum quantity limit
  GIVEN cart is empty
  WHEN customer tries to add "iPhone 15" with quantity 100
  THEN error "Maximum 10 items per product" is shown
    AND cart remains empty
```

**2. Create Acceptance Tests** (using Cucumber/Gherkin)

```gherkin
Feature: Shopping Cart

  Scenario: Add item to empty cart
    Given the cart is empty
    When I add "iPhone 15" to cart
    Then the cart should contain 1 item
    And the cart total should be "25,000,000 VND"

  Scenario: Add multiple quantities
    Given the cart is empty
    When I add "iPhone 15" with quantity 2
    Then the cart should contain 2 items
    And the cart total should be "50,000,000 VND"

  Scenario: Maximum quantity limit
    Given the cart is empty
    When I try to add "iPhone 15" with quantity 100
    Then I should see error "Maximum 10 items per product"
    And the cart should remain empty
```

**Step Definitions** (Code that executes steps):
```javascript
Given('the cart is empty', function() {
  this.cart = new ShoppingCart();
});

When('I add {string} to cart', function(productName) {
  this.product = { name: productName, price: 25000000 };
  this.cart.addItem(this.product);
});

Then('the cart should contain {int} item(s)', function(count) {
  assert.equal(this.cart.itemCount(), count);
});

Then('the cart total should be {string}', function(total) {
  assert.equal(this.cart.total(), total);
});
```

**3. Run Tests** → Initially FAIL (feature not implemented)

**4. Implement Feature**
```javascript
class ShoppingCart {
  constructor() {
    this.items = [];
  }

  addItem(product, quantity = 1) {
    if (quantity > 10) {
      throw new Error("Maximum 10 items per product");
    }
    for (let i = 0; i < quantity; i++) {
      this.items.push(product);
    }
  }

  itemCount() {
    return this.items.length;
  }

  total() {
    return this.items.reduce((sum, item) => sum + item.price, 0);
  }
}
```

**5. Run Tests Again** → Tests PASS ✅

**6. Refactor** → Improve code, tests ensure no regression

---

## 6. BEST PRACTICES

```
╔═══════════════════════════════════════════════════════════════╗
║                     BEST PRACTICES                            ║
╠═══════════════════════════════════════════════════════════════╣
║                                                               ║
║  ✅ USER STORIES:                                             ║
║     • Keep them SMALL (fit in 1 sprint)                      ║
║     • Focus on USER VALUE, not technical details             ║
║     • Use INVEST criteria to validate                        ║
║     • Encourage conversation (3 C's)                         ║
║                                                               ║
║  ✅ ACCEPTANCE CRITERIA:                                      ║
║     • Write BEFORE implementation                            ║
║     • Make them TESTABLE                                     ║
║     • Use Given-When-Then for clarity                        ║
║     • Cover happy path + edge cases                          ║
║     • Review with whole team                                 ║
║                                                               ║
║  ✅ ATDD:                                                     ║
║     • Start with Specification Workshop                      ║
║     • Collaborate: PO + Dev + Tester                         ║
║     • Automate acceptance tests                              ║
║     • Use tests as living documentation                      ║
║     • Keep tests maintainable                                ║
║                                                               ║
║  ✅ COLLABORATION:                                            ║
║     • Three Amigos meetings (PO, Dev, Tester)                ║
║     • Shared understanding là KEY                            ║
║     • Ask questions early                                    ║
║     • Document decisions                                     ║
║                                                               ║
╚═══════════════════════════════════════════════════════════════╝
```

---

## 7. CÂU HỎI ÔN TẬP

### Câu 1 (K2)
3 C's của user stories là gì?

A. Code, Commit, Check
B. Card, Conversation, Confirmation
C. Create, Collaborate, Complete
D. Context, Condition, Consequence

<details>
<summary>Đáp án</summary>

**B. Card, Conversation, Confirmation**

Card: Written story
Conversation: Discussion with team
Confirmation: Acceptance criteria
</details>

---

### Câu 2 (K2)
Trong INVEST, "V" stands for?

A. Verified
B. Validated
C. Valuable
D. Variable

<details>
<summary>Đáp án</summary>

**C. Valuable**

User story phải deliver value cho user/customer.
</details>

---

### Câu 3 (K3)
Given-When-Then format, "Given" represents gì?

A. Expected result
B. Action user takes
C. Precondition/context
D. Test data

<details>
<summary>Đáp án</summary>

**C. Precondition/context**

GIVEN: Initial state/context
WHEN: Action
THEN: Expected outcome
</details>

---

### Câu 4 (K2)
ATDD process bắt đầu với bước nào?

A. Write code
B. Write unit tests
C. Define acceptance criteria với team
D. Deploy to production

<details>
<summary>Đáp án</summary>

**C. Define acceptance criteria với team**

ATDD starts với Specification Workshop - team collaborates để define acceptance criteria.
</details>

---

### Câu 5 (K2)
User story nào vi phạm INVEST "V" (Valuable)?

A. As a customer, I want to view order history
B. As a user, I want to reset my password
C. As a developer, I want to refactor code
D. As an admin, I want to manage users

<details>
<summary>Đáp án</summary>

**C. As a developer, I want to refactor code**

Không valuable cho user/customer - chỉ technical benefit.
</details>

---

### Câu 6 (K2)
Acceptance criteria nên được written khi nào?

A. After implementation
B. During testing phase
C. Before implementation starts
D. After deployment

<details>
<summary>Đáp án</summary>

**C. Before implementation starts**

AC define "Done" criteria, nên written trước khi code để shared understanding.
</details>

---

## 8. CHECKLIST TỰ ĐÁNH GIÁ

### User Stories
- [ ] Viết được user story theo format (As a... I want... So that...)
- [ ] Hiểu 3 C's (Card, Conversation, Confirmation)
- [ ] Có thể apply 3 C's trong practice
- [ ] Phân biệt good vs bad user stories

### INVEST Criteria
- [ ] Biết 6 criteria của INVEST
- [ ] Có thể evaluate user story theo INVEST
- [ ] Hiểu tại sao mỗi criterion quan trọng
- [ ] Biết improve user story không meet INVEST

### Acceptance Criteria
- [ ] Viết được AC theo Given-When-Then format
- [ ] Hiểu difference giữa scenario-based vs rule-based AC
- [ ] Cover được happy path + edge cases
- [ ] AC testable và clear

### ATDD
- [ ] Hiểu ATDD process (5 steps)
- [ ] Phân biệt TDD vs ATDD vs BDD
- [ ] Biết lợi ích của ATDD
- [ ] Hiểu vai trò của mỗi team member trong ATDD

---

## TỔNG KẾT

```
╔═══════════════════════════════════════════════════════════════╗
║                    KEY TAKEAWAYS                              ║
╠═══════════════════════════════════════════════════════════════╣
║                                                               ║
║  1. Collaboration-based = Cùng nhau define requirements      ║
║                                                               ║
║  2. User Stories:                                            ║
║     → Format: As a [role], I want [feature], So that [ben]  ║
║     → 3 C's: Card, Conversation, Confirmation                ║
║                                                               ║
║  3. INVEST Criteria:                                         ║
║     → Independent, Negotiable, Valuable                      ║
║     → Estimable, Small, Testable                             ║
║                                                               ║
║  4. Acceptance Criteria:                                     ║
║     → Define "Done"                                          ║
║     → Given-When-Then format                                 ║
║     → Testable, Clear, Concise                               ║
║                                                               ║
║  5. ATDD Process:                                            ║
║     → Workshop → Write tests → Implement → Pass → Refactor  ║
║     → Whole team collaboration                               ║
║                                                               ║
║  6. Benefits:                                                ║
║     → Shared understanding                                   ║
║     → Prevent misunderstandings                              ║
║     → Living documentation                                   ║
║                                                               ║
╚═══════════════════════════════════════════════════════════════╝
```

---

**Tiếp theo**: [Bài Tập Giai Đoạn 5](./bai-tap-giai-doan-5.md)

---

**Version**: 1.0.0
**Last Updated**: November 2025
