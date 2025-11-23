# MODULE 4.4: DECISION TABLE TESTING

**Thời lượng**: 4-5 giờ | **Độ khó**: ⭐⭐⭐
**Tầm quan trọng**: ~10% câu hỏi trong kỳ thi ISTQB

---

## MỤC TIÊU HỌC TẬP

| ID | Mục tiêu | Level |
|----|----------|-------|
| FL-4.2.3 | Sử dụng Decision Table Testing để derive test cases | K3 |

---

## 1. DECISION TABLE LÀ GÌ?

### 1.1. Định Nghĩa

> **Decision Table** là kỹ thuật test các **combinations của conditions** và verify rằng hệ thống thực hiện đúng **actions** tương ứng.

```
╔═══════════════════════════════════════════════════════════════╗
║                    DECISION TABLE                             ║
╠═══════════════════════════════════════════════════════════════╣
║                                                               ║
║  NGUYÊN LÝ:                                                   ║
║  ─────────                                                    ║
║  Với nhiều conditions, có nhiều COMBINATIONS                 ║
║  Mỗi combination dẫn đến ACTION khác nhau                    ║
║  Decision Table giúp systematic cover tất cả combinations    ║
║                                                               ║
║  VÍ DỤ: Loan Approval                                        ║
║  ─────────────────────                                        ║
║                                                               ║
║  CONDITIONS:              │ COMBINATION 1 │ COMBINATION 2    ║
║  ─────────────────────────┼───────────────┼─────────────────  ║
║  Income > 10M VND?        │      Yes      │       No         ║
║  Good credit score?       │      Yes      │       Yes        ║
║  Has collateral?          │      No       │       Yes        ║
║  ─────────────────────────┼───────────────┼─────────────────  ║
║  ACTIONS:                 │               │                   ║
║  ─────────────────────────┼───────────────┼─────────────────  ║
║  Approve loan             │      Yes      │       Yes        ║
║  Interest rate            │      12%      │       15%        ║
║                                                               ║
╚═══════════════════════════════════════════════════════════════╝
```

### 1.2. Khi Nào Sử Dụng?

```
✅ SỬ DỤNG DECISION TABLE KHI:
   • Có nhiều conditions ảnh hưởng đến outcome
   • Business rules phức tạp (if-then-else)
   • Cần test tất cả combinations
   • Discount/pricing rules
   • Approval processes
   • Access control rules
```

---

## 2. CẤU TRÚC DECISION TABLE

### 2.1. Các Thành Phần

```
╔═══════════════════════════════════════════════════════════════╗
║              CẤU TRÚC DECISION TABLE                          ║
╠═══════════════════════════════════════════════════════════════╣
║                                                               ║
║                    │ Rule 1 │ Rule 2 │ Rule 3 │ Rule 4       ║
║  ══════════════════╪════════╪════════╪════════╪════════      ║
║  CONDITIONS:       │        │        │        │               ║
║  ──────────────────┼────────┼────────┼────────┼────────      ║
║  Condition 1       │   T    │   T    │   F    │   F          ║
║  Condition 2       │   T    │   F    │   T    │   F          ║
║  ══════════════════╪════════╪════════╪════════╪════════      ║
║  ACTIONS:          │        │        │        │               ║
║  ──────────────────┼────────┼────────┼────────┼────────      ║
║  Action 1          │   X    │        │   X    │               ║
║  Action 2          │        │   X    │        │   X          ║
║                                                               ║
║  GIẢI THÍCH:                                                  ║
║  • CONDITIONS: Các điều kiện input (T=True, F=False)         ║
║  • ACTIONS: Kết quả/hành động (X = thực hiện)               ║
║  • RULES: Mỗi cột là một combination                        ║
║  • Số rules = 2^n (với n conditions, nếu Boolean)           ║
║                                                               ║
╚═══════════════════════════════════════════════════════════════╝
```

### 2.2. Limited-Entry vs Extended-Entry

