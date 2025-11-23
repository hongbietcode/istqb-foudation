# MODULE 5.2: EXPERIENCE-BASED TECHNIQUES

**Thời lượng**: 3-4 giờ | **Độ khó**: ⭐⭐

---

## MỤC TIÊU HỌC TẬP

Sau khi hoàn thành module này, bạn sẽ:

| ID | Mục tiêu | Level |
|----|----------|-------|
| FL-4.4.1 | Giải thích error guessing | K2 |
| FL-4.4.2 | Giải thích exploratory testing | K2 |
| FL-4.4.3 | Giải thích checklist-based testing | K2 |

---

## 1. EXPERIENCE-BASED TECHNIQUES LÀ GÌ?

### 1.1. Tổng Quan

```
╔═══════════════════════════════════════════════════════════════╗
║            EXPERIENCE-BASED TECHNIQUES                        ║
╠═══════════════════════════════════════════════════════════════╣
║                                                               ║
║  📖 ĐỊNH NGHĨA:                                               ║
║     Test techniques dựa vào KINH NGHIỆM, KỸ NĂNG, INTUITION ║
║     của tester                                                ║
║                                                               ║
║  🔧 ĐẶC ĐIỂM:                                                 ║
║     • LESS FORMAL than Black-box/White-box                   ║
║     • Không có công thức rõ ràng                            ║
║     • Depend on tester's expertise                           ║
║     • Creative, intuitive                                    ║
║                                                               ║
║  📊 3 KỸ THUẬT CHÍNH:                                         ║
║     1. Error Guessing - Đoán lỗi dựa kinh nghiệm            ║
║     2. Exploratory Testing - Khám phá và test đồng thời     ║
║     3. Checklist-based Testing - Test theo checklist        ║
║                                                               ║
║  ✅ KHI NÀO DÙNG:                                             ║
║     • Specs unclear hoặc incomplete                          ║
║     • Time constraints (cần test nhanh)                      ║
║     • Complement formal techniques                           ║
║     • Early testing phases                                   ║
║                                                               ║
║  ⚠️ HẠN CHẾ:                                                 ║
║     • Không có coverage measurement                          ║
║     • Results depend on tester skill                         ║
║     • Khó reproduce (không systematic)                       ║
║     • Không đảm bảo completeness                            ║
║                                                               ║
╚═══════════════════════════════════════════════════════════════╝
```

---

## 2. ERROR GUESSING

### 2.1. Error Guessing Là Gì?

```
╔═══════════════════════════════════════════════════════════════╗
║                     ERROR GUESSING                            ║
╠═══════════════════════════════════════════════════════════════╣
║                                                               ║
║  📖 ĐỊNH NGHĨA:                                               ║
║     Technique để anticipate (dự đoán) errors, defects, và    ║
║     failures dựa trên:                                        ║
║     • Tester's experience                                    ║
║     • Knowledge của application                              ║
║     • Past defects                                           ║
║                                                               ║
║  🎯 MỤC ĐÍCH:                                                 ║
║     Design tests để TARGET các errors mà testers nghĩ rằng   ║
║     có thể xảy ra                                            ║
║                                                               ║
║  🔍 HOW IT WORKS:                                             ║
║     1. Tester thinks: "Lỗi nào hay xảy ra?"                 ║
║     2. List các potential errors                             ║
║     3. Design tests to expose those errors                   ║
║                                                               ║
║  📝 ALSO CALLED:                                              ║
║     • Fault Attack (tấn công lỗi)                           ║
║     • Defect-based technique                                 ║
║                                                               ║
╚═══════════════════════════════════════════════════════════════╝
```

### 2.2. Common Errors to Guess

