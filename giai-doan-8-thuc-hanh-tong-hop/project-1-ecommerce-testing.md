# Project 1: E-commerce Website Testing (ShopVN)

## 🎯 Mục Tiêu Project

Áp dụng **TẤT CẢ** kiến thức từ 7 giai đoạn trước vào một dự án thực tế hoàn chỉnh:
- Giai đoạn 1: Testing fundamentals
- Giai đoạn 2: Static testing (requirements review)
- Giai đoạn 3: Test levels & types
- Giai đoạn 4: Black-box techniques (EP, BVA, Decision Table, State Transition)
- Giai đoạn 5: White-box, Experience-based, Collaboration
- Giai đoạn 6: Test planning, estimation, prioritization, risk management
- Giai đoạn 7: Monitoring, reporting, configuration, defect management

**Thời gian**: 5-7 ngày (full-time) hoặc 2 tuần (part-time)

---

## 📋 Project Overview

### About ShopVN

**ShopVN** là nền tảng thương mại điện tử C2C (Consumer-to-Consumer) giống Shopee, cho phép:
- Người bán mở shop và đăng bán sản phẩm
- Người mua tìm kiếm, đặt hàng và thanh toán
- Hệ thống xử lý đơn hàng và giao hàng

### Project Context

**Company**: ShopVN Startup
**Release**: v2.0 - Major feature update
**Timeline**: Sprint 1-2 (4 weeks)
**Team**:
- 1 Test Lead (you)
- 2 Testers
- 4 Developers
- 1 Product Manager

### Scope of Testing

**In Scope**:
- User Registration & Login
- Product Search & Browse
- Shopping Cart
- Checkout & Payment
- Order Management

**Out of Scope**:
- Seller Dashboard (tested separately)
- Admin Panel
- Analytics
- Mobile app (web only)

---

## 📖 Requirements

### Epic 1: User Management

**US-101: User Registration**
```
As a new user
I want to register an account
So that I can shop on ShopVN

Acceptance Criteria:
- User can register with email + password
- Email must be valid format
- Password: 8-20 characters, must have letter + number
- Username: 3-20 characters, alphanumeric
- Email verification sent after registration
- User cannot register with existing email
- Registration form validates inputs
```

**US-102: User Login**
```
As a registered user
I want to login to my account
So that I can access my profile and orders

Acceptance Criteria:
- User can login with email + password
- Account locked after 5 failed attempts (30 mins)
- "Remember me" option saves session 7 days
- "Forgot password" sends reset email
- Social login: Google, Facebook
```

**US-103: User Profile**
```
As a logged-in user
I want to manage my profile
So that I can update my information

Acceptance Criteria:
- View/edit: Name, Phone, Address
- Change password (old password required)
- Upload profile picture (max 2MB, JPG/PNG)
- Add multiple shipping addresses (max 5)
```

### Epic 2: Product Management

**US-201: Product Search**
```
As a user
I want to search for products
So that I can find what I need

Acceptance Criteria:
- Search by keyword in product name/description
- Support Vietnamese with accents
- Sort by: Relevance, Price (Low-High, High-Low), Newest
- Filter by: Category, Price range, Location, Rating
- Display 20 products per page
- Pagination or infinite scroll
```

**US-202: Product Details**
```
As a user
I want to view product details
So that I can make purchase decision

Acceptance Criteria:
- Display: Images, Name, Price, Description
- Display: Seller info, Rating, Reviews
- Display: Stock quantity, Shipping options
- Related products section
- "Add to Cart" and "Buy Now" buttons
```

### Epic 3: Shopping Cart

**US-301: Add to Cart**
```
As a user
I want to add products to cart
So that I can purchase multiple items

Acceptance Criteria:
- Add product with quantity selection (1-999)
- Cannot exceed stock quantity
- Cart icon shows item count
- Cart persists across sessions (logged-in users)
- Guest cart saved 7 days in cookies
```

**US-302: Manage Cart**
```
As a user
I want to manage my cart
So that I can adjust before checkout

Acceptance Criteria:
- View all cart items with: Image, Name, Price, Quantity
- Update quantity (1-999)
- Remove items
- Select items for checkout (checkbox)
- Display subtotal and estimated shipping
- "Checkout" button (enabled if items selected)
```

### Epic 4: Checkout & Payment

**US-401: Checkout**
```
As a user
I want to checkout my cart
So that I can complete my purchase

Acceptance Criteria:
- Select shipping address (or add new)
- Select shipping method: Standard (3-5 days), Express (1-2 days)
- Select payment method: COD, Bank Transfer, Credit Card, E-Wallet
- Apply discount/voucher code
- Review order summary: Items, Shipping, Discount, Total
- "Place Order" button
```

**US-402: Payment Processing**
```
As a user
I want to pay for my order
So that my order is confirmed

Acceptance Criteria:
- COD: Order confirmed immediately
- Bank Transfer: Show bank details, pending until verified
- Credit Card: Redirect to payment gateway, process payment
- E-Wallet (Momo, ZaloPay): Redirect to app, process payment
- Payment success: Redirect to order confirmation
- Payment failure: Show error, allow retry
- Order status updated based on payment
```

### Epic 5: Order Management

**US-501: Order Tracking**
```
As a user
I want to track my orders
So that I know the status

Acceptance Criteria:
- View all orders: Pending, Processing, Shipped, Delivered, Cancelled
- Filter by status
- Order details: Items, Total, Shipping address, Tracking number
- Order states: Pending Payment → Paid → Processing → Shipped → Delivered
- Timeline showing order progress
```

**US-502: Order Cancellation**
```
As a user
I want to cancel my order
So that I can stop unwanted purchases

Acceptance Criteria:
- Cancel only if status = Pending or Processing
- Cannot cancel if Shipped or Delivered
- Cancellation reason required (dropdown)
- Refund processed if already paid (3-5 days)
- Email notification sent
```

---

## 🎭 Static Testing (Giai đoạn 2)

### Requirements Review

**Objective**: Review requirements BEFORE development

**Review Checklist**:

```
REQUIREMENTS REVIEW - ShopVN v2.0
Date: [Date]
Reviewer: [Your Name]

┌─────────────────────────────────────────────────────────┐
│                   REVIEW CHECKLIST                      │
├─────────────────────────────────────────────────────────┤
│                                                         │
│  ✅ COMPLETENESS                                        │
│  [✓] All user stories have acceptance criteria         │
│  [✓] Success and failure scenarios defined             │
│  [✓] Non-functional requirements specified             │
│  [✗] Missing: API response time requirements           │
│  [✗] Missing: Browser compatibility requirements       │
│                                                         │
│  ✅ CORRECTNESS                                         │
│  [✓] No logical contradictions                         │
│  [✓] Business rules are correct                        │
│  [?] US-301: Max cart quantity 999 - verify with PM    │
│                                                         │
│  ✅ CLARITY                                             │
│  [✓] Requirements are unambiguous                      │
│  [✗] US-401: "Estimated shipping" - calculation?       │
│  [✗] US-502: "Refund 3-5 days" - business or calendar? │
│                                                         │
│  ✅ TESTABILITY                                         │
│  [✓] Acceptance criteria are measurable                │
│  [✓] Test data can be identified                       │
│  [✓] Expected results are defined                      │
│                                                         │
│  ✅ CONSISTENCY                                         │
│  [✓] Terminology consistent across stories             │
│  [✓] No duplicate requirements                         │
│  [?] US-101 vs US-102: Account lockout duration        │
│       (US-102 says 30 mins, but US-101 doesn't mention)│
│                                                         │
└─────────────────────────────────────────────────────────┘

ISSUES FOUND: 5
- 2 Critical (Missing requirements)
- 3 Medium (Ambiguities)

ACTION ITEMS:
1. Clarify "estimated shipping" calculation with PM
2. Add API performance requirements
3. Specify browser compatibility (Chrome, Firefox, Safari, Edge)
4. Confirm "Refund 3-5 days" = business days
5. Standardize account lockout across all user stories
```

