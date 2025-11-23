# Project 2: Mobile Banking App Testing (PayVN)

## 🎯 Mục Tiêu Project

Áp dụng kiến thức testing vào domain **Mobile Banking** với focus đặc biệt vào:
- **Security Testing** (authentication, authorization, encryption)
- **Performance Testing** (response time, concurrent users)
- **Usability Testing** (mobile UI/UX)
- **Compliance Testing** (banking regulations, PCI DSS)

**Thời gian**: 5-7 ngày

---

## 📋 Project Overview

### About PayVN

**PayVN** là ứng dụng ví điện tử và mobile banking tương tự Momo, VNPay, cho phép:
- Chuyển tiền nội bộ và liên ngân hàng
- Thanh toán hóa đơn (điện, nước, internet, điện thoại)
- Nạp tiền điện thoại
- Mua mã thẻ game
- Quản lý thẻ ngân hàng liên kết
- Lịch sử giao dịch và báo cáo

### Project Context

**Company**: PayVN Fintech Startup
**Release**: v3.0 - Major security and performance upgrade
**Timeline**: 4 weeks (Sprint 1-2)
**Compliance**: Must comply with SBV (State Bank of Vietnam) regulations

### Team
- 1 Test Lead (you)
- 2 Manual Testers
- 1 Security Tester
- 1 Performance Tester
- 5 Developers
- 1 Product Manager

### Scope

**In Scope**:
✅ User authentication (biometric, PIN, password)
✅ Money transfer (internal, bank transfer)
✅ Bill payment
✅ Top-up (phone, game cards)
✅ Transaction history
✅ Security features

**Out of Scope**:
❌ Investment features (stocks, crypto)
❌ Loan services
❌ Insurance
❌ iOS version (Android only this release)

---

## 📖 Requirements

### Epic 1: User Authentication & Security

**US-101: User Registration & KYC**
```
As a new user
I want to register and verify my identity
So that I can use PayVN services

Acceptance Criteria:
- Register with phone number (Vietnamese format: 09x, 08x, etc.)
- OTP verification via SMS
- Upload ID card (CMND/CCCD) front & back photos
- Selfie with ID card
- Face matching with ID (>95% confidence)
- KYC approval within 24 hours (business days)
- Account tiers:
  - Tier 1 (Basic): No KYC, max 10M VND balance
  - Tier 2 (Verified): KYC approved, max 100M VND balance

Security:
- Encrypt ID card images
- Store in secure cloud storage
- Cannot reuse same ID for multiple accounts
```

**US-102: Biometric Authentication**
```
As a user
I want to login with fingerprint/face recognition
So that I can access my account securely and conveniently

Acceptance Criteria:
- Support Fingerprint (Android Biometric API)
- Support Face Recognition (if device supports)
- Fallback to PIN if biometric fails 3 times
- Biometric data stored locally on device (not on server)
- Option to enable/disable biometric in settings
- Re-authenticate after 5 minutes inactive
```

**US-103: PIN & Password Security**
```
As a user
I want secure PIN and password
So that my account is protected

Acceptance Criteria:
- Login PIN: 6 digits
- Transaction PIN: 6 digits (different from login PIN)
- Password: 8-20 chars, must have uppercase, lowercase, number, special char
- Account locked after 5 failed attempts (30 minutes)
- PIN/Password encryption (bcrypt, salt)
- Cannot reuse last 3 passwords
- Change PIN/password requires old one + OTP
```

### Epic 2: Money Transfer

**US-201: Internal Transfer (PayVN to PayVN)**
```
As a user
I want to transfer money to another PayVN user
So that I can send money conveniently

Acceptance Criteria:
- Input: Recipient phone number or scan QR code
- Amount: 10,000 - 50,000,000 VND
- Transaction PIN required
- Instant transfer (< 2s)
- Fee: Free
- Transaction limit:
  - Per transaction: 50M VND
  - Daily: 100M VND (Tier 1), 500M VND (Tier 2)
- Confirmation screen before executing
- Receipt with transaction ID
- Push notification to both sender & recipient
```

