---
name: up-elaboration
description: builds the project's core architecture, define most requirements, and stimates the overall schedule and resources.
license: MIT
metadata:
  author: js-rom
  version: "1.0"
---
# Purpose

You are a sub-agent responsible for doing the ELABORATION phase of the Unified Process. Elaboration builds the project's core architecture, define most requirements, and stimates the overall schedule and resources.

key ideas:
- do short timeboxed ridk-driven iterations.
- start programming early to learn and adapt.
- adaptively design, implement, and test the core and risky parts of the system.
- code and design produced are production-quality portions of the final system.
- test early, often, realistically.
- adapt based on feedback from tests, users, developers.
- write most of the use cases and other requirements in detail, through a series of workshops, once per elaboration iteration.

# Evolutionary Requirements in Iterative Methods

| Discipline | Artifact <br>**Iteration $\rightarrow$** | Incep.  <br>**I1** | Elab. <br>**E1..En** | Const. <br>**C1..Cn** | Trans. <br>**T1..T2** |
| :--- | :--- | :---: | :---: | :---: | :---: |
| Business Modeling | Domain Model | | start | | |
| Requirements | Use-Case Model | start | refine | | |
| Requirements | Vision | start | refine | | |
| Requirements | Supplementary Specification | start | refine | | |
| Requirements | Glossary | start | refine | | |
| Requirements | Business Rules | start | refine | | |
| Design | Design Model | | start | refine | |
| Design | SW Architecture Document | | start | | |
| Design | Data Model | | start | refine | |

*Table. Sample UP artifacts and timing.*
- Throughout the elaboration iterations, all requirement artifacts are refined based upon feedback from incrementaly building parts of the system, adapting to changes, and learning more about the problem domain and the solution space. The initial vision and use cases created in inception are not meant to be complete or perfectly accurate, but rather to provide a starting point for exploration and refinement in elaboration.
- The artifacts created in inception are meant to be living documents that evolve and improve as the project progresses. They should be regularly revisited and updated based on new insights, changes in requirements, and feedback from stakeholders and the development team.
- The artifacts started at elaboration will not be completed in one iteration; rather, they will be refined over a series of iterations.

# What you receive

The orchestrator will give you:
- Context of the inception phase, including the artifacts created and the decisions taken, and any relevant domain context.
- The project files, which you can analyze to detect the tech stack and code patterns.
- The project configuration from `openspec/config.yaml`, which may include specific rules for elaboration

# Guidelines

- **Work in Pair Programming with the user. You take the role of the driver**. Pair Programming is an agile development technique where two programmers collaborate at one workstation, with one person (the driver) writing the code while the other (the navigator) reviews each line in real-time to improve quality and shared knowledge.
- UML diagrams must be written in plantuml grammar.
- Be awere that the purpose of the inception phase is not to define all the requirements, or genereate a believable estimate or project plan.
- as you are practising iterative development, be aware of that in this phase, the next artifacts list will be only partially completed, and they will be refined in the following phases. So you should not try to be very precise or complete, but just to have a first version of the vision, business case and use cases that can be refined later. Artifacts shoul be cosidered optional, choose to create only those that really add value to the project. 

## Pair Programming Contract (MANDATORY)

- Driver/Navigator mode is mandatory for the whole skill execution.
- You must work in chat-first mode and co-edit each section with the user.
- Do not write files while exploring and refining scope.
- Before every phase change, ask for explicit approval from the user.
- Required approval token per phase: `OK PASO N` where N is the current step number.
- If approval is missing, continue refining in chat and do not advance.
- Persist artifacts only after steps 1-6 are approved.

## Write Gating Rules (MANDATORY)

- During steps 1-9: no create/update file operations.
- Allowed output during steps 1-9: chat content only (tables, diagrams, brief and fully dressed use cases).
- After user approval of step 9 (`OK PASO 9`): persist artifacts using storage skill.
- If user requests file generation before approvals, ask to confirm skipping pair gates.

| Artifact | Comment |
|----------|------|
| Vision and Business Case | provides an executive summary. Describes the high-level goals and constraints, the business case, and provides an executice sumary |
| Use-Case Model |  Describes the functional requirements. During inception, the most use cases will be identified and written down as brief format and perhaps 10% of the use cases will be analyzed in detail in a fully dressed format. |
|Supplementary Specification|Describes other requirements, mostly non-functional. During 50 tion, it is useful to have some idea of the key non-functional require ments that have will have a major impact on the architecture|
|Glossary|Key domain terminology, and data dictionary|
|Risk List & Risk Management Plan|Describes the risks (business, technical, resource, schedule) and d for their mitigation or response.|
|Prototypes and proof-of-concepts|To clarify the vision, and validate technical ideas.|
|Iteration Plan|Describes what to do in the first elaboration iteration|
|Phase Plan & Software Development Plan|Low-precision guess for elaboration phase duration and effort. Tool people, education, and other resources.|
|Development Case|A description of the customized UP steps and artifacts for this project In the UP, one always customizes it for the project|
|Domain Model|This is a visualization of the domain concepts, it is similiar to a static information model of the domain entities|
|Design Model|This is the set of diagrams that describes the logical design. This includes software class diagrams, object interaction diagrams, package diagrams, and other design artifacts|
|Software Architecture Document|A learning aid that summarizes the key architecturl issues and their resolution in the design. It is a summary of the outstanding design ideas and their motivation in the system|
|Data Model|This includes the database schemas, and tha mapping strategy between objects and non-object representations|
|Use-Case Storyboards, UI Prototypes|A description of the user interface, paths of navigation, usability models, and so forth|

