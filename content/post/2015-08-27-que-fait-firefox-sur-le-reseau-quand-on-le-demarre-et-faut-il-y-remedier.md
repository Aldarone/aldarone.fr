---
ID: 1621
author: Alda
date: 2015-08-27T00:00:00Z
post_date: 2015-08-27 15:58:52
post_excerpt: ""
post_title: |
  Que fait Firefox sur le réseau quand on le démarre et faut-il y remédier ?
published: true
url: |
  /que-fait-firefox-sur-le-reseau-quand-on-le-demarre-et-faut-il-y-remedier/
---

En lien avec les évènements relatés dans mon article précédent « <a href="https://aldarone.fr/une-avalanche-de-fud-sur-mozilla-et-firefox/">Une avalanche de FUD sur Mozilla et Firefox.</a> » <a href="https://ecirtam.net/links/">Oros</a> a conduit <a href="https://www.ecirtam.net/links/?40QYwg">une petite étude du comportement d'un Firefox fraîchement installé</a> et en a tiré <a href="https://github.com/Oros42/firefox_change_prefs">un fichier de configuration à appliquer</a> pour le rendre complètement silencieux.

Cependant, je trouve non seulement que son analyse manque cruellement d'explications et que son fichier de configuration propose des valeurs qui vont beaucoup trop loin à mon goût, d'autant que ces choix ont pour seule justification le fait de faire taire Firefox. Cette approche est donc dommageable et on voit déjà des partages affolés de la part de gens pour qui « requête réseau » signifie que Firefox vends leurs données personnelles à des grosses corporations :

https://twitter.com/molokoloco/status/636533449269084160

Je vais donc détailler un peu à quoi correspondent les requêtes listées ainsi que ce qui se trouve dans ce fichier de configuration et, quand c'est le cas, pourquoi j'estime qu'une telle désactivation est problématique.

Pour les requêtes réseaux, je n'ai pas leur contenu et ne pourrai donc pas en expliquer certaines mais les noms de domaine des autres sont pour la plupart assez parlants.

<pre><code>1 : www.mozilla.org.
1 : snippets.cdn.mozilla.net.
1 : geo.mozilla.org.
1 : location.services.mozilla.com.
1 : search.services.mozilla.com.
1 : self-repair.mozilla.org.
1 : aus4.mozilla.org.
3 : search.yahoo.com.
3 : ff.search.yahoo.com.
1 : ciscobinary.openh264.org.
1 : clients1.google.com.
1 : safebrowsing.google.com.
53 : safebrowsing-cache.google.com.
1 : ocsp.digicert.com.
</code></pre>

<code>geo.mozilla.org</code> et <code>location.services.mozilla.com</code> correspondent de manière assez évidente à un service de géolocalisation. Mozilla connait donc l'emplacement approximatif de tel navigateur. Ces requêtes disparaissent en passant <code>browser.search.geoip.url</code> à <code>false</code> cela a donc à voir avec les fonctionnalités de recherche comme nous le verrons dans le détails des options.

<code>search.services.mozilla.com</code>, <code>aus4.mozilla.org</code> et  <code>self-repair.mozilla.org</code> sont des domaines utilisés par Mozilla pour la maintenance de Firefox : des vérifications de mises à jour pour les deux premiers et le service Heartbeat pour le dernier. <a href="https://support.mozilla.org/en-US/kb/rate-your-firefox-experience-heartbeat">Heartbeat étant le service de feedback</a> pour Firefox (ce panneau « Rate your experience with Firefox » qu'on voit s'afficher de temps en temps.) Il permet à Mozilla de savoir combien de personnes démarrent leur Firefox chaque jour pour avoir un suivi statistique.

<code>search.yahoo.com</code> et <code>ff.search.yahoo.com</code> sont là pour fournir à Yahoo des statistiques d'utilisation. Ils ont un contrat avec Mozilla pour être le moteur de recherche par défaut, ces appels servent à justifier l'utilité de ce deal.

