# Module 7.3: Configuration Management (Quản Lý Cấu Hình)

## Mục Tiêu Học Tập

Sau khi hoàn thành module này, bạn sẽ:
- Hiểu được configuration management là gì và tại sao quan trọng
- Nắm được các khái niệm: baseline, version, release
- Biết cách quản lý test artifacts và dependencies
- Hiểu về traceability và impact analysis
- Áp dụng được change control process
- Sử dụng được version control tools cho testing

---

## 1. Configuration Management Là Gì?

### 1.1. Định Nghĩa

**Configuration Management (CM)** là quy trình:
- Xác định và kiểm soát các configuration items
- Quản lý các versions và changes
- Duy trì tính toàn vẹn (integrity) của sản phẩm
- Đảm bảo traceability xuyên suốt lifecycle

### 1.2. Tại Sao Cần Configuration Management?

**Vấn đề khi KHÔNG có CM**:

```
❌ CHAOS WITHOUT CM:

Tester A: "Tôi test version nào nhỉ?"
Tester B: "Build mới có fix bug 123 chưa?"
Developer: "Test cases nào đang run cho release 2.5?"
Manager: "Sao bug này test lại fail? Hôm qua đã pass mà!"

→ Mỗi người một version
→ Không biết test cái gì
→ Không reproduce được bugs
→ Lãng phí thời gian
→ Rủi ro cao khi release
```

**Lợi ích khi CÓ CM**:

```
✅ WITH CM:

• Biết chính xác version đang test
• Reproduce bugs dễ dàng (biết config)
• Track được changes và impacts
• Rollback nhanh khi có vấn đề
• Traceability đầy đủ
• Team collaboration hiệu quả
• Release confidence cao
```

### 1.3. Configuration Management Trong Testing

```
┌─────────────────────────────────────────┐
│      CM IN SOFTWARE TESTING             │
├─────────────────────────────────────────┤
│                                         │
│  📦 TEST ARTIFACTS                     │
│     • Test plans                       │
│     • Test cases / scripts             │
│     • Test data                        │
│     • Test results                     │
│     • Defect reports                   │
│                                         │
│  🔧 TEST ENVIRONMENT                   │
│     • Hardware config                  │
│     • Software versions                │
│     • Network setup                    │
│     • Test tools                       │
│                                         │
│  🔗 TRACEABILITY                       │
│     • Requirements ↔ Test cases       │
│     • Test cases ↔ Defects            │
│     • Code ↔ Tests                    │
│                                         │
│  📊 BASELINE MANAGEMENT                │
│     • Approved versions                │
│     • Release configurations           │
│     • Regression test sets             │
│                                         │
└─────────────────────────────────────────┘
```

---

## 2. Các Khái Niệm Cơ Bản

### 2.1. Configuration Item (CI)

**Configuration Item** là bất kỳ artifact nào được quản lý bởi CM system.

**Ví dụ CIs trong Testing**:

```
┌─────────────────────────────────────────┐
│       CONFIGURATION ITEMS               │
├─────────────────────────────────────────┤
│                                         │
│  📄 DOCUMENTS                          │
│     • Test_Plan_v2.3.pdf               │
│     • Test_Strategy_Sprint15.docx      │
│                                         │
│  🧪 TEST CASES                         │
│     • TC_Login_001.xlsx                │
│     • TestSuite_Payment_v1.5/          │
│                                         │
│  🤖 AUTOMATION SCRIPTS                 │
│     • login_test.py (commit abc123)    │
│     • payment_suite/ (branch: main)    │
│                                         │
│  💾 TEST DATA                          │
│     • users_testdata_v3.csv            │
│     • payment_mockdata.json            │
│                                         │
│  🔧 ENVIRONMENT CONFIG                 │
│     • qa_environment_config.yaml       │
│     • docker-compose.test.yml          │
│                                         │
│  📊 TEST RESULTS                       │
│     • TestRun_Sprint15_Results.html    │
│     • Performance_Report_Nov24.pdf     │
│                                         │
└─────────────────────────────────────────┘
```

### 2.2. Baseline

**Baseline** là một version ổn định, được phê duyệt chính thức của một hoặc nhiều CIs.

**Đặc điểm Baseline**:
- ✅ Được review và approve
- ✅ Frozen (không thay đổi tùy tiện)
- ✅ Làm reference cho future changes
- ✅ Có thể reproduce

**Ví dụ Test Baseline**:

```
┌──────────────────────────────────────────────┐
│  BASELINE: "Release 2.5 Test Baseline"      │
│  Date: Nov 20, 2024                         │
│  Status: APPROVED ✅                        │
├──────────────────────────────────────────────┤
│                                              │
│  Application Under Test:                    │
│    • App version: 2.5.0-RC1                 │
│    • Build: #456                            │
│    • Commit: a7b3f21                        │
│                                              │
│  Test Artifacts:                            │
│    • Test Plan: TP_v2.5_Final.pdf           │
│    • Test Suite: regression_v2.5/           │
│      - 450 test cases                       │
│      - Last updated: Nov 15, 2024           │
│    • Test Data: testdata_v2.5.zip           │
│    • Automation: commit b8c4e32             │
│                                              │
│  Environment:                               │
│    • OS: Ubuntu 22.04 LTS                   │
│    • Database: PostgreSQL 15.2              │
│    • API Gateway: nginx 1.24                │
│    • Config: qa_config_v2.5.yaml            │
│                                              │
│  Expected Results:                          │
│    • All 450 TCs documented                 │
│    • Expected outcomes defined              │
│                                              │
└──────────────────────────────────────────────┘

Usage:
→ Regression testing reference
→ Defect reproduction
→ Performance comparison baseline
```

### 2.3. Version vs Release

```
┌─────────────────────────────────────────┐
│        VERSION vs RELEASE               │
├─────────────────────────────────────────┤
│                                         │
│  VERSION                               │
│  • Định nghĩa: Bất kỳ save point nào  │
│  • Tần suất: Liên tục (mỗi change)    │
│  • Visibility: Internal team           │
│  • Status: Draft, In Progress          │
│  • Example:                            │
│    - test_login_v1.3.py                │
│    - test_plan_draft_v0.8.docx         │
│                                         │
│  RELEASE                               │
│  • Định nghĩa: Version được deploy    │
│  • Tần suất: Có kế hoạch (sprints)    │
│  • Visibility: Customers/Production    │
│  • Status: Approved, Stable            │
│  • Example:                            │
│    - App v2.5.0 (Production)           │
│    - Test Suite Release 2.5            │
│                                         │
└─────────────────────────────────────────┘

Relationship:
Version 1 → Version 2 → ... → Version N → RELEASE
(drafts)                          ↑
                           (approved baseline)
```

**Version Numbering Convention**:

```
MAJOR.MINOR.PATCH

Example: 2.5.3

2  = Major version (breaking changes)
5  = Minor version (new features, backward compatible)
3  = Patch (bug fixes)

Test artifacts can follow same convention:
• TestSuite_Payment_v2.5.3
  2 = Major test redesign
  5 = Added new test scenarios
  3 = Fixed test data issues
```

---

## 3. Traceability Management

### 3.1. Traceability Là Gì?

**Traceability** là khả năng theo dõi relationships giữa các artifacts trong software lifecycle.

