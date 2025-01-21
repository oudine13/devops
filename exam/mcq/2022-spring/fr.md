
# DevOps avec SRE QCM

## Partie 1. Questions sur l'exécution des commandes

### Question 1

Vous venez de modifier le fichier `README.md` dans votre dépôt Git local. Quelle(s) séquence(s) de commande(s) pousse(nt) les changements vers un dépôt distant ?

* [ ] A:
  ```bash
  git commit -m “some change”
  git push
  ```
* [ ] B:
  ```bash
  git add README.md
  git commit -m “some change”
  git push origin
  ```
* [ ] C:
  ```bash
  git push
  ```
* [ ] D:
  ```bash
  git add .
  git commit -m “some change”
  git push
  ```

### Question 2

Quelle(s) commande(s) se positionne(nt) sur la branche `master` ?

* [ ] A: `git checkout -f master`
* [ ] B: `git checkout`
* [ ] C: `git master`
* [ ] D: `git checkout master`

### Question 3

Quelle(s) commande(s) liste(nt) uniquement les conteneurs en cours d'exécution ?

* [ ] A: `docker ps` 
* [ ] B: `docker container ls`
* [ ] C: `docker container ls -a`
* [ ] D: `docker ps -a`

### Question 4

Quelle(s) commande(s) télécharge(nt) une image depuis un registre Docker si elle n'existe pas sur l'hôte actuel (où `$IMAGE` est un nom d'image).

* [ ] A: `docker load $IMAGE`
* [ ] B: `docker run $IMAGE`
* [ ] C: `docker pull $IMAGE`
* [ ] D: `docker image pull $IMAGE`

### Question 5

Considérant le fichier `Dockerfile` suivant :

```dockerfile
FROM node:12
WORKDIR /usr/src/app
COPY package.json .
RUN npm install
COPY . .
EXPOSE 4000
CMD [ "npm", "start" ]
```

Quelle(s) commande(s) exécute(nt) une application web accessible sur `http://localhost:8000` depuis l'hôte sur lequel ce conteneur est exécuté (où "myapp" est une image construite à l'aide de ce `Dockerfile`) ?

* [ ] A: `docker run -p 8000:4000 myapp`
* [ ] B: `docker run -p 4000:8000 myapp`
* [ ] C: `docker run myapp`
* [ ] D: `docker run myapp:latest`

### Question 6

Quelle(s) commande(s) répertorie(nt) les pods Kubernetes ?

* [ ] A: `kubectl ls pods`
* [ ] B: `kubectl get pods`
* [ ] C: `kubelet ls pods`
* [ ] D: `kubelet get pods`

### Question 7

Quelle(s) commande(s) répertorie(nt) les déploiements Kubernetes ?

* [ ] A: `kubectl ls deployments`
* [ ] B: `kubectl get deployments`
* [ ] C: `kubelet ls deployments`
* [ ] D: `kubelet get deployments`

### Question 8

Vous disposez du fichier `deployment.yaml` de configuration Kubernetes suivant :

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: webapp1
spec:
  replicas: 3
  selector:
    matchLabels:
      app: webapp1
  template:
    metadata:
      labels:
        app: webapp1
    spec:
      containers:
      - name: webapp1
        image: katacoda/docker-http-server:latest
```

Que va-t-il se passer en appliquant cette configuration ?

* [ ] A : Créer un déploiement et des pods
* [ ] B : Créer seulement un déploiement sans créer de pods
* [ ] C : Tirer une image du registre Docker vers le nœud de travail du cluster Kubernetes
* [ ] D : Exécuter 3 conteneurs en utilisant l'image `katacoda/docker-http-server:latest`.

### Question 9

Quelle(s) commande(s) permet(tent) d'exécuter une commande à l'intérieur d'un conteneur en cours d'exécution ?

* [ ] A: `docker exec ...`
* [ ] B: `docker run ...`
* [ ] C: `docker start ...`
* [ ] D: `docker create ...`

### Question 10

Vous avez le fichier `docker-compose.yml` suivant :

```yaml
version: '2.0'
services:
  web:
    build: .
    ports:
    - "5000:5000"
    volumes:
    - logvolume01:/var/log
    links:
    - redis
  redis:
    image: redis
volumes:
  logvolume01: {}
