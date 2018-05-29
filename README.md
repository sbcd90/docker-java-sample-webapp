docker-java-sample-webapp
=========================

## Getting started

- Build the java app

`mvn clean install`

- Take the war file from `target` & put it into `src/main/docker` directory.

## Docker commands approach

- Go into `src/main/docker` directory

- Build the docker image

`docker build -t tomcat:1 .`

- Run the image inside a container

`docker container run -p 8080:8080 tomcat:1`

- Go to `http://localhost:8080/docker-java-sample-webapp-1.0-SNAPSHOT?name=World` & see the app running in docker

- List all containers

`docker container ls`

- Stop container

`docker container kill <container-id>`

- Remove container

`docker rm <container-id>`

- List all images

`docker images`

- Remove image

`docker rmi tomcat:1`

- Remove base image

`docker rmi bitnami/tomcat:latest`

## Docker compose approach

- Go into `src/main/docker` directory

- Execute the command

`docker-compose up`

- When it is stopped, the corresponding containers are deleted also. But images remain. They have to be deleted using commands.

## Kubernetes approach

- Use docker edge channel. It has inbuilt kubernetes support.

- To get kubernetes dashboard running

- `kubectl cluster-info`
- `kubectl -n kube-system edit service kubernetes-dashboard`
- `You should see yaml representation of the service. Change type: ClusterIP to type: NodePort and save file. If it's already changed go to next step.`
- `kubectl -n kube-system get service kubernetes-dashboard`

- Now deploy the war

- Use helm 2.8.2
- `helm.exe install .`

- To delete entire deployment
- `kubectl delete deployment kissing-fish-java-sample-webapp`


## Extras

- Log into the container

`docker exec -it [container-id] bash`