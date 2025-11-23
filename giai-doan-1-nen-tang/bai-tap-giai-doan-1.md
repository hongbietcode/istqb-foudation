# BÀI TẬP GIAI ĐOẠN 1: NỀN TẢNG

**Tổng thời gian**: 4-6 giờ
**Số bài tập**: 15 exercises + 40 câu trắc nghiệm

---

## HƯỚNG DẪN SỬ DỤNG

### Cách làm bài tập hiệu quả:

1. **Tự làm trước**: Không xem đáp án ngay
2. **Viết ra giấy**: Giúp ghi nhớ tốt hơn
3. **Check đáp án**: Sau khi hoàn thành
4. **Hiểu tại sao**: Nếu sai, hiểu tại sao sai
5. **Làm lại**: Các bài sai sau 2-3 ngày

### Tiêu chí đạt:
- **Exercises**: Đạt ≥12/15 bài (80%)
- **Multiple Choice**: Đạt ≥32/40 câu (80%)
- **Overall**: ≥80% → Pass, tiến sang Giai đoạn 2

---

## PART A: PRACTICAL EXERCISES

### Exercise 1: Test Objectives

**Scenario**: Bạn là tester cho một mobile banking app mới.

**Câu hỏi**: Liệt kê 5 test objectives chính cho project này và giải thích tại sao mỗi objective quan trọng.

**Format trả lời**:
```
Objective 1: [Tên objective]
Tại sao quan trọng: [Giải thích]

[Repeat cho 5 objectives]
```

<details>
<summary><b>ĐÁP ÁN</b> (Click để xem)</summary>

```
Objective 1: Find critical security defects
Tại sao: Banking app handle sensitive financial data.
Security vulnerabilities có thể lead to data breach,
financial loss, và loss of customer trust.

Objective 2: Verify functional requirements met
Tại sao: App phải support core banking functions
(transfer, bill payment, balance check). Nếu
functions không work đúng, users không thể sử dụng.

Objective 3: Ensure performance meets requirements
Tại sao: Users expect fast response (< 2s). Slow app
dẫn đến poor user experience và app abandonment.

Objective 4: Reduce risk of production failures
Tại sao: Production failures trong banking app
= service disruption, customer complaints, regulatory
issues, và reputation damage.

Objective 5: Build confidence for go-live
Tại sao: Stakeholders cần confidence rằng app
stable và ready for thousands of users trước khi
launch to public.
```

**Scoring**:
- 5 objectives relevant: 2 points
- Clear explanations: 3 points
- Total: 5 points
</details>

---

### Exercise 2: Testing vs Debugging

**Scenario**: Developer nói với bạn: "I already tested my code, no bugs!"

**Câu hỏi**:
a) Giải thích tại sao developer testing code của họ khác với independent testing
b) Liệt kê 3 lý do tại sao vẫn cần independent testing ngay cả khi developer đã test

<details>
<summary><b>ĐÁP ÁN</b></summary>

```
a) Developer testing own code khác Independent testing:

DEVELOPER TESTING:
- Có bias (biết code works thế nào)
- Focus vào implementation (white-box)
- Có thể assume scenarios won't happen
- Debugging mindset (fix nếu thấy lỗi)
- Conflict of interest (own code)

INDEPENDENT TESTING:
- Objective (no bias)
- Focus vào requirements (black-box)
- No assumptions, test everything
- Testing mindset (find defects)
- No emotional attachment

b) 3 lý do cần independent testing:

1. DIFFERENT PERSPECTIVE:
   Developers test "does code work correctly?"
   Testers test "does it meet user needs?"
   → Find different types of defects

2. OBJECTIVITY:
   Developers unconsciously skip scenarios họ
   "know" won't be issue. Testers test everything
   → Find more edge cases

3. SPECIALIZATION:
   Testers có testing expertise (test design
   techniques, test strategies) developers
   thường không có
   → More effective testing
```

**Scoring**:
- Part a: 2.5 points
- Part b: 2.5 points (0.83/lý do)
- Total: 5 points
</details>

---

### Exercise 3: Error → Defect → Failure

**Scenario**: App Shopee có lỗi trong tính năng áp dụng voucher.

