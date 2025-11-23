# Module 7.4: Defect Management (Quản Lý Lỗi)

## Mục Tiêu Học Tập

Sau khi hoàn thành module này, bạn sẽ:
- Hiểu được defect lifecycle và các states
- Viết được defect reports hiệu quả và chi tiết
- Phân biệt được Severity vs Priority
- Tham gia defect triage meetings
- Sử dụng được defect metrics để improve quality
- Hiểu về root cause analysis
- Áp dụng defect prevention strategies

---

## 1. Defect Là Gì?

### 1.1. Định Nghĩa

**Defect** (còn gọi là Bug, Issue, Problem) là:
- Sai lệch giữa actual result và expected result
- Failure của software không hoạt động đúng như mong đợi
- Violation của requirements hoặc specifications

### 1.2. Phân Loại Defects

```
┌─────────────────────────────────────────┐
│        TYPES OF DEFECTS                 │
├─────────────────────────────────────────┤
│                                         │
│  1. FUNCTIONAL DEFECTS                 │
│     • Feature không hoạt động           │
│     • Sai logic nghiệp vụ              │
│     • Missing functionality            │
│                                         │
│  2. PERFORMANCE DEFECTS                │
│     • Slow response time               │
│     • Memory leaks                     │
│     • High CPU usage                   │
│                                         │
│  3. SECURITY DEFECTS                   │
│     • SQL injection                    │
│     • XSS vulnerabilities              │
│     • Authentication bypass            │
│                                         │
│  4. USABILITY DEFECTS                  │
│     • Confusing UI                     │
│     • Poor error messages              │
│     • Inconsistent design              │
│                                         │
│  5. COMPATIBILITY DEFECTS              │
│     • Browser issues                   │
│     • Device-specific problems         │
│     • OS compatibility                 │
│                                         │
│  6. DATA DEFECTS                       │
│     • Data corruption                  │
│     • Incorrect calculations           │
│     • Data loss                        │
│                                         │
└─────────────────────────────────────────┘
```

---

## 2. Defect Lifecycle

### 2.1. Defect States

```
┌─────────────────────────────────────────────────────────┐
│              DEFECT LIFECYCLE                           │
├─────────────────────────────────────────────────────────┤
│                                                         │
│   [NEW]                                                │
│     ↓                                                   │
│     ↓ Triage                                           │
│     ↓                                                   │
│   [ASSIGNED]                                           │
│     ↓                                                   │
│     ↓ Developer investigates                           │
│     ↓                                                   │
│   [IN PROGRESS] ←──────┐                               │
│     ↓                  │                               │
│     ↓ Fix completed    │ Need more work                │
│     ↓                  │                               │
│   [RESOLVED] ──────────┘                               │
│     ↓                                                   │
│     ↓ Tester verifies                                  │
│     ↓                                                   │
│   [VERIFIED] ────────┐                                 │
│     │                │                                 │
│     │                │ Verification fails              │
│     ↓                ↓                                 │
│   [CLOSED]      [REOPENED]                            │
│                      │                                 │
│                      └─→ Back to [ASSIGNED]            │
│                                                         │
│   SPECIAL STATES:                                      │
│   • [REJECTED]: Not a real defect                     │
│   • [DUPLICATE]: Already reported                     │
│   • [DEFERRED]: Fix in future release                 │
│   • [CANNOT REPRODUCE]: Cannot recreate issue         │
│                                                         │
└─────────────────────────────────────────────────────────┘
```

### 2.2. Defect State Descriptions

| State | Description | Owner | Next Actions |
|-------|-------------|-------|--------------|
| **New** | Mới tạo, chưa review | Tester | Triage team reviews |
| **Assigned** | Assigned to developer | Developer | Investigate and fix |
| **In Progress** | Developer đang fix | Developer | Complete fix |
| **Resolved** | Fix completed, ready to test | Tester | Verify fix |
| **Verified** | Fix confirmed working | Tester | Close after smoke test |
| **Closed** | Complete, no further action | - | Archive |
| **Reopened** | Fix didn't work, issue persists | Developer | Fix again |
| **Rejected** | Not a defect (expected behavior) | Tester | Clarify requirements |
| **Duplicate** | Same as existing defect | Tester | Link to original |
| **Deferred** | Will fix in future release | PM | Add to backlog |
| **Cannot Reproduce** | Unable to recreate issue | Tester | Provide more info |

---

## 3. Writing Effective Defect Reports

### 3.1. Defect Report Template

```
═══════════════════════════════════════════════════════════
DEFECT REPORT: DEF-1234
═══════════════════════════════════════════════════════════

📋 BASIC INFORMATION
────────────────────────────────────────────────────────
Defect ID:        DEF-1234
Title:            Payment fails for orders > 1M VND with GrabPay
Reported by:      Nguyen Van A (QA Engineer)
Date reported:    Nov 24, 2024, 10:30 AM
Environment:      QA (qa.momo.vn)
Build:            v2.5.0-RC3, Build #456
Severity:         Critical
Priority:         High
Component:        Payment Module
Assigned to:      Tran Van B (Backend Developer)
Status:           New

📝 DESCRIPTION
────────────────────────────────────────────────────────
When user attempts to pay for an order exceeding 1,000,000
VND using GrabPay payment method, the payment fails with
a timeout error. The order remains in "Pending Payment"
status and user cannot complete purchase.

Impact:
• 15% of premium orders affected (orders > 1M)
• User unable to complete purchase
• Affects revenue

🔁 STEPS TO REPRODUCE
────────────────────────────────────────────────────────
1. Login as test user: buyer001@test.com
2. Add items to cart (total > 1,000,000 VND)
   • Example: 2x Product ABC (650,000 VND each)
3. Go to checkout
4. Select payment method: GrabPay
5. Click "Confirm Payment"
6. Observe the result

✅ EXPECTED RESULT
────────────────────────────────────────────────────────
• Payment processed successfully
• User redirected to GrabPay authorization page
• After authorization, order status = "Paid"
• User receives confirmation email
• Transaction visible in transaction history

❌ ACTUAL RESULT
────────────────────────────────────────────────────────
• Spinner shows "Processing..." for ~60 seconds
• Error popup: "Payment timeout. Please try again."
• Order status remains "Pending Payment"
• No confirmation email
• Transaction not visible in history

📊 TEST DATA
────────────────────────────────────────────────────────
User account: buyer001@test.com / Test@123
Cart items:
  • Product: Smartphone XYZ (SKU: PHONE-001)
  • Quantity: 2
  • Unit price: 650,000 VND
  • Total: 1,300,000 VND

GrabPay test account: grabpay.test@sandbox.com

🖼️  EVIDENCE
────────────────────────────────────────────────────────
Screenshots:
  • [Attachment 1]: Error popup screenshot
  • [Attachment 2]: Browser console errors
  • [Attachment 3]: Network tab (API timeout)

Video:
  • [Attachment 4]: Screen recording of reproduction

Logs:
  • [Attachment 5]: Backend logs (payment-service.log)
  • Error: "GrabPay API timeout after 60000ms"
  • Timestamp: 2024-11-24 10:25:34

🔧 ENVIRONMENT DETAILS
────────────────────────────────────────────────────────
Browser:         Chrome 119.0.6045.105
OS:              macOS Sonoma 14.1
Screen size:     1920x1080
Network:         WiFi, stable connection
API version:     Payment API v2.3
Database:        PostgreSQL 14.5

🔍 ADDITIONAL INFORMATION
────────────────────────────────────────────────────────
Frequency:       100% reproducible
First observed:  Nov 24, 2024 (first test of high-value GrabPay)

Related defects: None

Workaround:      Use different payment method (e.g., Bank Transfer)
                 OR split order into smaller amounts (< 1M each)

Investigation notes:
• Tested with different amounts:
  - 500K VND: ✅ Works
  - 900K VND: ✅ Works
  - 1.0M VND: ❌ Fails
  - 1.5M VND: ❌ Fails
• Threshold appears to be exactly 1,000,000 VND

Possible root cause:
• Configuration issue with GrabPay API limit?
• Timeout setting too low for high-value transactions?

═══════════════════════════════════════════════════════════
```

