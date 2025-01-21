
# DevOps with SRE MCQ

## Part 1. Questions on command execution

### Question 1

You have just changed the `README.md` file in your local Git repository. Which sequence(s) of commands push(es) the changes to a remote repository?

* [ ] A:
  ```bash
  git push
  ```
* [ ] B:
  ```bash
  git commit -m “some change”
  git push
  ```
* [ ] C:
  ```bash
  git add README.md
  git commit -m “some change”
  git push origin
  ```
* [ ] D:
  ```bash
  git add .
  git commit -m “some change”
  git push
  ```

### Question 2

Which command(s) checkout(s) the `master` branch?

* [ ] A: `git switch master`
* [ ] B: `git checkout master`
* [ ] C: `git checkout`
* [ ] D: `git master`

### Question 3

You have launched a single virtual machine `vm01` with Vagrant. Which command(s) allow you to open a terminal in `vm01` from its SSH port `2222` and IP `127.0.0.1`?

* [ ] A: `vagrant run -p 2222 vm01`
* [ ] B: `vagrant ssh`
* [ ] C: `vagrant ssh vm01`
* [ ] D: `ssh -p 2222 -i ./.vagrant/machines/vm01/virtualbox/private_key vagrant@127.0.0.1`

### Question 4

You have a server with an endpoint `/health` returning `SERVER OK` when the service is healthy. You are performing a health check on your server with the following ansible playbook:

```
- name: Check Server health
  uri:
    url: http://127.0.0.1/-/health
    return_content: yes
  register: server_health
```

How would you display only the response `SERVER OK` in the terminal, if the server is healthy? (1 answer)

* [ ] A:
```
- name: Print Server health
  debug:
    msg: "SERVER OK"
```
* [ ] B:
```
- name: Print Server health
  debug:
    msg: server_health
```
* [ ] C:
```
- name: Print Server health
  debug:
    msg: "{{ server_health.content }}"
```
* [ ] D:
```
- name: Print Server health
  debug:
    msg: server_health.content
```

### Question 5

Which command(s) list(s) only running containers?

* [ ] A: `docker container ls -a`
* [ ] B: `docker ps -a` 
* [ ] C: `docker container ls`
* [ ] D: `docker ps` 

### Question 6

Which command(s) download(s) an image from a Docker registry if it doesn’t exist on the current host (where `$IMAGE` is an image name).

* [ ] A: `docker pull $IMAGE`
* [ ] B: `docker image pull $IMAGE`
* [ ] C: `docker load $IMAGE`
* [ ] D: `docker run $IMAGE`

### Question 7

You have the following `Dockerfile` file:

```dockerfile
FROM node:12
WORKDIR /usr/src/app
COPY package.json .
RUN npm install
COPY . .
EXPOSE 5000
CMD [ "npm", "start" ]
```

Which command(s) run(s) a web application accessible on `http://localhost:8000` from your host where you run this container (where “myapp” is an image built using this `Dockerfile`)? (1 answer)

* [ ] A: `docker run myapp`
* [ ] B: `docker run -p 8000:5000 myapp`
* [ ] C: `docker run -p 5000:8000 myapp`
* [ ] D: `docker run myapp:latest`

### Question 8

Which command(s) list(s) Kubernetes pods? (1 answer)

* [ ] A: `kubectl pods`
* [ ] B: `kubelet`
* [ ] C: `kubectl ls pods`
* [ ] D: `kubectl get pods`

### Question 9

With the following project stucture:

```
project/k8s/development
├── configmap
│   └── my-configmap.yaml
├── deployment
│   └── my-deployment.yaml
└── pvc
    └── my-pvc.yaml 
```

What happens if we run: (1 answer)

```
kubectl apply -f project/k8s/development 
```

* [ ] A: It will deploy all the objects
* [ ] B: It will only deploy `my-configmap.yaml`
* [ ] C: It will deploy all the objects if we give the `--recursive` option

### Question 10

You have the following Kubernetes configuration `deployment.yaml` file:

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: webapp1
spec:
  replicas: 5
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

What will happen by applying this configuration?

* [ ] A: Create a deployment and pods
* [ ] B: Create only a deployment without creating pods
* [ ] C: Run 5 containers using `katacoda/docker-http-server:latest` image
* [ ] D: Pull an image from the Docker registry to the worker node of the Kubernetes cluster

### Question 11

Which command(s) allow(s) to run a command inside a running container? (1 answer)

* [ ] A: `docker run ...`
* [ ] B: `docker exec ...`
* [ ] C: `docker start ...`
* [ ] D: `docker create ...`

### Question 12

You have the following `docker-compose.yml` file:

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

What `docker-compose up` command will do?

* [ ] A: Run 2 containers
* [ ] B: Pull 2 images
* [ ] C: Build 1 image and pull 1 image
* [ ] D: Persist Redis data on the host

