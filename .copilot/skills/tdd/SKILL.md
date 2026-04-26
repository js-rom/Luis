---
name: tdd
description: "Use when implementing changes with TDD and unit testing. Triggers: tdd, test-driven development, red green refactor, write failing test, test list, unit tests first, pruebas unitarias, desarrollo guiado por pruebas."
---

# TDD Skill

## Purpose

Apply TDD to implement behavior changes safely, keep existing behavior stable, and leave the code ready for the next change.


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
	- Build the Test List collaboratively with the user, using test-cases skill strategies:
		- factor identification,
		- equivalence classes (valid/invalid),
		- boundary value analysis,
		- combinatorial reduction (orthogonal/pairwise) when needed,
		- white-box paths only when risk justifies them.
	- Expose only the proposed next case slice (not the whole exhaustive catalog by default).
	- For each proposed slice, report rationale and trade-offs, then request explicit feedback using:
		- `Escribe OK CASOS N para continuar`.
	- Do not proceed to RED/GREEN for a case without explicit user approval.
2. Pick exactly one approved item from the list and **write one concrete automated test**.
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

## Strict Sequencing Rules (MANDATORY)

- Exactly one Test List item may be active at a time.
- Case agreement MUST happen before coding the test for that item.
- One cycle MUST be completed in this exact order: `RED -> GREEN -> REFACTOR`.
- Do NOT start the next Test List item until the current item has post-refactor GREEN evidence and is marked done.
- Do NOT batch multiple new tests in one cycle.
- Do NOT batch broad production implementation ahead of RED evidence.
- Do NOT execute RED for a new case without explicit user approval of that case.

## Interface vs Implementation Split (MANDATORY)

- During test writing, prioritize interface/behavior design.
- During make-pass, prioritize the minimal behavior change.
- During refactor, improve implementation design.
- Never implement production behavior before explicit RED evidence for the active item.
- Do not mix these concerns in the same micro-step unless strictly necessary.

## Anti-Patterns to Avoid (MUST)

- Writing all tests from the Test List before running any passing cycle.
- Selecting cases without explicit factor/equivalence/boundary reasoning.
- Ignoring combinatorial control when factors explode (pairwise/orthogonal alternatives).
- Advancing to implementation without explicit case approval from user.
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
- explicit approval request and user response,
- current Test List (or compact active+pending view),
- selected next test and why,
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
- final Test List with all items status,
- cycle-by-cycle RED -> GREEN -> REFACTOR evidence summary,
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

