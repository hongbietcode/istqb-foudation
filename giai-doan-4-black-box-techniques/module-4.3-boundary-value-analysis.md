# MODULE 4.3: BOUNDARY VALUE ANALYSIS (BVA)

**Thời lượng**: 4-5 giờ | **Độ khó**: ⭐⭐⭐
**Tầm quan trọng**: ~15% câu hỏi trong kỳ thi ISTQB

---

## MỤC TIÊU HỌC TẬP

Sau khi hoàn thành module này, bạn sẽ:

| ID | Mục tiêu | Level |
|----|----------|-------|
| FL-4.2.2 | Sử dụng Boundary Value Analysis để derive test cases | K3 |

---

## 1. BOUNDARY VALUE ANALYSIS LÀ GÌ?

### 1.1. Định Nghĩa

> **Boundary Value Analysis (BVA)** là kỹ thuật test tại các **giá trị biên** (boundaries) của các partitions, vì bugs thường xảy ra tại các điểm biên.

```
╔═══════════════════════════════════════════════════════════════╗
║                 BOUNDARY VALUE ANALYSIS                       ║
╠═══════════════════════════════════════════════════════════════╣
║                                                               ║
║  NGUYÊN LÝ:                                                   ║
║  ─────────                                                    ║
║  BUGS thường xảy ra tại BOUNDARIES!                          ║
║                                                               ║
║  Lý do:                                                       ║
║  • Developer dùng < thay vì <=                               ║
║  • Off-by-one errors                                         ║
║  • Incorrect boundary checks                                 ║
║                                                               ║
║  VÍ DỤ: Age 18-65                                            ║
║  ────────────────────                                         ║
║                                                               ║
║         17    18    19  ...  64    65    66                  ║
║          │     │     │        │     │     │                  ║
║          ▼     ▼     ▼        ▼     ▼     ▼                  ║
║       ┌─────┬─────┬─────────────────┬─────┬─────┐           ║
║       │INVLD│BOUND│     VALID       │BOUND│INVLD│           ║
║       └─────┴─────┴─────────────────┴─────┴─────┘           ║
║              ↑                           ↑                   ║
║           Lower                       Upper                   ║
║          Boundary                    Boundary                 ║
║                                                               ║
║  → Test ở 17, 18, 65, 66 có khả năng tìm bugs cao hơn!     ║
║                                                               ║
╚═══════════════════════════════════════════════════════════════╝
```

### 1.2. BVA Là Extension Của EP

```
╔═══════════════════════════════════════════════════════════════╗
║                  EP + BVA = COMPREHENSIVE                     ║
╠═══════════════════════════════════════════════════════════════╣
║                                                               ║
║  EP: Chia thành partitions, test 1 value BẤT KỲ từ mỗi      ║
║      partition                                                ║
║                                                               ║
║  BVA: Test specifically ở BOUNDARIES của partitions          ║
║                                                               ║
║  EXAMPLE: Age 18-65                                          ║
║                                                               ║
║  ┌─────────────────────────────────────────────────────────┐ ║
║  │ Invalid │         Valid (18-65)         │ Invalid       │ ║
║  │  < 18   │                               │  > 65         │ ║
║  └─────────┴───────────────────────────────┴───────────────┘ ║
║        │    │                           │    │               ║
║        │    │                           │    │               ║
║        ▼    ▼                           ▼    ▼               ║
║        17   18                          65   66              ║
║        ↑    ↑                           ↑    ↑               ║
║    Just  Lower                       Upper  Just             ║
║   below  bound                       bound  above            ║
║                                                               ║
║  EP only:  Test 10, 30, 80 (any value from each partition)  ║
║  EP + BVA: Test 17, 18, 65, 66 (at boundaries)              ║
║                                                               ║
╚═══════════════════════════════════════════════════════════════╝
```

---

## 2. HAI LOẠI BVA

### 2.1. 2-Value BVA (Two-Point BVA)

