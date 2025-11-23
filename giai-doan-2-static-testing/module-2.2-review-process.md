# MODULE 2.2: REVIEW PROCESS (QUY TRÌNH REVIEW)

**Thời lượng**: 3-4 giờ | **Độ khó**: ⭐⭐

---

## MỤC TIÊU HỌC TẬP (Learning Objectives)

Sau khi hoàn thành module này, bạn sẽ:

| ID | Mục tiêu | Level |
|----|----------|-------|
| FL-3.2.1 | Xác định các hoạt động trong review process | K1 |
| FL-3.2.2 | Nhận biết các vai trò trong review | K1 |
| FL-3.2.3 | Phân biệt các loại reviews khác nhau | K2 |
| FL-3.2.4 | Áp dụng review techniques | K2 |
| FL-3.2.5 | Giải thích các success factors của reviews | K2 |

---

## 1. REVIEW PROCESS LÀ GÌ?

### 1.1. Định Nghĩa

> **Review** là một loại static testing trong đó **con người** kiểm tra các work products để tìm defects. Review có thể **formal** (có process rõ ràng) hoặc **informal** (không formal).

```
REVIEW = Kiểm tra work products bởi con người
         ↓
         Có thể áp dụng cho BẤT KỲ work product nào:
         • Requirements
         • Designs
         • Code
         • Test cases
         • User manuals
```

### 1.2. Mục Đích Của Review

```
╔══════════════════════════════════════════════════════════════╗
║               MỤC ĐÍCH CỦA REVIEW                            ║
╠══════════════════════════════════════════════════════════════╣
║                                                              ║
║  🔍 TÌM DEFECTS                                              ║
║     → Phát hiện lỗi, thiếu sót trong work products          ║
║                                                              ║
║  📈 CẢI THIỆN CHẤT LƯỢNG                                     ║
║     → Nâng cao chất lượng của work products                 ║
║                                                              ║
║  📚 CHIA SẺ KIẾN THỨC                                        ║
║     → Reviewers học từ work product                         ║
║     → Author học từ feedback                                 ║
║                                                              ║
║  ✅ ĐẠT ĐƯỢC CONSENSUS                                       ║
║     → Thống nhất về approach, decisions                     ║
║                                                              ║
║  📏 ĐẢM BẢO TUÂN THỦ                                         ║
║     → Verify theo standards, guidelines                      ║
║                                                              ║
╚══════════════════════════════════════════════════════════════╝
```

---

## 2. CÁC HOẠT ĐỘNG TRONG REVIEW PROCESS

### 2.1. Tổng Quan Review Process

```
┌───────────────────────────────────────────────────────────────┐
│                    REVIEW PROCESS                              │
└───────────────────────────────────────────────────────────────┘
                              │
    ┌─────────────────────────┼─────────────────────────┐
    │                         │                         │
    ▼                         ▼                         ▼
┌────────┐              ┌────────────┐             ┌────────┐
│   1.   │              │     2.     │             │   3.   │
│Planning│─────────────→│  Initiate  │────────────→│Individual│
│        │              │   Review   │             │ Review │
└────────┘              └────────────┘             └────────┘
                                                       │
                              ┌─────────────────────────┘
                              │
                              ▼
                    ┌──────────────────┐
                    │        4.        │
                    │ Issue Communication│
                    │   and Analysis   │
                    └──────────────────┘
                              │
                              ▼
                    ┌──────────────────┐
                    │        5.        │
                    │ Fixing and       │
                    │ Reporting        │
                    └──────────────────┘
```

### 2.2. Chi Tiết Từng Hoạt Động

#### 2.2.1. Planning (Lập Kế Hoạch)

```
╔══════════════════════════════════════════════════════════════╗
║  ACTIVITY 1: PLANNING                                        ║
╠══════════════════════════════════════════════════════════════╣
║                                                              ║
║  📋 CÁC CÔNG VIỆC:                                           ║
║                                                              ║
║  1. Định nghĩa SCOPE                                         ║
║     → Work product nào sẽ được review?                       ║
║     → Review toàn bộ hay chỉ một phần?                       ║
║                                                              ║
║  2. Xác định OBJECTIVES                                      ║
║     → Tìm defects? Đảm bảo compliance?                       ║
║     → Check theo checklist nào?                              ║
║                                                              ║
║  3. Chọn REVIEW TYPE                                         ║
║     → Informal? Walkthrough? Technical? Inspection?          ║
║                                                              ║
║  4. Chỉ định NGƯỜI THAM GIA                                  ║
║     → Ai sẽ review? Cần bao nhiêu reviewers?                ║
║     → Ai là moderator, scribe?                               ║
║                                                              ║
║  5. Xác định ENTRY và EXIT CRITERIA                          ║
║     → Khi nào bắt đầu review?                                ║
║     → Khi nào hoàn thành review?                             ║
║                                                              ║
║  6. Lên LỊCH                                                 ║
║     → Deadline cho individual review                         ║
║     → Thời gian review meeting                               ║
║                                                              ║
╚══════════════════════════════════════════════════════════════╝
```

**Ví dụ Planning:**