```
╔═══════════════════════════════════════════════════════════════╗
║                  COMMON ERROR CATEGORIES                      ║
╠═══════════════════════════════════════════════════════════════╣
║                                                               ║
║  🔢 NUMERIC ERRORS:                                           ║
║     • Division by zero                                       ║
║     • Negative numbers                                       ║
║     • Very large numbers (overflow)                          ║
║     • Decimal/float precision issues                         ║
║                                                               ║
║  📝 STRING ERRORS:                                            ║
║     • Empty string ("")                                      ║
║     • Null value                                             ║
║     • Very long strings                                      ║
║     • Special characters (!@#$%^&*)                          ║
║     • SQL injection attempts (' OR '1'='1)                   ║
║     • XSS attempts (<script>alert('XSS')</script>)          ║
║                                                               ║
║  📅 DATE/TIME ERRORS:                                         ║
║     • Leap year (29 Feb)                                     ║
║     • Invalid dates (31 Feb, 32 Jan)                        ║
║     • Daylight Saving Time transitions                       ║
║     • Time zones                                             ║
║     • Year 2038 problem (Unix timestamp)                     ║
║                                                               ║
║  📁 FILE ERRORS:                                              ║
║     • File not found                                         ║
║     • Empty files                                            ║
║     • Very large files                                       ║
║     • Wrong file format                                      ║
║     • Corrupted files                                        ║
║                                                               ║
║  🔐 SECURITY ERRORS:                                          ║
║     • No authentication                                      ║
║     • Weak passwords                                         ║
║     • Session hijacking                                      ║
║     • CSRF attacks                                           ║
║                                                               ║
║  🌐 NETWORK ERRORS:                                           ║
║     • Network timeout                                        ║
║     • Connection lost                                        ║
║     • Slow network                                           ║
║     • API not responding                                     ║
║                                                               ║
║  💾 DATA ERRORS:                                              ║
║     • Duplicate entries                                      ║
║     • Missing required fields                                ║
║     • Data type mismatches                                   ║
║     • Foreign key constraints                                ║
║                                                               ║
╚═══════════════════════════════════════════════════════════════╝
```

### 2.3. Ví Dụ: Error Guessing cho Login Form

**Feature**: Login form với username và password

**Error Guessing**:

| Potential Error | Test Case |
|----------------|-----------|
| Empty username | username="", password="valid" |
| Empty password | username="valid", password="" |
| Both empty | username="", password="" |
| SQL Injection | username="admin'--", password="any" |
| XSS attack | username="<script>alert(1)</script>" |
| Very long inputs | username=1000 chars, password=1000 chars |
| Special chars | username="!@#$%", password="^&*()" |
| Case sensitivity | Username="ADMIN" vs "admin" |
| Leading/trailing spaces | username=" admin " |
| Multiple login attempts | Try 100 times rapidly (brute force) |
| Session timeout | Login, wait 30 mins, try action |
| Concurrent logins | Same user login from 2 browsers |

**Nguồn gốc errors**:
- ✅ Past bugs (từng có SQL injection)
- ✅ Common vulnerabilities (OWASP Top 10)
- ✅ Tester experience (đã test nhiều login forms)

---

## 3. EXPLORATORY TESTING

### 3.1. Exploratory Testing Là Gì?

```
╔═══════════════════════════════════════════════════════════════╗
║                  EXPLORATORY TESTING                          ║
╠═══════════════════════════════════════════════════════════════╣
║                                                               ║
║  📖 ĐỊNH NGHĨA (James Bach):                                  ║
║     "Simultaneous learning, test design, và test execution"  ║
║                                                               ║
║  🎯 ĐẶC ĐIỂM:                                                 ║
║     • LEARNING: Tìm hiểu application trong khi test         ║
║     • DESIGN: Design tests on-the-fly                        ║
║     • EXECUTE: Execute tests ngay lập tức                    ║
║     • All happen SIMULTANEOUSLY                              ║
║                                                               ║
║  ⏱️ SESSION-BASED:                                           ║
║     → Thường organize thành time-boxed sessions             ║
║     → Mỗi session: 60-120 minutes                           ║
║     → Focus on specific charter/mission                      ║
║                                                               ║
║  📝 CHARTER:                                                  ║
║     → Clear goal cho session                                 ║
║     → Example: "Explore payment flow to find usability      ║
║       issues"                                                ║
║                                                               ║
║  🔍 SO VỚI SCRIPTED TESTING:                                  ║
║     Scripted: Follow pre-written test cases                  ║
║     Exploratory: Freedom to explore, investigate            ║
║                                                               ║
╚═══════════════════════════════════════════════════════════════╝
```

### 3.2. Session-Based Test Management (SBTM)

