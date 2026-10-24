# Business case: live quizzes for the IT department

## 1. Problem
Lecturers in the IT department mark quizzes by hand and give students no live feedback during class. The pain is quantified with the following assumptions (the chapter's example values):
- lecturers running quizzes: 10
- marking time per lecturer per week: 1 h (the platform removes all of it through automatic scoring)
- teaching weeks per year: 30
- notional value of one hour: 10 USD (students are unpaid; used to compare)

Marking load: 10 lecturers x 1 h x 30 weeks = 300 h per year, worth 300 x 10 = 3,000 USD per year (notional).

## 2. Options
| Option | Description | One-off cost | Annual cost | Annual benefit |
|--------|-------------|--------------|-------------|----------------|
| A      | Do nothing: keep marking by hand | 0 | 0 | 0 |
| B      | Buy a Kahoot-like quiz SaaS: 10 lecturers x 15 USD x 12 months | 0 (no set-up fee assumed) | 1,800 | 3,000 (300 h x 10 USD) |
| C      | Build Realtime Quiz with the charter budget: 490 h x 10 USD = 4,900 (notional) + domain and tools 75 USD | 4,975 | 300 (hosting 12 x 25 USD) | 3,000 (300 h x 10 USD) |

**SaaS price is an assumption.** 15 USD per lecturer per month is the course default, not a quoted price from a vendor page; I did not verify a real education price, so a cited price (page and date) should replace it if one is found. The hosting for the project period (4 x 25 = 100 USD) is part of the 200 USD cash budget in the charter, and the 75 USD one-off is the charter's domain (15) plus tools (60).

## 3. Comparison
| Option | Net annual benefit | Payback (years) | Sensitivity (6 lecturers) |
|--------|--------------------|-----------------|---------------------------|
| B      | 3,000 - 1,800 = 1,200 | 0 / 1,200 = 0 (no one-off) | 1,800 - 1,080 = 720; payback 0 |
| C      | 3,000 - 300 = 2,700 | 4,975 / 2,700 = 1.84 | 1,800 - 300 = 1,500; payback 4,975 / 1,500 = 3.32 |

Sensitivity line: with 6 lecturers the marking saved is 6 x 1 x 30 = 180 h = 1,800 USD per year; the SaaS costs 6 x 15 x 12 = 1,080 USD. Option C advantage over B: 2,700 - 1,200 = 1,500 USD per year with 10 lecturers, 1,500 - 720 = 780 with 6 (the benefits are equal, so the difference is licence 1,800 or 1,080 minus hosting 300).

Cash view: the 4,900 USD effort is students' unpaid learning time. In cash, C costs 75 USD once and 300 USD per year against 1,800 USD per year for B, a saving of 1,500 USD per year, so the cash payback of C against B is 75 / 1,500 = 0.05 years.

All figures reconcile with [business-case.csv](business-case.csv), where each amount has its written-out formula.

## 4. Benefits not priced
- Learning outcome: the team practises a full software and project cycle, which is the purpose of the capstone.
- Data ownership: quiz results and student data stay with the department, which also simplifies the data protection approval.
- No per-seat limit: more lecturers or students do not raise the cost.
- Control of features and a code base that later semesters can extend (for example multi-node scaling).

## 5. Risks per option
**A, do nothing**
- Marking load and the lack of live feedback continue.
- Lecturers may use free external tools on their own, so student data ends up outside the department's control.

**B, buy a SaaS**
- The licence cost grows with the number of lecturers, and the vendor may change the price.
- Student data is stored with a vendor, which may need data protection approval and creates lock-in.
- No learning outcome for the capstone team.

**C, build**
- The campus proxy may block WebSocket (fallback: SockJS).
- Spring Boot 4 and Spring Security 7 are newer than most tutorials, which can slow the build.
- Could features may creep into the MVP and endanger the week-7 demo.
- Late answers may race with the closing of a question and client clocks drift, so the server's timer must be authoritative.
- The PDF export must render Khmer names.

## 6. Recommendation and review gate
**Recommendation: option C, build Realtime Quiz.** Payback is 1.84 years at 10 lecturers (4,975 / 2,700), and in cash terms it pays back in 0.05 years against buying (75 / 1,500). With only 6 lecturers the notional payback stretches to 3.32 years, so the case then rests on the unpriced benefits (learning outcome, data ownership). If fewer than 7 lecturers commit to use the platform next semester, the payback exceeds 3 years (7 lecturers: 4,975 / 1,800 = 2.76; 6 lecturers: 3.32), and the sponsor should review the choice.

**Review gate:** if the week-7 MVP demo fails (not all 8 Must features pass live), switch to option B for next semester and treat the build as a two-semester project. A second gate is the week-13 pilot readiness review; if the data protection approval is missing, the pilot does not start (see the charter, milestone week 13).