```
REVIEW PLAN: Requirements Document cho VNPay Transfer Feature
─────────────────────────────────────────────────────────────
Scope:           REQ-TRANSFER-001 đến REQ-TRANSFER-015
Objectives:      Tìm defects, verify completeness
Review Type:     Formal Inspection
Participants:
  - Author: BA Team Lead
  - Moderator: QA Manager
  - Reviewers: Senior Tester, Tech Lead, Product Owner
  - Scribe: Junior BA
Entry Criteria:  Requirements document completed (v1.0)
Exit Criteria:   All Critical/Major issues resolved
Schedule:
  - Distribute: Nov 20
  - Individual Review: Nov 20-22
  - Review Meeting: Nov 23, 10:00 AM
  - Fixing deadline: Nov 25
```

#### 2.2.2. Review Initiation (Khởi Động Review)

```
╔══════════════════════════════════════════════════════════════╗
║  ACTIVITY 2: REVIEW INITIATION                               ║
╠══════════════════════════════════════════════════════════════╣
║                                                              ║
║  📋 CÁC CÔNG VIỆC:                                           ║
║                                                              ║
║  1. PHÂN PHỐI work products                                  ║
║     → Gửi documents cho tất cả reviewers                    ║
║     → Include checklists, review guidelines                  ║
║                                                              ║
║  2. GIẢI THÍCH scope và objectives                           ║
║     → Làm rõ mục tiêu review                                 ║
║     → Focus areas                                            ║
║                                                              ║
║  3. TRẢ LỜI câu hỏi của reviewers                           ║
║     → Clarify ambiguities                                    ║
║     → Provide context                                        ║
║                                                              ║
╚══════════════════════════════════════════════════════════════╝
```

**Ví dụ Email Khởi Động Review:**

```
Subject: [REVIEW] Requirements Review - VNPay Transfer Feature

Xin chào team,

Mời các bạn tham gia review Requirements Document cho tính năng
Transfer của VNPay.

📎 Attachments:
- REQ-VNPay-Transfer-v1.0.pdf
- Review-Checklist-Requirements.xlsx

📅 Timeline:
- Individual Review: 20-22/11 (3 ngày)
- Review Meeting: 23/11, 10:00 AM, Phòng Meeting A

🎯 Focus areas:
- Completeness: Đủ requirements cho all scenarios?
- Clarity: Requirements có clear và testable?
- Consistency: Có mâu thuẫn giữa requirements?

Please ghi nhận findings vào file Review-Findings-Template.xlsx
và gửi lại trước meeting.

Thanks,
QA Manager
```

#### 2.2.3. Individual Review (Review Cá Nhân)

```
╔══════════════════════════════════════════════════════════════╗
║  ACTIVITY 3: INDIVIDUAL REVIEW                               ║
╠══════════════════════════════════════════════════════════════╣
║                                                              ║
║  📋 CÁC CÔNG VIỆC:                                           ║
║                                                              ║
║  1. MỖI REVIEWER đọc work product INDEPENDENTLY              ║
║     → Không discuss với người khác                           ║
║     → Tránh bias từ ý kiến người khác                       ║
║                                                              ║
║  2. GHI NHẬN potential defects                               ║
║     → Sử dụng checklist                                      ║
║     → Note location, description, severity                   ║
║                                                              ║
║  3. ĐẶT CÂU HỎI                                              ║
║     → Points of confusion                                    ║
║     → Questions for author                                   ║
║                                                              ║
║  4. SUGGESTIONS cho improvements                             ║
║     → Best practices                                         ║
║     → Alternative approaches                                 ║
║                                                              ║
╚══════════════════════════════════════════════════════════════╝
```

**Ví dụ Individual Review Findings:**

```
REVIEW FINDINGS - Senior Tester
Document: REQ-VNPay-Transfer-v1.0
Date: 22/11/2024
─────────────────────────────────────────────────────────────

Finding #1
Location:     REQ-TRANSFER-003
Type:         Defect - Ambiguity
Severity:     Major
Description:  "Transfer should complete quickly"
              → Không rõ "quickly" là bao nhiêu giây?
Suggestion:   "Transfer should complete within 3 seconds"

Finding #2
Location:     REQ-TRANSFER-007
Type:         Defect - Missing
Severity:     Critical
Description:  Thiếu requirement về OTP verification
              cho transfers > 10 million VND
Suggestion:   Add security requirement for OTP

Finding #3
Location:     REQ-TRANSFER-010, REQ-TRANSFER-012
Type:         Defect - Inconsistency
Severity:     Major
Description:  REQ-010 says "max 500M/transaction"
              REQ-012 says "max 1B/transaction"
              → Mâu thuẫn về max amount
Suggestion:   Confirm với Product Owner

Finding #4
Location:     General
Type:         Question
Description:  Có support international transfers không?
              Document chỉ mention domestic transfers.
```

#### 2.2.4. Issue Communication and Analysis

