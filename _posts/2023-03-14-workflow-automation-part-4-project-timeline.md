---
title: "Workflow Automation [4/6]:  Project Timeline & Milestones"
layout: post
author: "Miranda Ross"
categories: Research
---

__Project Timeline with planned vs. actual durations and start dates._
![Table 2](/assets/images/automation/timeline.png)

Timeline Variances
---------------------------------------------------------

The actual timeline did vary from the anticipated one (see Table 2). Building and configuring the containers was much shorter than anticipated. The Docker containers were faster than traditional servers to set up. Creating both the pentest report and the project templates was faster than expected. Connecting the scripts and converting output took about the same amount of time. Overall, the project was within the overall projected timeline, but the individual tasks varied.

Unanticipated Requirements
--------------------------------------------------------

During the project, there were some unanticipated requirements. The security configurations recommended in the documentation for Reconmap were not adequate for my needs. Occasionally, I test insecure networks by connecting my testing machine to the internal network. Using the recommended setup, others on an internal network would be able to access the login page of the platform. While there still were authentication requirements, I didn’t want anyone to be able to access the login page in the first place. I wanted the system to drop incoming traffic to most ports, only responding to localhost.

By default, the Docker configurations mapped the containers to all interfaces, for example, “8080:8080” listening on “0.0.0.0”. Anyone could connect to the IP from an internal network and access the system. For each of the listening ports, depending on the service running they were mapped to either “127.0.0.1: XXXX:XXXX” or “host.docker.internal: XXXX: XXXX”. This restricted ports to listening on the host’s internal interfaces only, ignoring any other traffic. The Windows machine's inbound rules and the Linux machine’s iptables were updated to drop traffic not matching the desired types as well.