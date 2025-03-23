# Security

This sections contains notes on API security and other helpful information.

- [OWASP](https://owasp.org/)
- [APIsec](https://www.apisec.ai/)
- [TryHackMe](https://tryhackme.com/)

## Contents

- [OWASP Top 10 API Security Risks](#owasp-top-10-api-security-risks)
- [Disaster Recovery Plans](#disaster-recovery-plans)
- [Chaos Engineering](#chaos-engineering)
- [Common Vulnerabilities](#common-vulnerabilities)
- [Add Salt to Passwords](#add-salt-to-passwords)

## OWASP Top 10 API Security Risks

1. Broken Object Level Authorization
1. Broken Authentication
1. Broken Object Property Level Authorization
1. Unrestricted Resource Consumption
1. Broken Function Level Authorization
1. Unrestricted Access to Sensitive Business Flows
1. Server Side Request Forgery
1. Security Misconfiguration
1. Improper Inventory Management
1. Unsafe Consumption of APIs

- [OWASP Top 10 API Security Risks – 2023](https://owasp.org/API-Security/editions/2023/en/0x11-t10/)
- [2023 OWASP API Top Ten](https://www.apisec.ai/blog/2023-owasp-api-top-ten)
- [OWASP API Security Top 10 Vulnerabilities: 2023](https://apisecurity.io/owasp-api-security-top-10/)

## Disaster Recovery Plans

Many things could occur to disrupt normal operation of your software. It could range from a natural disaster, an accident or nefarious actors attempting to impact your application. When an outage occurs, it is important to know how you will react. Depending on the size and scope of the application the response can range from simply waiting if that's reasonable in your situation to deploying the application to another region. In some cases, the application will already be built to handle large server outages by being cross-region. Below are a number of links discussing important disaster recovery concepts to keep in mind.

- [Disaster recovery options in the cloud](https://docs.aws.amazon.com/whitepapers/latest/disaster-recovery-workloads-on-aws/disaster-recovery-options-in-the-cloud.html)
- [What is a Disaster Recovery Plan?](https://cloud.google.com/learn/what-is-disaster-recovery)
- [What is a disaster recovery plan (DRP)? ](https://www.ibm.com/think/topics/disaster-recovery-plan)
- [Example: Disaster recovery plan](https://www.ibm.com/docs/en/i/7.5?topic=system-example-disaster-recovery-plan)
- [Emergency Services Sector Continuity Planning Suite](https://www.cisa.gov/emergency-services-sector-continuity-planning-suite)

## Chaos Engineering

In order to test your disaster recovery preparedness teams can run "game days" to see how software and teams respond to outages. Netflix is known for developing a "chaos engineering" culture to ensure systems run smoothly in the face of adversity. Below are links covering this topic.

- [AWS Well-Architected: Game day](https://wa.aws.amazon.com/wellarchitected/2020-07-02T19-33-23/wat.concept.gameday.en.html)
- [Break Your Software, or, How to Run a Gameday](https://medium.com/@rebeccaholzschuh/break-your-software-or-how-to-run-a-gameday-b68150188bb8)
- [How To Run An Epic Game Day ~ Chaos Engineering 101](https://www.jamesfrommontana.com/running-a-game-day-chaos-engineering-101/)
- [Introduction to GameDays](https://www.gremlin.com/community/tutorials/introduction-to-gamedays)
- [Netflix Blog: Chaos Engineering Articles](https://netflixtechblog.com/tagged/chaos-engineering)
- [Chaos Monkey](https://netflix.github.io/chaosmonkey/)

## Common Vulnerabilities

There are a lot of common things we need to keep in mind when building software. In terms of security, sanitizing user input is one that comes to mind. Below is a link to OWASP cheat sheets for many different aspects of software development as well as a few highlights:

- [OWASP Cheat Sheet Series](https://cheatsheetseries.owasp.org/index.html)
- [Cross Site Scripting Prevention Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/Cross_Site_Scripting_Prevention_Cheat_Sheet.html)
- [Input Validation Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/Input_Validation_Cheat_Sheet.html)
- [OAuth 2.0 Protocol Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/OAuth2_Cheat_Sheet.html)
- [SQL Injection Prevention Cheat Sheet](https://cheatsheetseries.owasp.org/cheatsheets/SQL_Injection_Prevention_Cheat_Sheet.html)

## Add Salt to Passwords

To help increase security around passwords it can be good to add what is known as "salt" before hashing them. To do this extra characters are appended to the passwords. Doing so can make it harder for people to crack and analyze.

- [Adding Salt to Hashing: A Better Way to Store Passwords](https://auth0.com/blog/adding-salt-to-hashing-a-better-way-to-store-passwords/)
- [Password Storage Cheat Sheet - Salting](https://cheatsheetseries.owasp.org/cheatsheets/Password_Storage_Cheat_Sheet.html#salting)
- [Salt (cryptography)](https://en.wikipedia.org/wiki/Salt_(cryptography))
