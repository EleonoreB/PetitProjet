Cahier des charges messagerie

La messagerie est le premier outil du Dashboard d'un utilisateur enregistré (V1 : artists seulement)
=>prevoir DashboardBundle
MessengerControler
rappel : bundler et Entities sont generes a la demande (avec tous les repertoires kil faut) par symfony...

Page de messagerie accessible soit
- via le lien @ d'un profil (personne destinataire du message)
- via le menu de mon profil, en mode connecté (sous Notifications)

Messages ranges en conversations par utilisateur. 
=>Conversations ou Dialogues ou echanges, discussion, causerie, entretien
Remarque : l'Entité Message ayant deja été créée pour faire une copie des mails envoyés par les visiteurs, il faudrait pour 
éviter toute confusion utiliser un autre nom d'entité : Avis, Pensée, Depeche, Parole, propos, flash (plutot pour le chat) ?
=> Parole rangé en Dialogue

Future feature : conversations à plusieurs (ex membres d'un ensemble etc) ?

Ligne 1 : menu du Dashboard

Ligne 2 :
Distinction utilisateur enregistré (subscribers : artist only en V1) et non enregistré (visitor), avec indicateur du
nombre de messages non lus (pour les visiteurs, on utilise la copie des mails envoyés (entité Message)


Ligne 3 : pagination des conversations et bouton new message (pour envoyer un message à un nouveau correspondant -ou un ancien)

Le reste de l'écran : 1/3 liste des conversations 2/3 conversation courante

Liste des conversations
Avant le premier : champ de recherche de personne avec autocompletion cf header site+filtre "artists only")
Photo (indicateur connected if relevant) / name+instrument / Date+hour(si >1month) / puce unread messages if relevant
trois couleurs de fond : selected (first by default), listed, hover
Sous la date/heure, une croix permet de supprimer toute la conversation (à mon avis c'est pas clair, 
il faudrait une grosse poubelle, et une explication  en tooltop)
Nombre de correspondants par page : à mettre en parametre. Pas trop pour ne pas avoir à scroller (pagination : page=5)
Le nb de messages non lus est mis a zero des l'affichage de la conversation en question

Conversations courante : afficher les X derniers messages, permettre le chargement des plus anciens avec fleche
Scrollbar pour ne page depasser la taille de l'ecran (scroller vers le message le plus récent)
Pour chaque message: 
Sender - Date 
a droite : poubelle permet de supprimer le message (précisement : l'occurence dans CETTE conversation. 
Elle existe toujours chez mon correspondant. Idem en ce qui concerne la suppression d'une conversation (cad de tous les messages d'une conversation)
contenu du message
En bas : nouveau message, bouton send. En V2 possibilité d'ajouter une piece jointe
action : si visiteur : envoi de mail (et enregistrement du Message)
	si register : enregistrement du xxx
	
Remarque : pour toutes les actions de suppression, pas de reelle suppression mais un tag boolean