**Defects Found in Requirements** (examples):

```
REQ-DEF-001: Missing Performance Requirements
Severity: High
Description: No API response time requirements specified.
Risk: System may be slow, no SLA to validate against.
Recommendation: Add: "All API calls < 2s (95th percentile)"

REQ-DEF-002: Ambiguous Shipping Cost Calculation
Severity: Medium
Description: US-401 mentions "estimated shipping" but no formula.
Risk: Testers don't know expected shipping cost.
Recommendation: Clarify: Based on weight? Distance? Fixed rate?

REQ-DEF-003: Inconsistent Account Lockout
Severity: Medium
Description: US-102 specifies 30-min lockout after 5 failed attempts,
            but US-101 (registration) doesn't mention it.
Risk: Unclear if lockout applies to registration attempts.
Recommendation: Clarify and document in both stories.
```

---

## 📊 Test Planning (Giai đoạn 6)

### Test Plan Document

```
═══════════════════════════════════════════════════════════
SHOPVN v2.0 - TEST PLAN
═══════════════════════════════════════════════════════════

1. INTRODUCTION
───────────────────────────────────────────────────────

Project: ShopVN E-commerce Platform v2.0
Prepared by: [Your Name] - Test Lead
Date: [Date]
Version: 1.0

Purpose:
This document outlines the testing strategy, scope, approach,
resources, and schedule for ShopVN v2.0 release.

───────────────────────────────────────────────────────

2. TEST SCOPE
───────────────────────────────────────────────────────

IN SCOPE:
✅ Functional Testing (all 5 epics)
✅ Integration Testing (APIs, Payment gateway)
✅ Non-functional Testing:
   - Performance (response time, load)
   - Security (authentication, XSS, SQL injection)
   - Usability (UI/UX)
   - Compatibility (browsers)
✅ Regression Testing
✅ User Acceptance Testing (UAT)

OUT OF SCOPE:
❌ Seller Dashboard (separate test plan)
❌ Admin Panel
❌ Mobile apps (future release)
❌ Penetration testing (external vendor)

───────────────────────────────────────────────────────

3. TEST APPROACH
───────────────────────────────────────────────────────

3.1. TEST LEVELS

COMPONENT TESTING:
• By: Developers
• Tools: Jest (Frontend), pytest (Backend)
• Coverage Target: 80%

INTEGRATION TESTING:
• By: Test Team
• Focus: API endpoints, Database, Payment gateway
• Tools: Postman, RestAssured

SYSTEM TESTING:
• By: Test Team
• Focus: End-to-end user scenarios
• Tools: Manual + Selenium automation

ACCEPTANCE TESTING:
• By: Product Team + Selected users
• Focus: Business requirements validation
• Tools: Manual testing

3.2. TEST TYPES

FUNCTIONAL:
• Black-box techniques: EP, BVA, Decision Table, State Transition
• Test all acceptance criteria

NON-FUNCTIONAL:
• Performance: JMeter (1000 concurrent users)
• Security: OWASP ZAP scan
• Usability: Heuristic evaluation
• Compatibility: Chrome, Firefox, Safari, Edge (latest 2 versions)

REGRESSION:
• Automated suite: 200+ test cases
• Run after every deployment
• CI/CD: GitHub Actions

3.3. TEST TECHNIQUES

┌──────────────────────┬────────────────────────────┐
│ Technique            │ Application                │
├──────────────────────┼────────────────────────────┤
│ Equivalence          │ Input validation           │
│ Partitioning (EP)    │ (email, password, quantity)│
│                      │                            │
│ Boundary Value       │ Quantity (1-999)           │
│ Analysis (BVA)       │ Price ranges               │
│                      │ Character limits           │
│                      │                            │
│ Decision Table       │ Discount calculation       │
│                      │ Shipping cost              │
│                      │ Payment method selection   │
│                      │                            │
│ State Transition     │ Order lifecycle            │
│                      │ Login attempts (lockout)   │
│                      │ Cart states                │
│                      │                            │
│ Exploratory Testing  │ Ad-hoc discovery           │
│                      │ Usability issues           │
│                      │                            │
│ Error Guessing       │ Edge cases                 │
│                      │ Common user mistakes       │
└──────────────────────┴────────────────────────────┘

───────────────────────────────────────────────────────

4. TEST ENVIRONMENT
───────────────────────────────────────────────────────

ENVIRONMENTS:

DEV: http://dev.shopvn.com
├─ For: Developer testing
├─ Data: Mock data
└─ Uptime: Not guaranteed

QA: http://qa.shopvn.com
├─ For: QA team testing
├─ Data: Test data (refreshed daily)
└─ Uptime: 95%

STAGING: http://staging.shopvn.com
├─ For: UAT, final validation
├─ Data: Production-like data (anonymized)
└─ Uptime: 99%

PRODUCTION: https://shopvn.com
├─ For: Live users
├─ Data: Real data
└─ Uptime: 99.9% SLA

HARDWARE/SOFTWARE:
• Cloud: AWS (EC2, RDS, S3)
• OS: Ubuntu 22.04
• Database: PostgreSQL 14
• Web Server: Nginx
• Application: Node.js 18 (Backend), React 18 (Frontend)
• Payment: Stripe API, Momo SDK

TEST TOOLS:
• Test Management: TestRail
• Automation: Selenium WebDriver, pytest
• API Testing: Postman, RestAssured
• Performance: JMeter
• Security: OWASP ZAP
• CI/CD: GitHub Actions
• Defect Tracking: Jira

───────────────────────────────────────────────────────

5. TEST ESTIMATION
───────────────────────────────────────────────────────

ESTIMATION METHOD: Three-Point Estimation

Test Case Design:
• Optimistic: 3 days
• Most Likely: 5 days
• Pessimistic: 8 days
• Expected: (3 + 4×5 + 8) / 6 = 5.2 days ≈ 5 days

Test Execution:
• Optimistic: 4 days
• Most Likely: 6 days
• Pessimistic: 10 days
• Expected: (4 + 4×6 + 10) / 6 = 6.3 days ≈ 6 days

Regression Testing:
• 2 days (automated suite)

UAT Support:
• 3 days

TOTAL: 5 + 6 + 2 + 3 = 16 days

TEAM: 3 testers × 16 days = 48 person-days

───────────────────────────────────────────────────────

6. TEST SCHEDULE
───────────────────────────────────────────────────────

SPRINT 1 (Week 1-2):
Week 1:
  • Requirements review (Static testing)
  • Test plan creation
  • Test case design (Epic 1-2)
  • Test environment setup

Week 2:
  • Test case design (Epic 3-5)
  • Test data preparation
  • Automation framework setup

SPRINT 2 (Week 3-4):
Week 3:
  • System testing (Epic 1-3)
  • Defect logging & tracking
  • Daily status reports

Week 4:
  • System testing (Epic 4-5)
  • Regression testing
  • UAT
  • Test completion report

───────────────────────────────────────────────────────

7. ENTRY & EXIT CRITERIA
───────────────────────────────────────────────────────

ENTRY CRITERIA:

✅ BEFORE SYSTEM TESTING STARTS:
  • [ ] Requirements approved and baselined
  • [ ] Test plan approved
  • [ ] Test cases reviewed and approved (>300 TCs)
  • [ ] Test environment set up and stable
  • [ ] Test data prepared
  • [ ] Build deployed to QA environment
  • [ ] Unit testing complete (>80% coverage)
  • [ ] Smoke testing passed

EXIT CRITERIA:

✅ BEFORE RELEASE TO PRODUCTION:
  • [ ] All test cases executed (>95%)
  • [ ] Pass rate ≥ 90%
  • [ ] No open P0/P1 defects
  • [ ] P2 defects < 10 open
  • [ ] Regression test passed
  • [ ] Performance test passed (<2s response time)
  • [ ] Security scan passed (no critical vulnerabilities)
  • [ ] UAT sign-off received
  • [ ] Test completion report approved

───────────────────────────────────────────────────────

8. RISK ANALYSIS & MITIGATION
───────────────────────────────────────────────────────

PRODUCT RISKS:

┌──────┬─────────────────────┬────┬────────┬──────┬────────┐
│ ID   │ Risk                │ L  │ Impact │ Risk │ Action │
├──────┼─────────────────────┼────┼────────┼──────┼────────┤
│ PR-01│ Payment gateway     │ 3  │   5    │  15  │ Focus  │
│      │ integration failure │    │        │(HIGH)│ testing│
│      │                     │    │        │      │ Early  │
│      │                     │    │        │      │ sandbox│
│      │                     │    │        │      │ testing│
├──────┼─────────────────────┼────┼────────┼──────┼────────┤
│ PR-02│ Performance issues  │ 4  │   4    │  16  │ Load   │
│      │ under peak load     │    │        │(HIGH)│ testing│
│      │ (flash sale)        │    │        │      │ 2000   │
│      │                     │    │        │      │ users  │
├──────┼─────────────────────┼────┼────────┼──────┼────────┤
│ PR-03│ SQL injection       │ 2  │   5    │  10  │ Input  │
│      │ vulnerability       │    │        │ (MED)│ valid. │
│      │                     │    │        │      │ Sec.   │
│      │                     │    │        │      │ scan   │
├──────┼─────────────────────┼────┼────────┼──────┼────────┤
│ PR-04│ Order data loss     │ 2  │   5    │  10  │ Data   │
│      │ during transaction  │    │        │ (MED)│ integ. │
│      │                     │    │        │      │ tests  │
├──────┼─────────────────────┼────┼────────┼──────┼────────┤
│ PR-05│ Vietnamese keyword  │ 3  │   3    │  9   │ Test   │
│      │ search not working  │    │        │ (MED)│ Viet   │
│      │                     │    │        │      │ inputs │
└──────┴─────────────────────┴────┴────────┴──────┴────────┘

Legend: L = Likelihood (1-5), Impact (1-5), Risk = L × I

PROJECT RISKS:

┌──────┬─────────────────────┬────┬────────┬──────┬────────┐
│ PJ-01│ Test environment    │ 3  │   3    │  9   │ Backup │
│      │ instability         │    │        │ (MED)│ env    │
│      │                     │    │        │      │ ready  │
├──────┼─────────────────────┼────┼────────┼──────┼────────┤
│ PJ-02│ Insufficient test   │ 2  │   4    │  8   │ Start  │
│      │ time (tight         │    │        │ (MED)│ early  │
│      │ schedule)           │    │        │      │ Risk-  │
│      │                     │    │        │      │ based  │
├──────┼─────────────────────┼────┼────────┼──────┼────────┤
│ PJ-03│ Tester unavailable  │ 2  │   3    │  6   │ Cross  │
│      │ (sick leave)        │    │        │ (LOW)│ train  │
│      │                     │    │        │      │ team   │
└──────┴─────────────────────┴────┴────────┴──────┴────────┘

───────────────────────────────────────────────────────

9. DELIVERABLES
───────────────────────────────────────────────────────

TEST DELIVERABLES:

1. Test Plan (this document)
2. Test Cases (>300 test cases)
   - Epic 1: 60 TCs
   - Epic 2: 50 TCs
   - Epic 3: 70 TCs
   - Epic 4: 80 TCs
   - Epic 5: 40 TCs
3. Test Data Sets
4. Traceability Matrix (Requirements → Test Cases)
5. Test Execution Logs
6. Defect Reports (~100 expected)
7. Test Progress Reports (weekly)
8. Test Completion Report
9. Automation Scripts (regression suite)

───────────────────────────────────────────────────────

10. APPROVALS
───────────────────────────────────────────────────────

Test Plan Prepared by:
Name: [Your Name]
Role: Test Lead
Date: __________
Signature: __________

Reviewed by:
Name: [PM Name]
Role: Product Manager
Date: __________
Signature: __________

Approved by:
Name: [Dev Lead Name]
Role: Development Lead
Date: __________
Signature: __________

═══════════════════════════════════════════════════════════
```