```
╔═══════════════════════════════════════════════════════════════╗
║                    2-VALUE BVA                                ║
╠═══════════════════════════════════════════════════════════════╣
║                                                               ║
║  Test 2 values tại mỗi boundary:                             ║
║  • Boundary value itself                                      ║
║  • Value ngay ngoài boundary (invalid side)                  ║
║                                                               ║
║  EXAMPLE: Valid range 18-65                                  ║
║                                                               ║
║          17     18                        65     66          ║
║           │      │                         │      │          ║
║           ▼      ▼                         ▼      ▼          ║
║       ──────────────────────────────────────────────         ║
║       Invalid │        Valid              │ Invalid          ║
║           ↑      ↑                         ↑      ↑          ║
║         Just   Lower                     Upper   Just        ║
║        below   bound                     bound   above       ║
║                                                               ║
║  TEST VALUES:                                                 ║
║  • Lower boundary: 17 (invalid), 18 (valid)                  ║
║  • Upper boundary: 65 (valid), 66 (invalid)                  ║
║                                                               ║
║  TOTAL: 4 test values cho 2-value BVA                        ║
║                                                               ║
╚═══════════════════════════════════════════════════════════════╝
```

### 2.2. 3-Value BVA (Three-Point BVA)

```
╔═══════════════════════════════════════════════════════════════╗
║                    3-VALUE BVA                                ║
╠═══════════════════════════════════════════════════════════════╣
║                                                               ║
║  Test 3 values tại mỗi boundary:                             ║
║  • Value ngay TRƯỚC boundary (just below)                    ║
║  • Boundary value itself                                      ║
║  • Value ngay SAU boundary (just above)                      ║
║                                                               ║
║  EXAMPLE: Valid range 18-65                                  ║
║                                                               ║
║       17    18    19              64    65    66             ║
║        │     │     │               │     │     │             ║
║        ▼     ▼     ▼               ▼     ▼     ▼             ║
║       ──────────────────────────────────────────────         ║
║       Invalid │           Valid           │ Invalid          ║
║        ↑     ↑     ↑               ↑     ↑     ↑             ║
║      Below Lower Above           Below Upper Above           ║
║            Bound                       Bound                  ║
║                                                               ║
║  TEST VALUES:                                                 ║
║  • Lower boundary: 17, 18, 19                                ║
║  • Upper boundary: 64, 65, 66                                ║
║                                                               ║
║  TOTAL: 6 test values cho 3-value BVA                        ║
║                                                               ║
╚═══════════════════════════════════════════════════════════════╝
```

### 2.3. So Sánh 2-Value và 3-Value BVA

| Aspect | 2-Value BVA | 3-Value BVA |
|--------|-------------|-------------|
| **Values/boundary** | 2 | 3 |
| **Total tests** | 4 (for 2 boundaries) | 6 (for 2 boundaries) |
| **Coverage** | Less thorough | More thorough |
| **Bug finding** | Good | Better |
| **Effort** | Less | More |
| **ISTQB default** | ✓ (Syllabus v4.0) | |

---

## 3. VÍ DỤ CHI TIẾT

### 3.1. Ví Dụ 1: Age Validation (18-65)

```
REQUIREMENT: User age must be between 18 and 65 (inclusive)

═══════════════════════════════════════════════════════════════

2-VALUE BVA:
────────────
Lower boundary: 17, 18
Upper boundary: 65, 66

┌──────┬───────┬─────────────────────────────────────────────┐
│ TC   │ Age   │ Expected Result                             │
├──────┼───────┼─────────────────────────────────────────────┤
│ TC1  │  17   │ Error: "Must be at least 18"               │
│ TC2  │  18   │ Success (boundary - accepted)              │
│ TC3  │  65   │ Success (boundary - accepted)              │
│ TC4  │  66   │ Error: "Must be 65 or younger"             │
└──────┴───────┴─────────────────────────────────────────────┘

═══════════════════════════════════════════════════════════════

3-VALUE BVA:
────────────
Lower boundary: 17, 18, 19
Upper boundary: 64, 65, 66

┌──────┬───────┬─────────────────────────────────────────────┐
│ TC   │ Age   │ Expected Result                             │
├──────┼───────┼─────────────────────────────────────────────┤
│ TC1  │  17   │ Error: "Must be at least 18"               │
│ TC2  │  18   │ Success                                     │
│ TC3  │  19   │ Success                                     │
│ TC4  │  64   │ Success                                     │
│ TC5  │  65   │ Success                                     │
│ TC6  │  66   │ Error: "Must be 65 or younger"             │
└──────┴───────┴─────────────────────────────────────────────┘
```

