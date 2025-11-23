# MODULE 3.2: TEST LEVELS (CÁC CẤP ĐỘ KIỂM THỬ)

**Thời lượng**: 3-4 giờ | **Độ khó**: ⭐⭐

---

## MỤC TIÊU HỌC TẬP (Learning Objectives)

Sau khi hoàn thành module này, bạn sẽ:

| ID | Mục tiêu | Level |
|----|----------|-------|
| FL-2.2.1 | Phân biệt được các test levels khác nhau | K2 |
| FL-2.2.2 | Xác định test objectives, test basis, test objects cho mỗi level | K1 |

---

## 1. TỔNG QUAN VỀ TEST LEVELS

### 1.1. Test Level Là Gì?

> **Test Level** là một nhóm các hoạt động testing được tổ chức và quản lý cùng nhau, liên quan đến mức độ chi tiết cụ thể của hệ thống.

```
╔═══════════════════════════════════════════════════════════════╗
║                      5 TEST LEVELS                            ║
╠═══════════════════════════════════════════════════════════════╣
║                                                               ║
║                    ┌──────────────────────┐                   ║
║                    │  ACCEPTANCE TESTING  │  ← User/Business  ║
║                    └──────────────────────┘                   ║
║                              ▲                                ║
║                    ┌──────────────────────┐                   ║
║                    │ SYSTEM INTEGRATION   │  ← Systems        ║
║                    │      TESTING         │                   ║
║                    └──────────────────────┘                   ║
║                              ▲                                ║
║                    ┌──────────────────────┐                   ║
║                    │   SYSTEM TESTING     │  ← Complete app   ║
║                    └──────────────────────┘                   ║
║                              ▲                                ║
║                    ┌──────────────────────┐                   ║
║                    │COMPONENT INTEGRATION │  ← Components     ║
║                    │      TESTING         │                   ║
║                    └──────────────────────┘                   ║
║                              ▲                                ║
║                    ┌──────────────────────┐                   ║
║                    │ COMPONENT TESTING    │  ← Units/Modules  ║
║                    │    (Unit Testing)    │                   ║
║                    └──────────────────────┘                   ║
║                                                               ║
╚═══════════════════════════════════════════════════════════════╝
```

### 1.2. Tại Sao Cần Nhiều Test Levels?

```
╔═══════════════════════════════════════════════════════════════╗
║           TẠI SAO CẦN NHIỀU TEST LEVELS?                      ║
╠═══════════════════════════════════════════════════════════════╣
║                                                               ║
║  1️⃣ MỖI LEVEL CÓ OBJECTIVES RIÊNG                            ║
║     → Unit: Find coding errors                               ║
║     → Integration: Find interface defects                    ║
║     → System: Verify complete functionality                  ║
║     → Acceptance: Validate business needs                    ║
║                                                               ║
║  2️⃣ KHÁC NHAU VỀ TEST BASIS                                  ║
║     → Unit: Code, detailed design                            ║
║     → System: Requirements, user stories                     ║
║     → Acceptance: Business processes                         ║
║                                                               ║
║  3️⃣ PHÁT HIỆN DEFECTS KHÁC NHAU                              ║
║     → Unit: Logic errors, calculation bugs                   ║
║     → Integration: Data flow issues, API mismatches          ║
║     → System: Missing features, wrong behavior               ║
║                                                               ║
║  4️⃣ TRÁCH NHIỆM KHÁC NHAU                                    ║
║     → Unit: Developers                                       ║
║     → System/Acceptance: Testers, Users                      ║
║                                                               ║
╚═══════════════════════════════════════════════════════════════╝
```

---

## 2. COMPONENT TESTING (UNIT TESTING)

### 2.1. Định Nghĩa

> **Component Testing** (còn gọi là Unit Testing) là kiểm tra các đơn vị nhỏ nhất của phần mềm một cách **độc lập** (isolated).

