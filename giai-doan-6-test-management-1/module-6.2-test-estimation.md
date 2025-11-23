# MODULE 6.2: TEST ESTIMATION

**Thời lượng**: 3-4 giờ | **Độ khó**: ⭐⭐⭐

---

## MỤC TIÊU HỌC TẬP

Sau khi hoàn thành module này, bạn sẽ:

| ID | Mục tiêu | Level |
|----|----------|-------|
| FL-5.1.6 | Áp dụng estimation based on ratios | K3 |
| FL-5.1.7 | Áp dụng extrapolation | K3 |
| FL-5.1.8 | Áp dụng Wideband Delphi (Planning Poker) | K3 |
| FL-5.1.9 | Áp dụng Three-point estimation | K3 |

---

## 1. TEST ESTIMATION LÀ GÌ?

### 1.1. Tổng Quan

```
╔═══════════════════════════════════════════════════════════════╗
║                    TEST ESTIMATION                            ║
╠═══════════════════════════════════════════════════════════════╣
║                                                               ║
║  📖 ĐỊNH NGHĨA:                                               ║
║     Process để predict EFFORT, TIME, và RESOURCES cần cho    ║
║     testing activities                                        ║
║                                                               ║
║  🎯 MỤC ĐÍCH:                                                 ║
║     • Plan resources                                         ║
║     • Set realistic schedules                                ║
║     • Budget allocation                                      ║
║     • Stakeholder expectations                               ║
║                                                               ║
║  📊 WHAT TO ESTIMATE:                                         ║
║     • Test effort (person-hours/days)                        ║
║     • Test duration (calendar time)                          ║
║     • Number of test cases                                   ║
║     • Defects expected                                       ║
║                                                               ║
║  ⚠️ CHALLENGES:                                               ║
║     • Requirements unclear                                   ║
║     • Changing scope                                         ║
║     • Team experience varies                                 ║
║     • Historical data limited                                ║
║                                                               ║
╚═══════════════════════════════════════════════════════════════╝
```

### 1.2. Factors Ảnh Hưởng Estimation

```
╔═══════════════════════════════════════════════════════════════╗
║              FACTORS AFFECTING ESTIMATION                     ║
╠═══════════════════════════════════════════════════════════════╣
║                                                               ║
║  📋 PRODUCT FACTORS:                                          ║
║     • Complexity của application                             ║
║     • Size (number of features, LOC)                         ║
║     • Quality of requirements                                ║
║     • Technology stack (new or familiar)                     ║
║                                                               ║
║  👥 TEAM FACTORS:                                             ║
║     • Team size và skills                                    ║
║     • Experience with domain                                 ║
║     • Availability (part-time/full-time)                     ║
║     • Team location (co-located/distributed)                 ║
║                                                               ║
║  🔧 PROCESS FACTORS:                                          ║
║     • Test approach (manual vs automated)                    ║
║     • Test techniques used                                   ║
║     • Tool availability                                      ║
║     • Test environment stability                             ║
║                                                               ║
║  📈 PROJECT FACTORS:                                          ║
║     • Schedule constraints                                   ║
║     • Risk level                                             ║
║     • Regulatory requirements                                ║
║     • Budget constraints                                     ║
║                                                               ║
╚═══════════════════════════════════════════════════════════════╝
```

---

## 2. TECHNIQUE 1: ESTIMATION BASED ON RATIOS

### 2.1. Concept

```
╔═══════════════════════════════════════════════════════════════╗
║            ESTIMATION BASED ON RATIOS                         ║
╠═══════════════════════════════════════════════════════════════╣
║                                                               ║
║  📖 CONCEPT:                                                  ║
║     Sử dụng HISTORICAL DATA từ past projects để tính ratio   ║
║     và apply cho project mới                                 ║
║                                                               ║
║  📐 COMMON RATIOS:                                            ║
║                                                               ║
║     RATIO 1: Test vs Development                             ║
║     ────────────────────────────────────────                 ║
║     Test Effort = Dev Effort × Ratio                         ║
║     Typical: 30-40% của dev effort                           ║
║                                                               ║
║     RATIO 2: Test Cases per Requirement                      ║
║     ────────────────────────────────────────                 ║
║     # Test Cases = # Requirements × Ratio                    ║
║     Typical: 3-5 test cases per requirement                  ║
║                                                               ║
║     RATIO 3: Test Cases per Function Point                   ║
║     ────────────────────────────────────────                 ║
║     # Test Cases = Function Points × Ratio                   ║
║     Typical: 1.2-1.5 test cases per FP                       ║
║                                                               ║
║     RATIO 4: Defects per Test Case                           ║
║     ────────────────────────────────────────                 ║
║     Expected Defects = # Test Cases × Ratio                  ║
║     Typical: 0.1-0.3 defects per test case                   ║
║                                                               ║
╚═══════════════════════════════════════════════════════════════╝
```

