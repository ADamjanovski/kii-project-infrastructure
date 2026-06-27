# Desired Deployment Flow

1. Developers push code to the application repository.
2. GitHub Actions runs lint and tests.
3. GitHub Actions builds backend and frontend images and pushes them to DockerHub with immutable SHA tags.
4. GitHub Actions clones the infrastructure repository and updates the Helm values file with the new image tags.
5. GitHub Actions commits and pushes that infrastructure change.
6. Argo CD detects the Git change in the infrastructure repository.
7. Argo CD syncs the Helm chart and Kubernetes resources to the cluster.
8. Kubernetes rolls out new application pods on the worker nodes.

