# Bài Tập Giai Đoạn 7: Test Management - Part 2

## Phần 1: Bài Tập Thực Hành

### Bài Tập 1: Test Monitoring Metrics (Module 7.1)

**Tình huống**: Bạn là Test Lead cho dự án VNPay QR Payment. Sprint 10 đang diễn ra.

**Dữ liệu Sprint 10 (ngày thứ 7/10)**:

```
Test Execution:
• Total test cases: 400
• Executed: 280
• Passed: 238
• Failed: 42
• Blocked: 5 (do 1 P1 defect)
• Not executed: 120

Defects:
• Total found: 68
• Fixed: 52
• Open: 16
  - Critical: 0
  - High: 1 (blocking 5 TCs)
  - Medium: 9
  - Low: 6

Time:
• Sprint duration: 10 days
• Days elapsed: 7
• Days remaining: 3

Velocity:
• Avg TCs executed/day: 40
```

**Yêu cầu**: Tính toán các metrics sau và đánh giá tình trạng sprint:

a) **Test Execution %** và **Pass Rate**
b) **Defect Rate** (defects per 100 TCs executed)
c) **ETA** (Estimated Time to Complete) - ngày nào sẽ hoàn thành 100% execution?
d) **Open Defect Rate** và **Fix Rate**
e) Đánh giá: Sprint có on track không? Có risk gì? Cần actions gì?

<details>
<summary>Đáp Án</summary>

**a) Test Execution % và Pass Rate**:

```
Test Execution % = (Executed / Total) × 100%
                 = (280 / 400) × 100%
                 = 70%

Pass Rate = (Passed / Executed) × 100%
          = (238 / 280) × 100%
          = 85%
```

**b) Defect Rate**:

```
Defect Rate = (Total Defects / Executed TCs) × 100
            = (68 / 280) × 100
            = 24.3 defects per 100 TCs

Benchmark:
• < 20: Good
• 20-30: Average
• > 30: High (quality concern)

→ 24.3 is in Average range
```

**c) ETA (Estimated Time to Complete)**:

```
Remaining TCs = 400 - 280 = 120 TCs
Velocity = 40 TCs/day

ETA = Remaining / Velocity
    = 120 / 40
    = 3 days

Current day: Day 7
ETA completion: Day 7 + 3 = Day 10

Sprint end: Day 10
→ Just on time! (no buffer)
```

**d) Open Defect Rate và Fix Rate**:

```
Open Defect Rate = (Open / Total) × 100%
                 = (16 / 68) × 100%
                 = 23.5%

Target: < 10% at sprint end
Current: 23.5% (⚠️ Above target)

Fix Rate = (Fixed / Total) × 100%
         = (52 / 68) × 100%
         = 76.5%

Target: > 90% at sprint end
Current: 76.5% (⚠️ Below target)
```

**e) Đánh giá và Actions**:

```
═══════════════════════════════════════════════════════════
STATUS ASSESSMENT - Sprint 10, Day 7
═══════════════════════════════════════════════════════════

📊 OVERALL: 🟡 AT RISK

POSITIVE SIGNALS:
✅ Pass rate: 85% (above 80% target)
✅ Execution pace: On track (70% at Day 7 of 10)
✅ No critical defects open
✅ Defect rate: 24.3 (average, acceptable)

CONCERNS:
⚠️  No buffer: ETA = Day 10, Sprint end = Day 10
    → Any delay = miss deadline
⚠️  5 TCs blocked by 1 High defect
    → Risk if not fixed soon
⚠️  Open defect rate: 23.5% (target < 10%)
    → 16 defects still open
⚠️  Fix rate: 76.5% (target > 90%)
    → Dev team may be slow

RISKS:
1. HIGH DEFECT (blocking 5 TCs):
   • If not fixed in 1 day → 5 TCs not tested
   • Remaining TCs: 120 → 125 (if blocker persists)
   • ETA would slip to Day 10.125 → MISS DEADLINE

2. NO BUFFER:
   • Any unexpected issue → delay
   • No time for retesting if new issues found

3. OPEN DEFECTS:
   • 16 defects still open
   • Need aggressive fixing & verification
   • Risk: Some may reopen

───────────────────────────────────────────────────────

🎯 RECOMMENDED ACTIONS:

IMMEDIATE (Today - Day 7):
1. ⚡ HIGH PRIORITY: Fix & verify blocking High defect
   → Unblock 5 test cases
   → Assign best developer
   → Target: Fixed by EOD

2. 📊 Re-plan remaining work:
   → If blocker fixed: Continue as planned
   → If blocker not fixed: Defer 5 blocked TCs or extend 1 day

SHORT-TERM (Day 8-9):
3. 🐛 Aggressive defect fixing:
   → Focus on Medium defects (9 open)
   → Target: Fix 6-7 Medium defects in Day 8-9
   → Get Open rate to < 15%

4. 🚀 Increase execution velocity (if possible):
   → Current: 40 TCs/day
   → Target: 45 TCs/day (if feasible)
   → Would complete by Day 9.7 (create buffer)

5. 📉 Prioritize remaining TCs:
   → Risk-based: High-risk scenarios first
   → If time runs out: Defer low-priority TCs

RISK MITIGATION:
6. ⚠️  Prepare contingency plan:
   Option A: Extend sprint 1 day (to Day 11)
   Option B: Defer 20 lowest-priority TCs
   Option C: Reduce scope (negotiate with PM)

7. 📢 Daily standup focus:
   → Blocker status (every day until resolved)
   → Defect fix progress
   → Any new risks

───────────────────────────────────────────────────────

📈 MONITORING PLAN (Day 8-10):

Day 8 Morning:
• Check: Is High defect fixed?
• Check: How many new defects found?
• Decide: Stick to plan or activate contingency?

Day 9 Morning:
• Check: Execution progress (should be ~360/400 = 90%)
• Check: Open defects (target < 10)
• Decide: Can we finish on time?

Day 10 Morning:
• Final push
• Focus on P1 test cases
• Defer P3 if time runs out

═══════════════════════════════════════════════════════════
```

**Key Lesson**: Metrics tell a story. Use them to:
- Identify risks early
- Make data-driven decisions
- Communicate clearly to stakeholders
- Take timely corrective actions
</details>

---

### Bài Tập 2: Test Reporting for Different Audiences (Module 7.2)

**Tình huống**: Sprint 12 testing hoàn thành cho Momo Bill Payment feature.

**Data**:
```
Test Execution:
• Total TCs: 350
• Executed: 348 (99.4%)
• Passed: 321 (92%)
• Failed: 27 (8%)
• Blocked: 2

Defects:
• Total: 82
• Critical: 2 (both FIXED & VERIFIED ✅)
• High: 12 (10 fixed, 2 open)
• Medium: 45 (38 fixed, 7 open)
• Low: 23 (18 fixed, 5 open)

Coverage:
• Requirements: 100%
• Risk coverage (High risk): 100%
• Code coverage: 89%

Performance:
• Target: < 2s response time
• Actual: 1.7s (95th percentile)
• Result: ✅ PASS

Security:
• Vulnerability scan: 0 Critical, 2 Medium
• Result: ✅ ACCEPTABLE (Medium issues documented)
```

**Yêu cầu**: Viết 3 versions của test completion summary cho:
a) **CTO** (Executive Summary - 5-7 bullet points)
b) **Project Manager** (Balanced - 1 page)
c) **Development Team** (Technical details)

<details>
<summary>Đáp Án</summary>

**a) For CTO (Executive Summary)**:

```
═══════════════════════════════════════════════════════════
MOMO BILL PAYMENT - TEST COMPLETION SUMMARY
Sprint 12 | Presented to: CTO
═══════════════════════════════════════════════════════════

📊 RELEASE DECISION: ✅ READY FOR PRODUCTION

KEY FINDINGS:

1. ✅ Quality: 92% pass rate (target: 90%)
   All critical defects resolved

2. ✅ Coverage: 100% requirements tested
   All high-risk scenarios covered

3. ✅ Performance: 1.7s response (target: < 2s)
   System handles peak load

4. ✅ Security: No critical vulnerabilities
   2 medium issues documented (non-blocking)

5. ⚠️  Minor concerns: 14 open defects (2 High, 12 Medium/Low)
   → No blocking issues, can be addressed in hotfix

💡 RECOMMENDATION:
✅ APPROVE production release on Dec 1

CONFIDENCE: HIGH
Business risk: LOW

───────────────────────────────────────────────────────
Prepared by: Test Lead | Nov 30, 2024
═══════════════════════════════════════════════════════════
```

**b) For Project Manager (Balanced)**:

```
═══════════════════════════════════════════════════════════
MOMO BILL PAYMENT - TEST COMPLETION REPORT
Sprint 12 | Presented to: Project Manager
Date: Nov 30, 2024
═══════════════════════════════════════════════════════════

📊 TEST EXECUTION SUMMARY
────────────────────────────────────────────────────────

Scope: Bill Payment feature (Electricity, Water, Internet)

Execution:
• Total test cases: 350
• Executed: 348 (99.4%) ✅
• Passed: 321 (92%) ✅
• Failed: 27 (8%)
• Not executed: 2 (blocked by environment issue - resolved)

Pass Rate: 92% (Target: > 90%) ✅

─────────────────────────────────────────────────────────

🐛 DEFECT SUMMARY
────────────────────────────────────────────────────────

Total Defects Found: 82

By Severity:
• Critical: 2 → 100% fixed & verified ✅
• High: 12 → 10 fixed (83%), 2 open ⚠️
• Medium: 45 → 38 fixed (84%), 7 open
• Low: 23 → 18 fixed (78%), 5 open

Overall Fix Rate: 83% (68/82)

Open Defects (14 total):
• 2 High:
  - DEF-890: UI misalignment on small screens (cosmetic)
  - DEF-901: Email notification 10-min delay (acceptable)
• 7 Medium: Minor UX improvements
• 5 Low: Cosmetic issues

Impact Assessment:
✅ No critical or high-severity blocking issues
✅ All open defects have workarounds or minor impact
✅ Safe to release, fix in next hotfix cycle

─────────────────────────────────────────────────────────

✅ EXIT CRITERIA STATUS
────────────────────────────────────────────────────────

Criteria                              Status   Result
───────────────────────────────────────────────────────
Test execution > 95%                  99.4%    ✅ PASS
Pass rate > 90%                       92%      ✅ PASS
Zero critical/high defects            ✅       ✅ PASS
Requirements coverage 100%            100%     ✅ PASS
Performance < 2s                      1.7s     ✅ PASS
Security scan completed               ✅       ✅ PASS
UAT approved                          ✅       ✅ PASS

Result: ALL CRITERIA MET ✅

─────────────────────────────────────────────────────────

📈 QUALITY METRICS
────────────────────────────────────────────────────────

Coverage:
• Requirements: 100% (50/50 user stories)
• High-risk scenarios: 100% (85/85 tests)
• Code coverage: 89% (target: 80%) ✅

Performance:
• Load test: 5,000 concurrent users ✅
• Response time: 1.7s (95th percentile) ✅
• Error rate: 0.1% (target: < 1%) ✅

Security:
• Vulnerability scan: 0 Critical, 2 Medium ✅
• Medium issues: Rate limiting & input sanitization
  → Documented, acceptable for release

─────────────────────────────────────────────────────────

⚠️  RISKS & MITIGATION
────────────────────────────────────────────────────────

IDENTIFIED RISKS:

🟡 MEDIUM: 2 High defects open (UI & email delay)
   • Impact: User experience, non-critical
   • Mitigation: Documented in known issues
   • Plan: Fix in hotfix v2.1.1 (Dec 8)

🟢 LOW: Email notification delay (10 mins vs instant)
   • Impact: User may not get instant confirmation
   • Mitigation: SMS notification still instant
   • Acceptable: Email is secondary notification

─────────────────────────────────────────────────────────

💡 RECOMMENDATION
────────────────────────────────────────────────────────

✅ RELEASE APPROVED for Dec 1, 2024

Confidence Level: HIGH

Reasoning:
• All critical functionality working
• Performance meets SLA
• Security acceptable
• Open defects minor/cosmetic
• No blocking issues

Post-Release Plan:
• Monitor first 24h closely
• Hotfix v2.1.1 with 14 open defects (Dec 8)
• Retrospective: Dec 5

─────────────────────────────────────────────────────────

📎 ATTACHMENTS
────────────────────────────────────────────────────────

• Detailed test results: [TestRail Report]
• Defect list: [Jira Filter]
• Performance report: [JMeter Results]
• Test coverage matrix: [Confluence]

═══════════════════════════════════════════════════════════
```

**c) For Development Team (Technical)**:

```
═══════════════════════════════════════════════════════════
MOMO BILL PAYMENT - TECHNICAL TEST REPORT
Sprint 12 | Audience: Development Team
═══════════════════════════════════════════════════════════

🔧 TEST ENVIRONMENT
────────────────────────────────────────────────────────

Application:
• Version: v2.1.0-RC4
• Build: #1245
• Git commit: f7a3c21
• Deployed: Nov 28, 2024

Infrastructure:
• Environment: QA (qa.momo.vn)
• Servers: 4x AWS EC2 t3.medium
• Database: RDS PostgreSQL 14.5
• Cache: ElastiCache Redis 7.0
• Load balancer: ALB

Test Data:
• Users: 500 test accounts
• Bill providers: 15 (VNPay, EVN, VNPT, etc.)
• Transactions: 10,000 test transactions

────────────────────────────────────────────────────────

🧪 TEST EXECUTION DETAILS
────────────────────────────────────────────────────────

Test Breakdown:
                  Designed  Executed  Passed  Failed
────────────────────────────────────────────────────────
Functional         250      249       232     17
Integration         50       50        45      5
Performance         30       30        30      0
Security            15       15        11      4
Usability            5        4         3      1
────────────────────────────────────────────────────────
TOTAL              350      348       321     27

Automation:
• Automated: 280 TCs (80%)
• Manual: 70 TCs (20%)
• Automation pass rate: 94%

────────────────────────────────────────────────────────

🐛 DEFECT ANALYSIS
────────────────────────────────────────────────────────

Defects by Component:
                      Total  Critical  High  Med  Low
──────────────────────────────────────────────────────
payment-service         24      1       4    15    4
billing-api             18      1       3    10    4
notification-service    12      0       2     8    2
web-ui                  20      0       2    10    8
database                 5      0       1     2    2
infrastructure           3      0       0     0    3
──────────────────────────────────────────────────────
TOTAL                   82      2      12    45   23

Top 5 Defects (Open):

1. DEF-890 [High]: UI misalignment on iPhone SE
   • Component: web-ui
   • Affected: Confirmation screen
   • Root cause: CSS media query missing for small screens
   • Workaround: Users can still complete payment
   • Fix ETA: Hotfix v2.1.1

2. DEF-901 [High]: Email notification delay (~10 mins)
   • Component: notification-service
   • Root cause: SQS queue backlog during peak load
   • Workaround: SMS notification instant, email is backup
   • Fix: Increase SQS workers from 2 to 5
   • Fix ETA: Hotfix v2.1.1

3. DEF-912 [Medium]: Bill amount rounding issue
   • Component: billing-api
   • Example: 10,005 VND displayed as 10,00 VND
   • Root cause: Decimal formatting
   • Workaround: Backend calculation correct, display only
   • Fix: Update number formatter

4. DEF-923 [Medium]: Transaction history pagination slow
   • Component: database
   • Issue: Query takes 3-5s for users with > 1000 transactions
   • Root cause: Missing index on transactions.user_id
   • Fix: Add index + query optimization

5. DEF-934 [Low]: Button tooltip missing translation
   • Component: web-ui
   • Issue: English text instead of Vietnamese
   • Root cause: Missing i18n key
   • Fix: Add translation

────────────────────────────────────────────────────────

⚡ PERFORMANCE TEST RESULTS
────────────────────────────────────────────────────────

Load Test Scenarios:

1. Normal Load (1,000 concurrent users):
   • Response time: 1.2s (95th percentile) ✅
   • Throughput: 800 req/s
   • Error rate: 0%
   • CPU: 45%, Memory: 60%

2. Peak Load (5,000 concurrent users):
   • Response time: 1.7s (95th percentile) ✅
   • Throughput: 3,500 req/s
   • Error rate: 0.1%
   • CPU: 78%, Memory: 85%

3. Stress Test (10,000 concurrent users):
   • Response time: 3.2s (95th percentile) ⚠️
   • Throughput: 6,000 req/s
   • Error rate: 2%
   • CPU: 95%, Memory: 92%
   • Note: Above expected peak (5K users)

Soak Test (24 hours, 2,000 users):
   • Stable response times ✅
   • No memory leaks ✅
   • No degradation ✅

Bottlenecks Identified:
• Database: Slow queries for pagination (DEF-923)
• Notification: SQS queue backlog (DEF-901)
• Recommendation: Add DB index, increase SQS workers

────────────────────────────────────────────────────────

🔒 SECURITY SCAN RESULTS
────────────────────────────────────────────────────────

OWASP ZAP Scan:
• Critical: 0 ✅
• High: 0 ✅
• Medium: 2 ⚠️
• Low: 5
• Info: 12

Medium Issues:

1. Rate Limiting Missing on /api/bills/pay endpoint
   • Risk: DoS attack possible
   • Recommendation: Implement rate limit (10 req/min)
   • Severity: Medium (internal API, authenticated)
   • Deferred: Add in hotfix

2. Input Sanitization on Bill Memo Field
   • Risk: XSS via memo field
   • Mitigation: Output encoding implemented
   • Residual risk: Low
   • Deferred: Add sanitization in hotfix

Low/Info Issues:
• Security headers (CSP, HSTS): Documented
• Cookie flags: Set correctly ✅

────────────────────────────────────────────────────────

🎯 COVERAGE ANALYSIS
────────────────────────────────────────────────────────

Requirements Traceability:

US-201: Select bill provider → 20 TCs (100% pass) ✅
US-202: Enter bill info → 18 TCs (94% pass)
US-203: Review & confirm → 15 TCs (100% pass) ✅
US-204: Process payment → 25 TCs (88% pass)
US-205: Send notifications → 12 TCs (92% pass)
US-206: Transaction history → 10 TCs (100% pass) ✅

Code Coverage (via pytest-cov):
• payment-service: 92%
• billing-api: 87%
• notification-service: 84%
• Overall: 89% (target: 80%) ✅

────────────────────────────────────────────────────────

🔄 REGRESSION TESTING
────────────────────────────────────────────────────────

Regression Suite: 180 TCs (automated)
• Executed: 180
• Passed: 177 (98%) ✅
• Failed: 3

Failed Regression TCs:
• TC-REG-045: Existing user profile test
  → Fixed, DEF-945
• TC-REG-112: Old payment flow
  → Updated test (expected behavior changed)
• TC-REG-134: API response format
  → Updated test (API v3 changes)

No regressions in existing functionality ✅

────────────────────────────────────────────────────────

💾 TEST DATA & ARTIFACTS
────────────────────────────────────────────────────────

Test Artifacts:
• Test cases: /test-cases/bill-payment-v2.1/
• Automation scripts: gitlab.com/momo/test-automation
  - Branch: sprint-12
  - Commit: a7f3c21
• Test data: /test-data/bill-payment/
• Test results: TestRail Project "Bill Payment"

Logs & Evidence:
• Application logs: S3 bucket (qa-logs/)
• Performance logs: JMeter results (attached)
• Security scan: ZAP report (attached)
• Screenshots: 150+ attached to defects

────────────────────────────────────────────────────────

🚀 DEPLOYMENT NOTES
────────────────────────────────────────────────────────

Pre-Deployment Checklist:
✅ All critical defects fixed
✅ Database migration tested
✅ Rollback procedure tested
✅ Feature flags configured
✅ Monitoring alerts set up

Deployment Plan:
• Blue-Green deployment
• Rollout: 10% → 25% → 50% → 100%
• Rollback trigger: Error rate > 5% or P0 defect

Post-Deployment Monitoring:
• Watch: Payment success rate (target: > 99%)
• Watch: Response time < 2s
• Watch: Error logs for new patterns
• Duration: 48 hours intensive monitoring

────────────────────────────────────────────────────────

📞 CONTACTS
────────────────────────────────────────────────────────

Test Team:
• Test Lead: Nguyen Van A (090-XXX-XXXX)
• Automation Engineer: Tran Van B
• Performance Tester: Le Thi C

Development Team:
• Backend Lead: Pham Van D
• Frontend Lead: Hoang Van E
• DevOps: Vo Thi F

On-call: Rotation schedule in PagerDuty

═══════════════════════════════════════════════════════════
```

**Key Differences**:

| Aspect | CTO | Project Manager | Dev Team |
|--------|-----|-----------------|----------|
| **Length** | 5-7 bullets | 1-2 pages | 3-5 pages |
| **Focus** | Business decision | Progress & risks | Technical details |
| **Metrics** | High-level only | Summary + trends | Detailed breakdown |
| **Language** | Business terms | Mixed | Technical terms |
| **Details** | Minimal | Moderate | Comprehensive |
| **Action** | Approve/reject | Plan next steps | Fix specific issues |

</details>

---

### Bài Tập 3: Configuration Management - Git Workflow (Module 7.3)

**Tình huống**: Team test automation có 3 testers working in parallel trên test suite cho Shopee.

**Current state**:
```
main branch:
  - test_login.py (v1.0)
  - test_checkout.py (v1.0)
  - test_payment.py (v1.0)
  - conftest.py (shared fixtures)

Tasks:
  - Tester A: Add new login tests (Google SSO)
  - Tester B: Fix flaky checkout test
  - Tester C: Refactor payment tests to use Page Object pattern
```

**Yêu cầu**:

a) Thiết kế Git branching strategy cho 3 testers
b) Viết Git commands cho Tester A từ start đến merge PR
c) Nếu Tester B và C đều modify `conftest.py` và conflict, mô tả conflict resolution process
d) Tạo sample `.gitignore` file cho test automation project

<details>
<summary>Đáp Án</summary>

**a) Git Branching Strategy**:

```
main (protected, stable test suite)
  │
  ├─── develop (integration branch)
        │
        ├─── feature/google-sso-tests (Tester A)
        │
        ├─── bugfix/fix-flaky-checkout (Tester B)
        │
        └─── refactor/payment-page-object (Tester C)

Rules:
• main: Production-ready, tagged releases
• develop: Integration branch, daily merges
• feature/*: New test scenarios
• bugfix/*: Fix failing/flaky tests
• refactor/*: Code improvements

Workflow:
1. Create feature branch from develop
2. Develop & commit changes
3. Push and create Pull Request to develop
4. Code review (minimum 1 approval)
5. Merge to develop after approval
6. Periodically: develop → main (with tag)
```

**b) Git Commands for Tester A** (Google SSO tests):