### 2.2. Ví Dụ 1: Test Effort dựa vào Dev Effort

**Scenario**: Shopee checkout feature

**Historical Data** (3 past projects):
```
Project A: Dev effort = 100 days, Test effort = 35 days → Ratio = 0.35
Project B: Dev effort = 80 days,  Test effort = 28 days → Ratio = 0.35
Project C: Dev effort = 120 days, Test effort = 48 days → Ratio = 0.40

Average Ratio = (0.35 + 0.35 + 0.40) / 3 = 0.367 ≈ 37%
```

**New Project**:
```
Development effort estimated: 150 days

Test Effort = 150 days × 0.37 = 55.5 days ≈ 56 days
```

**Refinement**: Adjust for complexity
```
New project có higher complexity → Add 10% buffer
Test Effort = 56 × 1.10 = 61.6 ≈ 62 days
```

### 2.3. Ví Dụ 2: Test Cases per Requirement

**Historical Data**:
```
Past Project:
- 50 requirements
- 180 test cases designed
- Ratio = 180 / 50 = 3.6 test cases per requirement
```

**New Project**:
```
Requirements: 75

Estimated Test Cases = 75 × 3.6 = 270 test cases
```

**Effort Calculation**:
```
Avg time per test case (from history):
- Design: 1 hour
- Execution: 0.5 hour
- Total: 1.5 hours per test case

Total Effort = 270 × 1.5 = 405 hours = 51 days (8 hours/day)
```

### 2.4. Pros & Cons

| Pros ✅ | Cons ❌ |
|---------|---------|
| Based on real data | Requires historical data |
| Quick to calculate | Past may not reflect future |
| Easy to explain | Projects must be similar |
| Objective | Doesn't account for unique factors |

---

## 3. TECHNIQUE 2: EXTRAPOLATION

### 3.1. Concept

```
╔═══════════════════════════════════════════════════════════════╗
║                    EXTRAPOLATION                              ║
╠═══════════════════════════════════════════════════════════════╣
║                                                               ║
║  📖 CONCEPT:                                                  ║
║     Measure actual progress, rồi EXTRAPOLATE (ngoại suy)     ║
║     để predict total effort                                  ║
║                                                               ║
║  🔄 PROCESS:                                                  ║
║                                                               ║
║     1. Complete PART of work                                 ║
║     2. Measure ACTUAL time taken                             ║
║     3. Calculate rate/velocity                               ║
║     4. EXTRAPOLATE to total work                             ║
║                                                               ║
║  📐 FORMULA:                                                  ║
║                                                               ║
║           Total Effort                                       ║
║     ────────────────────────────────────                     ║
║     Actual Effort     Total Work                             ║
║     ───────────── = ─────────────                            ║
║     Work Completed   Work Completed                          ║
║                                                               ║
║  ⏰ WHEN TO USE:                                              ║
║     • After completing initial work                          ║
║     • Have measurable progress                               ║
║     • Remaining work similar to completed                    ║
║                                                               ║
╚═══════════════════════════════════════════════════════════════╝
```

### 3.2. Ví Dụ 1: Test Case Design

**Scenario**: Designing test cases for Momo app

**Metrics after Week 1**:
```
Total Features to test: 20 features
Features completed: 5 features
Time taken: 40 hours

Rate = 40 hours / 5 features = 8 hours per feature
```

**Extrapolation**:
```
Remaining features = 20 - 5 = 15 features

Estimated remaining effort = 15 × 8 = 120 hours

Total effort = 40 (actual) + 120 (estimated) = 160 hours = 20 days
```

### 3.3. Ví Dụ 2: Test Execution

**Scenario**: Regression testing

**Metrics after Day 2**:
```
Total test cases: 500
Test cases executed: 120
Time taken: 16 hours (2 days × 8 hours)

Rate = 16 hours / 120 TCs = 0.133 hours per TC
     = 7.5 TCs per hour
```

**Extrapolation**:
```
Remaining TCs = 500 - 120 = 380

Estimated time = 380 / 7.5 = 50.67 hours ≈ 51 hours ≈ 6.4 days

Total duration = 2 days (actual) + 6.4 days = 8.4 days ≈ 9 days
```

