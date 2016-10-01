---
date: 2012-02-27T00:00:00Z
head_img:
- https://aldarone.fr/assets/MemoryLeak.png
head_img_alt:
- Ouh la belle fuite de mémoire.
title: "La configuration par défaut, ça marche jusqu&rsquo;à ce que ça marche plus."
slug: "la-configuration-par-defaut-ca-marche-jusqua-ce-que-ca-marche-plus"
---

<p>Je n'administre clairement pas mon serveur perso de manière admirable, la config par défaut est laissée pour la plupart des logiciels sans l'avoir vérifiée, il n'y a pas de système d'alertes pour l'occupation des disques ou de la RAM, ni même en cas de non réponse au ping. Pas bien tout ça !</p>

<p>Alors du coup, j'ai décidé de m'y mettre au fil de l'eau. J'ai installé un système de sauvegarde quand j'ai transféré la gestion de mes mails dessus, j'ai mis diverses alertes et vérifié la configuration de php et de mysql quand j'ai remarqué des fuites de mémoire.</p>

<p>C'est de cette dernière chose dont je vais vous parler aujourd'hui: des plantages récurrents de mon serveur depuis Janvier.</p>

<p><a href="https://aldarone.fr/wp-content/uploads/2012/02/screenshot.54.png" class="picture"><img src="https://aldarone.fr/assets/screenshot.54-540x133.png" alt="Host Unreachable" title="Host Unreachable" width="540" height="133" class="aligncenter size-large wp-image-577" /></a></p>

<p>Un serveur qui plante sans explication c'est pas très cool. Sans charge particulière, un coup il marche, la seconde d'après il répond plus aux pings. Et même pas un message d'erreur dans les logs. Au début du moins, puis un jour j'ai remarqué la ligne suivante dans <code>kern.log</code> : <code>[Hardware Error]: Machine check events logged</code></p>

<p>Elle s'est mise à apparaître systématiquement après chaque reboot. En cherchant un peu, il s'avère que la commande <code>mcelog</code> permet d'en savoir plus. Dans mon cas elle renvoyait ceci :</p>

<pre><code>HARDWARE ERROR. This is *NOT* a software problem!
 Please contact your hardware vendor
 MCE 0
 CPU 0 BANK 0
 MISC 61ba0000500010e ADDR cf9
 TIME 1329936775 Wed Feb 22 19:52:55 2012
 MCG status:
 MCi status:
 Uncorrected error
 MCi_MISC register valid
 MCi_ADDR register valid
 Processor context corrupt
 MCA: BUS Level-3 Observed-error-as-third-party Generic
 Memory-access Request-timeout Error
 Model:Response hard fail
 STATUS ae00030010020c03 MCGSTATUS 0
 MCGCAP 180204 APICID 0 SOCKETID 0
 CPUID Vendor Intel Family 15 Model 4
</code></pre>

<p>Ni une ni deux, j'ai demandé à OVH le remplacement de la RAM dans mon serveur. Une intervention plus tard, le problème avait empiré puisque le serveur était presque inutilisable : Les applications n'arrêtaient pas de planter en faisant des erreurs de segmentation (même Bash…)</p>

<p>Rebelote, OVH change à nouveau la RAM et le serveur repart correctement. Pendant 3 jours.</p>

<p>Nouveau problème : Le serveur répondait au ping, et c'est tout. Un tour dans l'interface de monitoring d'OVH et je me retrouve avec le graphique présenté en haut de cet article. Les processus qui consomment le plus ? 1 mysqld qui est à 1.3Go d'occupation et 10 php-fpm à 500Mo chacun. Sachant que j'ai 2Go + 500Mo de swap, ça peut pas coller. Tu m'étonnes qu'il est dans les choux !</p>

<p>La solution se trouvait évidemment dans la config.</p>

<p>MySQL pouvait ouvrir jusqu'à 100 threads pour supporter autant de connections, augmentant chaque fois l'occupation RAM. Or il n'y a que Dovecot, Prosody et PHP qui l'utilisent, chacun avec un nombre de connexions limitées.</p>

<p>Il suffit de changer la ligne suivante de <code>my.cnf</code> en remplaçant 100 par 30 (et encore, c'est large dans mon cas) et voila, on divise la RAM occupée par 3:</p>

<pre><code>max_connections = 100
</code></pre>

<p>De son côté, PHP-fpm est configuré pour ouvrir 10 processus fixes. Mais ils ne sont jamais recyclés par défaut, donc si un script a une fuite de mémoire et ne fait pas bien le ménage après exécution, le thread gonfle sans fin.</p>

<p>La solution se trouve dans php-fpm.conf, remplacez le 0 par 100 (ou plus, ça dépend de ce dont vous disposez comme ressources, à chaque fois qu'un processus est redémarré on perd le bénéfice d'Xcache par exemple) :</p>

<pre><code>pm.max_requests = 0
</code></pre>

<p>Ainsi, toutes les 100 requêtes exécutées, le processus est recyclé et la mémoire qu'il occupait est libérée.</p>

<p>Et tout de suite ça va mieux. Je pourrais (et vais) pousser un peu puisque le taux de RAM occupée oscille à présent entre 35 et 50%.</p>

<p>Mais c'était sans compter la loi de Murphy qui s'est acoquinée avec la loi des séries (celle qui veut qu'une emmerde n'arrive jamais seule)</p>

<p><img src="https://aldarone.fr/assets/epic-trollface-540x496.jpg" alt="Epic Trollface" title="Epic Trollface" width="540" height="496" class="aligncenter size-large wp-image-583" /></p>

<p>Oui parce qu'une semaine plus tard c'est l'alimentation du serveur qui grillait. Puis quelques heures plus tard, le serveur plantait à nouveau comme en janvier. OVH a donc gentiment changé la RAM (pour la 3<sup>ème</sup> fois), la carte mère et le CPU. Depuis, je touche du bois.</p>
