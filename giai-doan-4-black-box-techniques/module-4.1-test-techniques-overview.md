# MODULE 4.1: TEST TECHNIQUES OVERVIEW

**Thời lượng**: 1-1.5 giờ | **Độ khó**: ⭐

---

## MỤC TIÊU HỌC TẬP

Sau khi hoàn thành module này, bạn sẽ:

| ID | Mục tiêu | Level |
|----|----------|-------|
| FL-4.1.1 | Phân biệt các loại test techniques | K2 |

---

## 1. TẠI SAO CẦN TEST TECHNIQUES?

### 1.1. Vấn Đề: Không Thể Test Tất Cả

```
╔═══════════════════════════════════════════════════════════════╗
║           VẤN ĐỀ: EXHAUSTIVE TESTING IS IMPOSSIBLE            ║
╠═══════════════════════════════════════════════════════════════╣
║                                                               ║
║  VÍ DỤ: Test Age field (18-65)                               ║
║                                                               ║
║  Nếu test TẤT CẢ giá trị:                                    ║
║  • 18, 19, 20, 21, ... 65 = 48 test cases (chỉ valid)        ║
║  • + Invalid: 0, 1, 2, ... 17, 66, 67, ... 150              ║
║  • + Negative: -1, -2, -100...                               ║
║  • + Decimal: 18.5, 19.3...                                  ║
║  • + Characters: "abc", "!@#"...                             ║
║  • = Hàng NGHÌN test cases cho 1 field!                      ║
║                                                               ║
║  → KHÔNG FEASIBLE về thời gian và chi phí                    ║
║                                                               ║
║  GIẢI PHÁP: Sử dụng TEST TECHNIQUES                          ║
║  → Chọn test cases THÔNG MINH                                ║
║  → Coverage tốt với số lượng tests ít                        ║
║                                                               ║
╚═══════════════════════════════════════════════════════════════╝
```

### 1.2. Test Techniques Giúp Gì?

```
╔═══════════════════════════════════════════════════════════════╗
║              LỢI ÍCH CỦA TEST TECHNIQUES                      ║
╠═══════════════════════════════════════════════════════════════╣
║                                                               ║
║  ✅ SYSTEMATIC APPROACH                                       ║
║     → Có phương pháp rõ ràng thay vì random testing         ║
║                                                               ║
║  ✅ BETTER COVERAGE                                           ║
║     → Cover các scenarios quan trọng                         ║
║                                                               ║
║  ✅ FEWER TEST CASES                                          ║
║     → Giảm số lượng tests mà vẫn đảm bảo quality            ║
║                                                               ║
║  ✅ FIND MORE BUGS                                            ║
║     → Focus vào areas có khả năng có bugs cao               ║
║                                                               ║
║  ✅ REPRODUCIBLE                                              ║
║     → Ai cũng có thể apply techniques                       ║
║                                                               ║
║  ✅ MEASURABLE                                                ║
║     → Có thể đo coverage %                                   ║
║                                                               ║
╚═══════════════════════════════════════════════════════════════╝
```

---

## 2. BA LOẠI TEST TECHNIQUES

### 2.1. Tổng Quan

```
╔═══════════════════════════════════════════════════════════════╗
║                    TEST TECHNIQUES                            ║
╠═══════════════════════════════════════════════════════════════╣
║                                                               ║
║                    ┌─────────────────┐                        ║
║                    │ TEST TECHNIQUES │                        ║
║                    └────────┬────────┘                        ║
║           ┌─────────────────┼─────────────────┐               ║
║           ▼                 ▼                 ▼               ║
║   ┌───────────────┐ ┌───────────────┐ ┌───────────────┐      ║
║   │   BLACK-BOX   │ │   WHITE-BOX   │ │  EXPERIENCE-  │      ║
║   │  TECHNIQUES   │ │  TECHNIQUES   │ │    BASED      │      ║
║   └───────────────┘ └───────────────┘ └───────────────┘      ║
║           │                 │                 │               ║
║   • EP              • Statement       • Error Guessing       ║
║   • BVA               Coverage        • Exploratory          ║
║   • Decision Table  • Branch            Testing              ║
║   • State             Coverage        • Checklist-based      ║
║     Transition                                                ║
║                                                               ║
╚═══════════════════════════════════════════════════════════════╝
```

### 2.2. Black-box Techniques

