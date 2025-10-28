 📊 Group Test Management Report — Word Puzzle Game Plus

## 👥 Team Information

| Role | Name | Responsibilities Completed |
|------|------|---------------------------|
| Test Manager | Fatahi Showunmi | - Created comprehensive test plan<br>- Managed test schedule and resources<br>- Tracked metrics and progress |
| Risk Analyst | Dennis Gachuru | - Identified and assessed risks<br>- Designed risk-based test cases<br>- Prioritized testing efforts |
| Test Executor | Whitney Wairimu | - Executed test cases<br>- Logged and validated defects<br>- Captured test evidence |

## 🎯 Test Plan

### Objectives
- Verify functionality of new features: Reset Game, Leaderboard, and Bonus Round
- Ensure data integrity in localStorage implementation
- Validate score calculation and bonus round triggers
- Test UI/UX responsiveness and accessibility
- Identify and mitigate potential security risks

### Scope

**In Scope:**
- User input handling and validation.
- Hint functionality and correctness.
- New Puzzle generation and Reset behaviour.
- Leaderboard persistence and sorting logic.

**Out of Scope:**
- Server-side persistence
- Multiplayer features (not implemented in this project).

### Resources & Environment
- **Browser:** Chrome (latest version)
- **Tools:** VS Code, Github, Chrome DevTool
- **Test Data:** Word bank entries
- **Testing Duration:** 4 days

### Schedule

| Phase | Planned Duration | Actual Duration | Status | Owner |
|-------|------------------|-----------------|--------|-------|
| Test planning & risk analysis | 4 hrs | 4 hrs | Completed | Test Manager / Risk Analyst |
| Test design | 4 hrs | 4 hrs | Completed | Risk Analyst |
| Test execution | 1 day | 1 day | Completed | Test Executor |
| Defect triage & retest | 6 hrs | 6 hrs | Completed | All |
| Final report & sign-off | 8 hrs | 8 hrs | Completed | Test Manager |

### Entry/Exit Criteria

**Entry Criteria:**
- Application ran with live server.
- Test cases reviewed and signed off by Test Manager.
- Test data prepared and accessible.

**Exit Criteria:**
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

## Reflection

### Team Collaboration Effectiveness
- Daily sync meetings improved coordination
- Shared risk analysis enhanced test coverage
- Clear role definition increased efficiency

### Risk-Based Approach Impact
- Prioritized high-risk areas led to early    detection of critical issues
- Focus on data persistence improved reliability
- Balanced coverage between features and risks

### Improvement Areas
- Implement automated regression tests
- Expand browser compatibility testing
- Add performance metrics tracking
- Enhance test data generation

## Sign-Off

We certify that all planned testing activities have been completed according to the test plan and risk assessment.

| Name | Role | Initials | Date |
|------|------|-----------|------|
| Fatahi Showunmi | Test Manager | FS | 2025-10-28 |
| Dennis Gachuru | Risk Analyst | DG | 2025-10-28 |

###Test Cases

| ID | Feature | Objective | Steps (summary) | Expected Result | Actual Result | Status | Risk Link |
|----|---------|-----------|-----------------|-----------------|---------------|--------|-----------|
| TC-01 | Leaderboard | Verify top-3 sorting logic | Submit scores 70,80,180 → open leaderboard | Scores shown 180,80,70| 180,80,70 | Pass | R-01 |
| TC-02 | Reset Game | Verify Reset clears score & progress | Play to score >0 → Click Reset | Score=0, puzzle index resets | Score & index reset | Pass | R-02 |
| TC-03 | Bonus Round | Verify every 3rd puzzle applies x2 multiplier | Complete puzzles 1–3 and note points | Puzzle 3 points = base ×2 | Multiplier applied correctly | Pass | R-03 |
| TC-04 | Input Validation (Negative) | Ensure invalid inputs don't crash app | Submit "<script>" as answer | App sanitizes/blocks input; no crash | App threw an error | Fail | R-05 |
| TC-05 | Leaderboard (Boundary) | Verify only top 3 scores persist | Submit >3 scores with varying values | Only top-3 are stored | Top-3 retained | Pass | R-01 |
| TC-06 | Usability | New user can complete tutorial puzzle | Observe new user attempting tutorial | User completes with minor confusion (notes) | not Completed; no notes recorded | fail | R-04 |
| TC-07 | Reset + Persistence (Negative) | Reset does not clear leaderboard | Save score → Reset → check leaderboard | Leaderboard remains intact | Leaderboard intact | Pass | R-02, R-06 |
| TC-08 | Performance | App responsiveness under diffrent screen sizes | adapt to diffrent screen sizes | UI responds properly, no glitch| Responsive; acceptable | Pass | R-04 |

Total executed: 8 | Passed: 6 | Failed: 2

## Defects (GitHub Issues)

| ID | Issue Title       | Severity | Risk ID | Status |
|----|-------------------|----------|---------|--------|
| D-01 | Game never ends | Medium   | R-01    | Open |
| D-02 | no filtering and verification of input | High | R-05 | open |


## Metrics

- Test Case Pass Percent: (6 / 8) × 100 = 75%
- Defect Density: Defects / Test Cases = 2 / 8 = 0.25
- Risk Coverage Percent: 100% (6 / 6)
- Regression success rate:0 retest executed

### Defect Distribution
```
Critical: 0   
High:    1 
Medium:  1   
Low:     0 

### Defect Summary

- Total Defects Logged: 2
- Critical / High: 1
- Fix Rate: 0

## Test Control & Project Management

### Phases

| Phase | Deliverable | Actual Output | Variance | Owner |
|-------|-------------|---------------|----------|-------|
| Planning | Test plan & risk list | Completed | 2hrs| Test Manager |
| Design | Test cases documented | Completed | 2hrs | Risk Analyst |
| Execution | Test execution & evidence | Completed (see table) | 6hrs | Test Executor |
| Triage | Defect triage & retest | pending | - | all |
| Closure | Final report & sign-off | Pending | - | Test Manager |

**Progress Tracking Method:** GitHub Issues for defects, markdown files, risk analysis ,test cases and this report for metrics.

**Change Control Notes:** Any scope deviation or blocked tests were recorded as issues and communicated via the project board.


## ✅ Sign-Off
| Name | Role | Initials | Date |
|------|------|-----------|------|
| Whitney Wairimu | Test Executor | WW | 2025-10-28 |