<code>ciscobinary.openh264.org</code> a rapport avec le décodage des vidéos en h264 dans le lecteur HTML5. h264 est un codec brevet et les éditeurs de logiciel qui distribuent un codec h264 doivent payer une licence pour chaque codec distribué. Ça ne s'applique pas en Europe car (pour l'instant) les brevets logiciels sont encore considérés comme nuls mais aux États-Unis notamment, il faut passer à la caisse. Pour éviter à Mozilla de devoir mettre la plupart de ses économies dans le paiement de la licence à MPEG-LA, Cisco lui fournit gracieusement un codec nommé openh264. Cet appel réseau peut donc aussi bien être présent à des fins de statistiques mais aussi de mise à jour. (Si vous allez dans les Préférences - Modules - Plugins, <a href="https://aldarone.fr/wp-content/uploads/2015/08/Capture-d’écran_2015-08-26_19-11-46.png">vous verrez le codec en question</a>.)

Le grand nombre d'appels à Google ont rapport au service SafeBrowsing de Google (Navigation Sécurisée en français). C'est une liste noire de domaines qui contiennent ou ont contenu divers malwares ou qui pratiquent le phishing. Cela permet au navigateur de bloquer la page avant même de la charger et d'<a href="https://aldarone.fr/wp-content/uploads/2015/08/Capture-d’écran_2015-08-26_19-11-46.png">afficher une alerte</a> mais cela implique d'envoyer l'URL visitée au service. Et ce service est tenu par Google.

Le dernier, <code>ocsp.digicert.com</code>, concerne le protocole OCSP (<a href="https://fr.wikipedia.org/wiki/Online_Certificate_Status_Protocol">Online Certificate Status Protocol</a>) et sert à vérifier la validité d'un certificat chez son émetteur (ici, DigiCert) afin de s'assurer qu'il n'a pas été révoqué. Ni information personnelle, ni statistique, il s'agit d'un protocole de sécurité qui va de pair avec TLS.

On remarquera aussi que, contrairement aux cris d'horreur poussés par les détracteurs de Firefox Hello et de l'intégration de Pocket, strictement aucune requête réseau ne concerne ces fonctionnalités.

Voila pour les appels réseau que j'ai pu identifier, passons maintenant aux différents blocs du fichier de configuration.

<h3>Le rafraichissement automatique de certaines pages</h3>

<pre><code>user_pref("accessibility.blockautorefresh",true);
</code></pre>

On commence bien avec un réglage de bon sens. <code>accessibility.blockautorefresh</code> bloque le rafraichissement automatique de certaines pages. Cette fonction était sensée avant la démocratisation d'AJAX pour mettre à jour une page qui disposait d'un nouveau contenu mais la technique est usée et abusée par les sites de presse qui profitent des onglets en arrière plan pour se booster les vues et rentabiliser leurs lecteur⋅ices. Pour plus d'infos : <a href="http://kb.mozillazine.org/Accessibility.blockautorefresh">accessibility.blockautorefresh sur Mozillazine</a>.

<h3>Des préférences sans lien avec le réseau</h3>

<pre><code>user_pref("browser.cache.disk.enable", false);
user_pref("browser.download.panel.shown", true);
user_pref("browser.newtab.url","about:blank");
</code></pre>

Ces trois-là portent plus matière à controverse puisqu'il s'agit de préférence personnelle.

Pour le premier pas de cache sur le disque signifie potentiellement moins d'accès disques (et c'est bien) mais ça signifie aussi que le cache se vide quand on ferme Firefox. Il faudra donc charger à nouveau toutes les ressources sur chaque site web. Ça veut donc dire plus de trafic réseau, plus de charge sur les serveurs et des pages qui s'affichent globalement moins vite.

Pour le second, on force Firefox à nous demander où enregistrer les fichiers qu'on télécharge au lieu de les mettre d'office dans un dossier spécifié. C'est bien quand on apprécie ce comportement, c'est moins bien quand on préfère le comportement par défaut. De plus la présence de cette ligne empêche de modifier l'option dans Préférences - Général - Téléchargement.

Idem pour le dernier du bloc, afficher <code>about:blank</code> à l'ouverture d'un onglet n'est peut-être pas du goût de tout le monde. Alors que <code>about:mozilla</code> ou <code>about:about</code> valent le détour.

<h3>Google SafeBrowsing</h3>