```bash
# ─────────────────────────────────────────────────────
# STEP 1: Start from latest develop
# ─────────────────────────────────────────────────────
$ git checkout develop
$ git pull origin develop

# ─────────────────────────────────────────────────────
# STEP 2: Create feature branch
# ─────────────────────────────────────────────────────
$ git checkout -b feature/google-sso-tests

# ─────────────────────────────────────────────────────
# STEP 3: Develop tests
# ─────────────────────────────────────────────────────
# ... write test_login_google_sso.py ...
# ... update test_data/users.csv ...

# ─────────────────────────────────────────────────────
# STEP 4: Commit changes (following convention)
# ─────────────────────────────────────────────────────
$ git status
# On branch feature/google-sso-tests
# Untracked files:
#   tests/test_login_google_sso.py
# Modified:
#   test_data/users.csv

$ git add tests/test_login_google_sso.py test_data/users.csv

$ git commit -m "test(login): add Google SSO login tests

- Add 5 test cases for Google SSO authentication
- Test scenarios: valid login, invalid token, expired token
- Add Google SSO test users to test_data/users.csv
- Update conftest.py with google_auth fixture

Covers: US-456 (Google SSO integration)"

# ─────────────────────────────────────────────────────
# STEP 5: Push to remote
# ─────────────────────────────────────────────────────
$ git push origin feature/google-sso-tests

# Output:
# To gitlab.com:shopee/test-automation.git
#  * [new branch]      feature/google-sso-tests -> feature/google-sso-tests

# ─────────────────────────────────────────────────────
# STEP 6: Create Pull Request (on GitLab/GitHub UI)
# ─────────────────────────────────────────────────────
# PR Title: test(login): add Google SSO login tests
# Description:
#   ## Changes
#   - Added 5 test cases for Google SSO authentication
#   - Scenarios: valid, invalid token, expired token, revoked
#   - Added test data for Google SSO users
#
#   ## Test Results
#   All 5 new tests passing locally
#
#   ## Checklist
#   - [x] Tests pass locally
#   - [x] Follows coding standards
#   - [x] Test data added
#   - [x] Documentation updated
#
# Request review from: @test-lead, @senior-tester

# ─────────────────────────────────────────────────────
# STEP 7: Address review comments (if any)
# ─────────────────────────────────────────────────────
# Reviewer: "Please add docstrings to test functions"

# ... add docstrings ...

$ git add tests/test_login_google_sso.py
$ git commit -m "docs: add docstrings to Google SSO tests"
$ git push origin feature/google-sso-tests

# ─────────────────────────────────────────────────────
# STEP 8: Merge approved (by reviewer or Tester A)
# ─────────────────────────────────────────────────────
# On GitLab/GitHub UI: Click "Merge Pull Request"
# Merge strategy: Squash and merge (cleaner history)

# ─────────────────────────────────────────────────────
# STEP 9: Clean up local branch
# ─────────────────────────────────────────────────────
$ git checkout develop
$ git pull origin develop  # Get merged changes

$ git branch -d feature/google-sso-tests  # Delete local branch
# Deleted branch feature/google-sso-tests

# ─────────────────────────────────────────────────────
# DONE! Feature merged to develop
# ─────────────────────────────────────────────────────
```

**c) Conflict Resolution** (Tester B and C both modify conftest.py):

```bash
# ═════════════════════════════════════════════════════
# SCENARIO: Conflict in conftest.py
# ═════════════════════════════════════════════════════

# TESTER B finishes first
# ─────────────────────────────────────────────────────
$ git checkout bugfix/fix-flaky-checkout
$ git add tests/test_checkout.py conftest.py
$ git commit -m "fix: make checkout test more stable

- Add explicit waits in checkout flow
- Add retry logic in conftest.py (wait_for_element)
- Increase timeout from 10s to 15s"

$ git push origin bugfix/fix-flaky-checkout
# Creates PR → Reviewed → Merged to develop ✅

# conftest.py changes from Tester B:
# Added: wait_for_element() helper function

# ─────────────────────────────────────────────────────
# TESTER C finishes later
# ─────────────────────────────────────────────────────
$ git checkout refactor/payment-page-object
$ git add tests/test_payment.py page_objects/ conftest.py
$ git commit -m "refactor: use Page Object pattern for payment

- Create PaymentPage class in page_objects/
- Refactor test_payment.py to use PaymentPage
- Add page_object fixture in conftest.py"

$ git push origin refactor/payment-page-object
# Creates PR → ⚠️  GitLab shows conflict with develop

# conftest.py changes from Tester C:
# Added: payment_page fixture

# ═════════════════════════════════════════════════════
# CONFLICT RESOLUTION by Tester C
# ═════════════════════════════════════════════════════

# OPTION 1: Merge develop into feature branch
# ─────────────────────────────────────────────────────
$ git checkout refactor/payment-page-object

$ git pull origin develop
# Auto-merging conftest.py
# CONFLICT (content): Merge conflict in conftest.py
# Automatic merge failed; fix conflicts and then commit

$ git status
# On branch refactor/payment-page-object
# You have unmerged paths.
#   (fix conflicts and run "git commit")
#
# Unmerged paths:
#   (use "git add <file>..." to mark resolution)
#         both modified:   conftest.py

# ─────────────────────────────────────────────────────
# Open conftest.py in editor
# ─────────────────────────────────────────────────────
$ cat conftest.py

"""
import pytest
from selenium import webdriver

@pytest.fixture
def driver():
    driver = webdriver.Chrome()
    yield driver
    driver.quit()

<<<<<<< HEAD (Tester C's changes)
@pytest.fixture
def payment_page(driver):
    '''Fixture for PaymentPage object'''
    from page_objects.payment_page import PaymentPage
    return PaymentPage(driver)
=======
def wait_for_element(driver, locator, timeout=15):
    '''Helper to wait for element with retry logic'''
    from selenium.webdriver.support.ui import WebDriverWait
    from selenium.webdriver.support import expected_conditions as EC
    return WebDriverWait(driver, timeout).until(
        EC.presence_of_element_located(locator)
    )
>>>>>>> develop (Tester B's changes)
"""

# ─────────────────────────────────────────────────────
# Resolve conflict: Keep BOTH changes
# ─────────────────────────────────────────────────────
# Edit conftest.py:

"""
import pytest
from selenium import webdriver

@pytest.fixture
def driver():
    driver = webdriver.Chrome()
    yield driver
    driver.quit()

# From Tester B: Helper function
def wait_for_element(driver, locator, timeout=15):
    '''Helper to wait for element with retry logic'''
    from selenium.webdriver.support.ui import WebDriverWait
    from selenium.webdriver.support import expected_conditions as EC
    return WebDriverWait(driver, timeout).until(
        EC.presence_of_element_located(locator)
    )

# From Tester C: PaymentPage fixture
@pytest.fixture
def payment_page(driver):
    '''Fixture for PaymentPage object'''
    from page_objects.payment_page import PaymentPage
    return PaymentPage(driver)
"""

# ─────────────────────────────────────────────────────
# Mark conflict resolved and commit
# ─────────────────────────────────────────────────────
$ git add conftest.py

$ git commit -m "Merge develop and resolve conftest.py conflict

Kept both changes:
- wait_for_element() from bugfix/fix-flaky-checkout
- payment_page fixture from refactor/payment-page-object"

$ git push origin refactor/payment-page-object

# ─────────────────────────────────────────────────────
# PR now shows no conflicts ✅
# ─────────────────────────────────────────────────────
# Reviewer approves → Merge to develop

# ═════════════════════════════════════════════════════
# ALTERNATIVE: Rebase (cleaner history)
# ═════════════════════════════════════════════════════
$ git checkout refactor/payment-page-object
$ git rebase develop

# CONFLICT in conftest.py (same as above)
# ... resolve conflict same way ...

$ git add conftest.py
$ git rebase --continue

$ git push origin refactor/payment-page-object --force
# Force push needed after rebase

# ═════════════════════════════════════════════════════
```

**d) Sample `.gitignore` for Test Automation Project**:

```gitignore
# ═══════════════════════════════════════════════════════
# .gitignore for Test Automation Project (Python/Selenium)
# ═══════════════════════════════════════════════════════

# ───────────────────────────────────────────────────────
# Test Results / Reports (Generated Artifacts)
# ───────────────────────────────────────────────────────
reports/
test-results/
test-output/
htmlcov/
.coverage
*.xml
*.html
allure-results/
allure-report/
pytest_cache/
.pytest_cache/

# ───────────────────────────────────────────────────────
# Screenshots / Videos (Too Large)
# ───────────────────────────────────────────────────────
screenshots/
videos/
*.png
*.jpg
*.jpeg
*.gif
*.mp4
*.avi

# EXCEPTION: Keep sample screenshots for documentation
!docs/screenshots/*.png

# ───────────────────────────────────────────────────────
# Environment Files (Secrets)
# ───────────────────────────────────────────────────────
.env
.env.local
.env.*.local
secrets.yaml
secrets.json
credentials.json
config.local.yaml

# ───────────────────────────────────────────────────────
# IDE / Editor Settings
# ───────────────────────────────────────────────────────
.vscode/
.idea/
*.swp
*.swo
*~
.DS_Store
Thumbs.db

# ───────────────────────────────────────────────────────
# Python
# ───────────────────────────────────────────────────────
__pycache__/
*.py[cod]
*$py.class
*.so
.Python
build/
develop-eggs/
dist/
downloads/
eggs/
.eggs/
lib/
lib64/
parts/
sdist/
var/
wheels/
pip-wheel-metadata/
share/python-wheels/
*.egg-info/
.installed.cfg
*.egg

# Virtual Environments
venv/
env/
ENV/
.venv

# ───────────────────────────────────────────────────────
# Node.js (if using JavaScript/TypeScript)
# ───────────────────────────────────────────────────────
node_modules/
npm-debug.log*
yarn-debug.log*
yarn-error.log*
package-lock.json
yarn.lock

# ───────────────────────────────────────────────────────
# Logs
# ───────────────────────────────────────────────────────
*.log
logs/
*.log.*

# ───────────────────────────────────────────────────────
# Test Data (Large Files)
# ───────────────────────────────────────────────────────
# Ignore large test data files
test_data/*.dump
test_data/*.sql
test_data/*.zip
test_data/*.tar.gz

# EXCEPTION: Keep small CSV/JSON test data
!test_data/*.csv
!test_data/*.json

# ───────────────────────────────────────────────────────
# Browser Drivers (Downloaded)
# ───────────────────────────────────────────────────────
drivers/
chromedriver
geckodriver
msedgedriver
*.exe

# ───────────────────────────────────────────────────────
# OS Files
# ───────────────────────────────────────────────────────
.DS_Store
.DS_Store?
._*
.Spotlight-V100
.Trashes
ehthumbs.db
Thumbs.db

# ───────────────────────────────────────────────────────
# Temporary Files
# ───────────────────────────────────────────────────────
*.tmp
*.temp
*.bak
*.swp
*~.nib

# ───────────────────────────────────────────────────────
# Docker
# ───────────────────────────────────────────────────────
.dockerignore

# ───────────────────────────────────────────────────────
# CI/CD
# ───────────────────────────────────────────────────────
.gitlab-ci-local/

# ───────────────────────────────────────────────────────
# Database
# ───────────────────────────────────────────────────────
*.db
*.sqlite
*.sqlite3

# ═══════════════════════════════════════════════════════
# END OF .gitignore
# ═══════════════════════════════════════════════════════
```

**Key Principles**:

1. **Track**: Source code, configs (templates), docs, small test data
2. **Don't track**: Generated files, secrets, large files, IDE settings
3. **Exceptions**: Use `!pattern` to un-ignore specific files
4. **Comments**: Organize sections for readability

</details>

---

### Bài Tập 4: Defect Management Triage (Module 7.4)

**Tình huống**: Triage meeting cho Grab Food app. 8 new defects reported.

**Defects**:

```
DEF-401: App crashes when opening "Favorites" screen
- Reproducibility: 100%
- Affected: All users
- Workaround: None
- Effort: 4 hours

DEF-402: "Add to Cart" button text cut off on iPhone SE
- Reproducibility: 100%
- Affected: iPhone SE only (~3% users)
- Workaround: Button still works, text just truncated
- Effort: 1 hour

DEF-403: Restaurant search with Vietnamese accents returns empty
- Reproducibility: 100%
- Affected: ~70% searches (Vietnamese keywords)
- Workaround: Search without accents
- Effort: 8 hours

DEF-404: Checkout fails for orders > 5M VND with credit card
- Reproducibility: 100%
- Affected: ~5% orders (high-value)
- Workaround: Use different payment method
- Effort: 6 hours

DEF-405: Delivery tracking map shows wrong restaurant location
- Reproducibility: 50%
- Affected: Random
- Workaround: Delivery still arrives correct address
- Effort: 12 hours (hard to reproduce)

DEF-406: Push notification 30 mins late
- Reproducibility: 80%
- Affected: Most users
- Workaround: Users can check app
- Effort: 4 hours

DEF-407: Promo code "GRAB50" not working (CEO mentioned in town hall)
- Reproducibility: 100%
- Affected: Marketing campaign users
- Workaround: Use different promo
- Effort: 2 hours

DEF-408: Restaurant logo image quality low on iPad Pro
- Reproducibility: 100%
- Affected: iPad Pro only (~2% users)
- Workaround: Logo still visible
- Effort: 3 hours
```

**Context**:
- Sprint ends in 3 days
- Team: 3 developers available
- Capacity: 9 person-days (3 devs × 3 days)
- Total effort needed: 40 hours = 5 days
- Marketing campaign launches tomorrow

**Yêu cầu**:

a) Assign **Severity** and **Priority** to each defect
b) Triage decision: Assign, Defer, hay Reject?
c) Allocate defects to 3 developers (9 person-days capacity)
d) Justify decisions with risk analysis

<details>
<summary>Đáp Án</summary>

**a) Severity & Priority Assignment**:

```
┌────────┬─────────────────────┬──────────┬──────────┬────────────┐
│ DEF ID │ Issue               │ Severity │ Priority │ Effort     │
├────────┼─────────────────────┼──────────┼──────────┼────────────┤
│ DEF-401│ Favorites crash     │ CRITICAL │ P0       │ 4h         │
│ DEF-403│ Vietnamese search   │ HIGH     │ P1       │ 8h         │
│ DEF-404│ Checkout > 5M fail  │ HIGH     │ P1       │ 6h         │
│ DEF-407│ Promo GRAB50        │ MEDIUM   │ P0       │ 2h         │
│ DEF-406│ Notification delay  │ MEDIUM   │ P2       │ 4h         │
│ DEF-405│ Wrong map location  │ MEDIUM   │ P2       │ 12h        │
│ DEF-402│ Button text cut     │ LOW      │ P3       │ 1h         │
│ DEF-408│ Logo quality iPad   │ LOW      │ P3       │ 3h         │
└────────┴─────────────────────┴──────────┴──────────┴────────────┘

Rationale:

DEF-401 (Critical/P0):
• Severity: CRITICAL - App crash, complete feature broken
• Priority: P0 - Affects all users, no workaround
• Blocks: Cannot release with this bug

DEF-403 (High/P1):
• Severity: HIGH - Core feature (search) broken
• Priority: P1 - 70% users affected (Vietnamese majority)
• Business impact: User can't find restaurants

DEF-404 (High/P1):
• Severity: HIGH - Payment fails, revenue impact
• Priority: P1 - 5% high-value orders lost
• Business impact: Direct revenue loss

DEF-407 (Medium/P0):
• Severity: MEDIUM - One promo code broken (workaround exists)
• Priority: P0 - CEO mentioned, marketing campaign tomorrow
• Political/business urgency: Very high

DEF-406 (Medium/P2):
• Severity: MEDIUM - Feature degraded but works
• Priority: P2 - Users can check app, notification nice-to-have
• Impact: Moderate, can defer

DEF-405 (Medium/P2):
• Severity: MEDIUM - Display issue but delivery correct
• Priority: P2 - 50% repro, hard to fix (12h)
• Can defer: Delivery works, map is visual only

DEF-402 (Low/P3):
• Severity: LOW - Cosmetic, button still works
• Priority: P3 - Only 3% users (iPhone SE), no functional impact

DEF-408 (Low/P3):
• Severity: LOW - Image quality, cosmetic
• Priority: P3 - Only 2% users (iPad Pro)
```

**b) Triage Decisions**:

```
═══════════════════════════════════════════════════════════
TRIAGE DECISIONS - Grab Food Sprint 24
═══════════════════════════════════════════════════════════

✅ FIX IN SPRINT (Priority):

1. DEF-407 (Promo GRAB50) - 2h - P0
   Decision: ASSIGN - Fix immediately
   Reason: CEO mentioned + marketing campaign tomorrow
   Assigned to: Dev A (quick fix)

2. DEF-401 (Favorites crash) - 4h - P0
   Decision: ASSIGN - Fix today
   Reason: Critical, blocks release, all users affected
   Assigned to: Dev B (experienced with crash issues)

3. DEF-404 (Checkout > 5M) - 6h - P1
   Decision: ASSIGN - Fix this sprint
   Reason: Revenue impact, high-value orders lost
   Assigned to: Dev C (payment expert)

4. DEF-403 (Vietnamese search) - 8h - P1
   Decision: ASSIGN - Fix this sprint
   Reason: 70% users affected, core feature
   Assigned to: Dev A (after DEF-407)

Total: 20 hours = 2.5 days

───────────────────────────────────────────────────────

⏸️  DEFER TO NEXT SPRINT:

5. DEF-406 (Notification delay) - 4h - P2
   Decision: DEFER to Sprint 25
   Reason:
   • Workaround exists (users can check app)
   • Moderate impact
   • Need capacity for P0/P1 bugs
   Risk: Acceptable (notification is nice-to-have)

6. DEF-405 (Wrong map location) - 12h - P2
   Decision: DEFER to Sprint 26
   Reason:
   • High effort (12h), hard to reproduce
   • Delivery works correctly (map is visual)
   • 50% reproducibility (intermittent)
   • Team capacity limited
   Risk: Low (delivery address correct)

───────────────────────────────────────────────────────

🗑️  REJECT / LOW PRIORITY:

7. DEF-402 (Button text cut) - 1h - P3
   Decision: DEFER to UI polish sprint
   Reason:
   • Only 3% users (iPhone SE)
   • Cosmetic, button still functional
   • Low business impact
   Risk: None (users can still use feature)

8. DEF-408 (Logo quality iPad) - 3h - P3
   Decision: DEFER to UI polish sprint
   Reason:
   • Only 2% users (iPad Pro)
   • Cosmetic issue
   • Low priority
   Risk: None

═══════════════════════════════════════════════════════════
```

**c) Developer Allocation** (9 person-days / 72 hours available):

```
┌──────────────────────────────────────────────────────────┐
│            DEVELOPER ALLOCATION - Sprint 24              │
│            Capacity: 3 devs × 3 days = 72 hours          │
├──────────────────────────────────────────────────────────┤
│                                                          │
│  DEVELOPER A (24 hours available)                        │
│  ├─ Day 1 (8h):                                          │
│  │   └─ DEF-407: Promo GRAB50 (2h) ⚡                    │
│  │       → High priority, CEO mentioned                  │
│  │   └─ DEF-403: Vietnamese search (6h, partial)        │
│  │                                                       │
│  ├─ Day 2 (8h):                                          │
│  │   └─ DEF-403: Vietnamese search (continue, 2h)       │
│  │   └─ Code review for Dev B & C (2h)                  │
│  │   └─ Buffer / Testing (4h)                           │
│  │                                                       │
│  └─ Day 3 (8h):                                          │
│      └─ Support retesting (4h)                          │
│      └─ Buffer (4h)                                     │
│                                                          │
│  Total allocated: 10h (DEF-407: 2h + DEF-403: 8h)       │
│  Buffer: 14h                                             │
│                                                          │
│──────────────────────────────────────────────────────────│
│                                                          │
│  DEVELOPER B (24 hours available)                        │
│  ├─ Day 1 (8h):                                          │
│  │   └─ DEF-401: Favorites crash (4h) ⚡                 │
│  │       → Critical, all users affected                  │
│  │   └─ Investigation / Testing (4h)                    │
│  │                                                       │
│  ├─ Day 2 (8h):                                          │
│  │   └─ Verify DEF-401 fix (2h)                         │
│  │   └─ Code review (2h)                                │
│  │   └─ Support team (4h)                               │
│  │                                                       │
│  └─ Day 3 (8h):                                          │
│      └─ Regression testing support (4h)                 │
│      └─ Buffer (4h)                                     │
│                                                          │
│  Total allocated: 4h (DEF-401)                           │
│  Buffer: 20h                                             │
│                                                          │
│──────────────────────────────────────────────────────────│
│                                                          │
│  DEVELOPER C (24 hours available)                        │
│  ├─ Day 1 (8h):                                          │
│  │   └─ DEF-404: Checkout > 5M (6h)                     │
│  │       → High priority, revenue impact                 │
│  │   └─ Testing (2h)                                    │
│  │                                                       │
│  ├─ Day 2 (8h):                                          │
│  │   └─ Verify DEF-404 fix (2h)                         │
│  │   └─ Code review (2h)                                │
│  │   └─ Buffer (4h)                                     │
│  │                                                       │
│  └─ Day 3 (8h):                                          │
│      └─ Regression testing support (4h)                 │
│      └─ Buffer (4h)                                     │
│                                                          │
│  Total allocated: 6h (DEF-404)                           │
│  Buffer: 18h                                             │
│                                                          │
└──────────────────────────────────────────────────────────┘

SUMMARY:
  Total capacity: 72 hours
  Total allocated: 20 hours (28%)
  Total buffer: 52 hours (72%)

  ✅ Healthy allocation: ~30% work, 70% buffer
  ✅ Allows for: Testing, code review, unexpected issues
  ✅ Low risk of overload
```

**d) Risk Analysis & Justification**:

```
═══════════════════════════════════════════════════════════
RISK ANALYSIS - Grab Food Sprint 24
═══════════════════════════════════════════════════════════

📊 ALLOCATION DECISION RATIONALE:

Why fix only 4 defects (out of 8)?
───────────────────────────────────────────────────────
• 4 defects = 20 hours = 28% of capacity
• Leaves 72% buffer for:
  - Testing & verification
  - Code reviews
  - Unexpected issues
  - Regression testing

Why not fix all 8 defects?
───────────────────────────────────────────────────────
• Total effort: 40 hours = 56% capacity
• Risks if we try to fix all:
  ❌ Tight schedule → rushed fixes → more bugs
  ❌ No time for thorough testing
  ❌ Team burnout
  ❌ May miss sprint deadline anyway

───────────────────────────────────────────────────────

🎯 PRIORITIZATION LOGIC:

MUST FIX (P0/P1): 4 defects
───────────────────────────────────────────────────────

1. DEF-407 (Promo - 2h):
   Why P0 despite Medium severity?
   → CEO visibility + Marketing campaign tomorrow
   → Political/business urgency overrides technical severity
   → Quick fix (2h), low risk

2. DEF-401 (Crash - 4h):
   Why P0?
   → Affects ALL users (100%)
   → Complete feature broken (Favorites)
   → Cannot release with crash bug
   → Moderate effort (4h), manageable

3. DEF-404 (Checkout - 6h):
   Why P1?
   → Revenue impact (high-value orders lost)
   → 5% orders = significant $ amount
   → Workaround exists but not ideal
   → Moderate effort (6h)

4. DEF-403 (Search - 8h):
   Why P1?
   → Core feature (search)
   → 70% users affected (Vietnamese)
   → Business impact high
   → Larger effort (8h) but justified

CAN DEFER: 4 defects
───────────────────────────────────────────────────────

5-6. DEF-406, DEF-405 (Medium):
   Why defer?
   → Workarounds exist
   → Moderate business impact
   → Need capacity for P0/P1
   → Total 16 hours → would push to 50% capacity

7-8. DEF-402, DEF-408 (Low):
   Why defer?
   → Cosmetic issues
   → Limited user impact (3%, 2%)
   → Low business value
   → Can batch in UI polish sprint

───────────────────────────────────────────────────────

⚖️  RISK ASSESSMENT:

IF WE FIX SELECTED 4:
────────────────────────────────────────────────────────
PROS:
✅ All P0/P1 bugs resolved
✅ Safe to release
✅ Sustainable pace (28% capacity)
✅ Time for testing & quality
✅ Low risk of missing deadline

CONS:
⚠️  4 defects deferred
⚠️  Notification delay persists
→ Acceptable trade-off

OVERALL RISK: 🟢 LOW

────────────────────────────────────────────────────────

IF WE TRY TO FIX ALL 8:
────────────────────────────────────────────────────────
PROS:
✅ All defects resolved (ideal world)

CONS:
❌ 56% capacity → tight
❌ Risk of rushing → more bugs
❌ No buffer for unknowns
❌ Team stress
❌ May delay sprint anyway
❌ Quality may suffer

OVERALL RISK: 🔴 HIGH

→ Not recommended

───────────────────────────────────────────────────────

📋 CONTINGENCY PLAN:

IF any P0 takes longer than estimated:
───────────────────────────────────────────────────────
Option A: Defer DEF-403 (Vietnamese search)
  → Still release with 3/4 bugs fixed
  → 70% users affected but workaround exists

Option B: Extend sprint 1 day
  → Complete all 4 bugs
  → Delay release to Day 4

Decision criteria:
  → If blocked by Day 2 morning: Choose Option A or B
  → Daily standup to monitor

IF we finish early (unlikely but possible):
───────────────────────────────────────────────────────
Pick up: DEF-406 (Notification - 4h)
  → Moderate impact, reasonable effort
  → Would improve user experience

───────────────────────────────────────────────────────

💬 COMMUNICATION PLAN:

TO MANAGEMENT:
"4 critical/high bugs will be fixed this sprint (crash,
 search, checkout, promo). 4 lower-priority bugs deferred
 with acceptable workarounds. Release quality confident."

TO MARKETING TEAM:
"GRAB50 promo code will be fixed by tomorrow (priority)."

TO PRODUCT TEAM:
"Vietnamese search and high-value checkout will be fixed
 this sprint. Notification delay and map issues deferred
 to next sprint with workarounds."

═══════════════════════════════════════════════════════════
```

