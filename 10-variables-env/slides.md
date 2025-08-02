# SSH - Variables d'Environnement


<br>

* passer des variables de la machine local vers le remote


<br>

* définir la variable d'environnement

```
export MAVAR="v1.11"
```

<br>

* modifier la conf du serveur ssh dans /etc/ssh/sshd_config

```
AcceptEnv MAVAR
```

Rq : ou encore en ligne de commande

```
ssh -o SendEnv="MAVAR" 172.17.0.2
```

<br>

* éditer le fichier ~/.ssh/config

```
Host bastion
  Hostname 172.17.0.2
  User oki
  IdentityFile ~/.ssh/id_rsa
  SendEnv MAVARIABLE
```
