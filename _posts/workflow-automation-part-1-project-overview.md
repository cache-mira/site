---
title: Workflow Automation - Part 1, Project Overview
layout: post
author: "Miranda Ross"
categories: Research
---
# Standardization of Dynamic Security Assessment Workflows with Reconmap
Security assessments come in a wide variety of forms. Depending on an organization’s needs the audits can range from physical to digital, or a black-box engagement to an automated internal audit. The wrong type of security testing can leave systems vulnerable, having the potential to cause harm to the environment they intend to protect.  Team members are responsible for communicating and documenting a broad range of ever-changing details like updating the rules of engagement, checking current network statuses, assigning project tasks, and sharing the latest test results (D. Martin, 2013).

Standard workflow management systems, like Kanban or Scrum, can fall short when applied to security assessments (Atlassian, 2021.; Scrum.org, 2022). During an active engagement, the results of one test often impact the next step making it difficult to collate the rapidly changing data into meaningful high-value reports. The ability to be flexible and change directions at a moment's notice is critical to success— but shouldn’t be at the cost of an audit’s thoroughness. For example, being able to steal cookies with a cross-site scripting (XSS) attack falls into the background if you can bypass authentication entirely via an injection. However, if a reporter gets distracted by the injection and forgets to document the XSS it can leave a client’s system vulnerable.

In this case, I needed a new documentation platform as an individual contractor who collaborates with a rotating group of team members and clients. I had a system in place that was partially automated and had some structure to keep the client’s files and documentation separated. While it met my flexibility requirements, it did not satisfy my standardization and workflow management goals. Because I had requirements from my clients to keep their information off of third-party services like OneDrive or Evernote, it ruled out most dynamic note-taking and tracking systems. I chose to implement Reconmap to address this problem. Reconmap is an open-source locally hosted pentest platform that met my flexibility, standardization, and confidentiality needs (Santiago, 2022).

Reconmap was more flexible than other offline workflow systems. The platform already integrated several common security tools by default, and it was easy to make changes. Each analyst could add custom commands and tell the platform how it should process the results. When running tests on a specific client, it processed the results and added them to the appropriate targets. These unique workflows were saved as templates to reuse and to track changes in auditing techniques.
The project was estimated to take a week for one person to implement. The objective was to have a working version of the Reconmap platform configured and ready to be used with clients. The project consisted of four phases: 
⦁	Set up Docker containers
⦁	Configure access controls
⦁	Install custom tools and workflows
⦁	Run an example assessment

# Changes to the Project Environment
The previous setup for testing and report generation consisted of many moving parts. The programs included BurpSuite, custom python scripts, CLI tools, and Sublime & Typora. The local machine hosted virtual machines and connected to a remote server.

## Operating Systems
The operating systems were accessed through the host, which was Windows 11 Home on bare metal. This machine contained multiple Ubuntu virtual machines. A remote Windows Server 2019 and Ubuntu 18.04 LTS were on GCP and accessed through VMWare Horizon. The operating systems would not be changing soon, and the project needed to be compatible with all of them.

## Current Programs
### Custom Python Scripts
The custom python scripts ingested a scope of CIDR ranges or hostnames and performed basic reconnaissance. It ran through a series of unique tests to identify virtual hosting. These scripts would output to the client’s folder. The main program integrated multiple functions already. Since I wrote them to be modular it was convenient to take the individual modules and install them into the Reconmap platform through the “tools” function.
### BurpSuite
Manual testing of web applications used BurpSuite. The suite had a passive and active scanner, but the most used function was the Repeater. The platform needed to parse the output of manual testing done with the Repeater. A new program that was a subset of BurpSuite called Dastardly was integrated as well (PortSwigger, 2022). 
### CLI Tools
Testing regularly used several command line tools, and many were in GoLang. These tools included Subfinder (ProjectDiscovery, 2022), Waybackurls, Httprobe, and Nmap. The platform needed the capability of being regularly updated since the scripts changed often.
### Text/Code Editors
Sublime and Typora were used as code and markdown editors, respectively. Sublime was the code editor for writing modules or reading source code. Typora was a markdown editor that supported images and real-time rendering. The end reports needed to be compatible with markdown. A potential issue was that Reconmap outputs the reports in LaTeX— not markdown. Pandoc was used to convert LaTeX into the necessary formats.
### File Structure
Each client had a folder with the output of testing results. The output format varied but mainly consisted of JSON, txt files, screenshots, and videos. This data was collated into a more accessible format using Reconmap.
### Containers
There were no Docker containers in the workflow. This project used Docker containers to compartmentalize the resources. Data backup and deployments were automated using Docker. 
## Networking
The network consisted of the host machine (mid to high-end laptop), several Ubuntu virtual machines, and a remote server. These machines had secure methods of networking between them. The project was going to require networking between the containers and the agent will need to access the internet to perform tests. The host machines will need to be able to connect through a VPN. 
### New Environment Overview
The new environment consisted of a Docker container network hosting the platform Reconmap. There are six containers total to house the backend, web application, authentication server, and API. A command line tool was installed on all systems used for testing that could interact with the platform and send test results back to it to be processed.
On the platform itself, templates were installed for common testing strategies, vulnerabilities, and remediation recommendations. A report template was set up to automatically generate a draft of a report containing the results and evidence from testing. My custom commands and documentation were installed onto the system to run remotely.

# Methodology
The project’s development used the Plan-Do-Check-Act (PDCA) methodology. PDCA had four steps iterated in a cycle, starting with the “Plan” phase (Lean Enterprise Institute, 2022).
## Step 1: Plan
The first step, “Plan”, was to identify problems, set goals, and plan out the steps for how to meet those goals. The problem was disorganized notetaking during security assessments caused missed vulnerabilities, and report writing to take longer. The goal was to decrease the time taken to write reports in the long term and to increase their quality.
## Step 2: Do
The second step was “Do”. The plan implementation started in this phase by building containers with Docker compose and configuring settings, including the security controls. The new system did not need to uninstall anything from the previous one, so it was able to be updated as a hot swap while the original was still being used.
## Step 3: Check
The third step of PDCA was “Check” (in some cases, it is an “S” for “Study”). This phase focused on the evaluation of the platform in the previous step by monitoring the efficiency and quality of writing reports. The quality of the audit was determined by the thoroughness of documentation and coverage of the attack surface by comparing them to previous reports.
## Step 4: Act
In the final phase, “Act”, the results were analyzed and a few changes were made to smooth out the process (Roser, 2021). There were a few steps that required manual transfer of data that slowed down the system. This process was automated, producing better results. 