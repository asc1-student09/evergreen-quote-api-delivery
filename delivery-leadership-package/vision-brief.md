# Evergreen Quote: Vision Brief


## Product
**Name:** Evergreen Quote API (Phase 3 service delivery)
**Delivery week:** 3
**Delivery Lead:** Patricia Mengi
**Engineering team (represented by):** https://github.com/asc1-student09/evergreen-quote-api-delivery
**GitHub Project board:** https://github.com/users/asc1-student09/projects/4

## Who is the customer?
The Evergreen Quote API serves three customers:
 1. The website team, which calls REST routes to create and retrieve insurance quotes. 
 2. A partner-integration pilot, which uses GraphQL to request only the quote data it needs. 
 3. The operations team, which needs the service to be tested in a CI pipeline, packaged as a container, and runnable on the company's Kubernetes platform. 

## What pain does Evergreen Quote remove?
1. Website team: Without a back end, quote data wasn't saved. It stayed on the page and was erased every time a new entry was made. The website needs reliable quote routes it can depend on.
2. Partner-integration pilot: With REST alone, the partner would need multiple calls and would receive extra data it doesn't need. GraphQL lets the partner request just the fields it needs, which makes the integration more flexible.
3. Operations team: Without automated tests, a container, and Kubernetes readiness, operations faces bugs that reach production, services that behave differently on each server, and manual, error-prone deployments that are hard to scale or restart.

## What does "good" look like at end of the week?
By Friday:
    1. Website team can create and retrieve quotes through REST routes, and the data is saved in MongoDB with validation that rejects bad input.
    2. Partner-integration pilot can use GraphQL to request just the quote fields it needs.
    3. Operations team has a service that passes its tests in a CI pipeline, runs as container, and has been demonstrated on a local Kubernetes cluster, ready for the company's platform.
    4. All work is merged to main through a pull request with green CI.

## What are we explicitly NOT doing this week?
1. Not writing code from scratch. The team assembles provided, pre-built (routes, GraphQL layer, container recipe, CI workflow, and cluster manifests).
2. Not deploying to the company's production Kubernetes platform. This week's demo runs on a local cluster.
3. Not fixing the 5 npm audit vulnerabilities. Dependencies are pinned; the findings are logged in the risk register for later review.
4. Not adding user login or authentication
5. Not building or redesigning the website front end. We use the provided site. 


## How will we know if it worked?
1. Website (REST): All 6 seeded quotes can be retrieved through the REST API, and 100% of invalid quote requests are rejected with 400 error. 
2. Partner (GraphQL): A GraphQL query returns all 6 quotes with only the fields requested.
3. Operations: The CI pipeline shows 100% of tests passing (0 failures) on the pull request, the PR is merged to main, and the container runs on the local Kubernetes cluster with its pod showing Running and the service answering with a 200 status.


