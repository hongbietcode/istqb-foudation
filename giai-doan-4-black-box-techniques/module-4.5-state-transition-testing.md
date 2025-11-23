# MODULE 4.5: STATE TRANSITION TESTING

**Thời lượng**: 3-4 giờ | **Độ khó**: ⭐⭐⭐
**Tầm quan trọng**: ~5% câu hỏi trong kỳ thi ISTQB

---

## MỤC TIÊU HỌC TẬP

| ID | Mục tiêu | Level |
|----|----------|-------|
| FL-4.2.4 | Sử dụng State Transition Testing để derive test cases | K3 |

---

## 1. STATE TRANSITION TESTING LÀ GÌ?

### 1.1. Định Nghĩa

> **State Transition Testing** là kỹ thuật test các hệ thống có **states** (trạng thái) khác nhau, và các **events** (sự kiện) gây ra **transitions** (chuyển đổi) giữa các states.

```
╔═══════════════════════════════════════════════════════════════╗
║               STATE TRANSITION TESTING                        ║
╠═══════════════════════════════════════════════════════════════╣
║                                                               ║
║  CÁC THÀNH PHẦN:                                              ║
║  ──────────────                                               ║
║  • STATE: Trạng thái của hệ thống                            ║
║  • EVENT: Sự kiện gây ra chuyển trạng thái                   ║
║  • TRANSITION: Sự chuyển đổi từ state này sang state khác   ║
║  • ACTION: Hành động xảy ra khi transition                   ║
║  • GUARD: Điều kiện cần thỏa để transition xảy ra           ║
║                                                               ║
║  VÍ DỤ: Order Status                                         ║
║  ───────────────────                                          ║
║                                                               ║
║       ┌─────────┐   Payment    ┌─────────┐   Ship    ┌──────┐║
║       │   New   │────────────►│  Paid   │─────────►│Shipped│║
║       └─────────┘   received   └─────────┘           └──────┘║
║            │                                            │     ║
║            │ Cancel                          Delivered  │     ║
║            ▼                                            ▼     ║
║       ┌─────────┐                              ┌───────────┐ ║
║       │Cancelled│                              │ Delivered │ ║
║       └─────────┘                              └───────────┘ ║
║                                                               ║
╚═══════════════════════════════════════════════════════════════╝
```

### 1.2. Khi Nào Sử Dụng?

```
✅ SỬ DỤNG STATE TRANSITION KHI:
   • System có distinct states
   • Events trigger state changes
   • Same event có different effect depending on current state

EXAMPLES:
   • Order status: New → Paid → Shipped → Delivered
   • ATM: Idle → Card inserted → PIN entered → Transaction
   • Login: Active → Locked (after 3 failed attempts)
   • Document: Draft → Review → Approved → Published
```

---

## 2. STATE DIAGRAM VÀ STATE TABLE

### 2.1. State Diagram

```
╔═══════════════════════════════════════════════════════════════╗
║                    STATE DIAGRAM                              ║
╠═══════════════════════════════════════════════════════════════╣
║                                                               ║
║  KÝ HIỆU:                                                     ║
║  ───────                                                      ║
║  ○  Start point (initial state)                              ║
║  ◉  End point (final state)                                  ║
║  (○) State (circle)                                           ║
║  →  Transition (arrow)                                        ║
║  event [guard] / action  Label on transition                 ║
║                                                               ║
║  VÍ DỤ: Login với Account Lock                               ║
║  ─────────────────────────────                                ║
║                                                               ║
║            ○                                                  ║
║            │ Start                                            ║
║            ▼                                                  ║
║       ┌─────────┐                                             ║
║       │ Active  │◄─────────────────────────┐                 ║
║       │(count=0)│                          │                 ║
║       └────┬────┘                          │                 ║
║            │                               │                 ║
║            │ Wrong password               │                 ║
║            │ [count < 3]                  │                 ║
║            │ / count++                    │ Unlock          ║
║            ▼                               │                 ║
║       ┌─────────┐                          │                 ║
║       │ Active  │                          │                 ║
║       │(count=n)│──────────────────────────┘                 ║
║       └────┬────┘                                             ║
║            │                                                  ║
║            │ Wrong password                                   ║
║            │ [count = 3]                                     ║
║            ▼                                                  ║
║       ┌─────────┐                                             ║
║       │ Locked  │                                             ║
║       └─────────┘                                             ║
║                                                               ║
╚═══════════════════════════════════════════════════════════════╝
```

