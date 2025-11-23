# MODULE 3.1: SDLC VÀ TESTING

**Thời lượng**: 3-4 giờ | **Độ khó**: ⭐⭐

---

## MỤC TIÊU HỌC TẬP (Learning Objectives)

Sau khi hoàn thành module này, bạn sẽ:

| ID | Mục tiêu | Level |
|----|----------|-------|
| FL-2.1.1 | Giải thích ảnh hưởng của SDLC đến testing | K2 |
| FL-2.1.2 | Nhận biết good testing practices áp dụng cho mọi SDLC | K1 |
| FL-2.1.3 | Nhớ lại các test-first approaches (TDD, ATDD, BDD) | K1 |
| FL-2.1.4 | Tóm tắt DevOps và testing trong CI/CD | K2 |
| FL-2.1.5 | Mô tả shift-left approach | K2 |
| FL-2.1.6 | Giải thích cách retrospectives cải thiện testing | K2 |

---

## 1. SOFTWARE DEVELOPMENT LIFE CYCLE (SDLC)

### 1.1. SDLC Là Gì?

> **SDLC (Software Development Life Cycle)** là quy trình mô tả các phases từ concept ban đầu đến khi software được deploy và maintain.

```
SDLC = Vòng đời phát triển phần mềm
       ↓
       Từ ý tưởng → Phân tích → Thiết kế → Code → Test → Deploy → Bảo trì
```

### 1.2. Các SDLC Models Phổ Biến

```
╔══════════════════════════════════════════════════════════════╗
║                    SDLC MODELS                               ║
╠══════════════════════════════════════════════════════════════╣
║                                                              ║
║  📊 SEQUENTIAL MODELS (Tuần tự):                             ║
║     • Waterfall                                              ║
║     • V-Model                                                ║
║                                                              ║
║  🔄 ITERATIVE/INCREMENTAL MODELS:                            ║
║     • Iterative                                              ║
║     • Incremental                                            ║
║     • Spiral                                                 ║
║                                                              ║
║  🚀 AGILE MODELS:                                            ║
║     • Scrum                                                  ║
║     • Kanban                                                 ║
║     • XP (Extreme Programming)                               ║
║                                                              ║
╚══════════════════════════════════════════════════════════════╝
```

---

## 2. SEQUENTIAL MODELS

### 2.1. Waterfall Model

```
╔═══════════════════════════════════════════════════════════════╗
║                    WATERFALL MODEL                            ║
╠═══════════════════════════════════════════════════════════════╣
║                                                               ║
║   ┌─────────────┐                                            ║
║   │ Requirements│                                            ║
║   └──────┬──────┘                                            ║
║          ▼                                                   ║
║   ┌─────────────┐                                            ║
║   │   Design    │                                            ║
║   └──────┬──────┘                                            ║
║          ▼                                                   ║
║   ┌─────────────┐                                            ║
║   │   Coding    │                                            ║
║   └──────┬──────┘                                            ║
║          ▼                                                   ║
║   ┌─────────────┐                                            ║
║   │   Testing   │  ← Testing là 1 phase RIÊNG BIỆT          ║
║   └──────┬──────┘                                            ║
║          ▼                                                   ║
║   ┌─────────────┐                                            ║
║   │ Deployment  │                                            ║
║   └─────────────┘                                            ║
║                                                               ║
║   ĐẶC ĐIỂM:                                                  ║
║   • Phases chạy tuần tự (không quay lại)                    ║
║   • Testing sau khi development xong                        ║
║   • Formal documentation ở mỗi phase                        ║
║   • Phù hợp: projects có requirements ổn định               ║
║                                                               ║
╚═══════════════════════════════════════════════════════════════╝
```

**Testing trong Waterfall:**
- Testing là phase riêng biệt, SAU development
- Testers tham gia MUỘn trong project
- Defects found late = expensive to fix
- Formal test documentation required

### 2.2. V-Model (Verification & Validation Model)

