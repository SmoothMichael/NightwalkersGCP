# GCP ALine Jenkins CI/CD Pipeline 

Step 1: Setup GCLOUD CLI
https://cloud.google.com/sdk/docs/install-sdk

* AUTHENTICATE USING SMOOTHSTACK GMAIL


Step 2: Configure GClOUD CLI & Authorize Image / Helm Repositories

    `gcloud init`

    `gcloud auth configure-docker \
        us-east1-docker.pkg.dev`


Step 3: Create Project

    `export PROJECT_ID=<your-project-id>`

    `gcloud projects create $PROJECT_ID --name=$PROJECT_ID --set-as-default`


Step 4: Create Subnet and Cluster in Project VPC

    `gcloud container clusters create CLUSTER_NAME \
            --region=us-east1 \
            --enable-ip-alias \
            --create-subnetwork name=aline-cluster-subnet,range=10.5.0.0/20`

    `kubectl cluster-info`


Step 5: Push Images to Artifact Repository

(IMAGE NAME FORMAT: us-east--docker.pkg.dev/aline-jenkins-gcp/nightwalkers-images/your-image-name)

    `gcloud auth login`

    `docker tag <my-docker-image> us-east--docker.pkg.dev/aline-jenkins-gcp/nightwalkers-images/<your-image-name>`
