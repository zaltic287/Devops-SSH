%title: ANSIBLE
%author: Saliou


# SSH - votre config



<br>

* attention ordre de lecture de haut en bas

<br>

* exemple

```
touch ~/.ssh/config
chmod 600 ~/.ssh/config
cat ~/.ssh/config

Host * !monhost*
    User vagrant
    Port 22
    IdentityFile /myhome/.ssh/maclefprivee
    LogLevel INFO
    Compression yes
    ForwardAgent yes
    ForwardX11 yes
```

* astuce pour bypasser la conf

```
ssh -F /dev/null Saliou@monhost
```
