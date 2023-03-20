---
layout: post
title: Resources
---

The only resource you'll need to start is [Google](https://google.com/), learn to use it [here](https://tryhackme.com/resources/blog/google-fu "TryHackMe - GoogleFu").

All of the following can be found with the above technique, nothing here is unique.
This is just a collection of some my regularly used resources and is not comprehensive.

### SQL Injections
For a quick reference I use [PentestMonkey](
https://pentestmonkey.net/category/cheat-sheet/sql-injection "PenTestMonkey's SQL Injection Cheat Sheet") and [PortSwigger's](https://portswigger.net/web-security/sql-injection/cheat-sheet "PortSwigger's SQL Injection Cheat Sheet") SQL injection cheat sheets, or the SQL generic guides from [W3school](https://www.w3schools.com/sql/sql_quickref.asp). 

During active exploitation of injections that require WAF bypasses or other evasive techniques, I go directly to the documentation of the type of databases being exploited (correcting for version number). 
+ [MS Access](https://learn.microsoft.com/en-us/office/client-developer/access/desktop-database-reference/overview-of-the-access-sql-reference)
+ [MySQL](https://dev.mysql.com/doc/refman/8.0/en/dynindex-statement.html)
+ [IBM DB2](https://www.ibm.com/docs/en/db2-for-zos/11?topic=db2-sql)
+ [Oracle](https://docs.oracle.com/en/database/oracle/oracle-database/19/sqlrf/)

For exploitation I automate the process with [Python](https://www.learnpython.org/) to adjust for any unique circumstances.