**Câu hỏi**: Tạo một example hoàn chỉnh thể hiện flow Error → Defect → Failure, bao gồm:
- Error: Hành động sai của developer
- Defect: Bug cụ thể trong code
- Execution: Test scenario
- Failure: Kết quả sai quan sát được

<details>
<summary><b>ĐÁP ÁN</b> (Example)</summary>

```
ERROR (Human mistake):
Developer hiểu nhầm requirement về voucher stacking.
Requirement: "Maximum 1 voucher per order"
Developer nghĩ: "User có thể apply multiple nếu
total discount < 50%"

DEFECT (Bug in code):
Code:
```javascript
function applyVouchers(order, vouchers) {
  let totalDiscount = 0;
  for (let voucher of vouchers) {
    totalDiscount += voucher.amount;
    if (totalDiscount <= order.total * 0.5) {
      order.applyVoucher(voucher);  // ❌ DEFECT: No check for max 1
    }
  }
}
```

EXECUTION:
User đặt order 1,000,000đ
User apply 2 vouchers:
- SAVE100K: -100,000đ
- FREESHIP: -30,000đ

FAILURE:
Expected: Only first voucher applied (SAVE100K)
          Final price: 900,000đ
          Error message: "Maximum 1 voucher per order"

Actual:   Both vouchers applied
          Final price: 870,000đ  ❌ FAILURE!
          No error message

Impact: Customer gets extra discount (loss for company)
```

**Scoring**:
- Error identified clearly: 1 point
- Defect với code example: 2 points
- Execution scenario realistic: 1 point
- Failure với expected vs actual: 1 point
- Total: 5 points
</details>

---

### Exercise 4: Root Cause Analysis

**Scenario**: App crash với error "NullPointerException at PaymentService.java:45"

**Câu hỏi**: Sử dụng 5 Whys technique để tìm root cause. Viết 5 whys và identify root cause cuối cùng.

<details>
<summary><b>ĐÁP ÁN</b> (Example)</summary>

```
SYMPTOM: App crash với NullPointerException

WHY #1: Tại sao crash?
└─ Vì biến 'user.billingAddress' là null ở line 45

WHY #2: Tại sao billingAddress null?
└─ Vì user chưa set billing address (optional field)

WHY #3: Tại sao code không check null?
└─ Vì developer assume billing address always available

WHY #4: Tại sao developer assume vậy?
└─ Vì requirement không specify rõ billing address
   là optional

WHY #5: Tại sao requirement không rõ ràng?
└─ Vì không có requirement review process trước
   khi development

ROOT CAUSE: No requirement review process

IMMEDIATE FIX: Add null check trong code
if (user.billingAddress != null) { ... }

LONG-TERM FIX:
1. Implement requirement review process
2. Review checklist phải include edge cases
3. BA training về writing clear requirements
4. Developers phải ask questions khi unclear
```

**Scoring**:
- 5 Whys logical: 2 points
- Root cause identified: 1 point
- Immediate fix: 1 point
- Long-term fix: 1 point
- Total: 5 points
</details>

---

### Exercise 5: Seven Testing Principles

**Câu hỏi**: Cho mỗi scenario sau, identify which Testing Principle được demonstrate và explain why.

**Scenario A**: Tester chạy same 100 regression tests mỗi sprint trong 6 tháng. Ban đầu tìm ra 10 bugs/sprint, bây giờ chỉ tìm 0-1 bug/sprint.

**Scenario B**: E-commerce website có 10 modules. Module "Payment" có 60% total bugs mặc dù chỉ chiếm 10% code.

**Scenario C**: Medical device software passed tất cả 1000 test cases nhưng vẫn cause patient injury khi released.

**Scenario D**: Tester estimate rằng testing toàn bộ combinations của 20 input fields sẽ take 50 years.

**Scenario E**: Bug found trong requirement phase, fixed trong 10 minutes bằng cách clarify với BA. Same bug nếu found trong production sẽ require 2 days hotfix.

<details>
<summary><b>ĐÁP ÁN</b></summary>