```

Que fera la commande `docker-compose up` ?

* [ ] A: Build 1 image and pull 1 image
* [ ] B: Run 2 containers
* [ ] C: Pull 2 images
* [ ] D: Persist Redis data on the host

## Partie 2. Questions sur la connaissance de la théorie

### Question 11

Laquelle ou lesquelles des affirmations suivantes concernant DevOps est/sont correcte(s) ?

* [ ] A : DevOps ne convient qu'aux logiciels avec une architecture microservices
* [ ] B : DevOps est juste un ensemble d'outils
* [ ] C : DevOps réunit les équipes de développement et d'exploitation
* [ ] D : DevOps est mis en œuvre dans SRE (Site Reliability Engineering)

### Question 12

Quel ordre d'action est correct pour le développement piloté par les tests ?

* [ ] A :
  ```
  1. Refactoriser
  2. Ecrire un scénario de test
  3. Écrire le code fonctionnel
  ```
* [ ] B :
  ```
  1. Ecrire un scénario de test
  2. Ecrire le code fonctionnel
  3. Refactoriser 
  ```
* [ ] C : 
  ```
  1. Ecrire le code fonctionnel
  2. Ecrire un scénario de test
  3. Refactoriser
  ```

### Question 13

Quel(s) est (sont) le(s) principe(s) du Manifeste Agile ?

* [ ] A : Créer une culture d'apprentissage continu et dynamique.
* [ ] B : Le logiciel fonctionnel est la principale mesure du progrès.
* [ ] C : Livrer des logiciels fonctionnels fréquemment, de quelques semaines à quelques mois.
* [ ] D : La priorité absolue est de satisfaire le client en livrant rapidement et en permanence des logiciels de qualité.

### Question 14

Quelle(s) fonctionnalité(s) l'Orchestration de conteneurs fournit-elle ?

* [ ] A : Équilibrage de charge et routage du trafic
* [ ] B : Gestion d'une infrastructure informatique à l'aide de fichiers de configuration
* [ ] C : Surveillance de la santé des conteneurs
* [ ] D : Redémarrer les conteneurs cassés

### Question 15

Quel type de test simule le scénario réel de l'utilisateur qui est généralement difficile à automatiser ?

* [ ] A : Tests unitaires
* [ ] B : Tests d'intégration
* [ ] C : Tests fonctionnels
* [ ] D : Tests end-to-end

### Question 16

Quel type de test est proche du code source de votre application et s'exécute dans un environnement très contrôlé ?

* [ ] A : Tests unitaires
* [ ] B : Tests d'intégration
* [ ] C : Tests fonctionnels
* [ ] D : Tests end-to-end

### Question 17

Quelle(s) affirmation(s) concernant le Continuous Integration (CI) est (sont) correcte(s) ?

* [ ] A : Il s'agit d'une pratique consistant à fusionner fréquemment de petits changements de code.
* [ ] B : Il s'agit d'une pratique consistant à fusionner un changement important à la fin d'un cycle de développement.
* [ ] C : Il permet de construire des logiciels plus sains en développant et en testant par petits incréments
* [ ] D : Il construit des logiciels plus sains en les développant et en les testant par incréments plus importants.

### Question 18

Quelle(s) affirmation(s) concernant le Continuous Delivery (CD) est (sont) correcte(s) ?

* [ ] A : Il s'agit d'une discipline de développement logiciel dans laquelle les logiciels sont construits d'une manière qui permet de les déployer vers les clients à tout moment.
* [ ] B : Il s'agit d'une extension du Continuous Integration (CI) afin de s'assurer que vous pouvez diffuser rapidement de nouvelles modifications à vos clients de manière durable.
* [ ] C : Il étend le déploiement continu pour mettre en production les nouvelles modifications après qu'elles aient passé les tests automatisés.
* [ ] D : Il rend les déploiements de logiciels indolores

### Question 19

Quel(s) objet(s) n'existe(nt) pas dans Docker ?

* [ ] A: Data volumes
* [ ] B: Containers
* [ ] C: Users
* [ ] D: Images

### Question 20

Qu'est-ce qui peut être automatisé en appliquant des outils Infrastructure as Code (IaC) comme Ansible ?

* [ ] A : Processus de révision du code
* [ ] B : Provisionnement du cloud
* [ ] C : Gestion de la configuration de l'infrastructure
* [ ] D : Déploiement d'applications
