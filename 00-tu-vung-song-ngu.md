# TỪ VỰNG SONG NGỮ ISTQB - ENGLISH-VIETNAMESE GLOSSARY

## Hướng dẫn sử dụng

Đây là bảng thuật ngữ song ngữ Anh-Việt cho các từ khóa quan trọng trong ISTQB Foundation Level.

**Lưu ý quan trọng**:
- Trong thi ISTQB và công việc thực tế, **sử dụng thuật ngữ tiếng Anh**
- Phần tiếng Việt chỉ để **giúp bạn hiểu** nghĩa
- Một số thuật ngữ **không nên dịch** ra tiếng Việt (giữ nguyên tiếng Anh)

**Ký hiệu**:
- **(K1)**: Thuật ngữ cần nhớ (Remember level)
- **(K2)**: Thuật ngữ cần hiểu sâu (Understand level)
- **(K3)**: Thuật ngữ cần biết áp dụng (Apply level)
- **[ISTQB]**: Định nghĩa chính thức từ ISTQB Glossary

---

## A

### Acceptance Criteria **(K2)**
**Tiếng Việt**: Tiêu chí chấp nhận
**Định nghĩa**: Các điều kiện mà một sản phẩm phải đáp ứng để được chấp nhận bởi người dùng, khách hàng, hoặc bên liên quan khác.
**Ví dụ**: "User có thể login bằng email và password trong vòng 2 giây"

### Acceptance Testing **(K2)**
**Tiếng Việt**: Kiểm thử chấp nhận
**Định nghĩa**: Loại testing kiểm tra xem hệ thống có đáp ứng yêu cầu và sẵn sàng để deploy không.
**Các loại**: User Acceptance Testing (UAT), Operational Acceptance Testing (OAT)

### Accuracy **(K1)**
**Tiếng Việt**: Độ chính xác
**Định nghĩa**: Mức độ mà kết quả thực tế gần với kết quả mong đợi.

### Actual Result **(K2)**
**Tiếng Việt**: Kết quả thực tế
**Định nghĩa**: Kết quả quan sát được khi thực hiện test case.
**So sánh với**: Expected Result (Kết quả mong đợi)

### Ad Hoc Testing **(K1)**
**Tiếng Việt**: Kiểm thử tùy ý (không theo kế hoạch)
**Định nghĩa**: Testing không có thiết kế test case chính thức, thường dựa vào kinh nghiệm.

### Agile Software Development **(K2)**
**Tiếng Việt**: Phát triển phần mềm Agile
**Định nghĩa**: Phương pháp phát triển lặp và gia tăng, tập trung vào collaboration và feedback nhanh.

### Alpha Testing **(K1)**
**Tiếng Việt**: Kiểm thử Alpha
**Định nghĩa**: Testing do internal users thực hiện tại văn phòng nhà phát triển.

### Anomaly **(K1)**
**Tiếng Việt**: Bất thường, lỗi
**Định nghĩa**: Bất kỳ điều gì lệch khỏi kỳ vọng. Đồng nghĩa với defect, fault, problem.

### API Testing **(K1)**
**Tiếng Việt**: Kiểm thử API
**Định nghĩa**: Testing các Application Programming Interfaces trực tiếp, độc lập với UI.

### ATDD - Acceptance Test-Driven Development **(K2)**
**Tiếng Việt**: Phát triển dẫn dắt bởi test chấp nhận
**Định nghĩa**: Cách tiếp cận viết acceptance tests TRƯỚC khi viết code.
**Format**: Given-When-Then

---

## B

### Basis Test Set **(K1)**
**Tiếng Việt**: Tập test cơ sở
**Định nghĩa**: Tập hợp test cases đạt được 100% coverage theo một tiêu chí nhất định.

### BDD - Behavior-Driven Development **(K2)**
**Tiếng Việt**: Phát triển dẫn dắt bởi hành vi
**Định nghĩa**: Cách tiếp cận phát triển dựa trên behavior mong muốn, sử dụng ngôn ngữ tự nhiên.

### Beta Testing **(K1)**
**Tiếng Việt**: Kiểm thử Beta
**Định nghĩa**: Testing do external users thực hiện trong môi trường thực tế của họ.

### Black-Box Testing **(K2)**
**Tiếng Việt**: Kiểm thử hộp đen
**Định nghĩa**: Testing technique dựa trên specification mà không cần biết cấu trúc bên trong.
**Ví dụ**: EP, BVA, Decision Table, State Transition

### Boundary Value **(K3)**
**Tiếng Việt**: Giá trị biên
**Định nghĩa**: Giá trị ở ranh giới của một partition (min, max value).

### Boundary Value Analysis (BVA) **(K3)**
**Tiếng Việt**: Phân tích giá trị biên
**Định nghĩa**: Test technique tập trung vào testing các giá trị tại biên của partitions.
**Types**: 2-value BVA, 3-value BVA

### Branch **(K2)**
**Tiếng Việt**: Nhánh
**Định nghĩa**: Một đường đi có thể từ một decision point trong code.

### Branch Coverage **(K3)**
**Tiếng Việt**: Độ bao phủ nhánh
**Định nghĩa**: Phần trăm branches được execute bởi test cases.
**Công thức**: (Branches executed / Total branches) × 100%

### Bug **(K1)**
**Tiếng Việt**: Lỗi
**Định nghĩa**: Thuật ngữ thông dụng cho defect/fault. Đồng nghĩa với error, fault, defect.

---

## C

### Change-Related Testing **(K2)**
**Tiếng Việt**: Kiểm thử liên quan đến thay đổi
**Định nghĩa**: Testing sau khi có thay đổi code, bao gồm confirmation testing và regression testing.

### Checklist-Based Testing **(K2)**
**Tiếng Việt**: Kiểm thử dựa trên checklist
**Định nghĩa**: Experience-based technique sử dụng checklist về những gì cần test.

### Code Coverage **(K2)**
**Tiếng Việt**: Độ bao phủ code
**Định nghĩa**: Đo lường mức độ code được execute bởi tests.
**Types**: Statement coverage, Branch coverage, Path coverage

