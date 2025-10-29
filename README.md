TP3 - Programmation objet 1 (Application Media Player)
======================================================

Cours : 420-W20-SF - Programmation objet 1  
Cegep de Sainte-Foy – Hiver 2025  
Travail en equipe 

---------------------------------------------------------

Objectif du projet
------------------
Ce projet consiste a developper une application console qui simule un lecteur multimedia simplifie.  
L’utilisateur peut charger des medias musicaux et videos, creer et gerer une liste de lecture, trier les titres selon differents criteres, et ecouter les medias a l’aide d’un menu interactif.  

L’objectif est de mettre en pratique la programmation oriente objet, la manipulation de listes, la gestion d’exceptions et l’ecriture de tests unitaires.  

---------------------------------------------------------

Fonctionnement general du programme
-----------------------------------

1. Demarrage du programme  
Lors du lancement, un menu principal s’affiche avec les choix suivants :
- Charger les musiques  
- Charger les videos  
- Gerer la liste de lecture  
- Quitter le programme  

Chaque choix declenche une action specifique :
- Charger les musiques : lit le fichier songs.music et charge la liste des chansons disponibles.  
- Charger les videos : lit le fichier videos.video et charge la liste des videos disponibles.  
- Gerer la liste de lecture : ouvre un sous-menu pour ajouter, retirer, trier ou lire les medias.  
- Quitter : termine proprement le programme.  

---------------------------------------------------------

2. Gestion de la liste de lecture  
Lorsque l’utilisateur choisit de gerer la liste de lecture, un deuxieme menu s’affiche avec les options suivantes :
- Afficher la liste de lecture  
- Ajouter un media  
- Retirer un media  
- Trier la liste  
- Demarrer la lecture  
- Quitter  

a) Afficher la liste de lecture  
Le programme affiche les medias presents dans la liste avec leur numero d’ordre.  
L’affichage est genere par la methode ToString de la classe Playlist.  

b) Ajouter un media  
- Le programme affiche d’abord la liste actuelle.  
- Ensuite, il affiche les medias disponibles qui ne sont pas deja dans la liste.  
- L’utilisateur saisit le numero du media qu’il souhaite ajouter.  
- Le programme ajoute ce media a la liste tout en respectant l’ordre de tri actuel.  

c) Retirer un media  
- Le programme affiche la liste actuelle.  
- L’utilisateur saisit le numero du media a retirer.  
- Si l’index est invalide, une exception de type ArgumentOutOfRangeException est levee.  
- Si le media n’existe pas dans la liste, une exception de type ArgumentException est levee.  

d) Trier la liste  
La liste peut etre triee par titre ou par annee, en ordre croissant ou decroissant.  
Le tri est effectue en utilisant un comparateur approprie, qui implemente l’interface IMediaComparer.  

---------------------------------------------------------

3. Lecture de la liste de lecture  
Lorsque l’utilisateur demarre la lecture, le programme joue le premier media selon l’ordre actuel.  
Un troisieme menu s’affiche alors, permettant de :  
- Passer au media suivant  
- Revenir au media precedent  
- Arreter la lecture  
- Quitter la lecture  

Fonctionnement detaille :
- Avant de lire un nouveau media, le programme arrete celui qui etait en cours.  
- Si la fin de la liste est atteinte et que l’utilisateur choisit suivant, la lecture recommence au premier media.  
- Si le debut est atteint et que l’utilisateur choisit precedent, la lecture revient au dernier media.  
- Si la liste est vide, une exception de type InvalidOperationException est levee.  

---------------------------------------------------------

4. Gestion des fichiers et de la lecture
Les fichiers de musique et de video sont fournis dans le dossier mediaFiles.  
Ce dossier est automatiquement copie dans le dossier bin lors de l’execution du programme.  

Pour lire un fichier, le programme utilise la classe WindowsMediaPlayer :
- L’attribut URL indique le chemin du fichier a jouer.  
- Les methodes play et stop permettent de demarrer et d’arreter la lecture.  
Le chemin d’un fichier doit suivre ce format :
mediaFiles/nomDuFichier.extension  

---------------------------------------------------------

5. Exceptions gerees
Le programme gere plusieurs types d’exceptions :
- ArgumentOutOfRangeException : index invalide lors d’un retrait.  
- ArgumentException : tentative de retirer un media absent.  
- InvalidOperationException : tentative de lecture d’une liste vide.  
- NullReferenceException : parametre non initialise.  

Chaque exception est geree pour assurer la stabilite de l’application.  

---------------------------------------------------------

6. Tests unitaires
Les tests unitaires doivent etre ecrits pour la classe Playlist.  
Les methodes suivantes doivent etre testees :
- Ajout et retrait de medias.  
- Verification des doublons avec FilterUnusedMedias.  
- Generation des exceptions appropriees.  
- Tests de tri avec differents comparateurs.  

Les methodes PlayNext, PlayPrevious, Stop, Sort et ToString ne sont pas evaluees dans les tests unitaires.  


---------------------------------------------------------

Auteur
------
Cherif Ouattara - Etudiant AEC Programmation, bases de donnees et serveurs  
Cegep de Sainte-Foy  
GitHub : https://github.com/BoOm00001  
LinkedIn : https://www.linkedin.com/in/cherif-ouattara/
