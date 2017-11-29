## 1) Assests

A defeinition of our assests and a thread model of our system.

#### Asserts:
- Data
```
This is our data on a MySQL server that consists of user information, comments and stories.
```
- Machines
```
This is our physical machines hosted by Digital Ocean
```
- Software
```
This is our software code that runs our service
```
- Reputation
```
This is our good reputation for having 99%<uptime
```

#### Threats:
- Illegal content
- User data gets sniffed / data theft
- To not have atleast 95% availability
- That digital ocean is going down

#### Vulnerabilities:
- Communication is not secure over HTTP protocol
- We do not restrict what content gets posted to our service
- We do not have limitations or enforce strong user passwords
- HTTP Security Header is missing
..* X-Frame-Options - Protects against Clickjacking attacks	
..* X-XSS-Protection - Mitigates Cross-Site Scripting (XSS) attacks	
..* X-Content-Type-Options - Prevents possible phishing or XSS attacks		
- No moderation of posts / no feature to report posts
- DB backup not automated
- Our code is public on GitHub
- We host our service on Digital Ocean.

## 2) Risk Matrix

| Risk No    | Risk                        | Severity | Likelyhood | Impact |
| :--------:| --------------------------- | -------- | ---------- | ----------- |
| 0 | Meteors falling down and killing everyone | Catastrophic | >Rare | Moderate |
| 1 | Data theft because of insecure communication or brute force hacking | Moderate | likely | Low |
| 2 | Someone post illegal content | Moderate | likely | Moderate |
| 3 | Someone finds vulnerabilities in our (publicly available) source code and uses it to hack our system and bring it down | Moderate | possible | Moderate |
| 4 | Digital Ocean goes down and with it our service | Catastrophic | Rare | Moderate |

## OWTF Report
Screenshots and short documentation about the penetration tests
- What tests did we run
- What were the results from the tests
- Can the attack be seen in the logs and how do they look.
