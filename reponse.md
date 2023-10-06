 1 : il va d'abord falloir créer un dockerfile pour donner les informations de bases pour l'image (voir Dockerfile), ensuite il faudra se positionner dans le bon dossier, ici le dossier site-web grace à la commande :

  cd /Users/antoineporignaux/Desktop/cours_andré_kouamé/devoir_1/docker-devoir-premier-annee/site-web 
  
  (pour trouver l'emplcament exacte du fichier je fais un clic droit sur le dossier site-web dans la fenetre explorer de vs code qui est juste à droite, et je selectionne copy path), maintenant que nous sommmes dans le bon dossier nous pouvons exectuter les commandes ;

  docker build -t aporignaux11/the_list:3.4.5 .

  à présent l'image est créer et est dans le daemon.

  2 : pour créer 2 container similaires tournant sur 2 ports différents il faut utiliser les commandes :

  docker run -d -p 80:80 aporignaux11/the_list:3.4.5 

  docker run -d -p 8000:80 aporignaux11/the_list:3.4.5 

  les 2 container run et nous pouvons le verifier tapant l'url localhost:80 et localhost:8000 sur un navigateur, avec nos 2 commandes ci-dessus nos container ont des noms aléatoires, il faut donc les rename avec la commane :

  docker rename [former_name] site_web_one
  docker rename [former_name] site_web_two

  nos 2 containers portent à présent des noms définis 
 
  3 : il va falloir arreter le run des 2 containers precedents (ceux sur les ports 80 et 8000),
   avec la commande :

    docker container stop 6d2 e23 (les 2 dernières valeurs sont les id des containers)
    
    ensuite on va créer une nouvelle image car les modification apportée en local sur mon code html n'impactent pas mon image stockée sur mon deamon, pour créer une nouvelle image on utilise la commande :
    
    docker build -t aporignaux11/the_list:3.5.5 . 
    
    (on a changé le tag, concernat la version : le second chiffre indique une update, le premier une update majeur, et le troisième chiffre correspond à une correction de bug, ici on a modifié le 2e pour indiquer une update), après cela il nous suffit de recéer un ou plusieurs container, pour verifier que tout fonctionne nous allons utiliser les les 2 ports precedement utilisées, les ports 8000 et 80. en créer 2 container grace aux commandes: 
 
    docker run -d -p 8000:80 aporignaux11/the_list:3.5.5

    docker run -d -p 80:80 aporignaux11/the_list:3.5.5

    nous les renomerons ensuite site_web_one/two_updated grace à la commande : 
    
    docker container rename [former_name] [new_name]

4 : pour pull les 2 images il suffira d'utiliser les commandes :

    docker push aporignaux11/the_list:3.4.5

    docker push aporignaux11/the_list:3.5.5

    pour pull les immages il faut utiliser les commandes :
     docker pull aporignaux11/the_list:3.4.5
     docker pull aporignaux11/the_list:3.5.5
