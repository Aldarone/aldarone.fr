---
date: 2014-04-05T00:00:00Z
title: "Le support de Windows XP est fini, passer à GNU/Linux réclame un accompagnement"
slug: "le-support-de-windows-xp-est-fini-passer-a-gnulinux-reclame-un-accompagnement"
---

Le support de Windows XP arrive à son terme dans 3 jours. Après 13 ans, un support étendu de 5 ans, il va enfin entrer dans les archives de l'histoire et on en parlera plus. (En fait pas vraiment, la quasi-totalité du parc de distributeurs bancaire est sous XP et les banques n'ont pas assez d'argent -- lol --- pour le renouveler, donc Microsoft a annoncé qu'il développerait des patchs payant sur mesure.)

Depuis quelques jours, les personnes qui ont encore ce système d'exploitation voient s'afficher un message leur annonçant la nouvelle et les redirigeant vers une page de la boutique de Microsoft.

<img src="https://aldarone.fr/wp-content/uploads/2014/04/fin-support-windows-xp-1.png" alt="fin-support-windows-xp-1" width="345" height="152" class="aligncenter size-full wp-image-1500" />

Ces personnes se tournent donc vers leur proche « qui s'y connait® » pour lui demander conseil. Pour peu que ce proche soit un libriste, il y a de grandes chance pour que la réponse ressemble un peu à ceci :

<blockquote>
  Si tu es prêt à faire quelques efforts, je te conseille de passer à Linux.

  Windows est mal pensé et lourd. Il y a aussi plein de failles d'où la nécessité d'installer des antivirus et des anti-malwares etc.

  De toute façon ce qu'il y a de mieux c'est Linux parce que le code est ouvert, ça veut dire qu'on peut aller voir ce qui se passe dedans et le modifier si il nous convient pas. C'est formidable ! Microsoft et Apple sont méchants, leur code est fermé, on sait pas ce qu'ils font, d'ailleurs la NSA a sûrement des porte dérobé pour prendre le contrôle de ton ordinateur, avec les logiciels libre c'est pas possible de faire ça.

  Il y a 4-5 ans Linux c'était compliqué mais plus maintenant<sup id="fnref:1"><a href="#fn:1" rel="footnote">1</a></sup>, il y a des interfaces graphiques pour tout. Et tout les logiciels de base dont on a besoin sont installés. Et pour en installer de nouveau c'est très simple. En plus l'installation est signée pour être bien sûr qu'on installe la bonne version et pas une version modifiée par quelqu'un de malveillant.

  J'ai passé ma grand-mère à Linux il y a 3 ans<sup id="fnref:2"><a href="#fn:2" rel="footnote">2</a></sup> et elle en est très contente. Bref, Linux c'est cool.

  Par contre, je n'assure pas le support technique :P
</blockquote>

Objectivement, on a raison quand on dit ce genre de chose. Mais on rate complètement notre cible. Pourquoi ?

Le problème avec ce discours, c'est qu'il est complètement idéologique. Pas étonnant qu'il passe à mille lieues au dessus de la tête de notre auditoire.

On est face à quelqu'un qui est inquiet de l'avenir de son vieux PC de 10ans, qui est resté sous XP par peur du changement parce qu'à l'époque de Vista tout le monde lui disait que Vista c'était nul. Ensuite, confortable sur son XP qui marchait très bien, ille est passé à côté de 7. Maintenant que 8 est sorti, tout le monde lui dit que 8 c'est nul[^3].

Et nous en face on débarque avec nos grandes théories sur le logiciel libre, la sécurité offerte par l'open-source, l'éthique, la merveilleuse communauté prête à aider son prochain. Le résultat, c'est qu'on a l'air de ça :

https://www.youtube.com/watch?v=6xvv0UGtQHg

Alors qu'au fond de nous, on sait très bien qu'une transition vers GNU/Linux c'est pas aussi simple que ça. La preuve, on commence par commence par « <em>Si tu es prêt à faire quelques efforts</em> » et on termine par « <em>Par contre, je n'assure pas le support technique :P</em> » qui sonne comme un « <em>T'es très con d'utiliser Windows, mais si tu veux passer à Linux, tu te démerdes hein.</em> »

On sait très bien que parfois, ce foutu <code>update-manager</code> va planter sans raison. Que le PC va se mettre en veille mais OUPS, c'est une carte graphique AMD et on a installé <code>catalyst</code> parce que <code>radeon</code> a des perfs ridicules sur ce GPU donc il va freezer au démarrage. Qu'il va y avoir une mise à jour de xserver-xorg un peu foireuse et que tout ce que le PC affichera au prochain reboot c'est :

<pre><code>Ubuntu 13.10 (tty1)
login: _
</code></pre>

Et que fatalement, on aura un coup de fil affolé : « <em>Mon PC il marche plus, j'ai rien fait, Linux c'est de la merde</em> »

<img src="https://aldarone.fr/wp-content/uploads/2014/04/gollum-scream.gif" alt="gollum-scream" width="500" height="208" class="aligncenter size-full wp-image-1506" />

On voudrait que les gens soient aussi passionnés d'informatique que nous et acceptent de passer 2 heures à chercher dans des wikis comment installer cette fichue imprimante multifonction en wifi. Mais ils le sont pas. Et ils le seront jamais.

