# ROADMAP CHI TIẾT - GIÁO TRÌNH ISTQB FOUNDATION LEVEL

**Version**: 1.0.0
**Ngày tạo**: November 2025
**Dành cho**: Người mới bắt đầu học Software Testing

---

## TỔNG QUAN HOÀN CHỈNH

### 📚 GIÁO TRÌNH ĐẦY ĐỦ - TỰ CHECK TIẾN ĐỘ KHI HỌC

> **Hướng dẫn**: Đánh dấu ✅ vào checkbox `[ ]` khi bạn hoàn thành mỗi module/bài tập. Đổi `[ ]` thành `[x]` để đánh dấu hoàn thành.

#### Phần Cơ Bản
- [ ] 00-gioi-thieu.md - Giới thiệu đầy đủ về giáo trình
- [ ] 00-tu-vung-song-ngu.md - 200+ thuật ngữ Anh-Việt

#### Giai đoạn 1: Nền Tảng
- [ ] module-1.1-testing-la-gi.md
- [ ] module-1.2-co-ban-ve-testing.md
- [ ] module-1.3-quy-trinh-testing.md
- [ ] module-1.4-cong-cu-testing.md
- [ ] bai-tap-giai-doan-1.md

#### Giai đoạn 2: Static Testing
- [ ] module-2.1-static-testing-co-ban.md
- [ ] module-2.2-review-process.md
- [ ] bai-tap-giai-doan-2.md

#### Giai đoạn 3: Testing trong SDLC
- [ ] module-3.1-sdlc-va-testing.md
- [ ] module-3.2-test-levels.md
- [ ] module-3.3-test-types.md
- [ ] bai-tap-giai-doan-3.md

#### Giai đoạn 4: Black-Box Techniques ⭐⭐⭐ QUAN TRỌNG
- [ ] module-4.1-test-techniques-overview.md
- [ ] module-4.2-equivalence-partitioning.md
- [ ] module-4.3-boundary-value-analysis.md
- [ ] module-4.4-decision-table-testing.md
- [ ] module-4.5-state-transition-testing.md
- [ ] bai-tap-giai-doan-4.md (50 MCQs + 8 bài tập thực hành)

#### Giai đoạn 5: Other Techniques ⭐⭐
- [ ] module-5.1-white-box-testing.md (Statement & Branch Coverage)
- [ ] module-5.2-experience-based-techniques.md (Error Guessing, Exploratory, Checklist)
- [ ] module-5.3-collaboration-based-approaches.md (User Stories, INVEST, ATDD)
- [ ] bai-tap-giai-doan-5.md (30 MCQs + 5 bài tập thực hành)

#### Giai đoạn 6: Test Management - Part 1 ⭐⭐⭐
- [ ] module-6.1-test-planning.md (Entry/Exit, DoR/DoD, Test Pyramid, Quadrants)
- [ ] module-6.2-test-estimation.md (Ratios, Extrapolation, Planning Poker, Three-Point)
- [ ] module-6.3-test-case-prioritization.md (Risk-based, Coverage-based, Requirements-based)
- [ ] module-6.4-risk-management.md (Project vs Product risks, Risk analysis & control)
- [ ] bai-tap-giai-doan-6.md (35 MCQs + 6 bài tập thực hành)

#### Giai đoạn 7: Test Management - Part 2 ⭐⭐⭐
- [ ] module-7.1-test-monitoring-control.md (Test metrics, Monitoring techniques, Control actions)
- [ ] module-7.2-test-reporting.md (Progress vs Completion reports, Executive summary, Audiences)
- [ ] module-7.3-configuration-management.md (Baselines, Versions, Traceability, Git workflow)
- [ ] module-7.4-defect-management.md (Defect lifecycle, Severity vs Priority, RCA, Triage)
- [ ] bai-tap-giai-doan-7.md (30 MCQs + 4 bài tập thực hành chi tiết)

#### Giai đoạn 8: Thực hành Tổng hợp ⭐⭐⭐⭐ CỰC KỲ QUAN TRỌNG
- [ ] HUONG-DAN-THUC-HANH.md (Comprehensive guide, Weekly roadmap, Self-assessment)
- [ ] project-1-ecommerce-testing.md (ShopVN - 300+ test cases, All Black-box techniques)
- [ ] project-2-mobile-banking-testing.md (PayVN - Security, Performance, Compliance)
- [ ] project-3-education-platform-testing.md (LearnVN - Multi-role, Video streaming, Usability)

---

## 📋 CHI TIẾT NỘI DUNG (Đã hoàn thành 100%)

### GIAI ĐOẠN 4: Black-Box Techniques (2 tuần)

#### Module 2.1: Static Testing Cơ Bản
**Thời lượng**: 2-3 giờ | **Độ khó**: ⭐⭐

