# ADR-029: Testing Approach for Microservices

**Status**  
Accepted — 2025-11-19  

## Context

As the number of our microservice api servers grows, manual testing becomes slow and fragile. We need a consistent, lightweight testing approach that fits our existing tech stack and can be run automatically in CI.

Our services are:

- Written in: Python and Fast API
- Packaged as: Docker
- Hosted on: Cloud Run
- Code is hosted on: GitHub

We want:

- Fast feedback on breaking changes  
- Basic confidence that core flows work before deploy  
- A testing setup that is easy for all contributors to use  

## Decision

We will adopt the following minimal testing strategy:

1. **Unit Tests (Required for all services)**  
   - Use the **language-native test framework**:
     - Python: `pytest`
   - Every service will have a `/tests` (or `__tests__`) directory.
   - All new business logic must be covered by at least one unit test.
   -> This would slow down our development as we retrace our code and write pytests for all deployed api servers

2. **API/Integration Smoke Tests (Per Service)**  
   - Each service will expose a **simple health/ready endpoint** (e.g., `GET /health`).  
   - We will add a **small set of API smoke tests** that:
     - Start the service locally (via Docker or `docker-compose`)
     - Hit core endpoints (e.g., health, one “happy path” endpoint)  
   - These smoke tests are run in CI on every push to `main`.
   -> Already implemented

3. **Test Execution Rules**  
   - The `test` script in each service must:
     - Run unit tests
     - Optionally run integration/smoke tests (or provide a separate `test:integration` script)
   - CI will:
     - Run unit tests on all pushes and PRs
     - Run smoke tests at least on `main` and before deployment
   -> This would slow down our development as we retrace our code and write pytests for all deployed api servers

## Consequences

**Positive**

- Basic level of quality and regression protection as services grow.  
- Contributors use familiar tools (language-native frameworks).  
- Smoke tests give us early warning when services fail to start or core endpoints break.  

**Negative**

- Not full end-to-end coverage across all services.  
- Some manual testing will still be needed for complex flows.  
- Running smoke tests may slightly increase CI time.

## Alternatives Considered

1. **Only manual testing**  
   Rejected: doesn’t scale with more services and contributors.

2. **Full contract testing / complex E2E suite from day one**  
   Rejected for now: too heavy for our current stage and we don't have resources. We want a simple baseline first.

3. **No integration/smoke tests, only unit tests**  
   Rejected: unit tests alone don’t catch deployment/startup/config issues (i.e. SA configs)
