# Project charter: Realtime Quiz platform

| Field    | Value                              |
|----------|------------------------------------|
| Version  | 1.0 (draft for sponsor approval)   |
| Date     | 2026-09-29                         |
| Sponsor  | Head of the IT department          |
| PM       | Supervising lecturer               |

## 1. Purpose and justification
Lecturers in the IT department spend about 300 hours a year marking quizzes by hand (10 lecturers x 1 h per week x 30 weeks) and give students no live feedback during class. The Realtime Quiz platform lets instructors author multiple-choice quizzes and run live, timed sessions in which students join with a 6-character code, answer against a timer and see scores and a leaderboard instantly. The benefit is marking time saved, immediate feedback for students, and quiz data that stays in the department with no per-seat fee. The investment is 490 person-hours and 200 USD cash; the comparison of doing nothing, buying a SaaS and building is in [business-case.md](business-case.md), and its recommendation is in [section 6 of the business case](business-case.md#6-recommendation-and-review-gate).

## 2. Objectives and success criteria
| #  | Objective (what will be true)                                        | Success criterion (number + week)                                                         |
|----|----------------------------------------------------------------------|-------------------------------------------------------------------------------------------|
| O1 | All Must features work together in one live demonstration (MVP)       | 8 of 8 Must features pass a live demo with 0 blocking defects, week 7                     |
| O2 | The platform runs a real pilot session with students                  | 50 participants in one live session with 0 blocking defects, week 14                      |
| O3 | Broadcasts reach all clients quickly                                  | <= 500 ms at the 95th percentile in the week-13 load test, confirmed in the pilot, week 14 |
| O4 | One server instance carries the planned load                          | 20 sessions of 100 participants on 2 vCPU and 2 GB RAM with an error rate below 1 %, week 13 |
| O5 | The code is tested and every merge is checked                         | line coverage >= 80 % and CI green on every merge to main, measured at each phase tag and finally in week 14 |

## 3. High-level scope
In scope:
- Quiz authoring module for multiple-choice questions
- Live session module with a server-controlled timer for each question
- Instant feedback and scoring for every answer
- Leaderboard for each session
- Real-time updates to all participants of a session
- Accounts and roles for instructors, students and guests
- Support for multiple concurrent sessions
- Responsive user interface for phones and laptops
- Analytics and reporting views for instructors
- Export of results to CSV and PDF files
- Real-time notifications
- Multimedia in questions
- Project documentation, runbook and demo

Could features (only if time remains after the week-10 milestone, and never at the cost of a Must feature): chat during sessions, anonymous joining with a nickname, a question bank shared between quizzes, an admin screen for user management.

Out of scope:
- Native mobile apps
- Question types other than multiple choice (no free text)
- Video conferencing
- Integration with a learning management system (LMS)
- Multi-node scaling (the platform runs as one server instance)

## 4. Milestones
| Week | Milestone                                                                                       | Ends process group         |
|------|-------------------------------------------------------------------------------------------------|----------------------------|
| 1    | Charter approved, team formed                                                                   | Initiating                 |
| 3    | Project plan baselined; repository, CI and VPS environment running                              | Planning                   |
| 5    | Accounts, security and quiz authoring complete                                                  | Executing                  |
| 7    | MVP demo: all Must features working live                                                        | Executing                  |
| 10   | Should features complete (analytics, export, notifications, media); feature freeze              | Executing                  |
| 13   | Pilot readiness: 100-student load test green, data approval received, runbook handed to IT operations | Monitoring and controlling |
| 14   | Pilot with 50 students, closure                                                                 | Closing                    |

## 5. Budget summary
Effort:  students 4 x 14 x 8 h = 448 h; PM 14 x 3 h = 42 h; total 490 h
         (notional value 490 h x 10 USD = 4,900 USD; not cash, used for the comparison in business-case.md)
Cash:    hosting 4 x 25 USD = 100; domain 15; tools 60; subtotal 175 USD;
         reserve 25 USD (25 / 175 = 14 % of the cash lines);
         total 175 + 25 = 200 USD (the cash cap)

## 6. Assumptions
- Each of the four students has 8 hours per week and the PM has 3 hours per week for all 14 weeks.
- The sponsor decides on change requests within 5 working days.
- The Linode VPS at gicitc.com costs about 25 USD per month and is available from week 1.
- Students can reach the platform from campus networks, either through WebSocket or through the fallback.
- Fifty students and their lecturer are available for a pilot session in week 14.

## 7. Constraints
- Duration: 14 weeks, week 1 starts 2026-09-29, pilot in week 14.
- Cash: 200 USD cap, about 25 USD per month for hosting.
- Effort: 490 person-hours in total.
- Technical: one server instance with 2 vCPU and 2 GB RAM; no secrets in the repository.
- Quality: WCAG AA contrast and keyboard access; last two versions of the major browsers.

## 8. High-level risks
- The campus proxy may block WebSocket; mitigation: test through the campus network in week 3 and keep the SockJS fallback ready.
- Spring Boot 4 and Spring Security 7 are newer than most tutorials; mitigation: build a small vertical slice in weeks 2-3 and record what differs from the tutorials.
- Could features may creep into the MVP; mitigation: scope list in section 3, change requests approved by the sponsor, feature freeze in week 10.

## 9. Project manager authority
The PM decides alone, within the 490 h and the 200 USD: task allocation, the order of Should and Could features, the content of each phase demo, and spending the 25 USD reserve. The PM re-plans within these limits without approval.

The PM needs the sponsor's written approval, given within 5 working days, to: add scope (anything listed as out of scope, or a new Must feature), move the week-7 demo or the week-14 pilot, spend beyond the 200 USD cash cap or the reserve, or change the team members.

## 10. Approval
Sponsor: Head of the IT department   Date: 25/10/2026
PM: Supervising lecturer   Date: 25/10/2026
