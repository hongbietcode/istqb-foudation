# BÀI TẬP GIAI ĐOẠN 4: BLACK-BOX TECHNIQUES

**Thời lượng**: 4-6 giờ | **Độ quan trọng**: ⭐⭐⭐⭐⭐ (~40% đề thi)

---

## MỤC TIÊU

- Thực hành áp dụng 4 kỹ thuật Black-box
- Tính toán test cases và coverage
- Chuẩn bị cho các câu hỏi tính toán trong đề thi ISTQB

---

## PHẦN A: BÀI TẬP THỰC HÀNH

---

### BÀI TẬP 1: Equivalence Partitioning - Hệ Thống Đặt Phòng Khách Sạn

**Yêu cầu**: Hệ thống đặt phòng khách sạn có các rules:
- Số đêm: 1-30 đêm
- Số khách: 1-4 người/phòng
- Phương thức thanh toán: Credit Card, Debit Card, Bank Transfer
- Mã giảm giá: 6 ký tự alphanumeric (optional)

**Câu hỏi**:
1. Xác định tất cả equivalence partitions (valid và invalid)
2. Tính số test cases tối thiểu để đạt 100% EP coverage
3. Thiết kế test cases

<details>
<summary>Đáp án</summary>

**1. Equivalence Partitions:**

| Input | Valid Partitions | Invalid Partitions |
|-------|------------------|-------------------|
| Số đêm | VP1: 1-30 | IP1: < 1 (0, negative) |
|       |          | IP2: > 30 |
| Số khách | VP2: 1-4 | IP3: < 1 |
|         |          | IP4: > 4 |
| Thanh toán | VP3: Credit Card | |
|           | VP4: Debit Card | |
|           | VP5: Bank Transfer | IP5: Invalid method |
| Mã giảm giá | VP6: Valid (6 chars alphanumeric) | IP6: Invalid format |
|            | VP7: Empty (không nhập) | |

**2. Số test cases tối thiểu:**
- Valid: 7 partitions → ít nhất 1 test case cover được nhiều VPs
- Invalid: 6 partitions → 6 test cases (mỗi cái 1)
- **Minimum**: 7 test cases (nếu kết hợp thông minh)

**3. Test Cases:**

| TC | Số đêm | Số khách | Thanh toán | Mã giảm giá | Expected |
|----|--------|----------|------------|-------------|----------|
| 1 | 5 (VP1) | 2 (VP2) | Credit (VP3) | ABC123 (VP6) | Valid |
| 2 | 10 | 3 | Debit (VP4) | (empty) (VP7) | Valid |
| 3 | 15 | 1 | Bank (VP5) | DEF456 | Valid |
| 4 | 0 (IP1) | 2 | Credit | | Invalid |
| 5 | 31 (IP2) | 2 | Credit | | Invalid |
| 6 | 5 | 0 (IP3) | Credit | | Invalid |
| 7 | 5 | 5 (IP4) | Credit | | Invalid |
| 8 | 5 | 2 | Cash (IP5) | | Invalid |
| 9 | 5 | 2 | Credit | AB1 (IP6) | Invalid |

</details>

---

### BÀI TẬP 2: Boundary Value Analysis - Hệ Thống Tính Lương

**Yêu cầu**: Công ty tính bonus theo số năm làm việc:
- 0-2 năm: Không bonus
- 3-5 năm: Bonus 10%
- 6-10 năm: Bonus 20%
- >10 năm: Bonus 30%

Số giờ làm thêm trong tháng: 0-50 giờ

**Câu hỏi**:
1. Áp dụng 2-value BVA, xác định boundary values cho số năm làm việc
2. Áp dụng 3-value BVA cho cùng input
3. Thiết kế test cases cho số giờ làm thêm (2-value BVA)

<details>
<summary>Đáp án</summary>

**1. 2-value BVA cho số năm làm việc:**

| Boundary | Values |
|----------|--------|
| 0-2 / 3-5 | 2, 3 |
| 3-5 / 6-10 | 5, 6 |
| 6-10 / >10 | 10, 11 |

**Boundary values**: 2, 3, 5, 6, 10, 11 = **6 values**

**2. 3-value BVA cho số năm làm việc:**

| Boundary | Values |
|----------|--------|
| 0-2 / 3-5 | 2, 3, 4 |
| 3-5 / 6-10 | 4, 5, 6, 7 |
| 6-10 / >10 | 9, 10, 11 |

**Boundary values** (unique): 2, 3, 4, 5, 6, 7, 9, 10, 11 = **9 values**

**3. Test Cases cho số giờ làm thêm (2-value BVA):**

| Boundary | Values | Test Cases |
|----------|--------|------------|
| Min edge | -1, 0 | TC1: -1 (invalid), TC2: 0 (valid) |
| Max edge | 50, 51 | TC3: 50 (valid), TC4: 51 (invalid) |

**4 test cases tổng cộng**

</details>

---

### BÀI TẬP 3: Decision Table - Hệ Thống Giảm Giá E-commerce

**Yêu cầu**: Shopee áp dụng giảm giá theo rules:
- Điều kiện 1: Khách VIP (Yes/No)
- Điều kiện 2: Đơn hàng > 500K (Yes/No)
- Điều kiện 3: Sử dụng voucher (Yes/No)

**Actions**:
- Giảm 5% cho VIP
- Giảm 10% cho đơn > 500K
- Giảm 15% khi dùng voucher
- Các giảm giá được cộng dồn

**Câu hỏi**:
1. Tạo decision table đầy đủ
2. Có bao nhiêu rules?
3. Tính % giảm giá cho mỗi rule

<details>
<summary>Đáp án</summary>

**1. Decision Table:**