<pre><code>// I remove all URL because I don't want to
// connecte my PC to Google
user_pref("browser.safebrowsing.appRepURL", "");
user_pref("browser.safebrowsing.downloads.enabled", false);
user_pref("browser.safebrowsing.downloads.remote.enabled", false);
user_pref("browser.safebrowsing.enabled", false);
user_pref("browser.safebrowsing.gethashURL", "");
user_pref("browser.safebrowsing.malware.enabled", false);
user_pref("browser.safebrowsing.malware.reportURL", "");
user_pref("browser.safebrowsing.reportErrorURL", "");
user_pref("browser.safebrowsing.reportGenericURL", "");
user_pref("browser.safebrowsing.reportMalwareErrorURL", "");
user_pref("browser.safebrowsing.reportMalwareURL", "");
user_pref("browser.safebrowsing.reportPhishURL", "");
user_pref("browser.safebrowsing.reportURL", "");
user_pref("browser.safebrowsing.updateURL", "");
user_pref("browser.trackingprotection.gethashURL", "");
user_pref("browser.trackingprotection.updateURL", "");
user_pref("services.sync.prefs.sync.browser.safebrowsing.enabled",false);
user_pref("services.sync.prefs.sync.browser.safebrowsing.malware.enabled",false);
</code></pre>

Ici on s'attaque à SafeBrowsing de Google. Il y a des pour à propos de cette désactivation : On envoie pas les URLs visitées à Google, mais il y a des contres : on ouvre laisse plus de champs à une infection par Javascript ou à un Phishing. Bref, c'est quelque chose qu'il faudrait désactiver après réflexion et pas « parce que Firefox envoie des données mon dieu ! »

Ne vous leurrez pas non plus si vous utilisez GNU/Linux, pas plus tard que début août <a href="https://blog.mozilla.org/security/2015/08/06/firefox-exploit-found-in-the-wild/">une faille dans PDF.js permettait à un script JS de récupérer des fichiers de votre ordinateur</a>, l'exploit visait <code>/etc/passwd</code>, <code>.my.conf</code> (coucou le mot de passe MySQL) ou encore <code>.bash_history</code>.

Et en aucun cas ne faites ça chez un⋅e ami⋅e ou parent⋅e qui ne maîtrise pas l'outil informatique.

<h3>Le moteur de recherche par défaut</h3>

<pre><code>user_pref("browser.search.defaultenginename", "DuckDuckGo");
</code></pre>

Sur le fait de forcer DuckDuckGo comme moteur de recherche par défaut, je n'y vois personnellement aucun inconvénient mais il faudra penser à cette ligne si vous préférez utiliser autre chose. Un méta moteur comme l'instance <a href="https://framabee.org/">searx de Framasoft</a> par exemple.

<h3>La géolocalisation</h3>

<pre><code>user_pref("geo.enabled",false);
user_pref("browser.search.geoip.url", "");
user_pref("geo.wifi.uri", "");
</code></pre>

Ces règles de configuration désactivent la géolocalisation du navigateur. <code>geo.enabled</code> permet, quand sa valeur est <code>true</code>, d'autoriser certains sites à géolocaliser votre navigateur pour « améliorer » le service fourni. Ça va de Facebook Messenger qui le fait à des fins commerciales et <a href="https://medium.com/faith-and-future/stalking-your-friends-with-facebook-messenger-9da8820bd27d">qui fait fuiter l'info à vos amis</a> à <a href="http://www.monprochainbus.eu/">monprochainbus.eu</a> qui indique les arrêts de bus les plus proches sans qu'on ait rien à saisir. Dans tous les cas, Firefox vous demande l'autorisation.

De son côté, <code>browser.search.geoip.url</code> aide le navigateur à identifier le pays dans lequel vous vous trouvez à l'aide de la technique <a href="https://fr.wikipedia.org/wiki/GeoIP">GeoIP</a>. Pour cela il effectue une connexion à l'adresse <code>https://location.services.mozilla.com/v1/country?key=%MOZILLA_API_KEY%</code> et reçoit le nom standardisé du pays. Vous remarquerez l'envoi d'un identifiant unique <code>%MOZILLA_API_KEY%</code> qui identifie une installation de Firefox. Il est possible que ce soit utilisé à des fins de limitations du nombre de requêtes. Conserver l'URL en enlevant <code>?key=%MOZILLA_API_KEY%</code> ne perturbe pas plus Firefox que ça, empêche Mozilla de suivre votre instance particulière de Firefox mais cela fausse aussi certainement leurs statistiques d'usage par pays.

