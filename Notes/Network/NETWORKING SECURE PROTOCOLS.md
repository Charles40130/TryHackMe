***
**TLS** : crypotographic protocol operating at the OSI model's transport layer.
- allowe secure communication between a client and a server over an insecure network.
- many protocols have received security upgrades with the simple adddition of TLS
- it allows to upgrade security of many protocole (HTTP,  DNS , MQTT) which have become HTTPS , DoT ( DNS over TLS), MQTTS ect...


Quand un serveur (IMAP, HTTPS, etc.) utilise **TLS**, il présente un **certificat** au client.

👉 Ce certificat sert à :

- **chiffrer la connexion**
- **prouver l’identité du serveur**

Mais il y a **deux cas** :
### ❌ Certificat auto-signé (self-signed)

- Le serveur **se signe lui-même**
- Le client **ne peut pas faire confiance**
- Résultat :  
    👉 _“certificate not trusted”_, warning, refus possible

### ✅ Certificat signé (signed TLS)

- Le certificat est **signé par une autorité de certification (CA)**
- Le client **fait confiance automatiquement**
- Pas d’alerte, connexion propre 🔐
## 2️⃣ C’est quoi “obtenir un signed TLS” ?

👉 Ça veut dire :

> Obtenir un certificat TLS **signé par une autorité de certification reconnue**

Exemples de CA :
- Let’s Encrypt (gratuit)
- DigiCert    
- GlobalSign
- Sectigo
- etc.

Les systèmes (Linux, Windows, navigateurs, clients mail) **connaissent déjà ces CA**.

***
Before TLS
HTTP following two steps
1. Etablish a TCP three-way handshake with the target server
2. Communicate using HTTP protocol
	- example : issue HTTP requests such as ` GET / HTTP/1.1`

AFTER TLS :
HTTP OVER TLS ( HTTPS)
1. Etablish a TCP three-way handshake with the target server
2. Etablish a TLS session
3. Communicate using the HTTP protocol
	-  example : issue HTTP requests , such as ` GET / HTTP/1.1`
***

| Protocol | Default Port Number |
| -------- | ------------------- |
| HTTPS    | 443                 |
| SMTPS    | 465 and 587         |
| POP3S    | 995                 |
| IMAPS    | 993                 |
***
With TELNET, trafic is sent in cleartext.
To find a solution to that => SSH

**SSH** = Secure Shell
- v1 released in 1995
- OpenSSH released in 1999 ( open-source implementation of SSH protocol)

OpenSSH offers several benefits. We will list a few key points:

- **Secure authentication**: Besides password-based authentication, SSH supports public key and two-factor authentication.
- **Confidentiality**: OpenSSH provides end-to-end encryption, protecting against eavesdropping. Furthermore, it notifies you of new server keys to protect against man-in-the-middle attacks.
- **Integrity**: In addition to protecting the confidentiality of the exchanged data, cryptography also protects the integrity of the traffic.
- **Tunneling**: SSH can create a secure “tunnel” to route other protocols through SSH. This setup leads to a VPN-like connection.
- **X11 Forwarding**: If you connect to a Unix-like system with a graphical user interface, SSH allows you to use the graphical application over the network.
***
**SFTP** : SSH File Transfer Protocol
- allows secure file transfer
- use also the same n°port, 22

`sftp username@hostname` : connect to the machine 
`get filename` : download the file
`put filename` : upload files

So we have 2 solutions to transfer files ? SFTP and FTPS ?
Yes ! Let's see the differences :

**FTPS**
- FTP + TLS/SSL
- use many connexions

| Point                                            | SFTP     | FTPS          |
| ------------------------------------------------ | -------- | ------------- |
| Basé sur                                         | SSH      | FTP + TLS     |
| Nombre de connexions                             | 1        | Plusieurs     |
| Port par défaut                                  | 22       | 21 / 990      |
| Chiffrement                                      | Toujours | Oui           |
| Configuration firewall                           | Simple   | Plus complexe |
| Certificats                                      | ❌        | ✅             |
| Clés SSH                                         | ✅        | ❌             |
| Question                                         | Réponse  |               |
| SFTP permet plusieurs transferts en même temps ? | ✅ Oui    |               |
| FTPS est toujours plus rapide ?                  | ❌ Non    |               |
| Différence de vitesse notable ?                  | ❌ Rare   |               |
| Le plus simple / fiable ?                        | ✅ SFTP   |               |
z