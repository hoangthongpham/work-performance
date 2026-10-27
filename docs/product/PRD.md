# Work Performance — Product Requirements Document (PRD)

> **Task:** WP-001 | **Version:** 1.0-draft | **Date:** 2026-10-27 | **Status:** Draft — awaiting product-owner approval  
> **Product:** Web Application / Progressive Web App | **Strategy:** Personal-first, team-ready  
> **Source of truth:** This file. Detailed lifecycle, KPI formulas, ERD, and API contracts are follow-up design tasks.

## 1. Executive summary

Work Performance helps an individual plan, execute, track, and review tasks, projects, goals, and time spent, using weekly, monthly, and quarterly performance insights. The first release optimizes personal productivity while preserving data boundaries and authorization needed for future team collaboration.

**Product proposition:** one place to answer what needs doing, what matters most, what is late, whether plans match reality, and whether outcomes are improving—without burdensome manual data entry.

## 2. Problem and outcomes

### Current problems
- Tasks, deadlines, goals and time estimates can be scattered or disconnected.
- Finishing many tasks is not equivalent to delivering important outcomes.
- Retrospectives rely on memory and cannot easily compare planning vs actual results.
- A personal-only data model often requires costly redesign for teams.

### Desired outcomes
1. Capture and prioritize work rapidly.
2. See project progress, deadlines and blockers reliably.
3. Connect important work to outcomes and goals.
4. Measure delivery, on-time performance and estimate accuracy with transparent definitions.
5. Run actionable weekly reviews and preserve historical report snapshots.
6. Prepare for team workspaces without exposing personal data.

### Proposed validation signals (targets to confirm after pilot)
- User can create a basic task with title only.
- Completing and reviewing a week's work requires no duplicate data entry.
- All displayed KPI values can be traced to an eligible record and a calculation period.
- No cross-workspace read or write is permitted by API or background processing.

## 3. Personas and jobs to be done

| Persona | Release | Primary job |
|---|---|---|
| Individual contributor (owner of personal workspace) | MVP | Plan today/week; focus on priorities; complete work; reflect |
| Independent professional handling multiple projects | MVP | Track milestones, estimates, actual time and goals |
| Team member | Future | Receive, update and discuss assigned tasks |
| Team manager / workspace admin | Future | Allocate workload, monitor delivery, review team outcomes |

**Primary context:** Vietnamese user, local timezone display (Asia/Ho_Chi_Minh by default as a proposed setting), desktop and mobile web; localization framework should not assume a single language forever.

## 4. Product principles

1. **Personal-first:** new accounts receive a personal workspace automatically; no team-management UI required to start.
2. **Team-ready:** all business records belong to a workspace, with authorization enforced server-side.
3. **Low friction:** quick add, defaults, derived metrics and reusable task details; avoid repeated form fields.
4. **Transparent measurement:** display numerator, denominator, window, exclusions and missing-data states.
5. **Honest performance:** score is a supporting signal, not an evaluation verdict; consider task significance and data quality.
6. **Preserve history:** immutable closed-period snapshots with subsequent adjustments recorded separately.
7. **Accessible responsive UX:** mobile-first PWA and usable keyboard navigation.
8. **Security by default:** least privilege, workspace isolation, audit-sensitive actions.

## 5. Scope and release boundaries

### MVP (required)
- Account authentication, sign out and personal workspace provisioning.
- Dashboard (due soon, overdue, priority focus, work progress and KPI summary).
- Tasks: quick add, CRUD, status, priority, due date, tags, subtask, project assignment, list/kanban/calendar views, filtering and sorting.
- Projects: CRUD, status, target dates, linked tasks, milestones and derived progress.
- Time tracking: manual time entries, estimated vs logged duration per task; start/stop timer is desirable but not mandatory for first release.
- Goals and measurable key results with check-ins; monthly/quarterly cycles.
- Performance Analytics: weekly/monthly/quarterly views, calculation provenance, data-quality indicators and period snapshots.
- Weekly Review: guided accomplishments, missed items, blockers, improvement notes and next-week priorities.
- User settings: timezone, appearance (light/dark), reporting week start, configurable KPI weights.
- Workspace-aware authorization, audit history for material changes, testable APIs.

### Phase 2 (post-MVP)
Notifications/reminders, recurring tasks, external calendar sync, GitHub sync, independent VS Code API integration, CSV export, more advanced analytics.

### Phase 3 (post-MVP)
Team workspaces, invitations, role-based access, assignment and workload balancing, team goals, performance reviews, manager dashboards and analytics.

### Explicitly out of scope for MVP
Microservices, Kubernetes, billing, chat, native mobile apps, AI-based automatic rating, company-wide HR appraisal, direct writes to VS Extends, offline-first conflict resolution, and automatic GitHub data import.

