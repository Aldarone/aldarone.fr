---
ID: 167
author: Alda
bitlyURL:
- http://bit.ly/oczbnR
- http://bit.ly/oczbnR
date: 2011-10-03T00:00:00Z
dsq_thread_id:
- "432718683"
- "432718683"
head_img:
- |
  https://aldarone.fr/assets/Ubuntu-Nginx-MariaDB-PHP.jpg
- |
  https://aldarone.fr/assets/Ubuntu-Nginx-MariaDB-PHP.jpg
head_img_alt:
- Logo Ubuntu Nginx MariaDB PHP
- Logo Ubuntu Nginx MariaDB PHP
post_date: 2011-10-03 10:58:29
post_excerpt: ""
post_title: Avec quoi il marche ton serveur ?
published: true
url: /avec-quoi-il-marche-ton-serveur/
---

<p>Comme promis, un billet un peu technique pour vous expliquer quels logiciels se cachent derrière ce blog et comment ils sont configurés pour vivre en harmonie.</p>

<p>Quand j'ai commencé, c'était un LAMP classique (Ubuntu LTS server, Apache2, Mysql et Php). Assez rapidement j'ai eu envie d'optimiser un peu tout ça donc j'ai rajouté un Nginx qui envoyait tous les fichiers statiques (En me basant sur cet excellent tuto de PapyGeek: <a href="http://www.papygeek.com/software/optimiser-son-serveur-web-avec-nginx/">Optimiser son serveur web avec Nginx</a>)</p>

<p>Ça fait très bien tourner <a href="http://poly4mour.fr/">Poly4mour.fr</a>, <a href="http://noli.fr/">Noli.fr</a> ou encore <a href="http://www.fufusfous.fr/">Les Fufus fous</a> qui sont hébergés sur le même serveur et ça va rester comme ça un certain temps étant donné que je suis encore plus à l'aise avec Apache qu'avec Nginx.</p>

<p>Mais pour mon blog je voulais un truc qui me permettrai d'expérimenter un peu et donc Apache laisse la place à Nginx et Php-fpm.</p>

<p>J'en ai profité d'abord pour passer à la dernière version stable d'Nginx (celle présente dans Lucid Lynx va très bien mais il y a un dépot officiel alors autant l'utiliser) :</p>

<pre><code>sudo add-apt-repository ppa:nginx/stable
</code></pre>

<p>Il faut ensuite installer le paquet php-fpm qui permet d'utiliser php avec nginx. Il a été ajouté dans Ubuntu à partir de la version Maverick et n'est donc pas disponible dans les dépots pour Lucid. Heureusement, le responsable des paquets PHP pour Debian a un dépôt à jour sur Launchpad:</p>

<pre><code>sudo add-apt-repository ppa:ondrej/php5
</code></pre>

<p>(Si, comme moi vous avez mis à jour depuis Ubuntu 8.04, vous n'avez peut-être pas la commande <code>add-apt-repository</code>. Il vous faudra installer <code>python-software-properties</code> avant. Ou bien rajouter les dépot « à l'ancienne »)</p>

<p>Reste à lancer l'installation proprement dite:</p>

<pre><code>sudo apt-get update
sudo apt-get upgrade
sudo apt-get install php5-fpm
</code></pre>

<p>Et voila, tout est en place, on va maintenant dire à Nginx d'utiliser php-fpm pour servir le contenu dynamique:</p>

<p>Attention, nginx n'utilise pas les fichier <code>.htaccess</code>, si vous avez des règles d'URL rewriting, ou des restrictions sur certains fichiers il vous faudra lire un peu la doc d'Nginx pour adapter tout ça.</p>

<pre><code>server {
    listen   80;
    server_name aldarone.fr www.aldarone.fr blog.aldarone.fr;
    access_log  /var/log/nginx/aldarone.fr.access.log;
    error_log  /var/log/nginx/aldarone.fr.error.log error;

    root /home/web/aldarone/blog;

    #Réécriture d'URL pour supprimer www
    if ($host !~* ^aldarone.fr ) {
            rewrite ^/(.*)$ https://aldarone.fr/$1 permanent;
    }

    #La partie intéressante
    location ~ .php$ {
            fastcgi_split_path_info ^(.+.php)(.*)$;
            fastcgi_pass   127.0.0.1:9000; #php-fpm est en fait un démon qui écoute sur le port localhost:9000
            fastcgi_index  index.php;
            fastcgi_param  SCRIPT_FILENAME  /home/web/aldarone/blog$fastcgi_script_name; #Ici on indique à php le chemin des scripts qu'il exécute
            include fastcgi_params;
            fastcgi_param  QUERY_STRING     $query_string;
            fastcgi_param  REQUEST_METHOD   $request_method;
            fastcgi_param  CONTENT_TYPE     $content_type;
            fastcgi_param  CONTENT_LENGTH   $content_length;
            fastcgi_intercept_errors        on;
            fastcgi_ignore_client_abort     off;
            fastcgi_connect_timeout 60;
            fastcgi_send_timeout 180;
            fastcgi_read_timeout 180;
            fastcgi_buffer_size 128k;
            fastcgi_buffers 4 256k;
            fastcgi_busy_buffers_size 256k;
            fastcgi_temp_file_write_size 256k;
    }

    #Réécriture d'URL pour avoir de jolis permalinks sous wordpress
    rewrite /wp-admin$ $scheme://$host$uri/ permanent;
    try_files $uri $uri/ /index.php?$args;
}
</code></pre>

<p>Une fois la configuration en place, n'oubliez pas de relancer Nginx pour prendre les changements en compte:</p>

<pre><code>service nginx restart
</code></pre>

<p>Si tout s'est bien passé votre blog devrait être accessible normalement, à la différence qu'il se chargera plus rapidement et que l'occupation mémoire sera bien moindre.</p>

<p>Dans un prochain épisode, je vous expliquerai comment vous libérer de la mainmise d'Oracle sur MySQL en passant migrant vers MariaDB.</p>