# Criteria for measuring technical risk in the Ministry of Justice.


### Definition of Technical Risk

We are using the term _technical risk_ to talk about whether a given technology is in a healthy state.
 
### Origin

This came about from a discussion of technical debt as per Tom Read exco presentation - “becomes outdated and risky over time” “better user interfaces cover a myriad of potential issues”

We think that the term “technical debt” is in danger of being overloaded and so we will use the term “technical risk” for this conversation.
  

### Usage of Technical Risk Measures

This will allow us to have a way of articulating the health of a given technology to stakeholders. 

The measures described in this document should allow a conversation with many layers of the organisation.

The expectation is that the terms used here become the standard by which these conversations happen, whether thats with
delivery teams or the SMT.  


### Overview

Technical risk has been divided into 3 categories. 

- People: Do we have people who can iterate the system
- Technology: Is the system in a manageable and secure state.
- Atropy: Is the system degrading overtime, due to expiry of support or licences.

This process does *not* make assumptions about the relative importance of systems. It is not aware of business critically or operational concerns such as data privacy / fraud / etc. All systems are treated equally. Prioritization is outside of the scope of this work.


### Process

Anyone with knowledge of the systems can use this document to update the current state of the technical risk. 

This should be owned at the team level if possible. By a technical architect or equivalent. 

It should be updated on a quarterly basis - even if that is to say nothing has changed.

The criteria are a series of questions, the answers to which drive a red/amber/green status for the overall category. The google sheets we are currently using simplfy this process.

### Documents

**Central digital** [https://docs.google.com/spreadsheets/d/1pUwlFFbLJJe1P1EInJ_WWKq4aZlmzsEheSUSfFTRLXs/edit#gid=0](https://docs.google.com/spreadsheets/d/1pUwlFFbLJJe1P1EInJ_WWKq4aZlmzsEheSUSfFTRLXs/edit#gid=0)

**Justice Services** [https://docs.google.com/spreadsheets/d/1_QhfxBvxknVqvakePQJ8Efb0zGVUzX9q0cMZUryqg9U/edit?usp=drive_web&ouid=100348229431864504230](https://docs.google.com/spreadsheets/d/1_QhfxBvxknVqvakePQJ8Efb0zGVUzX9q0cMZUryqg9U/edit?usp=drive_web&ouid=100348229431864504230)


### The measures

#####People

**Description** Does the application code, environments and deployment pipeline have people within the organisation who are available to write and deploy updates across the stack?
	
For the purposes of this evaluation, people can be:

- Civil servants (including FTA)
- Contractors
- Managed service (for example Cap Gemini). Expectation that managed service can pick up ad-hoc and scheduled work.

To be included they however must:

- Understand the context and business need for the service and has previous experience of working on the service
- Have the skills necessary to and has experience of working on it
- Are willing to work on it
- Be currently working on application or available to pick up work on the same day


**Scoring**

Green:
- More than 1 civil servant
- 1 civil servant plus more than 1 contractor
- 1 civil servant plus managed service contract

Amber:
- 1 civil servant only
- 1 or less civil servants and 1 or more contractors only
- Only a managed contract

Red:
- 0 civil servants AND 0 contractors AND no managed service
	

##### Technology

**Description** Can the service be regularly and reliably deployed, and is the tech generally in a good state.


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
- Number of medium security risks >= 2 ands less than 5


Red

- more than 2 missing criteria from management section
- false response to "Team has a good understanding of application's security"
- Number of medium security risks > 5
- Number of high security risks > 1

##### Atrophy 

**Description** Does the application, its dependencies or its contracts require attention 

Criteria
- When do licences expire
- When will major dependencies go out of support
- When were general dependency updates last applied
- When were the oldest unapplied security patches released
- When does the support contract expire
- When do the next relevant legislation changes come into effect that are not already implemented (GDPR/Accessibility/specific) 
- Are we actively preventing degradation over time

Green

- Green unless conditions for amber / red are met

Amber

- Licences expiring in next 6 months
- Major dependencies out of support in the next 6 months
- Last general updates more the 6 months ago
- Oldest unapplied security patches released more than 3 months ago
- Support contract expiring in the next 9 months
- Next legislative change due within 6 months


Red

- Licences already expired
- Major dependencies already out of support
- Last general updates more the 1 year ago
- Oldest unapplied security patches released more than 6 months ago
- Support contract already expired
- Next legislative change due within 3 months


##### Appendix

**Intentional Neglect**

We know we can’t handle the risk, so letting it rot. Needs to be coupled with an active plan for replacement/retirement.



