# MODULE 6.4: RISK MANAGEMENT

**Thời lượng**: 3-4 giờ | **Độ khó**: ⭐⭐⭐

---

## MỤC TIÊU HỌC TẬP

Sau khi hoàn thành module này, bạn sẽ:

| ID | Mục tiêu | Level |
|----|----------|-------|
| FL-5.2.1 | Giải thích risk definition và attributes | K2 |
| FL-5.2.2 | Phân biệt project risks vs product risks | K2 |
| FL-5.2.3 | Thực hiện product risk analysis | K3 |
| FL-5.2.4 | Giải thích product risk control | K2 |

---

## 1. RISK LÀ GÌ?

### 1.1. Risk Definition

```
╔═══════════════════════════════════════════════════════════════╗
║                      RISK DEFINITION                          ║
╠═══════════════════════════════════════════════════════════════╣
║                                                               ║
║  📖 ĐỊNH NGHĨA:                                               ║
║     RISK = Potential future event có thể result in HARM      ║
║                                                               ║
║  📐 RISK FORMULA:                                             ║
║                                                               ║
║     RISK LEVEL = LIKELIHOOD × IMPACT                         ║
║                                                               ║
║     LIKELIHOOD (Xác suất):                                   ║
║     → Probability event sẽ xảy ra                            ║
║     → Scale: 1-5 (Very Low to Very High)                     ║
║                                                               ║
║     IMPACT (Hậu quả):                                        ║
║     → Severity nếu event xảy ra                              ║
║     → Scale: 1-5 (Very Low to Very High)                     ║
║                                                               ║
║  🎯 RISK ATTRIBUTES:                                          ║
║     • Risk ID (identifier)                                   ║
║     • Risk Description                                       ║
║     • Risk Owner (responsible person)                        ║
║     • Likelihood (1-5)                                       ║
║     • Impact (1-5)                                           ║
║     • Risk Level (Likelihood × Impact)                       ║
║     • Mitigation Strategy                                    ║
║     • Status (Open, Mitigated, Closed)                       ║
║                                                               ║
╚═══════════════════════════════════════════════════════════════╝
```

### 1.2. Risk Matrix

```
                    IMPACT
               1     2     3     4     5
            ┌─────┬─────┬─────┬─────┬─────┐
          5 │  5  │ 10  │ 15  │ 20  │ 25  │
            ├─────┼─────┼─────┼─────┼─────┤
          4 │  4  │  8  │ 12  │ 16  │ 20  │
LIKELIHOOD  ├─────┼─────┼─────┼─────┼─────┤
          3 │  3  │  6  │  9  │ 12  │ 15  │
            ├─────┼─────┼─────┼─────┼─────┤
          2 │  2  │  4  │  6  │  8  │ 10  │
            ├─────┼─────┼─────┼─────┼─────┤
          1 │  1  │  2  │  3  │  4  │  5  │
            └─────┴─────┴─────┴─────┴─────┘

RISK LEVELS:
  20-25: CRITICAL (Red) - Immediate action
  12-19: HIGH (Orange) - Urgent mitigation
  6-11:  MEDIUM (Yellow) - Monitor & mitigate
  1-5:   LOW (Green) - Accept or minimal action
```

---

## 2. PROJECT RISKS VS PRODUCT RISKS

### 2.1. So Sánh

```
╔═══════════════════════════════════════════════════════════════╗
║           PROJECT RISKS VS PRODUCT RISKS                      ║
╠═══════════════════════════════════════════════════════════════╣
║                                                               ║
║  🏗️ PROJECT RISKS:                                           ║
║     → Risks affecting PROJECT ACTIVITIES (process)           ║
║     → Impact: Schedule, cost, scope                          ║
║     → Managed by: Project Manager                            ║
║                                                               ║
║     EXAMPLES:                                                ║
║     • Key resources unavailable                              ║
║     • Budget cuts                                            ║
║     • Tool failures                                          ║
║     • Vendor delays                                          ║
║     • Poor communication                                     ║
║                                                               ║
║  📦 PRODUCT RISKS (QUALITY RISKS):                           ║
║     → Risks affecting PRODUCT QUALITY                        ║
║     → Impact: Functionality, performance, user satisfaction  ║
║     → Managed by: Test Manager, QA Team                      ║
║                                                               ║
║     EXAMPLES:                                                ║
║     • Software defects                                       ║
║     • Poor performance                                       ║
║     • Security vulnerabilities                               ║
║     • Usability issues                                       ║
║     • Data corruption                                        ║
║                                                               ║
╚═══════════════════════════════════════════════════════════════╝
```