| | R1 | R2 | R3 | R4 | R5 | R6 | R7 | R8 |
|---|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
| **CONDITIONS** |
| VIP? | N | N | N | N | Y | Y | Y | Y |
| Đơn > 500K? | N | N | Y | Y | N | N | Y | Y |
| Có voucher? | N | Y | N | Y | N | Y | N | Y |
| **ACTIONS** |
| Giảm 5% (VIP) | | | | | X | X | X | X |
| Giảm 10% (>500K) | | | X | X | | | X | X |
| Giảm 15% (voucher) | | X | | X | | X | | X |

**2. Số rules**: 2³ = **8 rules**

**3. % Giảm giá:**

| Rule | VIP | >500K | Voucher | Total Discount |
|------|-----|-------|---------|----------------|
| R1 | N | N | N | 0% |
| R2 | N | N | Y | 15% |
| R3 | N | Y | N | 10% |
| R4 | N | Y | Y | 25% |
| R5 | Y | N | N | 5% |
| R6 | Y | N | Y | 20% |
| R7 | Y | Y | N | 15% |
| R8 | Y | Y | Y | 30% |

</details>

---

### BÀI TẬP 4: Decision Table Nâng Cao - Hệ Thống Bảo Hiểm

**Yêu cầu**: Công ty bảo hiểm xét duyệt claim:
- Tuổi: <18, 18-60, >60
- Loại bệnh: Thông thường, Nghiêm trọng
- Thời gian tham gia: <1 năm, ≥1 năm

**Rules**:
- <18 tuổi: Cần người giám hộ ký
- >60 tuổi: Cần xét duyệt bổ sung
- Bệnh nghiêm trọng + <1 năm: Từ chối
- Các case khác: Approve

**Câu hỏi**:
1. Đây là Limited-entry hay Extended-entry decision table?
2. Tạo decision table
3. Có thể tối giản (collapse) rules nào?

<details>
<summary>Đáp án</summary>

**1. Extended-entry decision table** (vì Tuổi có 3 giá trị, không chỉ Y/N)

**2. Decision Table:**

| | R1 | R2 | R3 | R4 | R5 | R6 | R7 | R8 | R9 | R10 | R11 | R12 |
|---|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|:---:|
| **CONDITIONS** |
| Tuổi | <18 | <18 | <18 | <18 | 18-60 | 18-60 | 18-60 | 18-60 | >60 | >60 | >60 | >60 |
| Loại bệnh | TT | TT | NTr | NTr | TT | TT | NTr | NTr | TT | TT | NTr | NTr |
| Thời gian | <1y | ≥1y | <1y | ≥1y | <1y | ≥1y | <1y | ≥1y | <1y | ≥1y | <1y | ≥1y |
| **ACTIONS** |
| Cần giám hộ | X | X | X | X | | | | | | | | |
| Xét duyệt bổ sung | | | | | | | | | X | X | X | X |
| Từ chối | | | X | | | | X | | | | X | |
| Approve | X | X | | X | X | X | | X | X | X | | X |

*TT = Thông thường, NTr = Nghiêm trọng*

**3. Collapse rules:**
- R3, R7, R11 có thể gộp: Bệnh nghiêm trọng + <1 năm → Từ chối (bất kể tuổi)

</details>

---

### BÀI TẬP 5: State Transition - ATM Machine

**Yêu cầu**: ATM có các states:
- Idle (chờ thẻ)
- Card Inserted (đã đưa thẻ)
- PIN Entry (nhập PIN)
- Authenticated (xác thực OK)
- Transaction (đang giao dịch)
- Card Ejected (trả thẻ)

**Events**:
- Insert Card, Enter PIN (correct/wrong), Select Transaction, Complete, Cancel, Eject Card

**Rules**:
- Sai PIN 3 lần → Nuốt thẻ (Card Retained state)
- Cancel ở bất kỳ state nào → Card Ejected → Idle

**Câu hỏi**:
1. Vẽ State Transition Diagram
2. Tạo State Transition Table
3. Xác định số test cases để đạt "all states" coverage
4. Xác định số test cases để đạt "all transitions" coverage

<details>
<summary>Đáp án</summary>

**1. State Transition Diagram:**

```
                    ┌─────────────────────────────────────┐
                    │              [Cancel]               │
                    ▼                                     │
┌──────┐  Insert  ┌────────────┐  Enter PIN  ┌───────────┴─┐
│ IDLE │─────────►│   CARD     │────────────►│  PIN ENTRY  │
│      │          │  INSERTED  │             │             │
└──┬───┘          └─────┬──────┘             └──────┬──────┘
   │                    │                          │
   │  Eject             │ [Cancel]                 │ Correct PIN
   │                    ▼                          ▼
   │              ┌──────────────┐         ┌──────────────┐
   │              │ CARD EJECTED │◄────────│AUTHENTICATED │
   │              └──────────────┘ Cancel  └──────┬───────┘
   │                    │                         │
   │                    │                         │ Select Trans
   └────────────────────┘                         ▼
                                           ┌──────────────┐
                                           │ TRANSACTION  │
                                           └──────┬───────┘
                                                  │
                                                  │ Complete
                    ┌─────────────┐               │
   Wrong PIN x3     │    CARD     │◄──────────────┘
   ─────────────────►   RETAINED  │
                    └─────────────┘
```

**2. State Transition Table:**

