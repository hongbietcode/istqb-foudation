# MODULE 1.4: CÔNG CỤ TESTING & KỸ NĂNG TESTER

**Giai đoạn**: 1 - Nền tảng
**Thời lượng học**: 3-4 giờ
**Độ khó**: ⭐ Dễ

---

## MỤC TIÊU HỌC TẬP (Learning Objectives)

Sau khi hoàn thành module này, bạn sẽ có thể:

### FL-1.5.1 (K2) - Explain generic skills required for testing
**Giải thích được các kỹ năng chung cần có cho testing**

### FL-1.5.2 (K1) - Recall benefits of whole team approach
**Nhớ lại được lợi ích của whole team approach**

### FL-1.5.3 (K2) - Distinguish benefits of independence of testing
**Phân biệt được lợi ích của independence trong testing**

### FL-6.1.1 (K1) - Recall types of test tools
**Nhớ lại được các loại test tools**

### FL-6.2.1 (K2) - Explain benefits and risks of test automation
**Giải thích được lợi ích và rủi ro của test automation**

**Business Outcomes**: FL-BO11, FL-BO12

---

## PHẦN 1: KỸ NĂNG CẦN THIẾT CHO TESTER

### 1.1. Generic Skills (Kỹ năng chung)

#### 1. Testing Knowledge (Kiến thức Testing)
**Mô tả**: Hiểu biết về testing principles, techniques, và processes

**Bao gồm**:
- Test design techniques (EP, BVA, State Transition, etc.)
- Test levels và types
- SDLC models
- Defect lifecycle
- Test management

**Ví dụ áp dụng**:
```
Scenario: Testing login form

Kiến thức cần:
✓ EP/BVA: Design test cases cho email và password fields
✓ Security testing: Check SQL injection, XSS
✓ Usability: Verify error messages clear
✓ Performance: Check login response time
```

---

#### 2. Thoroughness (Tính tỉ mỉ, cẩn thận)
**Mô tả**: Chú ý đến detail, không bỏ sót

**Quan trọng vì**:
- Một detail nhỏ bị bỏ qua có thể là critical bug
- Test cases cần cover all scenarios
- Defect reports cần chi tiết để developers reproduce

**Ví dụ**:
```
KHÔNG tỉ mỉ:
"Login không work"

TỈ MỈ:
"Login fails với email 'test@example.com' và
password 'Pass123!' khi click 'Login' button.
Error: 'Invalid credentials'
Expected: Login successful
Browser: Chrome 118.0, Windows 11
Reproducible: 100%"
```

---

#### 3. Good Communication (Giao tiếp tốt)
**Mô tả**: Communicate rõ ràng, hiệu quả với team

**Cần giao tiếp với**:
- **Developers**: Giải thích bugs, clarify requirements
- **Product Owners**: Update progress, discuss priorities
- **Test Manager**: Report status, request resources
- **End users**: Conduct UAT, gather feedback

**Ví dụ tình huống**:
```
BAD Communication:
"Cái này bị lỗi rồi, fix đi!"
→ Developer không hiểu, frustration

GOOD Communication:
"Hi [Dev name], tôi thấy khi user click 'Submit'
với empty name field, app crash thay vì show
validation error. Có thể bạn check logic validation?
Tôi đã log bug BUG-123 với steps chi tiết."
→ Developer hiểu rõ, collaborate tốt
```

---

#### 4. Analytical Thinking (Tư duy phân tích)
**Mô tả**: Phân tích problems, tìm root causes, identify patterns

**Áp dụng vào**:
- Analyze requirements để identify test conditions
- Debug failures để find root causes
- Analyze defect trends để identify problem areas

**Ví dụ**:
```
Situation: 5 bugs found trong Payment module

ANALYSIS:
Pattern: Tất cả bugs related to decimal calculations
Root cause: Floating-point precision issue
Action: Suggest sử dụng decimal type thay vì float
Impact: Prevent similar bugs in future
```

---

#### 5. Technical Knowledge (Kiến thức kỹ thuật)
**Mô tả**: Hiểu technical aspects của test object

