# DevOps with SRE MCQ

## Part 1: Questions on Command Execution

### Question 1

Vous venez de modifier le fichier README.md dans votre dépôt Git local. Quelle(s) séquence(s) de commandes poussent les changements vers un dépôt distant ? (plusieurs réponses)

- [ ] A:
  
```bash
  git commit -m “some change”
  git push
```

- [ ] B:

```bash
  git add README.md
  git commit -m “some change”
  git push origin
```

- [ ] C:

```bash
  git push
```

- [ ] D:

```bash
  git add .
  git commit -m “some change”
  git push
```

### Question 2

Quelle commande(s) Git est(sont) utilisée(s) pour créer une nouvelle branche ? (plusieurs réponses)

- [ ] A:

```bash
git clone
```

- [ ] B:

```bash
git branch
```

- [ ] C:

```bash
git checkout
```

- [ ] D:

```bash
git checkout -b
```

### Question 3

Vous disposez d'un serveur avec un endpoint /health qui renvoie `SERVER OK` lorsque le service est sain. Vous effectuez un contrôle de santé sur votre serveur avec le playbook Ansible suivant :

```yaml
- name: Check Server health
uri:
url: http://127.0.0.1/-/health
return_content: yes
register: server_health
```

Comment afficheriez-vous uniquement la réponse `SERVER OK` dans le terminal, si le serveur est sain ? (1 réponse)

- [ ] A:

```yaml
- name: Print Server health
  debug:
  msg: "SERVER OK"
```

- [ ] B:

```yaml
- name: Print Server health
  debug:
  msg: server_health
```

- [ ] C:

```yaml
- name: Print Server health
  debug:
  msg: "{{ server_health.content }}"
```

- [ ] D:

```yaml
- name: Print Server health
  debug:
  msg: server_health.content
```

### Question 4

Quelle(s) commande(s) liste(nt) uniquement les conteneurs en cours d'exécution ? (plusieurs réponses)

- [ ] A:

```bash
docker ps
```

- [ ] B:

```bash
docker container ls
```

- [ ] C:

```bash
docker container ls -a
```

- [ ] D:

```bash
docker ps -a
```

### Question 5

Quelle(s) commande(s) télécharge(nt) une image d'un registre Docker si elle n'existe pas sur l'hôte actuel (où $IMAGE est le nom de l'image). (plusieurs réponses)

- [ ] A:

```bash
docker load $IMAGE
```

- [ ] B:

```bash
docker run $IMAGE
```

- [ ] C:

```bash
docker pull $IMAGE
```

- [ ] D:

```bash
docker image pull $IMAGE
```

### Question 6

Vous disposez du fichier Dockerfile suivant :

```dockerfile
FROM node:12
WORKDIR /usr/src/app
COPY package.json .
RUN npm install
COPY . .
EXPOSE 4000
CMD [ "npm", "start" ]
```

Quelle commande exécute une application web accessible sur <http://localhost:8000> depuis votre hôte où vous exécutez ce conteneur (où "myapp" est une image construite en utilisant ce Dockerfile) ? (1 réponse)

- [ ] A:

```bash
docker run -p 8000:4000 myapp
```

- [ ] B:

```bash
docker run -p 4000:8000 myapp
```

- [ ] C:

```bash
docker run myapp
```

- [ ] D:

```bash
docker run myapp:latest
```

### Question 7

Vous avez le fichier suivant `docker-compose.yml` :

```yaml
version: "3.0"
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

Que va faire la commande docker-compose up ? (plusieurs réponses)

- [ ] A: Construire 1 image et télécharger 1 image
- [ ] B: Exécuter 2 conteneurs
- [ ] C: Télécharger 2 images
- [ ] D: Persister les données Redis sur l'hôte

### Question 8

Quelle commande liste les pods Kubernetes ? (1 réponse)

- [ ] A:

```bash
kubectl ls pods
```

- [ ] B:

```bash
kubectl get pods
```

- [ ] C:

```bash  debug:
  msg: server_health.content
