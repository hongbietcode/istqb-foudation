# MODULE 1.3: QUY TRÌNH TESTING

**Giai đoạn**: 1 - Nền tảng
**Thời lượng học**: 4-5 giờ
**Độ khó**: ⭐⭐ Trung bình

---

## MỤC TIÊU HỌC TẬP (Learning Objectives)

Sau khi hoàn thành module này, bạn sẽ có thể:

### FL-1.4.1 (K2) - Explain impact of context on test process
**Giải thích được tác động của context lên quy trình testing**

### FL-1.4.2 (K2) - Explain test activities and respective tasks
**Giải thích được các hoạt động testing và tasks tương ứng**

### FL-1.4.3 (K2) - Differentiate testware that supports test activities
**Phân biệt được các testware hỗ trợ test activities**

### FL-1.4.4 (K2) - Explain value of maintaining traceability
**Giải thích được giá trị của việc duy trì traceability**

### FL-1.4.5 (K1) - Recognize roles in testing
**Nhận biết được các vai trò trong testing**

**Business Outcomes**: FL-BO2, FL-BO10

---

## 1. TEST PROCESS (Quy trình Testing)

### 1.1. Tổng quan

**Test Process** bao gồm các hoạt động chính:

```
┌────────────────────────────────────────────────────────────┐
│                    TEST PROCESS                            │
└────────────────────────────────────────────────────────────┘

1. TEST PLANNING
   └─ Define objectives, approach, resources, schedule

2. TEST MONITORING & CONTROL
   └─ Track progress, take corrective actions

3. TEST ANALYSIS
   └─ Analyze test basis, identify test conditions

4. TEST DESIGN
   └─ Design test cases from test conditions

5. TEST IMPLEMENTATION
   └─ Create test procedures, prepare environment

6. TEST EXECUTION
   └─ Run tests, compare results, log defects

7. TEST COMPLETION
   └─ Finalize, collect data, lessons learned
```

---

## 2. TEST PLANNING (Lập kế hoạch)

### 2.1. Mục đích

- Define **test objectives**
- Define **test approach** (cách thức test)
- Determine **resources** needed (người, tools, environment)
- Schedule **when** to test
- Define **entry & exit criteria**

### 2.2. Inputs (Đầu vào)

- **Test policy** (nếu có): Organization-level testing standards
- **Test strategy** (nếu có): High-level approach
- **Product risk analysis**: Identify high-risk areas
- **Requirements**: What to test
- **Resources availability**: Who, when, budget

### 2.3. Activities (Hoạt động)

#### Activity 1: Determine scope and objectives
**Quyết định phạm vi và mục tiêu**

**Ví dụ**:
```
Project: E-commerce website

Scope:
✓ IN SCOPE:
  - Functional testing of checkout flow
  - Payment integration testing
  - Performance testing (1000 concurrent users)
  - Security testing (OWASP Top 10)

✗ OUT OF SCOPE:
  - Legacy admin panel (will be deprecated)
  - Third-party analytics (not our responsibility)

Objectives:
- Find critical defects before go-live
- Verify performance requirements met
- Ensure security standards complied
```

#### Activity 2: Define test approach
**Định nghĩa cách tiếp cận**

**Ví dụ**:
```
Approach:
- Risk-based testing: Focus high-risk areas (payment, security)
- Test levels:
  ├─ Component testing: Developers (unit tests)
  ├─ System testing: Test team
  └─ UAT: Business users
- Test types:
  ├─ Functional: Manual + Automated (Selenium)
  ├─ Performance: JMeter
  └─ Security: OWASP ZAP
- Test design techniques:
  ├─ Equivalence Partitioning
  ├─ Boundary Value Analysis
  └─ Decision Table Testing
```

#### Activity 3: Determine test resources
**Xác định tài nguyên**