### 3.2. Best Practices viết Defect Report

```
┌─────────────────────────────────────────┐
│    DEFECT REPORT BEST PRACTICES         │
├─────────────────────────────────────────┤
│                                         │
│  ✅ DO:                                 │
│     • Be specific and factual          │
│     • Include clear steps to reproduce │
│     • Attach evidence (screenshots)    │
│     • Specify environment details      │
│     • Use proper severity/priority     │
│     • Isolate the issue                │
│     • Write objectively                │
│                                         │
│  ❌ DON'T:                              │
│     • Be vague ("it doesn't work")     │
│     • Skip reproduction steps          │
│     • Assume developer knows context   │
│     • Use emotional language           │
│     • Report multiple issues in one    │
│     • Suggest fixes (unless asked)     │
│                                         │
└─────────────────────────────────────────┘
```

**Good vs Bad Examples**:

❌ **Bad Defect Report**:
```
Title: Login broken

Description:
Login is not working. Please fix ASAP!
```
→ Không có thông tin gì hữu ích

✅ **Good Defect Report**:
```
Title: Login fails with "Invalid credentials" for valid users

Description:
Users cannot login using correct credentials. The system
returns "Invalid credentials" error even for known valid
username/password combinations.

Steps to Reproduce:
1. Go to https://qa.momo.vn/login
2. Enter username: test@momo.vn
3. Enter password: Test@123
4. Click "Login"

Expected: Dashboard page
Actual: "Invalid credentials" error message

Environment: Chrome 119, macOS Sonoma
Build: v2.5.0-RC3

Screenshot: [attached]
```
→ Clear, actionable, complete

---

## 4. Severity vs Priority

### 4.1. Severity (Mức Độ Nghiêm Trọng)

**Severity** = Technical impact của defect

```
┌─────────────────────────────────────────┐
│           SEVERITY LEVELS               │
├─────────────────────────────────────────┤
│                                         │
│  🔴 CRITICAL (Blocker)                 │
│     • Application crash                │
│     • Data loss                        │
│     • Security breach                  │
│     • Complete feature failure         │
│     Example: Cannot login at all       │
│                                         │
│  🟠 HIGH (Major)                       │
│     • Major feature broken             │
│     • No workaround                    │
│     • Significant functionality loss   │
│     Example: Payment fails for all     │
│                                         │
│  🟡 MEDIUM (Moderate)                  │
│     • Feature partially broken         │
│     • Workaround exists                │
│     • Moderate impact                  │
│     Example: Filter doesn't work       │
│                                         │
│  🟢 LOW (Minor)                        │
│     • Cosmetic issues                  │
│     • Minor inconvenience              │
│     • Minimal impact                   │
│     Example: Button alignment off      │
│                                         │
└─────────────────────────────────────────┘
```

### 4.2. Priority (Độ Ưu Tiên)

**Priority** = Business urgency to fix

```
┌─────────────────────────────────────────┐
│           PRIORITY LEVELS               │
├─────────────────────────────────────────┤
│                                         │
│  P0 - IMMEDIATE                        │
│     • Fix right now                    │
│     • Drop everything else             │
│     • Blocks release                   │
│                                         │
│  P1 - HIGH                             │
│     • Fix in current sprint            │
│     • High business impact             │
│     • Must fix before release          │
│                                         │
│  P2 - MEDIUM                           │
│     • Fix in next sprint               │
│     • Moderate business impact         │
│     • Can ship with this               │
│                                         │
│  P3 - LOW                              │
│     • Fix when time permits            │
│     • Low business impact              │
│     • Nice to have                     │
│                                         │
│  P4 - FUTURE                           │
│     • Backlog                          │
│     • Consider for future releases     │
│                                         │
└─────────────────────────────────────────┘
```

### 4.3. Severity vs Priority Matrix

```
                    PRIORITY
                 P0    P1    P2    P3
              ┌─────┬─────┬─────┬─────┐
         HIGH │  A  │  B  │  D  │  F  │
              ├─────┼─────┼─────┼─────┤
   S   MEDIUM │  C  │  D  │  E  │  G  │
   E          ├─────┼─────┼─────┼─────┤
   V      LOW │  E  │  F  │  G  │  H  │
              └─────┴─────┴─────┴─────┘

Legend:
A = Critical bug, immediate fix (e.g., Payment broken on Black Friday)
B = Critical bug, fix this sprint (e.g., Security vulnerability)
C = Medium bug, urgent fix (e.g., Important client affected)
D = Medium bug, normal priority
E = Low severity but high priority (e.g., CEO demo tomorrow)
F = Low severity, low priority (cosmetic)
```

**Examples**:

| Defect | Severity | Priority | Reason |
|--------|----------|----------|--------|
| Production database crash | Critical | P0 | All users affected, data loss risk |
| Payment fails for VIP customers | High | P1 | Revenue impact, but limited to VIPs |
| Typo in CEO's name on homepage | Low | P0 | Cosmetic but politically sensitive |
| Button color wrong | Low | P3 | No business impact |
| Search returns wrong results | High | P2 | Important but workaround exists |

---

## 5. Defect Triage Process

### 5.1. Defect Triage Meeting

**Mục đích**: Review new defects, assign, prioritize

**Participants**:
- Test Lead
- Development Lead
- Product Manager
- (Optional) Architecture Lead

**Frequency**: Daily hoặc 2-3 times/week

**Agenda**:
```
┌─────────────────────────────────────────┐
│      DEFECT TRIAGE MEETING              │
│      Duration: 30-45 mins               │
├─────────────────────────────────────────┤
│                                         │
│  1. REVIEW NEW DEFECTS (20 mins)       │
│     • Go through "New" defects         │
│     • Verify it's a real defect        │
│     • Assign severity & priority       │
│     • Assign to developer              │
│                                         │
│  2. REVIEW CRITICAL DEFECTS (10 mins)  │
│     • Status update on P0/P1           │
│     • Blockers?                        │
│     • Need help?                       │
│                                         │
│  3. REVIEW DEFERRED DEFECTS (5 mins)   │
│     • Any deferred bugs to reconsider? │
│     • Should any be promoted?          │
│                                         │
│  4. METRICS REVIEW (5 mins)            │
│     • Open defect count trend          │
│     • Aging defects (> 30 days)        │
│                                         │
└─────────────────────────────────────────┘
```

### 5.2. Triage Decision Tree

```
                    New Defect
                        │
                        ↓
            ┌───────────────────────┐
            │  Is it a real defect? │
            └───────────────────────┘
                 ↙         ↘
              Yes          No
               │            │
               │            ↓
               │       [REJECTED]
               │       (with reason)
               │
               ↓
    ┌──────────────────────┐
    │ Is it a duplicate?   │
    └──────────────────────┘
           ↙        ↘
        Yes         No
         │           │
         ↓           │
    [DUPLICATE]     │
    (link to orig)  │
                    ↓
         ┌─────────────────────┐
         │ Assess Severity     │
         │ Assess Priority     │
         └─────────────────────┘
                    │
                    ↓
         ┌─────────────────────┐
         │  Can fix now?       │
         └─────────────────────┘
              ↙         ↘
           Yes          No
            │            │
            ↓            ↓
       [ASSIGNED]    [DEFERRED]
       to developer  to backlog
```

### 5.3. Ví Dụ Triage Session - Shopee

**Setting**: Daily triage meeting, Sprint 15

**Defects to review**:

```
═══════════════════════════════════════════════════════════
SHOPEE - DEFECT TRIAGE SESSION
Date: Nov 24, 2024 | Sprint 15, Day 8
═══════════════════════════════════════════════════════════

🐛 DEF-1890: Search returns no results for "áo khoác"
────────────────────────────────────────────────────────
Reporter:     Nguyen Van A (QA)
Description:  Search with Vietnamese accents fails
Steps:        Enter "áo khoác" → 0 results (should show 1,234)

💬 TRIAGE DISCUSSION:
Test Lead:    "Search is critical, but how common is this?"
PM:           "Vietnamese input is 80% of searches. High priority."
Dev Lead:     "Encoding issue, probably 2h fix."

✅ DECISION:
  Severity:    HIGH (major feature broken)
  Priority:    P1 (fix this sprint)
  Assigned to: Developer Tran Van B
  Target:      Nov 25 (tomorrow)

───────────────────────────────────────────────────────

🐛 DEF-1891: Product image slightly blurry on iPhone SE
────────────────────────────────────────────────────────
Reporter:     Tester Tran Thi C
Description:  Image quality lower on small iPhone screens
Steps:        View product on iPhone SE → image quality poor

💬 TRIAGE DISCUSSION:
PM:           "What % users have iPhone SE?"
Test Lead:    "Less than 2% per analytics."
Dev Lead:     "Would need custom image optimization, 1 week effort."

✅ DECISION:
  Severity:    LOW (cosmetic, limited devices)
  Priority:    P3 (low business impact)
  Assigned to: DEFERRED to backlog
  Reason:      Low ROI, only 2% users affected

───────────────────────────────────────────────────────

🐛 DEF-1892: Cannot add more than 99 items to cart
────────────────────────────────────────────────────────
Reporter:     Tester Le Van D
Description:  Adding 100th item shows error
Steps:        Add 99 items → try to add one more → error

💬 TRIAGE DISCUSSION:
Test Lead:    "Is this a bug or business rule?"
PM:           "Business rule. Cart limit is 99 items by design."
Dev Lead:     "Working as intended."

✅ DECISION:
  Status:      REJECTED (not a defect)
  Action:      Update test case expectations
  Note:        Document cart limit in requirements

───────────────────────────────────────────────────────

🐛 DEF-1893: Payment fails for orders > 50M VND
────────────────────────────────────────────────────────
Reporter:     Tester Pham Van E
Description:  High-value payments timeout
Steps:        Cart total > 50M → select payment → timeout

💬 TRIAGE DISCUSSION:
Test Lead:    "Critical for high-value sellers."
PM:           "Flash sale next week, many high-value items. Must fix."
Dev Lead:     "API timeout config, 30 min fix."

✅ DECISION:
  Severity:    CRITICAL (payment broken)
  Priority:    P0 (fix today)
  Assigned to: Developer Nguyen Van F + Senior Dev code review
  Target:      Today 5PM
  Test:        Retest tomorrow morning

───────────────────────────────────────────────────────

🐛 DEF-1894: Same as DEF-1756 (checkout button disabled)
────────────────────────────────────────────────────────
Reporter:     Tester Hoang Thi G
Description:  Cannot click checkout button...

💬 TRIAGE DISCUSSION:
Dev Lead:     "This is duplicate of DEF-1756 fixed yesterday."
Test Lead:    "Ah yes, same issue. Not retested yet."

✅ DECISION:
  Status:      DUPLICATE
  Link to:     DEF-1756
  Action:      Tester will verify DEF-1756 fix

═══════════════════════════════════════════════════════════
SUMMARY:
────────────────────────────────────────────────────────
Reviewed: 5 defects
  • Assigned: 2 (DEF-1890, DEF-1893)
  • Deferred: 1 (DEF-1891)
  • Rejected: 1 (DEF-1892)
  • Duplicate: 1 (DEF-1894)

Action Items:
  • Dev F: Fix DEF-1893 by 5PM today ⚡
  • Dev B: Fix DEF-1890 by tomorrow
  • Tester G: Retest DEF-1756
  • Test Lead: Update test case for cart limit

Next Triage: Nov 25, 10:00 AM
═══════════════════════════════════════════════════════════
```

---

## 6. Defect Metrics

### 6.1. Common Defect Metrics

```
┌─────────────────────────────────────────┐
│         DEFECT METRICS                  │
├─────────────────────────────────────────┤
│                                         │
│  1. DEFECT DETECTION                   │
│     • Defects found per day/sprint     │
│     • Defects by severity              │
│     • Defects by component             │
│                                         │
│  2. DEFECT RESOLUTION                  │
│     • Fix rate (defects fixed/day)     │
│     • Average fix time                 │
│     • Reopened defects rate            │
│                                         │
│  3. DEFECT STATUS                      │
│     • Open defects count               │
│     • Age of open defects              │
│     • Defects by status                │
│                                         │
│  4. DEFECT QUALITY                     │
│     • Defect Removal Efficiency (DRE)  │
│     • Defect density                   │
│     • Escaped defects (to production)  │
│                                         │
└─────────────────────────────────────────┘
```

### 6.2. Key Metrics Formulas

**1. Defect Removal Efficiency (DRE)**

```
DRE = (Defects found in testing / Total defects) × 100%

Total defects = Testing defects + Production defects

Example:
• Found in testing: 150 defects
• Found in production: 10 defects
• Total: 160 defects

DRE = (150 / 160) × 100% = 93.75%

Interpretation:
• DRE > 95%: Excellent
• DRE 90-95%: Good
• DRE 80-90%: Acceptable
• DRE < 80%: Poor (many defects escape)
```

**2. Defect Density**

```
Defect Density = Total defects / Size

Size = KLOC (thousands of lines of code)
    or Function Points
    or User Stories

Example (using KLOC):
• Total defects: 120
• Code size: 15 KLOC

Defect Density = 120 / 15 = 8 defects/KLOC

Benchmarks:
• < 5 defects/KLOC: Good
• 5-10: Average
• > 10: High (quality concern)
```

**3. Defect Aging**

```
Defect Age = Current date - Reported date

Aging Categories:
• Fresh: < 7 days
• Recent: 7-14 days
• Aging: 15-30 days
• Stale: > 30 days

Example Report:
┌────────────┬───────┬────────┐
│ Age        │ Count │    %   │
├────────────┼───────┼────────┤
│ < 7 days   │   45  │  60%   │
│ 7-14 days  │   20  │  27%   │
│ 15-30 days │    8  │  11%   │
│ > 30 days  │    2  │   2% ⚠️│
└────────────┴───────┴────────┘

Action: Investigate stale defects
```

**4. Mean Time To Repair (MTTR)**

```
MTTR = Total time to fix all defects / Number of defects

Example:
• 20 defects fixed
• Total time: 160 hours

MTTR = 160 / 20 = 8 hours per defect

Track MTTR by severity:
• Critical: 4 hours (fast)
• High: 16 hours
• Medium: 40 hours
• Low: 80 hours
```

**5. Defect Leakage**

```
Defect Leakage = (Defects in Phase N+1 / Total defects) × 100%

Example: Defects leaked from QA to Production
• Found in QA: 100
• Found in Production: 8
• Total: 108

Leakage = (8 / 108) × 100% = 7.4%

Target: < 5% leakage
```

### 6.3. Defect Trend Analysis

**Example: Momo eKYC Sprint Analysis**

```
Defect Trend - Sprint 15

New Defects Opened (daily)
Count
  20│
    │     ╱╲
  15│    ╱  ╲
    │   ╱    ╲___
  10│  ╱         ╲___
    │ ╱              ╲___
   5│╱                   ╲___
    │                        ╲___
   0└────────────────────────────╲─
    Mon Tue Wed Thu Fri Mon Tue Wed Thu Fri
    Week 1              Week 2

Analysis:
📈 Peak: Week 1 Wed-Thu (core feature testing)
📉 Declining: Week 2 (fewer new features, regression)
✅ Good sign: Finding defects early


Defect Status Trend
Count
 100│
    │           Open ──┐
  80│          ___/    │
    │      ___/        │  ___
  60│  ___/            │_/   Fixed ─┐
    │                             │
  40│                              ╲___
    │                                  ╲___
  20│                                      ╲___
    │
   0└────────────────────────────────────────╲─
    Day 1  3   5   7   9  11  13  15

Analysis:
✅ Opened peaks early (Day 5)
✅ Fixed crosses Opened (Day 10)
✅ Downward trend at sprint end
🎯 Sprint exit: Only 12 open defects (all P3)


Defect by Severity (Sprint 15)
Count
  60│              ████████████  Medium (68)
    │              ████████████
  50│              ████████████
    │              ████████████
  40│              ████████████
    │              ████████████
  30│              ████████████
    │  ███         ████████████
  20│  ███         ████████████
    │  ███  ████   ████████████
  10│  ███  ████   ████████████   ██
    │  ███  ████   ████████████   ██
   0└─────────────────────────────────
     Crit  High   Medium         Low
      (8)  (24)    (68)          (15)

Total: 115 defects
Distribution: 7% Critical, 21% High, 59% Medium, 13% Low
```

