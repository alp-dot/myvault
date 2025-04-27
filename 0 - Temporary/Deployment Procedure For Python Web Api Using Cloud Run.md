---
created: 2025-02-15
tags: 
description: 
reference: https://youtu.be/02TrOBYrJkU?si=K2NqWBkn9qWotV5n
---
**1. Local Environment Preparation**

- Creating a Flask Application
    - When using Cloud Run, you need to configure the application to get the port number from the environment variable `PORT`.
- Creating a Dockerfile
    - Create a `Dockerfile` file and describe the Docker image build procedure.
    - Use a Python base image and install the necessary packages.
    - Copy the application code to the image and grant execution permissions.
    - Configure the application to start on `PORT` 8080.
- Building the Docker Image
    - Use the `docker build` command to build the Docker image.
    - Use the `-t` option to tag the image.
- Verifying Operation in the Local Environment
    - Use the `docker run` command to start the Docker container.
    - Configure port forwarding with the `-p` option to make it accessible from the local machine.
    - Access the API endpoint in a web browser to verify its operation.

**2. Deploying to Cloud Run**

- Creating a Google Cloud Project
    - Create a new project in the Google Cloud Platform console.
- Enabling the Cloud Run API
    - Enable the Cloud Run API in your project.
- Installing and Authenticating the Cloud SDK
    - Install the Cloud SDK on your local machine.
    - Run the `gcloud init` command to authenticate the Cloud SDK.
- Deploying to Cloud Run
    - Use the `gcloud run deploy` command to deploy the Docker image to Cloud Run.
    - Specify the Docker image path with the `--source` option.
    - Specify the `--platform-managed` option.
    - Specify the `--allow-unauthenticated` option to allow access to the API without authentication.
- Verifying the Deployment
    - After the deployment is complete, check the service URL in the Cloud Run console.
    - Access the service URL in a web browser to verify that the API is working.

**Reference Materials**

- Cloud Run Documentation: [https://cloud.google.com/run/docs](https://cloud.google.com/run/docs)
- Flask Documentation: [https://flask.palletsprojects.com/en/latest/](https://flask.palletsprojects.com/en/latest/)
- Docker Documentation: [https://docs.docker.com/](https://docs.docker.com/)
- k6 Documentation: [https://k6.io/docs/](https://k6.io/docs/) 