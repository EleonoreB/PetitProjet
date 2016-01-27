#Cahier des charges Messagerie

## Description générale

La messagerie est le premier outil du Dashboard d'un utilisateur enregistré 
(V1 : seuls les **artists** peuvent utiliser la messagerie)
> => prévoir Messengerbundle ET DashboardBundle

La page de messagerie accessible soit
- via le lien `@` d'un profil (personne destinataire du message)
- via le menu de mon profil, en mode connecté (sous **Notifications**)

Les messages sont rangés en conversations par utilisateur (1 utilisateur = 1 conversation, comprenant tous les messages).

### Remarque technique
 
L'Entité `Message` ayant deja été créée pour faire une copie des mails envoyés par les visiteurs, il faudrait pour 
éviter toute confusion utiliser un autre nom d'entité : Avis, Pensée, Depeche, Parole, Propos, Flash (plutot pour le chat) ?

=> Conversations ou Dialogues ou echanges, discussion, causerie, entretien

=> ou alors il faut changer l'entité `Message` en `MailMessage`. Voir avec Julien si compliqué

>*Future feature* : conversations à plusieurs (ex membres d'un ensemble etc) ?

####Je propose : 
**Propos** rangées en **Dialogues**, on garde les mots *Conversation/Discussion* pour un possible usage en conversation à plusieurs, ou pour un forum.

## Ecran d'affichage

1. Ligne 1 : menu du Dashboard, Messagerie en premier (autres : Liste d'artistes | Buddies | Forum...). 
Reprendre le look de l'admin

2. Ligne 2 :
Distinction utilisateur enregistré (*subscribers* : artist only en V1) et non enregistré (*visitor*), avec indicateur du
nombre de messages non lus (pour les visiteurs, on utilise la copie des mails envoyés (entité Message))

3. Ligne 3 : pagination des conversations  (syntaxe pagination : `page=5`) et bouton **New message** (pour envoyer un message 
à un nouveau correspondant -ou un ancien-). 

4. Le reste de l'écran : 1/3 liste des dialogues 2/3 dialogue courant

>Remarque : revoir la syntaxe de pagination : `/page/5` ou simplement `/5` serait plus approprié IMHO

##Liste des dialogues
Trois couleurs de fond : 
* selected (premier de la liste par défaut) = gris foncé, 
* listed = gris
* hover = gris pâle

####Remarque
**Nombre de correspondants par page** : à mettre en parametre extérieur (`parameters.yml`). 
Pas trop pour ne pas avoir à scroller

>Je ne suis pas certaine que le positionnement de la pagination soit optimal pour faire le lien avec la liste des correspondants : plutot en bas de la liste ?

### Cas Subscribers
Avant le premier : champ de recherche de personne avec autocompletion *(cf header site+filtre "artists only")*

Description de chaque dialogue, de gauche à droite :
* Photo (indicateur *connected* si approprié) 
* Prénom+Nom + instrument 
* Date (et heure si < 1 mois) du dernier message (1 mois = paramètre)
* puce rouge "nombre de messages non lus" si approprié

Sous la date/heure, une croix permet de supprimer tout le dialogue 
>(à mon avis cette croix c'est pas clair, il faudrait plutôt une grosse poubelle, et une explication  en tooltip)

####Remarque
Le nb de messages non lus est mis a zero dès l'affichage du dialogue en question

### Cas Visitors
Pas de champ de recherche en haut je suppose ?


##Affichage du dialogue courant
### Cas Subscribers
* Afficher les X derniers messages (X =paramètre), permettre le chargement *lazy* des plus anciens avec flèche (cf Events)
* Scrollbar pour ne pas dépasser la taille de l'ecran (scroller vers le propos le plus récent)

1. Pour chaque propos: 
  * Ligne 1 :Sender (Prénom+Nom) - Date et heure
  * Ligne, à droite : *poubelle* permet de supprimer le propos (précisement : l'occurence dans CE dialogue. Elle existe toujours chez mon correspondant. Idem en ce qui concerne la suppression d'un dialogue -cad de tous les propos d'un dialogue-)
  * Ligne 2 : contenu du propos
2. En bas : champ de texte pour la rédaction d'un nouveau propos, bouton send. En V2 possibilité d'ajouter une piece jointe.

### Cas Visitors
Récupération des copies de mails enregistrées en Message

Problématiques :
* Les items sont à récupérer dans l'entité Message, ils ne sont pas rangés par Propos/Dialogue à la création. Requete totalement différente.
* Donc a priori, pas de possiblité de suppression...
* En cas de réponse, l'entité n'est ni un message (le visiteur n'est pas l'expéditeur mais le destinataire) ni un Propos 
(on n'a pas deux utilisateurs enregistrés, sauf à créer un utilisateur provisoire). Même dans ce cas, on a une requete batarde Message/Propos. 
* Voir comment fonctionne Message : création d'un utilisateur provisoire ?

## Nouveau message
Si accès par `@` de la part d'un visiteur, ou si clic sur *New Message*, affichage de:
* champ de recherche de personne (cf en haut des dialogues)
* texte
* send

### Envoi de reponse, envoi d'un message 
Action : 
* Si visiteur écrit à un artiste :
	* fonctionnement actuel : copie dans un `Message` puis envoi de mail
	* nouveau fonctionnement : **se brancher avant** ou :
	* **modifier** ce fonctionnement pour l'intégrer dans le nouvel outil. Dans ce cas : prévoir la gestion
	des anciens `Messages`, attention à la migration éventuelle de l'entité
* si réponse au message d'un visiteur : envoi de mail (et enregistrement du truc) - prévoir 
bulle d'info expliquant le fonctionnement AVANT envoi
* si registered to registered : enregistrement du Propos et des dialogues afférents.


## Remarque générale
Pour toutes les actions de **suppression* citées, pas de réelle suppression mais un tag booléen à mettre à `false`.