```
╔═══════════════════════════════════════════════════════════════╗
║                      V-MODEL                                  ║
╠═══════════════════════════════════════════════════════════════╣
║                                                               ║
║  Requirements ────────────────────────► Acceptance Testing   ║
║       │                                        ▲              ║
║       ▼                                        │              ║
║  System Design ───────────────────────► System Testing       ║
║       │                                        ▲              ║
║       ▼                                        │              ║
║  Architecture ────────────────────► Integration Testing      ║
║       │                                        ▲              ║
║       ▼                                        │              ║
║  Module Design ──────────────────────► Unit Testing          ║
║       │                                        ▲              ║
║       ▼                                        │              ║
║       └───────────── CODING ───────────────────┘              ║
║                                                               ║
║  ĐẶC ĐIỂM:                                                   ║
║  • Mỗi dev phase có test phase tương ứng                    ║
║  • Test planning bắt đầu SỚM (parallel với dev phase)       ║
║  • Left side: Development, Right side: Testing               ║
║  • Verification (build right) & Validation (build right thing)║
║                                                               ║
╚═══════════════════════════════════════════════════════════════╝
```

**Testing trong V-Model:**

| Development Phase | Test Phase | Test Basis |
|------------------|------------|------------|
| Requirements | Acceptance Testing | Business requirements |
| System Design | System Testing | System specifications |
| Architecture | Integration Testing | Architecture design |
| Module Design | Unit Testing | Detailed design |

**Ví dụ V-Model cho Shopee:**

```
Requirements: "User can purchase products"
    └── Acceptance Test: Verify user can complete purchase

System Design: "Checkout flow with 5 steps"
    └── System Test: Test end-to-end checkout

Architecture: "Frontend ↔ API ↔ Database"
    └── Integration Test: Test API integrations

Module Design: "calculateTotal() function"
    └── Unit Test: Test calculation logic
```

---

## 3. ITERATIVE & INCREMENTAL MODELS

### 3.1. Iterative Model

```
╔═══════════════════════════════════════════════════════════════╗
║                    ITERATIVE MODEL                            ║
╠═══════════════════════════════════════════════════════════════╣
║                                                               ║
║         Iteration 1      Iteration 2      Iteration 3        ║
║         ┌──────┐         ┌──────┐         ┌──────┐           ║
║         │Plan  │         │Plan  │         │Plan  │           ║
║         │Design│   →     │Design│   →     │Design│           ║
║         │Build │         │Build │         │Build │           ║
║         │Test  │         │Test  │         │Test  │           ║
║         └──────┘         └──────┘         └──────┘           ║
║            │                │                │                ║
║            ▼                ▼                ▼                ║
║         Version 1  →    Version 2   →   Version 3            ║
║         (Basic)         (Enhanced)      (Complete)           ║
║                                                               ║
║  ĐẶC ĐIỂM:                                                   ║
║  • Phát triển qua nhiều iterations                          ║
║  • Mỗi iteration: Plan → Design → Build → Test               ║
║  • Product được REFINE qua mỗi iteration                    ║
║  • Early feedback từ users                                   ║
║                                                               ║
╚═══════════════════════════════════════════════════════════════╝
```

### 3.2. Incremental Model

```
╔═══════════════════════════════════════════════════════════════╗
║                   INCREMENTAL MODEL                           ║
╠═══════════════════════════════════════════════════════════════╣
║                                                               ║
║   Increment 1:  [  Login Module  ]                           ║
║                        ↓                                      ║
║   Increment 2:  [  Login  ][  Product Catalog  ]             ║
║                              ↓                                ║
║   Increment 3:  [Login][Catalog][  Shopping Cart  ]          ║
║                                      ↓                        ║
║   Increment 4:  [Login][Catalog][Cart][  Checkout  ]         ║
║                                             ↓                 ║
║   Final:        [  Complete E-commerce System  ]             ║
║                                                               ║
║  ĐẶC ĐIỂM:                                                   ║
║  • Deliver từng phần (increment) một                        ║
║  • Mỗi increment thêm NEW functionality                      ║
║  • Increments được INTEGRATED vào whole                      ║
║  • User có thể dùng early increments                        ║
║                                                               ║
╚═══════════════════════════════════════════════════════════════╝
```

