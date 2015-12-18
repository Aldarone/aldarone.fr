---
ID: 776
post_title: Désactiver PDF.js dans Firefox
author: Alda
post_date: 2013-01-12 12:28:14
post_excerpt: ""
layout: post
permalink: >
  http://aldarone.fr/desactiver-pdf-js-dans-firefox/
published: true
bitlyURL:
  - http://ltch.fr/X0PsMw
  - http://ltch.fr/X0PsMw
---
<p>La version 18 de Firefox pointe le bout de son nez et déjà le canal beta adopte la version 19.</p>

<p>Une des nouveautés de cette version (la 19 donc) est l'activation par défaut du plugin PDF développé en Javascript par mozilla : PDF.js</p>

<p>Si ce plugin est très utile (les novices n'auront plus à installer l'infâme usine à gaz qu'est Adobe Reader) il a aussi un support encore trop limité et ne permet pas de lire au mieux tous les PDFs.</p>

<p>Manque de bol, son activation dans Firefox est fait de manière que je qualifierai de douteuse. En effet, il ne lui importe pas que l'utilisateur ait déjà un plugin PDF actif et en soit satisfait, dès le premier lancement, PDF.js prend le dessus.</p>

<p>On serait tenté d'aller jeter un œil dans les modules complémentaires, onglet « plugins » pour le désactiver mais il n'y apparaît pas.</p>

<p>En cherchant un peu, on trouve une option <code>pdfjs.disabled : false</code> dans <code>about:config</code>, quand on la passe à <code>true</code> et qu'on redémarre Firefox, le plugin est bien désactivé mais la seule option qu'il reste est de télécharger le PDF alors que nous voulons l'ouvrir dans le navigateur.</p>

<p>Il faut chercher encore un peu l'option <code>plugin.disable_full_page_plugin_for_types : application/pdf</code>, la supprimer et redémarrer Firefox pour qu'enfin, notre plugin PDF préféré puisse agir à nouveau.</p>

<p>Bien sûr ce n'est encore qu'une Beta, espérons que Mozilla trouve un moyen de rendre la désactivation de PDF.js plus accessible. (Même si ça se résume à écrire la doc pour le faire…)</p>

<h2>TL;DR;</h2>

<ol>
<li>Taper <code>about:config</code> dans la barre d'adresse</li>
<li>Chercher <code>pdfjs.disabled</code> et le passer à <code>true</code></li>
<li>Chercher <code>plugin.disable_full_page_plugin_for_types</code> et supprimer <code>application/pdf</code></li>
<li>Redémarrer Firefox</li>
</ol>