---

## 7. Root Cause Analysis (RCA)

### 7.1. RCA Process

```
┌─────────────────────────────────────────┐
│       ROOT CAUSE ANALYSIS PROCESS       │
├─────────────────────────────────────────┤
│                                         │
│  1. DEFINE THE PROBLEM                 │
│     • What happened?                   │
│     • When did it happen?              │
│     • What is the impact?              │
│                                         │
│  2. COLLECT DATA                       │
│     • Timeline of events               │
│     • Logs and evidence                │
│     • Related defects                  │
│                                         │
│  3. IDENTIFY POSSIBLE CAUSES           │
│     • Brainstorm all possibilities     │
│     • Use "5 Whys" technique           │
│     • Use Fishbone diagram             │
│                                         │
│  4. IDENTIFY ROOT CAUSE                │
│     • Verify with data                 │
│     • Test hypothesis                  │
│     • Confirm root cause               │
│                                         │
│  5. RECOMMEND SOLUTIONS                │
│     • Short-term fix                   │
│     • Long-term prevention             │
│     • Process improvements             │
│                                         │
│  6. IMPLEMENT & VERIFY                 │
│     • Execute fixes                    │
│     • Verify effectiveness             │
│     • Monitor for recurrence           │
│                                         │
└─────────────────────────────────────────┘
```

### 7.2. 5 Whys Technique

**Example: Grab Food - Order Duplication Bug**

```
═══════════════════════════════════════════════════════════
5 WHYS ANALYSIS: Order Duplication Bug
═══════════════════════════════════════════════════════════

Problem: Users sometimes receive duplicate orders

WHY #1: Why did duplicate orders occur?
→ Because the "Place Order" button was clicked multiple times

WHY #2: Why was the button clicked multiple times?
→ Because users thought the first click didn't work (no feedback)

WHY #3: Why was there no feedback after first click?
→ Because the API call takes 3-5 seconds but UI didn't show loading

WHY #4: Why didn't the UI show loading state?
→ Because developer forgot to implement loading indicator

WHY #5: Why was loading indicator forgotten?
→ Because UI/UX requirements didn't explicitly specify loading states

ROOT CAUSE:
• Incomplete requirements (no loading state specified)
• No code review caught the missing feedback
• No test case for slow network conditions

───────────────────────────────────────────────────────

SOLUTIONS:

IMMEDIATE FIX:
✅ Add loading spinner after button click
✅ Disable button after first click
✅ Add idempotency key to API calls

PREVENTIVE ACTIONS:
✅ Update UI/UX guidelines: Always specify loading states
✅ Create checklist for code reviews: Check user feedback
✅ Add test cases: Simulate slow network in test plan
✅ Implement E2E monitoring: Detect duplicate orders

PROCESS IMPROVEMENTS:
✅ Three Amigos sessions: Dev + QA + Designer review specs
✅ Definition of Done: Includes all UI states (loading, error, success)

═══════════════════════════════════════════════════════════
```

### 7.3. Fishbone (Ishikawa) Diagram

**Example: VNPay - Payment Timeout Issues**

```
                         Payment Timeout Issues
                                  ⬤
                                 ╱│╲
                    ╭───────────╯ │ ╰───────────╮
                   ╱              │              ╲
              PEOPLE           METHOD          ENVIRONMENT
                │                │                 │
                │                │                 │
    • Lack of perf    • No retry logic    • Database overloaded
      testing         • Timeout too low    • Network latency
    • No monitoring   • Synchronous calls  • 3rd party API slow
                      • No caching         • Server undersized
                │                │                 │
                ╰────────╮       │       ╭────────╯
                         ╲       │      ╱
                          ╲      │     ╱
                           ╲     │    ╱
                            ╲    │   ╱
                             ╲   │  ╱
              TOOLS           ╲  │ ╱          PROCESS
                │              ╲│╱              │
                │               ⬤               │
    • No load testing    (ROOT CAUSES)  • No capacity planning
    • No APM tool                       • Requirements unclear
    • No alerting                       • No SLA defined

ANALYSIS:
Primary root causes identified:
1. METHOD: Synchronous API calls (blocking)
2. ENVIRONMENT: Database not optimized for scale
3. PROCESS: No performance requirements in acceptance criteria

Actions:
→ Refactor to async processing
→ Add database indexing and query optimization
→ Define performance requirements in Definition of Ready
```

---

## 8. Defect Prevention

### 8.1. Defect Prevention Strategies

```
┌─────────────────────────────────────────┐
│      DEFECT PREVENTION STRATEGIES       │
├─────────────────────────────────────────┤
│                                         │
│  1. EARLY TESTING                      │
│     • Shift-left testing               │
│     • Requirements review              │
│     • Design review                    │
│                                         │
│  2. CODE QUALITY                       │
│     • Code reviews                     │
│     • Static analysis                  │
│     • Pair programming                 │
│     • TDD (Test-Driven Development)    │
│                                         │
│  3. AUTOMATION                         │
│     • Automated regression tests       │
│     • CI/CD pipelines                  │
│     • Automated code quality checks    │
│                                         │
│  4. TRAINING                           │
│     • Secure coding training           │
│     • Testing best practices           │
│     • Technology training              │
│                                         │
│  5. PROCESS IMPROVEMENT                │
│     • Retrospectives                   │
│     • Root cause analysis              │
│     • Lessons learned                  │
│     • Continuous improvement           │
│                                         │
└─────────────────────────────────────────┘
```

### 8.2. Defect Prevention Checklist

**Requirements Phase**:
- [ ] Requirements are clear and testable
- [ ] Acceptance criteria defined
- [ ] Non-functional requirements specified
- [ ] Requirements reviewed by team
- [ ] Edge cases considered
- [ ] Dependencies identified

**Design Phase**:
- [ ] Design reviewed by peers
- [ ] Security considerations addressed
- [ ] Performance requirements accounted for
- [ ] Error handling designed
- [ ] Logging and monitoring planned
- [ ] Test strategy aligned with design

**Development Phase**:
- [ ] Code follows standards
- [ ] Unit tests written (TDD)
- [ ] Code peer reviewed
- [ ] Static analysis passed
- [ ] No hard-coded values
- [ ] Error handling implemented
- [ ] Logging added

**Testing Phase**:
- [ ] Test cases cover requirements
- [ ] Edge cases tested
- [ ] Integration tested
- [ ] Performance tested
- [ ] Security tested
- [ ] Usability tested

**Deployment Phase**:
- [ ] Deployment plan reviewed
- [ ] Rollback plan ready
- [ ] Monitoring configured
- [ ] Alerts set up
- [ ] Documentation updated
- [ ] Team trained

---

## 9. Ví Dụ Thực Tế: Shopee Search Bug

### Full Defect Lifecycle Example

