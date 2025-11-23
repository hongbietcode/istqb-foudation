# ĐỀ THI MẪU 1 - ISTQB FOUNDATION LEVEL

**Thời gian**: 60 phút
**Số câu**: 40 câu
**Điểm đạt**: 26/40 (65%)

---

## HƯỚNG DẪN

- Mỗi câu có 4 đáp án (A, B, C, D), chọn 1 đáp án đúng nhất
- Không có điểm trừ cho câu sai
- Format giống thi ISTQB thật
- Nên làm trong điều kiện giống thi thật (không tra cứu)

**Cấu trúc đề**:
- K1 (Remember): ~16 câu (40%)
- K2 (Understand): ~20 câu (50%)
- K3 (Apply): ~4 câu (10%)

---

## SECTION 1: FUNDAMENTALS OF TESTING (8 câu)

### Question 1 (K1)
Which of the following is a typical test objective?

A. Verifying that all defects have been fixed
B. Preventing defects by evaluating work products
C. Proving that the software is completely defect-free
D. Ensuring developers write correct code on first attempt

<details>
<summary>Đáp án & Giải thích</summary>

**Đáp án: B**

**Giải thích**:
- B ✅ **ĐÚNG**: Preventing defects through evaluation của work products (như requirements, design) là typical test objective. Đây là static testing.
- A ❌ SAI: Verifying defects fixed là testing activity, không phải primary objective
- C ❌ SAI: Không thể prove completely defect-free (Principle #1)
- D ❌ SAI: Developers writing correct code là mục tiêu của development, không phải testing objective

**Reference**: ISTQB Syllabus FL 1.1.1
</details>

---

### Question 2 (K2)
Which statement correctly describes the difference between testing and debugging?

A. Testing finds defects; debugging analyzes and fixes the causes of failures
B. Testing removes defects from code; debugging finds defects
C. Testing is done by testers only; debugging is done by developers only
D. Testing and debugging are the same activity with different names

<details>
<summary>Đáp án & Giải thích</summary>

**Đáp án: A**

**Giải thích**:
- A ✅ **ĐÚNG**: Testing = Find defects (by testers), Debugging = Analyze root cause và fix (by developers)
- B ❌ SAI: Ngược lại - Testing finds, debugging removes
- C ❌ SAI: Developers cũng có thể test (unit tests), và testers có thể support debugging
- D ❌ SAI: Testing và debugging là 2 activities khác nhau

**Reference**: ISTQB Syllabus FL 1.1.2
</details>

---

### Question 3 (K2)
What is the relationship between errors, defects, and failures?

A. Errors in code lead to defects in requirements, which cause failures
B. Human errors can lead to defects in code, which may cause failures when executed
C. Failures in production lead to defects being reported as errors
D. Errors, defects, and failures are three different names for the same thing

<details>
<summary>Đáp án & Giải thích</summary>

**Đáp án: B**

**Giải thích**:
- B ✅ **ĐÚNG**: Error (human mistake) → Defect (bug in work product) → Failure (incorrect behavior when executed)
- A ❌ SAI: Flow sai - errors không lead to defects trong requirements
- C ❌ SAI: Flow ngược lại
- D ❌ SAI: 3 concepts khác nhau, không phải synonyms

**Reference**: ISTQB Syllabus FL 1.2.3
</details>

---

### Question 4 (K1)
Which testing principle states that if the same tests are repeated many times, they will no longer find new defects?

A. Testing shows the presence of defects
B. Exhaustive testing is impossible
C. Defects cluster together
D. Pesticide paradox

<details>
<summary>Đáp án & Giải thích</summary>

**Đáp án: D**

**Giải thích**:
- D ✅ **ĐÚNG**: Pesticide paradox (Principle #5) - Tests "wear out", cần update regularly
- A ❌ SAI: Principle #1 - về proving presence, not absence
- B ❌ SAI: Principle #2 - về không thể test tất cả
- C ❌ SAI: Principle #4 - về bugs tập trung

**Reference**: ISTQB Syllabus FL 1.3
</details>

---

### Question 5 (K2)
Why is it important to start testing early in the software development lifecycle?

A. It is a requirement in all agile projects
B. It reduces the cost of fixing defects found later
C. It eliminates the need for testing in later phases
D. It ensures that all code will be defect-free

<details>
<summary>Đáp án & Giải thích</summary>

**Đáp án: B**

**Giải thích**:
- B ✅ **ĐÚNG**: Early testing saves time and money (Principle #3) - Defects found early cheaper to fix
- A ❌ SAI: Không phải requirement cho tất cả Agile projects
- C ❌ SAI: Không eliminate need for later testing
- D ❌ SAI: Không thể ensure defect-free

**Reference**: ISTQB Syllabus FL 1.3
</details>

---

### Question 6 (K2)
Which of the following is a consequence of the defects cluster together principle?

A. All modules will eventually have an equal number of defects
B. Testing effort should be focused on modules with the most defects
C. Defects found later in testing are more expensive to fix
D. Retesting should be performed on all modules equally

<details>
<summary>Đáp án & Giải thích</summary>

**Đáp án: B**

**Giải thích**:
- B ✅ **ĐÚNG**: Defects cluster (Principle #4) → Focus testing on high-defect areas
- A ❌ SAI: Modules KHÔNG có equal defects - chúng cluster
- C ❌ SAI: Đây là Principle #3 (Early testing), không phải #4
- D ❌ SAI: Nên focus vào high-risk areas, không equal

**Reference**: ISTQB Syllabus FL 1.3
</details>

---

### Question 7 (K2)
What is the main difference between Quality Assurance (QA) and Quality Control (QC)?

A. QA is concerned with processes; QC is concerned with products
B. QA tests products; QC improves processes
C. QA is performed by developers; QC by testers
D. QA and QC are two names for the same activity

<details>
<summary>Đáp án & Giải thích</summary>

**Đáp án: A**

**Giải thích**:
- A ✅ **ĐÚNG**: QA = Process-focused (prevent defects), QC = Product-focused (detect defects). Testing là part của QC.
- B ❌ SAI: Ngược lại
- C ❌ SAI: Roles không fixed như vậy
- D ❌ SAI: Khác nhau - QA preventive, QC detective

**Reference**: ISTQB Syllabus FL 1.2.4
</details>

---

### Question 8 (K2)
How does testing contribute to higher quality?

A. By ensuring all defects are found and fixed before release
B. By providing information about defects to support improvements
C. By replacing the need for good development practices
D. By proving the software is completely correct

<details>
<summary>Đáp án & Giải thích</summary>

**Đáp án: B**

**Giải thích**:
- B ✅ **ĐÚNG**: Testing provides information (defects, metrics) để support decision-making và improvements
- A ❌ SAI: Không thể ensure ALL defects found
- C ❌ SAI: Testing KHÔNG replace good development practices
- D ❌ SAI: Không thể prove completely correct (Principle #1)

**Reference**: ISTQB Syllabus FL 1.2.1
</details>

---

## SECTION 2: TESTING THROUGHOUT THE SDLC (8 câu)

### Question 9 (K2)
In which SDLC model is testing performed as a separate phase after coding is complete?

A. Agile
B. Iterative
C. V-model
D. Waterfall

<details>
<summary>Đáp án & Giải thích</summary>

**Đáp án: D**

**Giải thích**:
- D ✅ **ĐÚNG**: Waterfall = Sequential model với testing phase AFTER coding phase
- A ❌ SAI: Agile = Testing throughout sprints
- B ❌ SAI: Iterative = Testing trong mỗi iteration
- C ❌ SAI: V-model có testing activities parallel với development

**Reference**: ISTQB Syllabus FL 2.1.1
</details>

---

### Question 10 (K1)
Which test level focuses on testing individual components or units?

A. System testing
B. Integration testing
C. Component testing
D. Acceptance testing

<details>
<summary>Đáp án & Giải thích</summary>

**Đáp án: C**

**Giải thích**:
- C ✅ **ĐÚNG**: Component testing (unit testing) = Test individual components
- A ❌ SAI: System testing = Complete system
- B ❌ SAI: Integration testing = Interfaces between components
- D ❌ SAI: Acceptance testing = Business needs validation

**Reference**: ISTQB Syllabus FL 2.2.1
</details>

---

### Question 11 (K2)
Which test type focuses on "how well" the system performs rather than "what" it does?

A. Functional testing
B. Black-box testing
C. Non-functional testing
D. White-box testing

<details>
<summary>Đáp án & Giải thích</summary>

**Đáp án: C**

**Giải thích**:
- C ✅ **ĐÚNG**: Non-functional testing = "HOW WELL" (performance, security, usability)
- A ❌ SAI: Functional testing = "WHAT" system does
- B ❌ SAI: Black-box = Testing technique, không phải type
- D ❌ SAI: White-box = Testing technique, không phải type

**Reference**: ISTQB Syllabus FL 2.2.2
</details>

---

### Question 12 (K2)
What is the difference between confirmation testing and regression testing?

A. Confirmation verifies a fix; regression checks for unintended side effects
B. Confirmation is automated; regression is manual
C. Confirmation is for functional bugs; regression for performance
D. They are two names for the same activity

<details>
<summary>Đáp án & Giải thích</summary>

**Đáp án: A**

**Giải thích**:
- A ✅ **ĐÚNG**: Confirmation testing = Verify defect fixed, Regression testing = Check không break existing functionality
- B ❌ SAI: Cả hai đều có thể automated hoặc manual
- C ❌ SAI: Cả hai không limited to specific test types
- D ❌ SAI: Khác nhau - different objectives

**Reference**: ISTQB Syllabus FL 2.2.3
</details>

---

### Question 13 (K1)
Which of the following is a characteristic of component integration testing?

A. Tests complete end-to-end business processes
B. Tests interfaces between components
C. Tests individual functions in isolation
D. Tests user acceptance of the system

<details>
<summary>Đáp án & Giải thích</summary>

**Đáp án: B**

**Giải thích**:
- B ✅ **ĐÚNG**: Component integration testing = Test interfaces/interactions between components
- A ❌ SAI: System testing
- C ❌ SAI: Component testing (unit testing)
- D ❌ SAI: Acceptance testing (UAT)

**Reference**: ISTQB Syllabus FL 2.2.1
</details>

---

### Question 14 (K2)
Which ISO 25010 quality characteristic relates to the degree to which a system protects information?

A. Reliability
B. Security
C. Maintainability
D. Portability

<details>
<summary>Đáp án & Giải thích</summary>

**Đáp án: B**

**Giải thích**:
- B ✅ **ĐÚNG**: Security = Protection của information và data (confidentiality, integrity, authentication)
- A ❌ SAI: Reliability = Availability, fault tolerance
- C ❌ SAI: Maintainability = Ease of modification
- D ❌ SAI: Portability = Ease of transfer to another environment

**Reference**: ISTQB Syllabus FL 2.2.2
</details>

---

### Question 15 (K2)
When is maintenance testing typically performed?

A. Only when defects are found in production
B. When modifications, upgrades, or migrations occur
C. Only during the initial development phase
D. Only when the system is being retired

<details>
<summary>Đáp án & Giải thích</summary>

**Đáp án: B**

**Giải thích**:
- B ✅ **ĐÚNG**: Maintenance testing triggered by modifications, upgrades/migrations, OR retirement
- A ❌ SAI: Không chỉ khi có defects
- C ❌ SAI: Maintenance testing = AFTER initial development
- D ❌ SAI: Không chỉ khi retire, còn modifications và upgrades

**Reference**: ISTQB Syllabus FL 2.2.4
</details>

---

### Question 16 (K1)
What does "shift left" refer to in testing?

A. Moving testers to the left side of the office
B. Starting testing activities earlier in the SDLC
C. Reducing the number of test cases
D. Automating regression tests

<details>
<summary>Đáp án & Giải thích</summary>

**Đáp án: B**

**Giải thích**:
- B ✅ **ĐÚNG**: Shift Left = Move testing activities earlier (left) in SDLC timeline
- A ❌ SAI: Physical location không relevant
- C ❌ SAI: Không relate to số lượng test cases
- D ❌ SAI: Automation là separate concept

**Reference**: ISTQB Syllabus FL 2.1.5
</details>

---

## SECTION 3: STATIC TESTING (6 câu)

### Question 17 (K2)
What is the main difference between static testing and dynamic testing?

A. Static testing finds more defects than dynamic testing
B. Static testing does not require code execution; dynamic testing does
C. Static testing is automated; dynamic testing is manual
D. Static testing is cheaper; dynamic testing is more expensive

<details>
<summary>Đáp án & Giải thích</summary>

**Đáp án: B**

**Giải thích**:
- B ✅ **ĐÚNG**: Static testing = NO execution (reviews, analysis), Dynamic testing = WITH execution
- A ❌ SAI: Không necessarily more defects, different types
- C ❌ SAI: Cả hai có thể automated hoặc manual
- D ❌ SAI: Cost depends on context

**Reference**: ISTQB Syllabus FL 3.1.1
</details>

---

### Question 18 (K1)
Which of the following work products can be examined using static testing?

A. Only source code
B. Only test cases
C. Requirements, design documents, code, and test cases
D. Only documents created by developers

<details>
<summary>Đáp án & Giải thích</summary>

**Đáp án: C**

**Giải thích**:
- C ✅ **ĐÚNG**: Static testing có thể examine ANY work products (requirements, design, code, test cases, contracts, plans, etc.)
- A, B, D ❌ SAI: Too restrictive, static testing applies to nhiều work products

**Reference**: ISTQB Syllabus FL 3.1.3
</details>

---

### Question 19 (K2)
Which review type is the MOST formal?

A. Informal review
B. Walkthrough
C. Technical review
D. Inspection

<details>
<summary>Đáp án & Giải thích</summary>

**Đáp án: D**

**Giải thích**:
- D ✅ **ĐÚNG**: Inspection = Most formal (defined process, metrics, formal roles)
- A ❌ SAI: Informal review = Least formal
- B ❌ SAI: Walkthrough = Less formal than inspection
- C ❌ SAI: Technical review = Less formal than inspection

**Reference**: ISTQB Syllabus FL 3.2.4
</details>

---

### Question 20 (K1)
Who typically leads a walkthrough?

A. The moderator
B. The author of the work product
C. The test manager
D. An independent reviewer

<details>
<summary>Đáp án & Giải thích</summary>

**Đáp án: B**

**Giải thích**:
- B ✅ **ĐÚNG**: Walkthrough = Author leads and explains work product
- A ❌ SAI: Moderator leads inspection, không phải walkthrough
- C, D ❌ SAI: Test manager hoặc independent reviewer không necessarily lead walkthrough

**Reference**: ISTQB Syllabus FL 3.2.4
</details>

---

### Question 21 (K2)
What is a benefit of early and frequent stakeholder feedback obtained through reviews?

A. It eliminates the need for dynamic testing
B. It helps identify requirement defects before they become code defects
C. It guarantees defect-free requirements
D. It reduces the need for test planning

<details>
<summary>Đáp án & Giải thích</summary>

**Đáp án: B**

**Giải thích**:
- B ✅ **ĐÚNG**: Early feedback qua reviews → Find requirement defects early → Prevent becoming code defects → Cheaper
- A ❌ SAI: Không eliminate need for dynamic testing
- C ❌ SAI: Không guarantee defect-free
- D ❌ SAI: Không reduce need for test planning

**Reference**: ISTQB Syllabus FL 3.2.1
</details>

---

### Question 22 (K2)
Which role in a review is responsible for recording defects and decisions?

A. Manager
B. Author
C. Moderator
D. Scribe

<details>
<summary>Đáp án & Giải thích</summary>

**Đáp án: D**

**Giải thích**:
- D ✅ **ĐÚNG**: Scribe = Records defects, decisions, and recommendations
- A ❌ SAI: Manager = Initiates review, assigns resources
- B ❌ SAI: Author = Creator of work product being reviewed
- C ❌ SAI: Moderator = Leads meeting, ensures process followed

**Reference**: ISTQB Syllabus FL 3.2.3
</details>

---

## SECTION 4: TEST ANALYSIS AND DESIGN (10 câu)

### Question 23 (K3) - APPLY
A system accepts an age input with valid range 18-65. Using 2-value boundary value analysis, which test values should be selected?

A. 17, 18, 65, 66
B. 18, 65
C. 18, 19, 64, 65
D. 17, 19, 64, 66

<details>
<summary>Đáp án & Giải thích</summary>

**Đáp án: B**

**Giải thích**:
- B ✅ **ĐÚNG**: 2-value BVA = Test boundary values only → 18 (min), 65 (max)
- A ❌ SAI: Includes invalid values (17, 66) - đây là 3-value BVA
- C ❌ SAI: Includes just inside boundaries (19, 64) - đây là 3-value BVA
- D ❌ SAI: Invalid values + just inside

**2-value BVA**: Test min và max boundaries
**3-value BVA**: Test min-1, min, min+1 (và max-1, max, max+1)

**Reference**: ISTQB Syllabus FL 4.2.2
</details>

---

### Question 24 (K2)
What is the main purpose of equivalence partitioning?

A. To test all possible input values
B. To reduce the number of test cases while maintaining coverage
C. To find defects in boundary areas
D. To test invalid inputs only

<details>
<summary>Đáp án & Giải thích</summary>

**Đáp án: B**

**Giải thích**:
- B ✅ **ĐÚNG**: EP = Reduce test cases by testing 1 value from each partition (assuming all values trong partition treated same)
- A ❌ SAI: Exhaustive testing impossible (Principle #2)
- C ❌ SAI: Boundary defects là purpose của BVA, không phải EP
- D ❌ SAI: EP tests BOTH valid và invalid partitions

**Reference**: ISTQB Syllabus FL 4.2.1
</details>

---

### Question 25 (K3) - APPLY
A login system locks the account after 5 failed login attempts. Which state transition test cases achieve "all states" coverage?

States: Active, Locked
Events: Correct password, Wrong password (5 times)

A. Test: Start in Active, enter correct password, remain Active
B. Test 1: Active → Wrong 5 times → Locked
   Test 2: Active → Correct → Active
C. Test: Active → Locked only
D. Test all transitions including invalid ones

<details>
<summary>Đáp án & Giải thích</summary>

**Đáp án: B**

**Giải thích**:
- B ✅ **ĐÚNG**: "All States" coverage = Visit mỗi state ít nhất 1 lần
  - Test 1 visits: Active → Locked ✓
  - Test 2 visits: Active ✓ (already visited)
  - Both states covered!
- A ❌ SAI: Chỉ cover Active state, missing Locked
- C ❌ SAI: Chỉ cover Active → Locked transition, missing return to Active
- D ❌ SAI: "All transitions" coverage khác với "All states" coverage

**Coverage types**:
- All States: Visit each state once
- Valid Transitions: Execute each valid transition
- All Transitions: Test valid + invalid transitions

**Reference**: ISTQB Syllabus FL 4.2.4
</details>

---

### Question 26 (K2)
When should decision table testing be used?

A. When testing complex business rules with multiple conditions
B. When testing user interface designs
C. When testing performance requirements
D. When testing boundary values

<details>
<summary>Đáp án & Giải thích</summary>

**Đáp án: A**

**Giải thích**:
- A ✅ **ĐÚNG**: Decision table testing = Best for complex business rules với multiple conditions và combinations
- B ❌ SAI: UI design testing typically uses exploratory testing
- C ❌ SAI: Performance testing uses performance testing tools
- D ❌ SAI: Boundary values use BVA technique

**Reference**: ISTQB Syllabus FL 4.2.3
</details>

---

### Question 27 (K1)
Which black-box test technique uses state diagrams or state tables?

A. Equivalence partitioning
B. Boundary value analysis
C. Decision table testing
D. State transition testing

<details>
<summary>Đáp án & Giải thích</summary>

**Đáp án: D**

**Giải thích**:
- D ✅ **ĐÚNG**: State transition testing uses state diagrams hoặc state tables
- A, B, C ❌ SAI: Other black-box techniques không use state models

**Reference**: ISTQB Syllabus FL 4.2.4
</details>

---

### Question 28 (K2)
What is the main difference between black-box and white-box testing techniques?

A. Black-box focuses on functionality; white-box focuses on code structure
B. Black-box is manual; white-box is automated
C. Black-box finds more defects than white-box
D. Black-box is for developers; white-box is for testers

<details>
<summary>Đáp án & Giải thích</summary>

**Đáp án: A**

**Giải thích**:
- A ✅ **ĐÚNG**: Black-box = Based on specification (functionality), White-box = Based on code structure (implementation)
- B ❌ SAI: Cả hai có thể manual hoặc automated
- C ❌ SAI: Find different types of defects, không necessarily more
- D ❌ SAI: Both can be used by developers và testers

**Reference**: ISTQB Syllabus FL 4.1
</details>

---

### Question 29 (K2)
Statement coverage measures which of the following?

A. The percentage of all possible paths through the code
B. The percentage of executable statements executed by tests
C. The percentage of decision outcomes exercised
D. The percentage of requirements covered

<details>
<summary>Đáp án & Giải thích</summary>

**Đáp án: B**

**Giải thích**:
- B ✅ **ĐÚNG**: Statement coverage = (Statements executed / Total executable statements) × 100%
- A ❌ SAI: Path coverage, không phải statement coverage
- C ❌ SAI: Decision/Branch coverage
- D ❌ SAI: Requirements coverage, không phải code coverage

**Reference**: ISTQB Syllabus FL 4.3.1
</details>

---

### Question 30 (K1)
Which test technique relies on the tester's experience and intuition?

A. Equivalence partitioning
B. Error guessing
C. Decision table testing
D. Statement testing

<details>
<summary>Đáp án & Giải thích</summary>

**Đáp án: B**

**Giải thích**:
- B ✅ **ĐÚNG**: Error guessing = Experience-based technique dựa vào experience để guess errors
- A, C, D ❌ SAI: Structured techniques với formal rules

**Reference**: ISTQB Syllabus FL 4.4.1
</details>

---

### Question 31 (K2)
What characterizes exploratory testing?

A. Tests are designed, executed, and evaluated simultaneously
B. Tests follow a predetermined script
C. Tests are fully automated
D. Tests only focus on positive scenarios

<details>
<summary>Đáp án & Giải thích</summary>

**Đáp án: A**

**Giải thích**:
- A ✅ **ĐÚNG**: Exploratory testing = Design, Execute, và Learn simultaneously (không có pre-defined test cases)
- B ❌ SAI: Predetermined script = Scripted testing, không phải exploratory
- C ❌ SAI: Exploratory testing typically manual
- D ❌ SAI: Tests both positive và negative scenarios

**Reference**: ISTQB Syllabus FL 4.4.2
</details>

---

### Question 32 (K2)
In Acceptance Test-Driven Development (ATDD), when are acceptance criteria defined?

A. After coding is complete
B. Before the user story is implemented
C. During regression testing
D. Only for failed test cases

<details>
<summary>Đáp án & Giải thích</summary>

**Đáp án: B**

**Giải thích**:
- B ✅ **ĐÚNG**: ATDD = Define acceptance tests (Given-When-Then) BEFORE implementation
- A ❌ SAI: ATDD = Test-driven, tests come FIRST
- C ❌ SAI: Regression testing không relate to ATDD
- D ❌ SAI: Defined for ALL user stories, không chỉ failed

**Reference**: ISTQB Syllabus FL 4.5.3
</details>

---

## SECTION 5: TEST MANAGEMENT (8 câu)

### Question 33 (K2)
Which of the following is a typical entry criterion for test execution?

A. All defects have been fixed
B. Test environment is available and stable
C. All test cases have been executed
D. Exit criteria have been met

<details>
<summary>Đáp án & Giải thích</summary>

**Đáp án: B**

**Giải thích**:
- B ✅ **ĐÚNG**: Entry criteria = Conditions to START activity → Test environment ready là typical entry criterion cho test execution
- A ❌ SAI: All defects fixed là exit criterion, không phải entry
- C ❌ SAI: All test cases executed là exit criterion
- D ❌ SAI: Exit criteria met = Activity finished, không phải starting

**Reference**: ISTQB Syllabus FL 5.1.6
</details>

---

### Question 34 (K1)
What is the main purpose of test monitoring?

A. To design test cases
B. To track progress against the test plan
C. To execute tests
D. To write the test completion report

<details>
<summary>Đáp án & Giải thích</summary>

**Đáp án: B**

**Giải thích**:
- B ✅ **ĐÚNG**: Test monitoring = Track test progress and compare với plan
- A ❌ SAI: Test design activity
- C ❌ SAI: Test execution activity
- D ❌ SAI: Test completion activity

**Reference**: ISTQB Syllabus FL 5.3.1
</details>

---

### Question 35 (K3) - APPLY
A project has 500 test cases estimated to take 100 hours. After 50 hours, 200 test cases have been executed. Using extrapolation, how many more hours are needed to complete all tests?

A. 50 hours
B. 75 hours
C. 100 hours
D. 150 hours

<details>
<summary>Đáp án & Giải thích</summary>

**Đáp án: B**

**Giải thích**:
- B ✅ **ĐÚNG**:
  - Rate: 200 cases / 50 hours = 4 cases/hour
  - Remaining: 500 - 200 = 300 cases
  - Time needed: 300 / 4 = 75 hours

**Extrapolation**: Use current rate để project future effort

**Calculation steps**:
1. Calculate rate from actual data: cases per hour
2. Calculate remaining work
3. Divide remaining by rate

**Reference**: ISTQB Syllabus FL 5.1.4
</details>

---

### Question 36 (K2)
What is product risk?

A. Risk that the project will be late
B. Risk that the product will not meet quality requirements
C. Risk that the team will lack resources
D. Risk that the budget will be exceeded

<details>
<summary>Đáp án & Giải thích</summary>

**Đáp án: B**

**Giải thích**:
- B ✅ **ĐÚNG**: Product risk = Risk related to product QUALITY (defects, failures, not meeting requirements)
- A, C, D ❌ SAI: These are PROJECT risks (schedule, resources, budget), không phải product risks

**Product risks**: Quality issues (bugs, failures)
**Project risks**: Schedule, budget, resources, scope

**Reference**: ISTQB Syllabus FL 5.2.1
</details>

---

### Question 37 (K2)
Which metric would indicate test progress?

A. Number of defects found per module
B. Percentage of test cases executed
C. Code complexity score
D. Requirements coverage percentage

<details>
<summary>Đáp án & Giải thích</summary>

**Đáp án: B**

**Giải thích**:
- B ✅ **ĐÚNG**: Test progress metric = % test cases executed (e.g., 250/500 = 50% done)
- A ❌ SAI: Defect metric (quality), không phải progress
- C ❌ SAI: Code metric, không relate to test progress
- D ❌ SAI: Coverage metric (quality), không directly indicate progress

**Test Progress Metrics**:
- Test cases executed vs planned
- Time used vs planned
- Milestones achieved

**Reference**: ISTQB Syllabus FL 5.3.1
</details>

---

### Question 38 (K1)
What information should a defect report include?

A. Only the steps to reproduce
B. Unique ID, title, steps to reproduce, expected and actual results
C. Only the developer's name
D. Only the severity level

<details>
<summary>Đáp án & Giải thích</summary>

**Đáp án: B**

**Giải thích**:
- B ✅ **ĐÚNG**: Defect report components: ID, Title, Steps, Expected vs Actual, plus Severity, Priority, Status, Environment, etc.
- A, C, D ❌ SAI: Incomplete - defect report cần nhiều fields hơn

**Essential fields**: ID, Title, Description, Steps, Expected, Actual, Severity, Priority, Status

**Reference**: ISTQB Syllabus FL 5.5
</details>

---

### Question 39 (K2)
What is the difference between severity and priority of a defect?

A. Severity is technical impact; priority is business urgency
B. Severity is assigned by developers; priority by testers
C. Severity relates to cost; priority to time
D. They are the same thing with different names

<details>
<summary>Đáp án & Giải thích</summary>

**Đáp án: A**

**Giải thích**:
- A ✅ **ĐÚNG**: Severity = Technical impact (얼마나 serious?), Priority = Business urgency (cần fix nhanh thế nào?)
- B ❌ SAI: Roles không fixed như vậy
- C ❌ SAI: Không chính xác
- D ❌ SAI: Different concepts

**Example**: Homepage typo = Low Severity, High Priority (visible to all users)

**Reference**: ISTQB Syllabus FL 5.5
</details>

---

### Question 40 (K2)
What is the primary purpose of configuration management in testing?

A. To manage defects
B. To uniquely identify and control test items and testware
C. To monitor test execution
D. To prioritize test cases

<details>
<summary>Đáp án & Giải thích</summary>

**Đáp án: B**

**Giải thích**:
- B ✅ **ĐÚNG**: Configuration Management = Identify, control, track versions của test items và testware
- A ❌ SAI: Defect management là separate activity
- C ❌ SAI: Test monitoring là separate activity
- D ❌ SAI: Prioritization là test planning activity

**CM Purpose**: Version control, traceability, baselines

**Reference**: ISTQB Syllabus FL 5.4
</details>

---

## ANSWER SHEET

```
1.  B    11. C    21. B    31. A
2.  A    12. A    22. D    32. B
3.  B    13. B    23. B    33. B
4.  D    14. B    24. B    34. B
5.  B    15. B    25. B    35. B
6.  B    16. B    26. A    36. B
7.  A    17. B    27. D    37. B
8.  B    18. C    28. A    38. B
9.  D    19. D    29. B    39. A
10. C    20. B    30. B    40. B
```

---

## SCORING

- **Your Score**: _____ / 40
- **Percentage**: _____ %
- **Result**:
  - ≥ 26 (65%): **PASS** ✅
  - < 26 (65%): **FAIL** ❌

---

## NEXT STEPS

### If you scored ≥26 (PASS):
🎉 **Congratulations!** Bạn có kiến thức tốt!

**Next**:
- Review câu sai để hiểu rõ hơn
- Practice Đề 2 sau 2-3 ngày
- Continue studying weak areas

### If you scored <26 (FAIL):
📚 **Need more study!**

**Analyze**:
- Which sections scored lowest?
- Review corresponding modules
- Retake test sau 1 tuần study

---

**Good luck! 🍀**

**Version**: 1.0.0
**Based on**: ISTQB CTFL Syllabus v4.0.1
