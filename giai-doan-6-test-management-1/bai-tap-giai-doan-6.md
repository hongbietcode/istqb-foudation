# BÀI TẬP GIAI ĐOẠN 6: TEST MANAGEMENT - PART 1

**Thời lượng**: 3-4 giờ | **Độ quan trọng**: ⭐⭐⭐

---

## MỤC TIÊU

- Thực hành Test Planning activities
- Áp dụng 4 estimation techniques
- Prioritize test cases
- Thực hiện risk analysis

---

## PHẦN A: BÀI TẬP THỰC HÀNH

### BÀI TẬP 1: Write Entry & Exit Criteria

**Scenario**: System Testing cho Momo wallet app

**Câu hỏi**: Viết Entry và Exit Criteria

<details>
<summary>Đáp án Mẫu</summary>

**ENTRY CRITERIA - SYSTEM TESTING**

✅ Build & Environment:
- [ ] Build 3.5.0 deployed to staging
- [ ] Database seeded với 100 test accounts
- [ ] Payment gateway sandbox configured
- [ ] Smoke test passed (login, view balance work)

✅ Documentation:
- [ ] 80 test cases written và reviewed
- [ ] Test plan approved
- [ ] All requirements clarified

✅ Resources:
- [ ] 4 testers available
- [ ] Test devices ready (iOS, Android)
- [ ] Jira access granted

✅ Prerequisites:
- [ ] Unit testing >80% coverage
- [ ] Integration testing passed
- [ ] 0 Critical bugs from previous build

**EXIT CRITERIA - SYSTEM TESTING**

✅ Test Execution:
- [ ] 100% test cases executed
- [ ] 95%+ pass rate
- [ ] All failed tests analyzed

✅ Defect Status:
- [ ] 0 Critical bugs
- [ ] ≤3 High bugs (evaluated by PO)
- [ ] Medium/Low bugs documented

✅ Coverage:
- [ ] 100% requirements covered
- [ ] All critical flows tested
- [ ] Regression suite passed

✅ Non-Functional:
- [ ] Transaction time <3 seconds
- [ ] 5,000 concurrent users supported
- [ ] Security scan: 0 Critical vulnerabilities

✅ Documentation:
- [ ] Test execution report completed
- [ ] Known issues documented
- [ ] Sign-off from Test Manager + PO

</details>

---

### BÀI TẬP 2: Estimation Based on Ratios

**Scenario**: Previous project statistics
- Dev effort: 120 days
- Test effort: 42 days

**New Project**:
- Dev effort estimated: 180 days

**Câu hỏi**:
1. Calculate test effort ratio
2. Estimate new project test effort
3. If add 15% buffer, final estimate?

<details>
<summary>Đáp án</summary>

**1. Ratio**:
```
Ratio = Test Effort / Dev Effort
Ratio = 42 / 120 = 0.35 = 35%
```

**2. New Project Estimate**:
```
Test Effort = Dev Effort × Ratio
Test Effort = 180 × 0.35 = 63 days
```

**3. With 15% Buffer**:
```
Final = 63 × 1.15 = 72.45 ≈ 73 days
```

</details>

---

### BÀI TẬP 3: Extrapolation

**Scenario**: Test execution progress
- Total test cases: 600
- Executed (after 4 days): 200 TCs
- Time taken: 32 hours

**Câu hỏi**:
1. Calculate velocity (TCs per hour)
2. Estimate remaining time
3. Total duration?
4. With 20% buffer?

<details>
<summary>Đáp án</summary>

**1. Velocity**:
```
Velocity = 200 TCs / 32 hours = 6.25 TCs per hour
```

**2. Remaining Time**:
```
Remaining TCs = 600 - 200 = 400
Time = 400 / 6.25 = 64 hours = 8 days
```

**3. Total Duration**:
```
Total = 4 days (actual) + 8 days (estimated) = 12 days
```

**4. With 20% Buffer**:
```
Final = 12 × 1.20 = 14.4 ≈ 15 days
```

</details>

---

### BÀI TẬP 4: Three-Point Estimation

**Scenario**: Security testing duration

