# Project 3: Education Platform Testing (LearnVN)

## 🎯 Mục Tiêu Project

Áp dụng kiến thức testing vào domain **Online Education** với focus vào:
- **Content Management** (courses, lessons, videos)
- **Video Streaming** (performance, quality)
- **Interactive Learning** (quizzes, assignments)
- **User Experience** (learner journey, instructor tools)
- **Multi-role Testing** (Student, Instructor, Admin)

**Thời gian**: 5-7 ngày

---

## 📋 Project Overview

### About LearnVN

**LearnVN** là nền tảng học online giống Udemy, Coursera, cho phép:
- **Instructors**: Tạo và bán khóa học
- **Students**: Mua và học khóa học
- **Content**: Video lectures, quizzes, assignments, certificates
- **Business Model**: Marketplace (revenue split 70% instructor / 30% platform)

### Project Context

**Company**: LearnVN EdTech Startup
**Release**: v4.0 - Major feature update
**Timeline**: 6 weeks (Sprint 1-3)

### Scope

**In Scope**:
✅ User registration (Student, Instructor)
✅ Course creation and management
✅ Video upload and streaming
✅ Course enrollment and payment
✅ Learning experience (watch videos, take quizzes)
✅ Progress tracking and certificates
✅ Reviews and ratings

**Out of Scope**:
❌ Live streaming classes
❌ Mobile apps (web only)
❌ Corporate/Enterprise features
❌ Advanced analytics

---

## 📖 Requirements

### Epic 1: User Management (Multi-Role)

**US-101: Student Registration**
```
As a learner
I want to register as a student
So that I can enroll in courses

Acceptance Criteria:
- Register with email + password OR social login (Google, Facebook)
- Email verification required
- Profile fields: Name, Bio, Avatar (optional)
- Password: 8-20 chars, letter + number
- Free registration (no payment)
- Cannot register instructor and student with same email
```

**US-102: Instructor Registration**
```
As a teacher
I want to register as an instructor
So that I can create and sell courses

Acceptance Criteria:
- Register with email + password
- Additional fields:
  - Teaching expertise (dropdown: IT, Business, Design, etc.)
  - Bio (min 100 chars)
  - Video introduction (< 2 mins)
- Instructor verification process:
  - Submit credentials/portfolio
  - Admin review (24-48 hours)
- Payout information (bank account for earnings)
- Instructor agreement acceptance
```

**US-103: User Profile Management**
```
As a user (Student/Instructor)
I want to manage my profile
So that I can update my information

Acceptance Criteria:
- Edit: Name, Bio, Avatar
- Change password (old password required)
- Email change (verification required)
- Instructor: Can upload new intro video
- Student: View enrolled courses, progress
- Instructor: View created courses, earnings
```

### Epic 2: Course Creation (Instructor)

**US-201: Create Course**
```
As an instructor
I want to create a new course
So that I can teach students

Acceptance Criteria:
- Course fields:
  - Title (max 100 chars)
  - Subtitle (max 120 chars)
  - Description (rich text editor)
  - Category (IT, Business, Design, etc.)
  - Level (Beginner, Intermediate, Advanced)
  - Language (Vietnamese, English)
  - Price (Free or 99,000 - 5,000,000 VND)
  - Course image (16:9 ratio, max 2MB)
  - Promo video (< 2 mins, optional)
- Course status: Draft (not published)
- Save as draft (autosave every 30s)
- Cannot publish empty course
```

**US-202: Create Curriculum (Sections & Lectures)**
```
As an instructor
I want to organize course content
So that students can learn systematically

Acceptance Criteria:
- Structure:
  - Course → Sections → Lectures
  - Example: Section 1 "Introduction" → Lecture 1.1 "Welcome"
- Section:
  - Title (required)
  - Description (optional)
  - Learning objectives
- Lecture types:
  - Video lecture (primary)
  - Text article
  - Quiz
  - Assignment
  - Downloadable resources (PDF, ZIP)
- Drag & drop to reorder sections/lectures
- Preview course structure
- Must have ≥ 1 section, ≥ 3 lectures to publish
```

