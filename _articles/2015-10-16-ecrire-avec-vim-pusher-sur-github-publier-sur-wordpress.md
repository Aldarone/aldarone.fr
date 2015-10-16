---
ID: 1658
post_title: >
  Écrire avec VIM, pusher sur GitHub,
  publier sur WordPress
author:
  - ""
post_date:
  - 2015-10-14 12:11:57
post_excerpt:
  - ""
layout: post
permalink:
  - ""
published: true
---
## Résumé des épisodes précédents

Depuis à peu près un an mon code s'écrit dans VIM. Un VIM avec plein de plugins, mais un VIM quand même.

Depuis j'ai installé [VIMperator](http://www.vimperator.org/vimperator/) qui permet l'utilisation de Firefox au clavier, VIM-style, je suis passé de XFCE4 à GNOME3 à [i3wm](http://i3wm.org/) et je me tâte sérieusement à installer [muttator](http://www.vimperator.org/muttator) pour Thunderbird.

Et c'est tellement confortable que je n'arrive juste plus à m'en passer. Qu'on me demande d'utiliser un SublimeText, un IntelliJ ou un Notepad++ et je me met à pester devant tant d'inefficacité.

Ça a l'air un peu prétentieux dit comme ça et je me souviens très bien de ce que je trouve agaçant chez la plupart des évangélistes VIM : Ils oublient très souvent que passer à VIM c'est un investissement conséquent.

Il faut désapprendre à peu près tout ce qu'on sait sur les éditeurs de texte, apprendre une palanquée de raccourcis clavier et supporter d'être parfaitement inefficace pendant des semaines, voire des mois.

Impossible donc de jeter la pierre à celles et ceux qui n'ont pas le temps ou l'envie de s'y mettre.

Mais bref, je suis passé à VIM et je ne peux pas revenir en arrière. Du coup l'écriture d'article dans l'éditeur WordPress je kiffais moyen et j'avais commencé à écrire mes articles dans un fichier .md, des fois synchronisé sur ownCloud, des fois posé un peu n'importe ou sur mon disque dur.

C'était un joyeux bordel et je devais toujours me coltiner le copier-coller dans WordPress. Pour corriger l'orthographe, la grammaire ou réécrire des bouts c'était soit dans l'éditeur, soit à nouveau un copier-coller sur le PC. Bref, c'était chiant.

Et puis j'ai entendu parler de [Jekyll](http://jekyllrb.com/) qui permet d'écrire son blog en markdown et de générer des fichiers HTML qui vont bien.

Sauf que Aldarone.fr c'est pas juste mon blog, c'est aussi un réseau WordPress multisite qui héberge d'autres blogs, je peux pas simplement virer WordPress pour le remplacer par Jekyll. Il aurait aussi fallu gérer la conservation des URLs et tout. Bref, c'était chiant.

## La solution

Heureusement parmi les plugins WordPress il y a à boire et à manger, j'ai donc fini par trouver mon graal : [WordPress GitHub Sync](https://wordpress.org/plugins/wp-github-sync/)

Après la création d'un dépôt dédié sur Github, l'autorisation du plugin à y accéder et à être notifié quand le dépôt change, voila tous mes articles regroupés sur [Aldarone/aldarone.fr](https://github.com/Aldarone/aldarone.fr)

À partir de maintenant il me suffit d'enregistrer un fichier ````.md```` sur la branche master avec un peu de YAML dans l'en-tête pour définir son titre et son statut de publication pour que ce dernier soit automatiquement créé dans WordPress. De même, à chaque modification depuis l'administration, WPGHS fera un commit dans le dépôt pour répercuter les changements.

Tout n'est pas parfait et à l'heure actuelle je dois encore me rendre dans l'administration pour envoyer les images et gérer les catégories, les tags et l'image d'en tête, mais je vais pas trop me plaindre non plus.

## Et qu'est-ce que ça implique ?

Déjà, écrire son blog dans un dépôt Git c'est intéressant en terme de suivi de modifications. C'est en tout cas plus pratique que le système moisi de révisions intégré à WordPress.

En terme de sauvegarde c'est assez chouette aussi puisque tous mes articles depuis le début du blog ont été placés dans le dépôt et les prochains seront eux aussi conservés dans un format facilement exploitable si un jour je change de plateforme.

Enfin, comme le dépôt est public, mes brouillons seront visibles dessus avant publication, je pourrais les faire relire et corriger plus facilement.

Je ne compte pas désactiver le système de tickets ni de pull request donc les lecteurs et lectrices qui savent utiliser GitHub pourront proposer des corrections et modifications très simplement avec une PR, les autres pourront ouvrir un ticket pour signaler les erreurs.

Dans tous les cas, améliorer mon workflow d'écriture m'a donné un petit boost de motivation et je devrais publier plus régulièrement pendant un moment.

À la prochaine !