**Estimates**:
- Optimistic: 8 days
- Most Likely: 14 days
- Pessimistic: 26 days

**Câu hỏi**:
1. Calculate Expected (E)
2. Calculate Standard Deviation (SD)
3. 68% confidence interval?
4. 95% confidence interval?

<details>
<summary>Đáp án</summary>

**1. Expected (E)**:
```
E = (O + 4M + P) / 6
E = (8 + 4×14 + 26) / 6
E = (8 + 56 + 26) / 6
E = 90 / 6 = 15 days
```

**2. Standard Deviation (SD)**:
```
SD = (P - O) / 6
SD = (26 - 8) / 6
SD = 18 / 6 = 3 days
```

**3. 68% Confidence**:
```
E ± 1 SD = 15 ± 3 = 12 to 18 days
```

**4. 95% Confidence**:
```
E ± 2 SD = 15 ± 6 = 9 to 21 days
```

**Answer**: Security testing will take **15 days**, with 68% confidence between **12-18 days**.

</details>

---

### BÀI TẬP 5: Risk-Based Prioritization

**Scenario**: Grab features risk assessment

| Feature | Likelihood | Impact |
|---------|-----------|--------|
| Payment processing | 4 | 5 |
| Ride booking | 3 | 5 |
| Driver rating | 2 | 3 |
| Chat with driver | 3 | 2 |
| Ride history | 1 | 2 |

**Câu hỏi**:
1. Calculate Risk Level cho mỗi feature
2. Categorize (Critical/High/Medium/Low)
3. Prioritize test execution order

<details>
<summary>Đáp án</summary>

**1. Risk Levels**:

| Feature | L | I | Risk = L×I |
|---------|---|---|------------|
| Payment processing | 4 | 5 | **20** |
| Ride booking | 3 | 5 | **15** |
| Driver rating | 2 | 3 | **6** |
| Chat with driver | 3 | 2 | **6** |
| Ride history | 1 | 2 | **2** |

**2. Categorization**:
```
CRITICAL (20-25):
  • Payment processing (20)

HIGH (12-19):
  • Ride booking (15)

MEDIUM (6-11):
  • Driver rating (6)
  • Chat with driver (6)

LOW (1-5):
  • Ride history (2)
```

**3. Test Execution Order**:
```
Priority 1: Payment processing (Critical)
Priority 2: Ride booking (High)
Priority 3: Driver rating, Chat (Medium)
Priority 4: Ride history (Low) - test nếu còn time
```

</details>

---

### BÀI TẬP 6: Product Risk Analysis

**Scenario**: Mobile banking app risks

**Câu hỏi**: Identify 5 product risks, assess, và prioritize

<details>
<summary>Đáp án Mẫu</summary>

**PRODUCT RISKS**:

| ID | Risk | Likelihood | Impact | Risk Level |
|----|------|-----------|--------|------------|
| R1 | SQL Injection vulnerability | 2 | 5 | **10** (MH) |
| R2 | Money transfer calculation error | 3 | 5 | **15** (H) |
| R3 | App crashes on old devices | 3 | 2 | **6** (M) |
| R4 | Transaction timeout peak hours | 4 | 4 | **16** (H) |
| R5 | Biometric auth bypass | 2 | 5 | **10** (MH) |

**PRIORITIZATION**:
```
HIGH (12-19):
  R4: Transaction timeout (16)
  R2: Calculation error (15)

MEDIUM-HIGH (10-11):
  R1: SQL Injection (10)
  R5: Biometric bypass (10)

MEDIUM (6-9):
  R3: App crashes (6)
```

**MITIGATION STRATEGIES**:

**R4** (Transaction timeout):
- Performance testing (10K users)
- Load testing
- Database query optimization
- Caching implementation

**R2** (Calculation error):
- Extensive test cases (EP, BVA)
- Edge cases testing (large amounts, decimals)
- Code review by 2+ developers
- Pair testing with accountant

**R1** (SQL Injection):
- Security testing (OWASP Top 10)
- Penetration testing
- Code review for all database queries
- Use parameterized queries

</details>

