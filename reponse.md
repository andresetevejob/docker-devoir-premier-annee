1 - Créer une image docker pour le site web.Le nom de l’image doit contenir votre nom de docker hub, le nom de l’application ainsi que la version.

Réponse : Tout simplement on se place dans le dossier correspondant à notre site web par exemple, et on crée une image grace à la commande docker build -t gekikho/next-u-streaming:1.0.0 .

2 - à partir de l’image précédemment créer, démarrer deux conteneurs l’un tournant sur le port 80, et l’autre sur le port 8000,
Les conteneurs devront être accessible respectivement via ces adresses : http://localhost et http://localhost:8000, et ces conteneurs devront être nommés respectivement : site_web_one , site_web_two

Réponse : Pour faire cela, on va effectuer la commande :
docker run -d --name site_web_one -p 80:80 gekikho/next-u-streaming:1.0.0
docker run -d --name site_web_two -p 8000:8000 gekikho/next-u-streaming:1.0.0
Donc on a lancé deux containers qu'on a nommé, on leur a assigné chacun le port 80:80 et 8000:80, puis on leur a assigné l'image.

3 - L’entreprise soit mettre à jour son site web et deployer une nouvelle version. Que devriez vous faire ? Décrivez le processus que vous allez mettre en place ainsi que les différentes commandes.Pour la mise à jour du site web, vous pouvez modifier le texte de la page d’accueil , afin qu’on puisse identifiez la modification à la prochaine connexion au site web.

Réponse : Je modifie mon code, une fois que tout est bon, je crée une nouvelle image qui correspondra à la version 1.0.1 de mon site grâce à la commande : docker build -t gekikho/next-u-streaming:1.0.1 .
Ensuite je peux run un container en utilisant cette image, container qu'on va appeler site_web_three et mettre sur le port 30:80(localhost:30).

4- Poussez les différentes versions de votre image sur le hub
doc

Réponse : docker push gekikho/next-u-streaming:1.0.0
docker push gekikho/next-u-streaming:1.0.1
Et voilà les deux images sont push sur le dockerhub

NB : pour chacune des questions vous devez rajouter les commandes dans fichier .md appelé réponse qui se trouvera sur votre branche

Pour la question 4, vous devez en plus me donner les commandes pour je puisse pull vos images

docker pull gekikho/next-u-streaming:1.0.0
docker push gekikho/next-u-streaming:1.0.1