### 3.2. Ví Dụ 2: Password Length (8-20 characters)

```
REQUIREMENT: Password must be 8-20 characters

═══════════════════════════════════════════════════════════════

PARTITIONS (EP):
• Invalid: < 8 characters
• Valid: 8-20 characters
• Invalid: > 20 characters

BOUNDARIES:
• Lower: 7, 8 (2-value) or 7, 8, 9 (3-value)
• Upper: 19, 20, 21 (3-value) or 20, 21 (2-value)

═══════════════════════════════════════════════════════════════

2-VALUE BVA TEST CASES:
───────────────────────
┌──────┬──────────────────────┬───────────────────────────────┐
│ TC   │ Password             │ Expected Result               │
├──────┼──────────────────────┼───────────────────────────────┤
│ TC1  │ "Pass123" (7 chars)  │ Error: "Min 8 characters"    │
│ TC2  │ "Pass1234" (8 chars) │ Success                       │
│ TC3  │ "Pass...20chars"     │ Success                       │
│ TC4  │ "Pass...21chars"     │ Error: "Max 20 characters"   │
└──────┴──────────────────────┴───────────────────────────────┘

═══════════════════════════════════════════════════════════════

3-VALUE BVA TEST CASES:
───────────────────────
┌──────┬──────────────────────┬───────────────────────────────┐
│ TC   │ Password             │ Expected Result               │
├──────┼──────────────────────┼───────────────────────────────┤
│ TC1  │ 7 characters         │ Error                         │
│ TC2  │ 8 characters         │ Success                       │
│ TC3  │ 9 characters         │ Success                       │
│ TC4  │ 19 characters        │ Success                       │
│ TC5  │ 20 characters        │ Success                       │
│ TC6  │ 21 characters        │ Error                         │
└──────┴──────────────────────┴───────────────────────────────┘
```

### 3.3. Ví Dụ 3: Order Quantity (1-99)

```
REQUIREMENT: Order quantity must be 1-99 items

═══════════════════════════════════════════════════════════════

2-VALUE BVA:
────────────
Lower: 0, 1
Upper: 99, 100

┌──────┬──────────┬─────────────────────────────────────────┐
│ TC   │ Quantity │ Expected Result                         │
├──────┼──────────┼─────────────────────────────────────────┤
│ TC1  │    0     │ Error: "Minimum quantity is 1"         │
│ TC2  │    1     │ Success (lower boundary)               │
│ TC3  │   99     │ Success (upper boundary)               │
│ TC4  │  100     │ Error: "Maximum quantity is 99"        │
└──────┴──────────┴─────────────────────────────────────────┘
```

### 3.4. Ví Dụ 4: Transfer Amount (VNPay)

```
REQUIREMENT: Transfer 10,000 - 500,000,000 VND

═══════════════════════════════════════════════════════════════

2-VALUE BVA:
────────────
Lower: 9,999 and 10,000
Upper: 500,000,000 and 500,000,001

┌──────┬───────────────┬─────────────────────────────────────┐
│ TC   │ Amount (VND)  │ Expected Result                     │
├──────┼───────────────┼─────────────────────────────────────┤
│ TC1  │     9,999     │ Error: "Minimum is 10,000 VND"     │
│ TC2  │    10,000     │ Success                             │
│ TC3  │ 500,000,000   │ Success                             │
│ TC4  │ 500,000,001   │ Error: "Maximum is 500M VND"       │
└──────┴───────────────┴─────────────────────────────────────┘

3-VALUE BVA:
────────────
Lower: 9,999 / 10,000 / 10,001
Upper: 499,999,999 / 500,000,000 / 500,000,001

(6 test cases total)
```