**US-203: Upload Video Lectures**
```
As an instructor
I want to upload video lectures
So that students can watch them

Acceptance Criteria:
- Video upload:
  - Formats: MP4, MOV, AVI
  - Max size: 5GB per video
  - Resolution: 720p min, 1080p recommended
  - Duration: 2 mins - 4 hours
- Upload process:
  - Progress bar
  - Pause/Resume upload
  - Background upload (can navigate away)
- Video processing:
  - Auto-generate multiple qualities (360p, 480p, 720p, 1080p)
  - Subtitles auto-generation (optional)
  - Processing time: ~10 mins for 1-hour video
- Video player:
  - HTML5 player
  - Playback speed control (0.5x - 2x)
  - Quality selection
  - Captions/subtitles
  - Download (if instructor allows)
```

**US-204: Create Quiz**
```
As an instructor
I want to create quizzes
So that I can assess student learning

Acceptance Criteria:
- Quiz types:
  - Multiple choice (single answer)
  - Multiple select (multiple answers)
  - True/False
- Quiz fields:
  - Question (required)
  - Options (2-6 options for MCQ)
  - Correct answer(s) (required)
  - Explanation (optional, shown after submission)
- Quiz settings:
  - Passing score (e.g., 70%)
  - Attempts allowed (1, 2, 3, Unlimited)
  - Time limit (optional)
- Preview quiz before publish
```

**US-205: Publish Course**
```
As an instructor
I want to publish my course
So that students can enroll

Acceptance Criteria:
- Publish checklist (all must be met):
  [ ] Title & description complete
  [ ] Course image uploaded
  [ ] At least 1 section
  [ ] At least 3 lectures
  [ ] At least 30 mins total video content
  [ ] Price set (Free or Paid)
- Submit for review:
  - Admin review (quality check)
  - Approval within 24 hours
  - If rejected: Feedback provided
- Once approved:
  - Course live on marketplace
  - Instructor cannot unpublish (only archive)
```

### Epic 3: Course Discovery & Enrollment (Student)

**US-301: Browse Courses**
```
As a student
I want to browse courses
So that I can find what to learn

Acceptance Criteria:
- Homepage: Featured courses, Top-rated, New courses
- Categories: IT, Business, Design, Marketing, etc.
- Search:
  - By keyword (title, description, instructor)
  - Autocomplete suggestions
- Filter:
  - Category
  - Level (Beginner, Intermediate, Advanced)
  - Price (Free, Paid, Price range)
  - Language
  - Duration
  - Rating (4+ stars, 3+ stars)
- Sort:
  - Relevance (default)
  - Most Popular
  - Highest Rated
  - Newest
  - Price (Low to High, High to Low)
- Pagination: 12 courses per page
```

**US-302: Course Details Page**
```
As a student
I want to view course details
So that I can decide to enroll

Acceptance Criteria:
- Display:
  - Title, Subtitle, Description
  - Instructor name + rating
  - Course rating & reviews
  - Price
  - Course content (sections & lectures list)
  - Total duration, lecture count
  - What you'll learn (learning objectives)
  - Requirements
  - Sample video (promo or first lecture preview)
- Actions:
  - "Enroll Now" button (if not enrolled)
  - "Add to Cart" (if paid course)
  - "Add to Wishlist"
  - "Share" (social media)
- Related courses section
```

**US-303: Course Enrollment & Payment**
```
As a student
I want to enroll in a course
So that I can start learning

Acceptance Criteria:
- Free courses:
  - Click "Enroll Now"
  - Instant enrollment
  - Redirect to course player
- Paid courses:
  - Click "Enroll Now" or "Add to Cart"
  - Checkout page:
    - Course summary
    - Price, discounts
    - Payment methods: Credit card, Bank transfer, E-wallet
  - Payment processing
  - On success:
    - Enrollment confirmed
    - Email receipt
    - Access to course
- Course access:
  - Lifetime access (one-time payment)
  - Can watch unlimited times
  - Cannot transfer to another user
```

### Epic 4: Learning Experience (Student)

