# Discussion around how we measure technical risk in the Ministry of Justice.

Aim

We need a consistent approach to categorizing technical risk on our application estate. This is a test document that outlines the approach the Tech Arch community agreed to try out on the 7th March 2019.

Definition

This came about from a discussion of technical debt as per Tom Read exco presentation - “becomes outdated and risky over time” “better user interfaces cover a myriad of potential issues”

We think that the term “technical debt” is in danger of being overloaded and so we will use the term “technical risk” for this conversation.
 
TODO what does intentional neglect or pre-live services mean for the criteria.
Measures
We defined three measures, any of which can be given a red/amber/green status

People: does the application code, environments and deployment pipeline have people within the organisation who are available to write and deploy updates across the stack:
	
Criteria
Understands the context and business need for the service and has previous experience of working on the service
Has the skills necessary toand has experience of working on it
Is willing to work on it

Definition of “people”
Civil servants (including FTA)
Contractors
Managed service (for example Cap Gemini). Expectation that managed service can pick up ad-hoc and scheduled work.

Definition of “available”
Working on the application
Available to work on application from service area/agency

Scoring:
Green:
More than one civil servant
One civil servant plus more than one contractor
One civil servant plus managed service contract

	Amber:
Only 1 civil servant
Only contractors
Only a managed contract
Only 1 civil servant plus 1 contractor

	Red:
Nobody
	


Technology: can the team regularly and reliably deploy updates to the service, and is the tech generally in a good state:

Criteria:
How easy is it to deploy?
Team can deploy in working hours (High deployment frequency)
Application has automated tests (low % change failure)
Application has build promotion through test environments (low % change failure)
The team who owns the app own the complete deployment
Can deploy multiple times a day (Short lead time to deploy)
2) How risky is it to deploy and operate?
The alerts for an incident are well understood and sent to a known place
Logs are aggregated and are searchable
The application has a backup/recovery strategy
	3) How easy is it to change?
Code base can be easily changed (application architecture is well understood, can be built on dev machines)
	4) How secure is it?
The security status of the application is well understood 
What are the known risks?


	Green:
Yes to sections 1, 2, 3
Has a risk register that has been updated in the last 6 months
No high security risks, < 2 mediums.

	Amber (any of these trigger amber):
Deployment only in hours
Limited alerting or monitoring, undefined recipients of alerts
Need external actors to do deploy
Long deployments limiting frequency to <2 a day
Code base not well understood, so even if know the app a change takes multiple days
Has a risk register of some form but not updated in the last 6 months
No high security risks, 2-5 mediums.


Red (Any of these trigger red):
No automated tests
Deployments take so long they must be done over a weekend / overnight
No alerting/monitoring/log aggregation (any one of)
No backup/recovery strategy
Has no risk register of any form.
Has any known high risks.
Or 5+ mediums
	

Atrophy (does the application, its dependencies or its contracts require attention): 

Criteria
Licenses expiring
Versions of code/libraries/etc out of support
Behind on patching
Behind on security patching
Support contract expiring
Legislation changes are coming which will affect the service (eg GDPR, accessibility)
We aren’t actively preventing inevitable degradation over time

Green
No issues on any versions/contracts and application is being actively maintained to avoid degradation

Amber (Any of trigger amber):
Any of the licences/expiring in 6 months
Technologies going out of support in the next 6 months
Available patches not applied in last 6 months
Security patches available but not applied for last 3 months
Support contracts will expire in the next 9 months.
Legislation with significant impact changing in the next 6 months
Application is not being actively worked on so will degrade

Red (any of trigger):
Security patches older than 6 months not applied
Available patches not applied in last 12 months
Technologies already out of support
Legislation with significant impact changing in the next 3 months (or already past)

Appendix
Application Status
Systems can be defined as being in:

(is there a people/team component to these definitions)

Life support
This app is just being kept alive, with no patching or maintenance being applied. 

Support
This app is being actively maintained, patched, library versions are kept up to date, legislative changes applied and so on. But it is not under active development for new features.

Active
App is under active development by a service team, new features are being released.



Intentional Neglect

We know we can’t handle the risk, so letting it rot. Needs to be coupled with an active plan for replacement/retirement.


Useful to regard ATOS thinking. Won’t take on an app older than 5 years, or an app with support ending in less than 3 years.


Comments:

Given so many are public facing services, accessibility is important - these will need to be compliant with the new Public Body Accessibility Regulations by September 23rd 2020 latest 
GDPR?
