# Giai Đoạn 8: Hướng Dẫn Thực Hành Tổng Hợp

## 📋 Tổng Quan

Giai đoạn 8 là **giai đoạn thực hành tổng hợp cuối cùng** trước khi bạn tham gia kỳ thi ISTQB Foundation Level. Bạn sẽ áp dụng **TẤT CẢ kiến thức** từ 7 giai đoạn trước vào 3 dự án thực tế với độ phức tạp tăng dần.

### 🎯 Mục Tiêu Học Tập

1. **Tích hợp kiến thức**: Áp dụng đồng thời nhiều kỹ thuật testing trong một dự án
2. **Tư duy thực tế**: Xử lý các tình huống phức tạp như trong công việc thực tế
3. **Kỹ năng quyết định**: Chọn kỹ thuật phù hợp cho từng tình huống
4. **Quản lý testing**: Lập kế hoạch, theo dõi, báo cáo toàn diện
5. **Chuẩn bị thi**: Làm quen với format câu hỏi và yêu cầu của ISTQB

### 📊 3 Dự Án Thực Hành

| Dự Án | Trọng Tâm | Độ Khó | Thời Gian |
|-------|-----------|--------|-----------|
| **Project 1: ShopVN** (E-commerce) | Functional Testing, Black-box Techniques | ⭐⭐⭐ | 20-25 giờ |
| **Project 2: PayVN** (Mobile Banking) | Security, Performance, Compliance | ⭐⭐⭐⭐ | 25-30 giờ |
| **Project 3: LearnVN** (Education Platform) | Content Delivery, Multi-role, Usability | ⭐⭐⭐⭐ | 25-30 giờ |

**Tổng thời gian ước tính**: 70-85 giờ (10-12 tuần nếu học 7-8 giờ/tuần)

---

## 🗺️ Lộ Trình Thực Hành

### Tuần 1-3: Project 1 - ShopVN (E-commerce Testing)

#### 🎯 Mục Tiêu
- Làm chủ 4 kỹ thuật Black-box Testing chính
- Viết Test Plan hoàn chỉnh
- Tạo Traceability Matrix
- Viết defect reports và test reports chuẩn

#### 📅 Lộ Trình Chi Tiết

**Tuần 1: Requirements Analysis & Test Planning**
- Ngày 1-2: Đọc và phân tích requirements (5 Epics)
- Ngày 3: Static Testing - Review requirements, tìm ambiguity
- Ngày 4-5: Viết Test Plan (Risk analysis, Test approach, Entry/Exit criteria)
- Ngày 6-7: Tạo Traceability Matrix (Requirements → Test Cases)

**Tuần 2: Test Design & Execution**
- Ngày 1-2: Viết test cases cho User Management (EP, BVA)
- Ngày 3-4: Viết test cases cho Products & Cart (Decision Table)
- Ngày 5-6: Viết test cases cho Checkout & Orders (State Transition)
- Ngày 7: Review và cải thiện test cases

**Tuần 3: Test Execution & Reporting**
- Ngày 1-3: Execute test cases (giả lập môi trường thực tế)
- Ngày 4-5: Viết defect reports cho bugs phát hiện
- Ngày 6: Tạo Test Progress Report
- Ngày 7: Tạo Test Completion Report + Retrospective

#### ✅ Deliverables Checklist
- [ ] Requirements Review Report (ambiguities found)
- [ ] Test Plan (15-20 trang)
- [ ] 300+ Test Cases covering tất cả 5 Epics
- [ ] Requirements Traceability Matrix
- [ ] 20-30 Defect Reports (simulated)
- [ ] Test Progress Report (mid-sprint)
- [ ] Test Completion Report
- [ ] Lessons Learned document

#### 📚 Kiến Thức ISTQB Áp Dụng
- **LO 1.1-1.4**: Testing fundamentals, Test process
- **LO 2.1-2.3**: SDLC models, Test levels
- **LO 4.1-4.5**: Black-box techniques (EP, BVA, Decision Table, State Transition)
- **LO 5.1-5.3**: Test management, Planning, Estimation
- **LO 6.1-6.4**: Defect management, Configuration management

