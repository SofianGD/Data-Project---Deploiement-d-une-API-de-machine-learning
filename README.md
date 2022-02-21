# Data-Project---Deploiement-d-une-API-de-machine-learning

L’API :

Cette API est construite avec FastAPI.
Elle contient trois routes : 
-	/status : Permet de savoir si l’API est fonctionnelle 
-	/M1 : Permet d’obtenir le score du modèle 1 de machine learning
-	/M2 : Permet d’obtenir le score du modèle 2 de machine learning

Les routes /M1 et /M2 sont accessibles avec une authentification des utilisateurs suivants : 

Username	  Password
alice 	    wonderland
bob	        builder
clementine	mandarine



Comment fonctionne l’API ? 


Pour lancer l’API il faut exécuter le programme : train.py

Le fichier train.py est lancé, il calcule les scores des deux modèles de machine learning et les stocks dans un fichier texte « scores_modeles.txt » afin que les scores ne soient calculés qu’une seule et unique fois. 

A la fin du fichier train.py, on lance automatiquement le fichier main.py qui contient l’API FastAPI grâce à la commande :

cmd = 'python3 main.py'
os.system(cmd)

L’API est lancée et les scores sont disponibles.

Ainsi lors de nos différentes requêtes l’API ira chercher et lire les différents scores dans les fichiers textes qui ont été créé par le fichier train.py.

De cette manière les scores sont calculés une seule fois, au lancement de l’API.

De plus si on éteint l’API et qu’on la relance, les fichiers contenants les scores seront écrasé et remplacé par les nouveaux scores calculés.



Les Tests :

Ces tests ont pour but de vérifier le bon fonctionnement des différentes routes avec l’authentification des différents utilisateurs : 

Pour cela j’ai créé deux fichiers python : 
test1.py qui permet de tester le modèle 1 et test2.py qui permet de tester le modèle 2.

Par la suite, j’ai construit un docker-compose qui permet de conteneuriser l’API ainsi que les deux fichiers de tests afin de pouvoir tout tester simultanément.

J’ai rajouté un « sleep 15 » dans les dockerfiles des deux tests permettant aux programmes de tests d’attendre 15 secondes avant de s’exécuter, pour être sûr que l’API soit bien lancée et disponible.

Pour faciliter cela j’ai créé un fichier bash test.sh qui permet d’automatiser la création des différentes images et le lancement du docker-compose.


Kubernetes :

Trois fichiers sont nécessaires au bon déploiement de l’API : 
-	Un fichier de déploiement
-	Un Service
-	Un Ingress 
On choisira de déployer l’API sur 3 Pods.
![image](https://user-images.githubusercontent.com/95073322/154958341-74ddab0a-b66c-44d1-b203-805e63fa4395.png)



