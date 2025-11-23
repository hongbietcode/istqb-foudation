# MODULE 7.1: TEST MONITORING & CONTROL

**Thời lượng**: 2-3 giờ | **Độ khó**: ⭐⭐

---

## MỤC TIÊU HỌC TẬP

Sau khi hoàn thành module này, bạn sẽ:

| ID | Mục tiêu | Level |
|----|----------|-------|
| FL-5.3.1 | Giải thích test monitoring metrics | K2 |
| FL-5.3.2 | Sử dụng metrics để monitor progress | K3 |
| FL-5.3.3 | Giải thích test control actions | K2 |

---

## 1. TEST MONITORING LÀ GÌ?

### 1.1. Định Nghĩa

```
╔═══════════════════════════════════════════════════════════════╗
║                   TEST MONITORING                             ║
╠═══════════════════════════════════════════════════════════════╣
║                                                               ║
║  📖 ĐỊNH NGHĨA:                                               ║
║     Ongoing activity để CHECK test progress so với test plan ║
║                                                               ║
║  🎯 MỤC ĐÍCH:                                                 ║
║     • Track progress                                         ║
║     • Identify deviations từ plan                            ║
║     • Provide visibility                                     ║
║     • Enable corrective actions                              ║
║                                                               ║
║  📊 WHAT TO MONITOR:                                          ║
║     • Test execution progress (% complete)                   ║
║     • Test case pass/fail rates                              ║
║     • Defect discovery rates                                 ║
║     • Test coverage achieved                                 ║
║     • Resource utilization                                   ║
║     • Schedule adherence                                     ║
║                                                               ║
║  ⏰ WHEN:                                                     ║
║     • Continuously throughout testing                        ║
║     • Daily/weekly status checks                             ║
║     • Before milestone reviews                               ║
║                                                               ║
╚═══════════════════════════════════════════════════════════════╝
```

---

## 2. TEST METRICS

### 2.1. 7 Types of Test Metrics (ISTQB)

```
╔═══════════════════════════════════════════════════════════════╗
║                    7 TEST METRICS                             ║
╠═══════════════════════════════════════════════════════════════╣
║                                                               ║
║  1️⃣ PROJECT PROGRESS METRICS                                  ║
║     → % test cases executed                                  ║
║     → % test environment readiness                           ║
║                                                               ║
║  2️⃣ TEST PROGRESS METRICS                                     ║
║     → Test execution rate (TCs per day)                      ║
║     → Actual vs planned progress                             ║
║                                                               ║
║  3️⃣ PRODUCT QUALITY METRICS                                   ║
║     → Defect density (defects per module)                    ║
║     → Pass/fail rate                                         ║
║                                                               ║
║  4️⃣ DEFECT METRICS                                            ║
║     → Total defects found                                    ║
║     → Defects by severity/priority                           ║
║     → Defect discovery rate                                  ║
║     → Defect resolution rate                                 ║
║                                                               ║
║  5️⃣ RISK METRICS                                              ║
║     → Risk coverage (high-risk areas tested)                 ║
║     → Outstanding risks                                      ║
║                                                               ║
║  6️⃣ COVERAGE METRICS                                          ║
║     → Requirements coverage %                                ║
║     → Code coverage %                                        ║
║                                                               ║
║  7️⃣ COST METRICS                                              ║
║     → Cost per defect found                                  ║
║     → Test effort vs budget                                  ║
║                                                               ║
╚═══════════════════════════════════════════════════════════════╝
```

### 2.2. Common Metrics Explained

**1. Test Execution Progress**
```
Formula:
  Execution % = (Executed TCs / Total TCs) × 100%

Example:
  Total: 500 test cases
  Executed: 350
  Progress: 350/500 = 70%
```

**2. Pass Rate**
```
Formula:
  Pass Rate = (Passed TCs / Executed TCs) × 100%

Example:
  Executed: 350 TCs
  Passed: 315
  Pass Rate: 315/350 = 90%
```