| Current State | Event | Next State | Action |
|--------------|-------|------------|--------|
| Idle | Insert Card | Card Inserted | Display "Enter PIN" |
| Card Inserted | Enter PIN | PIN Entry | - |
| Card Inserted | Cancel | Card Ejected | Eject card |
| PIN Entry | Correct PIN | Authenticated | Display menu |
| PIN Entry | Wrong PIN (1-2) | PIN Entry | "Try again" |
| PIN Entry | Wrong PIN (3) | Card Retained | Retain card |
| PIN Entry | Cancel | Card Ejected | Eject card |
| Authenticated | Select Trans | Transaction | Process |
| Authenticated | Cancel | Card Ejected | Eject card |
| Transaction | Complete | Card Ejected | Eject card |
| Transaction | Cancel | Card Ejected | Eject card |
| Card Ejected | Eject Card | Idle | Ready |
| Card Retained | - | (End) | Contact bank |

**3. All States Coverage:**
States: Idle, Card Inserted, PIN Entry, Authenticated, Transaction, Card Ejected, Card Retained = **7 states**

Minimum test cases để visit all states:
- TC1: Idle → Card Inserted → PIN Entry → Authenticated → Transaction → Card Ejected → Idle (6 states)
- TC2: ... → PIN Entry → Wrong x3 → Card Retained (1 new state)

**Minimum: 2 test cases**

**4. All Transitions Coverage:**
Transitions: 13 (từ table trên)

Mỗi test case cover ~5-6 transitions
**Minimum: 3-4 test cases** để cover all transitions

</details>

---

### BÀI TẬP 6: State Transition - Đơn Hàng Online

**Yêu cầu**: Shopee order có các trạng thái:
- Pending → Confirmed → Processing → Shipped → Delivered
- Có thể Cancel từ Pending hoặc Confirmed
- Có thể Return từ Delivered (trong 7 ngày)

**Câu hỏi**:
1. Vẽ state diagram
2. Xác định valid và invalid transitions
3. Thiết kế test cases cho invalid transitions

<details>
<summary>Đáp án</summary>

**1. State Diagram:**

```
┌─────────┐  Confirm   ┌───────────┐  Process  ┌────────────┐
│ PENDING │───────────►│ CONFIRMED │──────────►│ PROCESSING │
└────┬────┘            └─────┬─────┘           └──────┬─────┘
     │                       │                        │
     │ Cancel                │ Cancel                 │ Ship
     │                       │                        │
     ▼                       ▼                        ▼
┌─────────┐            ┌───────────┐            ┌─────────┐
│CANCELLED│◄───────────│ CANCELLED │            │ SHIPPED │
└─────────┘            └───────────┘            └────┬────┘
                                                     │
                                                     │ Deliver
     ┌──────────────────────────────────────────────┘
     │
     ▼
┌───────────┐  Return   ┌──────────┐
│ DELIVERED │──────────►│ RETURNED │
└───────────┘           └──────────┘
```

**2. Valid và Invalid Transitions:**

| From State | Valid Events | Invalid Events |
|------------|--------------|----------------|
| Pending | Confirm, Cancel | Ship, Deliver, Return |
| Confirmed | Process, Cancel | Ship, Deliver, Return |
| Processing | Ship | Cancel, Confirm, Deliver, Return |
| Shipped | Deliver | Cancel, Confirm, Process, Return |
| Delivered | Return | Cancel, Confirm, Process, Ship |
| Cancelled | (none) | All events |
| Returned | (none) | All events |

**3. Test Cases cho Invalid Transitions:**

| TC | Current State | Event | Expected Result |
|----|--------------|-------|-----------------|
| 1 | Pending | Ship | Error: Cannot ship pending order |
| 2 | Pending | Deliver | Error: Invalid action |
| 3 | Pending | Return | Error: Order not delivered |
| 4 | Processing | Cancel | Error: Order already processing |
| 5 | Shipped | Cancel | Error: Order already shipped |
| 6 | Delivered | Cancel | Error: Order completed |
| 7 | Cancelled | Confirm | Error: Order cancelled |
| 8 | Returned | Ship | Error: Order returned |

</details>

---

### BÀI TẬP 7: Kết Hợp EP + BVA - Form Đăng Ký

**Yêu cầu**: Form đăng ký Grab Driver:
- Tuổi: 21-55
- Kinh nghiệm lái xe: ≥2 năm
- Điểm bằng lái: 0-12 (bị trừ điểm = không đạt nếu >6)

**Câu hỏi**:
1. Áp dụng EP xác định partitions
2. Áp dụng 2-value BVA cho tuổi
3. Thiết kế bộ test cases kết hợp EP + BVA

<details>
<summary>Đáp án</summary>

**1. EP Partitions:**

| Input | Valid Partitions | Invalid Partitions |
|-------|------------------|-------------------|
| Tuổi | VP1: 21-55 | IP1: <21 |
|      |            | IP2: >55 |
| Kinh nghiệm | VP2: ≥2 năm | IP3: <2 năm |
| Điểm bằng lái | VP3: 0-6 (đạt) | IP4: 7-12 (không đạt) |
|              |                | IP5: >12 |
|              |                | IP6: <0 |

**2. 2-value BVA cho tuổi:**

| Boundary | Values |
|----------|--------|
| Min valid | 20, 21 |
| Max valid | 55, 56 |

**Boundary values**: 20, 21, 55, 56

**3. Test Cases (EP + BVA):**

| TC | Tuổi | Kinh nghiệm | Điểm | Expected |
|----|------|-------------|------|----------|
| 1 | 30 (VP1) | 3 (VP2) | 2 (VP3) | Pass |
| 2 | 20 (IP1-BVA) | 3 | 2 | Fail: Under age |
| 3 | 21 (BVA) | 3 | 2 | Pass |
| 4 | 55 (BVA) | 3 | 2 | Pass |
| 5 | 56 (IP2-BVA) | 3 | 2 | Fail: Over age |
| 6 | 30 | 1 (IP3) | 2 | Fail: Insufficient exp |
| 7 | 30 | 2 (BVA) | 2 | Pass |
| 8 | 30 | 3 | 7 (IP4) | Fail: Too many points |
| 9 | 30 | 3 | 6 (BVA) | Pass |
| 10 | 30 | 3 | 0 (BVA) | Pass |