```
╔═══════════════════════════════════════════════════════════════╗
║           SESSION-BASED TEST MANAGEMENT (SBTM)                ║
╠═══════════════════════════════════════════════════════════════╣
║                                                               ║
║  📋 SESSION STRUCTURE:                                        ║
║                                                               ║
║  1. CHARTER (Mission)                                        ║
║     → What to explore                                        ║
║     → Example: "Test search functionality với edge cases"   ║
║                                                               ║
║  2. TIME BOX                                                 ║
║     → 90 minutes uninterrupted                              ║
║                                                               ║
║  3. SETUP                                                    ║
║     → Prepare test data, environment                         ║
║     → Duration breakdown:                                    ║
║       - Setup: 10%                                           ║
║       - Testing: 80%                                         ║
║       - Bug reporting: 10%                                   ║
║                                                               ║
║  4. EXPLORE & TEST                                           ║
║     → Follow interesting paths                               ║
║     → Investigate anomalies                                  ║
║     → Take notes                                             ║
║                                                               ║
║  5. DEBRIEF                                                  ║
║     → Document findings                                      ║
║     → Report bugs found                                      ║
║     → Areas covered                                          ║
║     → Questions raised                                       ║
║                                                               ║
╚═══════════════════════════════════════════════════════════════╝
```

### 3.3. Ví Dụ: Exploratory Testing Session

**Application**: Shopee mobile app

**Charter**: "Explore checkout flow để find payment-related bugs"

**Time**: 90 minutes

**Session Notes**:

```
Session Start: 14:00
Tester: Nguyen Van A

CHARTER: Explore checkout flow for payment bugs

SETUP (14:00-14:05):
- App version: 3.2.1
- Test device: iPhone 12, iOS 16
- Test account: test@email.com (balance: 1,000,000 VND)
- Added 3 items to cart (total: 750,000 VND)

EXPLORATION (14:05-15:20):

14:05 - Started checkout flow
     - ✅ Cart summary correct
     - 🐛 BUG #1: Discount code field accepts >20 chars
       (should be max 10)

14:15 - Testing payment methods
     - Tried: Credit Card, Debit, Momo, ShopeePay
     - ✅ All options available
     - 🔍 OBSERVATION: Momo option shows twice

14:25 - Applied promo code "SALE50"
     - ✅ 50% discount applied
     - 💡 QUESTION: Can I stack multiple promo codes?
     - Tried adding second code → ❌ Error message unclear
     - 🐛 BUG #2: Error "Invalid" instead of
       "Only 1 promo code allowed"

14:40 - Testing insufficient balance
     - Changed payment to ShopeePay
     - Balance: 1M, Order: 375K (after discount)
     - ✅ Works
     - Artificially set balance to 100K (via test account)
     - 🐛 BUG #3: App crashes when confirming order
       with insufficient balance

14:55 - Testing network interruption
     - Started order confirmation
     - Turned off WiFi mid-transaction
     - 🐛 BUG #4: Spinner shows forever, no timeout
     - After 5 mins, still loading
     - ⚠️ RISK: User might click multiple times →
       duplicate orders?

15:10 - Resumed with network
     - Order went through
     - ✅ No duplicate created (good!)
     - But order status unclear in "My Orders"
     - 🐛 BUG #5: Status shows "Processing" but payment
       already deducted

DEBRIEF (15:20-15:30):

📊 SUMMARY:
   - 5 bugs found (2 high, 3 medium)
   - 1 question raised (stacking promo codes)
   - Coverage: Checkout flow, 5 payment methods,
     edge cases

🔥 HIGH PRIORITY BUGS:
   - #3: App crash (insufficient balance)
   - #4: Infinite spinner (network issue)

💡 FOLLOW-UP:
   - Test with multiple promo codes (is it a feature?)
   - Test duplicate order prevention thoroughly
   - Security: Can user manipulate balance?

Session End: 15:30
```

### 3.4. Khi Nào Dùng Exploratory Testing