**3. Defect Discovery Rate**
```
Formula:
  Defect Rate = Defects Found / Test Cases Executed

Example:
  Defects: 45
  Executed TCs: 350
  Rate: 45/350 = 0.13 defects per TC
```

**4. Defect Removal Efficiency**
```
Formula:
  DRE = (Defects Found in Testing / Total Defects) × 100%

Example:
  Found in testing: 80 defects
  Found in production: 10 defects
  Total: 90
  DRE: 80/90 = 88.9%
```

**5. Requirements Coverage**
```
Formula:
  Coverage = (Requirements Tested / Total Requirements) × 100%

Example:
  Total requirements: 50
  Tested: 45
  Coverage: 45/50 = 90%
```

---

## 3. MONITORING DASHBOARDS

### 3.1. Example Dashboard

```
╔═══════════════════════════════════════════════════════════════╗
║              TEST EXECUTION DASHBOARD                         ║
║                  Sprint 15 - Week 2                           ║
╠═══════════════════════════════════════════════════════════════╣
║                                                               ║
║  📊 OVERALL PROGRESS                                          ║
║     Test Cases:     350/500 executed (70%)                   ║
║     Pass Rate:      315/350 passed (90%)                     ║
║     Failed:         35 (10%)                                 ║
║     Blocked:        150 (30%)                                ║
║                                                               ║
║  🐛 DEFECTS                                                   ║
║     Total Found:    45 defects                               ║
║     Critical:       2 (🔴 Open)                              ║
║     High:           8 (5 Fixed, 3 Open)                      ║
║     Medium:         20 (12 Fixed, 8 Open)                    ║
║     Low:            15 (10 Fixed, 5 Open)                    ║
║                                                               ║
║  📈 TRENDS                                                    ║
║     Defect Discovery: ↗️ Increasing (concern)                ║
║     Pass Rate:        ➡️ Stable at 90%                       ║
║     Execution Rate:   ↘️ Slowing (35 TCs/day → 28 TCs/day)  ║
║                                                               ║
║  ⚠️ RISKS                                                     ║
║     • 2 Critical bugs blocking 50 TCs                        ║
║     • Test environment unstable (3 outages this week)        ║
║     • Behind schedule by 2 days                              ║
║                                                               ║
╚═══════════════════════════════════════════════════════════════╝
```

### 3.2. Burndown Chart

```
Test Cases Remaining
│
500│ \
   │  \  Plan
   │   \___
400│    \  \
   │     \  \
300│      \  \ Actual
   │       \  \___
200│        \    \
   │         \    \___
100│          \      \___
   │           \________\___
  0└─────────────────────────► Days
    1  2  3  4  5  6  7  8  9 10

⚠️ Gap between Plan and Actual = Behind schedule
```

---

## 4. TEST CONTROL

### 4.1. Test Control Definition

```
╔═══════════════════════════════════════════════════════════════╗
║                     TEST CONTROL                              ║
╠═══════════════════════════════════════════════════════════════╣
║                                                               ║
║  📖 ĐỊNH NGHĨA:                                               ║
║     Taking ACTION để meet test objectives khi monitoring     ║
║     shows deviation từ plan                                  ║
║                                                               ║
║  🎯 MỤC ĐÍCH:                                                 ║
║     • Correct deviations                                     ║
║     • Get back on track                                      ║
║     • Adjust plans as needed                                 ║
║     • Manage risks                                           ║
║                                                               ║
║  🔄 CONTROL ACTIONS:                                          ║
║                                                               ║
║     1. RE-PRIORITIZE TESTS                                   ║
║        → Focus on high-risk areas first                      ║
║                                                               ║
║     2. ADJUST SCHEDULE                                       ║
║        → Extend timeline, add resources                      ║
║                                                               ║
║     3. CHANGE TEST APPROACH                                  ║
║        → More automation, pair testing                       ║
║                                                               ║
║     4. ADJUST SCOPE                                          ║
║        → Defer low-priority tests                            ║
║                                                               ║
║     5. FIX ROOT CAUSES                                       ║
║        → Stabilize test environment                          ║
║        → Improve test data management                        ║
║                                                               ║
╚═══════════════════════════════════════════════════════════════╝
```

