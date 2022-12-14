[![CircleCI](https://dl.circleci.com/status-badge/img/gh/angelo-inexa/udacityproject4/tree/master.svg?style=svg)](https://dl.circleci.com/status-badge/redirect/gh/angelo-inexa/udacityproject4/tree/master)

## Project Overview

the main goal of this project is  to operationalize a Machine Learning Microservice API. 

using a pre-trained, `sklearn` model that has been trained to predict housing prices in Boston according to several features, such as average rooms in a home and data about highway access, teacher-to-pupil ratios, and so on. This project aims  to operationalize a Python flask app—in a provided file, `app.py`—that serves out predictions (inference) about housing prices through API calls. This project could be extended to any pre-trained machine learning model, such as those for image recognition and data labeling.

### Project Tasks

 In this project we will:
* Test the project code using linting
* Complete a Dockerfile to containerize this application
* Deploy your containerized application using Docker and make a prediction
* Improve the log statements in the source code for this application
* Configure Kubernetes and create a Kubernetes cluster
* Deploy a container using Kubernetes and make a prediction
* Upload a complete Github repo with CircleCI to indicate that your code has been tested

## Setup the Environment

* Create a virtualenv with Python 3.7 and activate it. Refer to this link for help on specifying the Python version in the virtualenv. 
```bash
python3 -m pip install --user virtualenv
# You should have Python 3.7 available in your host. 
# Check the Python path using `which python3`
# Use a command similar to this one:
python3 -m virtualenv .devops
source .devops/bin/activate
```
* Run `make install` to install the necessary dependencies

```bash
cd project-ml-microservice-kubernetes
make install
```
* Run make lint to install the necessary dependencies
```bash
make lint
```
### Running `app.py`

1. Standalone:  `python app.py`
```bash
python3 app.py
```

2. Run in Docker:  `./run_docker.sh`
```bash
chmod +x ./run_docker.sh
./run_docker.sh
docker logs -f microserviceproject &> output_txt_files/docker_out.txt &
```
3. Test predictions(local): `./make_prediction.sh`
```bash
chmod +x ./make_prediction.sh 
./make_prediction.sh 
```
4. Push docker image: `./upload_docker.sh`
```bash
# edit docker_password.txt (set your docker hub password)
# edit upload_docker.sh (set your dockerHubImage, dockerHubLogin)
chmod +x ./upload_docker.sh
./upload_docker.sh
```

5. Run in Kubernetes:  `./run_kubernetes.sh`
```bash
chmod +x ./run_kubernetes.sh
./run_kubernetes.sh 
kubectl logs -f  -lapp=microserviceproject --all-containers=true &> output_txt_files/kubernetes_out.txt &
```
6. Test predictions(after deploy): `./make_prediction.sh`
```bash
chmod +x ./make_prediction.sh 
./make_prediction.sh 
```
