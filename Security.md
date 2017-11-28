## 1) Assests

A defeinition of our assests and a thread model of our system.

#### Asserts:
- Data
- Machines
- Software
- WWW
- Reputation
#### Threats:
- Someone finds a vulnerability in our souce code and uses it to hack our system
- Someone post illegal content
- User data can be sniffed
#### Vulnerabilities:
- Communication is not secure over HTTP protocol
- HTTP Security Header is missing
 - X-Frame-Options - Protects against Clickjacking attacks	
 - X-XSS-Protection - Mitigates Cross-Site Scripting (XSS) attacks	
 - X-Content-Type-Options - Prevents possible phishing or XSS attacks		
- No moderation of posts / no feature to report posts
- DB backup not automated
- Our code is public on GitHub
- We have control over the physical server as it's hosted on cloud services.

Threadmodel: Image!

## 2) Risk Matrix

| Risk No    | Risk                        | Severity | Likelyhood | Impact |
| :--------:| --------------------------- | -------- | ---------- | ----------- |
| 0 | Meteors falling down and killing everyone | Catastrophic | >Rare | Moderate |
| 1 | another risk | level? | how likely? | attentionlevel? |

A risk matrix.
