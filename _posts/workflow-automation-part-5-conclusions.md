---
title: "Workflow Automation, Part 5 - Conclusions and Deliverables"
layout: post
author: "Miranda Ross"
categories: Research
---

The project was considered successful because it improved the quality and efficiency of security assessments and report writing. The scope of the Government of the Netherlands’ public coordinated vulnerability disclosure program was used to test the platform. Their scope includes all the Dutch Central Government’s systems (Nationaal Cyber Security Centrum, 2022).

The quality was judged on how balanced the report was in its coverage and documentation. Consistent evidence was needed consisting of screenshots, videos, or logs for each subcategory of tests done. Report quality improved over time, creating clearer reports with actionable steps using best practices. How the reports should be balanced depends on the client’s needs, but generally contain evaluations on access controls, input sanitation, and misconfigurations that are evenly spread across the attack surface.

While the reconnaissance was documented before the project, the active testing phase was less consistent in the evidence-gathering process. Running tests through the new “rmap” command line tool allowed active testing to be documented automatically and consistently. During subdomain enumeration, the same program (Subfinder) was used but it now automatically updates the client’s folder with the new targets. Most tests done were documented thoroughly (~90%), the remaining test parsers still need to be configured to be logged correctly. This is an improvement to 60-80% of the documentation from previous clients.

The project was also considered successful because the time spent writing a report is less than the current methods on the same type of assessment. The time to write the initial report template took longer initially, but the template was able to be reused in future reports. The initial investment in implementing Reconmap and creating the templates reduced the time spent on redundant tasks in future reports.

# Project Deliverables
Reconmap was successfully installed on the Windows host machine and an Ubuntu virtual machine. The containers were configured with security controls and the application was verified to be ready for clients. Templates were written for commonly reported vulnerabilities.

## Deliverable 1: Docker containers running Reconmap.
The platform was built with Docker running six individual containers on a Windows and a Linux host (see Appendix A). The first container is the agent. This container is used for running commands, although you can also run commands from any terminal that you authenticate to the platform within the same network. The web-client container holds the web application you use to interact with the platform, which is accessible in the browser over port 5500. The Redis server acts as a caching and message brokering service. The MySQL server is the database that holds all the documentation and results put into Reconmap. A Keycloak server authenticates the end-user to the platform. An API server is used for communication between the backend and the front end. See figure A3 in see Appendix A for a network diagram of the network and systems Reconmap was installed on. 

## Deliverable 2: Interactive application.
The Application UI was verified to be working and ready for use with clients. The Dashboard was customized to show currently assigned tasks to the user (see Appendix B). All template editing systems were verified to be functional as well. The platform was configured with commands used, and the results collector was fed into the client database.

The UI had some security settings that needed to be adjusted as well. Default passwords were updated. Cross-Origin Resource Sharing was configured to only include the local domains. The ports were remapped in Docker to only serve the platform on the loopback address so other hosts in the local network could not access it.

# Deliverable 3: Project Templates
Report templates were written from previous reports and resources from OWASP, including their testing and prevention guides (see Appendix C). The reports contain variables that are replaced automatically when they are generated. For example, the Reflected Cross-Site Scripting Report (Ross, 2022) can be used when an RXSS is found by recording it as a found vulnerability on Reconmap and clicking the “Report” button. The RXSS template is included below in markup format (see Appendix C).

These report templates have increased reporting efficiency by streamlining the process for common vulnerabilities. Remediation steps were emphasized since it was noted to be one of the most inconsistent areas in previous reports. These templates can be reused and improved over time to generate consistent high-quality reports. 

# Appendix A
Screenshots of Docker Containers
	The two different operating systems run six containers: 
⦁	Agent for running commands
⦁	Web-client you access in the browser
⦁	Redis server for message brokering
⦁	MySQL database to hold the data
⦁	Keycloak authentication system
⦁	API server to interact with the platform.
 
_Figure A1._ The Docker containers running Reconmap on Windows 11. Shown here in the Docker Desktop application. 

 
_Figure A2._ Docker containers running Reconmap on an Ubuntu Server. These services are shown here launching from the terminal with docker-compose.
Network and Application Diagrams
 
_Figure A3._ This diagram shows the network of the systems running Reconmap for this project. It was generated with a network mapper tool from Visual Paradigm (VisualParadigm, 2022). The green check marks show the systems needed to be compatible with Reconmap.

# Appendix B
_Screenshots of Reconmap_
The following are screenshots of the finished Reconmap platform after it was installed. These screenshots show the user interface of the application and its customizable features.  

_Figure B1. A screenshot of the dashboard after successful installation of the Reconmap platform._
 
_Figure B2. A screenshot of Reconmap’s templates page._
 
_Figure B3. The system architecture for the Reconmap Platform (Santiago, 2022)._ 