**US-401: Watch Video Lectures**
```
As a student
I want to watch video lectures
So that I can learn the content

Acceptance Criteria:
- Course player:
  - Video player (HTML5)
  - Curriculum sidebar (sections & lectures list)
  - Progress indicator (e.g., "Lecture 5 of 20")
- Video controls:
  - Play/Pause
  - Seek (timeline scrubbing)
  - Volume control
  - Fullscreen
  - Playback speed (0.5x, 0.75x, 1x, 1.25x, 1.5x, 2x)
  - Quality selection (Auto, 360p, 480p, 720p, 1080p)
  - Captions/subtitles toggle
- Auto-play next lecture (can disable in settings)
- Mark lecture as complete (checkbox)
- Lecture notes section
- Q&A section (ask questions)
```

**US-402: Take Quizzes**
```
As a student
I want to take quizzes
So that I can test my understanding

Acceptance Criteria:
- Quiz interface:
  - Display questions one by one OR all at once (instructor choice)
  - Multiple choice: Radio buttons (single answer)
  - Multiple select: Checkboxes (multiple answers)
  - True/False: Two buttons
- Submit quiz:
  - Show score immediately
  - Show correct/incorrect answers
  - Show explanations (if provided by instructor)
  - Pass/Fail status based on passing score
- Retry:
  - If allowed multiple attempts
  - Reset answers, start fresh
- Progress:
  - Must pass quiz to proceed (if instructor requires)
```

**US-403: Submit Assignments**
```
As a student
I want to submit assignments
So that I can practice and get feedback

Acceptance Criteria:
- Assignment page:
  - Instructions
  - Deadline (if set)
  - File upload (PDF, ZIP, images)
  - Text submission (for written answers)
- Submit assignment:
  - Upload file (max 50MB)
  - Add comments/notes
  - "Submit" button
- After submission:
  - Cannot edit (unless instructor allows resubmission)
  - Wait for instructor review
  - Get notification when graded
- Grading:
  - Instructor gives score (0-100)
  - Instructor feedback
```

**US-404: Course Completion & Certificate**
```
As a student
I want to get a certificate
So that I can prove I completed the course

Acceptance Criteria:
- Completion criteria:
  - Watch all required lectures (100%)
  - Pass all quizzes (if any)
  - Submit all assignments (if any)
- Certificate:
  - Auto-generated on completion
  - Displays: Student name, Course name, Date, Certificate ID
  - Downloadable as PDF
  - Shareable link (verify authenticity)
  - LinkedIn sharable
- Progress tracking:
  - Progress bar (e.g., "65% complete")
  - Estimated time to completion
```

### Epic 5: Reviews & Ratings

**US-501: Leave Course Review**
```
As a student
I want to review a course
So that I can share my experience

Acceptance Criteria:
- Can review only if:
  - Enrolled in course
  - Watched at least 25% of lectures
- Review form:
  - Rating: 1-5 stars (required)
  - Review text: Min 50 chars (optional)
  - Would you recommend? Yes/No
- Edit review (within 30 days)
- Reviews appear on course page
- Instructor can respond to reviews
```

---

## 🎬 Video Streaming Test Cases

### Test Case: Video Upload Performance

```
TC-VIDEO-001: Upload Large Video File (2GB)
───────────────────────────────────────────────────────
Objective: Verify large video uploads successfully
Technique: Performance, Boundary testing

Test Data:
  Video: lecture_01.mp4
  Size: 2GB
  Format: MP4
  Resolution: 1080p
  Duration: 2 hours

Steps:
  1. Login as instructor
  2. Navigate to course curriculum
  3. Click "Upload Video"
  4. Select lecture_01.mp4 (2GB)
  5. Monitor upload progress

Expected Result:
  ✅ Upload progress bar appears
  ✅ Upload completes within reasonable time:
     - With 10 Mbps: ~30 mins
     - With 50 Mbps: ~6 mins
  ✅ Can pause/resume upload
  ✅ Can navigate away (background upload)
  ✅ On completion: "Processing" status
  ✅ Video processing completes (~20 mins)
  ✅ Multiple qualities generated (360p-1080p)

Priority: P1
───────────────────────────────────────────────────────

TC-VIDEO-002: Video Playback Quality Switching
───────────────────────────────────────────────────────
Objective: Verify seamless quality switching
Technique: Functional, Usability

Test Data:
  Video: Available in 360p, 480p, 720p, 1080p
  Network: Throttle to simulate different speeds

Steps:
  1. Enroll in course as student
  2. Start playing video (Auto quality)
  3. Change quality: 1080p → 480p
  4. Change quality: 480p → 1080p
  5. Observe playback

Expected Result:
  ✅ Quality switches without stopping video
  ✅ Playback continues from same timestamp
  ✅ < 2s buffering when switching quality
  ✅ Picture quality updates immediately

Priority: P1
───────────────────────────────────────────────────────

TC-VIDEO-003: Concurrent Video Streaming (Load Test)
───────────────────────────────────────────────────────
Objective: Verify platform handles many concurrent viewers
Technique: Load testing
Tool: JMeter, Custom scripts

Test Scenario:
  • Users: 5,000 concurrent
  • All watching different videos simultaneously
  • Duration: 30 minutes
  • Monitor: Buffering, quality degradation, errors

Expected Result:
  ✅ All users can stream without interruption
  ✅ Buffering < 5% of playback time
  ✅ No video failures
  ✅ CDN load balanced
  ✅ Server CPU < 80%, Memory < 85%

Priority: P0 (Critical for launch)
───────────────────────────────────────────────────────
```