## Part 2. Questions on knowledge of theory

### Question 13

Which of the following statement(s) about DevOps is(are) correct?

* [ ] A: DevOps is just a set of tools
* [ ] B: DevOps is only suitable for software with microservices architecture
* [ ] C: DevOps brings the development and operations teams together
* [ ] D: DevOps is implemented in SRE (Site Reliability Engineering)

### Question 14

What is(are) the principle(s) of the Agile Manifesto?

* [ ] A: Working software is the primary measure of progress
* [ ] B: Deliver working software frequently, from a couple of weeks to a couple of months
* [ ] C: To create a culture of continual and dynamic learning
* [ ] D: The highest priority is to satisfy the customer through early and continuous delivery of valuable software

### Question 15

What type of test is simulating the real user scenario that is typically hard to automate? (1 answer)

* [ ] A: Unit tests
* [ ] B: Integration tests
* [ ] C: Functional tests
* [ ] D: End-to-end tests

### Question 16

What type of test is close to the source code of your application and runs in a very controlled environment? (1 answer)

* [ ] A: Unit tests
* [ ] B: Integration tests
* [ ] C: Functional tests
* [ ] D: End-to-end tests

### Question 17

Which order of actions is correct for test-driven development? (1 answer)

* [ ] A: 
  ```
  1. Write the functional code
  2. Write a test case
  3. Refactor
  ```

* [ ] B:
  ```
  1. Refactor
  2. Write a test case
  3. Write the functional code
  ```

* [ ] C:
  ```
  1. Write a test case
  2. Write the functional code
  3. Refactor 
  ```

### Question 18

Which statement(s) about Continuous Integration (CI) is(are) correct?

* [ ] A: It is a practice of merging small code changes frequently
* [ ] B: It is a practice of merging a large change at the end of a development cycle
* [ ] C: It builds healthier software by developing and testing in smaller increments
* [ ] D: It builds healthier software by developing and testing in bigger increments

### Question 19

Which statement(s) about Continuous Delivery (CD) is(are) correct?

* [ ] A: It makes software deployments painless
* [ ] B: It is a software development discipline where software is built in a manner that allows for deploying to customers at any time
* [ ] C: It extends Continuous Integration (CI) to make sure that you can release new changes to your customers quickly in a sustainable way
* [ ] D: It extends the Continuous Deployment to release new changes to production after it passes automated testing

### Question 20

What statements are true about Github Workflows?

* [ ] A: Workflows must use a trigger
* [ ] B: In a repository, workflows are situed in `./workflows`
* [ ] C: Workflows run on your local machine by default
* [ ] D: Workflows executions are limited in private repositories

### Question 21

What can be automated by applying Infrastructure as Code (IaC) tools like Ansible?

* [ ] A: Cloud provisioning
* [ ] B: Code review process
* [ ] C: Infrastructure configuration management
* [ ] D: Application deployment

### Question 22

What elements are shared between containers?

* [ ] A: Application
* [ ] B: Binaries and Libraries
* [ ] C: Container Runtime
* [ ] D: Host Operating System

### Question 23

Which is not a Docker object? (1 answer)

* [ ] A: Containers
* [ ] B: Users
* [ ] C: Images
* [ ] D: Data volumes

### Question 24

Which functionality(ies) do(es) Container Orchestration provide?

* [ ] A: Restart broken containers
* [ ] B: Monitoring container health
* [ ] C: Load balancing and traffic routing
* [ ] D: Managing an IT infrastructure using configuration files

### Question 25

What are the most appropriate tools to manage a large number of containers?

* [ ] A: bash scripts
* [ ] B: Docker Swarm
* [ ] C: Kubernetes
* [ ] D: Docker Compose

### Question 26

By what Kubernetes object(s) a PersistentVolume can bind to?

* [ ] A: one pod
* [ ] B: many pods
* [ ] C: one PVC
* [ ] D: many PVCs

### Question 27

By default, which Kubernetes volume is deleted at the same time than its binded pod? (1 answer)

* [ ] A: nfs
* [ ] B: emptyDir
* [ ] C: hostPath
* [ ] D: persistentVolumeClaim

### Question 28

Which solution gives you the most control on your environment? (1 answer)

* [ ] A: On-Premises
* [ ] B: IaaS
* [ ] C: Paas
* [ ] D: SaaS

### Question 29

What service mesh allows?

* [ ] A: To perform A/B testing
* [ ] B: To manage services trafic
* [ ] C: To migrate infrastucture
* [ ] D: To deploy new services

### Question 30

When should we use Monitoring in DevOps: (1 answer)

* [ ] A: After deployment
* [ ] B: Whenever we can collect data
* [ ] C: Only in production