```
┌─────────────────────────────────────────┐
│      TRACEABILITY MATRIX                │
├─────────────────────────────────────────┤
│                                         │
│  REQUIREMENTS → TEST CASES              │
│  ↓                                      │
│  TEST CASES → TEST RESULTS              │
│  ↓                                      │
│  TEST RESULTS → DEFECTS                 │
│  ↓                                      │
│  DEFECTS → CODE CHANGES                 │
│  ↓                                      │
│  CODE CHANGES → REGRESSION TESTS        │
│                                         │
│  = Bi-directional traceability         │
│                                         │
└─────────────────────────────────────────┘
```

### 3.2. Requirement Traceability Matrix (RTM)

**RTM** maps requirements to test cases và defects.

**Ví dụ RTM cho Shopee Checkout**:

```
┌────────────────────────────────────────────────────────────────────────┐
│            REQUIREMENT TRACEABILITY MATRIX                             │
│            Feature: Shopee Checkout Flow                               │
├────────────────────────────────────────────────────────────────────────┤
│ Req ID │ Requirement          │ Test Cases    │ Status  │ Defects     │
├────────┼──────────────────────┼───────────────┼─────────┼─────────────┤
│ US-101 │ Add items to cart    │ TC-001        │ ✅ Pass │ -           │
│        │                      │ TC-002        │ ✅ Pass │ -           │
│        │                      │ TC-003        │ ✅ Pass │ -           │
├────────┼──────────────────────┼───────────────┼─────────┼─────────────┤
│ US-102 │ Apply discount code  │ TC-010        │ ✅ Pass │ -           │
│        │                      │ TC-011        │ ❌ Fail │ DEF-456     │
│        │                      │ TC-012        │ ✅ Pass │ -           │
├────────┼──────────────────────┼───────────────┼─────────┼─────────────┤
│ US-103 │ Select payment       │ TC-020        │ ✅ Pass │ -           │
│        │ method               │ TC-021        │ ✅ Pass │ -           │
│        │                      │ TC-022        │ ⚠️  Block│ DEF-457 (P1)│
│        │                      │ TC-023        │ ✅ Pass │ -           │
├────────┼──────────────────────┼───────────────┼─────────┼─────────────┤
│ US-104 │ Confirm order        │ TC-030        │ ✅ Pass │ -           │
│        │                      │ TC-031        │ ❌ Fail │ DEF-458     │
├────────┼──────────────────────┼───────────────┼─────────┼─────────────┤
│                                                                        │
│ COVERAGE SUMMARY:                                                      │
│ • Total Requirements: 4                                                │
│ • Total Test Cases: 11                                                 │
│ • Passed: 9 (82%)                                                      │
│ • Failed: 2 (18%)                                                      │
│ • Blocked: 1                                                           │
│ • Open Defects: 3                                                      │
│                                                                        │
│ ⚠️  Risk: US-103 blocked by P1 defect → May delay release             │
└────────────────────────────────────────────────────────────────────────┘
```

**Lợi ích của RTM**:

1. **Coverage Analysis**: Biết requirement nào đã/chưa test
2. **Impact Analysis**: Khi requirement thay đổi, biết test cases nào cần update
3. **Risk Assessment**: Requirements không có test cases = high risk
4. **Defect Tracking**: Biết defect impact requirement nào
5. **Progress Reporting**: % requirements tested/passed

### 3.3. Vertical Traceability

**Forward Traceability**: Từ requirements → tests → results

```
Requirement US-102: "User can apply discount code"
    ↓
Test Cases:
    • TC-010: Valid discount code
    • TC-011: Invalid discount code
    • TC-012: Expired discount code
    ↓
Test Results:
    • TC-010: PASS
    • TC-011: FAIL → DEF-456
    • TC-012: PASS
    ↓
Defects:
    • DEF-456: Error message not shown for invalid code
        ↓
        Code Fix: commit a3f7b21
        ↓
        Retest: TC-011 → PASS ✅
```

**Backward Traceability**: Từ test results → requirements

```
Test Result: TC-011 FAIL
    ↑
Test Case: TC-011 "Invalid discount code should show error"
    ↑
Requirement: US-102 "User can apply discount code"
    ↑
Epic: "Checkout Flow Optimization"
    ↑
Business Goal: "Increase conversion rate by 15%"

→ Một test fail → Impact business goal
→ Helps prioritize fixes
```

### 3.4. Horizontal Traceability

**Cross-artifact dependencies**:

```
Test Case TC-030: "Confirm order with GrabPay"
    ↔ Test Data: payment_testdata.csv (GrabPay account)
    ↔ Test Environment: QA env (GrabPay sandbox enabled)
    ↔ Automation Script: test_payment.py (line 234-267)
    ↔ API Mock: grabpay_mock_server (port 8080)

Change in ANY of these → Need to update others
```

**Example Impact Analysis**:

```
CHANGE: GrabPay API updated from v2 to v3

Impact Analysis via Traceability:
1. Requirements: US-103 (payment) → needs review
2. Test Cases: TC-022, TC-023 → update expected results
3. Test Data: payment_testdata.csv → add new fields
4. Automation: test_payment.py → update API calls
5. Environment: grabpay_mock_server → upgrade to v3
6. Documentation: Test_Plan.pdf → update API section

→ Without traceability: Risk bỏ sót updates
→ With traceability: Systematic impact assessment
```

---

## 4. Version Control cho Test Artifacts

### 4.1. Git cho Testing

**Tại sao dùng Git cho test artifacts?**

✅ Version history đầy đủ
✅ Collaboration hiệu quả
✅ Branching cho test development
✅ Code review cho test scripts
✅ CI/CD integration
✅ Rollback dễ dàng

**Test Repository Structure**:

```
test-automation/
│
├── .gitignore
├── README.md
├── requirements.txt
│
├── tests/
│   ├── unit/
│   ├── integration/
│   ├── e2e/
│   │   ├── test_login.py
│   │   ├── test_checkout.py
│   │   └── test_payment.py
│   └── performance/
│
├── test_data/
│   ├── users.csv
│   ├── products.json
│   └── payment_methods.yaml
│
├── config/
│   ├── qa_config.yaml
│   ├── staging_config.yaml
│   └── prod_config.yaml
│
├── page_objects/
│   ├── login_page.py
│   ├── checkout_page.py
│   └── payment_page.py
│
├── utils/
│   ├── driver_factory.py
│   └── test_helpers.py
│
├── reports/
│   └── .gitkeep (reports generated, not committed)
│
└── docs/
    ├── test_plan.md
    └── test_strategy.md
```

### 4.2. .gitignore cho Testing

**Nên ignore gì?**:

```
# .gitignore for test projects

# Test Results / Reports (generated artifacts)
reports/
test-results/
*.xml
*.html
allure-results/

# Screenshots / Videos (too large)
screenshots/
videos/
*.png
*.jpg
*.mp4

# Environment files with secrets
.env
secrets.yaml
credentials.json

# IDE settings
.idea/
.vscode/
*.swp

# OS files
.DS_Store
Thumbs.db

# Virtual environments
venv/
.venv/
env/

# Cache
__pycache__/
*.pyc
.pytest_cache/
node_modules/

# Large data files (if needed, use Git LFS)
*.dump
*.sql (> 10MB)
```

**Nên commit gì?**:

✅ Test scripts / code
✅ Test data (nhỏ gọn, mock data)
✅ Config templates (không có secrets)
✅ Documentation
✅ CI/CD pipeline configs
✅ Dependencies file (requirements.txt, package.json)

