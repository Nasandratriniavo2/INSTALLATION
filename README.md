# INSTALLATION
NSTALLATION DE MYSQL
CODE SOURCE:mysql-8.0.36.tar.gz
→Il faut tout d’abord décompresser et désarchiver:
    • :~$ tar -zxvf mysql-8.0.36.tar.gz

→Après on va se déplacer dans le répertoire:
    • :~$ cd  mysql-8.0.36

→Ensuite,on va lire les fichiers comme README pour voir comment installer mysql.
    • :~/mysql-8.0.36$ more README


→D’après les documentations,on a besoins de cmake:
    • :~/mysql-8.0.36$ sudo apt-get install cmake

→D’après les documentations,on a aussi besoins de créer un repertoire «build»:
    • :~/mysql-8.0.36$ mkdir build
    • :~/mysql-8.0.36$ cd build

→Ensuite,on va éxecuter la commande cmake pour faire sortir le makefile:
    • :~/mysql-8.0.36/build$ cmake ..
Seulement,il y’a des erreurs dû aux dépendances.(C’est au cours de l’ éxécution de «cmake ..» qu’on peut identifier les dépendances que cmake a besoins).On va donc installer les dépendances que mysql a besoins:
    • :~/mysql-8.0.36/build$ sudo apt-get install build essential
    • :~/mysql-8.0.36/build$ sudo apt-get install libblkid-dev e2fslibs-dev libboost-all-dev libbaudit-dev
    • :~/mysql-8.0.36/build$ sudo apt-get install pkg-config
    • cmake a besoins de boost pour fonctionner,donc on va installer par code source boost:
            ▪ CODE SOURCE:boost_1_77_0.tar.bz2
            ▪ DECOMPRESSION et DESARCHIVATION:
                  →:/mysql-8.0.36/build$ cd
                  →:~$ tar -jxvf boost_1_77_0.tar.bz2 
                  →:~$ cd boost_1_77_0
            ▪ On va executer le script bootstrap.sh puis on obtient un ficher «b2» que l’on va éxécuter et on va ensuite installer(On a identifier les étapes à suivre grâce aux documentations):
                  →:~/boost_1_77_0$ ./bootstrap.sh
                  →:~/boost_1_77_0$ sudo ./b2
                  →:~/boost_1_77_0$ sudo ./b2 install  
      
→Maintenant que l’on a les dépendances,on va refaire l’opération:
    • :~$ cd  mysql-8.0.36/build
    • :~/mysql-8.0.36/build$ cmake ..

→On va utiliser les commandes suivantes:
    • :~/mysql-8.0.36/build$ sudo make →Pour compiler les codes sources  
    • :~/mysql-8.0.36/build$ sudo make install →Pour envoyer les fichiers dans l’arborescence et termine l’installation

(Cette image correspond à la fin de l’opération de «make install»)

→Pour vérifier que mysql est bien installer, on va faire la commande suivante:
    • :~$ /usr/local/mysql/bin/mysql --version



INSTALLATION DE APACHE
CODE SOURCE:httpd-2.4.59.tar.gz
→Il faut tout d’abord décompresser et désarchiver:
    • :~$ tar -zxvf httpd-2.4.59.tar.gz

→Après on va se déplacer dans le répertoire:
    • :~$ cd httpd-2.4.59

→Puis,il faut lire les documentations pour comprendre comment installer apache.
    • :~/httpd-2.4.59$ more README

→Ensuite,on va éxecuter le fihier configure pour faire sortir le makefile:
    • :~/httpd-2.4.59$ ./configure
Seulement,il y’a des erreurs dû aux dépendances.On va donc télécharger les dépendances qu’apache a besoin(C’est au cours de l’éxécution «./configure» qu’on peut identifier les dépendances qu’apache a besoins):
    • :~/httpd-2.4.59$ sudo apt-get install libapr1 libapr1-dev
    • :~/httpd-2.4.59$ sudo apt-get install libaprutil libaprutil1-dev
    • :~/httpd-2.4.59$ sudo apt-get install libpcre3 libpcr3-dev 

→Maintenant que l’on a les dépendances,on va refaire l’opération:
    • :~/httpd-2.4.59$ ./configure

→On va utiliser les commandes suivantes:
    • :~/httpd-2.4.59$ sudo make →Pour compiler les codes sources  
    • :~/httpd-2.4.59$ sudo make install →Pour envoyer les fichiers dans l’arborescence


→Pour vérifier que apache est bien installer, on va faire la commande suivante:
    • :~$ /usr/local/apache2/bin/httpd -v
INSTALLATION DE PHP
CODE SOURCE:php-8.3.6.tar.gz
→Il faut tout d’abord décompresser et désarchiver:
    • :~$ tar -zxvf httpd-2.4.59.tar.gz

→Après on va se déplacer dans le répertoire:
    • :~$ cd php-8.3.6

→Puis,il faut lire les documentations pour comprendre comment installer php.
    • :~/php-8.3.6$ more README.md

→Ensuite,on va éxecuter le fihier configure pour faire sortir le makefile:
    • :~/php-8.3.6$ ./configure
Seulement,il y’a des erreurs dû aux dépendances.On va donc télécharger les dépendances que php a besoin(C’est au cours de l’ éxécution «./configure» qu’on peut identifier les dépendances que php a besoins):
    • :~/php-8.3.6$ sudo apt-get install libxml2-dev
    • :~/php-8.3.6$ sudo apt-get install libsqlite3-dev 

→Maintenant que l’on a les dépendances,on va refaire l’opération:
    • :~/php-8.3.6$ ./configure

→On va utiliser les commandes suivantes:
    • :~/php-8.3.6$ sudo make →Pour compiler les codes sources  
    • :~/php-8.3.6$ sudo make install →Pour envoyer les fichiers dans l’arborescence
      
→Pour vérifier que php est bien installer, on va faire la commande suivante:
    • :~$ php -v
      
