<!DOCTYPE html>
<html lang="fr">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<h2>Installation de logiciels</h2>
</head>
<body>

<h2>INSTALLATION DE MYSQL</h2>
<p><strong>CODE SOURCE:</strong> mysql-8.0.36.tar.gz</p>
<p>Il faut tout d’abord décompresser et désarchiver:</p>
<ul>
    <li><code>:~$ tar -zxvf mysql-8.0.36.tar.gz</code></li>
</ul>

<p>Après on va se déplacer dans le répertoire:</p>
<ul>
    <li><code>:~$ cd mysql-8.0.36</code></li>
</ul>

<p>Ensuite, on va lire les fichiers comme README pour voir comment installer mysql.</p>
<ul>
    <li><code>:~/mysql-8.0.36$ more README</code></li>
</ul>

<p>D’après les documentations, on a besoins de cmake:</p>
<ul>
    <li><code>:~/mysql-8.0.36$ sudo apt-get install cmake</code></li>
</ul>

<p>D’après les documentations, on a aussi besoins de créer un répertoire «build»:</p>
<ul>
    <li><code>:~/mysql-8.0.36$ mkdir build</code></li>
    <li><code>:~/mysql-8.0.36$ cd build</code></li>
</ul>

<p>Ensuite, on va éxécuter la commande cmake pour faire sortir le makefile:</p>
<ul>
    <li><code>:~/mysql-8.0.36/build$ cmake ..</code></li>
</ul>

<p>Seulement, il y’a des erreurs dû aux dépendances. (C’est au cours de l’éxécution de «cmake ..» qu’on peut identifier les dépendances que cmake a besoins). On va donc installer les dépendances que mysql a besoins:</p>
<ul>
    <li><code>:~/mysql-8.0.36/build$ sudo apt-get install build essential</code></li>
    <li><code>:~/mysql-8.0.36/build$ sudo apt-get install libblkid-dev e2fslibs-dev libboost-all-dev libbaudit-dev</code></li>
    <li><code>:~/mysql-8.0.36/build$ sudo apt-get install pkg-config</code></li>
    <li>Cmake a besoins de boost pour fonctionner, donc on va installer par code source boost:
        <ul>
            <li><strong>CODE SOURCE:</strong> boost_1_77_0.tar.bz2</li>
            <li>DECOMPRESSION et DESARCHIVATION:</li>
            <ul>
                <li><code>:~/mysql-8.0.36/build$ cd</code></li>
                <li><code>:~$ tar -jxvf boost_1_77_0.tar.bz2</code></li>
                <li><code>:~$ cd boost_1_77_0</code></li>
            </ul>
            <li>On va exécuter le script bootstrap.sh puis on obtient un fichier «b2» que l’on va éxécuter et on va ensuite installer (On a identifié les étapes à suivre grâce aux documentations):</li>
            <ul>
                <li><code>:~/boost_1_77_0$ ./bootstrap.sh</code></li>
                <li><code>:~/boost_1_77_0$ sudo ./b2</code></li>
                <li><code>:~/boost_1_77_0$ sudo ./b2 install</code></li>
            </ul>
        </li>
    </ul>
</ul>

<p>Maintenant que l’on a les dépendances, on va refaire l’opération:</p>
<ul>
    <li><code>:~$ cd mysql-8.0.36/build</code></li>
    <li><code>:~/mysql-8.0.36/build$ cmake ..</code></li>
</ul>

<p>On va utiliser les commandes suivantes:</p>
<ul>
    <li><code>:~/mysql-8.0.36/build$ sudo make</code> → Pour compiler les codes sources</li>
    <li><code>:~/mysql-8.0.36/build$ sudo make install</code> → Pour envoyer les fichiers dans l’arborescence et termine l’installation</li>
</ul>

<p>(Cette image correspond à la fin de l’opération de «make install»)</p>

<p>Pour vérifier que mysql est bien installé, on va faire la commande suivante:</p>
<ul>
    <li><code>:~$ /usr/local/mysql/bin/mysql --version</code></li>
</ul>

