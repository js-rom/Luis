# Supplementary Specification

## Purpose

Captures and identifies all requirements that are **not** expressed in the use cases. This includes non-functional requirements, quality attributes, constraints, and other system-wide concerns. It is the primary artifact for recording FURPS+ requirements in the Unified Process.

## Role in the Unified Process

The Supplementary Specification complements the use cases. While use cases capture functional, actor-goal-driven behavior, the Supplementary Specification captures:

- **Cross-cutting functional requirements** that apply to many use cases (e.g., logging, security, error handling).
- **Quality attribute requirements** (reliability, performance, usability, supportability).
- **Constraints** on implementation, components, interfaces, and legal matters.
- **Domain rules** and business rules that do not fit naturally inside a single use case.

It is produced starting in the **Inception phase** and refined throughout **Elaboration**.

## FURPS+ Model

Organize requirements using the **FURPS+** model:

- **F — Functionality:** Cross-cutting functional requirements not captured in use cases (e.g., authentication, logging, auditing, pluggable rules).
- **U — Usability:** Human factors, aesthetics, consistency, documentation needs.
- **R — Reliability:** Frequency of failure, recoverability, predictability, data integrity.
- **P — Performance:** Response time, throughput, capacity, resource usage.
- **S — Supportability:** Testability, adaptability, maintainability, configurability, internationalization.
- **+ — Extensions:**
  - **Implementation Constraints:** Programming languages, platforms, tools, standards mandated.
  - **Purchased / Third-Party Components:** External libraries, services, or packages required.
  - **Free Open Source Components:** FOSS candidates to be used.
  - **Interfaces:** Hardware devices, external software systems, and communication protocols.
  - **Application-Specific Domain (Business) Rules:** Tabulated rules with ID, description, changeability, and source.
  - **Legal Issues:** Licensing, compliance, tax, and regulatory requirements.

## Instructions for the Agent

Follow these rules when producing a Supplementary Specification:

### 1. Header and Revision History

- Title the document **Supplementary Specification**.
- Include a **Revision History** table with columns: `Version`, `Date`, `Description`, `Author`.
- Start with an inception-phase draft entry.

### 2. Introduction

- Write a short paragraph stating that this document is the repository for all system requirements **not** captured in the use cases.
- Reference the system or project by name.

### 3. Functionality

- List **cross-cutting** functional requirements: things that appear in multiple use cases or apply system-wide.
- Use named sub-sections for each concern (e.g., *Logging and Error Handling*, *Security*, *Pluggable Rules*).
- Do **not** duplicate functional behavior already described inside a specific use case.

### 4. Usability

- Describe human-factor considerations: text legibility, accessibility, color choices, feedback mechanisms (audio vs. visual).
- Mention the target user's context (e.g., speed requirements, operator attention patterns).

### 5. Reliability

- Describe recoverability strategies when external services fail.
- State availability targets or mean-time-to-recovery expectations if known.
- Flag areas that need more analysis with a note: *"Much more analysis is needed here."*

### 6. Performance

- State measurable performance goals (e.g., response time percentiles, throughput targets).
- Tie performance goals to user experience concerns identified in Usability when relevant.

### 7. Supportability

- Use sub-sections for **Adaptability** and **Configurability** at minimum.
- Describe how the system must accommodate variation across customers, deployments, or regions.
- Flag areas requiring further analysis.

### 8. Implementation Constraints

- List technology mandates (languages, frameworks, platforms) with a brief justification.
- Keep this section factual and concise.

### 9. Purchased Components

- List third-party components that must be acquired.
- Note any pluggability or integration requirements.

### 10. Free Open Source Components

- List FOSS candidates as bullet points.
- Mark them as candidates (not final decisions) unless confirmed.

### 11. Interfaces

#### Hardware and Peripheral Interfaces
- List devices the system must interact with.
- Briefly describe how the OS/software perceives each device (e.g., keyboard events, mouse events).

#### Software Interfaces
- Describe external systems the application must integrate with.
- Emphasize the need for pluggable or adaptable interfaces when multiple vendors are possible.

### 12. Application-Specific Domain (Business) Rules

- Present rules in a **table** with columns: `ID`, `Rule`, `Changeability`, `Source`.
- Assign sequential IDs (RULE1, RULE2, ...).
- Describe changeability qualitatively (Low / Medium / High) with a reason.
- State the source of authority for each rule (e.g., government regulation, retailer policy).

### 13. Legal Issues

- Cover licensing constraints for any components used.
- List mandatory regulatory compliance items (e.g., tax law, data protection).

### 14. Information in Domains of Interest *(optional)*

- Include this section when there are non-trivial domain concepts that affect requirements (e.g., pricing models, payment settlement cycles, tax complexity, item identifier schemes).
- Write one sub-section per domain concept. Keep each focused on **requirements implications**, not a full domain model.

---



---------------------------------------------------------------------------------------------------------
**Supplementary Specification**

### Revision History

| Version | Date | Description | Author |
| :--- | :--- | :--- | :--- |
| Inception draft | Jan 10, 2031 | First draft. To be refined primarily during elabora-<br>tion. | Craig Larman |
| | | | |

---------------------------------------------------------------------------------------------------------

### Introduction

This document is the repository of all NextGen POS requirements not captured in the use cases.

### Functionality

*(Functionality common across many use cases)*