```
╔═══════════════════════════════════════════════════════════════╗
║         LIMITED-ENTRY vs EXTENDED-ENTRY TABLES                ║
╠═══════════════════════════════════════════════════════════════╣
║                                                               ║
║  LIMITED-ENTRY: Conditions are Boolean (Yes/No, True/False)  ║
║  ─────────────────────────────────────────────────────────── ║
║                    │ R1 │ R2 │ R3 │ R4                       ║
║  ──────────────────┼────┼────┼────┼────                       ║
║  Member?           │ Y  │ Y  │ N  │ N                        ║
║  Order > 1M?       │ Y  │ N  │ Y  │ N                        ║
║  ──────────────────┼────┼────┼────┼────                       ║
║  Discount 20%      │ X  │    │    │                          ║
║  Discount 10%      │    │ X  │ X  │                          ║
║  No discount       │    │    │    │ X                        ║
║                                                               ║
║  EXTENDED-ENTRY: Conditions có nhiều values                  ║
║  ─────────────────────────────────────────────────────────── ║
║                    │  R1    │  R2    │  R3                   ║
║  ──────────────────┼────────┼────────┼────────               ║
║  Member level      │ Gold   │ Silver │ Regular               ║
║  Order amount      │ >1M    │ >500K  │ Any                   ║
║  ──────────────────┼────────┼────────┼────────               ║
║  Discount          │ 20%    │ 10%    │ 5%                    ║
║                                                               ║
╚═══════════════════════════════════════════════════════════════╝
```

---

## 3. QUY TRÌNH TẠO DECISION TABLE

```
╔═══════════════════════════════════════════════════════════════╗
║           QUY TRÌNH TẠO DECISION TABLE                        ║
╠═══════════════════════════════════════════════════════════════╣
║                                                               ║
║  STEP 1: XÁC ĐỊNH CONDITIONS                                  ║
║          → List tất cả conditions từ requirements            ║
║                                                               ║
║  STEP 2: XÁC ĐỊNH ACTIONS                                     ║
║          → List tất cả possible actions/outcomes             ║
║                                                               ║
║  STEP 3: TẠO TẤT CẢ RULES (Combinations)                      ║
║          → Với n Boolean conditions: 2^n rules               ║
║                                                               ║
║  STEP 4: XÁC ĐỊNH ACTIONS CHO MỖI RULE                        ║
║          → Dựa vào business logic                            ║
║                                                               ║
║  STEP 5: (Optional) SIMPLIFY/COLLAPSE                         ║
║          → Merge rules có same actions                       ║
║                                                               ║
║  STEP 6: TẠO TEST CASES                                       ║
║          → 1 test case per rule                              ║
║                                                               ║
╚═══════════════════════════════════════════════════════════════╝
```

---

## 4. VÍ DỤ CHI TIẾT

### 4.1. Ví Dụ 1: E-commerce Discount

**Business Rules**:
- If customer is Member AND order > 1,000,000 VND → 20% discount
- If customer is Member AND order ≤ 1,000,000 VND → 10% discount
- If NOT member AND order > 1,000,000 VND → 10% discount
- If NOT member AND order ≤ 1,000,000 VND → No discount

```
STEP 1 & 2: CONDITIONS và ACTIONS
═════════════════════════════════════════════════════════════════

CONDITIONS:
C1: Is customer a member?        (Yes/No)
C2: Order amount > 1,000,000?    (Yes/No)

ACTIONS:
A1: Apply 20% discount
A2: Apply 10% discount
A3: No discount

STEP 3 & 4: DECISION TABLE (Full)
═════════════════════════════════════════════════════════════════

                        │ Rule 1 │ Rule 2 │ Rule 3 │ Rule 4
════════════════════════╪════════╪════════╪════════╪════════
CONDITIONS:             │        │        │        │
────────────────────────┼────────┼────────┼────────┼────────
C1: Member?             │   Y    │   Y    │   N    │   N
C2: Order > 1M?         │   Y    │   N    │   Y    │   N
════════════════════════╪════════╪════════╪════════╪════════
ACTIONS:                │        │        │        │
────────────────────────┼────────┼────────┼────────┼────────
A1: 20% discount        │   X    │        │        │
A2: 10% discount        │        │   X    │   X    │
A3: No discount         │        │        │        │   X

STEP 6: TEST CASES
═════════════════════════════════════════════════════════════════

┌──────┬─────────┬───────────┬──────────────────────────────────┐
│ TC   │ Member? │ Amount    │ Expected Result                  │
├──────┼─────────┼───────────┼──────────────────────────────────┤
│ TC1  │   Yes   │ 2,000,000 │ 20% discount → Pay 1,600,000    │
│ TC2  │   Yes   │   500,000 │ 10% discount → Pay 450,000      │
│ TC3  │   No    │ 2,000,000 │ 10% discount → Pay 1,800,000    │
│ TC4  │   No    │   500,000 │ No discount → Pay 500,000       │
└──────┴─────────┴───────────┴──────────────────────────────────┘

Coverage: 4 rules, 4 test cases = 100%
```