```
═══════════════════════════════════════════════════════════
DEFECT LIFECYCLE: DEF-2456
Shopee Search Vietnamese Keywords Bug
═══════════════════════════════════════════════════════════

📅 DAY 1 - NOV 20, 2024
────────────────────────────────────────────────────────
10:00 AM - [NEW]
Reported by: Tester Nguyen Van A

Issue: Search with Vietnamese accents returns 0 results
Example: "áo khoác" → 0 results (should return 1,234 products)

Environment: QA, Chrome 119
Build: v3.2.0-RC5

Evidence: Screenshot attached

───────────────────────────────────────────────────────

11:00 AM - Triage Meeting
Attendees: Test Lead, Dev Lead, PM

Discussion:
• PM: "Vietnamese is 80% of searches. Critical!"
• Dev Lead: "Looks like encoding issue in new search service."
• Test Lead: "Need to test all Vietnamese characters."

Decision:
• Severity: HIGH
• Priority: P0 (blocks release)
• Assigned to: Developer Tran Van B
• ETA: Today

───────────────────────────────────────────────────────

11:05 AM - [ASSIGNED]
Status → ASSIGNED to Tran Van B

───────────────────────────────────────────────────────

02:00 PM - [IN PROGRESS]
Developer comment:
"Started investigation. Found issue in search-service:
UTF-8 encoding not properly configured in Elasticsearch.
Working on fix."

───────────────────────────────────────────────────────

04:30 PM - [RESOLVED]
Developer comment:
"Fixed. Problem was Elasticsearch index mapping.
Changed analyzer from 'standard' to 'vi_analyzer'.
Reindexed all products.

Fix deployed to QA: Build #v3.2.0-RC6
Ready for retest."

Code changes:
• File: search-service/config/elasticsearch.yml
• Commit: a7f3c21
• PR: #1234 (approved by senior dev)

───────────────────────────────────────────────────────

📅 DAY 2 - NOV 21, 2024
────────────────────────────────────────────────────────

09:00 AM - Retest by QA
Tester Nguyen Van A:

Test Results:
✅ TC-001: Search "áo khoác" → 1,234 results (PASS)
✅ TC-002: Search "điện thoại" → 3,456 results (PASS)
✅ TC-003: Search "túi xách" → 892 results (PASS)
❌ TC-004: Search "mũ bảo hiểm" → 0 results (FAIL)

Comment:
"Most Vietnamese keywords work now, but 'mũ bảo hiểm'
(3 words) still fails. Space handling issue?"

Status → [REOPENED]

───────────────────────────────────────────────────────

10:30 AM - [REOPENED] → [ASSIGNED]
Developer Tran Van B:
"Ah, multi-word tokenization issue. Investigating."

───────────────────────────────────────────────────────

02:00 PM - [IN PROGRESS]
Developer comment:
"Found it. Vietnamese analyzer needs whitespace tokenizer.
Updated config. Testing locally."

───────────────────────────────────────────────────────

04:00 PM - [RESOLVED]
Developer comment:
"Fixed. Updated Elasticsearch tokenizer configuration.
Tested all Vietnamese multi-word queries locally.

Deployed to QA: Build #v3.2.0-RC7
Ready for full retest."

Additional changes:
• File: search-service/config/elasticsearch.yml
• Added: whitespace tokenizer + vi_stopwords
• Commit: b8e4f32
• Reindexed: All 1.2M products

───────────────────────────────────────────────────────

📅 DAY 3 - NOV 22, 2024
────────────────────────────────────────────────────────

09:30 AM - Full Regression Test
Tester Nguyen Van A:

Tested 25 Vietnamese search scenarios:
✅ Single words: All PASS (15 tests)
✅ Multi-words: All PASS (8 tests)
✅ Special characters: All PASS (2 tests)

Also tested:
✅ English keywords: Still work (10 tests)
✅ Performance: < 500ms avg (acceptable)

Status → [VERIFIED]

Comment:
"All test cases pass. Vietnamese search working correctly.
No regression in English search. Ready to close."

───────────────────────────────────────────────────────

11:00 AM - [CLOSED]
Closed by: Test Lead

Final Summary:
• Found: Nov 20, 10:00 AM
• Fixed: Nov 21, 4:00 PM (1.5 days)
• Verified: Nov 22, 9:30 AM
• Total time: 2 days

Impact:
• Severity: HIGH
• Priority: P0
• Component: Search Service
• Root cause: Elasticsearch configuration
• Lines changed: 15 lines
• Tests: 25 Vietnamese search test cases added to regression

Prevention:
• Added: Vietnamese keyword tests to CI pipeline
• Added: Elasticsearch config validation
• Updated: Search service deployment checklist

───────────────────────────────────────────────────────

📊 POST-MORTEM (Nov 23)
────────────────────────────────────────────────────────

Root Cause Analysis (5 Whys):

Why did search fail for Vietnamese?
→ Elasticsearch not configured for Vietnamese

Why wasn't Elasticsearch configured correctly?
→ Default configuration used, not localized

Why was default configuration used?
→ Developer didn't know Vietnamese requires special config

Why didn't developer know?
→ No documentation on localization requirements

Why was there no documentation?
→ Process gap: Localization requirements not in checklist

ROOT CAUSE: Missing localization requirements in development checklist

───────────────────────────────────────────────────────

CORRECTIVE ACTIONS:

IMMEDIATE:
✅ Fixed search configuration
✅ Added Vietnamese test coverage

PREVENTIVE:
✅ Created: Localization Development Checklist
✅ Added: i18n/l10n requirements to Definition of Ready
✅ Scheduled: Team training on internationalization

PROCESS:
✅ Updated: Code review checklist (check localization)
✅ Added: Pre-deployment verification for all languages

═══════════════════════════════════════════════════════════
```

---

## 10. Thực Hành

### Câu Hỏi 1: Severity vs Priority

**Tình huống**: Classify các defects sau theo Severity và Priority:

a) Logo công ty bị lỗi trên homepage, CEO phát hiện trước demo với investors ngày mai
b) Database crash mỗi 100 transactions, affecting 1% users
c) Button màu sai (blue thay vì green) trên trang settings
d) Payment gateway fails for all transactions on Black Friday (hôm nay)
e) Report export to Excel bị lỗi format, 1 khách hàng VIP complain

<details>
<summary>Đáp án</summary>

a) **Logo lỗi trước demo CEO**
- Severity: LOW (cosmetic issue)
- Priority: P0 (CEO demo critical)
- Reason: Technical impact thấp nhưng business/political urgency cao

b) **Database crash 1% users**
- Severity: CRITICAL (data integrity, crashes)
- Priority: P0/P1 (immediate fix)
- Reason: Affects reliability, data loss risk, escalates if unaddressed

c) **Button màu sai**
- Severity: LOW (cosmetic)
- Priority: P3 (fix when time permits)
- Reason: No functional impact, no business urgency

d) **Payment fails Black Friday**
- Severity: CRITICAL (complete payment failure)
- Priority: P0 (URGENT - revenue impact)
- Reason: Maximum severity + maximum urgency = drop everything

e) **Report export lỗi (VIP khách hàng)**
- Severity: MEDIUM (feature broken but workaround exists - manual report)
- Priority: P1 (fix this sprint)
- Reason: VIP customer + business feature = high priority despite medium severity

**Matrix**:
```
              Priority
           P0    P1    P2    P3
        ┌─────┬─────┬─────┬─────┐
   CRIT │ b,d │     │     │     │
        ├─────┼─────┼─────┼─────┤
    MED │     │  e  │     │     │
        ├─────┼─────┼─────┼─────┤
    LOW │  a  │     │     │  c  │
        └─────┴─────┴─────┴─────┘
```

Key Lesson: Severity = technical, Priority = business urgency
</details>

### Câu Hỏi 2: Writing Defect Report

**Tình huống**: Bạn test Momo app và phát hiện:
- Login với email hợp lệ nhưng sai password 5 lần
- App không lock account (theo requirement nên lock sau 5 lần fail)
- Bạn có thể tiếp tục try unlimited times

**Câu hỏi**: Viết defect report đầy đủ cho issue này.

<details>
<summary>Đáp án</summary>

