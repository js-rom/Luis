# Purpose

the essence of architectural analysis is to identify factors that should influece the architecture, understand their variability and priority, and resolve them. You should ask the right questions to elicit architectural factors and choose skillful means to resolve the factors wheighing the trade-offs and rationale.

# Motivation
- reduce the risk of missing something centrally important in the design of the system.
- avoid applying excesive effort to low priority issues.
- help align the product with business goals.

# input artifacts
- Vision
- Use Case Model
- Supplementary Specification

# Points of change in a software system
- variation point: Variations in the existing current system or requirements, such as multiple tax calculator interfaces that must be supported.
- Evolution point: Speculative points of variation that may arise ub the future, but which are not present in the existing requirements.

variation points and evolution points are recurring key elements in architectural analysis, and they should be identified, documented, and resolved with appropriate design decisions.

# Typical architectural questions to consider

Architectural analysus is concerned with the identification and resolution of the system's non-functional requirements and quality attributes, in the context of the functional requirements. Some typical questions to consider include:
- how do reliability and fault tolerance requirements influence the architecture?
- How do licensing costs of purshased subcomponents affet profitability?
- how do the adaptability and configurabilitu requirements affect the design?
- how soes brand name and branding affect the architecture?

# Common steps in architectural analysis

1. identify and analyze the non-functional requirements and functional requirements in term of variability or change that have an impact on the architecture. these are the architectural factors or drivers.
2. Make architectural decisions forthose requiremtns with a significat architectural impact, analyze alternativs and create solutions that resolve the impact.

# Identification and analysis of architectural factors

- Architectural factors:
  - any and all of the FURPS+ requirements may have a significan influece on the architecture of the system, ranging from reliability, to schedule, to skills and to cost contraints. However, categories of functionality, reliability, performace, suportability, implementation and interface have the strongest architectural ingfluence.
- Quality scenarios (term promoted by the SEI):
  - are a useful tool to identify and analyze architectural factors. They consist of a stimulus, a response, and a measure of success. For example, a quality scenario for reliability might be: "When the system receives an invalid input, it should return an error message within 1 second 99% of the time in a production environment under "average" load conditions."
  - "average" load conditions should be defined in terms of the expected number of concurrent users, transactions per second, or other relevant metrics. A quality scenario is not really valid until it is testeable.
- Pick your battles:
  - select only really critical make-or-breake queality scenarios to the succes of the system.
- Describing factors:
  - create a factor table  that describe factors, measurs ans queality scenarios, variability, impact of factor on stakeholders and other factors, priority for success, and Difficulty or risk. group architectural factors into FURPS+ categories to help ensure a comprehensive analysis.
- Factors and UP artifacts:
  - Use cases, Vision, and suplementary Specification are important source of inspration when creating a factor table. In the use cases, the Special Requirements, Technology Variations, and Open Open Issues should be reviwed, and their implied or explicit architectural factors consolifated in the Suplementary Specification.

# Resolution of architectural factors

- The art of architecture is making skillful choices to resolvethis factors, in light of trade-offs, interdependecies, and priorities.
- Adept architects have knowledge in a variety of areas, for example architecrual styles and patterns, technologies, products, pitfalls, and trends, and apply this to their decisions.

## Recording architectural alternatives, decisions, and motivation:
- keep a recor of alternative solutions, decisions, influential factors, and motivations for the noteworthy issues and decisions. This is called a Technical Memo.
- Technical memos are recorded at Sofware Architecture Document.
- An important aspect of the technical memo is the motivation or rationale.
- explain also the rationale of rejecting the alternatives.
- an architectural decision described in a technical memo may resolve a group of factors, not only one.
- Priorities, there is a hierarchy of goals that guides architectural decisions:
  1. Inflexible constraints, including safety and legal compliance.
  2. Business goals, including profitability, market impact, and competitive advantage.
  3. All other indirect business goals

## Priorities and evolution points: under and over-engineering
- Avoid over-engineering by not addressing low-priority evolution points with significant effort.
- Avoid under-engineering by not neglecting high-priority evolution points that could lead to significant future costs or risks.
- Use architectural analysis to identify and prioritize evolution points, and make informed decisions about which ones to address in the current architecture.
- apply basic architectural principles such as low coupling, high cohrdion, protected variation (interfaces, indirection, service lookup, etc)
- apply separation of concerns and localization of impact. use techniques like 
  - Modularize the concern into a separate compoent or module.
  - USe decorators or interceptors to add behavior without modifying existing code.
  - Use aspect-oriented programming (AOP) techniques to separate cross-cutting concerns.
- explore architectural styles and patterns that are known to address the identified factors effectively, such as microservices for scalability and adaptability, or layered architecture for separation of concerns.

# Outputs
- Architectural factor tables
- Technical memos that record architectural decisions.