```
╔═══════════════════════════════════════════════════════════════╗
║          KHI NÀO DÙNG EXPLORATORY TESTING                     ║
╠═══════════════════════════════════════════════════════════════╣
║                                                               ║
║  ✅ EARLY TESTING                                             ║
║     → Specs chưa đầy đủ                                      ║
║     → Cần hiểu application quickly                           ║
║                                                               ║
║  ✅ TIME CONSTRAINTS                                          ║
║     → Urgent release, không đủ time viết test cases         ║
║     → Need to find critical bugs fast                        ║
║                                                               ║
║  ✅ COMPLEMENT SCRIPTED TESTS                                 ║
║     → Sau khi chạy xong automated tests                     ║
║     → Find bugs mà scripts missed                            ║
║                                                               ║
║  ✅ NEW FEATURES                                              ║
║     → Explore new functionality                              ║
║     → Understand behavior                                    ║
║                                                               ║
║  ✅ EXPERIENCED TESTERS                                       ║
║     → Senior testers với domain knowledge                    ║
║     → Can quickly identify risks                             ║
║                                                               ║
║  ⚠️ KHÔNG NÊN CHỈ DÙNG EXPLORATORY:                          ║
║     → Cần documentation (traceability)                       ║
║     → Regulatory compliance                                  ║
║     → Regression testing (dùng scripted)                    ║
║                                                               ║
╚═══════════════════════════════════════════════════════════════╝
```

---

## 4. CHECKLIST-BASED TESTING

### 4.1. Checklist-Based Testing Là Gì?

```
╔═══════════════════════════════════════════════════════════════╗
║                CHECKLIST-BASED TESTING                        ║
╠═══════════════════════════════════════════════════════════════╣
║                                                               ║
║  📖 ĐỊNH NGHĨA:                                               ║
║     Testing theo một checklist các items cần verify          ║
║                                                               ║
║  🔧 ĐẶC ĐIỂM:                                                 ║
║     • HIGH-LEVEL list of things to check                     ║
║     • Không detailed như test cases                          ║
║     • KHÔNG có expected results cụ thể                       ║
║     • Tester decides HOW to test mỗi item                    ║
║                                                               ║
║  📝 CHECKLIST FROM:                                           ║
║     • Past experience                                        ║
║     • Common issues                                          ║
║     • Standards/Guidelines                                   ║
║     • Domain knowledge                                       ║
║                                                               ║
║  ✅ LỢI ÍCH:                                                  ║
║     • Quick to create                                        ║
║     • Ensure consistency                                     ║
║     • Cover common areas                                     ║
║     • Flexible (testers có freedom)                         ║
║                                                               ║
║  ⚠️ HẠN CHẾ:                                                 ║
║     • Less detailed than test cases                          ║
║     • Không có traceability tốt                             ║
║     • Results vary by tester                                 ║
║                                                               ║
╚═══════════════════════════════════════════════════════════════╝
```

### 4.2. Checklist vs Test Cases

| Aspect | Test Cases | Checklist |
|--------|------------|-----------|
| **Detail** | Very detailed | High-level |
| **Steps** | Explicit steps | No explicit steps |
| **Expected Results** | Có | Không |
| **Test Data** | Specific | General |
| **Reproducibility** | High | Medium |
| **Flexibility** | Low | High |
| **Time to create** | Long | Quick |
| **Tester freedom** | Low | High |

**Example**:

**Test Case** (Detailed):
```
TC-001: Login với valid credentials
Precondition: User account exists (user: test@email.com, pass: Test@123)
Steps:
1. Navigate to https://app.com/login
2. Enter username "test@email.com"
3. Enter password "Test@123"
4. Click "Login" button

Expected Result:
- User redirected to dashboard (https://app.com/dashboard)
- Welcome message "Welcome, Test User!" displayed
- User avatar shown in top-right corner
```

**Checklist Item** (High-level):
```
☐ Login functionality
  - Valid credentials work
  - Invalid credentials rejected
  - Account lockout after N failed attempts
  - Password visibility toggle works
```

### 4.3. Ví Dụ: Web Application Testing Checklist