Enfin, <code>geo.wifi.uri</code> aide <a href="https://www.mozilla.org/fr/firefox/geolocation/">la géolocalisation de Firefox</a> à se montrer plus précise en utilisant Google Location Services. Firefox envoie donc votre IP, la liste des réseaux Wifi environnants et un identifiant unique régénéré toutes les deux semaines à Google pour obtenir une localisation fiable au niveau de la rue au lieu de n'avoir que GeoIP qui est fiable au niveau de la ville (et encore, parfois on a que le pays). Sans cette option, la précision prend un sacré coup ce qui peut jouer des tours aux personnes qui en ont l'utilité.

De plus <a href="https://aldarone.fr/que-fait-firefox-sur-le-reseau-quand-on-le-demarre-et-faut-il-y-remedier/#comment-449">comme indiqué dans ce commentaire</a>, il est possible d'utiliser Mozilla Location Service à la place de Google Location Service pour la préférence <code>geo.wifi.uri</code>.

<h3>D'autres préférences sans rapport avec le réseau</h3>

<pre><code>user_pref("browser.search.openintab",true);
user_pref("browser.search.showOneOffButtons",false);
user_pref("browser.startup.page", 0);
user_pref("browser.tabs.warnOnClose", false);
user_pref("browser.tabs.warnOnOpen", false);
user_pref("plugins.click_to_play",true);
user_pref("general.warnOnAboutConfig",false);
user_pref("browser.urlbar.trimURLs",false);
</code></pre>

Ici on retrouve à nouveau des préférences qui n'impactent pas la « vie privée », <code>browser.search.openintab</code> force l'ouverture d'un onglet après une recherche dans la barre de recherche, <code>browser.search.showOneOffButtons</code> masque les boutons des moteurs de recherche installés qui <a href="https://aldarone.fr/wp-content/uploads/2015/08/2014-12-09-12-14-37-199895.png">s'affichent en bas du champ de recherche</a>, <code>browser.startup.page</code> définit la page qui s'affiche au démarrage du navigateur (ici elle est à 0 donc une page blanche, par défaut c'est la page d'accueil. Du coup ça fait doublon puisque précédemment on a défini la page d'accueil à <code>about:blank</code>), les deux directives <code>browser.tabs</code> suppriment respectivement l'alerte du navigateur quand on le ferme et que plusieurs onglets sont ouverts et l'avertissement quand on ouvre un nouvel onglet alors qu'il y en a déjà 15 ouverts (<code>browser.tabs.warnOnOpen</code> va de pair avec <code>browser.tabs.maxOpenBeforeWarn</code> qui est par défaut à 15)

De son côté <code>plugins.click_to_play</code> force l'activation des plugins à « Toujours demander » ce qui est <a href="https://blog.mozilla.org/security/2014/02/28/update-on-plugin-activation/">le cas par défaut depuis Firefox 31</a>.

