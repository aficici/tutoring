# TutorHub — Product Specification Document

## Overview

TutorHub is a two-sided marketplace that connects students and parents with expert tutors. The platform supports session booking, in-app messaging, payment processing, and tutor management — available on both web and mobile.

---

## Table of Contents

1. [User Roles](#1-user-roles)
2. [Subjects & Categories](#2-subjects--categories)
3. [Design System](#3-design-system)
4. [Pages & Screens](#4-pages--screens)
5. [Features by Role](#5-features-by-role)
6. [Booking Flow](#6-booking-flow)
7. [Payment System](#7-payment-system)
8. [In-App Messaging](#8-in-app-messaging)
9. [Admin Panel](#9-admin-panel)
10. [Tech Stack](#10-tech-stack)
11. [Database Schema](#11-database-schema)
12. [Mobile App](#12-mobile-app)
13. [Non-Functional Requirements](#13-non-functional-requirements)
14. [Math Diagnostic Test System](#14-math-diagnostic-test-system)
15. [Student Upload System](#15-student-upload-system)
16. [AI Homework Helper](#16-ai-homework-helper)
17. [Session Notes & Recap](#17-session-notes--recap)
18. [Structured Study Programs](#18-structured-study-programs)
19. [Group Sessions](#19-group-sessions)
20. [Student Progress Tracker](#20-student-progress-tracker)
21. [Gamification](#21-gamification)
22. [Tutor Availability Alerts](#22-tutor-availability-alerts)
23. [Cancellation & Refund Policy](#23-cancellation--refund-policy)
24. [Referral Program](#24-referral-program)
25. [Package Deals](#25-package-deals)
26. [Blog & Resource Center](#26-blog--resource-center)
27. [Tutor Background Check](#27-tutor-background-check)
28. [Two-Factor Authentication](#28-two-factor-authentication)
29. [Platform Chatbot](#29-platform-chatbot)

---

## 1. User Roles

### Student
- Browses and searches for tutors
- Books sessions
- Sends and receives messages
- Leaves reviews after sessions
- Manages upcoming and past sessions
- Linked to a parent account (optional)

### Parent
- Creates and manages child (student) profiles
- Books sessions on behalf of children
- Pays for sessions
- Monitors child's session history and progress
- Communicates with tutors

### Tutor
- Creates a profile with subjects, bio, credentials, pricing, and availability
- Receives and manages booking requests
- Shares Zoom / Google Meet links for online sessions
- Provides in-person session address (optional)
- Receives payments after platform commission
- Responds to messages

### Admin
- Approves or rejects tutor applications
- Manages all users (students, parents, tutors)
- Views platform earnings and commissions
- Handles disputes and support tickets
- Manages subjects and categories
- Views analytics and reports

---

## 2. Subjects & Categories

### Mathematics
- Algebra
- Pre-Calculus
- Calculus
- AP Calculus (AB & BC)
- Geometry
- Trigonometry
- Statistics
- Differential Equations
- Math Olympiad
- AMC 8 / AMC 10 / AMC 12
- AIME
- SAT Math

### Science
- Chemistry
- Physics

### Computer Science
- AP Computer Science
- Python Programming
- Vibe Coding (Creative / AI-assisted coding)

### Languages
- French
- German

### Humanities
- History

---

## 3. Design System

### Brand Identity
**Name:** TutorHub
**Tagline:** "Learn from the best. Wherever you are."

### Color Palette
| Role | Color | Hex |
|------|-------|-----|
| Primary | Deep Indigo | `#4F46E5` |
| Secondary | Soft Violet | `#7C3AED` |
| Accent | Mint Green | `#10B981` |
| Background (Light) | Off White | `#F9FAFB` |
| Background (Dark) | Slate | `#0F172A` |
| Text Primary | Charcoal | `#111827` |
| Text Secondary | Cool Gray | `#6B7280` |
| Success | Emerald | `#059669` |
| Warning | Amber | `#F59E0B` |
| Error | Red | `#EF4444` |

### Typography
- **Font:** Inter (Google Fonts)
- **Headings:** Inter Bold (700)
- **Body:** Inter Regular (400)
- **Labels/Captions:** Inter Medium (500)

### Component Style
- Rounded corners: `border-radius: 12px` (cards), `8px` (buttons)
- Subtle shadows on cards
- Glassmorphism effect on hero sections
- Smooth hover animations (scale + shadow)
- Dark mode support

### Iconography
- Library: Lucide Icons or Heroicons

---

## 4. Pages & Screens

### Public Pages (No Auth Required)
| Page | Path | Description |
|------|------|-------------|
| Landing | `/` | Hero, features, how it works, subject categories, CTA |
| Browse Tutors | `/tutors` | Search, filter, tutor cards grid |
| Tutor Profile | `/tutors/[id]` | Full tutor details, reviews, booking button |
| Subject Page | `/subjects/[subject]` | Subject overview + filtered tutor list |
| About | `/about` | Company info |
| Contact | `/contact` | Contact form |
| Pricing | `/pricing` | How pricing works, commission info |
| Sign Up | `/signup` | Role selection (Student / Parent / Tutor) |
| Login | `/login` | Email + password login |

### Student Pages
| Page | Path | Description |
|------|------|-------------|
| Dashboard | `/dashboard` | Upcoming sessions, messages, quick actions |
| My Sessions | `/sessions` | Past and upcoming sessions |
| Book Session | `/book/[tutorId]` | Select session type, date/time, add meeting link |
| Messages | `/messages` | Inbox with all conversations |
| Profile | `/profile` | Edit personal info |
| Reviews | `/reviews` | Reviews I've written |

### Parent Pages
| Page | Path | Description |
|------|------|-------------|
| Dashboard | `/dashboard` | Children's sessions overview |
| Children | `/children` | Manage child profiles |
| Sessions | `/sessions` | All sessions across children |
| Payments | `/payments` | Payment history, invoices |
| Messages | `/messages` | All conversations |

### Tutor Pages
| Page | Path | Description |
|------|------|-------------|
| Dashboard | `/dashboard` | Earnings overview, upcoming sessions, reviews |
| My Profile | `/profile` | Edit tutor profile, subjects, pricing |
| Availability | `/availability` | Set weekly availability schedule |
| Sessions | `/sessions` | Manage all sessions |
| Earnings | `/earnings` | Earnings, commission breakdown, payout history |
| Messages | `/messages` | All conversations |

### Admin Pages
| Page | Path | Description |
|------|------|-------------|
| Dashboard | `/admin` | Platform stats, revenue, user counts |
| Tutor Applications | `/admin/applications` | Review and approve/reject tutor profiles |
| Users | `/admin/users` | View, search, edit, suspend users |
| Sessions | `/admin/sessions` | All sessions across platform |
| Payments | `/admin/payments` | All transactions, commission earnings |
| Disputes | `/admin/disputes` | Handle user-reported issues |
| Subjects | `/admin/subjects` | Manage subject list |
| Analytics | `/admin/analytics` | Charts: revenue, active users, sessions |

---

## 5. Features by Role

### Tutor Profile (Public)
- Profile photo
- Full name
- Headline (e.g. "MIT Graduate | AP Calculus & Physics Expert")
- Bio / About Me
- Subjects taught (multi-select with tags)
- Education & credentials
- Hourly rate (per session)
- Session types offered: Online / In-Person / Both
- Availability (shown as calendar)
- Average rating (stars) + number of reviews
- Individual reviews with comments
- Session count ("120+ sessions completed")
- Verification badge (approved by admin)
- "Book a Session" button
- "Message" button

### Search & Filter (Browse Tutors Page)
Filters:
- Subject / Category
- Session type (Online / In-Person / Both)
- Price range ($/hr)
- Rating (minimum stars)
- Availability (day of week)
- Location (city — for in-person)

Sort options:
- Most Popular
- Highest Rated
- Lowest Price
- Most Sessions

---

## 6. Booking Flow

### Step 1 — Select Session Type
- Online (Zoom / Google Meet)
- In-Person

### Step 2 — Select Date & Time
- Calendar view of tutor's availability
- Student picks a time slot

### Step 3 — Session Details
- Duration (30 min / 60 min / 90 min)
- Subject (from tutor's offered subjects)
- Notes to tutor (optional)
- For Online: student shares their Zoom/Google Meet link OR tutor shares theirs
- For In-Person: tutor's location is shown

### Step 4 — Payment
- Show session price
- Show platform fee (no visible line item — bundled)
- Pay via: Stripe (card), Zelle, or Venmo
- For Zelle/Venmo: manual confirmation step (student marks as paid, admin or tutor confirms)

### Step 5 — Confirmation
- Booking confirmed page
- Email confirmation sent to both parties
- Session appears in both dashboards

### After Session
- Student/Parent prompted to leave a review (rating + comment)
- Tutor receives payout (session fee minus 35% commission)

---

## 7. Payment System

### Commission Model
- Platform takes **35% commission** from every session
- Tutor receives **65%** of the session fee

**Example:**
- Session Price: $100
- Platform Commission: $35
- Tutor Payout: $65

### Payment Methods
| Method | Integration |
|--------|------------|
| Credit / Debit Card | Stripe |
| Zelle | Manual (user submits payment proof or admin confirms) |
| Venmo | Manual (same as Zelle) |

### Payout to Tutors
- Tutors add their payout preference (Stripe Connect, Zelle number, or Venmo handle)
- Payouts processed after session is completed
- Tutor can view full earnings breakdown in `/earnings`

### Invoices
- Auto-generated invoice per session for parents/students
- Downloadable as PDF

---

## 8. In-App Messaging

- Real-time chat between: Student ↔ Tutor, Parent ↔ Tutor
- Message threads organized by contact
- Unread message badge on nav icon
- Supports text messages
- Supports file attachments (PDF, images — for homework/notes)
- Notifications: email + push (mobile)
- Message history persists indefinitely

---

## 9. Admin Panel

### Dashboard Stats
- Total users (students, parents, tutors)
- Total sessions (today, this week, this month)
- Total platform revenue (commissions earned)
- Pending tutor applications
- Open disputes

### Tutor Applications
- List of tutors with status: Pending / Approved / Rejected
- Admin can view full tutor profile before approving
- Approve → tutor becomes searchable on platform
- Reject → tutor notified via email with reason

### User Management
- Search by name, email, role
- View user profile details
- Suspend / reactivate accounts
- Reset passwords

### Session Management
- View all sessions (filter by status, date, user)
- Cancel sessions (with refund trigger)

### Payments & Revenue
- All transactions table
- Filter by date range, method, status
- Total commission earned
- Export to CSV

### Disputes
- User-reported issues
- Admin can message both parties
- Mark as resolved / refund session

### Analytics
- Revenue over time (line chart)
- Sessions per subject (bar chart)
- New user signups (line chart)
- Tutor approval rate

---

## 10. Tech Stack

### Recommended Stack

| Layer | Technology |
|-------|-----------|
| Frontend (Web) | Next.js 14 (App Router) + TypeScript |
| Styling | Tailwind CSS + shadcn/ui |
| Mobile App | React Native (Expo) |
| Backend / API | Next.js API Routes or Node.js + Express |
| Database | PostgreSQL (via Neon or Supabase) |
| ORM | Prisma |
| Authentication | NextAuth.js or Clerk |
| Real-time Messaging | Supabase Realtime or Pusher |
| Payments | Stripe (cards + Stripe Connect for payouts) |
| File Storage | AWS S3 or Cloudflare R2 |
| Email | Resend or SendGrid |
| Deployment (Web) | Vercel |
| Deployment (Mobile) | Expo EAS Build |

---

## 11. Database Schema

### Users Table
```sql
users (
  id            UUID PRIMARY KEY,
  email         TEXT UNIQUE NOT NULL,
  password_hash TEXT NOT NULL,
  role          ENUM('student', 'parent', 'tutor', 'admin'),
  full_name     TEXT,
  avatar_url    TEXT,
  created_at    TIMESTAMP,
  is_active     BOOLEAN DEFAULT true
)
```

### Tutor Profiles Table
```sql
tutor_profiles (
  id              UUID PRIMARY KEY,
  user_id         UUID REFERENCES users(id),
  headline        TEXT,
  bio             TEXT,
  hourly_rate     DECIMAL,
  session_types   TEXT[], -- ['online', 'in_person']
  education       JSONB,
  credentials     TEXT,
  is_approved     BOOLEAN DEFAULT false,
  total_sessions  INT DEFAULT 0,
  avg_rating      DECIMAL DEFAULT 0,
  created_at      TIMESTAMP
)
```

### Subjects Table
```sql
subjects (
  id          UUID PRIMARY KEY,
  name        TEXT NOT NULL,
  category    TEXT NOT NULL,
  slug        TEXT UNIQUE
)

tutor_subjects (
  tutor_id    UUID REFERENCES tutor_profiles(id),
  subject_id  UUID REFERENCES subjects(id),
  PRIMARY KEY (tutor_id, subject_id)
)
```

### Availability Table
```sql
availability (
  id          UUID PRIMARY KEY,
  tutor_id    UUID REFERENCES tutor_profiles(id),
  day_of_week INT, -- 0=Sunday, 6=Saturday
  start_time  TIME,
  end_time    TIME
)
```

### Sessions Table
```sql
sessions (
  id              UUID PRIMARY KEY,
  tutor_id        UUID REFERENCES users(id),
  student_id      UUID REFERENCES users(id),
  subject_id      UUID REFERENCES subjects(id),
  session_type    ENUM('online', 'in_person'),
  scheduled_at    TIMESTAMP,
  duration_mins   INT,
  meeting_link    TEXT, -- Zoom or Google Meet URL
  location        TEXT, -- for in-person
  notes           TEXT,
  status          ENUM('pending', 'confirmed', 'completed', 'cancelled'),
  price           DECIMAL,
  created_at      TIMESTAMP
)
```

### Payments Table
```sql
payments (
  id              UUID PRIMARY KEY,
  session_id      UUID REFERENCES sessions(id),
  payer_id        UUID REFERENCES users(id),
  amount          DECIMAL,
  commission      DECIMAL, -- 35% of amount
  tutor_payout    DECIMAL, -- 65% of amount
  method          ENUM('stripe', 'zelle', 'venmo'),
  status          ENUM('pending', 'completed', 'refunded'),
  stripe_id       TEXT,
  created_at      TIMESTAMP
)
```

### Messages Table
```sql
messages (
  id          UUID PRIMARY KEY,
  sender_id   UUID REFERENCES users(id),
  receiver_id UUID REFERENCES users(id),
  content     TEXT,
  attachment  TEXT, -- file URL
  is_read     BOOLEAN DEFAULT false,
  created_at  TIMESTAMP
)
```

### Reviews Table
```sql
reviews (
  id          UUID PRIMARY KEY,
  session_id  UUID REFERENCES sessions(id),
  reviewer_id UUID REFERENCES users(id),
  tutor_id    UUID REFERENCES tutor_profiles(id),
  rating      INT CHECK (rating BETWEEN 1 AND 5),
  comment     TEXT,
  created_at  TIMESTAMP
)
```

### Children Table (Parent → Student links)
```sql
children (
  id          UUID PRIMARY KEY,
  parent_id   UUID REFERENCES users(id),
  student_id  UUID REFERENCES users(id)
)
```

---

## 12. Mobile App

### Platform
- iOS + Android via **React Native (Expo)**

### Screens (mirrors web functionality)
- Onboarding / Welcome
- Sign Up / Login
- Browse Tutors (with search & filters)
- Tutor Profile
- Book Session Flow
- My Sessions
- Messages (real-time chat)
- Notifications
- Profile & Settings
- Earnings (tutor only)

### Mobile-Specific Features
- Push notifications (new message, booking confirmed, session reminder)
- Biometric login (Face ID / Fingerprint)
- Native calendar integration for session reminders

---

## 13. Non-Functional Requirements

### Performance
- Page load under 2 seconds (web)
- App launch under 3 seconds (mobile)
- Real-time messages delivered under 500ms

### Security
- All passwords hashed (bcrypt)
- JWT or session-based authentication
- HTTPS enforced
- Input validation and sanitization
- Role-based access control (RBAC)
- Stripe PCI-compliant payment handling

### Scalability
- Stateless API design
- Database connection pooling
- CDN for static assets and images

### Accessibility
- WCAG 2.1 AA compliant
- Keyboard navigable
- Screen reader compatible

### Notifications
- Email: booking confirmations, session reminders (24h before), review prompts, approval status
- Push (mobile): new messages, session reminders, booking updates

---

*Document Version: 1.1*
*Last Updated: March 2026*

---

## 14. Math Diagnostic Test System

### Overview

The Math Diagnostic Test is an adaptive, combined assessment that covers all math topics offered on the platform. It identifies a student's knowledge gaps and weak areas, then generates a detailed Report Card with personalized suggestions and tutor recommendations.

The test is available:
- **Before booking** — as a placement tool to find the right tutor
- **Anytime from the student dashboard** — to track progress over time

**Retake policy:** Once per week per subject level.

---

### Math Topics Covered

The diagnostic branches across all platform math subjects:

| Topic Area | Subtopics |
|------------|-----------|
| Algebra | Linear equations, inequalities, systems of equations, polynomials, factoring, quadratics, functions |
| Geometry | Angles, triangles, circles, area/perimeter, coordinate geometry, proofs, transformations |
| Trigonometry | Unit circle, trig functions, identities, inverse trig, graphs, law of sines/cosines |
| Pre-Calculus | Functions & graphs, exponential/logarithmic functions, sequences & series, conic sections, limits intro |
| Calculus | Limits, derivatives, applications of derivatives, integrals, applications of integrals, FTC |
| AP Calculus AB/BC | All Calculus topics + series (BC), parametric/polar (BC), L'Hôpital's rule |
| Statistics | Descriptive stats, probability, distributions, hypothesis testing, confidence intervals, regression |
| Differential Equations | First-order ODEs, separable equations, linear equations, slope fields |
| Geometry (Olympiad) | Advanced proofs, circle theorems, similarity, power of a point |
| AMC / AIME / Olympiad | Number theory, combinatorics, advanced algebra, clever problem-solving techniques |
| SAT Math | Heart of Algebra, Problem Solving & Data Analysis, Passport to Advanced Math |

---

### Adaptive Test Engine

#### How It Works

1. The test starts with **baseline questions** across all major topic areas (one question per area).
2. Based on the student's response:
   - **Correct** → branch to a harder question in that subtopic
   - **Incorrect or skipped** → branch to an easier diagnostic question to pinpoint the gap
3. The engine continues branching until it has enough data per topic area (minimum 3 data points per topic).
4. The test ends when all topic areas are assessed OR after the max question limit is reached.

#### Question Limits
- Minimum: 20 questions
- Maximum: 60 questions
- Average session: ~35 questions
- Estimated time: 45–75 minutes (untimed, but a timer is shown for reference)

#### Difficulty Levels
| Level | Label | Description |
|-------|-------|-------------|
| 1 | Foundational | 6th–8th grade concepts |
| 2 | Intermediate | 9th–10th grade |
| 3 | Advanced | 11th–12th grade / Pre-college |
| 4 | AP / Honors | College Board AP level |
| 5 | Olympiad / Competition | AMC, AIME, Olympiad level |

---

### Question Formats

#### 1. Multiple Choice
- 4 answer options (A, B, C, D)
- One correct answer
- Common distractors based on typical student mistakes

**Example:**
> Solve for x: 2x + 5 = 13
> - A) 3
> - B) 4 ✓
> - C) 9
> - D) 6

#### 2. Fill in the Blank
- Student types a numerical or algebraic answer
- Accepts equivalent forms (e.g., `1/2` = `0.5`)
- For expressions: simple string matching with normalization

**Example:**
> Simplify: (x² − 9) / (x − 3) = ___
> Answer: x + 3

#### 3. Free Response
- Short written explanation or multi-step solution
- Student types their work in a text/math input box (LaTeX-supported)
- Graded by the assigned tutor OR auto-scored for numerical answers
- Flagged for tutor review if open-ended

**Example:**
> A train travels 60 mph for 2.5 hours. How far does it travel? Show your work.

---

### Test Interface (UI/UX)

#### Layout
- Clean, distraction-free single-question view
- Progress bar at the top showing % of test completed
- Topic tag shown on each question (e.g., "Algebra — Quadratics")
- Difficulty indicator (dot scale 1–5)
- Timer displayed (informational only, not enforced)
- "Flag for review" button per question
- "Skip question" allowed (counts as incorrect for adaptive branching)

#### Math Input
- LaTeX/MathJax rendering for all equations
- Equation editor for free response (students can type math symbols)
- On mobile: virtual keyboard with math symbols

#### Navigation
- No going back to previous questions (prevents second-guessing)
- "Submit Test" button appears after minimum questions answered
- Confirmation dialog before final submission

---

### Report Card

Generated immediately after test submission. Accessible from the student dashboard at any time.

#### Section 1 — Overall Summary
- Overall Score (percentage)
- Proficiency Level: Foundational / Developing / Proficient / Advanced / Expert
- Total questions answered / correct / incorrect / skipped
- Time taken
- Date of test
- Comparison to previous attempt (if retake)

**Example:**
```
Overall Math Score: 68%
Proficiency Level: Developing
Questions: 38 answered | 26 correct | 9 incorrect | 3 skipped
Time: 52 minutes
```

#### Section 2 — Topic Breakdown (Score Card per Topic)

A table and visual bar chart showing performance per topic:

| Topic | Score | Level Reached | Status |
|-------|-------|--------------|--------|
| Algebra | 85% | Advanced | ✅ Strong |
| Geometry | 72% | Intermediate | 🟡 Satisfactory |
| Trigonometry | 45% | Foundational | 🔴 Needs Work |
| Pre-Calculus | 38% | Foundational | 🔴 Needs Work |
| Calculus | 20% | Below Foundational | 🔴 Gap Identified |
| Statistics | 90% | Advanced | ✅ Strong |
| SAT Math | 78% | Intermediate | 🟡 Satisfactory |

Color coding:
- 🟢 Green (80–100%): Strong
- 🟡 Yellow (55–79%): Satisfactory — room for improvement
- 🔴 Red (0–54%): Gap identified — needs attention

#### Section 3 — Identified Weak Areas

Detailed breakdown of specific subtopics where the student struggled:

**Example:**
```
⚠️ Trigonometry — Unit Circle
   You struggled with identifying exact values of sine and cosine at standard angles.
   Common mistake: Confusing sin(π/3) with sin(π/6).

⚠️ Pre-Calculus — Rational Functions
   Difficulty with identifying vertical and horizontal asymptotes.

⚠️ Calculus — Limits
   Unable to evaluate limits using L'Hôpital's Rule and algebraic simplification.
```

#### Section 4 — Strengths

Topics where the student performed well, listed as positive reinforcement.

**Example:**
```
✅ Algebra — You demonstrated strong understanding of linear equations and systems.
✅ Statistics — Excellent grasp of probability and data interpretation.
```

#### Section 5 — Suggested Next Steps

Personalized action plan based on identified gaps:

```
📌 Priority 1 (Immediate): Trigonometry
   → Review: Unit Circle values, SOH-CAH-TOA, graphing sin/cos/tan
   → Practice: 20 targeted problems on trig identities
   → Goal: Reach Intermediate level before booking Calculus sessions

📌 Priority 2 (Short-term): Pre-Calculus Foundations
   → Review: Rational expressions, function transformations
   → Practice: 15 problems on asymptotes and piecewise functions

📌 Priority 3 (Long-term): Calculus Readiness
   → Complete Trigonometry and Pre-Calculus gaps first
   → Then begin limits and derivative concepts
```

#### Section 6 — Recommended Tutors

Based on the student's weakest topics, the platform surfaces 3–5 tutors:

- Filtered by: subjects matching weak areas
- Sorted by: rating, number of relevant sessions, availability
- Each card shows: tutor name, photo, subjects, rating, price/hr, "Book Now" button

**Example:**
```
Recommended for Trigonometry & Pre-Calculus:
┌─────────────────────────────────────────┐
│ 👤 Sarah M.  ⭐ 4.9  |  $65/hr          │
│ Specializes in: Trig, Pre-Calc, Calculus │
│ 142 sessions completed                  │
│ [Book a Session]  [View Profile]         │
└─────────────────────────────────────────┘
```

---

### Tutor Access to Report Card

- When a student **books a session**, their most recent diagnostic Report Card is **automatically shared** with the assigned tutor.
- Tutors can view the report from the session detail page.
- Tutors can see:
  - Full topic breakdown
  - Identified weak areas
  - Student's uploaded files (see Section 15)
- Tutors **cannot** edit the report card.
- Students can **opt out** of sharing the report card (toggle in profile settings). Default is **opt-in (shared)**.

---

### Retake Policy

- Students may retake the full diagnostic once every **7 days**.
- Previous report cards are saved and accessible in the student dashboard under "My Diagnostics".
- Progress comparison is shown between attempts (score deltas per topic).
- Retake cooldown timer shown in dashboard: "Next diagnostic available in X days".

---

### Diagnostic Pages & Screens

| Page | Path | Description |
|------|------|-------------|
| Diagnostic Home | `/diagnostic` | Intro page, instructions, start test or view history |
| Take Test | `/diagnostic/test` | Adaptive test interface, one question at a time |
| Results | `/diagnostic/results/[id]` | Full report card after submission |
| History | `/diagnostic/history` | All past diagnostics with scores and dates |
| Tutor View | `/sessions/[id]/diagnostic` | Tutor's view of student's report card |

---

### Diagnostic Database Tables

```sql
diagnostic_tests (
  id              UUID PRIMARY KEY,
  student_id      UUID REFERENCES users(id),
  status          ENUM('in_progress', 'completed', 'abandoned'),
  started_at      TIMESTAMP,
  completed_at    TIMESTAMP,
  total_questions INT,
  correct_answers INT,
  overall_score   DECIMAL,
  proficiency     ENUM('foundational', 'developing', 'proficient', 'advanced', 'expert'),
  time_taken_mins INT
)

diagnostic_questions (
  id              UUID PRIMARY KEY,
  topic           TEXT NOT NULL,
  subtopic        TEXT NOT NULL,
  difficulty      INT CHECK (difficulty BETWEEN 1 AND 5),
  format          ENUM('multiple_choice', 'fill_in_blank', 'free_response'),
  question_text   TEXT NOT NULL,
  options         JSONB,          -- for multiple choice: [{label, text, is_correct}]
  correct_answer  TEXT,           -- for fill_in_blank
  explanation     TEXT,           -- shown after test in report
  latex_content   BOOLEAN DEFAULT false
)

diagnostic_responses (
  id              UUID PRIMARY KEY,
  test_id         UUID REFERENCES diagnostic_tests(id),
  question_id     UUID REFERENCES diagnostic_questions(id),
  student_answer  TEXT,
  is_correct      BOOLEAN,
  time_spent_secs INT,
  flagged         BOOLEAN DEFAULT false,
  skipped         BOOLEAN DEFAULT false
)

diagnostic_topic_scores (
  id              UUID PRIMARY KEY,
  test_id         UUID REFERENCES diagnostic_tests(id),
  topic           TEXT NOT NULL,
  subtopic        TEXT,
  score           DECIMAL,
  level_reached   INT,
  status          ENUM('strong', 'satisfactory', 'needs_work', 'gap_identified'),
  questions_count INT
)

diagnostic_report_cards (
  id              UUID PRIMARY KEY,
  test_id         UUID REFERENCES diagnostic_tests(id),
  student_id      UUID REFERENCES users(id),
  weak_areas      JSONB,          -- [{topic, subtopic, description, common_mistake}]
  strong_areas    JSONB,          -- [{topic, description}]
  next_steps      JSONB,          -- [{priority, topic, actions[]}]
  recommended_tutor_ids UUID[],
  is_shared       BOOLEAN DEFAULT true,
  created_at      TIMESTAMP
)
```

---

## 15. Student Upload System

### Overview

Students can upload academic materials to the platform. These uploads serve two purposes:
1. **Diagnostic context** — help inform and personalize the diagnostic test report
2. **Tutor preparation** — give the assigned tutor visibility into what the student is working on before a session

---

### Supported File Types

| Category | Accepted Formats |
|----------|-----------------|
| Documents | PDF, DOC, DOCX |
| Images | JPG, JPEG, PNG |
| Spreadsheets | XLS, XLSX |
| Max file size | 25 MB per file |
| Max files per upload | 10 files at once |

---

### Upload Categories

Students label each upload with a category:

| Category | Description |
|----------|-------------|
| Homework | Assigned homework problems |
| Worksheet | Practice worksheets |
| Study Guide | Exam or chapter study guides |
| Quiz | Graded or ungraded quiz |
| Classwork | In-class notes or problems |
| Exam / Test | Past exams for review |
| Other | Anything else |

---

### Upload Flow

1. Student navigates to **"My Files"** or uploads directly from:
   - The Diagnostic Home page ("Upload materials to improve your results")
   - A session booking page ("Share materials with your tutor")
   - The student dashboard
2. Student selects files from device
3. Student selects category and subject tag (e.g., "Algebra", "Calculus")
4. Optional: add a note for the tutor (e.g., "These are the problems I got wrong on my quiz")
5. File is uploaded and stored securely
6. Student can manage (view, rename, delete) files from **My Files** page

---

### Diagnostic Integration

- When a student has uploaded files before taking the diagnostic:
  - A notice appears: "We found X uploaded files. These will be used to personalize your results."
  - The report card's **Suggested Next Steps** section references specific uploaded material:
    > "Based on your Quiz upload (Algebra — Chapter 4), we noticed errors in factoring quadratics. This aligns with your diagnostic score of 40% in that subtopic."
- This integration is informational and displayed in the Report Card — it does not change the adaptive question flow.

---

### Tutor Access to Uploads

- When a student books a session, the tutor receives a **session preparation view** that includes:
  - Student's diagnostic Report Card (if shared)
  - All files the student has tagged with the relevant subject
  - Student's optional note per file
- Tutors can **view and download** files but cannot edit or delete them.
- Students control which files are visible to tutors (toggle per file: Shared / Private).

---

### Upload Pages & Screens

| Page | Path | Description |
|------|------|-------------|
| My Files | `/files` | All uploaded files, filterable by category and subject |
| Upload | `/files/upload` | Upload interface with category and subject tagging |
| Session Prep (Tutor) | `/sessions/[id]/prep` | Tutor's view: diagnostic report + student files |

---

### Upload Database Tables

```sql
student_uploads (
  id            UUID PRIMARY KEY,
  student_id    UUID REFERENCES users(id),
  file_name     TEXT NOT NULL,
  file_url      TEXT NOT NULL,
  file_type     TEXT,
  file_size_kb  INT,
  category      ENUM('homework', 'worksheet', 'study_guide', 'quiz', 'classwork', 'exam', 'other'),
  subject_tag   TEXT,
  note          TEXT,
  is_shared     BOOLEAN DEFAULT true,
  uploaded_at   TIMESTAMP
)

session_uploads (
  session_id    UUID REFERENCES sessions(id),
  upload_id     UUID REFERENCES student_uploads(id),
  PRIMARY KEY (session_id, upload_id)
)
```

---

## 16. AI Homework Helper

### Overview

Between sessions, students can ask subject-specific questions and receive instant AI-powered explanations. The AI Helper reduces frustration when students are stuck and keeps them engaged on the platform rather than leaving for external tools.

Available to all registered students. Subject scope: all platform subjects (Math, Chemistry, Physics, History, CS, French, German).

---

### How It Works

1. Student opens the AI Helper from the dashboard or any subject page.
2. Student types a question or pastes a problem. Can also attach an image (photo of a textbook problem or handwritten work).
3. AI responds with:
   - Step-by-step explanation
   - Worked example if relevant
   - Concept summary
   - Suggestion to book a tutor if the topic is complex or recurring
4. Student can ask follow-up questions in the same thread.
5. Conversation is saved in the student's AI Helper history.

---

### Boundaries & Rules

- The AI **explains** and **guides** — it does not simply give final answers to homework without showing reasoning.
- Questions are scoped to academic subjects only. Off-topic prompts are rejected with a friendly message.
- Each student gets a **daily usage limit**:
  - Free: 10 questions/day
  - Premium (future): unlimited questions
- AI responses include a disclaimer: *"This is an AI explanation. For personalized help, book a session with a tutor."*

---

### Integration with Diagnostics & Tutors

- If a student asks about a topic flagged as weak in their diagnostic, a banner appears: *"This topic is in your improvement plan. [View Report Card]"*
- If a student asks 3+ questions on the same subtopic within a week, the platform suggests booking a tutor for that topic.

---

### Pages & Screens

| Page | Path | Description |
|------|------|-------------|
| AI Helper | `/ai-helper` | Main chat interface |
| History | `/ai-helper/history` | Past AI conversations by subject |

---

### Database Tables

```sql
ai_conversations (
  id            UUID PRIMARY KEY,
  student_id    UUID REFERENCES users(id),
  subject       TEXT,
  started_at    TIMESTAMP
)

ai_messages (
  id              UUID PRIMARY KEY,
  conversation_id UUID REFERENCES ai_conversations(id),
  role            ENUM('student', 'assistant'),
  content         TEXT NOT NULL,
  image_url       TEXT,
  created_at      TIMESTAMP
)
```

---

## 17. Session Notes & Recap

### Overview

After every completed session, the tutor writes a structured recap. This recap is saved to the student's profile, visible to the student and their parent, and used to inform future sessions.

---

### Recap Structure

Tutors fill in the following fields after each session:

| Field | Description |
|-------|-------------|
| Topics Covered | List of subjects/subtopics addressed in the session |
| What Went Well | Concepts the student understood clearly |
| Areas to Improve | Topics that still need work |
| Homework Assigned | Any tasks or practice problems assigned |
| Goals for Next Session | What the next session should focus on |
| Tutor Notes (Private) | Internal notes only visible to the tutor (not student) |

---

### Rules

- Tutors have **24 hours** after session completion to submit the recap.
- Reminder sent via email/push if not submitted within 12 hours.
- Recap is **locked for editing** after 48 hours.
- Students and parents can read the recap but cannot edit it.
- Recaps are visible to future tutors (if the student books a different tutor) — student can opt out.

---

### Integration

- Recap appears in the student's session history page.
- Parent dashboard shows a "Recent Recap" widget.
- If homework was assigned, it appears as a reminder in the student's dashboard until marked done.

---

### Pages & Screens

| Page | Path | Description |
|------|------|-------------|
| Write Recap (Tutor) | `/sessions/[id]/recap` | Tutor recap form |
| View Recap (Student/Parent) | `/sessions/[id]/recap/view` | Read-only recap view |

---

### Database Table

```sql
session_recaps (
  id                  UUID PRIMARY KEY,
  session_id          UUID REFERENCES sessions(id),
  tutor_id            UUID REFERENCES users(id),
  topics_covered      TEXT[],
  went_well           TEXT,
  areas_to_improve    TEXT,
  homework_assigned   TEXT,
  next_session_goals  TEXT,
  tutor_private_notes TEXT,
  is_shared           BOOLEAN DEFAULT true,
  submitted_at        TIMESTAMP
)
```

---

## 18. Structured Study Programs

### Overview

Tutors can create and sell multi-week structured programs — a curated series of sessions with defined goals, milestones, and curriculum. Programs are purchased upfront by students/parents.

**Examples:**
- "8-Week SAT Math Prep" — $480 (8 sessions × $60)
- "AP Calculus AB Full Course" — $900 (15 sessions)
- "AMC 10 Competition Prep" — $350 (7 sessions)

---

### Program Structure

| Field | Description |
|-------|-------------|
| Title | Program name |
| Subject(s) | Subjects covered |
| Description | What students will learn |
| Target Level | Grade level / exam target |
| Number of Sessions | Total sessions in program |
| Session Duration | Minutes per session |
| Total Price | Full program price |
| Weekly Schedule | How many sessions per week |
| Curriculum Outline | Week-by-week topics |
| Max Students | 1 (private) or up to 5 (group) |
| Prerequisites | What students should know before starting |

---

### Program Flow

1. Tutor creates a program from their dashboard.
2. Admin reviews and approves the program listing.
3. Program appears on the tutor's profile and a dedicated Programs page.
4. Student/parent purchases the program.
5. Sessions are automatically scheduled based on the weekly cadence.
6. Progress tracked via session recaps and milestone check-ins.
7. Certificate of completion issued at the end (optional, tutor decides).

---

### Commission

- Platform takes the standard **35% commission** on program purchases.

---

### Pages & Screens

| Page | Path | Description |
|------|------|-------------|
| Browse Programs | `/programs` | All available programs, filterable by subject/level |
| Program Detail | `/programs/[id]` | Full program info and purchase button |
| Create Program (Tutor) | `/tutor/programs/create` | Program creation form |
| My Programs (Student) | `/my-programs` | Enrolled programs and progress |

---

### Database Tables

```sql
programs (
  id                UUID PRIMARY KEY,
  tutor_id          UUID REFERENCES users(id),
  title             TEXT NOT NULL,
  description       TEXT,
  subjects          TEXT[],
  target_level      TEXT,
  session_count     INT,
  session_duration  INT,
  total_price       DECIMAL,
  sessions_per_week INT,
  curriculum        JSONB,
  max_students      INT DEFAULT 1,
  prerequisites     TEXT,
  is_approved       BOOLEAN DEFAULT false,
  is_active         BOOLEAN DEFAULT true,
  created_at        TIMESTAMP
)

program_enrollments (
  id            UUID PRIMARY KEY,
  program_id    UUID REFERENCES programs(id),
  student_id    UUID REFERENCES users(id),
  payment_id    UUID REFERENCES payments(id),
  status        ENUM('active', 'completed', 'cancelled'),
  enrolled_at   TIMESTAMP,
  completed_at  TIMESTAMP
)
```

---

## 19. Group Sessions

### Overview

Tutors can host small group sessions with 2–5 students simultaneously. Group sessions are priced lower per student, making tutoring more accessible.

---

### How It Works

1. Tutor creates a group session slot from their availability calendar.
2. Tutor sets: subject, topic, date/time, duration, max students (2–5), price per student.
3. Students browse and join open group sessions.
4. When the session is full, it is closed to new joiners.
5. Session proceeds like a standard online session — tutor shares Zoom/Google Meet link.
6. Each student is charged individually. Platform takes 35% from each payment.

---

### Group Session Rules

- Minimum 2 students required for a session to run.
- If minimum not reached 2 hours before the session, it is automatically cancelled and students are refunded.
- Students can see each other's first names only — no last names, no contact sharing.
- Students cannot message each other directly through the platform.

---

### Pages & Screens

| Page | Path | Description |
|------|------|-------------|
| Browse Group Sessions | `/group-sessions` | Open group sessions, filterable by subject/date |
| Group Session Detail | `/group-sessions/[id]` | Details + join button |
| Create Group Session (Tutor) | `/tutor/group-sessions/create` | Session creation form |

---

### Database Tables

```sql
group_sessions (
  id                UUID PRIMARY KEY,
  tutor_id          UUID REFERENCES users(id),
  subject_id        UUID REFERENCES subjects(id),
  topic             TEXT,
  scheduled_at      TIMESTAMP,
  duration_mins     INT,
  price_per_student DECIMAL,
  max_students      INT,
  min_students      INT DEFAULT 2,
  meeting_link      TEXT,
  status            ENUM('open', 'full', 'completed', 'cancelled'),
  created_at        TIMESTAMP
)

group_session_enrollments (
  session_id    UUID REFERENCES group_sessions(id),
  student_id    UUID REFERENCES users(id),
  payment_id    UUID REFERENCES payments(id),
  joined_at     TIMESTAMP,
  PRIMARY KEY (session_id, student_id)
)
```

---

## 20. Student Progress Tracker

### Overview

A visual dashboard that tracks a student's learning journey over time — combining diagnostic scores, session history, tutor recaps, and goals into one unified view.

---

### Components

#### Learning Timeline
- Chronological view of all activity: diagnostics taken, sessions completed, files uploaded, programs enrolled.

#### Skill Progress Chart
- Line or radar chart showing diagnostic scores per topic across all attempts.
- Visually shows improvement over time.
- Example: "Trigonometry: 45% → 62% → 78% over 3 diagnostics"

#### Goal Tracking
- Students (or parents) set learning goals:
  - "Reach AP level in Calculus by May"
  - "Score 750+ on SAT Math by October"
- Goals display a progress bar based on diagnostic scores and tutor feedback.
- Tutors can add milestone notes against goals.

#### Session Stats
- Total sessions completed
- Total hours studied
- Subjects studied
- Number of different tutors worked with

#### Homework Tracker
- Homework assigned in session recaps displayed as a checklist.
- Student marks items as done.
- Overdue items highlighted in red.

---

### Pages & Screens

| Page | Path | Description |
|------|------|-------------|
| Progress Dashboard | `/progress` | Full progress overview |
| Goals | `/progress/goals` | Set, view, and track learning goals |

---

### Database Table

```sql
student_goals (
  id            UUID PRIMARY KEY,
  student_id    UUID REFERENCES users(id),
  title         TEXT NOT NULL,
  subject       TEXT,
  target_score  DECIMAL,
  target_date   DATE,
  current_score DECIMAL,
  status        ENUM('active', 'achieved', 'expired'),
  created_at    TIMESTAMP
)
```

---

## 21. Gamification

### Overview

Achievements, streaks, and badges motivate students to stay engaged, complete sessions consistently, and improve their diagnostic scores.

---

### Streaks

- **Session Streak:** Consecutive weeks with at least one completed session.
- **Diagnostic Streak:** Consecutive weeks where the student took and improved their diagnostic score.
- Streak counter displayed on the student dashboard.
- Breaking a streak resets the counter to 0.

---

### Badges

| Badge | Trigger |
|-------|---------|
| First Step | Complete first session |
| On a Roll | Complete 5 sessions |
| Dedicated Learner | Complete 20 sessions |
| Century Club | Complete 100 sessions |
| Diagnostic Debut | Take first diagnostic test |
| Rising Star | Improve diagnostic score by 10%+ |
| Sharp Shooter | Score 90%+ on any topic |
| All-Rounder | Score above 70% in 5+ topics |
| Homework Hero | Complete 10 assigned homework items |
| Program Graduate | Complete a structured study program |

---

### Leaderboard (Opt-in)

- Anonymous leaderboard per subject showing top diagnostic scorers.
- Students must opt in to appear.
- Resets monthly.

---

### Database Tables

```sql
student_badges (
  id          UUID PRIMARY KEY,
  student_id  UUID REFERENCES users(id),
  badge_key   TEXT NOT NULL,
  earned_at   TIMESTAMP
)

student_streaks (
  student_id            UUID PRIMARY KEY REFERENCES users(id),
  session_streak        INT DEFAULT 0,
  diagnostic_streak     INT DEFAULT 0,
  last_session_week     DATE,
  last_diagnostic_week  DATE
)
```

---

## 22. Tutor Availability Alerts

### Overview

When a student wants to book a specific tutor but finds no open slots, they can set an alert. The student is notified as soon as the tutor opens a new slot.

---

### Flow

1. Student views a tutor's profile — no available slots shown.
2. Student clicks **"Notify Me When Available"**.
3. Student optionally selects preferred days/times.
4. When the tutor adds new availability, the student receives:
   - Email: "Good news! [Tutor Name] just opened new slots."
   - Push notification (mobile)
5. Clicking the notification takes the student directly to the tutor's booking page.
6. Alert auto-expires after 30 days if not triggered.

---

### Database Table

```sql
availability_alerts (
  id              UUID PRIMARY KEY,
  student_id      UUID REFERENCES users(id),
  tutor_id        UUID REFERENCES tutor_profiles(id),
  preferred_days  INT[],
  preferred_time  TEXT,
  is_active       BOOLEAN DEFAULT true,
  created_at      TIMESTAMP,
  expires_at      TIMESTAMP
)
```

---

## 23. Cancellation & Refund Policy

### Overview

A clear, enforced policy protecting both students/parents and tutors.

---

### Cancellation Windows

| Time Before Session | Cancellation by Student | Cancellation by Tutor |
|---------------------|------------------------|-----------------------|
| More than 24 hours | Full refund | Full refund + $5 platform credit to student |
| 12–24 hours | 50% refund | Full refund + $10 platform credit to student |
| Less than 12 hours | No refund | Full refund + $15 platform credit to student |
| No-show (student) | No refund | Tutor paid 50% |
| No-show (tutor) | Full refund + $15 credit | Tutor receives nothing, warning issued |

---

### Process

1. Cancellation requested by either party from the session detail page.
2. Reason required (dropdown + optional note).
3. Refund processed automatically for Stripe payments within 3–5 business days.
4. For Zelle/Venmo: admin manually processes refund within 24 hours.
5. Platform credit issued immediately to student's TutorHub wallet.
6. Tutor's cancellation count tracked — 3 late cancellations in 30 days triggers admin review.

---

### Dispute Process

- Either party can open a dispute within 48 hours of the cancellation decision.
- Admin reviews and makes final decision within 72 hours.
- Admin can issue full/partial refunds regardless of policy in exceptional cases.

---

### Database Table

```sql
cancellations (
  id              UUID PRIMARY KEY,
  session_id      UUID REFERENCES sessions(id),
  cancelled_by    UUID REFERENCES users(id),
  reason          TEXT,
  hours_before    DECIMAL,
  refund_amount   DECIMAL,
  credit_issued   DECIMAL,
  processed_at    TIMESTAMP
)
```

---

## 24. Referral Program

### Overview

Students, parents, and tutors earn rewards for bringing new users to the platform.

---

### Reward Table

| Referrer | Referred Person | Referrer Reward | Referred Person Reward |
|----------|----------------|-----------------|------------------------|
| Student / Parent | New Student/Parent | $10 credit after referred user's first session | $10 credit on signup |
| Student / Parent | New Tutor | $20 credit after tutor's first session | — |
| Tutor | New Tutor | $25 credit after referred tutor's first session | — |
| Tutor | New Student/Parent | $15 credit after first session | $10 credit on signup |

---

### Mechanics

- Every user gets a unique referral link and code on their profile page.
- Referral tracked via cookie + account creation.
- Credits added to TutorHub Wallet (internal credit system).
- Credits can be used toward session payments only — not withdrawable as cash.
- Credits expire after 12 months if unused.
- No cap on number of referrals.

---

### TutorHub Wallet

- Every user has an internal wallet for platform credits.
- Credits applied automatically at checkout if available.
- Wallet balance visible in profile/settings page.

---

### Database Tables

```sql
referrals (
  id              UUID PRIMARY KEY,
  referrer_id     UUID REFERENCES users(id),
  referred_id     UUID REFERENCES users(id),
  status          ENUM('pending', 'rewarded', 'expired'),
  referrer_credit DECIMAL,
  referred_credit DECIMAL,
  created_at      TIMESTAMP,
  rewarded_at     TIMESTAMP
)

wallet_transactions (
  id            UUID PRIMARY KEY,
  user_id       UUID REFERENCES users(id),
  amount        DECIMAL,
  type          ENUM('credit', 'debit'),
  reason        TEXT,
  balance_after DECIMAL,
  created_at    TIMESTAMP
)
```

---

## 25. Package Deals

### Overview

Tutors can offer session bundles at a discounted price. Students/parents purchase multiple sessions upfront and use them over time.

---

### Package Options

Tutors define their own packages:

| Package | Sessions | Discount |
|---------|----------|----------|
| Starter Pack | 3 sessions | 10% off |
| Value Pack | 5 sessions | 15% off |
| Power Pack | 10 sessions | 20% off |

- Maximum discount: 30%.
- Sessions in a package never expire.
- Packages are tutor-specific — sessions can only be used with the tutor they were purchased from.
- Platform takes 35% commission on the total package price at purchase.

---

### Flow

1. Student visits a tutor's profile — a "Packages" tab shows available bundles.
2. Student purchases a package.
3. Sessions credited to the student's account for that tutor.
4. When booking, student selects "Use Package Session" at checkout — no payment needed.
5. Package session balance shown on both student and tutor dashboards.

---

### Refund Policy

- Unused sessions: fully refundable within 7 days of purchase.
- After 7 days: 80% refund per unused session.
- Used sessions: non-refundable.

---

### Database Tables

```sql
packages (
  id            UUID PRIMARY KEY,
  tutor_id      UUID REFERENCES users(id),
  title         TEXT,
  session_count INT,
  price         DECIMAL,
  discount_pct  DECIMAL,
  is_active     BOOLEAN DEFAULT true,
  created_at    TIMESTAMP
)

package_purchases (
  id                 UUID PRIMARY KEY,
  package_id         UUID REFERENCES packages(id),
  student_id         UUID REFERENCES users(id),
  payment_id         UUID REFERENCES payments(id),
  sessions_total     INT,
  sessions_used      INT DEFAULT 0,
  sessions_remaining INT,
  purchased_at       TIMESTAMP
)
```

---

## 26. Blog & Resource Center

### Overview

A free content hub with educational articles, practice problems, and study guides. Serves two goals: help students directly, and drive organic SEO traffic to TutorHub.

---

### Content Types

| Type | Description |
|------|-------------|
| Article | Concept explanations (e.g. "How to Factor Quadratics") |
| Practice Problem Set | 10–20 curated problems per topic with solutions |
| Study Guide | Comprehensive topic overviews (e.g. "AP Calculus AB Complete Guide") |
| Exam Prep | SAT, AMC, AP exam tips and strategies |
| Tutor Spotlight | Featured tutor profiles and teaching philosophy |

---

### Content Structure

Each post includes:
- Title, subject tag(s), difficulty level, estimated read time
- Author (TutorHub staff or approved tutor)
- Body content with LaTeX rendering for math
- Related resources
- CTA: *"Need help with this topic? Find a tutor →"*

---

### Who Can Write

- **TutorHub staff** — create and publish directly.
- **Approved tutors** — submit articles for editorial review. If published, they receive attribution and a profile link.

---

### Pages & Screens

| Page | Path | Description |
|------|------|-------------|
| Blog Home | `/blog` | All articles, filterable by subject and type |
| Article | `/blog/[slug]` | Single article page |
| Practice Sets | `/resources/practice` | Browseable problem sets |
| Study Guides | `/resources/guides` | Comprehensive subject guides |

---

### Database Table

```sql
blog_posts (
  id            UUID PRIMARY KEY,
  title         TEXT NOT NULL,
  slug          TEXT UNIQUE NOT NULL,
  content       TEXT NOT NULL,
  type          ENUM('article', 'practice_set', 'study_guide', 'exam_prep', 'spotlight'),
  subjects      TEXT[],
  difficulty    INT,
  author_id     UUID REFERENCES users(id),
  is_published  BOOLEAN DEFAULT false,
  published_at  TIMESTAMP,
  created_at    TIMESTAMP
)
```

---

## 27. Tutor Background Check

### Overview

For tutors offering **in-person sessions**, a background check is required before their profile is approved for in-person bookings. Online-only tutors are exempt.

---

### Process

1. During onboarding, tutor selects session types (Online / In-Person / Both).
2. If In-Person is selected:
   - Tutor is prompted to complete a background check via a third-party integration (e.g. Checkr).
   - Tutor submits full legal name, date of birth, and last 4 digits of SSN.
   - Check typically completes within 1–3 business days.
3. Admin reviews the result:
   - **Clear** → tutor approved for in-person sessions.
   - **Flagged** → admin may approve online-only and reject in-person.
4. Approved tutor profile shows a **"Background Checked"** badge.
5. Background check must be renewed every **2 years**.

---

### Cost

- Fee: **$25**, paid by the tutor at onboarding via Stripe.
- Non-refundable regardless of outcome.

---

### Data & Privacy

- Raw background check data handled entirely by the third-party provider.
- TutorHub stores only: check status (pending / clear / flagged / expired) and expiry date.

---

### Database Table

```sql
background_checks (
  id            UUID PRIMARY KEY,
  tutor_id      UUID REFERENCES users(id),
  provider      TEXT DEFAULT 'checkr',
  status        ENUM('pending', 'clear', 'flagged', 'expired'),
  submitted_at  TIMESTAMP,
  completed_at  TIMESTAMP,
  expires_at    TIMESTAMP,
  fee_paid      BOOLEAN DEFAULT false
)
```

---

## 28. Two-Factor Authentication

### Overview

An optional but strongly recommended security layer for all users. Mandatory for admin accounts.

---

### Methods Supported

| Method | Description |
|--------|-------------|
| Authenticator App | Google Authenticator, Authy (TOTP) |
| SMS Code | 6-digit code via SMS |
| Email Code | 6-digit code to registered email |

---

### Flow

1. User goes to **Settings → Security → Enable 2FA**.
2. Selects preferred method.
3. For authenticator app: scan QR code, verify with first generated code.
4. For SMS/email: verification code sent, user enters to confirm.
5. Backup codes generated and displayed once — user must save them.
6. On every subsequent login: after password, user is prompted for second factor.

---

### Rules

- **Admin accounts:** 2FA is **mandatory** and cannot be disabled.
- **Tutors & Parents:** Strongly recommended. Prompted once on first login.
- **Students:** Optional. Prompted once, can dismiss.
- **Trusted Device:** Users can mark a device as trusted for 30 days (skips 2FA on that device).
- Lost 2FA access: recoverable via backup code or admin support.

---

### Database Tables

```sql
user_2fa (
  user_id       UUID PRIMARY KEY REFERENCES users(id),
  method        ENUM('totp', 'sms', 'email'),
  is_enabled    BOOLEAN DEFAULT false,
  totp_secret   TEXT,
  phone_number  TEXT,
  backup_codes  TEXT[],
  enabled_at    TIMESTAMP
)

trusted_devices (
  id            UUID PRIMARY KEY,
  user_id       UUID REFERENCES users(id),
  device_hash   TEXT,
  trusted_at    TIMESTAMP,
  expires_at    TIMESTAMP
)
```

---

*Document Version: 1.2*
*Last Updated: March 2026*

---

## 29. Platform Chatbot

### Overview

An AI-powered chatbot available to both guests and logged-in users. It answers questions about tutors, subjects, platform navigation, and more — helping users find what they need instantly without having to browse manually.

Available in two locations:
- **Floating widget** — persistent on every page (bottom-right corner), collapsible
- **Dedicated chat page** — `/chat` for a full-screen experience

---

### Who Can Use It

| User Type | Access |
|-----------|--------|
| Guest (not logged in) | Full access — can ask all questions, cannot book or view personal data |
| Logged-in Student | Full access + personalized responses based on their profile, diagnostics, and session history |
| Logged-in Parent | Full access + info about their children's sessions and tutors |
| Logged-in Tutor | Full access + help with their own profile, sessions, earnings |

---

### What the Chatbot Can Answer

#### About Tutors
- "Who teaches AP Calculus?"
- "Show me tutors available on weekends"
- "Who are your highest-rated math tutors?"
- "Tell me about [Tutor Name]"
- "What is [Tutor Name]'s teaching philosophy?"
- "What experience does [Tutor Name] have?"
- "What are [Tutor Name]'s qualifications and credentials?"
- "Can you show me reviews for [Tutor Name]?"
- "What do parents say about [Tutor Name]?"
- "How many students has [Tutor Name] tutored?"
- "Is [Tutor Name] available this week?"

#### About Subjects
- "What math subjects do you offer?"
- "Do you have tutors for AIME prep?"
- "What is the difference between AP Calculus AB and BC?"
- "What topics are covered in your Algebra tutoring?"
- "Do you offer German tutoring?"
- "Which tutors teach both Physics and Math?"

#### About the Platform
- "How do I book a session?"
- "How does payment work?"
- "What is your cancellation policy?"
- "How do I take the math diagnostic test?"
- "How do packages work?"
- "What is the 35% commission?"
- "How do I become a tutor?"
- "How do I add my child's profile?"
- "How do I use my referral code?"
- "How do I contact support?"

#### Personalized (Logged-in Users Only)
- "When is my next session?"
- "What did my tutor say about my last session?"
- "What are my weakest math topics?"
- "Which tutors are recommended for me?"
- "How many sessions have I completed?"
- "What's my current wallet balance?"
- "Show me my upcoming sessions"

---

### Tutor Profile Cards in Chat

When the chatbot surfaces a tutor, it displays a rich card inline in the chat:

```
┌──────────────────────────────────────────────┐
│ Sarah M.                       4.9 (142)     │
│ AP Calculus | Trigonometry | Pre-Calculus     │
│ "I focus on building intuition, not just      │
│  memorizing formulas."                        │
│                                               │
│ Education: MIT, B.S. Mathematics              │
│ Experience: 5 years, 142 sessions             │
│ Rate: $65/hr  |  Online & In-Person           │
│                                               │
│ "Sarah helped my son go from a 3 to a 5      │
│  on AP Calc in 8 weeks." — Parent, Jan 2026   │
│                                               │
│ [View Profile]  [Book a Session]  [Message]  │
└──────────────────────────────────────────────┘
```

---

### Tutor Knowledge Base Fields (Used by Chatbot)

The chatbot draws from structured tutor data including:

| Field | Description |
|-------|-------------|
| Qualifications | Degrees, certifications, test scores achieved |
| Experience | Years of tutoring, total sessions, subject specializations |
| Teaching Philosophy | Short statement written by tutor on their approach |
| Highlighted Testimonials | 1–3 selected student/parent reviews featured on the profile |
| Awards / Recognition | Any academic or teaching awards |
| Languages Spoken | e.g., English, French, German |

Tutors fill in these fields during profile creation. Teaching philosophy and testimonials are shown in chatbot responses when relevant.

---

### Chatbot Behavior & Rules

- **Friendly and concise** — short, clear answers with follow-up options suggested.
- **Never hallucinates tutor data** — only surfaces real tutor profiles from the database.
- **Escalates to human support** when it cannot answer:
  > "I'm not sure about that — would you like me to connect you with our support team?"
- **Suggests next actions** after every answer:
  > "Would you like to book a session with Sarah, or see more tutors like her?"
- **Does not handle payments or disputes** — redirects to the appropriate page or support.
- **Remembers context within a session** — if the user asks about a tutor and then asks "what are their reviews?", the chatbot understands the reference.
- **Guest users** who try to book are prompted to sign up:
  > "You'll need an account to book a session. [Sign Up — it's free]"

---

### Suggested Starter Prompts

Shown when the chatbot widget opens for the first time:

- "Find me a Calculus tutor"
- "How does booking work?"
- "Take the math diagnostic test"
- "What subjects do you offer?"
- "I need help with SAT Math prep"

---

### Floating Widget Behavior

- Appears as a small circular button (bottom-right) on every page.
- Clicking opens a slide-up chat panel (400px wide, 520px tall on desktop).
- On mobile: opens as a full-screen overlay.
- Persists across page navigation — does not reset between pages.
- Unread indicator dot shown if the bot sent a message the user hasn't seen.
- Can be minimized or closed (reopens in same state).

---

### Pages & Screens

| Page | Path | Description |
|------|------|-------------|
| Full Chat Page | `/chat` | Full-screen chatbot experience |
| Floating Widget | All pages | Collapsible chat bubble, bottom-right |

---

### Database Tables

```sql
chatbot_sessions (
  id          UUID PRIMARY KEY,
  user_id     UUID REFERENCES users(id),
  guest_token TEXT,
  started_at  TIMESTAMP,
  ended_at    TIMESTAMP
)

chatbot_messages (
  id          UUID PRIMARY KEY,
  session_id  UUID REFERENCES chatbot_sessions(id),
  role        ENUM('user', 'assistant'),
  content     TEXT NOT NULL,
  cards       JSONB,
  created_at  TIMESTAMP
)
```

---

*Document Version: 1.3*
*Last Updated: March 2026*