**Add Buffer** (for defect fixing, retesting):
```
Final estimate = 9 days × 1.2 = 10.8 days ≈ 11 days
```

### 3.4. Ví Dụ 3: Defect Fixing

**Metrics**:
```
Week 1: Fixed 8 bugs, took 32 hours → 4 hours per bug
Total bugs: 50

Remaining bugs = 50 - 8 = 42
Estimated time = 42 × 4 = 168 hours = 21 days
```

### 3.5. Pros & Cons

| Pros ✅ | Cons ❌ |
|---------|---------|
| Based on actual project data | Requires initial work done |
| Reflects current team velocity | Assumes consistent velocity |
| Can adjust mid-project | Early data may not be representative |
| Accurate for similar tasks | Learning curve not accounted |

---

## 4. TECHNIQUE 3: WIDEBAND DELPHI / PLANNING POKER

### 4.1. Wideband Delphi Concept

```
╔═══════════════════════════════════════════════════════════════╗
║                  WIDEBAND DELPHI                              ║
╠═══════════════════════════════════════════════════════════════╣
║                                                               ║
║  📖 CONCEPT:                                                  ║
║     TEAM-BASED estimation technique với multiple rounds      ║
║     để reach CONSENSUS                                       ║
║                                                               ║
║  👥 PARTICIPANTS:                                             ║
║     • Moderator (facilitates)                                ║
║     • Experts (3-7 people: devs, testers, BA)                ║
║                                                               ║
║  🔄 PROCESS:                                                  ║
║                                                               ║
║     1. KICKOFF                                               ║
║        → Present task to estimate                            ║
║        → Clarify requirements                                ║
║                                                               ║
║     2. INDIVIDUAL ESTIMATION                                 ║
║        → Each expert estimates INDEPENDENTLY                 ║
║        → Write down estimate (no discussion yet)             ║
║                                                               ║
║     3. REVEAL ESTIMATES                                      ║
║        → All estimates shown SIMULTANEOUSLY                  ║
║        → Prevent anchoring bias                              ║
║                                                               ║
║     4. DISCUSSION                                            ║
║        → Discuss differences (especially outliers)           ║
║        → Share reasoning                                     ║
║        → No arguing, just explain                            ║
║                                                               ║
║     5. RE-ESTIMATE                                           ║
║        → Estimate again với new information                  ║
║        → Repeat until CONSENSUS (estimates converge)         ║
║                                                               ║
║     6. FINAL ESTIMATE                                        ║
║        → Average, median, or agreed value                    ║
║                                                               ║
╚═══════════════════════════════════════════════════════════════╝
```

### 4.2. Planning Poker (Agile Variant)

```
╔═══════════════════════════════════════════════════════════════╗
║                    PLANNING POKER                             ║
╠═══════════════════════════════════════════════════════════════╣
║                                                               ║
║  📖 CONCEPT:                                                  ║
║     Wideband Delphi adapted for Agile, dùng STORY POINTS     ║
║                                                               ║
║  🎴 FIBONACCI CARDS:                                          ║
║     0, ½, 1, 2, 3, 5, 8, 13, 20, 40, 100, ?, ☕              ║
║     (Larger numbers = More uncertainty)                      ║
║                                                               ║
║  🔄 PROCESS:                                                  ║
║                                                               ║
║     1. PO presents USER STORY                                ║
║     2. Team asks QUESTIONS                                   ║
║     3. Each member picks CARD (face down)                    ║
║     4. REVEAL simultaneously                                 ║
║     5. Highest & Lowest explain REASONING                    ║
║     6. RE-VOTE until consensus                               ║
║                                                               ║
║  🎯 STORY POINTS:                                             ║
║     • Relative size (not hours)                              ║
║     • Consider: Complexity, Risk, Uncertainty                ║
║     • 1 SP = Simple story (reference)                        ║
║     • 8 SP = Too big, split story                            ║
║                                                               ║
╚═══════════════════════════════════════════════════════════════╝
```

### 4.3. Ví Dụ: Planning Poker Session

**User Story**:
```
As a Shopee customer,
I want to save items to wishlist,
So that I can purchase them later.
```

**Round 1** - Initial estimates:
```
Developer A: 3 SP (thinks it's straightforward)
Developer B: 8 SP (worries about sync across devices)
Tester C: 5 SP (moderate testing effort)
BA D: 3 SP (simple feature)

Outliers: Developer B (8 SP - highest)
```

