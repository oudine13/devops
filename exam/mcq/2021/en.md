
# DevOps with SRE MCQ

## Part 1. Questions on command execution

### Question 1

You have just changed the `README.md` file in your local Git repository. Which sequence(s) of commands push(es) the changes to a remote repository?

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

Which command(s) checkout(s) the `master` branch?

* [ ] A: `git checkout -f master`
* [ ] B: `git checkout`
* [ ] C: `git master`
* [ ] D: `git checkout master`

### Question 3

Which command(s) list(s) only running containers?

* [ ] A: `docker ps` 
* [ ] B: `docker container ls`
* [ ] C: `docker container ls -a`
* [ ] D: `docker ps -a`

### Question 4

Which command(s) stop(s) and not remove(s) a running container (where `$CONTAINER` is a container name or a container ID)?

* [ ] A: `docker kill $CONTAINER`
* [ ] B: `docker rmi $CONTAINER`
* [ ] C: `docker stop $CONTAINER`
* [ ] D: `docker rm $CONTAINER`

### Question 5

Which command(s) download(s) an image from a Docker registry if it doesn’t exist on the current host (where `$IMAGE` is an image name).

* [ ] A: `docker load $IMAGE`
* [ ] B: `docker run $IMAGE`
* [ ] C: `docker pull $IMAGE`
* [ ] D: `docker image pull $IMAGE`

### Question 6

You have the following `Dockerfile` file:

```dockerfile
FROM node:12
WORKDIR /usr/src/app
COPY package.json .
RUN npm install
COPY . .
EXPOSE 4000
CMD [ "npm", "start" ]
```

Which command(s) run(s) a web application accessible on `http://localhost:8000` from your host where you run this container (where “myapp” is an image built using this `Dockerfile`)?

* [ ] A: `docker run -p 8000:4000 myapp`
* [ ] B: `docker run -p 4000:8000 myapp`
* [ ] C: `docker run myapp`
* [ ] D: `docker run myapp:latest`

### Question 7

Which command(s) list(s) Kubernetes pods?

* [ ] A: `kubectl ls pods`
* [ ] B: `kubectl get pods`
* [ ] C: `kubelet ls pods`
* [ ] D: `kubelet get pods`

### Question 8

Which command(s) list(s) Kubernetes deployments?

* [ ] A: `kubectl ls deployments`
* [ ] B: `kubectl get deployments`
* [ ] C: `kubelet ls deployments`
* [ ] D: `kubelet get deployments`

### Question 9

Which command(s) apply(ies) configuration(s) in Kubernetes (where `$FILENAME` is a YAML file located in your current directory)?

* [ ] A: `kubectl run -f $FILENAME`
* [ ] B: `kubectl -f $FILENAME`
* [ ] C: `kubectl apply -f $FILENAME`
* [ ] D: `kubectl apply -f .`

### Question 10

You have the following Kubernetes configuration `deployment.yaml` file:

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

What will happen by applying this configuration?

* [ ] A: Create a deployment and pods
* [ ] B: Create only a deployment without creating pods
* [ ] C: Pull an image from the Docker registry to the worker node of the Kubernetes cluster
* [ ] D: Run 3 containers using `katacoda/docker-http-server:latest` image

### Question 11

Which command(s) allow(s) to run a command inside a running container

* [ ] A: `docker exec ...`
* [ ] B: `docker run ...`
* [ ] C: `docker start ...`
* [ ] D: `docker create ...`

### Question 12

Which command(s) start(s) one or many containers using Docker Compose (where `$SERVICE` is a service name, configured in `docker-compose.yml` file)?

* [ ] A: `docker compose up`
* [ ] B: `docker-compose up`
* [ ] C: `docker run -c .`
* [ ] D: `docker-compose start $SERVICE`

### Question 13

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

* [ ] A: Build 1 image and pull 1 image
* [ ] B: Run 2 containers
* [ ] C: Pull 2 images
* [ ] D: Persist redis data on the host

### Question 14

You have the following `docker-compose.yml` file:

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

Choose correct option(s) where "nginx" service is accessible and "redis" service attaches data:

* [ ] A: On the host: URL - `localhost:80`, folder - `/mnt/data`
* [ ] B: On the host: URL - `localhost:9000`, folder - `/data`
* [ ] C: In the container: URL - `localhost:80`, folder - `/data`
* [ ] D: In the container: URL - `localhost:9000`, folder - `/mnt/data`

### Question 15

You have the following Kubernetes manifest file:

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

Which statement(s) is(are) correct when applying the following manifest file:

