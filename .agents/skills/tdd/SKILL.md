---
name: tdd
description: "Use when implementing changes with TDD and unit testing. Triggers: tdd, test-driven development, red green refactor, write failing test, test list, unit tests first, pruebas unitarias, desarrollo guiado por pruebas."
---

# TDD Skill

## Purpose

Apply TDD to implement behavior changes safely, keep existing behavior stable, and leave the code ready for the next change.
This skill controls cycle sequencing; test design and test-quality criteria MUST be applied invoking [unit-testing skill](../unit-testing/SKILL.md).


## Scope

Use this skill for:
- new behavior development,
- bug fixes,
- incremental refactors protected by tests,
- unit testing in red-green-refactor cycles.

Do not use this skill as a rule to write all tests upfront.

## Code Language Rule (MANDATORY)

- All production code and test code created or modified during TDD cycles MUST be written in English.
- This includes class, method, variable, and test names, plus inline code comments and assertion messages.
- If existing code uses another language, normalize touched code to English unless the user explicitly requests otherwise.

## TDD Loop (MANDATORY)

1. Create and maintain a **Test List invoking [test-cases skill](../test-cases/SKILL.md)**.
  - Before elaborating, load the artifact in progress: `Use Case Realization` for the selected scenario and other relevant artifacts.
	- Build the Test List collaboratively with the user one by one, using test-cases skill strategies:
		- factor identification,
		- equivalence classes (valid/invalid),
		- boundary value analysis,
		- combinatorial reduction (orthogonal/pairwise) when needed,
		- white-box paths only when risk justifies them.
	- After the Test List and its rationale are agreed, ask the user explicitly:
		- `Do you want implementation one by one with prior user approval, or automatically without per-case approval?`
	- Then ask the user to choose execution mode:
		- `Guided mode`: implement one case at a time with explicit user approval before RED.
		- `Automatic mode`: implement the agreed list end-to-end **one case at a time** without per-case approval.
		- In `Automatic mode`, no per-case approval is required, but strict sequencing is still mandatory: one active case, one RED, one GREEN, one REFACTOR, then next case.
	- Record the selected mode before starting RED/GREEN cycles.
	- If the user does not choose explicitly, default to `Guided mode`.
	- After closing Step 1, persist `Test plan.md` using the storage skill and active Artifact Store Policy.
	- Persist it under: `openspec/artifacts/{domain}/05 Test/{{#}} {Iteration} Test plan.md`.
	- Build the artifact from the active schema template `test-plan.md`.
2. Pick exactly one item from the list and **write one concrete automated test**.
	- In `Guided mode`, the selected item MUST be explicitly approved by the user.
	- In `Automatic mode`, the selected item MUST come from the previously agreed Test List.
	- For test design/quality decisions, **invoke [unit-testing skill](../unit-testing/SKILL.md)**.
	- The test MUST include setup, invocation, and assertions.
	- The test code MUST be written in English.
	- Prefer starting from assertions and working backwards when useful.
3. **RED (mandatory): run the new test and capture failing evidence before any production code change**.
	- The cycle MUST stop if no failing evidence is produced.
	- Do NOT write production code for this item before RED evidence exists.
4. **GREEN (mandatory): make only the minimal change to pass**.
	- Change code so the new test and all previous tests pass.
	- Production code changes in this step MUST be written in English.
	- Capture executable GREEN evidence.
5. **REFACTOR (mandatory decision every cycle)**.
	- Refactor only while all tests are green.
	- Keep behavior unchanged.
	- If no refactor is needed, explicitly record `No refactor in this cycle` with rationale.
	- After refactor (or no-op), re-run relevant tests and capture post-refactor GREEN evidence.
	- For refactoring guidance, **invoke the [design-principles skill](../design-principles/SKILL.md) **.
6. Mark the completed test item as done.
	- If new scenarios are discovered, add them to Test List (as new pending items).
7. Repeat from step 2 until Test List is empty.

## TDD + Unit Testing Integration (MANDATORY)

- For every active Test List item, apply the quality model from [unit-testing skill](../unit-testing/SKILL.md): automated, self-verifying, repeatable, independent, and fast.
- Before closing each cycle, detect and fix relevant test anti-patterns defined in [unit-testing skill](../unit-testing/SKILL.md).
- Keep this skill focused on sequencing (`RED -> GREEN -> REFACTOR`) and use unit-testing skill as the design-quality gate for tests.
- If a required check needs real DB/network/process coupling, classify it as non-unit and track it outside this unit-level TDD loop.

