# MLOps-Project-for-a-Mask-R-CNN-on-GCP-using-uWSGI-Flask

## Business Overview
87% of Data Science Projects never make it to production - VentureBeat
Machine learning operations are widely known as MLOps include various technologies,
processes, and practices that automate deployment, monitoring, and management of
machine learning models in production. Many organizations are turning towards
machine learning and Artificial intelligence. MLOps advocates automation and
monitoring at all steps of the ML system. In this project, we aim to provide hands-on
experience in MLOps by using cloud computing. Google cloud platform is used as a
cloud provider. We would advise you to have a basic understanding of Image
Segmentation using Mask R-CNN with Tensorflow before jumping into this project.

## Aim
To provide an end-to-end machine learning development process to design, build and
manage reproducible, testable, and evolvable machine learning models by using
Google Cloud Platform(GCP)
Tech Stack
➔ Language: Python
➔ Services: GCP, uWSGI, Flask, Kubernetes, Docker
➔ Libraries: TensorFlow, mrcnn, matplotlib, os, flask
## Approach
The repository contains the code files involved in creating an automated MLOps
Pipeline on GCP (Google Cloud Platform).
Steps:
● Clone the repository
● Place your model H5 file inside the Models folder
● Change the model file name in Inference.py file at line number 40
Once you made the changes, create a new repository and commit the changes. From
here on, this will be your source repository. Proceed with the below steps
CLOUD BUILD TRIGGER
● In your GCP console, create a new cloud build trigger.
● Point the trigger to your source repository
GOOGLE KUBERNETES ENGINE (GKE)
● From the console launch a Kubernetes cluster
● Connect to the cluster and create the following two files
● deployment.yaml
● service.yaml
● Copy the code for both files from "Kubernetes Files" folder in the cloned
## repository
● Execute the following commands
○ kubectl apply -f deployment.yaml
○ kubectl apply -f service.yaml
● Get the name of the deployment with the following command
○ kubectl get deployments
CLOUD PUB/SUB
● Create a Pub/Sub topic with the name cloud-build
● Provide a subscription for the topic, which is to trigger a cloud function
CLOUD FUNCTIONS
● From Pub/Sub console launch the cloud function window
● Provide the following Environment variables through the GUI console
○ PROJECT (project name)
○ ZONE (Region in which the project is deployed ex.uscentral-1)
○ CLUSTER (Name of the Kubernetes cluster created earlier)
○ DEPLOYMENT (Name of the deployment inside the Kubernetes cluster)
● Copy the program code and requirements.txt files for the cloud function from
cloud-function-trigger folder
● Configure the Entrypoint for the cloud function as onNewImage
● Deploy the function
After successful deployment, make a commit to the source repository and the following
will happen in sequence
Cloud Build will push message to Pub/Sub upon successful build
Pub/Sub will trigger the cloud function
Cloud function will deploy the new image on Kubernetes
To test the deployment, check the logs on Kubernetes cluster using the following
command
● kubectl get pods
● kubectl logs <pod name>
The deployment will reflect in the logs as well as in the endpoints
Files Description
1. Kubernetes files: this folder contains all the required files to trigger Kubernetes
2. Cloud-function-trigger: this folder contains files for cloud function
3. Dockerfile: The docker image
4. Inference.py: file to load model and provide the output
5. __init__.py: required empty file
6. Main.py: file to host Flask API
7. Requirements.txt: all the required libraries
8. Uwsgi.ini: uWSGI configuration file
Project Takeaways
1. MLOps Architecture
2. Google Cloud Platform(GCP) based MLops architecture
3. Understanding various model files required for MLops
4. Understanding various components of GCP
5. How to create a cloud source repository in CGP and its structure
6. How to clone the git repository with the source repository
7. How to commit changes in the source repository
8. How to create a trigger fire repository
9. Flask deployment
10.Basics of uWSGI
11. How to create a uWSGI configuration file
12.Building Docker image
13.Cloud build
14.How to use cloud shell editor
15.Kubernetes architecture
16.Understanding files required for Kubernetes
17.Pub/Sub and creating a topic in it
18.Cloud function
19.How to trigger cloud function
20.Model deployment using Kubernetes
