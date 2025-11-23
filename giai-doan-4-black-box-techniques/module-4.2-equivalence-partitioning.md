# MODULE 4.2: EQUIVALENCE PARTITIONING (EP)

**Thời lượng**: 4-5 giờ | **Độ khó**: ⭐⭐⭐
**Tầm quan trọng**: ~15% câu hỏi trong kỳ thi ISTQB

---

## MỤC TIÊU HỌC TẬP

Sau khi hoàn thành module này, bạn sẽ:

| ID | Mục tiêu | Level |
|----|----------|-------|
| FL-4.2.1 | Sử dụng Equivalence Partitioning để derive test cases | K3 |

---

## 1. EQUIVALENCE PARTITIONING LÀ GÌ?

### 1.1. Định Nghĩa

> **Equivalence Partitioning (EP)** là kỹ thuật chia dữ liệu input (hoặc output) thành các **partitions** (phân vùng) sao cho mọi giá trị trong cùng một partition được hệ thống xử lý **như nhau**.

```
╔═══════════════════════════════════════════════════════════════╗
║                EQUIVALENCE PARTITIONING                       ║
╠═══════════════════════════════════════════════════════════════╣
║                                                               ║
║  NGUYÊN LÝ:                                                   ║
║  ─────────                                                    ║
║  Nếu một giá trị trong partition WORKS → tất cả WORK         ║
║  Nếu một giá trị trong partition FAILS → tất cả FAIL         ║
║                                                               ║
║  → Chỉ cần test 1 GIÁ TRỊ từ mỗi partition                  ║
║                                                               ║
║  VÍ DỤ: Age field (valid: 18-65)                             ║
║  ────────────────────────────────                             ║
║                                                               ║
║  ┌─────────┐  ┌───────────────────┐  ┌─────────────┐         ║
║  │ Invalid │  │      Valid        │  │   Invalid   │         ║
║  │  < 18   │  │     18 - 65       │  │    > 65     │         ║
║  └─────────┘  └───────────────────┘  └─────────────┘         ║
║       │               │                    │                  ║
║       ▼               ▼                    ▼                  ║
║   Test: 10        Test: 30            Test: 80               ║
║                                                               ║
║  → Chỉ cần 3 test cases thay vì test all 18-65!             ║
║                                                               ║
╚═══════════════════════════════════════════════════════════════╝
```

### 1.2. Valid vs Invalid Partitions

```
╔═══════════════════════════════════════════════════════════════╗
║              VALID vs INVALID PARTITIONS                      ║
╠═══════════════════════════════════════════════════════════════╣
║                                                               ║
║  VALID PARTITIONS:                                            ║
║  ─────────────────                                            ║
║  • Giá trị được hệ thống CHẤP NHẬN                           ║
║  • Xử lý bình thường, không có error                         ║
║  • Example: Age 18-65 cho adult user                         ║
║                                                               ║
║  INVALID PARTITIONS:                                          ║
║  ───────────────────                                          ║
║  • Giá trị bị hệ thống TỪ CHỐI                               ║
║  • Trigger error message hoặc rejection                      ║
║  • Example: Age < 18 hoặc > 65                               ║
║                                                               ║
║  LƯU Ý QUAN TRỌNG:                                            ║
║  ─────────────────                                            ║
║  • Cần test CẢ valid VÀ invalid partitions                   ║
║  • Invalid partitions test error handling                    ║
║  • Mỗi invalid partition test RIÊNG (không combine)         ║
║                                                               ║
╚═══════════════════════════════════════════════════════════════╝
```

---

## 2. QUY TRÌNH ÁP DỤNG EP

### 2.1. Các Bước Thực Hiện

