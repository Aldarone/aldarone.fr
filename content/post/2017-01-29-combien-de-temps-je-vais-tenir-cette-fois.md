+++
comments = true
date = "2017-01-29T17:57:33+01:00"
image = "img/colour-capture.jpg"
slug = "combien-de-temps-je-vais-my-tenir-cette-fois"
title = "Combien de temps je vais m'y tenir cette fois ?"
draft = false
+++

Histoire de pas toujours écrire un article fleuve et rester silencieuse ici de longues semaines en attendant l'idée suivante, je me suis dit que j'allais essayer de faire un petit bilan hebdo des trucs vu en ligne qui ont marqué ma semaine.

Après, je me connais, je sais bien que mes bonnes résolution tombent toujours à l'eau après quelques itérations donc c'est pas dit que je persiste longtemps. Mais j'espère que ça en intéressera le temps que ça durera.

Et j'ai aucune idée du format que ça aura parce que on est Mardi, j'ai juste mes notes de la veille et si ça se trouve d'ici Vendredi j'aurai de quoi écrire un petit roman que je ne voudrais pas forcément infliger au reste du monde.

## Lundi

### Arch et Linux sont dans un bâteau

On commence par un peu de technique parce que j'ai creusé un peu autour du noyau Linux et d'Arch. C'est toujours la version 4.8 qui est dans le dépôt stable alors que la version 4.9 est sortie en décembre et que la 4.8 ne sera plus supportée d'ici la fin du mois.

Il s'avère que la 4.9 a [un vilain bug][kernelbug] qui empêche les ordis ayant un processeur Intel de démarrer. Ça ne le fait pas avec tous les CPU Intel, mais c'est suffisamment gênant pour bloquer le noyau dans les dépôts testing. On espérait une résolution pour la 4.9.5 qui est sortie le 20 Janvier mais [apparemment ça serait plutôt pour la 4.9.6][kernelresolution] (cf. le dernier commentaire) qui sortira prochainement.

[kernelbug]: https://bugzilla.kernel.org/show_bug.cgi?id=192111
[kernelresolution]: https://bugs.archlinux.org/task/52246#comment154786

### Un mauvais docu sur le porn « amateur » professionnel

Ensuite, j'ai regardé le documentaire Netflix « [Hot Girls Wanted][hotgirlstrailer] » qui était… plutôt médiocre. Le docu commence alors que des adolescentes arrivent chez leur « agent » après avoir répondu à une annonce et se termine avec soulagement quand elles sont sauvées de la pornographie quelques mois plus tard.

L'angle choisi saute aux yeux, il s'agit une fois de plus de décrire le travail du sexe comme intrinsèquement mauvais au lieu d'attaquer l'industrie capitaliste qui exploite les travailleur⋅euses. La critique qu'en fait [le site Jezebel][hotgirlsjezebel] est assez instructive et pour une vraie critique de l'industrie du sexe, je conseillerai probablement « [Pornocratie, les nouvelles multinationales du sexe][pornocratie] » d'Ovidie si j'arrive à mettre la main dessus.

[hotgirlstrailer]: https://www.youtube.com/watch?v=qTkEIGsNXu4
[hotgirlsjezebel]: http://jezebel.com/in-hot-girls-wanted-porn-isnt-ruining-women-exploitat-1709109263
[pornocratie]: http://www.canalplus.fr/infos-documentaires/pornocratie/cid1429571-figure-du-x-engage-feministe-qui-est-la-realisatrice-ovidie.html

### Des réflexions du genre

J'ai aussi lu un article qui a éclairci d'un coup beaucoup des choses encore nébuleuses dans ma tête et qu'il va falloir que je digère un peu, c'est « [Anti-guide du questionnement de genre][antiguide] » du blog Raymond Reviens qui se veut une réponse au « [Petit guide du questionnement de genre][petitguide] » de chez Simonæ sous un angle qu'on pourrait qualifer de matérialiste et anti-libéral (d'où, entre autres, le fait que ça me parle)

