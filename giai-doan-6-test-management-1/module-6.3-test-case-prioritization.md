# MODULE 6.3: TEST CASE PRIORITIZATION

**Thời lượng**: 2-3 giờ | **Độ khó**: ⭐⭐

---

## MỤC TIÊU HỌC TẬP

Sau khi hoàn thành module này, bạn sẽ:

| ID | Mục tiêu | Level |
|----|----------|-------|
| FL-5.1.10 | Áp dụng risk-based prioritization | K3 |
| FL-5.1.11 | Áp dụng coverage-based prioritization | K3 |
| FL-5.1.12 | Áp dụng requirements-based prioritization | K3 |

---

## 1. TEST CASE PRIORITIZATION LÀ GÌ?

### 1.1. Tổng Quan

```
╔═══════════════════════════════════════════════════════════════╗
║            TEST CASE PRIORITIZATION                           ║
╠═══════════════════════════════════════════════════════════════╣
║                                                               ║
║  📖 ĐỊNH NGHĨA:                                               ║
║     Process để order test cases dựa trên IMPORTANCE          ║
║     → Execute high-priority tests FIRST                      ║
║                                                               ║
║  🎯 TẠI SAO CẦN PRIORITIZATION:                               ║
║                                                               ║
║     ⏰ TIME CONSTRAINTS:                                      ║
║     → Không đủ time test hết                                 ║
║     → Release deadlines tight                                ║
║                                                               ║
║     🎯 MAXIMIZE VALUE:                                        ║
║     → Find critical bugs early                               ║
║     → Test important features first                          ║
║                                                               ║
║     💰 OPTIMIZE RESOURCES:                                    ║
║     → Focus effort on high-value tests                       ║
║     → Better ROI                                             ║
║                                                               ║
║  📊 3 APPROACHES:                                             ║
║     1. Risk-based Prioritization                             ║
║     2. Coverage-based Prioritization                         ║
║     3. Requirements-based Prioritization                     ║
║                                                               ║
╚═══════════════════════════════════════════════════════════════╝
```

---

## 2. RISK-BASED PRIORITIZATION

### 2.1. Concept

```
╔═══════════════════════════════════════════════════════════════╗
║            RISK-BASED PRIORITIZATION                          ║
╠═══════════════════════════════════════════════════════════════╣
║                                                               ║
║  📖 CONCEPT:                                                  ║
║     Prioritize test cases dựa trên RISK LEVEL của features   ║
║                                                               ║
║  📐 RISK CALCULATION:                                         ║
║                                                               ║
║     RISK = LIKELIHOOD × IMPACT                               ║
║                                                               ║
║     LIKELIHOOD (Xác suất lỗi):                               ║
║     • High: Complex, new code, many changes                  ║
║     • Medium: Moderate complexity, some changes              ║
║     • Low: Simple, stable, well-tested                       ║
║                                                               ║
║     IMPACT (Hậu quả nếu lỗi):                                ║
║     • High: Critical business function, many users           ║
║     • Medium: Important but not critical                     ║
║     • Low: Minor feature, few users                          ║
║                                                               ║
║  🎯 PRIORITIZATION:                                           ║
║     HIGH RISK → Test FIRST                                   ║
║     MEDIUM RISK → Test SECOND                                ║
║     LOW RISK → Test LAST (or skip if time runs out)         ║
║                                                               ║
╚═══════════════════════════════════════════════════════════════╝
```

### 2.2. Risk Matrix

```
                    IMPACT
               Low    Medium   High
            ┌──────┬────────┬──────┐
       High │  M   │   H    │  VH  │
            ├──────┼────────┼──────┤
LIKELIHOOD  │      │        │      │
     Medium │  L   │   M    │  H   │
            ├──────┼────────┼──────┤
        Low │  VL  │   L    │  M   │
            └──────┴────────┴──────┘

VH = Very High (Priority 1 - Test IMMEDIATELY)
H  = High       (Priority 2 - Test EARLY)
M  = Medium     (Priority 3 - Test NORMALLY)
L  = Low        (Priority 4 - Test IF TIME)
VL = Very Low   (Priority 5 - SKIP if necessary)
```

### 2.3. Ví Dụ: Shopee Feature Risk Assessment