```
╔═══════════════════════════════════════════════════════════════╗
║               COMPONENT TESTING (UNIT TESTING)                ║
╠═══════════════════════════════════════════════════════════════╣
║                                                               ║
║  🎯 OBJECTIVES:                                               ║
║     • Find defects trong từng component                      ║
║     • Verify component works correctly                       ║
║     • Build confidence in component quality                  ║
║     • Reduce risk ở levels cao hơn                          ║
║                                                               ║
║  📚 TEST BASIS:                                               ║
║     • Component design                                        ║
║     • Source code                                            ║
║     • Data model                                             ║
║                                                               ║
║  🔍 TEST OBJECTS:                                             ║
║     • Functions / Methods                                    ║
║     • Classes / Modules                                      ║
║     • Database procedures                                    ║
║     • Scripts                                                ║
║                                                               ║
║  👤 THƯỜNG DO AI THỰC HIỆN:                                   ║
║     • Developers (người viết code)                           ║
║     • Với TDD: Test viết trước code                          ║
║                                                               ║
║  🔧 TOOLS:                                                    ║
║     • JUnit (Java)                                           ║
║     • Jest, Mocha (JavaScript)                               ║
║     • pytest (Python)                                        ║
║     • NUnit (C#)                                             ║
║                                                               ║
╚═══════════════════════════════════════════════════════════════╝
```

### 2.2. Ví Dụ Component Testing

```javascript
// Source code: calculateDiscount.js
function calculateDiscount(orderAmount, memberLevel) {
  if (orderAmount < 0) {
    throw new Error("Invalid order amount");
  }

  if (memberLevel === "GOLD") {
    return orderAmount * 0.15;
  } else if (memberLevel === "SILVER") {
    return orderAmount * 0.10;
  } else {
    return orderAmount * 0.05;
  }
}

// Unit Tests: calculateDiscount.test.js
describe('calculateDiscount', () => {

  // Test case 1: Gold member discount
  test('should return 15% discount for GOLD member', () => {
    expect(calculateDiscount(1000000, "GOLD")).toBe(150000);
  });

  // Test case 2: Silver member discount
  test('should return 10% discount for SILVER member', () => {
    expect(calculateDiscount(1000000, "SILVER")).toBe(100000);
  });

  // Test case 3: Regular member discount
  test('should return 5% discount for regular member', () => {
    expect(calculateDiscount(1000000, "REGULAR")).toBe(50000);
  });

  // Test case 4: Invalid input
  test('should throw error for negative amount', () => {
    expect(() => calculateDiscount(-100, "GOLD")).toThrow();
  });

});
```

### 2.3. Defects Tìm Được Ở Component Level

```
TYPICAL DEFECTS FOUND:
───────────────────────────────────────────────────────────────
✗ Logic errors (wrong conditions, calculations)
✗ Data handling errors (wrong data types, overflow)
✗ Boundary issues (off-by-one errors)
✗ Error handling issues (missing exception handling)
✗ Incorrect function behavior
```

---

## 3. COMPONENT INTEGRATION TESTING

### 3.1. Định Nghĩa

> **Component Integration Testing** kiểm tra **interfaces** và **interactions** giữa các components đã được unit test.

```
╔═══════════════════════════════════════════════════════════════╗
║             COMPONENT INTEGRATION TESTING                     ║
╠═══════════════════════════════════════════════════════════════╣
║                                                               ║
║  🎯 OBJECTIVES:                                               ║
║     • Verify interfaces between components                   ║
║     • Detect integration defects                             ║
║     • Verify data flow between components                    ║
║                                                               ║
║  📚 TEST BASIS:                                               ║
║     • Software design                                        ║
║     • Architecture diagrams                                  ║
║     • Interface specifications                               ║
║     • Communication protocols                                ║
║                                                               ║
║  🔍 TEST OBJECTS:                                             ║
║     • APIs                                                   ║
║     • Interfaces between modules                             ║
║     • Database interactions                                  ║
║     • Microservice communications                            ║
║                                                               ║
║  👤 THƯỜNG DO AI THỰC HIỆN:                                   ║
║     • Developers                                             ║
║     • Integration testers                                    ║
║                                                               ║
╚═══════════════════════════════════════════════════════════════╝
```