### 2.2. Chi Tiết Project Risks

**Common Project Risks:**
```
📅 SCHEDULE RISKS:
   • Delays in development
   • Testing time squeezed
   • Late requirement changes
   • Dependencies not met

💰 BUDGET RISKS:
   • Cost overruns
   • Insufficient test budget
   • Tool licensing costs

👥 RESOURCE RISKS:
   • Team members leave
   • Lack of skilled testers
   • Training needs not met
   • Conflicting priorities

🔧 TECHNICAL RISKS:
   • Tool failures
   • Test environment instability
   • Third-party integration issues
   • Technology complexity

📋 ORGANIZATIONAL RISKS:
   • Poor requirements
   • Lack of management support
   • Communication gaps
   • Political issues
```

### 2.3. Chi Tiết Product Risks

**Common Product Risks:**
```
🐛 FUNCTIONAL RISKS:
   • Core features don't work
   • Business logic errors
   • Data integrity issues
   • Incorrect calculations

⚡ PERFORMANCE RISKS:
   • Slow response time
   • Cannot handle load
   • Memory leaks
   • Battery drain (mobile)

🔒 SECURITY RISKS:
   • SQL injection vulnerabilities
   • XSS attacks
   • Weak authentication
   • Data exposure

💾 DATA RISKS:
   • Data loss
   • Data corruption
   • Migration failures
   • Backup failures

👤 USABILITY RISKS:
   • Confusing UI
   • Poor accessibility
   • Navigation issues
   • User frustration

🔗 INTEGRATION RISKS:
   • API failures
   • Third-party service issues
   • Version incompatibilities
```

---

## 3. PRODUCT RISK ANALYSIS

### 3.1. Risk Analysis Process

```
╔═══════════════════════════════════════════════════════════════╗
║              PRODUCT RISK ANALYSIS PROCESS                    ║
╠═══════════════════════════════════════════════════════════════╣
║                                                               ║
║  🔄 4 STEPS:                                                  ║
║                                                               ║
║  1️⃣ RISK IDENTIFICATION                                       ║
║     → Brainstorm potential risks                             ║
║     → Review requirements, architecture                      ║
║     → Learn from past projects                               ║
║                                                               ║
║  2️⃣ RISK ASSESSMENT                                           ║
║     → Determine Likelihood (1-5)                             ║
║     → Determine Impact (1-5)                                 ║
║     → Calculate Risk Level                                   ║
║                                                               ║
║  3️⃣ RISK PRIORITIZATION                                       ║
║     → Order risks by Risk Level                              ║
║     → Focus on high-risk items                               ║
║                                                               ║
║  4️⃣ RISK MITIGATION PLANNING                                  ║
║     → Define mitigation actions                              ║
║     → Assign owners                                          ║
║     → Set timelines                                          ║
║                                                               ║
╚═══════════════════════════════════════════════════════════════╝
```

### 3.2. Ví Dụ: Product Risk Analysis cho Shopee

**Step 1: Risk Identification**

Identified Risks:
1. Payment gateway integration failure
2. Product search returns incorrect results
3. Checkout process timeout under load
4. User data leaked via API
5. Promo code logic errors (wrong discounts)
6. App crashes on older devices
7. Wishlist data lost during server migration

**Step 2: Risk Assessment**

