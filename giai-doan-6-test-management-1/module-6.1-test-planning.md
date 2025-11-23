# MODULE 6.1: TEST PLANNING

**Thời lượng**: 3-4 giờ | **Độ khó**: ⭐⭐⭐

---

## MỤC TIÊU HỌC TẬP

Sau khi hoàn thành module này, bạn sẽ:

| ID | Mục tiêu | Level |
|----|----------|-------|
| FL-5.1.1 | Giải thích test planning activities | K2 |
| FL-5.1.2 | Viết entry và exit criteria | K3 |
| FL-5.1.3 | Phân biệt Definition of Ready và Done | K2 |
| FL-5.1.4 | Sử dụng Test Pyramid | K2 |
| FL-5.1.5 | Hiểu Testing Quadrants | K2 |

---

## 1. TEST PLANNING LÀ GÌ?

### 1.1. Định Nghĩa

```
╔═══════════════════════════════════════════════════════════════╗
║                      TEST PLANNING                            ║
╠═══════════════════════════════════════════════════════════════╣
║                                                               ║
║  📖 ĐỊNH NGHĨA:                                               ║
║     Activity để define TEST OBJECTIVES và phương tiện        ║
║     để đạt được objectives đó                                ║
║                                                               ║
║  🎯 MỤC ĐÍCH:                                                 ║
║     • Define WHAT to test                                    ║
║     • Define HOW to test                                     ║
║     • Define WHEN to test                                    ║
║     • Define WHO will test                                   ║
║     • Allocate RESOURCES                                     ║
║     • Manage RISKS                                           ║
║                                                               ║
║  📋 OUTPUT:                                                   ║
║     → TEST PLAN document                                     ║
║     → Test strategy                                          ║
║     → Test schedule                                          ║
║                                                               ║
║  ⏰ KHI NÀO:                                                  ║
║     • Early trong project lifecycle                          ║
║     • Continuously updated                                   ║
║     • Refined based on feedback                              ║
║                                                               ║
╚═══════════════════════════════════════════════════════════════╝
```

### 1.2. Test Planning Activities

```
╔═══════════════════════════════════════════════════════════════╗
║              TEST PLANNING ACTIVITIES                         ║
╠═══════════════════════════════════════════════════════════════╣
║                                                               ║
║  1️⃣ DETERMINE SCOPE & OBJECTIVES                             ║
║     → What features to test                                  ║
║     → What NOT to test (out of scope)                        ║
║     → Test objectives (find bugs, ensure quality, etc.)      ║
║                                                               ║
║  2️⃣ DEFINE TEST APPROACH                                     ║
║     → Test levels (Unit, Integration, System, UAT)           ║
║     → Test types (Functional, Performance, Security)         ║
║     → Test techniques (EP, BVA, Exploratory)                 ║
║                                                               ║
║  3️⃣ IDENTIFY TEST BASIS                                      ║
║     → Requirements documents                                 ║
║     → User stories                                           ║
║     → Design specs                                           ║
║                                                               ║
║  4️⃣ DEFINE ENTRY & EXIT CRITERIA                            ║
║     → Conditions to START testing                            ║
║     → Conditions to STOP testing                             ║
║                                                               ║
║  5️⃣ ESTIMATE EFFORT & SCHEDULE                               ║
║     → How long will testing take?                            ║
║     → Resource allocation                                    ║
║     → Timeline/milestones                                    ║
║                                                               ║
║  6️⃣ IDENTIFY RESOURCES                                       ║
║     → Test team (roles, skills)                              ║
║     → Test environment                                       ║
║     → Test tools                                             ║
║     → Test data                                              ║
║                                                               ║
║  7️⃣ DEFINE TEST DELIVERABLES                                 ║
║     → Test plan                                              ║
║     → Test cases                                             ║
║     → Test reports                                           ║
║     → Defect reports                                         ║
║                                                               ║
╚═══════════════════════════════════════════════════════════════╝
```

---

## 2. TEST PLAN DOCUMENT

### 2.1. Test Plan Components