---

## 📚 Quiz & Assessment Test Cases

### Test Case: Quiz with Multiple Attempts

```
TC-QUIZ-001: Retake Quiz After Failing
───────────────────────────────────────────────────────
Objective: Verify student can retake quiz
Technique: State Transition Testing

Quiz Settings:
  • Passing score: 70%
  • Attempts allowed: 3
  • Total questions: 10
  • Time limit: None

Test Steps:

ATTEMPT 1:
  1. Start quiz
  2. Answer 5 questions correctly, 5 wrong
  3. Submit quiz
  Expected Result:
     ❌ Score: 50% (Fail)
     ✅ Message: "You need 70% to pass. Retries left: 2"
     ✅ "Retake Quiz" button appears

ATTEMPT 2:
  4. Click "Retake Quiz"
  5. Answer 7 correctly, 3 wrong
  6. Submit quiz
  Expected Result:
     ✅ Score: 70% (Pass)
     ✅ Message: "Congratulations! You passed."
     ✅ Quiz marked as complete
     ✅ Can proceed to next lecture

Priority: P1
───────────────────────────────────────────────────────

TC-QUIZ-002: Quiz Time Limit Enforcement
───────────────────────────────────────────────────────
Objective: Verify quiz auto-submits when time expires
Technique: Boundary testing

Quiz Settings:
  • Time limit: 10 minutes
  • Questions: 10

Steps:
  1. Start quiz
  2. Answer 7 questions
  3. Wait until timer shows "0:00"
  4. Do NOT click "Submit"

Expected Result:
  ✅ Quiz auto-submits at 0:00
  ✅ Only 7 answered questions scored
  ✅ 3 unanswered = incorrect
  ✅ Score calculated based on 7/10

Priority: P1
───────────────────────────────────────────────────────
```

---

## 🎯 Course Discovery Test Cases (Search & Filter)

### Test Case: Decision Table - Search & Filter Combination

```
TC-SEARCH-001: Search with Multiple Filters
───────────────────────────────────────────────────────
Objective: Verify search + filter returns correct results
Technique: Decision Table Testing

Decision Table:

┌─────────────┬────┬────┬────┬────┬────┬────┬────┬────┐
│ Conditions  │ R1 │ R2 │ R3 │ R4 │ R5 │ R6 │ R7 │ R8 │
├─────────────┼────┼────┼────┼────┼────┼────┼────┼────┤
│ Keyword?    │ Y  │ Y  │ Y  │ Y  │ N  │ N  │ N  │ N  │
│ Category?   │ Y  │ Y  │ N  │ N  │ Y  │ Y  │ N  │ N  │
│ Level?      │ Y  │ N  │ Y  │ N  │ Y  │ N  │ Y  │ N  │
├─────────────┼────┼────┼────┼────┼────┼────┼────┼────┤
│ Expected    │    │    │    │    │    │    │    │    │
├─────────────┼────┼────┼────┼────┼────┼────┼────┼────┤
│ Results     │ A∩B│ A∩C│ A∩D│ A  │ B∩D│ B  │ D  │All │
│             │ ∩D │    │    │    │    │    │    │    │
└─────────────┴────┴────┴────┴────┴────┴────┴────┴────┘

Legend:
A = Matching keyword
B = Matching category
D = Matching level

Test Cases:

Rule R1: Keyword + Category + Level
  Input:
    • Keyword: "Python"
    • Category: "IT"
    • Level: "Beginner"
  Expected: Courses with "Python", in IT category, Beginner level

Rule R8: No filters
  Input: All filters empty
  Expected: All published courses (sorted by Relevance)

Priority: P1
───────────────────────────────────────────────────────
```

