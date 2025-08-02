# SSH : Installation & Configuration côté serveur


<br>

* Installation pour le client :

```
sudo apt install openssh-client
```

<br>

* Installation pour le serveur :

```
sudo apt install openssh-server
```

man sshd_config


<br>


cat /etc/ssh/sshd_config

----------------------------------------------------------------------------

# SSH : Installation & Configuration côté serveur


<br>

Principaux paramètres :
<br>

		* AcceptEnv : fixer les variables d'env pouvant être importées via le client
<br>

		* AllowAgentForwarding : permet de conserver votre clef (ex : rebond)
<br>

		* AllowGroups / DenyGroups : limiter les groupes à se connecter via ssh
<br>

		* AllowUsers / DenyUsers : limiter les users
<br>

		* Banner : ajouter une bannière à la connexion ssh
<br>

		* Password : mettre les deux à no pour disable password
				* ChallengeResponseAuthentication - RFC 4256 > poser des questions à l'utilisateurs (password..) > plus sécurisé
				* PasswordAuthentication - RFC 4252 > specific au password
<br>

		* ChrootDirectory : spécifier au chroot pour users/groups (utilisé avec match généralement)
<br>

		* Ciphers : combinaison des algorithmes d'échange
<br>

		* ClientAliveCountMax : le nombre connexion sans réponse avant cloture de la connexion
<br>

		* ClientAliveInterval : durée de la connexion ssh sans activité (envoi une requête si sans réponse = déconnexion)
<br>

		* Compression : defaut yes
<br>

		* DisableForwarding : supprime les fowarding agent, x11...
<br>

		* ExposeAuthInfo : permet d'afficher des informations l'authentification (path du fichier dans SSH_USER_AUTH)
<br>

		* FingerprintHash : type de hash pou rle fingerprint
<br>

		* ForceCommand : commande exécutée à la connexion (bypass les commandes clientes)
<br>

		* GatewayPorts : désactivation du port forwarding possible (no)
<br>

		* HostbasedAcceptedKeyTypes : type de clefs accepté : edcsa, rsa...

----------------------------------------------------------------------------

# SSH : Installation & Configuration côté serveur


<br>

		* HostbasedAuthentication : authentification sur la clef par host (pas par user)
<br>

		* HostKey / HostCertificate : localisation des fichiers de clefs ou certificatss
<br>

		* IPQoS : limitation de service via débit et/ou délai
<br>

		* Kerberos Authentication : activation de l'authentification via kerberos
<br>

		* ListenAddress : interface/ip d'écoute
<br>

		* LoginGraceTime : délai pour s'authentifier (120 secondes par défaut)
<br>

		* LogLevel : niveau de logs
<br>

		* Match : permet de conditionner une liste d'acions sous condition
<br>

		* MaxSessions : connexions permisses par connexion réseau
<br>

		* PermitEmptyPasswords : permettre un password vide
<br>

		* PermitOpen : quel port forwarding est autorisé
<br>

		* PermitRootLogin : autorisé la connexion en tant que root via ssh (défaut prohibit-password)
<br>

		* PermitUserRC : permettre l'utilisation d'un ssh rc (~/.ssh/rc) = similaire à profile
<br>

		* Port : spécifier le port d'écoute du serveur ssh
<br>

		* PrintLastLog : spécifie la denrière connexion réalisé sur le serveur à la connexion suivante
<br>

		* PrintMotd : affichage d'un message d'accueil (similaire à banner)
<br>

		* PubkeyAcceptedKeyTypes : type de clefs publiques autorisées
<br>

		* PubkeyAuthentication : autoriser ou non l'authentification par clef
<br>

		* StrictModes : vérifie les fichiers et directories avant d'accepter la connexion
<br>

		* SyslogFacility : format des logs
<br>

		* UsePAM (Pluggable Authentication Module) : utilisation du module PAM
<br>

		* X11Forwarding : authoriser le forward x11 (serveur graphique)

----------------------------------------------------------------------------

# SSH : Installation & Configuration côté serveur


<br>

* filtre par match (adduser saliou): 

* sudo adduser saliou

* sudo apt install figlet 

* figlet SALIOU

* copier le figlet et le coller dans le fichier banner.txt

```
Match User saliou
Banner /etc/banner.txt
X11Forwarding no
Match All
```
Ex : modification password (erreur)

<br>

* prise en compte des modifications

```
sudo service sshd restart
```

Rq : ssh maintient les connexions existantes
