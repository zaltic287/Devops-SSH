# SSH - Agent SSH


<br>

Objectifs :
* éviter de resaisir le password
* embarquer sa clef avec soi et ne pas la perdre en cas de rebond
* pour tout ce qui est à base de ssh : scp, sftp avec ssh...

<br>

* utilisation de la clef

```
ssh -i /localisation/clef/privee Saliou@monhost
```

ou plus facilement par un agent ssh (embarque votre configuration ssh)

<br>

* check si un agent tourne

```
ps -p $SSH_AGENT_PID
```

<br>

* lancement d'un agent ssh

```
eval `ssh-agent`
```

---------------------------------------------------------------------------

# SSH - Agent SSH


<br>

* ajout de la clef à l'agent (par défaut)

```
ssh-add
```

<br>

* ajout de plusieurs clef

```
ssh-add ~/.ssh/titi
ssh-add ~/.ssh/toto
```


<br>

* check de la clef de l'agent

```
ssh-add -l
```

---------------------------------------------------------------------------

# SSH - Agent SSH


<br>

* supprimer une clef de son agent

```
ssh-add -d ~/.ssh/titi
```

ou toutes les clefs

```
ssh-add -D
```

<br>

* clef de vérouillage de l'agent

```
ssh-add -x
```

* pour déverouiller toutes les clefs de l'agent

```
ssh-add -X
```

<br>

* durée d'une vie seconde d'une clef embarquée par l'agent

```
ssh-add -t 120 ~/.ssh/titi
```