**Nội dung chính**:
```
1. STATIC TESTING LÀ GÌ?
   1.1. Định nghĩa
   1.2. Static vs Dynamic Testing
   1.3. Work products có thể static test

2. GIÁ TRỊ CỦA STATIC TESTING
   2.1. Find defects EARLY
   2.2. Chi phí thấp hơn
   2.3. Improve quality của work products
   2.4. Find defects mà dynamic testing khó tìm

3. STATIC TESTING TECHNIQUES
   3.1. Reviews (Manual)
   3.2. Static Analysis (Tool-based)

4. WORK PRODUCTS EXAMINABLE
   4.1. Requirements documents
   4.2. Design specifications
   4.3. Code (source code)
   4.4. Test plans và test cases
   4.5. User manuals
   4.6. Contracts và project plans

5. DEFECTS FOUND BY STATIC TESTING
   5.1. Requirement defects
      - Ambiguity, inconsistency
      - Missing requirements
      - Incorrect logic
   5.2. Design defects
      - Inefficient algorithms
      - Missing error handling
   5.3. Code defects
      - Code standards violations
      - Security vulnerabilities
      - Maintainability issues
   5.4. Test defects
      - Incorrect test logic
      - Missing test coverage
```

**Ví dụ thực tế**:
- Static review requirement document của e-commerce
- Static analysis code với SonarQube
- Comparison table: Defects found by Static vs Dynamic

**Practice questions**: 10 câu

---

#### Module 2.2: Review Process
**Thời lượng**: 3-4 giờ | **Độ khó**: ⭐⭐

**Nội dung chính**:
```
1. REVIEW PROCESS ACTIVITIES
   1.1. Planning
      - Define scope, objectives
      - Select review type
      - Assign roles
   1.2. Review Initiation
      - Distribute work products
      - Explain objectives
   1.3. Individual Review
      - Each reviewer examines independently
      - Note potential defects
   1.4. Communication & Analysis
      - Review meeting (optional)
      - Discuss findings
      - Make decisions
   1.5. Fixing & Reporting
      - Author fixes defects
      - Report results

2. ROLES IN REVIEWS
   2.1. Manager (initiates, assigns resources)
   2.2. Author (creator of work product)
   2.3. Moderator/Facilitator (leads meeting)
   2.4. Scribe (records defects/decisions)
   2.5. Reviewer (examines work product)
   2.6. Review Leader (organizes review)

3. REVIEW TYPES
   3.1. Informal Review
      - No formal process
      - Pair review, buddy check
      - Example: Developer asks colleague to check code

   3.2. Walkthrough
      - Author leads
      - Scenarios, dry runs
      - Example: Designer walks through UX flow

   3.3. Technical Review
      - Technical experts
      - Focus on technical quality
      - Example: Architecture review

   3.4. Inspection
      - Most formal
      - Defined process, rules
      - Metrics collected
      - Example: Formal code inspection

4. SUCCESS FACTORS
   4.1. Management support
   4.2. Clear objectives
   4.3. Right people involved
   4.4. Adequate preparation time
   4.5. Focus on defects, not people
   4.6. Constructive atmosphere
```

**Case Study**: Conduct formal inspection for banking app requirement document

**Practice questions**: 10 câu

---

#### Bài tập Giai đoạn 2
**Exercises**:
1. Identify static testing opportunities trong project lifecycle
2. Choose appropriate review type cho scenarios
3. Conduct mock walkthrough meeting
4. Write review checklist cho requirement document

**Multiple Choice**: 20 câu

---

### GIAI ĐOẠN 3: Testing trong SDLC (1 tuần)

#### Module 3.1: SDLC và Testing
**Thời lượng**: 3-4 giờ | **Độ khó**: ⭐⭐

**Nội dung chính**:
```
1. SDLC MODELS
   1.1. Sequential Models
      - Waterfall: Phases tuần tự
      - V-Model: Testing phases tương ứng dev phases

   1.2. Iterative Models
      - Incremental: Deliver theo increments
      - Iterative: Refine through iterations

   1.3. Agile
      - Sprints, user stories
      - Continuous testing
      - Scrum, Kanban

2. TESTING IN DIFFERENT SDLC
   2.1. Waterfall Testing
      - Testing phase riêng biệt
      - Formal documentation
      - Sequential handoffs

   2.2. Agile Testing
      - Testing throughout sprint
      - Whole team approach
      - Test automation emphasized
      - BDD, ATDD, TDD

3. GOOD TESTING PRACTICES
   3.1. Early involvement of testers
   3.2. Test basis review
   3.3. Test environment setup early
   3.4. Continuous integration

4. TESTING AS DRIVER
   4.1. Test-Driven Development (TDD)
      - Write test first
      - Red-Green-Refactor cycle

   4.2. Acceptance Test-Driven Development (ATDD)
      - Write acceptance test first
      - Given-When-Then format

   4.3. Behavior-Driven Development (BDD)
      - Scenarios in natural language
      - Cucumber, SpecFlow

5. DEVOPS & TESTING
   5.1. Continuous Integration/Delivery (CI/CD)
   5.2. Automated testing pipeline
   5.3. Fast feedback loops

6. SHIFT LEFT
   6.1. Move testing earlier
   6.2. Benefits: Earlier defect detection

7. RETROSPECTIVES
   7.1. What went well/wrong
   7.2. Process improvement
```