```
╔═══════════════════════════════════════════════════════════════╗
║                  TEST PLAN COMPONENTS                         ║
╠═══════════════════════════════════════════════════════════════╣
║                                                               ║
║  📄 TYPICAL STRUCTURE:                                        ║
║                                                               ║
║  1. INTRODUCTION                                             ║
║     • Purpose of document                                    ║
║     • Project overview                                       ║
║     • References                                             ║
║                                                               ║
║  2. TEST SCOPE                                               ║
║     • Features to be tested (IN scope)                       ║
║     • Features NOT to be tested (OUT of scope)               ║
║     • Assumptions, constraints                               ║
║                                                               ║
║  3. TEST APPROACH/STRATEGY                                   ║
║     • Test levels                                            ║
║     • Test types                                             ║
║     • Test techniques                                        ║
║     • Automation strategy                                    ║
║                                                               ║
║  4. ENTRY & EXIT CRITERIA                                    ║
║     • Conditions to start testing                            ║
║     • Conditions to stop testing                             ║
║                                                               ║
║  5. TEST ENVIRONMENT                                         ║
║     • Hardware requirements                                  ║
║     • Software requirements                                  ║
║     • Network configuration                                  ║
║                                                               ║
║  6. TEST SCHEDULE                                            ║
║     • Timeline                                               ║
║     • Milestones                                             ║
║     • Dependencies                                           ║
║                                                               ║
║  7. RESOURCES                                                ║
║     • Test team (roles, responsibilities)                    ║
║     • Tools                                                  ║
║     • Training needs                                         ║
║                                                               ║
║  8. RISKS & MITIGATION                                       ║
║     • Identified risks                                       ║
║     • Mitigation strategies                                  ║
║                                                               ║
║  9. DELIVERABLES                                             ║
║     • Test plan (this document)                              ║
║     • Test cases                                             ║
║     • Test reports                                           ║
║                                                               ║
║  10. APPROVALS                                               ║
║     • Stakeholder sign-offs                                  ║
║                                                               ║
╚═══════════════════════════════════════════════════════════════╝
```

### 2.2. Ví Dụ: Test Plan cho Shopee Checkout Feature

**1. INTRODUCTION**
```
Purpose: Test plan cho Shopee checkout feature v2.5
Project: Shopee Mobile App Enhancement
Release: Q1 2025
```

**2. TEST SCOPE**

**IN SCOPE:**
- ✅ Cart management (add, update, remove items)
- ✅ Promo code application
- ✅ Payment method selection (ShopeePay, Cards, Bank Transfer)
- ✅ Order confirmation
- ✅ Receipt generation

**OUT OF SCOPE:**
- ❌ Shipping carrier integration (tested separately)
- ❌ Inventory management (backend team)
- ❌ Push notifications (future release)

**3. TEST APPROACH**

| Test Level | Responsibility | Tools |
|------------|---------------|-------|
| Unit Testing | Developers | Jest, pytest |
| Integration Testing | Dev + QA | Postman, Newman |
| System Testing | QA Team | Manual + Selenium |
| UAT | Business + Users | Manual |

**Test Types:**
- Functional: EP, BVA, Decision Tables
- Non-functional: Performance (1000 concurrent users), Security (payment data)
- Exploratory: 2 sessions/week

**Automation:**
- 70% regression tests automated (Selenium)
- API tests 100% automated (Newman)

**4. ENTRY & EXIT CRITERIA**

**Entry Criteria:**
- ✅ Requirements approved by PO
- ✅ Test environment ready (staging)
- ✅ Build deployed to test environment
- ✅ Test data prepared (10 test accounts)
- ✅ Test cases reviewed and approved

**Exit Criteria:**
- ✅ 100% test cases executed
- ✅ 95%+ test cases passed
- ✅ All Critical & High bugs resolved
- ✅ Medium bugs evaluated (defer or fix)
- ✅ Performance benchmarks met (<2s page load)
- ✅ Security scan passed (no critical vulnerabilities)

**5. TEST ENVIRONMENT**

| Component | Specification |
|-----------|--------------|
| Server | AWS EC2 t3.medium (2 vCPU, 4GB RAM) |
| Database | PostgreSQL 14 |
| App Version | Android 10+, iOS 14+ |
| Devices | Samsung S21, iPhone 12, iPad Pro |
| Network | WiFi + 4G simulation |

