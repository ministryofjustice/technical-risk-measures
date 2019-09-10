# Criteria for measuring technical risk in the Ministry of Justice.


### Definition of Technical Risk

We are using the term _technical risk_ to talk about whether a given technology is in a healthy state.

### Origin

This came about from a discussion of technical debt as per Tom Read's exco presentation - which used definitions like: “becomes outdated and risky over time” “better user interfaces cover a myriad of potential issues”

We think that the term _technical debt_ is in danger of being overloaded and so we will use the term _technical risk_ for this conversation.


### Usage of Technical Risk Measures

This will allow us to have a way of articulating the health of a given technology to stakeholders.

The measures described in this document should allow a conversation with many layers of the organisation.

The expectation is that the terms used here become the standard by which these conversations happen, whether that's with
delivery teams or the SMT.  


### Overview

Technical risk has been divided into 3 categories:

- People: Do we have people who can iterate the system?
- Technology: Is the system in a manageable and secure state?
- Atrophy: Is the system degrading over time, due to things like expiry of support or licences, legislation changing, lack of ongoing support?

This process does **not** make assumptions about the relative importance of systems. It is not aware of business criticality or operational concerns such as data privacy / fraud / etc. All systems are treated equally. Although these technical risk measures can and should be used to inform prioritization decisions, they need to be combined with local context and data on value/scale/criticality to do that effectively. Collecting that data is outside the scope of this work - we're discussing that aspect with the product profession.


### Process

Anyone with knowledge of the systems can use this document to update the current state of the technical risk.

This should be owned at the team level if possible, by a technical architect or equivalent.

It should be updated on at least a quarterly basis - even if that is to say nothing has changed.

The criteria are a series of questions, the answers to which drive a red/amber/green status for the overall category. The google sheets we are currently using simplfy this process.

Answer the questions as they're written, even if you aren't sure how they might apply in the context of the kind of technology involved or don't think it's a risk to not meet them in your context. We want to gather accurate data across a range of services and then use that to understand where our risks are overall and how significant they are to us at various levels, as well as to refine the criteria themselves.

### Scope

All of our technology has external dependencies at some level, whether that's on SaaS/PaaS/IaaS providers, hardware manufacturers, open-source code, commercial software or suppliers (of all sizes) who build and/or support our tech under a range of commercial arrangements.

When you're using these measures on a system, **consider all its technology that exists specifically for MOJ**, regardless of commercial arrangements or who does the work on it.

That could include:

- instances of services such as a content management system or enterprise software which are hosted for MOJ
- configuration for our use of commercial services, for example SaaS or cloud providers
- our build, testing and deployment pipelines around our use of commercial services
- custom software built and managed for us by a supplier
- all software that MOJ operates, either directly or through a supplier who operates it specifically for us
- devices used by MOJ staff

Any technology which is intended for real use is in scope as soon as it exists, even if it isn't actually in real use yet, for example a service at early private beta stage.

Short-lived technology which isn't intended to be used for real, such as a prototype or proof of concept which is thrown away, is generally not in scope. However, prototypes which are hosted somewhere are in scope and should be assessed, because they require some maintenance to avoid posing a security risk over time.

### Documents

**Central Digital** [https://docs.google.com/spreadsheets/d/1pUwlFFbLJJe1P1EInJ_WWKq4aZlmzsEheSUSfFTRLXs/edit#gid=0](https://docs.google.com/spreadsheets/d/1pUwlFFbLJJe1P1EInJ_WWKq4aZlmzsEheSUSfFTRLXs/edit#gid=0)

**Justice Services** [https://docs.google.com/spreadsheets/d/1_QhfxBvxknVqvakePQJ8Efb0zGVUzX9q0cMZUryqg9U/edit?usp=drive_web&ouid=100348229431864504230](https://docs.google.com/spreadsheets/d/1_QhfxBvxknVqvakePQJ8Efb0zGVUzX9q0cMZUryqg9U/edit?usp=drive_web&ouid=100348229431864504230)


### The measures

#### People

**Description** Does the application code, environments and deployment pipeline have people within the organisation who are available to write and deploy updates across the stack?

For the purposes of this evaluation, people can be:

- Civil servants (including FTA)
- Contractors
- Managed service (for example Cap Gemini). Expectation that managed service can pick up ad-hoc and scheduled work.

To be included they however must:

- Have the skills necessary to work on it
- Understand the context and business need for the service, from previous experience of working on the service
- Are willing to work on it
- Be currently working on the application or available to pick up work on the same day


**Scoring**

Green:
- 2 or more civil servants
- 1 civil servant plus 2 or more contractors
- 1 civil servant plus managed service contract

Amber:
- 1 civil servant and 0 contractors
- 1 civil servant plus 1 contractor
- 0 civil servants and 2 or more contractors
- Only a managed service contract

Red:
- 0 civil servants and 0 contractors and no managed service contract


#### Technology

**Description** Can the service be regularly and reliably deployed, and is the tech generally in a good state?


**Criteria**

Management

- Team can deploy in working hours
- Application has automated tests
- Application has build promotion through test environments
- Team who owns the app own the complete deployment
- Can deploy multiple times a day
- Alerts for an incident are well understood and sent to a known place
- Logs are aggregated and searchable
- Application has a backup/recovery strategy
- Code base can be easily changed

Security

- Team has a good understanding of application's security
- Number of medium security risks
- Number of high security risks


**Scoring**

Green

- Green unless conditions for amber / red are met


Amber
- 2-5 (inclusive) medium security risks


Red

- more than 2 missing criteria from management section
- false response to "Team has a good understanding of application's security"
- More than 5 medium security risks
- 1 or more high security risks


#### Atrophy

**Description** Does the application, its dependencies or its contracts require attention?

Criteria
- When do licences expire?
- When will major dependencies go out of support?
- When were general dependency updates last applied?
- When were the oldest unapplied security patches released?
- When does the support contract expire?
- When do the next relevant legislation changes come into effect that are not already implemented? (GDPR/Accessibility/specific to service)
- Are we actively preventing degradation over time?

Green

- Green unless conditions for amber / red are met

Amber

- Licences expiring in next 6 months
- Major dependencies out of support in the next 6 months
- Last general updates more than 6 months ago
- Oldest unapplied security patches released more than 3 months ago
- Support contract expiring in the next 9 months
- Next legislative change coming into effect within 6 months


Red

- Licences already expired
- Major dependencies already out of support
- Last general updates more than 1 year ago
- Oldest unapplied security patches released more than 6 months ago
- Support contract already expired
- Next legislative change coming into effect within 3 months


**Intentional Neglect**

This is for when we are choosing to not work on a system, for example when we are replacing it and are focusing time/money on the replacement. This **must** be
an active choice and there **must** be a plan to retire or replace the system.