```
SCENARIO A: Principle #5 - Pesticide Paradox
Explanation: Same tests chạy lại nhiều lần không
còn tìm được defects mới. Tests "wear out". Cần
add new tests cho new scenarios.

SCENARIO B: Principle #4 - Defects Cluster Together
Explanation: Bugs tend to concentrate trong một số
modules nhất định. Payment module là high-defect
area, cần focus testing effort vào đó.

SCENARIO C: Principle #7 - Absence-of-Defects Fallacy
Explanation: Zero bugs không = success. Software
có thể bug-free nhưng không meet user needs hoặc
sai trong design. Need validation, not just verification.

SCENARIO D: Principle #2 - Exhaustive Testing is Impossible
Explanation: Không thể test tất cả combinations.
Must prioritize dựa trên risk và use test design
techniques để reduce số test cases cần thiết.

SCENARIO E: Principle #3 - Early Testing Saves Time and Money
Explanation: Testing và finding bugs early trong
SDLC = cheaper và faster to fix. Cost to fix tăng
exponentially theo time.
```

**Scoring**: 1 point per correct principle + explanation
- Total: 5 points
</details>

---

### Exercise 6: Test Activities

**Scenario**: Project mới - Develop mobile food delivery app (giống GrabFood).

**Câu hỏi**: Cho mỗi test activity, liệt kê 3 specific tasks bạn sẽ làm và 1 deliverable (output) chính.

Activities to cover:
1. Test Planning
2. Test Analysis
3. Test Design
4. Test Implementation
5. Test Execution

<details>
<summary><b>ĐÁP ÁN</b> (Example)</summary>

```
1. TEST PLANNING
Tasks:
- Define test scope (in: ordering, out: restaurant management)
- Identify test approach (risk-based, focus payment & tracking)
- Estimate resources (2 testers, 6 weeks, Selenium + Appium)
Deliverable: Test Plan document

2. TEST ANALYSIS
Tasks:
- Review requirements để understand features (menu, cart, checkout)
- Identify test conditions (TC-001: Add item to cart, TC-002: Remove item, etc.)
- Define test data needs (test restaurants, test users, test menu items)
Deliverable: Test Conditions list (50 conditions)

3. TEST DESIGN
Tasks:
- Design test cases from conditions (TC-001 → Detailed steps)
- Apply test techniques (EP for quantity, BVA for delivery distance)
- Specify test data values (Restaurant A: 2km away, Item B: 50,000đ)
Deliverable: Test Cases document (200 test cases)

4. TEST IMPLEMENTATION
Tasks:
- Create automated scripts (Selenium cho web, Appium cho mobile)
- Setup test environment (Test server, Test database, Payment sandbox)
- Prepare test data (Load 100 test restaurants, 500 menu items)
Deliverable: Test Scripts + Test Environment ready

5. TEST EXECUTION
Tasks:
- Execute test cases manually and automated
- Compare actual vs expected results
- Log defects for failures (BUG-001: Cart total calculation wrong)
Deliverable: Test Execution Report + Defect Reports
```

**Scoring**:
- Each activity: 1 point (tasks + deliverable)
- Total: 5 points
</details>

---

### Exercise 7: Entry & Exit Criteria

**Scenario**: System testing phase cho banking app.

**Câu hỏi**:
a) Define 5 entry criteria (conditions để BẮT ĐẦU system testing)
b) Define 5 exit criteria (conditions để KẾT THÚC system testing)

<details>
<summary><b>ĐÁP ÁN</b></summary>

```
a) ENTRY CRITERIA (to start system testing):

1. CODE COMPLETE:
   All planned features implemented and code-frozen

2. BUILD DEPLOYED:
   Application deployed to test environment successfully

3. TEST CASES READY:
   All system test cases reviewed and approved
   (minimum 300 test cases)

4. TEST ENVIRONMENT STABLE:
   Test server, database, và integration points ready
   và stable (99% uptime last week)

5. TEST DATA PREPARED:
   Test users created, test accounts funded,
   test transactions loaded

b) EXIT CRITERIA (to finish system testing):

1. TEST EXECUTION COMPLETE:
   100% planned test cases executed

2. PASS RATE ACHIEVED:
   ≥95% test cases passed

3. CRITICAL DEFECTS RESOLVED:
   Zero critical/high severity defects open

4. COVERAGE ACHIEVED:
   - 100% requirement coverage
   - ≥80% code coverage

5. STAKEHOLDER SIGN-OFF:
   Test completion report reviewed and approved
   by Test Manager và Project Manager
```