**6. TEST SCHEDULE**

```
Week 1-2: Test case design & review
Week 3:   Test environment setup
Week 4-5: Test execution (System testing)
Week 6:   UAT
Week 7:   Regression + bug fixes
Week 8:   Final sign-off
```

**7. RESOURCES**

| Role | Name | Responsibility |
|------|------|----------------|
| Test Manager | Nguyen Van A | Overall coordination |
| Test Lead | Tran Thi B | Test design, execution |
| Testers (3) | Le Van C, D, E | Manual testing |
| Automation Engineer | Pham Van F | Selenium scripts |

**8. RISKS & MITIGATION**

| Risk | Impact | Mitigation |
|------|--------|------------|
| Payment gateway downtime | High | Use mock payment in test env |
| Test data insufficient | Medium | Automated test data generation |
| Resource unavailable | Medium | Cross-train team members |

---

## 3. ENTRY & EXIT CRITERIA

### 3.1. Entry Criteria

```
╔═══════════════════════════════════════════════════════════════╗
║                     ENTRY CRITERIA                            ║
╠═══════════════════════════════════════════════════════════════╣
║                                                               ║
║  📖 ĐỊNH NGHĨA:                                               ║
║     Conditions phải satisfied TRƯỚC KHI bắt đầu testing      ║
║                                                               ║
║  🎯 MỤC ĐÍCH:                                                 ║
║     • Ensure readiness                                       ║
║     • Prevent wasted effort                                  ║
║     • Set clear expectations                                 ║
║                                                               ║
║  ✅ TYPICAL ENTRY CRITERIA:                                   ║
║                                                               ║
║     📋 DOCUMENTATION:                                         ║
║     • Requirements documented và approved                    ║
║     • Test plan approved                                     ║
║     • Test cases reviewed                                    ║
║                                                               ║
║     🖥️ ENVIRONMENT:                                          ║
║     • Test environment set up                                ║
║     • Test data available                                    ║
║     • Access credentials provided                            ║
║                                                               ║
║     💻 BUILD:                                                 ║
║     • Testable build deployed                                ║
║     • Build meets smoke test criteria                        ║
║     • Known issues documented                                ║
║                                                               ║
║     👥 TEAM:                                                  ║
║     • Test team available                                    ║
║     • Tools installed và configured                          ║
║                                                               ║
╚═══════════════════════════════════════════════════════════════╝
```

**Ví dụ Entry Criteria:**
```
ENTRY CRITERIA - SYSTEM TESTING

✅ Build & Environment:
   □ Build 2.5.0 deployed to staging environment
   □ Database seeded with test data
   □ Payment gateway sandbox configured
   □ Smoke test passed (critical paths work)

✅ Documentation:
   □ 50 test cases written và reviewed
   □ Test plan approved by Test Manager
   □ Requirements clarified (no open questions)

✅ Resources:
   □ 3 testers available full-time
   □ Test devices ready (2 Android, 2 iOS)
   □ Jira access granted to all testers

✅ Prerequisites:
   □ Unit testing completed (>80% coverage)
   □ Integration testing passed
   □ No Critical bugs in previous build
```

### 3.2. Exit Criteria

```
╔═══════════════════════════════════════════════════════════════╗
║                      EXIT CRITERIA                            ║
╠═══════════════════════════════════════════════════════════════╣
║                                                               ║
║  📖 ĐỊNH NGHĨA:                                               ║
║     Conditions để STOP testing và consider testing DONE      ║
║                                                               ║
║  🎯 MỤC ĐÍCH:                                                 ║
║     • Define "Done"                                          ║
║     • Prevent over-testing                                   ║
║     • Quality gates                                          ║
║                                                               ║
║  ✅ TYPICAL EXIT CRITERIA:                                    ║
║                                                               ║
║     📊 COVERAGE:                                              ║
║     • X% test cases executed                                 ║
║     • Y% requirements covered                                ║
║     • Code coverage target met                               ║
║                                                               ║
║     🐛 DEFECTS:                                               ║
║     • No Critical bugs open                                  ║
║     • <N High bugs open                                      ║
║     • Medium/Low bugs reviewed (defer acceptable)            ║
║                                                               ║
║     ✅ PASS RATE:                                             ║
║     • >X% test cases passed                                  ║
║     • All critical scenarios passed                          ║
║                                                               ║
║     📈 NON-FUNCTIONAL:                                        ║
║     • Performance benchmarks met                             ║
║     • Security scan passed                                   ║
║     • Accessibility standards met                            ║
║                                                               ║
║     📝 DOCUMENTATION:                                         ║
║     • Test execution report completed                        ║
║     • Defect report submitted                                ║
║     • Sign-off from stakeholders                             ║
║                                                               ║
╚═══════════════════════════════════════════════════════════════╝
```

