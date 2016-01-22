---
ID: 782
post_title: >
  Windows 7, Lubuntu et Xubuntu sont dans
  un bateau
author: Alda
post_date: 2013-01-26 12:00:25
post_excerpt: ""
layout: post
permalink: >
  /windows-7-lubuntu-et-xubuntu-sont-dans-un-bateau/
published: true
bitlyURL:
  - http://ltch.fr/11YNt2d
  - http://ltch.fr/11YNt2d
---
<h1>De Windows 7…</h1>

<p><img src="https://aldarone.fr/assets/windows-7-boot-screen-205x153.jpg" alt="windows 7 boot screen" width="205" height="153" class="alignleft size-thumbnail wp-image-785" /></p>

<p>Il y a un peu moins d'un an, <a href="http://echarlotte.fr/">ma chère et tendre</a> qui utilisait Win7 sur son PC a attrapé un méchant ransomware qui passait par là (par une faille Java plus précisément.)</p>

<p>Elle a donc découvert avec horreur que la plupart de ses fichiers avaient été chiffrés à son insu et qu'un quelconque mafieux russe lui réclamait x€ pour les décoder.</p>

<p>Heureusement, <a href="http://www.malekal.com/">Malekal</a> avait la solution et proposait des liens vers les outils de désinfection adéquats.</p>

<p>Après plusieurs jours de désinfection et de récupération, il s'avérait qu'elle avait quand même perdu la plupart de ses photos et quelques autres documents dans la bataille. Sans compter tous les doublons de fichiers simplement renommés.</p>

<p>Elle se retrouvait donc avec des disque dur presque pleins et un système d'exploitation qui mettait plusieurs minutes à démarrer le moindre logiciel.</p>

<p>Ce fut l'occasion pour moi de faire un peu de sensibilisation à la sauvegarde et conservation des données (conseils que je n'applique absolument pas moi-même…) et aux failles de sécurités dans les plugins de navigateurs.</p>

<h1>… à peut-être Windows 8</h1>

<p><img src="https://aldarone.fr/assets/windows-8-clean-install-03-205x153.png" alt="windows 8 boot screen" width="205" height="153" class="alignright size-thumbnail wp-image-791" /></p>

