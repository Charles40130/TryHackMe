
- SIEM : Security Information and Event Management system
	- analyse use in security operations center

---
1. Host-Centric Log Sources
	- log sources capture events that occurred within or related to the host.
2. Network-Centric Log Sources
	- Network-related logs are generated when the hosts communicate with each other or access the internet to visit a website.
---
- Centralized Log Collection
- Normalization of Logs
- Correlation of Logs
- Real-time Alerting
- Dashboards and Reporting


---
#### Log Sources and Ingestion

- Windows Machine
	- Event Viewer

- Linux Machine
	- - /var/log/httpd: Contains HTTP Request  / Response and error logs.
	- /var/log/cron: Events related to cron jobs are stored in this location.
	- /var/log/auth.log and /var/log/secure: Stores authentication-related logs.
	- /var/log/kern: This file stores kernel-related events.

- Web Server
	- /var/log/apache or /var/log/httpd.

---
#### Alerting Process and Analysis

Example of detections rules:
- If a user gets five failed Login Attempts in 10 seconds, raise an alert for `Multiple Failed Login Attempts`
- If login is successful after multiple failed login attempts, raise an alert for `Successful Login After multiple Login Attempts`
- A rule is set to alert every time a user plugs in a USB (Useful if USB is restricted as per the company policy)
- If outbound traffic is > 25 MB, raise an alert to potential data exfiltration Attempt (Usually, it depends on the company policy)

How is a dection rule created ?

- Use-case 1
	- Adversaries tend to remove the logs during the post-exploitation phase to remove their tracks. A unique Event ID **104** is logged every time a user tries to remove or clear event logs. To create a rule based on this activity, we can set the condition as follows:

	 **Rule:** If the Log source is WinEventLog **AND** EventID is **104** - Trigger an alert `Event Log Cleared`
-  Use-Case 2:

	Adversaries use commands like `whoami` after the exploitation/privilege escalation phase. The following Fields will be helpful to include in the rule.

	- Log source: Identify the log source capturing the event logs
	- Event ID: Which Event ID is associated with Process Execution activity? In this case, Event ID 4688 will be helpful.
	- NewProcessName: Which process name will be helpful to include in the rule?

Alert Investigation
Some of the actions that are performed after the analysis are:

- Alert is a False Positive. It may require tuning the rule to avoid similar False positives from occurring again.
- Alert is a True Positive. Perform further investigation.
- Contact the asset owner to inquire about the activity.
- Suspicious activity is confirmed. Isolate the infected host.
- Block the suspicious IP.