## 6. End-to-end workflows

### WF-01 First use
Sign up/log in → personal workspace created → onboarding with timezone/week-start defaults → empty dashboard → quick-add first task.

### WF-02 Daily work
Open dashboard → inspect focus/due/overdue → create or reprioritize tasks → change status → log actual effort (if applicable) → finish tasks → dashboard refreshes.

### WF-03 Project planning
Create project → create milestone(s) and tasks → choose optional estimates/due dates → update task execution → project progress derived from task state.

### WF-04 Goal cycle
Create time-bounded goal → add one or more measurable key results → record check-ins → inspect goal progress and evidence → review at month/quarter end.

### WF-05 Weekly review
Select reporting week → inspect computed delivery/time/goal numbers with denominators → add reflection and next actions → close review to snapshot → prior snapshot stays unchanged even when underlying tasks change.

### WF-06 Corrections
After report close, editing a task is permitted by policy, but cannot mutate a previously published snapshot. New calculation reflects edits, and adjustment/audit information explains divergence.

## 7. Functional requirements

Priority notation: **MUST** = MVP release gate, **SHOULD** = MVP if feasible, **LATER** = Phase 2/3.

| ID | Priority | Requirement |
|---|---|---|
| FR-AUTH-01 | MUST | Authenticated users can access only authorized workspace resources |
| FR-AUTH-02 | MUST | Personal workspace created for each new user |
| FR-TASK-01 | MUST | Create task with title only; defaults set without extra prompts |
| FR-TASK-02 | MUST | Update status, priority, due date, project and tags; edit/delete subject to policy |
| FR-TASK-03 | MUST | Create subtask and show parent-child completion without cycles |
| FR-TASK-04 | MUST | Filter/sort tasks; show list, kanban and calendar |
| FR-TASK-05 | MUST | Track status and due-date changes as events |
| FR-TASK-06 | SHOULD | Add blockers/dependencies with cycle prevention |
| FR-PROJ-01 | MUST | CRUD project and milestones; derive progress from eligible tasks |
| FR-TIME-01 | MUST | Store estimates and manual time entries; calculate actual total |
| FR-TIME-02 | SHOULD | Start/stop timer with single-running-timer protection |
| FR-GOAL-01 | MUST | Create monthly/quarterly goals and measurable key results |
| FR-GOAL-02 | MUST | Record dated check-ins and track value/target progress |
| FR-DASH-01 | MUST | Show upcoming, overdue, priorities, project progress and selected period KPI summary |
| FR-AN-01 | MUST | Calculate documented KPI values by week/month/quarter |
| FR-AN-02 | MUST | Clearly show insufficient/no data rather than falsely reporting 0% |
| FR-AN-03 | MUST | Preserve closed-period snapshots with versioned metric definitions |
| FR-REV-01 | MUST | Guided weekly review with narrative and next priorities |
| FR-REV-02 | MUST | Close review and preserve its snapshot and author/time |
| FR-SET-01 | MUST | Configure timezone, week start, light/dark and KPI weights |
| FR-AUD-01 | MUST | Audit key task/review mutations with actor and timestamp |
| FR-INT-01 | LATER | Calendar/GitHub/VS Code integrations via independent contracts |
| FR-TEAM-01 | LATER | Team roles, invitations, assignments and team analytics |

### Core UX screens
Dashboard; My Tasks (List, Kanban, Calendar); Project List & Detail; Goals & OKRs; Time Entries; Performance Analytics; Weekly Review; Settings; Auth/Onboarding. Desktop sidebar and mobile bottom navigation; quick add is globally available.

## 8. Lifecycle proposal (to formalize in WP-002)

**Task:** Todo → In Progress → Done. Optional Blocked; Cancelled terminal; Reopened is an auditable transition from Done. A task may move backward with history. Due-date changes retain old/new value. Deleting should not erase historical aggregate evidence silently.

**Project:** Planned → Active → Completed / Archived; Paused optional. Project progress must not rely on ambiguous manual percentages when task data is available.

**Goal:** Draft → Active → Completed / Closed; Cancelled optional. Check-ins do not rewrite prior check-ins.

**Open decisions:** whether Blocked is separate from In Progress; behavior of cancelled task and parent/subtask; due-date freeze policy; reopen effect on on-time metrics.

## 9. Analytics and KPI policy (preliminary; detailed definitions in WP-003)