### 2.2. State Table

```
╔═══════════════════════════════════════════════════════════════╗
║                     STATE TABLE                               ║
╠═══════════════════════════════════════════════════════════════╣
║                                                               ║
║  STATE TABLE = Matrix format của State Diagram               ║
║                                                               ║
║  Rows: Current States                                         ║
║  Columns: Events                                              ║
║  Cells: Next State / Action                                   ║
║                                                               ║
║  VÍ DỤ: ATM State Table                                      ║
║  ───────────────────────                                      ║
║                                                               ║
║  Current     │ Insert  │ Enter  │ Valid   │ Invalid │ Eject  ║
║  State       │ Card    │ PIN    │ PIN     │ PIN     │ Card   ║
║  ════════════╪═════════╪════════╪═════════╪═════════╪════════║
║  Idle        │ Card    │   -    │    -    │    -    │   -    ║
║              │ Inserted│        │         │         │        ║
║  ────────────┼─────────┼────────┼─────────┼─────────┼────────║
║  Card        │    -    │ PIN    │    -    │    -    │ Idle   ║
║  Inserted    │         │ Entered│         │         │        ║
║  ────────────┼─────────┼────────┼─────────┼─────────┼────────║
║  PIN         │    -    │   -    │ Trans-  │ Card    │   -    ║
║  Entered     │         │        │ action  │ Inserted│        ║
║  ────────────┼─────────┼────────┼─────────┼─────────┼────────║
║  Transaction │    -    │   -    │    -    │    -    │ Idle   ║
║                                                               ║
║  "-" = Invalid transition (event không valid ở state này)   ║
║                                                               ║
╚═══════════════════════════════════════════════════════════════╝
```

---

## 3. COVERAGE CRITERIA

### 3.1. Các Mức Coverage

```
╔═══════════════════════════════════════════════════════════════╗
║               STATE TRANSITION COVERAGE                       ║
╠═══════════════════════════════════════════════════════════════╣
║                                                               ║
║  1️⃣ ALL STATES COVERAGE                                       ║
║     → Visit mỗi state ít nhất 1 lần                          ║
║     → Weakest coverage                                        ║
║                                                               ║
║  2️⃣ VALID TRANSITIONS COVERAGE (0-switch)                     ║
║     → Execute mỗi VALID transition ít nhất 1 lần            ║
║     → Most common requirement                                ║
║                                                               ║
║  3️⃣ ALL TRANSITIONS COVERAGE                                  ║
║     → Test cả valid VÀ invalid transitions                   ║
║     → Verify invalid events are handled correctly            ║
║                                                               ║
╚═══════════════════════════════════════════════════════════════╝
```

### 3.2. Công Thức Coverage

```
                        States visited
All States Coverage = ─────────────────── × 100%
                        Total states

                             Valid transitions tested
Valid Transitions Coverage = ───────────────────────── × 100%
                             Total valid transitions
```

---

## 4. VÍ DỤ CHI TIẾT

### 4.1. Ví Dụ 1: Order Status (E-commerce)

