[![Circle CI](https://circleci.com/gh/Omarmmaher/project4-ml-microservice-kubernetes/.svg?style=svg&circle-token=cb6b266511edc298f9a105ebebaa5c3e0ecaf138)](https://app.circleci.com/pipelines/github/Omarmmaher/project4-ml-microservice-kubernetes?branch=main)

## Project Overview

In this project, you will apply the skills you have acquired in this course to operationalize a Machine Learning Microservice API. 

You are given a pre-trained, `sklearn` model that has been trained to predict housing prices in Boston according to several features, such as average rooms in a home and data about highway access, teacher-to-pupil ratios, and so on. You can read more about the data, which was initially taken from Kaggle, on [the data source site](https://www.kaggle.com/c/boston-housing). This project tests your ability to operationalize a Python flask app—in a provided file, `app.py`—that serves out predictions (inference) about housing prices through API calls. This project could be extended to any pre-trained machine learning model, such as those for image recognition and data labeling.

### Project Tasks

Your project goal is to operationalize this working, machine learning microservice using [kubernetes](https://kubernetes.io/), which is an open-source system for automating the management of containerized applications. In this project you will:
* Test your project code using linting
* Complete a Dockerfile to containerize this application
* Deploy your containerized application using Docker and make a prediction
* Improve the log statements in the source code for this application
* Configure Kubernetes and create a Kubernetes cluster
* Deploy a container using Kubernetes and make a prediction
* Upload a complete Github repo with CircleCI to indicate that your code has been tested

You can find a detailed [project rubric, here](https://review.udacity.com/#!/rubrics/2576/view).

**The final implementation of the project will showcase your abilities to operationalize production microservices.**

---

## Setup the Environment

* Create a virtualenv with Python 3.7 and activate it. Refer to this link for help on specifying the Python version in the virtualenv. 
```bash
python3 -m pip install --user virtualenv
# You should have Python 3.7 available in your host. 
# Check the Python path using `which python3`
# Use a command similar to this one:
python3 -m virtualenv --python=<path-to-Python3.7> .devops
source .devops/bin/activate
```
* Run `make install` to install the necessary dependencies

### Running `app.py`

1. Standalone:  `python app.py`
2. Run in Docker:  `./run_docker.sh`
3. Run in Kubernetes:  `./run_kubernetes.sh`

### Kubernetes Steps

* Setup and Configure Docker locally
* Setup and Configure Kubernetes locally
* Create Flask app in Container
* Run via kubectl
Complete the Dockerfile
Specify a working directory. Copy the app.py source code to that directory Install any dependencies in requirements.txt (do not delete the commented # hadolint ignore statement). Expose a port when the container is created; port 80 is standard. Specify that the app runs at container launch.

python3 -m venv ~/.devops source ~/.devops/bin/activate $ make lint

Run a Container & Make a Prediction Build the docker image from the Dockerfile; it is recommended that you use an optional --tag parameter as described in the build documentation. List the created docker images (for logging purposes). Run the containerized Flask app; publish the container’s port (80) to a host port (8080). Run the container using the run_docker.sh script created before following the steps above:
$ . ./run_docker.sh After running the container we can able to run the prediction using the make_prediction.sh script:

$ . ./make_prediction.sh

Improve Logging & Save Output Add a prediction log statement Run the container and make a prediction to check the logs
$ docker ps

CONTAINER ID IMAGE COMMAND CREATED STATUS PORTS NAMES a7d374ad73a6 api "/bin/bash" 36 minutes ago Exited (0) 28 minutes ago exciting_visvesvaraya 89fd55581a44 api "make run-app" 44 minutes ago Exited (2) 44 minutes ago brave_poitras f0b0ece5a9b5 api "make run-app" 46 minutes ago Exited (2) 46 minutes ago elated_brahmagupta a6fcd4749e44 api "make run-app" 48 minutes ago Exited (2) 48 minutes ago dreamy_agnesi

Upload the Docker Image Create a Docker Hub account Built the docker container with this command docker build --tag=<your_tag> . (Don't forget the tag name) Define a dockerpath which is <docker_hub_username>/<project_name> Authenticate and tag image Push your docker image to the dockerpath
After complete all steps run the upload using the upload_docker.sh script:

$ . ./upload_docker.sh

Configure Kubernetes to Run Locally Install Kubernetes Install Minikube

Deploy with Kubernetes and Save Output Logs Define a dockerpath which will be “/path”, this should be the same name as your uploaded repository (the same as in upload_docker.sh) Run the docker container with kubectl; you’ll have to specify the container and the port List the kubernetes pods Forward the container port to a host port, using the same ports as before

After complete all steps run the kubernetes using run_kubernetes.sh script:

$ . ./run_kubernetes.sh After running the kubernete make a prediction using the make_prediction.sh script as we do in the second task.

Delete Cluster minikube delete

CircleCI Integration To create the file and folder on GitHub, click the Create new file button on the repo page and type .circleci/config.yml. You should now have in front of you a blank config.yml file in a .circleci folder.

Then you can paste the text from this yaml file into your file, and commit the change to your repository.

It may help to reference this CircleCI blog post on Github integration.