**Key Takeaways**:

1. **Severity ≠ Priority**: CEO's cosmetic bug can be P0
2. **Capacity management**: Leave buffer (70%), don't overload
3. **Risk-based**: Fix blockers first, defer acceptable risks
4. **Communication**: Transparent about trade-offs
5. **Contingency**: Always have Plan B

This triage balances **business needs**, **technical reality**, and **team capacity**.

</details>

---

## Phần 2: Câu Hỏi Trắc Nghiệm (MCQ)

### Module 7.1: Test Monitoring & Control

**Câu 1**: Test execution rate được tính như thế nào?
A. (Passed TCs / Total TCs) × 100%
B. (Executed TCs / Total TCs) × 100%
C. (Failed TCs / Executed TCs) × 100%
D. (Remaining TCs / Total TCs) × 100%

<details><summary>Đáp án</summary>
**B** - Test execution rate = (Executed TCs / Total TCs) × 100%

- A là Pass Rate
- C là Fail Rate
- D là Remaining %
</details>

**Câu 2**: Bạn có 500 TCs, đã execute 300, passed 240. Pass rate là bao nhiêu?
A. 48%
B. 60%
C. 80%
D. 85%

<details><summary>Đáp án</summary>
**C** - Pass Rate = (240 / 300) × 100% = 80%

Pass rate tính trên số TCs đã execute, không phải total TCs.
</details>

**Câu 3**: Test Monitoring là gì?
A. Fixing defects
B. Checking progress vs plan
C. Writing test cases
D. Executing tests

<details><summary>Đáp án</summary>
**B** - Test Monitoring là việc kiểm tra progress so với plan, tracking metrics.

- A, C, D là testing activities, không phải monitoring
</details>

**Câu 4**: Test Control action nào là hợp lý khi pass rate chỉ 70% (target 90%)?
A. Ignore và tiếp tục test
B. Report lên management
C. Investigate root cause và improve test quality
D. Giảm target xuống 70%

<details><summary>Đáp án</summary>
**C** - Control = Take corrective action. Investigate tại sao pass rate thấp và cải thiện.

- A: Không giải quyết vấn đề
- B: Cần action, không chỉ report
- D: Thay đổi target không cải thiện chất lượng
</details>

**Câu 5**: Defect Detection Percentage (DDP) là gì?
A. % defects found in testing
B. % defects fixed
C. % defects verified
D. % defects reopened

<details><summary>Đáp án</summary>
**A** - DDP = (Defects found in phase / Total defects) × 100%

Measures effectiveness of testing in finding defects.
</details>

---

### Module 7.2: Test Reporting

**Câu 6**: Executive Summary trong test report nên dài bao nhiêu?
A. 5-10 pages
B. 1-2 pages
C. < 1 page (5-7 bullet points)
D. As long as needed

<details><summary>Đáp án</summary>
**C** - Executive Summary nên ngắn gọn, < 1 page, 5-7 điểm chính.

Senior management thường chỉ đọc Executive Summary.
</details>

**Câu 7**: Test Progress Report vs Test Completion Report - khác nhau chính?
A. Length
B. Frequency và timing
C. Audience
D. Format

<details><summary>Đáp án</summary>
**B** - Progress Report: During testing (daily/weekly). Completion Report: End of cycle.

- A, C, D cũng khác nhau nhưng B là khác biệt chính về mục đích và timing
</details>

**Câu 8**: Báo cáo cho CEO nên focus vào?
A. Technical details và code coverage
B. Test case execution statistics
C. Business impact và release decision
D. Defect descriptions

<details><summary>Đáp án</summary>
**C** - CEO quan tâm business impact, risks, và có thể release không.

- A, B, D: Too technical cho CEO
</details>

**Câu 9**: Visualization nào tốt nhất để show test execution progress over time?
A. Pie chart
B. Burndown chart
C. Bar chart
D. Table

<details><summary>Đáp án</summary>
**B** - Burndown chart shows progress vs plan over time.

- A: Good for distribution
- C: Good for comparison
- D: Less visual
</details>

**Câu 10**: Trong test report, RAG status là gì?
A. Requirements Analysis Guide
B. Red-Amber-Green (traffic light status)
C. Risk Assessment Grid
D. Report Aggregation Gateway

<details><summary>Đáp án</summary>
**B** - RAG = Red (at risk), Amber (concern), Green (on track)

Visual status indicator dễ hiểu.
</details>

---

### Module 7.3: Configuration Management

**Câu 11**: Configuration Item (CI) là gì?
A. Only source code
B. Only test cases
C. Any artifact under CM control
D. Only documentation

<details><summary>Đáp án</summary>
**C** - CI = Bất kỳ artifact nào được quản lý bởi CM system.

Includes: code, tests, docs, configs, data, etc.
</details>

**Câu 12**: Baseline là gì?
A. Any version saved in Git
B. Approved, stable version of CIs
C. Latest commit on main branch
D. Developer's local changes

<details><summary>Đáp án</summary>
**B** - Baseline = Approved, stable, frozen version dùng làm reference.

- A, C: Versions nhưng chưa chắc là baseline
- D: Không phải baseline
</details>

**Câu 13**: Khi nào nên tạo test baseline?
A. After every commit
B. Every day
C. After sprint completion / major release
D. Never

<details><summary>Đáp án</summary>
**C** - Baseline tạo tại major milestones: sprint end, release, major refactoring.

- A, B: Too frequent
- D: Sai, cần baselines
</details>

**Câu 14**: Traceability Matrix giúp gì?
A. Track requirements coverage và impact analysis
B. Only track defects
C. Only track test execution
D. Generate test reports

<details><summary>Đáp án</summary>
**A** - RTM maps requirements ↔ tests ↔ defects, enables impact analysis.

- B, C: Chỉ một phần của traceability
- D: Không phải mục đích chính
</details>

**Câu 15**: File nào NÊN commit vào Git cho test project?
A. Test results (HTML reports)
B. Screenshots of failed tests
C. Test automation scripts
D. Virtual environment folder (venv/)

<details><summary>Đáp án</summary>
**C** - Test scripts là source code, nên track trong Git.

- A, B: Generated artifacts, không commit
- D: Dependencies, nên ignore (dùng requirements.txt thay vì commit venv/)
</details>

---

