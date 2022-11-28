
Shell et Jenkins- \
Premier Job via UI Jenkins \

#!/bin/bash \
git clone https://github.com/borelsaffo/alpinehelloworld.git \
cd alpinehelloworld  \
doker build -t ${IMAGE_NAME}:${IMAGE_TAG} . 

![image](https://user-images.githubusercontent.com/27947973/204240822-19fd57e3-ccb1-453f-9e2d-a4507d618032.png)
![image](https://user-images.githubusercontent.com/27947973/204242225-559ec930-4ae1-4c86-a3b4-e4ea730438e6.png)
![image](https://user-images.githubusercontent.com/27947973/204242284-032cb514-f7ed-47c7-b679-fdba008f6ecd.png)
![image](https://user-images.githubusercontent.com/27947973/204242448-1816b3ce-dcef-460d-bff5-3a36f16d2641.png)
le job recupère un projet sur Github et cree une image docker
![image](https://user-images.githubusercontent.com/27947973/204242613-4d1c7ff5-64f1-4456-bf07-bfa2db70beb5.png)
comme action a la fin du build: ici on suprime le working directory.
l'image builder, contruite peut etre publier dans un registry distant ou local.
![image](https://user-images.githubusercontent.com/27947973/204243627-3742d2a2-29d4-4c50-ac17-690815cac0d7.png)

resultat build

![image](https://user-images.githubusercontent.com/27947973/204245481-d5339aee-970e-45d4-815d-7f511975fc38.png)
![image](https://user-images.githubusercontent.com/27947973/204245413-c3421c8b-b6f9-401e-8804-a589bf50d366.png)

NB : sachant bien que Jenkins est un outil de CI, pour builder un projet, cela est fait par defaut dans un repertoire
si vous créer un job ou un projet que vous appelez : Build, un dossier build sera créer dans le repertoire de travail de l'outil Jenkins
Le répertoire de travail (/var/jenkins_home/workspace/build). Vous pouvez par exemple lors de la construction de votre job demandé a Jinkins de suprimer le remertoire de travail a la fin de l'exécution du job. ainsi à chaque fois que le job sera exécuté, jenkins se chargera également de suprimé le dossier du job
a la fin de l'exécution du job.


![image](https://user-images.githubusercontent.com/27947973/204245976-9af49a50-c697-4876-b6ec-8dd7e2d949d9.png)






Dans le job ci-dessous, après le build, on a une image docker, on contruit un container avec l'image builder
comme il s'agit d'une application web qu'on a packager dans une image Docker, on peut installer le pluging jenkin :"http_request' pour faire des tests.
https://plugins.jenkins.io/http_request   installer un pluging dans jenkins  pour faire du http

Deuxième job via UI Jenkins

#!/bin/bash \
cd alpinehelloworld \ 
doker build -t ${IMAGE_NAME}:${IMAGE_TAG} . \
docker run -d -p 80:5000 -e PORT=5000 --name ${IMAGE_NAME} ${IMAGE_NAME}:${IMAGE_TAG}


#!/bin/bash   \
curl  http://192.168.56.10  | grep -q "helloworld" \
docker stop ${IMAGE_NAME}  \
docker rm ${IMAGE_NAME} 

#!/bin/bash \
docker stop ${IMAGE_NAME}  \
docker rm ${IMAGE_NAME}  \



#!/bin/bash \
cd alpinehelloworld  \
docker build -t 199883/borelsaffo/${IMAGE_NAME}:${IMAGE_TAG} . \
docker run -d -p 80:5000 -e PORT=5000 --name ${IMAGE_NAME} 199883/borelsaffo/${IMAGE_NAME}:${IMAGE_TAG} \
sleep 5




Le plugin  docker-build-step      plugins gérer artefact

#!/bin/bash  \
cd alpinehelloworld  \
docker build -t 199883/borelsaffo:${IMAGE_NAME}-${IMAGE_TAG} .- \
docker run -d -p 80:5000 -e PORT=5000 --name ${IMAGE_NAME} 199883/borelsaffo:${IMAGE_NAME}-${IMAGE_TAG} \
sleep 5


====== Creer un compte sur https://heroku.com   pour la partie run ou déploy


installer plugins "github integration"    pour géré la parte webhook afin que le pipeline soit executer a chaque modification de code présent dans Github.
Ici le scénario est telle que le code source du projet soit situé dans un repo Github.


le plugins : "role-basedauthorization strategy"  permet de géré les utilisateurs et donc de leurs associer des role pour definir ce a quoi il ont accès.


Le plugin : "docker pipeline" très important : 

Bonjour 
s'il te plait peut tu ouvrire un jinkinsfile. 
parlant du plugin '' docker pipeline'' J'ai eu des soucis lorsque j'ai essayer d'exécuter des playbook ansible dans mon jenkinsfile
tel que définit dans le scénario de X, la partie authentification en SSH n'est pas tout a fais claire pour moi.

solution:    https://plugins.jenkins.io/configuration-as-code/