---

## 🧪 Test Cases (Giai đoạn 4-5)

### Sample Test Cases Using All Techniques

#### Technique 1: Equivalence Partitioning (EP)

**Feature**: User Registration - Email Validation

**EP Analysis**:

```
Input: Email field

Partitions:
┌─────────────────────────────────────────────────────┐
│ VALID PARTITIONS                                    │
├─────────────────────────────────────────────────────┤
│ VP1: Valid email format (user@domain.com)          │
│      Examples: test@gmail.com, user.name@shop.vn   │
└─────────────────────────────────────────────────────┘

┌─────────────────────────────────────────────────────┐
│ INVALID PARTITIONS                                  │
├─────────────────────────────────────────────────────┤
│ IP1: Missing @ symbol (usergmail.com)              │
│ IP2: Missing domain (user@)                        │
│ IP3: Missing local part (@gmail.com)               │
│ IP4: Multiple @ symbols (user@@gmail.com)          │
│ IP5: Special characters (user!#$@gmail.com)        │
│ IP6: Empty string ("")                             │
│ IP7: Spaces (user @gmail.com)                      │
└─────────────────────────────────────────────────────┘
```

**Test Cases**:

```
TC-REG-001: Register with Valid Email Format
───────────────────────────────────────────────────────
Objective: Verify registration accepts valid email
Technique: EP (VP1)
Pre-condition: User on registration page

Test Data:
  Email: testuser@gmail.com
  Password: Test1234
  Username: testuser

Steps:
  1. Enter email: testuser@gmail.com
  2. Enter password: Test1234
  3. Enter username: testuser
  4. Click "Register"

Expected Result:
  ✅ Registration successful
  ✅ Verification email sent
  ✅ Redirect to "Verify Email" page

Priority: P1
───────────────────────────────────────────────────────

TC-REG-002: Register with Missing @ Symbol
───────────────────────────────────────────────────────
Objective: Verify registration rejects email without @
Technique: EP (IP1)

Test Data:
  Email: testusergmail.com
  Password: Test1234
  Username: testuser

Steps:
  1. Enter email: testusergmail.com
  2. Enter password: Test1234
  3. Enter username: testuser
  4. Click "Register"

Expected Result:
  ❌ Error message: "Invalid email format"
  ❌ Registration not processed

Priority: P1
───────────────────────────────────────────────────────

TC-REG-003: Register with Empty Email
───────────────────────────────────────────────────────
Objective: Verify registration requires email
Technique: EP (IP6)

Test Data:
  Email: (empty)
  Password: Test1234
  Username: testuser

Steps:
  1. Leave email field empty
  2. Enter password: Test1234
  3. Enter username: testuser
  4. Click "Register"

Expected Result:
  ❌ Error message: "Email is required"
  ❌ Registration button disabled or validation error

Priority: P1
───────────────────────────────────────────────────────
```

