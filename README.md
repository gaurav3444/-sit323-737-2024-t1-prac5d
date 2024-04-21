# SIT323/SIT737: Cloud Native Application Development - 5.2D

This repository contains the code and instructions for publishing a microservice to a private container registry on Google Cloud Platform (GCP).

## Instructions:

### 1. Create a Private Container Registry (One-Time Setup):

- Go to the [GCP Console](https://console.cloud.google.com/).
- Navigate to Artifact Registry.
- Click **Create Repository**.
- Choose a name for your repository (e.g., `sit323-737-registry`).
- Select the region closest to your development environment.
- Click **Create**.

### 2. Authenticate with the Registry:

- Open a terminal window.
- Run the following command, replacing `<PROJECT_ID>` with your GCP project ID:

    ```bash
    docker login -u _json_key -p "$(gcloud auth print-json-key)" https://<PROJECT_ID>.artifacts.docker.io
    ```

### 3. Build and Tag Your Docker Image (Assuming Dockerfile exists):

- Navigate to your microservice directory containing the Dockerfile.
- Build the image using the following command (replace `<image-name>` with your desired name):

    ```bash
    docker build -t <PROJECT_ID>.artifacts.docker.io/<repository-name>:<tag> .
    ```

    - `<repository-name>` is the name you chose for your registry (e.g., `sit323-737-registry`).
    - `<tag>` can be a version number (e.g., `v1.0`).

### 4. Push the Image to the Registry:

- Push the built image to your private registry using:

    ```bash
    docker push <PROJECT_ID>.artifacts.docker.io/<repository-name>:<tag>
    ```

### 5. Verify the Image:

- You can verify if the image is accessible by running:

    ```bash
    docker run <PROJECT_ID>.artifacts.docker.io/<repository-name>:<tag>
    ```
