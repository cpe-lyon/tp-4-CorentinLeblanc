**Compte rendu TP 4 --Gestion des paquets**

Exercice 1. Commandes de base

1 -- Pour mettre a jour le système je me suis servis des commandes "sudo apt update" puis "sudo apt upgrade".
![image](https://user-images.githubusercontent.com/104362418/192204814-3eb2a78d-8b09-4fff-8891-76c723410413.png)
![image](https://user-images.githubusercontent.com/104362418/192205618-30d0941c-f5d8-4ee7-ab51-c73038a0e845.png)

2 -- J'ai donc créée un alias nommé "maj" à partir des commandes précédentes. Pour que notre alias ne soit pas perdu au prochain redémarrage, il faut modifier le fichier "bashrc".

![image](https://user-images.githubusercontent.com/104362418/192207272-4a793944-8389-4f5c-a234-9e510bc81cc5.png)

Le ";" sert à faire d'abord la première commande puis la deuxième.

3 -- En faisant un "cat" du fichier "/var/log/dpkg.log" pour obtenir les 5 derniers paquets installés sur ma machine.

![image](https://user-images.githubusercontent.com/104362418/192208194-0c6ebe9b-0d53-41fb-9d2f-e6f2ed4bac9b.png)

On retrouve bien les 5 derniers paquets installés sur ma machine grâce au ligne "status installed nom_du_paquet"

4 -- Les 5 derniers paquets installés avec la commandes "apt install" sont : 

![image](https://user-images.githubusercontent.com/104362418/192210064-f0905357-0a99-4fba-a02b-1249edbd7777.png)

Je suis arrivé à ce résultat en faisant un "cat" du fichier nommé "/var/log/apt/history.log".

5 -- Voici les deux commandes dont je me suis servi pour compter le nombre total de paquets installés sur la machine:

![image](https://user-images.githubusercontent.com/104362418/192212088-c7a09872-2f6a-4bbc-a8a5-18a2a79fc58a.png)

La légère différence s'explique par la fait que dpkg ne s'occupe pas des dépendances. Par conséquent, la première commande affiche les dépendances, pas la deuxième. On ne peut pas utiliser le fichier "dpkg.log" car ils listent tout l'historique et pas seulement les paquets installés.

6 -- Il y a 68953 paquets disponibles en téléchargement sur les dépôts Ubuntu :

![image](https://user-images.githubusercontent.com/104362418/192219065-1c421b56-5e94-4996-a25d-c55f15440c3b.png)

7 -- Les paquets "glances","tldr" et "hollywood" servent à afficher l'état des principales ressources d'un système, de sa charge et du fonctionnement des applications. "Hollywood" simule une interface de hacker mais ne sert à rien. Je n'ai pas réussi à faire fonctionner "tldr".

8 -- Le paquet "sudoku" permet de jouer au sudoku. J'ai pu l'installé grâce a "sudo apt install sudoku".

![image](https://user-images.githubusercontent.com/104362418/192221478-48546e9d-69ed-4a8c-8837-43de406dcf63.png)

Exercice 2.

La commande ls est installée à partir de la commande GNU Core Utilities. On peut obtenir cette information grâce à la commande "dpkg -S $(which -a ls)".

![image](https://user-images.githubusercontent.com/104362418/192242675-be5090ca-61e8-4569-918b-616b49f56871.png)

On retrouve donc bien le nom du package au début de la ligne, ici coreutils.

![image](https://user-images.githubusercontent.com/104362418/192245919-d1ad43d8-b4a3-4827-877c-d8482f6cbba2.png)

![image](https://user-images.githubusercontent.com/104362418/192243696-ee2ec8bc-adf0-40ab-86ee-c3a609b0a643.png)

Exercice 3.

Grâce à la commande "apt list --installed | grep nom_du_package", je peux savoir si le package est installé ou pas. 

![image](https://user-images.githubusercontent.com/104362418/192246754-a53e1571-5b95-42e3-b3be-b0bf1e5a6aa4.png)

Le package "burcado" n'est pas installé alors que "coreutils" est bien installé car on a un résultat.

