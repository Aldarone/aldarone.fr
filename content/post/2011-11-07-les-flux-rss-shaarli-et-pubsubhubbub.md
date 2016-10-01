---
ID: 360
author: Alda
bitlyURL:
- http://bit.ly/sgWSAF
- http://bit.ly/sgWSAF
date: 2011-11-07T00:00:00Z
dsq_thread_id:
- "463622275"
- "463622275"
head_img:
- |
  https://aldarone.fr/assets/PubSubHubbub.png
- |
  https://aldarone.fr/assets/PubSubHubbub.png
head_img_alt:
- Logo de PubSubHubbub
- Logo de PubSubHubbub
post_date: 2011-11-07 08:45:44
post_excerpt: ""
post_title: Les flux RSS, Shaarli et PubSubHubbub
published: true
url: /les-flux-rss-shaarli-et-pubsubhubbub/
---

Derrière ces termes barbares se cache trois outils qui servent beaucoup à la diffusion du contenu sur internet.

<a href="http://fr.wikipedia.org/wiki/Flux_RSS">Les flux RSS</a>, vous le savez sûrement, c'est ce qui nous évite de faire tous les jours le tour de nos sites préférés comme sur internet avant 2000. <a href="http://sebsauvage.net/rhaa/index.php?2011/09/16/09/29/58-adieu-delicious-diigo-et-stumbleupon-salut-shaarli-">Shaarli</a>, c'est un équivalent de <a href="http://delicious.com/">del.ico.us</a>, codé par <a href="http://sebsauvage.net/">Monsieur Sebsauvage</a>, et ça sert à mettre de côté et partager les liens que l'ont trouve intéressant. Et <a href="http://www.webrankinfo.com/dossiers/indexation/pubsubhubbub">PubSubHubbub</a> c'est quelque chose d'assez récent qui s'articule avec les flux RSS pour apporter de l'instantanéité.

Dans un flux RSS normal, l'abonné demande périodiquement au fournisseur si il y a du nouveau. Si le fournisseur à une nouvelle, il se passera donc au maximum une période (de quelques minutes à quelques heures) avant que son abonné l'apprenne.

Dans un flux RSS compatible PubSubHubbub, il y a un intermédiaire en plus, un « hub » qui est prévenu automatiquement par le fournisseur dès qu'il y a du nouveau. Et le hub va à son tour prévenir les abonnés immédiatement.

Comme souvent, c'est une technologie poussée par Google qui l'utilise également pour Feedburner, Google Reader, Google Alerts mais aussi pour son service d'indexation (Le googlebot agissant comme un abonné, il est prévenu dès qu'il y a du nouveau contenu à ajouter à l'index)

Et comme souvent, Goole a libéré cette technologie ce qui fait que tout le monde peut l'utiliser pour rendre son flux compatible, créer son hub ou faire son client d'abonnement.

Pourquoi je vous parle de tout ça ? Parce que quand j'utilisais encore Google Reader pour partager mes liens, je les publiais en temps réel sur Twitter à l'aide du service <a href="http://reader2twitter.appspot.com/">Reader2Twitter</a>. Mais maintenant que j'utilise Shaarli (sur le mini site « <a href="http://share.aldarone.fr/">Les petits liens d'Alda</a>. » ) je me retrouvais à devoir attendre plus d'une demi-heure que <a href="http://twitterfeed.com/">Twitterfeed</a> vérifie mon flux et publie les nouveautés sur Twitter. Et une demi-heure à l'âge de l'instantanéité, c'est long.

J'ai donc retroussé mes manches et ai quelque peu modifié Shaarli pour:
<ol><li>Rendre les flux RSS et ATOM générés compatibles avec PubSubHubbub</li>
<li>Prévenir un des hubs choisi qu'il y a une mise à jour.</li></ol>