### 3.2. Integration Strategies

```
╔═══════════════════════════════════════════════════════════════╗
║              INTEGRATION STRATEGIES                           ║
╠═══════════════════════════════════════════════════════════════╣
║                                                               ║
║  1️⃣ BIG BANG INTEGRATION                                      ║
║     All components integrated at once                        ║
║     ┌───┐ ┌───┐ ┌───┐                                        ║
║     │ A │ │ B │ │ C │  →  ┌─────────────┐                    ║
║     └───┘ └───┘ └───┘     │  A + B + C  │                    ║
║                           └─────────────┘                    ║
║     ✓ Fast setup                                             ║
║     ✗ Hard to isolate defects                               ║
║                                                               ║
║  2️⃣ INCREMENTAL INTEGRATION                                   ║
║     Components integrated one by one                         ║
║                                                               ║
║     2a. TOP-DOWN:                                             ║
║         ┌───┐                                                ║
║         │ A │ (tested first with stubs)                      ║
║         └─┬─┘                                                ║
║        ┌──┴──┐                                               ║
║       ┌┴┐   ┌┴┐                                              ║
║       │B│   │C│ (replace stubs gradually)                    ║
║       └─┘   └─┘                                              ║
║                                                               ║
║     2b. BOTTOM-UP:                                            ║
║       ┌───┐ ┌───┐                                            ║
║       │ B │ │ C │ (tested first with drivers)                ║
║       └─┬─┘ └─┬─┘                                            ║
║         └──┬──┘                                              ║
║          ┌─┴─┐                                               ║
║          │ A │ (integrated last)                             ║
║          └───┘                                               ║
║                                                               ║
╚═══════════════════════════════════════════════════════════════╝
```

### 3.3. Ví Dụ Component Integration Testing

```
VÍ DỤ: E-commerce Application
═══════════════════════════════════════════════════════════════

                    ┌─────────────┐
                    │   Frontend  │
                    │  (React)    │
                    └──────┬──────┘
                           │ API calls
                           ▼
                    ┌─────────────┐
                    │  Backend    │
                    │  (Node.js)  │
                    └──────┬──────┘
                           │ Queries
                           ▼
                    ┌─────────────┐
                    │  Database   │
                    │ (PostgreSQL)│
                    └─────────────┘

INTEGRATION TESTS:
───────────────────────────────────────────────────────────────
Test 1: Frontend → Backend API
        "When user clicks 'Add to Cart', API receives correct data"

Test 2: Backend → Database
        "When API saves order, data is correctly stored in DB"

Test 3: Backend → Payment Gateway (external)
        "When payment submitted, gateway returns correct response"
```

### 3.4. Defects Tìm Được Ở Integration Level

```
TYPICAL DEFECTS FOUND:
───────────────────────────────────────────────────────────────
✗ Interface mismatches (wrong data format, missing fields)
✗ Communication failures (timeout, connection errors)
✗ Data inconsistencies between components
✗ Incorrect API calls (wrong endpoints, methods)
✗ Missing error handling for integration failures
```

---

## 4. SYSTEM TESTING

### 4.1. Định Nghĩa

> **System Testing** kiểm tra **toàn bộ hệ thống** như một tổng thể, verify rằng hệ thống đáp ứng các requirements.

