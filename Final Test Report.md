# 🧪 Final Group Test Report — Word Puzzle Game Plus

**Level:** Intermediate QA | **Week 5:** Test Management

**Course:** Software Testing & Quality Assurance  
**Module:** Test Management (Week 5)  
**Project Type:** Group Assessment  
**Submission Date:** 2025-10-28

## Team Information

| Role | Name | Responsibilities |
|------|------|------------------|
| Test Manager | Fatahi Showunmi | Planning, scheduling, coordination, metric tracking |
| Risk Analyst | Dennis Gachuru | Risk identification, prioritization, test design linkage |
| Test Executor | Whitney Wairimu | Execution, evidence capture, defect logging |

## Group Rules

- Each student must belong to only one group.
- Duplicate membership or multiple submissions will result in invalidation.
- Every group member must contribute towards this project.

## Project Overview

**System Under Test:** Word Puzzle Game Plus  
**Technology Stack:** HTML, CSS, JavaScript  
**Environment:** Chrome Browser (Desktop)

### Features Under Test

| Feature | Description | Risk Category |
|---------|-------------|---------------|
| Reset Game | Clears score and progress instantly | High |
| Leaderboard | Stores top 3 scores in localStorage | Medium |
| Bonus Round | Every 3 puzzles → doubles score | High |

## Test Plan

### Objectives

- Ensure random letter generation and scoring function work correctly.
- Verify user inputs, hints, and leaderboard persistence operate as expected.
- Confirm UI updates for 'score', 'solved' and 'Bonus at' are correct and timely.

### Scope 

**In Scope:**
- User input handling and validation.
- Hint functionality and correctness.
- New Puzzle generation and Reset behaviour.
- Leaderboard persistence and sorting logic.

**Out of Scope:**
- Multiplayer features (not implemented in this project).

### Tools & Resources

- Chrome (latest stable) — recommended test browser
- VS Code — development / test scripting
- GitHub Issues / Projects — defect tracking and collaboration
- Chrome DevTool - UI responsiveness

### Schedule (planned vs actual)

| Phase | Planned Duration | Actual Duration | Status | Owner |
|-------|------------------|-----------------|--------|-------|
| Test planning & risk analysis | 4 hours | 4 hours | Completed | Test Manager / Risk Analyst |
| Test design | 4 hours | 4 hours | Completed | Risk Analyst |
| Test execution | 1 day | 1 day | Completed | Test Executor |
| Defect triage & retest | 6 hours | 6 hours | Completed | All |
| Final report & sign-off | 8 hours | 8 hours | Completed | Test Manager |

## Entry & Exit Criteria

Entry Criteria:
- Application ran with live-server.
- Test cases reviewed and signed off by Test Manager.
- Test data prepared and accessible.

Exit Criteria:
- All high-severity defects fixed and verified.
- Pass rate >= 80% for planned test cases.
- Risk coverage >= 80% for identified high/medium risks.
- Test execution status and metrics documented.

## Risk Analysis

### Risks

| ID | Feature | Risk Description | Likelihood | Impact | Priority | Mitigation Strategy |
|----|---------|------------------|------------|--------|----------|---------------------|
| R-01 | Leaderboard | Incorrect sorting → wrong top-3 shown | Medium | High | High | Add unit tests for sorting, snapshot after updates |
| R-02 | Reset Game | State not fully cleared → residual score persists | Low | High | Medium | Add integration test for reset; ensure reset function resets all relevant state variables |
| R-03 | Bonus Round | Bonus multiplier applied incorrectly (off-by-one) | Medium | Medium | Medium | Add boundary tests for round counters; add logging around multiplier calculation |
| R-04 | UI Responsiveness | Controls overlap at small widths → usability degradation | Medium | Medium | Medium | Add responsive checks in Chrome DevTools; add simple CSS fixes or constraints |
| R-05 | Input Validation | Invalid characters break scoring or crash the app | Low | High | Medium | Sanitize and validate inputs; add negative tests for special characters and scripts |
| R-06 | Persistence | localStorage or corruption prevents leaderboard save | Low | Low | Low | Limit stored entries; implement graceful fallback (in-memory) and user notification |

### Risk Coverage

- Total identified risks: 6
- Risks covered by test cases: 6
- Tested Risks Percent: 100%
- Untested Risks Percent: 0%

## Test Cases