**Comparison tables**: Testing trong Waterfall vs Agile
**Examples**: TDD cycle for discount calculation function
**Practice questions**: 15 câu

---

#### Module 3.2: Test Levels
**Thời lượng**: 3-4 giờ | **Độ khó**: ⭐⭐

**Nội dung chính**:
```
1. 5 TEST LEVELS

1.1. COMPONENT TESTING (Unit Testing)
    - Test smallest units (functions, classes)
    - Usually done by developers
    - Test basis: Code, design
    - Test objects: Modules, units
    - Defects: Logic errors, data flow issues
    - Example: Test calculateDiscount() function

1.2. COMPONENT INTEGRATION TESTING
    - Test interfaces between components
    - Integration strategies: Big Bang, Top-down, Bottom-up
    - Example: Test API calls between Frontend ↔ Backend

1.3. SYSTEM TESTING
    - Test complete system
    - Black-box testing
    - Test basis: Requirements, user stories
    - Both functional và non-functional
    - Example: Test e-commerce checkout flow end-to-end

1.4. SYSTEM INTEGRATION TESTING
    - Test interfaces between systems
    - Example: E-commerce ↔ Payment Gateway

1.5. ACCEPTANCE TESTING
    - Verify system meets business needs
    - Types:
      a. User Acceptance Testing (UAT): By users
      b. Operational Acceptance Testing (OAT): By ops team
      c. Contractual/Regulatory: Compliance
      d. Alpha/Beta Testing
    - Example: Business users test inventory management system

2. TEST OBJECTIVES BY LEVEL
   Component: Find defects, verify functions
   Integration: Test interfaces, interactions
   System: Verify end-to-end scenarios
   Acceptance: Validate business needs

3. TEST BASIS BY LEVEL
   Component: Code, unit design
   Integration: Interface specs, architecture
   System: Requirements, use cases
   Acceptance: Business processes, user stories
```

**Ví dụ**: Test levels cho mobile banking app
**Comparison table**: Test levels differences
**Practice questions**: 15 câu

---

#### Module 3.3: Test Types
**Thời lượng**: 3-4 giờ | **Độ khó**: ⭐⭐

**Nội dung chính**:
```
1. 4 TEST TYPES

1.1. FUNCTIONAL TESTING
    - Test "WHAT" system does
    - Based on requirements
    - Example: Test login works correctly

1.2. NON-FUNCTIONAL TESTING
    - Test "HOW WELL" system works
    - Based on ISO 25010 quality characteristics:
      a. Performance Efficiency
         - Time behavior (response time)
         - Resource utilization
         - Capacity
      b. Compatibility
         - Co-existence
         - Interoperability
      c. Usability
         - User error protection
         - Aesthetics, Accessibility
      d. Reliability
         - Maturity, Availability
         - Fault tolerance, Recoverability
      e. Security
         - Confidentiality, Integrity
         - Authentication, Authorization
      f. Maintainability
         - Modularity, Testability
      g. Portability
         - Adaptability, Installability

1.3. BLACK-BOX TESTING
    - Focus on inputs/outputs
    - No knowledge of code structure
    - Techniques: EP, BVA, Decision Table, State Transition

1.4. WHITE-BOX TESTING
    - Focus on code structure
    - Knowledge of implementation
    - Techniques: Statement, Branch coverage

2. CONFIRMATION & REGRESSION TESTING
   2.1. Confirmation Testing (Re-testing)
       - Verify defect fixed
       - Run same test that found bug

   2.2. Regression Testing
       - Verify changes didn't break existing
       - Run suite of existing tests
       - Candidates for automation

3. MAINTENANCE TESTING
   3.1. Triggers:
       - Modifications (fixes, enhancements)
       - Upgrades/Migrations
       - Retirement
   3.2. Scope:
       - Changed areas
       - Impact analysis
       - Regression testing
```

**Examples**: Non-functional testing cho each ISO 25010 characteristic
**Case study**: Maintenance testing cho system upgrade
**Practice questions**: 15 câu

---

#### Module 3.4: Regression & Confirmation
**Thời lượng**: 2 giờ | **Độ khó**: ⭐

**Nội dung**: Focus on Confirmation vs Regression testing với nhiều ví dụ

#### Bài tập Giai đoạn 3
**Exercises**:
1. Map test levels cho specific project
2. Identify appropriate test types
3. Design regression test strategy
4. TDD exercise - Write test first

**Multiple Choice**: 30 câu

---

### GIAI ĐOẠN 4: Black-Box Techniques (2 tuần) ⭐⭐⭐ QUAN TRỌNG NHẤT

#### Module 4.1: Test Techniques Overview
**Thời lượng**: 1.5 giờ | **Độ khó**: ⭐

**Nội dung**: Introduction to test design techniques, categories

---

#### Module 4.2: Equivalence Partitioning (EP)
**Thời lượng**: 4-5 giờ | **Độ khó**: ⭐⭐⭐

