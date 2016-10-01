---
date: "2011-10-07T00:00:00Z"
title: "Le parent-theme d'Aldarone.fr: Roots pour WordPress"
slug: "parent-theme-aldarone-fr-roots-wordpress"
---

![Roots Parent Theme](/img/Roots-parent-theme.jpg)

Après avoir parlé un peu de l'architecture système qui se cache derrière ce blog (avec mes articles sur <a href="https://aldarone.fr/avec-quoi-il-marche-ton-serveur/" title="Avec quoi il marche ton serveur ?">Comment utiliser nginx et php-fpm</a> et <a href="https://aldarone.fr/passer-de-mysql-a-mariadb/" title="Passer de MySQL à MariaDB">Comment remplacer MySQL par MariaDB</a>) je vais vous parler un peu de Wordpress.

Le thème est un « <a href="http://codex.wordpress.org/Child_Themes">child theme</a> » créé par moi et basé sur l'excellent <a href="http://www.rootstheme.com/">Roots</a> (dans le sens où c'est le seul « parent theme » qui ai réussi à me donner envie de faire un child plutôt que tout faire moi même).

Tout ce qu'il me fallait est là: <a href="http://fr.html5boilerplate.com/">HTML5 Boilerplate 2.0</a> pour le HTML, <a href="http://www.blueprintcss.org/">Blueprint</a> pour le système de grid CSS (mais on peut aussi utiliser <a href="http://cssgrid.net/">1140Grid</a> ou <a href="http://960.gs/">960gs</a> en changeant une option), compatibilité directe avec <a href="http://fancybox.net/">Fancybox</a> (seuls les fichiers JS sont à inclure)

Je n'ai donc eu que très peu de modifications à faire. L'essentiel s'est résumé à adapter un peu pour lui redonner un comportement de blog (il est plutôt fait pour des sites et l'usage des pages) et quelques classes ajoutées par-çi par-là en dur quand je ne trouvais pas le filter permettant de l'ajouter « proprement »

Prochainement vous aurez droits à quelques fonctions qui peuplent mon « <em>functions.php</em> » de manière quasi systématique.