**Ví dụ Exit Criteria:**
```
EXIT CRITERIA - SYSTEM TESTING

✅ Test Execution:
   □ 100% planned test cases executed
   □ 95%+ test cases passed
   □ All failed tests analyzed (not environment issues)

✅ Defect Status:
   □ 0 Critical bugs open
   □ ≤2 High bugs open (evaluated and acceptable)
   □ Medium/Low bugs reviewed by PO (defer OK)

✅ Coverage:
   □ 100% requirements covered
   □ All critical user flows tested
   □ Regression suite passed

✅ Non-Functional:
   □ Page load time <2 seconds (95th percentile)
   □ 1000 concurrent users supported
   □ Security scan: 0 Critical, 0 High vulnerabilities
   □ WCAG 2.1 AA compliance verified

✅ Documentation:
   □ Test execution report published
   □ Known issues documented
   □ Sign-off from Test Manager + PO
```

---

## 4. DEFINITION OF READY & DONE

### 4.1. Definition of Ready (DoR)

```
╔═══════════════════════════════════════════════════════════════╗
║               DEFINITION OF READY (DoR)                       ║
╠═══════════════════════════════════════════════════════════════╣
║                                                               ║
║  📖 ĐỊNH NGHĨA:                                               ║
║     Checklist cho user story/task SẴN SÀNG để bắt đầu work  ║
║                                                               ║
║  🎯 SCOPE:                                                    ║
║     Applied cho USER STORIES trước khi sprint planning       ║
║                                                               ║
║  ✅ TYPICAL DoR CRITERIA:                                     ║
║                                                               ║
║     □ User story clearly written (As a... I want... So that)║
║     □ Acceptance criteria defined (Given-When-Then)          ║
║     □ Dependencies identified                                ║
║     □ Estimated by team (story points)                       ║
║     □ Testable (can be verified)                             ║
║     □ Small enough (fits in sprint)                          ║
║     □ No blockers                                            ║
║                                                               ║
║  🚫 NOT READY = Don't pull into sprint                       ║
║                                                               ║
╚═══════════════════════════════════════════════════════════════╝
```

**Ví dụ DoR cho User Story:**
```
DEFINITION OF READY - USER STORY

Before pulling story into sprint, verify:

✅ Story Writing:
   □ Follows format: As a [role], I want [feature], So that [benefit]
   □ Meets INVEST criteria
   □ Business value clear

✅ Acceptance Criteria:
   □ 3-8 acceptance criteria defined
   □ Written in Given-When-Then format
   □ Cover happy path + edge cases
   □ Testable and verifiable

✅ Technical:
   □ No technical blockers
   □ API contracts defined (if needed)
   □ UI mockups available (if needed)
   □ Dependencies identified

✅ Team:
   □ Story discussed in refinement
   □ Questions answered
   □ Estimated (story points)
   □ Fits in sprint (not too big)

✅ Test:
   □ Testable (can write test cases)
   □ Test data requirements known
```

### 4.2. Definition of Done (DoD)