---

## 4. CÔNG THỨC TÍNH SỐ TEST CASES

```
╔═══════════════════════════════════════════════════════════════╗
║              CÔNG THỨC TÍNH SỐ TEST CASES                     ║
╠═══════════════════════════════════════════════════════════════╣
║                                                               ║
║  2-VALUE BVA:                                                 ║
║  ────────────                                                 ║
║  Number of test values = 2 × Number of boundaries            ║
║                                                               ║
║  Example: Range 18-65 có 2 boundaries                        ║
║  Test values = 2 × 2 = 4 (17, 18, 65, 66)                   ║
║                                                               ║
║  ═══════════════════════════════════════════════════════════  ║
║                                                               ║
║  3-VALUE BVA:                                                 ║
║  ────────────                                                 ║
║  Number of test values = 3 × Number of boundaries            ║
║                                                               ║
║  Example: Range 18-65 có 2 boundaries                        ║
║  Test values = 3 × 2 = 6 (17, 18, 19, 64, 65, 66)           ║
║                                                               ║
║  ═══════════════════════════════════════════════════════════  ║
║                                                               ║
║  MULTIPLE INPUTS:                                             ║
║  ────────────────                                             ║
║  Total = Sum of boundary values for all inputs               ║
║                                                               ║
║  Example: Input A (1-100) + Input B (0-50)                   ║
║  2-value: (2×2) + (2×2) = 8 boundary values                 ║
║                                                               ║
╚═══════════════════════════════════════════════════════════════╝
```

---

## 5. KẾT HỢP EP VÀ BVA

### 5.1. Quy Trình Kết Hợp

```
╔═══════════════════════════════════════════════════════════════╗
║                  EP + BVA COMBINED                            ║
╠═══════════════════════════════════════════════════════════════╣
║                                                               ║
║  STEP 1: Apply EP first                                       ║
║          → Xác định valid và invalid partitions              ║
║                                                               ║
║  STEP 2: Apply BVA at boundaries                             ║
║          → Xác định boundary values                          ║
║                                                               ║
║  STEP 3: Create test cases                                    ║
║          → BVA values cover the boundaries                   ║
║          → EP value (middle) optional if needed              ║
║                                                               ║
╚═══════════════════════════════════════════════════════════════╝
```

### 5.2. Ví Dụ Kết Hợp: Quantity (1-99)

```
═══════════════════════════════════════════════════════════════
EP ONLY (3 test cases):
═══════════════════════════════════════════════════════════════
• Invalid < 1:  Test với 0 hoặc -5
• Valid 1-99:   Test với 50 (any middle value)
• Invalid > 99: Test với 100 hoặc 150

═══════════════════════════════════════════════════════════════
2-VALUE BVA (4 test cases):
═══════════════════════════════════════════════════════════════
• 0 (just below lower boundary)
• 1 (lower boundary)
• 99 (upper boundary)
• 100 (just above upper boundary)

═══════════════════════════════════════════════════════════════
EP + BVA COMBINED:
═══════════════════════════════════════════════════════════════
BVA đã cover:
• Invalid < 1: ✓ (value 0)
• Valid 1-99: ✓ (values 1 và 99)
• Invalid > 99: ✓ (value 100)

→ BVA 4 test cases đủ cover cả EP partitions!
→ Không cần thêm middle value (50) vì không likely có bugs
```

---

## 6. BÀI TẬP THỰC HÀNH

### Bài tập 1: Discount Percentage

**Requirement**: Discount percentage must be between 5% and 50%

**Yêu cầu**: Tạo test cases với 2-value BVA

<details>
<summary>Đáp án</summary>

**Boundaries:**
- Lower: 4, 5
- Upper: 50, 51

