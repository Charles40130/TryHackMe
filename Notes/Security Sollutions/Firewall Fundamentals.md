- like a security guards outside shopping malls,banks ect...
- inspect the incoming and outgoing traffic of a device or a network

---
#### Types of Firewalls

<img src="https://tryhackme-images.s3.amazonaws.com/user-uploads/6645aa8c024f7893371eb7ac/room-content/6645aa8c024f7893371eb7ac-1725967312491.png" style="width:100%">
Stateless Firewall : This type of firewall operates on layer 3 and layer 4 of the OSI model and works solely by filtering the data based on predetermined rules without taking note of the state of the previous connections.

Stateful Firewall : Unlike stateless firewalls, this type of firewall goes beyond filtering packets by predetermined rules. It also keeps track of previous connections and stores them in a state table. This adds another layer of security by inspecting the packets based on their history with connections. Stateful firewalls operate at layer 3 and layer 4 of the OSI model.

Proxy Firewall : The problem with previous firewalls was their inability to inspect the contents of a packet. Proxy firewalls, or application-level gateways, act as intermediaries between the private network and the Internet and operate on the OSI model’s layer 7.

Next-Generation Firewall : This is the most advanced type of firewall that operates from layer 3 to layer 7 of the OSI model, offering deep packet inspection and other functionalities that enhance the security of incoming and outgoing network traffic.


| Firewalls                 | Characteristics                                                                                                                                                                                |
| ------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| Stateless firewalls       | - Basic filtering  <br>- No track of previous connections  <br>- Efficient for high-speed networks                                                                                             |
| Stateful firewalls        | - Recognize traffic by patterns  <br>- Complex rules can be applicable  <br>- Monitor the network connections                                                                                  |
| Proxy firewalls           | - Inspect the data inside the packets as well  <br>- Provides content filtering options  <br>- Provides application control  <br>- Decrypts and inspects SSL/TLS data packets                  |
| Next-generation firewalls | - Provides advanced threat protection  <br>- Comes with an intrusion prevention system  <br>- Identify anomalies based on heuristic analysis  <br>- Decrypts and inspects SSL/TLS data packets |


---

#### Rules in Firewalls
The basic components of a firewall’s rule are described below:

- **Source address:** The machine’s IP address that would originate the traffic.
- **Destination address:** The machine’s IP address that would receive the data.
- **Port:** The port number for the traffic.
- **Protocol:** The protocol that would be used during the communication.
- **Action:** This defines the action that would be taken upon identifying any traffic of this particular nature.
- **Direction:** This field defines the rule’s applicability to incoming or outgoing traffic.

Example Allow :

| Action | Source         | Destination | Protocol | Port | Direction |
| ------ | -------------- | ----------- | -------- | ---- | --------- |
| Allow  | 192.168.1.0/24 | Any         | TCP      | 80   | Outbound  |
Example Deny : 

| Action | Source | Destination    | Protocol | Port | Direction |
| ------ | ------ | -------------- | -------- | ---- | --------- |
| Deny   | Any    | 192.168.1.0/24 | TCP      | 22   | Inbound   |
Example Forward :

| Action  | Source | Destination | Protocol | Port | Direction |
| ------- | ------ | ----------- | -------- | ---- | --------- |
| Forward | Any    | 192.168.1.8 | TCP      | 80   | Inbound   |

Directionality of Rules :
##### Inbound Rules

Rules are categorized as inbound rules when they are meant to be applied to incoming traffic only. For example, you might allow incoming HTTP traffic (port 80) on your web server.

##### Outbound Rules

These rules are made for outgoing traffic only. For example, blocking all outgoing SMTP traffic (port 25) from all the devices except the mail server.

##### Forward Rules

Forwarding rules are created to forward specific traffic inside the network. For example, a forwarding rule can be created to forward the incoming HTTP (port 80) traffic to the web server located in your network.


---

#### Windows Defender Firewall


<img src="https://tryhackme-images.s3.amazonaws.com/user-uploads/5f9c7574e201fe31dad228fc/room-content/5f9c7574e201fe31dad228fc-1726660679211.png" alt="Windows Defender Firewall dashboard.">

<img src="https://tryhackme-images.s3.amazonaws.com/user-uploads/5f9c7574e201fe31dad228fc/room-content/5f9c7574e201fe31dad228fc-1726665055716.png" alt="Windows Defender Firewall different options.">

create inbound and outbound rules.
<img src="https://tryhackme-images.s3.amazonaws.com/user-uploads/5f9c7574e201fe31dad228fc/room-content/5f9c7574e201fe31dad228fc-1726665941554.png" alt="Inbound and outbound rules in Windows Defender firewall.">


---
#### Linux iptables Firewall



Netfilter
- framework inside Linux OS with core firewall functionnalities ( packet filtering, NAT , and connection tracking)
- Some common firewall utililities utilize this framework : 
	- **iptables:** This is the most widely used utility in many Linux distributions. It uses the Netfilter framework that provides various functionalities to control network traffic.
	- **nftables:** It is a successor to the “iptables” utility, with enhanced packet filtering and NAT capabilities. It is also based on the Netfilter framework.
	- **firewalld:** This utility also operates on the Netfilter framework and has predefined rule sets. It works differently from the others and comes with different pre-built network zone configurations.

- ufw (Uncomplicated Firewall ) 
	- eliminate the complication of making rules , giving an easier interface ( beginner-friendly)

```bash
shell-session
sudo ufw status
```
: know the status


```shell-session
sudo ufw enable
```

```shell-session
sudo ufw default allow outgoing
```

To deny all outgoing traffic from your machine as a default policy:
```bash
ufw default deny outgoing
```