### Module 7.4: Defect Management

**Câu 16**: Defect Severity vs Priority - khác nhau là gì?
A. Same thing, different words
B. Severity = Technical impact, Priority = Business urgency
C. Severity = Business impact, Priority = Technical impact
D. No difference

<details><summary>Đáp án</summary>
**B** - Severity = Mức độ technical impact. Priority = Business urgency to fix.

Can have Low Severity + High Priority (e.g., CEO demo bug).
</details>

**Câu 17**: Defect state "Reopened" nghĩa là gì?
A. Defect mới được phát hiện
B. Defect được assign lại cho developer khác
C. Fix không work, issue vẫn tồn tại
D. Defect bị duplicate

<details><summary>Đáp án</summary>
**C** - Reopened = Fix didn't work, tester verified và issue vẫn còn.

- A: New state
- B: Reassigned (vẫn ở Assigned state)
- D: Duplicate state
</details>

**Câu 18**: Defect triage meeting mục đích chính?
A. Fix defects
B. Review, assign, prioritize new defects
C. Write test cases
D. Execute tests

<details><summary>Đáp án</summary>
**B** - Triage = Review new defects, verify real bugs, assign severity/priority, assign owners.

- A: Fixing là developer's job, not triage meeting
- C, D: Not triage activities
</details>

**Câu 19**: 5 Whys technique dùng để làm gì?
A. Write 5 test cases
B. Find root cause of defects
C. Prioritize 5 defects
D. Test 5 scenarios

<details><summary>Đáp án</summary>
**B** - 5 Whys = Root Cause Analysis technique, ask "why" 5 times để dig deep.

- A, C, D: Không liên quan đến 5 Whys
</details>

**Câu 20**: Defect Removal Efficiency (DRE) là gì?
A. (Fixed defects / Total defects) × 100%
B. (Defects found in testing / Total defects) × 100%
C. (Defects found per day)
D. (Open defects / Total defects) × 100%

<details><summary>Đáp án</summary>
**B** - DRE = (Defects found in testing / Total defects) × 100%

Total defects = Testing defects + Production defects. Measures testing effectiveness.
</details>

---

### Tổng Hợp Các Modules

**Câu 21**: Test Manager cần report cho CTO về sprint status. Nên dùng loại report nào?
A. Daily standup notes
B. Detailed test cases list
C. Executive summary với RAG status
D. Technical test execution log

<details><summary>Đáp án</summary>
**C** - CTO cần Executive summary: ngắn gọn, business-focused, RAG status.

- A: Too informal
- B, D: Too detailed/technical
</details>

**Câu 22**: Baseline nào sau đây HỢP LỆ?
A. Local uncommitted changes
B. Sprint 15 approved test suite with tag v2.5.0
C. Work-in-progress feature branch
D. Random commit on develop branch

<details><summary>Đáp án</summary>
**B** - Baseline phải: Approved, stable, tagged, frozen.

- A, C: Not stable/approved
- D: May be stable but not necessarily approved baseline
</details>

**Câu 23**: Pass rate 85%, target 90%. Test Control action phù hợp?
A. Ignore vì chỉ lệch 5%
B. Investigate failed TCs và improve test/code quality
C. Giảm target xuống 85%
D. Chỉ report lên management

<details><summary>Đáp án</summary>
**B** - Test Control = Take action. Investigate và improve.

- A: 5% gap có thể significant
- C: Không cải thiện chất lượng
- D: Cần action, không chỉ report
</details>

**Câu 24**: Defect: App crash (Critical) trên CEO's iPhone trước demo ngày mai. Severity và Priority?
A. Severity: Critical, Priority: P0
B. Severity: Critical, Priority: P3
C. Severity: Low, Priority: P0
D. Severity: Low, Priority: P3

<details><summary>Đáp án</summary>
**A** - App crash = Critical severity. CEO demo tomorrow = P0 priority.

Both severity and urgency are high.
</details>

**Câu 25**: Git branching strategy tốt nhất cho test automation team (3 testers)?
A. Tất cả commit trực tiếp vào main
B. main (stable) ← develop ← feature branches
C. Mỗi tester có branch riêng, không merge
D. Không dùng branches, chỉ dùng tags

<details><summary>Đáp án</summary>
**B** - Gitflow: main (production) ← develop (integration) ← feature/bugfix branches.

- A: Risky, no isolation
- C: No integration
- D: Không practical
</details>

**Câu 26**: Trong RTM (Requirements Traceability Matrix), requirement "Login with Google" chưa có test cases. Risk?
A. No risk
B. Low risk
C. High risk - Untested requirement
D. Medium risk

<details><summary>Đáp án</summary>
**C** - High risk: Requirement không có tests = không được verify = high risk.

RTM reveals coverage gaps.
</details>

**Câu 27**: Defect rate: 30 defects/100 TCs. Đánh giá?
A. Excellent (< 20)
B. Good (20-30)
C. High (> 30), quality concern
D. Acceptable average range

<details><summary>Đáp án</summary>
**D** - Defect rate 20-30 per 100 TCs = Average/Acceptable range.

- < 20: Good
- > 30: High concern
</details>

**Câu 28**: File nào NÊN ignore trong .gitignore cho test project?
A. Test scripts (.py files)
B. Test results (HTML reports)
C. Test data (.csv files)
D. Test documentation (.md files)

<details><summary>Đáp án</summary>
**B** - Test results là generated artifacts, nên ignore.

- A, C, D: Nên commit (source code, data, docs)
</details>

**Câu 29**: Sprint có 100 TCs, đã execute 70, velocity 10 TCs/day. ETA hoàn thành?
A. 3 days
B. 7 days
C. 10 days
D. 1 day

<details><summary>Đáp án</summary>
**A** - Remaining = 100 - 70 = 30 TCs. ETA = 30 / 10 = 3 days.

</details>

**Câu 30**: Tại triage meeting, defect được classify là "Not a defect, expected behavior". State nào?
A. Assigned
B. Rejected
C. Deferred
D. Duplicate

<details><summary>Đáp án</summary>
**B** - Rejected: Not a real defect, working as intended.

- A: For real defects to fix
- C: Real defects but defer to future
- D: Duplicate of existing defect
</details>

---

## Tóm Tắt

### Nội Dung Đã Học (Giai Đoạn 7)

**Module 7.1: Test Monitoring & Control**
- Test metrics: Execution %, Pass rate, Defect rate, Coverage
- Monitoring: Track progress vs plan
- Control: Take corrective actions
- Dashboards and reports

**Module 7.2: Test Reporting**
- Progress Report vs Completion Report
- Executive Summary (< 1 page)
- Customize reports for different audiences
- Effective visualizations

**Module 7.3: Configuration Management**
- Configuration Items (CIs)
- Baselines and versions
- Traceability Matrix (RTM)
- Git workflow for testing
- Change control process

**Module 7.4: Defect Management**
- Defect lifecycle (New → Resolved → Closed)
- Writing effective defect reports
- Severity vs Priority
- Defect triage process
- Defect metrics (DRE, Density, MTTR)
- Root Cause Analysis (5 Whys, Fishbone)
- Defect prevention

### Điểm Quan Trọng

1. **Data-Driven Decisions**: Use metrics để đưa ra quyết định, không dựa vào feelings
2. **Communication**: Tailor reports theo audience (CTO vs PM vs Dev)
3. **Traceability**: Maintain RTM để track coverage và impact analysis
4. **Version Control**: Sử dụng Git properly cho test artifacts
5. **Defect Management**: Systematic process từ detection đến prevention
6. **Control Actions**: Monitoring without control is useless - take action!

### Chuẩn Bị Giai Đoạn 8

Giai đoạn 8 sẽ là **Thực Hành Tổng Hợp** - apply tất cả kiến thức từ 7 giai đoạn vào các projects thực tế.

---

**Chúc mừng! Bạn đã hoàn thành Giai Đoạn 7!** 🎉

Tiếp theo: Giai Đoạn 8 - Thực Hành Tổng Hợp & Đánh Giá Cuối Khóa
