# MODULE 5.1: WHITE-BOX TESTING

**Thời lượng**: 3-4 giờ | **Độ khó**: ⭐⭐⭐

---

## MỤC TIÊU HỌC TẬP

Sau khi hoàn thành module này, bạn sẽ:

| ID | Mục tiêu | Level |
|----|----------|-------|
| FL-4.3.1 | Viết test cases từ control flow | K3 |
| FL-4.3.2 | Tính statement coverage | K3 |
| FL-4.3.3 | Tính branch coverage | K3 |
| FL-4.3.4 | Giải thích value của white-box testing | K2 |

---

## 1. WHITE-BOX TESTING LÀ GÌ?

### 1.1. Định Nghĩa

```
╔═══════════════════════════════════════════════════════════════╗
║                   WHITE-BOX TESTING                           ║
╠═══════════════════════════════════════════════════════════════╣
║                                                               ║
║  📖 ĐỊNH NGHĨA:                                               ║
║     Testing dựa trên INTERNAL STRUCTURE của code             ║
║                                                               ║
║  🔧 ĐẶC ĐIỂM:                                                 ║
║     • Cần access và hiểu SOURCE CODE                         ║
║     • Focus on LOGIC, PATHS, CONDITIONS trong code           ║
║     • Also called "Structure-based testing"                  ║
║     • Also called "Glass-box testing" (nhìn xuyên qua)      ║
║                                                               ║
║  👨‍💻 AI LÀM:                                                   ║
║     • Developers (trong unit testing)                        ║
║     • Technical testers (có coding skills)                   ║
║                                                               ║
║  📊 MEASUREMENT:                                              ║
║     • Coverage % (얼마나nhiều code đã được executed)          ║
║                                                               ║
╚═══════════════════════════════════════════════════════════════╝
```

### 1.2. Black-box vs White-box

| Aspect | Black-box | White-box |
|--------|-----------|-----------|
| **Basis** | Specifications | Code structure |
| **Knowledge** | No code access | Need code access |
| **Focus** | Inputs → Outputs | Internal logic, paths |
| **Who** | Testers | Developers, Technical testers |
| **Level** | Any level | Mostly Component (Unit) |
| **Techniques** | EP, BVA, Decision Table | Statement, Branch coverage |

---

## 2. CONTROL FLOW GRAPH (CFG)

### 2.1. CFG Là Gì?

> **Control Flow Graph**: Biểu đồ visual code logic với nodes (statements) và edges (control flow).

```
╔═══════════════════════════════════════════════════════════════╗
║                  CONTROL FLOW GRAPH (CFG)                     ║
╠═══════════════════════════════════════════════════════════════╣
║                                                               ║
║  THÀNH PHẦN:                                                  ║
║                                                               ║
║  ⚪ NODE (hình tròn):                                        ║
║     → Represents 1 hoặc nhiều statements                     ║
║                                                               ║
║  ➡️ EDGE (mũi tên):                                          ║
║     → Represents control flow (program execution path)       ║
║                                                               ║
║  🔷 DECISION NODE (hình thoi):                               ║
║     → Represents IF, WHILE, FOR, SWITCH                      ║
║     → Có ≥2 outgoing edges (True/False branches)            ║
║                                                               ║
╚═══════════════════════════════════════════════════════════════╝
```

### 2.2. Ví Dụ CFG

**Code:**
```javascript
function checkDiscount(amount, isMember) {
    let discount = 0;                    // Statement 1

    if (amount > 1000) {                 // Decision 1
        discount = 10;                   // Statement 2
    }

    if (isMember) {                      // Decision 2
        discount += 5;                   // Statement 3
    }

    return discount;                     // Statement 4
}
```