```
╔═══════════════════════════════════════════════════════════════╗
║                    SYSTEM TESTING                             ║
╠═══════════════════════════════════════════════════════════════╣
║                                                               ║
║  🎯 OBJECTIVES:                                               ║
║     • Verify complete system functionality                   ║
║     • Validate system meets requirements                     ║
║     • Test end-to-end scenarios                              ║
║     • Test both functional and non-functional aspects        ║
║                                                               ║
║  📚 TEST BASIS:                                               ║
║     • System requirements specifications                     ║
║     • User stories và acceptance criteria                    ║
║     • Use cases                                              ║
║     • System behavior models                                 ║
║     • Risk analysis reports                                   ║
║                                                               ║
║  🔍 TEST OBJECTS:                                             ║
║     • Complete, integrated system                            ║
║     • System configuration                                   ║
║     • System documentation (user guides)                     ║
║                                                               ║
║  👤 THƯỜNG DO AI THỰC HIỆN:                                   ║
║     • Independent test team                                  ║
║     • QA team                                                ║
║                                                               ║
║  🔧 ENVIRONMENT:                                              ║
║     • Production-like environment                            ║
║     • Realistic test data                                    ║
║                                                               ║
╚═══════════════════════════════════════════════════════════════╝
```

### 4.2. Ví Dụ System Testing

```
VÍ DỤ: System Testing cho Mobile Banking App (VietQR)
═══════════════════════════════════════════════════════════════

TEST SCENARIO: Transfer money end-to-end

PRECONDITIONS:
- User đã login
- Account có số dư 10,000,000 VND
- Recipient account hợp lệ

TEST STEPS:
┌──────────────────────────────────────────────────────────────┐
│ Step │ Action                      │ Expected Result          │
├──────┼─────────────────────────────┼──────────────────────────┤
│  1   │ Select "Transfer"           │ Transfer screen shows    │
│  2   │ Enter recipient bank        │ Bank list displayed      │
│  3   │ Enter account number        │ Account validated        │
│  4   │ Enter amount: 1,000,000     │ Amount field populated   │
│  5   │ Enter description           │ Description accepted     │
│  6   │ Click "Continue"            │ Summary screen shows     │
│  7   │ Verify details              │ All info correct         │
│  8   │ Enter OTP                   │ OTP verified             │
│  9   │ Click "Confirm"             │ Processing indicator     │
│ 10   │ Wait for completion         │ Success message shown    │
│      │                             │ Balance: 9,000,000 VND   │
│      │                             │ Transaction history      │
│      │                             │ SMS notification sent    │
└──────────────────────────────────────────────────────────────┘

TEST TYPES TRONG SYSTEM TESTING:
───────────────────────────────────────────────────────────────
✓ Functional: Transfer works correctly
✓ Security: OTP required, data encrypted
✓ Performance: Complete trong 3 giây
✓ Usability: Flow dễ hiểu
✓ Compatibility: Works trên iOS và Android
```

### 4.3. System Testing Types

```
╔═══════════════════════════════════════════════════════════════╗
║            SYSTEM TESTING TYPES                               ║
╠═══════════════════════════════════════════════════════════════╣
║                                                               ║
║  FUNCTIONAL TESTING:                                          ║
║  ├── Feature testing                                          ║
║  ├── End-to-end testing                                       ║
║  ├── Scenario-based testing                                   ║
║  └── Use case testing                                         ║
║                                                               ║
║  NON-FUNCTIONAL TESTING:                                      ║
║  ├── Performance testing (load, stress, scalability)          ║
║  ├── Security testing                                         ║
║  ├── Usability testing                                        ║
║  ├── Compatibility testing                                    ║
║  ├── Reliability testing                                      ║
║  └── Accessibility testing                                    ║
║                                                               ║
╚═══════════════════════════════════════════════════════════════╝
```

---

## 5. SYSTEM INTEGRATION TESTING

### 5.1. Định Nghĩa

> **System Integration Testing** kiểm tra interfaces giữa **hệ thống của chúng ta** với **các hệ thống bên ngoài** (external systems, third-party services).

