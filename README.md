# Docker_Images_and_Containers

# Dockerized Flask Application

## Project Overview

This project demonstrates how to containerize a Python Flask application using Docker, build a custom Docker image, run the application inside a container, and publish the image to Docker Hub.

---

## Prerequisites

Before starting, ensure the following tools are installed:

* Docker Desktop
* Python 3.x
* Docker Hub Account
* Git (optional)

Verify Docker installation:

```bash
docker --version
docker info
```

---

## Project Structure

```text
.
├── app.py
├── requirements.txt
└── Dockerfile
```

### app.py

Contains the Flask application source code.

### requirements.txt

Contains Python dependencies required by the application.

### Dockerfile

Defines the instructions to build the Docker image.

---

## Dockerfile

```dockerfile
FROM python:3.11-alpine

WORKDIR /app

COPY requirements.txt .

RUN pip install -r requirements.txt

COPY . .

CMD ["python", "app.py"]
```

---

## Docker Login
Authenticate with Docker Hub:

```bash
docker login -u <dockerhub-username>
```

Example:

```bash
docker login -u srinivas1431
```
<img width="509" height="118" alt="Docker_Login1" src="https://github.com/user-attachments/assets/37096dde-892f-493b-8494-827071e86cb5" />
---

## Build Docker Image

Build the image using the Dockerfile:

```bash
docker build . -t dev:v1.0
```
<img width="543" height="313" alt="Docker_building_image2" src="https://github.com/user-attachments/assets/253b633a-0232-424f-bfa9-d720fca019ee" />

Verify image creation:

```bash
docker images
```
Output:

```text
REPOSITORY   TAG     IMAGE ID
dev          v1.0    2093396675c6
```
<img width="540" height="53" alt="Docker_images3" src="https://github.com/user-attachments/assets/1b9db0a7-88e2-4f2b-bcd5-f28820a64608" />

---

## Run Docker Container

Run the container and expose the Flask application:

```bash
docker run -p 5001:5000 dev:v1.0
```

Port Mapping:

```text
Host Port      : 5001
Container Port : 5000
```

Access the application:

```text
http://localhost:5001
```

Available endpoints:

```text
/
```

```text
/contact
```

---

## View Running Containers

```bash
docker ps
```

Example:

```text
CONTAINER ID   IMAGE      STATUS
b3506f1b0dcb   dev:v1.0   Up
```

---

## Stop Running Containers

```bash
docker stop <container-id>
```

Example:

```bash
docker stop b3506f1b0dcb
```

---

## Tag Docker Image

Tag the image before pushing to Docker Hub:

```bash
docker tag dev:v1.0 srinivas1431/dev:v1.0
```

Verify:

```bash
docker images
```

Output:

```text
REPOSITORY              TAG
dev                     v1.0
srinivas1431/dev        v1.0
```

---

## Push Image to Docker Hub

```bash
docker push srinivas1431/dev:v1.0
```

Successful push output:

```text
v1.0: digest: sha256:xxxxxxxxxxxxxxxx
```

---

## Remove Local Tagged Image

```bash
docker image rm srinivas1431/dev:v1.0
```

---

## Pull Image from Docker Hub

Download the image from Docker Hub:

```bash
docker pull srinivas1431/dev:v1.0
```

Verify:

```bash
docker images
```

---

## Docker Commands Used

| Command         | Description                    |
| --------------- | ------------------------------ |
| docker login    | Login to Docker Hub            |
| docker build    | Build Docker image             |
| docker run      | Run container                  |
| docker ps       | View running containers        |
| docker stop     | Stop running container         |
| docker images   | List local images              |
| docker tag      | Tag image for repository       |
| docker push     | Upload image to Docker Hub     |
| docker pull     | Download image from Docker Hub |
| docker image rm | Remove image                   |

---

## Learning Outcomes

By completing this project, you learned:

* Docker image creation
* Container lifecycle management
* Port mapping
* Docker Hub authentication
* Image tagging
* Image push and pull operations
* Running Flask applications inside containers

---

## Author

Srinivas Addepalli

Docker Hub Repository:

srinivas1431/dev:v1.0