**Control Flow Graph:**
```
         ┌────────────┐
         │  Start     │
         │  (S1)      │
         └─────┬──────┘
               │
         ┌─────▼──────┐
         │ amount>1000│ (Decision 1)
         │    (D1)    │
         └──┬──────┬──┘
       True │      │ False
            │      │
      ┌─────▼──┐  │
      │   S2   │  │
      │discount│  │
      │  = 10  │  │
      └─────┬──┘  │
            │     │
            └──┬──┘
               │
         ┌─────▼──────┐
         │ isMember?  │ (Decision 2)
         │    (D2)    │
         └──┬──────┬──┘
       True │      │ False
            │      │
      ┌─────▼──┐  │
      │   S3   │  │
      │discount│  │
      │  += 5  │  │
      └─────┬──┘  │
            │     │
            └──┬──┘
               │
         ┌─────▼──────┐
         │  S4        │
         │  return    │
         └────────────┘
```

**Paths trong CFG:**
- Path 1: S1 → D1(F) → D2(F) → S4
- Path 2: S1 → D1(F) → D2(T) → S3 → S4
- Path 3: S1 → D1(T) → S2 → D2(F) → S4
- Path 4: S1 → D1(T) → S2 → D2(T) → S3 → S4

---

## 3. STATEMENT COVERAGE

### 3.1. Statement Coverage Là Gì?

```
╔═══════════════════════════════════════════════════════════════╗
║                    STATEMENT COVERAGE                         ║
╠═══════════════════════════════════════════════════════════════╣
║                                                               ║
║  📖 ĐỊNH NGHĨA:                                               ║
║     % of executable statements được executed ít nhất 1 lần   ║
║                                                               ║
║  📐 CÔNG THỨC:                                                ║
║                                                               ║
║           Number of statements executed                       ║
║     SC = ──────────────────────────────── × 100%             ║
║           Total number of statements                          ║
║                                                               ║
║  🎯 MỤC TIÊU:                                                 ║
║     Execute MỖI statement trong code ít nhất 1 lần          ║
║                                                               ║
║  ✅ LỢI ÍCH:                                                  ║
║     • Find dead code (unreachable code)                      ║
║     • Ensure basic code execution                            ║
║     • Easy to measure                                        ║
║                                                               ║
║  ⚠️ HẠN CHẾ:                                                 ║
║     • Không guarantee test tất cả branches                   ║
║     • Không guarantee test tất cả conditions                 ║
║     • Weakest coverage criterion                             ║
║                                                               ║
╚═══════════════════════════════════════════════════════════════╝
```

### 3.2. Ví Dụ Statement Coverage

**Code:**
```python
def calculate_grade(score):
    grade = "F"              # S1

    if score >= 90:          # S2
        grade = "A"          # S3
    elif score >= 80:        # S4
        grade = "B"          # S5
    elif score >= 70:        # S6
        grade = "C"          # S7
    elif score >= 60:        # S8
        grade = "D"          # S9

    return grade             # S10
```

**Total statements**: 10 (S1-S10)

**Test Case 1**: `score = 85`
- **Executed**: S1, S2(False), S4(True), S5, S10
- **Coverage**: 5/10 = **50%**

**Test Case 2**: `score = 95`
- **Executed**: S1, S2(True), S3, S10
- **Coverage**: 4/10 = **40%**

**Test Suite (TC1 + TC2)**:
- **Executed**: S1, S2, S3, S4, S5, S10 (unique)
- **Coverage**: 6/10 = **60%**

**Để đạt 100% Statement Coverage, cần thêm**:
- TC3: `score = 75` → Execute S6, S7
- TC4: `score = 65` → Execute S8, S9

**Final Coverage với 4 TCs**: 10/10 = **100%**

---

## 4. BRANCH COVERAGE

### 4.1. Branch Coverage Là Gì?

