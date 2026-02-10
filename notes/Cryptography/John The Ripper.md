Identify the hash :
- https://hashes.com/en/tools/hash_identifier
or
- https://gitlab.com/kalilinux/packages/hash-identifier/-/tree/kali/master

`john --format=raw-md5 --wordlist=/usr/share/wordlists/rockyou.txt hash_to_crack.txt` 

john --show hash1.txt

john --show --format=raw-md5 hash1.txt



NTHash / NTLM 
- hash format modern windows operating system

`john --format=nt --wordlist=/usr/share/wordlists/rockyou.txt ntlm.txt`

***
**Cracking Hashes from /etc/shadow

`/etc/shadow`:file on linux machiens where password hashes are stored
- contain hash of passwords
- acces is very restrictive (root only)

`/etc/passwd` :
- contain name users
- informations of account
- ❌ don't contain hash of password

`unshadow`:tools of John use to combine passwd ( `etc/passwd` file) and `/etc/shadow`to understand and exploit to crack passwd

`unshadow [path to passwd] [path to shadow]`
- `unshadow` :invokes the unshadow tool
- `[path to passwd]` : file that contains the copy of the /etc/passwd file you've taken from the target machine
- `[path to shadow]` : file that contains the copy of the /etc/shadow file you've taken from the target machine

**Example Usage:**
`unshadow local_passwd local_shadow > unshadowed.txt
`
and after 

`john --wordlist=/usr/share/wordlists/rockyou.txt --format=sha512crypt unshadowed.txt`

