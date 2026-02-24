# Forms Service: CAPTCHA
This article is written for use for our tech specialists who work on the JetBrains Store and Forms Service. It covers the logic we should use to decide when a user should see a CAPTCHA or not.

## Context
We use CAPTCHA to block spam and to stop bots. However if we show it to everyone that would just annoy our customers and likely make them leave the site. So we only trigger a CAPTCHA when one of the following rules is met.

## The 5 Rules for CAPTCHA Triggering

### 1. High Frequency
If the system sees more than **500 requests** coming from the same IP address in a time frame of **under 20 minutes** it flags it automatically.

### 2. Known Blacklists
The system checks every IP against our security blacklist. If the sysyem finds out there is a matching IP adress, the user immediately gets shown a CAPTCHA.

### 3. Traffic Spikes
Our system compares traffic to the average traffic of the last 14 days at that exact hour. If the traffic is **more than double** the sysyem average it turns on CAPTCHA automatically. This is a great protections from DDoS attacks.

### 4. Repeat Data
If someone tries to send the same data **more than 5 times** in **30 seconds** it’s almost certainly not a human. The system flags this to stop bots from submissions.

### 5. Manual Admin Control
Sometimes an attack doesn't follow any of the rules. In those cases the team can go into the **Admin Panel**. Manually turn on CAPTCHA for specific requests.

## Important. Resources
* **[PLACEHOLDER]**. Request flow diagram
* **[PLACEHOLDER]**. Table of API error codes, for CAPTCHA failures.

*Drafted for intern project*