**Tùy context, cần biết**:
- **Web testing**: HTML, CSS, JavaScript, HTTP, APIs
- **Mobile testing**: iOS/Android, mobile-specific issues
- **Database testing**: SQL, database concepts
- **API testing**: REST, JSON, XML, authentication
- **Performance testing**: Load concepts, bottlenecks

**Level cần thiết**:
- **Manual tester**: Basic understanding
- **Automation tester**: Programming skills (JavaScript, Python, Java)
- **Performance tester**: Deep understanding của architecture

**Ví dụ**:
```
Web App Testing cần biết:
✓ HTTP status codes (200, 404, 500, etc.)
✓ Cookies, Sessions, Local Storage
✓ Browser DevTools (Network, Console)
✓ Basic JavaScript debugging
✓ API concepts (GET, POST, PUT, DELETE)
```

---

#### 6. Domain Knowledge (Kiến thức nghiệp vụ)
**Mô tả**: Hiểu business domain của test object

**Ví dụ domains**:
- **Banking**: Interest calculations, transaction types
- **E-commerce**: Order flow, payment methods, shipping
- **Healthcare**: Patient records, compliance (HIPAA)
- **Education**: Enrollment, grading, curriculum

**Giá trị**:
```
WITHOUT Domain Knowledge:
- Test chỉ theo spec (có thể miss business logic errors)
- Khó communicate với business users

WITH Domain Knowledge:
- Identify business logic bugs (spec có thể sai)
- Better test case design (real-world scenarios)
- Effective communication với stakeholders
```

**Case Study**:
```
Domain: E-commerce Discount System

Domain Knowledge giúp tester biết:
✓ Không được combine multiple percentage discounts
✓ Free shipping không apply với remote areas
✓ Flash sale price priority hơn member discount
✓ Refund cần trừ shipping fee đã sử dụng

→ Design test cases cover business rules này!
```

---

### 1.2. Soft Skills

#### 1. Curiosity (Tò mò)
**Mô tả**: Luôn hỏi "What if...?"

**Ví dụ**:
```
Feature: Upload profile photo

Curious Tester asks:
- What if file size > 10MB?
- What if file format là .exe?
- What if filename có special characters?
- What if user cancel during upload?
- What if network disconnect mid-upload?
- What if upload same file twice?

→ Tìm ra nhiều edge cases hơn!
```

---

#### 2. Skepticism (Hoài nghi lành mạnh)
**Mô tả**: Không assume code works, verify everything

**Ví dụ**:
```
Developer: "Tôi đã fix bug rồi, không cần test lại"

Skeptical Tester:
"Let me verify the fix..."
→ Tests → Finds regression bug!

Lesson: Always verify, don't trust blindly
```

---

#### 3. Creativity (Sáng tạo)
**Mô tả**: Think outside the box, find unusual scenarios

**Ví dụ**:
```
Standard Test: Enter email, password, click Login
Creative Test: Copy-paste 10,000 characters into password field
→ Found: UI breaks, app crashes!

Standard Test: Upload 1 photo
Creative Test: Upload 100 photos simultaneously
→ Found: Server timeout, no error handling!
```

---

#### 4. Attention to Detail (Chú ý chi tiết)
**Ví dụ**:
```
Tester notices:
- Button text: "Submi" (missing 't')
- Date format inconsistent: DD/MM vs MM/DD
- Error message has grammar mistake
- Loading icon doesn't center properly
- Minor UI alignment off by 2px

→ Polish product quality!
```

---

## PHẦN 2: WHOLE TEAM APPROACH

### 2.1. Định nghĩa

**Whole Team Approach**: Mọi team member chịu trách nhiệm quality, không chỉ testers.

### 2.2. Trong Agile

```
TRADITIONAL:
Developers → Write code
Testers → Test code
(Silos, handoffs, delays)

WHOLE TEAM APPROACH:
Developers + Testers + PO + Users → Collaborate để ensure quality
(Shared responsibility)
```

### 2.3. Benefits