[antiguide]: https://raymondreviens.wordpress.com/2017/01/17/anti-guide-du-questionnement-de-genre/
[petitguide]: http://simonae.fr/militantisme/thematiques-queer/petit-guide-questionnement-genre/

### LibreElec sur ODROID-C2

Et puis finalement, j'ai passé la dernière beta de [LibreElec sur mon Odroid-C2][libreelecc2]. Il a remplacé mon RaspberryPi 2 (qui tournait sous [OSMC][osmc]) pour lire mes fichiers médias puisqu'il est capable de décoder du HEVC 10bits et avec la dernière beta disponible je peux enfin afficher les vidéos youtube en FullHD. Le seul truc un peu relou c'est qu'il a fallu faire une installation complète au lieu de passer par le processus de mise à jour standard.

[libreelecc2]: http://forum.odroid.com/viewtopic.php?f=144&t=24753&sid=b91cb0c1223b33b08e91735f172a1f61
[osmc]: https://osmc.tv/

## Mardi :

### Pornocratie

Ça n'aura pas trop tardé, j'ai pu regarder « Pornocratie » qui était effectivement vachement plus intéressant que « Hot Girls Wanted » puisqu'il dénonce les montages financiers fait par les boites de streaming gratuit. Par contre il ne traite que de cet angle et fait un peu dans la nostalgie du temps avant le piratage où les travailleurs et travailleuses du sexe étaient respectées dans le métier 🤔

### La signature de Firefox Nightly

Apparemment il y a quelques semaines Mozilla a migré le système de build de Firefox sur une nouvelle plateforme et du coup la génération des signatures et des sommes de contrôle est toute pétée. Ça veut dire que quand on installe une verssion nightly, on peut pas être sûres qu'on est pas en train de télécharger une version modifiée par un tiers malveillant. [Tout devrait être rétabli d'ici la semaine prochaine][ffxnightly].

Comme j'utilise le paquet `firefox-nighlty-fr` d'Archlinux j'ai du un peu bidouiller le `PKGBUILD` pour désactiver la récupération et la vérification des checksums (en gros on replace les commandes curl correspondantes par un gros `'SKIP'` et on utilise l'option `--skipinteg` de `makepkg`)

[ffxnightly]: https://bugzilla.mozilla.org/show_bug.cgi?id=1305139#c17

## Mercredi :

### City of stars

Perso j'adore les comédies musicales, j'adore Ryan Gosling, j'adore Emma Stone et j'ai beaucoup aimé Whisplash. Donc j'étais très très hypé pour la sortie de « [La La Land][lalalandtrailer] »

Et je n'ai pas été déçu. Du rire et des larmes et des étoiles dans les yeux et les chansons en tête tout le reste de la semaine. C'est la crème de la comédie romantique hétéro monogame, avec des chansons en plus.

Le seul point noir c'est que la monogamie c'est vraiment de la merde.

[lalalandtrailer]: https://www.youtube.com/watch?v=0pdqf4P9MB8

### Bad Evil Singleton

Au boulot j'ai eu à intervenir sur du code comportant un Bad Evil Singleton. Du genre qui répand du Global State dans tous les sens et qui rend affreusement difficile la compréhension des entrée/sortie et le testing.

Du coup je laisse un message de service : [Tuez vos singletons][killsingletons] et faites de l'injection de dépendance.

[killsingletons]: https://testing.googleblog.com/2008/08/by-miko-hevery-so-you-join-new-project.html

## Jeudi :

### Ce beau pays qu'est la Russie

C'est toujours agréable de commencer la journée sur des bonnes nouvelles et ce matin là c'était donc l'annonce de la dépénalisation des violences conjugales en Russie. Au nom, bien sûr, de [la protection de cette institution séculaire qu'est la famille][russie]. Qu'est-ce qu'on ferait pas pour la sauver celle-là hein ?

