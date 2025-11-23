# MODULE 3.3: TEST TYPES (CÁC LOẠI KIỂM THỬ)

**Thời lượng**: 3-4 giờ | **Độ khó**: ⭐⭐

---

## MỤC TIÊU HỌC TẬP (Learning Objectives)

Sau khi hoàn thành module này, bạn sẽ:

| ID | Mục tiêu | Level |
|----|----------|-------|
| FL-2.3.1 | Phân biệt Functional Testing và Non-functional Testing | K2 |
| FL-2.3.2 | Xác định các đặc tính non-functional | K1 |
| FL-2.3.3 | Phân biệt Black-box và White-box Testing | K2 |
| FL-2.3.4 | Phân biệt Confirmation Testing và Regression Testing | K2 |

---

## 1. TỔNG QUAN VỀ TEST TYPES

### 1.1. Test Types Là Gì?

> **Test Type** là cách phân loại các hoạt động testing dựa trên **mục tiêu** cụ thể mà test hướng tới.

```
╔═══════════════════════════════════════════════════════════════╗
║                      TEST TYPES                               ║
╠═══════════════════════════════════════════════════════════════╣
║                                                               ║
║           Phân loại theo MỤC TIÊU TEST:                       ║
║           ────────────────────────────                        ║
║                                                               ║
║   ┌─────────────────┐     ┌─────────────────┐                ║
║   │  FUNCTIONAL     │     │ NON-FUNCTIONAL  │                ║
║   │  TESTING        │     │    TESTING      │                ║
║   │                 │     │                 │                ║
║   │ "WHAT" system   │     │ "HOW WELL"      │                ║
║   │    does         │     │ system works    │                ║
║   └─────────────────┘     └─────────────────┘                ║
║                                                               ║
║           Phân loại theo CÁCH TIẾP CẬN:                       ║
║           ─────────────────────────────                       ║
║                                                               ║
║   ┌─────────────────┐     ┌─────────────────┐                ║
║   │   BLACK-BOX     │     │   WHITE-BOX     │                ║
║   │   TESTING       │     │   TESTING       │                ║
║   │                 │     │                 │                ║
║   │ Focus on        │     │ Focus on        │                ║
║   │ behavior        │     │ structure       │                ║
║   └─────────────────┘     └─────────────────┘                ║
║                                                               ║
║           Phân loại theo MỤC ĐÍCH:                            ║
║           ────────────────────────                            ║
║                                                               ║
║   ┌─────────────────┐     ┌─────────────────┐                ║
║   │  CONFIRMATION   │     │   REGRESSION    │                ║
║   │   TESTING       │     │    TESTING      │                ║
║   │                 │     │                 │                ║
║   │ Verify fix      │     │ Verify no       │                ║
║   │   works         │     │ new bugs        │                ║
║   └─────────────────┘     └─────────────────┘                ║
║                                                               ║
╚═══════════════════════════════════════════════════════════════╝
```

---

## 2. FUNCTIONAL TESTING

### 2.1. Định Nghĩa

> **Functional Testing** kiểm tra **WHAT** (cái gì) mà hệ thống làm - tức là các **chức năng** và **hành vi** của hệ thống.

```
╔═══════════════════════════════════════════════════════════════╗
║                   FUNCTIONAL TESTING                          ║
╠═══════════════════════════════════════════════════════════════╣
║                                                               ║
║  📋 ĐỊNH NGHĨA:                                               ║
║     Kiểm tra hệ thống LÀM GÌ (what it does)                  ║
║     Dựa trên FUNCTIONAL REQUIREMENTS                         ║
║                                                               ║
║  🎯 MỤC TIÊU:                                                 ║
║     • Verify hệ thống làm đúng những gì yêu cầu             ║
║     • Kiểm tra inputs → outputs                              ║
║     • Verify business logic                                  ║
║                                                               ║
║  📚 TEST BASIS:                                               ║
║     • Functional requirements                                ║
║     • User stories                                            ║
║     • Use cases                                               ║
║     • Business rules                                          ║
║                                                               ║
║  💡 VÍ DỤ:                                                    ║
║     • Login function works correctly                         ║
║     • Cart calculation is accurate                           ║
║     • Order can be placed successfully                       ║
║     • Payment is processed                                    ║
║                                                               ║
╚═══════════════════════════════════════════════════════════════╝
```

