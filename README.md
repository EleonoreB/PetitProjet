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
		>git status 						// pour voir où on en est : les fichiers en rouge n'ont pas été ajoutés
    >git add monfichier (ou add * pour tous, paf)
    	>git status 						// les fichiers en vert ont ete ajoutés, il faut les commiter
    >git commit -m "jai fait des modifs" 	// c'est toujours pas la-bas
    >git push origin master					// Ayé c'est ajouté la-bas !
	
Remarque : quand je dis "ajouter", c'est les modifs. Ce peut être la suppression d'un fichier...

Si on refait des modifs apres un commit on peut recommiter avant de pusher ? 
Oui mais il faut d'abord RE-ajouter les modifs

NE JAMAIS FAIRE `git commit -a`  !!! Ca ouvre un editeur à la con dont je ne sais pas sortir !!


Récupérer un projet existant
============================
    git clone http//urlDuprojet la-bas _ca fait la copie effectivement_

Un truc rigolo, c'est qu'on peut cloner un projet pas distant. Par exemple avec cette arbo

    MesProjets
		PetitProjet
		Deux

Si dans *Deux* je fais `git init` puis `git clone ..\PetitProjet`, ca copie et j'obtiens

    MesProjets
        PetitProjet
        Deux
            PetitProjet // avec tout le contenu...
   
Bon par contre si on met des trucs dans PEtitProjet, je suis pas au courant
1. Entrons dans Deux\PetitProjet et faisons
    git remote -v
    git remote add upstream ..\..\PetitProjet // attention, deux .. à présent (ou chemin complet)
    git remote -v			// on s'est rajouté une reference
A présent, j'écoute

2. Modifions des trucs dans PetitProjet, addons, committons (pas de push puisque ce serait pour le serveur)

3. 
    git fetch upstream 		// les modifs sont recupérées, mais mises de cote (pour pas ecraser nos propres modifs...)
    git checkout master  	// apparemment inutile / je pense que c'est pour les branches
    git merge upstream/master

Soit on n'avais pas fait de modifs et on met a jour, soit on avait fait des modifs, 
et on va tenter un merge. Attention, quand je parle de modifs *commitées*. Si on committe pas,
tout est perdu je pense





	
    git fork http://urlDuprojet     _indique qu'on va faire une copie_
A priori, fork et pull request sont liés : c'est pour pouvoir envoyer les modifs la-bas apres.
https://help.github.com/articles/fork-a-repo/

Pull request : "Est-ce que je peux rajouter des trucs chez toi ?" (un peu idiot kan on est tout seul...)

C'est la qu'on va bosser sur une branche en fait ??