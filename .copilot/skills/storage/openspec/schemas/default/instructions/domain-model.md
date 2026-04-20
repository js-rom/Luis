# Domain Model

- The Domain Model illustratres noteworthy concepts in a domain. It can act as a source of inspiration for designing some software objects and will be an input to several artifacts.
- The Domain Model is a representation of **reasl-situation** conceptual classes, not of software objects.
- The Domain Model is a visual dictionary of the noteworthy abstractions, domain vocabulary, and information content of the domain.
- A Domain Model is no a data model. Do not exlude a class from the domain model just because it does not need to be persisted. Do not exlude a class from the domain model just because it has not attributes, it may have a purely behavioral role in the domain.


 ## Objectives
- Identify conceptual classes related to the current iteration
- Model appropiate attributes and associations
- create an intial or update the domain model

## Domain Model influece

- The domain model is influenced by use cases text. Conceptual classes - terms, concept attributes and associantions can be extracted form use cases.
- The domain objects, attributes, and associations that undergo state changes influence Operation Contracts.
- Some terms in the domain model can also influence the Glosary.
- Conceptual classes in the domain inspire the names of some software classes in the design.

## Modeling guidelines
- A domain model is illustrated with a set of class diagrams in which no operations *methods signature( are defined. It provide a conceptual perspective.)
- Similarity of naming between the domain model and the domain layer (models in software) supports a lower gap between the software representation and our mental model of the domain. Take inspiration from the realworld domain to create software classes.
- To find conceptual classes use both methods in [How to find conceptual classes](./domain-model.md#how-to-find-conceptual-classes)
- in general, showing a report of other information in a domain model is not usefull. This is a reaso to exclude it. On the other hand, if it has a special role in terms of the business rules it would be reasonable to include. For example a receipt confers to the bearer the right to return purchases.
- use existing names in the territory used by the staff of the business.
- Exclude irrelevant or out-of-scope feature for this iteration.
- Do not add things that are not there.
- Prefer model concepts as classes over attributes. Avoid representing concepts as attributes excepts when the concept is a number or a text. for example a phone number or a name.
- use description class (a class that describes information about something else, e.g., product description) when:
    - There needs to be a description about an item or service, independent of the current existence of any examples of those items or services.
    - Deleting instances of things they describe resultsresults in a loss of information that needs to be maintained, but was incorrectly associated with the deleted thing.
    - it reduces redundant or duplicated information.
- [Associations guidelines](./domain-model.md#associations)

## Domain Model antin-patterns
- models diagrams describig software classes, the domain layer of a software architecture, or software objects with responsabilities instead of real-situation objects without operations.

## Workflow (mandatory pair programming)
Bounded by he curent iteration requirements under design:
1. Find conceptual classes.
2. Draw them as classes in a UML class diagram
3. Add associations and attributes.

## How to find conceptual classes

### Use  category list
Make a list of candidate conceptual classes. The table below contains many common categories that are usually worth considering, with an emphasis on business information system needs. Examples are for a Point os Sale system, Monopoly Game and an airline reservation domain.

| Conceptual Class Category | Examples |
|---|---|
| **business transactions**<br><br>*Guideline:* These are critical (they involve money), so start with transactions. | Sale, Payment<br>Reservation |
| **transaction line items**<br><br>*Guideline:* Transactions often come with related line items, so consider these next. | SalesLineItem |
| **product or service related to a transaction or transaction line item**<br><br>*Guideline:* Transactions are for something (a product or service). Consider these next. | Item<br>Flight, Seat, Meal |
| **where is the transaction recorded?**<br><br>*Guideline:* Important. | Register, Ledger<br>FlightManifest |
| **roles of people or organizations related to the transaction; actors in the use case**<br><br>*Guideline:* We usually need to know about the parties involved in a transaction. | Cashier, Customer, Store<br>MonopolyPlayer<br>Passenger, Airline |
| **place of transaction; place of service** | Store<br>Airport, Plane, Seat |
| **noteworthy events, often with a time or place we need to remember** | Sale, Payment<br>MonopolyGame<br>Flight |
| **physical objects**<br><br>*Guideline:* This is especially relevant when creating device-control software, or simulations. | Item, Register<br>Board, Piece, Die<br>Airplane |
| **descriptions of things**<br><br>*Guideline:* See p. 147 for discussion. | ProductDescription<br>FlightDescription |
| **catalogs**<br><br>*Guideline:* Descriptions are often in a catalog. | ProductCatalog<br>FlightCatalog |
| **containers of things (physical or information)** | Store, Bin<br>Board<br>Airplane |
| **things in a container** | Item<br>Square (in a Board)<br>Passenger |
| **other collaborating systems** | CreditAuthorizationSystem<br>AirTrafficControl |
| **records of finance, work, contracts, legal matters** | Receipt, Ledger<br>MaintenanceLog |
| **financial instruments** | Cash, Check, LineOfCredit<br>TicketCredit |
| **schedules, manuals, documents that are regularly referred to in order to perform work** | DailyPriceChangeList<br>RepairSchedule |

### Use Noun phrase identification

use linguistic analysis to identify the nouns and noun phrases in textual descriptions of a domain, and cosider them as candidate conceptual classes or attributes. The fully dressed use cases are an excelent description to draw from for this analysis.

## Associations