```
═══════════════════════════════════════════════════════════
DEFECT REPORT: DEF-5678
═══════════════════════════════════════════════════════════

📋 BASIC INFORMATION
────────────────────────────────────────────────────────
Title:           Account not locked after 5 failed login attempts
Reported by:     [Your Name] (QA Engineer)
Date:            Nov 24, 2024, 2:30 PM
Environment:     QA (qa-api.momo.vn)
Build:           iOS v3.5.2 (Build 892)
Device:          iPhone 14 Pro, iOS 17.1
Severity:        HIGH
Priority:        P1
Component:       Authentication / Security
Status:          New

📝 DESCRIPTION
────────────────────────────────────────────────────────
Account is not locked after 5 failed login attempts, allowing
unlimited password guessing. This violates the security
requirement REQ-SEC-101 that states: "Account must be locked
for 30 minutes after 5 consecutive failed login attempts."

Security Impact:
• Vulnerable to brute force attacks
• No rate limiting on login attempts
• Account takeover risk

Business Impact:
• Security compliance issue
• Potential unauthorized access
• User account security at risk

🔁 STEPS TO REPRODUCE
────────────────────────────────────────────────────────
Pre-condition: Have a valid test account

1. Open Momo app
2. Tap "Đăng nhập" (Login)
3. Enter email: test.user@momo.vn
4. Enter wrong password: "WrongPass123"
5. Tap "Đăng nhập"
6. Observe error: "Sai mật khẩu"
7. Repeat steps 4-6 four more times (total 5 failed attempts)
8. Try to login again (6th attempt) with wrong password
9. Observe the result

✅ EXPECTED RESULT (per REQ-SEC-101)
────────────────────────────────────────────────────────
After 5 failed attempts:
• Login button should be disabled
• Error message: "Tài khoản đã bị khóa do nhập sai mật khẩu
  quá nhiều. Vui lòng thử lại sau 30 phút."
• Account locked for 30 minutes
• Cannot attempt login even with correct password
• After 30 min, account auto-unlocks

❌ ACTUAL RESULT
────────────────────────────────────────────────────────
After 5+ failed attempts:
• Login button remains enabled
• Can continue trying indefinitely
• Error message still shows: "Sai mật khẩu"
• No lockout mechanism triggered
• Account never locked

Tested:
• 10 failed attempts: No lock
• 20 failed attempts: No lock
• 50 failed attempts: Still no lock

📊 TEST DATA
────────────────────────────────────────────────────────
Test Account:
• Email: test.user@momo.vn
• Correct Password: Test@123456
• Wrong Password used: WrongPass123

Test Sequence:
Attempt | Password      | Result
───────────────────────────────────────
1       | WrongPass123  | Fail (expected)
2       | WrongPass123  | Fail (expected)
3       | WrongPass123  | Fail (expected)
4       | WrongPass123  | Fail (expected)
5       | WrongPass123  | Fail (expected)
6       | WrongPass123  | Should lock, but Fail ❌
7-50    | WrongPass123  | Should be locked, but Fail ❌
51      | Test@123456   | Success ❌ (should be locked!)

🖼️  EVIDENCE
────────────────────────────────────────────────────────
Screenshots:
• [Attachment 1]: Login screen after 5 failed attempts
                  (button still enabled)
• [Attachment 2]: Error message (no lock warning)
• [Attachment 3]: 50th failed attempt (still not locked)

Video:
• [Attachment 4]: Screen recording (5 failed + 1 success)

Logs:
• [Attachment 5]: App logs (login attempts captured)
• No lockout API calls observed in logs

🔧 ENVIRONMENT DETAILS
────────────────────────────────────────────────────────
Device:          iPhone 14 Pro
OS:              iOS 17.1
App Version:     3.5.2 (Build 892)
Environment:     QA (qa-api.momo.vn)
Network:         WiFi, stable
Backend API:     Auth Service v2.1

🔍 ADDITIONAL INFORMATION
────────────────────────────────────────────────────────
Reproducibility: 100% (tested on 3 different accounts)

Related Requirements:
• REQ-SEC-101: Account lockout after 5 failed attempts
• REQ-SEC-102: 30-minute lockout duration

Tested Variations:
✅ iOS app (iPhone 14): Reproduced
✅ iOS app (iPhone 11): Reproduced
✅ Android app: Reproduced
❌ Web app: NOT tested yet

Workaround: None (security issue cannot be worked around)

Possible Root Cause:
• Login API not implementing lockout logic
• Backend not tracking failed attempts count
• Missing Redis/DB entries for lockout state

Investigation Notes:
• Checked API response: No "attempt_count" field
• No rate limiting headers (X-RateLimit-*) in response
• Suggests backend issue, not just frontend

Risk Assessment:
• Security: HIGH (brute force vulnerability)
• Compliance: May violate security standards
• Urgency: HIGH (need fix before production release)

Suggested Test Cases for Verification:
1. Test lockout after exactly 5 attempts
2. Test unlock after 30 minutes
3. Test lockout persists across app restarts
4. Test lockout across different devices (same account)
5. Test correct password rejected during lockout

═══════════════════════════════════════════════════════════
```

**Good Points**:
✅ Clear, specific title
✅ Detailed reproduction steps
✅ Security impact explained
✅ Expected vs Actual clearly defined
✅ Evidence attached (screenshots, video, logs)
✅ Linked to requirements (REQ-SEC-101)
✅ Tested variations (iOS, Android)
✅ Risk assessment included
✅ Possible root cause hypothesis

This report gives developer everything needed to:
- Understand the issue
- Reproduce it
- Assess priority
- Investigate root cause
- Verify the fix
</details>

### Câu Hỏi 3: Triage Decision

**Tình huống**: Bạn là Test Lead trong triage meeting. 10 new defects, nhưng chỉ có 3 developers available và sprint kết thúc trong 2 ngày.

Defects:
1. DEF-101: Critical - Payment fails for all users (P0)
2. DEF-102: High - Search Vietnamese keywords returns wrong results (80% users affected)
3. DEF-103: Medium - Profile image upload slow (5s vs 2s target)
4. DEF-104: Low - Button text typo "Submt" instead of "Submit"
5. DEF-105: High - Cannot delete account (GDPR requirement)
6. DEF-106: Medium - Email notification delay (20 mins vs 5 mins)
7. DEF-107: Critical - Data shown to wrong user (privacy breach)
8. DEF-108: Low - Chart colors not matching design
9. DEF-109: Medium - Export to PDF cuts off content
10. DEF-110: High - App crashes on iPad Air (10% of iPad users)

**Câu hỏi**:
a) Prioritize tất cả defects
b) Chọn defects để fix trong sprint (3 devs × 2 days = 6 days)
c) Những defects nào defer?
d) Justify your decisions

<details>
<summary>Đáp án</summary>

**a) Prioritization**:

```
┌────────┬──────────┬──────────┬──────────┬──────────────┐
│ Def ID │ Severity │ Priority │ Effort   │ Decision     │
├────────┼──────────┼──────────┼──────────┼──────────────┤
│ DEF-101│ Critical │ P0       │ 1 day    │ FIX NOW ⚡   │
│ DEF-107│ Critical │ P0       │ 0.5 day  │ FIX NOW ⚡   │
│ DEF-105│ High     │ P1       │ 1 day    │ FIX NOW      │
│ DEF-102│ High     │ P1       │ 2 days   │ FIX NOW      │
│ DEF-110│ High     │ P1       │ 1.5 days │ DEFER (scope)│
│ DEF-103│ Medium   │ P2       │ 1 day    │ DEFER        │
│ DEF-106│ Medium   │ P2       │ 0.5 day  │ DEFER        │
│ DEF-109│ Medium   │ P2       │ 1 day    │ DEFER        │
│ DEF-104│ Low      │ P3       │ 0.1 day  │ DEFER        │
│ DEF-108│ Low      │ P3       │ 0.5 day  │ DEFER        │
└────────┴──────────┴──────────┴──────────┴──────────────┘
```

**b) Sprint Allocation** (6 person-days available):

**MUST FIX (Sprint commitment):**

1. **DEF-107 (0.5 day)** - Data privacy breach
   - Dev A: 4 hours
   - Reason: Critical security, legal risk
   - Cannot ship with this bug

2. **DEF-101 (1 day)** - Payment fails for all
   - Dev A: Remaining 1 day (4h left from Day 1 + Day 2)
   - Reason: Critical business impact, revenue loss
   - Blocks any release

3. **DEF-105 (1 day)** - Cannot delete account (GDPR)
   - Dev B: 1 day
   - Reason: Legal requirement (GDPR compliance)
   - High priority, regulatory risk

4. **DEF-102 (2 days)** - Vietnamese search
   - Dev C: 2 days
   - Reason: Affects 80% users (Vietnamese majority)
   - High impact, core functionality

**Total: 4.5 days out of 6 days → Good buffer**