```
╔═══════════════════════════════════════════════════════════════╗
║                  BLACK-BOX TECHNIQUES                         ║
╠═══════════════════════════════════════════════════════════════╣
║                                                               ║
║  📋 ĐẶC ĐIỂM:                                                 ║
║     • Based on SPECIFICATIONS (requirements, user stories)   ║
║     • Không cần biết internal code                           ║
║     • Focus on INPUT → OUTPUT behavior                       ║
║     • Also called "specification-based techniques"           ║
║                                                               ║
║  🔧 CÁC KỸ THUẬT:                                             ║
║                                                               ║
║  1. EQUIVALENCE PARTITIONING (EP)                            ║
║     → Chia inputs thành partitions                           ║
║     → Test 1 value từ mỗi partition                          ║
║                                                               ║
║  2. BOUNDARY VALUE ANALYSIS (BVA)                            ║
║     → Test ở boundaries của partitions                       ║
║     → Bugs thường ở biên                                     ║
║                                                               ║
║  3. DECISION TABLE TESTING                                   ║
║     → Test combinations của conditions                       ║
║     → Systematic coverage của business rules                 ║
║                                                               ║
║  4. STATE TRANSITION TESTING                                  ║
║     → Test systems có states                                 ║
║     → Test transitions giữa states                           ║
║                                                               ║
╚═══════════════════════════════════════════════════════════════╝
```

### 2.3. White-box Techniques

```
╔═══════════════════════════════════════════════════════════════╗
║                  WHITE-BOX TECHNIQUES                         ║
╠═══════════════════════════════════════════════════════════════╣
║                                                               ║
║  📋 ĐẶC ĐIỂM:                                                 ║
║     • Based on CODE STRUCTURE                                ║
║     • Cần biết và hiểu internal code                        ║
║     • Focus on code paths và logic                          ║
║     • Also called "structure-based techniques"               ║
║                                                               ║
║  🔧 CÁC KỸ THUẬT:                                             ║
║                                                               ║
║  1. STATEMENT COVERAGE                                       ║
║     → Execute mỗi statement ít nhất 1 lần                   ║
║     → Coverage = (Executed statements / Total) × 100%        ║
║                                                               ║
║  2. BRANCH COVERAGE (Decision Coverage)                       ║
║     → Execute mỗi branch (true/false) ít nhất 1 lần        ║
║     → Coverage = (Executed branches / Total) × 100%          ║
║                                                               ║
║  (Note: Branch coverage mạnh hơn Statement coverage)        ║
║                                                               ║
╚═══════════════════════════════════════════════════════════════╝
```

### 2.4. Experience-based Techniques

```
╔═══════════════════════════════════════════════════════════════╗
║               EXPERIENCE-BASED TECHNIQUES                     ║
╠═══════════════════════════════════════════════════════════════╣
║                                                               ║
║  📋 ĐẶC ĐIỂM:                                                 ║
║     • Based on TESTER'S EXPERIENCE và KNOWLEDGE             ║
║     • Less formal, more creative                             ║
║     • Useful khi specs unclear hoặc time limited            ║
║     • Complement black-box và white-box                     ║
║                                                               ║
║  🔧 CÁC KỸ THUẬT:                                             ║
║                                                               ║
║  1. ERROR GUESSING                                           ║
║     → Đoán bugs dựa vào experience                          ║
║     → Focus on common mistakes                               ║
║     → Example: Division by zero, null inputs, boundaries    ║
║                                                               ║
║  2. EXPLORATORY TESTING                                       ║
║     → Simultaneous learning, design, execution               ║
║     → Session-based                                          ║
║     → Creative, investigate as you go                        ║
║                                                               ║
║  3. CHECKLIST-BASED TESTING                                   ║
║     → Use checklists from experience                         ║
║     → Consistent coverage của common issues                  ║
║                                                               ║
╚═══════════════════════════════════════════════════════════════╝
```

---

## 3. SO SÁNH BA LOẠI TECHNIQUES

| Aspect | Black-box | White-box | Experience-based |
|--------|-----------|-----------|------------------|
| **Basis** | Specifications | Code structure | Tester knowledge |
| **Code access** | Không cần | Cần | Không cần |
| **Tester** | Testers | Developers | Senior testers |
| **Formal** | Formal | Formal | Less formal |
| **Coverage** | Functional | Structural | Ad hoc |
| **When to use** | Any level | Component level | Any level |

---

## 4. KHI NÀO DÙNG TECHNIQUE NÀO?

```
╔═══════════════════════════════════════════════════════════════╗
║              KHI NÀO DÙNG TECHNIQUE NÀO?                      ║
╠═══════════════════════════════════════════════════════════════╣
║                                                               ║
║  🎯 EQUIVALENCE PARTITIONING:                                 ║
║     → Input fields với ranges (age: 18-65)                   ║
║     → Multiple categories (payment: card/bank/wallet)        ║
║     → Reduce test cases cho large input domains             ║
║                                                               ║
║  🎯 BOUNDARY VALUE ANALYSIS:                                  ║
║     → Numeric inputs với min/max                             ║
║     → String lengths với limits                              ║
║     → Date ranges                                            ║
║     → Usually combine với EP                                 ║
║                                                               ║
║  🎯 DECISION TABLE:                                           ║
║     → Multiple conditions affect outcome                     ║
║     → Complex business rules                                 ║
║     → If-then-else logic                                     ║
║     → Example: Discount = f(member, amount, promo)          ║
║                                                               ║
║  🎯 STATE TRANSITION:                                         ║
║     → System có distinct states                             ║
║     → Events trigger state changes                          ║
║     → Example: Order status, ATM, Login attempts            ║
║                                                               ║
║  🎯 STATEMENT/BRANCH COVERAGE:                                ║
║     → Unit testing by developers                             ║
║     → Code quality measurement                               ║
║     → Find unreachable code                                  ║
║                                                               ║
║  🎯 ERROR GUESSING:                                           ║
║     → After formal testing, find more bugs                  ║
║     → Common pitfalls (null, empty, special chars)          ║
║                                                               ║
║  🎯 EXPLORATORY TESTING:                                      ║
║     → Learn new system quickly                              ║
║     → Time-boxed testing                                     ║
║     → Creative bug finding                                   ║
║                                                               ║
╚═══════════════════════════════════════════════════════════════╝
```

