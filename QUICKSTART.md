# Quick Start Guide: Kubernetes AI Landscape

This guide will help you get started with deploying AI/ML workloads on Kubernetes using the tools and frameworks from our landscape.

## Prerequisites

Before you begin, ensure you have:

- A Kubernetes cluster (v1.20+) running
- `kubectl` configured to access your cluster
- At least 8GB RAM and 4 CPU cores available
- Basic familiarity with containers and Kubernetes concepts

## Scenario 1: Complete MLOps Platform with Kubeflow

**Best for**: Teams wanting a comprehensive, all-in-one ML platform

### 1. Deploy Kubeflow

```bash
# Install kfctl
export PLATFORM=linux # or darwin for macOS
export KF_VERSION=1.4.0
wget "https://github.com/kubeflow/kfctl/releases/download/v${KF_VERSION}/kfctl_v${KF_VERSION}-0-gbc038f9_${PLATFORM}.tar.gz"
tar -xvf kfctl_v${KF_VERSION}-0-gbc038f9_${PLATFORM}.tar.gz
sudo mv kfctl /usr/local/bin/

# Deploy Kubeflow
export KF_NAME=kubeflow
export BASE_DIR=${HOME}
export KF_DIR=${BASE_DIR}/${KF_NAME}
export CONFIG_URI="https://raw.githubusercontent.com/kubeflow/manifests/v1.4-branch/kfdef/kfctl_k8s_istio.v1.4.0.yaml"

mkdir -p ${KF_DIR}
cd ${KF_DIR}
kfctl apply -V -f ${CONFIG_URI}
```

### 2. Access Kubeflow Dashboard

```bash
kubectl port-forward -n istio-system svc/istio-ingressgateway 8080:80
# Open http://localhost:8080 in your browser
```

### 3. What You Get

- **Jupyter Notebooks**: Interactive development environment
- **Kubeflow Pipelines**: ML workflow orchestration
- **Katib**: Automated hyperparameter tuning
- **KServe**: Model serving and inference
- **Central Dashboard**: Unified interface

## Scenario 2: Lightweight Model Serving with KServe

**Best for**: Teams focused primarily on model deployment and serving

### 1. Install KServe

```bash
# Install KServe
kubectl apply -f https://github.com/kserve/kserve/releases/download/v0.8.0/kserve.yaml

# Wait for installation to complete
kubectl wait --for=condition=ready pod -l control-plane=kserve-controller-manager -n kserve-system --timeout=300s
```

### 2. Deploy Your First Model

Create a file `sklearn-iris.yaml`:

```yaml
apiVersion: "serving.kserve.io/v1beta1"
kind: "InferenceService"
metadata:
  name: "sklearn-iris"
spec:
  predictor:
    sklearn:
      storageUri: "gs://kfserving-examples/models/sklearn/1.0/model"
```

Deploy the model:

```bash
kubectl apply -f sklearn-iris.yaml

# Check status
kubectl get inferenceservice sklearn-iris
```

### 3. Test the Model

```bash
# Get the model URL
kubectl get inferenceservice sklearn-iris -o jsonpath='{.status.url}'

# Test prediction (replace URL with your model's URL)
curl -v -H "Content-Type: application/json" \
  -d '{"instances": [[6.8, 2.8, 4.8, 1.4], [6.0, 3.4, 4.5, 1.6]]}' \
  http://sklearn-iris.default.example.com/v1/models/sklearn-iris:predict
```

## Scenario 3: Workflow Orchestration with Argo Workflows

**Best for**: Teams needing flexible, general-purpose workflow management

### 1. Install Argo Workflows

```bash
kubectl create namespace argo
kubectl apply -n argo -f https://github.com/argoproj/argo-workflows/releases/download/v3.4.4/install.yaml
```

### 2. Create a Simple ML Pipeline

Create `ml-pipeline.yaml`:

```yaml
apiVersion: argoproj.io/v1alpha1
kind: Workflow
metadata:
  generateName: ml-pipeline-
spec:
  entrypoint: ml-pipeline
  templates:
  - name: ml-pipeline
    dag:
      tasks:
      - name: data-preprocessing
        template: data-prep
      - name: model-training
        template: train-model
        dependencies: [data-preprocessing]
      - name: model-evaluation
        template: evaluate-model
        dependencies: [model-training]
  
  - name: data-prep
    container:
      image: python:3.8
      command: [python]
      args: ["-c", "print('Data preprocessing completed')"]
  
  - name: train-model
    container:
      image: python:3.8
      command: [python]
      args: ["-c", "print('Model training completed')"]
  
  - name: evaluate-model
    container:
      image: python:3.8
      command: [python]
      args: ["-c", "print('Model evaluation completed')"]
```

### 3. Run the Pipeline

```bash
argo submit -n argo ml-pipeline.yaml
argo list -n argo
argo logs -n argo @latest
```

## Scenario 4: Monitoring with Prometheus & Grafana

**Best for**: Teams needing comprehensive monitoring and observability

### 1. Install Prometheus Operator

```bash
# Add Prometheus community helm repo
helm repo add prometheus-community https://prometheus-community.github.io/helm-charts
helm repo update

# Install kube-prometheus-stack
helm install prometheus prometheus-community/kube-prometheus-stack \
  --namespace monitoring \
  --create-namespace
```

### 2. Access Grafana Dashboard

```bash
# Get Grafana admin password
kubectl get secret --namespace monitoring prometheus-grafana -o jsonpath="{.data.admin-password}" | base64 --decode ; echo

# Port forward to access Grafana
kubectl port-forward --namespace monitoring svc/prometheus-grafana 3000:80
# Access at http://localhost:3000 (admin/password-from-above)
```

### 3. What You Get

- **Prometheus**: Metrics collection and storage
- **Grafana**: Visualization dashboards
- **AlertManager**: Alert routing and management
- **Node Exporter**: Hardware metrics
- **Kube State Metrics**: Kubernetes object metrics

## Best Practices

### Resource Management

```yaml
# Always set resource requests and limits
resources:
  requests:
    memory: "64Mi"
    cpu: "250m"
    nvidia.com/gpu: 1
  limits:
    memory: "128Mi"
    cpu: "500m"
    nvidia.com/gpu: 1
```

### Security

```yaml
# Use security contexts
securityContext:
  runAsNonRoot: true
  runAsUser: 1000
  allowPrivilegeEscalation: false
  readOnlyRootFilesystem: true
```

### Storage

```yaml
# Use persistent volumes for data
volumeMounts:
- name: data-storage
  mountPath: /data
volumes:
- name: data-storage
  persistentVolumeClaim:
    claimName: ml-data-pvc
```

## Common Issues & Solutions

### Issue: Pods stuck in Pending state
**Solution**: Check resource requirements and node capacity
```bash
kubectl describe node <node-name>
kubectl describe pod <pod-name>
```

### Issue: Image pull errors
**Solution**: Verify image name and registry access
```bash
kubectl describe pod <pod-name>
# Check events section for specific error
```

### Issue: GPU not detected
**Solution**: Ensure GPU operator is installed
```bash
kubectl get nodes -o yaml | grep nvidia.com/gpu
```

## Next Steps

1. **Explore the tools**: Try different combinations based on your needs
2. **Join the community**: Connect with other practitioners
3. **Contribute**: Share your experiences and tools
4. **Scale up**: Move from experimentation to production

## Useful Commands

```bash
# Monitor resource usage
kubectl top nodes
kubectl top pods --all-namespaces

# Debug pods
kubectl logs <pod-name> -f
kubectl exec -it <pod-name> -- /bin/bash

# Check cluster info
kubectl cluster-info
kubectl get nodes -o wide
```

## Learning Resources

- [Kubernetes Documentation](https://kubernetes.io/docs/)
- [Kubeflow Tutorials](https://www.kubeflow.org/docs/started/getting-started/)
- [MLOps Best Practices](https://ml-ops.org/)
- [CNCF AI/ML Landscape](https://landscape.cncf.io/)

---

**Need Help?**

- ? Check our [main documentation](../README.md)
- ? Join our [community discussions](https://github.com/collabnix/kubernetes-ai-landscape/discussions)
- ? Report issues in our [issue tracker](https://github.com/collabnix/kubernetes-ai-landscape/issues)
- ? Connect on [Slack](http://collabnix.com/slack)