**Scoring**:
- Entry criteria (5 relevant): 2.5 points
- Exit criteria (5 relevant): 2.5 points
- Total: 5 points
</details>

---

### Exercise 8: Traceability

**Scenario**: Bạn có 3 requirements cho login feature:

- REQ-001: User can login with email and password
- REQ-002: User can reset password via email
- REQ-003: System locks account after 5 failed login attempts

**Câu hỏi**:
a) Create test cases cho mỗi requirement (2 test cases/requirement)
b) Create a Traceability Matrix
c) Giải thích 2 benefits của traceability này

<details>
<summary><b>ĐÁP ÁN</b></summary>

```
a) TEST CASES:

REQ-001: User can login with email and password
├─ TC-001: Login with valid credentials → Success
└─ TC-002: Login with invalid password → Error message

REQ-002: User can reset password via email
├─ TC-003: Request reset with valid email → Email sent
└─ TC-004: Request reset with invalid email → Error

REQ-003: System locks account after 5 failed attempts
├─ TC-005: Fail login 4 times → Account still active
└─ TC-006: Fail login 5 times → Account locked

b) TRACEABILITY MATRIX:

| Req ID  | Description           | Test Cases    | Status  | Defects |
|---------|-----------------------|---------------|---------|---------|
| REQ-001 | Login with creds     | TC-001,TC-002 | Passed  | -       |
| REQ-002 | Reset password       | TC-003,TC-004 | Passed  | -       |
| REQ-003 | Lock after 5 fails   | TC-005,TC-006 | Failed  | BUG-100 |

Coverage: 100% (3/3 requirements have test cases)

c) BENEFITS:

Benefit 1: COVERAGE VERIFICATION
Traceability matrix shows mọi requirement đều
có test cases cover. Nếu REQ-004 added mà không
có test case, dễ dàng spot missing coverage.

Benefit 2: IMPACT ANALYSIS
Nếu REQ-003 changes (e.g., lock after 3 attempts
instead of 5), traceability immediately shows
TC-005 và TC-006 cần update. Không miss affected
test cases.
```

**Scoring**:
- Test cases relevant: 2 points
- Traceability matrix correct: 1.5 points
- Benefits explained: 1.5 points
- Total: 5 points
</details>

---

### Exercise 9: Test Roles

**Scenario**: Small startup (10 people) developing e-commerce platform. Bạn là người duy nhất responsible for testing.

**Câu hỏi**:
a) Bạn phải cover cả Test Management và Testing activities. List ra daily/weekly tasks bạn cần làm.
b) Giải thích challenges của việc combine 2 roles này
c) Recommend solution để improve situation

<details>
<summary><b>ĐÁP ÁN</b></summary>

```
a) TASKS:

DAILY (Testing Role):
- Execute test cases (manual + automated)
- Log defects found
- Verify bug fixes
- Update test execution status
- Communicate với dev team về bugs

WEEKLY (Test Management Role):
- Update test plan based on changes
- Report progress to management
  (% tests done, defects found, risks)
- Prioritize test cases based on risk
- Monitor schedule và adjust nếu behind
- Coordinate với PO về requirements

BOTH:
- Design new test cases for new features
- Maintain automation scripts
- Setup/maintain test environment

b) CHALLENGES:

Challenge 1: TIME CONFLICT
Management tasks (planning, reporting) take time
away from execution. Risk: Testing execution delayed.

Challenge 2: LACK OF OBJECTIVITY
Hard to objectively assess own test coverage và
quality. Might have blind spots.

Challenge 3: OVERLOAD
Too many responsibilities → Potential burnout,
mistakes, hoặc rushed work.

Challenge 4: NO BACKUP
Nếu sick hoặc leave → Testing completely stopped.
Single point of failure.

c) SOLUTIONS:

Short-term (Immediate):
- PRIORITIZE: Focus high-risk features, automate
  regression để save time
- TIME MANAGEMENT: Block time for management tasks
  (e.g., Monday morning for planning/reporting)
- TOOLING: Use tools để automate repetitive tasks
  (test management tool, CI/CD)

Long-term (As company grows):
- HIRE: Thêm 1 tester để share workload
- WHOLE TEAM APPROACH: Train developers to write
  unit tests, involve PO trong acceptance testing
- CLEAR ROLE SPLIT: Nếu hire Test Manager, bạn
  focus on technical testing activities
```