```
╔═══════════════════════════════════════════════════════════════╗
║                DEFINITION OF DONE (DoD)                       ║
╠═══════════════════════════════════════════════════════════════╣
║                                                               ║
║  📖 ĐỊNH NGHĨA:                                               ║
║     Checklist cho user story/task được coi là HOÀN THÀNH     ║
║                                                               ║
║  🎯 SCOPE:                                                    ║
║     Applied khi story development & testing hoàn tất         ║
║                                                               ║
║  ✅ TYPICAL DoD CRITERIA:                                     ║
║                                                               ║
║     💻 CODE:                                                  ║
║     □ Code written và peer reviewed                          ║
║     □ Unit tests written (>80% coverage)                     ║
║     □ Code merged to main branch                             ║
║                                                               ║
║     🧪 TESTING:                                               ║
║     □ All acceptance criteria tested và passed               ║
║     □ Integration tests passed                               ║
║     □ Regression tests passed                                ║
║     □ No Critical/High bugs                                  ║
║                                                               ║
║     📝 DOCUMENTATION:                                         ║
║     □ Code commented                                         ║
║     □ API docs updated (if applicable)                       ║
║     □ User docs updated                                      ║
║                                                               ║
║     ✅ DEPLOYMENT:                                            ║
║     □ Deployed to test/staging environment                   ║
║     □ Demo ready (can show to PO)                            ║
║     □ PO accepted (sign-off)                                 ║
║                                                               ║
╚═══════════════════════════════════════════════════════════════╝
```

**Ví dụ DoD cho User Story:**
```
DEFINITION OF DONE - USER STORY

Story is DONE when:

✅ Development:
   □ Code implemented
   □ Code reviewed (1+ approvals)
   □ Unit tests written (coverage >80%)
   □ No linting errors
   □ Merged to develop branch

✅ Testing:
   □ All acceptance criteria verified
   □ Manual testing completed
   □ Exploratory testing (1 session)
   □ Regression suite passed (automated)
   □ No Critical bugs
   □ No High bugs (or deferred with PO approval)

✅ Documentation:
   □ README updated (if needed)
   □ API docs updated (if applicable)
   □ Release notes entry created

✅ Deployment:
   □ Deployed to staging environment
   □ Smoke test passed on staging
   □ Demo to PO completed
   □ PO accepted (story marked as Done in Jira)

✅ Cleanup:
   □ Test data cleaned up (if needed)
   □ Feature flag configured (if applicable)
```

### 4.3. DoR vs DoD vs Entry/Exit Criteria

| Aspect | Entry Criteria | DoR | DoD | Exit Criteria |
|--------|---------------|-----|-----|---------------|
| **Applied to** | Test phase | User Story | User Story | Test phase |
| **Scope** | Testing activity | Sprint planning | Story completion | Testing completion |
| **Checked by** | Test Manager | PO + Team | Dev + Tester + PO | Test Manager |
| **When** | Before testing starts | Before sprint | End of story | End of testing |
| **Purpose** | Ready to test | Ready to develop | Development done | Testing done |

---

## 5. TEST PYRAMID

### 5.1. Test Pyramid Concept

```
╔═══════════════════════════════════════════════════════════════╗
║                     TEST PYRAMID                              ║
╠═══════════════════════════════════════════════════════════════╣
║                                                               ║
║                      🔺                                        ║
║                     /  \                                       ║
║                    / UI \         ← FEW (Slow, Brittle)       ║
║                   /──────\                                     ║
║                  / API    \       ← MORE (Medium speed)       ║
║                 / Service  \                                   ║
║                /────────────\                                  ║
║               /   UNIT       \    ← MOST (Fast, Stable)       ║
║              /    TESTS       \                                ║
║             /──────────────────\                               ║
║                                                               ║
║  📖 CONCEPT:                                                  ║
║     Majority của tests nên ở level thấp (Unit)               ║
║     Ít tests ở level cao (UI)                                ║
║                                                               ║
║  🎯 RATIONALE:                                                ║
║     • Unit tests: FAST, stable, easy to maintain             ║
║     • UI tests: SLOW, brittle, expensive to maintain         ║
║                                                               ║
║  📊 TYPICAL RATIO:                                            ║
║     • 70% Unit tests                                         ║
║     • 20% Integration/API tests                              ║
║     • 10% UI/E2E tests                                       ║
║                                                               ║
╚═══════════════════════════════════════════════════════════════╝
```

### 5.2. Layers của Test Pyramid

