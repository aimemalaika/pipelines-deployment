# Pipelines Deployment

This repository contains Tekton pipelines and Kubernetes manifests for deploying the **Budget App**. It includes configurations for both the frontend and backend services.

## Directory Structure

```
v1/
  deployment/
    deployment-backend.yaml       # Backend deployment configuration
    deployment-frontend.yaml      # Frontend deployment configuration
    route-backend.yaml            # Backend route configuration
    route-frontend.yaml           # Frontend route configuration
    service-backend.yaml          # Backend service configuration
    service-frontend.yaml         # Frontend service configuration
  deployment-secret/
    git-basic-auth.yaml           # Git authentication secret
  pipeline/
    deployment-pipeline.yaml      # Tekton pipeline definition
  pipeline-runner/
    back-end-pipelinerun-deployment.yaml  # Backend pipeline run
    front-end-pipelinerun-deployment.yaml # Frontend pipeline run
  pvc/
    deployment-shared-pvc.yaml    # Persistent Volume Claim for shared storage
  tekton-tasks/
    buildah.yaml                  # Buildah task definition
    git-clone.yaml                # Git clone task definition
v2/
  deployment/
    deployment-backend.yaml       # Backend deployment configuration
    deployment-frontend.yaml      # Frontend deployment configuration
    route-backend.yaml            # Backend route configuration
    route-frontend.yaml           # Frontend route configuration
    service-backend.yaml          # Backend service configuration
    service-frontend.yaml         # Frontend service configuration
  deployment-secret/
    git-basic-auth.yaml           # Git authentication secret
  pipeline/
    deployment-pipeline.yaml      # Tekton pipeline definition
  pipeline-runner/
    back-end-pipelinerun-deployment.yaml  # Backend pipeline run
    front-end-pipelinerun-deployment.yaml # Frontend pipeline run
  pvc/
    deployment-shared-pvc.yaml    # Persistent Volume Claim for shared storage
  tekton-tasks/
    buildah.yaml                  # Buildah task definition
    git-clone.yaml                # Git clone task definition
```

## Key Components

- **Tekton Pipelines**: Automates the deployment process for the Budget App.
- **Kubernetes Manifests**: Defines the deployment, service, and route configurations for the frontend and backend.
- **Secrets**: Stores sensitive information like Git credentials.
- **Persistent Volume Claims**: Provides shared storage for pipeline tasks.

## Pipeline Versions

- **v1**: Contains manually triggered pipelines. Users need to manually initiate the pipeline runs using the `PipelineRun` manifests.
- **v2**: Introduces automated pipelines. These pipelines are designed to be triggered automatically based on specific events, such as code commits or merges.

## How to Use

1. **Set Up Secrets**:
   - Update the `git-basic-auth.yaml` file with your GitHub username and token.

2. **Deploy the Pipeline**:
   - Apply the pipeline and tasks using `kubectl apply -f`.

3. **Run the Pipeline**:
   - For v1, trigger the pipeline runs using the `PipelineRun` manifests in the `pipeline-runner` directory.
   - For v2, ensure the automated triggers are configured correctly.

4. **Deploy the Application**:
   - Apply the deployment, service, and route manifests to deploy the frontend and backend.

## Notes

- Ensure that your Kubernetes cluster has Tekton installed.
- Update the image names and repository URLs in the manifests as needed.

## License

This project is licensed under the MIT License.