---

## PHẦN B: CÂU HỎI TRẮC NGHIỆM (35 CÂU)

### NHÓM 1: TEST PLANNING (10 câu)

**Câu 1** (K2)
Test planning activity nào defines "WHAT to test"?

A. Define test approach
B. Determine scope & objectives
C. Estimate effort
D. Identify resources

<details>
<summary>Đáp án</summary>
**B. Determine scope & objectives**
</details>

---

**Câu 2** (K2)
Entry criteria are conditions to:

A. Stop testing
B. Start testing
C. Define test cases
D. Report defects

<details>
<summary>Đáp án</summary>
**B. Start testing**
</details>

---

**Câu 3** (K2)
Definition of Ready (DoR) applies to:

A. Test plan
B. User story before sprint
C. Test report
D. Defect report

<details>
<summary>Đáp án</summary>
**B. User story before sprint**
</details>

---

**Câu 4** (K2)
Definition of Done (DoD) means:

A. Testing completed
B. User story completed
C. Sprint finished
D. Project closed

<details>
<summary>Đáp án</summary>
**B. User story completed**
</details>

---

**Câu 5** (K2)
Test Pyramid: Majority tests ở layer nào?

A. UI tests
B. Integration tests
C. Unit tests
D. Manual tests

<details>
<summary>Đáp án</summary>
**C. Unit tests** (70%)
</details>

---

**Câu 6** (K2)
Test Pyramid ratio thông thường:

A. 50% Unit, 30% Integration, 20% UI
B. 70% Unit, 20% Integration, 10% UI
C. 60% UI, 30% Integration, 10% Unit
D. 80% Manual, 20% Automated

<details>
<summary>Đáp án</summary>
**B. 70% Unit, 20% Integration, 10% UI**
</details>

---

**Câu 7** (K2)
Testing Quadrant Q1 bao gồm:

A. Exploratory testing
B. Unit tests, Component tests
C. UAT
D. Performance testing

<details>
<summary>Đáp án</summary>
**B. Unit tests, Component tests**
</details>

---

**Câu 8** (K2)
Testing Quadrant Q3 (Business-Facing, Critique) bao gồm:

A. Unit tests
B. API tests
C. Exploratory testing, UAT
D. Load testing

<details>
<summary>Đáp án</summary>
**C. Exploratory testing, UAT**
</details>

---

**Câu 9** (K2)
Exit criteria example:

A. Requirements approved
B. Test environment ready
C. 95%+ test cases passed
D. Team available

<details>
<summary>Đáp án</summary>
**C. 95%+ test cases passed**
</details>

---

**Câu 10** (K2)
Ice Cream Cone là:

A. Good test automation strategy
B. Anti-pattern (too many UI/manual tests)
C. Type of test technique
D. Coverage metric

<details>
<summary>Đáp án</summary>
**B. Anti-pattern (too many UI/manual tests)**
</details>

---

### NHÓM 2: TEST ESTIMATION (10 câu)

**Câu 11** (K3)
Dev effort = 80 days, Test/Dev ratio = 40%. Test effort?

A. 32 days
B. 40 days
C. 80 days
D. 120 days

<details>
<summary>Đáp án</summary>
**A. 32 days** (80 × 0.40 = 32)
</details>

---

**Câu 12** (K3)
Executed 150 TCs trong 30 hours. Còn 350 TCs. Remaining time?

A. 30 hours
B. 50 hours
C. 70 hours
D. 100 hours

<details>
<summary>Đáp án</summary>
**C. 70 hours**
Rate = 30/150 = 0.2h per TC
350 × 0.2 = 70 hours
</details>

---

**Câu 13** (K2)
Extrapolation technique dùng khi nào?

A. Before project starts
B. After completing part of work
C. Only at project end
D. Never

<details>
<summary>Đáp án</summary>
**B. After completing part of work**
</details>

---

**Câu 14** (K2)
Planning Poker uses:

A. Standard deck cards
B. Fibonacci sequence cards
C. Random numbers
D. Binary numbers