**1. UNIT TESTS (Base - 70%)**
```
WHO: Developers
WHAT: Individual functions, classes, modules
TOOLS: JUnit, pytest, Jest
SPEED: Very Fast (milliseconds)
SCOPE: Narrow (isolated logic)

EXAMPLE:
✓ Test calculateDiscount(amount, percentage) function
✓ Test validateEmail(email) returns true/false
✓ Test UserService.createUser() with mock database
```

**2. INTEGRATION/API TESTS (Middle - 20%)**
```
WHO: Developers + QA
WHAT: Integration between components, API endpoints
TOOLS: Postman, Newman, RestAssured
SPEED: Medium (seconds)
SCOPE: Medium (multiple components)

EXAMPLE:
✓ Test POST /api/orders creates order in database
✓ Test payment service integrates with payment gateway
✓ Test frontend calls backend API correctly
```

**3. UI/E2E TESTS (Top - 10%)**
```
WHO: QA
WHAT: End-to-end user flows through UI
TOOLS: Selenium, Cypress, Playwright
SPEED: Slow (minutes)
SCOPE: Wide (entire system)

EXAMPLE:
✓ Test complete checkout flow (cart → payment → confirmation)
✓ Test user registration through web UI
✓ Test search → filter → add to cart flow
```

### 5.3. Ví Dụ: Test Pyramid cho Shopee

**Feature: Place Order**

```
           🔺 UI/E2E (10% - 5 tests)
          /────\
         / API  \  Integration (20% - 10 tests)
        /────────\
       /  UNIT    \ Unit (70% - 35 tests)
      /────────────\

TOTAL: 50 automated tests
```

**Unit Tests (35):**
- CalculateTotal(items, discount) → 5 tests
- ValidatePromoCode(code) → 8 tests
- CalculateShipping(weight, distance) → 6 tests
- FormatOrderNumber() → 3 tests
- ValidatePaymentDetails() → 7 tests
- etc. (35 total)

**Integration Tests (10):**
- POST /api/orders → Creates order in DB → 3 tests
- GET /api/promo-codes/:code → Returns valid code → 2 tests
- Payment service → Payment gateway integration → 3 tests
- Order service → Inventory service integration → 2 tests

**UI/E2E Tests (5):**
- Complete checkout flow (happy path)
- Checkout with promo code applied
- Checkout with insufficient stock
- Checkout with payment failure
- Checkout on mobile device

### 5.4. Anti-Pattern: Ice Cream Cone

```
╔═══════════════════════════════════════════════════════════════╗
║                ICE CREAM CONE (ANTI-PATTERN)                  ║
╠═══════════════════════════════════════════════════════════════╣
║                                                               ║
║               ┌──────────┐                                    ║
║               │  Manual  │  ← TOO MANY (Slow, Error-prone)   ║
║               │  Testing │                                    ║
║               └─────┬────┘                                    ║
║                     │                                         ║
║                 ┌───▼───┐                                     ║
║                 │  UI   │    ← TOO MANY (Automated but slow) ║
║                 │ Tests │                                     ║
║                 └───┬───┘                                     ║
║                  ┌──▼──┐                                      ║
║                  │ API │     ← Some                           ║
║                  └──┬──┘                                      ║
║                   ┌─▼─┐                                       ║
║                   │ U │      ← TOO FEW                        ║
║                   └───┘                                       ║
║                                                               ║
║  ❌ PROBLEMS:                                                 ║
║     • Slow feedback (manual + UI tests take hours)           ║
║     • High maintenance cost                                  ║
║     • Brittle (UI changes break tests)                       ║
║     • Low confidence (manual testing inconsistent)           ║
║                                                               ║
╚═══════════════════════════════════════════════════════════════╝
```

---

## 6. TESTING QUADRANTS

### 6.1. Agile Testing Quadrants