```
╔══════════════════════════════════════════════════════════════╗
║  ACTIVITY 4: ISSUE COMMUNICATION AND ANALYSIS                ║
╠══════════════════════════════════════════════════════════════╣
║                                                              ║
║  📋 CÁC CÔNG VIỆC:                                           ║
║                                                              ║
║  1. COMMUNICATE findings                                     ║
║     → Review meeting (formal reviews)                        ║
║     → Email/chat (informal reviews)                          ║
║                                                              ║
║  2. ANALYZE potential defects                                ║
║     → Xác nhận đó có phải defect hay không                  ║
║     → Assign severity/priority                               ║
║                                                              ║
║  3. DECIDE actions                                           ║
║     → Accept finding → Author fix                            ║
║     → Reject finding → Not a defect                          ║
║     → Defer → Fix later                                      ║
║                                                              ║
║  4. ASSIGN ownership                                         ║
║     → Ai sẽ fix defect nào?                                 ║
║     → Deadline?                                              ║
║                                                              ║
╚══════════════════════════════════════════════════════════════╝
```

**Ví dụ Review Meeting Minutes:**

```
REVIEW MEETING MINUTES
─────────────────────────────────────────────────────────────
Date:         23/11/2024, 10:00 - 11:30 AM
Participants: BA Team Lead (Author), QA Manager (Moderator),
              Senior Tester, Tech Lead, Product Owner,
              Junior BA (Scribe)
Document:     REQ-VNPay-Transfer-v1.0

FINDINGS DISCUSSED:
─────────────────────────────────────────────────────────────
#  | Finding              | Decision   | Owner    | Deadline
───|──────────────────────|────────────|──────────|──────────
1  | Ambiguity "quickly"  | ACCEPT     | BA Lead  | 24/11
2  | Missing OTP req      | ACCEPT     | BA Lead  | 24/11
3  | Inconsistent max     | ACCEPT     | BA Lead  | 24/11
   | (Confirm: 500M)      |            |          |
4  | International?       | DEFER      | PM       | Next ver

SUMMARY:
- Total findings: 12
- Accepted: 9
- Rejected: 1 (Not a defect)
- Deferred: 2

DECISION: Re-review required after fixes (Focus on Critical/Major)

Next Steps:
- Author fixes by 24/11
- Reviewers verify fixes by 25/11
- Final approval: 26/11
```

#### 2.2.5. Fixing and Reporting

```
╔══════════════════════════════════════════════════════════════╗
║  ACTIVITY 5: FIXING AND REPORTING                            ║
╠══════════════════════════════════════════════════════════════╣
║                                                              ║
║  📋 CÁC CÔNG VIỆC:                                           ║
║                                                              ║
║  1. AUTHOR FIXES defects                                     ║
║     → Sửa theo decisions từ review meeting                  ║
║     → Track fixes in defect tracking tool                   ║
║                                                              ║
║  2. COMMUNICATE fixes                                        ║
║     → Gửi updated work product                              ║
║     → Explain changes made                                   ║
║                                                              ║
║  3. REPORT review results                                    ║
║     → Review summary report                                  ║
║     → Metrics: defects found, time spent                     ║
║                                                              ║
║  4. OPTIONAL: Re-review                                      ║
║     → Verify fixes (for formal reviews)                      ║
║     → Confirm exit criteria met                              ║
║                                                              ║
╚══════════════════════════════════════════════════════════════╝
```

**Ví dụ Review Summary Report:**

```
╔══════════════════════════════════════════════════════════════╗
║                 REVIEW SUMMARY REPORT                        ║
╠══════════════════════════════════════════════════════════════╣
║                                                              ║
║  Document:     REQ-VNPay-Transfer-v1.0                       ║
║  Review Type:  Formal Inspection                             ║
║  Date:         20-26/11/2024                                 ║
║                                                              ║
║  ───────────────────────────────────────────────────────     ║
║  EFFORT SUMMARY                                              ║
║  ───────────────────────────────────────────────────────     ║
║  Planning:                2 hours                            ║
║  Individual Review:       8 hours (4 reviewers × 2h)         ║
║  Review Meeting:          1.5 hours                          ║
║  Fixing:                  3 hours                            ║
║  Re-review:               1 hour                             ║
║  TOTAL EFFORT:            15.5 hours                         ║
║                                                              ║
║  ───────────────────────────────────────────────────────     ║
║  DEFECTS SUMMARY                                             ║
║  ───────────────────────────────────────────────────────     ║
║  │ Severity │ Found │ Fixed │ Deferred │                    ║
║  │──────────│───────│───────│──────────│                    ║
║  │ Critical │   2   │   2   │    0     │                    ║
║  │ Major    │   5   │   5   │    0     │                    ║
║  │ Minor    │   3   │   2   │    1     │                    ║
║  │ Total    │  10   │   9   │    1     │                    ║
║                                                              ║
║  ───────────────────────────────────────────────────────     ║
║  DEFECT DENSITY                                              ║
║  ───────────────────────────────────────────────────────     ║
║  Document Size:           15 requirements (8 pages)          ║
║  Defects per requirement: 0.67                               ║
║  Defects per page:        1.25                               ║
║                                                              ║
║  ───────────────────────────────────────────────────────     ║
║  CONCLUSION                                                  ║
║  ───────────────────────────────────────────────────────     ║
║  Exit Criteria:           MET ✅                              ║
║  Document Status:         APPROVED for Development           ║
║                                                              ║
╚══════════════════════════════════════════════════════════════╝
```