* [ ] A: It creates 1 Deployment, 3 Pods, 1 Service
* [ ] B: Nginx web server is not accessible on `localhost:80` from the Kubernetes cluster
* [ ] C: It creates 3 Deployments, 1 Pod, 1 Service
* [ ] D: The service "hello" is stateful

## Part 2. Questions on knowledge of theory

### Question 16

Which of the following statement(s) about DevOps is(are) correct?

* [ ] A: DevOps is only suitable for software with microservices architecture
* [ ] B: DevOps is a set of tools
* [ ] C: DevOps brings the development and operations teams together
* [ ] D: DevOps is implemented in SRE (Site Reliability Engineering)

### Question 17

Which order of actions is correct for test-driven development? 

* [ ] A:
  ```
  1. Refactor
  2. Write a test case
  3. Write the functional code
  ```

* [ ] B:
  ```
  1. Write a test case
  2. Write the functional code
  3. Refactor 
  ```

* [ ] C: 
  ```
  1. Write the functional code
  2. Write a test case
  3. Refactor
  ```

### Question 18

The Manifesto for Agile Software Development includes the following item(s):

* [ ] A: Processes and tools over individuals and interactions
* [ ] B: Working software over comprehensive documentation
* [ ] C: Customer collaboration over contract negotiation
* [ ] D: Following a plan over responding to change

### Question 19

What is(are) the principle(s) of the Agile Manifesto?

* [ ] A: To create a culture of continual and dynamic learning
* [ ] B: Working software is the primary measure of progress
* [ ] C: Deliver working software frequently, from a couple of weeks to a couple of months
* [ ] D: The highest priority is to satisfy the customer through early and continuous delivery of valuable software

### Question 20

Which functionality(ies) do(es) Container Orchestration provide?

* [ ] A: Load balancing and traffic routing
* [ ] B: Managing an IT infrastructure using configuration files
* [ ] C: Monitoring container health
* [ ] D: Keeping interactions between containers secure or insecure

### Question 21

What type of test is simulating the real user scenario that is typically hard to automate?

* [ ] A: Unit tests
* [ ] B: Integration tests
* [ ] C: Functional tests
* [ ] D: End-to-end tests

### Question 22

What type of test is close to the source code of your application and runs in a very controlled environment?

* [ ] A: Unit tests
* [ ] B: Integration tests
* [ ] C: Functional tests
* [ ] D: End-to-end tests

### Question 23

Which statement(s) about Continuous Integration (CI) is(are) correct?

* [ ] A: It is a practice of merging small code changes frequently
* [ ] B: It is a practice of merging a large change at the end of a development cycle
* [ ] C: It builds healthier software by developing and testing in smaller increments
* [ ] D: It builds healthier software by developing and testing in bigger increments

### Question 24

Which statement(s) about Continuous Delivery (CD) is(are) correct?

* [ ] A: It is a software development discipline where software is built in a manner that allows for deploying to customers at any time
* [ ] B: It extends Continuous Integration (CI) to make sure that you can release new changes to your customers quickly in a sustainable way
* [ ] C: It extends the Continuous Deployment to release new changes to production after it passes automated testing
* [ ] D: It makes software deployments painless

### Question 25

Which is(are) not (a) Docker object(s)?

* [ ] A: Data volumes
* [ ] B: Containers
* [ ] C: Users
* [ ] D: Images

### Question 26

What can be automated by applying Infrastructure as Code (IaC) tools like Ansible?

* [ ] A: Code review process
* [ ] B: Cloud provisioning
* [ ] C: Infrastructure configuration management
* [ ] D: Application deployment

### Question 27

What Service Mesh does provide?

* [ ] A: Connection between services
* [ ] B: Infrastructure deployment
* [ ] C: Observability into service communications
* [ ] D: Securing connections

### Question 28

What is(are) the benefit(s) of microservice architecture?

* [ ] A: Each module can be scaled independently
* [ ] B: Architectures are typically better organized around business capabilities
* [ ] C: The lower level of agility for organizations
* [ ] D: Flexibility in choosing the programming language

### Question 29

What Ansible does not provide?

* [ ] A: Cloud provisioning
* [ ] B: Configuration management
* [ ] C: Container orchestration
* [ ] D: Application deployment

### Question 30

Which Kubernetes Volume type(s) is(are) most appropriate to use for stateless services?

* [ ] A: `emptyDir`
* [ ] B: `hostPath`
* [ ] C: `nfs`
* [ ] D: `persistentVolumeClaim`
