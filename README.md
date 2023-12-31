# TP3_CI
## Mise en place pour une application en Python d'une chaine d'intégration continue permettant de valider l'application avant de la packager dans une image de conteneur
Cet exercice permettra de valider vos compétences pour l'activité type 2 Déployer en continu une applicaton dans le cadre du titre RNCP Administrateur Devops.

### Description des fichiers 
Nous disposons ici: 

* d'un dossier **app** dans lequel on retrouve l'ensemble des programmes de l'application Python à tester. 

* d'un dossier **docker-app/python** dans lequel on retrouve le dockerfile nécessaire à la construction d'une image afin de pouvoir déployer l'application dans un conteneur. 

* d'un dossier **.github/workflows** contenant le fichier de pipeline au format yml. Ce fichier de pipeline contient une succession d'étapes automatisées de traitement de données permettant de tester l'application python.

### Pré requis 
-> Disposer de Git  
-> Disposer d'un compte sur un outil d'orchestration continue tel que Jenkins, Gitlab CI, Github Actions...) Dans le cadre de cet exercice j'ai utlisé Github Actions    
-> Disposer d'un compte sur le Hub Docker  

### Schéma de présentation des étapes du pipeline 
Le pipeline de ce TP permet de lancer une suite de tâches de manières automatisées, dans l'ordre:  
1. repot-clone: *récupération du code source dans un dépôt git*
2. pylint-test: *vérification des normes de codage*  
3. unittest-test: *test des modules individuels*  
4. robot-test: *automatisation de test*
5. radon-raw-test: *analyse de la complexité cyclomatique*
6. radon-cc-test *vérification des copier/coller dans le code*

Lors de l'exécution des jobs de chaque actions une visualisation succinte et détaillé est disponible dans Github Actions.  

Lorsque les tests sont validés, l'image docker est construite et pousser sur le docker hub.  

![CI](https://github.com/AZARZARSoukaina/TP3_CI/assets/105217130/6b15bc63-76e5-49a4-8562-f528d3696408)

### Configuration des paramètres du pipeline
1. Créer un nouveau répertoire sur Github dans lequel cloner ce répertoire
qui contient un fichier de pipeline permettant de récupérer le code source
d'une petite application python  
`https://github.com/AZARZARSoukaina/TP3_CI.git`

3. Créer un nouveau répertoire dans le Hubdocker puis créer un token   
en allant dans ***"Account settings"*** puis ***"Security"*** puis ***"New acces token"***   
-> Copier/coller le token quelque part, vous en aurez besoin prochainement   

4. Dans le répertoire Github déclarer les variables en allant dans ***"settings"*** puis ***"security"*** puis ***"secrets and variables"***
   
- Dans l'onglet **Secrets**, cliquer sur ***"New repository secret"*** nommer la première variable secrète `"DOCKER_TOKEN"` et associez lui le token crée à l'étape précédente   
Faites de même pour la variable `DOCKER_USER` à laquelle vous lui associez le nom de votre pseudo dans le hubdocker     

- Dans l'onglet **Variables** cliquez sur ***"New repository variable"*** et déclarer les variables suivantes en leur associant respectivement leurs valeurs:   

`DOCKER_REPO` : nom du repot créer sur le hub docker  
`IMAGE_FILE` : chemin du dockerfile de l'app soit docker-app/python/Dockerfile  
`IMAGE_OS` : ubuntu-latest  
`ROBOT_FILE_NAME`: nom du fichier robotframework soit machine.robot  
`ROBOT_FILE_WAY`: chemin du fichier robotframework soit ./app/test/system  
`DOCKER_IMAGE_VERSION`: version de l'iamge de l'application (à vous de la définir)  
`UNITTEST_FILE`: chemin du fichier unittest soit test/unit/test.py 

Une fois votre code pousser dans le répertoire github, aller dans l'onglet **Actions** et attendre la fin du déploiement (jusqu'à ce que tous les voyants soient verts)

![tp3pic](https://github.com/AZARZARSoukaina/TP3_CI/assets/105217130/07526a54-b541-4441-8151-508f3e9622ac)
