# TEMPLATE: TEST CASE

## Hướng Dẫn Sử Dụng

Template này dành cho việc viết test cases chi tiết. Copy template và fill in các fields.

---

## TEST CASE TEMPLATE (Simple Format)

```
TEST CASE ID: TC-[MODULE]-[NUMBER]
Example: TC-LOGIN-001

TITLE: [Mô tả ngắn gọn test case]
Example: Login với valid credentials

PRIORITY: [Critical / High / Medium / Low]

PRECONDITIONS:
[Điều kiện cần có trước khi execute]
Example:
- User account exists in database
- User is on login page
- Browser: Chrome latest version

TEST STEPS:
| Step | Action | Test Data | Expected Result |
|------|--------|-----------|-----------------|
| 1 | Navigate to login page | URL: /login | Login page displayed |
| 2 | Enter email | test@example.com | Email field populated |
| 3 | Enter password | Pass123! | Password field populated (masked) |
| 4 | Click "Login" button | - | User redirected to homepage |

POSTCONDITIONS:
[Trạng thái sau khi test]
Example: User logged in, session active

CREATED BY: [Tên tester]
CREATED DATE: [YYYY-MM-DD]
```

---

## EXAMPLE 1: Login Test Case

```
TEST CASE ID: TC-LOGIN-001

TITLE: Login với valid email và password

PRIORITY: Critical

PRECONDITIONS:
- User account exists: email=user@test.com, password=Pass123!
- Application deployed và accessible
- User không logged in
- Browser: Chrome 118+, Firefox 115+

TEST STEPS:
| Step | Action | Test Data | Expected Result |
|------|--------|-----------|-----------------|
| 1 | Open application URL | https://app.example.com | Homepage loads successfully |
| 2 | Click "Login" link | - | Login page displayed with email & password fields |
| 3 | Enter valid email | user@test.com | Email field shows entered value |
| 4 | Enter valid password | Pass123! | Password field shows masked characters (****) |
| 5 | Click "Login" button | - | • Loading indicator shows briefly<br>• Redirected to dashboard<br>• Welcome message: "Welcome, User!"<br>• Logout button visible |

POSTCONDITIONS:
- User session created
- Authentication token stored in cookies
- User status = "Online"

TEST DATA:
- Email: user@test.com
- Password: Pass123!

NOTES:
- Test in both Chrome và Firefox
- Verify session timeout sau 30 minutes idle

CREATED BY: Nguyen Van A
CREATED DATE: 2024-11-23
LAST MODIFIED: 2024-11-23
```

---

## EXAMPLE 2: E-commerce Add to Cart

```
TEST CASE ID: TC-CART-003

TITLE: Add product to cart from product detail page

PRIORITY: High

PRECONDITIONS:
- User logged in
- User on product detail page: Product ID = "PROD-123" (iPhone 15 Pro, Price: 28,000,000đ)
- Cart is empty (0 items)

TEST STEPS:
| Step | Action | Test Data | Expected Result |
|------|--------|-----------|-----------------|
| 1 | Verify product details displayed | - | • Product name: "iPhone 15 Pro"<br>• Price: "28,000,000đ"<br>• Stock status: "In Stock"<br>• "Add to Cart" button enabled |
| 2 | Select quantity | Quantity: 2 | Quantity field shows "2" |
| 3 | Click "Add to Cart" button | - | • Success toast: "Added to cart successfully"<br>• Cart icon badge shows "2"<br>• Button changes to "View Cart" for 3 seconds |
| 4 | Click cart icon | - | • Cart drawer opens from right<br>• Product listed: iPhone 15 Pro × 2<br>• Subtotal: 56,000,000đ<br>• "Checkout" button enabled |

POSTCONDITIONS:
- Cart contains 2 items
- Cart total = 56,000,000đ
- Cart persists after page refresh

TEST DATA:
- Product ID: PROD-123
- Product Name: iPhone 15 Pro
- Unit Price: 28,000,000đ
- Quantity: 2
- User: user@test.com

NOTES:
- Verify cart persists across browser sessions
- Test with different quantities (1, 5, 10)
- Verify stock check (cannot add more than available)

CREATED BY: Tran Thi B
CREATED DATE: 2024-11-23
EXECUTION HISTORY:
- 2024-11-23: PASSED (Chrome)
- 2024-11-24: PASSED (Firefox)
```

---

## EXAMPLE 3: Discount Code Application

```
TEST CASE ID: TC-DISCOUNT-010

TITLE: Apply valid percentage discount code to order

PRIORITY: High

PRECONDITIONS:
- User logged in
- Shopping cart has 1 item: Product A (Price: 1,000,000đ)
- Valid discount code exists in system:
  Code: SUMMER20
  Type: Percentage
  Value: 20%
  Min Order: 500,000đ
  Expiry: 2024-12-31
  Status: Active

TEST STEPS:
| Step | Action | Test Data | Expected Result |
|------|--------|-----------|-----------------|
| 1 | Navigate to checkout page | - | • Cart summary displayed<br>• Subtotal: 1,000,000đ<br>• Discount code field empty |
| 2 | Enter discount code in promo field | SUMMER20 | Code displayed in field |
| 3 | Click "Apply" button | - | • Success message: "Discount applied successfully"<br>• Discount row added: "SUMMER20: -200,000đ"<br>• New Total: 800,000đ<br>• Promo code field disabled<br>• "Apply" button → "Remove" button |
| 4 | Verify calculation | - | • Discount = 1,000,000 × 20% = 200,000đ ✓<br>• Total = 1,000,000 - 200,000 = 800,000đ ✓ |
| 5 | Proceed to payment | - | Order summary shows discounted amount |

POSTCONDITIONS:
- Order total = 800,000đ
- Discount code marked as "used" (if single-use)

TEST DATA:
- Discount Code: SUMMER20
- Cart Subtotal: 1,000,000đ
- Expected Discount: 200,000đ
- Expected Total: 800,000đ

EDGE CASES TO TEST:
- Order below minimum (< 500,000đ) → Error
- Expired code → Error
- Invalid code → Error
- Code already used (if single-use) → Error

CREATED BY: Le Van C
CREATED DATE: 2024-11-23
```

