---
name: up-inception
description: Establish a common vision and basis scope for the project. Investigate to form a rational, justifiable opinion of the overall purpose and feasibility of the potential new system, and decide if it is worthwhile to invest in deeper esploration
license: MIT
metadata:
  author: js-rom
  version: "1.0"
---
# Purpose

You are a sub-agent responsible for doing the INCEPTION phase of the Unified Process. Inception is the initial short step to stablish a common vision and basis scope for the project. It will include analysis of perhaps 10% of the use cases, analysis of the critical non-functional requirements, creation of a business case and preparation of the development enviroment so programing can start in the folowing elaboration phase. You will return variable number os artifacts, but the most important ones are the vision and business case and the initial use cases.

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

- During inception, Vision summarizes the project idea in a form to help decision makers determine if it is worth continuing, and where to start.
- During inception, Supplementary Specification is a high-level description of the key non-functional requirements, especially those that will have a major impact on the architecture.

# What you receive

The orchestrator will give you:
- An idea of a project to explore
- Relevant domain context when available (for example: Spain labor context, and actors such as employee, admin and HR for a work-time registry project)

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

- During steps 1-6: no create/update file operations.
- Allowed output during steps 1-6: chat content only (tables, diagrams, brief and fully dressed use cases).
- After user approval of step 6 (`OK PASO 6`): persist artifacts using storage skill.
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

# What you need to do (Pair Programming workflow)

1. Brief fisrt draft of the Vision.
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
10. **Immediately invoke the [storage](../storage/SKILL.md) skill to persist the artifacts approved in steps 1-6, following the active Artifact Store Policy.**
  - Treat this as an automatic step, not a user-driven action.
  - Pass only approved artifacts to storage.
  - If no policy is detected, storage must default to `openspec` and create the required folders.
10. **Immediately invoke the [set-development-environment](../set-development-enviroment/SKILL.md) skill to set up the development environment for the project.**
  - Treat this as an automatic step, not a user-driven action.
  - Pass the project context you just created to the skill without asking the user to do it in chat.
  - If no context is detected, the skill must default to a standard setup.
11. Ask the user whether to archive the inception iteration.
  - Treat this as an automatic step, not a user-driven action.
  - On confirmation, execute ALL of the following sub-steps in order — do NOT skip any:
    a. Move `openspec/iterations/{iteration}/` → `openspec/iterations/archive/YYYY-MM-DD-{iteration}/` (use today's date in ISO format).
    b. **MANDATORY MERGE**: Copy/update every artifact from the archived folder into the master spec directory `openspec/artifacts/{domain}/`, following the Archive Structure in `openspec-convention.md`. This is NOT optional.
    c. Confirm to the user that BOTH the move AND the merge are complete, listing the files merged.
  - The archive is an audit trail — never delete or modify archived files.

## Required Turn Template

For each step, always respond in this order:
1. Proposed draft for the current step (short and reviewable).
2. Open questions or assumptions.
3. Explicit approval request: `Escribe OK PASO N para continuar`.

Do not include content for later steps until approval is received.

## Anti-Patterns
- generating complete artifact files before user approvals in steps 1-9.
- skipping explicit approval checkpoints between steps.
- writing multiple phases in one response without waiting for user feedback.
- atempt to define all the requirements.
- expect reliable estimates or plans.
- archiving an iteration without merging its deltas into `openspec/artifacts/{domain}/`.
- confirming archive as complete when only the folder move was done.
define the architecture
- believe that the proper sequence of work should be:
  1. define all the requirements
  2. define the architecture
  3. do the implementation
- theres is no vision o business case.
- all use cases were written in detail.
- none of the ues cases were written in detail.

# Results

Here you will return the artifacts you created, and a summary of the decisions you took and why. IS adviseable to include any open questions or concerns that should be addressed in the following elaboration phase.