**Scoring**:
- Tasks comprehensive: 1.5 points
- Challenges identified: 1.5 points
- Solutions practical: 2 points
- Total: 5 points
</details>

---

### Exercise 10: Test Automation - Automate or Not?

**Câu hỏi**: Cho mỗi scenario sau, decide có nên automate không và explain why.

**Scenario A**: Login function - Will be used trong every test suite, run 100+ times

**Scenario B**: Exploratory testing for new UX design - Need human judgment on aesthetics

**Scenario C**: Data entry form với 50 fields - Need to test all valid/invalid combinations (500+ test cases)

**Scenario D**: Performance testing - Simulate 10,000 concurrent users

**Scenario E**: One-time migration script - Run once để migrate old data

<details>
<summary><b>ĐÁP ÁN</b></summary>

```
SCENARIO A: ✅ AUTOMATE
Reasoning:
- High reuse (run 100+ times)
- Stable functionality (login rarely changes)
- Repetitive (same steps every time)
- ROI: High (saves many hours)
→ Perfect candidate for automation

SCENARIO B: ❌ DO NOT AUTOMATE
Reasoning:
- Requires human judgment (aesthetics)
- Subjective evaluation (no clear pass/fail)
- Exploratory nature (undefined steps)
- One-time activity (design review)
→ Manual exploratory testing better

SCENARIO C: ✅ AUTOMATE
Reasoning:
- Large volume (500+ test cases)
- Data-driven testing (perfect for automation)
- Repetitive steps (just different data)
- Manual = Too time-consuming
→ Automate với data-driven framework

SCENARIO D: ✅ AUTOMATE (Must automate)
Reasoning:
- IMPOSSIBLE manually (10,000 users)
- Performance tools required (JMeter, Gatling)
- Need to measure response time accurately
- Must simulate real load
→ No alternative, must automate

SCENARIO E: ❌ DO NOT AUTOMATE
Reasoning:
- One-time activity (no reuse)
- Automation setup time > Manual execution time
- Script will never run again
- Better spend time on verification than automation
→ Manual execution + thorough validation
```

**Scoring**:
- Each scenario: 1 point (correct decision + good reasoning)
- Total: 5 points
</details>

---

## PART B: MULTIPLE CHOICE QUESTIONS (40 câu)

### Section 1: Fundamentals (10 câu)

**Question 1**
Which of the following is a typical test objective?

A. Verifying that all code has been written
B. Preventing defects by evaluating work products
C. Ensuring developers write defect-free code
D. Proving that software is 100% defect-free

<details>
<summary>Đáp án</summary>
<b>B</b> - Preventing defects through evaluation (static testing) là typical objective. A, C, D không realistic.
</details>

---

**Question 2**
Which statement correctly describes the difference between testing and debugging?

A. Testing finds defects; debugging analyzes and fixes them
B. Testing fixes defects; debugging finds them
C. Testing is done by developers; debugging by testers
D. Testing and debugging are the same activity

<details>
<summary>Đáp án</summary>
<b>A</b> - Testing = Find defects (testers), Debugging = Analyze và fix (developers)
</details>

---

**Question 3**
What is the relationship between errors, defects, and failures?

A. Errors in requirements lead to defects in code, which may cause failures
B. Failures in testing lead to defects in code, which may cause errors
C. Defects in requirements lead to errors in code, which may cause failures
D. Errors and defects are the same; only failures are different

<details>
<summary>Đáp án</summary>
<b>A</b> - Error (human mistake) → Defect (in work product) → Failure (when executed)
</details>

---

**Question 4**
Which testing principle states that the same tests lose effectiveness over time?

A. Testing shows presence of defects
B. Exhaustive testing is impossible
C. Defects cluster together
D. Pesticide paradox

<details>
<summary>Đáp án</summary>
<b>D</b> - Pesticide paradox: Tests wear out, need to update regularly
</details>

---

**Question 5**
Why is it important to perform testing early in the SDLC?