<p>De mon côté, mon passage à Windows 8 était concluant et je songeais à y rester pour un moment si je trouvais un moyen de prolonger le compte à rebours de la Consumer Preview (limitée à 2 x 90 jours d'usage.)</p>

<p>Comme il fallait aussi réinstaller le PC de Charlotte un jour, autant faire le mien et le sien dans la foulée.</p>

<p>Mais voila, la Consumer Preview arrive à expiration et j'ai une flemme terrible à l'idée de réinstaller tous mes logiciels, restaurer mes données, etc… C'est pourquoi, de manière assez paradoxale, j'ai profité de l'occasion pour migrer vers… <a href="http://archlinux.fr/">Archlinux</a></p>

<p>En parlant de ça avec Charlotte, on envisage rapidement d'acheter une version mise à jour Win8 encore en promo à 30€. Mais j'aime pas les mises à jour, je veux quelque chose qui peut s'installer sur un PC vierge et s'il faut passer par une installation de Win7 pour pouvoir utiliser Win8, ce n'est pas la peine.</p>

<p>J'ai donc réussi à la convaincre de me laisser lui installer…</p>

<h1>Lubuntu</h1>

<p><img src="https://aldarone.fr/assets/TVVBS-205x153.png" alt="Lubuntu 12.10 Boot" width="205" height="153" class="alignleft size-thumbnail wp-image-793" /></p>

<p>Lubuntu que j'utilise depuis quelques temps sur mon netbook faiblard et qui fait bien son boulot (mieux que son affreuse grande sœur Ubuntu…)</p>

<p>La sauvegarde de ses fichiers effectuée, on passe à l'installation qui se déroule sans encombre puis vient le moment de paramétrer la résolution d'écran.</p>

<h2>Il fallait bien que quelque chose cloche</h2>

<p>De base, LXDE n'a pas l'air de savoir gérer le multi-écran. Il est bien possible de régler les résolutions et d'activer l'emploi des deux écrans mais ça reste sans effet et son moniteur 21' 16/10 reste à la même résolution que son compère de 17' 4/3 à savoir 1024x768.</p>

<p>Qu'à cela ne tienne, il y a Xrandr et Arandr pour nous aider. Mais là encore, couille dans le pâté, Xrandr ne reconnait pas la résolution native de l'écran qui est 1680x1050. Il y a eu divers essais infructueux, comme par exemple :</p>

<ul>
<li>Utiliser le pilote ATI</li>
<li>Forcer un mode avec <code>cvt</code> et <code>xrandr</code></li>
<li>Éditer <code>xorg.conf</code></li>
</ul>

<p>Puis je me suis résolu a aller acheter un câble DVI pour remplacer le VGA qu'elle utilisait. (Ce qui a réglé le problème immédiatement.)</p>

<h2>Les limites de LXDE</h2>

<p>Ensuite on s'est attaqué à la personnalisation de l'environnement et on a très vite buté sur un manque de fonctionnalités :</p>

<ul>
<li>Des thèmes incomplets, moches, qui ne s'intègrent pas correctement à toutes les applications (<em>non, je suis pas un noob, je parle pas uniquement des applis root</em>.)</li>
<li>Impossible de définir un fond d'écran différent par écran</li>
<li>Une gestion curieuse des icônes</li>
</ul>

<p>J'installe rapidement une alternative que je connais, apprécie et utilise au quotidien sur mon PC : <strong>XFCE</strong></p>

<p>Au premier lancement tout baigne, les tableaux de bord sont là, le gestionnaire de fenêtres aussi, je continue en installant Dropbox et l'excellent <a href="https://help.ubuntu.com/community/FolderEncryption#Gnome_Encfs_Manager">Gnome EncFS Manager</a> pour monter son dossier Boxcryptor sans mot de passe.</p>

<h2>Et là, c'est le drame</h2>

<p>Après un reboot pour vérifier que la session s'ouvre et que le dossier se monte sans problème tout se casse la gueule.</p>

<p>Visiblement, Lubuntu est pas taillée pour que les utilisateurs aient plusieurs environnements de bureau installés puisque <code>openbox</code> utilisé par LXDE démarre sans qu'on lui ait demandé son avis, du coup <code>xfwm</code> se vautre, emportant <code>openbox</code> avec lui. Les thèmes GTK décident eux aussi d'aller faire un tour et on se retrouve sur un bureau inutilisable, sans gestionnaire de fenêtres et avec le thème par défaut.</p>

<p>Une réinitialisation du profil n'y change rien, je décide donc de ne pas perdre plus de temps et d'installer…</p>

<h1>Xubuntu</h1>

<p><img src="https://aldarone.fr/assets/xubuntu12.10-login-screen-205x153.png" alt="xubuntu 12.10 login screen" width="205" height="153" class="alignright size-thumbnail wp-image-796" /></p>

<p>On repart donc de zéro sans plein de paquets alternatifs installés dans tous les sens.</p>

<p>Côté thème on reste simple aussi :</p>

<ul>
<li><a href="http://lassekongo83.deviantart.com/art/Zukiwi-313347909">Zukiwi</a> pour les contrôles. (Personnellement, j'utilise son équivalent vert : <a href="http://lassekongo83.deviantart.com/art/Zukini-272660042">Zukini</a>)</li>
<li><a href="http://tiheum.deviantart.com/art/Faenza-Icons-173323228">Faenza</a> pour les icônes. (Que je complète par <a href="http://tiheum.deviantart.com/art/Faience-icon-theme-255099649">Faience</a> chez moi)</li>
</ul>

<p>Il reste à installer <a href="https://launchpad.net/polly">un client Twitter</a> et <a href="http://www.spotify.com/fr/download/previews/">Spotify</a> et les besoin de Charlotte seront couverts. Mais pour ça, elle se débrouillera et elle vous racontera elle-même.</p>