### 2.2. Ví Dụ Functional Testing

```
EXAMPLE: E-commerce Checkout Function
═══════════════════════════════════════════════════════════════

FUNCTIONAL REQUIREMENT:
"User should be able to checkout and pay for items in cart"

FUNCTIONAL TEST CASES:
───────────────────────────────────────────────────────────────
TC-001: Checkout with valid credit card
        Input: Valid cart, valid card details
        Expected: Order created, payment processed, confirmation shown

TC-002: Checkout with empty cart
        Input: Empty cart
        Expected: Error "Cart is empty"

TC-003: Checkout with out-of-stock item
        Input: Cart with item that went out of stock
        Expected: Warning shown, item removed from cart

TC-004: Calculate order total correctly
        Input: 3 items × 100,000đ + 10% discount + 30,000đ shipping
        Expected: Total = 300,000 - 30,000 + 30,000 = 300,000đ
```

---

## 3. NON-FUNCTIONAL TESTING

### 3.1. Định Nghĩa

> **Non-functional Testing** kiểm tra **HOW WELL** (tốt như thế nào) mà hệ thống hoạt động - tức là các **đặc tính chất lượng** của hệ thống.

```
╔═══════════════════════════════════════════════════════════════╗
║                 NON-FUNCTIONAL TESTING                        ║
╠═══════════════════════════════════════════════════════════════╣
║                                                               ║
║  📋 ĐỊNH NGHĨA:                                               ║
║     Kiểm tra hệ thống HOẠT ĐỘNG TỐT như thế nào              ║
║     Dựa trên NON-FUNCTIONAL REQUIREMENTS                     ║
║                                                               ║
║  🎯 MỤC TIÊU:                                                 ║
║     • Verify performance, security, usability                ║
║     • Kiểm tra quality characteristics                       ║
║     • Đảm bảo system đáp ứng quality standards              ║
║                                                               ║
║  📚 TEST BASIS:                                               ║
║     • Non-functional requirements                             ║
║     • SLAs (Service Level Agreements)                        ║
║     • ISO 25010 quality characteristics                      ║
║                                                               ║
║  💡 VÍ DỤ:                                                    ║
║     • Page loads trong 2 giây (Performance)                  ║
║     • Supports 10,000 concurrent users (Scalability)         ║
║     • Data is encrypted (Security)                           ║
║     • Easy to use for beginners (Usability)                  ║
║                                                               ║
╚═══════════════════════════════════════════════════════════════╝
```

### 3.2. ISO 25010 Quality Characteristics

```
╔═══════════════════════════════════════════════════════════════╗
║          ISO 25010 - PRODUCT QUALITY MODEL                    ║
╠═══════════════════════════════════════════════════════════════╣
║                                                               ║
║  1️⃣ FUNCTIONAL SUITABILITY                                    ║
║     • Functional completeness                                ║
║     • Functional correctness                                 ║
║     • Functional appropriateness                             ║
║                                                               ║
║  2️⃣ PERFORMANCE EFFICIENCY                                    ║
║     • Time behavior (response time, throughput)              ║
║     • Resource utilization (CPU, memory, disk)               ║
║     • Capacity (max users, transactions)                     ║
║                                                               ║
║  3️⃣ COMPATIBILITY                                             ║
║     • Co-existence (run alongside other software)            ║
║     • Interoperability (exchange data with others)           ║
║                                                               ║
║  4️⃣ USABILITY                                                 ║
║     • Appropriateness recognizability                        ║
║     • Learnability (easy to learn)                           ║
║     • Operability (easy to use)                              ║
║     • User error protection                                  ║
║     • User interface aesthetics                              ║
║     • Accessibility                                          ║
║                                                               ║
║  5️⃣ RELIABILITY                                               ║
║     • Maturity (frequency of failures)                       ║
║     • Availability (uptime)                                  ║
║     • Fault tolerance (handle errors gracefully)             ║
║     • Recoverability (recover from failures)                 ║
║                                                               ║
║  6️⃣ SECURITY                                                  ║
║     • Confidentiality (protect data access)                  ║
║     • Integrity (prevent unauthorized modification)          ║
║     • Non-repudiation (prove actions occurred)               ║
║     • Accountability (trace actions to entity)               ║
║     • Authenticity (prove identity)                          ║
║                                                               ║
║  7️⃣ MAINTAINABILITY                                           ║
║     • Modularity                                             ║
║     • Reusability                                            ║
║     • Analysability                                          ║
║     • Modifiability                                          ║
║     • Testability                                            ║
║                                                               ║
║  8️⃣ PORTABILITY                                               ║
║     • Adaptability (adapt to different environments)         ║
║     • Installability                                         ║
║     • Replaceability                                         ║
║                                                               ║
╚═══════════════════════════════════════════════════════════════╝
```