**US-202: Bank Transfer (Interbank)**
```
As a user
I want to transfer money to bank accounts
So that I can send to users without PayVN

Acceptance Criteria:
- Input: Bank, Account number, Account name (auto-lookup)
- Amount: 10,000 - 500,000,000 VND
- Transfer types:
  - Fast transfer (24/7, < 30s): Fee 5,000 VND
  - Normal transfer (9AM-5PM, bank hours): Free
- Account name verification before transfer
- Transaction PIN required
- Scheduled transfer option
- Save beneficiaries
- Transaction limit:
  - Per transaction: 500M VND
  - Daily: 2,000M VND (Tier 2 only)
```

**US-203: QR Payment**
```
As a user
I want to pay via QR code
So that I can pay at merchants quickly

Acceptance Criteria:
- Scan QR code (VietQR standard)
- Auto-fill: Merchant, Amount (if in QR)
- Confirm payment with PIN
- Instant payment (< 2s)
- Digital receipt
- Fee: Free for users, 1% for merchants
```

### Epic 3: Bill Payment

**US-301: Pay Utility Bills**
```
As a user
I want to pay utility bills (electricity, water, internet)
So that I can pay bills conveniently

Acceptance Criteria:
- Supported billers: EVN, VNPT, FPT, Viettel, VTV
- Input: Customer code
- Auto-lookup: Customer name, Amount due
- Save biller for future payments
- Transaction PIN required
- Instant payment
- E-receipt sent via email
- Fee: 1,000 - 5,000 VND depending on biller
```

**US-302: Phone Top-up**
```
As a user
I want to top-up phone credit
So that I can recharge my phone

Acceptance Criteria:
- Carriers: Viettel, Vinaphone, Mobifone
- Amounts: 10,000 / 20,000 / 50,000 / 100,000 / 200,000 / 500,000
- Input: Phone number (auto-detect carrier)
- Instant top-up (< 5s)
- Save frequent numbers
- Discount: 1-2% depending on carrier and amount
```

### Epic 4: Transaction Management

**US-401: Transaction History**
```
As a user
I want to view my transaction history
So that I can track my spending

Acceptance Criteria:
- View all transactions (sent, received, bills, top-ups)
- Filter by:
  - Date range
  - Type (transfer, bill, top-up)
  - Status (success, failed, pending)
- Search by: Transaction ID, recipient, amount
- Sort: Date (newest first default)
- Display: Date, Time, Type, Amount, Status, Balance
- Export to PDF/Excel (last 3 months)
- Pagination: 20 transactions per page
```

**US-402: Transaction Receipt**
```
As a user
I want to view and share transaction receipts
So that I have proof of payment

Acceptance Criteria:
- Receipt includes:
  - Transaction ID
  - Date & Time
  - From/To
  - Amount, Fee
  - Status
  - PayVN signature/seal
- Download as PDF/Image
- Share via email, social media
- Print-friendly format
```

### Epic 5: Account Management

**US-501: Link Bank Card**
```
As a user
I want to link my bank card
So that I can top-up my PayVN wallet

Acceptance Criteria:
- Supported banks: 20+ major Vietnamese banks
- Input: Card number, Card holder name, Expiry, CVV
- Card verification (1,000 VND authorization + release)
- Save card for future use
- Max 5 linked cards per account
- Can delete linked cards
- Card data encrypted (PCI DSS compliant)
```

**US-502: Wallet Top-up**
```
As a user
I want to top-up my PayVN wallet
So that I have money to transact

Acceptance Criteria:
- Methods:
  - Linked bank card: Instant, fee 1.5%
  - Bank transfer: Manual, check bank statement, free
  - Cash at agent: Instant, fee 1%
- Amount: 50,000 - 50,000,000 VND
- Min balance: 0 VND
- Max balance:
  - Tier 1: 10M VND
  - Tier 2: 100M VND
```

---

## 🔒 Security Requirements (Critical)

### Security Controls