---

#### Technique 2: Boundary Value Analysis (BVA)

**Feature**: Shopping Cart - Quantity Selection

**BVA Analysis**:

```
Input: Quantity field
Range: 1 - 999

Boundaries:
┌──────────────┬────────┬──────────┬──────────┐
│ Boundary     │ Min-1  │ Min      │ Min+1    │
├──────────────┼────────┼──────────┼──────────┤
│ Lower        │   0    │   1 ✅   │   2      │
└──────────────┴────────┴──────────┴──────────┘

┌──────────────┬────────┬──────────┬──────────┐
│ Boundary     │ Max-1  │ Max      │ Max+1    │
├──────────────┼────────┼──────────┼──────────┤
│ Upper        │  998   │  999 ✅  │  1000    │
└──────────────┴────────┴──────────┴──────────┘

2-Value BVA: 1, 999
3-Value BVA: 0, 1, 2, 998, 999, 1000
```

**Test Cases**:

```
TC-CART-010: Add Product with Minimum Quantity (BVA: Min)
───────────────────────────────────────────────────────
Objective: Verify cart accepts minimum quantity
Technique: BVA (2-value, Min boundary)

Test Data:
  Product: iPhone 15 Pro (Stock: 50)
  Quantity: 1

Steps:
  1. Go to product page
  2. Set quantity = 1
  3. Click "Add to Cart"

Expected Result:
  ✅ Product added to cart
  ✅ Cart shows 1 item
  ✅ Quantity = 1

Priority: P1
───────────────────────────────────────────────────────

TC-CART-011: Add Product with Below Minimum (BVA: Min-1)
───────────────────────────────────────────────────────
Objective: Verify cart rejects quantity < 1
Technique: BVA (3-value, Min-1)

Test Data:
  Product: iPhone 15 Pro
  Quantity: 0

Steps:
  1. Go to product page
  2. Try to set quantity = 0 (using keyboard or decrement)
  3. Click "Add to Cart"

Expected Result:
  ❌ Quantity field resets to 1 OR
  ❌ Error message: "Quantity must be at least 1"
  ❌ Product not added

Priority: P1
───────────────────────────────────────────────────────

TC-CART-012: Add Product with Maximum Quantity (BVA: Max)
───────────────────────────────────────────────────────
Objective: Verify cart accepts maximum quantity
Technique: BVA (2-value, Max boundary)

Test Data:
  Product: iPhone 15 Pro (Stock: 1000)
  Quantity: 999

Steps:
  1. Go to product page
  2. Set quantity = 999
  3. Click "Add to Cart"

Expected Result:
  ✅ Product added to cart
  ✅ Quantity = 999

Priority: P2
───────────────────────────────────────────────────────

TC-CART-013: Add Product with Above Maximum (BVA: Max+1)
───────────────────────────────────────────────────────
Objective: Verify cart rejects quantity > 999
Technique: BVA (3-value, Max+1)

Test Data:
  Product: iPhone 15 Pro (Stock: 1000)
  Quantity: 1000

Steps:
  1. Go to product page
  2. Try to set quantity = 1000
  3. Click "Add to Cart"

Expected Result:
  ❌ Quantity capped at 999 OR
  ❌ Error message: "Maximum quantity is 999"
  ❌ Cannot add > 999

Priority: P2
───────────────────────────────────────────────────────

TC-CART-014: Add Product Exceeding Stock (BVA: Special case)
───────────────────────────────────────────────────────
Objective: Verify cart prevents adding more than stock
Technique: BVA (stock boundary)

Test Data:
  Product: iPhone 15 Pro (Stock: 10)
  Quantity: 11

Steps:
  1. Go to product page
  2. Try to set quantity = 11
  3. Click "Add to Cart"

Expected Result:
  ❌ Quantity capped at 10 (stock) OR
  ❌ Error: "Only 10 items available"

Priority: P1
───────────────────────────────────────────────────────
```

---

#### Technique 3: Decision Table Testing

**Feature**: Discount Calculation

**Business Rules**:
- Member: Yes/No
- Order Value: < 500K / 500K-1M / > 1M
- Free Shipping: Yes/No

**Discount**:
- Member + Order > 1M: 15% discount + Free shipping
- Member + Order 500K-1M: 10% discount
- Member + Order < 500K: 5% discount
- Non-member + Order > 1M: 5% discount + Free shipping
- Non-member + Order < 1M: No discount

**Decision Table**:

```
┌─────────────────────────────────────────────────────────────┐
│               DISCOUNT DECISION TABLE                       │
├───────────┬─────┬─────┬─────┬─────┬─────┬─────┬─────┬─────┤
│Conditions │ R1  │ R2  │ R3  │ R4  │ R5  │ R6  │ R7  │ R8  │
├───────────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┤
│Member?    │  Y  │  Y  │  Y  │  Y  │  N  │  N  │  N  │  N  │
│Order>1M?  │  Y  │  Y  │  N  │  N  │  Y  │  Y  │  N  │  N  │
│Order>500K?│  Y  │  N  │  Y  │  N  │  Y  │  N  │  Y  │  N  │
├───────────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┤
│Actions    │     │     │     │     │     │     │     │     │
├───────────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┼─────┤
│Discount   │ 15% │  X  │ 10% │  5% │  5% │  X  │  0% │  0% │
│Free Ship  │  Y  │  X  │  N  │  N  │  Y  │  X  │  N  │  N  │
└───────────┴─────┴─────┴─────┴─────┴─────┴─────┴─────┴─────┘

Note: X = Impossible (Order > 1M implies Order > 500K)
Rules to test: R1, R3, R4, R5, R7, R8 (6 test cases)
```

**Test Cases**:

```
TC-DISCOUNT-001: Member with Order > 1M (Rule R1)
───────────────────────────────────────────────────────
Objective: Verify 15% discount + free shipping
Technique: Decision Table (R1)

Test Data:
  User: Member account
  Cart: Products totaling 1,200,000 VND

Steps:
  1. Login as member
  2. Add products to cart (total 1.2M)
  3. Go to checkout
  4. Observe discount and shipping

Expected Result:
  ✅ Discount: 15% (180,000 VND)
  ✅ Shipping: Free
  ✅ Total: 1,020,000 VND

Priority: P1
───────────────────────────────────────────────────────

TC-DISCOUNT-002: Member with Order 500K-1M (Rule R3)
───────────────────────────────────────────────────────
Objective: Verify 10% discount, no free shipping
Technique: Decision Table (R3)

Test Data:
  User: Member account
  Cart: Products totaling 800,000 VND
  Shipping: 30,000 VND

Steps:
  1. Login as member
  2. Add products (total 800K)
  3. Go to checkout

Expected Result:
  ✅ Discount: 10% (80,000 VND)
  ❌ Shipping: 30,000 VND (not free)
  ✅ Total: 750,000 VND

Priority: P1
───────────────────────────────────────────────────────

TC-DISCOUNT-003: Member with Order < 500K (Rule R4)
───────────────────────────────────────────────────────
Objective: Verify 5% discount only
Technique: Decision Table (R4)

Test Data:
  User: Member account
  Cart: 300,000 VND
  Shipping: 30,000 VND

Steps:
  1. Login as member
  2. Add products (300K)
  3. Go to checkout

Expected Result:
  ✅ Discount: 5% (15,000 VND)
  ❌ Shipping: 30,000 VND
  ✅ Total: 315,000 VND

Priority: P2
───────────────────────────────────────────────────────

TC-DISCOUNT-004: Non-Member with Order > 1M (Rule R5)
───────────────────────────────────────────────────────
Objective: Verify 5% discount + free shipping
Technique: Decision Table (R5)

Test Data:
  User: Guest user
  Cart: 1,500,000 VND

Steps:
  1. Browse as guest
  2. Add products (1.5M)
  3. Go to checkout

Expected Result:
  ✅ Discount: 5% (75,000 VND)
  ✅ Shipping: Free
  ✅ Total: 1,425,000 VND

Priority: P1
───────────────────────────────────────────────────────

TC-DISCOUNT-005: Non-Member with Order 500K-1M (Rule R7)
───────────────────────────────────────────────────────
Objective: Verify no discount
Technique: Decision Table (R7)

Test Data:
  User: Guest
  Cart: 700,000 VND
  Shipping: 30,000 VND

Steps:
  1. Browse as guest
  2. Add products (700K)
  3. Go to checkout

Expected Result:
  ❌ Discount: 0%
  ❌ Shipping: 30,000 VND (not free)
  ✅ Total: 730,000 VND

Priority: P2
───────────────────────────────────────────────────────

TC-DISCOUNT-006: Non-Member with Order < 500K (Rule R8)
───────────────────────────────────────────────────────
Objective: Verify no discount or free shipping
Technique: Decision Table (R8)

Test Data:
  User: Guest
  Cart: 200,000 VND
  Shipping: 30,000 VND

Steps:
  1. Browse as guest
  2. Add products (200K)
  3. Go to checkout

Expected Result:
  ❌ Discount: 0%
  ❌ Shipping: 30,000 VND
  ✅ Total: 230,000 VND

Priority: P2
───────────────────────────────────────────────────────
```

---

#### Technique 4: State Transition Testing

**Feature**: Order Status Lifecycle

**State Diagram**:

```
     [New Order]
          │
          │ Payment Success
          ↓
       [Paid]
          │
          │ Start Processing
          ↓
     [Processing] ←────────┐
          │                │
          │ Ship Order     │ Cancel
          ↓                │
      [Shipped]            │
          │                │
          │ Delivery       │
          ↓                │
     [Delivered]           │
                           │
     [Cancelled] ←─────────┘

Valid Transitions:
• New → Paid (payment success)
• New → Cancelled (payment failed or user cancel)
• Paid → Processing (seller starts)
• Paid → Cancelled (seller cancels)
• Processing → Shipped (shipped out)
• Processing → Cancelled (cancel before ship)
• Shipped → Delivered (delivery confirmed)

Invalid Transitions (examples):
• New → Processing (must pay first)
• Shipped → Cancelled (cannot cancel after shipped)
• Delivered → any state (final state)
```

**Test Cases for State Transitions**:

```
TC-ORDER-030: Valid Transition: New → Paid
───────────────────────────────────────────────────────
Objective: Verify order moves to Paid after payment
Technique: State Transition (Valid)

Initial State: New Order
Event: Payment Success

Steps:
  1. Create order (status = New)
  2. Select payment method: Credit Card
  3. Complete payment successfully

Expected Result:
  ✅ Order status → Paid
  ✅ Email notification sent
  ✅ Payment record created

Priority: P1
───────────────────────────────────────────────────────

TC-ORDER-031: Valid Transition: Paid → Processing
───────────────────────────────────────────────────────
Objective: Verify order moves to Processing
Technique: State Transition (Valid)

Initial State: Paid
Event: Seller starts processing

Steps:
  1. Order in Paid status
  2. Seller clicks "Start Processing"

Expected Result:
  ✅ Order status → Processing
  ✅ Notification to buyer
  ✅ Cannot cancel by buyer anymore

Priority: P1
───────────────────────────────────────────────────────

TC-ORDER-032: Valid Transition: Processing → Shipped
───────────────────────────────────────────────────────
Objective: Verify order moves to Shipped
Technique: State Transition (Valid)

Initial State: Processing
Event: Order shipped

Steps:
  1. Order in Processing status
  2. Seller enters tracking number
  3. Seller clicks "Mark as Shipped"

Expected Result:
  ✅ Order status → Shipped
  ✅ Tracking number saved
  ✅ Notification with tracking to buyer

Priority: P1
───────────────────────────────────────────────────────

TC-ORDER-033: Valid Transition: Shipped → Delivered
───────────────────────────────────────────────────────
Objective: Verify order moves to Delivered
Technique: State Transition (Valid)

Initial State: Shipped
Event: Delivery confirmed

Steps:
  1. Order in Shipped status
  2. Buyer receives package
  3. Buyer clicks "Confirm Delivery"

Expected Result:
  ✅ Order status → Delivered
  ✅ Payment released to seller
  ✅ Option to leave review

Priority: P1
───────────────────────────────────────────────────────

TC-ORDER-034: Valid Transition: Paid → Cancelled
───────────────────────────────────────────────────────
Objective: Verify user can cancel paid order
Technique: State Transition (Valid)

Initial State: Paid
Event: User cancels

Steps:
  1. Order in Paid status (not yet Processing)
  2. Buyer clicks "Cancel Order"
  3. Select cancellation reason
  4. Confirm cancellation

Expected Result:
  ✅ Order status → Cancelled
  ✅ Refund initiated
  ✅ Email confirmation sent

Priority: P1
───────────────────────────────────────────────────────

TC-ORDER-035: Invalid Transition: New → Processing
───────────────────────────────────────────────────────
Objective: Verify order cannot skip Payment state
Technique: State Transition (Invalid)

Initial State: New
Event: Try to process without payment

Steps:
  1. Create order (status = New)
  2. Attempt to move to Processing (via API or direct)

Expected Result:
  ❌ Error: "Order must be paid first"
  ❌ Status remains New
  ❌ Transition blocked

Priority: P2
───────────────────────────────────────────────────────

TC-ORDER-036: Invalid Transition: Shipped → Cancelled
───────────────────────────────────────────────────────
Objective: Verify cannot cancel after shipping
Technique: State Transition (Invalid)

Initial State: Shipped
Event: Try to cancel

Steps:
  1. Order in Shipped status
  2. Buyer attempts to click "Cancel Order"

Expected Result:
  ❌ "Cancel Order" button disabled OR
  ❌ Error: "Cannot cancel shipped order"
  ❌ Status remains Shipped

Priority: P1
───────────────────────────────────────────────────────

TC-ORDER-037: State Coverage - All States Visited
───────────────────────────────────────────────────────
Objective: Verify complete order lifecycle
Technique: State Transition (All States Coverage)

Test Path: New → Paid → Processing → Shipped → Delivered

Steps:
  1. Create order (New)
  2. Pay successfully (Paid)
  3. Seller processes (Processing)
  4. Seller ships (Shipped)
  5. Buyer confirms delivery (Delivered)

Expected Result:
  ✅ All state transitions work
  ✅ Order reaches final Delivered state
  ✅ No errors in lifecycle

Priority: P1
───────────────────────────────────────────────────────
```