---

## 👥 Multi-Role Testing Scenarios

### Scenario: Instructor Creates Course → Student Enrolls

```
MULTI-USER TEST SCENARIO
───────────────────────────────────────────────────────

Objective: Validate complete workflow from creation to enrollment

PHASE 1: INSTRUCTOR CREATES COURSE
───────────────────────────────────────────────────────
User: Instructor (instructor@learnvn.com)

Steps:
1. Login as instructor
2. Create new course:
   - Title: "Python for Beginners"
   - Category: IT
   - Level: Beginner
   - Price: 299,000 VND
3. Add curriculum:
   - Section 1: "Introduction"
     - Lecture 1.1: "Welcome" (Video, 5 mins)
     - Lecture 1.2: "Setup Python" (Video, 10 mins)
   - Section 2: "Variables & Data Types"
     - Lecture 2.1: "Variables" (Video, 15 mins)
     - Quiz 2.2: "Variables Quiz" (5 questions)
4. Upload videos (total 30 mins)
5. Create quiz (5 MCQ, passing score 60%)
6. Submit for review
7. Wait for admin approval (simulated)
8. Course published

Expected: Course live on marketplace

PHASE 2: STUDENT DISCOVERS COURSE
───────────────────────────────────────────────────────
User: Student (student@learnvn.com)

Steps:
9. Login as student
10. Search: "Python"
11. Filter: IT category, Beginner level
12. Find "Python for Beginners" course
13. Click course card → Course details page

Expected: Course appears in search results

PHASE 3: STUDENT ENROLLS
───────────────────────────────────────────────────────
14. On course details page, click "Enroll Now"
15. Checkout page appears
16. Select payment: Credit card
17. Enter card details (test card)
18. Complete payment

Expected:
  ✅ Payment successful
  ✅ Enrollment confirmed
  ✅ Redirect to course player

PHASE 4: STUDENT LEARNS
───────────────────────────────────────────────────────
19. Watch Lecture 1.1 (5 mins) → Mark complete
20. Watch Lecture 1.2 (10 mins) → Mark complete
21. Watch Lecture 2.1 (15 mins) → Mark complete
22. Take Quiz 2.2:
    - Attempt 1: 40% (Fail)
    - Attempt 2: 80% (Pass)

Expected:
  ✅ Progress: 100% (4/4 items complete)
  ✅ Certificate generated

PHASE 5: STUDENT LEAVES REVIEW
───────────────────────────────────────────────────────
23. After completion, leave review:
    - Rating: 5 stars
    - Review: "Great course for beginners!"
24. Submit review

Expected:
  ✅ Review appears on course page
  ✅ Course rating updated

PHASE 6: INSTRUCTOR VIEWS ANALYTICS
───────────────────────────────────────────────────────
25. Instructor logs in
26. Navigate to "My Courses" → "Python for Beginners"
27. View analytics:
    - Enrollments: 1
    - Revenue: 299,000 VND (before platform fee)
    - Completion rate: 100%
    - Average rating: 5.0

Expected: All data accurate

END-TO-END RESULT: ✅ PASS / ❌ FAIL
───────────────────────────────────────────────────────
```

---

## 📊 Performance Benchmarks