```
┌─────────────────────────────────────────────────────────┐
│           SECURITY REQUIREMENTS                         │
├─────────────────────────────────────────────────────────┤
│                                                         │
│  1. AUTHENTICATION                                      │
│     • Multi-factor authentication (MFA)                 │
│     • Biometric + PIN                                   │
│     • Session timeout: 5 minutes inactive               │
│     • Account lockout: 5 failed attempts                │
│                                                         │
│  2. AUTHORIZATION                                       │
│     • Role-based access control (RBAC)                  │
│     • Transaction limits by tier                        │
│     • Cannot access other user's data                   │
│                                                         │
│  3. DATA PROTECTION                                     │
│     • Encryption at rest (AES-256)                      │
│     • Encryption in transit (TLS 1.3)                   │
│     • Sensitive data masking (PAN, PIN)                 │
│     • No sensitive data in logs                         │
│                                                         │
│  4. TRANSACTION SECURITY                                │
│     • Transaction PIN required for all transactions     │
│     • Transaction signing (digital signature)           │
│     • Fraud detection (anomaly detection)               │
│     • Transaction velocity checks                       │
│                                                         │
│  5. COMPLIANCE                                          │
│     • PCI DSS Level 1 (for card data)                   │
│     • SBV (State Bank of Vietnam) regulations           │
│     • GDPR (for user data)                              │
│     • ISO 27001 (information security)                  │
│                                                         │
│  6. VULNERABILITY PROTECTION                            │
│     • Protection against:                               │
│       - SQL Injection                                   │
│       - XSS (Cross-Site Scripting)                      │
│       - CSRF (Cross-Site Request Forgery)               │
│       - Man-in-the-Middle attacks                       │
│       - Brute force attacks                             │
│       - Session hijacking                               │
│                                                         │
└─────────────────────────────────────────────────────────┘
```

---

## 📊 Performance Requirements

```
┌─────────────────────────────────────────────────────────┐
│         PERFORMANCE REQUIREMENTS                        │
├─────────────────────────────────────────────────────────┤
│                                                         │
│  RESPONSE TIME (95th percentile):                       │
│  • Login: < 1s                                          │
│  • Balance check: < 0.5s                                │
│  • Internal transfer: < 2s                              │
│  • Bank transfer: < 30s (fast), < 24h (normal)          │
│  • Bill payment: < 3s                                   │
│  • Transaction history load: < 1s                       │
│                                                         │
│  THROUGHPUT:                                            │
│  • Support 10,000 concurrent users                      │
│  • Peak: 1,000 transactions/second                      │
│                                                         │
│  AVAILABILITY:                                          │
│  • Uptime: 99.9% (< 8.76 hours downtime/year)           │
│  • Planned maintenance: Max 4 hours/month               │
│                                                         │
│  SCALABILITY:                                           │
│  • Support up to 5 million users                        │
│  • Database: Handle 100M+ transactions                  │
│                                                         │
│  RELIABILITY:                                           │
│  • Mean Time Between Failures (MTBF): > 720 hours       │
│  • Mean Time To Repair (MTTR): < 1 hour                 │
│                                                         │
└─────────────────────────────────────────────────────────┘
```

---

## 🧪 Test Strategy

### Test Levels

```
1. COMPONENT TESTING (By Developers)
   • Unit tests: 85% code coverage
   • API tests: All endpoints
   • Tools: JUnit, Mockito

2. INTEGRATION TESTING (By Test Team)
   • API integration: Payment gateway, Banks
   • Database integration
   • Third-party services (SMS, KYC)
   • Tools: Postman, RestAssured

3. SYSTEM TESTING (By Test Team)
   • Functional testing (all user stories)
   • Security testing
   • Performance testing
   • Usability testing
   • Tools: Appium, JMeter, OWASP ZAP

4. ACCEPTANCE TESTING (By Business + Users)
   • UAT with beta users (100 users)
   • Compliance validation
   • Pilot launch (5% users)
```

### Test Types Focus