```
Resources:
PEOPLE:
- Test Manager: 1 person (full-time)
- Test Analysts: 2 people (full-time)
- Automation Engineers: 1 person (part-time)

TOOLS:
- Test management: Jira + TestRail
- Automation: Selenium + Cypress
- Performance: JMeter
- CI/CD: Jenkins

ENVIRONMENT:
- Dev environment: For component testing
- Test environment: For system testing
- Staging: For UAT
- Production-like: For performance testing
```

#### Activity 4: Schedule test activities
**Lập lịch trình**

```
Timeline (8 weeks):

Week 1-2: Test Planning & Analysis
- Review requirements
- Identify test conditions
- Design test cases

Week 3-4: Test Implementation
- Create test scripts
- Setup test environment
- Prepare test data

Week 5-6: Test Execution
- Execute test cases
- Log defects
- Retest fixes

Week 7: Regression Testing
- Full regression suite
- Verify all fixes

Week 8: Test Completion
- Final reports
- Lessons learned
```

#### Activity 5: Define entry and exit criteria
**Định nghĩa tiêu chí vào/ra**

```
ENTRY CRITERIA (để bắt đầu testing):
✓ All features code-complete
✓ Build deployed to test environment
✓ Test environment stable
✓ Test cases reviewed and approved
✓ Test data prepared

EXIT CRITERIA (để kết thúc testing):
✓ All test cases executed
✓ 95% test cases passed
✓ Zero critical/high defects open
✓ All medium defects fixed or deferred
✓ Regression testing passed
✓ Performance benchmarks met
✓ Test completion report signed off
```

### 2.4. Outputs (Đầu ra)

**Test Plan Document** bao gồm:
- Test scope
- Test objectives
- Test approach
- Resources (people, tools, environment)
- Schedule
- Entry & exit criteria
- Risks and contingencies

---

## 3. TEST MONITORING & CONTROL

### 3.1. Test Monitoring (Giám sát)

**Mục đích**: Track test progress so với plan

**Metrics thường dùng**:
```
Progress Metrics:
- Test cases executed: 250/500 (50%)
- Test cases passed: 200/250 (80%)
- Test cases failed: 50/250 (20%)
- Defects found: 45
  ├─ Critical: 2
  ├─ High: 8
  ├─ Medium: 20
  └─ Low: 15

Time Metrics:
- Planned: 6 weeks
- Actual: 4 weeks elapsed
- Remaining: 2 weeks
- On track: Yes ✓

Coverage Metrics:
- Requirement coverage: 85%
- Code coverage: 78%
```

**Reporting**:
- Daily standup: Quick status update
- Weekly report: Detailed metrics
- Ad-hoc: When major issues arise

### 3.2. Test Control (Kiểm soát)

**Mục đích**: Take corrective actions khi deviate from plan

**Ví dụ actions**:

```
ISSUE: Test execution behind schedule (only 50% done, should be 75%)

CONTROL ACTIONS:
✓ Re-prioritize: Focus on high-risk test cases first
✓ Add resources: Bring in 1 more tester
✓ Reduce scope: Defer low-priority tests
✓ Extend timeline: Request 1 week extension
✓ Increase automation: Automate repetitive tests
```

```
ISSUE: Too many critical defects (10 critical bugs found)

CONTROL ACTIONS:
✓ Stop testing: Pause until critical bugs fixed
✓ Extra code review: For high-defect modules
✓ Regression testing: After each critical fix
✓ Risk assessment: Re-evaluate readiness for release
```

---

## 4. TEST ANALYSIS (Phân tích)

### 4.1. Mục đích

- Analyze **test basis** (requirements, specs, design)
- Identify **test conditions** (what to test)
- Identify **defects in test basis** (ambiguity, incompleteness)

### 4.2. Inputs

- **Test basis**:
  - Requirements documents
  - User stories
  - Design specifications
  - Use cases
  - Risk analysis results

### 4.3. Activities

#### Activity 1: Analyze test basis
**Phân tích cơ sở testing**