---

## 3. CÁC VAI TRÒ TRONG REVIEW

### 3.1. Danh Sách Vai Trò

```
╔══════════════════════════════════════════════════════════════╗
║                    ROLES IN REVIEWS                          ║
╠══════════════════════════════════════════════════════════════╣
║                                                              ║
║  👤 MANAGER                                                  ║
║     → Quyết định thực hiện review                           ║
║     → Cấp resources (time, people)                          ║
║     → May or may not participate                            ║
║                                                              ║
║  ✍️ AUTHOR                                                   ║
║     → Người tạo work product                                ║
║     → Giải thích work product                               ║
║     → Fix defects sau review                                ║
║                                                              ║
║  🎯 MODERATOR (Facilitator)                                  ║
║     → Lead review meeting                                    ║
║     → Đảm bảo review process được tuân thủ                  ║
║     → Mediate giữa các participants                         ║
║     → Quan trọng nhất trong formal reviews                  ║
║                                                              ║
║  📝 SCRIBE (Recorder)                                        ║
║     → Ghi chép defects và decisions                         ║
║     → Document review meeting minutes                        ║
║                                                              ║
║  🔍 REVIEWER                                                 ║
║     → Đọc và kiểm tra work product                          ║
║     → Identify defects, questions, suggestions              ║
║     → Có thể là nhiều người                                 ║
║                                                              ║
║  📊 REVIEW LEADER                                            ║
║     → Organize và coordinate review                         ║
║     → Assign roles                                           ║
║     → Track progress                                         ║
║     → Có thể cùng với Moderator                             ║
║                                                              ║
╚══════════════════════════════════════════════════════════════╝
```

### 3.2. Vai Trò Trong Các Loại Review

| Vai trò | Informal | Walkthrough | Technical | Inspection |
|---------|----------|-------------|-----------|------------|
| Manager | Optional | Optional | Optional | Usually |
| Author | ✅ | ✅ (leads) | ✅ | ✅ |
| Moderator | ❌ | Optional | Optional | ✅ (required) |
| Scribe | ❌ | Optional | Optional | ✅ (required) |
| Reviewer | ✅ (1-2) | ✅ (team) | ✅ (experts) | ✅ (trained) |
| Review Leader | ❌ | Optional | Optional | ✅ (required) |

### 3.3. Ví Dụ Thực Tế

**Scenario: Code Review cho Payment Module**

```
FORMAL CODE REVIEW - Payment Module
────────────────────────────────────────────────────────────

👤 MANAGER: Engineering Manager
   → Approved 4 hours for review process
   → Không tham gia trực tiếp

✍️ AUTHOR: Junior Developer (Nguyen Van A)
   → Viết PaymentService.java
   → Giải thích implementation choices
   → Fix issues sau review

🎯 MODERATOR: Senior QA Lead (Tran Thi B)
   → Facilitate review meeting
   → Ensure everyone has chance to speak
   → Keep discussion on track

📝 SCRIBE: Another QA Engineer (Le Van C)
   → Record all findings
   → Document decisions
   → Create review report

🔍 REVIEWERS:
   → Senior Developer (Pham Van D) - Check code quality
   → Security Expert (Hoang E) - Check security issues
   → Tester (Nguyen F) - Check testability

📊 REVIEW LEADER: Tech Lead (Vo Van G)
   → Organized review schedule
   → Assigned reviewers
   → Will track fixes to completion
```

---

## 4. CÁC LOẠI REVIEW

### 4.1. Tổng Quan

```
FORMALITY SPECTRUM
────────────────────────────────────────────────────────────────

Less Formal ◄──────────────────────────────────► More Formal

┌──────────┐   ┌────────────┐   ┌──────────┐   ┌───────────┐
│ Informal │   │ Walkthrough│   │ Technical│   │ Inspection│
│  Review  │   │            │   │  Review  │   │           │
└──────────┘   └────────────┘   └──────────┘   └───────────┘
     │               │               │               │
     ▼               ▼               ▼               ▼
 Buddy check    Author-led     Expert-led      Defined process
 No meeting     Scenarios      Technical focus  Metrics collected
 Quick          Educational    Quality focus    Most effective
```

### 4.2. Informal Review

```
╔══════════════════════════════════════════════════════════════╗
║                    INFORMAL REVIEW                           ║
╠══════════════════════════════════════════════════════════════╣
║                                                              ║
║  📝 ĐẶC ĐIỂM:                                                ║
║     • Không có formal process                                ║
║     • Buddy check, peer review                               ║
║     • Nhanh, lightweight                                     ║
║     • Có thể không có meeting                               ║
║                                                              ║
║  🎯 MỤC ĐÍCH:                                                ║
║     • Quick feedback                                         ║
║     • Find obvious defects                                   ║
║     • Get a second opinion                                   ║
║                                                              ║
║  👥 PARTICIPANTS:                                            ║
║     • Author + 1-2 colleagues                                ║
║     • No formal roles                                        ║
║                                                              ║
║  📊 DOCUMENTATION:                                           ║
║     • Minimal or none                                        ║
║     • Maybe just comments in PR                              ║
║                                                              ║
║  💡 VÍ DỤ:                                                   ║
║     "Hey, can you look at this code before I commit?"        ║
║     → Developer nhờ đồng nghiệp review code trên máy        ║
║                                                              ║
╚══════════════════════════════════════════════════════════════╝
```