**Discussion**:
```
Dev B: "We need to sync wishlist across mobile & web, handle
        offline mode, what if user not logged in?"

Dev A: "Oh, I didn't think about sync. That's complex."

PO: "For MVP, wishlist only for logged-in users, mobile-only."

Dev B: "Ah, then it's simpler. No sync across platforms for now."
```

**Round 2** - Re-estimate:
```
Developer A: 3 SP
Developer B: 5 SP
Tester C: 5 SP
BA D: 3 SP

Converging! Average ≈ 4 SP
```

**Round 3** - Final:
```
Team agrees: 5 SP

CONSENSUS REACHED ✅
```

### 4.4. Pros & Cons

| Pros ✅ | Cons ❌ |
|---------|---------|
| Team consensus | Time-consuming |
| Multiple perspectives | Requires team availability |
| Shared understanding | Dominant voices may influence |
| Identifies assumptions | Not suitable for large backlogs |
| Engaging/fun (poker variant) | Estimates still subjective |

---

## 5. TECHNIQUE 4: THREE-POINT ESTIMATION

### 5.1. Concept

```
╔═══════════════════════════════════════════════════════════════╗
║              THREE-POINT ESTIMATION (PERT)                    ║
╠═══════════════════════════════════════════════════════════════╣
║                                                               ║
║  📖 CONCEPT:                                                  ║
║     Estimate 3 scenarios để tính WEIGHTED AVERAGE            ║
║     Từ PERT (Program Evaluation & Review Technique)          ║
║                                                               ║
║  📐 THREE ESTIMATES:                                          ║
║                                                               ║
║     🌟 OPTIMISTIC (O)                                         ║
║        → Best case scenario                                  ║
║        → Everything goes smoothly                            ║
║        → ~10% probability                                    ║
║                                                               ║
║     📊 MOST LIKELY (M)                                        ║
║        → Normal scenario                                     ║
║        → Based on experience                                 ║
║        → ~80% probability                                    ║
║                                                               ║
║     ⚠️ PESSIMISTIC (P)                                        ║
║        → Worst case scenario                                 ║
║        → Everything goes wrong                               ║
║        → ~10% probability                                    ║
║                                                               ║
║  🧮 FORMULA:                                                  ║
║                                                               ║
║           O + 4M + P                                         ║
║     E = ──────────────                                       ║
║               6                                              ║
║                                                               ║
║     E = Expected estimate                                    ║
║     (Weighted average, biased toward Most Likely)            ║
║                                                               ║
╚═══════════════════════════════════════════════════════════════╝
```

### 5.2. Ví Dụ 1: Test Execution Duration

**Task**: Execute regression test suite (500 test cases)

**Three Estimates**:
```
OPTIMISTIC (O):  10 days
  → All tests pass
  → No environment issues
  → Team fully available

MOST LIKELY (M): 15 days
  → Some bugs found, need retesting
  → Minor environment glitches
  → Normal team availability

PESSIMISTIC (P): 25 days
  → Many bugs found
  → Environment unstable
  → Team members sick/unavailable
```

**Calculate Expected**:
```
E = (O + 4M + P) / 6
E = (10 + 4×15 + 25) / 6
E = (10 + 60 + 25) / 6
E = 95 / 6
E = 15.83 days ≈ 16 days
```

**Interpretation**: Plan for **16 days** (biased toward most likely 15 days, but accounts for risk).

### 5.3. Ví Dụ 2: Test Case Design

**Task**: Design test cases cho checkout feature

**Three Estimates**:
```
OPTIMISTIC (O):  30 hours
  → Requirements clear
  → Reuse existing test cases
  → No interruptions

MOST LIKELY (M): 50 hours
  → Some requirements clarification needed
  → Some new test cases
  → Normal interruptions (meetings, etc.)

PESSIMISTIC (P): 80 hours
  → Requirements unclear, many questions
  → All new test cases
  → Many interruptions, team dependencies
```

**Calculate**:
```
E = (30 + 4×50 + 80) / 6
E = (30 + 200 + 80) / 6
E = 310 / 6
E = 51.67 hours ≈ 52 hours ≈ 6.5 days
```

### 5.4. Standard Deviation (Uncertainty)