<h2>Mais alors, tout est perdu ?</h2>

Non, tout n'est pas perdu. Le saut entre XP et 8 est à peu près aussi énorme -- sinon plus -- que le saut entre XP et n'importe quel dérivé d'Ubuntu. Et il nous faut sauter sur cette occasion.

Est-ce que nous préférons voir nos proches nous demander de l'aide parce qu'ils ont un peu de mal à utiliser GNU/Linux ou est-ce que nous préférons les voir entrer à la FNAC pour renouveler leur PC de bureau et en sortir avec un portable surdimensionné, une licence OEM de Windows 8 pleine de crapwares et un SecureBoot impossible à désactiver ?

De toute façon il vont pester et galérer parce qu'ils ont perdus leurs marques et que cette fichue interface fait pas ce qu'ils attendent. Autant qu'ils le fasse sur un système qui leur donnera le goût de la liberté.

Pour ça, il faut prendre nos responsabilités et assurer un vrai accompagnement derrière.

<blockquote>
  Oui, ça va être dur. Oui, tu vas perdre tes marques et t'auras l'impression de repartir de zéro. Mais ça arrivera aussi avec ce nouveau Windows. Et si tu prends GNU/Linux, je serais là pour te filer un coup de main quand tu en auras besoin.
</blockquote>

<img src="https://aldarone.fr/wp-content/uploads/2014/04/independance.gif" alt="independance" width="500" height="203" class="aligncenter size-full wp-image-1508" />

<h2>Étape par étape</h2>

Premièrement, il faut établir la liste des besoins et des particularités du matériel. L'imprimante est compatible ? (oui, elle l'est) Est-ce que le pilote est facile à installer ? Est-ce que ce logiciel obscur qui n'a pas d'équivalent fonctionne avec WINE ou <code>mono</code> ? Bref, là dessus on est rôdé c'est du classique.

Ensuite, il faut lever cette impression de voyage sans retour. C'est à dire ne PAS installer de dual-boot de but en blanc.

Installer une dérivée d'Ubuntu sur le PC, déjà ça prend une petite demi-heure, une heure avec les mises à jour si on est ni en Avril ni en Octobre, on peut rajouter le redimensionnement de partition (et donc la sauvegarde des données au cas où) etc. Ça fait peur à la personne qui assiste à ça et qui, à la fin, comprend pas pourquoi son PC a démarré tout seul sur Ubuntu alors qu'il fallait booter Windows<sup id="fnref:4"><a href="#fn:4" rel="footnote">3</a></sup>.

<img src="https://aldarone.fr/wp-content/uploads/2014/04/barney-why.gif" alt="barney-why" width="360" height="306" class="aligncenter size-full wp-image-1513" />

Heureusement, on peut facilement installer un GNU/Linux sur une clé USB, non pas comme LiveUSB mais comme système complet et persistant :

<blockquote>
  Tiens, quand t'as besoin de faire un truc précis tu démarres ton PC normalement pour pas être perdu. Et quand tu veux juste glandouiller, surfer un peu, tu mets cette clé avant d'allumer ton PC comme ça tu t'habitues doucement. Et quand t'en aura marre de Windows, tu viens me voir et on fera ce qu'il faut.
</blockquote>

Démarrer GNU/Linux devient aussi simple et indolore que d'<a href="https://aldarone.fr/wp-content/uploads/2014/04/4d-usb.jpg">insérer une clé USB dans un port</a> et l'utilisateur/rice est rassuré⋅e parce que son disque dur est intact.

Pour finir, il faut rester disponible et à l'écoute. On vous fait déjà le plaisir de mettre cette foutue clé de temps en temps, s'il faut attendre 3 jours pour avoir du support ou se faire envoyer chier, elle va vite finir aux oubliettes.

Et comme convertir quelqu'un ça prend du temps, je déconseille de s'amuser à migrer 15 gus à la fois sous peine d'être rapidement débordé⋅e. Ne mettons pas la charrue avant les bœufs, une personne satisfaite c'est déjà pas mal (et bien assez de boulot.)

Bref, peut-être que si on arrive à dépasser nos réactions viscérales de « Windows c'est caca » et à remettre notre discours au niveau des besoins plutôt que de rester dans l'idéologie nébuleuse pour le/la néophyte, on arrivera à faire monter ce fichu taux d'utilisation <a href="https://en.wikipedia.org/wiki/Usage_share_of_operating_systems#Desktop_and_laptop_computers">qui stagne à 1.5% depuis bien trop longtemps</a>.

<div class="footnotes">
<hr />
<ol>

<li id="fn:1">
Ça va faire à peu près 10 ans que Linux était compliqué il y a 4-5 ans.&#160;<a href="#fnref:1" rev="footnote">&#8617;</a>
</li>

<li id="fn:2">
Ça fait 5 ans que j'ai passé ma grand-mère à Linux il y a 3 ans.&#160;<a href="#fnref:2" rev="footnote">&#8617;</a>
</li>

<li id="fn:4">
Allumer le PC, aller faire un tour, oublier le timeout grub. <em>Oups</em>&#160;<a href="#fnref:4" rev="footnote">&#8617;</a>
</li>

</ol>
</div>
