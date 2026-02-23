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


---
**Use John  and create custom Rules to crack Password

Organisations will require a certain level of password complexity to try and combat dictionnary attacks, rules like that :
- Lowercase letter
- Uppercase letter
- Number
- Symbol

**How to create Custom rules ?** 
- rules are defined in the `john.conf` in `/opt/john/john.conf` (on TryHackMe AttackBox) or `/etc/john/john.conf`

- `[0-9]`: Will include numbers 0-9  
- `[0]`: Will include only the number 0
- `[A-z]`: Will include both upper and lowercase 
- `[A-Z]`: Will include only uppercase letters
- `[a-z]`: Will include only lowercase letters

`john --wordlist=[path to wordlist] --rule=PoloPassword [path to file]`

***
**Cracking Password Protected Zip Files**

- **Zip2John**
`zip2john [options] [zip file] > [output file]`

- `[options]`: Allows you to pass specific checksum options to `zip2john`; this shouldn’t often be necessary
- `[zip file]`: The path to the Zip file you wish to get the hash of
- `>`: This redirects the output from this command to another file
- `[output file]`: This is the file that will store the output

Example :
`zip2john secure.zip > secure.txt`

and after

`john --wordlist=/usr/share/wordlists/rockyou.txt secure.txt`

command to unzip a file: `unzip [zipfile]`

***
**Cracking Password-Protected RAR Archives

**-Rar2john

`rar2john [rar file] > [output file]`

- `rar2john`: Invokes the `rar2john` tool
- `[rar file]`: The path to the RAR file you wish to get the hash of
- `>`: This redirects the output of this command to another file
- `[output file]`: This is the file that will store the output from the command

command to extract files from rar archive : `unrar x archive.rar`

***
**Cracking SSH Keys with John**

**-Ssh2john

`ssh2john [id_rsa private key file] > [output file]`

- `ssh2john`: Invokes the `ssh2john` tool
- `[id_rsa private key file]`: The path to the id_rsa file you wish to get the hash of
- `>`: This is the output director. We’re using it to redirect the output from this command to another file.
- `[output file]`: This is the file that will store the output from

Note : if `ssh2john` not installed , use ssh2john.py located in `/opt/john/ssh2john.py`

`python /opt/john/ssh2john.py id_rsa > id_rsa_hash.txt`

and after :

`john --wordlist=/usr/share/wordlists/rockyou.txt id_rsa_hash.txt`

***
To learn more about John : https://www.openwall.com/john/