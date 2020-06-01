[![CircleCI](https://circleci.com/gh/ruhulamingp/udacity-ml.svg?style=svg)](https://circleci.com/gh/ruhulamingp/udacity-ml)

## Project Summary

This is my 4th project of Udacity Nanodegree of Cloud Engineer. In this project we will build a kubernetes cluster where a machine learning model will run. An API is exposed which takes input of different property of house and predict the house price.

### Git Repo

https://github.com/ruhulamingp/udacity-ml

### Dependencies

Docker Minikube python3 pip venv

### Instruction

### Step 01 : Checking python app locally

a.  Clone the code from repository.

    git clone https://github.com/ruhulamingp/udacity-ml

b.  Create a virtualenv and activate it

    python3 -m venv ~/.devops
    source ~/.devops/bin/activate   

c.  Install necessary dependencies with Makefile

    make install

d.  Run standalone app:

    python app.py

### Step 02 : Running App in Docker

a.  Run the shell:

    ./run_docker.sh

This will build a docker container and run it on 8000 port of host. Then open a new terminal window keeping the container window open. 

b.  Then call the API with the following shell script to get the output of in the previous window:

    ./make_prediction.sh

### Step 03 : Running App in K8s

a.  Run the shell

    ./run_kubernetes.sh

b.  This will show the container creating status. Wait for sometime and after that in another terminal run following command to check the pod status:

    kubectl get pods
    
c.  Run prediction :

    ./make_prediction_k8s.sh

### Step 04: Adding Circle CI

Go to CircleCi and open an account with Github as organization. The add this project with the provided configuration. The add any line in readme and push to github. This will trigger a build and you will see whether it has failed or passed.

### Files

**makefile** Setup instruction of python environment and lint.

**app.py** Python code which we will run.

**Dockerfile** Definition of the Docker container which will expose the service in port 80.

**run_docker.sh** Building docker container from Docker file and run it on port 8000

**make_prediction.sh** Tests the docker container connecting with port 8000

**upload_docker.sh** Uploads the image to dockerhub

**run_kubernates.sh** Pulls the docker image and creates deployment.

**make_prediction_k8s.sh** Tests kubernetes cluster connecting with port 8001

**docker_out.txt** Output of terminal while running docker

**kubernetes_out.txt** Output of terminal while running kubernetes

**.circleci/config.yml** Circle Ci configuration mentioning steps to lint and build the project