```
═══════════════════════════════════════════════════════════
PERFORMANCE REQUIREMENTS - LEARNVN v4.0
═══════════════════════════════════════════════════════════

RESPONSE TIME (95th percentile):

User Actions:
├─ Homepage load: < 2s
├─ Search results: < 1s
├─ Course details page: < 2s
├─ Video start playback: < 3s (initial buffering)
├─ Quiz submission: < 1s
└─ Enrollment/Payment: < 5s

Video Streaming:
├─ Initial buffering: < 3s
├─ Subsequent buffering: < 1% of playback time
├─ Quality switching: < 2s
└─ Adaptive bitrate: Adjust within 5s of network change

THROUGHPUT:

Concurrent Users:
├─ Normal load: 5,000 users
├─ Peak load: 15,000 users (during promotions)
└─ Video streams: 10,000 concurrent streams

Transactions:
├─ Course enrollments: 500/min
├─ Video uploads: 100/hour
└─ Quiz submissions: 1,000/min

CAPACITY:

Storage:
├─ Videos: 50 TB (CDN)
├─ User data: 10 TB (Database)
└─ Backups: 60 TB

Users:
├─ Students: 500,000
├─ Instructors: 10,000
└─ Courses: 50,000

AVAILABILITY:

Uptime: 99.5% (< 44 hours downtime/year)
Planned maintenance: Max 6 hours/month (off-peak)

═══════════════════════════════════════════════════════════
```

---

## 🎨 Usability Heuristics Evaluation

```
┌─────────────────────────────────────────────────────────┐
│    USABILITY HEURISTICS CHECKLIST (Nielsen's 10)        │
├─────────────────────────────────────────────────────────┤
│                                                         │
│  1. VISIBILITY OF SYSTEM STATUS                         │
│     [ ] Loading indicators during video upload          │
│     [ ] Progress bar during video processing            │
│     [ ] Course completion percentage visible            │
│     [ ] Video buffering indicator                       │
│                                                         │
│  2. MATCH BETWEEN SYSTEM AND REAL WORLD                 │
│     [ ] Use familiar terms (Enroll, Watch, Complete)    │
│     [ ] Logical navigation (Browse → Details → Enroll)  │
│     [ ] Icons intuitive (Play, Pause, etc.)             │
│                                                         │
│  3. USER CONTROL AND FREEDOM                            │
│     [ ] Can pause/resume video anytime                  │
│     [ ] Can skip lectures (if already know content)     │
│     [ ] Can unenroll (with refund policy)               │
│     [ ] Can edit reviews                                │
│                                                         │
│  4. CONSISTENCY AND STANDARDS                           │
│     [ ] UI consistent across pages                      │
│     [ ] Button styles consistent                        │
│     [ ] Navigation menu always in same place            │
│                                                         │
│  5. ERROR PREVENTION                                    │
│     [ ] Confirm before deleting course                  │
│     [ ] Warn if leaving quiz without submitting         │
│     [ ] Validate inputs (email format, etc.)            │
│                                                         │
│  6. RECOGNITION RATHER THAN RECALL                      │
│     [ ] Show enrolled courses on dashboard              │
│     [ ] Recently watched courses visible                │
│     [ ] Autocomplete in search                          │
│                                                         │
│  7. FLEXIBILITY AND EFFICIENCY OF USE                   │
│     [ ] Keyboard shortcuts (Space = play/pause)         │
│     [ ] Playback speed control (0.5x - 2x)              │
│     [ ] Bulk actions (mark multiple lectures complete)  │
│                                                         │
│  8. AESTHETIC AND MINIMALIST DESIGN                     │
│     [ ] Clean interface, not cluttered                  │
│     [ ] Focus on content (video player)                 │
│     [ ] Remove unnecessary elements                     │
│                                                         │
│  9. HELP USERS RECOGNIZE, DIAGNOSE, AND RECOVER         │
│     [ ] Clear error messages (not "Error 500")          │
│     [ ] Suggest fixes ("Invalid email format" + example)│
│     [ ] Help links visible                              │
│                                                         │
│  10. HELP AND DOCUMENTATION                             │
│     [ ] FAQ section                                     │
│     [ ] Help center with tutorials                      │
│     [ ] Tooltips for complex features                   │
│     [ ] Contact support easily accessible               │
│                                                         │
└─────────────────────────────────────────────────────────┘
```

---

## 📋 Deliverables Checklist

