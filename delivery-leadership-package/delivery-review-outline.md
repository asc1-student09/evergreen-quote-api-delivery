# Delivery Review: Evergreen Quote

## Slide 1: Delivery goal & did we hit it?

- Goal: Deliver the Evergreen Quote API on `main` with green CI and a working local Kubernetes deployment by Thursday EOD.
- Hit? ☒ Yes  ☐ Partially  ☐ No
- One-line "why": Yes — the feature shipped on `main`, the merged PR was green, and the service ran successfully on kind with self-healing pods.

## Slide 2: What shipped

- curl transcript on `main`:
  - `curl localhost:3000/` -> `{"message":"Evergreen Quote API", "status":"ok"}`
  - `POST /api/quote` (auto, age 35, 50000) -> `"monthlyPremium":450`, the sponsor's rates
- Merged PR: https://github.com/asc1-student09/evergreen-quote-api-delivery/pull/13 (squash and merge, tagged `phase-3`)
- Green CI run: https://github.com/asc1-student09/evergreen-quote-api-delivery/actions/runs/42441687755 (installs from the lock file with `npm ci`, then runs 9 tests against a throwaway `mongo:7`)
- Extra work completed: inserted a quote by hand in mongosh, made a test fail on purpose, restored the Docker layer cache, and scaled the cluster to 5 replicas before deleting a pod and watching it self-heal.

## Slide 3: Two key decisions

- **Decision 1:** Said no to renters coverage this week. Why it mattered: it touches 6 areas and has no rate yet (a sponsor decision), so saying yes would have put the delivery goal at risk.
- **Decision 2:** Shipped on `node:22-alpine` despite the CVE flag. Why it mattered: it's moderate severity, the API isn't internet-exposed, and the patch lands next week, so holding would have missed the goal for little added safety. The upgrade is tracked in #11.
- (Both should be in `decision-memo.md`.)

## Slide 4: Risks & injects

- Top risk we tracked: AI-drafted code can look right in a demo but compute the wrong numbers. The tests caught it, and the bad $0.35 quote it left behind was cleared by re-seeding on Day 4.
- Inject #1 (Tue): Renters scope add + base image CVE. Re-prioritized the board, moved renters and the upgrade to next Wave, and sent the sponsor two asks with deadlines.
- Inject #2 (Wed): Customers getting 400s while `main` CI was red. I escalated it to engineering to confirm what was actually deployed and whether `main` was safe to merge. Go/no-go: GO WITH CONDITIONS on Day 3; full GO once the conditions were checked and documented on Day 4.

## Slide 5: What I'd do differently next round

- run `docker ps` before starting anything, because a leftover container served old config for hours.
- Put a specific day and time on every ask from the first draft, and scan for blanks before sending.
- Wire the website to the API earlier. The site still shows $400 while the API charges $450 (R6, in the Next Wave).

## Q&A prep: likely questions

- "Why didn't you ship renters?" 
  - No rate exists, and rates are the sponsor's call. It's ready for the next wave once the rate is set.
- "The demo returned quotes all week; why does one red test matter?" 
  - The demo can look right while a number is wrong. Tests are the team member that does the math, and a red test also stops a bad change from shipping.
- "Why ship with a known CVE?" 
  - Moderate severity, not internet-exposed this week, patch next week, sponsor confirmed, and the upgrade is tracked.
- "What's still open?" 
  - Four Next Wave cards: renters, base image upgrade, website rates, and the Copilot test improvement.