---

### Tuần 4-7: Project 2 - PayVN (Mobile Banking Testing)

#### 🎯 Mục Tiêu
- Thành thạo Security Testing (OWASP Top 10)
- Hiểu và thực hiện Performance Testing
- Áp dụng Compliance requirements (PCI DSS, SBV)
- Risk-based testing approach

#### 📅 Lộ Trình Chi Tiết

**Tuần 4: Security Testing Preparation**
- Ngày 1-2: Học về OWASP Top 10 và Security Testing Basics
- Ngày 3-4: Phân tích security requirements của PayVN
- Ngày 5-6: Viết Security Test Cases (50+ TCs)
- Ngày 7: Setup security testing tools (OWASP ZAP, Burp Suite - optional)

**Tuần 5: Performance Testing**
- Ngày 1-2: Học về Performance Testing (Load, Stress, Spike, Endurance)
- Ngày 3-4: Viết Performance Test Scenarios
- Ngày 5-6: Học sử dụng JMeter cơ bản
- Ngày 7: Tạo JMeter test scripts cho các scenarios chính

**Tuần 6: Compliance & Functional Testing**
- Ngày 1-2: Tìm hiểu PCI DSS và SBV regulations
- Ngày 3-4: Viết Compliance Test Checklist
- Ngày 5-6: Viết Functional test cases cho 5 Epics
- Ngày 7: Review toàn bộ test cases

**Tuần 7: Execution & Reporting**
- Ngày 1-3: Execute Security & Functional tests
- Ngày 4-5: Execute Performance tests (simulated)
- Ngày 6: Analyze results, write defect reports
- Ngày 7: Create comprehensive Test Report + Risk Assessment

#### ✅ Deliverables Checklist
- [ ] Security Test Plan
- [ ] 50+ Security Test Cases (OWASP Top 10)
- [ ] 30+ Performance Test Scenarios
- [ ] JMeter Test Scripts (optional but recommended)
- [ ] Compliance Checklist (PCI DSS, SBV)
- [ ] 100+ Functional Test Cases
- [ ] Security Vulnerability Report
- [ ] Performance Test Report
- [ ] Test Completion Report with Risk Assessment

#### 📚 Kiến Thức ISTQB Áp Dụng
- **LO 2.2**: Test levels (System Testing, Acceptance Testing)
- **LO 2.4**: Non-functional testing types (Security, Performance)
- **LO 3.1**: Static Testing (Code review for security)
- **LO 4.4**: Experience-based techniques (Error Guessing for security)
- **LO 5.1**: Risk-based testing approach
- **LO 5.4**: Test metrics for performance

#### 🔒 Security Testing Focus Areas
1. **Authentication & Authorization**: Login, Session Management, MFA
2. **Input Validation**: SQL Injection, XSS, Command Injection
3. **Cryptography**: Data encryption, Secure communication (HTTPS)
4. **Session Management**: Session fixation, Session hijacking
5. **Error Handling**: Information disclosure through error messages

#### ⚡ Performance Testing Focus Areas
1. **Load Testing**: 10,000 concurrent users, normal conditions
2. **Stress Testing**: Beyond capacity, finding breaking point
3. **Spike Testing**: Sudden traffic increases (flash sales)
4. **Endurance Testing**: Long-duration stability (24h continuous)

---

### Tuần 8-11: Project 3 - LearnVN (Education Platform Testing)

#### 🎯 Mục Tiêu
- Xử lý complexity của multi-role system
- Test content delivery và video streaming
- Thực hiện Usability Testing
- End-to-end scenario testing
- Integration testing giữa các components

#### 📅 Lộ Trình Chi Tiết

**Tuần 8: Multi-Role & Requirements Analysis**
- Ngày 1-2: Phân tích requirements cho Student role
- Ngày 3-4: Phân tích requirements cho Instructor role
- Ngày 5-6: Xác định integration points giữa các roles
- Ngày 7: Viết Test Strategy cho multi-role testing

**Tuần 9: Functional & Content Testing**
- Ngày 1-2: Test cases cho Course Creation (Instructor)
- Ngày 3-4: Test cases cho Course Discovery & Enrollment (Student)
- Ngày 5-6: Test cases cho Learning Experience (Video, Quiz, Progress)
- Ngày 7: Test cases cho Reviews & Ratings

