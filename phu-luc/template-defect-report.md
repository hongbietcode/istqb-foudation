# TEMPLATE: DEFECT REPORT (BUG REPORT)

## TEMPLATE CƠ BẢN

```
DEFECT ID: BUG-[NUMBER]
Example: BUG-1234

TITLE: [Mô tả ngắn gọn defect]
Example: Order status incorrect after successful payment

REPORTED BY: [Tên tester]
REPORTED DATE: [YYYY-MM-DD]

SEVERITY: [Critical / High / Medium / Low]
PRIORITY: [Critical / High / Medium / Low]

STATUS: [New / Open / In Progress / Fixed / Retest / Closed / Deferred / Rejected]

ENVIRONMENT:
- Application: [Name & Version]
- OS: [Windows 11 / macOS 14 / Ubuntu 22.04]
- Browser: [Chrome 118 / Firefox 115 / Safari 17]
- Database: [PostgreSQL 14 / MySQL 8.0]
- Test Environment: [Dev / Test / Staging]

DESCRIPTION:
[Detailed description of the defect]

STEPS TO REPRODUCE:
1. [Step 1]
2. [Step 2]
3. [Step 3]
...

EXPECTED RESULT:
[What should happen]

ACTUAL RESULT:
[What actually happens]

ATTACHMENTS:
- Screenshot: [filename.png]
- Video: [screenrecording.mp4]
- Logs: [error-log.txt]

TEST CASE ID: [TC-MODULE-###]

ASSIGNED TO: [Developer name]

FOUND IN VERSION: [v1.2.3]
FIXED IN VERSION: [v1.2.4]

COMMENTS:
[Additional notes, workarounds, discussions]
```

---

## EXAMPLE 1: Critical Bug - Payment Issue

```
DEFECT ID: BUG-1001

TITLE: Double charge when user clicks "Pay Now" button twice

REPORTED BY: Nguyen Van Tester
REPORTED DATE: 2024-11-23 14:30

SEVERITY: Critical
PRIORITY: Critical

STATUS: Open → In Progress

ENVIRONMENT:
- Application: E-commerce Website v2.3.0
- OS: Windows 11 Pro
- Browser: Chrome 118.0.5993.88
- Database: PostgreSQL 14.5
- Test Environment: Staging
- URL: https://staging.shop.example.com

DESCRIPTION:
When user clicks "Pay Now" button multiple times quickly during
checkout process, system processes payment multiple times,
resulting in double/triple charges to customer's credit card.

No debounce mechanism implemented on payment button.

STEPS TO REPRODUCE:
1. Login với account: user@test.com / Pass123!
2. Add product to cart (iPhone 15 Pro - 28,000,000đ)
3. Navigate to checkout page
4. Fill shipping information:
   - Name: Test User
   - Address: 123 Nguyen Hue, Q1, HCMC
   - Phone: 0901234567
5. Select payment method: Credit Card
6. Enter credit card details:
   - Card Number: 4111 1111 1111 1111 (test card)
   - Expiry: 12/25
   - CVV: 123
7. Click "Pay Now" button TWICE quickly (within 1 second)
8. Check order history page

EXPECTED RESULT:
- Only ONE payment transaction processed
- Only ONE order created
- Charge amount: 28,000,000đ (once)
- Order ID: ORD-12345
- Payment button should be disabled after first click to prevent
  double submission

ACTUAL RESULT:
- TWO payment transactions processed ❌
- TWO orders created: ORD-12345, ORD-12346 ❌
- Total charged: 56,000,000đ (28M × 2) ❌
- No UI feedback to prevent second click
- Customer complained về double charge

IMPACT:
- Financial loss for customers
- Customer trust damaged
- Refund processing overhead
- Potential legal issues
- Reproducibility: 100% (consistent)

ATTACHMENTS:
- Screenshot-1: [double-orders-in-history.png]
- Screenshot-2: [credit-card-statement-double-charge.png]
- Video: [double-click-payment-bug.mp4]
- Network logs: [payment-api-calls.har]

TEST CASE ID: TC-PAYMENT-005

ROOT CAUSE (After analysis):
- No debounce on payment button
- No idempotency check in backend API
- No transaction locking mechanism

SUGGESTED FIX:
1. Frontend: Add debounce (3 seconds) on payment button
2. Frontend: Disable button after first click
3. Backend: Implement idempotency key for payment API
4. Backend: Add transaction locking

ASSIGNED TO: Tran Van Developer
ASSIGNED DATE: 2024-11-23 15:00

FOUND IN VERSION: v2.3.0
TARGET FIX VERSION: v2.3.1 (Hotfix)

COMMENTS:
[2024-11-23 16:00] Dev confirmed bug, working on fix
[2024-11-23 18:30] Fix deployed to test environment
[2024-11-24 09:00] Retest: PASSED, bug fixed
```

---

## EXAMPLE 2: High Severity - Data Loss