**Ví dụ Informal Review:**

```
SCENARIO: Developer Review Pull Request
────────────────────────────────────────────────────────────

Developer A: "Hey B, can you review my PR for the login feature?"

Developer B checks PR on GitHub:
- Reads through 5 files changed
- Leaves inline comments:

  Comment 1 (line 45):
  "Consider using bcrypt instead of MD5 for password hashing"

  Comment 2 (line 78):
  "Missing null check here, could cause NPE"

  Comment 3 (line 92):
  "Looks good! 👍"

Developer A fixes issues and merges.

Total time: 15 minutes
No formal documentation created
```

### 4.3. Walkthrough

```
╔══════════════════════════════════════════════════════════════╗
║                      WALKTHROUGH                             ║
╠══════════════════════════════════════════════════════════════╣
║                                                              ║
║  📝 ĐẶC ĐIỂM:                                                ║
║     • AUTHOR LEADS the review                                ║
║     • Author "walks through" work product                    ║
║     • Scenarios, dry runs                                    ║
║     • Focus on learning và consensus                        ║
║                                                              ║
║  🎯 MỤC ĐÍCH:                                                ║
║     • Share knowledge với team                              ║
║     • Get feedback trên approach                            ║
║     • Train team members                                     ║
║     • Find defects (secondary)                              ║
║                                                              ║
║  👥 PARTICIPANTS:                                            ║
║     • Author leads                                           ║
║     • Team members                                           ║
║     • Scribe (optional)                                      ║
║                                                              ║
║  📊 DOCUMENTATION:                                           ║
║     • May have meeting notes                                 ║
║     • Action items list                                      ║
║                                                              ║
║  💡 VÍ DỤ:                                                   ║
║     Designer walks through UI mockups với team              ║
║     BA explains user stories                                 ║
║     Developer presents architecture decision                 ║
║                                                              ║
╚══════════════════════════════════════════════════════════════╝
```

**Ví dụ Walkthrough:**

```
SCENARIO: UI Design Walkthrough
────────────────────────────────────────────────────────────

Meeting: Design Walkthrough - E-commerce Checkout Flow
Duration: 45 minutes
Participants: UI Designer (Author), PM, Dev Lead, QA Lead

UI Designer: "Let me walk you through the new checkout design..."

[Screen 1: Cart Review]
Designer: "User sees cart summary here. They can update quantity
          or remove items. Total is shown at bottom."
PM: "What happens if an item goes out of stock while they're here?"
Designer: "Good question, I'll add a notification for that."

[Screen 2: Shipping Address]
Designer: "User selects or adds shipping address..."
Dev Lead: "Can we pre-fill from their profile?"
Designer: "Yes, that's the plan."

[Screen 3: Payment]
QA Lead: "What error message shows if card is declined?"
Designer: "I haven't designed that state yet. Let me add it."

Action Items:
1. Add out-of-stock notification - Designer - Nov 24
2. Add payment error states - Designer - Nov 24
3. Confirm address pre-fill logic - Dev Lead - Nov 25
```

### 4.4. Technical Review

```
╔══════════════════════════════════════════════════════════════╗
║                    TECHNICAL REVIEW                          ║
╠══════════════════════════════════════════════════════════════╣
║                                                              ║
║  📝 ĐẶC ĐIỂM:                                                ║
║     • Led by TECHNICAL EXPERTS                               ║
║     • Focus on technical correctness                         ║
║     • May or may not have author present                    ║
║     • More formal than walkthrough                          ║
║                                                              ║
║  🎯 MỤC ĐÍCH:                                                ║
║     • Evaluate technical quality                             ║
║     • Check conformance to standards                         ║
║     • Make technical decisions                               ║
║     • Find technical defects                                 ║
║                                                              ║
║  👥 PARTICIPANTS:                                            ║
║     • Technical experts (required)                           ║
║     • Author (optional - depends)                            ║
║     • Moderator (optional)                                   ║
║                                                              ║
║  📊 DOCUMENTATION:                                           ║
║     • Technical findings                                     ║
║     • Recommendations                                        ║
║     • May include metrics                                    ║
║                                                              ║
║  💡 VÍ DỤ:                                                   ║
║     Architecture review                                      ║
║     Security review                                          ║
║     Performance review                                       ║
║     Code review by senior developers                        ║
║                                                              ║
╚══════════════════════════════════════════════════════════════╝
```

**Ví dụ Technical Review:**