#### 1. Shared Responsibility
**Everyone cares about quality**

```
Developer:
- Write unit tests
- Review code
- Think about testability

Tester:
- Review requirements early
- Pair with developers
- Automate tests

PO:
- Write clear acceptance criteria
- Participate in demos
- Provide feedback quickly
```

---

#### 2. Better Communication
**Reduce misunderstandings**

```
Daily Standups:
- Developers share progress
- Testers share blockers
- PO clarifies requirements
- Quick decisions made

→ No "throw over the wall" mentality
```

---

#### 3. Faster Feedback
**Issues found và fixed nhanh hơn**

```
Developer finishes feature:
→ Pair with tester for quick check
→ Issues found immediately
→ Fix trong same day

vs.

Traditional:
Developer finishes → Wait for testing phase
→ Tester tests after 2 weeks → Finds issue
→ Developer already forgot code → Takes long to fix
```

---

#### 4. Skill Sharing
**Team members learn from each other**

```
Developers teach testers:
- Code structure
- Technical debugging
- Automation frameworks

Testers teach developers:
- Test design techniques
- User perspective
- Quality mindset
```

---

### 2.4. Ví dụ thực tế

```
USER STORY: "User can reset password via email"

WHOLE TEAM collaboration:

PO: Writes acceptance criteria (Given-When-Then)
Developer: Reviews AC, asks clarifications
Tester: Adds test scenarios PO missed
Designer: Reviews UX flow
Developer: Implements with unit tests
Tester: Pairs with dev for quick testing
Team: Demo together to stakeholders
Everyone: Retrospective to improve

Result: High quality, delivered fast
```

---

## PHẦN 3: INDEPENDENCE OF TESTING

### 3.1. Levels of Independence

```
LEVEL 1: No independent testing
└─ Developers test their own code only

LEVEL 2: Testing by another team member
└─ Developer A tests code của Developer B

LEVEL 3: Testing by dedicated test team
└─ Separate test team trong cùng organization

LEVEL 4: Testing by independent organization
└─ Third-party testing company (outsource)
```

### 3.2. Benefits of Independence

#### 1. Objectivity
**Không bị bias bởi code đã viết**

```
Developer tests own code:
- Might skip scenarios vì "I know code works"
- Focus on happy path
- Miss edge cases

Independent tester:
- No assumptions
- Test thoroughly
- Find unexpected issues
```

---

#### 2. Different Perspective
**Nhìn từ user perspective**

```
Developer perspective:
"Code executes without errors" ✓

Tester perspective:
"Does it meet user needs?"
"Is UX intuitive?"
"Is error message helpful?"
```

---

#### 3. Challenge Assumptions
**Question everything**

```
Developer: "Users sẽ không bao giờ làm thế"
Tester: "Let me test that scenario..."
→ Finds critical bug!
```

---

### 3.3. Drawbacks of Independence

#### 1. Communication Gap
```
Độc lập quá mức → Lack of collaboration
→ Testers không hiểu technical constraints
→ Developers không hiểu testing challenges
```

#### 2. Us vs Them Mentality
```
Developers: "Testers luôn complain"
Testers: "Developers write buggy code"
→ Blame game, not teamwork
```

#### 3. Cost
```
Independent test team hoặc outsource = Extra cost
```

---

### 3.4. Balance is Key

**IDEAL**: Combine independence with collaboration

```
✓ Dedicated testers (independence)
+ Whole team approach (collaboration)
= Best of both worlds

Example:
- Testers design test cases independently
- Developers write unit tests
- Testers và Developers pair for integration testing
- Daily collaboration in standups
- Shared responsibility for quality
```

---

## PHẦN 4: TEST TOOLS

### 4.1. Types of Test Tools

#### 1. Test Management Tools
**Purpose**: Quản lý test process

**Examples**:
- **Jira** (với Zephyr/Xray plugin)
- **TestRail**
- **qTest**
- **Azure Test Plans**

**Features**:
```
✓ Manage test cases
✓ Plan test execution
✓ Track test results
✓ Generate reports
✓ Integrate với defect tracking
✓ Traceability matrix
```