### 3.3. Iterative vs Incremental

| Aspect | Iterative | Incremental |
|--------|-----------|-------------|
| **Focus** | Refine whole product | Add new features |
| **Delivery** | Enhanced versions | New increments |
| **Example** | v1.0 → v1.1 → v1.2 | Module A → A+B → A+B+C |
| **Risk** | Requirements unclear | Integration issues |

---

## 4. AGILE DEVELOPMENT

### 4.1. Agile Là Gì?

> **Agile** là tập hợp các methodology dựa trên iterative development, collaboration, và flexibility để respond to change.

**Agile Manifesto Values:**
```
╔═══════════════════════════════════════════════════════════════╗
║                    AGILE MANIFESTO                            ║
╠═══════════════════════════════════════════════════════════════╣
║                                                               ║
║  Individuals and interactions  OVER  Processes and tools     ║
║                                                               ║
║  Working software              OVER  Comprehensive docs      ║
║                                                               ║
║  Customer collaboration        OVER  Contract negotiation    ║
║                                                               ║
║  Responding to change          OVER  Following a plan        ║
║                                                               ║
║  (Items on the left are valued MORE, but items on the right  ║
║   still have value)                                           ║
║                                                               ║
╚═══════════════════════════════════════════════════════════════╝
```

### 4.2. Scrum Framework

```
╔═══════════════════════════════════════════════════════════════╗
║                      SCRUM FRAMEWORK                          ║
╠═══════════════════════════════════════════════════════════════╣
║                                                               ║
║   Product Backlog                     Sprint (2-4 weeks)     ║
║   ┌─────────────┐                    ┌───────────────────┐   ║
║   │ User Story 1│ ───┐               │ Daily Standup     │   ║
║   │ User Story 2│    │               │ ↓                 │   ║
║   │ User Story 3│    │  Sprint       │ Development       │   ║
║   │ User Story 4│ ───┼─ Backlog ───► │ ↓                 │   ║
║   │ User Story 5│    │               │ Testing           │   ║
║   │ ...         │ ───┘               │ ↓                 │   ║
║   └─────────────┘                    │ Sprint Review     │   ║
║                                      │ Sprint Retro      │   ║
║                                      └─────────┬─────────┘   ║
║                                                │              ║
║                                                ▼              ║
║                                    Potentially Shippable     ║
║                                       Increment              ║
║                                                               ║
║   ROLES:                                                      ║
║   • Product Owner: Owns backlog, priorities                   ║
║   • Scrum Master: Facilitates process                        ║
║   • Development Team: Cross-functional (incl. testers)       ║
║                                                               ║
╚═══════════════════════════════════════════════════════════════╝
```

### 4.3. Testing trong Agile

```
╔═══════════════════════════════════════════════════════════════╗
║                 TESTING TRONG AGILE                           ║
╠═══════════════════════════════════════════════════════════════╣
║                                                               ║
║  📋 ĐẶC ĐIỂM:                                                 ║
║                                                               ║
║  1. TESTING THROUGHOUT THE SPRINT                            ║
║     → Không có separate test phase                           ║
║     → Test ngay khi code ready                               ║
║                                                               ║
║  2. WHOLE TEAM APPROACH                                       ║
║     → Testers là part of dev team                            ║
║     → Everyone responsible for quality                       ║
║                                                               ║
║  3. CONTINUOUS TESTING                                        ║
║     → Automated tests run frequently                         ║
║     → Fast feedback                                          ║
║                                                               ║
║  4. TEST AUTOMATION EMPHASIZED                                ║
║     → Unit tests (developers)                                ║
║     → Integration tests                                       ║
║     → UI automation                                          ║
║                                                               ║
║  5. LIGHTWEIGHT DOCUMENTATION                                 ║
║     → Focus on working software                              ║
║     → User stories với acceptance criteria                   ║
║                                                               ║
╚═══════════════════════════════════════════════════════════════╝
```

