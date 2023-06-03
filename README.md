# Python Resource Monitoring  App on K8s

Application to monitor computer resource utilization. Application is containerized using Docker and deployed on AWS EKS cluster using Python.

    Application built in Python using Flask and psutil
    Docker to containerize a Python application
        Creating Dockerfile
        Building Docker Image
        Running Docker Container
        Docker Commands
    AWS ECR repository and pushing Docker Image to ECR
    Kubernetes and AWS EKS cluster and Nodegroups
    Kubernetes Deployments and Services using Python


## Prerequisites

- AWS Account
- Programmatic access and AWS configured with CLI
- Python3 Installed
- Docker and Kubectl installed
- Code editor/IDE (PyCharm)

## **Part 1: Deploying the Flask application locally**

### **Step 1: Clone the code**

Clone the code from the repository:

$ git clone <repository_url>


### **Step 2: Install dependencies**

The application uses the **`psutil`**, **`Flask`**, and **`Plotly`** libraries. Install them using pip:

pip3 install -r requirements.txt


### **Step 3: Run the application**

To run the application, navigate to the root directory of the project and execute the following command:

$ python app.py


This will start the Flask server on **`localhost:5000`**. Navigate to [http://localhost:5000/](http://localhost:5000/) on your browser to access the application.

## **Part 2: Dockerizing the Flask application**

### **Step 1: Create a Dockerfile**

Create a **`Dockerfile`** in the root directory of the project.


### **Step 2: Build the Docker image**

Build the Docker image, executing the following command:

$ docker build -t <image_name> .


### **Step 3: Run the Docker container**

Run the Docker container, executing the following command:

$ docker run -p 5000:5000 <image_name>


This will start the Flask server in a Docker container on **`localhost:5000`**. Navigate to [http://localhost:5000/](http://localhost:5000/) on your browser to access the application.

## **Part 3: Pushing the Docker image to AWS ECR**

### **Step 1: Create an ECR repository**

Create an ECR repository. 


### **Step 2: Push the Docker image to ECR**

Push the Docker image to AWS ECR using the push commands on the console:

$ docker push <ecr_repo_uri>:


## **Part 4: Creating an AWS EKS cluster and deploying the app using Python**

### **Step 1: Create an EKS cluster**

Create an EKS cluster and add node group

### **Step 2: Create a node group**

Create a node group in the EKS cluster.

### **Step 3: Create deployment and service**

- Edit the name of the image on line 26 of the eks.py file with your image Uri.
- Once you run this file by running “python eks.py” on the terminal, deployment and service will be created.
- Check if application is running by running following commands:

    - kubectl get deployment -n default (check deployments)
    - kubectl get service -n default (check service)
    - kubectl get pods -n default (to check the pods)
    - kubectl get svc -n default (to check the service)

- Once your pod is up and running, run the port-forward to expose the service

    - kubectl port-forward svc/<service_name> 5000:5000