| ID | Risk | Likelihood | Impact | Risk Level |
|----|------|-----------|--------|------------|
| R1 | Payment gateway failure | 3 | 5 | **15** (HIGH) |
| R2 | Search incorrect results | 2 | 4 | **8** (MEDIUM) |
| R3 | Checkout timeout | 4 | 5 | **20** (CRITICAL) |
| R4 | User data leaked | 2 | 5 | **10** (MEDIUM-HIGH) |
| R5 | Promo code errors | 3 | 3 | **9** (MEDIUM) |
| R6 | App crashes old devices | 3 | 2 | **6** (MEDIUM-LOW) |
| R7 | Wishlist data lost | 2 | 2 | **4** (LOW) |

**Step 3: Risk Prioritization**

```
CRITICAL (20-25):
  R3: Checkout timeout under load (20)

HIGH (12-19):
  R1: Payment gateway failure (15)

MEDIUM (6-11):
  R4: User data leaked (10)
  R5: Promo code errors (9)
  R2: Search incorrect results (8)
  R6: App crashes (6)

LOW (1-5):
  R7: Wishlist data lost (4)
```

**Step 4: Mitigation Planning**

| Risk | Mitigation Strategy | Owner | Timeline |
|------|---------------------|-------|----------|
| R3 | • Performance testing (10K concurrent users)<br>• Load balancing setup<br>• Timeout optimization | Perf Engineer | Week 1-2 |
| R1 | • Integration testing with all gateways<br>• Mock gateway for testing<br>• Fallback mechanism | QA Lead | Week 1 |
| R4 | • Security testing (OWASP Top 10)<br>• Penetration testing<br>• Code review for API endpoints | Security Team | Week 2-3 |

### 3.3. Risk Identification Techniques

```
╔═══════════════════════════════════════════════════════════════╗
║           RISK IDENTIFICATION TECHNIQUES                      ║
╠═══════════════════════════════════════════════════════════════╣
║                                                               ║
║  1. BRAINSTORMING                                            ║
║     → Team session, all ideas welcome                        ║
║                                                               ║
║  2. EXPERT INTERVIEWS                                        ║
║     → Consult với domain experts                             ║
║                                                               ║
║  3. PAST PROJECT REVIEWS                                     ║
║     → Learn from historical issues                           ║
║                                                               ║
║  4. RISK CHECKLISTS                                          ║
║     → Use standard checklists (OWASP, etc.)                  ║
║                                                               ║
║  5. ARCHITECTURE REVIEW                                      ║
║     → Analyze design for weaknesses                          ║
║                                                               ║
║  6. FAILURE MODE ANALYSIS                                    ║
║     → What can go wrong? How?                                ║
║                                                               ║
╚═══════════════════════════════════════════════════════════════╝
```

---

## 4. PRODUCT RISK CONTROL

### 4.1. Risk Control Strategies

```
╔═══════════════════════════════════════════════════════════════╗
║              RISK CONTROL (MITIGATION)                        ║
╠═══════════════════════════════════════════════════════════════╣
║                                                               ║
║  🎯 4 STRATEGIES:                                             ║
║                                                               ║
║  1. RISK MITIGATION (REDUCE)                                 ║
║     → Take actions to REDUCE likelihood or impact            ║
║     → Most common approach                                   ║
║     → Example: More testing, code reviews                    ║
║                                                               ║
║  2. RISK TRANSFER                                            ║
║     → Transfer risk to 3rd party                             ║
║     → Example: Insurance, outsourcing                        ║
║                                                               ║
║  3. RISK ACCEPTANCE                                          ║
║     → ACCEPT risk (do nothing)                               ║
║     → For low-risk items                                     ║
║     → Document decision                                      ║
║                                                               ║
║  4. RISK AVOIDANCE                                           ║
║     → ELIMINATE risk completely                              ║
║     → Change approach/design                                 ║
║     → Example: Don't implement risky feature                 ║
║                                                               ║
╚═══════════════════════════════════════════════════════════════╝
```

### 4.2. Mitigation Through Testing

**Testing Activities để Mitigate Product Risks:**

