"# PetitProjet" 
Projet pour savoir se servir de GitHub

Note
=======
_git init_ ou _git clone_ cree un repertoire LA où on est, apres faut sauter dedans 
pour le reste des commandes
On a donc un .git a cote du repertoire, et un autre dedans

Ajouter des trucs sans faire de branche
=======================================

On fait des modifs ds un fichier
    \>git status _pour voir où on en est : les fichiers en rouge n'ont pas été ajoutés_

    \>add monfichier (ou add * pour tous, paf)
    	>git status _les fichiers en vert ont ete ajoutés, faut les commiter_
    \>add commit -m "jai fait des modifs" _c'est toujours pas la-bas_
    \>git push origin master

Ayé c'est ajouté la-bas !
Remarque : quand je dis "ajouter", c'est les modifs. Ce peut être la suppression d'un fichier...

Si on refait des modifs apres un commit on peut recommiter avant de pusher ? 
Oui mais il faut d'abord RE-ajouter les modifs

NE JAMAIS FAIRE `git commit -a`  !!! Ca ouvre un editeur à la con dont je ne sais pas sortir !!


Ajouter des trucs en faisant une branche
========================================


Récupérer un projet existant
============================
    git fork http://urlDuprojet     _indique qu'on va faire une copie_
    git clone http//urlDuprojet la-bas _ca fait la copie effectivement_
	
A priori, fork et pull request sont liés : c'est pour pouvoir envoyer les modifs la-bas apres.
https://help.github.com/articles/fork-a-repo/

Pull request : "Est-ce que je peux rajouter des trucs chez toi ?" (un peu idiot kan on est tout seul...)

C'est la qu'on va bosser sur une branche en fait ??