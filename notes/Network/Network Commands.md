***
**Telnet** = protocole réseau pour se **connecter à distance** à un server

* utilise généralement tcp
* Non sécurisé => mdp circulent en clair

* **Principaux usages**:
	- Tester des ports
	- Interagir avec des services simples (echo via port 7, daytime port 13, http via port 80)
	- Debug réseau

```bash
telnet <IP> <PORT>
```
Exemple :
```bash
telnet 10.80.127.44 80
```


Ensuite ajouter
```bash
GET / HTTP/1.1
Host: example.com
```

`GET` : correspond à une méthode HTTP , lire une ressource( autres méthodes POST,PUT,DELETE,HEAD)

/ : chemin de la ressource
- `/` -> page d'accueil
- `/index.html` 
- `/login`

`HTTP/1.1` -> version du protocole http

Puis appuyer 2 fois sur `Entrer` pour valider et recevoir le résultat

`telnet <adresse_ip>` ouvre une connexion TCP sur le port 23 par défaut et permet de se connecter au terminal distant de la machine ( comme ssh)
Mais alors quel est la diff avec ssh ?
- Telnet est non sécurisé les informations qui transitent par ce protocole sont en clairs à la différence de ssh
*** 
**Sniffing Réseau 👀**

**Tshark /Wireshark**
* Tshark = version en ligne de commande de Wireshark
* WireShark = interface graphique pour capturet et analyser le trafic réseau


***
**ICMP : Problèmes de réseau

Commandes :
* `ping : tester la connectectivité à un syst-ème ciblé et mesure le RTT.
* `traceroute` : découvrir les route de l'host à la cible (`tracert`sur Windows)

***
`whois` : voir les informations et registres d'un nom de domaine (nom, numéro tel , email , address)

exemple :
`whois google.com`  

Beaucoup de site faut le choix de ne pas afficher ces informations là.

En ce qui concerne les site avec des TLD récents ( `.app`, `.dev`, `.world`, `.tech` ect...) n'utilise pas le WHOIS classique, ils utilisent RDAP ( Registration Data Access Protocol) , ainsi `whois`ne donnera rien sur ce type de nom de domaine

***
**FTP** = File Transfer Protocol
* Permet de transférer des fichiers d'une machine à une autre
* 2 mods de transfert : binary ou ASCII
* Par défault on utilise le mode binary pour le transfer.
* ASCII est devenu presque inutile ajd, il était initialement utilisé pour les adapter les fins de lignes des fichiers

***
SMTP : Simple Mail Transfer Protocol
* Permet d'envoyer un mail entre 2 servers

`telnet <ip_adress> 25` : Telnet ( le client) ouvre une connexion TCP,
la connexion est établie vers `<ip_adress>` et le port `25` , ce port correspond au protocole SMTP , donc le serveur ( ou service) SMTP écoute sur ce port.

Attention :
le mot `serveur` est parfois ambigu
- Serveur = machine ( matériel/ VM)
	- un PC
	- un VPS
	- une machine physique dans un datacenter
- Serveur = service / logiciel , un programme qui:
	- écoute sur un port
	- attend des connexions
	- répond selon un protocole 
	- Dans SMTP , FTP , HTTP , quand on dit serveur on parle tjrs de ça


- `HELO` or `EHLO` permet d'initialiser la session SMTP
- `MAIL FROM: <user@example.com>`  spécifie l'email de l'envoyeur
- `RCPT TO: <recepteur@example.com>` spécifie l'email du receveur
- `DATA` indique que le client va démarrer l'envoi du contenu du message
- `.` indique que la fin de l'envoi du message email

***
**POP3 =Post Office Protocol v3**
* Protocol applicatif
* Permet de récupérer les emails depuis un server vers ton client mail

`telnet <ip_adress> 110` : Telnet ( le client) ouvre une connexion TCP, la connexion est établie vers `<ip_adress>` et le port 110, ce port correspond au protocol POP3, donc le serveur (ou service) SMTP écoute sur ce port

- `USER <username>` identifies the user
- `PASS <password>` provides the user’s password
- `STAT` requests the number of messages and total size
- `LIST` lists all messages and their sizes
- `RETR <message_number>` retrieves the specified message
- `DELE <message_number>` marks a message for deletion
- `QUIT` ends the POP3 session applying changes, such as deletions

 POP3 suffit lorsque on travaille ave un appareil , cependant comment check ses mails sur un autre pc, ou téléphone ? **IMAP** est la solution
*** 

**IMAP  = Internet Message Access Protocol 
- permet la synchronisation des messages

- `telnet 10.10.41.192 143` : Telnet ( le client) ouvre une connexion TCP, la connexion est établie verts `10.10.41.192` et le port 143, ce port correspond au service IMAP, donc le server (ou service) IMAP écoute sur ce port.

- `LOGIN <username> <password>` : authentifie l'utilisateur
- `SELECT <mailbox>` : selectionne la boite mail avec laquel travailler
- `FETCH <mail_number> <data_item_name>` 
- `MOVE <sequence_set> <mailbox>` : déplace le message spécifique vers l'autre boite mail
- `COPY <sequence_set> <data_item_name>` : copie le message spécifique vers la boite mail
- `LOGOUT` : logs out

***


Résumé :

| Protocol | Protocol de transfert | N° de port par défaut |
| -------- | --------------------- | --------------------- |
| TELNET   | TCP                   | 23                    |
| DNS      | UDP ou TCP            | 53                    |
| HTTP     | TCP                   | 80                    |
| HTTPS    | TCP                   | 443                   |
| FTP      | TCP                   | 21                    |
| SMTP     | TCP                   | 25                    |
| POP3     | TCP                   | 110                   |
| IMAP     | TCP                   | 143                   |
