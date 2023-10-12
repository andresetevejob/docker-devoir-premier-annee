# DEVOIR DOCKER PREMIERE ANNEE

Vous êtes embauché dans une structure de la place.cette dernière décide d’utiliser docker pour le déploiement de son site web.
l'application se trouve dans le dossier : site-web 

Travail à faire

1 - Créer une image docker pour le site web.Le nom de l’image doit contenir votre nom de docker hub, le nom de l’application ainsi que la version.


    docker build -t ilias19sh/imgilias:1.0.0 .


2 - à partir de l’image précédemment créer, démarrer deux conteneurs l’un tournant sur le port 80, et l’autre sur le port 8000,
Les conteneurs devront être accessible respectivement via ces adresses : http://localhost et http://localhost:8000, et ces conteneurs devront être nommés respectivement : site_web_one , site_web_two


    docker run -d -p 80:80 ilias19sh/imgilias:1.0.0
    docker run -d -p 8000:80 ilias19sh/imgilias:1.0.0
    docker rename nom_aléatoire site_web_one
    docker rename nom_aléatoire site_web_two


3 - L’entreprise soit mettre à jour son site web et deployer une nouvelle version. Que devriez vous faire ? Décrivez le processus que vous allez mettre en place ainsi que les différentes commandes.Pour la mise à jour du site web, vous pouvez modifier le texte de la page d’accueil , afin qu’on puisse identifiez la modification à la prochaine connexion au site web.

    docker container stop id_du_container1 
    docker container stop id_du_container2


    docker build -t ilias19sh/imgilias:1.0.1 .


    docker run -d -p 80:80 ilias19sh/imgilias:1.0.1
    docker run -d -p 8000:80 ilias19sh/imgilias:1.0.1
    docker rename nom_aléatoire site_web_one_1.0.1
    docker rename nom_aléatoire site_web_two_1.0.1

4- Poussez les différentes versions de votre image sur le hub


    docker push ilias19sh/imgilias:1.0.0
    docker push ilias19sh/imgilias:1.0.1

    docker pull ilias19sh/imgilias:1.0.0
    docker pull ilias19sh/imgilias:1.0.1