```
╔═══════════════════════════════════════════════════════════════╗
║           QUY TRÌNH EQUIVALENCE PARTITIONING                  ║
╠═══════════════════════════════════════════════════════════════╣
║                                                               ║
║  STEP 1: XÁC ĐỊNH INPUTS                                      ║
║          → Tìm các input fields/parameters                   ║
║                                                               ║
║  STEP 2: XÁC ĐỊNH PARTITIONS                                  ║
║          → Chia mỗi input thành valid + invalid partitions   ║
║                                                               ║
║  STEP 3: CHỌN TEST VALUES                                     ║
║          → Chọn 1 giá trị đại diện từ mỗi partition         ║
║                                                               ║
║  STEP 4: THIẾT KẾ TEST CASES                                  ║
║          → Tạo test cases từ các values đã chọn             ║
║          → Valid partitions có thể combine                   ║
║          → Invalid partitions test RIÊNG                     ║
║                                                               ║
╚═══════════════════════════════════════════════════════════════╝
```

---

## 3. VÍ DỤ CHI TIẾT

### 3.1. Ví Dụ 1: Age Field

**Requirement**: "User age must be between 18 and 65 (inclusive) to register"

```
STEP 1: INPUT
─────────────
Input: Age (số nguyên)

STEP 2: PARTITIONS
──────────────────
┌───────────────────────────────────────────────────────────────┐
│                         AGE PARTITIONS                        │
├────────────────┬─────────────────────┬───────────────────────┤
│    INVALID     │       VALID         │       INVALID         │
│     < 18       │      18 - 65        │        > 65           │
├────────────────┼─────────────────────┼───────────────────────┤
│   P1: < 18     │   P2: 18 - 65       │   P3: > 65            │
│   (Too young)  │   (Accepted)        │   (Too old)           │
└────────────────┴─────────────────────┴───────────────────────┘

STEP 3: TEST VALUES
───────────────────
P1 (Invalid < 18):  Age = 15
P2 (Valid 18-65):   Age = 30
P3 (Invalid > 65):  Age = 70

STEP 4: TEST CASES
──────────────────
┌──────┬───────┬─────────────────────────────────────────────┐
│ TC   │ Age   │ Expected Result                             │
├──────┼───────┼─────────────────────────────────────────────┤
│ TC1  │  15   │ Error: "Must be at least 18 years old"     │
│ TC2  │  30   │ Registration successful                     │
│ TC3  │  70   │ Error: "Must be 65 years or younger"       │
└──────┴───────┴─────────────────────────────────────────────┘

COVERAGE:
─────────
3 partitions defined, 3 tested = 100% EP coverage
```

### 3.2. Ví Dụ 2: Discount Code

**Requirement**:
- Discount code must be exactly 8 characters
- Must contain only letters (A-Z, a-z) and numbers (0-9)
- Valid codes start with "PROMO"

```
STEP 1: INPUT
─────────────
Input: Discount Code (string)

STEP 2: PARTITIONS
──────────────────
┌──────────────────────────────────────────────────────────────┐
│                    DISCOUNT CODE PARTITIONS                   │
├──────────────────────────────────────────────────────────────┤
│ VALID:                                                       │
│   P1: Exactly 8 chars, alphanumeric, starts with "PROMO"    │
│       Example: "PROMO123"                                    │
│                                                              │
│ INVALID:                                                     │
│   P2: Less than 8 characters        (e.g., "PROMO1")        │
│   P3: More than 8 characters        (e.g., "PROMO12345")    │
│   P4: Contains special characters   (e.g., "PROMO@#!")      │
│   P5: Does not start with "PROMO"   (e.g., "SALE1234")      │
│   P6: Empty string                  ("")                     │
└──────────────────────────────────────────────────────────────┘

STEP 3: TEST VALUES
───────────────────
P1: "PROMO123" (valid)
P2: "PROMO1"   (too short)
P3: "PROMO12345" (too long)
P4: "PROMO@#!" (invalid chars)
P5: "SALE1234" (wrong prefix)
P6: ""         (empty)

STEP 4: TEST CASES
──────────────────
┌──────┬─────────────┬────────────────────────────────────────┐
│ TC   │ Code        │ Expected Result                        │
├──────┼─────────────┼────────────────────────────────────────┤
│ TC1  │ PROMO123    │ Valid - Discount applied               │
│ TC2  │ PROMO1      │ Error: "Code must be 8 characters"    │
│ TC3  │ PROMO12345  │ Error: "Code must be 8 characters"    │
│ TC4  │ PROMO@#!    │ Error: "Only letters and numbers"     │
│ TC5  │ SALE1234    │ Error: "Invalid code"                 │
│ TC6  │ (empty)     │ Error: "Code is required"             │
└──────┴─────────────┴────────────────────────────────────────┘

COVERAGE: 6 partitions, 6 tested = 100%
```