### Component **(K1)**
**Tiếng Việt**: Thành phần
**Định nghĩa**: Phần nhỏ nhất có thể test được của hệ thống (function, class, module).

### Component Integration Testing **(K2)**
**Tiếng Việt**: Kiểm thử tích hợp thành phần
**Định nghĩa**: Testing các interface và interaction giữa các components.

### Component Testing **(K2)**
**Tiếng Việt**: Kiểm thử thành phần
**Định nghĩa**: Testing các components riêng lẻ. Còn gọi là unit testing, module testing.

### Concurrency **(K1)**
**Tiếng Việt**: Đồng thời
**Định nghĩa**: Khả năng nhiều users hoặc processes hoạt động cùng lúc.

### Confirmation Testing **(K2)**
**Tiếng Việt**: Kiểm thử xác nhận
**Định nghĩa**: Testing để xác nhận một defect đã được fix. Còn gọi là re-testing.

### Configuration Management **(K2)**
**Tiếng Việt**: Quản lý cấu hình
**Định nghĩa**: Quản lý tất cả testware và work products, đảm bảo version control.

### Coverage **(K2)**
**Tiếng Việt**: Độ bao phủ
**Định nghĩa**: Phần trăm test basis được cover bởi test cases.
**Ví dụ**: Requirement coverage, code coverage, decision coverage

### Coverage Item **(K2)**
**Tiếng Việt**: Mục bao phủ
**Định nghĩa**: Một item cần được test (requirement, branch, statement, etc.)

---

## D

### Debugging **(K2)**
**Tiếng Việt**: Gỡ lỗi
**Định nghĩa**: Quá trình tìm, phân tích và remove defects trong code.
**Khác với Testing**: Testing tìm defects, Debugging fix defects

### Decision **(K2)**
**Tiếng Việt**: Quyết định
**Định nghĩa**: Điểm trong code có thể đi theo nhiều đường (if, switch, loop).

### Decision Coverage **(K3)**
**Tiếng Việt**: Độ bao phủ quyết định
**Định nghĩa**: Phần trăm decision outcomes được test. Tương đương với branch coverage.

### Decision Table **(K3)**
**Tiếng Việt**: Bảng quyết định
**Định nghĩa**: Kỹ thuật test technique dùng bảng để thể hiện các combinations của conditions và actions.
**Types**: Full decision table, Minimized decision table

### Defect **(K2)**
**Tiếng Việt**: Khuyết tật, lỗi
**[ISTQB]**: Imperfection trong work product mà nó không đáp ứng requirements.
**Đồng nghĩa**: Bug, fault, error, problem

### Defect Density **(K1)**
**Tiếng Việt**: Mật độ lỗi
**Định nghĩa**: Số defects trên một đơn vị (per line of code, per function point).

### Defect Management **(K3)**
**Tiếng Việt**: Quản lý lỗi
**Định nghĩa**: Quy trình nhận biết, ghi nhận, phân loại, và theo dõi defects.

### Defect Report **(K3)**
**Tiếng Việt**: Báo cáo lỗi
**Định nghĩa**: Document chi tiết một defect.
**Bao gồm**: ID, title, description, steps to reproduce, expected vs actual results, severity, priority, status

### Definition of Done (DoD) **(K2)**
**Tiếng Việt**: Định nghĩa hoàn thành
**Định nghĩa**: Tập các tiêu chí một user story phải đáp ứng để được coi là Done.
**Ví dụ**: "Code written, reviewed, tested, and deployed"

### Definition of Ready (DoR) **(K2)**
**Tiếng Việt**: Định nghĩa sẵn sàng
**Định nghĩa**: Tập các tiêu chí một user story phải đáp ứng trước khi vào sprint.

### DevOps **(K2)**
**Tiếng Việt**: DevOps
**Định nghĩa**: Phương pháp kết hợp Development và Operations để tăng tốc delivery.
**Liên quan**: CI/CD, automation, continuous testing

### Dynamic Testing **(K2)**
**Tiếng Việt**: Kiểm thử động
**Định nghĩa**: Testing bằng cách EXECUTE code.
**Khác với**: Static testing (không execute code)

---

## E

### Endurance Testing **(K1)**
**Tiếng Việt**: Kiểm thử độ bền
**Định nghĩa**: Performance testing để kiểm tra stability của hệ thống trong thời gian dài.

### Entry Criteria **(K2)**
**Tiếng Việt**: Tiêu chí vào
**Định nghĩa**: Các điều kiện cần đáp ứng TRƯỚC KHI bắt đầu một test activity.
**Ví dụ**: "All test cases reviewed and approved"

### Equivalence Partition **(K3)**
**Tiếng Việt**: Phân vùng tương đương
**Định nghĩa**: Một tập hợp các giá trị được xử lý giống nhau bởi test object.

### Equivalence Partitioning (EP) **(K3)**
**Tiếng Việt**: Phân vùng tương đương
**Định nghĩa**: Test technique chia input/output thành các partitions có thể được test với một đại diện.
**Types**: Valid partition, Invalid partition

### Error **(K2)**
**Tiếng Việt**: Sai sót
**[ISTQB]**: Hành động của con người tạo ra kết quả sai.
**Error → Defect → Failure**

### Error Guessing **(K2)**
**Tiếng Việt**: Đoán lỗi
**Định nghĩa**: Experience-based technique dựa vào kinh nghiệm tester để dự đoán nơi có thể có defects.