**Test Cases:**

| TC | Discount % | Expected |
|----|------------|----------|
| TC1 | 4 | Error: "Minimum discount is 5%" |
| TC2 | 5 | Valid - discount applied |
| TC3 | 50 | Valid - discount applied |
| TC4 | 51 | Error: "Maximum discount is 50%" |

</details>

---

### Bài tập 2: File Upload Size

**Requirement**: File upload must be between 1KB and 10MB (10,240 KB)

**Yêu cầu**: Tạo test cases với 3-value BVA

<details>
<summary>Đáp án</summary>

**Boundaries (in KB):**
- Lower: 0, 1, 2
- Upper: 10,239, 10,240, 10,241

**Test Cases:**

| TC | Size (KB) | Expected |
|----|-----------|----------|
| TC1 | 0 | Error: "File too small" |
| TC2 | 1 | Success (lower boundary) |
| TC3 | 2 | Success |
| TC4 | 10,239 | Success |
| TC5 | 10,240 | Success (upper boundary) |
| TC6 | 10,241 | Error: "File exceeds 10MB limit" |

</details>

---

### Bài tập 3: PIN Code

**Requirement**: PIN must be exactly 6 digits (no more, no less)

**Yêu cầu**: Xác định boundaries và test cases

<details>
<summary>Đáp án</summary>

**Analysis:**
- Valid: Exactly 6 digits
- Invalid: < 6 digits
- Invalid: > 6 digits

**Boundaries (length):**
- Lower: 5, 6
- Upper: 6, 7

**Test Cases (2-value BVA):**

| TC | PIN | Length | Expected |
|----|-----|--------|----------|
| TC1 | 12345 | 5 | Error: "PIN must be 6 digits" |
| TC2 | 123456 | 6 | Success |
| TC3 | 1234567 | 7 | Error: "PIN must be 6 digits" |

Note: TC2 covers cả lower và upper boundary vì valid range chỉ có 1 value (6).

</details>

---

## 7. CÂU HỎI ÔN TẬP

### Câu 1 (K3)
Với requirement "Quantity must be 1-10", sử dụng 2-value BVA, test values nào cần test?

A. 0, 1, 10, 11
B. 1, 5, 10
C. 0, 5, 11
D. 1, 2, 9, 10

<details>
<summary>Đáp án</summary>

**A. 0, 1, 10, 11**

2-value BVA test:
- Lower boundary: 0 (just below), 1 (boundary)
- Upper boundary: 10 (boundary), 11 (just above)
</details>

---

### Câu 2 (K3)
Với requirement "Age 18-60", 3-value BVA cần bao nhiêu test cases?

A. 4
B. 6
C. 8
D. 3

<details>
<summary>Đáp án</summary>

**B. 6**

3-value BVA: 3 values × 2 boundaries = 6
- Lower: 17, 18, 19
- Upper: 59, 60, 61
</details>

---

### Câu 3 (K2)
Tại sao BVA hiệu quả trong việc tìm bugs?

A. Vì test ít cases hơn
B. Vì bugs thường xảy ra ở boundaries do coding mistakes
C. Vì không cần biết requirements
D. Vì dễ automate hơn

<details>
<summary>Đáp án</summary>

**B. Vì bugs thường xảy ra ở boundaries do coding mistakes**

Off-by-one errors, incorrect operators (<= vs <) thường xảy ra ở boundaries.
</details>

---

## 8. CHECKLIST TỰ ĐÁNH GIÁ

- [ ] Hiểu được nguyên lý của BVA
- [ ] Phân biệt được 2-value và 3-value BVA
- [ ] Xác định được boundary values từ requirements
- [ ] Tính được số test cases cần thiết
- [ ] Kết hợp được EP và BVA hiệu quả
- [ ] Hoàn thành được các bài tập thực hành

---

**Tiếp theo**: [Module 4.4: Decision Table Testing](./module-4.4-decision-table-testing.md)

---

**Version**: 1.0.0
**Last Updated**: November 2025