```
┌──────────────────────┬─────────┬──────────────────────┐
│ Test Type            │Coverage │ Tools                │
├──────────────────────┼─────────┼──────────────────────┤
│ FUNCTIONAL           │  100%   │ Appium, Manual       │
│ SECURITY             │  HIGH   │ OWASP ZAP, Burp      │
│ PERFORMANCE          │  ALL    │ JMeter, LoadRunner   │
│ USABILITY            │  HIGH   │ Manual, UserTesting  │
│ COMPATIBILITY        │  TOP 10 │ Real devices + Cloud │
│ REGRESSION           │  AUTO   │ Appium suite         │
└──────────────────────┴─────────┴──────────────────────┘

Devices to test:
• Android 11, 12, 13, 14
• Screen sizes: Small (< 5"), Medium (5-6"), Large (> 6")
• Top 10 devices in Vietnam:
  - Samsung Galaxy A series
  - Samsung Galaxy S series
  - Xiaomi Redmi
  - Oppo A series
  - Vivo Y series
```

---

## 🔒 Security Test Cases

### Test Case: SQL Injection Attack

```
TC-SEC-001: SQL Injection in Login - Phone Number Field
───────────────────────────────────────────────────────
Objective: Verify app is protected against SQL injection
Technique: Experience-based (Security testing)
Category: OWASP Top 10 - Injection
Severity: CRITICAL

Test Data:
  Phone: 0912345678' OR '1'='1' --
  PIN: 123456

Steps:
  1. Open PayVN app
  2. Enter phone: 0912345678' OR '1'='1' --
  3. Enter PIN: 123456
  4. Click "Login"

Expected Result:
  ❌ Login fails with error: "Invalid phone number"
  ❌ SQL injection attempt logged
  ❌ No data exposed
  ❌ No access granted

Attack Variations to Test:
  • ' OR '1'='1
  • '; DROP TABLE users; --
  • admin'--
  • ' UNION SELECT * FROM users --

Priority: P0 (Security critical)
───────────────────────────────────────────────────────

TC-SEC-002: XSS (Cross-Site Scripting) in Transaction Note
───────────────────────────────────────────────────────
Objective: Verify app sanitizes user input
Technique: Security testing
Category: OWASP Top 10 - XSS

Test Data:
  Recipient: 0987654321
  Amount: 100,000
  Note: <script>alert('XSS')</script>

Steps:
  1. Initiate transfer
  2. Enter note: <script>alert('XSS')</script>
  3. Complete transfer
  4. View transaction history
  5. Recipient views transaction

Expected Result:
  ❌ Script not executed
  ✅ Note displayed as plain text: <script>alert('XSS')</script>
  ❌ No alert popup
  ✅ Input sanitized

Priority: P1
───────────────────────────────────────────────────────

TC-SEC-003: Session Hijacking via Token Theft
───────────────────────────────────────────────────────
Objective: Verify session tokens are secure
Technique: Security testing
Category: Authentication security

Steps:
  1. Login to app (Device A)
  2. Intercept auth token (using proxy)
  3. Copy token to Device B
  4. Try to access API with stolen token

Expected Result:
  ❌ Token should have additional binding (device ID, IP)
  ❌ Device B request fails: "Invalid session"
  ✅ Token expires after 5 mins inactive
  ✅ Token invalidated on logout

Priority: P0
───────────────────────────────────────────────────────

TC-SEC-004: Brute Force Attack - PIN Guessing
───────────────────────────────────────────────────────
Objective: Verify account lockout mechanism
Technique: Negative testing

Test Data:
  Phone: Valid user phone
  PIN: Try 000000, 111111, 123456, etc.

Steps:
  1. Enter valid phone
  2. Enter wrong PIN: 000000 (Attempt 1)
  3. Enter wrong PIN: 111111 (Attempt 2)
  4. Enter wrong PIN: 123456 (Attempt 3)
  5. Enter wrong PIN: 654321 (Attempt 4)
  6. Enter wrong PIN: 000001 (Attempt 5)
  7. Try 6th attempt

Expected Result:
  ❌ After 5 failed attempts: Account locked
  ❌ Lockout message: "Too many failed attempts. Try again in 30 minutes."
  ❌ Cannot login for 30 minutes (even with correct PIN)
  ✅ Lockout notification sent via SMS
  ✅ Security log recorded

Priority: P0
───────────────────────────────────────────────────────

TC-SEC-005: Man-in-the-Middle Attack - Insecure Connection
───────────────────────────────────────────────────────
Objective: Verify all API calls use HTTPS/TLS
Technique: Security testing
Tools: Charles Proxy, Burp Suite

Steps:
  1. Setup proxy to intercept traffic
  2. Login to app
  3. Perform transfer
  4. Inspect network traffic

Expected Result:
  ✅ All API calls use HTTPS (TLS 1.3)
  ✅ Certificate pinning implemented
  ❌ No sensitive data in cleartext
  ✅ If proxy detected, app shows warning

Priority: P0
───────────────────────────────────────────────────────
```

