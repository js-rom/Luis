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

## TDD Loop (MANDATORY)

1. Create and maintain a **Test List invoking [test-cases skill](../test-cases/SKILL.md)**.
  - Before elaborating, load the artifact in progress: `Use Case Realization` for the selected scenario and other relevant artifacts.
	- List behavior scenarios and relevant variants.
	- Include regression concerns when relevant.
	- Focus on behavior, not implementation internals.
2. Pick exactly one item from the list and **write one concrete automated test**.
	- The test MUST include setup, invocation, and assertions.
	- Prefer starting from assertions and working backwards when useful.
3. **Make it pass**.
	- Change code so the new test and all previous tests pass.
	- If new scenarios are discovered, add them to Test List.
	- Mark the completed test item as done.
4. **Optionally refactor**.
	- Refactor only while all tests are green.
	- Keep behavior unchanged.
	- Optional per cycle, but MUST be done at least once at the end of the flow (when the Test List is empty).
	- For refactoring guidance, **invoke the [design-principles skill](../design-principles/SKILL.md) **.
5. Repeat from step 2 until Test List is empty.

## Interface vs Implementation Split (MANDATORY)

- During test writing, prioritize interface/behavior design.
- During make-pass, prioritize the minimal behavior change.
- During refactor, improve implementation design.
- Do not mix these concerns in the same micro-step unless strictly necessary.

## Anti-Patterns to Avoid (MUST)

- Writing all tests from the Test List before running any passing cycle.
- Writing tests without assertions only to increase coverage.
- Deleting assertions to fake green tests.
- Copying computed actual values into expected values (self-fulfilling checks).
- Refactoring while still in the red-to-green step.
- Abstracting too early; duplication is a hint, not an immediate command.
- Refactoring beyond what the current session/change requires.

## Heuristics (SHOULD)

- Choose the next test to maximize learning and reduce risk early.
- Prefer starting implementation from the class or component with lower efferent coupling (fewer outgoing dependencies) to minimize ripple effects and simplify isolated tests.
- When blocked by test order, reconsider sequencing.
- If a discovered scenario invalidates the current approach, prefer restarting from a better order over compounding complexity.
- Keep cycles short to maintain feedback speed and confidence.

## Working Protocol (Agent Behavior)

For each cycle, the agent MUST report:
- current Test List,
- selected next test and why,
- failing test evidence,
- minimal change made to pass,
- green evidence (new + existing tests),
- optional refactor summary,
- updated Test List.

The agent MUST NOT claim progress without executable test evidence.

## Output Contract (MUST)

When finishing a task, output:
- final Test List with all items status,
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