**Nội dung chính**:
```
1. CONCEPT
   - Chia inputs thành partitions
   - Mỗi partition treated giống nhau
   - Test 1 value từ mỗi partition

2. VALID & INVALID PARTITIONS
   Valid: System accepts
   Invalid: System rejects

3. COVERAGE
   Coverage = (Partitions tested / Total partitions) × 100%

4. STEP-BY-STEP PROCESS
   Step 1: Identify inputs
   Step 2: Identify partitions (valid + invalid)
   Step 3: Select test values (1/partition)
   Step 4: Design test cases

5. EXAMPLES
   Example 1: Age field (18-65)
   Example 2: Discount code
   Example 3: Email validation
   Example 4: Product quantity (1-999)
```

**10 hands-on exercises** với đáp án chi tiết
**Practice questions**: 15 câu

---

#### Module 4.3: Boundary Value Analysis (BVA)
**Thời lượng**: 4-5 giờ | **Độ khó**: ⭐⭐⭐

**Nội dung chính**:
```
1. CONCEPT
   - Test at boundaries of partitions
   - Bugs often at boundaries

2. 2-VALUE BVA
   - Test boundary values only
   - For each boundary: min, max

3. 3-VALUE BVA
   - Test boundary + just inside + just outside
   - For each boundary: min-1, min, min+1 (max-1, max, max+1)

4. COMBINING WITH EP
   - EP identifies partitions
   - BVA tests boundaries

5. STEP-BY-STEP PROCESS
   Step 1: Identify boundaries
   Step 2: Choose 2-value or 3-value
   Step 3: Select test values
   Step 4: Design test cases

6. EXAMPLES
   Example 1: Age (18-65) → 2-value: 18, 65
   Example 2: Age (18-65) → 3-value: 17,18,19,64,65,66
   Example 3: Order quantity (1-999)
   Example 4: File size limit (max 10MB)
```

**10 hands-on exercises**
**Practice questions**: 15 câu

---

#### Module 4.4: Decision Table Testing
**Thời lượng**: 4-5 giờ | **Độ khó**: ⭐⭐⭐

**Nội dung chính**:
```
1. CONCEPT
   - Test combinations of conditions
   - Conditions → Actions
   - Systematic coverage

2. DECISION TABLE COMPONENTS
   - Conditions (inputs)
   - Actions (outputs/results)
   - Rules (combinations)

3. TYPES
   3.1. Limited-Entry Table
       - Boolean (True/False, Yes/No)
   3.2. Extended-Entry Table
       - Multiple values

4. FULL vs MINIMIZED TABLE
   - Full: All combinations (2^n rules for n conditions)
   - Minimized: Merge rules with same actions

5. COVERAGE
   Coverage = (Rules tested / Total rules) × 100%

6. STEP-BY-STEP PROCESS
   Step 1: Identify conditions và actions
   Step 2: Create full decision table
   Step 3: Minimize (optional)
   Step 4: Design test cases (1 per rule)

7. EXAMPLES
   Example 1: Discount calculation (member?, order>1000?)
   Example 2: Loan approval (income, credit score, employment)
   Example 3: Shipping cost (weight, destination, express?)
```

**8 hands-on exercises**
**Practice questions**: 15 câu

---

#### Module 4.5: State Transition Testing
**Thời lượng**: 4-5 giờ | **Độ khó**: ⭐⭐⭐

**Nội dung chính**:
```
1. CONCEPT
   - Test systems với states
   - Transitions giữa states
   - Events trigger transitions

2. STATE DIAGRAM
   - States (circles)
   - Transitions (arrows)
   - Events/Actions (labels)

3. STATE TABLE
   - Matrix format
   - Rows: Current states
   - Columns: Events
   - Cells: Next state / Action

4. COVERAGE CRITERIA
   4.1. All States Coverage
       - Visit mỗi state ít nhất 1 lần
   4.2. Valid Transitions Coverage
       - Execute mỗi valid transition
   4.3. All Transitions Coverage
       - Test both valid và invalid transitions

5. STEP-BY-STEP PROCESS
   Step 1: Identify states
   Step 2: Identify events
   Step 3: Draw state diagram or table
   Step 4: Design test cases for coverage

6. EXAMPLES
   Example 1: ATM states (Idle, Card Inserted, PIN Entered, Transaction)
   Example 2: Order status (New, Paid, Shipped, Delivered, Cancelled)
   Example 3: Login attempts (Active, Locked)
   Example 4: Game character states
```

**8 hands-on exercises**
**Practice questions**: 15 câu

---

#### Bài tập Giai đoạn 4
**Exercises**: 20 exercises (5 per technique)
**Case study**: Apply all techniques to e-commerce checkout
**Multiple Choice**: 50 câu (quan trọng - chiếm 40% exam)

---

### GIAI ĐOẠN 5: Other Techniques (1 tuần)

#### Module 5.1: White-Box Testing
**Nội dung**:
- Statement Testing & Coverage
- Branch Testing & Coverage
- Control Flow Graphs
- Calculating coverage
- Value of white-box testing

#### Module 5.2: Experience-Based Techniques
**Nội dung**:
- Error Guessing (fault attacks)
- Exploratory Testing (session-based)
- Checklist-Based Testing

