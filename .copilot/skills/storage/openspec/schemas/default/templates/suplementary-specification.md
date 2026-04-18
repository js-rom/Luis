# Supplementary Specification

### Revision History

| Version | Date | Description | Author |
| :--- | :--- | :--- | :--- |
| Inception draft | {{date}} | First draft. To be refined primarily during elaboration. | {{author}} |
| | | | |

---

### Introduction

This document is the repository of all **{{project-name}}** requirements not captured in the use cases.

---

### Functionality

*(Functionality common across many use cases)*

***<Cross-cutting concern 1, e.g., Logging and Error Handling>***
<Describe the system-wide functional requirement.>

***<Cross-cutting concern 2, e.g., Security>***
<Describe the system-wide functional requirement.>

***<Cross-cutting concern 3, e.g., Pluggable Rules>***
<Describe the system-wide functional requirement.>

---

### Usability

***<Human Factors sub-section>***
<Describe legibility, accessibility, color, audio/visual feedback, and the user's operational context.>

- <Usability constraint 1>
- <Usability constraint 2>

---

### Reliability

***<Recoverability sub-section>***
<Describe how the system handles failure of external services or infrastructure. Include store-and-forward, retry, or degraded-mode strategies.>

*Much more analysis is needed here...*

---

### Performance

<Describe measurable performance goals. Reference the user experience concerns from Usability when relevant.>

- <Performance goal 1, e.g., "Authorization in less than X seconds, Y% of the time.">
- <Performance goal 2>

---

### Supportability

#### Adaptability
<Describe how the system accommodates variation in business rules or processing needs across customers or deployments.>

#### Configurability
<Describe what the system allows to be configured (topology, tiers, regional settings, etc.) and why.>

*Much more analysis is needed in this area.*

---

### Implementation Constraints

<List mandated technology choices with a brief justification.>

- <Constraint 1, e.g., "Must use {{technology}} for {{reason}}.">
- <Constraint 2>

---

### Purchased Components

- <Component name>. <Brief description and any pluggability or integration requirement.>
- <Component name>. <...>

---

### Free Open Source Components

<General recommendation for FOSS usage, if applicable.>

- <FOSS candidate 1>
- <FOSS candidate 2>
- ...

---

### Interfaces

#### Noteworthy Hardware and Interfaces

- <Device 1> (<how the OS/software perceives it, e.g., as keyboard events>)
- <Device 2> (<...>)

#### Software Interfaces

<Describe external systems the application integrates with. Note any need for pluggable or adaptable interfaces.>

- <External system 1>
- <External system 2>

---

### Application-Specific Domain (Business) Rules

*(See the separate Business Rules document for general rules.)*

| ID | Rule | Changeability | Source |
| :--- | :--- | :--- | :--- |
| RULE1 | <Description of rule 1> | <Low / Medium / High> — <reason> | <Source of authority> |
| RULE2 | <Description of rule 2> | <Low / Medium / High> — <reason> | <Source of authority> |
| RULE3 | <Description of rule 3> | <Low / Medium / High> — <reason> | <Source of authority> |

---

### Legal Issues

- <Licensing restriction or compliance requirement 1>
- <Licensing restriction or compliance requirement 2>

---

### Information in Domains of Interest *(optional)*

#### <Domain Concept 1, e.g., Pricing>
<Describe the domain knowledge and its requirements implications.>

#### <Domain Concept 2, e.g., Payment Handling>
<Describe the domain knowledge and its requirements implications.>

#### <Domain Concept N>
<...>