### 3.3. Các Loại Non-functional Testing

```
╔═══════════════════════════════════════════════════════════════╗
║            COMMON NON-FUNCTIONAL TEST TYPES                   ║
╠═══════════════════════════════════════════════════════════════╣
║                                                               ║
║  🚀 PERFORMANCE TESTING                                       ║
║  ├── Load Testing: Test under expected load                  ║
║  ├── Stress Testing: Test beyond capacity                    ║
║  ├── Spike Testing: Test sudden load increase                ║
║  ├── Endurance Testing: Test over extended time              ║
║  └── Scalability Testing: Test growth handling               ║
║                                                               ║
║  🔒 SECURITY TESTING                                          ║
║  ├── Vulnerability scanning                                   ║
║  ├── Penetration testing                                      ║
║  ├── Authentication testing                                   ║
║  └── Authorization testing                                    ║
║                                                               ║
║  👤 USABILITY TESTING                                         ║
║  ├── User experience testing                                  ║
║  ├── Accessibility testing (WCAG)                            ║
║  └── UI/UX evaluation                                        ║
║                                                               ║
║  📱 COMPATIBILITY TESTING                                     ║
║  ├── Browser compatibility                                    ║
║  ├── OS compatibility                                        ║
║  └── Device compatibility                                     ║
║                                                               ║
║  ⚡ RELIABILITY TESTING                                       ║
║  ├── Recovery testing                                         ║
║  └── Failover testing                                         ║
║                                                               ║
╚═══════════════════════════════════════════════════════════════╝
```

### 3.4. Ví Dụ Non-functional Testing

```
EXAMPLE: VNPay Mobile App - Non-functional Tests
═══════════════════════════════════════════════════════════════

🚀 PERFORMANCE TESTING:
───────────────────────────────────────────────────────────────
Test: Response time for money transfer
Requirement: Complete trong 3 giây
Test Steps:
1. Initiate transfer với 10,000,000 VND
2. Measure time from "Confirm" click to "Success" message
Result: 2.1 seconds ✓ PASSED

Test: Load test với 5,000 concurrent users
Requirement: System handles 5,000 users without degradation
Result: Average response time 2.5s, no errors ✓ PASSED

🔒 SECURITY TESTING:
───────────────────────────────────────────────────────────────
Test: SQL Injection on login
Requirement: System rejects malicious input
Test Steps:
1. Enter "admin' OR '1'='1" in username field
2. Submit form
Result: Login rejected, input sanitized ✓ PASSED

Test: Session timeout
Requirement: Session expires after 10 minutes inactivity
Result: Session expired at 10:02 ✓ PASSED

👤 USABILITY TESTING:
───────────────────────────────────────────────────────────────
Test: New user can complete transfer in first attempt
Requirement: 80% of new users succeed without help
Test Participants: 20 first-time users
Result: 18/20 (90%) completed successfully ✓ PASSED

📱 COMPATIBILITY TESTING:
───────────────────────────────────────────────────────────────
Test: App works on iOS 16+ và Android 12+
Devices tested:
- iPhone 14 Pro (iOS 17) ✓
- iPhone 12 (iOS 16) ✓
- Samsung S23 (Android 13) ✓
- Xiaomi 13 (Android 12) ✓
Result: All devices compatible ✓ PASSED
```

