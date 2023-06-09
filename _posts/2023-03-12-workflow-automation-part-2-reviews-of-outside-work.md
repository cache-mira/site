---
title: "Workflow Automation [2/6]: Research Review"
author: Miranda Ross
category: Research
layout: post
---
Work from other industry professionals was reviewed and considered while building this project. The following examples of seven pieces of work include articles, interviews, research studies, and a conference proceeding. They range from experiences of professionals to extended research studies.

Creating the Perfect Bug Bounty Automation.
------------------------------------------------------
_Hakluke: Creating the Perfect Bug Bounty Automation_ is an article by Hakluke (2021), a bug bounty hunter, that outlines setting up several automation processes for finding vulnerabilities. Their initial use of bash scripts and text files became unmanageable. The inability to cross-reference documents became problematic for Hakluke. Bug hunting needed something they could query and track effectively (Detectify Labs, 2021).

A PostgreSQL relational database with a Django front-end application created a platform capable of storing data in a meaningful way. Querying the data allowed the team to find more bugs and track how to find them; An issue with this method is the speed and scale at which they could run their platform.  Addressing speed and scaling became a priority since running multiple threads of their tools maxed out the CPU and RAM. Scaling vertically by running a more powerful server did not meet the bug hunter's needs, so they decided to try horizontal scaling (Detectify Labs, 2021). 

Horizontal scaling consists of creating low-powered worker virtual private servers (VPS) to complete tasks at the same time and report the results back to the master server. The workers pull tasks from a Redis server and store them in a job queue, costing them more than necessary. Their next step is to lower costs by scaling on demand with AWS services (Detectify Labs, 2021).

Writing a security report.
-------------------------------------------------------
In the article _Writing a Security Report Martin (2019)_, who created the Dradis Framework, walks through what security reports should contain and the common problems that arise when creating them. A helpful section is how to write for multiple audiences by structuring the report with different subsections: the executive summary, appendices, and technical details. Additionally, he brings up the topics of collation and coverage (Martin, 2013).

Collating results from different locations should be done during the testing phase, not just when writing the report. Waiting until the end of the testing process to gather evidence makes report writing take longer. Martin (2013) recommends using a collaboration tool to assist in this process. The coverage should be consistent and thorough. Failing to balance the assessment across the attack surface is a common issue. Creating a management system using a standard methodology can help guide the analyst through the testing phase (Martin, 2013).

Selection of penetration testing methodologies.
-------------------------------------------------------
This conference proceeding by Shanley and Johnstone (2015) was for the 13th Australian Information Security Management Conference. The research goal is to establish which frameworks were suitable to ensure the quality of penetration tests. The proceeding details and compares the variety of penetration testing frameworks. These evaluated organizations are ones respected in the field of security. The open-source frameworks and methodologies reviewed include the Information Systems Security Assessment Framework (ISSAF) from the Open Information Systems Security Group, the OSSTMM from the Institute for Security and Open Methodologies, and the OWASP Testing Guide (Shanley & Johnstone, 2015).

Shanley and Johnstone (2015) clarify the difference between frameworks. They ruled out several options because they were not frameworks, just named as one. Some of the remaining options lacked domain coverage. The ISSAF and OWASP’s Testing Guide provided domain coverage and met quality metrics making them “appropriate candidates to evaluate penetration testing frameworks” (Shanley & Johnstone, 2015).

Writing a Penetration Testing Report.
-------------------------------------------------------
In the white paper Writing a Penetration Testing Report, Alharbi (2010) emphasizes the importance of report writing. They include specifics of what a penetration test report should contain. Included in the white paper is an example report based on the recommended methodology. The example reports and formatting guidelines list specifics on standardizing a report's structure. Alharbi recommends logging results in a central location during information collection. The active testing phase should record all results where they are accessible to the report writer (Alharbi, 2010). 

Docker ecosystem – Vulnerability Analysis.
-------------------------------------------------------
This research study from Martin et al. (2018) was an analysis of Docker vulnerabilities. Even though this article talks about the structure in a cloud security context, it still applies to this project’s context since it needs to be compatible across a variety of networks and operating systems.  Part 4 is particularly relevant because it gives some details about Docker’s internals and architecture (pg 5-8). The daemon mentioned in part 4.3 can set iptables configurations and is remotely controllable through a UNIX socket, making protecting it a priority (Martin et al., 2018).

In part 5 Martin et al. (2018) focuses on security measures to take when using containers. The first aspect mentioned is the topic of isolation. There are several configurations at launch that can impact the isolation containers by controlling the amount of access they are granted. By default, the host is protected from the containers, but containers are not protected from each other.  Crawling Docker Hub revealed that 36% of official images contain High-Priority vulnerabilities with registered CVEs. Docker has features now to scan your images for these vulnerabilities. Developers can quickly package their entire environment, which can cause debugging tools and security keys to accidentally get pushed to production. The images themselves are necessary to audit to preserve a strong security posture (Martin et al., 2018).

Docker Security - OWASP Cheat Sheet Series.
-------------------------------------------------------
The Open Web Application Security Project (OWASP, 2017) published one of its cheat sheet series on Docker security. They give practical advice on improving the security of your containers. The first of these rules is to not expose the daemon socket used for controls. The second is to set a user when launching an image so the commands are restricted to that user’s privileges and not as root. The third and fourth rules are about limiting capabilities when running services, through the privilege’s flags. The fifth rule is to turn off inter-container communication. The sixth rule recommends using a security model like AppArmor.  Rule seven shows how to prevent some types of DoS by limiting resources like the CPU and memory. Rule eight sets the filesystems to read-only. The final three rules are to set the logs to at least info, check the images with both static analysis tools, and linting the Dockerfile at build time (OWASP, 2017).

Web Application Security Checklist.
-------------------------------------------------------
This resource by Selenius (2021) on AppSec Monkey contains a thorough walkthrough on auditing a web application. This guide can help with ensuring coverage during an assessment by acting as a reference. It also contains resources for each type of vulnerability to help with remediation that can be used during the report writing process (Selenius, 2021). 

There are several over-arching themes in this resource including browser side, server-side, and during development. Selenius says that part of defending against browser-side attacks is the sanitization of inputs (2021). Client-side, this involves generating HTML and using JavaScript safely to prevent XSS attacks. Another aspect is implementing a strong Content Security Policy, which is a header that defines where scripts can render from, as a layered prevention of XSS. The article also goes into detail on CSRF, Multi-factor authentication, and other common preventions. The server-side attack preventions also mention sanitizing user input. Other important topics covered are how to set up a WAF, the principle of least privileges, and preventing injection in parsers or databases. Incident response is also briefly covered, with more emphasis on secure development (Selenius, 2021).