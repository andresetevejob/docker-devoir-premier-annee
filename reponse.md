# Réponses aux questions README.MD

...

1 - docker build -t nunof083/app-place:1.0.0 .

2 - docker run -d -p 80:80 --name site_web_one nunof083/app-place:1.0.0
    docker run -d -p 8000:80 --name site_web_two nunof083/app-place:1.0.0


3 - Tout d'abord, il faudra faire docker build -t nunof083/app-place:1.0.1 . , cette commande va permettre d'installer une image mais également de faire une nouvelle version, ici c'est la 1.0.1

Apres, il faudra faire la commande docker run -d -p 80:80 nunof083/app-place:1.0.1 (80:80 va permettre de montrer que localhost), si on souhaite ouvrir un autre port, on peut faire docker run -d -p 8000:80 nunof083:app-place:1.0.1 (localhost:8000)
    
Par contre, si on souhaite toujours utiliser les ports 80:80 et 8000:80, faudra soit arrêter la version 1.0.0 avant: 

(docker container ls, reprendre container id et puis faire: docker container stop (container id)

Soit utiliser un autre port comme par exemple 81:80 (si on fait 81:80, ce sera localhost:81, donc il faudra exposer autre que 80 afin de pouvoir faire par ex 81:81 et que ça soit que localhost) et 8001:80, car on ne peut pas avoir 2 ports en activité en même temps.


4 - Pour pousser toutes les versions vers le Docker Hub, j'ai fait:

    docker push nunof083/app-place:1.0.0

    docker push nunof083/app-place:1.0.1

Pour les pull du docker hub:

    docker pull nunof083/app-place:1.0.0
    
    docker pull nunof083/app-place:1.0.1

...
