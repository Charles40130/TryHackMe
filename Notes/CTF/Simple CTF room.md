
Scanning service port  under port 1000 with nmap 

```
sudo nmap -p 1-1000 -Pn 10.114.155.60
```

Assez long , d'après gemini

```
sudo nmap -sS -p 1-1000 -T4 -Pn 10.114.155.60
```
Plus bruyant mais peut accélérer le scan

**Note**: Appuyer sur la touche espace durant le scan pour voir ou ca en est

nmap -sVC -Pn -oN initial_map 10.114.155.60

- 3 ports ouverts
- 21 , 80 et 2222
- ftp ,http et ssh


On s'attaque au service http
On peut déjà lancer ouvrir le site sur firefox pour voir ce que ca donne

Et faire en parrallèle une listage de page : 
```
gobuster dir -u 10.114.155.60 -w /usr/share/wordlists/dirb/small.txt -t 64
```

On trouve la page /simple, page sur laquel on a pas mal d'info

CMS Made Simple, version du CMS , on peut regarder si il y a pas un cve connu

Bingo ! CVE-2019-9053

On aurait pu utiliser l'outil : **searchsploit**
Permet de lister les potentiels cve 

```
searchsploit 'made simple'
```

Et on cherche dans la liste
