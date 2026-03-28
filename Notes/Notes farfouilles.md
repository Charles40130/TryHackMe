**Programme** : code "passif"

**Processus** : programme en train de s'executer
- instance active d'un programme
- avec :
	- mémoire
	- registre CPU
	- pile ( stack
	- UID / EUID
	- PID ( identifiant unique)

- UID ( Real uid) : Utilisateur qui a lancé le programme
- EUID ( Effective UID) : Utilisateur dont les privilèges sont utilisés par le processus

- SUID = Set User ID
	- C’est un **bit spécial sur un fichier exécutable** qui dit :
		“Quand quelqu’un lance ce programme, il s’exécute avec les droits du propriétaire du fichier”


`setreuid(a,b)` : permet de changer le UID réel et EUID du processus
ainsi le UID réel devient a et le UID devient b

