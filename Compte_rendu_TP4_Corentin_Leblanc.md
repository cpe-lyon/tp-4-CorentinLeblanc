**Compte rendu TP 4 --Gestion des paquets**

**<ins>Exercice 1. Commandes de base</ins>**

1 -- Pour mettre a jour le système je me suis servis des commandes "sudo apt update" puis "sudo apt upgrade".
![image](https://user-images.githubusercontent.com/104362418/192204814-3eb2a78d-8b09-4fff-8891-76c723410413.png)
![image](https://user-images.githubusercontent.com/104362418/192205618-30d0941c-f5d8-4ee7-ab51-c73038a0e845.png)

2 -- J'ai donc créée un alias nommé **"maj"** à partir des commandes précédentes. Pour que notre alias ne soit pas perdu au prochain redémarrage, il faut modifier le fichier **"bashrc"**.

![image](https://user-images.githubusercontent.com/104362418/192207272-4a793944-8389-4f5c-a234-9e510bc81cc5.png)

Le **";"** sert à faire d'abord la première commande puis la deuxième.

3 -- En faisant un **"cat"** du fichier **"/var/log/dpkg.log"** pour obtenir les 5 derniers paquets installés sur ma machine.

![image](https://user-images.githubusercontent.com/104362418/192208194-0c6ebe9b-0d53-41fb-9d2f-e6f2ed4bac9b.png)

On retrouve bien les 5 derniers paquets installés sur ma machine grâce au ligne **"status installed nom_du_paquet"**.
On peut également utiliser la commande "**grep " installed" /var/log/dpkg.log | tail -5 |cut -d' ' -f5 | cut -d: -f1**".

4 -- Les 5 derniers paquets installés avec la commandes **"apt install"** sont : 

![image](https://user-images.githubusercontent.com/104362418/192210064-f0905357-0a99-4fba-a02b-1249edbd7777.png)

Je suis arrivé à ce résultat en faisant un "cat" du fichier nommé **"/var/log/apt/history.log"**.
On peut également utiliser la commande "**grep "apt install" /var/log/apt/history.log | cut -d" " -f4**".

5 -- Voici les deux commandes dont je me suis servi pour compter le nombre total de paquets installés sur la machine:

![image](https://user-images.githubusercontent.com/104362418/192212088-c7a09872-2f6a-4bbc-a8a5-18a2a79fc58a.png)

La petite différence s’explique seulement par les quelques lignes de texte informatif affichées par apt list
On ne peut pas se contenter d’utiliser dpkg.log car il est vraisemblablement incomplet :
les lignes les plus anciennes de ce fichier sont régulièrement archivées.

6 -- Il y a 68953 paquets disponibles en téléchargement sur les dépôts Ubuntu :

![image](https://user-images.githubusercontent.com/104362418/192219065-1c421b56-5e94-4996-a25d-c55f15440c3b.png)

On peut utiliser la commande "**apt list | wc -l**".

7 -- Les paquets **"glances"**,**"tldr"** et **"hollywood"** servent à afficher l'état des principales ressources d'un système, de sa charge et du fonctionnement des applications. "Hollywood" simule une interface de hacker mais ne sert à rien. Je n'ai pas réussi à faire fonctionner **"tldr"**.

8 -- Le paquet **"sudoku"** permet de jouer au sudoku. J'ai pu l'installé grâce a **"sudo apt install sudoku"**.

![image](https://user-images.githubusercontent.com/104362418/192221478-48546e9d-69ed-4a8c-8837-43de406dcf63.png)

**<ins>Exercice 2.</ins>**

La commande ls est installée à partir de la commande GNU Core Utilities. On peut obtenir cette information grâce à la commande **"dpkg -S $(which -a ls)"**.

![image](https://user-images.githubusercontent.com/104362418/192242675-be5090ca-61e8-4569-918b-616b49f56871.png)

On retrouve donc bien le nom du package au début de la ligne, ici coreutils.

![image](https://user-images.githubusercontent.com/104362418/192245919-d1ad43d8-b4a3-4827-877c-d8482f6cbba2.png)

La commande pour obtenir a partir de quel paquet est installé la commande ls est "**which ls | xargs dpkg -S**".

![image](https://user-images.githubusercontent.com/104362418/192243696-ee2ec8bc-adf0-40ab-86ee-c3a609b0a643.png)

**<ins>Exercice 3.</ins>**

Voici la commande que j'ai utilisé pour arrivé à savoir si un package est installé ou non.

![image](https://user-images.githubusercontent.com/104362418/192952729-1f92fd08-78dc-4e47-b1e2-7a73dad057a6.png)

Le "grep "^i" sert a vérifier le commentaire qui apparaît en résultat de la commande, il y ici deux i si le programme est présent sinon il n'est pas installé.
On aurait pu aussi se servir de cette commande "**(dpkg -l "nomdupackage" | grep "^ii" > dev/null) && echo "installé" || echo "non installé"**".

**<ins>Exercice 4.</ins>**

Voici la liste des programmes qui sont livrés avec le package coreutils. 
J'ai utilisé la commande **"apt show coreutils"**:

![image](https://user-images.githubusercontent.com/104362418/192953482-850fa3d9-4d6b-441b-bc79-f18bf76663f9.png)

On peut se servir de la commande "**dpkg -L coreutils**".
Il s'agit d'un alias pour la commande test

**<ins>Exercice 5.</ins>**

Voici l'interface ou j'ai pu installer les packages demandés.

![image](https://user-images.githubusercontent.com/104362418/192954637-d2c7218b-301e-4b76-bf28-b5e3da3c8079.png)

Emacs est un éditeur de texte puissant qui sert pour beaucoup de langages. Il peut également servir de navigateur internet, de client mail.

![image](https://user-images.githubusercontent.com/104362418/192722341-d64689f7-9dff-4f5b-a02a-8aa7f9119642.png)

Lynx quand à lui est un navigateur web uniquement en mode texte utilisable via une console ou un terminal. Toutes la navigations se fait au clavier avec les différents éléments que peuvent avoir une page web(exemple : les liens hypertextes sont d'une couleur bien visible). Il est très utilisé en tant que navigateur adapté aux déficiences visuelles car il est facile d'utilisation et dispose même d'un synthétiseur vocal.

Procédé pour installez emacs via aptitude :

Lancer aptitude : aptitude

chercher le paquet emacs en tapant /^emacs$

Marquer le paquet pour installation avec +, puis procéder à l’installation en tapant deux fois
sur g

**<ins>Exercice 6.</ins>**

1 -- J'ai donc commencé par réalisé toutes les commandes données dans la question 1. PPA -> Personal Package Archives(Utilisé lorsque certains logiciels ne figurent pas dans les dépôts officiels).

![image](https://user-images.githubusercontent.com/104362418/192724431-91b84d9c-c48e-4a8e-bfa2-05e7a1d65e23.png)

Vu qu'il n'existe pas de dépôts officiels de Java par Oracle, on ne trouve pas le package lorsque l'on souhaite l'installer.

![image](https://user-images.githubusercontent.com/104362418/192724751-b88d1086-af19-4732-aebe-d6c6d900a302.png)

2 -- Un nouveau dossier nommé "source.list.d" à bien été créé. 
     Voici son contenu : 

![image](https://user-images.githubusercontent.com/104362418/192725332-58f274d8-ce8d-4258-a525-cb5431080d37.png)

Il contient un fichier avec l'extension **".list"** qui lui même contient l'adresse de notre dépot personnel ou PPA.

**<ins>Exercice 7.</ins>**

1 -- J'ai donc cloner le dépot git demandé

![image](https://user-images.githubusercontent.com/104362418/192726110-1e062991-033c-4567-9296-6a38d790e4f5.png)

2 -- J'ai par la suite installer le package **"make"** pour pouvoir éxecuter le Makefile présent après le clône du dépot git. J'ai installé les paquets manquants puis procéder à l'installation en local avec la commande "make install PREFIX=~/.local. Je peux donc désormais admirer un jolie bonsai pour me détendre lorsque le TP devient trop complexe.

![image](https://user-images.githubusercontent.com/104362418/192730316-4ade22e5-f6a7-4d9e-b896-63aa382c7c67.png)

4 -- J'ai donc recommencé la compilation à l''aide de la commande checkinstall :

![image](https://user-images.githubusercontent.com/104362418/192732530-1e4db842-6612-4f15-9d71-94ee08f67605.png)

Il y a bien un paquet en extension **".deb"** qui à été créé et je peux également éxecuté un bonsai depuis n'importe quel endroit.

![image](https://user-images.githubusercontent.com/104362418/192732947-4de278d4-9d3e-4965-92f6-ece636a1cf89.png)

**<ins>Exercice 8.</ins>**

Création d'un paquet Debian avec dpkg-deb

1 -- J'ai commencé par créer plusieurs sous-dossiers comme demandé dans la question et ensuite j'ai copié le script réalisée à l'exercice 2 dans le repértoire /usr/local/bin grâce à la commande **"cp"**.

2 -- J'ai ensuite créé un fichier **"control"** grâce à la commande **"touch"**.

3 -- Il a fallu que j'enlève les commentaires pour que la commande réussisse

![image](https://user-images.githubusercontent.com/104362418/192963904-a2772dff-d192-4bbf-9995-952ca0e03482.png)

Création du dépôt personnel avec reprepro

1 -- La création du dossier **"repo-cpe"** c'est faite avec mkdir

2 -- Même chose que la question précédente pour la création de sous-dossiers

3 -- J'ai bien créé le fichier distributions dans le fichier conf grâce à **"touch"** puis **"nano"** pour le modifier.

4 -- Voici l'exécution de la commande

![image](https://user-images.githubusercontent.com/104362418/192966707-c8333ecb-09ac-42fc-ac74-d184b9ff813a.png)

5 -- Voici la copie demandé et l'exécution de la commande suivante :

![image](https://user-images.githubusercontent.com/104362418/192982208-3850aa1c-be83-46a9-b404-f6b7a25fe689.png)

![image](https://user-images.githubusercontent.com/104362418/192982277-f0915c7a-178b-4fa6-9857-bc6d2f99cc8f.png)

6 -- J'ai créer une fichier dans le dossier **"/etc/apt/sources.list.d"**, puis renseigné la commande demandé.

![image](https://user-images.githubusercontent.com/104362418/192983285-8bfa2273-3203-4906-838d-ecd6c3e4515e.png)

7 -- Une erreur ressort en effet, ce n'est pas signé.

![image](https://user-images.githubusercontent.com/104362418/192983949-9aa3b6d1-1716-4f05-88e4-5a38637f0f3f.png)

Signature du dépôt avec GPG

1 -- J'ai effectué la commande demandé, il a fallu que je renseigne mon nom d'utilisateur,mon email et ma passphrase.

2 -- J'ai rajouté la ligne demandé au fichier distribution. 

![image](https://user-images.githubusercontent.com/104362418/192986110-55d3325f-3004-4bea-964f-19d4e371c71a.png)

3 -- Puis j'ai ajouté la clé a mon dépôt, cette méthode n'est pas sécurisée et obsolète. En entreprise on utiliserait gpg-agent.

![image](https://user-images.githubusercontent.com/104362418/192986561-e8cb679f-cc08-4ac4-ab5f-100ee7931d35.png)

On m'a demandé de renseigné ma passphrase et cela à fonctionné.

4 -- 
![image](https://user-images.githubusercontent.com/104362418/192987810-30de862f-275f-4688-b1b8-a63a4fa02060.png)

5 -- 
![image](https://user-images.githubusercontent.com/104362418/192988032-717c5a11-212e-4531-bece-eac5038d997c.png)