```
╔═══════════════════════════════════════════════════════════════╗
║                  STANDARD DEVIATION                           ║
╠═══════════════════════════════════════════════════════════════╣
║                                                               ║
║  📐 FORMULA:                                                  ║
║                                                               ║
║           P - O                                              ║
║     SD = ───────                                             ║
║             6                                                ║
║                                                               ║
║  📊 INTERPRETATION:                                           ║
║     • Large SD = High uncertainty                            ║
║     • Small SD = Low uncertainty                             ║
║                                                               ║
║  📈 CONFIDENCE INTERVAL:                                      ║
║     • 68% chance: E ± 1 SD                                   ║
║     • 95% chance: E ± 2 SD                                   ║
║                                                               ║
╚═══════════════════════════════════════════════════════════════╝
```

**Example** (Test Execution):
```
O = 10, M = 15, P = 25
E = 16 days

SD = (25 - 10) / 6 = 15 / 6 = 2.5 days

68% confidence: 16 ± 2.5 = 13.5 to 18.5 days
95% confidence: 16 ± 5.0 = 11 to 21 days
```

**Reporting**: "Testing will take 16 days, with 68% confidence between 13.5-18.5 days."

### 5.5. Pros & Cons

| Pros ✅ | Cons ❌ |
|---------|---------|
| Accounts for uncertainty | Requires 3 estimates (more work) |
| Weighted toward realistic | O and P can be arbitrary |
| Provides confidence interval | Formula may seem complex |
| Quantifies risk | Assumes certain distribution |

---

## 6. SO SÁNH 4 KỸ THUẬT

| Technique | Data Needed | Best For | Accuracy | Effort |
|-----------|-------------|----------|----------|--------|
| **Ratios** | Historical data | Similar projects | Medium | Low |
| **Extrapolation** | Partial completion | In-progress work | High | Low |
| **Wideband Delphi** | Team expertise | Complex, uncertain | Medium-High | High |
| **Three-Point** | O/M/P estimates | Risk analysis | Medium | Medium |

**Recommendation**: Combine techniques!
```
Example:
1. Use Ratios for initial ballpark
2. Use Planning Poker for story points
3. Use Three-Point for high-risk tasks
4. Use Extrapolation to refine mid-project
```

---

## 7. BÀI TẬP THỰC HÀNH

### Bài 1: Estimation Based on Ratios

**Scenario**: Grab driver app feature

**Historical Data**:
- Past Project: 30 requirements, 110 test cases designed
- New Project: 45 requirements

**Câu hỏi**: Estimate số test cases cần design?

<details>
<summary>Đáp án</summary>

**Ratio** = 110 test cases / 30 requirements = 3.67 TC/requirement

**Estimated Test Cases** = 45 × 3.67 = 165 test cases

If avg 1.5 hours per TC:
**Total Effort** = 165 × 1.5 = 247.5 hours ≈ 31 days

</details>

---

### Bài 2: Extrapolation

**Scenario**: Test execution

**Metrics**:
- Total test cases: 800
- Executed (after 3 days): 240 test cases
- Time: 24 hours

**Câu hỏi**:
1. Estimate remaining time?
2. Total duration?

<details>
<summary>Đáp án</summary>

**1. Rate** = 24 hours / 240 TCs = 0.1 hour per TC = 10 TCs per hour

**Remaining** = 800 - 240 = 560 TCs

**Remaining Time** = 560 / 10 = 56 hours = 7 days

**2. Total Duration** = 3 days (actual) + 7 days (estimated) = **10 days**

With 20% buffer: 10 × 1.2 = **12 days**

</details>

---

### Bài 3: Three-Point Estimation

**Scenario**: Performance testing

**Estimates**:
- Optimistic: 5 days
- Most Likely: 10 days
- Pessimistic: 20 days

**Câu hỏi**:
1. Calculate expected duration?
2. Calculate standard deviation?
3. 68% confidence interval?

<details>
<summary>Đáp án</summary>

**1. Expected (E)**:
```
E = (O + 4M + P) / 6
E = (5 + 4×10 + 20) / 6
E = (5 + 40 + 20) / 6
E = 65 / 6
E = 10.83 days ≈ 11 days
```

**2. Standard Deviation (SD)**:
```
SD = (P - O) / 6
SD = (20 - 5) / 6
SD = 15 / 6
SD = 2.5 days
```

**3. 68% Confidence Interval**:
```
E ± 1 SD = 11 ± 2.5 = 8.5 to 13.5 days
```

**Answer**: Performance testing will take **11 days**, with 68% confidence between **8.5-13.5 days**.

</details>

---

## 8. CÂU HỎI ÔN TẬP

### Câu 1 (K2)
Estimation based on ratios dựa vào gì?

A. Team voting
B. Historical data từ past projects
C. Three scenarios (O/M/P)
D. Actual progress measurement

<details>
<summary>Đáp án</summary>