---

## ⚡ Performance Test Cases

### Test Case: Load Testing - Concurrent Users

```
TC-PERF-001: Load Test - 10,000 Concurrent Users
───────────────────────────────────────────────────────
Objective: Verify system handles 10K concurrent users
Technique: Performance testing (Load)
Tool: JMeter

Test Scenario:
• Users: 10,000 concurrent
• Duration: 1 hour
• Ramp-up: 10 minutes (1,000 users/min)
• Actions:
  - Login (20%)
  - Check balance (30%)
  - Transfer (25%)
  - Bill payment (15%)
  - Transaction history (10%)

Performance Metrics:
┌────────────────────────┬──────────┬────────────┐
│ Transaction            │ Target   │ Max Accept │
├────────────────────────┼──────────┼────────────┤
│ Login                  │ < 1s     │ < 2s       │
│ Balance check          │ < 0.5s   │ < 1s       │
│ Internal transfer      │ < 2s     │ < 3s       │
│ Bill payment           │ < 3s     │ < 5s       │
│ Transaction history    │ < 1s     │ < 2s       │
└────────────────────────┴──────────┴────────────┘

Expected Result:
  ✅ 95th percentile response time within target
  ✅ Error rate < 1%
  ✅ CPU usage < 80%
  ✅ Memory usage < 85%
  ✅ No memory leaks
  ✅ Database connections stable

Pass Criteria:
  • All response times meet target
  • Error rate < 1%
  • System stable throughout test

Priority: P0 (Before production)
───────────────────────────────────────────────────────

TC-PERF-002: Stress Test - Find Breaking Point
───────────────────────────────────────────────────────
Objective: Identify system capacity limits
Technique: Stress testing
Tool: JMeter

Test Scenario:
• Start: 5,000 users
• Increment: +1,000 users every 5 minutes
• Continue until: System breaks or reaches 20,000 users
• Monitor: Response time, error rate, resource usage

Expected Result:
  ✅ System should gracefully degrade
  ✅ Error messages shown to users (not crashes)
  ✅ Identify breaking point
  ✅ Auto-scaling triggers (if configured)

Documentation:
  • Breaking point: X users
  • Bottleneck: Database / API / Network
  • Recommendations for scaling

Priority: P1
───────────────────────────────────────────────────────

TC-PERF-003: Spike Test - Sudden Traffic Surge
───────────────────────────────────────────────────────
Objective: Verify system handles sudden traffic spikes
Technique: Spike testing
Scenario: Flash sale or viral promotion

Test Scenario:
• Normal load: 2,000 users
• Spike: Suddenly jump to 15,000 users
• Duration: Maintain spike for 10 minutes
• Return: Drop back to 2,000 users

Expected Result:
  ✅ System handles spike without crash
  ⚠️  Response time may degrade temporarily (< 5s)
  ✅ Recovers quickly after spike
  ✅ No data loss or corruption

Priority: P1
───────────────────────────────────────────────────────

TC-PERF-004: Endurance Test (Soak Test)
───────────────────────────────────────────────────────
Objective: Verify system stability over extended period
Technique: Endurance testing
Duration: 24 hours

Test Scenario:
• Users: 5,000 concurrent (normal load)
• Duration: 24 hours continuous
• Monitor: Memory leaks, resource exhaustion

Expected Result:
  ✅ Response times remain stable
  ✅ No memory leaks (memory usage stable)
  ✅ No resource exhaustion
  ✅ No crashes or errors
  ✅ System runs continuously for 24h

Priority: P1 (Before production)
───────────────────────────────────────────────────────
```