### 3.3. Ví Dụ 3: Payment Amount (VNPay)

**Requirement**:
- Minimum transfer: 10,000 VND
- Maximum transfer: 500,000,000 VND

```
STEP 1: INPUT
─────────────
Input: Transfer Amount (number, VND)

STEP 2: PARTITIONS
──────────────────
┌──────────────────────────────────────────────────────────────┐
│                    AMOUNT PARTITIONS                          │
├──────────────────────────────────────────────────────────────┤
│                                                              │
│   INVALID      │        VALID          │      INVALID       │
│   < 10,000     │   10,000 - 500,000,000│     > 500,000,000  │
│                │                        │                    │
│   P1: Below    │   P2: Within range    │   P3: Above max    │
│       minimum  │                        │                    │
│                │                        │                    │
│ + P4: Zero (0)                                               │
│ + P5: Negative (-100,000)                                    │
│ + P6: Non-numeric ("abc")                                    │
└──────────────────────────────────────────────────────────────┘

STEP 3 & 4: TEST VALUES AND TEST CASES
──────────────────────────────────────
┌──────┬───────────────┬─────────────────────────────────────┐
│ TC   │ Amount        │ Expected Result                     │
├──────┼───────────────┼─────────────────────────────────────┤
│ TC1  │ 5,000         │ Error: "Minimum is 10,000 VND"     │
│ TC2  │ 1,000,000     │ Transfer successful                 │
│ TC3  │ 600,000,000   │ Error: "Maximum is 500M VND"       │
│ TC4  │ 0             │ Error: "Amount must be positive"   │
│ TC5  │ -100,000      │ Error: "Invalid amount"            │
│ TC6  │ "abc"         │ Error: "Must be a number"          │
└──────┴───────────────┴─────────────────────────────────────┘

COVERAGE: 6 partitions, 6 tested = 100%
```

### 3.4. Ví Dụ 4: Multiple Inputs - Login Form

**Requirement**:
- Email: Valid email format required
- Password: 8-20 characters

```
INPUTS VÀ PARTITIONS:
═════════════════════

INPUT 1: EMAIL
──────────────
Valid:   P1 - Valid email format (user@example.com)
Invalid: P2 - No @ symbol (userexample.com)
         P3 - No domain (user@)
         P4 - Empty ("")

INPUT 2: PASSWORD
─────────────────
Valid:   P5 - 8-20 characters (Pass1234)
Invalid: P6 - Less than 8 chars (Pass1)
         P7 - More than 20 chars (Pass123456789012345678901)
         P8 - Empty ("")


TEST CASES:
═══════════
Cách 1: Valid partitions có thể COMBINE
Cách 2: Invalid partitions test RIÊNG

┌──────┬───────────────────┬───────────────┬──────────────────┐
│ TC   │ Email             │ Password      │ Expected         │
├──────┼───────────────────┼───────────────┼──────────────────┤
│ TC1  │ user@example.com  │ Pass1234      │ Login success    │
│      │ (P1 valid)        │ (P5 valid)    │                  │
├──────┼───────────────────┼───────────────┼──────────────────┤
│ TC2  │ userexample.com   │ Pass1234      │ "Invalid email"  │
│      │ (P2 invalid)      │ (P5 valid)    │                  │
├──────┼───────────────────┼───────────────┼──────────────────┤
│ TC3  │ user@             │ Pass1234      │ "Invalid email"  │
│      │ (P3 invalid)      │ (P5 valid)    │                  │
├──────┼───────────────────┼───────────────┼──────────────────┤
│ TC4  │ (empty)           │ Pass1234      │ "Email required" │
│      │ (P4 invalid)      │ (P5 valid)    │                  │
├──────┼───────────────────┼───────────────┼──────────────────┤
│ TC5  │ user@example.com  │ Pass1         │ "Password too    │
│      │ (P1 valid)        │ (P6 invalid)  │  short"          │
├──────┼───────────────────┼───────────────┼──────────────────┤
│ TC6  │ user@example.com  │ (21+ chars)   │ "Password too    │
│      │ (P1 valid)        │ (P7 invalid)  │  long"           │
├──────┼───────────────────┼───────────────┼──────────────────┤
│ TC7  │ user@example.com  │ (empty)       │ "Password        │
│      │ (P1 valid)        │ (P8 invalid)  │  required"       │
└──────┴───────────────────┴───────────────┴──────────────────┘

Tổng: 8 partitions, 7 test cases
(TC1 covers 2 valid partitions cùng lúc)
```

