# DevOps with SRE MCQ

## Part 1: Questions on Command Execution

### Question 1

You have just changed the `README.md` file in your local Git repository. Which sequence(s) of commands push(es) the changes to a remote repository? (multiple answers)

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

Which Git command(s) is(are) used to create a new branch? (multiple answers)

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

You have a server with an endpoint /health returning `SERVER OK` when the service is healthy. You are performing a health check on your server with the following ansible playbook:

```yaml
- name: Check Server health
uri:
url: http://127.0.0.1/-/health
return_content: yes
register: server_health
```

How would you display only the response `SERVER OK` in the terminal, if the server is healthy? (1 answer)

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

Which command(s) list(s) only running containers? (multiple answers)

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

Which command(s) download(s) an image from a Docker registry if it doesn’t exist on the current host (where $IMAGE is an image name). (multiple answers)

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

You have the following Dockerfile file:

```dockerfile
FROM node:12
WORKDIR /usr/src/app
COPY package.json .
RUN npm install
COPY . .
EXPOSE 4000
CMD [ "npm", "start" ]
```

Which command run a web application accessible on <http://localhost:8000> from your host where you run this container (where “myapp” is an image built using this Dockerfile)? (1 answer)

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

You have the following `docker-compose.yml` file:

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

What docker-compose up command will do? (multiple answers)

- [ ] A: Build 1 image and pull 1 image
- [ ] B: Run 2 containers
- [ ] C: Pull 2 images
- [ ] D: Persist Redis data on the host

### Question 8

Which command list Kubernetes pods? (1 answer)

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

Which command list Kubernetes deployments? (1 answer)

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

What will happen by applying this configuration? (multiple answers)

- [ ] A: Create a deployment and pods
- [ ] B: Create only a deployment without creating pods
- [ ] C: Pull an image from the Docker registry to the worker node of the Kubernetes cluster
- [ ] D: Run 3 containers using `katacoda/docker-http-server:latest` image

## Part 2. Questions on knowledge of theoryPart 2. Questions on knowledge of theory

### Question 11

Which of the following statement(s) about DevOps is(are) correct? (multiple answers)

- [ ] A: DevOps is only suitable for software with microservices architecture
- [ ] B: DevOps is just a set of tools
- [ ] C: DevOps brings the development and operations teams together
- [ ] D: DevOps is implemented in SRE (Site Reliability Engineering)

### Question 12

What is(are) the principle(s) of the Agile Manifesto? (multiple answers)

- [ ] A: To create a culture of continual and dynamic learning
- [ ] B: Working software is the primary measure of progress
- [ ] C: Deliver working software frequently, from a couple of weeks to a couple of months
- [ ] D: The highest priority is to satisfy the customer through early and continuous delivery of valuable software

### Question 13

Which statement(s) about Continuous Integration (CI) is(are) correct? (multiple answers)

- [ ] A: It is a practice of merging small code changes frequently
- [ ] B: It is a practice of merging a large change at the end of a development cycle
- [ ] C: It builds healthier software by developing and testing in smaller increments
- [ ] D: It builds healthier software by developing and testing in bigger increments

### Question 14

Which statement(s) about Continuous Delivery (CD) is(are) correct? (multiple answers)

- [ ] A: It is a software development discipline where software is built in a manner that allows for deploying to customers at any time
- [ ] B: It extends Continuous Integration (CI) to make sure that you can release new changes to your customers quickly in a sustainable way
- [ ] C: It extends the Continuous Deployment to release new changes to production after it passes automated testing
- [ ] D: It makes software deployments painless

### Question 15

What is a microservice architecture? (1 answer)

- [ ] A: A software design approach that structures an application as a collection of small, independent services that communicate with each other through APIs
- [ ] B: A tool for optimizing software performance
- [ ] C: A framework for managing large-scale software projects
- [ ] D: A process for automating software deployments

### Question 16

Which order of actions is correct for test-driven development? (1 answer)

- [ ] A:
  1. Refactor
  2. Write a test case
  3. Write the functional code
- [ ] B:
  1. Write a test case
  2. Write the functional code
  3. Refactor
- [ ] C:
  1. Write the functional code
  2. Write a test case
  3. Refactor

### Question 17

What type of test is simulating the real user scenario that is typically hard to automate? (1 answer)

- [ ] A: Unit tests
- [ ] B: Integration tests
- [ ] C: Functional tests
- [ ] D: End-to-end tests

### Question 18

What type of test is close to the source code of your application and runs in a very controlled environment? (1 answer)

- [ ] A: Unit tests
- [ ] B: Integration tests
- [ ] C: Functional tests
- [ ] D: End-to-end tests

### Question 19

What is a Docker container? (1 answer)

- [ ] A: A virtual machine
- [ ] B: A lightweight, standalone executable package that contains all the necessary components to run an application, including code, dependencies, libraries, and system tools
- [ ] C: A tool for monitoring software performance
- [ ] D: A tool for automating software deployments

### Question 20

Which is not a Docker object? (1 answer)

- [ ] A: Data volumes
- [ ] B: Containers
- [ ] C: Users
- [ ] D: Images