```
╔═══════════════════════════════════════════════════════════════╗
║          WEB APPLICATION TESTING CHECKLIST                    ║
╠═══════════════════════════════════════════════════════════════╣
║                                                               ║
║  🔐 AUTHENTICATION & AUTHORIZATION                            ║
║  ☐ Login với valid/invalid credentials                       ║
║  ☐ Logout functionality                                      ║
║  ☐ Password reset flow                                       ║
║  ☐ Session timeout                                           ║
║  ☐ Remember me functionality                                 ║
║  ☐ Access control (roles/permissions)                        ║
║                                                               ║
║  📝 FORMS & INPUT VALIDATION                                  ║
║  ☐ Required fields validation                                ║
║  ☐ Field format validation (email, phone, etc.)             ║
║  ☐ Min/Max length validation                                 ║
║  ☐ Special characters handling                               ║
║  ☐ Error messages clear và helpful                          ║
║  ☐ Form submission (success/failure)                         ║
║                                                               ║
║  🌐 CROSS-BROWSER COMPATIBILITY                               ║
║  ☐ Chrome (latest version)                                   ║
║  ☐ Firefox (latest version)                                  ║
║  ☐ Safari (latest version)                                   ║
║  ☐ Edge (latest version)                                     ║
║  ☐ Mobile browsers (iOS Safari, Chrome Android)             ║
║                                                               ║
║  📱 RESPONSIVE DESIGN                                         ║
║  ☐ Desktop (1920x1080, 1366x768)                            ║
║  ☐ Tablet (768x1024)                                         ║
║  ☐ Mobile (375x667, 414x896)                                ║
║  ☐ Layout không bị vỡ                                       ║
║  ☐ Touch interactions work                                   ║
║                                                               ║
║  ⚡ PERFORMANCE                                               ║
║  ☐ Page load time <3 seconds                                ║
║  ☐ No memory leaks                                           ║
║  ☐ Images optimized                                          ║
║  ☐ API response time reasonable                              ║
║                                                               ║
║  🔒 SECURITY                                                  ║
║  ☐ SQL Injection prevention                                  ║
║  ☐ XSS prevention                                            ║
║  ☐ CSRF protection                                           ║
║  ☐ HTTPS enabled                                             ║
║  ☐ Sensitive data encrypted                                  ║
║                                                               ║
║  ♿ ACCESSIBILITY (WCAG)                                      ║
║  ☐ Keyboard navigation                                       ║
║  ☐ Screen reader compatible                                  ║
║  ☐ Alt text cho images                                       ║
║  ☐ Color contrast sufficient                                 ║
║                                                               ║
║  🎨 UI/UX                                                     ║
║  ☐ Consistent design (colors, fonts, spacing)               ║
║  ☐ Loading indicators                                        ║
║  ☐ Error messages friendly                                   ║
║  ☐ Confirmation dialogs cho critical actions                ║
║  ☐ Navigation intuitive                                      ║
║                                                               ║
╚═══════════════════════════════════════════════════════════════╝
```

### 4.4. Ví Dụ: Mobile App Testing Checklist

```
📱 MOBILE APP TESTING CHECKLIST (iOS & Android)

🚀 INSTALLATION & UPDATES
☐ Fresh install from App Store/Play Store
☐ Update from previous version
☐ Uninstall/Reinstall
☐ Install with low storage
☐ Permissions requests (Camera, Location, etc.)

📶 NETWORK CONDITIONS
☐ WiFi connection
☐ 4G/5G connection
☐ 3G/2G connection (slow network)
☐ No network (offline mode)
☐ Switch between WiFi ↔ Mobile data
☐ Airplane mode

🔋 DEVICE CONDITIONS
☐ Low battery (<10%)
☐ Battery saver mode
☐ Full storage (>95% used)
☐ Different screen sizes (small, medium, large)
☐ Different OS versions (iOS 14, 15, 16; Android 11, 12, 13)

📞 INTERRUPTIONS
☐ Incoming call during use
☐ Incoming SMS
☐ Push notification
☐ Alarm goes off
☐ App goes to background
☐ App resumed from background

🔄 DATA SYNC
☐ Data syncs across devices
☐ Offline changes sync when online
☐ Conflict resolution
☐ Real-time updates

⚙️ APP SETTINGS
☐ Notification settings work
☐ Language/Locale changes
☐ Dark mode / Light mode
☐ Font size changes

🎯 PERFORMANCE
☐ App launch time <3s
☐ Smooth scrolling
☐ No crashes
☐ No ANR (Application Not Responding)
☐ Memory usage reasonable
```

### 4.5. Tạo Checklist Hiệu Quả

