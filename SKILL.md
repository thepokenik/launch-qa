---
name: launch-qa
description: Audit first-time web user journeys before launch or after onboarding changes, using five simulated personas in a real browser.
---

# Launch QA

Find friction between an application's entry page and a verifiable first user success. Deliver prioritized, reproducible findings grounded in browser evidence. The five personas are simulations, not a statistical sample of real people. Respond in the user's language.

## Scope and completion

Use project context to establish the entry URL, environment, test access, and observable first-success criterion. State an inferred criterion; ask only when missing information prevents a meaningful journey. An audit is complete when all five personas have an outcome (completed, abandoned, or blocked), findings are consolidated, and coverage gaps are explicit.

An audit alone does not authorize product changes. When fixes are included in the request, continue through implementation and relevant verification without pausing for another approval of the same scope. Completion then also requires verification results for each attempted fix, including anything unresolved or blocked.

Prefer test environments and data for actions with external effects. Do not perform destructive actions or actions with external effects without authorization. If essential access or a real browser is unavailable, report the blocker; source inspection alone is not a tested journey.

## Five first-time journeys

Use a real browser and the same success criterion for every persona. Start each in an isolated session without shared cookies, storage, or authentication; use separate accounts or records when server state would affect another journey. Choose actions from what the interface reveals, without using source-code knowledge or discoveries from previous personas to bypass first-time friction.

1. **Impatient user:** skim, choose the first plausible button, and abandon at the first error.
2. **Skeptical user:** look for pricing, terms, and privacy before signing up, then attempt the goal.
3. **Mobile user:** use a 375 px viewport and slow 3G network emulation, if supported.
4. **Non-native English speaker:** interpret instructions literally without assuming knowledge the interface does not provide.
5. **Breaker:** try invalid input, back navigation, and double clicks within the test environment's limits, then attempt the goal.

Record steps, observed friction, outcome, and actual browser conditions. Link available screenshots to the relevant observation and avoid unnecessary sensitive data. Mark unsupported conditions, such as network emulation, as untested. Once a persona abandons or is blocked, later steps remain untested for that persona; any diagnostic exploration is separate evidence.

Run journeys yourself unless subagents are requested or authorized and available. Delegated journeys need the same goal and independent starting state; share findings only after their observations are recorded. Report unavailable requested capabilities, not the absence of optional delegation.

## Findings and priorities

Group observations of the same underlying problem. Each finding needs reproduction steps, expected and observed results, impact, severity, evidence, and status (**confirmed**, **suspected**, or **not reproduced**). Separate observations from inferences.

Count and name only personas that reached the relevant step and observed the problem. Include how many reached that step so untested personas are not mistaken for unaffected ones. Order by affected-persona count, then severity; prominently flag severe blockers even if only one persona encountered them. These counts describe simulated coverage, not real-user prevalence.

## Corrections when requested

With code access, fix confirmed problems within scope. Verify each fix against its original reproduction and relevant checks. Repeat affected journeys in fresh isolated sessions under the original conditions; repeat all five when changes touch the shared onboarding path, have uncertain cross-persona impact, or the user requests a full rerun. Label carried-forward results so they cannot be mistaken for fresh verification.

Report inaccessible code or unavailable retest conditions and continue independent work that remains possible. Stop at verified scoped fixes or explicit unresolved blockers; do not expand into unrelated improvements. A change is not a verified fix until subsequent observation or testing supports it.

## Deliverable

Present prioritized findings and evidence, each persona's outcome and coverage, and any fixes with their verification results. For retests, distinguish before, after, and not rerun. Include unresolved issues, limitations, and blocked or untested steps. Make the next actionable decision clear without claiming broader launch readiness than the tested scope supports.
