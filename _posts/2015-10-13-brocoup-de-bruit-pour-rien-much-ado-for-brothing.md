---
ID: 1646
post_title: 'Brocoup de bruit pour rien &#8211; Much ado for Brothing'
author:
  - Alda
post_date:
  - 2015-10-13 13:05:49
post_excerpt:
  - ""
layout: post
permalink: >
  /brocoup-de-bruit-pour-rien-much-ado-for-brothing/
published: true
---

À la fin de la semaine passée, une nouvelle inquiétante (pour ne pas dire catastrophique) a commencé à se répandre sur les internets :
Mozilla agirait de concert avec les féministes pour faire peser une insupportable censure sur le géant Google.

Voyez plutôt :

Google a annoncé fin septembre, le 22, un nouvel algorithme de compression nommé Brotli, capable d'offrir une compression équivalente à LZMA ou bzip2
pour des performances approchant celles de deflate. Qui dit nouveau format dit également nouvelle extension de fichier, c'est pourquoi, en suivant une convention
aussi vieille que techniquement dépassée, il fut tout naturellement proposé de tronquer le nom de l'algorithme à 3 caractères, donnant ainsi l'extension .bro
aux fichiers compressés par brotli.

C'est là que le bat blesse et que les vilaines féministes entrent en jeu pour exercer une pression terrible sur la personne ayant fait cette proposition,
forçant ainsi le malheureux développeur à s'auto-censurer pour ne pas subir plus de harcèlement de la part de ces furies.

Pour lutter contre la pensée unique qui émane de leur action, je décide ce soir, en dépit des risques, de reproduire ici les vifs échanges ayant eu lieu <a href="https://bugzilla.mozilla.org/show_bug.cgi?id=366559#c146">sur le bugtracker de Mozilla</a> :

<ol>
<li>Jyrki Alakuijala :

<blockquote>
  In https://datatracker.ietf.org/doc/draft-alakuijala-brotli/ section 12. 'IANA Considerations' we are making a reservation for content encoding type 'bro', not 'brotli'.

  We are hoping to establish a file ending .bro for brotli compressed files, a command line tool 'bro' for compressing and uncompressing brotli files, and a accept/content encoding type 'bro'.

  bro is short for brotli -- there are no hidden meanings in it, just practicality: less typing, less bytes to upload/download, shorter compressed filenames.

  <blockquote>
    Dans la section 12 du document « Préparations pour l'IANA » nous réservons le type d'encodage de contenu « bro » et non « brotli »

    Nous espérons fournir une extension en .bro pour les fichiers compressés par brotli, un outil en ligne de commande « bro » pour compresser et décompresser les fichiers brotli, ainsi qu'un type d'encodage « bro »

    Bro est le diminutif de brotli, il n'y a pas de sens caché, jsute de la praticité : Moins de caractères, moins d'octets à envoyer ou recevoir, des noms de fichier plus courts.
  </blockquote>
</blockquote></li>
<li>Patrick McManus :

<blockquote>
  Thanks for pointing that out jyrki, can I talk you out of it? Certainly not too late to change the draft registration.

  "bro" has a gender problem, even though the dual meaning is unintentional. It comes of misogynistic and unprofessional due to the world it lives in. I received a series of 'bro' jokes in response to my posting about this new feature.

  Best to avoid it rather than spending time defending an arbitrary nickname.

  My interest is only in content-encoding interop.

  <blockquote>
    Merci pour cette précision jyrki, est-ce que je peux rajouter quelque chose ? Il n'est certainement pas trop tard pour modifier le brouillon d'enregistrement.

    « bro » va poser un problème de genre, même si le double sens n'est pas volontaire. Il semble misogyne et peu professionnel en raison du monde dans lequel nous vivons. J'ai déjà reçu une série de « blague de bro » en réponse à mon annonce de cette nouvelle fonctionnalité.

    Il vaut mieux l'éviter plutôt que de perdre du temps à défendre un surnom arbitraire.

    Mon seul intérêt réside dans l'interopérabilité des encodages de contenu.
  </blockquote>
</blockquote></li>
<li>Jyrki Alakuijala :

<blockquote>
  would you be fine with 'br' ?

  <blockquote>
    Est-ce que « br » conviendrait ?
  </blockquote>
</blockquote></li>
<li>Patrick McManus :