<h2>INSTALLATION DE APACHE</h2>
<p><strong>CODE SOURCE:</strong> httpd-2.4.59.tar.gz</p>
<p>Il faut tout d’abord décompresser et désarchiver:</p>
<ul>
    <li><code>:~$ tar -zxvf httpd-2.4.59.tar.gz</code></li>
</ul>

<p>Après on va se déplacer dans le répertoire:</p>
<ul>
    <li><code>:~$ cd httpd-2.4.59</code></li>
</ul>

<p>Puis, il faut lire les documentations pour comprendre comment installer apache.</p>
<ul>
    <li><code>:~/httpd-2.4.59$ more README</code></li>
</ul>

<p>Ensuite, on va éxecuter le fichier configure pour faire sortir le makefile:</p>
<ul>
    <li><code>:~/httpd-2.4.59$ ./configure</code></li>
</ul>

<p>Seulement, il y’a des erreurs dû aux dépendances. On va donc télécharger les dépendances qu’apache a besoin (C’est au cours de l’éxécution «./configure» qu’on peut identifier les dépendances qu’apache a besoins):</p>
<ul>
    <li><code>:~/httpd-2.4.59$ sudo apt-get install libapr1 libapr1-dev</code></li>
    <li><code>:~/httpd-2.4.59$ sudo apt-get install libaprutil libaprutil1-dev</code></li>
    <li><code>:~/httpd-2.4.59$ sudo apt-get install libpcre3 libpcr3-dev</code></li>
</ul>

<p>Maintenant que l’on a les dépendances, on va refaire l’opération:</p>
<ul>
    <li><code>:~/httpd-2.4.59$ ./configure</code></li>
</ul>

<p>On va utiliser les commandes suivantes:</p>
<ul>
    <li><code>:~/httpd-2.4.59$ sudo make</code> → Pour compiler les codes sources</li>
    <li><code>:~/httpd-2.4.59$ sudo make install</code> → Pour envoyer les fichiers dans l’arborescence</li>
</ul>

<p>Pour vérifier que apache est bien installé, on va faire la commande suivante:</p>
<ul>
    <li><code>:~$ /usr/local/apache2/bin/httpd -v</code></li>
</ul>

<h2>INSTALLATION DE PHP</h2>
<p><strong>CODE SOURCE:</strong> php-8.3.6.tar.gz</p>
<p>Il faut tout d’abord décompresser et désarchiver:</p>
<ul>
    <li><code>:~$ tar -zxvf httpd-2.4.59.tar.gz</code></li>
</ul>

<p>Après on va se déplacer dans le répertoire:</p>
<ul>
    <li><code>:~$ cd php-8.3.6</code></li>
</ul>

<p>Puis, il faut lire les documentations pour comprendre comment installer php.</p>
<ul>
    <li><code>:~/php-8.3.6$ more README.md</code></li>
</ul>

<p>Ensuite, on va éxecuter le fichier configure pour faire sortir le makefile:</p>
<ul>
    <li><code>:~/php-8.3.6$ ./configure</code></li>
</ul>

<p>Seulement, il y’a des erreurs dû aux dépendances. On va donc télécharger les dépendances que php a besoin (C’est au cours de l’éxécution «./configure» qu’on peut identifier les dépendances que php a besoins):</p>
<ul>
    <li><code>:~/php-8.3.6$ sudo apt-get install libxml2-dev</code></li>
    <li><code>:~/php-8.3.6$ sudo apt-get install libsqlite3-dev</code></li>
</ul>

<p>Maintenant que l’on a les dépendances, on va refaire l’opération:</p>
<ul>
    <li><code>:~/php-8.3.6$ ./configure</code></li>
</ul>

<p>On va utiliser les commandes suivantes:</p>
<ul>
    <li><code>:~/php-8.3.6$ sudo make</code> → Pour compiler les codes sources</li>
    <li><code>:~/php-8.3.6$ sudo make install</code> → Pour envoyer les fichiers dans l’arborescence</li>
</ul>

<p>Pour vérifier que php est bien installé, on va faire la commande suivante:</p>
<ul>
    <li><code>:~$ php -v</code></li>
</ul>

</body>
</html>