```
╔═══════════════════════════════════════════════════════════════╗
║                     BRANCH COVERAGE                           ║
╠═══════════════════════════════════════════════════════════════╣
║                                                               ║
║  📖 ĐỊNH NGHĨA:                                               ║
║     % of branches (decision outcomes) executed ít nhất 1 lần ║
║                                                               ║
║  📐 CÔNG THỨC:                                                ║
║                                                               ║
║           Number of branches executed                         ║
║     BC = ────────────────────────────── × 100%               ║
║           Total number of branches                            ║
║                                                               ║
║  🎯 MỤC TIÊU:                                                 ║
║     Execute CẢ TRUE và FALSE outcome của mỗi decision        ║
║                                                               ║
║  🔢 TÍNH SỐ BRANCHES:                                         ║
║     • Mỗi IF có 2 branches (True, False)                     ║
║     • Mỗi ELSE IF cũng là 1 decision → +2 branches           ║
║     • SWITCH với N cases → N+1 branches (including default)  ║
║                                                               ║
║  ✅ LỢI ÍCH:                                                  ║
║     • Stronger than Statement Coverage                       ║
║     • Find logic errors                                      ║
║     • Test decision-making thoroughly                        ║
║                                                               ║
║  📊 QUAN HỆ:                                                  ║
║     100% Branch Coverage → 100% Statement Coverage           ║
║     (nhưng ngược lại KHÔNG đúng)                             ║
║                                                               ║
╚═══════════════════════════════════════════════════════════════╝
```

### 4.2. Ví Dụ Branch Coverage

**Code:**
```javascript
function validateAge(age) {
    let valid = false;       // S1

    if (age >= 18) {         // Decision 1
        valid = true;        // S2
    }

    return valid;            // S3
}
```

**Decision 1 có 2 branches**:
- Branch 1: `age >= 18` is **True**
- Branch 2: `age >= 18` is **False**

**Total branches**: 2

**Test Case 1**: `age = 20`
- **Path**: S1 → D1(True) → S2 → S3
- **Branches covered**: Branch 1 (True)
- **Branch Coverage**: 1/2 = **50%**

**Test Case 2**: `age = 15`
- **Path**: S1 → D1(False) → S3
- **Branches covered**: Branch 2 (False)
- **Branch Coverage**: 1/2 = **50%**

**Test Suite (TC1 + TC2)**:
- **Branches covered**: Both branches (True and False)
- **Branch Coverage**: 2/2 = **100%**

---

## 5. STATEMENT VS BRANCH COVERAGE

### 5.1. So Sánh

```
╔═══════════════════════════════════════════════════════════════╗
║          STATEMENT COVERAGE vs BRANCH COVERAGE                ║
╠═══════════════════════════════════════════════════════════════╣
║                                                               ║
║  Code:                                                        ║
║  ┌────────────────────────────────────────────┐              ║
║  │  function check(x, y) {                    │              ║
║  │      if (x > 0 && y > 0) {    // Decision │              ║
║  │          return "Both positive";           │              ║
║  │      }                                     │              ║
║  │      return "Not both positive";          │              ║
║  │  }                                         │              ║
║  └────────────────────────────────────────────┘              ║
║                                                               ║
║  Decision có 2 branches: True, False                         ║
║  Nhưng condition "x>0 && y>0" có 4 outcomes:                ║
║    1. x>0=T, y>0=T → Overall=T                              ║
║    2. x>0=T, y>0=F → Overall=F                              ║
║    3. x>0=F, y>0=T → Overall=F                              ║
║    4. x>0=F, y>0=F → Overall=F                              ║
║                                                               ║
║  TEST CASE: check(1, 1)                                      ║
║  → Statement Coverage: 100% (all statements executed)        ║
║  → Branch Coverage: 50% (only True branch)                   ║
║                                                               ║
║  THÊM TEST CASE: check(0, 0)                                 ║
║  → Branch Coverage: 100% (both branches)                     ║
║                                                               ║
╚═══════════════════════════════════════════════════════════════╝
```

### 5.2. Branch Coverage Mạnh Hơn

