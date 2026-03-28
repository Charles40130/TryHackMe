
SOC : Security Operations Center
- keep **Detection** and **Response** intact

**Detection** :
- Detect vulnerabilities
- Detect unauthorized activity
- Detect policy violations
- Detect intrusions

**Response** :
- Support with the incident response

3 pillars of a SOC :
- People
- Process
- Technology

---
### People
- SOC team
	- SOC analyst (Level 1, 2 or 3)
		- Level 1 : first responders to any detection , basic alert triage to determine if a specific detection is harmful
		- Level 2 : While level 1 does the first-level analysis , some detection may require deeper investigation. more investigations and correlate the data from multiple data sources to perform a proper analysis
		- Level 3 :  experienced professionals who proactively look for any threat indicators and support incident response activities. Critical severity detection that need detailed responses , eradication and recovery.
	- Security Engineer : Analyse work on security solutions , these solutions need to deployment and configuration. Deploy and configure these security solutions to ensure their smooth operations.
	- Detection Engineer : Establish security rules to detect harmful activities.
	- SOC Manager :manages the processes the SOC team follows and provides support, remains in contact with the organization's CISO ( cjhief Information Securiy Officer ) to provide him with update on the SOC team's current security posture and efforts.

---
### Process
- Each role has its own Processes

#### Alert Triage
- first response to any alert is to perform the triage
- analyszing the specific alert
- determines the severity of the alert
- answering the 5 Ws
	- Who ?
	- What ?
	- Why ?
	- When ?
	- Where ?

Example :
**Alert:** Malware detected on Host: GEORGE PC

| 5 Ws   | Answers                                                                                                                                                                                                                       |
| ------ | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| What?  | A malicious file was detected on one of the hosts inside the organization’s network.                                                                                                                                          |
| When?  | The file was detected at 13:20 on June 5, 2024.                                                                                                                                                                               |
| Where? | The file was detected in the directory of the host: "GEORGE PC".                                                                                                                                                              |
| Who?   | The file was detected for the user George.                                                                                                                                                                                    |
| Why?   | After the investigation, it was found that the file was downloaded from a pirated software-selling website. The investigation with the user revealed that they downloaded the file as they wanted to use a software for free. |
#### Reporting
- alerts need to be escalated to higher-level analyst for a timely response and resolution
- escalated as tickets and assigned to the relevant people
- report should discuss all the 5Ws along with a thorough analysis, screenshots

#### Incident Response and Forensics
- Reported detection point to highly malicious activities that are critical, high-level teams initiate an incident response
- The incident response process id discussed in detail in the Incident response room, few time detailed forensics activity also need to be performed.
- forensic activity aims to determine the incident's root cause by analyzing the artifacts from a system or network
---
### Technology
- Security solutions to minimize the SOC team's manual effort to detect and response to threats.
- security solutions centralize all the information of devices,applications present in the network and aotmate the detection and response capabilities.

Security solutions :
- SIEM : Security Information and Event Management
	- popular tool used in almost every SOC environment
	- collect logs from various network devices
	- detection rules are configured
	- alerts
- EDR : Endpoint Detection and Response
	- provides the SOC team with detailed real-time and historical visibility of the devices' activites.
	- operates on the endpoint level and carry out automated responses
- Firewall : barrier between your internal and external networks ( such as the Internet)
	- monitor incoming and outgoing network traffic and filters any unauthorized traffic.
	- 