</details>

---

### BÀI TẬP 8: Tổng Hợp - Hệ Thống Vay Tiền Online

**Scenario**: MoMo cung cấp dịch vụ vay tiền với rules:

**Inputs**:
- Số tiền vay: 1-50 triệu
- Kỳ hạn: 3, 6, 12 tháng
- Credit score: 300-850
- Thu nhập/tháng: ≥5 triệu

**Business Rules**:
- Credit score <500: Từ chối
- Credit score 500-650: Chỉ được vay tối đa 10 triệu
- Credit score 651-750: Được vay tối đa 30 triệu
- Credit score >750: Được vay full 50 triệu
- Thu nhập <5 triệu: Từ chối

**Câu hỏi**:
1. Áp dụng EP cho tất cả inputs
2. Áp dụng BVA cho Credit score
3. Tạo Decision Table cho việc approve/reject
4. Tính tổng số test cases cần thiết

<details>
<summary>Đáp án</summary>

**1. EP:**

| Input | Valid Partitions | Invalid Partitions |
|-------|------------------|-------------------|
| Số tiền | VP1: 1-10tr | IP1: <1tr |
|        | VP2: 11-30tr | IP2: >50tr |
|        | VP3: 31-50tr | |
| Kỳ hạn | VP4: 3 tháng | IP3: Khác |
|       | VP5: 6 tháng | |
|       | VP6: 12 tháng | |
| Credit | VP7: 500-650 | IP4: <300 |
|       | VP8: 651-750 | IP5: 300-499 |
|       | VP9: >750 | IP6: >850 |
| Thu nhập | VP10: ≥5tr | IP7: <5tr |

**2. BVA cho Credit Score:**

| Boundary | 2-value | 3-value |
|----------|---------|---------|
| 500 | 499, 500 | 499, 500, 501 |
| 650/651 | 650, 651 | 649, 650, 651, 652 |
| 750/751 | 750, 751 | 749, 750, 751, 752 |

**3. Decision Table (simplified):**

| | R1 | R2 | R3 | R4 | R5 |
|---|:---:|:---:|:---:|:---:|:---:|
| **CONDITIONS** |
| Credit Score | <500 | 500-650 | 500-650 | 651-750 | >750 |
| Số tiền | Any | ≤10tr | >10tr | ≤30tr | Any |
| Thu nhập ≥5tr | Any | Y | Y | Y | Y |
| **ACTIONS** |
| Reject | X | | X | | |
| Approve ≤10tr | | X | | | |
| Approve ≤30tr | | | | X | |
| Approve full | | | | | X |

**4. Tổng test cases:**
- EP: ~10 valid + 7 invalid = 17
- BVA: ~8 boundary values = 8
- Decision Table: ~5 rules = 5
- **Tổng: ~20-25 test cases** (loại bỏ overlap)

</details>

---

## PHẦN B: CÂU HỎI TRẮC NGHIỆM (50 CÂU)

### NHÓM 1: EQUIVALENCE PARTITIONING (15 câu)

**Câu 1** (K2)
Mục đích chính của Equivalence Partitioning là gì?

A. Test tất cả các giá trị có thể
B. Giảm số test cases trong khi vẫn đảm bảo coverage tốt
C. Chỉ test các giá trị invalid
D. Test các boundaries

<details>
<summary>Đáp án</summary>

**B. Giảm số test cases trong khi vẫn đảm bảo coverage tốt**

Giải thích: EP chia input domain thành partitions, chỉ cần test 1 value từ mỗi partition vì các values trong cùng partition được expected xử lý như nhau.
</details>

---

**Câu 2** (K3)
Input field "Discount code" chấp nhận: 5-10 ký tự alphanumeric. Có bao nhiêu equivalence partitions?

A. 2
B. 3
C. 4
D. 5

<details>
<summary>Đáp án</summary>

**B. 3**

- VP1: 5-10 ký tự alphanumeric (valid)
- IP1: <5 ký tự
- IP2: >10 ký tự

Có thể có thêm IP3: chứa special characters (tùy interpretation)
</details>

---

**Câu 3** (K3)
Age field accepts 18-65. Test value 45 thuộc partition nào?

A. Invalid partition
B. Boundary value
C. Valid partition
D. Out of range

<details>
<summary>Đáp án</summary>

**C. Valid partition**

Giải thích: 45 nằm trong range 18-65, thuộc valid partition. Nó không phải boundary (boundaries là 18, 65 hoặc 17, 18, 65, 66).
</details>

---

**Câu 4** (K3)
Shipping options: Standard, Express, Same-day. Có bao nhiêu valid partitions cho input này?

A. 1
B. 2
C. 3
D. 4

<details>
<summary>Đáp án</summary>

**C. 3**

Giải thích: Mỗi option là một valid partition:
- VP1: Standard
- VP2: Express
- VP3: Same-day

(Có thể có IP: invalid option)
</details>

---

**Câu 5** (K3)
Password field: 8-20 chars, must contain letter and number. Bao nhiêu test cases tối thiểu để cover tất cả equivalence partitions?

A. 2
B. 3
C. 4
D. 5

<details>
<summary>Đáp án</summary>

**C. 4**

Partitions:
- VP1: Valid (8-20, có letter và number)
- IP1: <8 chars
- IP2: >20 chars
- IP3: No letter
- IP4: No number

Minimum 4 test cases (1 cho VP1, có thể combine IP1+IP3, IP2+IP4, hoặc 1 cho mỗi IP).
</details>

---

**Câu 6** (K2)
Trong EP, tại sao chỉ cần test 1 value từ mỗi partition?

