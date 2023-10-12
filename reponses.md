1- Tout d'abord il faut crée une image avec la commande : docker build -t komanboni/app-mugiwara:1.0.0 .
2- Pour démarrer deux contener avec des ports différent on utilise la commande :
pour le premier : docker run -d -p 80:80 --name site_web_one komanboni/app-mugiwara:1.0.0  pour notre premier site web il es bien sur le port 80
pour le deuxième : docker run -d -p 8000:80 --name site_web_one komanboni/app-mugiwara:1.0.0  pour le deuxième qui es bien sur le port 8000

3- Dans un premier temps nous faisaons une mise a jour de cette image donc docker build -t komanboni/app-mugiwara:2.0.0 . l'image a bien été mise a jour
Ensuite comme vue dans le cours il faudra arrêter les deux précédents contener donc en faisant : docker stop site_web_one et two
mais aussi il faudra faire un docker rm  site_web_one et two.
Puis nous finiront donc par lancer ces deuw contener avec la mise a jour de leurs nouvelles versions donc :
docker run -d -p 80:80 --name site_web_one komanboni/app-mugiwara:2.0.0 
docker run -d -p 8000:80 --name site_web_two komanboni/app-mugiwara:2.0.0.

4- Pour push l'image on fais : docker push komanboni/app-mugiwara:1.0.0  et docker push komanboni/app-mugiwara:2.0.0

et pour que vous puissez pull vous devrez faire docker pull komanboni/app-mugiwara:1.0.0 et docker pull komanboni/app-mugiwara:2.0.0 