## Strict Sequencing Rules (MANDATORY)

- Exactly one Test List item may be active at a time.
- Case agreement MUST happen before coding the test for that item.
- One cycle MUST be completed in this exact order: `RED -> GREEN -> REFACTOR`.
- Do NOT start the next Test List item until the current item has post-refactor GREEN evidence and is marked done.
- Do NOT batch multiple new tests in one cycle.
- Do NOT run RED for multiple pending items before completing GREEN for the active item.
- Do NOT batch broad production implementation ahead of RED evidence.
- In `Guided mode`, do NOT execute RED for a new case without explicit user approval of that case.
- In `Automatic mode`, do NOT execute RED for cases outside the previously agreed Test List.
- In `Automatic mode`, process the Test List as a strict loop: select next agreed item, complete full `RED -> GREEN -> REFACTOR`, mark done, then continue.

## Interface vs Implementation Split (MANDATORY)

- During test writing, prioritize interface/behavior design.
- During make-pass, prioritize the minimal behavior change.
- During refactor, improve implementation design.
- Never implement production behavior before explicit RED evidence for the active item.
- Do not mix these concerns in the same micro-step unless strictly necessary.

## Anti-Patterns to Avoid (MUST)

- Writing all tests from the Test List before running any passing cycle.
- Running RED for several Test List items before finishing GREEN for the first one.
- Selecting cases without explicit factor/equivalence/boundary reasoning.
- Ignoring combinatorial control when factors explode (pairwise/orthogonal alternatives).
- Advancing to implementation without respecting the selected approval policy:
	- `Guided mode`: explicit per-case user approval.
	- `Automatic mode`: prior user consensus of the complete Test List and rationale.
- Implementing production code before obtaining RED evidence for the active test.
- Moving to the next Test List item without finishing post-refactor GREEN for the current item.
- Merging multiple Test List items into one combined RED/GREEN step.
- Writing tests without assertions only to increase coverage.
- Deleting assertions to fake green tests.
- Copying computed actual values into expected values (self-fulfilling checks).
- Refactoring while still in the red-to-green step.
- Abstracting too early; duplication is a hint, not an immediate command.
- Refactoring beyond what the current session/change requires.

## Heuristics (SHOULD)

- Choose the next test to maximize learning and reduce risk early.
- Prioritize cases that cover new equivalence classes, critical boundaries, or high-risk factor interactions.
- Prefer starting implementation from the class or component with lower efferent coupling (fewer outgoing dependencies) to minimize ripple effects and simplify isolated tests.
- When blocked by test order, reconsider sequencing.
- If a discovered scenario invalidates the current approach, prefer restarting from a better order over compounding complexity.
- Keep cycles short to maintain feedback speed and confidence.

## Working Protocol (Agent Behavior)

For each cycle, the agent MUST report:
- proposed case slice derived from factors/equivalence classes/boundaries,
- rationale for selecting that slice now,
- selected execution mode (`Guided mode` or `Automatic mode`) and confirmation source,
- in `Guided mode`, explicit approval request and user response for the active case,
- current Test List (or compact active+pending view),
- selected next test and why,
- unit-testing quality gate status for the active test (execute/maintain/readability + anti-pattern check),
- failing test evidence (RED) captured before production code changes,
- minimal change made to pass,
- green evidence (new + existing tests),
- refactor summary or explicit no-op refactor rationale,
- post-refactor green evidence,
- updated Test List.

The agent MUST NOT claim progress without executable test evidence.

## Output Contract (MUST)

When finishing a task, output:
- case-selection summary based on test-cases skill (factors, equivalence classes, boundaries, and reduction strategy),
- execution mode used (`Guided mode` or `Automatic mode`) and how approvals were handled,
- final Test List with all items status,
- cycle-by-cycle RED -> GREEN -> REFACTOR evidence summary,
- summary of how [unit-testing skill](../unit-testing/SKILL.md) criteria were applied (quality model + anti-pattern findings/fixes),
- list of tests added/updated,
- list of production code changes linked to test items,
- confirmation that full relevant suite is green,
- concise note on refactors performed and why,
- follow-up risks or pending scenarios (if any).

## Completion Criteria

- Test List is empty (or explicitly deferred items are justified).
- New behavior works.
- Previously working behavior still works.
- Code remains ready for the next change.

