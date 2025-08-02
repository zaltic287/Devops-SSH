# SSH - Génération et Utilisation de la clef



<br>

* principe clefs
		* clef privée
		* clef privée
		* type de clef / algorithme (rsa, dsa, ecdsa)
		* longeur de clef (dépend de l'algo ecdsa 521)

<br>

* génération via ssh-keygen

```
ssh-keygen -t ecdsa -b 521
```

<br>

* spécifier la localisation de sortie

```
ssh-keygen -t ecdsa -b 521 -f /myhome/.ssh/maclefprivee
```

<br>

* ssh-keygen fourni un prompt pour vous aider

<br>

* important : ajout d'une passphrase 
		* sinon une clef ssh est plus dangereuse qu'un password

<br>

* permissions sur les fichiers de clefs < 0600

--------------------------------------------------------------------------------------

# SSH - Génération et Utilisation de la clef



<br>

* ajout de votre clef publique sur le host distant

```
vim /home/user/.ssh/authorized_keys
```

Remarque : specific pour une ip

```
from="10.0.0.?,*.example.com",no-X11-forwarding ssh-rsa AB3Nz...EN8w== Saliou@monhost
```

<br>

* utilisation de la clef

```
ssh -i /localisation/clef/privee Saliou@monhost
```

