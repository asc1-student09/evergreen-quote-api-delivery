# Decision Memo: Renters coverage, not this week

> Copy to `delivery-leadership-package/decision-memo.md`. Target length: ~250 words. Write for a non-technical reader. Name the options you **rejected**, not just the one you picked.

**Date:** Tue, Nov 3, 2026
**Author:** Patricia Mengi, Delivery Lead
**Decision area:** Day 2 scope tradeoff (Inject #1)

## Context

A partner aggregator asked for renters coverage to be quotable through the API by Thursday, calling it "just one more dropdown option." Our delivery goal for this week is already set: an assembled, tested, database-backed API, shipped both ways and merged with a green build.

## Options considered

1. **Option A: Say yes, deliver renters by Thursday.** pro: the partner can start sending traffic sooner. Con: the system rejects renters quotes today, and adding it touches six parts of the product (the quote rules, the rate table, the sample data, the partner interface, and the website dropdown). Something else this week would have to come out, and we have no renters rate to charge.
2. **Option B: Say no this week, add renters in the next wave.** Pro: this week's delivery goal stays protected. Con: the partner waits.
3. **Option C: Try to fit it in if time allows.** Rejected: "maybe" gives the partner no reliable date and puts this week's goal at risk.

## Recommendation

Option B. We hold this week's scope and schedule renters for the next wave, once the sponsor confirms a renters rate.

## Why

We can't quote a price we haven't set. Renters rates are a business decision, and without one, any quote we gave customers would be a guess.

## What would change my mind

If the sponsor provides an approved renters rate by Mon, Nov 9 12 PM, I'll plan renters into the next wave right away.
