+++
comments = true
date = "2017-01-29T12:30:00+02:00"
image = "img/plastic-face.jpg"
slug = "combien-de-temps-je-vais-my-tenir-cette-fois"
title = "Combien de temps je vais m'y tenir cette fois ?"
draft = true
+++

Histoire de pas toujours écrire un article fleuve et rester silencieuse ici de longues semaines en attendant l'idée suivante, je me suis dit que j'allais essayer de faire un petit bilan hebdo des trucs vu en ligne qui ont marqué ma semaine.

Après, je me connais, je sais bien que mes bonnes résolution tombent toujours à l'eau après quelques itérations donc c'est pas dit que je persiste longtemps. Mais j'espère que ça en intéressera le temps que ça durera.

Et j'ai aucune idée du format que ça aura parce que on est Mardi, j'ai juste mes notes de la veille et si ça se trouve d'ici Vendredi j'aurai de quoi écrire un petit roman que je ne voudrais pas forcément infliger au reste du monde.

## Lundi

On commence par un peu de technique parce que j'ai creusé un peu autour du noyau Linux et d'Arch. C'est toujours la version 4.8 qui est dans le dépôt stable alors que la version 4.9 est sortie en décembre et que la 4.8 ne sera plus supportée d'ici la fin du mois.

Il s'avère que la 4.9 a [un vilain bug][kernelbug] qui empêche les ordis ayant un processeur Intel de démarrer. Ça ne le fait pas avec tous les CPU Intel, mais c'est suffisamment gênant pour bloquer le noyau dans les dépôts testing. On espérait une résolution pour la 4.9.5 qui est sortie le 20 Janvier mais [apparemment ça serait plutôt pour la 4.9.6][kernelresolution] (cf. le dernier commentaire) qui sortira prochainement.

[kernelbug]: https://bugzilla.kernel.org/show_bug.cgi?id=192111
[kernelresolution]: https://bugs.archlinux.org/task/52246#comment154786

Ensuite, j'ai regardé le documentaire Netflix « [Hot Girls Wanted][hotgirlstrailer] » qui était… plutôt médiocre. Le docu commence alors que des adolescentes arrivent chez leur « agent » après avoir répondu à une annonce et se termine avec soulagement quand elles sont sauvées de la pornographie quelques mois plus tard.

L'angle choisi saute aux yeux, il s'agit une fois de plus de décrire le travail du sexe comme intrinsèquement mauvais au lieu d'attaquer l'industrie capitaliste qui exploite les travailleur⋅euses. La critique qu'en fait [le site Jezebel][hotgirlsjezebel] est assez instructive et pour une vraie critique de l'industrie du sexe, je conseillerai probablement « [Pornocratie, les nouvelles multinationales du sexe][pornocratie] » d'Ovidie si j'arrive à mettre la main dessus.

[hotgirlstrailer]: https://www.youtube.com/watch?v=qTkEIGsNXu4
[hotgirlsjezebel]: http://jezebel.com/in-hot-girls-wanted-porn-isnt-ruining-women-exploitat-1709109263
[pornocratie]: http://www.canalplus.fr/infos-documentaires/pornocratie/cid1429571-figure-du-x-engage-feministe-qui-est-la-realisatrice-ovidie.html

J'ai aussi lu un article qui a éclairci d'un coup beaucoup des choses encore nébuleuses dans ma tête et qu'il va falloir que je digère un peu, c'est « [Anti-guide du questionnement de genre][antiguide] » du blog Raymond Reviens qui se veut une réponse au « [Petit guide du questionnement de genre][petitguide] » de chez Simonæ sous un angle qu'on pourrait qualifer de matérialiste et anti-libéral (d'où, entre autres, le fait que ça me parle)

[antiguide]: https://raymondreviens.wordpress.com/2017/01/17/anti-guide-du-questionnement-de-genre/
[petitguide]: http://simonae.fr/militantisme/thematiques-queer/petit-guide-questionnement-genre/

Et puis finalement, j'ai passé la dernière beta de [LibreElec sur mon Odroid-C2][libreelecc2]. Il a remplacé mon RaspberryPi 2 (qui tournait sous [OSMC][osmc]) pour lire mes fichiers médias puisqu'il est capable de décoder du HEVC 10bits et avec la dernière beta disponible je peux enfin afficher les vidéos youtube en FullHD. Le seul truc un peu relou c'est qu'il a fallu faire une installation complète au lieu de passer par le processus de mise à jour standard.

[libreelecc2]: http://forum.odroid.com/viewtopic.php?f=144&t=24753&sid=b91cb0c1223b33b08e91735f172a1f61
[osmc]: https://osmc.tv/
