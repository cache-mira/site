---
title: "Workflow Automation [3/6]: Goals, Objectives & Deliverables"
layout: post
author: "Miranda Ross"
categories: Research
---
![Project’s Goals, Objectives, and Deliverables](/assets/images/automation/goals.png)

Goal 1: Improve Report Quality
==================================================================

Improving the report quality meant improving the coverage and consistency of the reports. A workflow management platform was implemented for tracking the testing and reports to check for coverage. One way coverage of the reports was balanced was to utilize standard testing frameworks, by verifying all areas of testing were being properly documented.

Objective 1.a: Implement Workflow Management
------------------------------------------------------------------

This was the initialization of the platform. This platform allowed the data to be gathered and tracked from testing to generate reports and consists of a group of Docker containers.

### Deliverable: Build and Configure Reconmap Containers.

The Docker containers containing Reconmap were pulled from their official GitHub repositories. Docker compose was used to spin up the containers. The security configurations were set from the documentation, along with a few additional layers for connecting to an insecure network. These Docker containers were locally hosted on the Windows 11 machine. When running the containers there was an application started and accessed through the browser to interact with the API, agent, and database. 

Objective 1.b: Use Standard Testing Frameworks.
------------------------------------------------------------------

Standard testing frameworks helped guide testing and balanced reports. These base frameworks were customized to remove tasks that do not apply to the current client.

### Deliverable: Create Framework Templates.

OWASP’s Web Application Security Testing Guide was used to generate project templates for thorough coverage. For example, some of the tests included Broken Access Controls, Injection, and Server-Side Request Forgery (OWASP Foundation, 2020).

Goal 2: Reduce Time to Report
==================================================================

Unorganized testing can generate documentation that is scattered and not cohesive. Time spent trying to retrace steps and having to gather evidence was reduced by using a workflow system that adds results to a database. These results were configured to be automatically translated and added to the client’s projects in an organized way for further analysis.

Objective 2.a: Automate Processes.
------------------------------------------------------------------

Security testing contains many types of reoccurring processes. The testing process was evaluated for anything that could safely be automated. Some tests remained manual and supervised, like any sort of aggressive testing that has the potential to negatively impact the client. Good candidates for automation were Open-Source Intelligence Gathering (OSINT), since it doesn’t send traffic to the client, and checking for leaked secrets and API keys. The current system had some automation already in place, although they were not integrated into a trackable workflow.

### Deliverable: Connect Script Results to Database.

One of the Docker containers built earlier was a Redis database with the results of tests mapped to the clients. Automation scripts were built to send their results to be processed by the database and were one of the quickest ways to organize the output of testing procedures. In Reconmap, these scripts were added under tools, with the parser configured to store the results in the desired format. The platform came with around a dozen scripts pre-configured as well. 

Objective 2.b: Streamline Report Writing.
------------------------------------------------------------------

Report writing can take extra time when you rewrite or copy and paste common vulnerabilities and remediations. When collaborating this problem was exaggerated by having to communicate the results between team members. The time spent writing reports was reduced by having a central platform to gather results. Security assessment report templates allowed for the first draft of a report to be automatically generated based on the testing results in the database, reducing redundancy in the writing process.

### Deliverable 2.b.i: Create Report Templates.

Reconmap came with some standard report templates to get started. For this project, the templates were customized. One template contained an overall picture of broad security assessments while the other templates were targeted reports for specific vulnerabilities. These templates contained best practices for remediation that were already acquired.

### Deliverable 2.b.ii: Convert Report to Markdown.

The output of generated reports was in LaTeX and then exported to PDF. Markdown was the format required by clients. Automatic conversion to markdown was necessary to not bottleneck report writing. This was done with Pandoc (Pandoc, n.d.). 