### 3.5. Functional vs Non-functional Testing

| Aspect | Functional | Non-functional |
|--------|------------|----------------|
| **Focus** | WHAT system does | HOW WELL it works |
| **Question** | "Does it work?" | "How fast/secure/usable?" |
| **Basis** | Requirements, user stories | SLAs, quality standards |
| **Measurable** | Pass/Fail | Metrics (seconds, %, etc.) |
| **Example** | Login works | Login completes in 2s |
| **Tools** | Selenium, manual | JMeter, LoadRunner |

---

## 4. BLACK-BOX TESTING

### 4.1. Định Nghĩa

> **Black-box Testing** kiểm tra hệ thống mà KHÔNG biết internal structure/implementation. Focus vào inputs và outputs.

```
╔═══════════════════════════════════════════════════════════════╗
║                   BLACK-BOX TESTING                           ║
╠═══════════════════════════════════════════════════════════════╣
║                                                               ║
║       INPUT                                     OUTPUT        ║
║         │                                         ▲           ║
║         │     ┌─────────────────────────┐        │           ║
║         │     │                         │        │           ║
║         └────►│    BLACK BOX            │────────┘           ║
║               │    (Unknown inside)     │                    ║
║               │                         │                    ║
║               └─────────────────────────┘                    ║
║                                                               ║
║  📋 ĐỊNH NGHĨA:                                               ║
║     Test dựa trên SPECIFICATIONS, không cần biết code        ║
║     Tester không thấy/không cần biết internal logic         ║
║                                                               ║
║  🎯 FOCUS:                                                    ║
║     • Input → Output behavior                                ║
║     • Functional requirements                                ║
║     • User perspective                                       ║
║                                                               ║
║  👤 THƯỜNG DO AI THỰC HIỆN:                                   ║
║     • Testers (không cần coding skills)                      ║
║     • Business analysts                                      ║
║     • End users                                              ║
║                                                               ║
║  🔧 TECHNIQUES:                                               ║
║     • Equivalence Partitioning                               ║
║     • Boundary Value Analysis                                ║
║     • Decision Table Testing                                 ║
║     • State Transition Testing                               ║
║                                                               ║
╚═══════════════════════════════════════════════════════════════╝
```

### 4.2. Ví Dụ Black-box Testing

```
EXAMPLE: Login Function - Black-box Test
═══════════════════════════════════════════════════════════════

SPECIFICATION:
- Email: Valid email format required
- Password: 8-20 characters, must include number và letter
- Result: Success → Dashboard, Failure → Error message

BLACK-BOX TEST CASES:
(Tester không cần biết code, chỉ cần biết spec)
───────────────────────────────────────────────────────────────
TC  │ Email              │ Password      │ Expected
────┼────────────────────┼───────────────┼─────────────────────
01  │ user@example.com   │ Pass1234      │ Login success
02  │ user@example.com   │ wrongpass     │ "Invalid credentials"
03  │ invalidemail       │ Pass1234      │ "Invalid email format"
04  │ (empty)            │ Pass1234      │ "Email required"
05  │ user@example.com   │ (empty)       │ "Password required"
06  │ user@example.com   │ 12345678      │ "Password must include letter"
07  │ user@example.com   │ abcdefgh      │ "Password must include number"
```

---

## 5. WHITE-BOX TESTING

### 5.1. Định Nghĩa

> **White-box Testing** (Structural Testing) kiểm tra hệ thống DỰA TRÊN knowledge về internal structure/code.

