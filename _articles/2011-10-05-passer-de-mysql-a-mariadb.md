---
ID: 193
post_title: Passer de MySQL à MariaDB
author: Alda
post_date: 2011-10-05 08:45:01
post_excerpt: ""
layout: post
permalink: >
  http://aldarone.fr/passer-de-mysql-a-mariadb/
published: true
head_img:
  - >
    http://aldarone.fr/assets/Larry-Ellison.jpg
  - >
    http://aldarone.fr/assets/Larry-Ellison.jpg
head_img_alt:
  - Larry Ellison
  - Larry Ellison
bitlyURL:
  - http://bit.ly/r8kt80
  - http://bit.ly/r8kt80
dsq_thread_id:
  - "434543036"
  - "434543036"
---
<p><strong>Mise à jour 16/10/2011</strong>: Dans la première version j'utilisais l'ancienne version stable de MariaDB (5.1), suite au <a href="http://aldarone.fr/passer-de-mysql-a-mariadb/#comment-335383041">commentaire de Guillaume</a> je l'ai mis à jour pour utiliser la version 5.2.</p>

<p>Depuis quelques temps, Oracle ne se sent plus pisser: Ils rachètent Sun, ils ferment les sources des logiciels qu'ils possèdent, ils font des procès pour gagner des thunes,...</p>

<p>Ils ont tué OpenOffice. Ils vont tuer Java. Donc quand ils ont acheté MySQL, les libristes l'avaient mauvaise. Pourquoi maintiendraient-ils un des plus grand concurrent de leur propre système de base de données ?</p>

<p>Ça n'a pas tardé d'ailleurs, la semaine dernière ils ont annoncé la sortie d'extensions « closed sources » pour MySQL. Donc le passage en mode « open core » : La base devrait rester ouverte mais des fonctions intéressantes vont devenir opaques... Inutile de se leurrer, ce n'est qu'un premier pas vers la mort de MySQL.</p>

<p>Heureusement, le libre est un monde capable de grandes choses (quand les gens ne passent pas leur temps à se troller et à forker pour des raisons d'ego) et un dérivé de MySQL a vu le jour: MariaDB.</p>

<p>En fait comme pour LibreOffice, ce sont de nombreux développeurs du logiciel d'origine qui sont parti continuer leur boulot ailleurs, loin d'Oracle. MariaDB c'est donc MySQL, mais en mieux et en toujours libre, la compatibilité étant évidemment de mise.</p>

<p>Pour remplacer le démon MySQL (au sens informatique et idéologique du terme) <del datetime="2011-10-16T09:33:05+00:00">il existe un dépôt maintenu par le site <a href="http://ourdelta.org/">OurDelta.org</a> que l'on retrouve sur cette page: <a href="http://nerdvana.us.mirror.ourdelta.org/deb/dists/lucid/mariadb-ourdelta/">Dépot MariaDB Lucid Lynx</a> (Ils ont aussi des dépôts pour Debian et CentOS).</del> on peut utiliser le dépôt officiel MariaDB dans sa dernière version stable (la 5.2) :</p>

<pre><code>sudo -s
apt-key adv --recv-keys --keyserver keyserver.ubuntu.com 1BB943DB
echo '# MariaDB repository list - created 2011-10-16 09:36 UTC
# http://downloads.askmonty.org/mariadb/repositories/
deb http://ftp.osuosl.org/pub/mariadb/repo/5.2/ubuntu lucid main
deb-src http://ftp.osuosl.org/pub/mariadb/repo/5.2/ubuntu lucid main' &gt; /etc/apt/sources.list.d/mariadb.list
apt-get update
</code></pre>

<p>Si vous avez Debian ou une autre version d'Ubuntu (ou que vous voulez utiliser MariaDB 5.1 ou 5.3) vous pouvez aller sur <a href="http://downloads.askmonty.org/mariadb/repositories/">le générateur de sources.list de MariaDB</a>.</p>

<p>Pensez à éteindre mysql après avoir fait vos sauvegardes (<code>sudo services mysql stop</code>) et lancez l'installation:</p>

<pre><code>sudo apt-get install mariadb-server mariadb-client
</code></pre>

<p>Terminé ! Le fichier de conf est le même (<code>/etc/mysql/my.cnf</code>), le script de démarrage s'appelle toujours <code>mysql</code> mais si vous avez besoin d'en avoir le coeur net voila ce qu'on obtient en se connectant en ligne de commande:</p>

<pre><code>mysql -p
Enter password:
Welcome to the MariaDB monitor.  Commands end with ; or g.
Your MariaDB connection id is 181
Server version: 5.2.9-MariaDB-mariadb102~lucid-log (MariaDB - http://mariadb.com/)

This software comes with ABSOLUTELY NO WARRANTY. This is free software,
and you are welcome to modify and redistribute it under the GPL v2 license

Type 'help;' or 'h' for help. Type 'c' to clear the current input statement.

MariaDB [(none)]&gt;
</code></pre>

<p>Un bémol toutefois, la compatibilité a beau être excellente il reste néanmoins quelques petits trucs qui ne marchent pas. Par exemple MariaDB n'aime pas la date <code>0000-00-00 00:00:00</code>, or c'est une date par défaut utilisé dans pas mal de schémas (Wordpress par exemple). Pour une application qui a déjà sa base configurée ça ne posera pas de problème, en revanche elle n'arrivera pas à la créer dans le cas d'une nouvelle installation.</p>

<p>Pour y remédier, il suffit de supprimer le mode strict dans le fichier de configuration <code>/etc/mysql/my.cnf</code> en commentant la ligne suivante:</p>

<pre><code>sql-mode = STRICT_TRANS_TABLES 
</code></pre>

<p>J'imagine que vous êtes des gens responsables et donc il est inutile que je précise qu'il est recommandé de faire des backups et des tests avant d'opérer une migration sur un serveur en production.</p>