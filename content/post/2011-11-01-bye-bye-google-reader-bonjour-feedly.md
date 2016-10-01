---
date: 2011-11-01T00:00:00Z
head_img:
- https://aldarone.fr/assets/Feedly.png
head_img_alt:
- Feedly Logo
title: "Bye bye Google Reader, bonjour Feedly"
slug: "bye-bye-google-reader-bonjour-feedly"
---

Google l'avait <a href="http://googlereader.blogspot.com/2011/10/upcoming-changes-to-reader-new-look-new.html">annoncé il y a quelques jours</a>, Google Reader allait subir une refonte. J'aurais pu dire « bénéficier d'une mise à jour » si j'avais été positif mais « subir » est le bon mot.

Soyons honnête, l'interface native de Google Reader était assez moche. Personnellement j'utilisais l'extension Stylish (disponible pour <a href="https://addons.mozilla.org/fr/firefox/addon/stylish/" title="Stylish pour Firefox">Firefox</a> et <a href="https://chrome.google.com/webstore/detail/fjnbnpbmkenffdnngjfgmeleoegfcffe" title="Stylish pour Chrome">Chrome</a>) pour lui appliquer une CSS nommée « <a href="http://userstyles.org/styles/17120/google-reader-simple-and-clean">Simple &amp; Clean</a> » (rapidement modifiée pour utiliser la police Ubuntu au lieu d'Helvetica)

Avec la refonte appliquée ce matin, forcément ma CSS ne fonctionnait plus mais pire : les webdesigners de google ont réussi à rendre l'interface encore plus moche. Il parait que c'est pour s'intégrer à la charte de Google+ mais on est franchement en dessous de la refonte de Gmail, de l'Agenda et de Docs. Tout est gris et gras et comble de l'horreur, les fonctions de partages d'article ont été remplacées par un bouton +1.

Ce qui fait la force de Google Reader à mon sens (outre le fait d'avoir ses flux RSS en ligne) c'est aussi la possibilité de partager les articles que l'on trouve intéressants, de découvrir de nouveaux flux et de s'abonner aux flux partagés par d'autres qui étaient alors intégrés directement dans l'interface, comme un flux classique. Là, il ne reste plus rien. Pour suivre les partages il va falloir quitter Reader et se rendre sur G+.

Ça ne me convient pas et je me suis donc mis à la recherche d'alternatives.

<h2>L'auto-hébergement</h2>

Première solution qui semble évidente pour moi : installer un lecteur de flux en php sur mon serveur. De manière étonnante ça ne court pas les rues puisqu'on a deux maigres solutions opensource qui se battent en duel : <a href="http://tt-rss.org/redmine/">Tiny Tiny RSS</a> et <a href="http://rsslounge.aditu.de/">RSSLounge</a> (avec RSSLounge dans le rôle du challenger favori pour le moment.)

Je met de côté <a href="http://feedafever.com/">Fever</a> qui séduit beaucoup semble-t-il mais il est privateur et payant et n'a donc aucun intérêt en auto-hébergement.

Le problème : Les fonctions de partage se résument à Twitter et Facebook, la mise à jour des flux n'est pas automatique (elle se fait à la consultation et il faut donc mariner le temps que mes 1000 abonnements s'actualisent) et la découverte de nouveaux flux similaires est inexistante.

Il y a encore des progrès à faire mais je garde un œil là dessus.

<h2>Les solutions externes</h2>

La première alternative à Reader qui me vient à l'esprit est Netvibes que j'ai pas mal utilisé au moment de leur dernière grosse mise à jour. Mais j'ai fini par revenir chez Google car il était impossible d'afficher les articles les plus anciens en premier. Là vous commencez à me trouver tatillon un peu non ?

Puis quelqu'un a recommandé <a href="http://feedly.com/">Feedly</a> sur twitter. Je l'avais testé il y a fort fort longtemps mais à l'époque il ne proposait qu'une vue « Magazine » qui ne me convenait pas du tout.

De l'eau a coulé sous les ponts et après une matinée de test je dois dire que je suis séduit.

<h2>Le fonctionnement de Feedly</h2>

Feedly gère les flux de manière synchronisée à Google Reader, la migration est donc on ne peut plus simple puisqu'il n'y a même pas à exporter et réimporter ses flux ailleurs. On récupère donc l'intégralité des données : Dossiers, articles lus, articles partagés, etc...

La contrepartie est que Feedly est entièrement dépendant de Google. Et peut-être qu'un jour ils fermeront les vannes (<a href="http://googlegeodevelopers.blogspot.com/2011/10/introduction-of-usage-limits-to-maps.html" title="API Google Maps limitée à 25000 requetes">comme ils le font actuellement avec Google Maps</a>.)

L'interface est claire, les boutons de partage sont à portée de clic, plein de façons d'afficher les articles sont disponibles (la vue « Magazine » forcément mais également en mode « Titres seulement », « Résumé », « Complet » ou encore « Miniatures » ), les options de classements sont toutes là aussi et cerise sur le gâteau : c'est également le cas des raccourcis de navigation ( « j » et « k » pour naviguer dans la liste mais bien d'autres. Il suffit d'appuyer sur « ? » pour en afficher la liste.)

Le seul point noir que je lui trouve, c'est la pagination. Il y a 20 articles par page et, certes, on passe à la page suivante/précédente facilement mais il y a du coup une petite latence un peu gênante quand on a beaucoup de flux non lus.

Pour accéder au service, il faut installer l'extension Feedly pour <a href="https://addons.mozilla.org/fr/firefox/addon/feedly/" title="Extension Feedly pour Firefox">Firefox</a> ou <a href="https://chrome.google.com/webstore/detail/hipbfijinpcgfogaopmgehiegacbhmob" title="Extension Feedly pour Chrome">Chrome</a> ce qui ajoute un raccourci dans la barre d'icônes (malheureusement sans compteur d'articles non lus) et le reste est automatique.

L'extension ajoute également un petit bouton à moitié transparent nommé Feedly-mini en bas à droite de chaque site (il est évidemment possible de le désactiver dans les options.) Il permet de s'abonner rapidement aux flux du site consulté ou encore de partager la page sur twitter, facebok, e-mail, etc...