<details>
<summary>Đáp án</summary>
**B. Fibonacci sequence cards** (1, 2, 3, 5, 8, 13, ...)
</details>

---

**Câu 15** (K2)
Wideband Delphi aims để:

A. Quick estimate
B. Team consensus through rounds
C. Manager decides
D. Historical data only

<details>
<summary>Đáp án</summary>
**B. Team consensus through rounds**
</details>

---

**Câu 16** (K3)
Three-Point: O=10, M=20, P=40. Expected (E)?

A. 20
B. 22
C. 23.33
D. 25

<details>
<summary>Đáp án</summary>
**C. 23.33**
E = (10 + 4×20 + 40) / 6 = 140 / 6 = 23.33
</details>

---

**Câu 17** (K3)
Three-Point: O=5, P=25. Standard Deviation?

A. 2.5
B. 3.33
C. 5
D. 20

<details>
<summary>Đáp án</summary>
**B. 3.33**
SD = (25 - 5) / 6 = 20 / 6 = 3.33
</details>

---

**Câu 18** (K2)
Story points trong Planning Poker represent:

A. Hours
B. Days
C. Relative size/complexity
D. Number of test cases

<details>
<summary>Đáp án</summary>
**C. Relative size/complexity**
</details>

---

**Câu 19** (K2)
Estimation based on ratios requires:

A. Team voting
B. Historical data
C. Three estimates
D. Current progress

<details>
<summary>Đáp án</summary>
**B. Historical data**
</details>

---

**Câu 20** (K2)
Best practice: Combine estimation techniques?

A. No, use only one
B. Yes, for better accuracy
C. Only for large projects
D. Not recommended

<details>
<summary>Đáp án</summary>
**B. Yes, for better accuracy**
</details>

---

### NHÓM 3: TEST PRIORITIZATION (5 câu)

**Câu 21** (K3)
Likelihood=3, Impact=4. Risk Level?

A. 7
B. 12
C. 1
D. 0.75

<details>
<summary>Đáp án</summary>
**B. 12** (3 × 4 = 12)
</details>

---

**Câu 22** (K2)
Coverage-based prioritization aims:

A. Test high-risk only
B. Maximum coverage sớm
C. Test randomly
D. Minimize time

<details>
<summary>Đáp án</summary>
**B. Maximum coverage sớm**
</details>

---

**Câu 23** (K2)
Requirements-based prioritization lấy priority từ:

A. Tester decides
B. Code complexity
C. Business/PO priorities
D. Random

<details>
<summary>Đáp án</summary>
**C. Business/PO priorities**
</details>

---

**Câu 24** (K2)
Test nào execute FIRST?

A. Longest tests
B. Smoke tests
C. Performance tests
D. Exploratory

<details>
<summary>Đáp án</summary>
**B. Smoke tests**
</details>

---

**Câu 25** (K3)
TC covers 4 reqs, TC2 covers 1 req. Coverage-based?

A. TC1 first
B. TC2 first
C. No difference
D. Cannot determine

<details>
<summary>Đáp án</summary>
**A. TC1 first** (covers more)
</details>

---

### NHÓM 4: RISK MANAGEMENT (10 câu)

**Câu 26** (K2)
Risk Level formula:

A. Likelihood + Impact
B. Likelihood × Impact
C. Likelihood - Impact
D. Likelihood / Impact

<details>
<summary>Đáp án</summary>
**B. Likelihood × Impact**
</details>

---

**Câu 27** (K2)
Project risk example:

A. SQL injection
B. Key tester unavailable
C. Poor performance
D. Incorrect logic

<details>
<summary>Đáp án</summary>
**B. Key tester unavailable** (Resource risk)
</details>

---

**Câu 28** (K2)
Product risk example:

A. Budget cuts
B. Schedule delays
C. Security vulnerabilities
D. Team conflicts

<details>
<summary>Đáp án</summary>
**C. Security vulnerabilities**
</details>

---

**Câu 29** (K2)
Product risk analysis steps:

A. Identify → Assess → Prioritize → Mitigate
B. Find → Fix → Report
C. Plan → Execute → Close
D. Design → Code → Test

