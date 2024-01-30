# SSH Z is sleeping

## Etape à suivre

* Tout d'abord, allez dans ce site pour *telecharger* un fichier utile pour ce defi : [debian-openssl](https://hdm.io/tools/debian-openssl/?fbclid=IwAR3MECf0l_Ss03PgyrdGMMXsKVTa-L55vjsvtY9yDgCAAIfA1lgrRY7_B04) et après, télécharger ce fichier appelé `SSH 2048-bit RSA Keys X86 (48.0M)`
* Après téléchargement, il faut **extracter** ce fichier

* Maintenant, allez dans le chemins de ce challenge `rantoo@warchall:/home/level/08_sshz$` en utilisant ces commandes qui génère la "fingerprint" (empreinte) MD5 de la clé publique SSH stockée dans le fichier `ssh-keygen -l -E md5 -f /home/level/08_sshz/backups/authorized_keys.backup`

* `ssh-keygen`: C'est la commande principale pour la gestion des clés SSH.
* `-l`: Cette option est utilisée pour montrer la longueur de la clé, le nombre de bits dans la clé. Cela affiche la longueur de la clé en bits.
* `-E md5`: Cette option spécifie l'algorithme de hachage utilisé pour afficher la "fingerprint" (empreinte) de la clé. Dans ce cas, l'algorithme MD5 est utilisé pour générer la *fingerprint*.
* `/home/level/08_sshz/backups/authorized_keys.backup` : affiche l'empreinte et cela peut être utile pour vérifier l'authenticité d'une clé ou pour des raisons de sécurité lors de la gestion des clés SSH.

````sh
rantoo@warchall:/home/level/08_sshz$ ssh-keygen -l -E md5 -f /home/level/08_sshz/backups/authorized_keys.backup

````
* sortie : `2048 MD5:2b:cd:07:a7:01:e9:4a:04:74:d7:7e:e4:d6:d0:f8:06 no comment (RSA)`.

** Donc, on le fingerprint mais il faut enlever tout les `:` 
* resultat obtenu: `2bcd07a701e94a0474d77ee4d6d0f806`
* Après, Essayer de chercher ce fichier `2bcd07a701e94a0474d77ee4d6d0f806` dans le fichier que nous allons télécharger.


### ouvrir le terminal PowerShell 
* Mais tout d'abord, il faut passer cet scripts `scp -P (port_ssh) `et guider vers le fichier *cible* `2bcd07a701e94a0474d77ee4d6d0f806` [On peut utiliser Tab] en mettant à la fin `user@warchall.net:~/`.
* A mon cas, 

````sh
PS C:\Users\Ranto> scp -P 19198 C:\Users\Ranto\Downloads\Compressed\debian_ssh_rsa_2048_x86\rsa\2048\2bcd07a701e94a0474d77ee4d6d0f806-23669 rantoo@warchall.net:~/

````

Ensuite, taper le mot de passe warchall ou "ssh_password" .
````sh
rantoo@warchall.net's password:
2bcd07a701e94a0474d77ee4d6d0f806-23669                                                              100% 1671     5.1KB/s   00:00

````

* Maintenant, ouvrir le repertoire personnel dans le terminal warchall.
* Et normalement le fichier `2bcd07a701e94a0474d77ee4d6d0f806` devrait être là après `ls`

* il faut donner la permission en ce fichier avec `chmod 600` (*avoir l'accès à le lire*) et le l'exécute avec le commande `ssh -i`.

````sh
rantoo@warchall:~$ chmod 600 2bcd07a701e94a0474d77ee4d6d0f806-23669

````
Enfin, 
* Ces commande SSH tente de se connecter au serveur distant warchall.net en tant qu'utilisateur `level08`, en utilisant la clé privée spécifiée `2bcd07a701e94a0474d77ee4d6d0f806-23669` pour l'authentification, et en se connectant sur le port SSH spécifié `19198`
  
````sh
rantoo@warchall:~$ ssh -i ~/2bcd07a701e94a0474d77ee4d6d0f806-23669 level08@warchall.net -p 19198
PrivateKeysAreGold
Connection to warchall.net closed.

````
The Passkey of this level is : **PrivateKeysAreGold**

