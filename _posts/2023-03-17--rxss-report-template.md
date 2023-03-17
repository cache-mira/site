---
title: "Report Template - RXSS"
layout: post
author: "Miranda Ross"
categories: Research
---


========================
The report templates were written to be unique and valuable to the client receiving a vulnerability report. They have variables that will automatically be replaced by the platform. The following is the Reflected Cross-Site Scripting report template.

_See the full template in raw markdown on [GitHub](/report_templates/reflected-cross-site-scripting.md).

Reflected Cross Site Scripting 
---------------------------------------------

***Metadata***
----------------------------------------------------------------
- **Target codename:** \[target-codename\]
- **Category:** Reflected Cross-Site Scripting
- **Vulnerable Location**: \[rxss-hostname\]\[rxss-path\]
- **Vulnerable Parameter:** \[rxss-param\]
- **Payload:** \[rxss-payload\]
- **HTTP Request: ** \[RXSS-HTTP Request\]
- **CWE:** CWE-79: Improper Neutralization of Input During Web Page Generation
- **CVSS:** 6.1

***Introduction/Description***
----------------------------------------------------------------

A reflected cross-site scripting vulnerability was found on the \[rxss-hostname\] domain at the \[rxss-path\] endpoint in the \[rxss-param\] parameter.

Reflected Cross-Site Scripting (XSS) attacks are a type of injection, in which malicious scripts are injected into otherwise benign and trusted websites. XSS attacks occur when an attacker uses a web application to send malicious code, generally in the form of a browser-side script, to a different end user. Flaws that allow these attacks to succeed are quite widespread and occur anywhere a web application uses input from a user within the output it generates without validating or encoding it.

***Proof of Concept***
----------------------------------------------------------------

Visit the below URL to see the domain \[rxss-hostname\] in a pop-up alert box. The domain name verifies the DOM is reachable through this cross-site scripting attack, allowing the attacker to access cookies.

**Link to full URL with Payload:** [\[poc-payload\]](\[poc-payload\])
**URL with payload in plain text:**
> \[poc-payload\]

***Impact***
----------------------------------------------------------------

An attacker can use a reflected cross-site scripting attack to steal \[rxss-hostname\] cookies from an authenticated user by having them click on a malicious link. Stolen cookies allow the attacker to take over the user's session. This vulnerability may also allow attackers to deface \[rxss-hostname\] or embed malicious content.

***Remediation***
----------------------------------------------------------------

Help prevent XSS attacks by using the following best practices.

__Validate and sanitize user input__
> Make sure to validate and sanitize all user input to ensure that it does not contain any malicious code. This can be done using server-side input validation and sanitization functions.

__Use content security policies (CSPs).__
> CSPs allow you to specify which domains are allowed to load resources on your website. This can help to prevent attackers from injecting malicious code from third-party domains.

__Use an XSS prevention library.__
>There are several libraries available that can help to prevent XSS attacks by automatically escaping user input and implementing other security measures.

__Keep your software and libraries up to date.__
> Make sure to keep all software and libraries used on your website up to date to ensure that you have the latest security fixes and patches.

**Find out more from [OWASP's Cross Site Scripting Prevention Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/Cross_Site_Scripting_Prevention_Cheat_Sheet.html)**

***Severity Scores***
----------------------------------------------------------------
__\[CWE-79\]: Improper Neutralization of Input During Web Page Generation__\\
__CVSS v3.1 Base Score: \[6.1\]__\\

| Metric              | Value    | Comments                                                     |
|:--------------------|:---------|:-------------------------------------------------------------|
|---
| Attack Vector       | Network  | The attack can only be exploited over a network. The target \[rxss-hostname\] can be accessed over the internet. |
|---
| Attack Complexity   | Low      | The attacker can expect repeatable success.                  |
|---
| Privileges Required | None     | The attacker requires no privileges to perform the attack.   |
|---
| User Interaction    | Required | A victim needs to click the malicious link created by the attacker. |
|---
| Scope               | Changed  | The **vulnerable component** is the vulnerable \[rxss-hostname\] server. The **impacted component** is the victim's browser. |
|---
| Confidentiality     | Low      | Information in the victim's browser associated with \[rxss-hostname\] can be read by the malicious JavaScript code and sent to the attacker. |
|---
| Integrity           | Low      | Information in the victim's browser associated with \[rxss-hostname\] can be modified by the malicious JavaScript code. |
|---
| Availability        | None     | The malicious JavaScript code cannot significantly impact the victim's browser. 
{: rules="groups"}



* * *
_Figure C1._ Reflected Cross-Site Scripting Report Template (Ross, 2022).