---

## 5. COVERAGE (ĐỘ BAO PHỦ)

### 5.1. Coverage Là Gì?

> **Coverage** đo lường mức độ một test suite bao phủ được test basis hoặc code.

```
                    Items tested
Coverage (%) = ───────────────────── × 100%
                    Total items

Example:
- 8 partitions defined, 6 tested → 75% EP coverage
- 10 statements, 8 executed → 80% statement coverage
- 4 branches, 4 executed → 100% branch coverage
```

### 5.2. Coverage Types

| Technique | Coverage Measurement |
|-----------|---------------------|
| Equivalence Partitioning | % partitions tested |
| Boundary Value Analysis | % boundary values tested |
| Decision Table | % rules tested |
| State Transition | % states/transitions tested |
| Statement Coverage | % statements executed |
| Branch Coverage | % branches executed |

---

## 6. BEST PRACTICES

```
╔═══════════════════════════════════════════════════════════════╗
║                     BEST PRACTICES                            ║
╠═══════════════════════════════════════════════════════════════╣
║                                                               ║
║  ✅ COMBINE MULTIPLE TECHNIQUES                               ║
║     → EP + BVA cho input validation                          ║
║     → Decision Table cho business rules                      ║
║     → Exploratory sau formal testing                        ║
║                                                               ║
║  ✅ START WITH BLACK-BOX                                      ║
║     → Requirements-based testing trước                       ║
║     → Không cần biết implementation                         ║
║                                                               ║
║  ✅ USE WHITE-BOX FOR UNIT TESTING                           ║
║     → Measure code coverage                                  ║
║     → Find dead code, missing paths                         ║
║                                                               ║
║  ✅ ADD EXPERIENCE-BASED                                      ║
║     → After formal techniques                                ║
║     → Find edge cases và unexpected bugs                    ║
║                                                               ║
║  ✅ DOCUMENT YOUR APPROACH                                    ║
║     → Which techniques used                                  ║
║     → What coverage achieved                                 ║
║     → Rationale for choices                                  ║
║                                                               ║
╚═══════════════════════════════════════════════════════════════╝
```

---

## 7. CÂU HỎI ÔN TẬP

### Câu 1 (K2)
Tại sao cần sử dụng test techniques?

A. Vì exhaustive testing is possible
B. Để systematic chọn test cases với good coverage
C. Vì không có requirements
D. Để replace automated testing

<details>
<summary>Đáp án</summary>

**B. Để systematic chọn test cases với good coverage**

Giải thích: Test techniques giúp chọn test cases thông minh, đạt coverage tốt với số lượng tests ít.
</details>

---

### Câu 2 (K2)
Black-box techniques dựa trên gì?

A. Source code
B. Specifications và requirements
C. Tester experience only
D. Database schema

<details>
<summary>Đáp án</summary>

**B. Specifications và requirements**

Giải thích: Black-box = specification-based, dựa vào requirements/user stories.
</details>

---

### Câu 3 (K1)
Technique nào thuộc nhóm Experience-based?

A. Equivalence Partitioning
B. Branch Coverage
C. Exploratory Testing
D. Decision Table

<details>
<summary>Đáp án</summary>

**C. Exploratory Testing**

Giải thích: Exploratory Testing dựa vào kinh nghiệm của tester, không formal.
</details>

---

## 8. PREVIEW CÁC MODULES TIẾP THEO

```
GIAI ĐOẠN 4: BLACK-BOX TECHNIQUES

Module 4.2: Equivalence Partitioning (EP)
         → Chia inputs thành partitions
         → Test 1 value từ mỗi partition
         → ⭐⭐⭐ Quan trọng - ~15% exam

Module 4.3: Boundary Value Analysis (BVA)
         → Test ở boundaries
         → 2-value và 3-value BVA
         → ⭐⭐⭐ Quan trọng - ~15% exam

Module 4.4: Decision Table Testing
         → Test combinations of conditions
         → Systematic business rule testing
         → ⭐⭐⭐ Quan trọng - ~10% exam

Module 4.5: State Transition Testing
         → Test systems với states
         → State diagrams và state tables
         → ⭐⭐ Important - ~5% exam
```

---

**Tiếp theo**: [Module 4.2: Equivalence Partitioning](./module-4.2-equivalence-partitioning.md)

---

**Version**: 1.0.0
**Last Updated**: November 2025