```
┌─────────────────────────────────────────────────────────┐
│     PROJECT 3 DELIVERABLES - EDUCATION PLATFORM         │
├─────────────────────────────────────────────────────────┤
│                                                         │
│  PLANNING:                                              │
│  [ ] Test Plan (EdTech-specific)                        │
│  [ ] Video Streaming Test Strategy                      │
│  [ ] Multi-Role Test Strategy                           │
│  [ ] Performance Test Plan (video CDN)                  │
│  [ ] Usability Test Plan                                │
│                                                         │
│  TEST CASES:                                            │
│  [ ] Functional Test Cases (250+ TCs)                   │
│      [ ] Instructor workflow (50 TCs)                   │
│      [ ] Student workflow (100 TCs)                     │
│      [ ] Video streaming (30 TCs)                       │
│      [ ] Quiz & assessment (40 TCs)                     │
│      [ ] Search & discovery (30 TCs)                    │
│  [ ] Performance Test Cases (Video CDN)                 │
│  [ ] Usability Test Scenarios                           │
│                                                         │
│  EXECUTION:                                             │
│  [ ] Multi-role test execution logs                     │
│  [ ] Video streaming performance results                │
│  [ ] Usability test findings                            │
│  [ ] Defect reports                                     │
│                                                         │
│  COMPLETION:                                            │
│  [ ] Test Completion Report                             │
│  [ ] Video Streaming Performance Report                 │
│  [ ] Usability Assessment Report                        │
│  [ ] Recommendations for Launch                         │
│                                                         │
└─────────────────────────────────────────────────────────┘
```

---

## 🎯 Unique Challenges in EdTech Testing

| Challenge | Testing Approach |
|-----------|-----------------|
| **Video Quality** | Test multiple resolutions, adaptive bitrate |
| **Large Files** | Test upload/download of 1GB+ files |
| **CDN Performance** | Test from different geographic locations |
| **Multi-Role** | Test workflows across Student, Instructor, Admin |
| **Content Piracy** | Test DRM, video download restrictions |
| **Progress Tracking** | Test accurate progress calculation |
| **Certificate Generation** | Test certificate data accuracy, uniqueness |
| **Concurrent Learning** | Test many students watching simultaneously |

---

## 📚 Key Differences from Previous Projects

| Aspect | E-commerce | Mobile Banking | Education |
|--------|------------|----------------|-----------|
| **Focus** | Transactions | Security | Content Delivery |
| **Critical Path** | Checkout | Transfer Money | Watch Videos |
| **Performance** | API speed | Transaction speed | Video streaming |
| **User Roles** | Buyer/Seller | User | Student/Instructor |
| **Content** | Product data | Financial data | Video content |
| **Storage** | Product images | Transaction logs | Video files (TB) |
| **Testing Priority** | Functional | Security | Performance (CDN) |

---

## 🎓 Learning Outcomes

After completing this project, you'll have experience in:

✅ **Content Management Testing**
   - File upload (large files)
   - Rich text editors
   - Multi-media content

✅ **Video Streaming Testing**
   - CDN performance
   - Adaptive bitrate streaming
   - Quality switching
   - Concurrent streams

✅ **Interactive Learning Testing**
   - Quiz logic and scoring
   - Progress tracking algorithms
   - Certificate generation

✅ **Multi-Role Testing**
   - Testing as Student
   - Testing as Instructor
   - Cross-role interactions

✅ **Usability Testing**
   - Heuristic evaluation
   - User journey testing
   - Learning experience optimization

---

## 🎉 Congratulations!

Bạn đã hoàn thành **3 comprehensive projects** covering:
1. **E-commerce** (Functional testing, Black-box techniques)
2. **Mobile Banking** (Security, Performance)
3. **Education Platform** (Content delivery, Multi-role)

You've applied **ALL knowledge** from 7 phases:
✅ Testing fundamentals
✅ Static testing
✅ Test levels & types
✅ Black-box techniques (EP, BVA, Decision Table, State Transition)
✅ White-box & Experience-based techniques
✅ Test management (planning, estimation, risk)
✅ Monitoring, reporting, configuration, defect management

---

## 🚀 Next Steps

1. **Review your work** across all 3 projects
2. **Self-assessment**: Can you apply each technique confidently?
3. **Prepare for ISTQB exam**: Move to mock exams
4. **Build portfolio**: Use these projects in job interviews

**You're ready for the ISTQB Foundation Level exam! 🎓**

---

**Good luck! 🚀**
