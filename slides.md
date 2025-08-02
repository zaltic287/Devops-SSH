%title: Notions
%author: xavki


# SSH : Principes


<br>

* SSH = Secure Shell

<br>

* rempaçant de telnet ou rsh (remote shell)
	dérivé scp (copy = cp)

<br>

* sécurité des communications entre 2 machines
	* cryptographie

<br>

* port par défaut = 22

<br>

* on parle aussi tunnel SSH

<br>

* architecture : 
	* client > server
	* vérification de la connexion précédente

Rq : forward X11 (interface graphique)

<br>

* objectif (idem https) :
	* lutter contre les interception
	* lutter contre l'usurpation

-----------------------------------------------------------------

# Chiffrement symétrique


<br>

* clef commune à celui qui émet le message et celui qui le lit

* les deux protagonistes doivent avoir la même clef

<br>

* avantage principal : très rapide à déchiffrer

<br>

* inconvénient principal : pas assez sécurisé si la clef compromise


<br>

# Chiffrement astmétrique


<br>

* chaque individu possède une paire de clef :
	* clef publique : transmis aux autres personnes
	* clef privée : qu'il conserve et sécurise

<br>

* attention :
	* un message chiffré par une clef publique
	* uniquement décrypté par la clef privée qui correspond
	* calculs complexes

<br>

* avantage principal : méthode très sécurisée

<br>

* inconvénient principal : message long à déchiffrer

----------------------------------------------------------------------

# Et pour SSH ?


<br>

* besoin d'un système performant : sécurisé et rapide
	* mixte des deux méthodes

<br>

Communication SSH :

<br>

0. Client > Serveur : TCP - initie la connexion - poignée de main (handshake) SYNchronize

<br>

1. Serveur > Client : TCP - réponse handshake SYN/ACKnowledge

<br>

2. Client > Serveur : TCP - confirmation handshake ACK

<br>

3. Client > Serveur : SSH - Version serveur

<br>

4. Serveur > Client : SSH - Version client

<br>

...init key

<br>

5. Client > Serveur : SSH - requête Diffie Hellman (objectif définir clef symétrique)

<br>

6. Serveur > Client : SSH - envoi de la clef symétrique chiffré par la clef publique asymétrique

<br>

7. Client > Serveur : SSH - début des échanges par le chiffrement de la clef symétrique