### 4.2. Ví Dụ 2: Flight Booking Rules (3 Conditions)

**Business Rules**:
- Domestic flight + Economy class → Price = Base price
- Domestic flight + Business class → Price = Base × 2
- International flight + Economy class → Price = Base × 3
- International flight + Business class → Price = Base × 5
- Weekend surcharge: Add 10% if booking for weekend

```
CONDITIONS:
C1: International flight? (Y/N)
C2: Business class? (Y/N)
C3: Weekend? (Y/N)

ACTIONS:
A1: Base price (1x)
A2: Business domestic (2x)
A3: Economy international (3x)
A4: Business international (5x)
A5: Add 10% weekend surcharge

DECISION TABLE (2^3 = 8 rules):
═════════════════════════════════════════════════════════════════

               │ R1 │ R2 │ R3 │ R4 │ R5 │ R6 │ R7 │ R8
═══════════════╪════╪════╪════╪════╪════╪════╪════╪════
C1: Intl?      │ Y  │ Y  │ Y  │ Y  │ N  │ N  │ N  │ N
C2: Business?  │ Y  │ Y  │ N  │ N  │ Y  │ Y  │ N  │ N
C3: Weekend?   │ Y  │ N  │ Y  │ N  │ Y  │ N  │ Y  │ N
═══════════════╪════╪════╪════╪════╪════╪════╪════╪════
A1: 1x         │    │    │    │    │    │    │ X  │ X
A2: 2x         │    │    │    │    │ X  │ X  │    │
A3: 3x         │    │    │ X  │ X  │    │    │    │
A4: 5x         │ X  │ X  │    │    │    │    │    │
A5: +10%       │ X  │    │ X  │    │ X  │    │ X  │

TEST CASES: 8 test cases (1 per rule)
```

### 4.3. Ví Dụ 3: Simplified Table (Collapsed Rules)

```
ORIGINAL: 8 rules (from Example 2)

SIMPLIFIED (merge rules with same base price, ignore weekend):

               │ R1      │ R2          │ R3       │ R4
═══════════════╪═════════╪═════════════╪══════════╪════════
C1: Intl?      │ N       │ N           │ Y        │ Y
C2: Business?  │ N       │ Y           │ N        │ Y
C3: Weekend?   │ -       │ -           │ -        │ -
═══════════════╪═════════╪═════════════╪══════════╪════════
Price          │ 1x      │ 2x          │ 3x       │ 5x

("-" means "don't care" - condition doesn't affect base price)

Note: Weekend surcharge được test separately
```

---

## 5. TÍNH SỐ RULES VÀ COVERAGE

```
╔═══════════════════════════════════════════════════════════════╗
║              TÍNH SỐ RULES                                    ║
╠═══════════════════════════════════════════════════════════════╣
║                                                               ║
║  FULL TABLE (Boolean conditions):                             ║
║  ────────────────────────────────                             ║
║  Number of Rules = 2^n                                        ║
║  (n = number of Boolean conditions)                          ║
║                                                               ║
║  Examples:                                                    ║
║  • 2 conditions → 2² = 4 rules                               ║
║  • 3 conditions → 2³ = 8 rules                               ║
║  • 4 conditions → 2⁴ = 16 rules                              ║
║  • 5 conditions → 2⁵ = 32 rules                              ║
║                                                               ║
║  ═══════════════════════════════════════════════════════════  ║
║                                                               ║
║  COVERAGE:                                                    ║
║  ─────────                                                    ║
║  Coverage (%) = (Rules tested / Total rules) × 100%          ║
║                                                               ║
║  100% coverage = Test ALL rules                              ║
║                                                               ║
╚═══════════════════════════════════════════════════════════════╝
```

