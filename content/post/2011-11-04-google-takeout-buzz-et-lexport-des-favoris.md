---
date: 2011-11-04T00:00:00Z
head_img:
- |
  https://aldarone.fr/assets/DataLiberationFront.jpg
head_img_alt:
- Data Liberation Front
title: "Google Takeout, Buzz et l'export des favoris"
slug: "google-takeout-buzz-et-lexport-des-favoris"
---

Comme annoncé dans un article précédent, Google Reader a mis fin aux partages d'articles comme on le connaissait. Dommage pour moi, je m'en servais aussi comme outil de bookmarking (un peu comme ce que d'autres font avec Delicious)

J'ai pu trouver la liste de ces partages en bidouillant des URL (genre ils sont cachés ici: <a href="http://www.google.com/reader/shared/06987377928849278758">http://www.google.com/reader/shared/06987377928849278758</a>, la solution sautait aux yeux dès le départ !) mais il ne fait aucun doute que ça va bientôt disparaître, cette page comme mes liens. Donc il me fallait un moyen de les récupérer.

Heureusement, avec la sortie de Google+, Google a rendu disponible un outil nommé Google Takeout (développé par un groupuscule interne: le Data Liberation Front, les joyeux drilles sur la photo ci-dessus) qui promet de nous permettre de télécharger toutes les données que Google a sur nous. Je m'attendais donc à voir une belle option: « Google Reader » dans la liste. Mais non.

<img src="https://aldarone.fr/wp-content/uploads/2011/11/GoogleTakeout01.png" alt="Les options de Google Takeout" title="Google Takeout" width="540" height="300" class="aligncenter size-full wp-image-345" />

C'est là que je me suis souvenu que les partages Google Reader se retrouvaient automatiquement sur Buzz. Logiquement en téléchargeant mes données Buzz je devrais récupérer ce que j'ai partagé (je ne m'en suis jamais servi autrement que via Reader…)

Et effectivement, Google me propose un fichier zip contenant 287 fichiers html. Oui, un fichier par partage:

<a class="picture" href="https://aldarone.fr/wp-content/uploads/2011/11/screenshot.10.png"><img src="https://aldarone.fr/assets/screenshot.10-540x421.png" alt="screenshot.10" title="screenshot.10" width="540" height="421" class="aligncenter size-large wp-image-346" /></a>

Et ce n'est même pas une capture de la page partagée : il n'y a que la photo de profil, et le lien:

<a class="picture" href="https://aldarone.fr/wp-content/uploads/2011/11/screenshot.11.png"><img src="https://aldarone.fr/assets/screenshot.11-540x53.png" alt="screenshot.11" title="screenshot.11" width="540" height="53" class="aligncenter size-large wp-image-347" /></a>

Ce n'est donc pas décemment exploitable. J'ai donc passé mon après-midi sur une solution permettant de regrouper tous ces liens et d'en faire un fichier bookmarks.html au format Netscape qui puisse être importé dans tous les navigateurs et services de bookmarking. Ça tombe bien, j'apprends le PHP, c'est un bon exercice.

Étant débutant, il se peut que vous trouviez des choses un peu aberrantes, des endroits où le code peut être optimisé. J'ai fait au mieux de mes compétences actuelles, n'hésitez pas à me corriger si vous voyez quelque chose qui vous choque.

Il me fallait d'abord un outil simple pour parcourir le code HTML et récupérer les éléments nécessaires, j'ai trouvé mon bonheur avec « <a href="http://simplehtmldom.sourceforge.net/">PHP Simple HTML DOM Parser</a>. » Ensuite il me fallait des infos sur la norme des bookmarks.html, j'ai trouvé ma réponse <a href="http://msdn.microsoft.com/en-us/library/aa753582%28v=vs.85%29.aspx">chez Microsoft</a>.

Le minimum est là, on peut donc commencer:

<pre class="brush: php">
    $file = file_get_contents('./buzz/example.html');
    $html = str_get_html($file);
    $title = $html-&gt;find('div[class=entry-title]', 0)-&gt;plaintext;
    $date = $html-&gt;find('abbr[class=published]', 0)-&gt;title;
    $link = $html-&gt;find('div[class=entry-content]', 0)-&gt;first_child()-&gt;href;

    echo '<DT><A HREF="'.$link.'">'.$title.'</A></DT>'."n";

    $html-&gt;clear();
    unset($html);
</pre>

Les problèmes qui se présentent à ce stade, c'est que la date doit être au format UNIX alors que Buzz l'a mise dans un format un peu chelou: <code>0000-00-00T00:00:00.000</code>. Dans certains partages, il n'y a tout simplement pas de lien, ce qui affole un peu PHP au niveau des E_NOTICE. Et pour finir, le parser n'aime pas trop les accents.

Pour résoudre le problème de la date, un peu de comptage de caractères est nécessaire:

<pre class="brush: php">
function date_convert($date){
    $year = substr($date, 0, 4);
    $month = substr($date, 5, 2);
    $day = substr($date, 8, 2);
    $hour = substr($date, 11, 2);
    $min = substr($date, 14, 2);
    $sec = substr($date, 17, 2);

    $date = mktime($hour, $min, $sec, $month, $day, $year);
    return $date;
}
</pre>

Pour les accents c'est un peu plus astucieux, il va falloir encoder tous les caractères en HTML puis décoder les balises pour que le parser puisse faire son boulot:

<pre class="brush: php">
function char_convert($text){
    $text = htmlentities($text, ENT_NOQUOTES, "UTF-8");
    $text = htmlspecialchars_decode($text);
    return $text;
}
</pre>

Et pour les fichiers sans lien, un « <code>if</code> » suffit.

Maintenant qu'on récupère tout à peu près correctement, on va pouvoir peaufiner. Comme ce sont des liens de flux RSS on voit souvent du http://feedproxy.google.com/~r/9gag/~3/3dFZLa-CYI8/466983 au lieu d'avoir une belle URL claire et limpide. Il va falloir sortir cURL pour faire le ménage (et on va aussi en profiter pour virer les liens morts ainsi que les paramètres que rajoute feedburner pour les statistiques) :

<pre class="brush: php">
function real_url($link){
    if ( ! empty($link) ) { return; }
    $options = array(
     CURLOPT_NOBODY         =&gt; true,     // Asks header only
     CURLOPT_RETURNTRANSFER =&gt; true,     // return web page
     CURLOPT_HEADER         =&gt; true,    // return headers
     CURLOPT_FOLLOWLOCATION =&gt; true,     // follow redirects
     CURLOPT_ENCODING       =&gt; "",       // handle all encodings
     CURLOPT_USERAGENT      =&gt; "spider", // who am i
     CURLOPT_AUTOREFERER    =&gt; true,     // set referer on redirect
     CURLOPT_CONNECTTIMEOUT =&gt; 10,      // timeout on connect
     CURLOPT_TIMEOUT        =&gt; 15,      // timeout on response
     CURLOPT_MAXREDIRS      =&gt; 10,       // stop after 10 redirects
    );

    $ch      = curl_init( $link );
    curl_setopt_array( $ch, $options );
    $content = curl_exec( $ch );
    $err     = curl_errno( $ch );
    $errmsg  = curl_error( $ch );
    $header  = curl_getinfo( $ch );
    curl_close( $ch );

    $http_code = $header["http_code"];
    $url = $header["url"];

    if ( $http_code != 404 ) {
     // Ces trois lignes suppriment les paramètres feedburner.
     // Merci Sebastien SAUVAGE ;D
     $i=strpos($url,'&amp;utm_source='); if ($i) $url=substr($url,0,$i);
     $i=strpos($url,'?utm_source='); if ($i) $url=substr($url,0,$i);
     $i=strpos($url,'#xtor=RSS-'); if ($i) $url=substr($url,0,$i);

     return $url;
    }
    else {
     return;
    }
}
</pre>

Le résultat final est disponible ici : <a href="https://aldarone.fr/assets/buzz2bookmarks.txt">Télécharger le script pour passer de Buzz à bookmarks.html</a>.

J'y ai ajouté une variable pour choisir le dossier qui contient les fichiers html de Buzz, ainsi que la boucle qui les parcourt. Il ne prend pas de paramètres et vous aurez besoin du fichier <a href="http://sourceforge.net/projects/simplehtmldom/files/latest/download">simple_html_dom.php</a>. Au niveau du temps d'exécution... La vérification de la validité des liens prend un peu de temps: Pour 287 fichiers il a fallu 5 minutes et le nombre de lien valides est de 209 (mais là ça dépendra de vos partages.)

Maintenant que vous avez vos liens dans un format standard, libre à vous d'en faire ce que vous voulez. Pour ma part je pense installer <a href="http://sebsauvage.net/wiki/doku.php?id=php:shaarli">Shaarli</a> prochainement.
