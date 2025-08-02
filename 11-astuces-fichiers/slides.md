# SSH - Astuces fichiers et répertoires


<br>

* monter un répertoire vide

```
sshfs /tmp/Saliou 172.17.0.2:/tmp/
```

* diff entre un fichier distant et un local

```
ssh 172.17.0.2 cat /tmp/Saliou | diff /tmp/Saliou/test -
```

* copie de répertoires entre 2 machines

```
ssh 172.17.0.2 "cd /tmp/ && tar -cf - ." | ssh 172.17.0.3 "cd /tmp && tar -xf -"
```

* gros fichier = risque de déconnexion

```
rsync –partial –progress –rsh=ssh $file_source $user@$host:$destination_file
```

* si vous n'avez pas ssh-copy-id

```
cat ~/.ssh/id_rsa.pub | ssh user@machine "mkdir ~/.ssh; cat >> ~/.ssh/authorized_keys"
```

* test du débit

```
yes | pv | ssh 172.17.0.2 "cat > /dev/null"
```