### 4.3. Branching Strategy cho Testing

```
┌─────────────────────────────────────────┐
│      GIT BRANCHING FOR TESTING          │
├─────────────────────────────────────────┤
│                                         │
│  main (stable test suite)              │
│  │                                      │
│  ├─ develop (integration branch)       │
│  │  │                                   │
│  │  ├─ feature/login-tests             │
│  │  │  (new test scenarios)            │
│  │  │                                   │
│  │  ├─ feature/payment-automation      │
│  │  │  (new automation scripts)        │
│  │  │                                   │
│  │  └─ bugfix/fix-flaky-test-TC-123    │
│  │     (fix unstable test)             │
│  │                                      │
│  └─ release/v2.5                        │
│     (test suite for release 2.5)       │
│                                         │
└─────────────────────────────────────────┘

Workflow:
1. Create feature branch from develop
2. Develop/update tests
3. Create Pull Request
4. Code review by senior tester
5. Merge to develop after approval
6. Periodically merge develop → main
7. Tag releases: v2.5.0, v2.5.1, etc.
```

**Commit Message Convention**:

```
<type>(<scope>): <subject>

Types:
- test: Add/update test cases
- fix: Fix failing/flaky test
- refactor: Refactor test code
- docs: Update test documentation
- chore: Update dependencies, config

Examples:
✅ test(login): add test for password recovery
✅ fix(payment): fix flaky test TC-456
✅ refactor(checkout): use page object pattern
✅ docs(readme): update setup instructions
✅ chore: upgrade selenium to 4.15.2
```

### 4.4. Tagging và Releases

**Git Tags cho Test Baselines**:

```bash
# Tag a stable test baseline
git tag -a v2.5.0-baseline -m "Test baseline for Release 2.5"

# Tag format:
v<app-version>-baseline

Examples:
- v2.5.0-baseline (regression suite for v2.5.0)
- v2.5.1-hotfix-baseline
- v3.0.0-beta-baseline

# View all tags
git tag -l

# Checkout a specific baseline
git checkout v2.5.0-baseline
```

**Release Notes cho Test Suite**:

```
═══════════════════════════════════════════
TEST SUITE RELEASE NOTES - v2.5.0
Release Date: Nov 25, 2024
═══════════════════════════════════════════

📦 WHAT'S NEW:

✨ New Test Scenarios (45 test cases):
  • GrabPay integration tests (15 TCs)
  • Multi-restaurant orders (18 TCs)
  • Advanced search filters (12 TCs)

🔧 IMPROVEMENTS:
  • Refactored all payment tests to use Page Object
  • Reduced test execution time by 30%
  • Added parallel execution support
  • Improved test data management

🐛 BUG FIXES:
  • Fixed flaky login test (TC-123)
  • Resolved timeout issues in checkout tests
  • Fixed test data conflicts in parallel runs

📊 TEST COVERAGE:
  • Total test cases: 450 (was 405)
  • Automation coverage: 85% (was 78%)
  • Execution time: 45 mins (was 65 mins)

🔧 TECHNICAL CHANGES:
  • Upgraded Selenium to 4.15.2
  • Added Allure reporting
  • Migrated to pytest fixtures
  • Added Docker support for test env

📖 DOCUMENTATION:
  • Updated README with setup instructions
  • Added test strategy document
  • Documented CI/CD integration

🔗 COMPATIBLE WITH:
  • Application v2.5.0+
  • Test environment: QA v2.5
  • Python 3.11+

───────────────────────────────────────────
Full Changelog: v2.4.0...v2.5.0
───────────────────────────────────────────
```

---

## 5. Change Control Process

### 5.1. Change Control Là Gì?

**Change Control** là quy trình đánh giá và approve changes trước khi implement.

**Mục đích**:
- Đánh giá impact của changes
- Đảm bảo quality
- Minimize risks
- Maintain traceability

### 5.2. Change Request Workflow

```
┌──────────────────────────────────────────────────────────┐
│            CHANGE CONTROL WORKFLOW                       │
├──────────────────────────────────────────────────────────┤
│                                                          │
│  1. SUBMIT CHANGE REQUEST                               │
│     Who: Tester, Dev, PM                                │
│     What: Describe proposed change                      │
│     ↓                                                    │
│                                                          │
│  2. IMPACT ANALYSIS                                     │
│     • What artifacts affected?                          │
│     • Effort required?                                  │
│     • Risk assessment?                                  │
│     • Timeline impact?                                  │
│     ↓                                                    │
│                                                          │
│  3. REVIEW & APPROVE                                    │
│     Reviewers: Test Lead, Tech Lead, PM                 │
│     Decision: Approve / Reject / Request More Info      │
│     ↓                                                    │
│                                                          │
│  4. IMPLEMENT CHANGE                                    │
│     • Update affected artifacts                         │
│     • Update traceability                               │
│     • Document changes                                  │
│     ↓                                                    │
│                                                          │
│  5. VERIFY CHANGE                                       │
│     • Review changes                                    │
│     • Test if applicable                                │
│     • Confirm traceability updated                      │
│     ↓                                                    │
│                                                          │
│  6. CLOSE CHANGE REQUEST                                │
│     • Update CM system                                  │
│     • Notify stakeholders                               │
│     • Archive documentation                             │
│                                                          │
└──────────────────────────────────────────────────────────┘
```

### 5.3. Change Request Template

**Ví dụ Change Request cho Test Artifact**:

```
═══════════════════════════════════════════════════════════
CHANGE REQUEST: CR-2024-1156
═══════════════════════════════════════════════════════════

📋 BASIC INFORMATION:
────────────────────────────────────────────────────────
Submitted by:    Nguyen Van A (QA Engineer)
Date submitted:  Nov 24, 2024
Priority:        Medium
Type:            Test Case Update

📝 DESCRIPTION:
────────────────────────────────────────────────────────
Change Request:
Update test cases for payment flow due to GrabPay API
upgrade from v2 to v3.

Reason for Change:
• GrabPay has deprecated API v2 (EOL: Dec 31, 2024)
• New v3 API has different request/response format
• Current tests will fail with v3 integration

📊 IMPACT ANALYSIS:
────────────────────────────────────────────────────────
Affected Artifacts:
1. Test Cases:
   • TC-022: GrabPay payment success (update steps)
   • TC-023: GrabPay payment failure (update expected)
   • TC-024: GrabPay refund flow (major rewrite)

2. Test Data:
   • payment_testdata.csv (add new fields: transaction_id_v3)

3. Automation Scripts:
   • test_payment.py (update API calls)
   • grabpay_helper.py (rewrite helper functions)

4. Test Environment:
   • Mock server needs v3 endpoints

5. Documentation:
   • Test Plan section 4.3 (update API details)

Effort Estimate:
• Analysis: 2 hours
• Updates: 8 hours
• Testing: 4 hours
• Total: 14 hours (~ 2 days)

Risk Assessment:
• Risk if approved: Low (planned change)
• Risk if rejected: HIGH (tests will fail after Dec 31)

Dependencies:
• Requires GrabPay v3 sandbox access
• Mock server update by DevOps

Timeline Impact:
• Sprint capacity: -2 days (14 hours / 7h per day)
• Can absorb in current sprint if started by Nov 27

⚖️ RECOMMENDATION:
────────────────────────────────────────────────────────
✅ APPROVE

Justification:
• Mandatory change (v2 deprecated)
• Low risk, well-defined scope
• Sufficient time to complete

───────────────────────────────────────────────────────

REVIEW & APPROVAL:
────────────────────────────────────────────────────────
[ ] Approved    [ ] Rejected    [ ] More Info Needed

Test Lead:       ________________  Date: __________
Tech Lead:       ________________  Date: __________
Project Manager: ________________  Date: __________

Comments:
_________________________________________________________

═══════════════════════════════════════════════════════════
```