```
╔═══════════════════════════════════════════════════════════════╗
║                   WHITE-BOX TESTING                           ║
╠═══════════════════════════════════════════════════════════════╣
║                                                               ║
║       INPUT                                     OUTPUT        ║
║         │                                         ▲           ║
║         │     ┌─────────────────────────┐        │           ║
║         │     │ if (x > 0) {            │        │           ║
║         └────►│   return x * 2;  ←──────┼────────┘           ║
║               │ } else {                │                    ║
║               │   return 0;  ←──────────┼───                 ║
║               │ }                       │   Test cả 2 paths  ║
║               └─────────────────────────┘                    ║
║                                                               ║
║  📋 ĐỊNH NGHĨA:                                               ║
║     Test dựa trên CODE STRUCTURE, cần biết implementation   ║
║     Tester có thể thấy và hiểu code                        ║
║                                                               ║
║  🎯 FOCUS:                                                    ║
║     • Code coverage (statements, branches)                   ║
║     • Internal logic paths                                   ║
║     • Data flow                                              ║
║                                                               ║
║  👤 THƯỜNG DO AI THỰC HIỆN:                                   ║
║     • Developers                                             ║
║     • Technical testers (có coding skills)                   ║
║                                                               ║
║  🔧 TECHNIQUES:                                               ║
║     • Statement Coverage                                     ║
║     • Branch Coverage (Decision Coverage)                    ║
║     • Path Coverage                                          ║
║                                                               ║
╚═══════════════════════════════════════════════════════════════╝
```

### 5.2. Statement Coverage và Branch Coverage

```
╔═══════════════════════════════════════════════════════════════╗
║               STATEMENT vs BRANCH COVERAGE                    ║
╠═══════════════════════════════════════════════════════════════╣
║                                                               ║
║  CODE EXAMPLE:                                                ║
║  ─────────────                                               ║
║  1│ function getDiscount(amount, isMember) {                 ║
║  2│   let discount = 0;                    ← Statement 1     ║
║  3│   if (amount > 1000) {                 ← Branch A        ║
║  4│     discount = 10;                     ← Statement 2     ║
║  5│   }                                                      ║
║  6│   if (isMember) {                      ← Branch B        ║
║  7│     discount += 5;                     ← Statement 3     ║
║  8│   }                                                      ║
║  9│   return discount;                     ← Statement 4     ║
║ 10│ }                                                        ║
║                                                               ║
║  ═══════════════════════════════════════════════════════════  ║
║                                                               ║
║  STATEMENT COVERAGE:                                          ║
║  "Execute mỗi statement ít nhất 1 lần"                       ║
║                                                               ║
║  Test: getDiscount(2000, true)                               ║
║  → Line 2 ✓, Line 4 ✓, Line 7 ✓, Line 9 ✓                   ║
║  → 4/4 statements = 100% statement coverage                  ║
║                                                               ║
║  ═══════════════════════════════════════════════════════════  ║
║                                                               ║
║  BRANCH COVERAGE:                                             ║
║  "Execute mỗi branch (true/false) ít nhất 1 lần"            ║
║                                                               ║
║  Branch A: amount > 1000 (True/False)                        ║
║  Branch B: isMember (True/False)                             ║
║                                                               ║
║  Tests needed:                                                ║
║  Test 1: getDiscount(2000, true)  → A=T, B=T                ║
║  Test 2: getDiscount(500, false)  → A=F, B=F                ║
║  → 4/4 branches = 100% branch coverage                       ║
║                                                               ║
╚═══════════════════════════════════════════════════════════════╝
```

### 5.3. Black-box vs White-box Testing

| Aspect | Black-box | White-box |
|--------|-----------|-----------|
| **Knowledge** | No internal knowledge | Full code access |
| **Focus** | Behavior, functionality | Code structure, paths |
| **Tester** | Testers, users | Developers, tech testers |
| **Test basis** | Requirements, specs | Source code |
| **Techniques** | EP, BVA, Decision Table | Statement, Branch coverage |
| **When** | Any test level | Mainly component level |
| **Advantage** | User perspective | Thorough code testing |
| **Disadvantage** | May miss code paths | Doesn't test from user view |

---

## 6. CONFIRMATION TESTING VÀ REGRESSION TESTING

### 6.1. Confirmation Testing (Re-testing)

