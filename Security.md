## 1) Assests

A defeinition of our assests and a thread model of our system.

#### Asserts:
- Data
- Machines
- Software
- WWW
- Reputation
#### Threats:
- Someone finds vulnerabilities in our (publicly available) source code and uses it to hack our system
- Someone post illegal content
- User data gets sniffed / data theft because of insecure communication
#### Vulnerabilities:
- Communication is not secure over HTTP protocol
- HTTP Security Header is missing
..* X-Frame-Options - Protects against Clickjacking attacks	
..* X-XSS-Protection - Mitigates Cross-Site Scripting (XSS) attacks	
..* X-Content-Type-Options - Prevents possible phishing or XSS attacks		
- No moderation of posts / no feature to report posts
- DB backup not automated
- Our code is public on GitHub
- We have control over the physical server as it's hosted on cloud services.

Threadmodel: Image!

## 2) Risk Matrix

| Risk No    | Risk                        | Severity | Likelyhood | Impact |
| :--------:| --------------------------- | -------- | ---------- | ----------- |
| 0 | Meteors falling down and killing everyone | Catastrophic | >Rare | Moderate |
| 1 | Data theft because of insecure communication | Moderate | likely | Low |
| 2 | Someone post illegal content | Moderate | likely | Moderate |
| 3 | Someone finds vulnerabilities in our (publicly available) source code and uses it to hack our system | Moderate | possible | Moderate |
| 4 | another risk | level? | how likely? | attentionlevel? |

A risk matrix.