---

## 5. TESTING TRONG DIFFERENT SDLC MODELS

### 5.1. So Sánh Testing Approaches

| Aspect | Waterfall | V-Model | Agile |
|--------|-----------|---------|-------|
| **Khi nào test?** | Sau dev phase | Parallel với dev | Throughout sprint |
| **Test planning** | Upfront | Early | Just-in-time |
| **Documentation** | Formal, detailed | Formal | Lightweight |
| **Test automation** | Optional | Optional | Essential |
| **Feedback loop** | Long | Medium | Short |
| **Change handling** | Difficult | Difficult | Easy |
| **Tester role** | Separate team | Separate team | Part of team |

### 5.2. Good Testing Practices (Áp dụng cho MỌI SDLC)

```
╔═══════════════════════════════════════════════════════════════╗
║            GOOD TESTING PRACTICES FOR ALL SDLCs               ║
╠═══════════════════════════════════════════════════════════════╣
║                                                               ║
║  ✅ 1. EARLY TESTER INVOLVEMENT                               ║
║        → Testers tham gia từ requirements phase              ║
║        → Review requirements, designs                        ║
║                                                               ║
║  ✅ 2. TEST BASIS DEFINED                                     ║
║        → Mỗi test level có test basis rõ ràng               ║
║        → Requirements, designs, code                         ║
║                                                               ║
║  ✅ 3. TEST ANALYSIS & DESIGN EARLY                          ║
║        → Design test cases parallel với dev                  ║
║        → Identify test data needs                            ║
║                                                               ║
║  ✅ 4. TEST ENVIRONMENT READY                                 ║
║        → Environment setup trước khi test                    ║
║        → Test data prepared                                   ║
║                                                               ║
║  ✅ 5. TEST ACTIVITIES ALIGNED WITH DEV                       ║
║        → Testing corresponding to dev phase                  ║
║        → Integration points defined                          ║
║                                                               ║
║  ✅ 6. DIFFERENT TEST LEVELS                                  ║
║        → Component, Integration, System, Acceptance          ║
║        → Each level has specific objectives                  ║
║                                                               ║
╚═══════════════════════════════════════════════════════════════╝
```

---

## 6. TEST-FIRST APPROACHES

### 6.1. Test-Driven Development (TDD)

```
╔═══════════════════════════════════════════════════════════════╗
║              TEST-DRIVEN DEVELOPMENT (TDD)                    ║
╠═══════════════════════════════════════════════════════════════╣
║                                                               ║
║                    RED-GREEN-REFACTOR CYCLE                   ║
║                                                               ║
║                        ┌─────────┐                            ║
║                        │  RED    │                            ║
║                   ┌────│ Write   │────┐                       ║
║                   │    │ Failing │    │                       ║
║                   │    │  Test   │    │                       ║
║                   │    └─────────┘    │                       ║
║                   │                   │                       ║
║                   ▼                   │                       ║
║            ┌──────────┐               │                       ║
║            │ REFACTOR │               │                       ║
║            │ Improve  │               │                       ║
║            │  Code    │               │                       ║
║            └────┬─────┘               │                       ║
║                 │                     │                       ║
║                 │    ┌─────────┐      │                       ║
║                 └────│  GREEN  │──────┘                       ║
║                      │ Write   │                              ║
║                      │Minimal  │                              ║
║                      │Code to  │                              ║
║                      │  Pass   │                              ║
║                      └─────────┘                              ║
║                                                               ║
║  PROCESS:                                                     ║
║  1. RED: Write test that FAILS (no code yet)                 ║
║  2. GREEN: Write MINIMAL code to make test pass              ║
║  3. REFACTOR: Improve code while keeping tests passing       ║
║  4. Repeat                                                    ║
║                                                               ║
╚═══════════════════════════════════════════════════════════════╝
```

**Ví dụ TDD:**