```
STATES:
• S1: New (Order created)
• S2: Paid (Payment received)
• S3: Shipped (Order shipped)
• S4: Delivered (Order delivered)
• S5: Cancelled

EVENTS:
• E1: Pay (Customer pays)
• E2: Ship (Seller ships)
• E3: Deliver (Carrier delivers)
• E4: Cancel (Customer/Seller cancels)

STATE DIAGRAM:
═══════════════════════════════════════════════════════════════

              ○ Start
              │
              ▼
         ┌─────────┐
         │   New   │◄───────────────────────────┐
         │   (S1)  │                            │
         └────┬────┘                            │
              │                                 │
         E1   │ Pay                             │
              ▼                                 │
         ┌─────────┐                            │
         │  Paid   │                            │
         │   (S2)  │                            │
         └────┬────┘                            │
              │                            E4   │
         E2   │ Ship                      Cancel│
              ▼                                 │
         ┌─────────┐                            │
         │ Shipped │────────────────────────────┤
         │   (S3)  │                            │
         └────┬────┘                            │
              │                                 │
         E3   │ Deliver                         │
              ▼                                 │
         ┌─────────┐                  ┌─────────┐
         │Delivered│                  │Cancelled│
         │   (S4)  │                  │   (S5)  │
         └─────────┘                  └─────────┘
              ◉                            ◉

STATE TABLE:
═══════════════════════════════════════════════════════════════

Current   │   E1: Pay   │  E2: Ship  │ E3: Deliver │ E4: Cancel
State     │             │            │             │
══════════╪═════════════╪════════════╪═════════════╪═══════════
S1: New   │    S2       │     -      │      -      │    S5
S2: Paid  │     -       │    S3      │      -      │    S5
S3: Ship  │     -       │     -      │     S4      │    S5
S4: Done  │     -       │     -      │      -      │     -
S5: Cancel│     -       │     -      │      -      │     -

VALID TRANSITIONS: 6
(New→Paid, Paid→Shipped, Shipped→Delivered, New→Cancelled,
 Paid→Cancelled, Shipped→Cancelled)

TEST CASES (Valid Transitions Coverage):
═══════════════════════════════════════════════════════════════

┌──────┬────────────────────────────────────────────────────────┐
│ TC   │ Test Scenario                                          │
├──────┼────────────────────────────────────────────────────────┤
│ TC1  │ New → Pay → Paid                                       │
│ TC2  │ Paid → Ship → Shipped                                  │
│ TC3  │ Shipped → Deliver → Delivered                          │
│ TC4  │ New → Cancel → Cancelled                               │
│ TC5  │ Paid → Cancel → Cancelled                              │
│ TC6  │ Shipped → Cancel → Cancelled                           │
└──────┴────────────────────────────────────────────────────────┘

Coverage: 6/6 valid transitions = 100%
```

### 4.2. Ví Dụ 2: Login Account Lock

```
REQUIREMENT:
• After 3 wrong password attempts, account is locked
• Admin can unlock account

STATES:
• S1: Active (attempts = 0)
• S2: Active (attempts = 1)
• S3: Active (attempts = 2)
• S4: Locked

EVENTS:
• E1: Correct password → Login success
• E2: Wrong password → Increment attempts
• E3: Unlock (Admin action)

STATE DIAGRAM:
═══════════════════════════════════════════════════════════════

                    ○
                    │
                    ▼
              ┌───────────┐
         ┌───►│  Active   │◄─────────────────────┐
         │    │ (count=0) │                      │
         │    └─────┬─────┘                      │
         │          │                            │
    E1   │     E2   │ Wrong                      │
 Correct │          ▼                            │
         │    ┌───────────┐                      │
         │◄───│  Active   │                 E3   │
         │    │ (count=1) │               Unlock │
         │    └─────┬─────┘                      │
         │          │                            │
    E1   │     E2   │ Wrong                      │
 Correct │          ▼                            │
         │    ┌───────────┐                      │
         │◄───│  Active   │                      │
              │ (count=2) │                      │
              └─────┬─────┘                      │
                    │                            │
               E2   │ Wrong                      │
                    ▼                            │
              ┌───────────┐                      │
              │  Locked   │──────────────────────┘
              └───────────┘

TEST CASES:
═══════════════════════════════════════════════════════════════

┌──────┬─────────────────────────────────────────────────────┐
│ TC   │ Sequence                           │ Expected State │
├──────┼─────────────────────────────────────┼────────────────┤
│ TC1  │ Correct password                   │ Login success  │
│ TC2  │ Wrong → Correct                    │ Login success  │
│ TC3  │ Wrong → Wrong → Correct            │ Login success  │
│ TC4  │ Wrong → Wrong → Wrong              │ Locked         │
│ TC5  │ Wrong × 3 → Unlock → Correct       │ Login success  │
└──────┴─────────────────────────────────────┴────────────────┘
```

---

## 5. INVALID TRANSITIONS