```
SCENARIO: Architecture Review for Microservices Migration
────────────────────────────────────────────────────────────

Meeting: Architecture Review
Duration: 2 hours
Participants:
  - Solution Architect (Expert, leads review)
  - Senior Backend Dev (Expert)
  - DevOps Engineer (Expert)
  - System Designer (Author - optional attendance)

AGENDA:
1. Review proposed microservices architecture
2. Evaluate technology choices
3. Assess scalability và security
4. Identify risks

REVIEW FINDINGS:

Finding 1 - CRITICAL
Component: Service-to-Service Communication
Issue: Synchronous HTTP calls between services will cause
       cascading failures
Recommendation: Implement message queue (RabbitMQ/Kafka)
                for async communication

Finding 2 - MAJOR
Component: Database Design
Issue: Single database for all services defeats microservices purpose
Recommendation: Database per service pattern

Finding 3 - MAJOR
Component: API Gateway
Issue: No rate limiting designed
Recommendation: Add rate limiting to prevent DDoS

Finding 4 - MINOR
Component: Logging
Issue: No centralized logging strategy
Recommendation: Implement ELK stack

DECISION: Architecture needs revision before development starts
```

### 4.5. Inspection (Fagan Inspection)

```
╔══════════════════════════════════════════════════════════════╗
║                      INSPECTION                              ║
╠══════════════════════════════════════════════════════════════╣
║                                                              ║
║  📝 ĐẶC ĐIỂM:                                                ║
║     • MOST FORMAL review type                                ║
║     • Defined process với rules                              ║
║     • Trained participants                                   ║
║     • METRICS collected và analyzed                          ║
║     • Most effective at finding defects                      ║
║                                                              ║
║  🎯 MỤC ĐÍCH:                                                ║
║     • Maximize defect detection                              ║
║     • Process improvement (using metrics)                    ║
║     • Ensure quality standards                               ║
║                                                              ║
║  👥 PARTICIPANTS (Required roles):                           ║
║     • Moderator (leads, keeps process)                       ║
║     • Author (explains, answers questions)                   ║
║     • Reviewers (examine, find defects)                      ║
║     • Scribe (records findings)                              ║
║     • Review Leader (organizes)                              ║
║                                                              ║
║  📊 DOCUMENTATION (Required):                                ║
║     • Review plan                                            ║
║     • Individual review logs                                 ║
║     • Meeting minutes                                        ║
║     • Defect log                                             ║
║     • Review metrics report                                  ║
║                                                              ║
║  📈 METRICS COLLECTED:                                       ║
║     • Preparation time                                       ║
║     • Meeting time                                           ║
║     • Defects found                                          ║
║     • Defect density                                         ║
║     • Review rate (pages/hour)                               ║
║                                                              ║
╚══════════════════════════════════════════════════════════════╝
```

### 4.6. So Sánh Các Loại Review

| Tiêu chí | Informal | Walkthrough | Technical | Inspection |
|----------|----------|-------------|-----------|------------|
| **Formality** | Thấp nhất | Thấp-TB | TB-Cao | Cao nhất |
| **Leader** | Không có | Author | Expert | Moderator |
| **Process** | Không | Flexible | Defined | Strict |
| **Documentation** | Không/Ít | Optional | Có | Required |
| **Metrics** | Không | Không | Optional | Required |
| **Training** | Không | Không | Optional | Required |
| **Defect detection** | Thấp | TB | Cao | Cao nhất |
| **Cost** | Thấp | Thấp | TB | Cao |
| **Best for** | Quick check | Knowledge sharing | Tech decisions | Critical docs |

---

## 5. REVIEW TECHNIQUES

### 5.1. Ad hoc Review

```
TECHNIQUE: AD HOC
─────────────────────────────────────────────────────────────
Cách làm:    Reviewer đọc work product và tự tìm defects
             Không có guidance cụ thể

Ưu điểm:     Quick, easy, no preparation needed

Nhược điểm:  Depends on reviewer's experience
             May miss specific types of defects
             Inconsistent coverage

Best for:    Informal reviews, quick checks
```

### 5.2. Checklist-Based Review

```
TECHNIQUE: CHECKLIST-BASED
─────────────────────────────────────────────────────────────
Cách làm:    Reviewer sử dụng checklist để systematic check
             Checklist contains items to verify

Ưu điểm:     Consistent coverage
             Easy for beginners
             Can capture organizational knowledge

Nhược điểm:  May miss defects not on checklist
             Checklist needs maintenance

Best for:    Formal reviews, compliance checks
```

**Ví dụ Requirements Review Checklist:**

```
REQUIREMENTS REVIEW CHECKLIST
─────────────────────────────────────────────────────────────
Category: Completeness
□ All functional requirements defined?
□ All non-functional requirements defined?
□ Error handling specified?
□ Edge cases covered?

Category: Clarity
□ Each requirement is unambiguous?
□ Each requirement is testable?
□ Technical jargon explained?
□ Acronyms defined?

Category: Consistency
□ No contradictions between requirements?
□ Terminology used consistently?
□ Numbering/format consistent?

Category: Correctness
□ Requirements align with business needs?
□ Calculations/formulas correct?
□ References to other docs accurate?

Category: Traceability
□ Each requirement has unique ID?
□ Source/origin documented?
□ Dependencies identified?
```

### 5.3. Scenario-Based Review

```
TECHNIQUE: SCENARIO-BASED
─────────────────────────────────────────────────────────────
Cách làm:    Reviewer "dry runs" scenarios through work product
             Check if work product supports each scenario

Ưu điểm:     Tests real-world usage
             Good for finding missing requirements

Nhược điểm:  Scenarios may not cover everything

Best for:    Requirements reviews, design reviews
```

