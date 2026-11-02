# Risk Register

> Copy to `delivery-leadership-package/risk-register.md`. At least 5 rows. **No boilerplate**; your peers will grade you on whether these are real.

| # | Risk | Owner | Likelihood (L/M/H) | Impact (L/M/H) | Mitigation | Trigger to escalate |
|---|---|---|---|---|---|---|
| R1 | AI-drafted code can look fine in a demo but compute wrong answers($0.35 vs. $400) | Delivery Lead | M | H | Every change must pass npm test before merging, and premium math is checked against the rate table. | Any test fails on main, or premium looks absurd in a demo |
| R2 | Bad data outlives bad code. The $0.35 quote is still in the database even though the code is fixed  | Delivery Lead | H | H: wrong calculation reaches the customer | Thursday's seed clears it; until then, don't use this data for real calculations | The partner integration team starts pulling quotes for real calculations before the reset |
| R3 | Typos in hand-typed commands or code cause runs to fail | Delivery Lead | H | M:it slows delivery, but tests and error messages usually catch it fast  | Copy/paste from the README, use Tab autocomplete, run npm test before committing | Stuck on the same error for more than 15 minutes, or CI fails on the PR |
| R4 | 5 known npm audit vulnerabilities in dependencies, not fixed this week | Delivery Lead | L: the service runs locally only this week, so exploitation is unlikely | H:a security breach in an insurance app | Dependencies pinned; findings logged, schedule a fix review before any production deployment | Before production deployment, or if npm audit reports a critical finding  |
| R5 | Partner integration team can't get what they need (the API is down or changes shape) | Delivery Lead | M | H: customers can't get quotes through the partner's app | All tests pass before merging; keep REST and GraphQL fields stable; notify partners before any change | The health route stops returning ok, or a partner reports an error |

## How I'll use this register

I will re-read this register at every daily check-in (10:00), whenever an injecti or surprise changes the plan, and once more before merging the final PR. It lives in the repository, so the team, the instructor and the sponsor can all see it. The cadence is daily, plus an immediate update whenever a trigger fires or a new risk appears; I will raise any risk that hits its trigger at the next check-in, or sooner if it is High impact. 