**Sprint Capacity Check**:
```
Dev A: 0.5 (DEF-107) + 1.0 (DEF-101) = 1.5 days → OK
Dev B: 1.0 (DEF-105) = 1.0 day → OK
Dev C: 2.0 (DEF-102) = 2.0 days → OK
──────────────────────────────────────────────
Total: 4.5 days (75% of 6 days capacity)
Buffer: 1.5 days for contingency
```

**c) Defects to DEFER**:

**DEF-110** - iPad crash (High)
- Reason: High effort (1.5 days), limited scope (10% of iPad users only)
- Workaround: Users can use iPhone app or web
- Decision: Defer to next sprint, higher priority items first

**DEF-103** - Slow image upload (Medium)
- Reason: Performance issue but not blocking
- Workaround: Users can wait 5s (not ideal but acceptable)
- Decision: Defer to performance optimization sprint

**DEF-106** - Email delay (Medium)
- Reason: 20 mins still acceptable for most notifications
- Impact: Moderate, not urgent
- Decision: Defer to next sprint

**DEF-109** - PDF export issue (Medium)
- Reason: Affects export feature, not core flow
- Workaround: Export to Excel or CSV instead
- Decision: Defer

**DEF-104** - Typo "Submt" (Low)
- Reason: Cosmetic, users still understand
- Effort: Minimal but not worth sprint time
- Decision: Defer, fix in next hotfix batch

**DEF-108** - Chart colors (Low)
- Reason: Pure cosmetic, no functional impact
- Decision: Defer to UI polish sprint

**d) Justification & Communication**:

```
═══════════════════════════════════════════════════════════
TRIAGE DECISION SUMMARY - Sprint 25
Date: Nov 24, 2024
═══════════════════════════════════════════════════════════

CONTEXT:
• Sprint ends: 2 days (Nov 26)
• Available: 3 developers × 2 days = 6 person-days
• New defects: 10
• Existing work: Minimal (most features complete)

───────────────────────────────────────────────────────

DECISIONS:

✅ FIX IN SPRINT (4 defects, 4.5 days):

1. DEF-107 (Critical - Privacy breach) - 0.5 day
   → MUST FIX: Legal/security risk, cannot release

2. DEF-101 (Critical - Payment fails) - 1 day
   → MUST FIX: Complete feature broken, revenue impact

3. DEF-105 (High - GDPR deletion) - 1 day
   → MUST FIX: Regulatory requirement, compliance

4. DEF-102 (High - Vietnamese search) - 2 days
   → SHOULD FIX: Affects 80% users, core feature

───────────────────────────────────────────────────────

⏸️  DEFER TO NEXT SPRINT (6 defects):

DEF-110 (High - iPad crash):
• Reason: High effort, limited scope (10% iPad users)
• Risk: Acceptable (workaround: use iPhone/web)
• Plan: Sprint 26 high priority

DEF-103, 106, 109 (Medium):
• Reason: Not blocking release, workarounds exist
• Risk: Low (user experience impact only)
• Plan: Sprint 26 or 27

DEF-104, 108 (Low):
• Reason: Cosmetic, no functional impact
• Risk: None
• Plan: Next hotfix batch

───────────────────────────────────────────────────────

📊 RISK ANALYSIS:

IF WE FIX ONLY P0/P1:
✅ Release is safe (no critical/high-pri bugs)
✅ Sprint capacity not overloaded (75% utilized)
✅ Buffer for unexpected issues (1.5 days)
⚠️  6 bugs deferred (acceptable trade-off)

IF WE TRY TO FIX ALL 10:
❌ Sprint overload (12+ days work in 6 days)
❌ Risk of rushing → more bugs
❌ Team burnout
❌ May delay release anyway

───────────────────────────────────────────────────────

💡 RECOMMENDATION:

✅ APPROVE Sprint plan: Fix 4 critical/high defects

RATIONALE:
• Focuses on highest business/security risks
• Manageable scope (75% capacity)
• Leaves buffer for unknowns
• Deferred bugs have acceptable workarounds
• Maintains sustainable pace

CONTINGENCY:
• If any P0/P1 takes longer: Defer DEF-102 (search)
  to next sprint and extend timeline 1 day
• Daily standup to monitor progress
• If all done early: Pick up DEF-110 (iPad crash)

───────────────────────────────────────────────────────

COMMUNICATION PLAN:

TO DEVELOPMENT TEAM:
"We have 4 high-priority bugs to fix this sprint. Focus
 areas: privacy, payment, GDPR, and search. These are
 critical for release. We have 1.5 days buffer."

TO PRODUCT MANAGEMENT:
"6 defects will be deferred to manage sprint scope and
 ensure quality of critical fixes. All deferred bugs have
 acceptable workarounds and will be prioritized next sprint."

TO STAKEHOLDERS:
"Sprint testing found 10 issues. 4 critical/high bugs will
 be fixed before release (privacy, payment, compliance).
 6 lower-priority bugs deferred with workarounds. Release
 quality confident."

═══════════════════════════════════════════════════════════
```

**Key Decision Factors**:
1. **Risk**: P0/P1 = Cannot ship, P2/P3 = Can defer
2. **Capacity**: Realistic 75% allocation, not 100%
3. **Impact**: Security/Legal > Revenue > UX > Cosmetic
4. **Buffer**: Always leave slack for unknowns
5. **Communication**: Transparent about trade-offs
</details>

### Câu Hỏi 4: Root Cause Analysis

**Tình huống**: Production incident - User data shown to wrong user.

Timeline:
- Nov 20, 3PM: Release v2.5.0 to production
- Nov 20, 8PM: First user report "seeing other people's data"
- Nov 20, 9PM: Confirmed 50 users affected
- Nov 20, 10PM: Rollback to v2.4.0
- Nov 21: Investigation

Investigation findings:
- New feature: Caching layer added (Redis)
- Cache key was user email (e.g., "cache:user@example.com")
- But email normalization inconsistent:
  - Some places: lowercase (user@example.com)
  - Other places: original case (User@Example.com)
- Result: User@Example.com got cache of user@example.com

**Câu hỏi**: Perform 5 Whys analysis và đề xuất preventive actions.

<details>
<summary>Đáp án</summary>