### 5.4. Emergency Changes

**Fast-track process cho urgent changes**:

```
EMERGENCY CHANGE CRITERIA:

✅ Qualifies as Emergency:
  • Production P1/P0 defect
  • Security vulnerability
  • Data loss risk
  • Critical feature broken

❌ NOT Emergency:
  • Feature requests
  • Cosmetic issues
  • "Nice to have" improvements

Emergency Process:
1. Verbal approval from Test Lead + PM
2. Immediate implementation
3. Retrospective documentation within 24h
4. Post-mortem review in next meeting
```

---

## 6. Ví Dụ Thực Tế: Momo eKYC Project

### Tình Huống: Configuration Management cho Momo eKYC Testing

**Project**: Momo eKYC (Electronic Know Your Customer)
**Duration**: 4 sprints
**Team**: 5 testers, 2 test automation engineers

### 6.1. Configuration Items Identification

```
┌──────────────────────────────────────────────────────────┐
│     MOMO eKYC - CONFIGURATION ITEMS                      │
├──────────────────────────────────────────────────────────┤
│                                                          │
│  📄 DOCUMENTATION CIs:                                  │
│     • Test_Strategy_eKYC_v1.0.pdf                       │
│     • Test_Plan_Sprint_15.docx                          │
│     • Risk_Assessment_eKYC.xlsx                         │
│                                                          │
│  🧪 TEST CASE CIs:                                      │
│     • Manual_Tests_v2.3/ (200 test cases in Excel)     │
│     • Exploratory_Charter_Template_v1.0.docx            │
│                                                          │
│  🤖 AUTOMATION CIs:                                     │
│     • ekyc-automation/ (Git repo)                       │
│       - Branch: main (stable)                           │
│       - Tag: v2.3.0                                     │
│       - 150 automated test scripts                      │
│                                                          │
│  💾 TEST DATA CIs:                                      │
│     • Valid_IDs_TestData_v1.5.csv (100 valid IDs)      │
│     • Invalid_IDs_TestData_v1.2.csv                    │
│     • Face_Images_Dataset/ (500 images)                │
│       - Version tracked via hash                        │
│                                                          │
│  🔧 ENVIRONMENT CIs:                                    │
│     • QA_Environment_Config_v2.3.yaml                   │
│       - API endpoints                                   │
│       - Database configs                                │
│       - 3rd party service endpoints                     │
│     • Docker_Test_Env_v2.3/ (Docker compose)           │
│                                                          │
│  🎯 TEST RESULTS CIs:                                   │
│     • Sprint_15_Test_Results_Final.html                 │
│     • Regression_Test_Report_v2.3.pdf                   │
│     • Performance_Test_Results_Nov24.xlsx               │
│                                                          │
└──────────────────────────────────────────────────────────┘
```

### 6.2. Baseline Management

**Sprint 15 Test Baseline**:

```
═══════════════════════════════════════════════════════════
MOMO eKYC - SPRINT 15 TEST BASELINE
Baseline ID: BASELINE-eKYC-2.3.0
Date: Nov 20, 2024
Status: APPROVED ✅
═══════════════════════════════════════════════════════════

🎯 APPLICATION UNDER TEST:
────────────────────────────────────────────────────────
  Application: Momo eKYC Service
  Version: 2.3.0-RC2
  Build: #892
  Git Commit: f7a3c21
  Environment: QA (qa.ekyc.momo.vn)

📦 TEST ARTIFACTS BASELINE:
────────────────────────────────────────────────────────
  1. Test Strategy:
     • File: Test_Strategy_eKYC_v1.0.pdf
     • SHA256: 7f3a9b2c...
     • Approved: Nov 10, 2024

  2. Test Cases (Manual):
     • File: Manual_Tests_v2.3.xlsx
     • Total: 200 test cases
     • SHA256: a2f7c3d1...

  3. Automation Suite:
     • Repository: gitlab.com/momo/ekyc-automation
     • Branch: main
     • Tag: v2.3.0
     • Commit: f7a3c21
     • Test Scripts: 150

  4. Test Data:
     • Valid IDs: Valid_IDs_v1.5.csv (SHA256: 8b4e...)
     • Invalid IDs: Invalid_IDs_v1.2.csv (SHA256: 3c7f...)
     • Face Images: face_images_v1.0.zip (SHA256: 9a2d...)

  5. Expected Results:
     • Expected_Results_Sprint15.xlsx
     • Contains expected outcomes for all 350 tests

🔧 ENVIRONMENT BASELINE:
────────────────────────────────────────────────────────
  Infrastructure:
    • Cloud: AWS ap-southeast-1
    • Compute: 4x EC2 t3.medium
    • Database: RDS PostgreSQL 14.5
    • Cache: ElastiCache Redis 7.0

  Software Versions:
    • OS: Ubuntu 22.04 LTS
    • Python: 3.11.5
    • Node.js: 18.17.0
    • API Gateway: nginx 1.24.0

  3rd Party Services:
    • OCR Service: Vision API v1.3
    • Face Recognition: Face++ v3.2
    • ID Verification: MyInfo Sandbox v2.1

  Configuration:
    • File: qa_env_config_v2.3.yaml
    • SHA256: 5d3a9f2b...

📊 ACCEPTANCE CRITERIA:
────────────────────────────────────────────────────────
  Exit Criteria for this Baseline:
    ✅ All 350 test cases executed
    ✅ Pass rate ≥ 95%
    ✅ Zero P0/P1 defects
    ✅ Performance: ID verification < 3s
    ✅ Face matching accuracy ≥ 98%

🔒 BASELINE CONTROL:
────────────────────────────────────────────────────────
  • This baseline is FROZEN
  • Any changes require Change Request (CR)
  • Baseline owner: Test Lead (Nguyen Van A)
  • Review board: Test Lead, Tech Lead, PM

📎 REFERENCES:
────────────────────────────────────────────────────────
  • Jira Epic: EKYC-123
  • Confluence: https://wiki.momo.vn/ekyc/baseline-2.3
  • Storage: s3://momo-qa/baselines/ekyc-2.3.0/

═══════════════════════════════════════════════════════════
```

### 6.3. Traceability Matrix

**eKYC Requirements Traceability**:

```
┌─────────────────────────────────────────────────────────────────────────────┐
│  MOMO eKYC - REQUIREMENT TRACEABILITY MATRIX (Sprint 15)                    │
├─────────────────────────────────────────────────────────────────────────────┤
│                                                                             │
│  Req ID   │ Requirement        │ Test Cases     │ Auto? │ Status  │ Defects│
│───────────┼────────────────────┼────────────────┼───────┼─────────┼────────│
│  REQ-101  │ ID Card OCR        │ TC-001 to      │  Yes  │ ✅ Pass │ -      │
│           │ Capture & Extract  │ TC-025 (25)    │       │         │        │
│           │ • Front/Back scan  │ ├─ Manual: 5   │       │         │        │
│           │ • Extract fields   │ └─ Auto: 20    │       │         │        │
│           │ • Validate format  │                │       │         │        │
│───────────┼────────────────────┼────────────────┼───────┼─────────┼────────│
│  REQ-102  │ Face Capture       │ TC-026 to      │ Partial│ ⚠️ 92% │ DEF-789│
│           │ • Liveness check   │ TC-050 (25)    │       │         │ (Med)  │
│           │ • Photo quality    │ ├─ Manual: 10  │       │         │        │
│           │ • Multiple angles  │ └─ Auto: 15    │       │         │        │
│───────────┼────────────────────┼────────────────┼───────┼─────────┼────────│
│  REQ-103  │ Face Matching      │ TC-051 to      │  Yes  │ ⚠️ 88% │ DEF-790│
│           │ • ID photo vs      │ TC-100 (50)    │       │         │ (High) │
│           │   Live selfie      │ ├─ Manual: 15  │       │         │ DEF-791│
│           │ • Accuracy ≥ 98%   │ └─ Auto: 35    │       │         │ (Med)  │
│───────────┼────────────────────┼────────────────┼───────┼─────────┼────────│
│  REQ-104  │ ID Verification    │ TC-101 to      │  Yes  │ ✅ Pass │ -      │
│           │ via MyInfo         │ TC-130 (30)    │       │         │        │
│           │ • API integration  │ ├─ Manual: 8   │       │         │        │
│           │ • Data validation  │ └─ Auto: 22    │       │         │        │
│───────────┼────────────────────┼────────────────┼───────┼─────────┼────────│
│  REQ-105  │ Fraud Detection    │ TC-131 to      │ Partial│ 🔴 65% │ DEF-792│
│           │ • Fake ID detect   │ TC-180 (50)    │       │         │ (P1)   │
│           │ • Photo spoofing   │ ├─ Manual: 35  │       │         │ DEF-793│
│           │ • Risk scoring     │ └─ Auto: 15    │       │         │ (High) │
│───────────┼────────────────────┼────────────────┼───────┼─────────┼────────│
│  REQ-106  │ eKYC Completion    │ TC-181 to      │  Yes  │ ✅ Pass │ -      │
│           │ & Notification     │ TC-200 (20)    │       │         │        │
│           │ • Status update    │ ├─ Manual: 5   │       │         │        │
│           │ • User notification│ └─ Auto: 15    │       │         │        │
│───────────┴────────────────────┴────────────────┴───────┴─────────┴────────│
│                                                                             │
│  SUMMARY:                                                                   │
│  ├─ Total Requirements: 6                                                  │
│  ├─ Total Test Cases: 200                                                  │
│  │   • Manual: 78 (39%)                                                    │
│  │   • Automated: 122 (61%)                                                │
│  ├─ Coverage: 100% (all requirements have tests)                           │
│  ├─ Overall Pass Rate: 87%                                                 │
│  └─ Open Defects: 5 (1 P1, 2 High, 2 Medium)                              │
│                                                                             │
│  ⚠️  CRITICAL ISSUES:                                                       │
│  • REQ-105 (Fraud Detection): Only 65% pass rate, 1 P1 defect             │
│    → Blocks release, requires immediate attention                          │
│                                                                             │
│  📊 AUTOMATION COVERAGE:                                                    │
│  • Target: 70% automation                                                  │
│  • Actual: 61%                                                             │
│  • Gap: 9% (18 test cases)                                                 │
│    → Plan to automate in next sprint                                       │
│                                                                             │
└─────────────────────────────────────────────────────────────────────────────┘
```

**Defect Traceability**:

```
┌──────────────────────────────────────────────────────────────────┐
│  DEFECT-789: Face liveness check fails in low light             │
├──────────────────────────────────────────────────────────────────┤
│  Severity: Medium                                                │
│  Found in: Sprint 15, Nov 22, 2024                              │
│                                                                  │
│  Traceability:                                                   │
│  ↑ Requirement: REQ-102 (Face Capture)                          │
│  ↑ Test Case: TC-035 (Face capture in low light)               │
│  ↑ Test Result: FAIL (Nov 22, Run #47)                         │
│  ↓ Code: face_capture.py, line 156                             │
│  ↓ Fix: Commit a7f3c21 (Nov 23)                                │
│  ↓ Retest: TC-035 → PASS ✅ (Nov 24, Run #52)                  │
│                                                                  │
│  Impact Analysis:                                                │
│  • Related test cases also need retest:                         │
│    - TC-036 (Different lighting conditions)                     │
│    - TC-037 (Night mode)                                        │
│  • No other requirements affected                               │
└──────────────────────────────────────────────────────────────────┘
```

### 6.4. Change Control Example

**Change Request: Update Test Data after CMND → CCCD Migration**:

```
═══════════════════════════════════════════════════════════
CHANGE REQUEST: CR-2024-0892
═══════════════════════════════════════════════════════════

📋 CHANGE INFORMATION:
────────────────────────────────────────────────────────
Type:            Test Data Update
Submitted by:    Tran Thi B (Senior Tester)
Date:            Nov 23, 2024
Priority:        HIGH
Urgency:         Required for Sprint 16

📝 DESCRIPTION:
────────────────────────────────────────────────────────
Vietnam is transitioning from old ID cards (CMND 9 digits)
to new Citizen Cards (CCCD 12 digits). Our test data
currently uses mostly CMND format. Need to update test
data to include CCCD format to reflect real user base.

Current State:
• Valid_IDs_v1.5.csv: 100 entries
  - 90 CMND (9 digits)
  - 10 CCCD (12 digits)

Desired State:
• Valid_IDs_v2.0.csv: 100 entries
  - 30 CMND (9 digits) - legacy support
  - 70 CCCD (12 digits) - new standard

📊 IMPACT ANALYSIS:
────────────────────────────────────────────────────────
Affected Configuration Items:

1. ✏️  Test Data:
   • Valid_IDs_TestData_v1.5.csv → v2.0.csv
     - Add 60 new CCCD entries
     - Keep 30 CMND for backward compatibility
   • Invalid_IDs_TestData_v1.2.csv → v1.3.csv
     - Add invalid CCCD formats

2. ✏️  Test Cases (Manual):
   • TC-001: Update expected for CCCD format
   • TC-005: Update validation rules
   • TC-010: Add CCCD-specific test cases (new)

3. ✏️  Automation Scripts:
   • ocr_test.py: Update regex patterns
   • validation_test.py: Add CCCD validation logic
   • test_data_factory.py: Add CCCD generator

4. ✏️  Documentation:
   • Test Plan section 3.2: Update test data description
   • Test Data Management Guide: Add CCCD format

5. ℹ️  NOT Affected:
   • Application code (already supports both formats)
   • Test environment
   • Other test artifacts

Effort Estimate:
• Collect real CCCD samples: 4 hours
• Update test data files: 2 hours
• Update test cases: 3 hours
• Update automation: 5 hours
• Documentation: 2 hours
• Review & validation: 2 hours
─────────────────
Total: 18 hours (~2.5 days)

Risk Assessment:
Risk if Approved:
• LOW - Well-defined scope
• Sufficient time to implement
• No production impact

Risk if Rejected:
• MEDIUM - Test coverage gap
• Test data không reflect reality
• May miss CCCD-specific bugs

Timeline Impact:
• Sprint 16 capacity: Can accommodate
• No impact on current Sprint 15

Dependencies:
• Need sample CCCD data (can get from team)
• No external dependencies

⚖️  RECOMMENDATION:
────────────────────────────────────────────────────────
✅ APPROVE

Justification:
• Aligns with real-world usage (70% CCCD adoption)
• Improves test coverage
• Low risk, clear scope
• Important for product quality

Proposed Schedule:
• Week 1 Sprint 16: Update test data & test cases
• Week 2 Sprint 16: Update automation
• Ready for Sprint 16 testing

───────────────────────────────────────────────────────

APPROVAL SECTION:
────────────────────────────────────────────────────────
[✅] Approved    [ ] Rejected    [ ] More Info Needed

Test Lead:       Nguyen Van A        Date: Nov 24, 2024
Comments: Approved. Good catch. Let's prioritize this.

Tech Lead:       Pham Van C          Date: Nov 24, 2024
Comments: Approved. App supports both, good to test both.

Project Manager: Le Thi D            Date: Nov 24, 2024
Comments: Approved. Fits Sprint 16 scope.

───────────────────────────────────────────────────────

IMPLEMENTATION:
────────────────────────────────────────────────────────
Assigned to:     Tran Thi B
Start date:      Nov 27, 2024
Target date:     Nov 29, 2024
Status:          APPROVED - Ready to implement

───────────────────────────────────────────────────────

VERIFICATION:
────────────────────────────────────────────────────────
Verification Plan:
1. Review updated test data (sample check)
2. Run smoke tests with new data
3. Verify automation passes
4. Peer review by another tester

Verified by:     ________________  Date: __________

═══════════════════════════════════════════════════════════
```

