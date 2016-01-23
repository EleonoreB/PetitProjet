"# PetitProjet" 
Projet pour savoir se servir de GitHub

Note
=======
git init ou git clone cree un repertoire LA où on est, apres faut sauter dedans 
pour le reste des commandes
On a donc un .git a cote du repertoire, et un autre dedans

Ajouter des trucs sans faire de branche
=======================================

On fait des modifs ds un fichier
>git status pour voir où on en est : les fichiers en rouge n'ont pas été ajoutés

>add monfichier (ou add * pour tous, paf)
	>git status : les fichiers en vert ont ete ajoutés, faut les commiter
>add commit -m "jai fait des modifs"
>git push origin master

Ayé c'est ajouté la-bas