| Feature | Likelihood | Impact | Risk | Priority |
|---------|-----------|--------|------|----------|
| **Payment processing** | High (Complex, nhiều gateway) | High (Business critical) | **VH** | **1** |
| **Search functionality** | Medium (Stable code) | High (Core feature) | **H** | **2** |
| **Order history** | Low (Simple, stable) | High (Important) | **M** | **3** |
| **Product recommendations** | High (New ML model) | Medium (Nice to have) | **H** | **2** |
| **Wishlist** | Low (Simple CRUD) | Low (Minor feature) | **VL** | **5** |
| **Share on social media** | Medium | Low | **L** | **4** |

**Test Order**:
1. Payment processing (VH)
2. Search functionality, Product recommendations (H)
3. Order history (M)
4. Share on social media (L)
5. Wishlist (VL) - Skip nếu không đủ time

### 2.4. Factors Ảnh Hưởng Risk

**LIKELIHOOD Factors:**
```
HIGH Likelihood:
✓ New feature (chưa tested)
✓ Complex logic (nhiều conditions)
✓ Nhiều dependencies
✓ Technology mới (team chưa quen)
✓ Frequent code changes
✓ Previous defects in area

LOW Likelihood:
✓ Stable, mature code
✓ Simple logic
✓ Well-tested trước đó
✓ Few changes
```

**IMPACT Factors:**
```
HIGH Impact:
✓ Business-critical (payment, checkout)
✓ Security/privacy sensitive
✓ Regulatory requirements
✓ High user traffic
✓ Revenue-generating
✓ Visible to all users

LOW Impact:
✓ Nice-to-have features
✓ Limited user base
✓ Non-critical functions
✓ Easy workarounds available
```

---

## 3. COVERAGE-BASED PRIORITIZATION

### 3.1. Concept

```
╔═══════════════════════════════════════════════════════════════╗
║           COVERAGE-BASED PRIORITIZATION                       ║
╠═══════════════════════════════════════════════════════════════╣
║                                                               ║
║  📖 CONCEPT:                                                  ║
║     Prioritize để achieve MAXIMUM COVERAGE sớm nhất          ║
║                                                               ║
║  🎯 STRATEGIES:                                               ║
║                                                               ║
║     1. REQUIREMENTS COVERAGE                                 ║
║        → Ensure mỗi requirement tested ít nhất 1 lần        ║
║        → Prioritize TCs covering untested requirements       ║
║                                                               ║
║     2. CODE COVERAGE                                         ║
║        → Execute TCs covering most code paths                ║
║        → Prioritize TCs với high statement/branch coverage   ║
║                                                               ║
║     3. FUNCTIONAL AREA COVERAGE                              ║
║        → Spread tests across different modules               ║
║        → Avoid focusing too much on one area                 ║
║                                                               ║
║     4. DIVERSITY COVERAGE                                    ║
║        → Mix test types (positive, negative, boundary)       ║
║        → Different test techniques                           ║
║                                                               ║
║  📊 GOAL:                                                     ║
║     Achieve broad coverage early → Find diverse bugs fast    ║
║                                                               ║
╚═══════════════════════════════════════════════════════════════╝
```

### 3.2. Requirements Coverage Strategy

**Example**: E-commerce app với 10 requirements

**Test Cases**:
```
TC1: Covers Req-1, Req-2
TC2: Covers Req-2, Req-3, Req-4
TC3: Covers Req-5
TC4: Covers Req-1, Req-6
TC5: Covers Req-7, Req-8, Req-9
TC6: Covers Req-3
TC7: Covers Req-10
TC8: Covers Req-4, Req-5
```

**Prioritization để maximize coverage nhanh**:

| Order | Test Case | New Reqs Covered | Cumulative Coverage |
|-------|-----------|------------------|---------------------|
| 1 | TC2 | Req-2, 3, 4 (3 reqs) | 3/10 = 30% |
| 2 | TC5 | Req-7, 8, 9 (3 reqs) | 6/10 = 60% |
| 3 | TC1 | Req-1 (1 req) | 7/10 = 70% |
| 4 | TC3 | Req-5 (1 req) | 8/10 = 80% |
| 5 | TC4 | Req-6 (1 req) | 9/10 = 90% |
| 6 | TC7 | Req-10 (1 req) | 10/10 = 100% ✅ |
| 7 | TC6 | (none - already covered) | 100% |
| 8 | TC8 | (none - already covered) | 100% |