```
═══════════════════════════════════════════════════════════
ROOT CAUSE ANALYSIS: Production Data Leak Incident
Incident ID: INC-2024-1120
Date: Nov 21, 2024
═══════════════════════════════════════════════════════════

📋 INCIDENT SUMMARY
────────────────────────────────────────────────────────
What Happened:
Users saw other users' data (names, orders, addresses)

When:
• Nov 20, 8PM - First report
• Nov 20, 9PM - Confirmed widespread
• Nov 20, 10PM - Rollback completed

Impact:
• 50 users affected
• Privacy breach (GDPR violation)
• User trust impact
• 2 hours downtime (rollback)

Severity: CRITICAL (Privacy / Security)

🔍 5 WHYS ANALYSIS
────────────────────────────────────────────────────────

WHY #1: Why did users see wrong data?
→ Because Redis cache returned wrong user's data

WHY #2: Why did cache return wrong user's data?
→ Because cache key collision: different emails mapped
   to same cache key

WHY #3: Why did cache key collision occur?
→ Because email was used as cache key but with inconsistent
   case normalization
   • Login flow: "user@example.com" (lowercase)
   • Profile API: "User@Example.com" (original case)

WHY #4: Why was email normalization inconsistent?
→ Because different services handled email differently:
   • Auth service: Always lowercase
   • Profile service: Preserved original case
   No shared email normalization library

WHY #5: Why was there no shared normalization?
→ Because:
   • Microservices developed independently
   • No data consistency guidelines
   • Code review didn't catch it
   • No integration test for case sensitivity

ROOT CAUSE:
1. Immediate: Cache key design flaw (email without normalization)
2. Underlying: No data consistency standards across services
3. Process: Insufficient integration testing

───────────────────────────────────────────────────────

🎯 CONTRIBUTING FACTORS
────────────────────────────────────────────────────────

1. CODE DESIGN:
   ❌ Cache key based on email (user input, variable case)
   ❌ No email normalization before caching
   ❌ No uniqueness validation

2. TESTING GAPS:
   ❌ No test with different email cases
   ❌ Integration tests didn't cover cache
   ❌ No cross-service consistency tests

3. CODE REVIEW:
   ❌ Reviewers didn't question cache key design
   ❌ No security review for new cache layer
   ❌ No checklist for data consistency

4. DEPLOYMENT:
   ❌ No canary deployment (went to 100% immediately)
   ❌ No monitoring alert for "wrong user" scenarios
   ❌ No immediate rollback trigger

───────────────────────────────────────────────────────

✅ CORRECTIVE ACTIONS
────────────────────────────────────────────────────────

IMMEDIATE FIXES (Completed):
✅ Rollback to v2.4.0 (Nov 20, 10PM)
✅ Cleared all Redis cache (Nov 20, 10PM)
✅ Notified affected users (Nov 21, 9AM)
✅ Incident report to management (Nov 21, 10AM)

SHORT-TERM FIXES (This Week):
✅ Fix cache key to use user_id (not email)
   • File: cache/user_cache.py
   • Change: cache:user:<user_id> instead of cache:<email>
   • Commit: abc123f

✅ Add email normalization library
   • New package: @company/email-utils
   • Function: normalizeEmail(email) → lowercase + trim
   • All services updated to use this

✅ Add integration tests
   • Test: User login with "User@Example.com"
   • Then: Profile API call
   • Assert: Correct user data returned
   • Test: Multiple users with same email different case
   • Assert: No cache collision

✅ Deploy with canary (5% → 25% → 100%)

───────────────────────────────────────────────────────

🛡️  PREVENTIVE ACTIONS (Next 2 Weeks)
────────────────────────────────────────────────────────

1. STANDARDS & GUIDELINES:
   □ Create: Data Consistency Guidelines
     • Email normalization: Always lowercase
     • ID fields: Always use immutable IDs, not user input
     • Cache keys: Document key design rationale

   □ Create: Caching Best Practices Doc
     • Key design: Use immutable identifiers
     • Validation: Keys must be unique and deterministic
     • Testing: Must test cache with varied inputs

2. CODE REVIEW ENHANCEMENTS:
   □ Update: Code Review Checklist
     • [ ] If caching: Is cache key immutable?
     • [ ] If user input: Is normalization consistent?
     • [ ] If personal data: Is access control validated?

   □ Require: Security review for features handling PII
   □ Mandatory: Architecture review for new infra (cache, DB)

3. TESTING IMPROVEMENTS:
   □ Add: Integration test suite for cross-service data flow
   □ Add: Security test cases
     • Test: User A cannot see User B's data
     • Test: Case sensitivity in all user inputs
     • Test: Cache isolation between users

   □ Automate: Run integration tests in CI/CD

4. MONITORING & ALERTING:
   □ Add: Monitoring for "wrong user data" scenarios
     • Alert: If user_id in cache ≠ user_id in request
     • Alert: If same session_id shows different user_ids

   □ Add: Cache hit/miss rate monitoring
   □ Add: User data access logs (audit trail)

5. DEPLOYMENT SAFETY:
   □ Policy: All releases use canary deployment
     • 5% for 1 hour
     • If no errors: 25% for 2 hours
     • If no errors: 100%

   □ Policy: Rollback SLA: < 15 mins from decision
   □ Runbook: Automated rollback scripts

───────────────────────────────────────────────────────

📚 LESSONS LEARNED
────────────────────────────────────────────────────────

WHAT WENT WELL:
✅ Fast detection (1 hour from first report)
✅ Quick rollback decision (2 hours total)
✅ Clear communication to users
✅ Team mobilized quickly

WHAT WENT WRONG:
❌ Issue not caught in testing (test gap)
❌ No canary deployment (went to 100% immediately)
❌ No monitoring alert for this scenario
❌ Code review missed the cache key design flaw

WHAT WE LEARNED:
📌 Cache keys must use immutable identifiers (user_id, not email)
📌 User input needs consistent normalization across all services
📌 Integration tests critical for cross-service features
📌 Security review needed for all features handling PII
📌 Canary deployment catches issues before full impact
📌 Monitoring must cover "wrong user" scenarios

───────────────────────────────────────────────────────

👥 RESPONSIBLE PARTIES
────────────────────────────────────────────────────────

Incident Owner: Engineering Manager
RCA Owner: Senior Backend Engineer

Action Item Owners:
• Data guidelines: Tech Lead (Due: Dec 1)
• Code review checklist: Engineering Manager (Due: Nov 28)
• Integration tests: QA Lead (Due: Dec 5)
• Monitoring: DevOps Lead (Due: Dec 1)
• Deployment policy: CTO (Due: Nov 30)

───────────────────────────────────────────────────────

📅 FOLLOW-UP
────────────────────────────────────────────────────────

Review Date: Dec 8, 2024
Review Agenda:
• Verify all corrective actions completed
• Review effectiveness (any similar issues?)
• Share learnings company-wide
• Update incident response playbook

═══════════════════════════════════════════════════════════
```

**Key Takeaways**:

1. **5 Whys dug deep**: From symptom (wrong data) to root cause (no standards)
2. **Multi-level solutions**:
   - Immediate: Fix the bug
   - Short-term: Add tests, improve deployment
   - Long-term: Process improvements, standards
3. **Ownership clear**: Each action has owner and deadline
4. **Learn and improve**: Lessons documented, shared
5. **Prevent recurrence**: Multiple safeguards added

This RCA transforms an incident into organizational learning.
</details>

---

## Tóm Tắt

### Key Takeaways

1. **Defect Lifecycle**:
   - New → Assigned → In Progress → Resolved → Verified → Closed
   - Special states: Reopened, Rejected, Duplicate, Deferred
   - Each state has clear owner and next actions

2. **Effective Defect Reports**:
   - Clear title and description
   - Detailed reproduction steps
   - Expected vs actual results
   - Evidence (screenshots, logs)
   - Environment details
   - Objective, factual language

3. **Severity vs Priority**:
   - **Severity**: Technical impact (Critical/High/Medium/Low)
   - **Priority**: Business urgency (P0/P1/P2/P3)
   - Different: Can have low severity but high priority (CEO demo bug)

4. **Defect Triage**:
   - Regular meetings to review, assign, prioritize
   - Verify real defects vs expected behavior
   - Balance severity, priority, capacity
   - Make data-driven decisions

5. **Defect Metrics**:
   - DRE (Defect Removal Efficiency): % found in testing
   - Defect density: Defects per KLOC
   - Defect aging: How long defects stay open
   - MTTR: Mean time to repair
   - Track trends to improve quality

6. **Root Cause Analysis**:
   - 5 Whys: Dig deeper to find root cause
   - Fishbone diagram: Categorize contributing factors
   - Focus on process improvement, not blame
   - Document lessons learned

7. **Defect Prevention**:
   - Shift-left: Early testing, reviews
   - Automation: CI/CD, regression tests
   - Standards: Coding guidelines, checklists
   - Training: Continuous learning
   - Retrospectives: Learn from defects

### Defect Management Checklist

**When Defect Found**:
- [ ] Verify it's a real defect
- [ ] Check if duplicate
- [ ] Write clear defect report
- [ ] Attach evidence (screenshot, logs)
- [ ] Assign severity and priority
- [ ] Submit to tracking system

**During Triage**:
- [ ] Review all new defects
- [ ] Validate severity/priority
- [ ] Assign to developer
- [ ] Set target fix date
- [ ] Document decisions

**When Fix Ready**:
- [ ] Verify fix with original test case
- [ ] Run regression tests
- [ ] Check for side effects
- [ ] Update defect status
- [ ] Document in release notes

**Periodic Review**:
- [ ] Review defect metrics
- [ ] Identify patterns/trends
- [ ] Perform RCA for critical defects
- [ ] Update preventive actions
- [ ] Share learnings with team

---

**Giai đoạn 7 hoàn thành!** Bạn đã học về Test Management Part 2:
- Module 7.1: Test Monitoring & Control
- Module 7.2: Test Reporting
- Module 7.3: Configuration Management
- Module 7.4: Defect Management

**Tiếp theo**: Bài tập tổng hợp cho giai đoạn 7.
