#Docker and Kubernetes tutorials start

**DOCKER IMAGE**

*Image is a template for creating an environment of your choice
*Snapshot
*Has everything needed to run the apps (dependencies, modules and code)
*OS, software, App code

**Steps:**

1. Create image with all dependencies installed
2. Run container from that image
3. Commit changes into new snapshot
4. Save snapshot as Docker Image
5. Push Docker Image to Registry
6. Deploy on Kubernetes Cluster
7. Access app via Ingress or NodePort service
8. Monitor using Prometheus/Grafana
9. Scale up/down based on load

###Step 1: Installing Dependencies
bash
sh

**CONTAINER**
Containers in Docker are created using images, which are read-only templates that define the container's contents. An image is created by writing a Dockerfile, which is a script that contains instructions for building the image.

### Use an official Python runtime as a parent image

FROM python:3.7-slim

### Set the working directory in the container

WORKDIR /app

### Add the current directory contents into the container at /app

ADD . /app

### Install any needed packages specified in requirements.txt

RUN pip install --no-cache-dir -r requirements.txt

### Make port 80 available to the world outside this container

EXPOSE 80

### Run app.py when the container launches

CMD ["python", "app.py"]

### To run a container of an image

docker run [OPTIONS] IMAGE[:TAG|@DIGEST]
**IMAGE**

### Build the image by defining a name and version tag

docker build -t myimage:v1 .

### List images built locally

docker images

### Tag the image with a more specific tag (optional)

docker tag myimage:v1 username/repository:tag

### Push the image to Docker Hub

docker push username/repository:tag
**HOST**

### Run the image and map port 80 of the container to port 8090

### of the host machine - making it accessible via localhost:8090

docker run -p 8090:80 myimage:v1</s>
**DETACH MODE**
docker run -d <imageName>:<tagName>
**INTERACTIVE TERMINAL**
docker run -it <imageName>:<tagName> bash
**VOLUMES**
docker run -d -P -v /data:/usr/src/app myimage
**ENVIRONMENT VARIABLES**
docker run -e "DB_USER=dbuser" -e "DB_PASSWORD=
password" myimage
**NETWORKS**
docker network create mynetwork
docker run --net mynetwork --ip 172.30.45.6
**EXPOSING MULTIPLE PORTS**
docker run -p 8080:8080 -p 909
0:9090 myimage
**CONTAINERS AS SERVICES**
