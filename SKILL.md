---
name: launch-qa
description: Evaluate first-time web user journeys before launch using five simulated personas in a real browser. Capture and prioritize friction, and fix and retest issues when requested.
---

# Launch QA

Evaluate the path from an application's entry page to a verifiable first user success. Respond in the user's language unless instructed otherwise. Treat the five personas as simulations, not a statistical sample of real people.

## Prepare

Inspect the project and its instructions to determine how to run or access the application, its environment and entry URL, and an observable first-success criterion. Identify available test accounts, data, browser capabilities, and delegation tools. Infer what you can; ask only for information necessary to proceed that cannot be obtained from the project or environment. Prefer test environments and test data for actions with external effects, and stay within the authorized scope. If a real browser or essential access is unavailable, report the blocker instead of claiming a journey was tested.

Determine whether the request includes fixes. An audit alone does not authorize product changes.

## Run five journeys

Use a real browser. Start each persona in an isolated session without shared cookies, storage, or authentication state, and attempt the same first-success criterion. Use separate test accounts or records where needed to prevent one journey from changing another's starting state. Observe and record steps, outcomes, confusion and blockers, available screenshots, and whether the journey was completed, abandoned, or blocked. Avoid unnecessary sensitive data in captures and reports.

1. **Impatient user:** skim, choose the first plausible button, and abandon at the first error.
2. **Skeptical user:** look for pricing, terms, and privacy before signing up, then attempt the goal.
3. **Mobile user:** use a 375 px viewport and slow 3G network emulation, if supported.
4. **Non-native English speaker:** interpret instructions literally without assuming knowledge the interface does not provide.
5. **Breaker:** try invalid input, back navigation, and double clicks within the test environment's limits, then attempt the goal.

Record actual browser and environment conditions. If a condition cannot be reproduced, such as slow 3G, explicitly record the limitation and do not claim it was tested. If a persona stops or is blocked, do not infer what would have happened on later steps. Save or link available screenshots with enough context to associate them with the relevant observation.

When the user requests or authorizes subagents and the environment permits, assign one journey per subagent, respecting any requested model and reasoning level when available. Run batches if concurrency is limited. Otherwise conduct separate journeys yourself and report the delegation limitation. Report only delegation and model settings actually used.

## Consolidate

Group observations of the same underlying problem. For each item record:

- Number and names of affected personas, counting only those that reached the relevant step and observed the issue.
- Reproduction steps, observed and expected results, impact, severity, and evidence or screenshot links.
- Status: **confirmed**, **suspected**, or **not reproduced**, with any uncertainty or relevant conditions.

Order by the number of affected simulated personas, using severity as the tie-breaker. Highlight severe blockers even when only one persona encountered them. Distinguish direct observations from inferences and do not imply that persona counts represent real-user prevalence.

## Fix and retest when requested

If fixes are requested and code is accessible, fix confirmed problems within scope and run checks appropriate to the changes. Then repeat all five journeys in fresh isolated sessions under the original conditions, and verify each fix specifically. Record new problems, remaining issues, and blockers. Do not claim a fix is verified without subsequent observation or testing; report any inability to repeat a condition or journey. If fixes are not requested or code is inaccessible, report findings and any limitation without changing the product.

## Report

Deliver the consolidated, prioritized issues and available evidence, corrections and their verification results, and each persona's outcome before and, if retested, after changes. Include limitations, unresolved items, and blocked or untested steps. Make clear what was actually observed and tested.