---

## 6. BÀI TẬP THỰC HÀNH

### Bài tập 1: Insurance Premium

**Business Rules**:
- Age < 25: High risk premium
- Age ≥ 25: Standard premium
- Smoker: Add 50% to premium
- Non-smoker: No additional charge

**Yêu cầu**: Tạo decision table và test cases.

<details>
<summary>Đáp án</summary>

**Conditions:**
- C1: Age < 25? (Y/N)
- C2: Smoker? (Y/N)

**Actions:**
- A1: High risk premium
- A2: Standard premium
- A3: Add 50% for smoking

**Decision Table:**

|  | R1 | R2 | R3 | R4 |
|--|----|----|----|----|
| C1: Age < 25? | Y | Y | N | N |
| C2: Smoker? | Y | N | Y | N |
| A1: High risk | X | X | | |
| A2: Standard | | | X | X |
| A3: +50% | X | | X | |

**Test Cases:**

| TC | Age | Smoker | Expected Premium |
|----|-----|--------|------------------|
| TC1 | 22 | Yes | High risk + 50% |
| TC2 | 22 | No | High risk |
| TC3 | 30 | Yes | Standard + 50% |
| TC4 | 30 | No | Standard |

</details>

---

### Bài tập 2: Login Access Control

**Business Rules**:
- Valid username AND valid password → Login success
- Valid username AND invalid password → "Wrong password"
- Invalid username → "User not found" (regardless of password)

**Yêu cầu**: Tạo decision table.

<details>
<summary>Đáp án</summary>

**Conditions:**
- C1: Valid username? (Y/N)
- C2: Valid password? (Y/N)

**Decision Table:**

|  | R1 | R2 | R3 | R4 |
|--|----|----|----|----|
| C1: Valid username? | Y | Y | N | N |
| C2: Valid password? | Y | N | Y | N |
| A1: Login success | X | | | |
| A2: "Wrong password" | | X | | |
| A3: "User not found" | | | X | X |

Note: R3 và R4 có thể collapse vì khi username invalid, password không matter.

**Collapsed:**

|  | R1 | R2 | R3 |
|--|----|----|-----|
| C1: Valid username? | Y | Y | N |
| C2: Valid password? | Y | N | - |
| A1: Login success | X | | |
| A2: "Wrong password" | | X | |
| A3: "User not found" | | | X |

</details>

---

## 7. CÂU HỎI ÔN TẬP

### Câu 1 (K3)
Với 3 Boolean conditions, cần bao nhiêu rules trong full decision table?

A. 3
B. 6
C. 8
D. 9

<details>
<summary>Đáp án</summary>

**C. 8**

2^3 = 8 rules
</details>

---

### Câu 2 (K3)
Decision table testing phù hợp nhất cho scenario nào?

A. Testing input field validation
B. Testing combinations of business rules
C. Testing performance
D. Testing user interface

<details>
<summary>Đáp án</summary>

**B. Testing combinations of business rules**

Decision tables tốt cho testing các combinations của conditions và resulting actions.
</details>

---

## 8. CHECKLIST TỰ ĐÁNH GIÁ

- [ ] Hiểu được nguyên lý của Decision Table
- [ ] Xác định được Conditions và Actions từ requirements
- [ ] Tạo được full decision table
- [ ] Tính được số rules (2^n)
- [ ] Có thể simplify/collapse rules khi cần
- [ ] Tạo được test cases từ decision table

---

**Tiếp theo**: [Module 4.5: State Transition Testing](./module-4.5-state-transition-testing.md)

---

**Version**: 1.0.0
**Last Updated**: November 2025
