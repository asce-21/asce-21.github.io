
# Cross site scripting on Calico Labs

After running some subdomain enumeration scan on the domain **calicolabs.com** ,I found a **Calico Research** subdomain https://wi38.research.calicolabs.com/ . The application has **Genome Browser** functionality in which there is no validation of user input and an attacker can provide malicious HTML and javascript input in **set track name** paramter. The user can then create a permalink url with the saved malicious javascript and share it with other users to execute payload on their browser.

### Steps to reproduce

1 . Access the set track name feature under genome browser.

 <img src="/assets/images/calico-xss/1.png" alt="Step 1" width="600" height="331"> 

2 . Provide malicious javascript to alert domain name as input.

 <img src="/assets/images/calico-xss/2.png" alt="Step 2" width="600" height="331"> 

3 . The javascript will execute as we can see the domain name popup.

 <img src="/assets/images/calico-xss/3.png" alt="Step 3" width="600" height="331">

4 . By using create permalink functionality attacker can copy the URL with javascript saved on the current page and share it with other.

 <img src="/assets/images/calico-xss/4.png" alt="Step 4" width="600" height="331">

5 . By accessing the copied URL on another browser we can confirm the javascript will be executed successfully on other users' browser.

 <img src="/assets/images/calico-xss/5.png" alt="Step 5" width="600" height="331">


### TIMELINE

- Oct 5, 2024 : The issue reported to Google VRP.
- Oct 7, 2024 : Status updated to Triaged.
- Oct 11, 2024 : The issue identified as an Abuse Risk and triaged to Trust & Safety team.
- Oct 15, 2024 : The bug is accepted and reported to the responsible product team.
- Nov 6, 2024 : Update from Google Vulnerability Reward Program panel has decided that the security impact of this issue does not meet the bar for a financial reward.
- Dec 13, 2024 : After few follow-ups issue reopened.
- Dec 30, 2024 : Report Sent to Google VRP for reconsideration.
- Jan 17, 2025 : Google VRP decide to reward the issue.
- Jan 20, 2025 : The issue is fixed.