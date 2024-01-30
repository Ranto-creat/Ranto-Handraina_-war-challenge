# 13_tryouts

## Etape 1 
* Créer un fichier `cat.c` dans le repertoire personnel
* Mettre ces codes à l'interieur de ce fichier

`cat.c`
````sh  
#include <stdio.h>
#include <unistd.h>
#include <string.h>
int main(int argc, char *argv[]) {
    FILE *fp = fopen(argv[1], "w");
    char buf[16];
    memset(buf, 0, sizeof buf);
    lseek(3, 0, SEEK_SET);
    read(3, buf, sizeof buf);
    fprintf(fp, "%s", buf);
    return 0;
}
````
* Le but de ce code est de lire les 16 premiers octets du descripteur de fichier numéro 3 (`lseek(3, 0, SEEK_SET); read(3, buf, sizeof buf);`) et d'écrire ces données dans un fichier spécifié en ligne de commande (`FILE *fp = fopen(argv[1], "w"); fprintf(fp, "%s", buf);`).


## Etape 2 
* Toujours dans le repertoire personnel
1. Exécuter le commande `gcc -m32 cat.c -o cat`

* `gcc`: C'est le compilateur GNU pour les langages de programmation comme le C, le C++, etc.

* `-m32`: Cet indicateur spécifie à GCC de générer un code pour une architecture 32 bits. En d'autres termes, cela indique au compilateur de produire un exécutable qui est compatible avec une architecture de 32 bits.

* `cat.c`: C'est le fichier source C à compiler.

* `-o cat`: Cet indicateur spécifie le nom de l'exécutable de sortie. L'exécutable généré sera appelé `cat`. Vous pouvez changer le nom du fichier exécutable en modifiant le paramètre qui suit l'option `-o`.


````sh
rantoo@warchall:~$ gcc -m32 cat.c -o cat

````

2. Ensuite, on exécute ces commandes `PATH=$HOME:$PATH`


* `PATH` est une variable d'environnement qui spécifie les répertoires dans lesquels le système d'exploitation recherche les exécutables (programmes) lorsque vous saisissez une commande dans le terminal.

* `$HOME` est une variable d'environnement qui représente le répertoire personnel de l'utilisateur.

* La commande `PATH=$HOME:$PATH` ajoute le répertoire personnel de l'utilisateur (`$HOME`) au début de la liste des répertoires spécifiés dans la variable `PATH`. 
* Le `:` est un séparateur utilisé dans la variable PATH pour séparer différents répertoires.

=> **En ajoutant `$HOME` au début de `PATH`, vous indiquez au système d'exploitation de rechercher d'abord les exécutables dans le répertoire personnel de l'utilisateur, puis dans les autres répertoires spécifiés dans `PATH`.**

* En résumé, `PATH=$HOME:$PATH` ajoute le répertoire personnel de l'utilisateur au début de la variable `PATH`, facilitant l'exécution des programmes situés dans le répertoire.

````sh
rantoo@warchall:~$ PATH=$HOME:$PATH

````
## Etape 3 
Allez dans le **repertoire de challenge actuel** et exécuter `tryouts` avec la commande `./tryouts` 
 ````sh
 rantoo@warchall:/home/level/matrixman/13_tryouts$ ./tryouts

Enter your guess:                   ???

 ````
Il dit *Enter your guess* et maintenant nous pouvons utiliser `export PATH=$PATH` vient de commande `PATH=$HOME:$PATH` précédente, pour l'exporter vers `/home/user/utilisateur/seed`

````sh
rantoo@warchall:/home/level/matrixman/13_tryouts$ ./tryouts

Enter your guess: export PATH=$PATH

````

## Etape 4 

Enfin, il faut regarder tout simplement si ça passe, en exécutant `nano /home/user/rantoo/seed`

````sh
rantoo@warchall:~$ nano /home/user/rantoo/seed


`EveryDayShuffle4`

````
The passkey is : EveryDayShuffle4