---

## 4. CÔNG THỨC TÍNH COVERAGE

```
                    Số partitions được test
EP Coverage (%) = ────────────────────────── × 100%
                    Tổng số partitions
```

**Ví dụ**:
- Xác định được 6 partitions
- Test 5 partitions
- Coverage = 5/6 × 100% = 83.3%

---

## 5. QUY TẮC QUAN TRỌNG

```
╔═══════════════════════════════════════════════════════════════╗
║              QUY TẮC QUAN TRỌNG TRONG EP                      ║
╠═══════════════════════════════════════════════════════════════╣
║                                                               ║
║  1️⃣ MỖI PARTITION CHỈ TEST 1 GIÁ TRỊ                          ║
║     → Không cần test nhiều values trong cùng partition      ║
║     → 1 value đại diện cho cả partition                     ║
║                                                               ║
║  2️⃣ VALID PARTITIONS CÓ THỂ COMBINE                           ║
║     → 1 test case có thể cover nhiều valid partitions       ║
║     → Tiết kiệm số lượng test cases                         ║
║                                                               ║
║  3️⃣ INVALID PARTITIONS PHẢI TEST RIÊNG                        ║
║     → Mỗi invalid partition = 1 test case riêng             ║
║     → Để verify correct error handling                      ║
║     → Nếu combine: Không biết lỗi nào gây fail             ║
║                                                               ║
║  4️⃣ LUÔN CÓ CẢ VALID VÀ INVALID                               ║
║     → Đừng chỉ test happy path                              ║
║     → Invalid partitions test error handling                ║
║                                                               ║
╚═══════════════════════════════════════════════════════════════╝
```

---

## 6. BÀI TẬP THỰC HÀNH

### Bài tập 1: Product Quantity

**Requirement**: E-commerce website cho phép order quantity từ 1 đến 99 items.

**Yêu cầu**: Xác định partitions và tạo test cases.

<details>
<summary>Đáp án</summary>

**Partitions:**
- P1 (Invalid): < 1 (e.g., 0, -5)
- P2 (Valid): 1 - 99
- P3 (Invalid): > 99 (e.g., 100, 150)
- P4 (Invalid): Non-integer (e.g., 2.5, "abc")

**Test Cases:**

| TC | Quantity | Expected |
|----|----------|----------|
| TC1 | 0 | Error: "Minimum quantity is 1" |
| TC2 | 50 | Order accepted |
| TC3 | 100 | Error: "Maximum quantity is 99" |
| TC4 | 2.5 | Error: "Must be a whole number" |

Coverage: 4/4 = 100%
</details>

---

### Bài tập 2: Username Registration

**Requirement**:
- Username: 4-15 characters
- Only letters, numbers, underscore
- Cannot start with number

**Yêu cầu**: Xác định partitions và test cases.

<details>
<summary>Đáp án</summary>