---

## 7. Thực Hành

### Câu Hỏi 1: Configuration Items

**Câu hỏi**: Bạn đang setup CM cho một test project. Classify các items sau thành:
- A: Should track in version control (Git)
- B: Should track metadata only (not full file)
- C: Should not track

Items:
1. Test automation scripts (.py files)
2. Test execution videos (500 MB each)
3. Test cases in Excel
4. Screenshot of failed tests
5. Test data (10 MB CSV file)
6. Test results HTML reports
7. API credentials file
8. Test environment config (without secrets)
9. Test strategy document (PDF)
10. Selenium ChromeDriver binary

<details>
<summary>Đáp án</summary>

1. Test automation scripts → **A** (Track in Git)
   - Core test code, needs version history

2. Test execution videos → **C** (Don't track)
   - Too large, generated artifacts
   - Store temporarily, archive separately if needed

3. Test cases in Excel → **A** (Track in Git)
   - Critical test artifact
   - Or use test management tool with versioning

4. Screenshots of failed tests → **C** (Don't track)
   - Generated artifacts, attached to defects instead

5. Test data (10 MB CSV) → **A** (Track in Git)
   - Reasonable size, essential for test reproduction
   - If > 100MB, consider Git LFS or **B**

6. Test results HTML reports → **C** (Don't track)
   - Generated artifacts
   - Can be regenerated from test runs

7. API credentials file → **C** (NEVER track)
   - Security risk
   - Use secrets management system
   - Git ignore this file

8. Test environment config (without secrets) → **A** (Track in Git)
   - Configuration as code
   - Template for environment setup

9. Test strategy document → **A** (Track in Git)
   - Important documentation
   - Or in Markdown format for better diff

10. ChromeDriver binary → **C** (Don't track)
    - Binary file, large
    - Download via package manager or CI script
    - Document version in requirements.txt

**Best Practice**:
- Track: Source code, configs, docs, test data (reasonable size)
- Don't track: Generated files, binaries, secrets, large media
- Metadata only: Very large essential files (use Git LFS or external storage + manifest)
</details>

### Câu Hỏi 2: Traceability Analysis

**Tình huống**: Requirement REQ-205 "User can reset password via email" thay đổi:
- Old: Send plain text email với link reset
- New: Send HTML email với OTP code (no link)

**Câu hỏi**: Dựa vào traceability, artifacts nào cần update?

Traceability Matrix:
```
REQ-205 (Password Reset)
  → TC-450: Send reset email
  → TC-451: Click reset link
  → TC-452: Enter new password
  → Test Data: test_emails.csv (has email addresses)
  → Automation: test_password_reset.py
  → Mock: email_service_mock.js (mocks email sending)
  → Doc: Test_Plan.pdf (section 5.3 describes flow)
```

<details>
<summary>Đáp án</summary>

**Artifacts cần update**:

1. **Test Cases** (Impact: HIGH)
   - ✏️  TC-450: Update expected result - check HTML email format
   - ❌ TC-451: DELETE - no longer có link to click
   - ✏️  TC-452: ADD new step - enter OTP before password
   - ➕ TC-453: NEW - validate OTP code
   - ➕ TC-454: NEW - OTP expiration (e.g., 5 mins)
   - ➕ TC-455: NEW - invalid OTP handling

2. **Test Data** (Impact: MEDIUM)
   - ✏️  test_emails.csv: May need additional fields
   - ➕ Add: expected_otp column (for validation)
   - Consider: OTP generation logic in test data factory

3. **Automation Scripts** (Impact: HIGH)
   - ✏️  test_password_reset.py:
     - Remove: link clicking logic
     - Add: OTP extraction from email
     - Add: OTP input step
     - Update: assertions for HTML email

4. **Mock Services** (Impact: HIGH)
   - ✏️  email_service_mock.js:
     - Update: Email template to HTML
     - Add: OTP generation
     - Add: OTP storage for validation

5. **Documentation** (Impact: MEDIUM)
   - ✏️  Test_Plan.pdf section 5.3:
     - Update flow diagram
     - Update test scenarios
     - Add OTP-related test conditions

6. **Environment** (Impact: LOW)
   - ℹ️  May need: HTML email viewer/parser
   - Check: Email service mock supports HTML

**Impact Assessment Summary**:
- Test Cases: 3 updated, 1 deleted, 3 new = 6 TCs affected
- Effort: ~8 hours (2 hours TC update, 4 hours automation, 2 hours validation)
- Risk: Medium (significant behavior change)

**Without Traceability**:
- Risk bỏ sót TC-451 (still testing old flow)
- May forget update automation
- Documentation outdated
→ Traceability ensures systematic impact analysis
</details>

### Câu Hỏi 3: Git Workflow

**Tình huống**: Team có 3 testers đang làm việc parallel:
- Tester A: Adding new login tests
- Tester B: Fixing flaky checkout test
- Tester C: Refactoring payment tests to use Page Object

**Câu hỏi**:
a) Mô tả Git branching strategy phù hợp
b) Tester A finish trước, steps để merge code?
c) Nếu Tester B và C có conflict ở cùng file `conftest.py`, resolve như thế nào?

<details>
<summary>Đáp án</summary>

**a) Git Branching Strategy**:

```
main (protected, stable test suite)
  │
  ├─── develop (integration branch)
        │
        ├─── feature/login-tests (Tester A)
        │
        ├─── bugfix/fix-flaky-checkout (Tester B)
        │
        └─── refactor/payment-page-object (Tester C)
```

