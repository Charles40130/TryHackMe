
Intrusion Detection System (IDS)
- plays the role of surveillance camera inside the building
- notifies the security administrators about a malicious activity
- 

---
#### Types of IDS

Deployment modes:
- **Host Intrusion Detection System ( HIDS )** : installed individually on the hosts and responsible for only detecting potential security threats associated with that particular host
- **Network Intrusion Detection System (NIDS)** : Network-based IDS solutions are crucial in detecting potentially malicious activities within the whole network, regardless of any specific hosts.

<img style="width:60%" src="https://tryhackme-images.s3.amazonaws.com/user-uploads/6645aa8c024f7893371eb7ac/room-content/6645aa8c024f7893371eb7ac-1723026309300.png" alt="Difference between NIDS and HIDS.">


Detection Modes :
- **Signature-Based IDS** : Each attacks has its unique pattern which is known as a signature. IDS preserved  signatures in their databases to detect the same attack if it happens in the future.
- **Anormaly-Based IDS **: Learn the normal behavior of the network and performs detection if there is any deviation from the normal behavior.Can detect zero-deay attack, however this type of IDS may generate a lot of false positives because the nature of most legitimate programs matches the malicious ones.
- **Hybrid IDS** : Combines the detection methods of signature-based IDS and anomaly-based IDS to leverage

----
#### IDS Example : Snort

Snort
- widely used open source IDS solution developed in 1998
- use signature-based and anomaly based detections to identify known threats
- Can create rules based on your requirement to detect specific traffic

 <img style="width:95%" src="https://tryhackme-images.s3.amazonaws.com/user-uploads/6645aa8c024f7893371eb7ac/room-content/6645aa8c024f7893371eb7ac-1722881168080.png" alt="Difference between Packet Sniffer mode, Packet Logging mode, and NIDS mode.">
 

| Mode                                    | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                 | Use Case                                                                                                                                                                                                                             |
| --------------------------------------- | ----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Packet sniffer mode                     | This mode reads and displays network packets without performing any analysis on them. The packet sniffer mode of Snort does not directly relate to IDS capabilities, but it can be helpful in network monitoring and troubleshooting. In some cases, system administrators might need to read the traffic flow without performing any detection to diagnose specific issues. In this case, they can utilize the packet sniffer mode of Snort. This mode allows you to display the network traffic on the console or even output it in a file.               | The network team observes some network performance issues. To diagnose the issue, they need detailed insights into the network traffic. For this purpose, they can utilize Snort’s packet sniffer mode.                              |
| Packet logging mode                     | Snort performs detection on the network traffic in real-time and displays the detections as alerts on the console for the security administrators to take action. However, in some cases, the network traffic needs to be logged for later analysis. The packet logging mode of Snort allows you to log the network traffic as a PCAP (standard packet capture format) file. This includes all the network traffic and any detections from it. Forensic investigators can use these Snort log files to perform the root cause analysis of previous attacks. | The security team needs to initiate a forensic investigation of a network attack. They would need the traffic logs to perform the root cause analysis. The network traffic logged through Snort’s packet logging mode can help them. |
| Network Intrusion Detection System mode | Snort’s NIDS mode is the primary mode that monitors network traffic in real-time and applies its rule files to identify any match to the known attack patterns stored as signatures. If there is a match, it generates an alert. This mode provides the main functionality of an IDS solution.                                                                                                                                                                                                                                                              | The security team must proactively monitor their network or systems to detect potential threats. They can leverage Snort’s NIDS mode to achieve this.                                                                                |

---
### Snort Usage
- configuration file stored in the `/etc/snort`

##### Rule format
<img style="width:100%" src="https://tryhackme-images.s3.amazonaws.com/user-uploads/6645aa8c024f7893371eb7ac/room-content/6645aa8c024f7893371eb7ac-1725532438800.png">

- **Action:** This specifies which action to take when the rule triggers. In this case, we have the action to "alert" when the traffic matches this rule.
- **Protocol:** This refers to the protocol that matches this rule. In this case, we use the protocol "ICMP" when pinging a host.
- **Source IP:** This determines the IP originating from the traffic. Since we want to detect traffic from any source IP, we set this as "any".
- **Source port:** This determines the port from which the traffic originates. Since we want to detect traffic from any source port, we set this as "any".
- **Destination IP:** This specifies the destination IP to which the matching traffic comes; it generates the alert. In this case, we used "$HOME_NET". This is a variable, and we defined its value as our whole network’s range in Snort’s configuration file.
- **Destination port:** This specifies the port the traffic would reach. Since we want to detect traffic coming to any port, we set it to "any."
- **Rule metadata:** Every rule has some metadata. That is defined at the end of the rule in parentheses. The following are its components:
    - **Message (msg):** This describes the message displayed when the subject rule triggers. The message should indicate the type of activity detected. In this case, we used "Ping Detected".
    - **Signature ID (sid):** Every rule has a unique identifier that differentiates it from others. This identifier is called the signature ID (sid). In this case, we set the sid to "10001".
    - **Rule revision (rev):** This sets the rule's revision number. Every time the rule is modified, its revision number is incremented, which helps in tracking changes to any rule.

#### Rule Creation

1. Open the "local.rules"
```shell-session
sudo nano /etc/snort/rules/local.rules
```
#### Rule testing
```shell-session
sudo snort -q -l /var/log/snort -i lo -A console -c /etc/snort/snort.conf
```

Open another tab and make a ping
```shell-session
ping 127.0.0.1
```

And we obtain :
```shell-session
sudo snort -q -l /var/log/snort -i lo -A console -c /etc/snort/snort.conf
07/24-10:46:52.401504  [**] [1:1000001:1] Loopback Ping Detected [**] [Priority: 0] {ICMP} 127.0.0.1 -> 127.0.0.1
07/24-10:46:53.406552  [**] [1:1000001:1] Loopback Ping Detected [**] [Priority: 0] {ICMP} 127.0.0.1 -> 127.0.0.1
07/24-10:46:54.410544  [**] [1:1000001:1] Loopback Ping Detected [**] [Priority: 0] {ICMP} 127.0.0.1 -> 127.0.0.1
```

---
#### Analyser un fichier de capture de trafic (.pcap)

```shell-session
sudo snort -q -A console -c /etc/snort/snort.conf -r /chemin/vers/ton/fichier.pcap
```