**Ví dụ**: Analyze user story
```
User Story:
"As a customer, I want to apply a discount code
so that I can get a discount on my order"

ANALYSIS:
Questions to clarify:
- Discount code format? (uppercase/lowercase?)
- Discount type? (percentage/fixed amount?)
- Minimum order value?
- Can combine multiple codes?
- Expiry date handling?
- Max usage limit per user?

→ Need clarification from PO!
```

#### Activity 2: Identify test conditions
**Xác định điều kiện test**

```
From user story above, test conditions:

TC-1: Valid discount code applied successfully
TC-2: Invalid discount code rejected
TC-3: Expired discount code rejected
TC-4: Discount code already used (max limit)
TC-5: Order below minimum value
TC-6: Multiple discount codes combination
TC-7: Case sensitivity of code
TC-8: Special characters in code
TC-9: Discount calculation correctness
TC-10: UI feedback messages
```

#### Activity 3: Define test data needs
**Xác định nhu cầu test data**

```
Test Data needed:
- Valid discount codes: SUMMER2024, WELCOME10
- Expired codes: EXPIRED2023
- Invalid codes: NOTEXIST, 123XYZ
- Edge cases: Very long code, special chars (@#$%)
- Order amounts: Below min, at min, above min
- User accounts: New user, existing user, loyalty member
```

### 4.4. Outputs

- **Test conditions** list
- **Test data requirements**
- **Defects in test basis** (ambiguities, missing info)
- **Bi-directional traceability**: Requirements ↔ Test conditions

---

## 5. TEST DESIGN (Thiết kế)

### 5.1. Mục đích

- Elaborate test conditions into **detailed test cases**
- Design **test procedures** (order of test cases)
- Identify **test data values**

### 5.2. Activities

#### Activity 1: Design test cases
**Thiết kế test cases**

**Ví dụ**: From test condition "Valid discount code applied"

```
TEST CASE: TC-DISC-001

Title: Apply valid percentage discount code

Preconditions:
- User logged in
- Shopping cart has 1 item (price: 1,000,000 VND)
- Discount code SUMMER20 valid (20% off, min order 500k)

Test Steps:
1. Navigate to checkout page
2. Enter discount code "SUMMER20" in promo code field
3. Click "Apply" button

Test Data:
- Discount code: SUMMER20
- Cart total: 1,000,000 VND

Expected Results:
- Success message: "Discount applied successfully"
- Discount amount: -200,000 VND (20%)
- New total: 800,000 VND
- Discount code field disabled (cannot apply again)

Priority: High
```

#### Activity 2: Design test procedures
**Thiết kế thủ tục test**

```
TEST PROCEDURE: TP-CHECKOUT-001

Name: End-to-end checkout with discount

Test Cases (in order):
1. TC-CART-001: Add item to cart
2. TC-CART-002: Update quantity
3. TC-CART-003: View cart summary
4. TC-DISC-001: Apply valid discount code  ← From above
5. TC-PAY-001: Select payment method
6. TC-PAY-002: Complete payment
7. TC-ORD-001: Verify order confirmation

Purpose: Verify complete checkout flow with discount
```

#### Activity 3: Identify test data
**Xác định test data cụ thể**

```
Test Data Set: TD-DISC-001

Discount Codes:
├─ SUMMER20: 20% off, min 500k, expires 31/8/2024
├─ WELCOME10: 10% off, no min, expires 31/12/2024
├─ FREESHIP: Free shipping, min 200k, expires 30/9/2024
└─ VIP50: 50% off, min 2tr, max 500k, VIP only

Users:
├─ Regular user: user1@test.com / Pass123
├─ VIP user: vip@test.com / VipPass123
└─ New user: new@test.com / NewPass123

Products:
├─ Product A: 500,000 VND
├─ Product B: 1,000,000 VND
└─ Product C: 2,500,000 VND
```

### 5.3. Outputs

- **Test cases**: Detailed steps with expected results
- **Test procedures**: Sequences of test cases
- **Test data**: Specific values for testing
- **Traceability**: Test conditions ↔ Test cases