<blockquote>
  sounds good - thanks. I'll make that change and let the content-provider I know is working with this know.

  <blockquote>
    Ça m'a l'air bien, merci. Je vais répercuter ce changement et je vais prévenir les fournisseurs de contenu qui travaillent dessus.
  </blockquote>
</blockquote></li>
<li>Jyrki Alakuijala :

<blockquote>
  No, thank you for the advice. It is always better to fix things like this as early as possible.

  <blockquote>
    Non, merci à toi pour le conseil. C'est toujours mieux de corriger ce genre de choses le plus tôt possible.
  </blockquote>
</blockquote></li>
</ol>

Quelle pression insupportable pèse sur les épaules de ce malheureux Jyrki.

<img src="http://stream1.gifsoup.com/view/991630/dramatic-look-o.gif" alt="dramatic look" />

<h2>Un peu de sérieux s'il vous plait.</h2>

Depuis cet instant, nous pouvons voir fleurir les articles incendiaires écris par des hommes se sentant menacés par une modification mineure dans un brouillon de spécification.

Sur <a href="http://www.ghacks.net/2015/10/11/bro-file-extension-offensive-changed-to-br-instead/">gHacks</a> on peut ainsi lire :

<blockquote>
  While it does not really matter in the end if the extension is called bro or br or something else, bro should not be offensive to anyone especially since barely anyone will ever come into contact with it in first place. People who are offended by a file extension, or think others might be offended by it, should get their priorities straight as there are bigger fish to fry.
</blockquote>

Dans un même paragraphe, l'auteur est capable d'affirmer que ça n'a aucune espèce d'importance puis de conclure que les féministes devraient revoir leurs priorités. Pourquoi s'affoler, en faire un article et s'opposer de tout son poids contre un changement qui n'aurait pas la moindre importance ?

Du côté de <a href="https://www.reddit.com/r/technology/comments/3oa2qh/google_removes_bro_file_extension_from_project/">Reddit</a>, ça titre comme ça :

<blockquote>
  Google removes .bro file extension from project for possibly being offensive and/or misogynistic according to feminists
</blockquote>

Alors qu'il s'agit d'une discussion entre deux hommes dont aucun ne déclare spécifiquement qu'ils sont féministes.

Sur <a href="http://tech.slashdot.org/story/15/10/10/2212233/there-is-no-bro-in-brotli-googlemozilla-engineers-nix-file-type-as-offensive">Slashdot</a>, on prétend que le sujet fait controverse depuis l'annonce de Brotli :

<blockquote>
  Several weeks ago, Google launched Brotli, a new open source compression algorithm for the web. Since then, controversy broke out over the choice of 'bro' as the content encoding type.
</blockquote>

Si on regarde la chronologie des fait, c'est n'est absolument pas le cas :

Brotli a été annoncé le 22 septembre. Le premier commentaire que je cite plus haut a été posté le 05 octobre, la proposition de passer à .br plutôt que .bro a été émise, acceptée et commitée le 06 octobre. Le post sur Slashdot est arrivé le 10 octobre, soit 4 jours après « la bataille »

C'est aussi à partir de ce moment que l'on trouve en trouve des traces sur Reddit et que les commentaires du ticket Bugzilla ainsi que du commit validant la modification commencent à se faire troller.

Qualifier ces évènements de controversés revient à utiliser une définition très particulière du mot « controverse » quand toute cette histoire n'est qu'une discussion sur un coin de table pendant la rédaction d'un brouillon qui a été ensuite montée en épingle par les conservateurs et les réactionnaires. Un cas d'école illustrant parfaitement leur maitrise du <a href="https://fr.wikipedia.org/wiki/Fear,_uncertainty_and_doubt">FUD</a> et de l'<a href="https://fr.wikipedia.org/wiki/Astroturfing">astroturfing</a>.

Je laisserai donc le mot de la fin au développeur qui a effectué la modification :

<blockquote>
  Even if we don't understand why people are upset from our cultural standpoint, they would be (unnecessarily) upset and this is enough reason not to use it.

  <blockquote>
    Même si, de notre point de vue culturel, nous ne comprenons pas pourquoi cela dérangerait des gens, illes le seraient sans nécessité et c'est une raison suffisante pour de pas utiliser cette extension.
  </blockquote>
</blockquote>