<code>user_pref("general.warnOnAboutConfig",false);</code> supprime simplement l'avertissement qui s'affiche en visitant la page <code>about:config</code> (comme quand on coche la case « Ne plus me demander » de cette même page d'avertissement.)

Le dernier force l'affichage de <code>http://</code> ou de <code>https://</code> dans la barre d'adresse puisqu'ils sont masqués par défaut depuis Firefox 7. À ça on pourrait rajouter le passage de <code>browser.urlbar.formatting.enabled</code> à <code>false</code> qui va empêcher d'afficher le domaine en noir et les autres parties de l'URL en gris.

<h3>Les rapports de santé de Firefox</h3>

<pre><code>user_pref("datareporting.healthreport.service.enabled",false);
user_pref("datareporting.healthreport.uploadEnabled",false);
</code></pre>

Le service rapport de santé est un service qui enregistre divers statistiques d'utilisation comme les derniers crashes de Firefox ou le temps de démarrage moyen. Désactiver le service empêche purement et simplement la création de tels rapports et désactiver le partage fait que Mozilla ne reçoit plus les rapport générés. S'il est compréhensible de désactiver le partage du rapport, il peut par contre s'avérer problématique de désactiver la création de ces rapports qui peuvent servir à dépanner un Firefox bancal.

Les rapports en question sont accessibles via la page <code>about:healthreport</code>, en cliquant sur données brutes vous pouvez voir les rapports tels qu'ils sont envoyés à Mozilla, la page en question contient également un bouton pour désactiver le partage (même effet que <code>datareporting.healthreport.uploadEnabled</code>) et un lien vers une page d'explication assez bien faite : <a href="https://support.mozilla.org/fr/kb/bilan-sante-firefox-comprendre-performances">Bilan de santé de Firefox – comprendre vos performances navigateur</a>

<h3>L'injection de contenu dans le presse-papier</h3>

<pre><code>user_pref("dom.event.clipboardevents.enable",false);
</code></pre>

Cette préférence désactive les évènements JavaScript <code>oncopy</code>, <code>oncut</code> et <code>onpaste</code> qui permettent aux sites web de manipuler le contenu du presse papier. Désactiver cette fonction n'a que du positif puisque le site sur lequel vous faites un copier-coller ne pourra pas rajouter du texte arbitraire comme un lien promotionnel après le contenu désiré.

<h3>Les suggestions de recherche</h3>

<pre><code>user_pref("browser.search.suggest.enabled",false);
</code></pre>

Cette option va désactiver les suggestions de la barre de recherche. C'est ce qui permet à DuckDuckGo de vous suggérer « Les hommes les plus riches du monde » quand vous saisissez « Les hommes » ou « Les femmes les plus belles du monde » quand vous saisissez « Les femmes » (On notera au passage l'influence du patriarcat sur les suggestions de recherche…).

Pour que ça fonctionne, Firefox envoie une requête à chaque lettre tapée dans le champ de recherche. Personnellement j'ai du mal à saisir l'intérêt de désactiver les suggestions que je trouve souvent pertinentes, d'autant que quand je tape une phrase, je me fiche de savoir que mon moteur de recherche sait que j'en ai saisi chaque lettre une par une.

Sans les suggestions, Firefox se rabat sur son historique interne.

<h3>Le User Agent et ses potes</h3>

<pre><code>// user-agent
user_pref("general.appname.override", "");
user_pref("general.appversion.override", "");
user_pref("general.oscpu.override", "");
user_pref("general.platform.override", "");
user_pref("general.useragent.override", "Mozilla/5.0 ()");
user_pref("general.useragent.vendor", "");
</code></pre>

Le user-agent est une chaine de caractère identifiant les différents navigateurs, leur version et leur environnement. À titre d'exemple, celui de mon Firefox est <code>Mozilla/5.0 (X11; Linux x86_64; rv:41.0) Gecko/20100101 Firefox/41.0</code> On retrouve l'environnement pour lequel Firefox a été compilé, sa version, la version de son moteur, etc. Ce bloc-là masque tout ce qu'il est possible de masquer dans cette chaine et force en plus sa valeur à une chaine arbitraire et je suis plus que dubitatif sur l'utilité de dissimuler cette information.

Par contre la conséquence la plus directe est de faire baisser les statistiques d'utilisation de Firefox puisque les sites qui recensent de telles statistiques ne sauront plus par quel navigateur ils sont visités. Les parts de marché de Firefox sont déjà en baisse plus ou moins constante au profit de Chrome et contribuer à les faire diminuer pour aucun bénéfice revient à confirmer Chrome dans sa position de nouvel IE6 (et on ne veut vraiment pas amplifier le mouvement).

Bref, masquer son user-agent, sauf cas spécifiques comme par exemple à des fins de tests ou encore quand on utilise Opera et que Google fournit délibérément une version inutilisable de ses application, n'a aucun intérêt.

<strong>Mise à jour</strong> : Visiblement Google aime bien faire n'importe quoi avec les user-agents et semble empêcher le plein écran sur Youtube si <code>general.useragent.override</code> ne contient pas <code>Gecko</code>, merci à un⋅e anonyme sur OpenNews pour le signalement. (<a href="https://www.ecirtam.net/opennews/?fFXtjQ">Le lien vers la question</a>, <a href="https://www.ecirtam.net/links/?WCa8lg">le lien vers la réponse</a>)

