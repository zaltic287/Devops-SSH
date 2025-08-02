%title: SSH
%author: Saliou


# SSH - Remote Forwarding


<br>

Documentation :https://system.cs.kuleuven.be/cs/system/security/ssh/tunneling/vpn.shtml

* accéder à un port d'une autre machine via un rebond

* par exemple si le port est inaccessible via firewall

<br>

* plateforme de test

```
 sudo apt update && sudo apt install iptables nginx curl
 sudo systemctl start nginx
 sudo iptables -I INPUT -s 172.17.0.4 -j DROP
 sudo iptables -L
```

-------------------------------------------------------------------

# SSH - Remote Forwarding


<br>

* demo

```
ssh -R 8888:172.17.0.3:80 172.17.0.4
```

* en mode background

```
ssh -fNR 8888:172.17.0.3:80 172.17.0.4
```