***Logging and Error Handling***
Log all errors to persistent storage.

***Pluggable Rules***
At various scenario points of several use cases (to be defined) support the ability to customize the functionality of the system with a set of arbitrary rules that execute at that point or event.

***Security***
All usage requires user authentication.

### Usability

***Human Factors***
The customer will be able to see a large-monitor display of the POS. Therefore:

* Text should be easily visible from 1 meter.
* Avoid colors associated with common forms of color blindness.

Speed, ease, and error-free processing are paramount in sales processing, as the buyer wishes to leave quickly, or they perceive the purchasing experience (and seller) as less positive.

The cashier is often looking at the customer or items, not the computer display. Therefore, signals and warnings should be conveyed with sound rather than only via graphics.

### Reliability

***Recoverability***
If there is failure to use external services (payment authorizer, accounting system, ...) try to solve with a local solution (e.g., store and forward) in order to still complete a sale. Much more analysis is needed here...

### Performance

As mentioned under human factors, buyers want to complete sales processing *very* quickly. One bottleneck is external payment authorization. Our goal: authorization in less than1 minute, 90% of the time.

***

### Supportability

#### Adaptability
Different customers of the NextGen POS have unique business rule and processing needs while processing a sale. Therefore, at several defined points in the scenario (for example, when a new sale is initiated, when a new line item is added) pluggable business rule will be enabled.

#### Configurability
Different customers desire varying network configurations for their POS systems, such as thick versus thin clients, two-tier versus N-tier physical layers, and so forth. In addition, they desire the ability to modify these configurations, to reflect their changing business and performance needs. Therefore, the system will be somewhat configurable to reflect these needs. Much more analysis is needed in this area to discover the areas and degree of flexibility, and the effort to achieve it.

### Implementation Constraints

NextGen leadership insists on a Java technologies solution, predicting this will improve long-term porting and supportability, in addition to ease of development.

### Purchased Components

- Tax calculator. Must support pluggable calculators for different countries.

### Free Open Source Components

In general, we recommend maximizing the use of free Java technology open source components on this project.

Although it is premature to definitively design and choose components, we suggest the following as likely candidates:

- JLog logging framework  
- ...

### Interfaces

#### Noteworthy Hardware and Interfaces

- Touch screen monitor (this is perceived by operating systems as a regular monitor, and the touch gestures as mouse events)
- Barcode laser scanner (these normally attach to a special keyboard, and the scanned input is perceived in software as keystrokes)
- Receipt printer
- Credit/debit card reader
- Signature reader (but not in release 1)

#### Software Interfaces

For most external collaborating systems (tax calculator, accounting, inventory, ...) we need to be able to plug in varying systems and thus varying interfaces.

### Application-Specific Domain (Business) Rules

*(See the separate Business Rules document for general rules.)*

| ID    | Rule | Changeability | Source |
|-------|------|--------------|--------|
| RULE1 | Purchaser discount rules. Examples: <br> Employee—20% off. <br> Preferred Customer—10% off. <br> Senior—15% off. | High. <br> Each retailer uses different rules. | Retailer policy. |
| RULE2 | Sale (transaction-level) discount rules. <br> Applies to pre-tax total. Examples: <br> 10% off if total greater than $100 USD. <br> 5% off each Monday. <br> 10% off all sales from 10am to 3pm today. <br> Tofu 50% off from 9am–10am today. | High. <br> Each retailer uses different rules, and they may change daily or hourly. | Retailer policy. |
| RULE3 | Product (line item level) discount rules. Examples: <br> 10% off tractors this week. <br> Buy 2 veggieburgers, get 1 free. | High. <br> Each retailer uses different rules, and they may change daily or hourly. | Retailer policy. |

### Legal Issues

We recommend some open source components if their licensing restrictions can be resolved to allow resale of products that include open source software.  

All tax rules must, by law, be applied during sales. Note that these can change frequently.

### Information in Domains of Interest

#### Pricing

In addition to the pricing rules described in the domain rules section, note that products have an *original price*, and optionally a *permanent markdown price*. A product’s price (before further discounts) is the permanent markdown price, if present. Organizations maintain the original price even if there is a permanent markdown price, for accounting and tax reasons.

#### Credit and Debit Payment Handling

When an electronic credit or debit payment is approved by a payment authorization service, they are responsible for paying the seller, not the buyer. Consequently, for each payment, the seller needs to record monies owing in their accounts receivable, from the authorization service. Usually on a nightly basis, the authorization service will perform an electronic funds transfer to the seller’s account for the daily total owing, less a (small) per transaction fee that the service charges.

#### Sales Tax

Sales tax calculations can be very complex, and regularly change in response to legislation at all levels of government. Therefore, delegating tax calculations to third-party calculator software (of which there are several available) is advisable. Tax may be owing to city, region, state, and national bodies. Some items may be tax exempt without qualification, or exempt depending on the buyer or target recipient (for example, a farmer or a child).

#### Item Identifiers: UPCs, EANs, SKUs, Bar Codes, and Bar Code Readers

The NextGen POS needs to support various item identifier schemes. UPCs (Universal Product Codes), EANs (European Article Numbering) and SKUs (Stock Keeping Units) are three common identifier systems for products that are sold. Japanese Article Numbers (JANs) are a kind of EAN version. SKUs are completely arbitrary identifiers defined by the retailer.