---

## 6. TEST IMPLEMENTATION (Triển khai)

### 6.1. Mục đích

- Create/acquire **testware** needed for execution
- Prepare **test environment**
- Prepare **test data**
- Build **test suites** from test procedures

### 6.2. Activities

#### Activity 1: Develop/prioritize test procedures
**Phát triển và ưu tiên test procedures**

```
Test Suite: Smoke Tests (Run first)
Priority: Critical
├─ TP-LOGIN-001: Login functionality
├─ TP-SEARCH-001: Search products
└─ TP-CART-001: Add to cart

Test Suite: Checkout Tests
Priority: High
├─ TP-CHECKOUT-001: Standard checkout
├─ TP-CHECKOUT-002: Checkout with discount
└─ TP-CHECKOUT-003: Checkout with shipping

Test Suite: Regression Tests
Priority: Medium
├─ All functional tests
└─ Integration tests
```

#### Activity 2: Create automated test scripts
**Tạo automation scripts**

**Ví dụ** (Selenium - pseudo code):
```javascript
// TC-DISC-001: Apply valid discount code

test('Apply valid percentage discount code', async () => {
  // Preconditions
  await login('user1@test.com', 'Pass123');
  await addToCart('Product B'); // 1,000,000 VND

  // Test steps
  await navigateTo('/checkout');
  await fillField('promo_code', 'SUMMER20');
  await click('apply_button');

  // Verify expected results
  expect(getSuccessMessage()).toBe('Discount applied successfully');
  expect(getDiscountAmount()).toBe('-200,000 VND');
  expect(getTotalAmount()).toBe('800,000 VND');
  expect(isFieldDisabled('promo_code')).toBe(true);
});
```

#### Activity 3: Build test suites
**Xây dựng test suites**

```
Regression Suite: REGRESSION-FULL

Includes:
- Smoke tests (30 test cases - 30 mins)
- Functional tests (200 test cases - 8 hours)
- Integration tests (50 test cases - 3 hours)

Total: 280 test cases, ~12 hours manual execution
Automation: 150 test cases automated → 2 hours execution
```

#### Activity 4: Prepare test environment
**Chuẩn bị môi trường**

```
Test Environment Setup:

INFRASTRUCTURE:
✓ Web server: Nginx configured
✓ App server: Node.js 18.x installed
✓ Database: PostgreSQL 14 with test data
✓ Cache: Redis configured

APPLICATIONS:
✓ Frontend deployed: v1.2.3
✓ Backend API deployed: v2.3.4
✓ Payment gateway: Sandbox mode

NETWORK:
✓ Firewall rules configured
✓ SSL certificates installed
✓ DNS configured: test.example.com

TOOLS:
✓ Test management: TestRail connected
✓ Defect tracking: Jira integrated
✓ Automation: Selenium Grid ready
```

#### Activity 5: Prepare test data
**Chuẩn bị test data**

```
Test Data loaded:

USERS:
✓ 100 test users created
✓ 10 VIP users created
✓ 5 admin users created

PRODUCTS:
✓ 500 products in catalog
✓ 50 products with discounts
✓ 20 products out of stock

TRANSACTIONS:
✓ 1000 historical orders
✓ 50 pending orders
✓ 100 discount codes active

DATABASE:
✓ Backup created: test-data-v1.sql
✓ Reset script ready: reset-db.sh
```

### 6.3. Outputs

- **Test procedures** ready to execute
- **Automated test scripts**
- **Test suites** organized
- **Test environment** configured
- **Test data** loaded
- **Test execution schedule**

---

## 7. TEST EXECUTION (Thực thi)

### 7.1. Mục đích

- **Execute** test procedures
- **Compare** actual results vs expected results
- **Log** defects for failures
- **Log** test results

### 7.2. Activities

#### Activity 1: Execute tests
**Thực thi tests**

