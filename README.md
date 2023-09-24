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
4. robot-test: **
5. radon-raw-test: *analyse de la complexité cyclomatique*
6. radon-cc-test *vérification des copier/coller dans le code*

Lors de l'exécution des jobs de chaque actions une visualisation succinte et détaillé est disponible dans Github Actions.  

Lorsque les tests sont validés, l'image docker est construite et pousser sur le docker hub.  

![CI](https://github.com/AZARZARSoukaina/TP3_CI/assets/105217130/6b15bc63-76e5-49a4-8562-f528d3696408)



### Configuration des paramètres du pipeline