---

#### 2. Static Testing Tools
**Purpose**: Analyze code/documents WITHOUT execution

**Examples**:
- **SonarQube**: Code quality analysis
- **ESLint**: JavaScript linting
- **Grammarly**: Document review
- **Checkstyle**: Java code style

**What they find**:
```
✓ Code smells
✓ Code complexity
✓ Coding standard violations
✓ Duplicate code
✓ Security vulnerabilities (static)
✓ Documentation issues
```

---

#### 3. Test Design & Implementation Tools
**Purpose**: Help design và implement tests

**Examples**:
- **Selenium IDE**: Record/playback web tests
- **Katalon Studio**: Test automation platform
- **Postman**: API testing
- **Cucumber**: BDD framework

**Features**:
```
✓ Generate test cases from models
✓ Record user actions
✓ Create test data
✓ Design test procedures
```

---

#### 4. Test Execution & Coverage Tools
**Purpose**: Execute tests và measure coverage

**Examples**:
- **Selenium WebDriver**: Web automation
- **Cypress**: Modern web testing
- **Appium**: Mobile automation
- **JUnit/TestNG**: Unit testing frameworks
- **Istanbul/JaCoCo**: Code coverage

**Features**:
```
✓ Execute automated tests
✓ Capture screenshots/videos
✓ Measure code coverage
✓ Generate execution reports
✓ Integrate với CI/CD
```

---

#### 5. Non-Functional Testing Tools
**Purpose**: Test performance, security, etc.

**Performance Testing**:
- **JMeter**: Load testing
- **Gatling**: Performance testing
- **LoadRunner**: Enterprise load testing
- **k6**: Modern load testing

**Security Testing**:
- **OWASP ZAP**: Security scanning
- **Burp Suite**: Penetration testing
- **Nessus**: Vulnerability scanner

**Features**:
```
PERFORMANCE:
✓ Simulate concurrent users
✓ Measure response times
✓ Identify bottlenecks
✓ Generate load reports

SECURITY:
✓ Scan for vulnerabilities
✓ SQL injection testing
✓ XSS testing
✓ Security audit reports
```

---

#### 6. DevOps Tools
**Purpose**: Support CI/CD và continuous testing

**Examples**:
- **Jenkins**: CI/CD automation
- **GitLab CI**: Integrated CI/CD
- **GitHub Actions**: Workflow automation
- **Docker**: Containerization
- **Kubernetes**: Orchestration

**Use in Testing**:
```
Pipeline:
1. Code commit → Git
2. Trigger build → Jenkins
3. Run unit tests → JUnit
4. Run integration tests → Selenium
5. Run security scan → OWASP ZAP
6. Deploy to test environment → Docker
7. Run smoke tests → Cypress
8. Generate report → Allure

→ Automated, fast feedback!
```

---

#### 7. Collaboration Tools
**Purpose**: Team communication và collaboration

**Examples**:
- **Slack**: Team messaging
- **Microsoft Teams**: Collaboration platform
- **Confluence**: Documentation
- **Miro**: Visual collaboration

---

### 4.2. Tool Support for Testing - Summary Table

| Tool Category | Purpose | Examples | When to Use |
|---------------|---------|----------|-------------|
| **Test Management** | Organize tests | Jira, TestRail | All projects |
| **Static Testing** | Code analysis | SonarQube, ESLint | During development |
| **Test Automation** | Execute tests | Selenium, Cypress | Regression testing |
| **API Testing** | Test APIs | Postman, RestAssured | API projects |
| **Performance** | Load testing | JMeter, Gatling | High-traffic systems |
| **Security** | Security scan | OWASP ZAP, Burp | All web apps |
| **CI/CD** | Automation pipeline | Jenkins, GitLab CI | DevOps projects |
| **Collaboration** | Team work | Slack, Confluence | All teams |

---

## PHẦN 5: TEST AUTOMATION

### 5.1. Benefits of Test Automation