A. It is required by all SDLC models
B. It reduces the cost of fixing defects
C. It eliminates the need for later testing
D. It guarantees defect-free software

<details>
<summary>Đáp án</summary>
<b>B</b> - Early testing = Find defects early = Cheaper to fix (Principle #3)
</details>

---

**Question 6**
Which of the following is a consequence of the "defects cluster together" principle?

A. All modules will have equal numbers of defects
B. Testing should focus more on high-defect areas
C. Defects found late are more expensive to fix
D. Automated testing will find all defects

<details>
<summary>Đáp án</summary>
<b>B</b> - Since defects cluster, focus testing effort on high-defect areas
</details>

---

**Question 7**
What is the main difference between Quality Assurance (QA) and Quality Control (QC)?

A. QA focuses on processes; QC focuses on products
B. QA focuses on products; QC focuses on processes
C. QA is performed by testers; QC by developers
D. QA and QC are the same activity

<details>
<summary>Đáp án</summary>
<b>A</b> - QA = Process-oriented (prevent defects), QC = Product-oriented (detect defects)
</details>

---

**Question 8**
How does testing contribute to higher quality?

A. By finding and fixing all defects before release
B. By providing information to support decision-making
C. By replacing the need for code reviews
D. By guaranteeing zero defects in production

<details>
<summary>Đáp án</summary>
<b>B</b> - Testing provides information (defect data, metrics) để support decisions
</details>

---

**Question 9**
Which testing principle explains why 100% testing coverage does not guarantee a defect-free system?

A. Testing shows presence, not absence
B. Exhaustive testing is impossible
C. Early testing saves money
D. Absence-of-defects fallacy

<details>
<summary>Đáp án</summary>
<b>A</b> - Cannot prove absence of defects, only presence (Principle #1)
</details>

---

**Question 10**
In which phase of the SDLC is it typically LEAST expensive to fix a defect?

A. Requirements
B. Design
C. Implementation
D. Production

<details>
<summary>Đáp án</summary>
<b>A</b> - Defects found trong requirements phase cheapest to fix
</details>

---

### Section 2: Test Process (10 câu)

**Question 11**
Which test activity involves analyzing the test basis to identify testable features?

A. Test planning
B. Test analysis
C. Test design
D. Test implementation

<details>
<summary>Đáp án</summary>
<b>B</b> - Test analysis: Analyze test basis, identify test conditions
</details>

---

**Question 12**
What is the main purpose of test implementation?

A. To design test cases
B. To execute test procedures
C. To create testware needed for execution
D. To archive test results

<details>
<summary>Đáp án</summary>
<b>C</b> - Test implementation: Create testware (scripts, data, environment)
</details>

---

**Question 13**
Which of the following is an output of test analysis?

A. Test plan
B. Test conditions
C. Test procedures
D. Defect reports

<details>
<summary>Đáp án</summary>
<b>B</b> - Test analysis output: Test conditions list
</details>

---

**Question 14**
During test execution, what should a tester do when actual results differ from expected results?

A. Modify the test case to match actual results
B. Log a defect report
C. Ignore minor differences
D. Ask developer to change requirements

<details>
<summary>Đáp án</summary>
<b>B</b> - Actual ≠ Expected → Log defect report
</details>

---

**Question 15**
What is the primary purpose of test monitoring and control?

A. To design test cases
B. To track progress and take corrective actions
C. To execute tests
D. To analyze requirements

<details>
<summary>Đáp án</summary>
<b>B</b> - Monitoring: Track progress; Control: Take corrective actions
</details>

---

**Question 16**
Which activity is part of test completion?

A. Designing test cases
B. Executing test procedures
C. Archiving testware
D. Implementing test automation

<details>
<summary>Đáp án</summary>
<b>C</b> - Test completion: Archive testware, lessons learned
</details>

---

**Question 17**
Why is traceability between requirements and test cases important?

A. It enables automation of tests
B. It helps verify coverage and perform impact analysis
C. It reduces the cost of testing
D. It eliminates the need for test planning

<details>
<summary>Đáp án</summary>
<b>B</b> - Traceability: Verify coverage + Impact analysis khi changes
</details>

---

**Question 18**
Which of the following is testware?

A. Requirements document
B. Test plan
C. Source code
D. User manual

<details>
<summary>Đáp án</summary>
<b>B</b> - Testware = Work products created trong test process (test plan, test cases, scripts, reports)
</details>

---

**Question 19**
What is an exit criterion?

A. Condition to start testing
B. Condition to finish testing
C. Reason for test failure
D. Type of test technique

<details>
<summary>Đáp án</summary>
<b>B</b> - Exit criteria: Conditions để finish/complete test activity
</details>

---

**Question 20**
Which role is primarily responsible for test planning and monitoring?

A. Developer
B. Tester
C. Test Manager
D. Business Analyst

<details>
<summary>Đáp án</summary>
<b>C</b> - Test Manager: Planning, monitoring, controlling, reporting
</details>

---

### Section 3: Skills & Independence (10 câu)

**Question 21**
Which skill is MOST important for a tester?

A. Programming ability
B. Attention to detail
C. Project management
D. System administration

<details>
<summary>Đáp án</summary>
<b>B</b> - Attention to detail: Fundamental tester skill
</details>

---

**Question 22**
What is a benefit of independent testing?

A. Testers find different types of defects than developers
B. Independent testing is always cheaper
C. No communication needed với development team
D. Eliminates need for developer testing

<details>
<summary>Đáp án</summary>
<b>A</b> - Independent testing: Different perspective → Different types of defects
</details>

---

**Question 23**
What is the "whole team approach"?

A. Everyone does testing, no dedicated testers needed
B. Everyone is responsible for quality
C. All testing is done by the team lead
D. Testing and development are completely separated

<details>
<summary>Đáp án</summary>
<b>B</b> - Whole team approach: Shared responsibility for quality
</details>

---

**Question 24**
Which level of test independence is HIGHEST?

A. No independent testing
B. Testing by another team member
C. Testing by independent test team
D. Testing by independent organization

<details>
<summary>Đáp án</summary>
<b>D</b> - Testing by independent organization (third-party) = Highest independence
</details>

---

**Question 25**
What is a drawback of high test independence?

A. Better objectivity
B. Different perspective
C. Communication gaps
D. More defects found

<details>
<summary>Đáp án</summary>
<b>C</b> - Too much independence → Communication gaps, "us vs them" mentality
</details>

---

**Question 26**
Which generic skill involves understanding the business domain of the test object?

A. Testing knowledge
B. Domain knowledge
C. Technical knowledge
D. Analytical thinking

<details>
<summary>Đáp án</summary>
<b>B</b> - Domain knowledge: Understanding business context
</details>

---

**Question 27**
Why is good communication important for testers?

A. To write test automation scripts
B. To explain defects và collaborate with team
C. To design test cases
D. To execute tests faster

<details>
<summary>Đáp án</summary>
<b>B</b> - Communication: Explain bugs, collaborate, report status
</details>

---

**Question 28**
What does "analytical thinking" mean for a tester?

A. Ability to write code
B. Ability to analyze problems và find patterns
C. Ability to manage projects
D. Ability to use test tools

<details>
<summary>Đáp án</summary>
<b>B</b> - Analytical thinking: Analyze problems, find root causes, identify patterns
</details>

---

**Question 29**
In Agile, who is responsible for testing quality?

A. Only testers
B. Only developers
C. Only Product Owner
D. Whole team

<details>
<summary>Đáp án</summary>
<b>D</b> - Agile whole team approach: Everyone responsible for quality
</details>

---

**Question 30**
What is a benefit of testers working closely with developers?

A. Testers can find defects faster
B. Developers don't need to write unit tests
C. Better understanding và collaboration
D. Testing phase can be skipped

<details>
<summary>Đáp án</summary>
<b>C</b> - Close collaboration: Better understanding, faster feedback, shared responsibility
</details>

---

### Section 4: Tools & Automation (10 câu)

**Question 31**
Which type of tool is used to manage test cases và track results?

A. Static analysis tool
B. Test management tool
C. Coverage measurement tool
D. Performance testing tool

<details>
<summary>Đáp án</summary>
<b>B</b> - Test management tools: Jira, TestRail (manage cases, track results)
</details>

---

**Question 32**
What is a static analysis tool used for?

A. Executing automated tests
B. Analyzing code without execution
C. Measuring performance
D. Managing test cases

<details>
<summary>Đáp án</summary>
<b>B</b> - Static analysis: Analyze code WITHOUT execution (SonarQube, ESLint)
</details>

---

**Question 33**
Which tool would be used for load testing?

A. Selenium
B. JMeter
C. SonarQube
D. TestRail

<details>
<summary>Đáp án</summary>
<b>B</b> - JMeter: Performance/load testing tool
</details>

---

**Question 34**
What is a benefit of test automation?

A. All testing can be automated
B. Automated tests can run frequently with minimal effort
C. Eliminates need for manual testing
D. Always cheaper than manual testing

<details>
<summary>Đáp án</summary>
<b>B</b> - Automation benefit: Run frequently, minimal effort, fast feedback
</details>

---

**Question 35**
What is a risk of test automation?

A. Tests run too fast
B. Unrealistic expectations về automation coverage
C. Too much test coverage
D. Defects found too quickly

<details>
<summary>Đáp án</summary>
<b>B</b> - Automation risk: Unrealistic expectations (automate everything, no maintenance, etc.)
</details>

---

**Question 36**
Which type of testing is BEST suited for automation?

A. Exploratory testing
B. Usability testing
C. Regression testing
D. Ad-hoc testing

<details>
<summary>Đáp án</summary>
<b>C</b> - Regression testing: Repetitive, run nhiều lần → Perfect cho automation
</details>

---

**Question 37**
Which tool would be used to measure code coverage?

A. Selenium
B. JaCoCo
C. JMeter
D. Jira

<details>
<summary>Đáp án</summary>
<b>B</b> - JaCoCo (Java) / Istanbul (JavaScript): Code coverage tools
</details>

---

**Question 38**
What is a disadvantage of over-reliance on test automation?

A. Tests run too frequently
B. May miss issues that require human observation
C. Too many defects found
D. Costs too little

<details>
<summary>Đáp án</summary>
<b>B</b> - Over-reliance: Miss UX issues, usability problems cần human judgment
</details>

---

**Question 39**
Which tool is used for API testing?

A. Selenium
B. Appium
C. Postman
D. JaCoCo

<details>
<summary>Đáp án</summary>
<b>C</b> - Postman: API testing tool (REST APIs)
</details>

---

**Question 40**
What is the main purpose of CI/CD tools like Jenkins?

A. To write test cases
B. To automate build, test, and deployment
C. To manage test data
D. To execute manual tests

<details>
<summary>Đáp án</summary>
<b>B</b> - Jenkins: CI/CD automation (build → test → deploy pipeline)
</details>

---

## SCORING & ASSESSMENT

### Part A: Practical Exercises
- Total: 50 points (10 exercises × 5 points)
- Pass: ≥40 points (80%)

### Part B: Multiple Choice
- Total: 40 points (40 questions × 1 point)
- Pass: ≥32 points (80%)

### Overall Assessment
- **Total**: 90 points
- **Pass**: ≥72 points (80%)
- **Good**: ≥77 points (85%)
- **Excellent**: ≥81 points (90%)

---

## NEXT STEPS

### If you scored ≥80%: 🎉
**CONGRATULATIONS!** Bạn đã nắm vững Giai đoạn 1!

**Ready for**:
- 📚 [Giai đoạn 2: Static Testing](../giai-doan-2-static-testing/module-2.1-static-testing-co-ban.md)

**Before moving on**:
- Review any questions bạn missed
- Ensure hiểu rõ tất cả concepts
- Rest 1-2 days trước khi start Giai đoạn 2

---

### If you scored <80%: 📖
**DON'T WORRY!** Cần ôn lại một số concepts.

**Action plan**:
1. Identify topics bạn weak (check which questions missed)
2. Re-study relevant modules:
   - Module 1.1: Test objectives, Testing vs Debugging
   - Module 1.2: Errors/Defects/Failures, 7 Principles, QA vs Testing
   - Module 1.3: 7 Test Activities, Testware, Traceability
   - Module 1.4: Test Skills, Tools, Automation
3. Làm lại exercises sau 2-3 ngày
4. Target: ≥80% trước khi chuyển sang Giai đoạn 2

---

**Good luck! You're doing great! 💪**