---

## TEMPLATE: Test Case với Negative Testing

```
TEST CASE ID: TC-[MODULE]-[NUMBER]

TITLE: [Describe negative scenario]

TYPE: Negative Test

PRIORITY: [Critical / High / Medium / Low]

OBJECTIVE: Verify system handles invalid input correctly

PRECONDITIONS:
[Required state before test]

TEST STEPS:
| Step | Action | Test Data (INVALID) | Expected Result (Error Handling) |
|------|--------|---------------------|----------------------------------|
| 1 | ... | ... | System rejects input |
| 2 | ... | ... | Clear error message shown |
| 3 | ... | ... | System remains stable (no crash) |

POSTCONDITIONS:
- No data corrupted
- System state unchanged
- Error logged

CREATED BY:
CREATED DATE:
```

---

## EXAMPLE 4: Negative Test - Invalid Email

```
TEST CASE ID: TC-LOGIN-NEG-001

TITLE: Login với invalid email format

TYPE: Negative Test

PRIORITY: Medium

OBJECTIVE: Verify system validates email format và shows appropriate error

PRECONDITIONS:
- User on login page
- No fields filled

TEST STEPS:
| Step | Action | Test Data (INVALID) | Expected Result |
|------|--------|---------------------|-----------------|
| 1 | Enter invalid email | invalidemail | Email field shows entered value |
| 2 | Enter valid password | Pass123! | Password field populated |
| 3 | Click "Login" button | - | • Login button disabled OR<br>• Error message: "Please enter a valid email address"<br>• Email field highlighted in red<br>• Focus returns to email field<br>• Login NOT processed |
| 4 | Correct email format | test@example.com | Error message clears |
| 5 | Click "Login" button | - | Login proceeds normally |

TEST DATA - INVALID EMAILS:
- invalidemail (no @)
- test@  (incomplete domain)
- @example.com (no local part)
- test..user@example.com (consecutive dots)
- test@.com (invalid domain)

POSTCONDITIONS:
- No login attempt sent to backend
- No session created
- Error properly handled và logged

CREATED BY: Nguyen Van D
CREATED DATE: 2024-11-23
```

---

## TEST CASE FORMAT (Excel/Spreadsheet Style)

Nếu quản lý trong Excel/Google Sheets:

| Field | Description | Example |
|-------|-------------|---------|
| **ID** | Unique identifier | TC-LOGIN-001 |
| **Module** | Feature being tested | Login |
| **Title** | Short description | Login with valid credentials |
| **Priority** | Critical/High/Medium/Low | Critical |
| **Type** | Positive/Negative/Boundary | Positive |
| **Preconditions** | Setup needed | User exists, on login page |
| **Test Steps** | Numbered actions | 1. Enter email... |
| **Test Data** | Input values | email: test@example.com |
| **Expected Result** | What should happen | Redirected to homepage |
| **Postconditions** | End state | User logged in |
| **Status** | Not Run/Pass/Fail/Blocked | Pass |
| **Execution Date** | When executed | 2024-11-23 |
| **Executed By** | Tester name | Nguyen Van A |
| **Actual Result** | What happened | Same as expected |
| **Defect ID** | If failed | BUG-123 |
| **Comments** | Additional notes | Tested on Chrome only |

---

## TIPS VIẾT TEST CASE TỐT

### 1. Clear và Specific
```
❌ BAD: "Test login"
✅ GOOD: "Verify user can login with valid email and password"
```

### 2. Include Expected Results
```
❌ BAD: Step: Click Login button
✅ GOOD: Step: Click Login button
           Expected: User redirected to /dashboard within 2 seconds
```

### 3. Provide Actual Test Data
```
❌ BAD: Test Data: Valid email
✅ GOOD: Test Data: test@example.com
```

### 4. Consider Edge Cases
```
Normal: Quantity = 5
Boundary: Quantity = 1 (min), Quantity = 999 (max)
Invalid: Quantity = 0, Quantity = 1000, Quantity = -1
```

### 5. Make Reproducible
- Exact steps
- Exact data
- Environment details
- Anyone should be able to execute

### 6. One Objective per Test Case
```
❌ BAD: TC-001: Test login, logout, and profile update
✅ GOOD:
  TC-001: Test login with valid credentials
  TC-002: Test logout
  TC-003: Test profile update
```

---

## CHECKLIST: Test Case Review

Trước khi finalize test case, check:

- [ ] Test Case ID unique và follows naming convention
- [ ] Title clearly describes what's being tested
- [ ] Priority assigned correctly
- [ ] Preconditions clear và complete
- [ ] Test steps numbered và sequential
- [ ] Each step has clear action
- [ ] Test data specific (not "valid data")
- [ ] Expected results detailed
- [ ] Postconditions defined
- [ ] Can be executed by another tester (reproducible)
- [ ] Grammar và spelling correct
- [ ] Linked to requirement ID (traceability)

---

## DOWNLOAD TEMPLATES

**Excel Template**: Available in `templates/test-case-template.xlsx`
**Google Sheets**: [Link to template]

---

**Version**: 1.0.0
**Last Updated**: November 2025
**Maintained by**: ISTQB Vietnam Community