---

## 📑 Traceability Matrix (Giai đoạn 7)

```
═══════════════════════════════════════════════════════════════════════════
SHOPVN v2.0 - REQUIREMENTS TRACEABILITY MATRIX (RTM)
═══════════════════════════════════════════════════════════════════════════

┌──────────┬────────────────────────┬───────────────┬────────┬──────────┐
│ Req ID   │ Requirement            │ Test Cases    │Status  │ Defects  │
├──────────┼────────────────────────┼───────────────┼────────┼──────────┤
│ US-101   │ User Registration      │ TC-REG-001 to │ 92%    │ DEF-012  │
│          │ - Email validation     │ TC-REG-015    │ Pass   │ (Medium) │
│          │ - Password rules       │ (15 TCs)      │        │          │
│          │ - Username rules       │               │        │          │
├──────────┼────────────────────────┼───────────────┼────────┼──────────┤
│ US-102   │ User Login             │ TC-LOGIN-001  │ 100%   │ DEF-023  │
│          │ - Email + Password     │ to            │ Pass   │ (High)   │
│          │ - Account lockout      │ TC-LOGIN-020  │        │ FIXED    │
│          │ - Remember me          │ (20 TCs)      │        │          │
│          │ - Social login         │               │        │          │
├──────────┼────────────────────────┼───────────────┼────────┼──────────┤
│ US-103   │ User Profile           │ TC-PROFILE    │ 95%    │ -        │
│          │ - Edit info            │ -001 to -012  │ Pass   │          │
│          │ - Change password      │ (12 TCs)      │        │          │
│          │ - Upload picture       │               │        │          │
├──────────┼────────────────────────┼───────────────┼────────┼──────────┤
│ US-201   │ Product Search         │ TC-SEARCH     │ 85%    │ DEF-045  │
│          │ - Keyword search       │ -001 to -025  │ Pass   │ (High)   │
│          │ - Vietnamese accents   │ (25 TCs)      │        │ DEF-046  │
│          │ - Sort & Filter        │               │        │ (Medium) │
├──────────┼────────────────────────┼───────────────┼────────┼──────────┤
│ US-202   │ Product Details        │ TC-PRODUCT    │ 100%   │ -        │
│          │ - Display info         │ -001 to -010  │ Pass   │          │
│          │ - Related products     │ (10 TCs)      │        │          │
├──────────┼────────────────────────┼───────────────┼────────┼──────────┤
│ US-301   │ Add to Cart            │ TC-CART-001   │ 90%    │ DEF-067  │
│          │ - Quantity selection   │ to            │ Pass   │ (Medium) │
│          │ - Stock validation     │ TC-CART-015   │        │          │
│          │ - Cart persistence     │ (15 TCs)      │        │          │
├──────────┼────────────────────────┼───────────────┼────────┼──────────┤
│ US-302   │ Manage Cart            │ TC-CART-016   │ 100%   │ -        │
│          │ - View items           │ to            │ Pass   │          │
│          │ - Update quantity      │ TC-CART-030   │        │          │
│          │ - Remove items         │ (15 TCs)      │        │          │
├──────────┼────────────────────────┼───────────────┼────────┼──────────┤
│ US-401   │ Checkout               │ TC-CHECKOUT   │ 88%    │ DEF-089  │
│          │ - Shipping address     │ -001 to -035  │ Pass   │ (High)   │
│          │ - Shipping method      │ (35 TCs)      │        │ DEF-090  │
│          │ - Payment method       │               │        │ (Critical│
│          │ - Discount code        │               │        │ OPEN)    │
├──────────┼────────────────────────┼───────────────┼────────┼──────────┤
│ US-402   │ Payment Processing     │ TC-PAYMENT    │ 75%    │ DEF-101  │
│          │ - COD                  │ -001 to -045  │ Pass   │ (Critical│
│          │ - Bank Transfer        │ (45 TCs)      │        │ OPEN)    │
│          │ - Credit Card          │               │        │ DEF-102  │
│          │ - E-Wallet             │               │        │ (High)   │
├──────────┼────────────────────────┼───────────────┼────────┼──────────┤
│ US-501   │ Order Tracking         │ TC-ORDER-001  │ 95%    │ -        │
│          │ - View orders          │ to            │ Pass   │          │
│          │ - Filter by status     │ TC-ORDER-025  │        │          │
│          │ - Order details        │ (25 TCs)      │        │          │
├──────────┼────────────────────────┼───────────────┼────────┼──────────┤
│ US-502   │ Order Cancellation     │ TC-ORDER-026  │ 100%   │ -        │
│          │ - Cancel rules         │ to            │ Pass   │          │
│          │ - Refund processing    │ TC-ORDER-040  │        │          │
│          │ - Notifications        │ (15 TCs)      │        │          │
└──────────┴────────────────────────┴───────────────┴────────┴──────────┘

═══════════════════════════════════════════════════════════════════════════

SUMMARY:
├─ Total Requirements: 11 user stories
├─ Total Test Cases: 252
├─ Executed: 252 (100%)
├─ Passed: 233 (92.5%)
├─ Failed: 19 (7.5%)
├─ Open Defects: 8 (2 Critical, 3 High, 3 Medium)
└─ Requirements Coverage: 100%

⚠️  CRITICAL ISSUES:
• US-401/US-402: Payment gateway integration has 2 critical defects
  - DEF-090: Payment fails for orders > 5M VND
  - DEF-101: Credit card authorization timeout
  → Blocks release, must fix before going live

📊 COVERAGE ANALYSIS:
• All user stories have test cases ✅
• High-risk areas (Payment, Checkout) thoroughly tested ✅
• 92.5% pass rate (target: 90%) ✅

═══════════════════════════════════════════════════════════════════════════
```

---

## 🐛 Sample Defect Reports (Giai đoạn 7)

### Defect 1: Critical Payment Issue