**Ví dụ Scenario-Based Review:**

```
SCENARIOS FOR CHECKOUT REQUIREMENTS REVIEW
─────────────────────────────────────────────────────────────

Scenario 1: Happy Path
"User adds item to cart, proceeds to checkout, pays with credit card"
→ Walk through requirements... All steps covered? ✓

Scenario 2: Out of Stock
"User tries to checkout but item becomes out of stock"
→ Walk through requirements... Handling defined? ❌ MISSING

Scenario 3: Payment Fails
"User submits payment but card is declined"
→ Walk through requirements... Error message defined? ❌ AMBIGUOUS

Scenario 4: Session Timeout
"User is in checkout but session times out"
→ Walk through requirements... Not covered? ❌ MISSING

FINDINGS: 3 scenarios reveal gaps in requirements
```

### 5.4. Role-Based Review

```
TECHNIQUE: ROLE-BASED (Perspective-Based)
─────────────────────────────────────────────────────────────
Cách làm:    Mỗi reviewer đọc từ perspective của một role
             (User, Developer, Tester, Administrator, etc.)

Ưu điểm:     Different perspectives find different defects
             Broader coverage

Nhược điểm:  Requires clear role definition
             Some overlap possible

Best for:    Requirements reviews với multiple stakeholders
```

**Ví dụ Role-Based Review:**

```
ROLE-BASED REVIEW ASSIGNMENTS
─────────────────────────────────────────────────────────────

Document: Mobile Banking App Requirements

Reviewer 1 - AS END USER:
→ Focus: Usability, user experience, user-friendly messages
→ Questions to ask:
  - Can users easily understand each feature?
  - Are error messages helpful?
  - Is navigation intuitive?

Reviewer 2 - AS DEVELOPER:
→ Focus: Technical feasibility, completeness for implementation
→ Questions to ask:
  - Is this implementable?
  - Are all inputs/outputs defined?
  - What about edge cases?

Reviewer 3 - AS TESTER:
→ Focus: Testability, acceptance criteria
→ Questions to ask:
  - Can I write test cases from this?
  - Are expected results clear?
  - What test data do I need?

Reviewer 4 - AS SECURITY OFFICER:
→ Focus: Security requirements, vulnerabilities
→ Questions to ask:
  - Are authentication requirements clear?
  - How is sensitive data protected?
  - What about audit logging?
```

---

## 6. SUCCESS FACTORS CHO REVIEWS

### 6.1. Các Yếu Tố Thành Công

```
╔══════════════════════════════════════════════════════════════╗
║               SUCCESS FACTORS FOR REVIEWS                    ║
╠══════════════════════════════════════════════════════════════╣
║                                                              ║
║  📋 ORGANIZATIONAL FACTORS:                                  ║
║     ✓ Management support và commitment                      ║
║     ✓ Reviews integrated into SDLC                          ║
║     ✓ Adequate time và resources allocated                  ║
║     ✓ Culture that values quality                           ║
║                                                              ║
║  🎯 REVIEW PROCESS FACTORS:                                  ║
║     ✓ Clear objectives defined                               ║
║     ✓ Right review type selected                             ║
║     ✓ Appropriate checklists used                            ║
║     ✓ Entry và exit criteria defined                        ║
║     ✓ Findings properly tracked                              ║
║                                                              ║
║  👥 PEOPLE FACTORS:                                          ║
║     ✓ Right people involved (skills, perspectives)           ║
║     ✓ Adequate preparation time given                        ║
║     ✓ Participants trained in review process                ║
║     ✓ Constructive, positive atmosphere                     ║
║     ✓ Focus on DEFECTS, not PEOPLE                          ║
║     ✓ Author receptive to feedback                          ║
║                                                              ║
║  📄 WORK PRODUCT FACTORS:                                    ║
║     ✓ Work product complete enough for review               ║
║     ✓ Appropriate size (not too large)                      ║
║     ✓ Distributed with enough lead time                     ║
║                                                              ║
╚══════════════════════════════════════════════════════════════╝
```

### 6.2. Common Mistakes to Avoid

```
╔══════════════════════════════════════════════════════════════╗
║             COMMON REVIEW MISTAKES                           ║
╠══════════════════════════════════════════════════════════════╣
║                                                              ║
║  ❌ MISTAKE: Criticizing the AUTHOR instead of the WORK     ║
║     → "You always make this mistake"                         ║
║     ✓ FIX: "This logic has an issue..."                     ║
║                                                              ║
║  ❌ MISTAKE: Không đủ preparation time                       ║
║     → Reviewers skim-read in meeting                        ║
║     ✓ FIX: Give at least 2-3 days for individual review     ║
║                                                              ║
║  ❌ MISTAKE: Review document quá lớn                         ║
║     → 100-page document in one review                       ║
║     ✓ FIX: Break into smaller chunks                        ║
║                                                              ║
║  ❌ MISTAKE: No clear objectives                             ║
║     → Reviewers don't know what to focus on                 ║
║     ✓ FIX: Define specific review objectives                ║
║                                                              ║
║  ❌ MISTAKE: Không track fixes                               ║
║     → Defects found but never fixed                         ║
║     ✓ FIX: Track defects in tool, verify fixes             ║
║                                                              ║
║  ❌ MISTAKE: Wrong people involved                           ║
║     → No technical expert in architecture review            ║
║     ✓ FIX: Match reviewers to work product type            ║
║                                                              ║
╚══════════════════════════════════════════════════════════════╝
```

