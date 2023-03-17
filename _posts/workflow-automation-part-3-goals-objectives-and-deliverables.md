---
title: "Workflow Automation, Part 3 - Goals, Objectives and Deliverables"
layout: post
author: "Miranda Ross"
categories: Research
---


[Project’s Goals, Objectives, and Deliverables](/assets/images/goals_table_1.png)

# Goal 1: Improve Report Quality
Improving the report quality meant improving the coverage and consistency of the reports. A workflow management platform was implemented for tracking the testing and reports to check for coverage. One way coverage of the reports was balanced was to utilize standard testing frameworks, by verifying all areas of testing were being properly documented.
## Objective 1.a: Implement Workflow Management.
This was the initialization of the platform. This platform allowed the data to be gathered and tracked from testing to generate reports and consists of a group of Docker containers.
### Deliverable: Build and Configure Reconmap Containers.
The Docker containers containing Reconmap were pulled from their official GitHub repositories. Docker compose was used to spin up the containers. The security configurations were set from the documentation, along with a few additional layers for connecting to an insecure network. These Docker containers were locally hosted on the Windows 11 machine. When running the containers there was an application started and accessed through the browser to interact with the API, agent, and database. 
## Objective 1.b: Use Standard Testing Frameworks.
Standard testing frameworks helped guide testing and balanced reports. These base frameworks were customized to remove tasks that do not apply to the current client.
### Deliverable: Create Framework Templates.
OWASP’s Web Application Security Testing Guide was used to generate project templates for thorough coverage. For example, some of the tests included Broken Access Controls, Injection, and Server-Side Request Forgery (OWASP Foundation, 2020).
# Goal 2: Reduce Time to Report
Unorganized testing can generate documentation that is scattered and not cohesive. Time spent trying to retrace steps and having to gather evidence was reduced by using a workflow system that adds results to a database. These results were configured to be automatically translated and added to the client’s projects in an organized way for further analysis. 
## Objective 2.a: Automate Processes.
Security testing contains many types of reoccurring processes. The testing process was evaluated for anything that could safely be automated. Some tests remained manual and supervised, like any sort of aggressive testing that has the potential to negatively impact the client. Good candidates for automation were Open-Source Intelligence Gathering (OSINT), since it doesn’t send traffic to the client, and checking for leaked secrets and API keys. The current system had some automation already in place, although they were not integrated into a trackable workflow.
### Deliverable: Connect Script Results to Database.
One of the Docker containers built earlier was a Redis database with the results of tests mapped to the clients. Automation scripts were built to send their results to be processed by the database and were one of the quickest ways to organize the output of testing procedures. In Reconmap, these scripts were added under tools, with the parser configured to store the results in the desired format. The platform came with around a dozen scripts pre-configured as well. 
## Objective 2.b: Streamline Report Writing.
Report writing can take extra time when you rewrite or copy and paste common vulnerabilities and remediations. When collaborating this problem was exaggerated by having to communicate the results between team members. The time spent writing reports was reduced by having a central platform to gather results. Security assessment report templates allowed for the first draft of a report to be automatically generated based on the testing results in the database, reducing redundancy in the writing process.
### Deliverable 2.b.i: Create Report Templates.
Reconmap came with some standard report templates to get started. For this project, the templates were customized. One template contained an overall picture of broad security assessments while the other templates were targeted reports for specific vulnerabilities. These templates contained best practices for remediation that were already acquired.
### Deliverable 2.b.ii: Convert Report to Markdown.
The output of generated reports was in LaTeX and then exported to PDF. Markdown was the format required by clients. Automatic conversion to markdown was necessary to not bottleneck report writing. This was done with Pandoc (Pandoc, n.d.). 

# Project Timeline with Milestones
## Table 2
_Project Timeline with planned vs. actual durations and start dates._
[insert-table]()


## Timeline Variances
The actual timeline did vary from the anticipated one (see Table 2). Building and configuring the containers was much shorter than anticipated. The Docker containers were faster than traditional servers to set up. Creating both the pentest report and the project templates was faster than expected. Connecting the scripts and converting output took about the same amount of time. Overall, the project was within the overall projected timeline, but the individual tasks varied.
Unanticipated Requirements

During the project, there were some unanticipated requirements. The security configurations recommended in the documentation for Reconmap were not adequate for my needs. Occasionally, I test insecure networks by connecting my testing machine to the internal network. Using the recommended setup, others on an internal network would be able to access the login page of the platform. While there still were authentication requirements, I didn’t want anyone to be able to access the login page in the first place. I wanted the system to drop incoming traffic to most ports, only responding to localhost.