```
╔═══════════════════════════════════════════════════════════════╗
║              AGILE TESTING QUADRANTS                          ║
╠═══════════════════════════════════════════════════════════════╣
║                                                               ║
║                    Supporting the Team                        ║
║                            │                                  ║
║              Q2            │            Q1                    ║
║         ┌──────────────────┼──────────────────┐               ║
║         │  Functional      │  Technology      │               ║
║         │  - Manual        │  - Unit Tests    │               ║
║         │  - Story Tests   │  - Component     │               ║
║Business │  - Prototypes    │    Tests         │ Technology    ║
║ Facing  │  - Simulations   │  - TDD           │  Facing       ║
║         ├──────────────────┼──────────────────┤               ║
║         │  Critique        │  Critique        │               ║
║         │  - Exploratory   │  - Performance   │               ║
║         │  - Usability     │  - Load          │               ║
║         │  - UAT           │  - Security      │               ║
║              Q3            │            Q4                    ║
║                            │                                  ║
║                   Critique Product                            ║
║                                                               ║
╚═══════════════════════════════════════════════════════════════╝
```

### 6.2. Chi Tiết 4 Quadrants

**Q1: Technology-Facing, Support Development (Automated)**
```
🎯 PURPOSE: Support developers, prevent bugs
👥 WHO: Developers
🤖 AUTOMATION: Yes (mostly)

TESTS:
• Unit Tests (TDD)
• Component Tests
• API/Service Tests

EXAMPLE:
✓ Test calculateDiscount() function
✓ Test UserService with mocked database
✓ Test REST API endpoints

TOOLS: JUnit, pytest, Jest, Postman
```

**Q2: Business-Facing, Support Development (Manual + Automated)**
```
🎯 PURPOSE: Clarify requirements, guide development
👥 WHO: Testers, BA, PO
🤖 AUTOMATION: Partial

TESTS:
• Functional Tests
• Story Tests (ATDD)
• Prototypes
• Workflow Tests

EXAMPLE:
✓ Test user story acceptance criteria
✓ Verify checkout flow works end-to-end
✓ Test business rules (discounts, eligibility)

TOOLS: Cucumber, FitNesse, Manual testing
```

**Q3: Business-Facing, Critique Product (Manual)**
```
🎯 PURPOSE: Find issues that matter to users
👥 WHO: Testers, Users, BA
🤖 AUTOMATION: No (exploratory nature)

TESTS:
• Exploratory Testing
• Usability Testing
• UAT (User Acceptance)
• Alpha/Beta Testing

EXAMPLE:
✓ Exploratory session: "Find issues in payment flow"
✓ Usability: "Is checkout intuitive?"
✓ UAT: Business users verify features

TOOLS: Session-based testing, User feedback
```

**Q4: Technology-Facing, Critique Product (Automated + Tools)**
```
🎯 PURPOSE: Non-functional quality attributes
👥 WHO: Performance engineers, Security experts
🤖 AUTOMATION: Yes (tools)

TESTS:
• Performance Testing
• Load Testing
• Security Testing
• Scalability Testing
• Reliability Testing

EXAMPLE:
✓ Test app handles 10,000 concurrent users
✓ Test response time < 2 seconds
✓ Security scan (SQL injection, XSS)
✓ Stress test (find breaking point)

TOOLS: JMeter, LoadRunner, Burp Suite, OWASP ZAP
```

### 6.3. Sử Dụng Testing Quadrants

**Trong Sprint Planning:**
```
PO presents story → Team discusses:

Q1: "What unit tests do we need?" (Developers)
Q2: "How will we test acceptance criteria?" (Testers)
Q3: "Do we need exploratory session?" (Testers)
Q4: "Any performance concerns?" (Tech Lead)
```

**Trong Testing:**
```
Q1 & Q2: Support Development
→ Run during development
→ Immediate feedback

Q3 & Q4: Critique Product
→ Run after features built
→ Find issues before release
```

---

## 7. CÂU HỎI ÔN TẬP

### Câu 1 (K2)
Test planning activity nào xác định "what to test"?

A. Define test approach
B. Determine scope & objectives
C. Estimate effort
D. Identify resources

<details>
<summary>Đáp án</summary>

**B. Determine scope & objectives**

Giải thích: Scope defines WHAT features to test và what NOT to test.
</details>

---

### Câu 2 (K2)
Entry criteria define gì?

A. Conditions để stop testing
B. Conditions để start testing
C. Test objectives
D. Test deliverables

