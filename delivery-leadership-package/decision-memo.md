# Decision Memo: Renters coverage, not this week

**Date:** Tue, Nov 3, 2026  
**Author:** Patricia Mengi, Delivery Lead  
**Decision area:** Day 2 scope tradeoff (Inject #1)

## Context

A partner aggregator asked for renters coverage to be quotable through the API by Thursday, calling it "just one more dropdown option." Our delivery goal for this week is already set: an assembled, tested, database-backed API, shipped and merged with a green build.

## Options considered

1. **Option A: Say yes and deliver renters by Thursday.**
   - Pro: the partner can begin sending traffic sooner.
   - Con: renters coverage is not currently supported, and adding it touches six parts of the product: quote rules, the rate table, sample data, the partner interface, and the website dropdown. It would also force us to remove something else from this week's plan, and we do not yet have a renters rate to charge.

2. **Option B: Say no this week and add renters in the next wave.**
   - Pro: this week's delivery goal stays protected.
   - Con: the partner must wait longer.

3. **Option C: Try to fit it in if time allows.**
   - Rejected: "maybe" gives the partner no reliable date and puts this week's goal at risk.

## Recommendation

**Option B.** We hold this week's scope and schedule renters for the next wave, once the sponsor confirms a renters rate.

## Why

We cannot quote a price we have not approved. Renters rates are a business decision, and without one, any quote we provide would be a guess.

## What would change my mind

If the sponsor provides an approved renters rate by Monday, Nov 9 at 12:00 PM, I will move renters into the next wave immediately.

---

# Decision Memo: Ship on the current base image

**Date:** Tue, Nov 3, 2026  
**Author:** Patricia Mengi, Delivery Lead  
**Decision area:** Day 2 slip (Inject #1)

## Context

The platform team flagged a moderate-severity CVE on `node:22-alpine`, which is the base image used in our Dockerfile. The patched version will be available in the next scheduled upgrade window next week. We must keep containerization on track this week.

## Options considered

1. **Option A: Ship this week on `node:22-alpine` and upgrade next week.**
   - Pro: this week's delivery goal stays on track.
   - Con: we run on a flagged image for a few days.

2. **Option B: Delay the container work until the patched version lands.**
   - Pro: we avoid running on the flagged image.
   - Con: we miss this week's goal and depend on another team for timing.

## Recommendation

**Option A.** Ship this week on the current image, and upgrade as soon as the patch lands.

## Why

The risk is low this week. The CVE is moderate severity, and the API is not exposed to the internet. Holding the release would cost the full delivery for very little added safety. The sponsor confirmed this decision on Nov 4.

## What would change my mind

If the CVE were raised to high or critical, or if the API needed to be internet-exposed before the patch lands, I would delay. The upgrade is tracked in #11 and will be complete once the Dockerfile is updated and CI is green.