%title: SSH
%author: Saliou


# SSH - Proxy Socks


<br>

* passer par une machine qui fait office de proxy

	navigateur > socket local > ssh client > ssh server > internet

<br>

* mise en place

```
sudo apt install -y curl iptables
sudo iptables -I OUTPUT -d www.google.fr -p tcp --match multiport --dports 443,80 -j DROP
```

<br>

* lancement du proxy socks

```
ssh -D 8888  172.17.0.2
```

* firefox : préférences > General > Network Settings > Settings > proxy socks

```
127.0.0.1,localhost | port 8888
```

<br>

* un peu plus -q -C -N -f

```
ssh -D 8888 -q -C -N -f  172.17.0.2
```