<h3>La lecture HTML5 sous windows et les DRM</h3>

<pre><code>user_pref("media.directshow.enabled",false);
user_pref("media.windows-media-foundation.enabled",false);
</code></pre>

Ces deux préférences n'ont d'intérêt que sous windows et vont désactiver le lecteur interne de Firefox en ce qui concerne les fichiers mp4 et mp3. Le problème qui se pose c'est que les sites proposant un lecteur HTML5 comme SoundCloud ou Youtube vont à présent utiliser la rétro-compatibilité et se rabattront sur Flash. Ce qui est un peu paradoxal quand on pense protéger sa vie privée.

<pre><code>user_pref("media.eme.enabled",false);
user_pref("media.gmp-eme-adobe.enabled",false);
</code></pre>

Celles-là ont rapport avec le support des EMEs (Encrypted Media Extension) qui sont les DRMs standardisées de HTML5. Comme les DRMs c'est purement et simplement de la merde il parait logique de désactiver leur support. Néanmoins, les sites avec EME risquent une fois encore de se rabattre sur Flash qui a lui aussi son système de DRMs, non standardisé lui. Si vous voulez éviter à tout prix les DRMs il faudra donc vous assurer de désactiver Flash également. Et de garder à l'esprit que si votre navigateur ne lit pas les fichiers que tous les autres utilisateur⋅ices arrivent à lire, ce n'est pas de sa faute.

<h3>Des fuites d'information</h3>

<pre><code>user_pref("media.peerconnection.enabled",false);
user_pref("network.proxy.socks_remote_dns",true);
user_pref("network.http.sendRefererHeader",0);
</code></pre>

La première préférence à rapport à WebRTC. Ce protocole sert à la communication directe entre deux navigateurs. C'est ce qui permet par exemple de jouer en réseau ou de faire de la conférence vidéo en web. Ici, WebRTC est désactivé de force car son implémentation actuelle expose les adresses IPs locales de l'ordinateur.  N'importe quel site web est donc capable de récupérer la liste de vos IPs et est susceptible de contacter d'autres ordinateurs sur le réseau avec des appels AJAX depuis votre navigateur. (Il lui faut tout de même connaître les IPs de destination.) Les proxys et les VPN verront eux aussi leurs adresses exposées. Si vous n'utilisez pas WebRTC il est donc plus sûr de désactiver cette option. Le bug concernant cette faille est visible ici <a href="https://bugzilla.mozilla.org/show_bug.cgi?id=1189167">[meta] ICE candidate generation control and user authorization</a> et les développements autour sont assez actifs.

À noter que Chrome y est également vulnérable car le problème provient d'un flou dans le standard WebRTC.

La seconde force Firefox à envoyer les requêtes DNS à travers le proxy si vous en utilisez un. Avec la valeur par défaut, les requêtes sont envoyées sur le résolveur DNS de l'ordinateur et le réseau que vous essayez de contourner à l'aide d'un proxy connait tous les domaines que vous visitez.

Finalement, la dernière bloque l'envoi du referer aux sites que vous visitez. Le referer est le site de provenance quand vous cliquez sur un lien. Par exemple si je visite le Shaarli de SebSauvage et que je clique sur un lien vers le blog de Kevin, ce dernier aura la possibilité de savoir que j'ai cliqué sur un lien chez Seb pour arriver chez lui. Ce n'est valable qu'en HTTP car en HTTPS le referer n'est jamais envoyé par Firefox.

<h3>Des requêtes en avance</h3>

<pre><code>user_pref("network.dns.disablePrefetch",true);
user_pref("network.http.speculative-parallel-limit",0);
</code></pre>

Ces deux-là visent à améliorer le temps de réaction de Firefox au moment de cliquer sur un lien. Ainsi, le DNS Prefetch consite à lister les liens d'une page et de résoudre les noms de domaines associés pour s'épargner la durée de résolution au moment du clic. Ça fournit à votre résolveur DNS la liste des domaines liés sur une page et le désactiver augmente le temps de réponse de Firefox de quelques millisecondes (le temps de la résolution DNS). À la fin de la journée, le gain en vitesse cumulé est appréciable et le risque en terme de vie privée est pour le moins inexistant.