**Manual Testing**:
```
Tester execute TC-DISC-001:

Step 1: Navigate to checkout ✓
Step 2: Enter code "SUMMER20" ✓
Step 3: Click "Apply" button ✓

Results:
✓ Success message shown ✓
✓ Discount: -200,000 VND ✓
✓ Total: 800,000 VND ✓
✓ Code field disabled ✓

Status: PASSED
```

**Automated Testing**:
```
Running: Regression Suite
[========================================] 150/150

Results:
- Passed: 142 (94.7%)
- Failed: 5 (3.3%)
- Blocked: 3 (2%)

Duration: 1h 45m
```

#### Activity 2: Compare results
**So sánh kết quả**

```
TC-PAY-003: Payment with credit card

Expected Result:
- Payment successful
- Order status: "Paid"
- Confirmation email sent

Actual Result:
- Payment successful ✓
- Order status: "Pending" ❌ DIFFERENCE!
- Confirmation email sent ✓

→ FAILED (Status incorrect)
```

#### Activity 3: Log defects
**Ghi nhận lỗi**

```
DEFECT REPORT: BUG-1234

Title: Order status incorrect after payment

Severity: High
Priority: High

Description:
After successful credit card payment, order status
shows "Pending" instead of "Paid"

Steps to Reproduce:
1. Add product to cart
2. Checkout with credit card
3. Complete payment successfully
4. Check order status

Expected: Status = "Paid"
Actual: Status = "Pending"

Environment: Test server v1.2.3
Found by: TC-PAY-003
```

#### Activity 4: Log test results
**Ghi nhận kết quả**

```
Test Execution Log: 2024-11-23

Summary:
- Test cases executed: 50
- Passed: 42 (84%)
- Failed: 5 (10%)
- Blocked: 3 (6%)

Defects logged: 5
- BUG-1234: Order status incorrect (High)
- BUG-1235: Discount not applied (Critical)
- BUG-1236: Email template broken (Low)
- BUG-1237: Performance slow (Medium)
- BUG-1238: UI alignment issue (Low)

Blocked tests:
- TC-PAY-004: Blocked by BUG-1235
- TC-PAY-005: Blocked by BUG-1235
- TC-SHIP-001: Test data missing
```

### 7.3. Outputs

- **Test execution results**
- **Defect reports**
- **Test logs**
- **Actual vs expected comparison**

---

## 8. TEST COMPLETION (Hoàn thành)

### 8.1. Mục đích

- Finalize testing
- Archive testware
- Analyze lessons learned
- Use information to improve

### 8.2. Activities

#### Activity 1: Check exit criteria
**Kiểm tra tiêu chí ra**

```
Exit Criteria Check:

✓ All test cases executed: 500/500 (100%)
✓ Pass rate: 95% (475/500) - Target: 95% ✓
✓ Critical defects: 0 open - Target: 0 ✓
✓ High defects: 1 open (deferred) - Target: 0 ❌
✗ Medium defects: 5 open (3 fixed, 2 deferred)
✓ Regression passed: Yes ✓
✓ Performance: Response < 2s ✓
✓ Security scan: No critical issues ✓

DECISION: APPROVED for release
(1 High defect deferred to next release with PO approval)
```

#### Activity 2: Create test completion report
**Tạo báo cáo hoàn thành**

```
TEST COMPLETION REPORT
Project: E-commerce Website v1.2.3
Test Period: 2024-10-01 to 2024-11-23

EXECUTIVE SUMMARY:
Quality Level: GOOD - Approved for production release

TEST EXECUTION:
- Total test cases: 500
- Executed: 500 (100%)
- Passed: 475 (95%)
- Failed: 25 (5%)

DEFECTS:
- Total found: 45
- Fixed: 40
- Deferred: 5
- Critical: 0
- High: 1 (deferred with approval)

COVERAGE:
- Requirement coverage: 98%
- Code coverage: 82%

RISKS:
- 1 High defect deferred (BUG-1240: Edge case in discount)
- Mitigation: Document known issue, monitor in production

RECOMMENDATION: GO LIVE
```

