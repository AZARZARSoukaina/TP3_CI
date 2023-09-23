# TP3_CI
## Mise en place pour une application en Python d'une chaine d'intégration continue permettant de valider l'application avant de la packager dans une image de conteneur
Cet exercice permettra de valider vos compétences pour l'activité type 2 Déployer en continu une applicaton dans le cadre du titre RNCP Administrateur Devops.

### Description des fichiers 
Nous disposons ici: 

* d'un dossier **app** dans lequel on retrouve l'ensemble des programmes del'application Python à tester. 

* d'un dossier **docker-app/python** dans lequel on retouve le dockerfile nécessaire à la construction d'une image afin de pouvoir déployer l'application dans un conteneur. 

* d'un dossier **.github/workflows** contenant le fichier de pipeline au format yml. Ce fichier de pipeline contient une succession d'étapes automatisées de traitement de données permettant de tester l'application python. Cf Schéma de présentation des étapes du pipeline. 

### Pré requis 
-> Disposer de Git  
-> Disposer d'un compte sur un outil d'orchestration continue tel que Jenkins, Gitlab CI, Github Actions...) Dans le cadre de cet exercice j'ai utlisé Github Actions    
-> Disposer d'un compte sur le Hub Docker  

### Schéma de présentation des étapes du pipeline 

### Configuration des paramètres du pipeline