[russie]: http://www.lemonde.fr/europe/article/2017/01/26/contre-les-valeurs-occidentales-la-russie-depenalise-les-violences-domestiques_5069197_3214.html
### La justice en milieu anarcho-queer

Pour rester dans des sujets similaires, je suis tombé sur un texte intéressant sur [la manière de gérer les agressions sexuelles en milieu queer et féministe][colonelrobles] qui fait écho à quelque chose que j'avais lu sur il y a un moment sur [la gestion de la criminalité, sur l'exil et sur la peine de mort dans une société anarchiste][devianceanar].

[colonelrobles]: https://colonellerobles.wordpress.com/2014/02/26/premiers-pas-sur-une-corde-raide/
[devianceanar]: http://www.atelierdecreationlibertaire.com/IMG/pdf/Deviance_en_societe_libertaire.pdf

## Vendredi :

### Une alternative à Twitter

Toujours à l'affut pour quitter les services centralisés et privateurs, j'ai décidé de tester Mastodon qui est une réimplémentation de GNUSocial avec une interface beaucoup plus sexy (semblable à celle de Tweetdeck) et quelques fonctionnalités bienvenues.

Déjà l'équivalent des « Tweets » s'appelle les « Pouets », ensuite il est possible de passer par une étape de validation avant que quelqu'un puisse nous suivre tout en continuant à poster des pouets publics. À l'opposé on peut publier des pouets visibles uniquement pour nos followers même si on ne les valide pas.

Enfin, il y a un système de [Content Warning][contentwarning] qui permet d'écrire des spoilers, ou du contenu trigger qui ne sera affiché qu'après un clic sur un bouton.

J'ai rapidement trouvé [un script super bien foutu pour synchroniser mon compte avec Twitter][mastodontotwitter] et à part pour répondre aux tweets ou aux mentions je n'utilise plus que ça depuis.

Pour tester il faut s'incrire sur [mastodon.social][mastodonsocial] et pour me suivre il suffit d'ajouter [Alda@mastodon.social][mastodonprofile] (Ça marche aussi avec GNUSocial)

[contentwarning]: https://www.youtube.com/watch?v=0Y3T6Xz5h7o
[mastodontotwitter]: https://github.com/halcy/MastodonToTwitter
[mastodonsocial]: https://mastodon.social/auth/sign_up
[mastodonprofile]: https://mastodon.social/users/Alda

### Aux chiottes le citoyennisme

J'ai dépassé mon quotat de gens qui employaient les termes « citoyen » et « démocratie participative » à tout bout de champ du coup j'ai ressorti un article à ce propos trouvé sur « La Bibliothèque Anarchiste » : « [Individus ou citoyens][citoyennisme] » qui donne du grain à moudre.

[citoyennisme]: https://fr.theanarchistlibrary.org/library/machete-individus-ou-citoyens

### Arch et Linux sont encore dans un bateau

Finalement, j'ai fini ma semaine en mettant le noyau Linux à jour suite à la sortie de la version 4.9.6 dans les dépôts. Et la bonne nouvelle c'est que des corrections sympa sont présentes dans le module i915 ce qui m'a permis de réactiver deux fonctions d'économie d'énergie qui causaient le clignotement de l'écran de mon laptop. J'ai gagné 2W de consommation sur batterie ce qui me fait gagner de précieuses minutes d'usage, et c'est cool.

En parlant de mon laptop, il ne me reste plus quà résoudre un problème de webcam qui ne fonctionne qu'en 480p alors qu'elle est FullHD, un problème de hotplug HDMI et le décodage matériel des vidéos en HEVC ou VP9 10bits et il sera 100% fonctionnel. Pour un modèle sorti en septembre 2016, le support matériel est plutôt bon.

## Fin

Voilà du coup le résumé de la semaine, c'est un peu long, peut-être que je splitterai à l'avenir, ou peut-être que je mettrai moins d'info. Si vous avez des suggestions vous pouvez commenter sur les divers rézosocio, je suis pas si dur à trouver. 😛