```
═══════════════════════════════════════════════════════════
DEFECT REPORT: DEF-090
═══════════════════════════════════════════════════════════

BASIC INFORMATION:
────────────────────────────────────────────────────────
Defect ID:        DEF-090
Title:            Payment fails for orders > 5M VND with Credit Card
Reported by:      [Your Name] (QA Engineer)
Date reported:    [Date], 2:30 PM
Environment:      QA (qa.shopvn.com)
Build:            v2.0-RC3, Build #245
Severity:         CRITICAL
Priority:         P0
Component:        Payment Module
Assigned to:      Backend Team
Status:           Open → In Progress

DESCRIPTION:
────────────────────────────────────────────────────────
When user attempts to pay for an order exceeding 5,000,000 VND
using Credit Card payment method, the payment fails with a
timeout error after 60 seconds. The order remains in "Pending
Payment" status.

Business Impact:
• High-value orders (15% of revenue) cannot be completed
• Customer frustration → abandoned carts
• Competitive disadvantage
• Revenue loss estimated: 50M VND/day

Technical Impact:
• Payment gateway integration broken for large amounts
• Blocks release to production

STEPS TO REPRODUCE:
────────────────────────────────────────────────────────
Pre-condition: User logged in, cart has products > 5M VND

1. Add products to cart: Total = 5,200,000 VND
2. Go to Checkout
3. Select shipping address
4. Select payment method: "Credit Card"
5. Click "Place Order"
6. Enter credit card details on payment gateway:
   - Card: 4242 4242 4242 4242 (Stripe test card)
   - Expiry: 12/25
   - CVV: 123
7. Click "Pay Now"
8. Observe result

EXPECTED RESULT:
────────────────────────────────────────────────────────
✅ Payment processed successfully within 10 seconds
✅ Order status → Paid
✅ Redirect to order confirmation page
✅ Email confirmation sent

ACTUAL RESULT:
────────────────────────────────────────────────────────
❌ Loading spinner shows for ~60 seconds
❌ Error popup: "Payment timeout. Please try again."
❌ Order status remains "Pending Payment"
❌ No email sent
❌ Payment not recorded

TEST DATA:
────────────────────────────────────────────────────────
User account: testuser@shopvn.com / Test1234
Cart items:
  • MacBook Pro M3: 45,000,000 VND × 1
  • Shipping: 0 VND (free shipping > 1M)
  • Total: 5,200,000 VND

Credit card (test): 4242 4242 4242 4242, 12/25, CVV: 123

Test Results by Amount:
  • 1,000,000 VND: ✅ Payment successful
  • 3,000,000 VND: ✅ Payment successful
  • 4,999,999 VND: ✅ Payment successful
  • 5,000,000 VND: ❌ Payment timeout
  • 5,200,000 VND: ❌ Payment timeout
  • 10,000,000 VND: ❌ Payment timeout

→ Threshold appears to be exactly 5,000,000 VND

EVIDENCE:
────────────────────────────────────────────────────────
Screenshots:
  • [Attachment 1]: Error popup screenshot
  • [Attachment 2]: Browser console errors
  • [Attachment 3]: Network tab showing timeout

Video:
  • [Attachment 4]: Screen recording (payment attempt)

Logs:
  • [Attachment 5]: Backend logs (payment-service.log)
    Error: "Stripe API timeout after 60000ms"
    Timestamp: 2024-12-01 14:25:34

  • [Attachment 6]: API response
    Status: 504 Gateway Timeout
    Response body: {"error": "Payment gateway timeout"}

ENVIRONMENT DETAILS:
────────────────────────────────────────────────────────
Browser:         Chrome 119.0.6045.105
OS:              Windows 11
Screen size:     1920x1080
Network:         WiFi, stable connection (50 Mbps)
API version:     Payment Service v2.1
Payment Gateway: Stripe API v2023-10-16

ADDITIONAL INFORMATION:
────────────────────────────────────────────────────────
Frequency:       100% reproducible for orders ≥ 5M VND
First observed:  Dec 1, 2024 (first test of high-value payments)

Related test cases:
  • TC-PAYMENT-015: Pay with Credit Card (< 5M) → PASS
  • TC-PAYMENT-016: Pay with Credit Card (≥ 5M) → FAIL

Related defects: None

Workaround:
  • Use different payment method (COD, Bank Transfer)
  • Split order into multiple smaller orders (< 5M each)

Root Cause Analysis (Preliminary):
  • Possible: Stripe API timeout setting too low (60s)
  • Possible: Payment service request timeout configuration
  • Possible: Currency conversion issue (VND large numbers)
  • Need: Developer investigation of Stripe integration

Impact on Release:
  ⚠️  BLOCKER - Cannot release with this defect
  • Affects 15% of high-value orders
  • Critical business functionality broken

Recommended Actions:
  1. Investigate Stripe API timeout configuration
  2. Check if amount format/currency causing issue
  3. Increase timeout OR optimize payment processing
  4. Add error handling and retry logic
  5. Test with various high-value amounts (5M - 50M)

═══════════════════════════════════════════════════════════
```

### Defect 2: High Severity Search Issue

```
═══════════════════════════════════════════════════════════
DEFECT REPORT: DEF-045
═══════════════════════════════════════════════════════════

BASIC INFORMATION:
────────────────────────────────────────────────────────
Defect ID:        DEF-045
Title:            Product search with Vietnamese accents returns empty results
Reported by:      [Your Name]
Date reported:    [Date]
Environment:      QA
Build:            v2.0-RC3
Severity:         HIGH
Priority:         P1
Component:        Search Module
Status:           Assigned → In Progress

DESCRIPTION:
────────────────────────────────────────────────────────
When user searches for products using Vietnamese keywords with
accents (e.g., "áo khoác", "điện thoại"), the search returns
0 results even though matching products exist in database.

Search without accents works correctly (e.g., "ao khoac").

Impact:
• 70% of users search with Vietnamese accents
• Core functionality broken for majority of users
• Poor user experience → lost sales

STEPS TO REPRODUCE:
────────────────────────────────────────────────────────
1. Go to homepage
2. Enter search keyword: "áo khoác"
3. Click Search button
4. Observe results

EXPECTED RESULT:
────────────────────────────────────────────────────────
✅ Display 1,234 products matching "áo khoác"
✅ Products with "áo", "khoác" in name/description shown

ACTUAL RESULT:
────────────────────────────────────────────────────────
❌ Message: "No products found"
❌ 0 results displayed
❌ Suggestion: "Try different keywords"

But searching "ao khoac" (no accents) → 1,234 results ✅

TEST DATA:
────────────────────────────────────────────────────────
Test Cases:
┌────────────────────────┬──────────┬─────────────────┐
│ Keyword                │ Expected │ Actual          │
├────────────────────────┼──────────┼─────────────────┤
│ "áo khoác"             │ 1,234    │ 0 ❌            │
│ "ao khoac" (no accent) │ 1,234    │ 1,234 ✅        │
│ "điện thoại"           │ 3,456    │ 0 ❌            │
│ "dien thoai"           │ 3,456    │ 3,456 ✅        │
│ "túi xách"             │ 892      │ 0 ❌            │
│ "tui xach"             │ 892      │ 892 ✅          │
└────────────────────────┴──────────┴─────────────────┘

EVIDENCE:
────────────────────────────────────────────────────────
Screenshots: [Attached]
API Request:
  GET /api/search?q=áo+khoác
  Response: {"results": [], "total": 0}

Root Cause (Suspected):
  • Search index not configured for Vietnamese
  • Elasticsearch analyzer missing Vietnamese support
  • Accent normalization not implemented

RECOMMENDED FIX:
────────────────────────────────────────────────────────
• Configure Elasticsearch with Vietnamese analyzer
• Add accent-insensitive search
• Reindex all products

═══════════════════════════════════════════════════════════
```

---

## 📊 Test Execution & Reporting (Giai đoạn 7)

### Test Progress Report (Week 3)