| ID | Metric | Initial calculation concept | Important exception |
|---|---|---|---|
| KPI-01 | Task Completion Rate | completed eligible tasks / tasks in eligible cohort | Define cohort by planned/due/completed dates |
| KPI-02 | On-time Completion Rate | eligible completed tasks completed by frozen due date / eligible completed tasks with due date | Missing due date = N/A/excluded, never assumed on-time |
| KPI-03 | Estimate Accuracy | actual vs estimated duration, shown in time and variance % | Estimate=0/missing or actual missing shown separately |
| KPI-04 | Overdue Tasks | unfinished tasks whose due instant passed at period cut-off | User timezone and all-day semantics matter |
| KPI-05 | Goal Progress | key-result measured progress by target and direction | Zero target, inverse metrics and weights |
| KPI-06 | Project Progress | eligible completed tasks / eligible total tasks (initial) | Task size/weight may change interpretation |
| KPI-07 | Workload | planned and tracked duration by selected period | Unestimated tasks separate |
| KPI-08 | Performance Trend | comparable metric deltas across equivalent closed periods | Show N/A for non-comparable periods |

Reference performance dimensions: Goal Achievement 35%; Delivery 30%; Planning Accuracy 20%; Continuous Improvement 15%. These are **default proposals, not approved business rules**. Allow configuration with weights summing to 100%. Avoid presenting an overall score when data sufficiency criteria are not met; never use a single score as a definitive judgment.

**Required formalization before implementation:** exact cohort and denominators, missing values, relative changes, all-day due dates, reopened/completed/cancelled tasks, dates changed after start, timezone and DST, period cut-off, review re-calculation and snapshot versioning.

## 10. Data ownership and integrity

- Each business record is scoped to exactly one workspace, with referential integrity enforcing same-workspace relations wherever relevant.
- Authorization is checked in service/policy/query paths, not trusted to client filtering.
- User can own/join multiple workspaces eventually; MVP permits personal workspace only in UI.
- Persist timestamps as UTC instants; date-only deadlines and reporting calendar days use workspace/user timezone explicitly.
- Capture task events (at least status, due date, completion, project movement) and review snapshot provenance.
- Audit logs must avoid secrets and excessive personal content. Retention/deletion policy is an open decision.
- No team permissions or invitations required in MVP; schema preserves later extensibility.

## 11. Nonfunctional requirements

| ID | Requirement and proposed acceptance approach |
|---|---|
| NFR-SEC-01 | Automated denial tests for cross-workspace API access and mutation; unauthenticated requests denied |
| NFR-SEC-02 | Secure session/token management, input validation, rate limits, secrets outside Git |
| NFR-PERF-01 | Set baselines on representative dataset; proposed p95 API latency under 500 ms for standard list/detail endpoints in controlled staging tests, to validate |
| NFR-UX-01 | Responsive at 360 px mobile through desktop widths; no unintended horizontal overflow in primary views |
| NFR-ACC-01 | Target WCAG 2.2 AA for key flows; keyboard focus and contrast audits |
| NFR-REL-01 | Backup/restore and safe schema migration documented/tested before production |
| NFR-OBS-01 | Structured errors/logging, request correlation and health endpoints; no credentials in logs |
| NFR-TEST-01 | PHPUnit/Pest backend, Vitest frontend, Playwright critical journeys; lint/typecheck/build in CI |
| NFR-DATA-01 | Archived review snapshots stay stable; audit trail describes modifications to input data |
| NFR-PWA-01 | Installable responsive shell and graceful online/offline error messaging; offline edits not promised for MVP |

**Accessibility, performance and security are release quality gates; numeric budgets are hypotheses pending infrastructure and baseline evidence.**

## 12. Acceptance criteria by module

### AC-01 Onboarding & security
- Given a new account, when registration succeeds, then it has an accessible personal workspace.
- Given a record in workspace B, when a user authorized only for workspace A requests or mutates it, then no record content leaks and no mutation occurs.
- Given an unauthenticated request, then protected APIs reject it.

### AC-02 Tasks
- Given title alone, when the user uses Quick Add, then a task is created with defined default status and workspace.
- Given a task moved across Kanban, when saved, then list, calendar and dashboard agree on status.
- Given due date/status changes, when audited, then previous and new values can be traced.
- Given subtasks, when calculating progress, then cycles and accidental double counting are prevented.

### AC-03 Projects
- Given project tasks and milestones, when one task completes, then project view updates using a documented progress denominator.
- Given no tasks, then progress displays an explicit empty state.

### AC-04 Time
- Given multiple time entries, then actual duration is their valid total without overlaps being silently assumed.
- Given no estimate, then estimate-accuracy display is N/A, not 0%.

### AC-05 Goals
- Given a measurable key result with baseline/current/target, then progress follows documented direction/bounds.
- Given a check-in, then the dated value and actor remain accessible.

### AC-06 Performance
- Given a reporting period and eligible data, then KPI output includes value, cohort/denominator and metric-definition version.
- Given missing or insufficient data, then UI shows a meaningful missing-data message.
- Given a closed snapshot and later task edit, then the stored snapshot remains unchanged.