<details>
<summary>Đáp án</summary>
**A. Identify → Assess → Prioritize → Mitigate**
</details>

---

**Câu 30** (K2)
Risk mitigation strategy example:

A. Do nothing
B. More testing, code reviews
C. Transfer to insurance only
D. Ignore the risk

<details>
<summary>Đáp án</summary>
**B. More testing, code reviews**
</details>

---

**Câu 31** (K2)
Risk-based testing principle:

A. Test everything equally
B. High risk → More testing
C. Only test low-risk
D. Random testing

<details>
<summary>Đáp án</summary>
**B. High risk → More testing**
</details>

---

**Câu 32** (K3)
Feature: L=2, I=5. Risk Level và category?

A. 7, Medium
B. 10, Medium-High
C. 3, Low
D. 25, Critical

<details>
<summary>Đáp án</summary>
**B. 10, Medium-High**
(2 × 5 = 10)
</details>

---

**Câu 33** (K2)
4 risk control strategies:

A. Find, Fix, Report, Close
B. Mitigate, Transfer, Accept, Avoid
C. Plan, Do, Check, Act
D. Design, Code, Test, Deploy

<details>
<summary>Đáp án</summary>
**B. Mitigate, Transfer, Accept, Avoid**
</details>

---

**Câu 34** (K2)
Who manages product risks?

A. Project Manager
B. Developer
C. Test Manager, QA Team
D. Business Analyst

<details>
<summary>Đáp án</summary>
**C. Test Manager, QA Team**
</details>

---

**Câu 35** (K2)
Risk register is:

A. One-time document
B. Living document, updated regularly
C. Only for project start
D. Not needed

<details>
<summary>Đáp án</summary>
**B. Living document, updated regularly**
</details>

---

## ĐÁP ÁN NHANH

| Câu | Đáp án | Câu | Đáp án | Câu | Đáp án | Câu | Đáp án |
|-----|--------|-----|--------|-----|--------|-----|--------|
| 1 | B | 10 | B | 19 | B | 28 | C |
| 2 | B | 11 | A | 20 | B | 29 | A |
| 3 | B | 12 | C | 21 | B | 30 | B |
| 4 | B | 13 | B | 22 | B | 31 | B |
| 5 | C | 14 | B | 23 | C | 32 | B |
| 6 | B | 15 | B | 24 | B | 33 | B |
| 7 | B | 16 | C | 25 | A | 34 | C |
| 8 | C | 17 | B | 26 | B | 35 | B |
| 9 | C | 18 | C | 27 | B | | |

---

## TÓM TẮT GIAI ĐOẠN 6

```
╔═══════════════════════════════════════════════════════════════╗
║         GIAI ĐOẠN 6 - TEST MANAGEMENT PART 1                  ║
╠═══════════════════════════════════════════════════════════════╣
║                                                               ║
║  📋 TEST PLANNING:                                            ║
║     • Entry/Exit Criteria                                    ║
║     • DoR/DoD                                                ║
║     • Test Pyramid (70/20/10)                                ║
║     • Testing Quadrants (Q1-Q4)                              ║
║                                                               ║
║  📊 TEST ESTIMATION:                                          ║
║     • Ratios: Test = Dev × Ratio                             ║
║     • Extrapolation: Actual progress → Total                 ║
║     • Wideband Delphi/Planning Poker: Team consensus         ║
║     • Three-Point: E = (O + 4M + P) / 6                      ║
║                                                               ║
║  🎯 PRIORITIZATION:                                           ║
║     • Risk-based: High risk → Test first                     ║
║     • Coverage-based: Max coverage early                     ║
║     • Requirements-based: Business priorities                ║
║                                                               ║
║  ⚠️ RISK MANAGEMENT:                                          ║
║     • Risk = Likelihood × Impact                             ║
║     • Project risks vs Product risks                         ║
║     • Risk Analysis: Identify → Assess → Mitigate            ║
║     • RBT: High risk → More testing                          ║
║                                                               ║
╚═══════════════════════════════════════════════════════════════╝
```

---

**Version**: 1.0.0
**Last Updated**: November 2025