A. Để tiết kiệm thời gian
B. Vì các values trong partition được xử lý giống nhau
C. Vì boundaries không quan trọng
D. Vì invalid values không cần test

<details>
<summary>Đáp án</summary>

**B. Vì các values trong partition được xử lý giống nhau**

Giải thích: Assumption của EP là nếu 1 value trong partition works, tất cả values khác trong partition đó cũng works.
</details>

---

**Câu 7** (K3)
Temperature sensor: -40°C to 85°C. Có bao nhiêu equivalence partitions?

A. 1
B. 2
C. 3
D. 4

<details>
<summary>Đáp án</summary>

**C. 3**

- IP1: < -40°C
- VP1: -40°C to 85°C
- IP2: > 85°C
</details>

---

**Câu 8** (K2)
Output equivalence partitioning được sử dụng khi nào?

A. Khi input partitions không rõ ràng
B. Khi muốn verify output values
C. Khi cần derive test cases từ expected outputs
D. Khi testing boundaries

<details>
<summary>Đáp án</summary>

**C. Khi cần derive test cases từ expected outputs**

Giải thích: Output EP partition outputs thành groups và derive inputs để produce mỗi output partition.
</details>

---

**Câu 9** (K3)
Hệ thống có 4 valid partitions và 3 invalid partitions. Minimum test cases cho 100% EP coverage?

A. 3
B. 4
C. 7
D. 12

<details>
<summary>Đáp án</summary>

**C. 7**

Minimum = số partitions = 4 valid + 3 invalid = 7
(1 test case cho mỗi partition)
</details>

---

**Câu 10** (K3)
Có thể combine multiple valid partitions trong 1 test case được không?

A. Không, mỗi test case chỉ cover 1 partition
B. Có, để giảm số test cases
C. Chỉ với invalid partitions
D. Chỉ khi inputs độc lập

<details>
<summary>Đáp án</summary>

**B. Có, để giảm số test cases**

Giải thích: Một test case có thể cover nhiều valid partitions của các inputs khác nhau. Ví dụ: TC với age=25 (valid) và amount=100 (valid) cover 2 VPs.
</details>

---

**Câu 11** (K3)
Quantity field: accepts 1-100. Giá trị nào KHÔNG phải là representative value tốt cho valid partition?

A. 1
B. 50
C. 100
D. 101

<details>
<summary>Đáp án</summary>

**D. 101**

Giải thích: 101 > 100, thuộc invalid partition, không phải valid partition.
</details>

---

**Câu 12** (K2)
EP coverage được tính như thế nào?

A. Executed partitions / Total partitions × 100%
B. Executed tests / Total tests × 100%
C. Valid partitions / Total partitions × 100%
D. Passed tests / Total tests × 100%

<details>
<summary>Đáp án</summary>

**A. Executed partitions / Total partitions × 100%**
</details>

---

**Câu 13** (K3)
User type: Admin, Manager, Staff, Guest. Chỉ test "Admin" và "Staff". EP coverage là bao nhiêu?

A. 25%
B. 50%
C. 75%
D. 100%

<details>
<summary>Đáp án</summary>

**B. 50%**

2 partitions tested / 4 total partitions = 50%
</details>

---

**Câu 14** (K2)
Khi nào nên tách 1 partition thành nhiều partitions?

A. Khi partition quá lớn
B. Khi các values trong partition được xử lý khác nhau
C. Khi muốn nhiều test cases hơn
D. Khi testing performance

<details>
<summary>Đáp án</summary>

**B. Khi các values trong partition được xử lý khác nhau**

Giải thích: Nếu discover rằng system xử lý một số values trong partition khác với các values còn lại, cần tách thành partitions riêng.
</details>

---

