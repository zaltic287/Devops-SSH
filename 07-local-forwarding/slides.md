%title: SSH
%author: Saliou


# SSH - Local Forwarding


<br>

Documentation :https://system.cs.kuleuven.be/cs/system/security/ssh/tunneling/vpn.shtml

* accéder à un port d'une autre machine via un intermédiaire

* par exemple si le port est inaccessible via firewall

<br>

* plateforme de test

```
 sudo apt update
 sudo apt install iptables nginx curl
 sudo iptables -I INPUT ! -i lo -p tcp --dport 80 -j DROP
 sudo iptables -L
```

-------------------------------------------------------------------

# SSH - Local Forwarding


<br>

* premier cas : sans rebond

```
ssh -fNL 8888:localhost:80 172.17.0.2
```

<br>

* avec un rebond simple et utilisation du localhost (127.0.0.1)

```
ssh -L 8888:172.17.0.3:80 172.17.0.2
```

<br>

* avec rebond et utilisation d'une autre interface que la lo

```
ssh -L 172.17.0.1:8888:172.17.0.3:80 172.17.0.2
```

<br>

* en mode background

```
ssh -fNL 172.17.0.1:8888:172.17.0.3:80 172.17.0.2
```
