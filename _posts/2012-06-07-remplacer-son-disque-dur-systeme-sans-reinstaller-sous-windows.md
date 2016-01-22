---
ID: 602
post_title: >
  Remplacer son disque dur système sans
  réinstaller (Sous Windows)
author: Alda
post_date: 2012-06-07 22:40:44
post_excerpt: ""
layout: post
permalink: >
  /remplacer-son-disque-dur-systeme-sans-reinstaller-sous-windows/
published: true
head_img:
  - >
    https://aldarone.fr/assets/FuckThatShit.jpg
  - >
    https://aldarone.fr/assets/FuckThatShit.jpg
head_img_alt:
  - Fuck That Shit
  - Fuck That Shit
bitlyURL:
  - http://bit.ly/LyVFsC
  - http://bit.ly/LyVFsC
dsq_thread_id:
  - "717352181"
  - "717352181"
---
<p>J'étais tranquillement en train de jouer à <a href="http://www.bay12games.com/dwarves/">Dwarf Fortress</a> quand mon ordi s'est brusquement figé en émettant un des bruits les plus horrible qui soit: <strong>Celui d'un disque dur à l'agonie</strong>.</p>

<p>Ce moment où vous entendez le plateau ralentir et s'arrêter, suivi d'un claquement puis du bruit du plateau qui repart et où la seule chose qui vous traverse l'esprit c'est « Oh putain non, repart, s'il te plait résiste encore un peu s'il te plait. »</p>

<p>Heureusement pour moi il a bien voulu continuer de fonctionner et j'ai pu me précipiter chez mon fournisseur pour commander un nouveau disque dur (non, toujours pas un SSD, je suis pauvre moi m'sieur/dame.)</p>

<p>[caption id="attachment_605" align="aligncenter" width="400" caption="Non, il ne ressemble pas à ça tout de même."]<img src="https://aldarone.fr/wp-content/uploads/2012/06/the-foolproof-option-remove-and-destroy-your-hard-drive.jpg" alt="Disque dur détruit" title="Disque dur détruit" width="400" height="300" class="size-full wp-image-605" />[/caption]</p>

<p>3 jours plus tard je reçois le nouveau disque dans ma boite à lettres et je commence à chercher le moyen de copier à l'identique le contenu et les partitions de l'ancien.</p>

<p>Microsoft propose une solution très simple <strong>intégrée à Windows</strong> avec l'outil de sauvegarde. Ils appellent ça une « sauvegarde du système »</p>

<p>En trois clics me voila en train de faire ma sauvegarde sur mon disque secondaire, après 45 min d'attente, j'éteins mon PC, échange les disque et démarre en mode restauration pour… restaurer la sauvegarde sur le nouveau disque.</p>

<p>Évidemment, ça ne marche pas. <a href="https://www.google.fr/search?q=windows%207%20restore%200x80070057">Je ne suis pas le seul</a>. Il fallait s'y attendre, mais je voulais y croire.</p>

<p>Bien sûr, puisque c'est le message d'erreur le plus générique possible il y a tout un tas de solutions à tout un tas de situations différentes mais aucune qui semble convenir.</p>

<p>Heureusement, j'ai trouvé <strong>LA solution à l'erreur 0x80070057 quand on restaure une sauvegarde système sous Win7</strong>. Il faut simplement oublier complètement l'outil officiel de Windows et utiliser <a href="http://clonezilla.org/">CloneZilla</a> en faisant une copie disque à disque. En 30min c'était plié.</p>

<p>Les outils open-source, c'est le bien.</p>