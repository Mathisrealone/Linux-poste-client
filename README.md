# Linux Exercice

## Exercice 1 :

Pour ce premier exercice, j’ai créé un dossier appelé files puis je me suis déplacé à l’intérieur. J’y ai créé trois fichiers : fichier1.txt, fichier2.txt et .fichier3.txt (ce dernier étant caché car son nom commence par un point). Quand j’ai affiché le contenu du dossier avec la commande ls, seuls les deux premiers fichiers sont apparus. Ensuite, je suis revenu dans mon répertoire personnel et j’ai copié fichier1.txt sous un nouveau nom modifichier.txt.

<img src="/Linux-poste-client/linuxscreen/Ex1 -débutant.png">

## Exercice 2 :

Pour ce deuxième exercice, je me suis déplacé dans le dossier Documents. Comme il était vide, j’y ai créé un fichier log.txt. Ensuite, j’ai redirigé la liste du contenu du dossier /etc dans ce fichier grâce à la commande ls /etc > log.txt. Enfin, j’ai ouvert log.txt avec l’éditeur nano pour consulter ou modifier son contenu.

<img src="/Linux-poste-client/linuxscreen/Ex2 -débutant.png">

Ensuite, j’ai utilisé la commande tail -n 10 /var/log/syslog afin d’afficher les dix dernières lignes du fichier syslog. J’ai ensuite essayé de les ajouter directement à /var/log/syslog, mais j’ai eu une erreur de permission. Finalement, j’ai redirigé ces dix lignes vers mon fichier log.txt dans le dossier Documents.

<img src="/Linux-poste-client/linuxscreen/Ex2 - débutant (2).png">

Et pour finir, j’ai utilisé la commande grep 'error' /var/log/syslog afin de rechercher toutes les lignes contenant le mot error dans le fichier de log système syslog.

<img src="/Linux-poste-client/linuxscreen/Ex2 - débutant (3).png">
