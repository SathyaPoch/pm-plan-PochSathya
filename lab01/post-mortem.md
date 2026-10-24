# Post-mortem: CampusPay wallet (fictional case from Lab-01)

## 1. Timeline and sources
| # | When | Event | Source |
|---|------|-------|--------|
| 1 | Start of the semester | The university asks its IT unit to build a cashless payment app for the canteen and the library fines in one semester. | fictional case from Lab-01 |
| 2 | Start of the semester | The head of finance "sponsors" the app by e-mail but never attends a review. | fictional case from Lab-01 |
| 3 | Start of the semester | The lead developer acts as project manager and coder at the same time. | fictional case from Lab-01 |
| 4 | Start of the semester | Success is defined only as "launch in September". | fictional case from Lab-01 |
| 5 | During the semester | After a survey, the requirements grow from canteen payments to bus tickets and parking. | fictional case from Lab-01 |
| 6 | Before launch day | No test with real card terminals is run. | fictional case from Lab-01 |
| 7 | Launch day to day 3 | The terminals reject 40 % of payments, the canteen queue doubles and the app is withdrawn after three days. | fictional case from Lab-01 |
| 8 | Five months later | The app relaunches for the canteen only. | fictional case from Lab-01 |

## 2. Classification and organisation
Project / programme: it started as one project (a payment app for two services), but the survey added bus tickets and parking, so the scope grew into several services that need coordination, in effect a small programme that was run without programme management.
Structure and PM authority: the case does not name the structure; the facts suggest a functional organisation in which the IT unit builds and finance owns the need. The PM was also the lead developer, so the PM had little time for management and no stated authority over scope, budget or the finance side.
Sponsor, charter, PMO: the sponsor existed only on paper (an e-mail, no reviews attended); no charter, no signed objectives and no PMO are mentioned in the case, so nobody was able to approve or refuse scope changes.

## 3. Success criteria
Stated: "launch in September", a date only.
Missing measurable criteria: payment success rate on real terminals (for example at least 99 %), a test with real card terminals before launch, queue time in the canteen, a limit on scope, and a defined "done" for each service.
Ignored dimensions (benefits, users, operations, team): benefits (shorter queues and less cash handling were never measured), users (students and canteen staff were not part of any test), operations (nobody planned who supports terminals and failed payments after launch) and team (one person did both management and coding).

## 4. Process groups and knowledge areas
| Process group              | What went wrong or was skipped |
|----------------------------|--------------------------------|
| Initiating                 | No charter and no real sponsor: the head of finance never accepted the role, so nobody could refuse the added bus-ticket and parking scope. |
| Planning                   | The plan contained only a launch month, with no test plan, no scope baseline and no risk list for the card terminals. |
| Executing                  | The team added services after the survey and built toward the date instead of toward tested, working payments. |
| Monitoring and controlling | Progress was judged by the calendar; without a single end-to-end test, nobody saw the terminal problem before launch day (the invisibility trap). |
| Closing                    | The app was withdrawn after three days and relaunched later, with no formal lessons learned or hand-over to operations in the case. |

Knowledge areas most responsible:
1. Scope management: requirements grew from the canteen and library fines to bus tickets and parking (event 5) with no change control.
2. Quality management: no test with real card terminals (event 6) led to 40 % rejected payments (event 7).
3. Stakeholder management: the sponsor never attended a review (event 2) and users were not involved, so nobody guarded the goals.

## 5. Ethics
Decision examined: launching on the promised date without running a test on real card terminals (events 6 and 7).
- Responsibility: not met; the team was accountable for the result and chose the date over finding out whether payments worked.
- Respect: not met; real students and canteen staff became the testers, and the queue doubled for them.
- Fairness: not met; the users carried the cost of the failed launch while the decision makers did not.
- Honesty: at risk; announcing a launch that no end-to-end test supports presents the app as ready when the evidence was missing.

## 6. What our project will do differently
| # | Commitment (We will ...) | Measured by | By week | Charter line |
|---|--------------------------|-------------|---------|--------------|
| 1 | We will run a live load test with 100 simulated students from the campus network, not only on a developer laptop, before the pilot | load test report with 0 errors and broadcast latency <= 500 ms at the 95th percentile | 13 | milestone week 13, O3 and O4 |
| 2 | We will hold a signed charter with a named sponsor who attends the week-7 and week-13 gates | signature on the charter and minutes of both gates | 1 | section 10 approval, authority clause (section 9) |
| 3 | We will freeze scope to the Must and Should lists and accept a change only through a written request approved by the sponsor within 5 working days | change log with one decision per request and no out-of-scope item built | 10 | scope section 3, authority clause (section 9), risk "Could features creep" |
| 4 | We will show working behaviour at the end of every phase with a tagged commit and a short demo instead of reporting percent complete | one tag and one demo note per phase, and 8 of 8 Must features in the week-7 demo | 7 | O1, milestones weeks 5 and 7 |
| 5 | We will secure the data approval and hand a runbook to IT operations before the pilot so that users and operations are not surprised | written approval from the data protection officer and a signed hand-over note from IT operations | 13 | milestone week 13, O2, assumption on pilot availability |