### AC-07 Weekly Review
- Given the selected week, then the review can reference calculated KPIs, blockers and next-week priorities.
- Given a closed review, then reopen/correction follows explicit policy and the original snapshot is retained.

### AC-08 Mobile/desktop
- Given mobile width of 360 px, then tasks, quick add and reviews are usable without unintended horizontal overflow.
- Given keyboard-only interaction, then core dialogs, menus and forms remain operable.

## 13. Test and release gates

**Traceability:** each MUST requirement maps to at least one automated test and any applicable manual UX review. CI blocks merge on failing unit/integration tests, typecheck, lint or build; E2E critical journeys gate release.

Suggested coverage target: at least 80% on critical business logic, *not* a substitute for required scenario coverage. Tests must cover workspace isolation, transitions, metric edge cases, snapshot immutability, timezone boundaries and mobile workflows.

Evidence must include command, environment, commit SHA, passed/failed/skipped counts, and known omissions. Never mark PASS without an observed run. Release needs migration/backup/restore/rollback drills, security triage, staging verification and product-owner approval.

## 14. Dependencies and constraints

- Proposed stack (requires compatibility verification at S0): Vue 3/TypeScript/Vite, Tailwind CSS/shadcn-vue, Pinia, Laravel 13/PHP 8.3+, Sanctum, PostgreSQL 17, Redis, Nginx, Docker Compose, REST /api/v1.
- Modular monolith, PWA, no microservices/Kubernetes for MVP.
- Standalone repository `hoangthongpham/work-performance`; no changes to `hoangthongpham/vs_extends` or any unrelated project.
- Branches `main` stable, `dev` integration, `feature/*` per task; merge requires approval.
- Never assume local machine paths, credentials or production deployment target.

## 15. Roadmap baseline

| Phase | Period estimate | Deliverable / gate |
|---|---|---|
| P0 Planning | Week 1 | PRD approved; business rule decision log |
| P1 Architecture & UX | Week 2 | ERD, API, security design, UI prototype approved |
| S0 Foundation | Week 3 | Repo structure, Docker, auth, migrations, CI green |
| S1 Work Management | Weeks 4–5 | Tasks/projects use cases and tests |
| S2 Goals & Time | Week 6 | Goals, check-ins and tracking tests |
| S3 Analytics | Weeks 7–8 | Versioned metrics, scenarios and snapshots tests |
| S4 Reviews & QA | Week 9 | Weekly Review and full regression |
| S5 Release | Week 10 | Staging + production readiness, rollback, user approval |

Estimate is provisional; schedule adjusts with validated scope and test results.

## 16. Risks and mitigations

- **Vanity KPIs / gaming:** never rank on task count alone; show data quality and underlying dimensions.
- **Deadline changes bias on-time rate:** preserve due-date history and agree frozen baseline policy before metric engine.
- **Scope creep:** defer integrations, team collaboration and advanced automation.
- **Time entry burden:** optional tracking and lightweight entry; unknown ≠ zero.
- **Team expansion leaks:** workspace-bound data and authorization tests from S0.
- **Historical inconsistency:** version metric definitions and freeze closed snapshots.

## 17. Open decisions requiring product-owner sign-off

| ID | Decision | Proposed default |
|---|---|---|
| D-01 | How to define task commitment/weekly cohort? | Due-in-period plus explicit planned-week membership; avoid mixing denominators |
| D-02 | Which due date determines on-time success after edits? | Frozen commitment due date, with change history |
| D-03 | Do task points/complexity enter MVP performance? | Show task-level priority first; weighted analysis later |
| D-04 | Can a completed task be reopened? | Yes, audited; historical snapshot unchanged |
| D-05 | Task delete vs archive? | Archive/soft delete business records with retention policy |
| D-06 | Does MVP require timer? | Manual entries MUST; timer SHOULD |
| D-07 | Is composite performance score enabled by default? | No; present four dimensions separately |
| D-08 | Week start and timezone? | Monday; configurable timezone |
| D-09 | Handling zero or empty denominator? | N/A with explanation |
| D-10 | Deployment host/domain and authentication options? | Determine during S0; do not assume |

## 18. Definition of Done — WP-001

- [x] Versioned PRD draft documents product goals, MVP boundaries, personas and workflows.
- [x] Functional requirements and testable acceptance criteria defined.
- [x] NFRs, KPI assumptions, data isolation and risks recorded.
- [x] Proposed roadmap, quality gates and open decision register recorded.
- [ ] Product owner reviews and approves v1.0.
- [ ] Follow-up WP-002/WP-003 details lifecycle and KPI definitions.

**Status: Draft ready for review, not approved.**
