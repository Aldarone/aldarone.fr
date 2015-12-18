---
ID: 1664
post_title: >
  Facebook pour Android, tueuse de
  smartphone
author:
  - Alda
post_date:
  - 2015-10-19 13:50:44
post_excerpt:
  - ""
layout: post
published: true
---
Cette semaine j'ai installé la dernière version de Resurrection Remix sur mon Galaxy S3.

J'ai fait la totale :

* [Resurrection Remix](http://forum.xda-developers.com/galaxy-s3/development/rom-resurrection-remix-5-2-1-t2972523)
* [Boeffla Kernel](http://www.boeffla-kernel.de/)
* [Xposed Framework](http://forum.xda-developers.com/showthread.php?t=3034811)
* [Tk GAPPS](http://forum.xda-developers.com/android/software/tk-gapps-t3116347) (Édition Pico)

Avec ça le S3 tourne avec la dernière version de Lollipop et il tourne bien.

Enfin… Jusqu'au moment d'installer les appli Facebook et Facebook Messenger où c'est la catastrophe. Son temps de réaction s'effondre et la batterie fond à vue d'œil.
J'ai même parfois l'impression que c'est au sens propre tellement le CPU se met à chauffer.

J'avais déjà des soupçons depuis la dernière réinstallation complète de mon téléphone et ce coup ci c'était la goutte de trop et j'ai finalement fait ce que j'aurais du faire depuis longtemps : Je les ai virées.

## Facebook t'abuses un peu quand même.

Déjà à l'installation on peut se douter qu'il y a un truc chelou. Parce que les permissions demandées font juste peur.

[caption id="attachment_1675" align="aligncenter" width="1024"]<a href="http://aldarone.fr/wp-content/uploads/2015/10/facebook-permissions.png"><img src="http://aldarone.fr/wp-content/uploads/2015/10/facebook-permissions-1024x891.png" alt="Moi quand je vois ça, je m&#039;en fout parce que j&#039;utilise XPrivacy, mais j&#039;ai de la peine pour les gens qui ne savent pas comment se couvrir." width="1024" height="891" class="size-large wp-image-1675" /></a> Moi quand je vois ça, je m'en fout parce que j'utilise XPrivacy, mais j'ai de la peine pour les gens qui ne savent pas comment se couvrir.[/caption]

Ensuite le poids téléchargé est un peu effrayant lui aussi.

[caption id="attachment_1676" align="aligncenter" width="1024"]<a href="http://aldarone.fr/wp-content/uploads/2015/10/facebook-size.png"><img src="http://aldarone.fr/wp-content/uploads/2015/10/facebook-size-1024x226.png" alt="20 Mo pour une appli de messagerie et 44Mo pour une autre qui va bêtement appeler une API ? J&#039;imagine que le code espion ça pèse lourd…" width="1024" height="226" class="size-large wp-image-1676" /></a> 20 Mo pour une appli de messagerie et 44Mo pour une autre qui va bêtement appeler une API ? J'imagine que le code espion ça pèse lourd…[/caption]

Et puis passé le quart d'heure nécessaire à l'installation (véridique) la place occupé sur la partition ````/data```` est juste ÉNORME !

[caption id="attachment_1677" align="aligncenter" width="1024"]<a href="http://aldarone.fr/wp-content/uploads/2015/10/facebook-size-2.png"><img src="http://aldarone.fr/wp-content/uploads/2015/10/facebook-size-2-1024x529.png" alt="Yep, le code espion ça pèse vraiment très lourd en fait." width="1024" height="529" class="size-large wp-image-1677" /></a> Yep, le code espion ça pèse vraiment très lourd en fait.[/caption]

C'est lent, ça met des plombes à s'installer, ça pèse une tonne. Est-ce que ça vaut le coup de les garder juste pour avoir de quoi glandouiller dans le bus en allant ou en rentrant du boulot ?

Ben non. Hop, à la benne. Et là miracle : Mon téléphone est rapide à nouveau.

Connaissant Facebook j'imagine sans peine que ses applis écoutent en permanence tout ce qu'elles peuvent et que si ça ne se voit pas trop sur les téléphone récents, quand il commence à faire son âge ça fini par se remarquer.

## Heureusement il y a un remplaçant : Face Slim

[Face Slim](https://github.com/indywidualny/FaceSlim) qui porte décidément bien son nom, qui est Libre, disponible sur [F-Droid](https://f-droid.org/) et qui consiste en fait à afficher la version mobile de Facebook dans un navigateur intégré en fournissant aussi un moyen d'être notifié ainsi que quelques raccourcis.

[![Télécharger Face Slim sur F-Droid](https://camo.githubusercontent.com/7df0eafa4433fa4919a56f87c3d99cf81b68d01c/68747470733a2f2f662d64726f69642e6f72672f77696b692f696d616765732f632f63342f462d44726f69642d627574746f6e5f617661696c61626c652d6f6e2e706e67)](https://f-droid.org/app/org.indywidualni.fblite)

Le fichier d'installation fait 800Ko, installée elle occupe 2,55Mo et elle réagit à la vitesse de la 3G. Juste ce qu'on attend d'une telle appli en fait.

Comme ça je peux laisser libre cours à mes bas instincts et continuer de profiter d'un téléphone rapide.