kubectl pods
```

- [ ] D:

```bash
kubelet
```

### Question 9

Quelle commande liste les déploiements Kubernetes ? (1 réponse)

- [ ] A:

```bash
kubectl ls deployments
```

- [ ] B:

```bash
kubectl get deployments
```

- [ ] C:

```bash
kubectl deployments
```

- [ ] D:

```bash
kubelet
```

### Question 10

Vous avez le fichier de configuration Kubernetes suivant `deployment.yaml` :

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

Que se passera-t-il en appliquant cette configuration ? (plusieurs réponses)

- [ ] A: Créer un déploiement et des pods
- [ ] B: Créer uniquement un déploiement sans créer de pods
- [ ] C: Télécharger une image du registre Docker vers le nœud worker du cluster Kubernetes
- [ ] D: Exécuter 3 conteneurs en utilisant l'image `katacoda/docker-http-server:latest`

## Part 2. Questions on knowledge of theoryPart 2. Questions on knowledge of theory

### Question 11

Parmi les affirmations suivantes sur DevOps, lesquelles sont correctes ? (plusieurs réponses)

- [ ] A: DevOps convient uniquement aux logiciels avec une architecture de microservices
- [ ] B: DevOps n'est qu'un ensemble d'outils
- [ ] C: DevOps rapproche les équipes de développement et d'opérations
- [ ] D: DevOps est implémenté dans le SRE (Site Reliability Engineering)

### Question 12

Quels sont les principes du Manifeste Agile ? (plusieurs réponses)

- [ ] A: Créer une culture d'apprentissage continu et dynamique
- [ ] B: Un logiciel opérationnel est la principale mesure du progrès
- [ ] C: Livrer fréquemment un logiciel opérationnel, de quelques semaines à quelques mois
- [ ] D: La priorité la plus élevée est de satisfaire le client grâce à une livraison précoce et continue d'un logiciel de valeur

### Question 13

Quelles affirmations concernant l'Intégration Continue (CI) sont correctes ? (plusieurs réponses)

- [ ] A: C'est une pratique consistant à fusionner de petits changements de code fréquemment
- [ ] B: C'est une pratique de fusionner un grand changement à la fin d'un cycle de développement
- [ ] C: Elle permet de construire un logiciel plus sain en développant et en testant par petits incréments
- [ ] D: Elle permet de construire un logiciel plus sain en développant et en testant par de plus grands incréments

### Question 14

Quelles affirmations concernant la Livraison Continue (CD) sont correctes ? (plusieurs réponses)

- [ ] A: C'est une discipline de développement logiciel où le logiciel est construit de manière à pouvoir être déployé chez les clients à tout moment
- [ ] B: Elle prolonge l'Intégration Continue (CI) pour s'assurer que vous pouvez rapidement livrer de nouvelles modifications à vos clients de manière durable
- [ ] C: Elle prolonge le Déploiement Continu pour libérer de nouvelles modifications en production après avoir réussi les tests automatisés
- [ ] D: Elle rend les déploiements de logiciels sans douleur

### Question 15

Qu'est-ce qu'une architecture de microservices ? (1 réponse)

- [ ] A: Une approche de conception logicielle qui structure une application comme une collection de petits services indépendants qui communiquent entre eux via des API
- [ ] B: Un outil pour optimiser les performances logicielles
- [ ] C: Un cadre pour gérer des projets logiciels à grande échelle
- [ ] D: Un processus pour automatiser les déploiements de logiciels

### Question 16

Quel est l'ordre correct des actions pour le développement piloté par les tests ? (1 réponse)

- [ ] A:
  1. Refactoriser
  2. Écrire un cas de test
  3. Écrire le code fonctionnel
- [ ] B:
  1. Écrire un cas de test
  2. Écrire le code fonctionnel
  3. Refactoriser
- [ ] C:
  1. Écrire le code fonctionnel
  2. Écrire un cas de test
  3. Refactoriser

### Question 17

Quel type de test simule un scénario d'utilisateur réel qui est généralement difficile à automatiser ? (1 réponse)

- [ ] A: Tests unitaires
- [ ] B: Tests d'intégration
- [ ] C: Tests fonctionnels
- [ ] D: Tests de bout en bout

### Question 18

Quel type de test est proche du code source de votre application et s'exécute dans un environnement très contrôlé ? (1 réponse)

- [ ] A: Tests unitaires
- [ ] B: Tests d'intégration
- [ ] C: Tests fonctionnels
- [ ] D: Tests de bout en bout

### Question 19

Qu'est-ce qu'un conteneur Docker ? (1 réponse)

- [ ] A: Une machine virtuelle
- [ ] B: Un package exécutable autonome et léger qui contient tous les composants nécessaires pour exécuter une application, y compris le code, les dépendances, les bibliothèques et les outils système
- [ ] C: Un outil pour surveiller les performances logicielles
- [ ] D: Un outil pour automatiser les déploiements de logiciels

### Question 20

Lequel n'est pas un objet Docker ? (1 réponse)

- [ ] A: Volumes de données
- [ ] B: Conteneurs
- [ ] C: Utilisateurs
- [ ] D: Images