**Strategy**: Chạy TC2, TC5, TC1, TC3, TC4, TC7 trước để đạt 100% coverage nhanh.

### 3.3. Additional Coverage Factors (ACoF)

**Technique** (ISO 29119):
```
Priority Score = Σ (Coverage Factor × Weight)

Coverage Factors:
• Requirements covered
• Code covered (statement/branch %)
• Functions tested
• User scenarios covered

Weights depend on project priorities
```

---

## 4. REQUIREMENTS-BASED PRIORITIZATION

### 4.1. Concept

```
╔═══════════════════════════════════════════════════════════════╗
║         REQUIREMENTS-BASED PRIORITIZATION                     ║
╠═══════════════════════════════════════════════════════════════╣
║                                                               ║
║  📖 CONCEPT:                                                  ║
║     Prioritize test cases dựa trên PRIORITY của requirements ║
║                                                               ║
║  🎯 PROCESS:                                                  ║
║                                                               ║
║     1. REQUIREMENTS PRIORITIZED (by PO/Business)             ║
║        → Must-have (P1)                                      ║
║        → Should-have (P2)                                    ║
║        → Nice-to-have (P3)                                   ║
║                                                               ║
║     2. MAP TEST CASES TO REQUIREMENTS                        ║
║        → Traceability matrix                                 ║
║                                                               ║
║     3. INHERIT PRIORITY                                      ║
║        → TCs testing P1 requirements → P1 priority           ║
║        → TCs testing P2 requirements → P2 priority           ║
║                                                               ║
║     4. EXECUTE IN ORDER                                      ║
║        → P1 tests first                                      ║
║        → P2 tests second                                     ║
║        → P3 tests if time allows                             ║
║                                                               ║
╚═══════════════════════════════════════════════════════════════╝
```

### 4.2. Ví Dụ: MosCo W Prioritization

**Requirements** (MoSCoW method):
```
MUST HAVE (P1):
  Req-1: User can login
  Req-2: User can make payment
  Req-3: User can view transaction history

SHOULD HAVE (P2):
  Req-4: User can save payment methods
  Req-5: User can set up recurring payments

COULD HAVE (P3):
  Req-6: User can customize dashboard
  Req-7: User can export statements as PDF

WON'T HAVE (this release):
  Req-8: Cryptocurrency support
```

**Test Cases**:
```
TC-001: Login với valid credentials → Tests Req-1 (P1)
TC-002: Login với invalid credentials → Tests Req-1 (P1)
TC-003: Payment with credit card → Tests Req-2 (P1)
TC-004: Payment with insufficient funds → Tests Req-2 (P1)
TC-005: View transaction history → Tests Req-3 (P1)
TC-006: Save new payment method → Tests Req-4 (P2)
TC-007: Set up recurring payment → Tests Req-5 (P2)
TC-008: Customize dashboard → Tests Req-6 (P3)
```

**Prioritized Test Execution Order**:
```
PRIORITY 1 (MUST HAVE):
  1. TC-001 (Login valid)
  2. TC-002 (Login invalid)
  3. TC-003 (Payment credit card)
  4. TC-004 (Payment insufficient)
  5. TC-005 (View history)

PRIORITY 2 (SHOULD HAVE):
  6. TC-006 (Save payment method)
  7. TC-007 (Recurring payment)

PRIORITY 3 (COULD HAVE):
  8. TC-008 (Customize dashboard)
```

### 4.3. Traceability Matrix

```
╔═══════════════════════════════════════════════════════════════╗
║              TRACEABILITY MATRIX                              ║
╠═══════════════════════════════════════════════════════════════╣
║                                                               ║
║  Requirement │ Priority │ Test Cases        │ Status         ║
║  ────────────┼──────────┼───────────────────┼────────────    ║
║  Req-1       │   P1     │ TC-001, TC-002    │ ✅ Passed      ║
║  Req-2       │   P1     │ TC-003, TC-004    │ 🔄 In Progress ║
║  Req-3       │   P1     │ TC-005            │ ⏳ Not Started ║
║  Req-4       │   P2     │ TC-006            │ ⏳ Not Started ║
║  Req-5       │   P2     │ TC-007            │ ⏳ Not Started ║
║  Req-6       │   P3     │ TC-008            │ ⏳ Not Started ║
║                                                               ║
╚═══════════════════════════════════════════════════════════════╝
```

