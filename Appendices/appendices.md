---
layout: default
title:  "Appendices"
---

# Appendix A: Planning checklist

Use this checklist at project backlog and sprint backlog stage to assess the impact on testing, and to assure that the appropriate level of effort is being assigned

Risks of an incorrect implementation:

<center>Supporting comments</center>
[  ] Reputational

[  ] Financial

[  ] Regulatory

[  ] Integration: Does the sprint require a stub to be developed?

Considerations for estimation of test effort and definition of acceptance criteria:
 
<center>Supporting comments</center>

[  ] Complexity of the requirement(s) from a technical perspective

[  ] Supplier and SFA knowledge level of existing systems, if applicable.

[  ] Maturity of the team

[  ] Integrations between components and any dependencies.

[  ] Test Data: Complexity. Dependencies

[  ] Architectural complexity

[  ] Dependencies on other parties (e.g. for setting up of data/ infrastructure) 

[  ] Performance (Load, Stress, Volume, Soak)

[  ] Security

[  ] Cross-browser/ Mobile testing

[  ] Usability

[  ] Accessibility

[  ] Data Migration

[  ] Reporting/ Management Information/ Audit

[  ] Disaster Recovery
 
[  ] Regression


# Appendix B: Sprint 0 Checklist

|Task|Area|Complete|
|---|---|---|
|Decide on deployment method|Deployment||
|Create an auto deployment process to set up test environments after a build|Deployment||
|Decide upon the architecture of the system|Design||
|Create Domain model|Design||
|Create project glossary to aid use of ubiquitous language|Design||
|Set up tool for task management, such as TFS or Jira|Dev||
|Setup build machines and write build definitions|Dev||
|Set up automated test framework, such as Axe|Dev/Test||
|Decide on Third party framework to use, such as: Logging, Aspect Oriented Programming, Object Relational Mapper, Dependency Injection framework, Mocking framework|Dev||
|Decide on how to manage the system|Dev||
|Decide on which unit testing framework to use|Dev||
|Decide on what parts of the system should be configurable, i.e. config settings|Dev||
|Agree on location for all logging and a tool to aid viewing logs|Dev||
|Set up code review framework|Dev||
|Create stub services for integration testing|Dev||
|Determine which browsers, devices, OS are in scope for the project, and their relative priorities|Dev/Test||
|Prepare Test environment, virtual and physical.|Environment||
|Project Test approach signed off by the SFA Test Lead|Governance/ Test||
|Prepare Source control server and folder structure|Governance||
|Setup Team Wiki and/or collaborative store to share information|Governance||
|Align Product owner with product backlog|Governance||
|Identify stories to be included in sprint 1 and 2|Governance||
|Understand the team's capacity and availability|Governance||
|Ensure team have workstations set up with all tools required|Governance||
|Decide on the scrum team|Governance||
|Decide on a branching strategy|Governance||
|Decide on the Software development lifecycle Process|Governance||
|Set permissions for machines, projects|Governance||
|Agree on a coding standard for the project|Governance||
|Create the solution and all project stubs, ensuring including all references.|Governance||
|Identify user stories|Product Backlog||
|Sprint 1 planning meeting|Sprint Backlog||
|Prepare Test data|Test||
|Create test data setup scripts|Test||
|Ensure all team members are trained with sufficient skills to get started|Training||
|Develop, deploy and test a walking skeleton|All||


 # Appendix C: Browser compatibility checklist
|No.|Test|Desired Outcome|Severity|
|---|---|---|---|---|
|1.|Is the website dependent on cookies|No||||
|2.|Does JavaScript need to be enabled to view the website?|No||||
|3.|Do downloads work as expected?|Yes||||
|4.|Do form controls work as expected and tab through in the expected order?|Yes||||
|5.|Do all digital certificates and SSL URLs work correctly? Note: SSL URLs should only be available through https://|Yes||||
|6.|Does the website require any plugins to work?|No||||
|7.|Have you validated the HTML or XHTML mark-up? (See W3C mark-up validator in next section)|Yes||||
|8.|Can the size of the text be changed on the webpage?|Yes||||
|9.|Is the printed version of the page as expected?|Yes||||
|10.|Do video files work as expected?|Yes||||
|11.|Do audio files work as expected?|Yes||||
|12.|Do animations work as expected?|Yes||||
|13.|Do special characters with HTML character encoding display correctly>|Yes||||
|14.|Do hyperlinks work on the page and in the navigation work similarly in each browser? (Opens in same window, new tab, new window)|Yes||||
|15.|Is the website’s CSS valid (see CSS validation tool in next section)|Yes||||
|16.|Does the web page scroll horizontally with the following screen resolutions, when viewed at 100% 800 x 600, 1024 x 768, 1280 x 960, 1280 x 1024, 1680 x 1050|No||||
|17.|Can the page be zoomed in and out (Crtl + Mouse-Wheel)|Yes||||
|18.|Do page styles appear similar in each browser? (Text/paragraph spacing, image alignment, and table structure)|Yes||||
|19.|Are the page header and footer sections displayed as expected?|Yes||||
|20.|Do all content images have alt tags and do they display in all browsers?|Yes||||
|21.|Can the page be viewed in a text only version?|Yes||||
|22.|Can the page be viewed without styles?|Yes||||
|23.|Do all decorative images have alt tags? Decorative images, such as bullets and design-related images should have blank ``<alt>`` attributes so that text-only browsers and voice browsers ignore them.|No||||
|24.|Is the ‘favicon’ displayed in the web address field, and also in your list of favourites/bookmarks?|Yes||||

# Appendix D: Severity & Priority Classification

|Severity Level (Severity denotes the priority to the business of the defect)|Definition|
|---|---|
|S1: Critical|The defect affects critical functionality, critical data or the functioning of the entire system or results in unrecoverable data loss Or The defect would cause financial loss to the ESFA, or severe reputational damage.The defect does not have a workaround|
|S2: High|The defect affects a major part of the system which may be inaccessible or not functioning or the defect would cause a degree of reputational damage to the ESFA. The bug has no workaround, or a workaround exists which would be unacceptable to end users.|
|S3: Medium|The defect allows the user to continue with their task but they are inconvenienced. The defect has a workaround that an end user would find acceptable if appropriately advised, or the workaround is obvious to them.|
|S4: Low|The defect either does not affect functionality or data or affects it in a way that the majority of users would not notice. It either has a workaround or does not need a workaround. It does not impact productivity or efficiency. It is merely an inconvenience.| 

Priority

Priority denotes the effect on the test team and therefore how soon a fix should be delivered. The higher the priority of a defect, the more likely that entire sections of the application are not functioning or accessible, and therefore could be masking other defects. 

|Level|Definition|Deployment Time|
|---|---|---|
|P1 - Critical|Prevents all test execution, or meaningful execution of tests in an area of the system|As soon as a fix is available|
|P2 - Severe|Prevents further execution of a test script|Next available deployment. Extraordinary deployment if none scheduled|
|P3 - Medium|Testing can continue with workarounds and possible retesting required|Before the end of the sprint unless added to the backlog|
|P4 - Cosmetic|Does not prevent testing continuing|Before the end of the sprint unless added to the backlog|
