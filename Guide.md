
Shell et Jenkins

#!/bin/bash
git clone https://github.com/borelsaffo/alpinehelloworld.git
cd alpinehelloworld 
doker build -t ${IMAGE_NAME}:${IMAGE_TAG} .



https://plugins.jenkins.io/http_request   installer le plugin dans jenkins  pour faire du http

#!/bin/bash
cd alpinehelloworld 
doker build -t ${IMAGE_NAME}:${IMAGE_TAG} .
docker run -d -p 80:5000 -e PORT=5000 --name ${IMAGE_NAME} ${IMAGE_NAME}:${IMAGE_TAG}


#!/bin/bash
curl  http://192.168.56.10  | grep -q "helloworld"
docker stop ${IMAGE_NAME} 
docker rm ${IMAGE_NAME} 

#!/bin/bash
docker stop ${IMAGE_NAME} 
docker rm ${IMAGE_NAME} 



#!/bin/bash
cd alpinehelloworld 
docker build -t 199883/borelsaffo/${IMAGE_NAME}:${IMAGE_TAG} .
docker run -d -p 80:5000 -e PORT=5000 --name ${IMAGE_NAME} 199883/borelsaffo/${IMAGE_NAME}:${IMAGE_TAG}
sleep 5




Le plugin  docker-build-step      plugins gérer artefact

#!/bin/bash
cd alpinehelloworld 
docker build -t 199883/borelsaffo:${IMAGE_NAME}-${IMAGE_TAG} .
docker run -d -p 80:5000 -e PORT=5000 --name ${IMAGE_NAME} 199883/borelsaffo:${IMAGE_NAME}-${IMAGE_TAG}
sleep 5

creer un compte sur https://heroku.com


installer plugins github integration    pour géré la parte webhook afin que le pipeline soit executer a chaque modification de code.


le plugins : role-basedauthorization strategy permet de géré les utilisateurs et donc de leurs associer des role pour definir ce a quoi il ont accès.
Le plugin : docker pipeline très important : 

Bonjour 
s'il te plait peut tu ouvrire un jinkinsfile. 
parlant du plugin '' docker pipeline'' J'ai eu des soucis lorsque j'ai essayer d'exécuter des playbook ansible dans mon jenkinsfile
tel que définit dans le scénario de Dirane, la partie authentification en SSH n est pas tout a fais claire pour moi




https://plugins.jenkins.io/configuration-as-code/