**Benefits**:
- ✅ Clear mapping requirements → test cases
- ✅ Easy to track coverage
- ✅ Prioritization aligned với business priorities
- ✅ Can demonstrate compliance (traceability)

---

## 5. KẾT HỢP CÁC APPROACHES

### 5.1. Multi-Criteria Prioritization

```
╔═══════════════════════════════════════════════════════════════╗
║          MULTI-CRITERIA PRIORITIZATION                        ║
╠═══════════════════════════════════════════════════════════════╣
║                                                               ║
║  📊 WEIGHTED SCORE MODEL:                                     ║
║                                                               ║
║     Priority Score = (Risk × W1) + (Coverage × W2) +         ║
║                      (Requirement Priority × W3)             ║
║                                                               ║
║     Where W1 + W2 + W3 = 1 (weights sum to 100%)            ║
║                                                               ║
║  🎯 EXAMPLE WEIGHTS:                                          ║
║     W1 (Risk) = 50%                                          ║
║     W2 (Coverage) = 30%                                      ║
║     W3 (Req Priority) = 20%                                  ║
║                                                               ║
╚═══════════════════════════════════════════════════════════════╝
```

### 5.2. Ví Dụ: Scoring Model

**Test Cases cho Grab app**:

| TC | Risk | Coverage | Req Priority | Score | Final Priority |
|----|------|----------|--------------|-------|----------------|
| TC-1 | 9 (VH) | 8 (covers 3 reqs) | 10 (P1) | **8.9** | **1** |
| TC-2 | 8 (H) | 7 | 10 (P1) | **8.3** | **2** |
| TC-3 | 7 (H) | 9 (covers 4 reqs) | 8 (P2) | **7.7** | **3** |
| TC-4 | 5 (M) | 6 | 8 (P2) | **6.0** | **4** |
| TC-5 | 3 (L) | 5 | 5 (P3) | **4.1** | **5** |

**Calculation for TC-1**:
```
Risk = 9/10 = 0.9
Coverage = 8/10 = 0.8
Req Priority = 10/10 = 1.0

Score = (0.9 × 0.5) + (0.8 × 0.3) + (1.0 × 0.2)
      = 0.45 + 0.24 + 0.20
      = 0.89 = 8.9/10
```

### 5.3. Decision Tree Approach

```
                Test Case
                    │
        ┌───────────┴───────────┐
        │                       │
    Critical Feature?      Non-Critical
        │                       │
    ┌───┴───┐              Priority 3-5
    │       │
  High    Medium
  Risk    Risk
    │       │
Priority 1  Priority 2
```

---

## 6. ADDITIONAL FACTORS

### 6.1. Other Prioritization Factors

```
╔═══════════════════════════════════════════════════════════════╗
║            OTHER PRIORITIZATION FACTORS                       ║
╠═══════════════════════════════════════════════════════════════╣
║                                                               ║
║  ⏰ TIME FACTORS:                                             ║
║     • Test execution time (quick tests first?)               ║
║     • Time-sensitive features (seasonal, deadlines)          ║
║                                                               ║
║  📊 DEFECT HISTORY:                                           ║
║     • Areas with many past defects → Higher priority         ║
║     • Defect-prone modules                                   ║
║                                                               ║
║  👥 CUSTOMER IMPACT:                                          ║
║     • Features used by most users                            ║
║     • Customer-requested features                            ║
║     • SLA commitments                                        ║
║                                                               ║
║  🔗 DEPENDENCIES:                                             ║
║     • Test blocking other tests → Higher priority            ║
║     • Integration points                                     ║
║                                                               ║
║  🔄 TEST TYPE:                                                ║
║     • Smoke tests → FIRST (sanity check)                     ║
║     • Regression → EARLY (ensure stability)                  ║
║     • Exploratory → AFTER scripted tests                     ║
║                                                               ║
╚═══════════════════════════════════════════════════════════════╝
```

### 6.2. Smoke Test Priority

```
ALWAYS FIRST: Smoke Tests
│
├─ Can system start?
├─ Can user login?
├─ Can access main pages?
└─ Critical paths functional?
   │
   └─ IF PASS → Continue with prioritized tests
      IF FAIL → STOP, fix blocker bugs first
```

---

## 7. CÂU HỎI ÔN TẬP

### Câu 1 (K2)
Risk-based prioritization dựa trên công thức nào?

