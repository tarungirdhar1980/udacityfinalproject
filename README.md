# udacityfinalproject

Udacity Capstone Project1

Screenshots for various steps have been added to screenshots directory

setup
This project uses rolling update strategy and deploy ML application.

successfull capstone deployment

https://app.circleci.com/pipelines/github/tarungirdhar1980/udacityfinalproject/70/workflows/32361fc5-4cb6-4158-a341-0acd07ce9779

markdown status

https://circleci.com/gh/tarungirdhar1980/udacityfinalproject.svg?style=svg&circle-token=32361fc5-4cb6-4158-a341-0acd07ce9779

In this project, you will apply the skills you have acquired in this course to operationalize a Machine Learning Microservice API.

You are given a pre-trained, sklearn model that has been trained to predict housing prices in Boston according to several features, such as average rooms in a home and data about highway access, teacher-to-pupil ratios, and so on. You can read more about the data, which was initially taken from Kaggle, on the data source site. This project tests your ability to operationalize a Python flask app—in a provided file, app.py—that serves out predictions (inference) about housing prices through API calls. This project could be extended to any pre-trained machine learning model, such as those for image recognition and data labeling.

###########################

Setup the Environment
###########################

Following steps must be executed to setup environment from user's local machine. #Build code -Initialize the Python virtual environment: make setup

Install necessary dependencies for build: make install-for-build
Test the project's code using linting: make lint
Lints shell scripts, Dockerfile and python code
Create a Dockerfile to "containerize" the application: make build-docker
Deploy the containerized application to a public Docker Registry -Docker Hub : make upload-docker
#Deploy Code

Install necessary dependencies for build: make install-for-k8s
Deploy a Kubernetes cluster: make eks-create-cluster
Deploy the application: make kubernetes-deployment
Update the app in the cluster, using a rolling-update strategy: make rolling-update
Delete the cluster: make eks-delete-cluster
#The CirclCI pipeline(config.yml) will execute the following steps automatically:

make setup
make install-for-build
make lint
Build and publish the container image #For first time
Create kubernetes cluster on AWS EKS
create kubernetes deployment and deploy application containers with image pulled from dockerhub.
#For upgrades Perform rolling update on the cluster

#######################

Running app.py
#######################

Standalone: python app.py
Run in Docker: ./run_docker.sh
Run in Kubernetes: ./run_kubernetes.sh
#############################

Testing the application
#############################

Standalone / Local K8 cluster:

Run: 'make_prediction.sh
AWS EKS K8 cluster:

Run: aws eks --region $AWS_DEFAULT_REGION update-kubeconfig --name <CLUSTER_NAME>
Run: 'make_prediction.sh
File Details
app.py: Python script that invokes machine learning model to predict housing prices.
dockerfile: Helps genrate container image of the application
makefile: Python contruct that can hol set of frequently used commands like for env setup, installtion of dependencies, testing etc.
requirements.txt: Dependencies that are required by application in the environment.
run_docker.sh: Shell script containing commands for creating docker image build for application.
run_keberentes.sh: Runs commands for application image deployment using kubernetes.
upload_docker.sh: Runs commands to to upload docker image to docker hub repository.
make predictions.sh: Runs curl command with input JSon for making price predictions with application.
install_eksctl.sh : Installs eksctl utility.
build_docker.sh: Builds docker image.
install_kubectl.sh: Installs kubectl utility
eks_create_cluster.sh: Checks and creates AWS EKS Kubernetes cluster if does not already exist.
config_cluster.yaml: Contains configuration for cluster creation.
.circleci/config.yml: Contains config for CircleCI CI/CD Pipeline.
