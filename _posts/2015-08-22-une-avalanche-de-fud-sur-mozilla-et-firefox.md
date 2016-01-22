---
ID: 1613
post_title: >
  Une avalanche de FUD sur Mozilla et
  Firefox.
author: Alda
post_date: 2015-08-22 15:04:57
post_excerpt: ""
layout: post
permalink: >
  /une-avalanche-de-fud-sur-mozilla-et-firefox/
published: true
---
<strong>Attention</strong> : Cet article est un peu technique et certaines notions risquent de vous échapper si vous n'avez pas quelques connaissances de base en développement web.

Depuis l'introduction d'un bouton Pocket dans Firefox il ne se passe pas une seule semaine (j'aurais pratiquement même tendance à dire « un seul jour » au point où on en est) sans que Mozilla se prenne un nouveau FUD dans la face.

<h2>Petite définition de FUD :</h2>

FUD est un acronyme signifiant « Fear, uncertainty and doubt » ou, en français : « Peur, incertitude, doute »

C'est généralement une stratégie marketing organisée par une entreprise pour dénigrer un concurrent en semant la peur, l'incertitude et le doute dans l'esprit des clients.

Il s'agit de manipuler une information pour la parsemer d'hypothèses et de conditionnel afin de la rendre angoissante. La répétition de cette manipulation ancre le FUD dans l'inconscient collectif et le rend plus efficace.

<h2>Les derniers FUD auquel Mozilla a du faire face :</h2>

<h3>Firefox Social API, ou Facebook dans mon Firefox</h3>

Celui là est assez vieux et il a fini par être oublié. En 2012, Mozilla active la Social API dans Firefox Beta et <a href="https://blog.mozilla.org/futurereleases/2012/10/22/help-us-test-the-social-api-with-facebook-messenger-for-firefox/">lance un appel à testeures</a> pour essayer leur intégration de Facebook Messenger.

Cette API est très simple et se configure à l'aide d'une bête chaine en JSON passée au navigateur à l'aide d'un évènement Javascript. En gros, on indique un nom, quelques urls et l'emplacement de boutons et de cadres.

Ensuite Firefox demande confirmation aux utilisateurices pour l'activation du module et le navigateur se charge d'afficher le contenus des pages référencées dans les cadres définis.

Si vous voulez voir un exemple d'implémentation, j'ai participé en mai à l'ajout du <a href="https://github.com/shaarli/Shaarli/commit/8b3c67fccbe7e68b304d3071b1f7a77e0f1fc048#diff-103112dc6ce11f478e58961c697d9931R18">module Social API sur Shaarli</a>. Comme on peut le voir c'est très simple et très innocent.

Pourtant, dès cette annonce on a pu voir des inquiets s'agiter et répéter à tort et à travers que Facebook s'infiltrait dans un module propriétaire de Firefox, que c'était la fin de la protection de la vie privée par Mozilla, une pluie de pierre et de feu, sacrifices humains, copulation entre chiens et chats, etc.

En dépit du fait que Mozilla avait accompagné un article expliquant que les modules Social n'avaient accès à aucune information (à l'exception de l'URL et de la description de la page quand l'utilisateure cliquait sur « Partager » évidemment) : <a href="https://blog.mozilla.org/privacy/2012/10/22/being-social-with-privacy-in-mind/">Being social with privacy in mind</a>

<blockquote>
  This new functionality doesn’t give your social network access to any additional information from your browser. Again: it’s a lot like having a tab open to your social network.
</blockquote>

Trois ans plus tard la Social API est largement tombée dans l'oubli, Facebook a supprimé la page d'activation du module et les gens ont heureusement oublié que « Facebook est intégré par défaut dans Firefox »

<h3>Firefox Hello</h3>

Un peu sur le même modèle mais beaucoup plus récent, fin 2014, <a href="https://blog.mozilla.org/futurereleases/2014/10/16/test-the-new-firefox-hello-webrtc-feature-in-firefox-beta/">Mozilla annonce l'arrivée de Firefox Hello</a>. Un bouton permettant la discussion instantanée directement dans Firefox en utilisant le protocole WebRTC.

Pour l'occasion ils ont fait un partenariat avec TokBoxi (propriétée de Telefonica), spécialiste dans les communications WebRTC, pour utiliser leur plateforme.

Rebelote, Mozilla a vendu la vie privée de ses utilisateuricess avec une extension privatrice rendue obligatoire qui ralenti incroyablement Firefox et qui espionne leurs moindres faits et gestes.

Alors que le bouton ne fait strictement rien tant qu'on ne clique pas dessus, de même que son affichage ne ralenti par Firefox puisque les boutons de barre d'outils sont chargés de manière asynchrone.

<h3>Firefox Pocket integration</h3>

C'est cette fois en Juin 2015 que Mozilla annonce <a href="https://blog.mozilla.org/blog/2015/06/02/firefox-puts-you-in-control-of-your-online-life/">l'intégration d'un bouton Pocket dans Firefox</a>. Pocket est un service de marque-page dont le principal intérêt est sa capacité à reformater le contenu des pages qu'on y enregistre pour qu'elles soient plus lisibles.