---

## 7. CÂU HỎI ÔN TẬP

### Câu 1 (K1)
Trong review process, ai là người FIX defects?

A. Moderator
B. Reviewer
C. Author
D. Scribe

<details>
<summary>Đáp án</summary>

**C. Author**

Giải thích: Author là người tạo work product, nên họ responsible cho việc fix defects sau review.
</details>

---

### Câu 2 (K1)
Loại review nào có formality level CAO NHẤT?

A. Informal review
B. Walkthrough
C. Technical review
D. Inspection

<details>
<summary>Đáp án</summary>

**D. Inspection**

Giải thích: Inspection là loại review formal nhất với defined process, required roles, và metrics collection.
</details>

---

### Câu 3 (K2)
Trong walkthrough, ai là người LEAD review meeting?

A. Moderator
B. Author
C. Review Leader
D. Senior reviewer

<details>
<summary>Đáp án</summary>

**B. Author**

Giải thích: Trong walkthrough, author leads review meeting, "walks through" work product cho team.
</details>

---

### Câu 4 (K1)
Activity nào KHÔNG thuộc review process?

A. Planning
B. Test execution
C. Individual review
D. Issue communication

<details>
<summary>Đáp án</summary>

**B. Test execution**

Giải thích: Test execution là dynamic testing. Review process bao gồm: Planning, Initiation, Individual Review, Issue Communication, Fixing & Reporting.
</details>

---

### Câu 5 (K2)
Yếu tố nào quan trọng NHẤT cho thành công của review?

A. Using expensive review tools
B. Having many reviewers
C. Focus on defects not people
D. Long review meetings

<details>
<summary>Đáp án</summary>

**C. Focus on defects not people**

Giải thích: Tạo constructive atmosphere bằng cách focus vào defects, không criticize author là success factor quan trọng.
</details>

---

### Câu 6 (K1)
Role nào responsible cho ghi chép defects trong review meeting?

A. Author
B. Moderator
C. Scribe
D. Review Leader

<details>
<summary>Đáp án</summary>

**C. Scribe**

Giải thích: Scribe (Recorder) responsible cho documenting defects và decisions trong review meeting.
</details>

---

### Câu 7 (K2)
Khi nào nên sử dụng Technical Review thay vì Walkthrough?

A. Khi cần training team members
B. Khi cần đánh giá technical quality bởi experts
C. Khi author muốn explain approach
D. Khi không có đủ thời gian

<details>
<summary>Đáp án</summary>

**B. Khi cần đánh giá technical quality bởi experts**

Giải thích:
- Technical Review: Focus on technical quality, led by experts
- Walkthrough: Focus on knowledge sharing, led by author
</details>

---

### Câu 8 (K2)
Checklist-based review technique có ưu điểm gì?

A. Không cần preparation
B. Consistent coverage của review items
C. Faster than ad hoc
D. Finds more defects than inspection

<details>
<summary>Đáp án</summary>

**B. Consistent coverage của review items**

Giải thích: Checklist giúp reviewers check systematic, không bỏ sót items quan trọng, đảm bảo consistency giữa các reviews.
</details>

---

### Câu 9 (K2)
Scenario-based review technique phù hợp nhất cho?

A. Code review
B. Test case review
C. Requirements review
D. Configuration review

<details>
<summary>Đáp án</summary>

**C. Requirements review**

Giải thích: Scenario-based review "dry runs" real-world scenarios qua requirements, giúp tìm missing requirements và gaps.
</details>

---

### Câu 10 (K2)
Điều nào KHÔNG phải success factor cho reviews?

A. Management support
B. Adequate preparation time
C. Large work products to review
D. Focus on defects not people

<details>
<summary>Đáp án</summary>

**C. Large work products to review**

Giải thích: Work products quá lớn thực ra là anti-pattern. Nên break into smaller chunks để review hiệu quả hơn.
</details>

---

## 8. CHECKLIST TỰ ĐÁNH GIÁ

Đánh dấu ✅ khi bạn đã hiểu:

- [ ] Liệt kê được 5 activities trong review process
- [ ] Mô tả được vai trò của mỗi role trong review
- [ ] Phân biệt được 4 loại reviews (Informal, Walkthrough, Technical, Inspection)
- [ ] Biết khi nào sử dụng loại review nào
- [ ] Giải thích được 4 review techniques
- [ ] Nêu được ít nhất 5 success factors cho reviews
- [ ] Có thể tham gia một review meeting hiệu quả

---

## TÀI LIỆU THAM KHẢO

- ISTQB CTFL Syllabus v4.0.1 - Chapter 3: Static Testing
- ISTQB Glossary
- Fagan, M.E. "Design and Code Inspections to Reduce Errors in Program Development"

---

**Tiếp theo**: [Bài tập Giai đoạn 2](./bai-tap-giai-doan-2.md)

---

**Version**: 1.0.0
**Last Updated**: November 2025
