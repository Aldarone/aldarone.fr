---
ID: 521
post_title: Comment tu télécharges toi ?
author: Alda
post_date: 2012-01-29 16:30:26
post_excerpt: ""
layout: post
permalink: >
  http://aldarone.fr/comment-tu-telecharges-toi/
published: true
bitlyURL:
  - http://bit.ly/yk7aVW
  - http://bit.ly/yk7aVW
head_img:
  - http://aldarone.fr/assets/usenet.jpg
  - http://aldarone.fr/assets/usenet.jpg
head_img_alt:
  - Usenet
  - Usenet
dsq_thread_id:
  - "556712682"
  - "556712682"
---
Cette question, de plus en plus de personnes me la posent en voyant que je ne suis pas inquiété plus que ça par la fermeture de Megaupload.

Pourquoi je ne m'en fais pas ? Parce que je n'ai jamais vraiment utilisé le téléchargement direct (au sens populaire du terme.) Quand eMule a commencé à sentir le sapin, j'ai fait comme tout le monde et je suis passé à Bittorrent. Et quand HADOPI s'en est mêlée, au lieu de me ruer vers des services remplis de pubs, de popups qui clignotent et de temps d'attente inutiles, j'ai choisi une autre solution moins connue: USENET.

<h3>Usenet c'est quoi ?</h3>

Usenet c'est l'ancêtre des forums de discussion. Il a été créé en 1979, après les mails mais avant le DNS et le web.

C'est donc un service qui permet de poster des messages texte dans des groupes de discussions organisés par thèmes. Les catégories principales sont comp. misc. news. rec. sci. soc. talk. biz. et alt. et chacune dispose de ses règles spécifiques: Messages textes uniquement pour les 8 premiers, publicité autorisée sur le 8ème, créations de sous-branches libres sur le dernier.

Il existe aussi des catégories privées comme microsoft. ou proxad. qui ne sont généralement accessibles que via certains serveurs.

[source]<a href="https://fr.wikipedia.org/wiki/Usenet" target="_blank">Wikipédia</a>[/source]

<h3>Et comment ça marche ?</h3>

Usenet est un réseau de serveurs reposant sur le protocole NNTP. L'utilisateur se connecte sur un serveur avec un client compatible (Une grande majorité des logiciels d'e-mail le sont) et demande à recevoir la liste des X derniers messages d'un certain groupe.

Quand un utilisateur poste un message sur un ou plusieurs groupes, le serveur le réceptionne et l'ajoute à sa liste.

Périodiquement, les serveurs s'interrogent les uns les autres pour synchroniser la liste des messages qui figurent dans les groupes qu'ils gèrent.

Pour ne pas saturer l'espace nécessaire au stockage de tous ces messages, chaque serveur possède une durée de rétention qui lui est propre. Les messages plus anciens sont alors définitivement supprimés.

<h3>Ok mais quel rapport avec le téléchargement si on parle de messages en texte ?</h3>

La hiérarchie alt.binaries. est spécialisée dans la diffusion de fichiers binaires encodés en ASCII. Et c'est là dedans qu'on va trouver ce qui nous intéresse.

Mettons que nous voulions télécharger l'iso d'une version d'ubuntu. Nous allons nous abonner au groupe alt.binaries.boneless et récupérer la liste des derniers messages. Là, si on a de la chance on verra des centaines de lignes ayant pour sujet quelque chose comme « Ubuntu.Desktop.10.04LTS.x64-LiNUX [01/23] - "ub10ltd6.par2" yEnc (1/1) »

On pourrait tous les télécharger un par un et les décoder pour obtenir des archives RAR et des fichiers PAR.

Ces fichiers PAR sont utilisés pour reconstituer les autres fichiers téléchargés en cas de corruption des données (ce qui arrive de temps en temps.)

<h3>Ça m'a l'air compliqué ton truc…</h3>

Ça l'est, mais ça se simplifie !

Évidemment il n'est pas du tout pratique de télécharger ces milliers de messages, puis de les décoder pour enfin avoir le fichier qu'on voulait. Donc un nouveau type de logiciel est apparu: les newsgrabber.

Spécialisés dans le téléchargement de binaires sur usenet, ils regroupent les message pour n'avoir qu'une ligne à sélectionner par fichier et se chargent de décoder les messages. Par la suite ils évolueront et se chargeront même de vérifier l'intégrité des fichiers décodés, de leur réparation si le besoin s'en fait sentir et de l'extraction des archives.

Néanmoins, si l'usage se simplifie, il n'est toujours pas pratique de devoir s'abonner à un groupe, télécharger toute la liste des sujets existants et la parcourir pour trouver ce qu'on cherche. C'est pourquoi se sont développés des moteurs de recherche spécialisés dans l'indexation de usenet ainsi qu'un nouveau format de fichier :

<h4>Les fichiers NZB</h4>

