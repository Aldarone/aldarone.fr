---
ID: 1556
post_title: Fuck you ownCloud. Fuck you.
author:
  - Alda
post_date:
  - 2014-12-08 23:09:57
post_excerpt:
  - ""
layout: post
permalink: ""
published: true
---

/! Ce billet contient un certain niveau de rage et de frustration envers un logiciel non coopératif et bugué. Merci d'en tenir compte lors de votre lecture. /!

<h3>Mise à jour du 09 décembre 2014, 14h</h3>

J'ai reçu un mail d'un lecteur qui m'explique comment il a laissé tomber Owncloud devant le manque constant de fiabilité et est passé à <a href="http://seafile.com/en/home/">SeaFile</a>. Il donne plus de détails sur son blog : « <a href="http://eliotberriot.com/blog/2013/12/18/owncloud-sparkleshare-git-annex-seafile-quelle-solution-libre-pour-heberger-et-synchroniser-ses-fichiers/">Ownbutt, SparkleShare, Git-Annex, Seafile... Quelle solution libre pour héberger et synchroniser ses fichiers ?</a> » et a rédigé une dépêche sur LinuxFR pour présenter la version 3 : « <a href="https://linuxfr.org/news/seafile-un-dropbox-like-libre-a-heberger-sort-en-version-3">Seafile, un Dropbox-like libre à héberger sort en version 3</a> »

Effectivement ça a l'air alléchant, mais SeaFile <a href="https://github.com/haiwen/seafile/issues/801">ne propose pas encore de service CardDav, ni CalDav</a> pour synchroniser des contacts ou des calendriers. Ayant laissé tomber mon instance <a href="http://baikal-server.com/">Baïkal</a> pour passer à OwnCloud, ça m'embêterait de séparer à nouveau ces services là.

<h3>Article d'origine</h3>

ownButt est un logiciel en PHP qui sert à héberger son propre service de partage de fichiers. Globalement c'est un équivalent libre de Dropbox qui fait aussi de la synchro de contacts et de calendriers.

Il y a quelques temps maintenant, les gestionnaires du projet ont annoncé en grande pompe le module de chiffrement côté serveur qui permet aux utilisateurices de s'assurer que leur hébergeur ne pourra pas voir le contenu des fichiers envoyés. (À ce point là, il est important de noter que la personne en charge de l'administration dispose d'une clé de récupération, au cas où.)

Même si je suis mon propre hébergeur, je me suis empressé d'activer ce module lors de l'installation de mon instance il y a deux ou trois mois, imaginant déjà libérer mes potes du joug de Dropbox en les rassurant sur le fait que je ne pourrais pas accéder à leurs dick- ou clit-pics sans qu'illes soient au courant.

Si vous êtes pressés je vous la fait courte : J'aurais pas dû.

<img src="http://aldarone.fr/wp-content/uploads/2014/12/yjt6EZL.gif" alt="yjt6EZL" width="500" height="271" class="aligncenter size-full wp-image-1559" />

J'ai donc commencé à utiliser le client de synchronisation d'abord en transférant toute ma dropbox, puis en activant l'envoi automatique de mes photos prises sur mon téléphone, puis en y mettant mes dotfiles pour y avoir accès de partout.

Jusqu'au jour où, pour une raison inconnue, le client de synchronisation d'ownButt a merdé pendant la synchro de mon dossier .atom (l'éditeur de github) et je me suis retrouvé avec MariaDB qui râlait à la DUPLICATE ENTRY dans une table.

Évidemment à ce point il y a trop de fichiers en erreur pour corriger à la main et ça me semble trop aléatoire pour être scripté rapidement.

Après recherches, des pistes semblent indiquer que c'est dû à la manière dont le module de chiffrement gère (mal) les noms de fichiers. Je me suis donc dit que j'allais juste le désactiver, qu'ownButt déchiffrerait mes fichiers au fil des accès et que j'aurais juste à supprimer mon dossier pourri et à le renvoyer.

Hahaha, naïf que je suis. Il faut lancer manuellement une requête de déchiffrement dans les options et évidemment ça prend un temps fou. Firefox laisse tomber la requête AJAX au bout d'une demi heure, mais ça continue de tourner et c'est le max execution time de PHP qui détermine le temps avant plantage (En l’occurrence, ce fut une heure)

Je ne me laisse pas démonter et je met un petit <code>set_time_limit(0)</code> au début du script histoire d'être sûr et je le relance en gardant un œil sur les logs dans un <a href="http://danielmiessler.com/study/tmux/">tmux</a>. Deux heures plus tard il plante à nouveau <code>Calling method -&gt;machintruc() on a non-object</code>



Je commence un peu à m'échauffer parce que quand on utilise des fonctions qui renvoient <code>null</code> ou un objet, la moindre des choses c'est de vérifier qu'on a bien un objet après l'appel à cette fonction… J'ajoute cette vérif en loguant bien les erreurs et je relance le bouzin.

Après cinq heures à mouliner<sup id="fnref:1"><a href="1" rel="footnote">1</a></sup> c'est au tour de MariaDB de se plaindre : <code>General error: 2006 MySQL server has gone away</code> Parce que oui, le timeout il est par défaut à 300 secondes. Donc on ouvre la connexion et cinq heures plus tard il y a plus personne au bout du fil. Nouvel essai.

Après 6 heures, les logs s'arrêtent de défiler (j'ai rajouté le log du chemin de chaque fichier déchiffré histoire de voir quand ça s'arrête parce que sinon c'est le noir complet) et comme il n'y a pas d'erreur je commence à me dire que ça y est, peut-être mes galères sont terminées. Je me connecte donc à l'interface web pour voir et… « <em>Le chiffrement était désactivé mais vos fichiers sont toujours chiffrés. Veuillez vous rendre sur vos Paramètres personnels pour déchiffrer vos fichiers.</em> » cette cochonnerie de message est toujours là. MAIS IL Y A PAS D'ERREUR ! APACHE SE TOURNE LES POUCES !

Évidemment après vérification, une grande partie de mes fichiers est toujours chiffrée, j'ai beau relancer leur script de merde ça ne change absolument rien et le client de synchro râle toujours qu'il n'a pas pu synchroniser * fichiers en raison d'une erreur inattendue sur le serveur.

Bref, je suis bon pour tout supprimer et tout renvoyer. Ce qui avec mon accès ADSL va prendre environ… 130 heures à vitesse maxi. (&#12494;&#3232;&#30410;&#3232;)&#12494;



N'activez pas le module de chiffrement d'ownButt. Sauf si vous voulez vous prendre la tête pour rien.

<div class="footnotes">
<hr />
<ol>

<li id="fn:1">
J'ai 7Go de données, je veux bien que ça prenne du temps, mais c'est rageant quand ça plante pour des conneries…&#160;<a href="1" rev="footnote">&#8617;</a>
</li>

</ol>
</div>