| Metric | Statement Coverage | Branch Coverage |
|--------|-------------------|-----------------|
| **Strength** | Weak | Stronger |
| **What it tests** | Statements executed | Decision outcomes |
| **Subsumes** | - | Statement Coverage |
| **Typical target** | 80-90% | 70-85% |
| **100% guarantees** | All code runs | All decisions tested |

**Key Point**:
- **100% Branch Coverage** → **100% Statement Coverage** (always true)
- **100% Statement Coverage** → Branch Coverage có thể <100% (not guaranteed)

---

## 6. VÍ DỤ TỔNG HỢP: DISCOUNT CALCULATOR

### 6.1. Code

```python
def calculate_discount(amount, is_member, has_coupon):
    """
    Tính discount cho đơn hàng Shopee
    - Member: +5% discount
    - Coupon: +10% discount
    - Amount > 500K: +5% additional
    """
    discount = 0                          # S1

    if is_member:                         # D1
        discount += 5                     # S2

    if has_coupon:                        # D2
        discount += 10                    # S3

    if amount > 500000:                   # D3
        discount += 5                     # S4

    if discount > 20:                     # D4
        discount = 20  # Max 20%         # S5

    return discount                       # S6
```

### 6.2. Control Flow Graph

```
      Start
        │
      ┌─▼─┐
      │S1 │ discount = 0
      └─┬─┘
        │
      ┌─▼─────┐
      │  D1   │ is_member?
      └┬────┬─┘
     T │    │ F
    ┌──▼─┐  │
    │ S2 │  │
    └──┬─┘  │
       └──┬─┘
          │
      ┌───▼────┐
      │  D2    │ has_coupon?
      └┬─────┬─┘
     T │     │ F
    ┌──▼─┐   │
    │ S3 │   │
    └──┬─┘   │
       └──┬──┘
          │
      ┌───▼────┐
      │  D3    │ amount>500K?
      └┬─────┬─┘
     T │     │ F
    ┌──▼─┐   │
    │ S4 │   │
    └──┬─┘   │
       └──┬──┘
          │
      ┌───▼────┐
      │  D4    │ discount>20?
      └┬─────┬─┘
     T │     │ F
    ┌──▼─┐   │
    │ S5 │   │
    └──┬─┘   │
       └──┬──┘
          │
      ┌───▼──┐
      │  S6  │ return
      └──────┘
```

### 6.3. Statement Coverage Analysis

**Total statements**: 6 (S1, S2, S3, S4, S5, S6)

**Test Case 1**: `amount=600000, is_member=True, has_coupon=True`
- **Path**: S1 → D1(T) → S2 → D2(T) → S3 → D3(T) → S4 → D4(T) → S5 → S6
- **Statements executed**: S1, S2, S3, S4, S5, S6
- **Statement Coverage**: 6/6 = **100%** ✅

Chỉ cần **1 test case** để đạt 100% Statement Coverage!

### 6.4. Branch Coverage Analysis

**Total decisions**: 4 (D1, D2, D3, D4)
**Total branches**: 4 × 2 = **8 branches**

**Test Case 1**: `amount=600000, is_member=True, has_coupon=True`
- **Branches**: D1(T), D2(T), D3(T), D4(T)
- **Branch Coverage**: 4/8 = **50%**

**Test Case 2**: `amount=100000, is_member=False, has_coupon=False`
- **Branches**: D1(F), D2(F), D3(F), D4(F)
- **Branch Coverage**: 4/8 = **50%**

**Test Suite (TC1 + TC2)**:
- **All branches covered**: D1(T/F), D2(T/F), D3(T/F), D4(T/F)
- **Branch Coverage**: 8/8 = **100%** ✅

Cần **tối thiểu 2 test cases** để đạt 100% Branch Coverage.

---

## 7. VALUE CỦA WHITE-BOX TESTING