### 4.2. Control Actions Examples

**Situation 1**: Behind schedule (30% behind)
```
MONITORING:
  Planned: 500 TCs in 10 days
  Actual: After 7 days, only 245 TCs executed (49%)
  Expected: Should be at 350 TCs (70%)
  Gap: 105 TCs behind

CONTROL ACTIONS:
  ✓ Re-prioritize: Skip low-priority tests (save 50 TCs)
  ✓ Add resources: Bring in 2 more testers
  ✓ Extend hours: Overtime for critical tests
  ✓ Parallelize: Run tests on multiple environments
```

**Situation 2**: High defect discovery rate
```
MONITORING:
  Week 1: 10 defects
  Week 2: 25 defects (↗️ 150% increase)
  Week 3: 40 defects (↗️ 60% increase)
  Trend: Exponentially increasing

CONTROL ACTIONS:
  ✓ Pause testing: Let dev team fix critical bugs first
  ✓ Root cause analysis: Why so many bugs?
  ✓ Add code reviews: Before testing resumes
  ✓ Adjust entry criteria: Higher quality threshold
```

**Situation 3**: Test environment unstable
```
MONITORING:
  5 environment outages in 2 days
  50% of test time lost waiting for fix

CONTROL ACTIONS:
  ✓ Escalate to IT: Priority support
  ✓ Use backup environment: If available
  ✓ Switch to manual testing: While env is down
  ✓ Document issues: For future improvement
```

---

## 5. MONITORING VS CONTROL

```
╔═══════════════════════════════════════════════════════════════╗
║              MONITORING VS CONTROL                            ║
╠═══════════════════════════════════════════════════════════════╣
║                                                               ║
║  MONITORING (Check):                                         ║
║  ├─ Collect metrics                                          ║
║  ├─ Compare actual vs planned                                ║
║  ├─ Identify deviations                                      ║
║  └─ Report status                                            ║
║                                                               ║
║  CONTROL (Act):                                              ║
║  ├─ Decide corrective actions                                ║
║  ├─ Implement changes                                        ║
║  ├─ Adjust plans                                             ║
║  └─ Manage risks                                             ║
║                                                               ║
║  RELATIONSHIP:                                               ║
║     Monitoring → Identifies problems                         ║
║     Control → Fixes problems                                 ║
║                                                               ║
╚═══════════════════════════════════════════════════════════════╝
```

---

## 6. PRACTICAL EXAMPLE

### 6.1. Scenario: Shopee Testing Project

**Week 3 Status Report**:

**MONITORING DATA**:
```
PLANNED:
  • 600 test cases total
  • 60 TCs/day execution rate
  • 10 days timeline
  • By end of Day 6: 360 TCs executed (60%)

ACTUAL:
  • By end of Day 6: 240 TCs executed (40%)
  • Execution rate: 40 TCs/day (lower than 60)
  • 120 TCs behind schedule (20%)

DEFECTS:
  • 35 defects found
  • 5 Critical (3 blocking tests)
  • 15 High
  • 15 Medium/Low

PASS RATE:
  • 200/240 passed = 83%
  • Target: 90%
  • Below target by 7%
```

**ANALYSIS**:
```
ROOT CAUSES:
  1. Test environment down 2 days (40% time lost)
  2. Critical bugs blocking 60 test cases
  3. New tester not productive yet (learning curve)
  4. Test data issues (10 TCs failed due to bad data)
```