```
╔═══════════════════════════════════════════════════════════════╗
║              TẠO CHECKLIST HIỆU QUẢ                          ║
╠═══════════════════════════════════════════════════════════════╣
║                                                               ║
║  📋 NGUỒN CHECKLIST:                                          ║
║                                                               ║
║  1. PAST DEFECTS                                             ║
║     → Analyze previous bugs                                  ║
║     → Add items để prevent recurrence                        ║
║                                                               ║
║  2. REQUIREMENTS & SPECS                                      ║
║     → Extract key functionalities                            ║
║     → List critical features                                 ║
║                                                               ║
║  3. STANDARDS & GUIDELINES                                    ║
║     → OWASP (security)                                       ║
║     → WCAG (accessibility)                                   ║
║     → Industry standards                                     ║
║                                                               ║
║  4. DOMAIN KNOWLEDGE                                          ║
║     → E-commerce: Payment, checkout                          ║
║     → Banking: Security, transactions                        ║
║     → Social media: Privacy, sharing                         ║
║                                                               ║
║  5. TEAM EXPERIENCE                                           ║
║     → Lessons learned                                        ║
║     → Common mistakes                                        ║
║                                                               ║
║  ✅ BEST PRACTICES:                                           ║
║     • Keep it CONCISE (1-2 pages max)                        ║
║     • Use CATEGORIES (organize items)                        ║
║     • PRIORITIZE (critical items first)                      ║
║     • UPDATE regularly (add new items)                       ║
║     • Make it ACTIONABLE (clear what to check)              ║
║                                                               ║
╚═══════════════════════════════════════════════════════════════╝
```

---

## 5. SO SÁNH 3 KỸ THUẬT

| Aspect | Error Guessing | Exploratory Testing | Checklist-based |
|--------|---------------|--------------------|-----------------|
| **Basis** | Past errors | Learning + Testing | Checklist items |
| **Structure** | Ad hoc | Session-based | Organized list |
| **Formal** | Least formal | Medium | Medium formal |
| **Documentation** | Minimal | Session notes | Checklist |
| **Reproducible** | Hard | Medium | Medium |
| **Coverage** | Targeted | Broad | Systematic |
| **Best for** | Finding bugs | Exploring | Consistency |
| **Time** | Quick | Medium (sessions) | Quick-Medium |

---

## 6. KẾT HỢP VỚI FORMAL TECHNIQUES

```
╔═══════════════════════════════════════════════════════════════╗
║          KẾT HỢP FORMAL + EXPERIENCE-BASED                    ║
╠═══════════════════════════════════════════════════════════════╣
║                                                               ║
║  🎯 STRATEGY:                                                 ║
║                                                               ║
║  Phase 1: FORMAL TECHNIQUES (70% effort)                     ║
║     → EP, BVA cho input validation                           ║
║     → Decision Tables cho business rules                     ║
║     → State Transition cho workflows                         ║
║     ✅ Systematic coverage                                    ║
║                                                               ║
║  Phase 2: EXPERIENCE-BASED (30% effort)                      ║
║     → Error Guessing: Target common pitfalls                 ║
║     → Exploratory: Find unexpected bugs                      ║
║     → Checklist: Ensure nothing missed                       ║
║     ✅ Creative, intuitive bug finding                        ║
║                                                               ║
║  📊 BEST OF BOTH:                                             ║
║     Formal → Coverage, Reproducibility, Documentation        ║
║     Experience → Creativity, Speed, Real-world insights      ║
║                                                               ║
╚═══════════════════════════════════════════════════════════════╝
```

**Ví dụ**: Testing e-commerce checkout

1. **Formal (EP + BVA)**: Test quantity field 1-999
   - Partitions: Valid (1-999), Invalid (<1, >999)
   - Boundaries: 0, 1, 999, 1000

2. **Error Guessing**: Try quantity = 99999999 (integer overflow?)

3. **Exploratory**: Session "Explore checkout with network interruptions"

4. **Checklist**: Use "E-commerce checkout checklist"

---

## 7. CÂU HỎI ÔN TẬP

### Câu 1 (K2)
Error guessing dựa vào gì?

A. Formal algorithms
B. Tester's experience và knowledge
C. Code coverage
D. Requirements only

<details>
<summary>Đáp án</summary>

**B. Tester's experience và knowledge**

Giải thích: Error guessing dựa vào kinh nghiệm của tester để dự đoán errors có thể xảy ra.
</details>

---