Setup:
```bash
# Tester A
git checkout develop
git pull origin develop
git checkout -b feature/login-tests

# Tester B
git checkout develop
git pull origin develop
git checkout -b bugfix/fix-flaky-checkout

# Tester C
git checkout develop
git pull origin develop
git checkout -b refactor/payment-page-object
```

**b) Tester A finishes first - Merge steps**:

```bash
# Tester A (local)
git add tests/test_login.py test_data/login_data.csv
git commit -m "test(login): add SSO login test cases"
git push origin feature/login-tests

# Tester A creates Pull Request on GitLab/GitHub
# PR title: "test(login): add SSO login test cases"
# Description: "Added 5 new test cases for SSO login..."
```

**Code Review Process**:
1. Tester A creates PR: feature/login-tests → develop
2. Request review from Test Lead or peer (Tester B/C)
3. Reviewer checks:
   - Code quality
   - Test coverage
   - No conflicts with develop
   - Tests pass in CI
4. Reviewer approves
5. Tester A (or reviewer) merges PR:
   - Option 1: Merge commit
   - Option 2: Squash merge (cleaner history)
6. Delete feature branch after merge

```bash
# After merge
git checkout develop
git pull origin develop
# feature/login-tests changes now in develop
```

**c) Conflict Resolution (Tester B và C)**:

**Scenario**: Both modify `conftest.py`

```bash
# Tester B finishes, creates PR
git push origin bugfix/fix-flaky-checkout
# PR: bugfix/fix-flaky-checkout → develop

# Code review → Approved → Merged ✅
# conftest.py from Tester B now in develop
```

```bash
# Tester C finishes later
git push origin refactor/payment-page-object
# Creates PR: refactor/payment-page-object → develop

# ⚠️  GitHub shows: "This branch has conflicts with develop"
```

**Tester C resolves conflict**:

```bash
# Option 1: Merge develop into feature branch
git checkout refactor/payment-page-object
git pull origin develop  # Pull latest develop (has Tester B's changes)

# ⚠️  CONFLICT in conftest.py
# Auto-merging conftest.py
# CONFLICT (content): Merge conflict in conftest.py

# Open conftest.py, see:
<<<<<<< HEAD (Tester C's changes)
@pytest.fixture
def payment_page(driver):
    return PaymentPage(driver)  # Tester C added this
=======
@pytest.fixture(autouse=True)
def setup_teardown():  # Tester B added this
    print("Setup")
    yield
    print("Teardown")
>>>>>>> develop (Tester B's changes)

# Manually resolve: Keep BOTH changes
@pytest.fixture(autouse=True)
def setup_teardown():
    print("Setup")
    yield
    print("Teardown")

@pytest.fixture
def payment_page(driver):
    return PaymentPage(driver)

# Save file
git add conftest.py
git commit -m "Merge develop and resolve conftest.py conflict"
git push origin refactor/payment-page-object

# Now PR has no conflicts → Can be reviewed and merged
```

**Option 2: Rebase** (cleaner history):
```bash
git checkout refactor/payment-page-object
git rebase develop

# Resolve conflicts same way
git add conftest.py
git rebase --continue
git push origin refactor/payment-page-object --force
```

**Best Practices**:
- Communicate: "I'm updating conftest.py" → avoid surprises
- Small PRs: Easier to review, less conflicts
- Frequent sync: Pull develop regularly
- CI/CD: Automated tests catch integration issues
- Code review: Catch problems early
</details>

### Câu Hỏi 4: Baseline Identification

**Câu hỏi**: Bạn là Test Lead. Khi nào nên tạo test baseline? Choose all that apply:

A. Sau mỗi test case được viết
B. Khi sprint testing hoàn thành và approved
C. Trước major release (e.g., v3.0.0)
D. Mỗi ngày cuối ngày
E. Khi có major refactoring của test suite
F. Sau mỗi commit vào Git

<details>
<summary>Đáp án</summary>

**Correct Answers: B, C, E**

**B. Khi sprint testing hoàn thành và approved** ✅
- Sprint end → stable point
- Test results reviewed and approved
- Baseline = reference cho sprint tiếp theo
- Example: "Sprint 15 Test Baseline"

**C. Trước major release (e.g., v3.0.0)** ✅
- Major release → critical milestone
- Baseline = regression test set cho future
- Helps reproduce issues in production
- Example: "Release 3.0.0 Test Baseline"

**E. Khi có major refactoring của test suite** ✅
- Before refactor: Baseline old version (backup)
- After refactor: New baseline
- Allows comparison and rollback if needed
- Example: "Pre-PageObject-Refactor Baseline"

**Incorrect:**

**A. Sau mỗi test case** ❌
- Too frequent, không practical
- Baseline is for stable snapshots, not every change

**D. Mỗi ngày** ❌
- Too frequent
- Daily = versions, not baselines
- Nightly builds ≠ baselines

**F. Sau mỗi commit** ❌
- Commits are versions, not baselines
- Baseline is approved, committed version may not be

**Baseline Frequency Guideline**:

```
TOO FREQUENT          APPROPRIATE              TOO RARE
     ↓                    ↓                        ↓
Every commit -------- Sprint end ----------- Only major releases
Every day ----------- Major milestones----- Never
Every test case ----- After refactoring
```

**Summary**:
- Baseline = Stable, approved, significant milestone
- Not too frequent (overhead), not too rare (lack of reference)
- Tied to: Sprints, releases, major changes
</details>

### Câu Hỏi 5: Change Control Decision

**Tình huống**: Bạn là Test Lead, nhận được Change Request:

```
CR-1234: Add performance testing for checkout flow

Requester: Product Manager
Reason: Recent production slowdowns during peak hours
Proposal: Add load testing (10K concurrent users)

Current Sprint: Sprint 16 (Week 2 of 2)
Sprint Goal: Functional testing for new features
Team: 5 testers (none with performance testing experience)
Tools: No load testing tools currently

Estimate:
- Learn JMeter: 2 days
- Setup environment: 1 day
- Write tests: 3 days
- Execute & analyze: 2 days
Total: 8 days

Sprint Capacity Remaining: 3 days
```

**Câu hỏi**:
a) Bạn có approve CR này không? Tại sao?
b) Nếu reject, khuyến nghị thay thế?
c) Nếu Product Manager insist "must have this sprint", bạn phản hồi như thế nào?

<details>
<summary>Đáp án</summary>

**a) Decision: ❌ REJECT (for current sprint)**

**Reasoning**:

1. **Scope**: Out of current sprint scope
   - Sprint 16 goal: Functional testing
   - Performance testing = new workstream
   - Violates sprint commitment

2. **Capacity**: Insufficient time
   - Need: 8 days
   - Available: 3 days
   - Gap: -5 days (167% over capacity)

3. **Skills**: Skill gap
   - Team has no performance testing experience
   - Learning curve: 2 days
   - Risk of poor quality tests

4. **Tools**: No infrastructure
   - Need to procure/setup JMeter
   - Environment needs load testing capability
   - Additional overhead

5. **Risk**: High delivery risk
   - May compromise functional testing quality
   - Rush job → unreliable results
   - Team burnout

**b) Alternative Recommendations**:

```
═══════════════════════════════════════════════════════════
CHANGE REQUEST CR-1234: RESPONSE
═══════════════════════════════════════════════════════════

Decision: ❌ REJECT for Sprint 16

BUT: ✅ PROPOSE ALTERNATIVE PLAN

───────────────────────────────────────────────────────────
OPTION 1: Add to Sprint 17 (RECOMMENDED)
───────────────────────────────────────────────────────────

Timeline:
• Sprint 17: Week 1-2 (Dec 4-15)
• Proper planning and preparation

Plan:
Week 1:
  • Training: 2 testers learn JMeter (2 days)
  • Setup: Performance test environment (1 day)
  • Design: Test scenarios and success criteria (1 day)

Week 2:
  • Develop: Write load tests (3 days)
  • Execute: Run tests and collect data (1 day)
  • Analyze: Generate report with recommendations (1 day)

Benefits:
✅ Adequate time and resources
✅ Proper training
✅ Quality results
✅ Doesn't compromise Sprint 16 functional testing

───────────────────────────────────────────────────────────
OPTION 2: Quick Assessment (Compromise)
───────────────────────────────────────────────────────────

If urgency is genuine:

Sprint 16 (remaining 3 days):
  • Quick spike: 1 tester, 1 day
  • Use simple tool (e.g., Apache Bench, Locust)
  • Basic load test: 1000 users (not 10K)
  • Preliminary findings only

Sprint 17:
  • Comprehensive testing per Option 1

Benefits:
✅ Quick initial signal
✅ Doesn't derail Sprint 16
⚠️  Results are preliminary, not comprehensive

───────────────────────────────────────────────────────────
OPTION 3: External Help (If Critical)
───────────────────────────────────────────────────────────

If truly critical and can't wait:

  • Hire external performance testing consultant
  • Run in parallel to Sprint 16 work
  • Team can focus on Sprint 16 goals
  • Consultant delivers performance test results

Cost: ~$5,000 - $10,000
Timeline: Can start immediately, 1-2 weeks

Benefits:
✅ Expert quality results
✅ No impact on team Sprint 16
⚠️  Additional cost

═══════════════════════════════════════════════════════════
```

**c) Response to "Must have this sprint" insistence**:

```
Email/Meeting Response:

───────────────────────────────────────────────────────────
Hi [Product Manager],

I understand performance issues are concerning and urgency
is appreciated. However, I must raise several risks with
adding this to Sprint 16:

📊 DATA-DRIVEN ANALYSIS:

Sprint 16 Capacity:
  • Current commitments: 5 testers × 7h/day × 3 days = 105 hours
  • Performance testing need: 8 days = 56 hours
  • Impact: 53% of remaining capacity

This means one of three outcomes:

OUTCOME 1: Accept performance testing
  ⚠️  Risk: Sprint 16 functional testing incomplete
  • 7 functional features at risk
  • May delay release
  • Technical debt increases

OUTCOME 2: Do both
  ⚠️  Risk: Both done poorly
  • Rushed functional testing → bugs in production
  • Rushed performance testing → unreliable data
  • Team burnout
  • Can't make decisions on unreliable data anyway

OUTCOME 3: Delay non-critical functional tests
  ⚠️  Risk: Deferred work accumulates
  • Sprint 17 overloaded
  • Velocity decreases

───────────────────────────────────────────────────────────

❓ CLARIFYING QUESTIONS:

To find the best path forward, I need to understand:

1. What specifically triggered this urgency?
   • Production incident?
   • Customer complaints?
   • Proactive concern?

2. What decision will performance data inform?
   • Release go/no-go?
   • Infrastructure scaling?
   • Future optimization?

3. What's the actual deadline?
   • Is Sprint 16 end (Dec 1) hard deadline?
   • Or can Sprint 17 (Dec 15) work?

4. What confidence level is needed?
   • Quick signal (80% confidence) → Doable in 3 days
   • Reliable data (95% confidence) → Needs proper time

───────────────────────────────────────────────────────────

💡 MY RECOMMENDATION:

Based on risk-benefit analysis, I recommend:

SHORT TERM (Sprint 16 - 3 days):
  ✅ Quick performance spike (1 tester, 1 day)
     → Gives initial signal
  ✅ Complete Sprint 16 functional testing (4 testers)
     → Protects release quality

MEDIUM TERM (Sprint 17):
  ✅ Comprehensive performance testing
     → Reliable data for decisions

This approach:
  • Addresses urgent need (quick spike)
  • Protects quality (proper functional testing)
  • Provides reliable data (Sprint 17 comprehensive test)
  • Manages team capacity and morale

───────────────────────────────────────────────────────────

📞 NEXT STEPS:

Let's discuss:
  • Your specific concerns and urgency drivers
  • Trade-offs you're willing to accept
  • Resource options (e.g., external consultant)

I'm available for a call today to align on the best path.

Regards,
[Test Lead]
───────────────────────────────────────────────────────────
```

**Key Principles in Response**:

1. **Data-driven**: Use numbers, not feelings
2. **Transparent**: Clear about risks and trade-offs
3. **Collaborative**: Seek to understand PM's drivers
4. **Solution-oriented**: Offer alternatives, not just "no"
5. **Professional**: Respectful but firm on risks
6. **Accountable**: Willing to discuss and find compromise

**Outcome**:
- Good PM will appreciate analysis and accept Sprint 17
- If still insists Sprint 16, escalate to Engineering Manager
- Document decision and risks in writing
- If forced to proceed, get explicit acknowledgment of risks
</details>

---

## Tóm Tắt

### Key Takeaways

1. **Configuration Management Purpose**:
   - Control and track test artifacts
   - Maintain integrity and traceability
   - Enable reproducibility
   - Support collaboration

2. **Core Concepts**:
   - **Configuration Item (CI)**: Any artifact under CM control
   - **Baseline**: Approved, stable version of CIs
   - **Version**: Any save point of a CI
   - **Release**: Approved version deployed to production

3. **Traceability**:
   - **Vertical**: Requirements → Tests → Results → Defects
   - **Horizontal**: Cross-artifact dependencies
   - **Benefits**: Impact analysis, coverage analysis, gap identification

4. **Version Control**:
   - Use Git for test artifacts
   - Branching strategy for parallel development
   - Commit conventions for clarity
   - Tagging for baselines

5. **Change Control**:
   - Formal process for approving changes
   - Impact analysis before implementation
   - Balance between control and agility
   - Emergency fast-track for critical issues

6. **Best Practices**:
   - Track source code, configs, docs, reasonable test data
   - Don't track generated files, binaries, secrets
   - Maintain RTM for coverage and impact analysis
   - Create baselines at major milestones
   - Implement change control but keep it lightweight
   - Use tools (Git, Jira, TestRail) effectively

### Checklist: Configuration Management

**Setup Phase**:
- [ ] Identify all configuration items
- [ ] Choose version control system (Git)
- [ ] Define repository structure
- [ ] Create .gitignore for generated files
- [ ] Setup branching strategy
- [ ] Define baseline criteria

**Operation Phase**:
- [ ] Maintain traceability matrix
- [ ] Follow commit conventions
- [ ] Create baselines at milestones
- [ ] Tag releases appropriately
- [ ] Implement change control process
- [ ] Review and update CM process regularly

**For Each Test Cycle**:
- [ ] Verify baseline defined
- [ ] Check all CIs under version control
- [ ] Update traceability matrix
- [ ] Document environment configuration
- [ ] Archive test results with CI references
- [ ] Update baseline after approval

---

**Trong module tiếp theo**: Defect Management - quản lý bugs từ detection đến resolution.
