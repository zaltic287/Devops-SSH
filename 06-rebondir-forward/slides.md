# SSH - Rebondir et Forward d'agent


<br>

Objectifs :
- rebondir entre plusieurs serveurs intermédiaire
- embarquer son agent et donc sa clef

<br>

* Jump :

exemple : srv1 > srv2 > srv3 > ... > srv x

```
ssh -J user@srv1,user@srv2,user@srv3 user@srvx
ssh -J 172.17.0.2,172.17.0.3,172.17.0.4 172.17.0.5
```

<br>

* forward d'agent > embarquer sa clef

```
ssh -A 172.17.0.2
ssh -A 172.17.0.3
ssh 172.17.0.4
```

-------------------------------------------------------------------

# SSH - Rebondir et Forward d'agent


<br>

* exemple création d'un user sur serveur distant et ajout de la clef

```
ssh -J 172.17.0.2 devops@172.17.0.3
```

<br>

* pour l'intégrer dans son ssh config

```
Host *
  ForwardAgent yes
Host bastion
  Hostname 172.17.0.2
  User oki
  IdentityFile ~/.ssh/id_rsa
Host srv1
  Hostname 172.17.0.3
  User devops
  ProxyJump bastion
```

ssh srv1


* ou si pas de jump la proxy command

```
Host srv1
  Hostname 172.17.0.3
  User devops
  ProxyCommand ssh bastion -W %h:%p        # Si ProxyJump n'est pas disponible
```
