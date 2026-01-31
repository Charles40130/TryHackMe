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

