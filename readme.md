# Preparation

1. Install AWS CLI and configure your AWS credentials.
2. Install and configure kubectl for managing Kubernetes clusters.

3. Install and configure AWS eksctl for managing EKS clusters.

On Mac:
```bash
brew tap weaveworks/tap
brew install weaveworks/tap/eksctl
```

# Create repository

```bash
aws ecr create-repository --repository-name le-export
```

# Create EKS Cluster

```bash
eksctl create cluster -f cluster.yml
```

# Getting fresh kubeconfig.yaml

```bash
eksctl utils write-kubeconfig --cluster le-production-5
```

or 

```bash
aws eks --region us-east-1 update-kubeconfig --name le-production-5
```

# Apply the deployment

```bash
kubectl apply -f deployment.yaml
```

# Accesing pods

```bash
export KUBECONFIG=$(pwd)/kubeconfig.yaml
kubectl cluster-info
```

# Deleting resources

```bash
eksctl delete cluster -f cluster.yml
```

# Additional setup

