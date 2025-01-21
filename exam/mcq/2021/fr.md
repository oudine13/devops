
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

Quelle(s) commande(s) arrête(nt) et ne supprime(nt) pas un conteneur en cours d'exécution (où `$CONTAINER` est un nom de conteneur ou un ID de conteneur) ?

* [ ] A: `docker kill $CONTAINER`
* [ ] B: `docker rmi $CONTAINER`
* [ ] C: `docker stop $CONTAINER`
* [ ] D: `docker rm $CONTAINER`

### Question 5

Quelle(s) commande(s) télécharge(nt) une image depuis un registre Docker si elle n'existe pas sur l'hôte actuel (où `$IMAGE` est un nom d'image).

* [ ] A: `docker load $IMAGE`
* [ ] B: `docker run $IMAGE`
* [ ] C: `docker pull $IMAGE`
* [ ] D: `docker image pull $IMAGE`

### Question 6

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

### Question 7

Quelle(s) commande(s) répertorie(nt) les pods Kubernetes ?

* [ ] A: `kubectl ls pods`
* [ ] B: `kubectl get pods`
* [ ] C: `kubelet ls pods`
* [ ] D: `kubelet get pods`

### Question 8

Quelle(s) commande(s) répertorie(nt) les déploiements Kubernetes ?

* [ ] A: `kubectl ls deployments`
* [ ] B: `kubectl get deployments`
* [ ] C: `kubelet ls deployments`
* [ ] D: `kubelet get deployments`

### Question 9

Quelle(s) commande(s) applique(nt) une(des) configuration(s) dans Kubernetes (où `$FILENAME` est un fichier YAML situé dans votre répertoire actuel) ?

* [ ] A: `kubectl run -f $FILENAME`
* [ ] B: `kubectl -f $FILENAME`
* [ ] C: `kubectl apply -f $FILENAME`
* [ ] D: `kubectl apply -f .`

### Question 10

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

### Question 11

Quelle(s) commande(s) permet(tent) d'exécuter une commande à l'intérieur d'un conteneur en cours d'exécution ?

* [ ] A: `docker exec ...`
* [ ] B: `docker run ...`
* [ ] C: `docker start ...`
* [ ] D: `docker create ...`

### Question 12

Quelle(s) commande(s) démarre(nt) un ou plusieurs conteneurs en utilisant Docker Compose (où `$SERVICE` est un nom de service, configuré dans le fichier `docker-compose.yml`) ?

* [ ] A: `docker compose up`
* [ ] B: `docker-compose up`
* [ ] C: `docker run -c .`
* [ ] D: `docker-compose start $SERVICE`

### Question 13

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
* [ ] D: Persist redis data on the host

### Question 14

Vous disposez du fichier `docker-compose.yml` suivant :

```yaml
version: "3.8"
services:
  nginx:
    build: nginx
    ports:
      - "9000:80"
  redis:
    image: redis
    volumes:
      - /mnt/data:/data
```

Choisissez la ou les options correctes où le service "nginx" est accessible et le service "redis" attache les données :

* [ ] A : Sur la machine hôte : URL - `localhost:80`, dossier - `/mnt/data`
* [ ] B : Sur la machine hôte : URL - `localhost:9000`, dossier - `/data`
* [ ] C : Dans le conteneur : URL - `localhost:80`, dossier - `/data`
* [ ] D : Dans le conteneur : URL - `localhost:9000`, dossier - `/mnt/data`

### Question 15

Vous disposez du fichier manifeste Kubernetes suivant :

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: hello
spec:
  selector:
    matchLabels:
      app: hello
  replicas: 3
  template:
    metadata:
      labels:
        app: hello
    spec:
      containers:
        - name: hello
          image: nginx
          ports:
            - name: http
              containerPort: 80
---
apiVersion: v1
kind: Service
metadata:
  name: hello
spec:
  type: NodePort
  selector:
    app: hello
  ports:
    - port: 80
```

Quelle(s) affirmation(s) est (sont) correcte(s) lors de l'application du fichier manifeste suivant :

* [ ] A : Il crée 1 déploiement, 3 pods et 1 service.
* [ ] B : Le serveur web Nginx n'est pas accessible sur `localhost:80` depuis le cluster Kubernetes.
* [ ] C : Il crée 3 Déploiements, 1 Pod, 1 Service
* [ ] D : Le service "hello" est en état

## Partie 2. Questions sur la connaissance de la théorie

### Question 16

Laquelle ou lesquelles des affirmations suivantes concernant DevOps est/sont correcte(s) ?

* [ ] A : DevOps ne convient qu'aux logiciels avec une architecture microservices
* [ ] B : DevOps est un ensemble d'outils
* [ ] C : DevOps réunit les équipes de développement et d'exploitation
* [ ] D : DevOps est mis en œuvre dans SRE (Site Reliability Engineering)

### Question 17

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

### Question 18

Le Manifeste pour le développement logiciel agile comprend le(s) point(s) suivant(s) :

* [ ] A : Processus et outils plutôt que personnes et interactions
* [ ] B : logiciel fonctionnel plutôt que documentation complète
* [ ] C : La collaboration avec le client plutôt que la négociation de contrats
* [ ] D : Suivre un plan plutôt que réagir au changement

### Question 19

Quel(s) est (sont) le(s) principe(s) du Manifeste Agile ?

* [ ] A : Créer une culture d'apprentissage continu et dynamique.
* [ ] B : Le logiciel fonctionnel est la principale mesure du progrès.
* [ ] C : Livrer des logiciels fonctionnels fréquemment, de quelques semaines à quelques mois.
* [ ] D : La priorité absolue est de satisfaire le client en livrant rapidement et en permanence des logiciels de qualité.

### Question 20

Quelle(s) fonctionnalité(s) l'Orchestration de conteneurs fournit-elle ?

* [ ] A : Équilibrage de charge et routage du trafic
* [ ] B : Gestion d'une infrastructure informatique à l'aide de fichiers de configuration
* [ ] C : Surveillance de la santé des conteneurs
* [ ] D : Maintenir les interactions entre les conteneurs sécurisées ou non

### Question 21
Quel type de test simule le scénario réel de l'utilisateur qui est généralement difficile à automatiser ?

* [ ] A : Tests unitaires
* [ ] B : Tests d'intégration
* [ ] C : Tests fonctionnels
* [ ] D : Tests end-to-end

### Question 22

Quel type de test est proche du code source de votre application et s'exécute dans un environnement très contrôlé ?

* [ ] A : Tests unitaires
* [ ] B : Tests d'intégration
* [ ] C : Tests fonctionnels
* [ ] D : Tests end-to-end

### Question 23

Quelle(s) affirmation(s) concernant le Continuous Integration (CI) est (sont) correcte(s) ?

* [ ] A : Il s'agit d'une pratique consistant à fusionner fréquemment de petits changements de code.
* [ ] B : Il s'agit d'une pratique consistant à fusionner un changement important à la fin d'un cycle de développement.
* [ ] C : Il permet de construire des logiciels plus sains en développant et en testant par petits incréments
* [ ] D : Il construit des logiciels plus sains en les développant et en les testant par incréments plus importants.

### Question 24

Quelle(s) affirmation(s) concernant le Continuous Delivery (CD) est (sont) correcte(s) ?

* [ ] A : Il s'agit d'une discipline de développement logiciel dans laquelle les logiciels sont construits d'une manière qui permet de les déployer vers les clients à tout moment.
* [ ] B : Il s'agit d'une extension du Continuous Integration (CI) afin de s'assurer que vous pouvez diffuser rapidement de nouvelles modifications à vos clients de manière durable.
* [ ] C : Il étend le déploiement continu pour mettre en production les nouvelles modifications après qu'elles aient passé les tests automatisés.
* [ ] D : Il rend les déploiements de logiciels indolores

### Question 25

Quel(s) objet(s) n'existe(nt) pas dans Docker ?

* [ ] A: Data volumes
* [ ] B: Containers
* [ ] C: Users
* [ ] D: Images

### Question 26

Qu'est-ce qui peut être automatisé en appliquant des outils Infrastructure as Code (IaC) comme Ansible ?

* [ ] A : Processus de révision du code
* [ ] B : Provisionnement du cloud
* [ ] C : Gestion de la configuration de l'infrastructure
* [ ] D : Déploiement d'applications

### Question 27

Que fournit le Service Mesh ?

* [ ] A : Connexion entre les services
* [ ] B : Déploiement d'infrastructure
* [ ] C : Observabilité dans les communications de services
* [ ] D : Sécurisation des connexions

### Question 28

Quel(s) est (sont) l'avantage(s) de l'architecture microservice ?

* [ ] A : Chaque module peut être mis à l'échelle de façon indépendante
* [ ] B : Les architectures sont généralement mieux organisées autour des capacités de l'entreprise.
* [ ] C : Le niveau d'agilité plus faible pour les organisations
* [ ] D : Flexibilité dans le choix du langage de programmation

### Question 29

Qu'est-ce qu'Ansible ne fournit PAS ?

* [ ] A : Le provisionnement du cloud
* [ ] B : Gestion de la configuration
* [ ] C : Orchestration de conteneurs
* [ ] D : Déploiement d'applications

### Question 30

Quel(s) type(s) de volume Kubernetes est (sont) le(s) plus approprié(s) à utiliser pour les services sans état ?

* [ ] A: `emptyDir`
* [ ] B: `hostPath`
* [ ] C: `nfs`
* [ ] D: `persistentVolumeClaim`