```javascript
// Step 1 - RED: Write failing test
test('calculateDiscount returns 10% for orders over 1000000', () => {
  expect(calculateDiscount(1500000)).toBe(150000);
});
// TEST FAILS - function doesn't exist yet

// Step 2 - GREEN: Write minimal code
function calculateDiscount(orderAmount) {
  if (orderAmount > 1000000) {
    return orderAmount * 0.1;
  }
  return 0;
}
// TEST PASSES

// Step 3 - REFACTOR: Improve code
const DISCOUNT_THRESHOLD = 1000000;
const DISCOUNT_RATE = 0.1;

function calculateDiscount(orderAmount) {
  return orderAmount > DISCOUNT_THRESHOLD
    ? orderAmount * DISCOUNT_RATE
    : 0;
}
// TEST STILL PASSES
```

### 6.2. Acceptance Test-Driven Development (ATDD)

```
╔═══════════════════════════════════════════════════════════════╗
║       ACCEPTANCE TEST-DRIVEN DEVELOPMENT (ATDD)               ║
╠═══════════════════════════════════════════════════════════════╣
║                                                               ║
║  PROCESS:                                                     ║
║                                                               ║
║  1. DISCUSS                                                   ║
║     BA + Dev + Tester discuss user story                     ║
║     Define acceptance criteria together                      ║
║            ↓                                                  ║
║  2. DISTILL                                                   ║
║     Write acceptance tests from criteria                     ║
║     Format: Given-When-Then                                  ║
║            ↓                                                  ║
║  3. DEVELOP                                                   ║
║     Developers implement to pass acceptance tests            ║
║            ↓                                                  ║
║  4. DEMO                                                      ║
║     Show working feature with passing tests                  ║
║                                                               ║
║  KEY POINT:                                                   ║
║  → Acceptance tests defined BEFORE development               ║
║  → Tests become executable specifications                    ║
║                                                               ║
╚═══════════════════════════════════════════════════════════════╝
```

### 6.3. Behavior-Driven Development (BDD)

```
╔═══════════════════════════════════════════════════════════════╗
║          BEHAVIOR-DRIVEN DEVELOPMENT (BDD)                    ║
╠═══════════════════════════════════════════════════════════════╣
║                                                               ║
║  BDD = TDD + Better communication                            ║
║                                                               ║
║  FORMAT: GIVEN-WHEN-THEN (Gherkin syntax)                    ║
║                                                               ║
║  ┌─────────────────────────────────────────────────────────┐ ║
║  │ Feature: User Login                                      │ ║
║  │                                                          │ ║
║  │ Scenario: Successful login with valid credentials        │ ║
║  │                                                          │ ║
║  │   Given user is on login page                           │ ║
║  │   And user has valid account                            │ ║
║  │   When user enters email "test@example.com"             │ ║
║  │   And user enters password "Pass123!"                   │ ║
║  │   And user clicks Login button                          │ ║
║  │   Then user is redirected to dashboard                  │ ║
║  │   And welcome message shows "Welcome, Test User"        │ ║
║  │                                                          │ ║
║  │ Scenario: Failed login with wrong password               │ ║
║  │                                                          │ ║
║  │   Given user is on login page                           │ ║
║  │   When user enters email "test@example.com"             │ ║
║  │   And user enters password "wrongpassword"              │ ║
║  │   And user clicks Login button                          │ ║
║  │   Then error message shows "Invalid credentials"        │ ║
║  │   And user remains on login page                        │ ║
║  └─────────────────────────────────────────────────────────┘ ║
║                                                               ║
║  TOOLS: Cucumber, SpecFlow, Behave                           ║
║                                                               ║
╚═══════════════════════════════════════════════════════════════╝
```

### 6.4. So Sánh TDD, ATDD, BDD

| Aspect | TDD | ATDD | BDD |
|--------|-----|------|-----|
| **Focus** | Unit level | Acceptance level | Behavior/Scenarios |
| **Who writes?** | Developers | Team (BA+Dev+Test) | Team |
| **Language** | Code | Natural/Code | Gherkin (Given-When-Then) |
| **Scope** | Functions, methods | User stories | Features, scenarios |
| **Example** | `assertEquals(5, add(2,3))` | "Order total equals sum" | "Given cart has items..." |

