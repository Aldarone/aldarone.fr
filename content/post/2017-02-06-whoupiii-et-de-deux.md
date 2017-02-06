+++
comments = true
date = "2017-02-06T19:00:00+01:00"
image = "img/caterpillar.jpg"
slug = "whoupiii-et-de-deux"
title = "Whoupiii ! Et de deux !"
draft = false
+++

Hey c'est donc la deuxième fois de suite que j'écris un article recensant les choses intéressantes de la semaine et je ne le fais qu'avec un seul jour de retard.

On dirait que je suis bien partie, même si cette fois sera plus sobre que la précédente, la faute à l'actualité qui a bouffé tout le temps disponible sur twitter et les tâches pas très passionnantes au boulot qui ne m'ont pas motivées à stimuler ma curiosité.

## Lundi

### Le Global State c'est comme les Singletons : de la merde

En premier lieu et suite au lien à propos des Singletons de [la semaine dernière][articleprecedent], voilà un petit avertissement qui va de pair avec ces sales bêtes : le grand méchant [Global State][globalstate] qui rend impossible à suivre le flux d'informations qui transite dans nos application.

[articleprecedent]: https://aldarone.fr/combien-de-temps-je-vais-my-tenir-cette-fois/
[globalstate]: http://softwareengineering.stackexchange.com/questions/148108/why-is-global-state-so-evil

### Rafraîchir la navigation par onglets

Ensuite, pour celles et ceux qui le savent, Mozilla développe un nouveau moteur HTML, CSS, JS en Rust nommé Servo ainsi qu'un navigateur expérimental nommé browser.html. Si Servo va à terme remplacer Gecko dans Firefox, browser.html est uniquement là pour tenter des trucs vite fait. Celà leur permet donc de réfléchir à des moyens de remplacer la navigation classique utilisant des onglets par [un nouveau concept se basant sur des arbres][trailnavigation]. Et le moins qu'on puisse dire c'est que ça a l'air entousiasmant !

[trailnavigation]: https://medium.com/@patrykadas/lossless-web-navigation-with-trails-9cd48c0abb56#.z76gla3pm

### Nos amis les crustacés et leurs potes céphalopodes

Et pour le dernier lien de la journée, voilà une étude fort intéressante grâce à laquelle nous apprenons que [les crustacés et les céphalopodes ressentent bel et bien la douleur][crustacé]. Ça fait donc un argument de moins pour les ennemis des animaux.

[crustacé]: https://www.washingtonpost.com/national/health-science/do-lobsters-and-other-invertebrates-feel-pain-new-research-has-some-answers/2014/03/07/f026ea9e-9e59-11e3-b8d8-94577ff66b28_story.html

## Mardi

### Ne faites pas votre propre crypto

Pour le seul lien du jour vous aurez droit à un petit coup de gueule technique contre un article expliquant comment utiliser des mots de passe dans ses playbooks Ansible sans devoir les stocker en clair.

C'est effectivement une bonne pratique que de ne pas stocker en clair ses mots de passe, surtout à côté de ses playbooks, mais il y a une règle d'or en sécurité informatique qui est la suivante : NE FAITES PAS VOTRE PROPRE CRYPTO. Sauf bien sûr si vous êtes une bande d'experts en crypto (et seulement si vous êtes une bande)

[Cet article][badcrypto] montre donc comment écrire en Python un script qui va chiffrer et déchiffrer des mots de passe à l'aide de l'algo 3DES. Cet intéressant d'un point de vue éducatif mais de grâce ne faites pas ça chez vous.

Déjà parce que vous avez mieux à faire que maintenir un énième script maison, ensuite parce que [le NIST estime que 3DES ne sera plus fiable d'ici 2030][nist] et enfin parce qu'Ansible a déjà de quoi gérer ce souci à l'aide de la commande [ansible-vault][vault]

Donc retenez deux choses : Ne faites pas votre propre crypto et lisez la doc de vos outils.

[badcrypto]: http://lesaventuresdeyannigdanslemondeit.blogspot.com/2017/01/chiffrementdechiffrement-des-mots-de.html
[nist]: https://www.keylength.com/fr/4/
[vault]: http://docs.ansible.com/ansible/playbooks_vault.html

## Mercredi

### Gitlab.com et ses backups foireux

Ce jour a suirtout été marqué par [l'énorme plantage de Gitlab.com][gitlabfail] qui, à la suite d'une erreur de manip et d'une politique de backup non testée, a perdu 6h de données.

Ils ont fait preuve d'une transparence assez exemplaire, allant même jusqu'à livestreamer les réparations.

[gitlabfail]: https://about.gitlab.com/2017/02/01/gitlab-dot-com-database-incident/

## Vendredi

### C'est quoi un blanc ?

Enfin, pour terminer ce billet, voilà une réflexion assez cruciale dans les luttes de l'anti-racisme politique qui, en plus d'éclairer pas mal sur le sens de ces luttes permet d'évacuer les accusations de « vrai racisme, » de « racialisme, » ou de « communautarisme dont sont souvent accusés les partisans de cet anti-racisme politique :  [Mais qui sont les blancs ?][pirblanc]

[pirblanc]: http://indigenes-republique.fr/mais-qui-sont-les-blancs/

## Fin

Je vous avais prévenu qu'il y aurais moins de liens cette fois, mais j'espère me rattraper la semaine prochaine !