**Partitions:**
- P1 (Valid): 4-15 chars, valid chars, starts with letter/underscore
- P2 (Invalid): < 4 characters
- P3 (Invalid): > 15 characters
- P4 (Invalid): Contains special characters (!@#$)
- P5 (Invalid): Starts with number
- P6 (Invalid): Empty

**Test Cases:**

| TC | Username | Expected |
|----|----------|----------|
| TC1 | john_doe | Registration successful |
| TC2 | joe | Error: "Minimum 4 characters" |
| TC3 | johndoe123456789 | Error: "Maximum 15 characters" |
| TC4 | john@doe | Error: "Only letters, numbers, underscore" |
| TC5 | 1johndoe | Error: "Cannot start with number" |
| TC6 | (empty) | Error: "Username required" |

Coverage: 6/6 = 100%
</details>

---

### Bài tập 3: Flight Booking - Passenger Count

**Requirement**:
- Minimum: 1 passenger
- Maximum: 9 passengers
- At least 1 adult required for booking

Passenger types: Adult (12+), Child (2-11), Infant (0-1)

**Yêu cầu**: Xác định partitions cho total passengers và tạo test cases.

<details>
<summary>Đáp án</summary>

**Partitions for Total Passengers:**
- P1 (Invalid): 0 passengers
- P2 (Valid): 1-9 passengers
- P3 (Invalid): > 9 passengers

**Partitions for Adult Count:**
- P4 (Invalid): 0 adults (at least 1 required)
- P5 (Valid): ≥ 1 adult

**Test Cases:**

| TC | Adults | Children | Infants | Total | Expected |
|----|--------|----------|---------|-------|----------|
| TC1 | 2 | 1 | 0 | 3 | Booking successful |
| TC2 | 0 | 0 | 0 | 0 | Error: "At least 1 passenger" |
| TC3 | 5 | 3 | 2 | 10 | Error: "Maximum 9 passengers" |
| TC4 | 0 | 2 | 1 | 3 | Error: "At least 1 adult required" |

</details>

---

## 7. CÂU HỎI ÔN TẬP

### Câu 1 (K3)
Cho requirement: "Order amount must be between 50,000 VND and 10,000,000 VND"

Minimum number of test cases để đạt 100% EP coverage là bao nhiêu?

A. 2
B. 3
C. 4
D. 5

<details>
<summary>Đáp án</summary>

**B. 3**

Partitions:
- P1 (Invalid): < 50,000
- P2 (Valid): 50,000 - 10,000,000
- P3 (Invalid): > 10,000,000

3 partitions → 3 test cases
</details>

---

### Câu 2 (K3)
Cho input field "Password" với requirement: 8-16 characters. Invalid partitions nào cần được test?

A. Only passwords with < 8 characters
B. Only passwords with > 16 characters
C. Both < 8 và > 16 characters, mỗi cái test riêng
D. Không cần test invalid

<details>
<summary>Đáp án</summary>

**C. Both < 8 và > 16 characters, mỗi cái test riêng**

Invalid partitions phải test riêng để verify đúng error message cho từng case.
</details>

---

### Câu 3 (K3)
Với 2 input fields, mỗi field có 3 partitions (1 valid, 2 invalid). Minimum test cases cần là bao nhiêu?

A. 3
B. 5
C. 6
D. 9

<details>
<summary>Đáp án</summary>

**B. 5**

- TC1: Valid1 + Valid2 (combine valid)
- TC2: Invalid1a + Valid2
- TC3: Invalid1b + Valid2
- TC4: Valid1 + Invalid2a
- TC5: Valid1 + Invalid2b

Invalid partitions test riêng, valid có thể combine.
</details>

---

## 8. CHECKLIST TỰ ĐÁNH GIÁ

- [ ] Hiểu được nguyên lý của Equivalence Partitioning
- [ ] Phân biệt được Valid và Invalid partitions
- [ ] Có thể xác định partitions từ requirements
- [ ] Biết cách chọn test values từ mỗi partition
- [ ] Hiểu quy tắc: Valid combine, Invalid test riêng
- [ ] Tính được EP coverage
- [ ] Hoàn thành được các bài tập thực hành

---

**Tiếp theo**: [Module 4.3: Boundary Value Analysis](./module-4.3-boundary-value-analysis.md)

---

**Version**: 1.0.0
**Last Updated**: November 2025