**Tuần 10: Non-Functional & Usability Testing**
- Ngày 1-2: Video streaming test cases (Upload, Playback, Quality)
- Ngày 3-4: Performance test scenarios (5000 concurrent video streams)
- Ngày 5-6: Usability Testing (Nielsen's 10 Heuristics)
- Ngày 7: Accessibility Testing (WCAG guidelines)

**Tuần 11: Integration & E2E Testing**
- Ngày 1-3: End-to-end scenarios (Instructor → Student flow)
- Ngày 4-5: Integration testing (Payment, Email, Video CDN)
- Ngày 6: Execute all test cases
- Ngày 7: Final Test Report + Recommendations

#### ✅ Deliverables Checklist
- [ ] Multi-Role Test Strategy
- [ ] 150+ Functional Test Cases (Student role)
- [ ] 100+ Functional Test Cases (Instructor role)
- [ ] 50+ Video Streaming Test Cases
- [ ] Usability Evaluation Report (Nielsen's Heuristics)
- [ ] 30+ End-to-End Scenarios
- [ ] Integration Test Report
- [ ] Test Completion Report
- [ ] UX Improvement Recommendations

#### 📚 Kiến Thức ISTQB Áp Dụng
- **LO 2.2**: Integration Testing, System Testing, Acceptance Testing
- **LO 2.4**: Usability Testing, Accessibility Testing
- **LO 4.2**: White-box techniques (for integration testing)
- **LO 4.4**: Exploratory Testing
- **LO 5.2**: Test estimation for complex projects

#### 🎥 Video Streaming Testing Focus
1. **Upload Performance**: Large files (2GB), concurrent uploads
2. **Video Processing**: Transcoding, multiple qualities (360p-1080p)
3. **Playback Quality**: Adaptive bitrate streaming
4. **Concurrent Streaming**: 5000+ simultaneous viewers
5. **Bandwidth Optimization**: CDN performance

#### 👥 Multi-Role Testing Scenarios
1. **Instructor Journey**: Signup → Create Course → Upload Content → Publish → Monitor Reviews
2. **Student Journey**: Signup → Browse → Enroll → Learn → Complete → Review
3. **Cross-Role Interactions**: Instructor responds to student questions
4. **Admin Journey**: Manage users, Approve courses, Handle disputes

---

## 🎓 Phương Pháp Học Hiệu Quả

### 1. **Learning by Doing**
```
Đọc Requirements → Tự viết Test Cases → So sánh với mẫu → Cải thiện
```
- Không nên đọc ngay phần "sample test cases"
- Hãy tự viết test cases trước, sau đó mới xem mẫu
- So sánh và học hỏi từ sự khác biệt

### 2. **Simulate Real Environment**
- Giả lập bạn đang làm việc tại công ty thực tế
- Set deadlines cho bản thân
- Làm việc theo sprint (1 sprint = 1 tuần)
- Daily review: 15 phút mỗi ngày để review công việc

### 3. **Active Learning**
Cho mỗi test case bạn viết, hãy tự hỏi:
- ✅ Kỹ thuật nào phù hợp nhất? Tại sao?
- ✅ Test case này cover learning objective nào?
- ✅ Nếu là tester thực tế, bạn sẽ viết như thế nào?
- ✅ Có edge cases nào bị bỏ sót không?

### 4. **Peer Review (Nếu Có Thể)**
- Tìm bạn học cùng để review test cases cho nhau
- Tham gia groups/forums về ISTQB
- Share công việc trên GitHub để nhận feedback

### 5. **Link to ISTQB Syllabus**
Mỗi khi làm một task, check xem nó relate đến learning objectives nào:
```
Viết EP test case → LO 4.2.1 Equivalence Partitioning
Viết Test Plan → LO 5.1.1 Test Planning
Viết Defect Report → LO 6.2.1 Defect Management
```

---

## 📊 Tự Đánh Giá Năng Lực

### ✅ Checklist Hoàn Thành Project

#### **Project 1: ShopVN**
Bạn đã hoàn thành tốt nếu:
- [ ] Viết được 300+ test cases với các kỹ thuật khác nhau
- [ ] Phân biệt rõ khi nào dùng EP, BVA, Decision Table, State Transition
- [ ] Test Plan đầy đủ các phần: Scope, Approach, Resources, Schedule, Risks
- [ ] Traceability Matrix map chính xác Requirements → Test Cases
- [ ] Defect reports có đủ thông tin để dev reproduce
- [ ] Test reports trả lời được câu hỏi: "Sản phẩm có ready để release không?"

#### **Project 2: PayVN**
Bạn đã hoàn thành tốt nếu:
- [ ] Hiểu và áp dụng được OWASP Top 10 vào test cases
- [ ] Viết được performance test scenarios cho 4 loại tests
- [ ] Hiểu compliance requirements (PCI DSS, SBV) và test được
- [ ] Áp dụng risk-based testing approach (prioritize high-risk areas)
- [ ] Security test cases cover authentication, authorization, data protection
- [ ] Performance test report phân tích được bottlenecks

#### **Project 3: LearnVN**
Bạn đã hoàn thành tốt nếu:
- [ ] Xử lý được complexity của multi-role system
- [ ] End-to-end scenarios cover toàn bộ user journey
- [ ] Usability evaluation áp dụng đúng Nielsen's 10 Heuristics
- [ ] Video streaming tests cover upload, processing, playback
- [ ] Integration tests verify tương tác giữa các components
- [ ] Test strategy hợp lý cho dự án phức tạp

### 📈 Rubric Tự Đánh Giá

| Tiêu Chí | Xuất Sắc (90-100%) | Tốt (75-89%) | Đạt (60-74%) | Chưa Đạt (<60%) |
|----------|-------------------|--------------|--------------|------------------|
| **Test Coverage** | >95% requirements covered | 80-95% covered | 60-79% covered | <60% covered |
| **Test Quality** | Test cases rõ ràng, có thể execute ngay | Đủ thông tin nhưng cần chỉnh sửa nhỏ | Thiếu một số thông tin | Không đủ để execute |
| **Technique Selection** | Chọn đúng kỹ thuật cho từng tình huống | Đúng >80% trường hợp | Đúng >60% trường hợp | Sử dụng kỹ thuật chưa phù hợp |
| **Documentation** | Documents hoàn chỉnh, professional | Đầy đủ nhưng cần polish | Thiếu một số phần | Không đầy đủ |
| **Risk Analysis** | Identify và prioritize risks chính xác | Identify được risks chính | Identify được một số risks | Thiếu risk analysis |

---

## 🔗 Mapping Sang ISTQB Exam Topics

### **Phân Bố Learning Objectives Trong 3 Projects**

| Learning Objective | Project 1 | Project 2 | Project 3 |
|-------------------|-----------|-----------|-----------|
| **LO 1.1-1.4**: Testing Fundamentals | ✅✅✅ | ✅✅ | ✅✅ |
| **LO 2.1**: SDLC Models | ✅✅ | ✅✅✅ | ✅✅ |
| **LO 2.2**: Test Levels | ✅✅ | ✅✅ | ✅✅✅ |
| **LO 2.3**: Test Types | ✅✅✅ | ✅✅ | ✅✅ |
| **LO 2.4**: Non-functional Testing | ✅ | ✅✅✅ | ✅✅✅ |
| **LO 3.1-3.2**: Static Testing | ✅✅ | ✅✅ | ✅ |
| **LO 4.1-4.5**: Test Techniques | ✅✅✅ | ✅✅ | ✅✅ |
| **LO 5.1-5.4**: Test Management | ✅✅✅ | ✅✅✅ | ✅✅✅ |
| **LO 6.1-6.4**: Tools & Automation | ✅ | ✅✅ | ✅✅ |

**Giải thích ký hiệu:**
- ✅ = Covered cơ bản
- ✅✅ = Covered đầy đủ với nhiều ví dụ
- ✅✅✅ = Focus chính của project

### **Format Câu Hỏi ISTQB Trong Projects**

Projects được thiết kế để bạn gặp tất cả dạng câu hỏi ISTQB:

1. **Definition Questions**: "What is...?" "Which of the following is...?"
   - Ví dụ: Phân biệt Equivalence Partitioning vs Boundary Value Analysis

2. **Application Questions**: "Which technique should be used...?"
   - Ví dụ: Chọn kỹ thuật phù hợp cho từng scenario

3. **Analysis Questions**: "What is the defect...?" "What is missing...?"
   - Ví dụ: Phân tích requirements để tìm ambiguity

4. **Calculation Questions**: "How many test cases...?" "What is the pass rate...?"
   - Ví dụ: Tính số test cases cho EP, BVA

---

## 🎯 Tips & Best Practices

### 📝 **Writing Test Cases**

#### ❌ **Bad Example**
```
TC-001: Test login
Steps: Login
Expected: Success
```

#### ✅ **Good Example**
```
TC-LOGIN-001: Login with Valid Credentials
Technique: Equivalence Partitioning (Valid Partition)
Preconditions: User "testuser@gmail.com" exists, password "Pass123!@#"

Test Steps:
1. Navigate to login page (https://shopvn.com/login)
2. Enter email: testuser@gmail.com
3. Enter password: Pass123!@#
4. Click "Đăng nhập" button

Expected Results:
- System validates credentials successfully
- User redirected to homepage (https://shopvn.com)
- Display "Xin chào, Test User" in header
- Session cookie created with 30-minute expiry

Traceability: REQ-AUTH-001, REQ-AUTH-002
Priority: P0 (Critical)
```

### 🐛 **Writing Defect Reports**

#### ❌ **Bad Example**
```
Bug: Login không work
```

#### ✅ **Good Example**
```
[BUG-PAY-001] [Critical] Payment timeout for orders >10M VND

Environment: PayVN Mobile App v2.5.0, Android 13, Samsung Galaxy S21
Reporter: Nguyen Van A | Date: 2024-01-15

Summary:
Payment transactions fail with timeout error when order value exceeds 10,000,000 VND
using VNPay payment gateway.

Steps to Reproduce:
1. Login as user "testuser@payvn.com"
2. Navigate to "Chuyển tiền" → "Tới số điện thoại"
3. Enter recipient: 0987654321
4. Enter amount: 11,000,000 VND
5. Select payment method: "VNPay"
6. Click "Xác nhận thanh toán"
7. Complete VNPay authentication

Expected Result:
- Transaction processed successfully
- Balance deducted from sender
- Confirmation screen displayed

Actual Result:
- After 30 seconds, error "ERR_TIMEOUT_001" displayed
- Balance NOT deducted
- No transaction record in history

Severity: Critical (Blocks major functionality)
Priority: P0 (Must fix before release)
Frequency: 10/10 attempts (100% reproducible)

Additional Info:
- Works fine for amounts <10M VND
- Issue affects all payment gateways, not just VNPay
- Backend logs show: "Gateway timeout after 30s"
```

### 📊 **Test Metrics to Track**

#### **During Execution**
```
Daily Tracking:
- Test cases executed today: 45
- Test cases passed: 38 (84%)
- Test cases failed: 5 (11%)
- Test cases blocked: 2 (5%)
- New defects found: 7
- Defects fixed today: 3
```

#### **End of Project**
```
Summary Metrics:
- Total test cases: 312
- Test coverage: 96% (299/312 requirements covered)
- Pass rate: 87% (272/312 passed)
- Defect detection rate: 4.5% (14 defects / 312 TCs)
- Critical defects: 2
- High defects: 5
- Medium defects: 7
- Test efficiency: 2.5 defects per day
```

---

## 🚀 Chuẩn Bị Thi ISTQB Sau Khi Hoàn Thành 3 Projects

### ✅ **Bạn Đã Sẵn Sàng Nếu:**

1. **Hoàn thành cả 3 projects** với chất lượng tốt (>75% theo rubric)
2. **Hiểu rõ tất cả 57 Learning Objectives** trong ISTQB Syllabus v4.0.1
3. **Làm được 30 câu MCQ** trong bài tập mỗi module (avg >80%)
4. **Phân biệt rõ** các concepts:
   - Verification vs Validation
   - Error vs Defect vs Failure
   - Test Case vs Test Procedure vs Test Suite
   - Static Testing vs Dynamic Testing
   - Black-box vs White-box vs Experience-based

### 📚 **Bước Tiếp Theo**

#### **Tuần 1-2 Trước Thi: Review Toàn Bộ Syllabus**
- [ ] Đọc lại ISTQB Syllabus v4.0.1 (150+ trang)
- [ ] Tạo flashcards cho 57 Learning Objectives
- [ ] Review lại tất cả bài tập MCQ từ 7 giai đoạn

#### **Tuần Cuối: Mock Exams**
- [ ] Làm 3 bộ mock exam (40 câu x 3 = 120 câu)
- [ ] Target: >90% để chắc chắn pass (pass threshold: 65%)
- [ ] Review lại các câu sai, hiểu rõ tại sao sai

#### **Ngày Thi**
- Đọc kỹ đề (60 phút cho 40 câu = 1.5 phút/câu)
- Làm câu dễ trước, câu khó đánh dấu làm sau
- Không bỏ câu nào (không trừ điểm)
- Review lại toàn bộ đề trước khi submit

---

## 📞 Hỗ Trợ & Resources

### 🌐 **ISTQB Official Resources**
- **Syllabus**: https://www.istqb.org/certifications/certified-tester-foundation-level
- **Glossary**: https://glossary.istqb.org/
- **Sample Exam**: https://www.istqb.org/downloads/send/51-ctfl-2018/329-ctfl-2018-sample-exam-questions.html

### 📖 **Recommended Books**
1. **"Foundations of Software Testing: ISTQB Certification"** - Rex Black
2. **"Software Testing"** - Ron Patton
3. **"Lessons Learned in Software Testing"** - Cem Kaner

### 💬 **Communities**
- **ISTQB LinkedIn Group**: Trao đổi với tester trên toàn thế giới
- **VietNam Tester Group (Facebook)**: Cộng đồng tester Việt Nam
- **Ministry of Testing**: https://www.ministryoftesting.com/

### 🎥 **Video Courses**
- ISTQB Foundation Level trên Udemy (có subtitles tiếng Việt)
- YouTube channels: "Testing World", "Software Testing Help"

---

## 🎓 Lời Kết

Chúc mừng bạn đã hoàn thành **8 giai đoạn** của chương trình ISTQB Foundation Level! 🎉

Bạn đã đi được một chặng đường dài:
- ✅ **7 giai đoạn lý thuyết**: 28 modules với 57 Learning Objectives
- ✅ **3 dự án thực hành**: 500+ test cases, 3 domains khác nhau
- ✅ **Sẵn sàng thi ISTQB**: Kiến thức đầy đủ để pass exam với điểm cao

### 🌟 **Điều Quan Trọng Nhất**

Testing không chỉ là viết test cases. Testing là:
- 🎯 **Mindset**: Luôn đặt câu hỏi "What if...?"
- 🔍 **Attention to detail**: Chú ý những điều người khác bỏ qua
- 🧩 **Problem solving**: Tìm ra bugs trước khi users gặp phải
- 📊 **Communication**: Báo cáo rõ ràng để stakeholders hiểu

### 🚀 **Next Steps After ISTQB**

1. **Specialized Certifications**:
   - ISTQB Agile Tester Extension
   - ISTQB Test Automation Engineer
   - ISTQB Performance Testing
   - ISTQB Security Testing

2. **Practical Skills**:
   - Learn automation: Selenium, Playwright, Cypress
   - Learn API testing: Postman, REST Assured
   - Learn CI/CD: Jenkins, GitHub Actions
   - Learn cloud testing: AWS, Azure

3. **Real-World Experience**:
   - Join open-source projects
   - Contribute to bug bounty programs
   - Build your own testing portfolio

---

**Good luck với kỳ thi ISTQB! Bạn làm được! 💪**

---

*Tài liệu được tạo bởi ISTQB Foundation Level Curriculum v4.0.1*
*Cập nhật lần cuối: 2024*