> **Confirmation Testing** kiểm tra rằng defect đã được FIX thành công.

```
╔═══════════════════════════════════════════════════════════════╗
║                 CONFIRMATION TESTING                          ║
╠═══════════════════════════════════════════════════════════════╣
║                                                               ║
║  📋 ĐỊNH NGHĨA:                                               ║
║     Chạy lại SAME TEST(s) đã tìm ra defect                  ║
║     Verify rằng defect đã được fix                          ║
║                                                               ║
║  🔄 PROCESS:                                                  ║
║                                                               ║
║     1. Test fails → Defect reported                          ║
║            ↓                                                  ║
║     2. Developer fixes defect                                 ║
║            ↓                                                  ║
║     3. Tester runs SAME test again                           ║
║            ↓                                                  ║
║     4. Test passes → Defect confirmed fixed ✓                ║
║        OR                                                     ║
║        Test fails → Defect still exists ✗                    ║
║                                                               ║
║  💡 VÍ DỤ:                                                    ║
║     TC-LOGIN-003 failed: "Login fails với valid email"       ║
║     → Developer fixed login validation                       ║
║     → Tester re-runs TC-LOGIN-003                            ║
║     → TC-LOGIN-003 passes → Defect fixed ✓                   ║
║                                                               ║
╚═══════════════════════════════════════════════════════════════╝
```

### 6.2. Regression Testing

> **Regression Testing** kiểm tra rằng changes (fixes, new features) KHÔNG phá vỡ existing functionality.

```
╔═══════════════════════════════════════════════════════════════╗
║                  REGRESSION TESTING                           ║
╠═══════════════════════════════════════════════════════════════╣
║                                                               ║
║  📋 ĐỊNH NGHĨA:                                               ║
║     Chạy EXISTING tests sau khi có changes                   ║
║     Verify không có unintended side effects                  ║
║                                                               ║
║  🔄 KHI NÀO CẦN REGRESSION:                                   ║
║     • Sau khi fix defect                                     ║
║     • Sau khi add new feature                                ║
║     • Sau khi refactor code                                  ║
║     • Sau khi environment changes                            ║
║     • Sau khi integrate new component                        ║
║                                                               ║
║  📦 REGRESSION TEST SUITE:                                    ║
║     Tập hợp tests được chọn để chạy mỗi khi có change        ║
║     Thường bao gồm:                                          ║
║     • Critical functionality tests                           ║
║     • Core business flow tests                               ║
║     • Previously failed tests                                ║
║     • Tests related to changed areas                         ║
║                                                               ║
║  💡 VÍ DỤ:                                                    ║
║     Developer fixed login bug                                ║
║     → Run confirmation test for login (TC-LOGIN-003)         ║
║     → ALSO run regression tests:                             ║
║       • TC-CART-001: Add to cart still works?               ║
║       • TC-PAYMENT-001: Payment still works?                ║
║       • TC-PROFILE-001: Profile update still works?         ║
║                                                               ║
╚═══════════════════════════════════════════════════════════════╝
```

### 6.3. Confirmation vs Regression Testing

```
╔═══════════════════════════════════════════════════════════════╗
║         CONFIRMATION vs REGRESSION TESTING                    ║
╠═══════════════════════════════════════════════════════════════╣
║                                                               ║
║  SCENARIO: Developer fixes Login Bug (BUG-123)               ║
║                                                               ║
║  ┌─────────────────────────────────────────────────────────┐ ║
║  │                                                         │ ║
║  │  CONFIRMATION TESTING:                                  │ ║
║  │  ─────────────────────                                  │ ║
║  │  Run: TC-LOGIN-003 (test that found BUG-123)           │ ║
║  │  Purpose: Verify BUG-123 is fixed                      │ ║
║  │  Result: PASS → Bug confirmed fixed ✓                  │ ║
║  │                                                         │ ║
║  └─────────────────────────────────────────────────────────┘ ║
║                         +                                     ║
║  ┌─────────────────────────────────────────────────────────┐ ║
║  │                                                         │ ║
║  │  REGRESSION TESTING:                                    │ ║
║  │  ─────────────────────                                  │ ║
║  │  Run: Regression test suite                             │ ║
║  │  Tests: TC-CART-001, TC-PAYMENT-001, TC-PROFILE-001... │ ║
║  │  Purpose: Verify fix didn't break other features       │ ║
║  │  Result: All PASS → No regression ✓                    │ ║
║  │                                                         │ ║
║  └─────────────────────────────────────────────────────────┘ ║
║                                                               ║
╚═══════════════════════════════════════════════════════════════╝
```

