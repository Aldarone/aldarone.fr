---
date: 2015-05-16T00:00:00Z
title: "Les communications chiffrées faciles en Mai 2015"
slug: "les-communications-chiffrees-pour-les-non-informaticien%e2%8b%85nes-en-mai-2015"
---

Il y a un peu plus d'un an, j'ai parlé de moyens pour sécuriser nos communications sur nos téléphones mobiles. J'avais parlé de TextSecure, Redphone et Telegram.

Avec le vote de la loi sur le renseignement qui <a href="http://www.laquadrature.net/fr/lassemblee-nationale-vote-la-surveillance-de-masse-des-citoyens-francais">autorise maintenant le gouvernement à surveiller tout un chacun</a> sans passer par le moindre juge, il me semble pertinent de refaire un point sur ce qui a changé ou non et sur les nouveaux moyens disponibles.

Si vous n'y connaissez rien en chiffrement, ce n'est pas grave, vous pouvez continuer à lire. Je ne présenterai que des outils qui fonctionnent immédiatement après s'être installés parce que je fais parti de celleux qui pensent qu'une bonne sécurité doit être accessible à toutes et à tous, même si on ne sait pas ce qu'est le chiffrement à courbes elliptiques (et aussi parce que les arcanes de la sécurité ont tendance à me filer mal au crane.)

Comme d'habitude, la sécurité n'est possible que lorsqu'il est possible d'examiner le code source des applications qui la mettent en place afin de pouvoir contrôler que le logiciel ne dissimule rien. Exit donc Whatsapp, Skype, Facebook, Bleep, etc. Même si ils prétendent fournir de la sécurité, on est sensé les croire sur parole sans vérification possible. Et vous avez vraiment envie de croire sur parole une entreprise capitaliste vous ?

Les logiciels dont je vais parler sont Libres, donc open-source et gratuits. Le chiffrement n'est actif qu'avec les contacts qui utilisent le même logiciel que vous.

<h1>Les messages mobiles</h1>

Cette section concerne les SMS et équivalents et se compose de trois logiciels très proches : TextSecure, SMSSecure et Signals.

<h2>Textsecure</h2>

<img src="https://aldarone.fr/wp-content/uploads/2014/02/textsecure.jpg" alt="TextSecure, la sécurité simplifiée" width="705" height="344" class="size-full wp-image-1464" />

Celui là c'est un peu mon préféré. Il était déjà opérationnel l'an dernier et je l'utilise quotidiennement depuis ce moment là.

C'est une application pour Android qui peut remplacer (sans obligation) l'application SMS standard. Si vous décidez de conserver votre application SMS, vous recevrez les messages TextSecure dans TextSecure et les SMS dans l'application SMS.

Elle permet également d'envoyer des MMS qui seront, eux aussi, chiffrés.

Au premier lancement elle demande de saisir votre numéro de téléphone et quelques secondes plus tard vous recevez un SMS spécial qu'elle utilise automatiquement pour s'activer.

Vous pourrez dès lors envoyer des messages chiffrés aux contacts qui l'utilisent, sans même y faire attention. Le chiffrement est simplement indiqué par un petit cadenas au bas de chaque message envoyé ou reçu.

Les SMS reçus sont en vert et les messages TextSecure sont en bleu.

Concernant le mode de transport il y a plusieurs choses à savoir :

<ul>
<li>Les messages transitent par internet, il vous faut donc un forfait compatible (mais de nos jours pratiquement tous les forfaits incluent au moins 20Mo de données par mois et TextSecure en consomme environ 600Ko)</li>
<li>Ils transitent par les serveurs de Google puis par les serveurs d'OpenWhisper (les gens qui développement TextSecure).
Comme les communications sont chiffrées, Google pourra uniquement voir que vous utilisez l'application (mais comme vous l'avez installée, ils se savent déjà) et de son côté OpenWhisper ne verra que l'identifiant de la personne à qui vous envoyez un message (pour lui délivrer un message, il est logique que le transporteur en connaisse l'adresse)</li>
</ul>

<a href="https://play.google.com/store/apps/details?id=org.thoughtcrime.securesms"><img src="https://aldarone.fr/wp-content/uploads/2015/05/Disponible-sur-GooglePlay-300x110.jpg" alt="Télécharger TextSecure sur Google Play" width="300" height="110" class="aligncenter size-medium wp-image-1594" /></a>

Néanmoins, pour ne pas passer par Google et OpenWhisper ou pour ne pas être obligé⋅e d'utiliser internet, il y a une alternative : SMSSecure.

<h2>SMSSecure</h2>

<img src="https://aldarone.fr/wp-content/uploads/2015/05/smssecure.png" alt="SMS Encryption made easy" width="450" height="120" class="size-full wp-image-1591" />

SMSSecure est très proche de TextSecure puisqu'il partage une grande partie de son code source et donc la même méthode de chiffrement.

