# Stakeholder Status Update: Evergreen Quote

**To:** Fox
**From:** Patricia Mengi, Delivery Lead
**Date:** Tue, Nov 3, 2026 (Day 2, Inject #1)

## What shipped today

- Quote routes and GraphQL were wired; the test suite caught a routing defect, and the fix is in place.
- Service name and sponsor rates (auto 90 / home 135 / life 70) are configured and live.

## What slipped (and why)

- Renters coverage is not this week. The API rejects renters quotes today, and adding it touches six areas: quote rules, rate table, seed data, tests, GraphQL schema, and the site dropdown. There is no renters rate yet, and that is a sponsor decision. It has been moved to the next wave (#10).

## What’s next (tomorrow)

- Containerize on `node:22-alpine`. The CVE is moderate, the API is not internet-exposed, and the patched image lands next week. The upgrade is tracked in #11.
- Enable CI and review the site deploy.

## What I need from you

1. Confirm the ship decision on `node:22-alpine` by Wed, Nov 4, 11:00 AM.
2. Send the renters rate by Mon, Nov 9, 12:00 PM.