| Aspect | Confirmation Testing | Regression Testing |
|--------|---------------------|-------------------|
| **Purpose** | Verify defect is fixed | Verify no new bugs introduced |
| **Scope** | Specific test(s) for defect | Broader set of existing tests |
| **When** | After defect fix | After any change |
| **Test source** | Test that found defect | Regression test suite |
| **Question** | "Is the bug fixed?" | "Did we break anything else?" |

### 6.4. Regression Testing và Automation

```
╔═══════════════════════════════════════════════════════════════╗
║          REGRESSION TESTING & AUTOMATION                      ║
╠═══════════════════════════════════════════════════════════════╣
║                                                               ║
║  🤖 TẠI SAO AUTOMATE REGRESSION TESTS?                        ║
║                                                               ║
║  • Regression tests run FREQUENTLY (every build/release)     ║
║  • Manual regression is TIME-CONSUMING và BORING            ║
║  • Same tests run REPEATEDLY                                 ║
║  • Automation gives FAST feedback                            ║
║  • Automation is CONSISTENT (no human errors)                ║
║                                                               ║
║  📊 REGRESSION TEST SUITE GROWTH:                             ║
║                                                               ║
║  Sprint 1:  ████                    (20 tests)               ║
║  Sprint 5:  ████████████            (60 tests)               ║
║  Sprint 10: ████████████████████    (100 tests)              ║
║  Sprint 20: ████████████████████████████████  (200 tests)    ║
║                                                               ║
║  → Suite grows over time                                      ║
║  → Manual execution becomes impractical                      ║
║  → Automation is ESSENTIAL for regression                    ║
║                                                               ║
║  🎯 WHAT TO AUTOMATE:                                         ║
║  ✓ Critical business flows                                   ║
║  ✓ Stable features (rarely change)                          ║
║  ✓ Data-driven tests                                         ║
║  ✓ Frequently executed tests                                 ║
║                                                               ║
║  ❌ WHAT NOT TO AUTOMATE:                                     ║
║  ✗ Tests for features still changing                        ║
║  ✗ One-time tests                                            ║
║  ✗ Exploratory testing                                       ║
║  ✗ Usability testing                                         ║
║                                                               ║
╚═══════════════════════════════════════════════════════════════╝
```

---

## 7. MAINTENANCE TESTING

### 7.1. Định Nghĩa

> **Maintenance Testing** là testing cho một hệ thống **đã tồn tại** khi có modifications, migrations, hoặc retirement.

```
╔═══════════════════════════════════════════════════════════════╗
║                   MAINTENANCE TESTING                         ║
╠═══════════════════════════════════════════════════════════════╣
║                                                               ║
║  🔄 TRIGGERS (Khi nào cần Maintenance Testing):               ║
║                                                               ║
║  1. MODIFICATIONS                                             ║
║     • Bug fixes                                               ║
║     • Enhancements (new features)                            ║
║     • Hot fixes                                               ║
║                                                               ║
║  2. MIGRATIONS                                                ║
║     • Platform migration (Windows → Linux)                   ║
║     • Database migration (Oracle → PostgreSQL)               ║
║     • Cloud migration (On-prem → AWS)                        ║
║                                                               ║
║  3. RETIREMENT                                                ║
║     • System being decommissioned                            ║
║     • Data migration/archival testing                        ║
║                                                               ║
║  📋 SCOPE OF MAINTENANCE TESTING:                             ║
║                                                               ║
║  • Testing the CHANGED areas                                  ║
║  • REGRESSION testing for unchanged areas                    ║
║  • IMPACT ANALYSIS to determine scope                        ║
║                                                               ║
╚═══════════════════════════════════════════════════════════════╝
```