Le principe est tout simple: Ils recensent le nom du/des groupes contenant les messages qui nous intéressent ainsi que la liste de ces messages. Nous n'avons plus qu'à récupérer le fichier NZB généré par notre moteur de recherche et à le fournir en pâture à notre newsgrabber pour qu'il se charge de faire son boulot.

<!--nextpage-->

<h3>Passage à la pratique</h3>
<h4>Trouver un fournisseur</h4>

Du fait de la quantité assez phénoménale de fichiers disponibles sur Usenet et de l'impossibilité qu'ont les fournisseurs à afficher de la publicité dans votre newsgrabber, l'accès à la hiérarchie atl.binaries. est toujours payante. Avec, en France, une exception à la règle: Free propose 7 à 10 jours de rétention à ses abonnés via son serveur news.free.fr (mais ils sont régulièrement condamnés à filtrer les groupes les plus orientés piratage)

Les deux fournisseurs les plus connus sont <a href="http://www.giganews.com/" target="_blank">Giganews</a> et <a href="http://www.usenext.fr/" target="_blank">Usenext</a> qui proposent tous deux plus de 1200 jours de rétention avec un taux de disponibilité des fichiers de 99%.

Usenext propose des offres «hybrides» à partir de 10€/mois. Elles offrent un volume de téléchargement illimité si votre vitesse ne dépasse pas 2Mbps au delà de cette vitesse l'abonnement se fait par paliers: 30Go, 80Go, 250Go.

Giganews commence lui à 10$ (7.5€) pour 10Go/mois et l'offre illimitée est à 35$ (25€). À noter que Giganews offre l'accès à sa plateforme vyprVPN dans le cas d'un abonnement illimité, ça peut éviter d'en souscrire un abonnement VPN à côté.

Personnellement je préconise <a href="http://www.astraweb.com/" target="_blank">Astraweb</a> qui propose l'illimité à 15$ (10€) sans limite de débit et une rétention de 1250 jours.

<h4>Trouver un newsgrabber</h4>

Il en existe évidemment plusieurs, des gratuits comme des payants, opensource ou non.

Mes recommandations: Si vous êtes sous linux, je vous recommande chaudement <a href="http://sabnzbd.org/" target="_blank">SabNZBd</a> et pour les utilisateurs de Windows vous avez le choix entre <a href="http://www.ideosi.fr/niouzefire.php" target="_blank">NiouzeFire</a> et la version windows de SabNZBd (mais vous allez pas forcément trouver ça très intuitif)

<h4>Trouver des NZB</h4>

Là aussi vous avez le choix entre plusieurs services, de qualité plus où moins identique. Pour nous frenchies, la référence est <a href="http://www.binnews.in/" target="_blank">Binnews.in</a>. Il s'agit d'un site alimenté par ses utilisateurs qui référencent et catégorisent les fichiers. Ce site ne fourni pas de fichier NZB mais uniquement le nom des fichiers afin de les trouver plus facilement sur un moteur de recherche.

Côté moteur de recherche, il y a <a href="https://www.binsearch.info/" target="_blank">Binsearch</a>, <a href="http://nzbindex.nl" target="_blank">NZBindex</a> ou encore <a href="https://www.mysterbin.com/" target="_blank">MysterBin</a>. À vous de choisir celui que vous préférez utiliser, ils se valent.

Et puis il y a les services tout en un comme <a href="http://nzbmatrix.com/" target="_blank">NZBMatrix</a> ou <a href="http://www.newzbin2.es/" target="_blank">NewzBin</a> qui sont similaires à binnews à la différence qu'ils proposent des NZB et qu'ils réclament une somme modique pour l'accès au catalogue: 8£ l'année pour Newzbin ou 7£ à vie pour NZBMatrix. (Il recensent par contre un contenu essentiellement anglophone.)

<h3>Avertissement</h3>

Vous trouverez bien évidemment beaucoup de contenu protégé par le droit d'auteur sur Usenet. Usenext a par exemple été condamné à ce propos car leurs publicitées étaient trop orientées dans cette direction. Newzbin a fermé il y a un an (le Newzbin actuel est une refonte) car les autorités australiennes ont estimé que le site était dédié à la contrefaçon d'œuvres protégées. Et Free est obligé de retirer des groupes de ses serveurs tous les 6 mois, à chaque notification des ayants droits.

Le tout est de ne pas céder à la tentation. Contrairement au P2P, il est impossible pour quiconque de savoir ce que vous téléchargez sur Usenet (sauf pour votre fournisseur) mais je ne serais pas tenu pour responsable si vous remplissez votre disque dur de contenu piraté et que vous vous faites avoir par un moyen quelconque.

<p class="source">Vous trouverez d'autres liens vers des newsgrabbers et des moteurs de recherche sur le wiki de Korben: <a href="http://free.korben.info/index.php/T%C3%A9l%C3%A9chargements_et_%C3%A9changes_de_fichiers#Newsgroups" target="_blank">Téléchargements et échanges de fichiers</a></p>