```
╔═══════════════════════════════════════════════════════════════╗
║            VALUE CỦA WHITE-BOX TESTING                        ║
╠═══════════════════════════════════════════════════════════════╣
║                                                               ║
║  ✅ FIND CODE-LEVEL DEFECTS                                   ║
║     → Logic errors, wrong conditions                         ║
║     → Off-by-one errors trong loops                          ║
║                                                               ║
║  ✅ DETECT DEAD CODE                                          ║
║     → Unreachable statements                                 ║
║     → Never-executed paths                                   ║
║                                                               ║
║  ✅ IMPROVE CODE QUALITY                                      ║
║     → Identify complex code (high cyclomatic complexity)     ║
║     → Encourage refactoring                                  ║
║                                                               ║
║  ✅ COMPLEMENT BLACK-BOX                                      ║
║     → Black-box: Test requirements                           ║
║     → White-box: Test implementation                         ║
║     → Together: Comprehensive coverage                       ║
║                                                               ║
║  ✅ USEFUL FOR UNIT TESTING                                   ║
║     → Developers test own code thoroughly                    ║
║     → TDD cycle (write test → code → refactor)              ║
║                                                               ║
║  ✅ OBJECTIVE MEASUREMENT                                     ║
║     → Coverage % is quantifiable                             ║
║     → Easy to track progress                                 ║
║     → Can set coverage goals (e.g., >80%)                   ║
║                                                               ║
║  ⚠️ LIMITATIONS:                                              ║
║     → 100% coverage ≠ Bug-free code                         ║
║     → Không test requirements correctness                    ║
║     → Cần technical skills                                   ║
║                                                               ║
╚═══════════════════════════════════════════════════════════════╝
```

---

## 8. THỰC HÀNH: CALCULATE BMI

### Bài Tập

**Code:**
```javascript
function calculateBMI(weight, height) {
    if (weight <= 0 || height <= 0) {           // D1
        return "Invalid input";                 // S1
    }

    let bmi = weight / (height * height);       // S2
    let category;                                // S3

    if (bmi < 18.5) {                           // D2
        category = "Underweight";               // S4
    } else if (bmi < 25) {                      // D3
        category = "Normal";                    // S5
    } else if (bmi < 30) {                      // D4
        category = "Overweight";                // S6
    } else {
        category = "Obese";                     // S7
    }

    return category;                             // S8
}
```

**Câu hỏi**:
1. Vẽ Control Flow Graph
2. Có bao nhiêu statements?
3. Có bao nhiêu decisions và branches?
4. Thiết kế test cases để đạt 100% Statement Coverage
5. Thiết kế test cases để đạt 100% Branch Coverage

<details>
<summary>Đáp án</summary>

**1. CFG**: (Tự vẽ theo mẫu các ví dụ trên)

**2. Statements**: 8 (S1 đến S8)

**3. Decisions và Branches**:
- **Decisions**: 4 (D1, D2, D3, D4)
- **Branches**: 8
  - D1: True, False
  - D2: True, False
  - D3: True (18.5≤BMI<25), False (BMI≥25)
  - D4: True (25≤BMI<30), False (BMI≥30)

**4. Test Cases cho 100% Statement Coverage** (minimum 2):

| TC | weight | height | Path | Statements |
|----|--------|--------|------|------------|
| 1 | 0 | 1.7 | D1(T) → S1 | S1 |
| 2 | 70 | 1.75 | D1(F) → S2,S3 → D2(F) → D3(T) → S5 → S8 | S2,S3,S5,S8 |

Coverage: 5/8 = 62.5% (missing S4, S6, S7)

**Cần thêm**:
| TC | weight | height | BMI | Statements |
|----|--------|--------|-----|------------|
| 3 | 50 | 1.75 | 16.3 | S4 (Underweight) |
| 4 | 85 | 1.75 | 27.8 | S6 (Overweight) |
| 5 | 95 | 1.75 | 31.0 | S7 (Obese) |

**5 TCs → 100% Statement Coverage**

**5. Test Cases cho 100% Branch Coverage** (minimum 5):