```
╔═══════════════════════════════════════════════════════════════╗
║           TESTING TO MITIGATE RISKS                           ║
╠═══════════════════════════════════════════════════════════════╣
║                                                               ║
║  HIGH RISK → MORE TESTING:                                   ║
║                                                               ║
║     ✓ More test cases (deeper coverage)                      ║
║     ✓ Multiple test techniques (EP, BVA, State, etc.)        ║
║     ✓ More experienced testers assigned                      ║
║     ✓ Earlier testing (shift-left)                           ║
║     ✓ More reviews (code, design, requirements)              ║
║     ✓ Exploratory testing sessions                           ║
║     ✓ Non-functional testing (performance, security)         ║
║     ✓ Beta testing với real users                            ║
║                                                               ║
║  LOW RISK → LESS TESTING:                                    ║
║                                                               ║
║     ✓ Fewer test cases (basic coverage)                      ║
║     ✓ Simple techniques                                      ║
║     ✓ Junior testers can handle                              ║
║     ✓ Can skip if time runs out                              ║
║                                                               ║
╚═══════════════════════════════════════════════════════════════╝
```

### 4.3. Ví Dụ: Risk Mitigation Plan

**Risk R3**: Checkout timeout under load (Risk Level: 20 - CRITICAL)

**Mitigation Actions**:
```
1. TESTING APPROACH:
   ✓ Performance testing: 10,000 concurrent users
   ✓ Stress testing: Find breaking point
   ✓ Spike testing: Sudden traffic surge
   ✓ Endurance testing: 4-hour sustained load

2. TEST ENVIRONMENT:
   ✓ Production-like environment
   ✓ Load balancer configured
   ✓ Database scaled (read replicas)

3. MONITORING:
   ✓ Response time targets: <2 seconds (95th percentile)
   ✓ CPU/Memory usage monitoring
   ✓ Database query performance

4. CONTINGENCY:
   ✓ Circuit breaker pattern implemented
   ✓ Timeout values configurable
   ✓ Queue system for high traffic

5. ACCEPTANCE CRITERIA:
   ✓ 10K users → Response time <2s
   ✓ No timeout errors
   ✓ 99.9% success rate
```

**Result**: Risk Level reduced from 20 → 8 (Medium)
```
Before: Likelihood=4, Impact=5 → Risk=20
After mitigation: Likelihood=2, Impact=4 → Risk=8
```

---

## 5. RISK-BASED TESTING

### 5.1. Concept

```
╔═══════════════════════════════════════════════════════════════╗
║                RISK-BASED TESTING (RBT)                       ║
╠═══════════════════════════════════════════════════════════════╣
║                                                               ║
║  📖 DEFINITION:                                               ║
║     Test approach sử dụng RISK ANALYSIS để guide testing     ║
║                                                               ║
║  🎯 PRINCIPLES:                                               ║
║                                                               ║
║     HIGH RISK → MORE TESTING                                 ║
║     ├─ More test cases                                       ║
║     ├─ More techniques                                       ║
║     ├─ Experienced testers                                   ║
║     ├─ Earlier testing                                       ║
║     └─ More thorough testing                                 ║
║                                                               ║
║     LOW RISK → LESS TESTING                                  ║
║     ├─ Fewer test cases                                      ║
║     ├─ Basic techniques                                      ║
║     ├─ Can skip if time limited                              ║
║     └─ Lighter testing                                       ║
║                                                               ║
║  ✅ BENEFITS:                                                 ║
║     • Focus resources on high-risk areas                     ║
║     • Better test ROI                                        ║
║     • Stakeholder confidence                                 ║
║     • Transparent decision-making                            ║
║                                                               ║
╚═══════════════════════════════════════════════════════════════╝
```

### 5.2. RBT Process

```
       Product Risk Analysis
               │
      ┌────────┴────────┐
      │                 │
   HIGH RISK        LOW RISK
      │                 │
      ▼                 ▼
┌──────────┐      ┌──────────┐
│  HEAVY   │      │  LIGHT   │
│ TESTING  │      │ TESTING  │
└────┬─────┘      └────┬─────┘
     │                 │
     ├─ More TCs       ├─ Fewer TCs
     ├─ EP+BVA+DT+ST   ├─ EP only
     ├─ Experienced    ├─ Junior OK
     ├─ Early          ├─ Later
     └─ Thorough       └─ Basic
```