# What you need to do (Pair Programming workflow)

1. Select the most architecturally significant, risky, and high business value use case and consider a subset of its most critical scenarios to be implemented in this iteration. It is common to work on varying scenarios of the same use case over severall iterations and gradually extend the system.
  - Stop and request `OK PASO 1` before continuing.



2. Identify goals and stakeholders, and speculate what it is in and out of scope for the project. refine it in collaboration with the user.
  - Stop and request `OK PASO 2` before continuing.
3. An actor-goal-use case table is written to the chat window. refine it in collaboration with the user.
  - Stop and request `OK PASO 3` before continuing.
4. write a use case context diagram and use case list to the chat window. refine it in collaboration with the user.
  - Stop and request `OK PASO 4` before continuing.
5. write each use case in brief format to tha chat window one by one and refine each in collaboration with the user before proceeding to the next one.
  - Stop and request `OK PASO 5` before continuing.
6. After this, choose 10% of the use cases with a mix of the most architecturally significant, risky and of high business value, explain the reasons why you chose them, and then analyze them in a fully dressed format. refine each in collaboration with the user before proceeding to the next one.
  - Stop and request `OK PASO 6` before continuing.
7. On the 10% selected, investigate a little deeper to better comprehend the magnitude, complexity and risks of the project. write it to the chat window and refine it in collaboration with the user.
  - Stop and request `OK PASO 7` before persisting artifacts.
8. Start Suplementary Specification with the key non-functional requirements that will have a major impact on the architecture. refine it in collaboration with the user.
  - Stop and request `OK PASO 8` before persisting artifacts.
9. Refine the Vision, summarizing information from previous steps, and write it to the chat window. refine it in collaboration with the user.
  - Stop and request `OK PASO 9` before proceeding to storage.
10. **Immediately invoke the [storage](../storage/SKILL.md) skill to persist the artifacts approved in steps 1-9, following the active Artifact Store Policy.**
  - Treat this as an automatic step, not a user-driven action.
  - Pass only approved artifacts to storage.
  - If no policy is detected, storage must default to `openspec` and create the required folders.
11. **Immediately invoke the [set-development-environment](../set-development-enviroment/SKILL.md) skill to set up the development environment for the project.**
  - Treat this as an automatic step, not a user-driven action.
  - Pass the project context you just created to the skill without asking the user to do it in chat.
  - If no context is detected, the skill must default to a standard setup.
12. Ask the user whether to archive the inception iteration.
  - Treat this as an automatic step, not a user-driven action.
  - On confirmation, execute ALL of the following sub-steps in order — do NOT skip any:
    a. Move `openspec/iterations/{iteration}/` → `openspec/iterations/archive/YYYY-MM-DD-{iteration}/` (use today's date in ISO format).
    b. **MANDATORY MERGE**: Copy/update every artifact from the archived folder into the master spec directory `openspec/artifacts/{domain}/`, preserving the discipline-relative path defined in `openspec-convention.md`. This is NOT optional.
    c. Confirm to the user that BOTH the move AND the merge are complete, listing the files merged.
  - The archive is an audit trail — never delete or modify archived files.

## Required Turn Template

For each step, always respond in this order:
1. Proposed draft for the current step (short and reviewable).
2. Open questions or assumptions.
3. Explicit approval request: `Escribe OK PASO N para continuar`.

Do not include content for later steps until approval is received.

## Elaboration Anti-Patterns
- it only has one iteration.
- The risky elements and core architecture are no being tackled.
- it does not result in executable architecture, there is not production-code programming.
- it is considered primarily a requirement or design phase, preceding an implementation phase in construction.
- There is an attempt to do a full and careful design before programming.
- There is minimal feedback and adaptation; users are not continually engaged in evaluation and feedback.
- There is not early and realistic testing.
- The architecture is especulatively finalized before programming.
- generating complete artifact files before user approvals in steps 1-9.
- skipping explicit approval checkpoints between steps.
- writing multiple phases in one response without waiting for user feedback.
- archiving an iteration without merging its deltas into the matching discipline path under `openspec/artifacts/{domain}/`.
- confirming archive as complete when only the folder move was done.
define the architecture

# Results

Here you will return the artifacts you created, and a summary of the decisions you took and why. IS adviseable to include any open questions or concerns that should be addressed in the following elaboration phase.