```
╔═══════════════════════════════════════════════════════════════╗
║              SYSTEM INTEGRATION TESTING                       ║
╠═══════════════════════════════════════════════════════════════╣
║                                                               ║
║  🎯 OBJECTIVES:                                               ║
║     • Verify interfaces with external systems                ║
║     • Test data exchange between systems                     ║
║     • Verify system interoperability                         ║
║                                                               ║
║  📚 TEST BASIS:                                               ║
║     • System architecture                                     ║
║     • Interface specifications                               ║
║     • API documentation (external)                           ║
║     • SLAs with third parties                                ║
║                                                               ║
║  🔍 TEST OBJECTS:                                             ║
║     • Subsystems                                             ║
║     • External system interfaces                             ║
║     • APIs với third-party services                          ║
║                                                               ║
╚═══════════════════════════════════════════════════════════════╝
```

### 5.2. Ví Dụ System Integration Testing

```
VÍ DỤ: E-commerce Website với External Systems
═══════════════════════════════════════════════════════════════

           ┌─────────────────────────────────────────┐
           │           E-COMMERCE SYSTEM             │
           │                                         │
           │  ┌───────┐  ┌───────┐  ┌───────────┐  │
           │  │ Cart  │  │ Order │  │ Inventory │  │
           │  └───┬───┘  └───┬───┘  └─────┬─────┘  │
           │      │          │            │        │
           └──────┼──────────┼────────────┼────────┘
                  │          │            │
    ──────────────┼──────────┼────────────┼──────────────
    EXTERNAL      │          │            │
    SYSTEMS       ▼          ▼            ▼
           ┌──────────┐ ┌─────────┐ ┌──────────┐
           │ PAYMENT  │ │ SHIPPING│ │ SUPPLIER │
           │ GATEWAY  │ │ PARTNER │ │  SYSTEM  │
           │ (VNPay)  │ │ (GHN)   │ │          │
           └──────────┘ └─────────┘ └──────────┘

SYSTEM INTEGRATION TESTS:
───────────────────────────────────────────────────────────────
Test 1: E-commerce ↔ VNPay
        "Order payment is correctly processed via VNPay"
        - Send payment request
        - Receive payment response
        - Handle success/failure scenarios

Test 2: E-commerce ↔ GHN (Shipping)
        "Order is correctly submitted to shipping partner"
        - Send order details
        - Receive shipping tracking number
        - Handle delivery status updates

Test 3: E-commerce ↔ Supplier
        "Inventory sync với supplier system"
        - Product updates received
        - Stock levels synchronized
```

---

## 6. ACCEPTANCE TESTING

### 6.1. Định Nghĩa

> **Acceptance Testing** xác nhận rằng hệ thống **đáp ứng business requirements** và sẵn sàng để **deploy** cho users.

```
╔═══════════════════════════════════════════════════════════════╗
║                   ACCEPTANCE TESTING                          ║
╠═══════════════════════════════════════════════════════════════╣
║                                                               ║
║  🎯 OBJECTIVES:                                               ║
║     • Establish confidence trong system quality              ║
║     • Validate system meets business needs                   ║
║     • Verify regulatory/contractual compliance               ║
║     • Enable business users to determine acceptability       ║
║                                                               ║
║  📚 TEST BASIS:                                               ║
║     • Business processes                                      ║
║     • User requirements                                       ║
║     • Regulations, contracts                                  ║
║     • Use cases từ user perspective                          ║
║     • Risk analysis reports                                   ║
║                                                               ║
║  🔍 TEST OBJECTS:                                             ║
║     • Complete system from user perspective                  ║
║     • Business processes                                      ║
║     • Forms, reports                                         ║
║     • Operational procedures                                  ║
║                                                               ║
║  👤 THƯỜNG DO AI THỰC HIỆN:                                   ║
║     • Business users / Customers                             ║
║     • Product Owner                                          ║
║     • Subject matter experts                                 ║
║                                                               ║
╚═══════════════════════════════════════════════════════════════╝
```

### 6.2. Các Loại Acceptance Testing