Ici encore, sacrifice de la vie privée, espionnage des utilisateurs, ralentissements du navigateur.

Je vais quand même faire une mention spéciale à Numérama pour le titre le plus imbécilement racoleur et mensonger qu'il m'ait été donné de voir parmis tous les articles alarmistes sur le sujet : <a href="http://www.donotlink.com/gf33">« L'add-on Pocket imposé par Mozilla sur Firefox avait une faille »</a>

Notez l'élément de langage : « imposé » quand le simple fait de masquer le bouton en deux clic désactive effectivement l'add-on en question. Et notez également que la faille dont il est question ici n'a absolument rien à voir avec cet addon mais plutôt avec l'infrastructure de Pocket. Pour preuve, on peut lire <a href="https://www.gnu.gl/blog/Posts/multiple-vulnerabilities-in-pocket/">l'article expliquant les détails de la faille</a> et on peut également utiliser son cerveau et réaliser que Mozilla n'a publié aucun correctif en rapport avec Pocket au moment où la faille a été corrigée.

Comme avec Firefox Hello, le bouton ne fait toujours rien tant qu'on ne clique pas dessus, son affichage ne ralenti toujours pas Firefox et le simple fait de l'enlever de la barre d'outil désactive l'exécution du code d'affichage du bouton (logique).

<h3>La signature obligatoire des add-ons</h3>

En février 2015, Mozilla annonce que <a href="https://blog.mozilla.org/addons/2015/02/10/extension-signing-safer-experience/">Firefox refusera de lancer les add-ons qui n'ont pas été signés sur addons.mozilla.org</a> (Aussi appelé AMO). Cette décision est motivée par la sécurité des utilisateurs et vise à analyser le code de toutes les extension Firefox afin d'interdire celles qui tenteraient des choses curieuses comme envoyer le contenu de vos fichiers ou la liste de vos mots de passe sur un serveur distant. (Oui, les add-ons peuvent faire ça.)

L'initiative vise aussi à diminuer le nombre de barres d'outils et de malware publicitaires installés par des programmes comme… Flash Player.

Si les utilisateurices de Firefox peuvent se satisfaire d'un add-on installé de base qu'il est possible de désactiver, avec la signature obligatoire on touche là au cœur même de la liberté des gens puisque la première plainte émise a été de ne plus pouvoir télécharger ses add-ons ailleurs que sur AMO, d'ouvrir la porte à la voie de la censure et de transformer Mozilla en dictature de la pensée unique (rien que ça).

Pourtant, rien de tout ça n'est fondé.

Les extensions qui sont déjà sur AMO sont déjà soumise à une procédure de vérification. Elle est manuelle, effectuée par des bénévoles, la vérification peut prendre plusieurs jours. Et ça fait bien longtemps que personne ne s'en est plain. Ces add-ons seront signés automatiquement.

Les extensions qui ne sont pas sur AMO, et là est la nouveautée, seront soumises à une vérification automatique puis signées. Si la vérification automatique échoue c'est une vérification manuelle qui aura lieu, la même que celle pour les add-ons de l'AMO. Après signature, le/la développeureuse récupère le fichier xpi de l'extension et est libre de le distribuer où bon lui semble.

Avant signature et pendant le développement de l'add-on il faudra utiliser Firefox Aurora ou Firefox Developper Edition pour lancer des add-ons non signés.

Le point faible de tout ça reste la procédure de review manuelle. À titre d'exemple <a href="https://github.com/EFForg/https-everywhere/issues/2051#issuecomment-130513727">ça fait 9 mois que HTTPS Everywhere est en review sur l'AMO</a>, étant un add-on soutenu par l'EFF ils ont pu obtenir une signature rapide en demandant directement à Mozilla mais tout le monde n'est pas l'EFF.

Mozilla est bien conscient de ça et prévoit d'améliorer le processus de vérification automatique ainsi que d'augmenter la taille des équipes salariées et bénévoles pour la vérification manuelle.

<h3>La fin des add-ons XUL et SDK</h3>

Hier, le 21 Août 2015, Mozilla annonce <a href="https://blog.mozilla.org/addons/2015/08/21/the-future-of-developing-firefox-add-ons/">l'obsolescence des add-ons classiques qui utilisent XUL, des add-ons jetpack et des add-ons SDK</a> pour introduire une nouvelle API d'add-on qui sera majoritairement compatible avec celle utilisée par Chrome et Opera mais qui sera étendue pour maintenir l'existence d'add-ons populaires existants.

La raison avancée est que les add-ons dépendant d'interface bas niveau empêchent les évolutions du navigateur. Electrolysis qui doit apporter le support du multi-process et le sandboxing des onglets a largement été retarder à cause d'incompatibilité avec des extensions très utilisées. Il est impossible de remplacer le Gecko vieillissant par Servo pour les mêmes raisons.

Mettre en place une API limitera, certes, les possibilités de développement d'add-ons mais permettra en même temps de faire des changement profonds dans le fonctionnement de Firefox sans trop s'inquiéter de voir tous les add-ons crasher dans tous les sens.

