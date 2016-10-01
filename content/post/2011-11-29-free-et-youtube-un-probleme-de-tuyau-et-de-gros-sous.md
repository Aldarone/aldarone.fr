---
date: 2011-11-29T00:00:00Z
head_img:
- https://aldarone.fr/assets/Rodolphe.jpg
head_img_alt:
- Rodolphe de Free
title: "Free et Youtube: un problème de tuyau et de gros sous"
slug: "free-et-youtube-un-probleme-de-tuyau-et-de-gros-sous"
---

Voila le sujet qui anime la twitto/blogosphère française en ce moment: Le débit pour regarder les videos sur youtube est déplorable quand on a « tout compris » (ce qui au final donne l'impression de n'avoir rien compris en fait.)

Il y a un excellent article chez Numerama qui résume bien l'histoire (<a href="http://www.numerama.com/magazine/20728-suspecte-de-brider-youtube-free-veut-que-google-investisse-davantage.html">Suspecté de brider YouTube, Free veut que Google investisse davantage</a>) donc je ne rappellerai pas tous ces éléments ici.

Je vais juste vous faire part d'une petite constatation faite en comparant le chemin vers Youtube que l'on soit chez Free ou chez SFR.

En effet, depuis un accès Free, l'information passe successivement par les routeurs de Free (logique) puis va chez Cogent, Level3 et arrive enfin à Google.

<pre class="brush: text plain; highlight: [8, 12]">Détermination de l'itinéraire vers youtube.com [173.194.66.91] avec un maximum de 30 sauts :

  1    10 ms     1 ms     1 ms  192.168.3.254
  2     *        *        *     Délai d'attente de la demande dépassé.
  3    26 ms    25 ms    37 ms  213.228.35.254
  4     *        *        *     Délai d'attente de la demande dépassé.
  5    30 ms    29 ms    30 ms  bzn-crs16-1-be1104.intf.routers.proxad.net [212.27.50.185]
  6    33 ms    30 ms    40 ms  te2-8.365.mag02.par01.atlas.cogentco.com [149.6.160.101]
  7    31 ms    32 ms    30 ms  te0-5-0-4.ccr22.par01.atlas.cogentco.com [130.117.49.85]
  8    48 ms    38 ms    38 ms  te0-4-0-6.ccr22.lon13.atlas.cogentco.com [154.54.37.209]
  9    38 ms    38 ms    38 ms  level3.lon01.atlas.cogentco.com [130.117.15.82]
 10   151 ms    65 ms    67 ms  unknown.Level3.net [212.113.15.186]
 11    59 ms    40 ms    39 ms  209.85.255.78
 12    39 ms    38 ms    40 ms  209.85.253.90
 13    40 ms    40 ms    40 ms  72.14.232.134
 14   120 ms    41 ms    40 ms  72.14.236.191
 15     *        *        *     Délai d'attente de la demande dépassé.
 16    40 ms    40 ms    40 ms  we-in-f91.1e100.net [173.194.66.91]

Itinéraire déterminé.</pre>

Quand on est chez SFR, l'itinéraire n'est pas du tout pareil:

<pre class="brush: text plain; highlight: [10]">traceroute to youtube.com (173.194.34.37), 30 hops max, 60 byte packets
...
 2  214.160.96.84.rev.sfr.net (84.96.160.214)  39.772 ms  41.473 ms  46.224 ms
 3  225.162.96.84.rev.sfr.net (84.96.162.225)  46.233 ms  46.236 ms  46.234 ms
 4  133.143.96.84.rev.sfr.net (84.96.143.133)  47.917 ms  47.930 ms *
 5  V3799.nts1-co-1.gaoland.net (84.96.251.133)  60.548 ms
    V4073.cbv3-co-1.n9uf.net (62.39.148.85)  60.561 ms
    V3799.nts1-co-1.gaoland.net (84.96.251.133)  60.561 ms
 6  72.14.217.1 (72.14.217.1)  60.558 ms  80.897 ms
    86.201.118.80.rev.sfr.net   (80.118.201.86)  82.589 ms
 7  72.14.238.234 (72.14.238.234)  95.165 ms 42.796 ms  42.791 ms
 8  209.85.242.47 (209.85.242.47)  42.798 ms  42.782 ms 52.550 ms
 9  173.194.34.37 (173.194.34.37)  52.559 ms  52.563 ms  52.561 ms</pre>

On quitte SFR et « <em>OH ! Google !</em> » directement.

Visiblement, Google et SFR ont trouvé un accord pour se brancher directement l'un chez l'autre. Donc quand @AlexArchambault nous dit que Google ne veut pas investir, c'est faux: L'infrastructure est là et elle fonctionne apparemment très bien pour les autres FAI.

Notons qu'Orange est connecté directement chez Google via son propre opérateur de transit: Opentransit ou encore que Google est présent chez un autre opérateur de transit Français: FranceIX. Il n'y a donc visiblement aucune raison d'aller récupérer les contenus de l'autre côté de l'atlantique (Cogent et Level3 sont des opérateurs internationaux) puisque Google semble les rendre disponible directement en France.

Peut-être que Free devrait faire son boulot de FAI et fournir Internet à ses clients au lieu de vouloir se goinfrer sur un marché biface. Sinon on aura bientôt Internet, Internet par Orange mais aussi Internet par Free.