Il faut tout d'abord récupérer <a href="http://code.google.com/p/pubsubhubbub/source/browse/#svn/trunk/publisher_clients/php">la librairie disponible pour PHP sur le site de PubSubHubbub: Publisher.php</a>

Puis rajouter quelques lignes au fichier index.php de Shaarli:

<pre class="brush: php; highlight: [4,5,6,7,8,9,10,11,12,13,14,15,16,17]" title="Ligne 299">
// ------------------------------------------------------------------------------------------
// Misc utility functions:

// Update pubsubhubbub
// External library import
include './publisher.php';
$hub_url = 'http://pubsubhubbub.appspot.com/';
function pubsubhub()
{
        global $hub_url;
        $p = new Publisher($hub_url);
        $topic_url = array (
                        serverUrl().$_SERVER['SCRIPT_NAME'].'?do=atom',
                        serverUrl().$_SERVER['SCRIPT_NAME'].'?do=rss'
                     );
        $p-&gt;publish_update($topic_url);
}

// Returns the server URL (including port and http/https), without path.
// eg. "http://myserver.com:8080"
// You can append $_SERVER['SCRIPT_NAME'] to get the current script URL.
</pre>

<pre class="brush: php; highlight: [9,10,11,12]" title="Ligne 650">
// Ouput the last 50 links in RSS 2.0 format.
function showRSS()
{
    global $LINKSDB;

// ...    

     echo 'Shared linksfr-FR'.$pageaddr.''."nn";
    echo '<!-- PubSubHubbub Discovery -->
          
          
          <!-- End Of PubSubHubbub Discovery -->';
    $i=0;
    $keys=array(); foreach($linksToDisplay as $key=&gt;$value) { $keys[]=$key; }  // No, I can't use array_keys().

// ...

}
</pre>

<pre class="brush: php; highlight: [12,13,14]" title="Ligne 680">
function showATOM()
{
    global $LINKSDB;

// ...

    $feed='';
    $feed.='<title>'.htmlspecialchars($GLOBALS['title']).'</title>';
    if (!$GLOBALS['config']['HIDE_TIMESTAMPS'] || isLoggedIn()) $feed.=''.htmlspecialchars($latestDate).'';
    $feed.='';
    $feed.='<!-- PubSubHubbub Discovery -->
            
            <!-- End Of PubSubHubbub Discovery -->';
    $feed.=''.htmlspecialchars($pageaddr).'';
    $feed.=''.htmlspecialchars($pageaddr).''."nn"; // Yes, I know I should use a real IRI (RFC3987), but the site URL will do.
    $feed.=$entries;
    $feed.='';
    echo $feed;
    exit;
}
</pre>

<pre class="brush: php; highlight: [8]" title="Ligne 1030">
    // -------- User clicked the "Save" button when editing a link: Save link to database.
    if (isset($_POST['save_edit']))
    {
        
// ...

        $LINKSDB-&gt;savedb(); // save to disk
        pubsubhub();
        invalidateCaches();

        // If we are called from the bookmarklet, we must close the popup:

// ...
        exit;
    }
</pre>

Une fois ces modifications effectuées, il ne reste plus qu'à attendre que les abonnés demandent une mise à jour du flux. Ensuite s'ils sont compatibles, ils passeront en mode PubSubHubbub. Pour tester c'est très simple, il suffit de créer un flux feedburner. De base il se met à jour tous les quarts d'heure, avec PubSubHubbub activé c'est instantané.

Concernant la mise à jour des liens sur twitter, Twitterfeed avait annoncé la compatibilité en 2010 mais il a quand même fallu attendre plus de 30min avant de voir mes liens apparaître. Je suis donc passé à <a href="http://dlvr.it/">dlvr.it</a> qui a une fréquence de mise à jour minimum de 15min et qui permet de cocher une case pour activer PubSubHubbub. Les liens n'arrivent toujours pas en temps réel (il faudrait pour ça que je monte mon propre client je suppose) mais les 5 minutes que j'ai constaté sont un délai déjà plus acceptable.