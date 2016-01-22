---
ID: 1449
post_title: 'Un peu d&rsquo;intimité dans votre téléphone'
author: Alda
post_date: 2014-02-19 12:59:47
post_excerpt: ""
layout: post
permalink: /un-peu-dintimite-dans-votre-telephone/
published: true
---
En ces temps troublés de surveillance généralisée, les écoutes de la NSA, le scandale Amesys il ne fait plus aucun doute que tout ce qu'on dit ou écrit en clair sur Internet est enregistré et sera utilisé contre nous.

[caption id="attachment_1454" align="alignleft" width="200"]<img src="https://aldarone.fr/wp-content/uploads/2014/02/team_fortress_2_wallpaper_happy_spy_by_dunkmovies-d5rg9xh-200x125.jpg" alt="« La curiosité c&#039;est mon péché mignon »" width="200" height="125" class="size-quarter wp-image-1454" /> « La curiosité c'est mon péché mignon »[/caption]

Et si vous pensez n'avoir rien à cacher, vous ne pourriez être plus dans l'erreur. Seriez-vous prêt⋅es, par exemple, à m'envoyer une copie de vos mails ? À me laisser lire vos SMS ou vos messages facebook ? Voire à me laisser installer de quoi en rediriger systématiquement une copie chez moi pour que cette consultation ne soit plus ponctuelle mais systématique et automatique ?

J'en doute, alors pourquoi accepter que d'autres le fassent sans vous en demander la permission ?

Le plus souvent, c'est parce que la cryptographie fait peur. C'est des maths compliquées, il y a plein de gens qui vous disent qu'on est de toute façon jamais protégés à 100% et ça utilise des concepts hyper obscurs.

Si vous vous êtes déjà retrouvé face à quelqu'un qui tente de vous expliquer le besoin de chiffrement en décrivant dans le détail un échange de clé Diffie-Hellman, vous savez sûrement qu'on en ressort avec le cerveau en bouillie et l'impression que c'est se donner beaucoup de mal pour que la NSA ne sache pas que vous aurez un quart d'heure de retard en rentrant du boulot.

C'est pour ça que je vais tenter de procéder autrement en présentant quelques exemples de solutions simples à mettre en place sur votre ordiphone pour que vos communications gagnent un peu en confidentialité.

Parce qu'il faut bien l'avouer, pour l'instant, passer un appel c'est comme crier dans la rue en espérant que personne d'autre que votre correspondant n'écoute et envoyer un sms ou un mms, c'est brandir une pancarte en espérant que personne d'autre ne regarde.

Ces solutions sont toutes <strong>libres</strong>, c'est à dire que le code source des logiciels et les protocoles de sécurité sont publics afin que toutes celles et ceux qui le veulent et qui le peuvent puissent vérifier qu'il n'y a pas anguille sous roche. Ce n'est pas un gage d'infaillibilité, mais c'est un gage de confiance puisque c'est le seul moyen d'être sûr qu'aucune action malveillante ne sera entreprise volontairement par le logiciel et ses développeurs.

En revanche, elles ne sont pas anonymisantes. Un observateur sera <strong><em>capable de voir avec qui</em></strong> vous discutez, mais il lui sera tout de même <strong><em>impossible de savoir de quoi</em></strong> vous discutez.

<h2>Pour sécuriser ses appels : RedPhone</h2>

[caption id="attachment_1458" align="alignright" width="300"]<img src="https://aldarone.fr/wp-content/uploads/2014/02/8315ae507a049ffeaf669c32b8644681-300x146.jpg" alt="RedPhone, la sécurité simplifiée." width="300" height="146" class="size-medium wp-image-1458" /> RedPhone, la sécurité simplifiée.[/caption]

RedPhone est une solution libre de VoIP chiffrée. Concrètement, ça veut dire que vous allez passer des appels qui passeront par la 3G (et seront comptés dans votre consommation « data ») ou WiFi au lieu d'être décomptés de votre forfait voix et que le flux audio sera chiffré pour que seul votre correspondant puisse entendre ce que vous dites.

Son utilisation est enfantine : Une fois que vous avez <a href="https://play.google.com/store/apps/details?id=org.thoughtcrime.redphone">téléchargé et installé RedPhone</a>, le logiciel va vous demander votre numéro de téléphone et va vous envoyer un SMS de confirmation qu'il récupèrera automatiquement. Voila, vous êtes prêt.

À partir de maintenant, quand vous voudrez passer un appel sécurisé, lancez RedPhone, choisissez un contact. Si il utilise RedPhone, l'appel sera chiffré, si il n'utilise pas RedPhone vous pourrez lui envoyer un message lui demandant de l'installer.

[gallery type="rectangular" link="file" ids="1460,1459,1461"]

<strong>Note technique :</strong> Vous avez peut-être froncé les sourcils, à raison, au moment de lui indiquer votre numéro de téléphone. C'est nécessaire pour établir l'annuaire des numéros disponibles sur RedPhone et savoir facilement si votre correspondant peut recevoir les appels et c'est également la solution la plus fiable pour répondre à une contrainte technique appelée « NAT Traversal. »