#### Activity 3: Archive testware
**Lưu trữ testware**

```
Testware Archive: project-v1.2.3-testware.zip

Contents:
├─ test-plan.pdf
├─ test-cases/
│   ├─ functional-tests.xlsx
│   ├─ performance-tests.xlsx
│   └─ security-tests.xlsx
├─ test-data/
│   ├─ test-users.csv
│   └─ test-products.csv
├─ test-scripts/
│   ├─ automation/
│   └─ manual/
├─ test-results/
│   ├─ execution-logs/
│   └─ screenshots/
├─ defect-reports/
│   └─ all-defects-export.csv
└─ test-completion-report.pdf

Stored: SharePoint/Projects/Ecommerce/Testing/
Retention: 2 years
```

#### Activity 4: Lessons learned
**Bài học kinh nghiệm**

```
LESSONS LEARNED

WHAT WENT WELL:
✓ Risk-based testing helped prioritize effectively
✓ Early automation saved time in regression
✓ Daily standups kept team aligned
✓ Good collaboration with dev team

WHAT COULD IMPROVE:
✗ Test environment unstable in week 3 (delayed 2 days)
✗ Test data preparation took longer than planned
✗ Some requirements ambiguous (caused rework)
✗ Performance testing started too late

ACTION ITEMS:
→ Improve test environment stability (DevOps)
→ Start test data prep earlier (1 week before execution)
→ Implement requirement review checklist
→ Include performance testing from week 1

BEST PRACTICES TO CONTINUE:
→ Pair testing for complex features
→ Automation-first for regression
→ Weekly test summary to stakeholders
```

### 8.3. Outputs

- **Test completion report**
- **Archived testware**
- **Lessons learned document**
- **Process improvement recommendations**

---

## 9. TESTWARE

### 9.1. Định nghĩa

**Testware**: Tất cả work products được tạo ra trong test process.

### 9.2. Các loại Testware

| Test Activity | Testware Created |
|---------------|------------------|
| **Planning** | Test plan, Test strategy, Schedule |
| **Monitoring** | Test progress reports, Metrics dashboards |
| **Analysis** | Test conditions, Requirements traceability matrix |
| **Design** | Test cases, Test procedures, Test data specs |
| **Implementation** | Test scripts (automated), Test suites, Test data |
| **Execution** | Test logs, Defect reports, Test results |
| **Completion** | Test completion report, Lessons learned |

### 9.3. Ví dụ Testware

```
PROJECT TESTWARE REPOSITORY

/test-planning/
├─ test-plan-v1.0.pdf
├─ test-strategy.md
└─ resource-allocation.xlsx

/test-cases/
├─ functional/
│   ├─ login-tests.xlsx
│   ├─ checkout-tests.xlsx
│   └─ payment-tests.xlsx
├─ non-functional/
│   ├─ performance-tests.jmx
│   └─ security-tests.md

/test-scripts/
├─ selenium/
│   ├─ login.spec.js
│   ├─ checkout.spec.js
│   └─ regression-suite.js
└─ api/
    └─ api-tests.postman.json

/test-data/
├─ users.csv
├─ products.json
└─ test-data-generator.py

/test-results/
├─ 2024-11-20-execution-log.html
├─ 2024-11-21-execution-log.html
└─ defects-export.csv

/test-reports/
├─ weekly-report-w1.pdf
├─ weekly-report-w2.pdf
└─ test-completion-report.pdf
```

---

## 10. TRACEABILITY (Khả năng truy vết)

### 10.1. Định nghĩa

**Traceability**: Khả năng trace relationships giữa:
- Requirements → Test cases
- Test cases → Test results
- Test cases → Defects

### 10.2. Tại sao quan trọng?

#### 1. Ensure coverage
**Đảm bảo độ bao phủ**
```
Requirement REQ-001 được test bởi:
├─ TC-001
├─ TC-002
└─ TC-003

→ Biết requirement nào đã/chưa được test
```

