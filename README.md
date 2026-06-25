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
<img width="534" height="140" alt="Docker_port_mapping4" src="https://github.com/user-attachments/assets/9ad15481-ced2-46e8-96f3-bf69b7ce226a" />

Access the application:

```text
http://localhost:5001
```

Available endpoints:

```text
/
```
<img width="536" height="95" alt="Docker_hello12" src="https://github.com/user-attachments/assets/8135e4d6-3684-46d2-ad06-1449cdc9aee0" />

```text
/contact
```
<img width="432" height="116" alt="Docker_Contact13" src="https://github.com/user-attachments/assets/f09c0af3-d52c-4e49-9524-ced00e6b896e" />

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
<img width="540" height="117" alt="Docker_ps6" src="https://github.com/user-attachments/assets/c4bdc5f3-bf1a-4b2a-9ef0-4a26bb2dceb0" />

---

## Stop Running Containers

```bash
docker stop <container-id>
```

Example:

```bash
docker stop b3506f1b0dcb
```
<img width="532" height="56" alt="Docker_stop6" src="https://github.com/user-attachments/assets/db9442d1-e4a9-4438-b55c-ee898684d4e5" />

---

## Tag Docker Image

Tag the image before pushing to Docker Hub:

```bash
docker tag dev:v1.0 srinivas1431/dev:v1.0
```
<img width="530" height="13" alt="Docker_tag7" src="https://github.com/user-attachments/assets/ac736904-f19e-4874-85a4-6e2ce75c8a5d" />

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
<img width="536" height="76" alt="Docker_tagged_image8" src="https://github.com/user-attachments/assets/c42ed6bc-c1e2-4189-887f-ce8d897ea859" />

---

## Push Image to Docker Hub

```bash
docker push srinivas1431/dev:v1.0
```

Successful push output:

```text
v1.0: digest: sha256:xxxxxxxxxxxxxxxx
```
<img width="532" height="155" alt="Docker_push9" src="https://github.com/user-attachments/assets/53f7e98d-b140-472d-8e30-35c0e21d6576" />

---

## Remove Local Tagged Image

```bash
docker image rm srinivas1431/dev:v1.0
```
<img width="547" height="79" alt="Docker_rm_image10" src="https://github.com/user-attachments/assets/9e53cee4-cc7b-4159-859e-e2ace60a94ef" />

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
<img width="544" height="143" alt="Docker_image_pull11" src="https://github.com/user-attachments/assets/1a528b63-9ac6-49e4-8c6a-907ebce3e7d9" />

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