```
DEFECT ID: BUG-1002

TITLE: User profile data lost after session timeout

REPORTED BY: Le Thi Tester
REPORTED DATE: 2024-11-23

SEVERITY: High
PRIORITY: High

STATUS: New

ENVIRONMENT:
- Application: User Management System v1.5.2
- OS: macOS 14.1
- Browser: Safari 17.0
- Test Environment: Test Server
- Session Timeout: 30 minutes (configured)

DESCRIPTION:
When user edits profile information and session expires before
saving, all entered data is lost upon session renewal. No
warning shown to user about impending timeout, và no
auto-save mechanism.

STEPS TO REPRODUCE:
1. Login to system: admin@test.com / Admin123!
2. Navigate to Profile Settings page
3. Click "Edit Profile" button
4. Start editing fields:
   - Full Name: "Nguyen Van Test Updated"
   - Phone: "0987654321"
   - Address: "456 Le Loi, Q3, HCMC"
   - Bio: [Type 200 words for 10 minutes]
5. Wait for session to expire (30 minutes idle, không interact)
6. Click "Save Changes" button

EXPECTED RESULT:
Option A: Auto-save draft periodically
Option B: Warning before session expires: "Session expiring in 5
         minutes. Please save your work."
Option C: Preserve form data, allow user to re-authenticate và continue

ACTUAL RESULT:
- Session expires silently (no warning)
- Click "Save" → Redirected to login page
- After re-login → Form is empty, all data LOST ❌
- 10 minutes work wasted
- Very frustrating UX

IMPACT:
- Poor user experience
- Data loss
- User frustration
- Time wasted
- Reproducibility: 100%

ATTACHMENTS:
- Screenshot: [empty-form-after-relogin.png]
- Video: [session-timeout-data-loss.mp4]

TEST CASE ID: TC-PROFILE-012

SUGGESTED SOLUTIONS:
1. Implement auto-save draft every 2 minutes
2. Show warning 5 mins before timeout
3. Preserve form data in localStorage
4. Extend session on user activity (typing, clicking)

ASSIGNED TO: Pham Van Developer

FOUND IN VERSION: v1.5.2
```

---

## EXAMPLE 3: UI Bug - Medium Severity

```
DEFECT ID: BUG-1003

TITLE: Date picker shows incorrect calendar for February 2024

REPORTED BY: Hoang Minh Tester
REPORTED DATE: 2024-11-23

SEVERITY: Medium
PRIORITY: Medium

STATUS: Open

ENVIRONMENT:
- Application: Booking System v3.1.0
- OS: Windows 11
- Browser: Chrome 118
- Screen Resolution: 1920x1080

DESCRIPTION:
Date picker component displays February 2024 với 30 days
instead of 29 days (2024 is leap year). Days 29 và 30 are
selectable nhưng invalid dates.

STEPS TO REPRODUCE:
1. Navigate to booking page
2. Click on "Check-in Date" field
3. Date picker calendar opens
4. Click next month arrow để navigate to February 2024
5. Observe calendar display

EXPECTED RESULT:
- February 2024 should show 29 days (leap year)
- Day 29 should be selectable
- Day 30, 31 should NOT exist

ACTUAL RESULT:
- February 2024 shows 30 days ❌
- Day 30 is selectable (but invalid date)
- Selecting Feb 30 causes error on submit

IMPACT:
- User confusion
- Booking errors
- Minor usability issue
- Workaround: Users can manually enter correct date

ATTACHMENTS:
- Screenshot: [feb-30-showing.png]
- Console Error: [date-validation-error.txt]

TEST CASE ID: TC-BOOKING-025

AFFECTED MONTHS:
- All months with < 31 days potentially affected
- Tested February specifically (leap year issue)

SUGGESTED FIX:
- Update date picker library to latest version
- Or: Add custom validation for days in month

ASSIGNED TO: Frontend Team

FOUND IN VERSION: v3.1.0
```

---

## SEVERITY vs PRIORITY

### Severity (Technical Impact)

```
CRITICAL:
- System crash
- Data corruption/loss
- Security breach
- Financial transaction errors
- Complete feature breakdown
Examples:
- Payment processed twice
- Database corrupted
- User passwords exposed

HIGH:
- Major function not working
- Significant data issue
- Workaround difficult/complex
Examples:
- Cannot complete checkout
- Search returns no results
- Profile data lost

MEDIUM:
- Feature partially working
- Minor data issues
- Workaround exists và reasonable
Examples:
- UI alignment off
- Minor calculation error
- Slow performance

LOW:
- Cosmetic issues
- Typos, grammar
- Minor UI glitches
Examples:
- Button color wrong
- Spelling mistake
- Icon misaligned
```

### Priority (Business Urgency)

