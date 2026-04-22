## Evolution of Application Architecture
- 80s–90s: Monolithic apps on physical servers (Waterfall model)
- Late 90s–2000s: Virtualization, n-tier apps (Agile)
- 2010–Present: Cloud + Microservices + Containers + DevOps

## **Monolithic Architecture**
Single large application (UI + Logic + Database combined)

* Components:
UI (User Interface)
Data Access Layer
Data Store (Database)

Example: Old e-commerce systems (Amazon/Flipkart)

* Advantages:
- Easy deployment (single unit)
- Easier testing & debugging
- Better performance (shared memory)

* Disadvantages:
- Hard to scale (only whole app)
- Difficult to update/change tech
- Large & complex

## **Microservices Architecture**
Application divided into small independent services

* Key Features:
- Each service has specific function
- Communicate via APIs (REST, messaging)
- Each service has its own database

Example Services: User Service, Payment Service, Order Service, etc.

* Advantages:
- Fault isolation (one failure ≠ whole system down)
- Faster development (parallel teams)
- Easy maintenance & debugging
- Independent scaling

## Microservices + Containers
Each microservice runs in a container
Improves: Deployment speed, Reliability, Isolation
Managed using Kubernetes (auto-scaling, self-healing)

## Docker Compose
Tool to manage multi-container applications

* Key Points:
- Uses docker-compose.yml (YAML file)
- Defines entire app in one file
- Runs all containers with one command

* Why needed:
- Avoid multiple complex docker run commands
- Easy reproducibility
- Simplified networking & dependencies

* Key Concepts in Docker Compose
Service: Blueprint of container
Image vs Build:
Image → Prebuilt
Build → Custom Dockerfile
Ports: Host:Container mapping
Volumes: Persistent storage
Networks: Communication between services
depends_on: Controls startup order

* Benefits of Docker Compose
Multi-container management
Easy scaling (--scale)
Automatic networking
Cleaner & readable config
Reproducible environments


## Question:
Design a docker compose configuration using a environment variables to configure communication between a node.js backend service and a mongoDB database service
=> - for installation go to your https or nodejs.org
   - if you want to check it is installes use command **node-check**
   - create package.json
      -- npm init -y
      -- npm install express mangoose
   - server.js this is we are creating a express framework which haldels a requests and response