A. Risk = Likelihood + Impact
B. Risk = Likelihood × Impact
C. Risk = Likelihood / Impact
D. Risk = Impact only

<details>
<summary>Đáp án</summary>

**B. Risk = Likelihood × Impact**

Risk là tích của xác suất (likelihood) và hậu quả (impact).
</details>

---

### Câu 2 (K3)
Feature có Likelihood=High, Impact=Low. Risk level?

A. Very High
B. High
C. Medium
D. Low

<details>
<summary>Đáp án</summary>

**C. Medium**

Theo risk matrix: High likelihood × Low impact = Medium risk.
</details>

---

### Câu 3 (K2)
Coverage-based prioritization aims để gì?

A. Test high-risk features only
B. Achieve maximum coverage sớm
C. Test requirements theo thứ tự
D. Minimize test execution time

<details>
<summary>Đáp án</summary>

**B. Achieve maximum coverage sớm**

Coverage-based wants broad coverage early để find diverse bugs fast.
</details>

---

### Câu 4 (K2)
Requirements-based prioritization lấy priority từ đâu?

A. Test Manager decides
B. Based on code complexity
C. Business/PO prioritizes requirements
D. Random assignment

<details>
<summary>Đáp án</summary>

**C. Business/PO prioritizes requirements**

Requirements-based inherits priority từ business priorities (MoSCoW, etc.).
</details>

---

### Câu 5 (K2)
Test case nào nên execute FIRST?

A. Longest execution time
B. Smoke tests
C. Exploratory tests
D. Performance tests

<details>
<summary>Đáp án</summary>

**B. Smoke tests**

Smoke tests always first để verify basic functionality trước khi continue.
</details>

---

### Câu 6 (K3)
TC-1 covers 3 requirements, TC-2 covers 1 requirement. Coverage-based prioritization?

A. TC-1 first (covers more)
B. TC-2 first (simpler)
C. No difference
D. Cannot determine

<details>
<summary>Đáp án</summary>

**A. TC-1 first (covers more)**

Coverage-based prefers tests covering more requirements để maximize coverage nhanh.
</details>

---

## 8. CHECKLIST TỰ ĐÁNH GIÁ

### Risk-Based
- [ ] Hiểu công thức Risk = Likelihood × Impact
- [ ] Sử dụng risk matrix để assess risk level
- [ ] Identify high-risk features trong project
- [ ] Prioritize test cases based on risk

### Coverage-Based
- [ ] Hiểu goal: maximize coverage early
- [ ] Analyze test cases để identify coverage
- [ ] Prioritize TCs covering most requirements/code
- [ ] Balance coverage across functional areas

### Requirements-Based
- [ ] Map test cases to requirements (traceability)
- [ ] Inherit priority từ requirement priority
- [ ] Understand MoSCoW method
- [ ] Create traceability matrix

### Multi-Criteria
- [ ] Combine multiple prioritization approaches
- [ ] Calculate weighted scores
- [ ] Adjust weights based on project needs
- [ ] Consider additional factors (time, defect history)

---

## TỔNG KẾT

```
╔═══════════════════════════════════════════════════════════════╗
║                    KEY TAKEAWAYS                              ║
╠═══════════════════════════════════════════════════════════════╣
║                                                               ║
║  1. RISK-BASED:                                              ║
║     → Risk = Likelihood × Impact                             ║
║     → High risk → Test FIRST                                 ║
║     → Focus on critical, complex areas                       ║
║                                                               ║
║  2. COVERAGE-BASED:                                          ║
║     → Maximize coverage nhanh                                ║
║     → Spread tests across requirements/code                  ║
║     → Broad coverage → Find diverse bugs early               ║
║                                                               ║
║  3. REQUIREMENTS-BASED:                                      ║
║     → Align với business priorities                          ║
║     → Must-have requirements tested first                    ║
║     → Traceability matrix ensures coverage                   ║
║                                                               ║
║  4. BEST PRACTICE:                                           ║
║     → COMBINE approaches (weighted scoring)                  ║
║     → Always run SMOKE TESTS first                           ║
║     → Adjust priorities based on feedback                    ║
║                                                               ║
╚═══════════════════════════════════════════════════════════════╝
```

---

**Tiếp theo**: [Module 6.4: Risk Management](./module-6.4-risk-management.md)

---

**Version**: 1.0.0
**Last Updated**: November 2025