#### Module 5.3: Collaboration-Based Approaches
**Nội dung**:
- User Story writing (3 C's: Card, Conversation, Confirmation)
- INVEST criteria
- Acceptance criteria (Given-When-Then)
- ATDD process

#### Bài tập Giai đoạn 5
**Multiple Choice**: 30 câu

---

### GIAI ĐOẠN 6: Test Management - Part 1 (1 tuần)

#### Module 6.1: Test Planning
**Nội dung**:
- Test plan components
- Entry/Exit criteria
- Definition of Ready/Done
- Test Pyramid
- Testing Quadrants

#### Module 6.2: Test Estimation
**Nội dung**:
- 4 estimation techniques:
  1. Estimation based on ratios
  2. Extrapolation
  3. Wideband Delphi (Planning Poker)
  4. Three-point estimation

#### Module 6.3: Test Case Prioritization
**Nội dung**:
- Risk-based prioritization
- Coverage-based prioritization
- Requirements-based prioritization

#### Module 6.4: Risk Management
**Nội dung**:
- Risk definition (Likelihood × Impact)
- Project risks vs Product risks
- Product risk analysis
- Product risk control

#### Bài tập Giai đoạn 6
**Multiple Choice**: 35 câu

---

### ✅ GIAI ĐOẠN 7: Test Management - Part 2 (1 tuần) - HOÀN THÀNH 100%

#### ✅ Module 7.1: Test Monitoring & Control
**File**: `giai-doan-7-test-management-2/module-7.1-test-monitoring-control.md`

**Nội dung**:
- 7 types of test metrics (Project progress, Test progress, Product quality, Defects, Risk, Coverage, Cost)
- Common metrics formulas (Execution %, Pass rate, Defect rate, DRE)
- Monitoring dashboards và burndown charts
- Test control actions
- Practical examples: Shopee testing project

#### ✅ Module 7.2: Test Reporting
**File**: `giai-doan-7-test-management-2/module-7.2-test-reporting.md`

**Nội dung**:
- Test Progress Report vs Test Completion Report
- Executive Summary best practices (< 1 page)
- Customizing reports for different audiences (CTO, PM, Dev Team)
- Effective visualizations (Burndown, Defect trends, Pass rates)
- Real-world examples: Grab Food weekly report, Momo completion report

#### ✅ Module 7.3: Configuration Management
**File**: `giai-doan-7-test-management-2/module-7.3-configuration-management.md`

**Nội dung**:
- Configuration Items (CIs) identification
- Baselines vs Versions vs Releases
- Requirements Traceability Matrix (RTM)
- Git workflow for test automation (branching strategy, commit conventions)
- Change control process
- Real-world example: Momo eKYC baseline management

#### ✅ Module 7.4: Defect Management
**File**: `giai-doan-7-test-management-2/module-7.4-defect-management.md`

**Nội dung**:
- Defect lifecycle (New → Assigned → In Progress → Resolved → Verified → Closed)
- Writing effective defect reports (template provided)
- Severity vs Priority (with matrix and examples)
- Defect triage process (decision tree, meeting agenda)
- Defect metrics (DRE, Density, MTTR, Aging)
- Root Cause Analysis (5 Whys, Fishbone diagram)
- Defect prevention strategies
- Real-world example: Shopee search bug full lifecycle

#### ✅ Bài tập Giai đoạn 7
**File**: `giai-doan-7-test-management-2/bai-tap-giai-doan-7.md`

**Practical Exercises**: 4 comprehensive exercises
1. Test Monitoring Metrics (VNPay QR Payment sprint analysis)
2. Test Reporting for Different Audiences (Momo Bill Payment)
3. Configuration Management Git Workflow (Shopee test automation)
4. Defect Management Triage (Grab Food defect allocation)

**Multiple Choice**: 30 câu covering all 4 modules

---

### ✅ GIAI ĐOẠN 8: Thực hành Tổng hợp (10-12 tuần) - HOÀN THÀNH 100%

#### ✅ Hướng Dẫn Thực Hành
**File**: `giai-doan-8-thuc-hanh-tong-hop/HUONG-DAN-THUC-HANH.md`

**Nội dung**:
- Tổng quan 3 dự án thực hành (70-85 giờ)
- Lộ trình chi tiết từng tuần cho mỗi project
- Phương pháp học hiệu quả (Learning by Doing)
- Rubric tự đánh giá năng lực
- Mapping sang 57 Learning Objectives ISTQB
- Tips & Best practices (Writing test cases, defect reports, metrics)
- Chuẩn bị thi ISTQB (Review plan, Mock exams strategy)
- Next steps after ISTQB (Specialized certifications, Practical skills)

---

#### ✅ Dự án 1: ShopVN - E-commerce Testing
**File**: `giai-doan-8-thuc-hanh-tong-hop/project-1-ecommerce-testing.md`

**Mô tả**: Testing website thương mại điện tử (Shopee-like platform)
**Thời gian**: 20-25 giờ (3 tuần)
**Trọng tâm**: Functional Testing, Black-box Techniques
**Độ khó**: ⭐⭐⭐

**Requirements**: 5 Epics covering:
1. User Management (Registration, Login, Profile, Password Management)
2. Product Management (Browse, Search, Filter, Product Details)
3. Shopping Cart (Add/Remove/Update items, Cart persistence)
4. Checkout & Payment (Address, Payment methods, Order confirmation)
5. Order Management (Order history, Status tracking, Cancellation, Returns)

**Test Techniques Applied**:
- Equivalence Partitioning (EP): Email validation, Input validation
- Boundary Value Analysis (BVA): Quantity (1-999), Price ranges
- Decision Table: Discount calculation (Member status × Order value)
- State Transition: Order lifecycle (New → Paid → Shipped → Delivered)

**Deliverables**:
- Requirements Review Report (ambiguities found)
- Test Plan (Risk analysis, Test approach, Entry/Exit criteria)
- 300+ Test Cases covering all 5 Epics
- Requirements Traceability Matrix
- 20-30 Defect Reports (simulated)
- Test Progress Report + Test Completion Report
- Lessons Learned document

**Learning Outcomes**:
- Master all 4 Black-box techniques
- Write professional Test Plan
- Create comprehensive Traceability Matrix
- Understand defect management lifecycle

---

#### ✅ Dự án 2: PayVN - Mobile Banking Testing
**File**: `giai-doan-8-thuc-hanh-tong-hop/project-2-mobile-banking-testing.md`

**Mô tả**: Testing ứng dụng ví điện tử di động (Momo-like wallet app)
**Thời gian**: 25-30 giờ (4 tuần)
**Trọng tâm**: Security, Performance, Compliance Testing
**Độ khó**: ⭐⭐⭐⭐

**Requirements**: 5 Epics covering:
1. Authentication & Authorization (Login, MFA, Biometric, Session)
2. Money Transfer (P2P, Bank transfer, QR Payment)
3. Bill Payment (Utilities, Mobile top-up, Services)
4. Transaction History (View, Filter, Export, Dispute)
5. Account Management (KYC, Limits, Security settings)

**Test Focus Areas**:
- **Security Testing**: OWASP Top 10 coverage
  - SQL Injection, XSS, Session Hijacking
  - Authentication bypass, Brute force attacks
  - Data encryption, Secure communication (HTTPS)
- **Performance Testing**:
  - Load Testing: 10,000 concurrent users
  - Stress Testing: Beyond capacity, breaking point
  - Spike Testing: Sudden traffic increase
  - Endurance Testing: 24h continuous operation
- **Compliance**: PCI DSS, SBV (State Bank of Vietnam) regulations

**Deliverables**:
- Security Test Plan
- 50+ Security Test Cases (OWASP Top 10)
- 30+ Performance Test Scenarios
- JMeter Test Scripts (optional but recommended)
- Compliance Checklist (PCI DSS, SBV)
- 100+ Functional Test Cases
- Security Vulnerability Report
- Performance Test Report
- Test Completion Report with Risk Assessment

**Learning Outcomes**:
- Master Security Testing techniques
- Understand Performance Testing types
- Apply Compliance requirements to testing
- Risk-based testing approach

---

#### ✅ Dự án 3: LearnVN - Education Platform Testing
**File**: `giai-doan-8-thuc-hanh-tong-hop/project-3-education-platform-testing.md`

**Mô tả**: Testing nền tảng học trực tuyến (Udemy-like platform)
**Thời gian**: 25-30 giờ (4 tuần)
**Trọng tâm**: Content Delivery, Multi-role Testing, Usability
**Độ khó**: ⭐⭐⭐⭐

**Requirements**: 5 Epics covering:
1. User Management (Student & Instructor roles, Permissions)
2. Course Creation & Management (Instructor: Create, Upload, Publish)
3. Course Discovery & Enrollment (Student: Browse, Search, Enroll)
4. Learning Experience (Video playback, Progress tracking, Quizzes)
5. Reviews & Ratings (Student reviews, Instructor responses)

**Test Focus Areas**:
- **Multi-Role Testing**:
  - Student journey: Browse → Enroll → Learn → Complete → Review
  - Instructor journey: Create → Upload → Publish → Monitor
  - Cross-role interactions
- **Content Delivery Testing**:
  - Video upload performance (2GB files)
  - Video transcoding (360p-1080p)
  - Adaptive bitrate streaming
  - 5000+ concurrent video streams
- **Usability Testing**:
  - Nielsen's 10 Heuristics evaluation
  - Accessibility (WCAG guidelines)
- **Integration Testing**:
  - Payment gateway integration
  - Email notification system
  - Video CDN integration

**Deliverables**:
- Multi-Role Test Strategy
- 150+ Functional Test Cases (Student role)
- 100+ Functional Test Cases (Instructor role)
- 50+ Video Streaming Test Cases
- Usability Evaluation Report (Nielsen's Heuristics)
- 30+ End-to-End Scenarios
- Integration Test Report
- Test Completion Report
- UX Improvement Recommendations

**Learning Outcomes**:
- Handle multi-role system complexity
- Test content delivery and video streaming
- Perform Usability Testing
- Execute End-to-end scenario testing
- Integration testing between components

---

**Tổng kết Giai đoạn 8**:
- ✅ 3 dự án thực tế covering 3 domains khác nhau
- ✅ 500+ test cases tổng hợp
- ✅ Áp dụng TẤT CẢ kiến thức từ 7 giai đoạn trước
- ✅ Chuẩn bị đầy đủ cho kỳ thi ISTQB
- ✅ Kinh nghiệm thực tế với Functional, Security, Performance, Usability testing

---

## ÔN THI ISTQB

### Tóm tắt Kiến thức
**File**: `on-thi-istqb/tom-tat-kien-thuc.md`

**Nội dung**:
- 57 Learning Objectives summary
- 7 Testing Principles explained
- Key concepts cheat sheet
- Common mistakes to avoid

---

### Đề Thi Mẫu

#### Đề 1: Practice Exam Set 1
**File**: `on-thi-istqb/cau-hoi-mau-set-1.md`
- 40 câu multiple choice
- Format giống thi thật
- Time limit: 60 minutes
- K1: ~16 câu (40%)
- K2: ~20 câu (50%)
- K3: ~4 câu (10%)

#### Đề 2: Practice Exam Set 2
**File**: `on-thi-istqb/cau-hoi-mau-set-2.md`
- 40 câu (format tương tự)

#### Đề 3: Practice Exam Set 3
**File**: `on-thi-istqb/cau-hoi-mau-set-3.md`
- 40 câu (format tương tự)

#### Đáp án & Giải thích
**File**: `on-thi-istqb/dap-an-giai-thich.md`
- Đáp án cho 120 câu
- Giải thích chi tiết tại sao đúng/sai
- Trích dẫn từ syllabus

---

### Mẹo Làm Bài Thi
**File**: `on-thi-istqb/meo-lam-bai-thi.md`

**Nội dung**:
- Time management (60 mins cho 40 câu)
- Elimination technique
- Keywords to watch for
- Common traps
- Marking strategy

---

## PHỤ LỤC (TEMPLATES)

### Template 1: Test Plan
**File**: `phu-luc/template-test-plan.md`

**Sections**:
1. Introduction
2. Test Scope
3. Test Approach
4. Test Resources
5. Test Schedule
6. Entry & Exit Criteria
7. Risks & Mitigation
8. Deliverables
9. Approvals

---

### Template 2: Test Case
**File**: `phu-luc/template-test-case.md`

**Fields**:
- Test Case ID
- Test Case Title
- Preconditions
- Test Steps (Step #, Action, Expected Result)
- Test Data
- Priority
- Status
- Execution Date
- Executed By
- Actual Result
- Pass/Fail

---

### Template 3: Defect Report
**File**: `phu-luc/template-defect-report.md`

**Fields**:
- Defect ID
- Title
- Date Reported
- Reported By
- Severity
- Priority
- Status
- Description
- Steps to Reproduce
- Expected Result
- Actual Result
- Environment
- Attachments
- Assigned To
- Comments/History

---

### Template 4: Test Report
**File**: `phu-luc/template-test-report.md`

**Sections**:
1. Executive Summary
2. Test Scope
3. Test Execution Summary
4. Defects Summary
5. Coverage Analysis
6. Risks
7. Recommendations
8. Conclusion

---

### Checklist: Review Checklist
**File**: `phu-luc/checklist-review.md`

**Categories**:
- Requirements Review Checklist
- Design Review Checklist
- Code Review Checklist
- Test Case Review Checklist

---

### Tài nguyên Tham khảo
**File**: `phu-luc/tai-nguyen-tham-khao.md`

**Nội dung**:
- ISTQB Official Resources
- Recommended Books
- Online Courses
- Practice Platforms
- YouTube Channels
- Communities (Vietnam)
- Tools References

---

## HƯỚNG DẪN SỬ DỤNG ROADMAP

### Cho Học Viên:

1. **Follow Theo Thứ Tự**:
   - Giai đoạn 1 → 2 → 3 → ... → 8
   - Không skip giai đoạn

2. **Hoàn Thành Bài Tập**:
   - Đạt ≥80% mỗi giai đoạn mới tiến tiếp

3. **Thực Hành Nhiều**:
   - Giai đoạn 4 (Black-box) quan trọng nhất
   - Làm nhiều exercises

4. **Mock Exams**:
   - Đề 1: Sau giai đoạn 5
   - Đề 2: Sau giai đoạn 7
   - Đề 3: Trước thi 1 tuần

### Cho Contributors:

Nếu bạn muốn expand giáo trình:

1. **Pick một Module** từ roadmap này
2. **Follow Format** của modules đã hoàn thành (Giai đoạn 1)
3. **Include**:
   - Learning Objectives
   - Detailed Content
   - Vietnamese Examples
   - Practice Questions
   - Self-Assessment Checklist

4. **Quality Standards**:
   - Rõ ràng, dễ hiểu
   - Ví dụ Việt Nam (Grab, Shopee, etc.)
   - Practical exercises
   - Bám sát ISTQB syllabus v4.0.1

---

## TIMELINE ĐỀ XUẤT

### Intensive (11 tuần - Full-time)
```
Week 1-2:  Giai đoạn 1 - Nền tảng
Week 3:    Giai đoạn 2 - Static Testing
Week 4:    Giai đoạn 3 - Testing trong SDLC
Week 5-6:  Giai đoạn 4 - Black-box Techniques
Week 7:    Giai đoạn 5 - Other Techniques
Week 8:    Giai đoạn 6 - Test Management Part 1
Week 9:    Giai đoạn 7 - Test Management Part 2
Week 10-11: Giai đoạn 8 - Dự án + Ôn thi
```

### Part-time (6 tháng)
```
Month 1:   Giai đoạn 1-2
Month 2:   Giai đoạn 3
Month 3:   Giai đoạn 4
Month 4:   Giai đoạn 5-6
Month 5:   Giai đoạn 7
Month 6:   Giai đoạn 8 + Ôn thi
```

---

## 🎉 KẾT LUẬN

### HOÀN THÀNH 100% GIÁO TRÌNH ISTQB FOUNDATION LEVEL!

Giáo trình này cung cấp:
- ✅ **8 giai đoạn hoàn chỉnh**: Từ nền tảng đến thực hành tổng hợp
- ✅ **28 modules chi tiết**: Covering all 57 ISTQB Learning Objectives
- ✅ **3 dự án thực tế**: E-commerce, Banking, Education Platform
- ✅ **500+ test cases mẫu**: Áp dụng tất cả kỹ thuật testing
- ✅ **200+ câu MCQ**: Practice questions trong mỗi giai đoạn
- ✅ **100% tiếng Việt**: Với ví dụ từ công ty Việt Nam (Grab, Shopee, Momo)
- ✅ **Templates thực tế**: Test Plan, Test Cases, Defect Reports, Test Reports
- ✅ **Chuẩn ISTQB v4.0.1**: Bám sát 100% syllabus chính thức

### 📊 Tổng Quan Nội Dung

| Giai Đoạn | Modules | Exercises | MCQs | Trạng Thái |
|-----------|---------|-----------|------|------------|
| 1. Nền Tảng | 4 | 5 | 30 | ✅ 100% |
| 2. Static Testing | 2 | 4 | 20 | ✅ 100% |
| 3. SDLC & Testing | 3 | 5 | 30 | ✅ 100% |
| 4. Black-box Techniques | 5 | 8 | 50 | ✅ 100% |
| 5. Other Techniques | 3 | 5 | 30 | ✅ 100% |
| 6. Test Management 1 | 4 | 6 | 35 | ✅ 100% |
| 7. Test Management 2 | 4 | 4 | 30 | ✅ 100% |
| 8. Thực hành Tổng hợp | 3 projects | - | - | ✅ 100% |
| **TỔNG** | **28** | **37** | **225+** | **✅ 100%** |

### 🎯 Bắt Đầu Học Ngay!

**Lộ trình đề xuất**:
1. **Intensive (11 tuần)**: Full-time, 8 giờ/ngày
2. **Part-time (6 tháng)**: 10-15 giờ/tuần

**Cách sử dụng roadmap**:
- 📝 Đọc module theo thứ tự từ Giai đoạn 1 → 8
- ✅ Đánh dấu `[x]` vào checkbox mỗi khi hoàn thành module
- 📊 Target: >80% điểm bài tập mỗi giai đoạn trước khi chuyển giai đoạn tiếp theo
- 🔄 Review lại các module khó (đặc biệt Giai đoạn 4)

**Sau khi hoàn thành**:
- ✅ Hiểu rõ 57 Learning Objectives của ISTQB
- ✅ Thành thạo tất cả kỹ thuật testing (Black-box, White-box, Experience-based)
- ✅ Viết được Test Plan, Test Cases, Defect Reports chuyên nghiệp
- ✅ Có kinh nghiệm thực hành với 3 dự án lớn
- ✅ Sẵn sàng thi ISTQB Foundation Level với tự tin cao

### 🚀 Bước Tiếp Theo

**Để chuẩn bị thi ISTQB**:
1. Hoàn thành cả 8 giai đoạn (đặc biệt Giai đoạn 4 & 8)
2. Làm lại tất cả MCQ questions (target >90%)
3. Làm 3 bộ mock exam (40 câu x 3)
4. Review lại 57 Learning Objectives
5. Đăng ký thi tại ISTQB Exam Provider

**Sau khi pass ISTQB**:
- Tiếp tục với ISTQB Advanced Level certifications
- Học automation: Selenium, Playwright, Cypress
- Thực hành trên dự án thực tế
- Tham gia cộng đồng tester Việt Nam

---

**Chúc bạn thành công với ISTQB Foundation Level! 🎓**

**"Testing is not just finding bugs. It's about ensuring quality, building confidence, and delivering value."**

---

**Version History**:
- v1.0.0 (Nov 2025): Initial roadmap with Phase 1 complete
- v2.0.0 (Nov 2025): Completed all 8 phases - Full curriculum ready!
- v2.1.0 (Nov 2025): Restructured for learning - Reset checkboxes for self-tracking