**CONTROL ACTIONS**:
```
IMMEDIATE (This week):
  ✓ Escalate Critical bugs to dev team (resolve in 2 days)
  ✓ Fix test environment (IT priority support)
  ✓ Pair new tester with senior (faster learning)
  ✓ Create automation script for test data setup

ADJUSTMENTS:
  ✓ Extend timeline by 2 days (10 → 12 days)
  ✓ Re-prioritize: Focus on unblocked high-risk tests
  ✓ Skip 50 low-priority tests (defer to next sprint)
  ✓ Daily standup to monitor progress closely

REVISED PLAN:
  • Days 7-8: Focus on unblocked tests (80 TCs)
  • Days 9-10: Execute blocked tests (once bugs fixed)
  • Days 11-12: Regression testing (60 TCs)
  • Target: 550/600 TCs executed (92%)
```

---

## 7. STATUS REPORTING

### 7.1. Daily Status Report

```
╔═══════════════════════════════════════════════════════════════╗
║              DAILY TEST STATUS - Day 6                        ║
╠═══════════════════════════════════════════════════════════════╣
║                                                               ║
║  TODAY'S PROGRESS:                                           ║
║    • Executed: 45 test cases                                 ║
║    • Passed: 38 (84%)                                        ║
║    • Failed: 7 (16%)                                         ║
║    • Blocked: 15 (Critical bugs)                             ║
║                                                               ║
║  CUMULATIVE:                                                 ║
║    • Total Executed: 240/600 (40%)                           ║
║    • Total Passed: 200/240 (83%)                             ║
║    • Remaining: 360 TCs                                      ║
║                                                               ║
║  DEFECTS:                                                    ║
║    • New Today: 5 defects (2 High, 3 Medium)                 ║
║    • Total Open: 25 defects                                  ║
║    • Blocking: 3 Critical bugs                               ║
║                                                               ║
║  IMPEDIMENTS:                                                ║
║    • Test environment down for 3 hours                       ║
║    • Waiting on dev team for Critical bug fix               ║
║                                                               ║
║  PLAN FOR TOMORROW:                                          ║
║    • Execute 50 TCs (payment & checkout modules)             ║
║    • Retest 10 TCs (bugs fixed)                              ║
║                                                               ║
╚═══════════════════════════════════════════════════════════════╝
```

### 7.2. Weekly Status Report

```
╔═══════════════════════════════════════════════════════════════╗
║           WEEKLY TEST STATUS - Week 2                         ║
╠═══════════════════════════════════════════════════════════════╣
║                                                               ║
║  OVERALL STATUS: ⚠️ YELLOW (Behind schedule but recoverable) ║
║                                                               ║
║  PROGRESS:                                                   ║
║    • Executed: 240/600 TCs (40%)                             ║
║    • Expected: 360 TCs (60%)                                 ║
║    • Behind: 120 TCs (20%)                                   ║
║                                                               ║
║  QUALITY:                                                    ║
║    • Pass Rate: 83% (Target: 90%)                            ║
║    • Defects: 35 found (5 Critical)                          ║
║    • Critical bugs blocking 60 TCs                           ║
║                                                               ║
║  RISKS:                                                      ║
║    🔴 HIGH: Test environment unstable                        ║
║    🟡 MEDIUM: Behind schedule                                ║
║    🟡 MEDIUM: Pass rate below target                         ║
║                                                               ║
║  ACTIONS TAKEN:                                              ║
║    ✓ Escalated Critical bugs                                 ║
║    ✓ Extended timeline by 2 days                             ║
║    ✓ Re-prioritized test cases                               ║
║                                                               ║
║  NEXT WEEK PLAN:                                             ║
║    • Target: 450/600 TCs executed (75%)                      ║
║    • Focus: High-risk areas                                  ║
║    • Contingency: Skip low-priority if needed                ║
║                                                               ║
╚═══════════════════════════════════════════════════════════════╝
```

---

## 8. CÂU HỎI ÔN TẬP

### Câu 1 (K2)
Test monitoring là gì?

A. Fixing defects
B. Checking progress so với plan
C. Writing test cases
D. Executing tests