#### 2. Impact analysis
**Phân tích tác động**
```
Requirement REQ-005 thay đổi

Affected test cases:
├─ TC-015 (need update)
├─ TC-016 (need update)
└─ TC-020 (may need update)

→ Biết test cases nào cần review/update
```

#### 3. Defect analysis
**Phân tích lỗi**
```
Defect BUG-123 found in TC-050

Related to:
└─ Requirement REQ-010

Similar defects:
├─ BUG-100 (same requirement)
└─ BUG-105 (same requirement)

→ Pattern: REQ-010 area has many bugs
→ Action: Extra testing needed
```

### 10.3. Traceability Matrix

```
REQUIREMENTS TRACEABILITY MATRIX

REQ ID | Description        | Test Cases       | Status  | Defects
-------|--------------------|-----------------  |---------|----------
REQ-001| User login        | TC-001, TC-002   | Passed  | -
REQ-002| Forgot password   | TC-003, TC-004   | Passed  | -
REQ-003| Apply discount    | TC-010 to TC-015 | Failed  | BUG-123
REQ-004| Payment process   | TC-020 to TC-025 | Blocked | BUG-124
REQ-005| Order tracking    | -                | Not tested | -

Coverage: 80% (4/5 requirements tested)
```

### 10.4. Bi-directional Traceability

```
FORWARD TRACEABILITY (Requirements → Tests):
REQ-003: Apply discount code
  ├─ TC-010: Valid code
  ├─ TC-011: Invalid code
  ├─ TC-012: Expired code
  ├─ TC-013: Case sensitivity
  ├─ TC-014: Special characters
  └─ TC-015: Multiple codes

BACKWARD TRACEABILITY (Tests → Requirements):
TC-010: Apply valid discount code
  └─ Verifies: REQ-003 (Apply discount)
```

---

## 11. TEST ROLES (Vai trò trong Testing)

### 11.1. Hai vai trò chính

#### Test Management Role
**Chịu trách nhiệm**: Overall test process

**Responsibilities**:
- Write test plan
- Monitor and control testing
- Report to stakeholders
- Manage test team
- Schedule testing activities
- Allocate resources

**Titles**: Test Manager, Test Lead, QA Manager

---

#### Testing Role
**Chịu trách nhiệm**: Technical test activities

**Responsibilities**:
- Analyze test basis
- Design test cases
- Implement tests (manual/automated)
- Execute tests
- Log defects
- Review testware

**Titles**: Tester, Test Analyst, QA Engineer, Test Automation Engineer

### 11.2. Bảng so sánh

| Aspect | Test Manager | Tester |
|--------|--------------|--------|
| **Focus** | Management, planning | Technical, execution |
| **Activities** | Plan, monitor, report | Design, implement, execute |
| **Decisions** | Strategic | Tactical |
| **Stakeholders** | Management, clients | Dev team, test manager |
| **Deliverables** | Test plan, reports | Test cases, defects |

### 11.3. Collaboration

```
PROJECT TEAM STRUCTURE

Product Owner
    │
    ├─ Development Team
    │   ├─ Developers (write code)
    │   └─ DevOps (infrastructure)
    │
    └─ Test Team
        ├─ Test Manager (plan, manage)
        └─ Testers (design, execute)

COLLABORATION:
- PO ↔ Test Manager: Requirements, priorities
- Test Manager ↔ Dev Lead: Schedule, resources
- Testers ↔ Developers: Defects, clarifications
- Whole team: Daily standups, retrospectives
```

---

## 12. CONTEXT AND TEST PROCESS

### 12.1. Context factors

Test process bị ảnh hưởng bởi:

#### 1. SDLC Model
```
Waterfall:
- Sequential testing phase
- Formal test planning
- Extensive documentation

Agile:
- Testing throughout sprints
- Lightweight documentation
- Continuous testing
```

