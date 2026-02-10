# 🔐 GPG (GNU Privacy Guard)

## 🧠 Définition

**GPG (GNU Privacy Guard)** est un logiciel libre implémentant le standard **OpenPGP**.  
Il permet de :

- 🔒 **Chiffrer** des fichiers et messages
    
- 🔓 **Déchiffrer** des données protégées
    
- ✍️ **Signer numériquement**
    
- ✅ **Vérifier l’authenticité** et l’intégrité des données
    

GPG est largement utilisé pour la **sécurité des emails**, des fichiers sensibles et des échanges cryptographiques.

---

## 📌 Pourquoi utiliser GPG ?

Objectifs de sécurité :

- **Confidentialité** → seul le destinataire peut lire le message
    
- **Authenticité** → vérifier l’identité de l’expéditeur
    
- **Intégrité** → garantir que le message n’a pas été modifié
    
- **Non-répudiation** → l’expéditeur ne peut nier l’envoi
    

---

## 🔑 Cryptographie utilisée par GPG

### 🔐 Cryptographie asymétrique

- Chaque utilisateur possède :
    
    - une **clé publique** (à partager)
        
    - une **clé privée** (à garder secrète)
        
- Ce qui est chiffré avec la clé publique ne peut être déchiffré qu’avec la clé privée
    

### 🔒 Cryptographie symétrique

- Une **clé secrète unique** chiffre et déchiffre les données
    
- Rapide mais nécessite un échange sécurisé de la clé
    

### 🔁 Chiffrement hybride (OpenPGP)

GPG combine les deux :

1. Le message est chiffré avec une **clé symétrique**
    
2. Cette clé est chiffrée avec la **clé publique du destinataire**
    
3. Le destinataire utilise sa **clé privée** pour déchiffrer la clé symétrique
    
4. Le message est déchiffré
    

➡️ Sécurité + performance

---

## 🗝️ Clés GPG

### Types de clés

- **Clé publique** → chiffrement + vérification de signature
    
- **Clé privée** → déchiffrement + signature
    
- **Sous-clés** → usage spécifique (chiffrement, signature)
    

### Protection

- La clé privée est protégée par une **passphrase**
    
- Stockée localement dans le **keyring GPG**
    

---

## 📦 Trousseau de clés (Keyring)

Emplacement par défaut :

- `~/.gnupg/`
    

Contenu :

- `pubring.kbx` → clés publiques
    
- `private-keys-v1.d/` → clés privées chiffrées
    
- `trustdb.gpg` → niveau de confiance des clés
    

---

## 📥 Importation d’une clé

### Commande

`gpg --import backup.key`

### Définition

Importe une clé OpenPGP dans le trousseau local GPG.

### Fonctionnement

1. Lecture du fichier `backup.key`
    
2. Détection des clés (publique / privée)
    
3. Ajout dans le keyring local
    
4. La clé privée reste chiffrée par la passphrase
    

### Cas d’usage

- Restaurer une clé depuis une sauvegarde
    
- Importer une clé privée pour déchiffrer des messages anciens
    

### ⚠️ Sécurité

- `backup.key` est **très sensible**
    
- À supprimer ou stocker hors ligne après import
    

---

## 📤 Déchiffrement d’un message

### Commande

`gpg --decrypt confidential_message.gpg`

### Définition

Déchiffre un fichier chiffré avec la clé publique du destinataire.

### Fonctionnement

1. Analyse du fichier chiffré
    
2. Identification de la clé privée requise
    
3. Demande de la **passphrase**
    
4. Déchiffrement de la clé symétrique
    
5. Déchiffrement du message
    

### Résultat

- Affichage du message dans le terminal
    
- Ou création d’un fichier en clair
    

---

## 🔗 Lien logique entre les commandes

|Étape|Rôle|
|---|---|
|Génération / import clé|Posséder la clé privée|
|`gpg --import`|Rendre la clé disponible|
|`gpg --decrypt`|Lire les messages chiffrés|
|Passphrase|Protection de la clé privée|

Sans clé privée importée → **impossible de déchiffrer**

---

## 🛡️ Bonnes pratiques de sécurité

- 🔒 Passphrase longue et robuste
    
- 💾 Sauvegarde des clés hors ligne
    
- 🧨 Suppression des backups après import
    
- 🔍 Vérification des clés :
    

`gpg --list-secret-keys`

- 🚨 Révocation immédiate en cas de compromission