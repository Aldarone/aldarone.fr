---
date: 2011-11-08T00:00:00Z
head_img:
- https://aldarone.fr/assets/cookies.jpg
head_img_alt:
- Cookies
title: "Intégrez les videos youtube en HTTPS et sans cookie sur votre blog wordpress"
slug: "integrez-les-videos-youtube-en-https-et-sans-cookie-sur-votre-blog-wordpress"
---

Beaucoup de gens l'ignorent (moi-même jusqu'à la semaine dernière…) mais il est possible de consulter Youtube de manière sécurisée et sans se faire suivre par tout un tas de cookies.

Depuis la version 2.9, wordpress gère nativement la découverte oEmbed qui permet aux sites comme youtube, flickr, twitter et bien d'autres de fournir automatiquement le code d'intégration d'une video ou d'une photo à celui qui le demande.

C'est ainsi qu'en collant une URL youtube sur une ligne vide, wordpress est capable d'afficher automatiquement le lecteur flash aux visiteurs. Mais par défaut, il intègre la video depuis http://youtube.com.

Pour plus de confidentialité, j'ai créé un petit plugin (30 lignes, excusez du peu) qui va dire à wordpress de récupérer le code depuis la version sécurisée et confidentielle de youtube: https://www.youtube-nocookie.com. Et bien sûr dans une iframe afin d'être compatible avec les terminaux mobiles.

<pre class="brush: php">
/*
Plugin Name: Youtube oEmbed NoCookie/SSL
Plugin URI: https://aldarone.fr/
Description: Ce plugin sert à intégrer les videos youtube en utilisant une iframe, le protocole HTTPS et le domaine nocookie de youtube.
Version: 1.0a1
Author: Alda Marteau-Hardi
Author URI: https://aldarone.fr/
License: CC BY-NC-SA
*/

wp_embed_register_handler('youtube_ssl', '#http://(?:www.youtube.com/watch?v=|youtu.be/)([a-z0-9_-]+)#i', 'wp_embed_handler_youtube_ssl');

function wp_embed_handler_youtube_ssl( $matches, $attr, $url, $rawattr ) {
    // If the user supplied a fixed width AND height, use it
    if ( !empty($rawattr['width']) &amp;&amp; !empty($rawattr['height']) ) {
        $width  = (int) $rawattr['width'];
        $height = (int) $rawattr['height'];
    } else {
        list( $width, $height ) = wp_expand_dimensions( 420, 315, $attr['width'], $attr['height'] );
    }
    $embed = sprintf(
                 '',
                 esc_attr($width),
                 esc_attr($height),
                 esc_attr($matches[1])
             );
    return apply_filters('embed_youtube_ssl', $embed, $matches, $attr, $url, $rawattr);
}
</pre>

Si vous utilisiez cette fonction de wordpress (qui permet d'intégrer la video simplement en copiant l'url dans une nouvelle ligne, ou avec le shortcode [embed]) vous n'avez rien à changer. Une fois le plugin activé vos videos s'afficheront dans une iframe sécurisée et sans cookies. A noter que le plugin gère les attribut « width » et « height » du shortcode [embed] et que ça fonctionne aussi avec le domaine raccourci youtu.be.

<strong>Trucs à faire</strong> :
<ul><li><del datetime="2011-11-10T10:30:29+00:00">Prendre en compte les options du player passées dans l'URL.</del></li>
<li>Créer une page d'option pour régler certains paramètres par défaut:
 <ul>
 <li><del datetime="2011-11-17T09:03:47+00:00">Choix entre <code>iframe</code> (pour ceux qui tiennent à la compatibilité iPhone) et <code>object</code> (pour ceux qui tiennent aux standards du web)</del></li>
 <li>Format du lecteur (4/3, 16/9, 16/10, personnalisé.)</li>
 <li>Afficher les videos similaires.</li>
 <li>Masquer les contrôles, seulement la barre de progression, tout afficher.</li>
 </ul></li>
</ul>

<strong>Mise à jour 1.0.1 (17/11/2011)</strong> :
<ul><li>Ajout du plugin dans le dépot wordpress (ça facilite les mises à jour et ça apporte un peu de visibilité)</li>
<li>Changement du nom du plugin: Youtube Privacy</li>
<li>Ajout du panel d'option avec pour l'instant la possibilité de choisir d'utiliser une iframe ou un object. (l'iframe est compatible iPhone et Opera mobile, object est valide en xhtml strict)</li>
</ul>

<strong>Mise à jour 1.0a2 (10/11/2011)</strong> :
<ul><li>Première mise à jour du plugin, je laisse tomber l'iframe pour utiliser la balise object qui est plus recommandée par les instances supérieures du web. (Du coup ça marche plus sous iPhone, merci Apple.)</li>
<li>Les options du player passées dans l'URL sont à présent prises en compte (la liste se trouve ici: <a href="http://code.google.com/intl/fr-FR/apis/youtube/player_parameters.html">YouTube Embedded Player Parameters</a>)</li>
<li>Vous pouvez également lancer la lecture directement à un moment donné. Par exemple en rajoutant <code>#t=1m10s</code> la lecture se lancera à 1 minute et 10sec de video.</li>
<li>La taille du player passe d'un ratio de 4/3 à 16/9 et les contrôles disparaissent après quelques secondes (et réapparaissent en bougeant la souris bien sûr)</li>
</ul>

<a href="http://wordpress.org/extend/plugins/youtube-privacy/">Télécharger le plugin Youtube Privacy</a> (Si vous avez téléchargé une version à partir de cet article, merci de la supprimer et de la réinstaller à partir du dépot wordpress. Sinon pas de mise à jour automatique et sûrement un conflit entre les deux)