Cette application est apparue quand les développeurs et développeuses de TextSecure ont décidé⋅es d'arrêter le support du chiffrement pour les SMS en raison d'un trop grand nombre de correctifs nécessaire qui les empêchaient de se concentrer sur l'ajout de nouvelles fonctions.

D'autres personnes ont donc copié le code source et ont supprimé tout rapport avec Google et OpenWhisper pour ne développer que la partie SMS.

L'interface est donc très proche/identique à celle de TextSecure et pour recevoir des SMS chiffrés elle doit obligatoirement remplacer votre application SMS standard. (Vous pouvez toujours utiliser TextSecure à côté.)

Elle permet également d'envoyer des MMS qui seront, eux aussi, chiffrés.

Une fois installée, il n'y a qu'à sélectionner un contact qui vous a prévenu qu'ille l'utilise et cliquer sur le petit cadenas en haut à droite. Elle va alors lui envoyer un SMS de préparation auquel son téléphone répondra automatiquement et la suite de la conversation se déroulera de manière sécurisée.

Concernant le mode de transport il y a là aussi des choses à savoir :

<ul>
<li>Elle utilise les SMS ; comme un message chiffré prend plus de place qu'un message classique il est possible qu'un message de moins de 140 caractères soit automatiquement coupé en plusieurs parties et que votre forfait soit décompté de plusieurs SMS. Attention donc si vous n'avez pas de SMS illimités.</li>
<li>Contrairement à TextSecure où Google peut savoir que vous l'utilisez et où OpenWhisper peut savoir à qui vous écrivez, ici c'est votre opérateur mobile et toute personne qui écoute le réseau téléphonique qui peut savoir à qui vous écrivez. À vous de choisir à qui vous préférez exposer votre liste d'interlocuteur⋅ices.</li>
</ul>

<a href="https://play.google.com/store/apps/details?id=org.smssecure.smssecure"><img src="https://aldarone.fr/wp-content/uploads/2015/05/Disponible-sur-GooglePlay-300x110.jpg" alt="Téléchargez SMSSecure sur Google Play" width="300" height="110" class="aligncenter size-medium wp-image-1594" /></a>

<a href="https://f-droid.org/repository/browse/?fdid=org.smssecure.smssecure"><img src="https://aldarone.fr/wp-content/uploads/2015/05/Get_it_on_F-Droid-300x104.png" alt="Get_it_on_F-Droid" width="300" height="104" class="aligncenter size-medium wp-image-1596" /></a>

<h2>Signal</h2>

<img src="https://aldarone.fr/wp-content/uploads/2015/05/07533689-photo-logo-application-signal-ios.jpg" alt="Signal - Private Messenger" width="202" height="195" class="aligncenter size-full wp-image-1600" />

Il y a un an, aucune solution libre n'existait pour les personnes possédant un iPhone. Mais maintenant il y a Signal.

Signal est l'exact équivalent de TextSecure pour Android et comme il est développée par les mêmes personnes, les gens utilisant Signal peuvent discuter en toute transparence avec les gens utilisant TextSecure.

L'application utilise la même procédure d'activation que TextSecure : Au premier lancement on saisit son numéro, on reçoit un SMS d'activation et c'est prêt.

La seule différence est qu'Apple n'autorise pas les applications tierces à accéder aux SMS, vous ne pourrez donc pas récupérer tous vos messages dans une seule application et le seul mode de transport disponible sera le même que TextSecure, avec les mêmes points à retenir que ceux cités plus haut.

<a href="https://itunes.apple.com/us/app/signal-private-messenger/id874139669"><img src="https://aldarone.fr/wp-content/uploads/2015/05/DispoSurAppStore-300x111.jpg" alt="Téléchargez Signal sur l'App Store" width="300" height="111" class="aligncenter size-medium wp-image-1595" /></a>

<h1>Les appels mobiles</h1>

Pour ce point, il y a une solution pour Android : RedPhone, et une solution pour iPhone : Signal (oui, la même)

<h2>RedPhone</h2>

<img src="https://aldarone.fr/wp-content/uploads/2014/02/8315ae507a049ffeaf669c32b8644681.jpg" alt="RedPhone, la sécurité simplifiée." width="705" height="344" class="size-full wp-image-1458" />

Développée par OpenWhisper (les mêmes qui font TextSecure et Signal, décidément), RedPhone permet de passer des appels chiffrés via Internet. Ce ne sera donc pas décompté de votre forfait voix, mais de votre quota de données (sauf si vous êtes en Wifi, ce qui permet de s'affranchir du même coup d'une mauvaise couverture.)

L'activation se déroule comme avec TextSecure et l'usage est ensuite transparent. La réception d'appel se fait sans manipulation particulière et au moment de passer un appel, si RedPhone détecte que votre correspondant⋅e est dans son annuaire, il vous offrira le choix de sécuriser l'appel ou non.

Comme pour TextSecure, les données transitent par Google et OpenWhisper, donc Google sait que vous utilisez RedPhone et OpenWhisper sait qui vous appelez. Encore une fois, sans RedPhone c'est votre opérateur mobile qui sait qui vous appelez mais il sait également ce que vous racontez.