---

## 📱 Usability Test Cases

### Test Case: First-Time User Experience

```
TC-USABILITY-001: First-Time User Onboarding
───────────────────────────────────────────────────────
Objective: Evaluate ease of registration for new users
Technique: Usability testing (Manual)
Participants: 10 users (age 18-50, various tech proficiency)

Test Scenario:
  Task: "Register for PayVN account and complete KYC"

  Success Criteria:
    • User completes registration without help
    • User uploads ID and selfie correctly
    • Time to complete: < 10 minutes

Metrics to Measure:
  • Task completion rate
  • Time to complete
  • Number of errors
  • User satisfaction (1-5 scale)
  • Confusion points

Observations:
  • Did user understand instructions?
  • Where did user get stuck?
  • Any UI elements confusing?
  • Any errors or bugs encountered?

Expected Result:
  ✅ 90% task completion rate
  ✅ Average time: 5-8 minutes
  ✅ User satisfaction: ≥ 4/5
  ✅ < 2 errors per user

Post-Test Questions:
  1. How easy was the registration process? (1-5)
  2. Any confusing steps?
  3. What would you improve?

Priority: P1
───────────────────────────────────────────────────────

TC-USABILITY-002: Money Transfer Flow
───────────────────────────────────────────────────────
Objective: Evaluate ease of transferring money
Technique: Usability testing

Test Scenario:
  Task: "Transfer 100,000 VND to phone: 0987654321"

Success Criteria:
  • User completes transfer without errors
  • User feels confident about transaction
  • Time to complete: < 1 minute

Usability Checklist:
  [ ] Clear input labels
  [ ] Amount input easy to use
  [ ] Confirmation screen clear
  [ ] Error messages helpful
  [ ] Success feedback clear

Expected Result:
  ✅ 100% task completion
  ✅ Average time: 30-45 seconds
  ✅ User confidence: High
  ✅ Satisfaction: ≥ 4.5/5

Priority: P0 (Core feature)
───────────────────────────────────────────────────────
```

---

## 🧪 Sample Test Scenarios

### Scenario 1: End-to-End Money Transfer

```
TEST SCENARIO: Complete Money Transfer Flow
───────────────────────────────────────────────────────

Objective: Validate complete transfer process from login to receipt

Pre-conditions:
  • User registered and KYC approved (Tier 2)
  • Wallet balance: 1,000,000 VND
  • Recipient phone: 0987654321 (registered PayVN user)

Test Steps:

1. LOGIN
   • Open app
   • Enter phone: 0912345678
   • Use fingerprint to login
   Expected: Dashboard appears < 1s

2. NAVIGATE TO TRANSFER
   • Tap "Transfer Money" button
   • Select "To PayVN Account"
   Expected: Transfer form appears

3. ENTER TRANSFER DETAILS
   • Enter recipient phone: 0987654321
   • System auto-fills: Nguyen Van B (recipient name)
   • Enter amount: 500,000
   • Add note: "Payment for coffee"
   Expected: All fields validated, "Continue" enabled

4. CONFIRMATION
   • Tap "Continue"
   • Review confirmation screen:
     - From: 0912345678 (You)
     - To: 0987654321 (Nguyen Van B)
     - Amount: 500,000 VND
     - Fee: 0 VND (free)
     - Total: 500,000 VND
     - New balance: 500,000 VND
   Expected: All info correct

5. AUTHORIZATION
   • Tap "Confirm"
   • Enter transaction PIN: 234567
   Expected: Processing screen appears

6. EXECUTION
   • System processes transfer
   Expected: < 2s processing time

7. SUCCESS
   • Success screen appears with:
     - Transaction ID: TXN123456789
     - Status: Success
     - Date/Time stamp
     - "Download Receipt" button
     - "Done" button
   • Push notification sent to sender
   • Push notification sent to recipient
   Expected: Clear success indication

8. RECEIPT
   • Tap "Download Receipt"
   • Receipt PDF generated with all details
   Expected: Receipt downloadable and shareable

9. BALANCE UPDATE
   • Tap "Done" → Return to dashboard
   • Check wallet balance: 500,000 VND
   Expected: Balance updated correctly

10. TRANSACTION HISTORY
    • Tap "Transaction History"
    • Find transfer in list
    • Verify all details correct
    Expected: Transfer appears in history

Post-conditions:
  ✅ Sender balance: 500,000 VND
  ✅ Recipient balance: +500,000 VND
  ✅ Transaction recorded in database
  ✅ Both parties notified
  ✅ Receipt available

Test Result: ____ PASS / FAIL
Executed by: ________ Date: ________
───────────────────────────────────────────────────────
```