| ID | Feature | Objective | Steps (summary) | Expected Result | Actual Result | Status | Risk Link |
|----|---------|-----------|-----------------|-----------------|---------------|--------|-----------|
| TC-01 | Leaderboard | Verify top-3 sorting logic | Submit scores 70, 80, 180 → open leaderboard | Scores shown 180, 80, 70 | 180, 80, 70 | Pass | R-01 |
| TC-02 | Reset Game | Verify Reset clears score & progress | Play to score >0 → Click Reset | Score=0, puzzle index resets | Score & index reset | Pass | R-02 |
| TC-03 | Bonus Round | Verify every 3rd puzzle applies x2 multiplier | Complete puzzles 1–3 and note points | Puzzle 3 points = base ×2 | Multiplier applied correctly | Pass | R-03 |
| TC-04 | Input Validation (Negative) | Ensure invalid inputs don't crash app | Submit "<script>" as answer | App sanitizes/blocks input; no crash | App threw an error | Fail | R-05 |
| TC-05 | Leaderboard (Boundary) | Verify only top 3 scores persist | Submit >3 scores with varying values | Only top-3 are stored | Top-3 retained | Pass | R-01 |
| TC-06 | Usability | New user can complete tutorial puzzle | Observe new user attempting tutorial | User completes with minor confusion (notes) | Not Completed; no notes recorded | Fail | R-04 |
| TC-07 | Reset + Persistence (Negative) | Reset does not clear leaderboard | Save score → Reset → check leaderboard | Leaderboard remains intact | Leaderboard intact | Pass | R-02, R-06 |
| TC-08 | Performance | App responsiveness under different screen sizes | Adapt to different screen sizes | UI responds properly; no freezes; no glitch | Responsive; acceptable | Pass | R-04 |

Total executed: 8 | Passed: 6 | Failed: 2

## Defects (GitHub Issues)

| ID | Issue Title | Severity | Risk ID | Status | GitHub Link |
|----|-------------|----------|---------|--------|-------------|
| D-01 | Game never ends | Medium | R-01 | Open | https://github.com/PLP-Database-Design/wk-5-MuchaiG-1/issues/2 |
| D-02 | No filtering and verification of input | High | R-05 | Open | https://github.com/PLP-Database-Design/wk-5-MuchaiG-1/issues/3 |


## Metrics

- Test Case Pass Percent: (6 / 8) × 100 = 75%
- Defect Density: Defects / Test Cases = 2 / 8 = 25%
- Risk Coverage Percent: 100% (6 / 6)
- Regression Success Rate: 0 retest executed.

### Defect Summary

- Total Defects Logged: 2
- Critical / High: 1
- Fix Rate: 0 

## Test Control & Project Management

### Phases

| Phase | Deliverable | Actual Output | Variance | Owner |
|-------|-------------|---------------|----------|-------|
| Planning | Test plan & risk list | Completed | 2 hrs | Test Manager |
| Design | Test cases documented | Completed | 2hrs | Risk Analyst |
| Execution | Test execution & evidence | Completed (see table) | 6 hrs | Test Executor |
| Triage | Defect triage & retest | Pending | - | All |
| Closure | Final report & sign-off | Pending  | - | Test Manager |

**Progress Tracking Method:** GitHub Issues for defects, Markdown files for risk analysis, test cases and metrics.

**Change Control Notes:** Any scope deviation or blocked tests were recorded as issues and communicated via the project board.

## Lessons Learned

- Most Defect Prone Feature: User interface input (R-05) - No filtering and verification of input.
- Risk Analysis Impact: Prioritizing User-inputs tests found high-impact defects early.
- Team Communication Effectiveness: Daily short syncs helped coordinate testing.
- Improvements for Next Cycle: Add small unit tests for core logic (input validation,sorting, multiplier) and automate a smoke test that runs on each push.

## Attachments

- Evidence folder: /docs/evidence/ — place screenshots and console logs here.
- Issue links: add screenshots and console logs to the GitHub issues listed above.

## Sign Off

| Name | Role | Initials | Date |
|------|------|-----------|------|
| Fatahi Showunmi | Test Manager | FS | 2025-10-28 |
| Dennis Gachuru | Risk Analyst | DG | 2025-10-28 |
| Whitney Wairimu | Test Executor | WW | 2025-10-28 |

## Overall Summary

Statement:
The team executed the planned test cases against the Word Puzzle Game Plus. Most planned test cases passed (75% pass rate). One high-severity defects was identified and still open and one medium-severity defect remains open. The team recommends prioritizing the open defects before final sign-off and adding small automated checks for sorting and input validation.

Test Status: ☐ Completed / ☑ In Progress / ☐ Deferred