```
╔═══════════════════════════════════════════════════════════════╗
║            TYPES OF ACCEPTANCE TESTING                        ║
╠═══════════════════════════════════════════════════════════════╣
║                                                               ║
║  1️⃣ USER ACCEPTANCE TESTING (UAT)                             ║
║     • Do BUSINESS USERS thực hiện                            ║
║     • Verify system đáp ứng business needs                   ║
║     • Real business scenarios                                ║
║     • "Can I do my job with this system?"                    ║
║                                                               ║
║  2️⃣ OPERATIONAL ACCEPTANCE TESTING (OAT)                      ║
║     • Do OPERATIONS/SYSADMIN team thực hiện                  ║
║     • Test backup/restore                                     ║
║     • Test disaster recovery                                  ║
║     • Test system administration tasks                       ║
║     • "Can we maintain and support this system?"             ║
║                                                               ║
║  3️⃣ CONTRACTUAL ACCEPTANCE TESTING                            ║
║     • Verify contract requirements met                       ║
║     • Acceptance criteria từ contract                        ║
║     • Legal/compliance aspects                               ║
║                                                               ║
║  4️⃣ REGULATORY ACCEPTANCE TESTING                             ║
║     • Government regulations                                  ║
║     • Industry standards (PCI-DSS, HIPAA)                    ║
║     • Safety standards                                        ║
║                                                               ║
║  5️⃣ ALPHA & BETA TESTING                                      ║
║     • Alpha: Internal users at developer site               ║
║     • Beta: External users at customer site                 ║
║                                                               ║
╚═══════════════════════════════════════════════════════════════╝
```

### 6.3. Ví Dụ UAT

```
VÍ DỤ: UAT cho Inventory Management System
═══════════════════════════════════════════════════════════════

PARTICIPANTS: Warehouse Manager, Inventory Staff, Purchasing Team

UAT SCENARIO 1: Daily Inventory Check
────────────────────────────────────────────────────────────────
User: Warehouse Staff (Anh Minh)
Business Process: Morning inventory verification

Steps:
1. Login với account warehouse staff
2. Mở báo cáo "Daily Stock Report"
3. Verify stock levels match physical count
4. Update discrepancies
5. Submit report for approval

Expected:
- Report shows accurate stock levels
- Can update và submit within 15 minutes
- Manager receives notification

User Feedback: "Dễ sử dụng, nhưng cần thêm barcode scan feature"

UAT SCENARIO 2: Purchase Order Creation
────────────────────────────────────────────────────────────────
User: Purchasing Manager (Chị Lan)
Business Process: Create PO when stock low

Steps:
1. Review low stock alerts
2. Create purchase order for supplier
3. Select items, quantities, prices
4. Submit for approval
5. Send PO to supplier

Expected:
- System suggests reorder quantities
- PO format matches company standard
- Email sent to supplier automatically

User Feedback: "PASSED - Process matches our workflow"
```

### 6.4. Alpha vs Beta Testing

| Aspect | Alpha Testing | Beta Testing |
|--------|--------------|--------------|
| **Location** | Developer's site | Customer's site |
| **Testers** | Internal users, QA | External users, customers |
| **Environment** | Controlled | Real environment |
| **Support** | Developers available | Remote support |
| **Goal** | Find bugs before release | Validate in real-world |
| **Feedback** | Direct, immediate | Via feedback forms |

---

## 7. SO SÁNH CÁC TEST LEVELS

### 7.1. Summary Table

| Aspect | Component | Component Integration | System | System Integration | Acceptance |
|--------|-----------|----------------------|--------|-------------------|------------|
| **Focus** | Single unit | Component interfaces | Complete system | External interfaces | Business needs |
| **Test Basis** | Code, design | Architecture | Requirements | External APIs | Business processes |
| **Performer** | Developer | Developer/Tester | Tester | Tester | User/Customer |
| **Environment** | Dev environment | Test environment | Staging | Staging | Production-like |
| **Automation** | High | Medium-High | Medium | Medium | Low |

### 7.2. Ví Dụ Tổng Hợp: Shopee

