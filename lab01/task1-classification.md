# Task 1: project, operation or programme?

| #  | Initiative | Temporary? | Unique? | Coordinated? | Class | Justification |
|----|------------|------------|---------|--------------|-------|---------------|
| 1  | Build the Realtime Quiz platform and pilot it with 50 students in week 14 | yes | yes | no | Project | It ends with the week-14 pilot and delivers a platform that did not exist before, with no sibling projects. |
| 2  | Run the nightly backup of the gicitc.com PostgreSQL database | no | no | no | Operation | It repeats every night with the same output and no end date; it is part of keeping the service running. |
| 3  | Move the department's three web servers to a new Linode region before 15 December | yes | yes | no | Project | It has a deadline (15 December) and a one-off result, the three servers running in the new region, after which the work stops. |
| 4  | Answer helpdesk tickets within the 4-hour service level | no | no | no | Operation | It is a continuous service with a standing 4-hour target and no end date; every ticket repeats the same routine. |
| 5  | "Digital classroom": Realtime Quiz, LMS upgrade and lecture capture sharing one login and one grade export | yes | yes | yes | Programme | Three related projects; the shared login and grade export are a benefit that none of them delivers alone, so they are coordinated. |
| 6  | Apply the monthly security patches to the VPS | no | no | no | Operation | It repeats every month with the same output and no end date; it keeps the VPS secure and creates nothing new. |
| 7  | Add multi-node scaling (RabbitMQ relay, Redis registry) to Realtime Quiz next semester | yes | yes | no | Project | It is planned for one semester and adds a capability that does not exist yet (a relay and a registry), so it has its own end and result. |
| 8  | Operate the Realtime Quiz platform after go-live: password resets, restarts, monitoring | no | no | no | Operation | It starts at go-live and has no end date; password resets, restarts and monitoring repeat for as long as the service runs. |
| 9  | Write and publish the department's annual IT report for the dean by 31 January | yes | yes | no | Project | It has a fixed deadline (31 January) and each edition has new content, so one report is a single bounded deliverable. |
| 10 | Replace 40 wireless access points in two buildings during the summer break | yes | yes | no | Project | It is bounded by the summer break and delivers a one-off result, 40 new access points installed; it shares no benefit with other projects. |

## Grey zones
**Row 7 (multi-node scaling).** It could be read as a maintenance release that belongs to operations or as a new project. It is a project if the sponsor authorises and funds it separately, with a budget and a clear "done" (for example, two nodes passing the 100-student load test); if it is just an open-ended item in the operations backlog without its own end date, it is operations.

**Row 9 (annual IT report).** It repeats every year, which points to an operation, yet each edition has new content and a hard deadline, which points to a project. It is a small yearly project if it gets its own scope, deadline and people each year; it is an operation if the same team follows a fixed template and routine with no separate authorisation.

## What our project hands over
At go-live in week 14 the Realtime Quiz project hands the running platform to the department's IT operations (the administrator of the gicitc.com VPS), who then own restarts, monitoring, backups, security patches and password resets as ongoing operations. To run it, they need from the team a runbook, the production Docker Compose and environment-variable list (with no secrets in the repository), a tested backup and restore procedure, a monitoring checklist and a list of known issues. The team delivers these before the week-13 pilot readiness gate and holds one hand-over session, so that after week 14 the lecturers raise support requests with IT operations rather than with the students.