```
╔═══════════════════════════════════════════════════════════════╗
║                  INVALID TRANSITIONS                          ║
╠═══════════════════════════════════════════════════════════════╣
║                                                               ║
║  DEFINITION:                                                  ║
║  Events mà KHÔNG NÊN có effect ở state hiện tại             ║
║                                                               ║
║  VÍ DỤ: Order Status                                         ║
║  • "Ship" event khi order ở state "New" → Invalid            ║
║  • "Pay" event khi order ở state "Delivered" → Invalid       ║
║                                                               ║
║  WHY TEST INVALID?                                            ║
║  • Verify system rejects invalid events                      ║
║  • Verify system stays in correct state                      ║
║  • Verify appropriate error message                          ║
║                                                               ║
║  TEST CASE EXAMPLE:                                           ║
║  ─────────────────                                            ║
║  Current State: New                                           ║
║  Event: Ship (invalid at this state)                         ║
║  Expected: Error "Cannot ship - payment required first"      ║
║  Expected State: Remains "New"                               ║
║                                                               ║
╚═══════════════════════════════════════════════════════════════╝
```

---

## 6. BÀI TẬP THỰC HÀNH

### Bài tập 1: ATM Machine

**States**: Idle, Card Inserted, PIN Entered, Transaction Mode
**Events**: Insert Card, Enter PIN (valid/invalid), Withdraw, Eject Card

**Yêu cầu**: Vẽ state diagram và tạo test cases cho valid transitions.

<details>
<summary>Đáp án</summary>

**State Diagram:**
```
        ┌──────────────────────────────────────────┐
        │                                          │
        ▼                                          │
   ┌─────────┐   Insert    ┌─────────────┐        │
   │  Idle   │────Card────►│ Card        │        │
   └─────────┘             │ Inserted    │        │
        ▲                  └──────┬──────┘        │
        │                         │               │
   Eject│                   Valid │ PIN           │ Eject
   Card │                         ▼               │
        │                  ┌─────────────┐        │
        │                  │ PIN         │────────┘
        │                  │ Entered     │ (Invalid PIN)
        │                  └──────┬──────┘
        │                         │
        │                  Withdraw│
        │                         ▼
        │                  ┌─────────────┐
        └──────────────────│ Transaction │
             Complete      │ Mode        │
                           └─────────────┘
```

**Test Cases:**

| TC | Sequence | Expected |
|----|----------|----------|
| TC1 | Insert Card | State: Card Inserted |
| TC2 | Insert → Valid PIN | State: PIN Entered |
| TC3 | Insert → Invalid PIN | State: Card Inserted, Error message |
| TC4 | Insert → Valid PIN → Withdraw | Transaction completes |
| TC5 | Insert → Eject | State: Idle |

</details>

---

## 7. CÂU HỎI ÔN TẬP

### Câu 1 (K3)
Cho hệ thống có 4 states và 6 valid transitions. Để đạt 100% valid transitions coverage cần tối thiểu bao nhiêu test cases?

A. 4
B. 6
C. Phụ thuộc vào diagram
D. 10

<details>
<summary>Đáp án</summary>

**C. Phụ thuộc vào diagram**

Số test cases phụ thuộc vào cách các transitions được kết nối. Có thể cover nhiều transitions trong 1 test case nếu chúng liên tiếp.
</details>

---

### Câu 2 (K2)
State Transition Testing phù hợp nhất cho?

A. Input validation
B. Systems với distinct states và events causing state changes
C. Performance testing
D. Database testing

<details>
<summary>Đáp án</summary>

**B. Systems với distinct states và events causing state changes**
</details>

---

## 8. CHECKLIST TỰ ĐÁNH GIÁ

- [ ] Hiểu được các thành phần của State Transition (State, Event, Transition, Action)
- [ ] Vẽ được State Diagram từ requirements
- [ ] Tạo được State Table
- [ ] Hiểu được các coverage levels (All States, Valid Transitions, All Transitions)
- [ ] Xác định được valid và invalid transitions
- [ ] Tạo được test cases từ state diagram

---

**Tiếp theo**: [Bài tập Giai đoạn 4](./bai-tap-giai-doan-4.md)

---

**Version**: 1.0.0
**Last Updated**: November 2025