**B. Historical data từ past projects**

Ratios use past data to calculate typical ratios (e.g., test effort = 35% of dev effort).
</details>

---

### Câu 2 (K3)
Dev effort = 100 days. Historical ratio: Test = 30% of Dev. Test effort?

A. 30 days
B. 70 days
C. 100 days
D. 130 days

<details>
<summary>Đáp án</summary>

**A. 30 days**

Test Effort = 100 × 0.30 = 30 days
</details>

---

### Câu 3 (K2)
Extrapolation technique sử dụng khi nào?

A. Before project starts
B. After completing part of work
C. Only at project end
D. During requirements phase

<details>
<summary>Đáp án</summary>

**B. After completing part of work**

Extrapolation measures actual progress rồi extrapolate để predict total.
</details>

---

### Câu 4 (K3)
Executed 100 TCs trong 20 hours. Còn 300 TCs. Estimated remaining time?

A. 20 hours
B. 40 hours
C. 60 hours
D. 80 hours

<details>
<summary>Đáp án</summary>

**C. 60 hours**

Rate = 20h / 100 TCs = 0.2h per TC
Remaining = 300 × 0.2 = 60 hours
</details>

---

### Câu 5 (K2)
Planning Poker là variant của technique nào?

A. Extrapolation
B. Three-Point Estimation
C. Wideband Delphi
D. Ratios

<details>
<summary>Đáp án</summary>

**C. Wideband Delphi**

Planning Poker là Agile adaptation của Wideband Delphi, uses Fibonacci cards.
</details>

---

### Câu 6 (K3)
Three-Point Estimation, O=5, M=10, P=20. Expected (E)?

A. 10
B. 11
C. 11.67
D. 15

<details>
<summary>Đáp án</summary>

**C. 11.67** (or approximately 12)

E = (5 + 4×10 + 20) / 6 = 65 / 6 = 10.83 ≈ 11 days

(Closest answer is C if options are 10, 11, 11.67, 15)
</details>

---

## 9. CHECKLIST TỰ ĐÁNH GIÁ

### Ratios
- [ ] Tính được ratio từ historical data
- [ ] Apply ratio cho project mới
- [ ] Hiểu common ratios (test vs dev, TC per requirement)
- [ ] Biết adjust cho complexity

### Extrapolation
- [ ] Tính rate từ actual progress
- [ ] Extrapolate remaining effort
- [ ] Hiểu khi nào technique này accurate
- [ ] Biết add buffer cho risks

### Wideband Delphi / Planning Poker
- [ ] Hiểu process (kickoff, estimate, discuss, re-estimate)
- [ ] Biết Fibonacci sequence trong Planning Poker
- [ ] Understand story points vs hours
- [ ] Có thể facilitate session

### Three-Point
- [ ] Define được O, M, P estimates
- [ ] Calculate expected using formula
- [ ] Calculate standard deviation
- [ ] Interpret confidence intervals

---

## TỔNG KẾT

```
╔═══════════════════════════════════════════════════════════════╗
║                    KEY TAKEAWAYS                              ║
╠═══════════════════════════════════════════════════════════════╣
║                                                               ║
║  1. ESTIMATION BASED ON RATIOS:                              ║
║     → Use historical data                                    ║
║     → Test Effort = Dev Effort × Ratio                       ║
║     → Quick, objective                                       ║
║                                                               ║
║  2. EXTRAPOLATION:                                           ║
║     → Measure actual progress                                ║
║     → Calculate rate/velocity                                ║
║     → Extrapolate to total                                   ║
║     → Accurate mid-project                                   ║
║                                                               ║
║  3. WIDEBAND DELPHI / PLANNING POKER:                        ║
║     → Team consensus estimation                              ║
║     → Multiple rounds until converge                         ║
║     → Fibonacci cards (Planning Poker)                       ║
║     → Engaging, shared understanding                         ║
║                                                               ║
║  4. THREE-POINT ESTIMATION:                                  ║
║     → O, M, P scenarios                                      ║
║     → E = (O + 4M + P) / 6                                   ║
║     → SD = (P - O) / 6                                       ║
║     → Accounts for uncertainty                               ║
║                                                               ║
║  💡 COMBINE techniques for best results!                     ║
║                                                               ║
╚═══════════════════════════════════════════════════════════════╝
```

---

**Tiếp theo**: [Module 6.3: Test Case Prioritization](./module-6.3-test-case-prioritization.md)

---

**Version**: 1.0.0
**Last Updated**: November 2025
