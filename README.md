"# PetitProjet" 
Projet pour savoir se servir de GitHub

Note
=======
git init ou git clone cree un repertoire LA o� on est, apres faut sauter dedans 
pour le reste des commandes
On a donc un .git a cote du repertoire, et un autre dedans

Ajouter des trucs sans faire de branche
=======================================

On fait des modifs ds un fichier
>git status pour voir o� on en est : les fichiers en rouge n'ont pas �t� ajout�s

>add monfichier (ou add * pour tous, paf)
	>git status : les fichiers en vert ont ete ajout�s, faut les commiter
>add commit -m "jai fait des modifs"
>git push origin master

Ay� c'est ajout� la-bas
