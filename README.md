# docker_myMicroservice
this repository has a prof of concept about implementation of microservices in docker

# Docker

In `Dockerfile` there is all the configuration for the docker image, wich is used as template for the application.

In `.dockerignore` put files that cannot be in docker image, is like a `gitignore`

## Commands

To build the application in docker image.

`docker build -t mymicroservice .`

To list docker images.

`docker images`

To run docker images.

`docker run -it --rm -p 3000:80 --name mymicroservicecontainer mymicroservice`

To login in dockerhub

`docker login`

To retag (rename) docker image

`docker tag NAME_DOCKER_IMAGE NEW_NAME_DOCKER_IMAGE`

To push docker image to docker hub

`docker psuh DOCKER_IMAGE_NAME`

# Azure Kubernetes Service (AKS)

Provide a kubernetes as a managed service.

Kubernetes is a container orchestration platform.

Use a deploy.yaml file to define the process of publish in aks

## Commands

To login azure account in local

`az login`

To install aks cli

`az aks install-cli`

To create a resource group in West US region.

`az group create --name pruebas-concepto --location westus`

List as table all locations.

`az account list-locations -o table`

Create a AKS cluster in resourse group.

`az aks create --resource-group pruebas-concepto --name cluster-container --node-count 1 --enable-addons http_application_routing --generate-ssh-keys`

to fix error about resour group not found.

`az account list --output table`
`az account set --subscription <subscription-id>`

To download credential to deploy to the new aks cluster

`az aks get-credentials --resource-group pruebas-concepto --name cluster-container`

To deploy base on settings in deploy.yaml

`kubectl apply -f deploy.yaml`

To test deploy

`kubectl get service mymicroservice --watch`

To scale the service in N replicas

`kubectl scale --replicas=2 deployment/mymicroservice`