#### 1. Time Savings (Tiết kiệm thời gian)
```
Manual Regression: 40 hours (1 person × 40 hours)
Automated Regression: 2 hours execution

Repeat 10 times:
Manual: 400 hours
Automated: 20 hours + setup time

→ Saves 380+ hours!
```

---

#### 2. Consistency (Nhất quán)
```
Manual Test:
- Human errors possible
- Different testers → Different results
- Boredom → Missed steps

Automated Test:
- Exact same steps every time
- No human errors
- 100% reproducible
```

---

#### 3. Reusability (Tái sử dụng)
```
Once automated:
✓ Run multiple times
✓ Run on different environments
✓ Run on different browsers
✓ Run on different OS
✓ Integrate to CI/CD

ROI = High!
```

---

#### 4. Faster Feedback
```
Commit code → CI trigger → Tests run → Results in 15 minutes
vs.
Commit code → Wait for tester → Manual test → Results next day
```

---

#### 5. Better Coverage
```
Automation can test:
✓ 1000s of combinations
✓ Large data sets
✓ Concurrent users (performance)
✓ Long-running tests (endurance)

Manual: Too time-consuming
```

---

#### 6. Enables CI/CD
```
Continuous Deployment requires:
→ Fast automated testing
→ Immediate feedback
→ Confidence to deploy

Manual testing = Too slow for CD
```

---

### 5.2. Risks of Test Automation

#### 1. Unrealistic Expectations
**Risk**: "Automate everything!"

```
REALITY:
- Not all tests should be automated
- Setup takes time (weeks/months)
- Maintenance effort needed
- Still need manual exploratory testing

SOLUTION:
- Automate high-value tests (regression, smoke)
- Keep some manual tests (usability, ad-hoc)
- Set realistic goals
```

---

#### 2. Inaccurate Estimates
**Risk**: Underestimate effort

```
COMMON MISTAKE:
"Writing automation script = 1 hour"

REALITY:
- Initial script: 1 hour
- Make it robust: 3 hours
- Handle edge cases: 2 hours
- Maintenance over time: ongoing
- Total: Much more!

SOLUTION:
- Factor in maintenance
- Budget for framework setup
- Account for learning curve
```

---

#### 3. Inappropriate Tool Use
**Risk**: Sử dụng tool không phù hợp

```
BAD:
- Selenium for API testing (dùng Postman!)
- Manual testing for performance (dùng JMeter!)
- Over-automation (automate trivial tests)

GOOD:
- Right tool for right job
- Cost-benefit analysis
- Consider maintenance effort
```

---

#### 4. Over-Reliance on Automation
**Risk**: Nghĩ automation = No manual testing needed

```
DANGER:
"We have automation, không cần manual testing"
→ Miss UX issues
→ Miss exploratory findings
→ Miss usability problems

BALANCE:
Automation: Regression, Repetitive tests
Manual: Exploratory, Usability, New features
```

---

#### 5. Tool Vendor Lock-in
**Risk**: Depend quá nhiều vào commercial tool

```
PROBLEM:
- Tool license expensive
- Vendor discontinues product
- Hard to migrate to another tool

MITIGATION:
- Use open-source when possible
- Design framework tool-agnostic
- Evaluate vendor stability
```

---

#### 6. Compatibility Issues
**Risk**: Scripts break khi environment changes

```
EXAMPLE:
- Browser update → Selenium scripts fail
- API version change → Tests break
- UI redesign → Locators invalid

SOLUTION:
- Robust locator strategies
- Version control for test code
- CI pipeline catches breaks early
- Regular maintenance schedule
```

---

### 5.3. When to Automate vs Manual

#### Automate GOOD for:
```
✓ Regression tests (run repeatedly)
✓ Smoke tests (run after every build)
✓ Data-driven tests (many combinations)
✓ Performance tests (load, stress)
✓ API tests (fast, stable)
✓ Repetitive tests (same steps)
```

#### Manual BETTER for:
```
✓ Exploratory testing
✓ Usability testing
✓ Ad-hoc testing
✓ Tests that change frequently
✓ One-time tests
✓ Visual design verification
```