<a href="https://play.google.com/store/apps/details?id=org.thoughtcrime.redphone"><img src="https://aldarone.fr/wp-content/uploads/2015/05/Disponible-sur-GooglePlay-300x110.jpg" alt="Télécharger RedPhone sur Google Play" width="300" height="110" class="aligncenter size-medium wp-image-1594" /></a>

<h2>Signal</h2>

<img src="https://aldarone.fr/wp-content/uploads/2015/05/07533689-photo-logo-application-signal-ios.jpg" alt="Signal - Private Messenger" width="202" height="195" class="aligncenter size-full wp-image-1600" />

Pour iPhone, OpenWhisper a choisi d'unifier les usages et Signal permet également de recevoir ou d'émettre des appels vers d'autres personnes utilisant Signal ou RedPhone.

L'activation se fait en même temps que l'activation des messages et pour appeler quelqu'un il suffit de se rendre dans l'historique des messages et de cliquer sur appeler.

<a href="https://itunes.apple.com/us/app/signal-private-messenger/id874139669"><img src="https://aldarone.fr/wp-content/uploads/2015/05/DispoSurAppStore-300x111.jpg" alt="Téléchargez Signal sur l'App Store" width="300" height="111" class="aligncenter size-medium wp-image-1595" /></a>

<h1>La messagerie instantanée et les conférences audio/vidéo</h1>

Maintenant on s'éloigne un peu du mobile pour s'attaquer à un gros morceau de la communication en ligne : Les conférences audio / vidéo et la messagerie instantanée.

On connait tous Skype, le leader sur le marché. Il appartient à Microsoft, propose des fonctions payantes et, en dépit de la sécurisation qu'il annonce, s'avère <a href="http://news.softpedia.com/news/Skype-Provided-Backdoor-Access-to-the-NSA-Before-Microsoft-Takeover-NYT-362384.shtml">être aussi sécurisé qu'une passoire (lien en anglais)</a>.

Pour le remplacer, il n'y a pas grand monde. Mais l'alternative la plus aboutie est Tox.

<h2>Tox</h2>

<img src="https://aldarone.fr/wp-content/uploads/2015/05/tox4.png" alt="Tox me maybe" width="650" height="200" class="aligncenter size-full wp-image-1593" />

Tox est un logiciel encore incomplet mais néanmoins déjà utilisable au quotidien.

Il permet de communiquer de plusieurs manières :

<ul>
<li>Message texte avec une ou plusieurs personnes.</li>
<li>Conversation audio avec une ou plusieurs personnes.</li>
<li>Conversation vidéo avec une personne. (Les conférences vidéos à plusieurs sont prévues mais les développeurs galèrent un peu sur la meilleure interface possible pour ce cas.)</li>
</ul>

Après installation, Tox génère un identifiant : le ToxId. Il n'y a qu'à le communiquer à votre contact et après avoir accepté sa requête vous voila prêt⋅es à communiquer.

La communication s'effectue sans passer par aucun serveur et sans moyen de lire ou d'altérer le message pendant qu'il transite.

<p>Cependant, comme il n'est pas tout à fait terminé il y a quelques points noirs qui seront prochainement résolus (d'ici la fin de l'année) :
* Pour accepter une requête de contact il faut être connecté⋅e. Si vous êtes déconnecté⋅e au moment où votre contact l'envoie, il devra la réémettre.
* Il est impossible d'envoyer des messages à quelqu'un qui est hors ligne car ils disparaîtront dans l'oubli.
* Il est impossible de rejoindre spontanément une conversation groupée, le seul moyen est d'y être invité⋅e.</p>

Pour le reste tout y est : Smileys, audio, video, transfert de fichiers,…

Il est disponible sur <a href="https://wiki.tox.chat/Binaries#windows">Windows</a>, sur <a href="https://wiki.tox.chat/Binaries#mac_os_x">MacOS</a> et sur <a href="https://wiki.tox.chat/Binaries#gnulinux">GNU/Linux</a>.

Vous avez maintenant toutes les clés en main pour mettre des bâtons dans les roues de quiconque voudrait surveiller vos communications instantanées.

Ce n'est qu'en proposant à vos contacts de les utiliser que vos communications seront protégées puisqu'il n'y a qu'avec les contacts qui utilisent le même logiciel que vous que le chiffrement fonctionne. TextSecure et RedPhone sont compatibles avec Signal mais Tox ne fonctionne qu'avec les utilisateur et les utilisatrices de Tox et SMSSecure ne fonctionne qu'avec les personnes utilisant SMSSecure.

Alors n'hésitez pas, motivez vos contacts et sortez couvert⋅es !

<hr />

Crédits : <a href="https://www.flickr.com/photos/sally_monster/3644997857/">Lockpicking with the hackers.</a> par <a href="https://www.flickr.com/photos/sally_monster/">Sally Crossthwaite</a>