By default, the Docker configurations mapped the containers to all interfaces, for example, “8080:8080” listening on “0.0.0.0”. Anyone could connect to the IP from an internal network and access the system. For each of the listening ports, depending on the service running they were mapped to either “127.0.0.1: XXXX:XXXX” or “host.docker.internal: XXXX: XXXX”. This restricted ports to listening on the host’s internal interfaces only, ignoring any other traffic. The Windows machine's inbound rules and the Linux machine’s iptables were updated to drop traffic not matching the desired types as well.

# Conclusions
The project was considered successful because it improved the quality and efficiency of security assessments and report writing. The scope of the Government of the Netherlands’ public coordinated vulnerability disclosure program was used to test the platform. Their scope includes all the Dutch Central Government’s systems (Nationaal Cyber Security Centrum, 2022).

The quality was judged on how balanced the report was in its coverage and documentation. Consistent evidence was needed consisting of screenshots, videos, or logs for each subcategory of tests done. Report quality improved over time, creating clearer reports with actionable steps using best practices. How the reports should be balanced depends on the client’s needs, but generally contain evaluations on access controls, input sanitation, and misconfigurations that are evenly spread across the attack surface. 

While the reconnaissance was documented before the project, the active testing phase was less consistent in the evidence-gathering process. Running tests through the new “rmap” command line tool allowed active testing to be documented automatically and consistently. During subdomain enumeration, the same program (Subfinder) was used but it now automatically updates the client’s folder with the new targets. Most tests done were documented thoroughly (~90%), the remaining test parsers still need to be configured to be logged correctly. This is an improvement to 60-80% of the documentation from previous clients.  

The project was also considered successful because the time spent writing a report is less than the current methods on the same type of assessment. The time to write the initial report template took longer initially, but the template was able to be reused in future reports. The initial investment in implementing Reconmap and creating the templates reduced the time spent on redundant tasks in future reports.
 
# Project Deliverables
Reconmap was successfully installed on the Windows host machine and an Ubuntu virtual machine. The containers were configured with security controls and the application was verified to be ready for clients. Templates were written for commonly reported vulnerabilities.

## Deliverable 1: Docker containers running Reconmap.
The platform was built with Docker running six individual containers on a Windows and a Linux host (see Appendix A). The first container is the agent. This container is used for running commands, although you can also run commands from any terminal that you authenticate to the platform within the same network. The web-client container holds the web application you use to interact with the platform, which is accessible in the browser over port 5500. The Redis server acts as a caching and message brokering service. The MySQL server is the database that holds all the documentation and results put into Reconmap. A Keycloak server authenticates the end-user to the platform. An API server is used for communication between the backend and the front end.   See figure A3 in see Appendix A for a network diagram of the network and systems Reconmap was installed on. 

## Deliverable 2: Interactive application.
The Application UI was verified to be working and ready for use with clients. The Dashboard was customized to show currently assigned tasks to the user (see Appendix B). All template editing systems were verified to be functional as well. The platform was configured with commands used, and the results collector was fed into the client database.
The UI had some security settings that needed to be adjusted as well. Default passwords were updated. Cross-Origin Resource Sharing was configured to only include the local domains. The ports were remapped in Docker to only serve the platform on the loopback address so other hosts in the local network could not access it.

## Deliverable 3: Project Templates
Report templates were written from previous reports and resources from OWASP, including their testing and prevention guides (see Appendix C). The reports contain variables that are replaced automatically when they are generated. For example, the Reflected Cross-Site Scripting Report (Ross, 2022) can be used when an RXSS is found by recording it as a found vulnerability on Reconmap and clicking the “Report” button. The RXSS template is included below in markup format (see Appendix C).

These report templates have increased reporting efficiency by streamlining the process for common vulnerabilities. Remediation steps were emphasized since it was noted to be one of the most inconsistent areas in previous reports. These templates can be reused and improved over time to generate consistent high-quality reports. 

# Appendix A
## Screenshots of Docker Containers
	The two different operating systems run six containers: 
⦁	Agent for running commands
⦁	Web-client you access in the browser
⦁	Redis server for message brokering
⦁	MySQL database to hold the data
⦁	Keycloak authentication system
⦁	API server to interact with the platform.
 
_Figure A1._ The Docker containers running Reconmap on Windows 11. Shown here in the Docker Desktop application. 
[placeholder]
 
_Figure A2._ Docker containers running Reconmap on an Ubuntu Server. These services are shown here launching from the terminal with docker-compose.
Network and Application Diagrams
[placeholder]

_Figure A3._ This diagram shows the network of the systems running Reconmap for this project. It was generated with a network mapper tool from Visual Paradigm (VisualParadigm, 2022). The green check marks show the systems needed to be compatible with Reconmap.

