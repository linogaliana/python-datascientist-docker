# Image docker pour le cours "Python pour data-scientists et économistes" :snake:
[![build-doc Actions Status](https://github.com/linogaliana/python-datascientist-docker/actions/workflows/prod.yml/badge.svg)](https://github.com/linogaliana/python-datascientist-docker/actions)
[![Docker Pulls](https://img.shields.io/docker/pulls/linogaliana/python-datascientist)](https://hub.docker.com/repository/docker/linogaliana/python-datascientist/general)

Ce dépôt Github stocke les images `Docker` 🐳 nécessaire pour construire le site
<https://linogaliana-teaching.netlify.app/> ou pour répliquer les exemples. 
Le dépôt des codes sources du site est disponible sur
[Github](https://github.com/linogaliana/python-datascientist)

# Environnements disponibles

Ce dépôt présente deux environnements de développement intégrés à un environnement `conda` complet pour pouvoir répliquer l'ensemble des codes du site web :

* Une image `visualstudio` [python-datascientist-vstudio](https://hub.docker.com/repository/docker/linogaliana/python-datascientist-vstudio). Cette dernière est 
utilisable sur le `SSP Cloud` en cliquant sur le bouton ci-dessous [![Onyxia](https://img.shields.io/badge/SSPcloud-Tester%20via%20SSP--cloud-informational&color=yellow?logo=Python)](https://datalab.sspcloud.fr/launcher/inseefrlab-helm-charts-datascience/vscode?onyxia.friendlyName=%C2%ABpython-ENSAE%C2%BB&security.whitelist.enable=false&service.image.custom.enabled=true&service.image.custom.version=%C2%ABlinogaliana%2Fpython-datascientist-vstudio%C2%BB&resources.requests.memory=%C2%AB8Gi%C2%BB)
* Une image `rstudio` proposant l'ensemble de l'écosystème `R Markdown` et `reticulate` pour faire l'interface entre l'environnement `conda` du cours et `R`. Cette image sert d'environnement de construction du site *web*

L'environnement `conda` nécessaire pour faire tourner l'ensemble du
cours est disponible dans le fichier [environment.yml](environment.yml). 
Il est recommandé d'utiliser la `conda-forge` afin de bénéficier de versions
récentes des packages. 


# Déploiement du site

Le site est construit de manière automatique grâce à [Hugo](https://gohugo.io/)
à partir d'un environnement conteneurisée [Docker](https://hub.docker.com/repository/docker/linogaliana/python-datascientist/general) 
La reproductibilité des exemples et des exercices est testée avec 
Github Actions ([![build-doc Actions Status](https://github.com/InseeFrLab/utilitR/workflows/Docker%20Build%20and%20Website%20Deploy/badge.svg)](https://github.com/linogaliana/python-datascientist/actions)).


## Tester les codes Python

Il est possible d'utiliser une installation personnelle de `Python` ou 
des serveurs partagés: 

* Binder ([![Binder](https://mybinder.org/badge_logo.svg)](https://mybinder.org/v2/gh/linogaliana/python-datascientist/master)
)
* Google colab ([![Open In Colab](https://colab.research.google.com/assets/colab-badge.svg)](http://colab.research.google.com/github/linogaliana/python-datascientist/blob/pandas_intro/static/notebooks/numpy.ipynb))
* SSPCloud Datalab ([![Onyxia](https://img.shields.io/badge/SSPcloud-Tester%20via%20SSP--cloud-informational&color=yellow?logo=Python)](https://datalab.sspcloud.fr/launcher/inseefrlab-helm-charts-datascience/vscode?onyxia.friendlyName=%C2%ABpython-ENSAE%C2%BB&security.whitelist.enable=false&service.image.custom.enabled=true&service.image.custom.version=%C2%ABlinogaliana%2Fpython-datascientist-vstudio%C2%BB&resources.requests.memory=%C2%AB8Gi%C2%BB) pour les élèves de l'ENSAE et
les agents du système statistique public

## Utilisation de l'image Docker [![Docker Pulls](https://img.shields.io/docker/pulls/linogaliana/python-datascientist)](https://hub.docker.com/repository/docker/linogaliana/python-datascientist/general)

Pour améliorer la reproductibilité des exemples, plusieurs images `Docker` sont
automatiquement construites et mises à disposition depuis 
[DockerHub](https://hub.docker.com/repository/docker/linogaliana/python-datascientist).

Pour le moment, l'utilisation de `Python` se fait à travers `Rstudio` (via
le package `reticulate`) ou à travers `Visual Studio`.
Des versions futures amélioreront la compatibilité
avec les notebooks `Jupyter`. 

### Utiliser en local l'image Visual Studio

```shell
docker pull linogaliana/python-datascientist-vstudio
docker run --rm -p 8787:8787 -e PASSWORD=test linogaliana/python-datascientist-vstudio
```


### Utiliser en local l'image RStudio

Cette image peut être déployée en local, de la manière suivante:

```shell
docker pull linogaliana/python-datascientist
docker run --rm -p 8787:8787 -e PASSWORD=test linogaliana/python-datascientist
```

Elle peut également être appelée depuis un *pipeline* d'intégration continue
`Github` ou `Gitlab` puisque l'image se trouve sur `DockerHub`.



### Github Actions

```
container: linogaliana/python-datascientist:latest
```

### Gitlab CI

```
image: linogaliana/python-datascientist:latest
```