```
SHOPEE E-COMMERCE PLATFORM - TEST LEVELS
═══════════════════════════════════════════════════════════════

1️⃣ COMPONENT TESTING (Developers)
   └── Test calculateShippingFee() function
   └── Test validatePromoCode() function
   └── Test ProductService.getDetails() method

2️⃣ COMPONENT INTEGRATION TESTING (Dev/QA)
   └── CartService ↔ ProductService integration
   └── OrderService ↔ InventoryService integration
   └── PaymentService ↔ WalletService integration

3️⃣ SYSTEM TESTING (QA Team)
   └── Complete checkout flow (cart → payment → confirmation)
   └── Search và filter functionality
   └── Performance: 10,000 concurrent users
   └── Security: Payment data encryption

4️⃣ SYSTEM INTEGRATION TESTING (QA Team)
   └── Shopee ↔ VNPay/MoMo payment gateways
   └── Shopee ↔ GHN/GHTK shipping partners
   └── Shopee ↔ Seller Center external API

5️⃣ ACCEPTANCE TESTING (Business Users)
   └── UAT: Sellers test product listing flow
   └── UAT: Buyers test purchase experience
   └── OAT: Ops team tests admin console
   └── Beta: 1000 users test new features
```

---

## 8. CÂU HỎI ÔN TẬP

### Câu 1 (K2)
Test level nào focus vào interfaces giữa components?

A. Component testing
B. Component integration testing
C. System testing
D. Acceptance testing

<details>
<summary>Đáp án</summary>

**B. Component integration testing**

Giải thích: Component integration testing focus vào interfaces và interactions giữa các components.
</details>

---

### Câu 2 (K1)
Ai thường thực hiện User Acceptance Testing (UAT)?

A. Developers
B. QA testers
C. Business users / Customers
D. Database administrators

<details>
<summary>Đáp án</summary>

**C. Business users / Customers**

Giải thích: UAT do business users thực hiện để verify system đáp ứng business needs.
</details>

---

### Câu 3 (K2)
Component testing khác với System testing ở điểm nào chính?

A. Component testing do testers thực hiện
B. Component testing test từng unit riêng lẻ, System testing test toàn bộ hệ thống
C. System testing không cần test environment
D. Component testing tìm được nhiều bugs hơn

<details>
<summary>Đáp án</summary>

**B. Component testing test từng unit riêng lẻ, System testing test toàn bộ hệ thống**

Giải thích: Component (unit) testing test isolated units, System testing test complete integrated system.
</details>

---

### Câu 4 (K1)
Test basis cho System testing là gì?

A. Source code
B. Component design
C. System requirements và user stories
D. API specifications

<details>
<summary>Đáp án</summary>

**C. System requirements và user stories**

Giải thích: System testing dựa vào requirements/user stories để verify system behavior.
</details>

---

### Câu 5 (K2)
Operational Acceptance Testing (OAT) focus vào gì?

A. User interface usability
B. Business process validation
C. Backup, recovery, và system administration
D. Payment processing

<details>
<summary>Đáp án</summary>

**C. Backup, recovery, và system administration**

Giải thích: OAT do operations team thực hiện, focus vào maintainability, backup/restore, disaster recovery.
</details>

---

## 9. CHECKLIST TỰ ĐÁNH GIÁ

Đánh dấu ✅ khi bạn đã hiểu:

- [ ] Phân biệt được 5 test levels
- [ ] Nêu được objectives của mỗi test level
- [ ] Xác định được test basis cho mỗi level
- [ ] Biết ai thường thực hiện mỗi test level
- [ ] Hiểu được các integration strategies (Big Bang, Top-down, Bottom-up)
- [ ] Phân biệt được các loại acceptance testing (UAT, OAT, Alpha, Beta)
- [ ] Có thể áp dụng test levels cho một project thực tế

---

**Tiếp theo**: [Module 3.3: Test Types](./module-3.3-test-types.md)

---

**Version**: 1.0.0
**Last Updated**: November 2025