### Exhaustive Testing **(K2)**
**Tiếng Việt**: Kiểm thử toàn diện
**Định nghĩa**: Testing tất cả combinations của inputs và preconditions.
**Lưu ý**: KHÔNG THỂ thực hiện (Testing Principle #2)

### Exit Criteria **(K2)**
**Tiếng Việt**: Tiêu chí ra
**Định nghĩa**: Các điều kiện cần đáp ứng để HOÀN THÀNH một test activity.
**Ví dụ**: "All critical defects fixed and verified"

### Expected Result **(K2)**
**Tiếng Việt**: Kết quả mong đợi
**Định nghĩa**: Kết quả dự kiến từ test basis khi execute một test case.
**So sánh với**: Actual Result

### Exploratory Testing **(K2)**
**Tiếng Việt**: Kiểm thử khám phá
**Định nghĩa**: Testing không có test cases chi tiết trước, tester vừa design vừa execute vừa learn.
**Format**: Session-based testing (time-boxed sessions)

---

## F

### Fail **(K1)**
**Tiếng Việt**: Thất bại, fail
**Định nghĩa**: Test case cho kết quả khác với expected result.

### Failure **(K2)**
**Tiếng Việt**: Hỏng hóc, lỗi phát sinh
**[ISTQB]**: Sự kiện test object không thực hiện đúng function như yêu cầu.
**Error → Defect → Failure**

### Failure Rate **(K1)**
**Tiếng Việt**: Tỷ lệ hỏng hóc
**Định nghĩa**: Tỷ lệ failures xảy ra trong một khoảng thời gian.

### False Negative **(K1)**
**Tiếng Việt**: Âm tính giả
**Định nghĩa**: Test PASS nhưng thực tế có defect (nguy hiểm nhất!).

### False Positive **(K1)**
**Tiếng Việt**: Dương tính giả
**Định nghĩa**: Test FAIL nhưng thực tế không có defect (do test case sai hoặc môi trường).

### Fault **(K1)**
**Tiếng Việt**: Lỗi
**Định nghĩa**: Đồng nghĩa với defect, bug. Imperfection có thể gây ra failure.

### Functional Testing **(K2)**
**Tiếng Việt**: Kiểm thử chức năng
**Định nghĩa**: Testing tập trung vào "what" the system does (CHỨC NĂNG).
**Khác với**: Non-functional testing (HOW the system works)

---

## G

### Given-When-Then **(K2)**
**Tiếng Việt**: Cho-Khi-Thì
**Định nghĩa**: Format viết acceptance criteria trong BDD/ATDD.
**Format**:
- **Given**: Preconditions (điều kiện đầu)
- **When**: Action (hành động)
- **Then**: Expected result (kết quả mong đợi)

---

## H

### Happy Path **(K1)**
**Tiếng Việt**: Đường đi vui vẻ
**Định nghĩa**: Scenario mà không có errors hoặc exceptions xảy ra.

---

## I

### Impact Analysis **(K2)**
**Tiếng Việt**: Phân tích tác động
**Định nghĩa**: Đánh giá change ảnh hưởng đến những phần nào của hệ thống.

### Incident **(K1)**
**Tiếng Việt**: Sự cố
**Định nghĩa**: Bất kỳ sự kiện nào cần điều tra. Có thể là defect hoặc không.

### Incremental Development Model **(K2)**
**Tiếng Việt**: Mô hình phát triển gia tăng
**Định nghĩa**: Phát triển hệ thống qua nhiều increments, mỗi increment thêm functionality.

### Independence of Testing **(K2)**
**Tiếng Việt**: Tính độc lập của kiểm thử
**Định nghĩa**: Mức độ separation giữa testers và developers.
**Levels**: Self-testing → Team testing → Independent test team → Third-party testing

### Inspection **(K2)**
**Tiếng Việt**: Thanh tra
**Định nghĩa**: Loại formal review có process nghiêm ngặt, tìm defects trong work products.
**Roles**: Author, Moderator, Scribe, Reviewers, Manager

### Integration **(K2)**
**Tiếng Việt**: Tích hợp
**Định nghĩa**: Quá trình kết hợp các components hoặc systems lại với nhau.

### Integration Testing **(K2)**
**Tiếng Việt**: Kiểm thử tích hợp
**Định nghĩa**: Testing các interfaces giữa components hoặc systems.
**Types**: Component integration testing, System integration testing

### INVEST Criteria **(K2)**
**Tiếng Việt**: Tiêu chí INVEST
**Định nghĩa**: Tiêu chí cho user story tốt:
- **I**ndependent (Độc lập)
- **N**egotiable (Có thể thương lượng)
- **V**aluable (Có giá trị)
- **E**stimable (Có thể ước lượng)
- **S**mall (Nhỏ gọn)
- **T**estable (Có thể test)

### ISO 25010 **(K2)**
**Tiếng Việt**: ISO 25010
**Định nghĩa**: Standard định nghĩa 8 quality characteristics:
1. Functional Suitability (Phù hợp chức năng)
2. Performance Efficiency (Hiệu năng)
3. Compatibility (Tương thích)
4. Usability (Khả năng sử dụng)
5. Reliability (Độ tin cậy)
6. Security (Bảo mật)
7. Maintainability (Khả năng bảo trì)
8. Portability (Tính di động)

### Iterative Development Model **(K2)**
**Tiếng Việt**: Mô hình phát triển lặp
**Định nghĩa**: Phát triển qua nhiều iterations, mỗi iteration refine sản phẩm.

---

## L

### Load Generator **(K1)**
**Tiếng Việt**: Trình tạo tải
**Định nghĩa**: Tool tạo ra load cho performance testing (simulate concurrent users).

### Load Testing **(K1)**
**Tiếng Việt**: Kiểm thử tải
**Định nghĩa**: Performance testing để xem hệ thống hoạt động thế nào dưới expected load.

---

## M

### Maintenance Testing **(K2)**
**Tiếng Việt**: Kiểm thử bảo trì
**Định nghĩa**: Testing sau khi hệ thống đã được deploy và có modifications/upgrades.
**Triggers**: Modifications, Migrations/Upgrades, Retirement

### Manual Testing **(K1)**
**Tiếng Việt**: Kiểm thử thủ công
**Định nghĩa**: Testing được thực hiện bởi con người (không dùng automation tools).

### Metrics **(K2)**
**Tiếng Việt**: Chỉ số đo lường
**Định nghĩa**: Các measurement để track quality, progress, hoặc effectiveness.
**Ví dụ**: Defect density, test coverage, pass rate

### Moderator **(K2)**
**Tiếng Việt**: Người điều phối
**Định nghĩa**: Role chủ trì review meeting, đảm bảo quy trình được tuân thủ.

---

## N

### Negative Testing **(K1)**
**Tiếng Việt**: Kiểm thử âm tính
**Định nghĩa**: Testing với invalid/unexpected inputs để xem hệ thống xử lý errors thế nào.

### Non-Functional Testing **(K2)**
**Tiếng Việt**: Kiểm thử phi chức năng
**Định nghĩa**: Testing tập trung vào "HOW WELL" the system works.
**Examples**: Performance, security, usability, reliability, compatibility

---

## O

### Oracle **(K1)**
**Tiếng Việt**: Nguồn tham chiếu
**Định nghĩa**: Nguồn xác định expected result (spec, existing system, user expert).

---

## P

### Pass **(K1)**
**Tiếng Việt**: Đạt, pass
**Định nghĩa**: Test case cho kết quả giống với expected result.

### Path **(K2)**
**Tiếng Việt**: Đường đi
**Định nghĩa**: Một chuỗi các events từ entry đến exit point trong component/system.

### Performance Efficiency **(K2)**
**Tiếng Việt**: Hiệu năng
**Định nghĩa**: Mức độ hệ thống sử dụng tài nguyên hiệu quả.
**Includes**: Time behavior, Resource utilization, Capacity

### Performance Testing **(K2)**
**Tiếng Việt**: Kiểm thử hiệu năng
**Định nghĩa**: Testing đo lường performance characteristics.
**Types**: Load testing, Stress testing, Spike testing, Endurance testing

### Pesticide Paradox **(K2)**
**Tiếng Việt**: Nghịch lý thuốc trừ sâu
**Định nghĩa**: Testing Principle #5 - Nếu chạy đi chạy lại cùng tests, chúng sẽ không còn tìm được defects mới.

### Portability **(K1)**
**Tiếng Việt**: Tính di động
**Định nghĩa**: Mức độ dễ dàng transfer hệ thống sang môi trường khác.

### Positive Testing **(K1)**
**Tiếng Việt**: Kiểm thử dương tính
**Định nghĩa**: Testing với valid/expected inputs.

### Postcondition **(K2)**
**Tiếng Việt**: Điều kiện sau
**Định nghĩa**: Trạng thái của hệ thống SAU KHI execute test case.

### Precondition **(K2)**
**Tiếng Việt**: Điều kiện trước
**Định nghĩa**: Trạng thái của hệ thống cần có TRƯỚC KHI execute test case.

### Priority **(K3)**
**Tiếng Việt**: Độ ưu tiên
**Định nghĩa**: Mức độ quan trọng để fix defect TỪ BUSINESS PERSPECTIVE.
**Levels**: High, Medium, Low
**Khác với**: Severity (technical impact)

### Product Risk **(K3)**
**Tiếng Việt**: Rủi ro sản phẩm
**Định nghĩa**: Risk liên quan đến product quality (defects, failures).
**Khác với**: Project risk (schedule, budget)

### Project Risk **(K2)**
**Tiếng Việt**: Rủi ro dự án
**Định nghĩa**: Risk ảnh hưởng đến ability to achieve project objectives (late delivery, budget overrun).

---

## Q

### Quality **(K2)**
**Tiếng Việt**: Chất lượng
**[ISTQB]**: Mức độ một sản phẩm đáp ứng stated/implied needs của stakeholders.

### Quality Assurance (QA) **(K2)**
**Tiếng Việt**: Đảm bảo chất lượng
**Định nghĩa**: Process-oriented activities để ensure processes được follow đúng.
**Khác với**: Testing (product-oriented)

### Quality Control (QC) **(K1)**
**Tiếng Việt**: Kiểm soát chất lượng
**Định nghĩa**: Product-oriented activities để kiểm tra product quality. Testing là một phần của QC.

---

## R

### Ramp Down **(K1)**
**Tiếng Việt**: Giảm tải
**Định nghĩa**: Giảm load dần trong performance testing.

### Ramp Up **(K1)**
**Tiếng Việt**: Tăng tải
**Định nghĩa**: Tăng load dần trong performance testing.

### Regression Testing **(K2)**
**Tiếng Việt**: Kiểm thử hồi quy
**Định nghĩa**: Testing để xác nhận changes không gây ra unintended side effects.
**Khi nào**: After bug fix, new feature, refactoring, environment change

### Reliability **(K2)**
**Tiếng Việt**: Độ tin cậy
**Định nghĩa**: Mức độ hệ thống perform đúng functions trong specified conditions và time period.

### Requirement **(K1)**
**Tiếng Việt**: Yêu cầu
**Định nghĩa**: Điều mà stakeholder cần từ hệ thống.
**Types**: Functional requirements, Non-functional requirements

### Requirements-Based Testing **(K2)**
**Tiếng Việt**: Kiểm thử dựa trên yêu cầu
**Định nghĩa**: Black-box technique design test cases từ requirements.

### Retrospective **(K2)**
**Tiếng Việt**: Họp hồi tưởng
**Định nghĩa**: Meeting sau sprint/iteration để review what went well/wrong và improve.

### Review **(K2)**
**Tiếng Việt**: Xem xét, đánh giá
**Định nghĩa**: Type of static testing trong đó work product được examined bởi stakeholders.
**Types**: Informal review, Walkthrough, Technical review, Inspection

### Reviewer **(K2)**
**Tiếng Việt**: Người đánh giá
**Định nghĩa**: Role tham gia review và provide feedback.

### Risk **(K2)**
**Tiếng Việt**: Rủi ro
**Định nghĩa**: Factor có thể gây ra negative consequences trong tương lai.
**Components**: Likelihood (khả năng xảy ra) × Impact (tác động)

### Risk Analysis **(K3)**
**Tiếng Việt**: Phân tích rủi ro
**Định nghĩa**: Quá trình identify và assess risks.
**Steps**: Risk identification → Risk assessment (likelihood × impact)

### Risk-Based Testing **(K3)**
**Tiếng Việt**: Kiểm thử dựa trên rủi ro
**Định nghĩa**: Approach ưu tiên testing dựa trên risk levels.

### Risk Control **(K2)**
**Tiếng Việt**: Kiểm soát rủi ro
**Định nghĩa**: Quá trình implement actions để giảm risk.
**Actions**: Mitigation (giảm thiểu), Monitoring (theo dõi)

### Risk Level **(K3)**
**Tiếng Việt**: Mức độ rủi ro
**Định nghĩa**: Qualitative/quantitative measure của risk.
**Formula**: Risk Level = Likelihood × Impact

### Root Cause **(K2)**
**Tiếng Việt**: Nguyên nhân gốc rễ
**Định nghĩa**: Nguyên nhân cơ bản gây ra defects. Fix root cause sẽ prevent similar defects.

---

## S

### Sanity Testing **(K1)**
**Tiếng Việt**: Kiểm thử lý trí
**Định nghĩa**: Quick testing để xác định có nên proceed với testing chi tiết không.

### SDLC - Software Development Lifecycle **(K2)**
**Tiếng Việt**: Vòng đời phát triển phần mềm
**Định nghĩa**: Các phases từ conception đến retirement của software.
**Models**: Waterfall, V-model, Agile, Iterative, Incremental

### Security Testing **(K1)**
**Tiếng Việt**: Kiểm thử bảo mật
**Định nghĩa**: Testing để đánh giá khả năng bảo vệ data và maintain security.

### Sequential Development Model **(K2)**
**Tiếng Việt**: Mô hình phát triển tuần tự
**Định nghĩa**: SDLC model mà mỗi phase phải hoàn thành trước khi sang phase tiếp theo.
**Examples**: Waterfall, V-model

### Service Virtualization **(K1)**
**Tiếng Việt**: Ảo hóa dịch vụ
**Định nghĩa**: Method emulate behavior của components/services không available.

### Severity **(K3)**
**Tiếng Việt**: Mức độ nghiêm trọng
**Định nghĩa**: Mức độ impact của defect LÊN HỆ THỐNG (technical perspective).
**Levels**: Critical, Major, Minor, Trivial
**Khác với**: Priority (business urgency)

### Shift Left **(K2)**
**Tiếng Việt**: Dịch trái
**Định nghĩa**: Approach làm testing sớm hơn trong SDLC để tìm defects sớm.

### Smoke Testing **(K1)**
**Tiếng Việt**: Kiểm thử khói
**Định nghĩa**: Subset của tests chạy để verify basic functionality trước khi testing chi tiết.

### Spike Testing **(K1)**
**Tiếng Việt**: Kiểm thử đột biến
**Định nghĩa**: Performance testing với sudden bursts của peak loads.

### Stakeholder **(K2)**
**Tiếng Việt**: Bên liên quan
**Định nghĩa**: Người/nhóm có interest trong activities/outcomes của project/system.

### State Diagram **(K3)**
**Tiếng Việt**: Biểu đồ trạng thái
**Định nghĩa**: Diagram thể hiện states của system và transitions giữa chúng.

### State Transition Testing **(K3)**
**Tiếng Việt**: Kiểm thử chuyển trạng thái
**Định nghĩa**: Black-box technique design tests từ state diagrams/state tables.
**Coverage**: All states, Valid transitions, All transitions (including invalid)

### Statement **(K2)**
**Tiếng Việt**: Câu lệnh
**Định nghĩa**: Một entity in code có thể execute (một dòng code thực thi).

### Statement Coverage **(K3)**
**Tiếng Việt**: Độ bao phủ câu lệnh
**Định nghĩa**: Phần trăm statements được execute bởi test cases.
**Công thức**: (Statements executed / Total statements) × 100%

### Static Analysis **(K1)**
**Tiếng Việt**: Phân tích tĩnh
**Định nghĩa**: Analysis của code structure mà không execute (dùng tools).

### Static Testing **(K2)**
**Tiếng Việt**: Kiểm thử tĩnh
**Định nghĩa**: Testing work products mà KHÔNG EXECUTE code.
**Methods**: Reviews, Static analysis
**Khác với**: Dynamic testing (execute code)

### Stress Testing **(K1)**
**Tiếng Việt**: Kiểm thử căng thẳng
**Định nghĩa**: Performance testing dưới load vượt quá limits bình thường.

### Stub **(K1)**
**Tiếng Việt**: Stub
**Định nghĩa**: Skeletal/temporary implementation của component, thay cho actual component.

### System Integration Testing **(K2)**
**Tiếng Việt**: Kiểm thử tích hợp hệ thống
**Định nghĩa**: Testing interfaces giữa systems, packages, microservices.

### System Testing **(K2)**
**Tiếng Việt**: Kiểm thử hệ thống
**Định nghĩa**: Testing toàn bộ system như một integrated whole.

---

## T

### TDD - Test-Driven Development **(K2)**
**Tiếng Việt**: Phát triển dẫn dắt bởi test
**Định nghĩa**: Approach viết tests TRƯỚC khi viết code.
**Cycle**: Red (write failing test) → Green (write code to pass) → Refactor

### Technical Review **(K2)**
**Tiếng Việt**: Đánh giá kỹ thuật
**Định nghĩa**: Formal review bởi technical experts để đánh giá technical quality.

### Test **(K1)**
**Tiếng Việt**: Bài kiểm thử
**Định nghĩa**: Set of activities để identify differences giữa actual và expected results.

### Test Analysis **(K2)**
**Tiếng Việt**: Phân tích kiểm thử
**Định nghĩa**: Activity analyze test basis để identify testable features và define test conditions.

### Test Approach **(K2)**
**Tiếng Việt**: Cách tiếp cận kiểm thử
**Định nghĩa**: Implementation của test strategy cho một project.

### Test Automation **(K1)**
**Tiếng Việt**: Tự động hóa kiểm thử
**Định nghĩa**: Sử dụng software tools để execute tests và compare results.

### Test Basis **(K2)**
**Tiếng Việt**: Cơ sở kiểm thử
**Định nghĩa**: Work products dùng để derive test cases (requirements, design, code, risk analysis).

### Test Case **(K2)**
**Tiếng Việt**: Ca kiểm thử
**Định nghĩa**: Set of preconditions, inputs, actions, expected results và postconditions.
**Components**: Test case ID, Title, Preconditions, Steps, Test data, Expected results, Priority

### Test Closure **(K2)**
**Tiếng Việt**: Kết thúc kiểm thử
**Định nghĩa**: Activity tổng kết testing sau khi đã đạt exit criteria.

### Test Completion Report **(K2)**
**Tiếng Việt**: Báo cáo hoàn thành kiểm thử
**Định nghĩa**: Report tổng kết testing activities và results.
**Includes**: Summary of testing, Metrics, Outstanding defects, Lessons learned

### Test Condition **(K2)**
**Tiếng Việt**: Điều kiện kiểm thử
**Định nghĩa**: Testable aspect của component/system (feature, function, quality attribute).

### Test Control **(K2)**
**Tiếng Việt**: Kiểm soát kiểm thử
**Định nghĩa**: Activity take actions để meet test plan objectives dựa trên test monitoring.

### Test Coverage **(K2)**
**Tiếng Việt**: Độ bao phủ kiểm thử
**Định nghĩa**: Extent mà test cases cover test basis/code.

### Test Data **(K1)**
**Tiếng Việt**: Dữ liệu kiểm thử
**Định nghĩa**: Data created/selected để thỏa preconditions và inputs của test cases.

### Test Design **(K2)**
**Tiếng Việt**: Thiết kế kiểm thử
**Định nghĩa**: Activity derive và specify test cases từ test conditions.

### Test Design Technique **(K2)**
**Tiếng Việt**: Kỹ thuật thiết kế kiểm thử
**Định nghĩa**: Defined way để derive test cases.
**Categories**: Black-box, White-box, Experience-based

### Test Environment **(K2)**
**Tiếng Việt**: Môi trường kiểm thử
**Định nghĩa**: Hardware, software, data, và infrastructure cần để execute tests.

### Test Execution **(K2)**
**Tiếng Việt**: Thực thi kiểm thử
**Định nghĩa**: Activity run tests và compare actual results với expected results.

### Test Implementation **(K2)**
**Tiếng Việt**: Triển khai kiểm thử
**Định nghĩa**: Activity prepare testware needed để execute tests (scripts, data, environment).

### Test Level **(K2)**
**Tiếng Việt**: Cấp độ kiểm thử
**Định nghĩa**: Specific instantiation of test process.
**5 Levels**: Component testing, Component integration testing, System testing, System integration testing, Acceptance testing

### Test Management **(K2)**
**Tiếng Việt**: Quản lý kiểm thử
**Định nghĩa**: Planning, estimating, monitoring, controlling test activities.

### Test Manager **(K1)**
**Tiếng Việt**: Quản lý kiểm thử
**Định nghĩa**: Role chịu trách nhiệm test management và test leadership.

### Test Monitoring **(K2)**
**Tiếng Việt**: Giám sát kiểm thử
**Định nghĩa**: Activity gather metrics và thông tin về test progress.

### Test Object **(K2)**
**Tiếng Việt**: Đối tượng kiểm thử
**Định nghĩa**: Component/system được test.

### Test Objective **(K2)**
**Tiếng Việt**: Mục tiêu kiểm thử
**Định nghĩa**: Reason/purpose của testing.
**Examples**: Find defects, Verify requirements, Gain confidence, Provide information

### Test Oracle **(K1)**
**Tiếng Việt**: Nguồn tham chiếu kiểm thử
**Định nghĩa**: Xem "Oracle"

### Test Plan **(K3)**
**Tiếng Việt**: Kế hoạch kiểm thử
**Định nghĩa**: Document mô tả test objectives, resources, approach, schedule, và activities.
**Includes**: Scope, Approach, Resources, Schedule, Entry/exit criteria, Risks

### Test Planning **(K3)**
**Tiếng Việt**: Lập kế hoạch kiểm thử
**Định nghĩa**: Activity define test objectives và approach để meet objectives trong constraints.

### Test Policy **(K1)**
**Tiếng Việt**: Chính sách kiểm thử
**Định nghĩa**: High-level document mô tả testing principles và objectives của organization.

### Test Procedure **(K2)**
**Tiếng Việt**: Thủ tục kiểm thử
**Định nghĩa**: Sequence of test cases in execution order, còn gọi là test script.

### Test Progress Report **(K2)**
**Tiếng Việt**: Báo cáo tiến độ kiểm thử
**Định nghĩa**: Report định kỳ về test progress so với test plan.
**Includes**: Status of tests, Defects found, Risks, Issues

### Test Report **(K2)**
**Tiếng Việt**: Báo cáo kiểm thử
**Định nghĩa**: Report về testing activities và results.
**Types**: Test progress report, Test completion report

### Test Script **(K1)**
**Tiếng Việt**: Kịch bản kiểm thử
**Định nghĩa**: Xem "Test Procedure" hoặc automation script.

### Test Session **(K2)**
**Tiếng Việt**: Phiên kiểm thử
**Định nghĩa**: Uninterrupted period of testing, thường dùng trong exploratory testing (time-boxed).

### Test Strategy **(K2)**
**Tiếng Việt**: Chiến lược kiểm thử
**Định nghĩa**: High-level description của test levels, test approach, và resources cho organization/program.

### Test Suite **(K2)**
**Tiếng Việt**: Bộ kiểm thử
**Định nghĩa**: Set of test cases hoặc test procedures để execute cho specific objective.

### Test Technique **(K2)**
**Tiếng Việt**: Kỹ thuật kiểm thử
**Định nghĩa**: Xem "Test Design Technique"

### Test Type **(K2)**
**Tiếng Việt**: Loại kiểm thử
**Định nghĩa**: Group of test activities để test specific characteristics.
**4 Types**: Functional, Non-functional, Black-box, White-box

### Testability **(K2)**
**Tiếng Việt**: Khả năng kiểm thử
**Định nghĩa**: Degree mà test conditions có thể được established cho test object.

### Tester **(K1)**
**Tiếng Việt**: Người kiểm thử
**Định nghĩa**: Role skilled trong testing activities.

### Testing **(K2)**
**Tiếng Việt**: Kiểm thử
**[ISTQB]**: Process gồm planning, preparation, và evaluation để determine một test object satisfies requirements.
**Khác với**: Debugging (developers fix defects)

### Testing Quadrants **(K2)**
**Tiếng Việt**: Các góc phần tư kiểm thử
**Định nghĩa**: Model với 4 quadrants support team understand test types và levels:
- **Q1**: Technology-facing, Support development (Unit tests, Component tests)
- **Q2**: Business-facing, Support development (Functional tests, Story tests)
- **Q3**: Business-facing, Critique product (Exploratory, Usability, UAT)
- **Q4**: Technology-facing, Critique product (Performance, Security, Scalability)

### Testware **(K2)**
**Tiếng Việt**: Sản phẩm kiểm thử
**Định nghĩa**: Work products produced trong test process.
**Examples**: Test plans, test cases, test scripts, test data, test reports

### Think Time **(K1)**
**Tiếng Việt**: Thời gian suy nghĩ
**Định nghĩa**: Thời gian user nghĩ trước khi thực hiện action tiếp theo.

### Three-Point Estimation **(K3)**
**Tiếng Việt**: Ước lượng ba điểm
**Định nghĩa**: Estimation technique dùng 3 estimates:
- **Optimistic (a)**: Best case
- **Most likely (m)**: Most realistic
- **Pessimistic (b)**: Worst case
**Formula**: E = (a + 4m + b) / 6

### Traceability **(K2)**
**Tiếng Việt**: Khả năng truy vết
**Định nghĩa**: Ability trace requirements → test cases → test results → defects.

### Transaction **(K1)**
**Tiếng Việt**: Giao dịch
**Định nghĩa**: Set of activities từ initiation đến completion của one or more processes.

---

## U

### Unit Testing **(K2)**
**Tiếng Việt**: Kiểm thử đơn vị
**Định nghĩa**: Xem "Component Testing"

### Usability **(K2)**
**Tiếng Việt**: Khả năng sử dụng
**Định nghĩa**: Mức độ user có thể sử dụng product một cách effective, efficient, và satisfying.

### Usability Testing **(K1)**
**Tiếng Việt**: Kiểm thử khả năng sử dụng
**Định nghĩa**: Testing để đánh giá usability của product.

### Use Case **(K1)**
**Tiếng Việt**: Ca sử dụng
**Định nghĩa**: Sequence of transactions giữa external actor và system để achieve goal.

### User Acceptance Testing (UAT) **(K2)**
**Tiếng Việt**: Kiểm thử chấp nhận người dùng
**Định nghĩa**: Acceptance testing do intended users thực hiện.

### User Story **(K2)**
**Tiếng Việt**: Câu chuyện người dùng
**Định nghĩa**: High-level user/business requirement ở format:
"As a [role], I want [feature], so that [benefit]"
**3 C's**: Card, Conversation, Confirmation

---

## V

### Validation **(K2)**
**Tiếng Việt**: Xác nhận
**[ISTQB]**: Confirmation product meets stakeholders' actual needs (building the RIGHT product).
**Khác với**: Verification (building the product RIGHT)

### Valid Partition **(K3)**
**Tiếng Việt**: Phân vùng hợp lệ
**Định nghĩa**: Equivalence partition chứa valid values (hệ thống accept).

### Verification **(K2)**
**Tiếng Việt**: Kiểm chứng
**[ISTQB]**: Confirmation work product meets specified requirements (building the product RIGHT).
**Khác với**: Validation (building the RIGHT product)

### Virtual User **(K1)**
**Tiếng Việt**: Người dùng ảo
**Định nghĩa**: Simulation của user activities trong performance testing.

### V-Model **(K2)**
**Tiếng Việt**: Mô hình chữ V
**Định nghĩa**: Sequential SDLC model mỗi development phase tương ứng với test level:
- Requirements ↔ Acceptance Testing
- Design ↔ System Testing
- Detailed Design ↔ Integration Testing
- Code ↔ Component Testing

---

## W

### Walkthrough **(K2)**
**Tiếng Việt**: Duyệt bước
**Định nghĩa**: Type of review mà author leads participants qua work product.

### Waterfall Model **(K2)**
**Tiếng Việt**: Mô hình thác nước
**Định nghĩa**: Sequential SDLC model mỗi phase chảy xuống phase tiếp theo như thác nước.
**Phases**: Requirements → Design → Implementation → Testing → Maintenance

### White-Box Testing **(K2)**
**Tiếng Việt**: Kiểm thử hộp trắng
**Định nghĩa**: Testing technique dựa trên internal structure của test object.
**Examples**: Statement testing, Branch testing, Path testing

### Whole Team Approach **(K2)**
**Tiếng Việt**: Cách tiếp cận toàn đội
**Định nghĩa**: Practice mà mọi team member chịu trách nhiệm product quality, không chỉ testers.

### Wideband Delphi **(K3)**
**Tiếng Việt**: Delphi băng thông rộng
**Định nghĩa**: Estimation technique sử dụng expert consensus.
**Also known as**: Planning Poker (Agile version)

---

## Các thuật ngữ KHÔNG NÊN dịch sang tiếng Việt

Những thuật ngữ sau **luôn sử dụng tiếng Anh** trong công việc:

- **Agile, Scrum, Sprint, Backlog**
- **DevOps, CI/CD, Pipeline**
- **API, REST, SOAP**
- **Bug, Defect, Issue**
- **Commit, Push, Pull Request, Merge**
- **Framework, Library, Plugin**
- **Git, GitHub, GitLab**
- **Mock, Stub, Spy**
- **Refactoring**
- **Repository, Branch**
- **Selenium, Cypress, JMeter** (tên tools)
- **UI, UX, GUI**

---

## Các thuật ngữ dễ nhầm lẫn

### 1. Error vs Defect vs Failure
- **Error (Sai sót)**: Human action → produce wrong result
- **Defect (Khuyết tật)**: Flaw in code/document (result of error)
- **Failure (Hỏng hóc)**: System deviation from expected (result of defect)
**Flow**: Error → Defect → Failure

### 2. Verification vs Validation
- **Verification**: Are we building the product RIGHT? (theo spec)
- **Validation**: Are we building the RIGHT product? (theo user needs)

### 3. Severity vs Priority
- **Severity**: Technical impact (얼마나 nghiêm trọng?)
- **Priority**: Business urgency (cần fix sớm thế nào?)
**Example**: Typo on homepage = Low severity, High priority

### 4. Confirmation Testing vs Regression Testing
- **Confirmation Testing**: Verify defect ĐÃ FIX
- **Regression Testing**: Verify fix không GÂY LỖI MỚI

### 5. Black-box vs White-box
- **Black-box**: Test WHAT (functionality) - không cần biết code
- **White-box**: Test HOW (structure) - cần biết code

### 6. Functional vs Non-functional
- **Functional**: WHAT system does (features)
- **Non-functional**: HOW WELL system works (performance, security)

### 7. Static vs Dynamic Testing
- **Static**: Không execute code (reviews, analysis)
- **Dynamic**: Execute code (run tests)

### 8. Test Level vs Test Type
- **Test Level**: WHEN to test (component, system, acceptance)
- **Test Type**: WHAT ASPECT to test (functional, performance, security)

### 9. Entry Criteria vs Exit Criteria
- **Entry Criteria**: Conditions BEFORE starting
- **Exit Criteria**: Conditions BEFORE stopping

### 10. Test Basis vs Test Object
- **Test Basis**: Documents dùng để design tests (requirements, specs)
- **Test Object**: Thing being tested (software, system)

---

## Abbreviations (Viết tắt) thường dùng

| Viết tắt | Đầy đủ | Tiếng Việt |
|----------|--------|------------|
| **ATDD** | Acceptance Test-Driven Development | Phát triển dẫn dắt bởi test chấp nhận |
| **BDD** | Behavior-Driven Development | Phát triển dẫn dắt bởi hành vi |
| **BVA** | Boundary Value Analysis | Phân tích giá trị biên |
| **CI/CD** | Continuous Integration/Continuous Delivery | Tích hợp liên tục/Phân phối liên tục |
| **CTFL** | Certified Tester Foundation Level | Chứng chỉ tester cấp nền tảng |
| **DoD** | Definition of Done | Định nghĩa hoàn thành |
| **DoR** | Definition of Ready | Định nghĩa sẵn sàng |
| **EP** | Equivalence Partitioning | Phân vùng tương đương |
| **ISTQB** | International Software Testing Qualifications Board | Hội đồng chứng chỉ kiểm thử phần mềm quốc tế |
| **OAT** | Operational Acceptance Testing | Kiểm thử chấp nhận vận hành |
| **QA** | Quality Assurance | Đảm bảo chất lượng |
| **QC** | Quality Control | Kiểm soát chất lượng |
| **SDLC** | Software Development Lifecycle | Vòng đời phát triển phần mềm |
| **SUT** | System Under Test | Hệ thống đang được kiểm thử |
| **TDD** | Test-Driven Development | Phát triển dẫn dắt bởi test |
| **UAT** | User Acceptance Testing | Kiểm thử chấp nhận người dùng |
| **UI** | User Interface | Giao diện người dùng |
| **UX** | User Experience | Trải nghiệm người dùng |

---

## Cách học thuật ngữ hiệu quả

### 1. Flashcards
Tạo flashcards (dùng Anki hoặc Quizlet):
- **Front**: Thuật ngữ tiếng Anh
- **Back**: Định nghĩa + Ví dụ thực tế

### 2. Active Recall
Thay vì đọc lại, tự hỏi:
- "Boundary Value Analysis là gì?"
- "Khác biệt giữa Verification và Validation?"

### 3. Spaced Repetition
Ôn lại theo lịch:
- Ngày 1: Học
- Ngày 2: Ôn lại
- Ngày 7: Ôn lại
- Ngày 30: Ôn lại

### 4. Use in Context
Sử dụng trong câu:
- "I will use Equivalence Partitioning to design test cases for the login form"
- "The Severity is Critical but Priority is Low"

### 5. Teach Others
Giải thích thuật ngữ cho người khác bằng tiếng Việt.

---

## Priority Học

### Must Know (K1 - Nhớ)
40 thuật ngữ CƠ BẢN NHẤT - học trước:
Test, Testing, Testware, Defect, Error, Failure, Bug, Test Case, Test Suite, Test Plan, Coverage, Quality, QA, QC, Verification, Validation, Black-box, White-box, Functional, Non-functional, Static, Dynamic, Component Testing, Integration Testing, System Testing, Acceptance Testing, Manual Testing, Automation, Pass, Fail, Expected Result, Actual Result, Requirement, SDLC, Agile, Waterfall, Tester, Developer, Stakeholder, Review

### Should Know (K2 - Hiểu)
80 thuật ngữ QUAN TRỌNG - học sau khi nắm K1:
Tất cả thuật ngữ đánh dấu **(K2)** trong glossary trên

### Must Apply (K3 - Áp dụng)
20 thuật ngữ CẦN THỰC HÀNH:
EP, BVA, Decision Table, State Transition, Statement Coverage, Branch Coverage, Test Plan, Test Case, Defect Report, Priority, Severity, Risk Level, Entry Criteria, Exit Criteria, Test Estimation, etc.

---

## Next Steps

- 📚 **Bắt đầu học**: [Module 1.1 - Testing là gì?](giai-doan-1-nen-tang/module-1.1-testing-la-gi.md)
- 📖 **Full Glossary**: Tham khảo [ISTQB Glossary v4.6.2](../glossary.md) để tra cứu chi tiết

---

**Tips**: Print glossary này ra và đặt bên cạnh khi học. Mỗi khi gặp thuật ngữ mới, highlight và làm flashcard ngay!

**Ngày cập nhật**: November 2025
**Version**: 1.0.0
**Based on**: ISTQB Standard Glossary v4.6.2
