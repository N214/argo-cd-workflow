Argo suite test

This test include Argo CD, Argo Event and Argo Workflow.

## Instruction
- Create local k8s cluster with kind

- Install Argo CD

```sh
helm repo add argo https://argoproj.github.io/argo-helm
helm upgrade --install my-argo-cd argo/argo-cd --version 7.7.3 \
    --set configs.params."applicationsetcontroller\.enable\.progressive\.syncs"=true \
    --set configs.cm."timeout\.reconciliation"="30s"
```

- Install Argo Workflow

```sh
ARGO_WORKFLOWS_VERSION="v3.6.0"
kubectl apply -n argo -f "https://github.com/argoproj/argo-workflows/releases/download/${ARGO_WORKFLOWS_VERSION}/quick-start-minimal.yaml"
```

- Install Argo event

### App project
### Applicationset