Les réactions FUDesques ne sont sont pas fait attendre et <a href="http://www.downthemall.net/the-likely-end-of-downthemall/">le développeur de DownThemAll! a été le premier à s'enflammer</a> en déclarant la mort de DownThemAll, NoScript ou Greasemonkey.

Bref, c'est la fin de la personnalisation dans Firefox qui achève une transformation en clone de Chrome, transformation entamée avec l'arrivée de l'interface Australis apparue dans les nightlies fin 2013.

Dans <a href="https://linuxfr.org/users/kalenx/journaux/la-fin-du-permissive-add-on-model-chez-mozilla-ou-comment-flinguer-une-base-d-extensions">les journaux LinuxFR</a> c'est la panique également puisqu'on apprend ceci :

<blockquote>
  L'impossibilité d'accéder au coeur de Firefox et de son interface mènera à la disparition d'extensions extrêmement appréciées et utilisées telles que, outre DownThemAll, TreeStyleTab, NoScript, FireGestures, Drag2Go, Greasemonkey, TabMixPlus, FireFTP, FoxyProxy, AllInOne Sidebar et beaucoup d'autres.
  
  Comprenons-nous bien : on ne parle pas ici d'un classique cassage d'API qui requiert la réécriture de certaines parties de ces extensions pour les rendre compatibles. Non, on parle d'un changement qui rendra ces extensions impossibles à implémenter en tout ou en partie.
</blockquote>

Ou encore que l'API n'est pas officiellement publiée alors qu'il reste 18 mois à vivre aux extensions old-school.

Là encore, rien n'est fondé puisque dans l'article même de cette annonce, Mozilla donne le lien vers la documentation actuelle : <a href="https://wiki.mozilla.org/WebExtensions">WebExtensions</a> sur laquelle figure des liens vers les modules et fonctions supportées, les fonctions qui ne sont pas encore implémentées, une mention indiquant qu'elles le seront prochainement <strong>ainsi qu'une liste de fonctions non supportées par Chrome qui seront conservées dans Firefox pour garder des extensions en vie</strong> :

<blockquote>
  We plan to add our own APIs based on the needs of existing Firefox add-ons :
  
  <ul>
  <li><strong>NoScript</strong>-type functionality. This would come in the form of extensions to webRequest and possibly contentSettings.</li>
  <li>Sidebars. Opera already supports sidebar functionality; Chrome may soon. We would like to be able to implement <strong>Tree Style Tabs</strong> or <strong>Vertical Tabs</strong> by hiding the tab strip and showing a tab sidebar.</li>
  <li>Toolbars. Firefox has a lot of existing toolbar add-ons.</li>
  <li>Better keyboard shortcut support. We'd like to support <strong>Vimperator</strong>-type functionality.</li>
  <li>Ability to add tabs to about:addons.</li>
  <li>Ability to modify the tab strip (<strong>Tab Mix Plus</strong>).</li>
  <li>Ability to take images of frames/tabs (like canvas.drawWindow)</li>
  </ul>
</blockquote>

On voit bien que contrairement à ce qui est colporté, Mozilla est conscient de la nécessité de préserver l'existence de nombreuses extensions et qu'ils ne se priveront pas d'aller plus loins que l'API de Chrome pour le faire.

En bref, les extensions Chrome seront facilement portables sur Firefox, les extensions simple de Firefox seront facilement portable sur Chrome et les extensions plus lourdes conserveront leurs fonctionnalités avancées.

<h2>Conclusion</h2>

Je suis prêt à admettre qu'une certaine inquiétude puisse se faire sentir devant tous les changements opérés par Mozilla cette année mais il me semble qu'une fois contextualisés ces changements deviennent soit compréhensibles même si pas idéaux, soit justifiés.

Hello et Pocket résultent de partenariats commerciaux. On le sait et elle était extrêmement critiquée pour ça, Mozilla dépendait grandement du financement de Google (<a href="http://techcrunch.com/2012/11/15/mozilla-releases-annual-report-for-2011-revenue-up-33-to-163m-majority-from-google/">85% en 2011</a>) pourtant et pour s'en détacher, c'est Yahoo qui devient le nouveau moteur par défaut en Novembre 2014 et on imagine bien qu'ils n'ont pas la puissance financière d'un Google.

Mozilla se trouve donc obligée de diversifier ses partenariat et jusqu'à présent en parvenant avec succès à protéger la vie privée de ses utilisateurices.

Du côté des add-ons, il s'agit de choix techniques qui visent à diminuer le nombre de malwares infectant le navigateur et à permettre plus facilement la réduction de dette technique présente dans Gecko.

J'ai, en revanche du mal à saisir ce qui pousse des gens qui ont tout à perdre de la défection de Firefox à propager des articles alarmistes et infondés pour manifester leur inquiétude.

Le seul effet que ces critiques ont est de ternir l'image d'un Firefox qui n'en a pas besoin et d'affaiblir le seul navigateur Libre et indépendant, poussant les gens à… utiliser Chrome.

À suivre : <a href="https://aldarone.fr/que-fait-firefox-sur-le-reseau-quand-on-le-demarre-et-faut-il-y-remedier/">Les requêtes envoyées par un Firefox tout neuf</a>.