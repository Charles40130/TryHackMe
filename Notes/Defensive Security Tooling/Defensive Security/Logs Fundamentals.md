
- Logs contain traces of a lot of things

| Log Type         | Usage                                                                                                                                                                                            | Example                                                                                                                                                |
| ---------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------ |
| System Logs      | The system logs can be helpful in troubleshooting running issues in the OS. These logs provide information on various operating system activities.                                               | - System Startup and shutdown events  <br>- Driver Loading events  <br>- System Error events  <br>- Hardware events                                    |
| Security Logs    | The security logs help detect and investigate incidents. These logs provide information on the security-related activities in the system.                                                        | -Authentication events  <br>- Authorization events  <br>- Security Policy changes events  <br>- User Account changes events - Abnormal Activity events |
| Application Logs | The application logs contain specific events related to the application. Any interactive or non-interactive activity happening inside the application will be logged here.                       | - User Interaction events  <br>- Application Changes events  <br>- Application Update events  <br>- Application Error events                           |
| Audit Logs       | The Audit logs provide detailed information on the system changes and user events. These logs are helpful for compliance requirements and can play a vital role in security monitoring as well.  | - Data Access events  <br>- System Change events  <br>- User Activity events  <br>- Policy Enforcement events                                          |
| Network Logs     | Network logs provide information on the network’s outgoing and incoming traffic. They play crucial roles in troubleshooting network issues and can also be handy during incident investigations. | - Incoming Network Traffic events  <br>- Outgoing Network Traffic events  <br>- Network Connection Logs - Network Firewall Logs                        |
| Access Logs      | The Access logs provide detailed information about the access to different resources. These resources can be of different types, providing us with information on their access.                  | - Webserver Access Logs  <br>- Database Access Logs - Application Access Logs  <br>- API Access Logs                                                   |


---
### Windows Event Logs Analysos

Event Viewer : logs stored in Windows Operating System in 3 types:
- Application
- System
- Security


Logs are like this :
- **Description:** This field has a detailed information of the activity.
- **Log Name:** The Log Name indicates the log file name.
- **Logged:** This field indicates the time of the activity.
- **Event ID:** Event IDs are unique identifiers for a specific activity.