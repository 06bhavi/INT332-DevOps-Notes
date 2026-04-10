## **What is Environment variables?**
 These are key value pairs used by applications to 
 - Read configration
 - Store secrets
 - Control applications
## Why we need environment variables?
  1. without -e:
    - configuration must be hard coded in image
    - need to rebuild image for every change
  2. with -e: 
    - same image -> different behaviour
    - widely used in microservices & cloud deployments

## Why we create dockerfile?
a docker file is used to create a docker image that runs a shell script automatically when the container starts
* we will create a simple app where value is fix inside the image.
 - docker build -t myapp:v1 .
 - docker run myapp:v1

## -p optional flag in run command
   - p stands for publish port:- it allows users outside the container to access an application running inside the container.
   - syntax of -p
        docker run -p <HOST_PORT>:<CONTAINER_PORT> IMAGE 
        example:- docker run -p 8080:80 nginx
##  TASK 1
- run ubuntu container
- pass -e college-cse
- show echo $college
- stop container then check what happened
ans:- docker run -it -e COLLEGE=CSE ubuntu bash
      echo $COLLEGE
      exit
      docker ps -a

## Practice Question
1. Run a docker container named "DB-app" based on the "mongodb" image, and expose port 80 on the host port 8082 on the container? 

### Docker Volumes
It is a persistent storage mechanism used by containers to store data.

* why we need docker volumes?
- data is stored on host machine
- container can be recreated without losing data

* Types of storage in docker
- volumes :-  persistent | managed by docker | stored in docker area | safer
- Bind Mounts :- persistent | managed by user | stored in host path | less secure
- tmpfs :- no persistent | in memory | 

* characterstics of storage
- independent of container life cycle
- can be shared by a multiple container
- managed fully by a docker

* question :- you need to start a new container using the nginx image while setting the environment variable Env_MODE=Production . write the docker run command to achieve this

* Practice Question
1. you need to start a new container using the nginx image while setting an environment variable ENV_MODE = production. Write the docker run command to achieve this.
=> 
  - docker run -it -e ENV_MODE=Production nginx bash
  - echo $ENV_MODE
  - exit

2. You have a running container named my_app, but it's not behaving as expected. You want to ckeck its logs to debug any errors. Write the command to view its logs and follow new log entries in real-time.
=> 
  - docker logs -f <container name>
  

3. A container named web_server was stopped. Write the command to: A) start the container again. B) Stop the container when needed.
=> 
- docker run -d --name web_server nginx
- docker start web_server
- docker stop web_server

* `Bind Mount` 
  mount host folder directly in browser changes reflect instantly in a browser

 - docker run -- mount type=<type>,source=<src>,target=<dest> IMAGE
    type - what type of storage (volume / bind/ tmpfs)
    source path (volume name or host name)
    target(Path inside container)
 - Example:-
   1. mkdir D:\docker-volume-demo
   2. echo Hello from HOST machine> D:\docker -volume-demo\hostfile.txt
   3. docker run -it --name app1 -v D:\docker-volume-demo:/data ubuntu bash
   4. inside container 
       - ls
       - cd data
       - cat hostfile.txt
  5. modify file inside container
      - echo "Modified inside container">>/data/hostfile.txt
      - cat hostfile.txt
## Practice question
1. Create a docker volume named studentdata.
2. Run an ubuntu container and mount studentdata at /student.
3. Create a file inside the container and verify it persists after conatiner deletion.
4. attatch the same volume to another container and verify the file exists.
5. demonstrate data sharing between two containers using a shared volume
6. show that deleting container does not delete the volume data.
=>
   - docker volume create studentdata
   - docker run -it --name student -v C:\Userd\hp\studentdata:/student ubuntu bash
   - ls 
   - echo "Hello ubuntu">>/student/file2.txt
   - cd student
   - cat file2.txt
   - 

## Types of Docker Network
- a ping is failed because default bridge have no isolation

## when to use host network
- no port maping needed direct access via local host

* Question:- 
1. Update the ubuntu container, install the apache and PHP, then push updated on to docker hub.
  - docker pull ubuntu
  - docker run -dit --name a1 ubuntu -> run container
  - docker exec -it a1 bash -> enter container
  - apt update -> install pakages
  - apt install -y apache2 php > install pakages
  - exit
2. compare the size of base image and updated image after commit.
  - 

## To build an image from docker file
Example:-  create ubuntu docker file
 - Base Image : FROM ubuntu:latest
 - Maintainer(optional): LABEL maintainer="Student Demo"
 - Install package: RUN apt update && apt install -y php
 - Default command when container runs : CMD["echo" , "Hello Students"]

## Practical 3 
creating a python flask for web application and run a python web application inside docker so it works anywhere without any set up issues 

- create a one folder mkdir docker_python
- cd docker_python
- code
- dir
- make 3 files, first is app.py, second is requirements.txt, third is docker file


flask for web framework
@app.route("/)- for home page path
host - assessing form outside a container
port - app runs on this port 

* create flask file app.py
from flask import flask
app=flask(__name__)
@app.route("/")
def home():
   return "Hello from docker"
app.run(host="0.0.0.0", port=5000)

* create a requirements.txt
 - flask
* create a docker file

after creating all this use these commands
- docker build -t python11
- docker run -p 5001:5000 python11
* to modify all these 
- create new file app2.py

## question
* create docker file, app.py, requirements.txt
- mkdir docker_python
- cd docker_python
- dir
- docker build -t python11 .
- docker run -p 5001:5000 python11
- modify app -> app2 
-  docker build -t pythonapp2 .
- docker run -p 5001:5000 pythonapp2

* you are assigned a task to develop a dockerized web application for a college registration system. Given specifications:
- folder name must be : student_app
- application should: display registration form
- accept the following details: 

## CA1- 
## CA2- project
- practical application of the concepts learned regarding docker,maven, github actions and jenkins

PAT- secure authentication

## question:- 
you are assigned a basic devops task to deploy a static web page using docker.
- your objective is to : 
  pull the latest **NGINX docker image**
- create a simple **HTML page**
- run the container and display the HTML page using **NGINX static hosting**
- use **docker volume mounting** to connect HTML file to the container

## question:- 
Imagine you're managing a project with multiple containers. Answer the following :
- how will you build an image and run a container?
- how do you save changes made to a running container?
- how can you go inside a container (for example, a web app and a database)?
- how to pull image from docker hub