### 5.3. Example: Test Intensity Matrix

| Feature | Risk Level | # Test Cases | Techniques | Tester |
|---------|-----------|--------------|------------|---------|
| Payment | 20 (Critical) | 50 | EP, BVA, DT, Exploratory | Senior |
| Search | 12 (High) | 30 | EP, BVA, State | Mid-level |
| Profile | 8 (Medium) | 15 | EP, BVA | Mid-level |
| Wishlist | 4 (Low) | 8 | EP | Junior |
| Share | 3 (Low) | 5 | Smoke only | Junior |

---

## 6. RISK MONITORING & REVIEW

### 6.1. Ongoing Risk Management

```
╔═══════════════════════════════════════════════════════════════╗
║            RISK MONITORING & REVIEW                           ║
╠═══════════════════════════════════════════════════════════════╣
║                                                               ║
║  🔄 CONTINUOUS PROCESS:                                       ║
║                                                               ║
║  1. TRACK RISK STATUS                                        ║
║     → Open, In Progress, Mitigated, Closed                   ║
║                                                               ║
║  2. MEASURE EFFECTIVENESS                                    ║
║     → Did mitigation work?                                   ║
║     → Re-assess risk level                                   ║
║                                                               ║
║  3. IDENTIFY NEW RISKS                                       ║
║     → As project progresses                                  ║
║     → Requirements change                                    ║
║                                                               ║
║  4. UPDATE RISK REGISTER                                     ║
║     → Living document                                        ║
║     → Regular reviews (weekly/sprint)                        ║
║                                                               ║
║  5. COMMUNICATE                                              ║
║     → Status reports                                         ║
║     → Escalate if needed                                     ║
║                                                               ║
╚═══════════════════════════════════════════════════════════════╝
```

### 6.2. Risk Register

```
╔═══════════════════════════════════════════════════════════════╗
║                    RISK REGISTER                              ║
╠═══════════════════════════════════════════════════════════════╣
║                                                               ║
║  Risk ID: R3                                                 ║
║  Risk: Checkout timeout under load                           ║
║  Category: Product Risk - Performance                        ║
║                                                               ║
║  ASSESSMENT:                                                 ║
║    Likelihood: 4 → 2 (after mitigation)                     ║
║    Impact: 5 → 4                                             ║
║    Risk Level: 20 (Critical) → 8 (Medium)                    ║
║                                                               ║
║  MITIGATION:                                                 ║
║    • Performance testing completed ✅                         ║
║    • Load balancer configured ✅                              ║
║    • Response time <2s achieved ✅                            ║
║                                                               ║
║  STATUS: Mitigated (2024-11-20)                              ║
║  OWNER: Performance Engineer                                 ║
║                                                               ║
║  NOTES:                                                      ║
║    Tested with 15K users, all passed.                        ║
║    Continue monitoring in production.                        ║
║                                                               ║
╚═══════════════════════════════════════════════════════════════╝
```

---

## 7. CÂU HỎI ÔN TẬP

### Câu 1 (K2)
Risk level được tính bằng công thức nào?

A. Likelihood + Impact
B. Likelihood × Impact
C. Likelihood - Impact
D. Likelihood / Impact

<details>
<summary>Đáp án</summary>

**B. Likelihood × Impact**

Risk Level = Likelihood (xác suất) × Impact (hậu quả)
</details>

---

### Câu 2 (K2)
Project risk là gì?

A. Risk affecting product quality
B. Risk affecting project activities (schedule, cost, scope)
C. Risk to end users
D. Security vulnerabilities

<details>
<summary>Đáp án</summary>

**B. Risk affecting project activities (schedule, cost, scope)**

Project risks affect the PROJECT PROCESS, not product quality.
</details>

---