---

## 7. DEVOPS VÀ CI/CD

### 7.1. DevOps Là Gì?

> **DevOps** = Development + Operations. Là approach để tăng collaboration giữa dev và ops teams, automate processes, enable continuous delivery.

```
╔═══════════════════════════════════════════════════════════════╗
║                     DEVOPS PIPELINE                           ║
╠═══════════════════════════════════════════════════════════════╣
║                                                               ║
║   DEVELOPMENT              OPERATIONS                         ║
║   ───────────              ──────────                         ║
║                                                               ║
║   Plan → Code → Build → Test → Release → Deploy → Monitor    ║
║     │      │      │       │        │        │         │       ║
║     └──────┴──────┴───────┴────────┴────────┴─────────┘       ║
║                           │                                   ║
║                    CONTINUOUS FEEDBACK                        ║
║                                                               ║
║   ┌─────────────────────────────────────────────────────────┐ ║
║   │                                                         │ ║
║   │   CI (Continuous Integration)                           │ ║
║   │   ──────────────────────────                            │ ║
║   │   • Developers merge code frequently                    │ ║
║   │   • Automated build triggered                           │ ║
║   │   • Automated tests run                                 │ ║
║   │   • Fast feedback on integration issues                 │ ║
║   │                                                         │ ║
║   │   CD (Continuous Delivery/Deployment)                   │ ║
║   │   ───────────────────────────────────                   │ ║
║   │   • Code always in deployable state                     │ ║
║   │   • Automated deployment to staging                     │ ║
║   │   • One-click (or automatic) deploy to production       │ ║
║   │                                                         │ ║
║   └─────────────────────────────────────────────────────────┘ ║
║                                                               ║
╚═══════════════════════════════════════════════════════════════╝
```

### 7.2. Testing trong CI/CD Pipeline

```
CI/CD PIPELINE VỚI TESTING
═══════════════════════════════════════════════════════════════

       Developer                    CI Server              Production
       commits code                 (Jenkins, GitLab)      Server
           │                              │                    │
           ▼                              │                    │
    ┌────────────┐                        │                    │
    │   COMMIT   │────────────────────────┤                    │
    └────────────┘                        │                    │
                                          ▼                    │
                                   ┌────────────┐              │
                                   │   BUILD    │              │
                                   └─────┬──────┘              │
                                         │                     │
                                         ▼                     │
                              ┌─────────────────────┐          │
                              │   UNIT TESTS        │          │
                              │   (Fast, automated) │          │
                              └─────────┬───────────┘          │
                                        │ Pass?                │
                                        ▼                      │
                              ┌─────────────────────┐          │
                              │ INTEGRATION TESTS   │          │
                              │ (API, Database)     │          │
                              └─────────┬───────────┘          │
                                        │ Pass?                │
                                        ▼                      │
                              ┌─────────────────────┐          │
                              │  DEPLOY TO STAGING  │          │
                              └─────────┬───────────┘          │
                                        │                      │
                                        ▼                      │
                              ┌─────────────────────┐          │
                              │   E2E TESTS         │          │
                              │   UI Automation     │          │
                              └─────────┬───────────┘          │
                                        │ Pass?                │
                                        ▼                      │
                              ┌─────────────────────┐          │
                              │  DEPLOY TO PROD     │──────────┤
                              └─────────────────────┘          │
                                                               │
                                                    ┌──────────▼──────┐
                                                    │   MONITORING    │
                                                    │   & ALERTS      │
                                                    └─────────────────┘
```

### 7.3. Testing Benefits trong DevOps

