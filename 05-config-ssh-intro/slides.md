# SSH - ssh config


<br>

Objectifs :
- configurer ses connexions ssh
- en fonction des hosts (pattern possible)
- définition d'éléments standards : user, port, clef
- d'autres éléments : forward agent, forward X...
- proxy et jump
- toutes les options de ssh

* attention : se lit de haut en bas


<br>

* redéfinir le nom cible pour ssh

* permet de renommer le host 172.17.0.2 en toto

```
Host toto
  HostName 172.17.0.2
```

--------------------------------------------------------------------------

# SSH - ssh config


<br>

* définir le user à utiliser pour se connecter à la host toto

```
Host toto
  HostName 172.17.0.2
  User oki
```

<br>

* le port et la clef à utiliser

```
Host toto
  HostName 172.17.0.2
  User oki
  Port 22
  IdentityFile ~/.ssh/id_rsa
```

--------------------------------------------------------------------------

# SSH - ssh config


<br>

* multiplexer sa connexion (réutilisation de connexion tcp)

```
Host *
  User oki
  Port 22
  IdentityFile ~/.ssh/id_rsa
  ControlPath ~/.ssh/controlmasters/%r@%h:%p
  ControlMaster auto
  ControlPersist 600
  PreferredAuthentication publickey
  AddressFamily inet
  Protocol 2
  Compression yes
```

<br>

* forwarding

```
Host toto
  HostName 172.17.0.2
  User oki
  Port 22
  IdentityFile ~/.ssh/id_rsa
  ForwardAgent yes
  ForwardX11 yes
  ForwardX11Trusted yes
```