En effet, quand vous utilisez votre smartphone, vous êtes probablement en WiFi derrière une box, ou dans le réseau privé de votre opérateur mobile, bref vous n'avez pas un accès <em>direct</em> à internet. Et dans ce cas, il est très compliqué d'établir une connexion avec un tiers situé lui aussi derrière une box ou dans un réseau privé sans passer par un intermédiaire. Toutefois, dans le cas de RedPhone, cet intermédiaire ne sert que de relais et ne peut pas écouter la conversation.

<h2>Sécuriser ses messages</h2>

Nous avons vu à quel point il était aisé de passer des appels sécurisés, maintenant voyons comment échanger des messages et des documents. Vous verrez, c'est tout aussi simple.

<h3>La sécurité sans concession : TextSecure</h3>

[caption id="attachment_1464" align="alignright" width="300"]<img src="https://aldarone.fr/wp-content/uploads/2014/02/textsecure-300x146.jpg" alt="TextSecure, la sécurité simplifiée" width="300" height="146" class="size-medium wp-image-1464" /> TextSecure, la sécurité simplifiée[/caption]

TextSecure est une solution libre d'envoi de SMS chiffrés. Concrètement, cela veut dire que vous allez envoyer des SMS chiffrés qui seront traités comme n'importe quel SMS par votre opérateur et qui seront déchiffrés sur le téléphone de votre correspondant⋅e. Depuis la version 2 il est également possible de passer par les serveurs de TextSecure (qui ont le même rôle que ceux de RedPhone) afin que votre opérateur soit dans l'incapacité de savoir avec qui vous communiquez.

Si vous avez une impression de déjà vu, c'est normal, elle est développée par la même communauté que RedPhone.

À l'utilisation, c'est tout aussi enfantin. L'application se présente comme une application de SMS classique. Elle est d'ailleurs en passe de devenir l'application SMS par défaut de la célèbre ROM pour Android : « Cyanogen »

Après avoir <a href="https://play.google.com/store/apps/details?id=org.thoughtcrime.securesms">téléchargé et installé TextSecure</a> l'application vous demandera si vous souhaitez créer un mot de passe pour protéger vos messages au cas où votre téléphone tomberai entre de mauvaises mains, puis elle vous demandera si il faut importer les SMS déjà existants dans le téléphone vers sa propre base. L'intérêt de cette opération étant que vos SMS se retrouvent chiffrés sur votre téléphone et que pour les lire il faudra entrer le mot de passe créé précédemment.

Vous pourrez tout de même réaliser un export chiffré ou en clair de la base de messages en guise de sauvegarde.

À partir de maintenant, si vos contacts utilisent eux aussi TextSecure, l'application vous proposera de chiffrer vos échanges. Cela se matérialise par un premier échange de clé (celui dont l'explication technique donne mal à la tête) automatique puis les SMS seront chiffrés automatiquement sans autre action nécessaire de votre part et sans aucun intermédiaire impliqué.

[gallery type="rectangular" link="file" ids="1470,1466,1467,1468,1469"]

Notez tout de même que si vous créer un mot de passe au démarrage de l'application et que vous même l'oubliez, il vous sera impossible de lire les messages présents dans la base, ils seront alors perdus à jamais. Vous devrez supprimer l'application et la réinstaller pour pouvoir régénérer un nouveau mot de passe et recommencer avec une base vide.

<h3>La sécurité pratique : Telegram</h3>

<img src="https://aldarone.fr/wp-content/uploads/2014/02/Telegram.png" alt="Telegram" width="300" height="300" class="alignright size-full wp-image-1472" />

Dans la première édition de cet article, je présentais Telegram comme une alternative moins sécurisée mais plus pratique à TextSecure, toutefois depuis la sortie de TextSecure V2 il n'y a plus davantage à utiliser Telegram puisque l'écart de fonctionnalité est inexistant et la sécurité est bien meilleure.

<h2>Simple comme bonjour</h2>

<img src="https://aldarone.fr/wp-content/uploads/2014/02/Montessori-game-Baby-educational-toys-children-old-thirteen-hole-intelligence-box-shape-building-block-toy-gift-150x150.jpg" alt="Montessori-game-Baby-educational-toys-children-old-thirteen-hole-intelligence-box-shape-building-block-toy-gift" width="150" height="150" class="alignleft size-thumbnail wp-image-1480" />

Après de longues années où le besoin de confidentialité croissait et où les solutions pour en profiter à un niveau suffisant étaient particulièrement rebutantes, nous voyons à présent arriver de nouvelles applications qui s'installent en un clic et sont aussi simple d'utilisation et pratique que n'importe quelle autre application non sécurisée.

Il ne vous reste plus qu'à sauter le pas.

<h2>Diffie-Hellman</h2>

Et comme je ne peux décemment pas vous laisser comme ça en évoquant Diffie-Hellman tout le long de l'article ainsi que les maux de tête qu'il engendre chez les personnes qui ont des boutons dès qu'ils entendent « Arithmétique » voila une petite vidéo en anglais qui vulgarise ce fameux échange de clés en utilisant des couleurs, de la peinture, une corde et une horloge.

https://www.youtube.com/watch?v=3QnD2c4Xovk