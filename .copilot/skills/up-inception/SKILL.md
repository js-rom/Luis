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


# What you receive

The orchestrator will give you:
- An idea of a project to explore

# What you need to do

1. Explore **in colaboration** with the user the questions bellow to stablish a common vision and scope for the project.**Propose an aswer** and ask for comfimation or editing to the user. You can ask questions as:
  - What is the vision and business case for this project?
  - Is it feasible?
  - Rough unreliable range of cost
  - Should we proceed or stop?

Be awere that the purpose of the inception phase is not to define all the requirements, or genereate a believable estimate or project plan.

2. Do just enough investigation **in colaboration** with the user to form a rational, justifiable opinion of the overall purpose and feasibility of the potential new system, and decide if it is worthwhile to invest in deeper esploration (elaboration phase purpose)

3. Create a list os non-detailed uses-cases and ask the user for comfirmation, additions or modifications. Ask the user which ones to detail, and then detail them. Ask for comfirmation or editing to the user.


4. as you are practising iterative development, be aware of that in this phase, the next artifacts list will be only partially completed, and they will be refined in the following phases. So you should not try to be very precise or complete, but just to have a first version of the vision, business case and use cases that can be refined later. Artifacts shoul be cosidered optional, choose to create only those that really add value to the project. 

| Artifact | Comment |
|----------|------|
| Vision and Business Case | provides an executive summary. Describes the high-level goals and constraints, the business case, and provides an executice sumary |
| Use-Case Model |  Describes the functional requirements. During inception, the most use cases will be identified and perhaps 10% of the use cases will be analyzed in detail. |
|Supplementary Specification|Describes other requirements, mostly non-functional. During 50 tion, it is useful to have some idea of the key non-functional require ments that have will have a major impact on the architecture|
|Glossary|Key domain terminology, and data dictionary|
|Risk List & Risk Management Plan|Describes the risks (business, technical, resource, schedule) and d for their mitigation or response.|
|Prototypes and proof-of-concepts|To clarify the vision, and validate technical ideas.|
|Iteration Plan|Describes what to do in the first elaboration iteration|
|Phase Plan & Software Development Plan|Low-precision guess for elaboration phase duration and effort. Tool people, education, and other resources.|
|Development Case|A description of the customized UP steps and artifacts for this project In the UP, one always customizes it for the project|

5. Remenber that the gratest value of modeling is understanding, rather than to document reliable specifications.

6.**Immediately invoke the [storage](../storage/SKILL.md) skill to persist the artifacts you created, following the active Artifact Store Policy.**
  - Treat this as an automatic step, not a user-driven action.
  - Pass the artifacts you just created to storage without asking the user to do it in chat.
  - If no policy is detected, storage must default to `openspec` and create the required folders.

## Anti-Patterns
- atempt to define all the requirements.
- expect reliable estimates or plans.
define the architecture
- believe that the proper sequence of work should be:
  1. define all the requirements
  2. define the architecture
  3. do the implementation
- theres is no vision o business case.
- all use cases were written in detail.
- none of the ues cases were written in detail.

# Results
Confirm that artifacts were persisted via [storage](../storage/SKILL.md), then return the artifacts you created and a summary of decisions. Include any open questions or concerns for elaboration.