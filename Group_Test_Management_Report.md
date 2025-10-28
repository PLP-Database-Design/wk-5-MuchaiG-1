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

### Risk-Based Approach Impact
- Prioritized high-risk areas led to early    detection of critical issues
- Focus on data persistence improved reliability
- Balanced coverage between features and risks

## Sign-Off

We certify that all planned testing activities have been completed according to the test plan and risk assessment.

| Name | Role | Initials | Date |
|------|------|-----------|------|
| Dennis Gachuru | Risk Analyst | DG | 2025-10-28 |