```
╔═══════════════════════════════════════════════════════════════╗
║           TESTING BENEFITS TRONG DEVOPS                       ║
╠═══════════════════════════════════════════════════════════════╣
║                                                               ║
║  ✅ FAST FEEDBACK                                             ║
║     → Developers biết ngay khi code break tests              ║
║     → Minutes, not days                                       ║
║                                                               ║
║  ✅ CONTINUOUS TESTING                                        ║
║     → Tests run on every commit                              ║
║     → No manual trigger needed                               ║
║                                                               ║
║  ✅ REGRESSION DETECTION                                      ║
║     → Automated tests catch regressions early                ║
║     → Before code reaches production                         ║
║                                                               ║
║  ✅ QUALITY GATES                                             ║
║     → Code cannot proceed if tests fail                      ║
║     → Enforced quality standards                             ║
║                                                               ║
║  ✅ CONFIDENCE TO DEPLOY                                      ║
║     → Passing tests = confidence to release                  ║
║     → More frequent releases possible                        ║
║                                                               ║
╚═══════════════════════════════════════════════════════════════╝
```

---

## 8. SHIFT-LEFT APPROACH

### 8.1. Shift-Left Là Gì?

> **Shift-Left** = Move testing activities EARLIER in the SDLC (to the LEFT on timeline).

```
TRADITIONAL APPROACH:
═══════════════════════════════════════════════════════════════
Requirements → Design → Development → TESTING → Release
                                         ↑
                                    Testing starts
                                    HERE (late)

SHIFT-LEFT APPROACH:
═══════════════════════════════════════════════════════════════
Requirements → Design → Development → Testing → Release
      ↑            ↑           ↑
   Testing     Testing     Testing
   starts      continues   continues
   HERE        HERE        HERE
   (early!)
```

### 8.2. Shift-Left Activities

```
╔═══════════════════════════════════════════════════════════════╗
║               SHIFT-LEFT TESTING ACTIVITIES                   ║
╠═══════════════════════════════════════════════════════════════╣
║                                                               ║
║  📋 REQUIREMENTS PHASE:                                       ║
║     • Review requirements for testability                    ║
║     • Write acceptance criteria                              ║
║     • Identify test scenarios early                          ║
║     • Find ambiguities và gaps                              ║
║                                                               ║
║  🎨 DESIGN PHASE:                                             ║
║     • Review designs for testability                         ║
║     • Plan test approach                                     ║
║     • Design test cases                                      ║
║     • Identify test data requirements                        ║
║                                                               ║
║  💻 DEVELOPMENT PHASE:                                        ║
║     • TDD - Write tests before code                          ║
║     • Code reviews                                           ║
║     • Static analysis                                        ║
║     • Unit testing by developers                             ║
║                                                               ║
╚═══════════════════════════════════════════════════════════════╝
```

### 8.3. Benefits của Shift-Left

```
     Chi phí sửa defect
           ▲
           │
     100x  │                                    ╱
           │                                  ╱
           │                                ╱
      50x  │                              ╱
           │                            ╱
           │                          ╱
      10x  │                        ╱
           │                      ╱
       1x  │  ●─────────────────╱
           │
           └──────────────────────────────────────►
              Req    Design    Dev    Test   Prod

     SHIFT-LEFT = Find defects khi chi phí sửa còn THẤP!
```

---

## 9. RETROSPECTIVES

### 9.1. Retrospective Là Gì?

> **Retrospective** = Meeting cuối sprint/phase để review what went well, what went wrong, và how to improve.

```
╔═══════════════════════════════════════════════════════════════╗
║                     RETROSPECTIVE                             ║
╠═══════════════════════════════════════════════════════════════╣
║                                                               ║
║   3 KEY QUESTIONS:                                            ║
║                                                               ║
║   😊 What went WELL?                                          ║
║      → Continue doing                                         ║
║                                                               ║
║   😔 What went WRONG?                                         ║
║      → Stop doing or fix                                      ║
║                                                               ║
║   🔧 What can we IMPROVE?                                     ║
║      → Action items for next sprint                          ║
║                                                               ║
╚═══════════════════════════════════════════════════════════════╝
```

### 9.2. Testing Improvements từ Retrospectives