**Câu 15** (K3)
Field accepts: A-Z, a-z, 0-9, và special chars (!@#). Bao nhiêu valid partitions cho character types?

A. 2
B. 3
C. 4
D. 5

<details>
<summary>Đáp án</summary>

**C. 4**

- VP1: Uppercase (A-Z)
- VP2: Lowercase (a-z)
- VP3: Digits (0-9)
- VP4: Special chars (!@#)

(Nếu tất cả được chấp nhận như nhau, có thể group thành ít hơn)
</details>

---

### NHÓM 2: BOUNDARY VALUE ANALYSIS (15 câu)

**Câu 16** (K2)
BVA dựa trên observation gì?

A. Users thường input boundaries
B. Defects cluster ở boundaries của partitions
C. Boundaries dễ test hơn
D. Boundaries có performance tốt hơn

<details>
<summary>Đáp án</summary>

**B. Defects cluster ở boundaries của partitions**

Giải thích: Experience cho thấy developers thường mắc lỗi ở boundary conditions (off-by-one errors, wrong comparisons như < vs <=).
</details>

---

**Câu 17** (K3)
Input range: 10-100. Áp dụng 2-value BVA, test values là gì?

A. 10, 100
B. 9, 10, 100, 101
C. 10, 11, 99, 100
D. 9, 10, 11, 99, 100, 101

<details>
<summary>Đáp án</summary>

**B. 9, 10, 100, 101**

2-value BVA: boundary và 1 neighbor bên ngoài
- Min boundary: 9 (invalid), 10 (valid)
- Max boundary: 100 (valid), 101 (invalid)
</details>

---

**Câu 18** (K3)
Input range: 10-100. Áp dụng 3-value BVA, có bao nhiêu test values?

A. 4
B. 6
C. 8
D. 10

<details>
<summary>Đáp án</summary>

**B. 6**

3-value BVA: boundary, 1 inside, 1 outside
- Min: 9, 10, 11
- Max: 99, 100, 101
= 6 values
</details>

---

**Câu 19** (K3)
Discount rate: 0%-50%. 2-value BVA values là gì?

A. 0, 50
B. -1, 0, 50, 51
C. 0, 1, 49, 50
D. -1, 0, 1, 49, 50, 51

<details>
<summary>Đáp án</summary>

**B. -1, 0, 50, 51**

2-value: boundary + immediate neighbor outside
- Min: -1 (invalid), 0 (valid)
- Max: 50 (valid), 51 (invalid)
</details>

---

**Câu 20** (K2)
2-value BVA và 3-value BVA khác nhau như thế nào?

A. 3-value test nhiều partitions hơn
B. 3-value thêm value bên trong partition
C. 3-value chỉ test invalid values
D. 2-value thorough hơn

<details>
<summary>Đáp án</summary>

**B. 3-value thêm value bên trong partition**

Giải thích:
- 2-value: boundary + 1 outside
- 3-value: boundary + 1 inside + 1 outside
</details>

---

**Câu 21** (K3)
String length: 5-20 characters. 2-value BVA cho length?

A. 4, 5, 20, 21
B. 5, 20
C. 4, 5, 6, 19, 20, 21
D. 1, 5, 20, 100

<details>
<summary>Đáp án</summary>

**A. 4, 5, 20, 21**

2-value BVA:
- Min: 4 (invalid), 5 (valid)
- Max: 20 (valid), 21 (invalid)
</details>

---

**Câu 22** (K3)
Age partitions: 0-17 (minor), 18-65 (adult), 66+ (senior). 2-value BVA cho tất cả boundaries?

A. 17, 18, 65, 66
B. 0, 17, 18, 65, 66
C. 16, 17, 18, 19, 64, 65, 66, 67
D. 17, 18, 19, 65, 66, 67

<details>
<summary>Đáp án</summary>

**A. 17, 18, 65, 66**

2-value cho mỗi internal boundary:
- 17/18 boundary: 17, 18
- 65/66 boundary: 65, 66
</details>

---

**Câu 23** (K2)
BVA thường được sử dụng kết hợp với technique nào?

A. Decision Table
B. State Transition
C. Equivalence Partitioning
D. Exploratory Testing

<details>
<summary>Đáp án</summary>

**C. Equivalence Partitioning**

Giải thích: EP xác định partitions, BVA focus vào boundaries của các partitions đó. Hai techniques complement nhau.
</details>

---

**Câu 24** (K3)
Order quantity: 1-999. Minimum test cases cho 2-value BVA?

A. 2
B. 4
C. 6
D. 8

<details>
<summary>Đáp án</summary>

**B. 4**

2-value BVA:
- 0 (invalid), 1 (valid) - min boundary
- 999 (valid), 1000 (invalid) - max boundary
= 4 test values = 4 test cases
</details>

---

**Câu 25** (K3)
Date field: 01/01/2020 - 31/12/2025. Boundary values cho year?

A. 2020, 2025
B. 2019, 2020, 2025, 2026
C. 2019, 2020, 2021, 2024, 2025, 2026
D. 2020, 2021, 2024, 2025

<details>
<summary>Đáp án</summary>

**B. 2019, 2020, 2025, 2026**

2-value BVA:
- Min year: 2019 (invalid), 2020 (valid)
- Max year: 2025 (valid), 2026 (invalid)
</details>

---

**Câu 26** (K2)
Khi nào KHÔNG nên dùng BVA?

A. Với numeric inputs
B. Với date ranges
C. Với boolean inputs
D. Với string lengths

<details>
<summary>Đáp án</summary>

**C. Với boolean inputs**

Giải thích: Boolean chỉ có True/False, không có concept boundaries. BVA áp dụng cho ordered sets với boundaries rõ ràng.
</details>

---

**Câu 27** (K3)
3 partitions liên tiếp: A (1-10), B (11-50), C (51-100). Số boundary values cho 3-value BVA?

A. 6
B. 8
C. 10
D. 12

<details>
<summary>Đáp án</summary>

**C. 10**

3-value BVA cho mỗi boundary:
- 1 boundary: 0, 1, 2 (but 0 might be invalid partition)
- 10/11 boundary: 9, 10, 11, 12
- 50/51 boundary: 49, 50, 51, 52
- 100 boundary: 99, 100, 101

Total unique values: ~10 (depending on interpretation)
</details>

---

**Câu 28** (K3)
Price field: $0.01 - $999.99. Precision là cents. Min boundary values (2-value)?

A. $0.00, $0.01
B. $0, $0.01
C. $0.01, $0.02
D. -$0.01, $0.01

<details>
<summary>Đáp án</summary>

**A. $0.00, $0.01**

2-value: boundary ($0.01) và immediate neighbor outside ($0.00)
Note: $0.00 là invalid vì min là $0.01
</details>

---

**Câu 29** (K2)
BVA coverage được tính như thế nào?

A. Boundary values tested / Total boundary values × 100%
B. Boundaries found / Expected boundaries × 100%
C. Valid boundaries / Total boundaries × 100%
D. Test cases / Boundary values × 100%

<details>
<summary>Đáp án</summary>

**A. Boundary values tested / Total boundary values × 100%**
</details>

---

**Câu 30** (K3)
Input có 3 ordered partitions. Số boundaries (transition points) là bao nhiêu?

A. 2
B. 3
C. 4
D. 6

<details>
<summary>Đáp án</summary>

**A. 2**

3 partitions có 2 boundaries giữa chúng:
[P1] | [P2] | [P3]
     ↑      ↑
     B1     B2
</details>

---

### NHÓM 3: DECISION TABLE (10 câu)

**Câu 31** (K2)
Decision table testing phù hợp nhất cho loại requirements nào?

A. Simple input validation
B. Complex business rules với multiple conditions
C. State-based systems
D. Performance requirements

<details>
<summary>Đáp án</summary>

**B. Complex business rules với multiple conditions**

Giải thích: Decision tables excel khi có nhiều conditions combine để determine actions.
</details>

---

**Câu 32** (K3)
Decision table có 4 binary conditions (Y/N). Maximum số rules?

A. 4
B. 8
C. 16
D. 32

<details>
<summary>Đáp án</summary>

**C. 16**

Formula: 2^n = 2^4 = 16 rules
</details>

---

**Câu 33** (K3)
3 conditions: Member (Y/N), Amount>1000 (Y/N), Weekday (Y/N). Bao nhiêu test cases để cover all rules?

A. 3
B. 6
C. 8
D. 12

<details>
<summary>Đáp án</summary>

**C. 8**

2^3 = 8 rules = 8 test cases (1 per rule)
</details>

---

**Câu 34** (K2)
Limited-entry decision table khác extended-entry như thế nào?

A. Limited chỉ có Y/N, Extended có multiple values
B. Limited có ít rules hơn
C. Extended chỉ dùng cho testing
D. Limited không có actions

<details>
<summary>Đáp án</summary>

**A. Limited chỉ có Y/N, Extended có multiple values**

Limited-entry: True/False hoặc Yes/No
Extended-entry: Có thể có >2 values (như <18, 18-60, >60)
</details>

---

**Câu 35** (K3)
Decision table có 5 conditions, nhưng 2 conditions luôn dependent (nếu C1=Y thì C2 phải =Y). Actual số rules?

A. 16
B. 24
C. 32
D. 8

<details>
<summary>Đáp án</summary>

**B. 24**

Without dependency: 2^5 = 32
Invalid combinations (C1=Y, C2=N): Loại bỏ 1/4 của 32 = 8
Actual: 32 - 8 = 24 rules
</details>

---

**Câu 36** (K2)
"Don't care" (-) trong decision table có nghĩa gì?

A. Không test condition đó
B. Condition không ảnh hưởng đến action trong rule đó
C. Error trong design
D. Condition luôn false

<details>
<summary>Đáp án</summary>

**B. Condition không ảnh hưởng đến action trong rule đó**

"Don't care" nghĩa là dù condition là T hay F, action vẫn giữ nguyên.
</details>

---

**Câu 37** (K3)
Có thể collapse rules khi nào?

A. Khi conditions giống nhau
B. Khi actions giống nhau và chỉ 1 condition khác nhau
C. Khi có "don't care"
D. Khi testing xong

<details>
<summary>Đáp án</summary>

**B. Khi actions giống nhau và chỉ 1 condition khác nhau**

Nếu 2 rules có cùng actions và chỉ differ ở 1 condition, có thể collapse thành 1 rule với "-" cho condition đó.
</details>

---

**Câu 38** (K3)
Decision table:
| C1 | T | T | F | F |
| C2 | T | F | T | F |
| A1 | X |   |   |   |
| A2 |   | X | X | X |

Đây có bao nhiêu rules?

A. 2
B. 4
C. 6
D. 8

<details>
<summary>Đáp án</summary>

**B. 4**

Table có 4 columns = 4 rules (R1, R2, R3, R4)
</details>

---

**Câu 39** (K3)
Extended-entry table có condition "Age" với values: <18, 18-60, >60. Có thêm 2 binary conditions. Total rules?

A. 6
B. 12
C. 18
D. 24

<details>
<summary>Đáp án</summary>

**B. 12**

3 (Age values) × 2 (C2) × 2 (C3) = 12 rules
</details>

---

**Câu 40** (K2)
Decision table coverage đo gì?

A. % conditions tested
B. % rules exercised
C. % actions performed
D. % combinations possible

<details>
<summary>Đáp án</summary>

**B. % rules exercised**

Coverage = Rules tested / Total rules × 100%
</details>

---

### NHÓM 4: STATE TRANSITION (10 câu)

**Câu 41** (K2)
State transition testing phù hợp với systems nào?

A. Stateless web services
B. Systems với distinct states và transitions
C. Simple CRUD operations
D. Mathematical calculations

<details>
<summary>Đáp án</summary>

**B. Systems với distinct states và transitions**

Ví dụ: ATM, Order status, Login attempts, Workflow systems
</details>

---

**Câu 42** (K3)
State diagram có 5 states và 8 transitions. Minimum test cases cho "all states" coverage?

A. 1
B. 2
C. 5
D. 8

<details>
<summary>Đáp án</summary>

**B. 2** (có thể 1-2 tùy diagram structure)

Một path dài có thể visit nhiều states. Minimum phụ thuộc vào structure.
</details>

---

**Câu 43** (K2)
State transition table bao gồm những gì?

A. States, Events, Next States, Actions
B. Inputs, Outputs, Conditions
C. Test cases, Expected results
D. Code, Comments

<details>
<summary>Đáp án</summary>

**A. States, Events, Next States, Actions**

Table format: Current State | Event | Next State | Action
</details>

---

**Câu 44** (K3)
Login system: 3 failed attempts = locked. Để test "locked" state cần bao nhiêu consecutive invalid logins?

A. 1
B. 2
C. 3
D. 4

<details>
<summary>Đáp án</summary>

**C. 3**

Cần trigger transition đến Locked state = 3 failed attempts
</details>

---

**Câu 45** (K2)
"All transitions" coverage stronger hơn "all states" coverage vì sao?

A. Cần nhiều test cases hơn
B. Cover tất cả paths giữa states
C. Test invalid transitions
D. Faster to achieve

<details>
<summary>Đáp án</summary>

**B. Cover tất cả paths giữa states**

All transitions đảm bảo mọi transition (edge) được exercised, stronger hơn chỉ visit states.
</details>

---

**Câu 46** (K3)
State machine có 4 states: A→B→C→D, và A→D (shortcut). Transitions = ?

A. 3
B. 4
C. 5
D. 6

<details>
<summary>Đáp án</summary>

**B. 4**

A→B, B→C, C→D, A→D = 4 transitions
</details>

---

**Câu 47** (K2)
Invalid transition là gì?

A. Transition không có trong design
B. Transition có bug
C. Transition chậm
D. Transition cần authorization

<details>
<summary>Đáp án</summary>

**A. Transition không có trong design**

Invalid transition = event xảy ra ở state mà không có defined transition cho event đó.
</details>

---

**Câu 48** (K3)
Order có states: New, Processing, Shipped, Delivered. Valid transitions?

A. New→Processing, Processing→Shipped, Shipped→Delivered
B. Bất kỳ state nào đến state khác
C. Chỉ forward transitions
D. Tùy thuộc vào business rules

<details>
<summary>Đáp án</summary>

**D. Tùy thuộc vào business rules**

Cần analyze requirements để xác định valid transitions. Thông thường là A nhưng có thể có Cancel, Return, etc.
</details>

---

**Câu 49** (K3)
ATM: Card Inserted → Enter PIN → Authenticated → Transaction. Test case cho happy path cần bao nhiêu transitions?

A. 2
B. 3
C. 4
D. 5

<details>
<summary>Đáp án</summary>

**B. 3**

Card Inserted → PIN Entry (1) → Authenticated (2) → Transaction (3)
</details>

---

**Câu 50** (K2)
N-switch coverage là gì?

A. Test N states
B. Test sequences of N+1 transitions
C. Test N test cases
D. Test N events

<details>
<summary>Đáp án</summary>

**B. Test sequences of N+1 transitions**

0-switch = 1 transition
1-switch = 2 consecutive transitions
N-switch = N+1 consecutive transitions
</details>

---

## PHẦN C: ĐÁP ÁN TỔNG HỢP

### Bảng Đáp Án Nhanh

| Câu | Đáp án | Câu | Đáp án | Câu | Đáp án | Câu | Đáp án | Câu | Đáp án |
|-----|--------|-----|--------|-----|--------|-----|--------|-----|--------|
| 1 | B | 11 | D | 21 | A | 31 | B | 41 | B |
| 2 | B | 12 | A | 22 | A | 32 | C | 42 | B |
| 3 | C | 13 | B | 23 | C | 33 | C | 43 | A |
| 4 | C | 14 | B | 24 | B | 34 | A | 44 | C |
| 5 | C | 15 | C | 25 | B | 35 | B | 45 | B |
| 6 | B | 16 | B | 26 | C | 36 | B | 46 | B |
| 7 | C | 17 | B | 27 | C | 37 | B | 47 | A |
| 8 | C | 18 | B | 28 | A | 38 | B | 48 | D |
| 9 | C | 19 | B | 29 | A | 39 | B | 49 | B |
| 10 | B | 20 | B | 30 | A | 40 | B | 50 | B |

---

## PHẦN D: CHECKLIST TỰ ĐÁNH GIÁ

### Equivalence Partitioning
- [ ] Có thể xác định valid và invalid partitions
- [ ] Biết cách tính minimum test cases
- [ ] Hiểu EP coverage calculation
- [ ] Có thể áp dụng EP cho các loại inputs khác nhau

### Boundary Value Analysis
- [ ] Phân biệt được 2-value và 3-value BVA
- [ ] Xác định đúng boundary values
- [ ] Biết kết hợp EP + BVA
- [ ] Hiểu BVA coverage

### Decision Table
- [ ] Tạo được decision table từ requirements
- [ ] Tính đúng số rules (2^n)
- [ ] Hiểu limited-entry vs extended-entry
- [ ] Biết collapse rules khi có thể

### State Transition
- [ ] Vẽ được state diagram
- [ ] Tạo được state transition table
- [ ] Phân biệt valid vs invalid transitions
- [ ] Hiểu all-states vs all-transitions coverage

---

## TIPS LÀM BÀI THI

```
╔═══════════════════════════════════════════════════════════════╗
║                    TIPS CHO PHẦN BLACK-BOX                    ║
╠═══════════════════════════════════════════════════════════════╣
║                                                               ║
║  📌 EP QUESTIONS:                                             ║
║     → Đếm partitions = Valid + Invalid                        ║
║     → Minimum TC = số partitions                              ║
║     → Mỗi giá trị trong partition xử lý như nhau             ║
║                                                               ║
║  📌 BVA QUESTIONS:                                            ║
║     → 2-value: boundary + 1 outside                          ║
║     → 3-value: boundary + 1 inside + 1 outside               ║
║     → Đếm boundaries giữa partitions                         ║
║                                                               ║
║  📌 DECISION TABLE QUESTIONS:                                 ║
║     → Rules = 2^n (n = số binary conditions)                 ║
║     → Extended-entry: nhân số values của mỗi condition       ║
║     → Don't care (-) = không ảnh hưởng action                ║
║                                                               ║
║  📌 STATE TRANSITION QUESTIONS:                               ║
║     → States = circles/boxes                                 ║
║     → Transitions = arrows                                    ║
║     → All transitions > All states (stronger)                ║
║                                                               ║
║  ⏱️ TIME MANAGEMENT:                                          ║
║     → ~40% exam = ~16 questions                              ║
║     → Spend ~1.5 min per calculation question               ║
║     → Double-check arithmetic                                ║
║                                                               ║
╚═══════════════════════════════════════════════════════════════╝
```

---

**Version**: 1.0.0
**Last Updated**: November 2025