| TC | weight | height | BMI | D1 | D2 | D3 | D4 | Category |
|----|--------|--------|-----|----|----|----|----|----------|
| 1 | 0 | 1.7 | - | T | - | - | - | Invalid |
| 2 | 70 | 1.75 | 22.9 | F | F | T | - | Normal |
| 3 | 50 | 1.75 | 16.3 | F | T | - | - | Underweight |
| 4 | 85 | 1.75 | 27.8 | F | F | F | T | Overweight |
| 5 | 95 | 1.75 | 31.0 | F | F | F | F | Obese |

**All 8 branches covered → 100%**

</details>

---

## 9. CÔNG CỤ ĐO COVERAGE

### 9.1. Các Công Cụ Phổ Biến

| Language | Tools |
|----------|-------|
| **JavaScript/TypeScript** | Istanbul (nyc), Jest coverage, Codecov |
| **Python** | Coverage.py, pytest-cov |
| **Java** | JaCoCo, Cobertura, Emma |
| **C#** | OpenCover, dotCover, Coverlet |
| **PHP** | PHPUnit Coverage, Xdebug |
| **Ruby** | SimpleCov |
| **Go** | go test -cover |

### 9.2. Ví Dụ: Jest Coverage Report

```bash
$ jest --coverage

----------------|---------|----------|---------|---------|
File            | % Stmts | % Branch | % Funcs | % Lines |
----------------|---------|----------|---------|---------|
discount.js     |   85.71 |    66.67 |     100 |   85.71 |
validate.js     |     100 |      100 |     100 |     100 |
----------------|---------|----------|---------|---------|
All files       |   92.86 |    83.33 |     100 |   92.86 |
----------------|---------|----------|---------|---------|
```

**Interpretation**:
- Statement Coverage: 92.86% (rất tốt)
- Branch Coverage: 83.33% (tốt, nhưng cần improve)
- Function Coverage: 100% (xuất sắc)

---

## 10. BEST PRACTICES

```
╔═══════════════════════════════════════════════════════════════╗
║                     BEST PRACTICES                            ║
╠═══════════════════════════════════════════════════════════════╣
║                                                               ║
║  ✅ SET REALISTIC TARGETS                                     ║
║     → 80-90% statement coverage là reasonable                ║
║     → 100% often not practical (exception handlers, etc.)    ║
║                                                               ║
║  ✅ PRIORITIZE BRANCH COVERAGE                                ║
║     → Branch > Statement coverage                            ║
║     → Focus on decision logic                                ║
║                                                               ║
║  ✅ COMBINE WITH BLACK-BOX                                    ║
║     → White-box for implementation                           ║
║     → Black-box for requirements                             ║
║                                                               ║
║  ✅ USE IN UNIT TESTING                                       ║
║     → Developers write unit tests                            ║
║     → Measure coverage locally                               ║
║                                                               ║
║  ✅ INTEGRATE WITH CI/CD                                      ║
║     → Automated coverage reports                             ║
║     → Block merge if coverage drops                          ║
║                                                               ║
║  ✅ DON'T CHASE 100% BLINDLY                                  ║
║     → Focus on critical paths                                ║
║     → Some code hard to test (UI, third-party libs)         ║
║                                                               ║
║  ⚠️ COVERAGE ≠ QUALITY                                        ║
║     → High coverage doesn't mean no bugs                     ║
║     → Need good assertions trong tests                       ║
║                                                               ║
╚═══════════════════════════════════════════════════════════════╝
```

---

## 11. CÂU HỎI ÔN TẬP

### Câu 1 (K2)
White-box testing dựa vào gì?

A. Specifications
B. User requirements
C. Internal code structure
D. User experience

<details>
<summary>Đáp án</summary>

**C. Internal code structure**

Giải thích: White-box = structure-based testing, cần access và hiểu code.
</details>

---

### Câu 2 (K3)
Code có 10 statements. Test suite execute 8 statements. Statement coverage?

