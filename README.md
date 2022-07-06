# Image docker pour le cours "Python pour data-scientists et économistes" :snake:
[![build-doc Actions Status](https://github.com/linogaliana/python-datascientist-docker/actions/workflows/prod.yml/badge.svg)](https://github.com/linogaliana/python-datascientist-docker/actions)
[![Docker Pulls](https://img.shields.io/docker/pulls/linogaliana/python-datascientist)](https://hub.docker.com/repository/docker/linogaliana/python-datascientist/general)

Ce dépôt Github stocke les images `Docker` 🐳 nécessaire pour construire le site
<https://linogaliana-teaching.netlify.app/> ou pour répliquer les exemples. 
Le dépôt des codes sources du site est disponible sur
[Github](https://github.com/linogaliana/python-datascientist)

# Environnements disponibles

Ce dépôt présente un environnement de développement intégrés à un environnement `conda` complet pour pouvoir répliquer l'ensemble des codes du site web.


L'environnement `conda` nécessaire pour faire tourner l'ensemble du
cours est disponible dans le fichier [environment.yml](environment.yml). 
Il est recommandé d'utiliser la `conda-forge` afin de bénéficier de versions
récentes des packages. 


# Déploiement du site

Le site est construit de manière automatique grâce à [Hugo](https://gohugo.io/)
à partir d'un environnement conteneurisée [Docker](https://hub.docker.com/repository/docker/linogaliana/python-datascientist/general) 
La reproductibilité des exemples et des exercices est testée avec 
Github Actions ([![build-doc Actions Status](https://github.com/InseeFrLab/utilitR/workflows/Docker%20Build%20and%20Website%20Deploy/badge.svg)](https://github.com/linogaliana/python-datascientist/actions)).



### Utiliser en local l'image Visual Studio

```shell
docker pull linogaliana/python-datascientist-vstudio
docker run --rm -p 8787:8787 -e PASSWORD=test linogaliana/python-datascientist-vstudio
```


### Github Actions

```
container: linogaliana/python-datascientist:latest
```

### Gitlab CI

```
image: linogaliana/python-datascientist:latest
```
