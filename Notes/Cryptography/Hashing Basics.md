How can be sure that a file we want to download is exactly the same original file ? compare hash values !

**Hash value** : fixed-size string or characters that is computed by a hash function

`md5sum passport.jpg` : show the md5 hash

***
3 insecure practices
* Storing passwords in plaintext
* Storing passwords using a deprecated encryption
* Storing passwords using an insecure hashing algorithm

**Storing Passwords in Plaintext**
- Rockyou is good example

**Using an insecure encryption algorithm
- Adobe

**Insecure hash function**
- LinkedIn data breach in 2012 , use SHA-1

***
**Using hashing to store passwords**
- Hash function always turn the same input into the same output. => Problem if someone cracks the hash
* Raimbow table 

=> Solution : add a "salt" to the passwords


***
**Recognising password hashes**

Linux passwords

password hashes are stored in `/etc/shadow`


`shadow` file contains the password information, each line contains 9 fields separated by `:`.

`man 5 shadow` 

The encrypted password field contains the hashed passphrase with four components: prefix (algorithm id), options (parameters), salt, and hash. It is saved in the format `$prefix$options$salt$hash`

| Prefix                         | Algorithm                                                                                                                                                                                        |
| ------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| `$y$`                          | yescrypt is a scalable hashing scheme and is the default and recommended choice in new systems                                                                                                   |
| `$gy$`                         | gost-yescrypt uses the GOST R 34.11-2012 hash function and the yescrypt hashing method                                                                                                           |
| `$7$`                          | scrypt is a password-based key derivation function                                                                                                                                               |
| `$2b$`, `$2y$`, `$2a$`, `$2x$` | bcrypt is a hash based on the Blowfish block cipher originally developed for OpenBSD but supported on a recent version of FreeBSD, NetBSD, Solaris 10 and newer, and several Linux distributions |
| `$6$`                          | sha512crypt is a hash based on SHA-2 with 512-bit output originally developed for GNU libc and commonly used on (older) Linux systems                                                            |
| `$md5`                         | SunMD5 is a hash based on the MD5 algorithm originally developed for Solaris                                                                                                                     |
| `$1$`                          | md5crypt is a hash based on the MD5 algorithm originally developed for FreeBSD                                                                                                                   |


***
**Hashcat** : use for crack hashes

`hashcat -m <hash_type> -a <attack_mode> hashfile wordlist`
- `-m <hash_type>` :specifies the hash-type numeric format. Example : `-m 1000`is for NTLM , `-m 3200` is for bcrypt
- `-a <attack_mode>` :specfies the attack-mode. Example : `-a 0` is for straight, ie trying one password from the wordlist after the other
- `hashfile` : the file containing the hash you want to crack
- `wordlist` : the security word list you want to use in your attack

Example:
	`hashcat -m 3200 -a 0 hash.txt /usr/share/wordlists/rockyou.txt`




---

# 🧠 FICHE MÉTHODE — Identifier un hash en 10 secondes

## ✅ 1. Regarde le début

### 👉 Commence par `$` ?

→ Hash de mot de passe structuré (**MCF**)

**À connaître par cœur :**

|Préfixe|Algo|
|---|---|
|`$2a$`, `$2b$`, `$2y$`|**bcrypt**|
|`$5$`|SHA-256-crypt|
|`$6$`|**SHA-512-crypt**|
|`$argon2`|Argon2|

👉 Très souvent → hashes Linux / bases utilisateurs.

---

## ✅ 2. Sinon → regarde la longueur

|Longueur|Algo probable|
|---|---|
|32 hex|MD5|
|40 hex|SHA-1|
|**64 hex**|**SHA-256**|
|128 hex|SHA-512|

⚠️ uniquement `0-9 a-f` → hex.

---

## ✅ 3. Vérifie s’il y a un salt

Exemples :

```
hash:salt
salt:hash
$id$salt$hash
```

👉 Change le **mode Hashcat** !

---

## ✅ 4. Choisis le bon mode Hashcat

Réflexes :

```
bcrypt → 3200
SHA-256 → 1400
SHA-512-crypt → 1800
MD5 → 0
```

---

## ✅ 5. Ordre d’attaque intelligent

Toujours :

1️⃣ rockyou.txt  
2️⃣ règles  
3️⃣ brute force ciblé

👉 Ne brute force jamais au hasard.

---

# ⚠️ ERREUR DE DÉBUTANT #1

Confondre :

👉 **SHA-256**  
avec  
👉 **SHA-256-crypt**

➡️ Le `$` change tout.

---

# 🎯 Raccourci mental (très puissant)

👉 `$` = mot de passe Linux / bcrypt  
👉 pas de `$` = hash brut  
👉 64 hex = SHA-256

---
**Commande compter le nb de caractères du hash**



hashcat --show -m 0 hash.txt
hashcat -m 0 -a 3 hash.txt ?d?d?d?d?d?d?d?d
