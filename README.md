# **Projet 7 : Implémentez un modèle de scoring/API**
## <u>Mission</u>
En tant que Data Scientist au sein de l'entreprise "Prêt à dépenser", proposant des crédits à la consommation pour des personnes ayant peu ou pas du tout d'historique de prêt, l'idée est de mettre en oeuvre un outil de "**scoring crédit**" pour calculer la probabilité qu'un client rembourse son crédit, et ainsi, de classifier la demande en crédit *accordé* ou *refusé*. Pour cela, il est nécessaire de développer un algorithme de classification en s'appuyant sur différentes sources de données (comportement, provenant d'institutions financières, ...).
La création d'un **dashboard interactif** est développé pour plus de transparence lors de l'octroi de crédit et pour que les clients aient accès à leurs données personnelles et puissent les explorer plus facilement. 

Pour cela, le modèle de scoring de prédiction est mis en production à l'aide d'une API, puis le dashboard interactif appelle l'API pour les prédictions. 

## <u>Données</U>
Pour mener à bien le projet, différents fichiers .csv contenant les informations nécessaires sont téléchargés [ici](https://www.kaggle.com/c/home-credit-default-risk/data). Les fichiers sont les suivants:
- Fichier HomeCredit_columns_description.csv
- Fichier application_train.csv
- Fichier application_test.csv
- Fichier bureau.csv
- Fichier bureau_balance.csv
- Fichier credit_card_balance.csv 
- Fichier installments_payments.csv
- Fichier POS_CASH_balance.csv
- Fichier previous_application.csv
- Fichier sample_submission.csv

## <u>Description du répertoire</u>
Le répertoire contient d'abord le notebook jupyter de nettoyage et modélisation : `Projet7_nettoyage_modelisation.ipynb`, ainsi que la ``Note_methodologique.pdf`` et d'un fichier `data_processing.py`.

Le dossier "api" est constitué d'un fichier `api.py` FastAPI récupérant le score calculé au préalable dans le fichier `data_processing.py` pour chaque client selon son identifiant et renvoyant stockant les informations client dans un dictionnaire en tant que "réponse".

## <u>Protection des données </u>
Les données traitées provenant du fichier `data_processing.py` sont stockées sur github. Néanmoins, afin de garantir la **protection des données clients** et respecter la conformité du **RGPD** (Règlement Général sur la Protection des données), dans une situation concrète, il serait indispensable de limiter l'accès aux données aux personnes autorisées dans un lieu de stockage conforme au RGPD .

## <u>Lancement de l'API en local</u>
Une fois l'api enregistrée au format .py. Elle est d'abord lancée en local en spécifiant l'hôte et le port dans le code.

Exemple ```: uvicorn.run(app, host="localhost", port=8000)```.

L'api est alors accessible en local à l'adresse précisée.

## <u>Déploiement de l'API sur Heroku</u>
Les fichiers nécessaires à l'application sont stockés sur github. 
Il est également nécessaire de créer un compte Heroku. Les étapes pour la création de l'application api sont les suivantes :
* Dans "dashboard", cliquer sur `New` > `Create new app`
* Donner un nom à l'api
* Préciser la méthode de déploiement (GitHub dans notre cas)
* Connecter à GitHub
* Choisir le déploiement automatique
* Déployer la branche `Deploy Branch`
* Lorsque le déploiement est fait, cliquez sur `Open app` dirigeant directement sur l'url de l'application