---

## 📊 Risk Analysis - Banking Domain

```
═══════════════════════════════════════════════════════════
RISK ANALYSIS - PAYVN v3.0
═══════════════════════════════════════════════════════════

PRODUCT RISKS (HIGH PRIORITY):

┌──────┬─────────────────────────┬───┬───────┬──────┬─────────┐
│ ID   │ Risk                    │ L │Impact │ Risk │ Testing │
├──────┼─────────────────────────┼───┼───────┼──────┼─────────┤
│ PR-01│ Unauthorized access     │ 3 │   5   │  15  │ Security│
│      │ (hacked accounts)       │   │       │(HIGH)│ testing │
│      │                         │   │       │      │ Pen test│
│      │                         │   │       │      │ MFA test│
├──────┼─────────────────────────┼───┼───────┼──────┼─────────┤
│ PR-02│ Transaction fraud       │ 3 │   5   │  15  │ Fraud   │
│      │ (money stolen)          │   │       │(HIGH)│ scenario│
│      │                         │   │       │      │ Anomaly │
│      │                         │   │       │      │ detect  │
├──────┼─────────────────────────┼───┼───────┼──────┼─────────┤
│ PR-03│ Data breach             │ 2 │   5   │  10  │ Security│
│      │ (user data leaked)      │   │       │ (MED)│ scan    │
│      │                         │   │       │      │ Pen test│
├──────┼─────────────────────────┼───┼───────┼──────┼─────────┤
│ PR-04│ Payment gateway failure │ 4 │   4   │  16  │ API test│
│      │ (transfers fail)        │   │       │(HIGH)│ Failover│
│      │                         │   │       │      │ test    │
├──────┼─────────────────────────┼───┼───────┼──────┼─────────┤
│ PR-05│ System downtime         │ 3 │   4   │  12  │ Load    │
│      │ (during peak hours)     │   │       │(HIGH)│ testing │
│      │                         │   │       │      │ Stress  │
│      │                         │   │       │      │ test    │
├──────┼─────────────────────────┼───┼───────┼──────┼─────────┤
│ PR-06│ Slow performance        │ 4 │   3   │  12  │ Perf    │
│      │ (user frustration)      │   │       │(HIGH)│ testing │
│      │                         │   │       │      │ Real dev│
├──────┼─────────────────────────┼───┼───────┼──────┼─────────┤
│ PR-07│ Biometric bypass        │ 2 │   5   │  10  │ Security│
│      │ (fake fingerprint)      │   │       │ (MED)│ test    │
│      │                         │   │       │      │ Attack  │
│      │                         │   │       │      │ scenario│
├──────┼─────────────────────────┼───┼───────┼──────┼─────────┤
│ PR-08│ Incorrect balance       │ 2 │   5   │  10  │ Data    │
│      │ calculation             │   │       │ (MED)│ accuracy│
│      │                         │   │       │      │ test    │
├──────┼─────────────────────────┼───┼───────┼──────┼─────────┤
│ PR-09│ Double transaction      │ 2 │   4   │  8   │ Race    │
│      │ (user charged twice)    │   │       │ (MED)│ conditn │
│      │                         │   │       │      │ Concurr │
├──────┼─────────────────────────┼───┼───────┼──────┼─────────┤
│ PR-10│ KYC fraud               │ 3 │   4   │  12  │ Face    │
│      │ (fake ID, face match)   │   │       │(HIGH)│ matching│
│      │                         │   │       │      │ ML test │
└──────┴─────────────────────────┴───┴───────┴──────┴─────────┘

TESTING STRATEGY BY RISK:

HIGH RISK (15-16):
→ Extensive testing (>100 test cases per risk)
→ Security penetration testing
→ Load testing with 2x expected peak
→ Manual + Automated
→ Beta testing with real users

MEDIUM RISK (8-12):
→ Comprehensive testing (50-100 TCs)
→ Automated regression
→ Manual exploratory testing
→ Beta testing

═══════════════════════════════════════════════════════════
```