<details>
<summary>Đáp án</summary>

**B. Conditions để start testing**

Entry = conditions to START, Exit = conditions to STOP.
</details>

---

### Câu 3 (K2)
Definition of Ready applies cho gì?

A. Test plan
B. User story (before sprint)
C. User story (after development)
D. Test report

<details>
<summary>Đáp án</summary>

**B. User story (before sprint)**

DoR: Story sẵn sàng để pull into sprint.
DoD: Story hoàn thành.
</details>

---

### Câu 4 (K2)
Trong Test Pyramid, layer nào có MOST tests?

A. UI/E2E tests
B. Integration tests
C. Unit tests
D. Manual tests

<details>
<summary>Đáp án</summary>

**C. Unit tests**

Test Pyramid: 70% Unit, 20% Integration, 10% UI.
</details>

---

### Câu 5 (K2)
Tại sao Unit tests nên là majority?

A. Easiest to write
B. Fast, stable, easy to maintain
C. Cover all requirements
D. Don't need developers

<details>
<summary>Đáp án</summary>

**B. Fast, stable, easy to maintain**

Unit tests run in milliseconds, isolated, less brittle than UI tests.
</details>

---

### Câu 6 (K2)
Testing Quadrant Q1 (Technology-Facing, Support Development) bao gồm gì?

A. Exploratory testing
B. Unit tests, Component tests
C. UAT
D. Performance testing

<details>
<summary>Đáp án</summary>

**B. Unit tests, Component tests**

Q1: Technology-facing, support dev = Unit/Component tests (automated).
</details>

---

## 8. CHECKLIST TỰ ĐÁNH GIÁ

### Test Planning
- [ ] Hiểu 7 test planning activities
- [ ] Biết các components của test plan document
- [ ] Có thể viết test plan cho project nhỏ

### Entry & Exit Criteria
- [ ] Viết được entry criteria cho test phase
- [ ] Viết được exit criteria với measurable targets
- [ ] Phân biệt entry/exit criteria vs DoR/DoD

### DoR & DoD
- [ ] Viết được Definition of Ready cho user story
- [ ] Viết được Definition of Done cho user story
- [ ] Hiểu difference giữa DoR và DoD

### Test Pyramid
- [ ] Giải thích được Test Pyramid concept
- [ ] Biết typical ratio (70/20/10)
- [ ] Hiểu tại sao Unit tests should be majority
- [ ] Nhận biết anti-pattern (Ice Cream Cone)

### Testing Quadrants
- [ ] Hiểu 4 quadrants
- [ ] Biết loại tests thuộc quadrant nào
- [ ] Áp dụng quadrants trong planning

---

## TỔNG KẾT

```
╔═══════════════════════════════════════════════════════════════╗
║                    KEY TAKEAWAYS                              ║
╠═══════════════════════════════════════════════════════════════╣
║                                                               ║
║  1. Test Planning = Define objectives, approach, resources   ║
║                                                               ║
║  2. Test Plan Document:                                      ║
║     → 10 sections (Scope, Approach, Entry/Exit, etc.)        ║
║                                                               ║
║  3. Entry Criteria = Conditions to START testing             ║
║     Exit Criteria = Conditions to STOP testing               ║
║                                                               ║
║  4. DoR = Story ready for sprint                             ║
║     DoD = Story completed                                    ║
║                                                               ║
║  5. Test Pyramid:                                            ║
║     → 70% Unit (fast, stable)                                ║
║     → 20% Integration (medium)                               ║
║     → 10% UI (slow, brittle)                                 ║
║                                                               ║
║  6. Testing Quadrants:                                       ║
║     → Q1: Unit tests (tech, support)                         ║
║     → Q2: Story tests (business, support)                    ║
║     → Q3: Exploratory (business, critique)                   ║
║     → Q4: Performance (tech, critique)                       ║
║                                                               ║
╚═══════════════════════════════════════════════════════════════╝
```

---

**Tiếp theo**: [Module 6.2: Test Estimation](./module-6.2-test-estimation.md)

---

**Version**: 1.0.0
**Last Updated**: November 2025