<h3>Activation de Firefox Hello</h3>

<pre><code>user_pref("loop.enabled",true);
</code></pre>

Cette préférence active Firefox Hello, c'est la valeur par défaut donc on empêche sa désactivation. Ce qui ne mène à rien puisque Firefox Hello est basé sur WebRTC qui a été désactivé quelques lignes avant.

<h3>Les versions de TLS</h3>

<pre><code>user_pref("security.ssl3.dhe_rsa_aes_128_sha",false);
user_pref("security.ssl3.dhe_rsa_aes_256_sha",false);
user_pref("security.tls.version.max",3);
user_pref("security.tls.version.min",2);
</code></pre>

Ces lignes concernent le protocole TLS qui définit la sécurité en HTTPS. La valeur de <code>tls.version.min</code> indique qu'on accepte au moins TLS1.1 et celle de <code>tls.version.max</code> indique qu'on accepte au plus TLS1.2 (la dernière en date). Les deux premières lignes ont rapport à SSLv3 et ne sont pas pertinentes puisque SSLv3 est antérieure à TLS1.0 et est donc désactivé.

<h3>Un bloqueur de traqueur intégré</h3>

<pre><code>user_pref("privacy.trackingprotection.enabled",false);
</code></pre>

À partir de la version 35, Firefox intègre un bloqueur de traceurs basé sur la liste de Disconnect.me, il serait remarquablement efficace puisqu'une paire de chercheurs <a href="http://www.ghacks.net/2015/05/24/firefox-tracking-protection-decreases-page-load-times-by-44/">ont publié une étude à son sujet début 2015</a> indiquant une augmentation de 44% de la vitesse de chargement, une diminution de 39% du traffic réseau et une diminution de 66% du nombre de cookies. Cette fonction est désactivée par défaut et la valeur de cette préférence empêche ici son éventuelle activation (ce qui n'est pas très logique si notre but est d'améliorer la protection de notre vie privée avec Firefox).

<h3>La télémétrie : analyse des performances et des fonctions les plus utilisées de Firefox</h3>

<pre><code>user_pref("toolkit.telemetry.enabled",false);
</code></pre>

La télémétrie permet à Mozilla de recueillir des informations importante sur le comportement de Firefox dans une vaste diversité d'environnements. Elle est désactivée par défaut dans Firefox Stable et ESR mais activée par défaut sur Beta, Developper et Aurora. La présence de cette préférence empêche son activation et on se retrouve donc à utiliser Firefox sans contribuer à son amélioration. Et c'est dommage.

<h3>Conclusion</h3>

S'il est tout à fait justifié de surveiller les usages réseaux de nos applications favorites pour veiller à ce qu'elles ne nous trahissent pas, chercher aveuglément à les bloquer est loin d'être une solution pertinente. Surtout quand cela amène à proposer une configuration à poser puis oublier présentée comme « Améliorant la vie privée » quand cette configuration mêle préférences personnelles, lignes obsolètes ou redondantes et valeurs exposant à plus de tracking ou de malwares, en dépit de quelques parties pertinentes.

Au vu du temps que m'a pris la simple recherche pour comprendre l'intérêt de ces options, je suis convaincu que la plupart des gens qui verront et appliqueront ce fichier ne feront que le survoler se retrouvant du coup avec un Firefox au fonctionnement modifié pouvant même être considéré comme défaillant (puisqu'il n'y a plus de WebRTC, plus de lecteur HTML5, plus d'optimisation du chargement de certaines pages) et j'estime qu'il y a une certaine responsabilité qui ne doit pas se limiter à une bête notice « Lisez le fichier avant de l'appliquer » quand on fournit une telle configuration sur internet. (Non, je n'aime pas trop <a href="http://opensource.org/licenses/mit-license.php">la licence MIT</a> non plus.)

Néanmoins, j'espère que cet article vous aura permis d'en apprendre plus sur le fonctionnement de Firefox et que vous mesurerez bien les tenants et les aboutissants des modifications de configuration que vous ferez à l'avenir.

<hr />

Crédit photo: <a href="https://www.flickr.com/photos/mpastwa/2671066786/">social network hub</a> par <a href="https://www.flickr.com/photos/mpastwa/">Mathias Pastwa</a>