---

## PHẦN 6: PRACTICE QUESTIONS

### Question 1 (K2)
Which of the following is a benefit of independent testing?

A. Independent testers find different types of defects than developers
B. Independent testing is cheaper than testing by developers
C. Independent testers do not need to communicate with the development team
D. Independent testing eliminates the need for developers to test their own code

**Đáp án**: A
**Giải thích**: Independent testers bring different perspective và find different defects. B, C, D đều sai.

---

### Question 2 (K1)
Which skill is MOST important for a tester?

A. Ability to write code
B. Attention to detail
C. Knowledge of test tools
D. Ability to manage projects

**Đáp án**: B
**Giải thích**: Attention to detail là fundamental skill. A, C helpful nhưng không bắt buộc. D là test manager skill.

---

### Question 3 (K2)
Which of the following is a benefit of test automation?

A. All testing can be automated
B. Automation eliminates the need for manual testing
C. Automated tests can be run frequently with minimal effort
D. Automated testing is cheaper than manual testing for all types of tests

**Đáp án**: C
**Giải thích**: Automated tests có thể run nhiều lần với minimal effort. A, B, D đều sai.

---

### Question 4 (K1)
Which type of tool would be used to measure the percentage of code executed by automated tests?

A. Test management tool
B. Test execution tool
C. Coverage measurement tool
D. Static analysis tool

**Đáp án**: C
**Giải thích**: Coverage measurement tools (như JaCoCo, Istanbul) measure code coverage.

---

### Question 5 (K2)
What is a risk of test automation?

A. It requires no maintenance once implemented
B. It can lead to over-reliance on automated testing
C. It eliminates the need for test planning
D. It is always more cost-effective than manual testing

**Đáp án**: B
**Giải thích**: Over-reliance on automation là risk. A, C, D đều sai.

---

## SELF-ASSESSMENT CHECKLIST

- [ ] Tôi có thể liệt kê 5 generic skills cần cho tester
- [ ] Tôi hiểu whole team approach và benefits
- [ ] Tôi phân biệt được levels of independence
- [ ] Tôi nhớ được 7 types of test tools
- [ ] Tôi có thể giải thích benefits và risks của automation
- [ ] Tôi biết khi nào nên automate vs manual test

**Đạt ≥5/6** → Hoàn thành Giai đoạn 1!

---

## KEY TAKEAWAYS

1. **Generic Skills**: Testing knowledge, Thoroughness, Communication, Analytical thinking, Technical knowledge, Domain knowledge
2. **Whole Team Approach**: Shared responsibility, Better communication, Faster feedback
3. **Independence**: Brings objectivity nhưng cần balance với collaboration
4. **Test Tools**: 7 categories - Management, Static, Design, Execution, Non-functional, DevOps, Collaboration
5. **Automation**: Benefits (time savings, consistency) vs Risks (unrealistic expectations, maintenance)
6. **Balance**: Automate regression/repetitive, Manual cho exploratory/usability

---

## CONGRATULATIONS! 🎉

Bạn đã hoàn thành **GIAI ĐOẠN 1: NỀN TẢNG**!

### Bạn đã học được:
- ✓ Testing là gì và tại sao quan trọng
- ✓ 7 Testing Principles
- ✓ Error → Defect → Failure
- ✓ 7 Test Activities
- ✓ Testware và Traceability
- ✓ Test Roles
- ✓ Kỹ năng cần thiết
- ✓ Test Tools và Automation

### Tiếp theo:
📝 **BÀI TẬP**: [Bài tập Giai đoạn 1](bai-tap-giai-doan-1.md) - Củng cố kiến thức
📚 **MODULE TIẾP**: [Giai đoạn 2: Static Testing](../giai-doan-2-static-testing/module-2.1-static-testing-co-ban.md)

**Thời gian nghỉ**: 1 ngày trước khi làm bài tập
**Thời gian ôn**: 1 giờ review tất cả modules của Giai đoạn 1

---

**Tổng thời gian Giai đoạn 1**: 14-18 giờ