### 7.2. Impact Analysis

```
IMPACT ANALYSIS - Xác định scope of testing
═══════════════════════════════════════════════════════════════

CHANGE: Update payment gateway from VNPay to MoMo

IMPACT ANALYSIS:
───────────────────────────────────────────────────────────────

DIRECTLY AFFECTED:
├── PaymentService module
├── Checkout flow
├── Payment confirmation screen
└── Payment API endpoints

POTENTIALLY AFFECTED (via dependencies):
├── Order processing (depends on payment)
├── Refund functionality
├── Transaction reporting
└── Email notifications (payment receipts)

NOT AFFECTED:
├── User registration/login
├── Product catalog
├── Cart functionality
└── User profile management

TEST SCOPE DECISION:
───────────────────────────────────────────────────────────────
✓ Full testing: Payment-related features
✓ Regression testing: Order processing, refunds, notifications
✗ No testing needed: Login, catalog, cart, profile
```

---

## 8. CÂU HỎI ÔN TẬP

### Câu 1 (K2)
Functional testing focus vào gì?

A. How fast system responds
B. What the system does
C. How secure the system is
D. How many users can use the system

<details>
<summary>Đáp án</summary>

**B. What the system does**

Giải thích: Functional testing kiểm tra WHAT system does - tức là chức năng và hành vi của hệ thống.
</details>

---

### Câu 2 (K1)
Theo ISO 25010, đặc tính nào liên quan đến response time?

A. Usability
B. Security
C. Performance Efficiency
D. Reliability

<details>
<summary>Đáp án</summary>

**C. Performance Efficiency**

Giải thích: Performance Efficiency bao gồm Time behavior (response time), Resource utilization, và Capacity.
</details>

---

### Câu 3 (K2)
Black-box testing khác white-box testing ở điểm nào?

A. Black-box test nhanh hơn
B. Black-box không cần biết internal code structure
C. White-box do users thực hiện
D. Black-box chỉ dùng cho non-functional testing

<details>
<summary>Đáp án</summary>

**B. Black-box không cần biết internal code structure**

Giải thích: Black-box test dựa vào specifications, không cần biết code. White-box cần biết code structure.
</details>

---

### Câu 4 (K2)
Khi nào cần chạy Regression Testing?

A. Chỉ khi release version mới
B. Chỉ khi có new feature
C. Sau bất kỳ change nào (fix, feature, refactor)
D. Chỉ khi customer request

<details>
<summary>Đáp án</summary>

**C. Sau bất kỳ change nào (fix, feature, refactor)**

Giải thích: Regression testing chạy sau mọi change để verify không có unintended side effects.
</details>

---

### Câu 5 (K2)
Confirmation testing và Regression testing khác nhau như thế nào?

A. Confirmation test toàn bộ system, Regression test một phần
B. Confirmation verify fix works, Regression verify no new bugs
C. Confirmation do developers làm, Regression do testers làm
D. Không có sự khác biệt

<details>
<summary>Đáp án</summary>

**B. Confirmation verify fix works, Regression verify no new bugs**

Giải thích: Confirmation testing verify defect đã fix. Regression testing verify changes không break existing features.
</details>

---

## 9. CHECKLIST TỰ ĐÁNH GIÁ

Đánh dấu ✅ khi bạn đã hiểu:

- [ ] Phân biệt được Functional và Non-functional testing
- [ ] Nêu được 8 đặc tính chất lượng theo ISO 25010
- [ ] Phân biệt được Black-box và White-box testing
- [ ] Giải thích được Statement và Branch coverage
- [ ] Phân biệt được Confirmation và Regression testing
- [ ] Hiểu được khi nào cần Maintenance testing
- [ ] Biết được tại sao Regression testing nên automate

---

**Tiếp theo**: [Bài tập Giai đoạn 3](./bai-tap-giai-doan-3.md)

---

**Version**: 1.0.0
**Last Updated**: November 2025