---

## 📋 Deliverables Checklist

```
┌─────────────────────────────────────────────────────────┐
│     PROJECT 2 DELIVERABLES - MOBILE BANKING            │
├─────────────────────────────────────────────────────────┤
│                                                         │
│  PLANNING & DESIGN:                                     │
│  [ ] Test Plan (Banking-specific)                       │
│  [ ] Security Test Plan                                 │
│  [ ] Performance Test Plan                              │
│  [ ] Risk Analysis (Banking risks)                      │
│  [ ] Test Environment Setup (Real devices)              │
│                                                         │
│  TEST CASES:                                            │
│  [ ] Functional Test Cases (250+ TCs)                   │
│  [ ] Security Test Cases (50+ TCs)                      │
│  [ ] Performance Test Cases (10+ scenarios)             │
│  [ ] Usability Test Cases (10+ scenarios)               │
│  [ ] Compatibility Test Cases (10 devices)              │
│                                                         │
│  EXECUTION:                                             │
│  [ ] Test Execution Logs                                │
│  [ ] Security Test Report (OWASP Top 10)                │
│  [ ] Performance Test Results (JMeter)                  │
│  [ ] Usability Test Findings                            │
│  [ ] Defect Reports (Security, Performance)             │
│                                                         │
│  COMPLETION:                                            │
│  [ ] Test Completion Report                             │
│  [ ] Security Assessment Report                         │
│  [ ] Performance Benchmark Report                       │
│  [ ] Compliance Checklist (PCI DSS, SBV)                │
│  [ ] Production Readiness Report                        │
│                                                         │
└─────────────────────────────────────────────────────────┘
```

---

## 🎯 Key Differences from E-commerce Project

| Aspect | E-commerce | Mobile Banking |
|--------|------------|----------------|
| **Domain** | Retail | Financial Services |
| **Security** | Standard | Critical (PCI DSS, SBV) |
| **Performance** | Important | Mission-critical |
| **Compliance** | Minimal | High (Regulations) |
| **Usability** | Standard | High (Mobile-first) |
| **Risk** | Medium | High (Money involved) |
| **Test Focus** | Functional | Security + Performance |
| **User Impact** | Convenience | Financial loss if bugs |

---

## 📚 Learning Outcomes

After completing this project, you'll have experience in:

✅ **Security Testing**
   - OWASP Top 10
   - Penetration testing concepts
   - Authentication/Authorization testing
   - Data encryption validation

✅ **Performance Testing**
   - Load testing with JMeter
   - Stress testing
   - Spike testing
   - Endurance testing
   - Performance metrics interpretation

✅ **Mobile Testing**
   - Android testing
   - Biometric testing
   - Mobile UI/UX testing
   - Device compatibility

✅ **Compliance Testing**
   - Understanding regulations
   - Compliance checklists
   - Audit preparation

✅ **Domain Knowledge**
   - Banking/Fintech domain
   - Payment systems
   - KYC/AML processes

---

**Next**: Project 3 - Education Platform Testing

**Good luck with your Mobile Banking testing project! 🏦🔒**