```
═══════════════════════════════════════════════════════════
SHOPVN v2.0 - WEEKLY TEST PROGRESS REPORT
Week 3: Sprint 2, Day 1-5
Date: [Date]
═══════════════════════════════════════════════════════════

📊 OVERALL STATUS: 🟡 AT RISK

───────────────────────────────────────────────────────

1. TEST EXECUTION SUMMARY
───────────────────────────────────────────────────────

Test Cases:
• Total: 300
• Executed: 210 (70%)
• Passed: 188 (89% pass rate)
• Failed: 22 (11%)
• Blocked: 5 (by DEF-090)
• Not executed: 90

Velocity: 42 TCs/day (target: 45 TCs/day)
ETA: 2.1 days remaining (on track for Week 4 Day 2)

Progress vs Plan:
Planned: 75% by end of Week 3
Actual: 70%
Gap: -5% (1 day behind)

───────────────────────────────────────────────────────

2. DEFECTS
───────────────────────────────────────────────────────

New defects this week: 12
Total open defects: 18

By Severity:
• Critical: 2 (DEF-090, DEF-101) 🔴
• High: 3 (DEF-045, DEF-089, DEF-102)
• Medium: 8
• Low: 5

Top Critical Defects:

DEF-090: Payment fails for orders > 5M
  • Status: In Progress (Dev fixing)
  • ETA: End of today
  • Blocking: 5 test cases (payment flows)
  • Risk: HIGH - Blocks release

DEF-101: Credit card authorization timeout
  • Status: New
  • Assigned to: Backend Team
  • Impact: Cannot complete credit card payments
  • Risk: HIGH - Blocks release

───────────────────────────────────────────────────────

3. TEST COVERAGE
───────────────────────────────────────────────────────

By Epic:
  Epic 1 (User Management):    100% ✅
  Epic 2 (Product):             95%  ✅
  Epic 3 (Shopping Cart):       85%  ⚠️
  Epic 4 (Checkout/Payment):    50%  🔴
  Epic 5 (Orders):              40%  🔴

Requirements Coverage: 85%
High-Risk Coverage: 100% ✅

───────────────────────────────────────────────────────

4. RISKS & ISSUES
───────────────────────────────────────────────────────

🔴 HIGH RISK: Payment Module Defects
  • 2 critical defects in payment
  • Blocking 5 test cases
  • May delay release by 2-3 days
  • Mitigation: Developers working overtime

🟡 MEDIUM RISK: Behind Schedule
  • 5% behind plan (1 day)
  • Need to catch up Week 4
  • Mitigation: Focus on high-priority TCs

🟢 RESOLVED: Environment Stability
  • Was unstable Week 2
  • Fixed this week ✅

───────────────────────────────────────────────────────

5. NEXT WEEK PLAN (Week 4)
───────────────────────────────────────────────────────

Mon-Tue:
  • Complete Epic 4-5 testing (90 TCs)
  • Retest fixed critical defects

Wed:
  • Regression testing (200 TCs automated)
  • Performance testing

Thu:
  • UAT support
  • Fix any new issues

Fri:
  • Test completion report
  • Release decision meeting

───────────────────────────────────────────────────────

6. RECOMMENDATIONS
───────────────────────────────────────────────────────

1. ⚡ URGENT: Fix DEF-090 and DEF-101 this week
   → Blocks release, highest priority

2. 📈 Increase velocity to 50 TCs/day Week 4
   → Catch up 1-day delay

3. 🎯 Focus on Epic 4-5 (Checkout, Orders)
   → Behind schedule, critical functionality

4. 🔄 Daily standup on critical defects
   → Track progress, unblock quickly

───────────────────────────────────────────────────────

PREPARED BY:
[Your Name] - Test Lead
Date: [Date]
═══════════════════════════════════════════════════════════
```

---

## 🎯 Final Deliverables Checklist

```
┌─────────────────────────────────────────────────────────┐
│           PROJECT DELIVERABLES CHECKLIST                │
├─────────────────────────────────────────────────────────┤
│                                                         │
│  PHASE 1: PLANNING                                      │
│  [✓] Test Plan Document                                 │
│  [✓] Risk Analysis                                      │
│  [✓] Test Estimation                                    │
│  [✓] Test Schedule                                      │
│  [✓] Resource Allocation                                │
│                                                         │
│  PHASE 2: DESIGN                                        │
│  [✓] Requirements Review Report (Static Testing)        │
│  [✓] Test Cases (300+ TCs)                              │
│      [✓] Epic 1: User Management (60 TCs)               │
│      [✓] Epic 2: Product (50 TCs)                       │
│      [✓] Epic 3: Shopping Cart (70 TCs)                 │
│      [✓] Epic 4: Checkout/Payment (80 TCs)              │
│      [✓] Epic 5: Orders (40 TCs)                        │
│  [✓] Test Data Sets                                     │
│  [✓] Traceability Matrix (RTM)                          │
│                                                         │
│  PHASE 3: EXECUTION                                     │
│  [✓] Test Execution Logs                                │
│  [✓] Defect Reports (~15 sample defects)                │
│  [✓] Daily Status Reports                               │
│  [✓] Weekly Progress Reports                            │
│  [✓] Test Metrics Dashboard                             │
│                                                         │
│  PHASE 4: COMPLETION                                    │
│  [✓] Test Completion Report                             │
│  [✓] Defect Analysis Report                             │
│  [✓] Lessons Learned Document                           │
│  [✓] Recommendations for Production                     │
│                                                         │
│  BONUS:                                                 │
│  [✓] Automation Strategy                                │
│  [✓] CI/CD Integration Plan                             │
│  [✓] Performance Test Results                           │
│                                                         │
└─────────────────────────────────────────────────────────┘
```

---

## 📚 Learning Checklist

Sau khi hoàn thành project này, bạn đã apply:

```
✅ GIAI ĐOẠN 1: Testing Fundamentals
   [✓] Hiểu được test objectives
   [✓] Áp dụng 7 testing principles
   [✓] Testing vs Debugging
   [✓] Test activities trong STLC

✅ GIAI ĐOẠN 2: Static Testing
   [✓] Requirements review
   [✓] Tìm defects trong requirements
   [✓] Review process và roles

✅ GIAI ĐOẠN 3: Test Levels & Types
   [✓] Component, Integration, System, Acceptance testing
   [✓] Functional vs Non-functional testing
   [✓] Confirmation và Regression testing

✅ GIAI ĐOẠN 4: Black-Box Techniques
   [✓] Equivalence Partitioning (Email, Password)
   [✓] Boundary Value Analysis (Quantity, Price)
   [✓] Decision Table Testing (Discount calculation)
   [✓] State Transition Testing (Order lifecycle)

✅ GIAI ĐOẠN 5: Other Techniques
   [✓] White-box (Code coverage concepts)
   [✓] Experience-based (Error guessing, Exploratory)
   [✓] Collaboration (User stories, Acceptance criteria)

✅ GIAI ĐOẠN 6: Test Management Part 1
   [✓] Test Planning (Entry/Exit criteria, Test Pyramid)
   [✓] Test Estimation (Three-point method)
   [✓] Test Prioritization (Risk-based)
   [✓] Risk Management (Product & Project risks)

✅ GIAI ĐOẠN 7: Test Management Part 2
   [✓] Test Monitoring (Metrics, Dashboards)
   [✓] Test Control (Corrective actions)
   [✓] Test Reporting (Progress vs Completion)
   [✓] Configuration Management (Traceability Matrix)
   [✓] Defect Management (Lifecycle, Severity vs Priority)
```

---

## 🎓 Next Steps

1. **Complete this project** (5-7 days)
2. **Self-review**:
   - Did you apply all techniques correctly?
   - Are test cases clear and complete?
   - Is traceability matrix accurate?
3. **Move to Project 2**: Mobile Banking Testing (different domain)
4. **Then Project 3**: Education Platform Testing
5. **Final preparation**: Mock exams và ôn tập ISTQB

**Good luck! 🚀**

---

**Note**: This is a COMPREHENSIVE practical project. Take your time, apply everything you learned, and refer back to modules 1-7 as needed. Quality over speed!