```
CRITICAL:
- Fix immediately (hotfix)
- Blocks release
- Affects many users
Examples:
- Payment bug in production
- Security vulnerability
- Legal compliance issue

HIGH:
- Fix in current sprint
- Important but not blocking
Examples:
- High-use feature broken
- Performance issue affecting UX

MEDIUM:
- Fix in next sprint
- Can be scheduled
Examples:
- Nice-to-have feature bug
- Low-use feature issue

LOW:
- Fix when time permits
- Can be deferred
Examples:
- Visual polish
- Edge case bugs
- Feature requests
```

### Severity vs Priority Matrix

| Scenario | Severity | Priority | Example |
|----------|----------|----------|---------|
| Payment failure | Critical | Critical | Fix now! |
| Homepage crash | Critical | Critical | Hotfix! |
| Admin panel typo | Low | Low | Next release |
| Homepage typo | Low | High | Highly visible |
| Rare edge case bug | High | Low | Few users affected |

---

## DEFECT LIFECYCLE

```
NEW → OPEN → IN PROGRESS → FIXED → RETEST → CLOSED
         ↓                              ↓
    REJECTED                      REOPENED
         ↓                              ↑
    CLOSED                         (if retest fails)

DEFERRED: Postponed to future release
```

### Status Definitions

- **NEW**: Just reported, not triaged
- **OPEN**: Confirmed, assigned to developer
- **IN PROGRESS**: Developer working on fix
- **FIXED**: Developer completed fix
- **RETEST**: Tester verifying fix
- **CLOSED**: Verified fixed, closed
- **REJECTED**: Not a bug / Cannot reproduce / Working as designed
- **DEFERRED**: Will fix in future release
- **REOPENED**: Retest failed, still broken

---

## TIPS VIẾT DEFECT REPORT TỐT

### 1. Clear, Specific Title
```
❌ BAD: "Login not working"
✅ GOOD: "Login fails with valid credentials on Chrome"
```

### 2. Reproducible Steps
```
❌ BAD: "I clicked around and it crashed"
✅ GOOD:
1. Login as user@test.com
2. Navigate to /orders
3. Click order #12345
4. Click "Cancel Order"
→ System crashes
```

### 3. Include Test Data
```
❌ BAD: "Tested with valid data"
✅ GOOD: "Tested with email: test@example.com, password: Pass123!"
```

### 4. Attach Evidence
- Screenshots (highlight issue in red box)
- Video recordings (for complex repro steps)
- Error logs, console outputs
- Network HAR files (for API issues)

### 5. Be Objective, Not Emotional
```
❌ BAD: "This stupid button doesn't work!"
✅ GOOD: "Submit button remains disabled after all required fields filled"
```

### 6. One Bug per Report
```
❌ BAD: Report có 5 different bugs
✅ GOOD: Create 5 separate bug reports
```

---

## CHECKLIST: Defect Report Review

Trước khi submit bug report:

- [ ] Title clear và descriptive
- [ ] Severity và Priority assigned correctly
- [ ] Environment details complete (OS, browser, version)
- [ ] Steps to reproduce detailed và numbered
- [ ] Steps can be followed by someone else
- [ ] Test data provided (usernames, inputs)
- [ ] Expected result stated clearly
- [ ] Actual result stated clearly
- [ ] Screenshots/videos attached
- [ ] Test Case ID referenced (traceability)
- [ ] Impact described (how many users affected)
- [ ] Reproducibility rate mentioned (100%, 50%, Intermittent)
- [ ] Grammar và spelling checked

---

## COMMON MISTAKES TO AVOID

### 1. Vague Description
❌ "System is slow"
✅ "Product search takes 15 seconds (expected <2s) when searching for 'laptop'"

### 2. Missing Reproduction Steps
❌ "I found a bug in checkout"
✅ [Detailed step-by-step như examples trên]

### 3. Wrong Severity/Priority
❌ UI typo marked as Critical
✅ UI typo marked as Low severity, priority depends on visibility

### 4. Multiple Bugs in One Report
❌ "Login page has 3 bugs: typo, button broken, slow load"
✅ Create 3 separate bug reports

### 5. No Evidence
❌ Text description only
✅ Include screenshots, videos, logs

---

## TEMPLATE: Security Defect Report

Security bugs cần thêm information:

```
DEFECT ID: SEC-BUG-[NUMBER]

SECURITY TYPE: [SQL Injection / XSS / CSRF / Authentication / Authorization / etc.]

CVSS SCORE: [If calculated]

DESCRIPTION:
[Detailed technical description]

VULNERABILITY:
[What security principle violated]

EXPLOIT STEPS:
[How to exploit this vulnerability]

PROOF OF CONCEPT:
[Code/payload used to demonstrate]

IMPACT:
[What attacker can do]

AFFECTED USERS:
[All users / Admin only / Public / etc.]

RECOMMENDED FIX:
[Technical fix suggestions]

CONFIDENTIALITY: [Restrict access to security team only]
```

---

**Good bug reports lead to faster fixes! 🐛→🔧**

**Version**: 1.0.0
**Last Updated**: November 2025
