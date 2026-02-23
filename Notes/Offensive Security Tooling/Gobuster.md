- open-source offensive tool
- wirtter in Golang
- enumarate web dir. , DNS subdomains, vhosts , amazon s3 buckets, google cloud storage by brute force
---
`gobuster --help` : list all commands /help page

### Example
Focus on `dir` mode

`gobuster dir -u "http://www.example.thm/" -w /usr/share/wordlists/dirb/small.txt -t 64`

- `gobuster dir` indicates that we will use the directory and file enumeration mode.
- `-u "http://www.example.thm/"` tells Gobuster that the target URL is [http://example.thm/](http://example.thm/).
- `-w /usr/share/wordlists/dirb/small.txt` directs Gobuster to use the _small.txt_ wordlist to brute force the web directories. Gobuster will use each entry in the wordlist to form a new URL and send a GET request to that URL. If the first entry of the wordlist were images, Gobuster would send a GET request to [http://example.thm/images/.](http://example.thm/images/.)
- `-t 64` sets the number of threads Gobuster will use to 64. This improves the performance drastically.

Overview of Gobuster `dir` command :
`gobuster dir --help`

---
- When using the IP , you may target a different website than inteded
	 web server can host multiple websites using on IP (called virtual hosting) => use HOSTNAME if you want to be sure

```
gobuster dir -u "http://www.example.thm" -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt -r
````

```
gobuster dir -u "http://www.example.thm" -w /usr/share/wordlists/dirbuster/directory-list-2.3-medium.txt -x .php,.js
```
look dir located at `http://example.thm` using the wordlist *directory-list-2.3-medium.txt* . Also lists all files that habe .php or .js extension

- Add ` -t 64` to accelerate the enumeration command

`curl www.offensivetools.thm/secret/flag.js` : download the file


---
### Focus on `DNS` MODE

`gobuster dns --help`

Follow command syntax :
`gobuster dns -d example.thm -w /path/to/wordlist`

```
gobuster dns -d offensivetools.thm -w /usr/share/wordlists/SecLists/Discovery/DNS/subdomains-top1million-5000.txt 
````


----
### Focus `Vhost` mode

Virtual hosts : différent websites on the same machine , look like subdomains but are not.

Virtual hosts are IP-based and running on the same server , subdomains are set up in DNS.

Gobuster scans:

- `vhost` mode will navigate to the URL created by combining the configured HOSTNAME (-u flag) with an entry of a wordlist.
- `dns` mode will do a DNS lookup to the FQDN created by combining the configured domain name (-d flag) with an entry of a wordlist.

`gobuster vhost --help` : help command

```
gobuster vhost -u "http://example.thm" -w /path/to/wordlist
```


```
gobuster vhost -u "http://10.114.155.143" --domain offensivetools.thm -w /usr/share/wordlists/SecLists/Discovery/DNS/subdomains-top1million-5000.txt --append-domain --exclude-length 201-404

```

- `gobuster vhost` instructs Gobuster to enumerate virtual hosts.
- `-u "http://10.114.155.143"` sets the URL to browse to 10.114.155.143.
- `-w /usr/share/wordlists/SecLists/Discovery/DNS/subdomains-top1million-5000.txt` configures Gobuster to use the _subdomains-top1million-5000.txt_ wordlist. Gobuster appends each entry in the wordlist to the configured domain. If no domain is explicitly configured with the `--domain` flag, Gobuster will extract it from the URL. E.g., _test.example.thm_, _help.example.thm_, etc. If any subdomains are found, Gobuster will report them to you in the terminal.  
    
- `--domain example.thm` sets the top- and second-level domains in the `Hostname:` part of the request to _example.thm._  
    
- `--append-domain` appends the configured domain to each entry in the wordlist. If this flag is not configured, the set hostname would be _www_, _blog_, etc. This will cause the command to work incorrectly and display false positives.
- `--exclude-length` filters the responses we get from the sent web requests. With this flag, we can filter out the false positives. If you run the command without this flag, you will notice you will get a lot of false positives like "Found: Orion.example.thm Status: 404 [Size: 279]" or  "Found: pm.example.thm Status: 404 [Size: 276]". These false positives typically have a similar response size, so we can use this to filter out most false positives. We expect to get a 200 OK response back to have a true positive. There are, however, exceptions, but it is not in the scope of this room to go deeper into these.