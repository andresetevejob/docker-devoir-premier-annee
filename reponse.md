# ma première étape a été de créer un fichier dockerfile et d'y ajouter le code suivant


FROM ubuntu

RUN apt-get update

RUN apt-get install nginx -y

COPY . /var/www/html/

EXPOSE 80

CMD ["nginx","-g","daemon off;"]

# ensuite j'ai créé une image docker avec le code : docker build -t rmpnr/sitewebbb:1.0

# j'ai lancé deux container sur les ports 80 et 8000 et je les ai renommé avec les codes suivants :

docker run -d -p 80:80 rmpnr/sitewebbb:1.0
docker run -d -p 8000:80 rmpnr/sitewebbb:1.0
docker rename nom_aléatoire site_web_one
docker rename nom_aléatoire site_web_two

# j'ai stoppé les deux container en allant directement sur docker et en appuyant sur le stop mais j'aurai pu utiliser "docker container stop ..."
# j'ai modifié les codes html et css des sites et je les ai remit en ligne avec les codes suivants :
docker build -t rmpnr/sitewebbb:1.2
docker run -d -p 80:80 rmpnr/sitewebbb:1.2
docker run -d -p 8000:80 rmpnr/sitewebbb:1.2
# puis je les ai renommé une nouvelle fois
docker rename nom_aléatoire site_one
docker rename nom_aléatoire site_two

# je les ai push  avec la commande 
docker push rmpnr/sitewebbb:1.0
docker push  rmpnr/sitewebbb:1.2

# vous pouvez les pull avec la commande 
docker pull rmpnr/sitewebbb:1.0
docker pull  rmpnr/sitewebbb:1.2