<details>
<summary>Đáp án</summary>
**B. Checking progress so với plan**

Monitoring = ongoing checking để track progress.
</details>

---

### Câu 2 (K2)
Test control là gì?

A. Collecting metrics
B. Reporting status
C. Taking action để correct deviations
D. Planning tests

<details>
<summary>Đáp án</summary>
**C. Taking action để correct deviations**

Control = actions to fix problems identified by monitoring.
</details>

---

### Câu 3 (K3)
Executed 350 TCs, Passed 315. Pass rate?

A. 85%
B. 90%
C. 95%
D. 100%

<details>
<summary>Đáp án</summary>
**B. 90%**

Pass Rate = 315/350 = 0.90 = 90%
</details>

---

### Câu 4 (K2)
Example của test control action:

A. Collect metrics
B. Re-prioritize tests
C. Report status
D. Track defects

<details>
<summary>Đáp án</summary>
**B. Re-prioritize tests**

Re-prioritizing là control action (adjusting plan).
</details>

---

### Câu 5 (K2)
Behind schedule 20%. Best control action?

A. Do nothing
B. Report only
C. Extend timeline or re-prioritize
D. Cancel testing

<details>
<summary>Đáp án</summary>
**C. Extend timeline or re-prioritize**

Control actions để get back on track.
</details>

---

### Câu 6 (K2)
Defect removal efficiency (DRE) measures:

A. Defects found per TC
B. % defects found in testing vs total defects
C. Defects fixed per day
D. Defect severity

<details>
<summary>Đáp án</summary>
**B. % defects found in testing vs total defects**

DRE = (Defects in testing / Total defects) × 100%
</details>

---

## 9. CHECKLIST TỰ ĐÁNH GIÁ

### Test Monitoring
- [ ] Hiểu test monitoring definition
- [ ] Biết 7 types of test metrics
- [ ] Calculate metrics: pass rate, execution %, defect rate
- [ ] Read và interpret dashboards
- [ ] Identify deviations từ plan

### Test Control
- [ ] Hiểu test control definition
- [ ] List được control actions
- [ ] Decide appropriate actions cho situations
- [ ] Understand monitoring → control relationship
- [ ] Apply control actions trong scenarios

### Practical Skills
- [ ] Create status reports (daily, weekly)
- [ ] Use burndown charts
- [ ] Communicate status effectively
- [ ] Escalate issues properly

---

## TỔNG KẾT

```
╔═══════════════════════════════════════════════════════════════╗
║                    KEY TAKEAWAYS                              ║
╠═══════════════════════════════════════════════════════════════╣
║                                                               ║
║  1. TEST MONITORING:                                         ║
║     → Check progress vs plan                                 ║
║     → Collect metrics continuously                           ║
║     → Identify deviations                                    ║
║                                                               ║
║  2. 7 TEST METRICS:                                          ║
║     → Project progress, Test progress                        ║
║     → Product quality, Defects                               ║
║     → Risk, Coverage, Cost                                   ║
║                                                               ║
║  3. KEY METRICS:                                             ║
║     → Execution % = Executed / Total                         ║
║     → Pass Rate = Passed / Executed                          ║
║     → Defect Rate = Defects / TCs                            ║
║                                                               ║
║  4. TEST CONTROL:                                            ║
║     → Take actions to fix problems                           ║
║     → Re-prioritize, Adjust schedule, Change approach        ║
║     → Extend timeline, Add resources                         ║
║                                                               ║
║  5. MONITORING → CONTROL:                                    ║
║     → Monitoring identifies problems                         ║
║     → Control fixes problems                                 ║
║     → Continuous cycle                                       ║
║                                                               ║
╚═══════════════════════════════════════════════════════════════╝
```

---

**Tiếp theo**: [Module 7.2: Test Reporting](./module-7.2-test-reporting.md)

---

**Version**: 1.0.0
**Last Updated**: November 2025
