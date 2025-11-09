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

## Exercice 3 :

Pour cet exercice, j’ai créé un fichier secret.txt dans le dossier Documents. J’ai affiché les permissions des fichiers avec ls -l et j’ai remarqué que secret.txt était accessible en lecture et écriture pour tous. J’ai donc modifié ses permissions avec chmod 600 secret.txt pour que seul mon utilisateur puisse lire et écrire dans ce fichier.

<img src="/Linux-poste-client/linuxscreen/Ex3 - débutant .png">

## Exercice 1 Inter :

Pour cet exercice, j’ai utilisé htop, une interface interactive en ligne de commande qui permet de visualiser et gérer les processus en cours d’exécution.

<img src="/Linux-poste-client/linuxscreen/Doc3 - inter 1.png">

Grâce à htop, j’ai pu afficher la liste complète des processus et trier les colonnes pour identifier celui qui utilisait le plus de RAM.

<img src="/Linux-poste-client/linuxscreen/Doc3 - inter 2.png">

Une fois le processus identifié, j’ai utilisé la fonctionnalité nice dans htop pour modifier sa priorité, ce qui m’a permis d’ajuster la façon dont le système alloue les ressources CPU à ce processus.

<img src="/Linux-poste-client/linuxscreen/Doc3 - inter 3.png">

Enfin, pour terminer j’ai sélectionné son PID et utilisé la commande de fin de processus directement depuis l’interface. Cette approche m’a permis d’effectuer toutes les manipulations de manière visuelle et sécurisée, sans avoir besoin de mémoriser les PID ou les commandes exactes en ligne de commande.

## Exercice 2 Inter :

Pour cet exercice, j’ai commencé par créer un dossier backups dans mon répertoire personnel afin d’y stocker mes sauvegardes. Ensuite, j’ai utilisé la commande tar avec les options -czf pour créer une archive compressée du dossier Documents. J’ai nommé cette archive backup suivie de la date du jour, grâce à la commande $(date +%Y%m%d) intégrée dans le nom du fichier, ce qui permet d’avoir une sauvegarde datée automatiquement. Une fois la commande exécutée, j’ai vérifié dans le dossier backups que le fichier backup 20251008.tar.gz avait bien été créé, confirmant que la sauvegarde avait été réalisée avec succès.

<img src="/Linux-poste-client/linuxscreen/ex 2 inter 1.png">

Aprés ça, j’ai commencé par créer un script nommé backup.sh dans mon répertoire personnel, à l’aide de la commande touch. J’ai ensuite ouvert ce script avec nano afin d’y écrire les instructions nécessaires pour automatiser la sauvegarde de mes fichiers. Une fois le script rédigé, j’ai rendu ce fichier exécutable avec la commande chmod +x /home/mathis/backup.sh.

Ensuite, j’ai configuré une tâche planifiée avec crontab pour que ce script s’exécute automatiquement à une heure précise chaque jour. Pour cela, j’ai ouvert l’éditeur de crontab avec crontab -e, choisi nano comme éditeur par défaut, puis ajouté la ligne : 0 2 \* \* \* /home/mathis/backup.sh

Cette ligne indique que le script backup.sh sera exécuté tous les jours à 2h du matin, ce qui permet d’effectuer des sauvegardes automatiques de manière régulière sans intervention manuelle. Enfin, j’ai vérifié la bonne prise en compte de la tâche avec la commande crontab -l.

<img src="/Linux-poste-client/linuxscreen/ex 2 inter 2.png">

## Exercice 3 Inter :

Pour sauvegarder les résultats dans un fichier :

    journalctl -u ssh --since "24 hours ago" | grep "Failed" > sshd_failed_logins.txt

Ou avec les fichiers de logs :

    grep "Failed password" /var/log/auth.log > sshd_failed_logins.txt

Avec journalctl

    journalctl -u sshd --since "24 hours ago" | grep -E "Failed password|Invalid user" > sshd_failed_logins.txt

Avec auth.log

    grep -E "Failed password|Invalid user" /var/log/auth.log | grep "$(date -d '24 hours ago' '+%b %d')" > sshd_failed_logins.txt

Pour vérifier le contenu du fichier créé :

    cat sshd_failed_logins.txt

Ou pour compter le nombre de tentatives échouées :

    wc -l sshd_failed_logins.txt