```
VÍ DỤ RETROSPECTIVE - Sprint 5

WHAT WENT WELL:
✅ Automated tests caught 3 regressions before release
✅ New test data setup process saved 4 hours
✅ Pair testing with developers improved communication

WHAT WENT WRONG:
❌ Found critical bug in production (missed in testing)
❌ Test environment was unstable, blocked testing for 2 days
❌ Test cases took too long to execute (8 hours)

IMPROVEMENTS FOR NEXT SPRINT:
┌─────────────────────────────────────────────────────────────┐
│ Issue              │ Action                │ Owner   │ Done │
├────────────────────┼───────────────────────┼─────────┼──────┤
│ Missed critical    │ Add security testing  │ Tester  │ □    │
│ bug                │ to checklist          │         │      │
├────────────────────┼───────────────────────┼─────────┼──────┤
│ Unstable test      │ DevOps to fix         │ DevOps  │ □    │
│ environment        │ environment issues    │         │      │
├────────────────────┼───────────────────────┼─────────┼──────┤
│ Long test          │ Parallelize tests,    │ Team    │ □    │
│ execution          │ optimize slow tests   │         │      │
└─────────────────────────────────────────────────────────────┘
```

---

## 10. CÂU HỎI ÔN TẬP

### Câu 1 (K2)
SDLC model nào có testing phase RIÊNG BIỆT sau development phase?

A. Agile
B. Waterfall
C. Scrum
D. Iterative

<details>
<summary>Đáp án</summary>

**B. Waterfall**

Giải thích: Waterfall có các phases tuần tự, testing là phase riêng sau development. Agile test throughout sprint.
</details>

---

### Câu 2 (K1)
TDD là viết tắt của?

A. Test Document Design
B. Test-Driven Development
C. Testing During Development
D. Technical Design Document

<details>
<summary>Đáp án</summary>

**B. Test-Driven Development**

Giải thích: TDD = Test-Driven Development, write test BEFORE code.
</details>

---

### Câu 3 (K2)
Trong V-Model, unit testing tương ứng với development phase nào?

A. Requirements
B. System Design
C. Module Design
D. Architecture

<details>
<summary>Đáp án</summary>

**C. Module Design**

Giải thích: V-Model matching: Module Design ↔ Unit Testing, Architecture ↔ Integration, System Design ↔ System Testing.
</details>

---

### Câu 4 (K2)
Lợi ích chính của Shift-Left testing là gì?

A. Giảm số lượng tests
B. Tìm defects sớm khi chi phí sửa còn thấp
C. Không cần automation
D. Testers không cần tham gia requirements

<details>
<summary>Đáp án</summary>

**B. Tìm defects sớm khi chi phí sửa còn thấp**

Giải thích: Shift-Left = Move testing earlier → Find defects when fix cost is low.
</details>

---

### Câu 5 (K1)
BDD sử dụng format nào để viết scenarios?

A. If-Then-Else
B. Given-When-Then
C. Input-Process-Output
D. Setup-Execute-Verify

<details>
<summary>Đáp án</summary>

**B. Given-When-Then**

Giải thích: BDD dùng Gherkin syntax: Given (context), When (action), Then (outcome).
</details>

---

## 11. CHECKLIST TỰ ĐÁNH GIÁ

Đánh dấu ✅ khi bạn đã hiểu:

- [ ] Giải thích được các SDLC models (Waterfall, V-Model, Agile)
- [ ] So sánh được testing trong các SDLC khác nhau
- [ ] Nêu được good testing practices áp dụng cho mọi SDLC
- [ ] Hiểu được TDD, ATDD, BDD và sự khác biệt
- [ ] Giải thích được DevOps và CI/CD
- [ ] Mô tả được Shift-Left approach và benefits
- [ ] Hiểu được mục đích của retrospectives

---

**Tiếp theo**: [Module 3.2: Test Levels](./module-3.2-test-levels.md)

---

**Version**: 1.0.0
**Last Updated**: November 2025