#### 2. Test Levels
```
Component Testing:
- Developers do most testing
- Focus on code coverage
- Automated unit tests

Acceptance Testing:
- Business users involved
- Focus on business requirements
- Manual exploratory testing
```

#### 3. Product Characteristics
```
Safety-critical (Medical device):
- Rigorous test process
- 100% requirement coverage
- Formal reviews
- Extensive documentation

Mobile Game:
- Flexible test process
- Focus on UX
- Beta testing
- Minimal documentation
```

#### 4. Risk Levels
```
High-risk (Banking app):
- Extensive security testing
- Performance testing
- Disaster recovery testing

Low-risk (Internal tool):
- Basic functional testing
- Minimal performance testing
- No security audit
```

---

## 13. PRACTICE QUESTIONS

### Question 1 (K2)
Which of the following is the main objective of test completion activities?

A. To verify that all defects have been fixed
B. To ensure the test environment is ready for the next project
C. To collect and archive testware for future reference
D. To check whether all test cases have been executed

**Đáp án**: C
**Giải thích**: Main objective of test completion là archive testware, lessons learned, và analyze data for improvements.

---

### Question 2 (K2)
Why is traceability between test basis and test cases important?

A. It enables proper control over the test process
B. It allows testing to be automated
C. It enables verification of test coverage and impact analysis
D. It prevents defects from being introduced into the product

**Đáp án**: C
**Giải thích**: Traceability giúp verify coverage và analyze impact khi requirements change.

---

### Question 3 (K1)
Which of the following is a test management activity?

A. Designing test cases
B. Writing automated test scripts
C. Monitoring test progress
D. Executing test procedures

**Đáp án**: C
**Giải thích**: Monitoring test progress là test management activity. A, B, D là testing activities.

---

### Question 4 (K2)
During which test activity is the actual result compared with the expected result?

A. Test analysis
B. Test design
C. Test implementation
D. Test execution

**Đáp án**: D
**Giải thích**: During test execution, actual results được compare với expected results.

---

### Question 5 (K2)
Which of the following is testware created during test implementation?

A. Test conditions
B. Test cases
C. Test suites
D. Defect reports

**Đáp án**: C
**Giải thích**: Test suites được tạo trong test implementation. A là test analysis, B là test design, D là test execution.

---

## 14. SELF-ASSESSMENT CHECKLIST

- [ ] Tôi có thể liệt kê 7 test activities và giải thích mỗi activity
- [ ] Tôi hiểu inputs và outputs của mỗi test activity
- [ ] Tôi biết các loại testware được tạo ra ở mỗi activity
- [ ] Tôi hiểu tại sao traceability quan trọng
- [ ] Tôi có thể phân biệt test management role vs testing role
- [ ] Tôi hiểu context ảnh hưởng test process như thế nào
- [ ] Tôi có thể cho ví dụ về entry và exit criteria

**Đạt ≥6/7** → Sẵn sàng cho Module 1.4!

---

## 15. KEY TAKEAWAYS

1. **7 Test Activities**: Planning → Monitoring/Control → Analysis → Design → Implementation → Execution → Completion
2. **Testware**: Work products tạo ra ở mỗi activity (test plan, test cases, test scripts, reports, etc.)
3. **Traceability**: Requirements ↔ Test cases ↔ Results ↔ Defects (quan trọng cho coverage và impact analysis)
4. **Test Roles**: Test Manager (manage) vs Tester (execute)
5. **Context matters**: SDLC, product type, risk level ảnh hưởng test process

---

## NEXT STEPS

📚 **Tiếp theo**: [Module 1.4: Công cụ Testing](module-1.4-cong-cu-testing.md)
💪 **Bài tập**: Sau khi học xong Module 1.4 → [Bài tập Giai đoạn 1](bai-tap-giai-doan-1.md)

**Ôn tập**: Review 7 test activities và testware của mỗi activity

---

**Thời gian học**: 4-5 giờ
