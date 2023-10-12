1 - Dans un premier temps je créer une image docker qui contient mon dockerhub name, un nom d'image et une version:
    
    docker build -t neileruaa/firsthomewok:1.0 .

2 - Dans un second temps je run deux containers tournant sur les ports 80 et 8000, et les renomme par la suite au souhait du patron

    docker run -d -p 80:80 neileruaa/firsthomewok:1.0
    docker run -d -p 8000:80 neileruaa/firsthomewok:1.0
    docker rename nom_aléatoire site_web_one
    docker rename nom_aléatoire site_web_two

3 - Maintenant que l'entreprise veut mettre a jour et deployer une nouvelle versions je doit arréter les deux containers précedement créer:

    docker container stop id_du_container1 
    docker container stop id_du_container2

    Puis je créer une nouvelle version de l'image précedente avec les modifications du code html:

    docker build -t neileruaa/firsthomewok:1.1 .

    Je refait désormais l'étape 2 avec la nouvelle version:

    docker run -d -p 80:80 neileruaa/firsthomewok:1.1
    docker run -d -p 8000:80 neileruaa/firsthomewok:1.1
    docker rename nom_aléatoire site_web_one_1.1
    docker rename nom_aléatoire site_web_two_1.1

4 - Je vais maintenant push les deux images précedement créer:

    docker push neileruaa/firsthomewok:1.0
    docker push neileruaa/firsthomewok:1.1

    Et vous pouvez les pull avec ses commandes:

    docker pull neileruaa/firsthomewok:1.0
    docker pull neileruaa/firsthomewok:1.1






    