### Câu 3 (K2)
Product risk (quality risk) là gì?

A. Schedule delays
B. Budget overruns
C. Software defects affecting product quality
D. Team member leaves

<details>
<summary>Đáp án</summary>

**C. Software defects affecting product quality**

Product risks affect PRODUCT QUALITY (defects, performance, security, etc.).
</details>

---

### Câu 4 (K2)
Example nào là PROJECT risk?

A. SQL injection vulnerability
B. Key tester unavailable
C. Poor application performance
D. Incorrect business logic

<details>
<summary>Đáp án</summary>

**B. Key tester unavailable**

Resource unavailability là project risk. A, C, D là product risks.
</details>

---

### Câu 5 (K3)
Risk có Likelihood=3, Impact=4. Risk Level?

A. 7
B. 12
C. 1
D. 0.75

<details>
<summary>Đáp án</summary>

**B. 12**

Risk Level = 3 × 4 = 12 (Medium-High risk)
</details>

---

### Câu 6 (K2)
Risk-based testing principle?

A. Test everything equally
B. High risk → More testing, Low risk → Less testing
C. Only test high-risk areas
D. Random testing

<details>
<summary>Đáp án</summary>

**B. High risk → More testing, Low risk → Less testing**

RBT allocates effort based on risk level.
</details>

---

## 8. CHECKLIST TỰ ĐÁNH GIÁ

### Risk Basics
- [ ] Hiểu risk definition
- [ ] Tính được Risk Level = Likelihood × Impact
- [ ] Sử dụng risk matrix
- [ ] Biết risk attributes (ID, description, owner, etc.)

### Project vs Product Risks
- [ ] Phân biệt project risks vs product risks
- [ ] Identify examples của mỗi loại
- [ ] Biết ai manage mỗi loại risk

### Product Risk Analysis
- [ ] Thực hiện 4 steps: Identify, Assess, Prioritize, Mitigate
- [ ] Brainstorm risks cho project
- [ ] Assess likelihood và impact
- [ ] Create risk register

### Risk Control
- [ ] Hiểu 4 strategies: Mitigate, Transfer, Accept, Avoid
- [ ] Apply testing để mitigate risks
- [ ] Adjust test intensity based on risk
- [ ] Monitor và update risk status

### Risk-Based Testing
- [ ] Apply RBT principles
- [ ] Allocate test effort based on risk
- [ ] Use risk analysis để prioritize testing

---

## TỔNG KẾT

```
╔═══════════════════════════════════════════════════════════════╗
║                    KEY TAKEAWAYS                              ║
╠═══════════════════════════════════════════════════════════════╣
║                                                               ║
║  1. RISK DEFINITION:                                         ║
║     → Risk = Potential future harmful event                  ║
║     → Risk Level = Likelihood × Impact                       ║
║                                                               ║
║  2. PROJECT RISKS:                                           ║
║     → Affect project activities (schedule, cost, scope)      ║
║     → Example: Resource unavailable, budget cuts             ║
║                                                               ║
║  3. PRODUCT RISKS (QUALITY RISKS):                           ║
║     → Affect product quality                                 ║
║     → Example: Defects, performance, security issues         ║
║                                                               ║
║  4. PRODUCT RISK ANALYSIS:                                   ║
║     → Identify → Assess → Prioritize → Mitigate              ║
║     → Use risk matrix để assess                              ║
║                                                               ║
║  5. RISK CONTROL:                                            ║
║     → Mitigate (reduce), Transfer, Accept, Avoid             ║
║     → Testing is key mitigation activity                     ║
║                                                               ║
║  6. RISK-BASED TESTING:                                      ║
║     → HIGH RISK → MORE TESTING                               ║
║     → LOW RISK → LESS TESTING                                ║
║     → Optimize test effort                                   ║
║                                                               ║
╚═══════════════════════════════════════════════════════════════╝
```

---

**Tiếp theo**: [Bài Tập Giai Đoạn 6](./bai-tap-giai-doan-6.md)

---

**Version**: 1.0.0
**Last Updated**: November 2025
