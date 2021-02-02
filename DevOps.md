#DevOps

---
Etape   : lancer docker
	: sudo docker pull "image"
	: creer un dockerfile, le configurer
	: build le dockerfile, sudo docker build....
	: lancer le conteneur , sudo docker run .....
----

---- Commandes docker utiles
sudo docker images		// listes les images
sudo docker ps 		// liste tout les conteneurs actuels
sudo docker ps -a 		// liste tout les conteneurs 
sudo docker stop id/name 
sudo docker rm id/name
sudo docker rm -f name  	//
sudo docker port conteneur 	// liste les ports utilisés
sudo docker stats
sudo docker inspect
sudo docker logs
docker network create my-net
sudo docker-compose up --build  // build et lance docker compose (docker-compose.yml)


----

---- RUN
Argument cmmd : sudo docker run [arg] [nomUser/nomImage]
-it 				// -IT garde la session ouverte, exit pour quitter
-p xxxx:xxxx			// mappage port local:conteneur
-P 				// mappe aléatoirement tout les ports du conteneur 
-d 				// detached mode, detache le conteneur du terminal
--link xxxxx			// connecte deux conteneurs entre eux
--volume /home/enagnon/Bureau/test2:/var/lib/postgresql/data
--name nomConteneur
----
dockerfile // fichier de config du conteneur cmmd shell/python

docker hub: 
soekip
enagnon-farell...@cpe.fr
dallez94123

docker build -t nomUser/nomImage .  // bien mettre le point

docker run -p 8888:5000 --name nomConteneur nomUser/nomImage
docker pull adminer
docker pull openjdk
docker run --link DBname -p 8080:8080 adminer

copy local destination
	sudo docker run -p portMachine:portConteneur --name nomConteneur nomUser/nomImage
	
	 .sudo docker run -p 5432:5432 --name postgres soekip/postgres
	sudo docker run --link postgres:db -p 8080:8080  --name adm adminer
Lancer avec un volume :
	sudo docker run -p 5432:5432 --volume /home/enagnon/Bureau/test2:/var/lib/postgresql/data --name postgres soekip/postgres

---- dockerfiles
COPY docker-entrypoint-initdb.d/*.sql /docker-entrypoint-initdb.d/

# lors du run, les scripts sql dans le dossier init sont éxécutés ssi la bdd est vide


--------------------------------

Why should we run the container with a flag -e to give the environment variables ?
	Ce n'est pas très prudent de définir le mot de passe directement dans le Dockerfile, il vaut mieux utiliser le parametre -e pour acceder à la variable d'environnement correspondant au mot de passe
	
	
Why do we need a volume to be attached to our postgres container ?
	Pour ne pas perdre les données lors de la suppression du conteneur (bdd)
	
	
Why do we need a multistage build ?
	Cela permet d'automatiser le processus de deploiement, en laisant docker compiler le programme java plutot que de le faire manuellement
	

Why do we need a reverse proxy ? 
	Un reverse proxy sert à avoir un tampon entre les serveurs internes et interne. Cela permet egalement d'acceder au backend depuis internet



------