### Câu 2 (K2)
Exploratory testing là gì?

A. Testing without any plan
B. Simultaneous learning, design, và execution
C. Only manual testing
D. Random testing

<details>
<summary>Đáp án</summary>

**B. Simultaneous learning, design, và execution**

Giải thích: Definition của James Bach - learn, design, execute đồng thời.
</details>

---

### Câu 3 (K2)
Session-based exploratory testing thường kéo dài bao lâu?

A. 10-15 minutes
B. 30-45 minutes
C. 60-120 minutes
D. 3-4 hours

<details>
<summary>Đáp án</summary>

**C. 60-120 minutes**

Giải thích: Sessions thường 60-120 mins, uninterrupted testing.
</details>

---

### Câu 4 (K2)
Checklist-based testing khác test cases ở điểm nào?

A. Checklist không có expected results chi tiết
B. Checklist formal hơn
C. Checklist có traceability tốt hơn
D. Checklist không thể reuse

<details>
<summary>Đáp án</summary>

**A. Checklist không có expected results chi tiết**

Giải thích: Checklist là high-level, không có detailed steps và expected results như test cases.
</details>

---

### Câu 5 (K1)
Technique nào KHÔNG phải experience-based?

A. Error Guessing
B. Exploratory Testing
C. Boundary Value Analysis
D. Checklist-based Testing

<details>
<summary>Đáp án</summary>

**C. Boundary Value Analysis**

Giải thích: BVA là black-box technique, formal, không phải experience-based.
</details>

---

### Câu 6 (K2)
Khi nào NÊN dùng exploratory testing?

A. Regulatory compliance testing
B. Specs unclear, need quick feedback
C. Regression testing
D. When full documentation required

<details>
<summary>Đáp án</summary>

**B. Specs unclear, need quick feedback**

Giải thích: Exploratory tốt khi specs không rõ, time constraints, hoặc explore new features.
</details>

---

## 8. CHECKLIST TỰ ĐÁNH GIÁ

### Error Guessing
- [ ] Hiểu error guessing là gì
- [ ] Biết list common errors (numeric, string, date, security)
- [ ] Có thể anticipate errors từ experience
- [ ] Biết khi nào dùng error guessing

### Exploratory Testing
- [ ] Hiểu exploratory testing concept
- [ ] Biết session-based test management
- [ ] Có thể tạo test charter
- [ ] Biết document exploratory session
- [ ] Phân biệt exploratory vs scripted testing

### Checklist-based Testing
- [ ] Hiểu checklist-based testing
- [ ] Phân biệt checklist vs test cases
- [ ] Biết tạo checklist hiệu quả
- [ ] Có thể apply checklist trong testing

### Tổng Hợp
- [ ] Biết combine formal + experience-based techniques
- [ ] Hiểu value của mỗi technique
- [ ] Biết khi nào dùng technique nào

---

## TỔNG KẾT

```
╔═══════════════════════════════════════════════════════════════╗
║                    KEY TAKEAWAYS                              ║
╠═══════════════════════════════════════════════════════════════╣
║                                                               ║
║  1. Experience-based = Dựa vào kinh nghiệm tester            ║
║                                                               ║
║  2. Error Guessing:                                          ║
║     → Dự đoán lỗi từ past experience                        ║
║     → Target common pitfalls                                 ║
║                                                               ║
║  3. Exploratory Testing:                                     ║
║     → Simultaneous learning, design, execution               ║
║     → Session-based (60-120 mins)                           ║
║     → Good for unclear specs, quick feedback                ║
║                                                               ║
║  4. Checklist-based:                                         ║
║     → High-level items to check                             ║
║     → Quick, consistent, flexible                            ║
║     → Less detailed than test cases                          ║
║                                                               ║
║  5. Best Practice:                                           ║
║     → 70% Formal techniques (systematic coverage)            ║
║     → 30% Experience-based (creative bug finding)            ║
║                                                               ║
║  6. All 3 techniques complement formal techniques            ║
║                                                               ║
╚═══════════════════════════════════════════════════════════════╝
```

---

**Tiếp theo**: [Module 5.3: Collaboration-Based Approaches](./module-5.3-collaboration-based-approaches.md)

---

**Version**: 1.0.0
**Last Updated**: November 2025