A. 20%
B. 80%
C. 90%
D. 100%

<details>
<summary>Đáp án</summary>

**B. 80%**

8/10 × 100% = 80%
</details>

---

### Câu 3 (K3)
Decision có 3 branches. Test suite cover 2 branches. Branch coverage?

A. 33%
B. 50%
C. 66.67%
D. 100%

<details>
<summary>Đáp án</summary>

**C. 66.67%**

2/3 × 100% = 66.67%
</details>

---

### Câu 4 (K2)
Statement về branch coverage nào ĐÚNG?

A. Statement coverage stronger than Branch coverage
B. 100% Branch coverage guarantees 100% Statement coverage
C. Branch coverage và Statement coverage bằng nhau
D. Coverage metrics không liên quan

<details>
<summary>Đáp án</summary>

**B. 100% Branch coverage guarantees 100% Statement coverage**

Giải thích: Branch coverage subsumes (bao gồm) Statement coverage. Nếu test all branches, tất cả statements sẽ được executed.
</details>

---

### Câu 5 (K3)
Code:
```
if (x > 0 && y > 0) {
    print("Both positive");
}
print("Done");
```

Test case: x=1, y=1. Statement coverage?

A. 50%
B. 66%
C. 100%
D. 75%

<details>
<summary>Đáp án</summary>

**C. 100%**

Cả 2 statements đều executed (print "Both positive" và print "Done").
</details>

---

### Câu 6 (K2)
Value chính của white-box testing là gì?

A. Test user requirements
B. Find logic errors trong code
C. Test UI/UX
D. Replace black-box testing

<details>
<summary>Đáp án</summary>

**B. Find logic errors trong code**

White-box focuses on internal logic, paths, conditions.
</details>

---

## 12. CHECKLIST TỰ ĐÁNH GIÁ

### Kiến Thức
- [ ] Hiểu white-box testing là gì
- [ ] Phân biệt black-box vs white-box
- [ ] Hiểu Control Flow Graph
- [ ] Biết vẽ CFG từ code đơn giản

### Statement Coverage
- [ ] Tính được Statement Coverage từ test cases
- [ ] Thiết kế test cases để improve Statement Coverage
- [ ] Biết identify dead code từ coverage report

### Branch Coverage
- [ ] Đếm được số branches trong code
- [ ] Tính được Branch Coverage
- [ ] Thiết kế test cases để đạt target Branch Coverage
- [ ] Hiểu Branch Coverage > Statement Coverage

### Thực Hành
- [ ] Viết được test cases từ CFG
- [ ] Analyze coverage report
- [ ] Biết sử dụng coverage tools (Jest, Coverage.py, etc.)

---

## TỔNG KẾT

```
╔═══════════════════════════════════════════════════════════════╗
║                    KEY TAKEAWAYS                              ║
╠═══════════════════════════════════════════════════════════════╣
║                                                               ║
║  1. White-box testing = Structure-based testing              ║
║     → Focus on internal code logic                           ║
║                                                               ║
║  2. Statement Coverage = % statements executed               ║
║     → Weakest criterion                                      ║
║                                                               ║
║  3. Branch Coverage = % decision outcomes tested             ║
║     → Stronger than Statement Coverage                       ║
║     → 100% Branch → 100% Statement (always)                  ║
║                                                               ║
║  4. Realistic targets:                                       ║
║     → Statement: 80-90%                                      ║
║     → Branch: 70-85%                                         ║
║                                                               ║
║  5. Value: Find logic errors, dead code, improve quality    ║
║                                                               ║
║  6. Best used in Unit Testing by Developers                 ║
║                                                               ║
║  7. Complement with Black-box techniques                     ║
║                                                               ║
╚═══════════════════════════════════════════════════════════════╝
```

---

**Tiếp theo**: [Module 5.2: Experience-Based Techniques](./module-5.2-experience-based-techniques.md)

---

**Version**: 1.0.0
**Last Updated**: November 2025