# Appendix B
## Screenshots of Reconmap
The following are screenshots of the finished Reconmap platform after it was installed. These screenshots show the user interface of the application and its customizable features.  
### Figure B1. A screenshot of the dashboard after successful installation of the Reconmap platform.

 
### Figure B2. A screenshot of Reconmap’s templates page.
 
### Figure B3. The system architecture for the Reconmap Platform (Santiago, 2022). 

# Appendix C
## Report Template Examples
The report templates were written to be unique and valuable to the client receiving a vulnerability report. They have variables that will automatically be replaced by the platform. The following is the Reflected Cross-Site Scripting report template.

# Reflected Cross Site Scripting - Report Template
## Metadata
----------------------------------------------------------------
- **Target codename:** {{{target-codename}}}
- **Category:** Reflected Cross-Site Scripting
- **Vulnerable Location**: {{{rxss-hostname}}}{{{rxss-path}}}
- **Vulnerable Parameter:** {{{rxss-param}}}
- **Payload:** `{{{rxss-payload}}}`
- **HTTP Request: ** `` {{{RXSS-HTTP Request}}}```
- **CWE:** CWE-79: Improper Neutralization of Input During Web Page Generation
- **CVSS:** 6.1
## Introduction/Description
----------------------------------------------------------------
A reflected cross-site scripting vulnerability was found on the {{{rxss-hostname}}} domain at the {{rxss-path}} endpoint in the {{rxss-param}} parameter.

Reflected Cross-Site Scripting (XSS) attacks are a type of injection, in which malicious scripts are injected into otherwise benign and trusted websites. XSS attacks occur when an attacker uses a web application to send malicious code, generally in the form of a browser-side script, to a different end user. Flaws that allow these attacks to succeed are quite widespread and occur anywhere a web application uses input from a user within the output it generates without validating or encoding it.

## Proof of Concept
----------------------------------------------------------------
Visit the below URL to see the domain {{{rxss-hostname}}} in a pop-up alert box. The domain name verifies the DOM is reachable through this cross-site scripting attack, allowing the attacker to access cookies.

**Link to full URL with Payload:** [{{{poc-payload}}}]({{{poc-payload}}})
**URL with payload in plain text:**
```{{{poc-payload}}}```

## Impact
----------------------------------------------------------------
An attacker can use a reflected cross-site scripting attack to steal {{{rxss-hostname}}} cookies from an authenticated user by having them click on a malicious link. Stolen cookies allow the attacker to take over the user's session. This vulnerability may also allow attackers to deface {{{rxss-hostname}}} or embed malicious content.

## Remediation
----------------------------------------------------------------
Help prevent XSS attacks by using the following best practices.
### Validate and sanitize user input
Make sure to validate and sanitize all user input to ensure that it does not contain any malicious code. This can be done using server-side input validation and sanitization functions.

### Use content security policies (CSPs).
CSPs allow you to specify which domains are allowed to load resources on your website. This can help to prevent attackers from injecting malicious code from third-party domains.

### Use an XSS prevention library.
There are several libraries available that can help to prevent XSS attacks by automatically escaping user input and implementing other security measures.

### Keep your software and libraries up to date.
Make sure to keep all software and libraries used on your website up to date to ensure that you have the latest security fixes and patches.

**Find out more from [OWASP's Cross Site Scripting Prevention Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/Cross_Site_Scripting_Prevention_Cheat_Sheet.html)**

## Severity Scores
----------------------------------------------------------------
### CWE-79: Improper Neutralization of Input During Web Page Generation 

### CVSS v3.1 Base Score: 6.1
| Metric              | Value    | Comments                                                     |
| :------------------ | :------- | :----------------------------------------------------------- |
| Attack Vector       | Network  | The attack can only be exploited over a network. The target {{{rxss-hostname}}} can be accessed over the internet. |
| Attack Complexity   | Low      | The attacker can expect repeatable success.                  |
| Privileges Required | None     | The attacker requires no privileges to perform the attack.   |
| User Interaction    | Required | A victim needs to click the malicious link created by the attacker. |
| Scope               | Changed  | The **vulnerable component** is the vulnerable {{{rxss-hostname}}} server. The **impacted component** is the victim's browser. |
| Confidentiality     | Low      | Information in the victim's browser associated with {{{rxss-hostname}}} can be read by the malicious JavaScript code and sent to the attacker. |
| Integrity           | Low      | Information in the victim's browser associated with {{{rxss-hostname}}} can be modified by the malicious JavaScript code. |
| Availability        | None     | The malicious JavaScript code cannot significantly impact the victim's browser. |

Figure C1. Reflected Cross-Site Scripting Report Template (Ross, 2022).

Not all posts need a title.

<!-- excerpt_separator -->

They sometimes just want to be left alone.