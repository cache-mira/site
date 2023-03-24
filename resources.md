---
layout: post
title: Resources
---

The only resource you'll need to start is [Google](https://google.com/), learn to use it [here](https://tryhackme.com/resources/blog/google-fu "TryHackMe - GoogleFu").

All of the following can be found with the above technique, nothing here is unique.
This is just a collection of some my regularly used resources and is not comprehensive.

Some of the places I look regularly for new research:

+ Synack's [Exploits Explained](https://www.synack.com/blog/) - A blog series written by the Red Team on exploits you'll see in the wild.
+ [Intigriti's Bug Bytes](https://blog.intigriti.com/category/bugbytes/) - A weekly newsletter containing new research from a variety of sources. 
+ PortSwigger Research](https://portswigger.net/research) - A collection from the staff who work on BurpSuite.
+ Reading through [current writeups](https://pentester.land/writeups/) shows you how testers are using exploits in real life scenarios.
+ Glancing at [Exploit Databases](https://www.exploit-db.com/)' latest proof of concepts to see the latest publicly available exploits. 

## Specific Exploit Resouecs

### SQL Injections

For a quick reference I use [PentestMonkey](
https://pentestmonkey.net/category/cheat-sheet/sql-injection "PenTestMonkey's SQL Injection Cheat Sheet") and [PortSwigger's](https://portswigger.net/web-security/sql-injection/cheat-sheet "PortSwigger's SQL Injection Cheat Sheet") SQL injection cheat sheets, or the SQL generic guides from [W3school](https://www.w3schools.com/sql/sql_quickref.asp). 

During active exploitation of injections that require WAF bypasses or other evasive techniques, I go directly to the documentation of the type of databases being exploited (correcting for version number). 
+ [MS Access](https://learn.microsoft.com/en-us/office/client-developer/access/desktop-database-reference/overview-of-the-access-sql-reference)
+ [MySQL](https://dev.mysql.com/doc/refman/8.0/en/dynindex-statement.html)
+ [IBM DB2](https://www.ibm.com/docs/en/db2-for-zos/11?topic=db2-sql)
+ [Oracle](https://docs.oracle.com/en/database/oracle/oracle-database/19/sqlrf/)

For exploitation I automate the process with [Python](https://www.learnpython.org/) to adjust for any unique circumstances.

