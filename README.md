# Kubernetes AI Landscape ??

A comprehensive collection of AI/ML tools, frameworks, and resources in the Kubernetes ecosystem for building, deploying, and managing machine learning workloads at scale.

[![GitHub stars](https://img.shields.io/github/stars/collabnix/kubernetes-ai-landscape.svg)](https://github.com/collabnix/kubernetes-ai-landscape/stargazers)
[![GitHub forks](https://img.shields.io/github/forks/collabnix/kubernetes-ai-landscape.svg)](https://github.com/collabnix/kubernetes-ai-landscape/network)
[![GitHub issues](https://img.shields.io/github/issues/collabnix/kubernetes-ai-landscape.svg)](https://github.com/collabnix/kubernetes-ai-landscape/issues)
[![License](https://img.shields.io/badge/license-MIT-blue.svg)](LICENSE)

## ? Table of Contents

- [Overview](#overview)
- [MLOps Platforms](#mlops-platforms)
- [Model Serving & Inference](#model-serving--inference)
- [Workflow Orchestration](#workflow-orchestration)
- [Training & Experimentation](#training--experimentation)
- [Data Processing & Pipelines](#data-processing--pipelines)
- [Monitoring & Observability](#monitoring--observability)
- [GPU & Resource Management](#gpu--resource-management)
- [Development & Notebooks](#development--notebooks)
- [? MCP Servers for Kubernetes](MCP-SERVERS.md)
- [Security & Compliance](#security--compliance)
- [Commercial & Managed Solutions](#commercial--managed-solutions)
- [Getting Started](#getting-started)
- [Contributing](#contributing)
- [Community](#community)

## Overview

Kubernetes has become the de facto standard for orchestrating AI/ML workloads, providing scalability, portability, and robust resource management for machine learning operations. This repository catalogs the essential tools and frameworks that power the Kubernetes AI ecosystem.

### Why Kubernetes for AI/ML?

- **Scalability**: Dynamic scaling of ML workloads based on demand
- **Portability**: Deploy anywhere Kubernetes runs (cloud, on-premise, edge)
- **Resource Management**: Efficient GPU/CPU allocation and optimization
- **Containerization**: Consistent environments from development to production
- **Automation**: GitOps and CI/CD integration for ML pipelines

## MLOps Platforms

Comprehensive platforms for end-to-end machine learning lifecycle management.

| Tool | Description | Category | License | GitHub Stars | Key Features |
|------|-------------|----------|---------|--------------|--------------|
| [Kubeflow](https://kubeflow.org/) | Complete ML platform for Kubernetes with pipelines, notebooks, and model serving | End-to-End MLOps | Apache 2.0 | 14k+ | Pipelines, Notebooks, Katib, KServe, Multi-framework support |
| [MLflow](https://mlflow.org/) | Open source platform for ML lifecycle management | Experiment Tracking | Apache 2.0 | 18k+ | Tracking, Projects, Models, Registry, Deployment |
| [ZenML](https://zenml.io/) | Extensible open-source MLOps framework for reproducible pipelines | MLOps Framework | Apache 2.0 | 4k+ | Pipeline orchestration, Model deployment, Stack management |
| [Metaflow](https://metaflow.org/) | Human-friendly library for data science projects | Data Science Platform | Apache 2.0 | 8k+ | Versioning, Scaling, Deployment, Human-centric design |

## Model Serving & Inference

Tools for deploying and serving ML models in production environments.

| Tool | Description | Category | License | GitHub Stars | Supported Frameworks |
|------|-------------|----------|---------|--------------|---------------------|
| [KServe](https://kserve.github.io/) | Kubernetes-native serverless ML inference platform | Model Serving | Apache 2.0 | 5.5k+ | TensorFlow, PyTorch, XGBoost, SKLearn, ONNX, Hugging Face |
| [Seldon Core](https://www.seldon.io/) | ML deployment platform for Kubernetes with advanced features | Model Serving | BSL 1.1 | 4k+ | SKLearn, XGBoost, SparkML, Custom models |
| [Ray Serve](https://docs.ray.io/en/latest/serve/) | Scalable model serving library with Python-first approach | Model Serving | Apache 2.0 | 33k+ | Any Python framework, PyTorch, TensorFlow, SKLearn |
| [TensorFlow Serving](https://www.tensorflow.org/tfx/serving) | Production ML model serving system for TensorFlow | Model Serving | Apache 2.0 | 6k+ | TensorFlow, TensorFlow Lite |
| [TorchServe](https://pytorch.org/serve/) | PyTorch model serving framework | Model Serving | Apache 2.0 | 4k+ | PyTorch, TorchScript, ONNX |
| [Triton Inference Server](https://developer.nvidia.com/triton-inference-server) | NVIDIA's inference serving software | Model Serving | BSD 3-Clause | 8k+ | TensorFlow, PyTorch, ONNX, TensorRT, Custom backends |
| [BentoML](https://bentoml.com/) | Framework for building ML services | Model Serving | Apache 2.0 | 7k+ | All Python ML frameworks |

## Workflow Orchestration

Tools for managing and orchestrating ML pipelines and workflows.

| Tool | Description | Category | License | GitHub Stars | Key Capabilities |
|------|-------------|----------|---------|--------------|------------------|
| [Argo Workflows](https://argoproj.github.io/workflows/) | Container-native workflow engine for Kubernetes | Workflow Orchestration | Apache 2.0 | 15k+ | DAG workflows, Parallel execution, Artifact management |
| [Apache Airflow](https://airflow.apache.org/) | Platform for workflow orchestration and scheduling | Workflow Orchestration | Apache 2.0 | 36k+ | Python DAGs, Rich UI, Extensive integrations |
| [Tekton](https://tekton.dev/) | Cloud-native CI/CD pipeline framework | CI/CD Pipelines | Apache 2.0 | 8k+ | Kubernetes-native, Reusable tasks, GitOps |
| [Kubeflow Pipelines](https://www.kubeflow.org/docs/components/pipelines/) | ML workflow orchestration platform | ML Pipelines | Apache 2.0 | Part of Kubeflow | ML-specific, Component reuse, Experiment tracking |
| [Prefect](https://prefect.io/) | Modern workflow orchestration platform | Workflow Management | Apache 2.0 | 16k+ | Python-native, Dynamic workflows, Error handling |

## Training & Experimentation

Frameworks and tools for distributed training and hyperparameter optimization.

| Tool | Description | Category | License | GitHub Stars | Training Support |
|------|-------------|----------|---------|--------------|------------------|
| [Katib](https://www.kubeflow.org/docs/components/katib/) | Kubernetes-native hyperparameter tuning | Hyperparameter Tuning | Apache 2.0 | Part of Kubeflow | AutoML, NAS, Multi-objective optimization |
| [Ray](https://ray.io/) | Distributed computing framework for ML | Distributed Training | Apache 2.0 | 33k+ | Distributed training, Hyperparameter tuning, Reinforcement learning |
| [Horovod](https://horovod.ai/) | Distributed deep learning training framework | Distributed Training | Apache 2.0 | 14k+ | TensorFlow, PyTorch, MXNet, Multi-GPU/Multi-node |
| [PyTorch Lightning](https://lightning.ai/) | High-level interface for PyTorch | Training Framework | Apache 2.0 | 28k+ | Scalable training, Multi-GPU, TPU support |
| [TensorFlow Extended (TFX)](https://www.tensorflow.org/tfx) | End-to-end ML platform for TensorFlow | ML Platform | Apache 2.0 | 2k+ | Data validation, Transform, Training, Serving |

## Data Processing & Pipelines

Tools for data ingestion, processing, and pipeline management.

| Tool | Description | Category | License | GitHub Stars | Data Support |
|------|-------------|----------|---------|--------------|--------------|
| [Apache Spark](https://spark.apache.org/) | Unified analytics engine for big data processing | Data Processing | Apache 2.0 | 39k+ | Batch, Streaming, ML, SQL, Graph processing |
| [Dask](https://dask.org/) | Parallel computing library for Python | Data Processing | BSD 3-Clause | 12k+ | Pandas, NumPy, Scikit-learn scaling |
| [Flyte](https://flyte.org/) | Cloud-native workflow automation platform | Data Orchestration | Apache 2.0 | 5k+ | Type-safe pipelines, Versioning, Multi-cloud |
| [Pachyderm](https://pachyderm.com/) | Data versioning and pipelines for ML | Data Versioning | Apache 2.0 | 6k+ | Git-like data versioning, Pipeline automation |
| [DVC](https://dvc.org/) | Data version control for ML projects | Data Versioning | Apache 2.0 | 13k+ | Git integration, Experiment tracking, Model management |

## Monitoring & Observability

Tools for monitoring ML models and infrastructure performance.

| Tool | Description | Category | License | GitHub Stars | Monitoring Features |
|------|-------------|----------|---------|--------------|-------------------|
| [Prometheus](https://prometheus.io/) | Monitoring and alerting toolkit | Infrastructure Monitoring | Apache 2.0 | 55k+ | Metrics collection, Alerting, Time-series DB |
| [Grafana](https://grafana.com/) | Observability and monitoring platform | Visualization | AGPL 3.0 | 62k+ | Dashboards, Alerting, Multi-datasource |
| [TensorBoard](https://www.tensorflow.org/tensorboard) | Visualization toolkit for ML experiments | ML Monitoring | Apache 2.0 | Part of TF | Metrics visualization, Model graphs, Profiling |
| [MLRun](https://mlrun.org/) | Open MLOps platform for managing ML lifecycle | MLOps Monitoring | Apache 2.0 | 1.4k+ | Experiment tracking, Model monitoring, Feature store |
| [Evidently](https://evidentlyai.com/) | ML model monitoring and data drift detection | Model Monitoring | Apache 2.0 | 5k+ | Data drift, Model performance, Interactive reports |

## GPU & Resource Management

Specialized tools for GPU scheduling and resource optimization.

| Tool | Description | Category | License | GitHub Stars | GPU Features |
|------|-------------|----------|---------|--------------|--------------|
| [NVIDIA GPU Operator](https://github.com/NVIDIA/gpu-operator) | GPU resource management for Kubernetes | GPU Management | Apache 2.0 | 1.8k+ | Automated GPU setup, Driver management, Monitoring |
| [Volcano](https://volcano.sh/) | Batch system for high-performance workloads | Batch Scheduling | Apache 2.0 | 4k+ | Gang scheduling, GPU affinity, Queue management |
| [Yunikorn](https://yunikorn.apache.org/) | Resource scheduler for big data and ML workloads | Resource Scheduling | Apache 2.0 | 400+ | Multi-tenant, Resource quotas, Preemption |
| [NVIDIA Run:ai](https://run.ai/) | GPU orchestration platform | GPU Orchestration | Commercial | N/A | Dynamic GPU allocation, Workload management, Multi-tenancy |

## Development & Notebooks

Interactive development environments and notebook platforms.

| Tool | Description | Category | License | GitHub Stars | IDE Support |
|------|-------------|----------|---------|--------------|-------------|
| [JupyterHub](https://jupyter.org/hub) | Multi-user notebook server | Notebook Platform | BSD 3-Clause | 8k+ | Jupyter notebooks, Multi-user, Spawners |
| [Kubeflow Notebooks](https://www.kubeflow.org/docs/components/notebooks/) | Jupyter notebooks in Kubernetes | ML Notebooks | Apache 2.0 | Part of Kubeflow | Pre-configured images, Volume support, RBAC |
| [Code Server](https://coder.com/) | VS Code in the browser | Cloud IDE | MIT | 67k+ | VS Code, Remote development, Extensions |
| [Kale](https://github.com/kubeflow-kale/kale) | Convert Jupyter notebooks to Kubeflow pipelines | Notebook Automation | Apache 2.0 | 600+ | Notebook to pipeline, Auto-annotation, Katib integration |

## ? MCP Servers for Kubernetes

Model Context Protocol (MCP) servers enable AI assistants to interact with Kubernetes clusters through standardized interfaces. **[? View Complete MCP Servers Guide](MCP-SERVERS.md)**

### Popular Kubernetes MCP Servers

| Tool | Description | Language | Key Features |
|------|-------------|----------|--------------|
| [kubernetes-mcp-server](https://github.com/manusa/kubernetes-mcp-server) | Native Kubernetes/OpenShift MCP server | Go | Cross-platform binaries, Helm support, OpenShift support |
| [mcp-k8s-go](https://github.com/strowk/mcp-k8s-go) | Lightweight extensible Kubernetes MCP server | Go | Pod logs, Events, Namespaces, Extensible architecture |
| [k8s-multicluster-mcp](https://github.com/razvanmacovei/k8s-multicluster-mcp) | Multi-cluster Kubernetes operations | Python | Multi-cluster support, Context switching |

### Quick Start with MCP

```bash
# Install the recommended MCP server
npx kubernetes-mcp-server@latest

# Add to Claude Desktop config
{
  "mcpServers": {
    "kubernetes": {
      "command": "npx",
      "args": ["kubernetes-mcp-server@latest"]
    }
  }
}
```

**Use Cases:**
- ?? Natural language cluster management
- ? Automated troubleshooting with AI
- ? Resource discovery and analysis
- ? Security auditing assistance

## Security & Compliance

Tools and frameworks for securing ML workloads and ensuring compliance.

| Tool | Description | Category | License | GitHub Stars | Security Features |
|------|-------------|----------|---------|--------------|-------------------|
| [Istio](https://istio.io/) | Service mesh for microservices | Service Mesh | Apache 2.0 | 35k+ | mTLS, Traffic policies, Security policies |
| [Open Policy Agent (OPA)](https://openpolicyagent.org/) | Policy engine for cloud-native environments | Policy Management | Apache 2.0 | 9k+ | Policy as code, Admission control, RBAC |
| [Falco](https://falco.org/) | Runtime security monitoring | Runtime Security | Apache 2.0 | 7k+ | Anomaly detection, Rule engine, Kubernetes-aware |
| [Cosign](https://sigstore.dev/) | Container signing and verification | Supply Chain Security | Apache 2.0 | 4k+ | Image signing, SBOM, Attestations |

## Commercial & Managed Solutions

Enterprise and cloud-managed platforms for Kubernetes AI/ML.

| Platform | Provider | Description | Key Features |
|----------|----------|-------------|--------------|
| [Google Vertex AI](https://cloud.google.com/vertex-ai) | Google Cloud | Managed ML platform | AutoML, Custom training, Model serving, Pipelines |
| [Amazon SageMaker](https://aws.amazon.com/sagemaker/) | AWS | Complete ML service | Notebooks, Training, Hosting, Pipelines |
| [Azure Machine Learning](https://azure.microsoft.com/en-us/services/machine-learning/) | Microsoft | Cloud ML service | Designer, AutoML, MLOps, Responsible AI |
| [Databricks](https://databricks.com/) | Databricks | Unified analytics platform | Collaborative notebooks, MLflow, Delta Lake |
| [H2O.ai](https://h2o.ai/) | H2O.ai | AI/ML platform | AutoML, Model interpretability, MLOps |

## Getting Started

### ?? Prerequisites
- Kubernetes cluster (v1.20+)
- kubectl configured
- Basic understanding of containers and Kubernetes
- Python/R for ML development

### ? Quick Start Options

#### Option 1: Complete MLOps with Kubeflow
```bash
# Install kfctl
wget https://github.com/kubeflow/kfctl/releases/download/v1.2.0/kfctl_v1.2.0_linux.tar.gz
tar -xvf kfctl_v1.2.0_linux.tar.gz
sudo mv kfctl /usr/local/bin/

# Deploy Kubeflow
export KF_NAME=my-kubeflow
export BASE_DIR=${HOME}/kubeflow
export KF_DIR=${BASE_DIR}/${KF_NAME}
export CONFIG_URI="https://raw.githubusercontent.com/kubeflow/manifests/v1.2-branch/kfdef/kfctl_k8s_istio.v1.2.0.yaml"

mkdir -p ${KF_DIR}
cd ${KF_DIR}
kfctl apply -V -f ${CONFIG_URI}
```

#### Option 2: Model Serving with KServe
```bash
kubectl apply -f https://github.com/kserve/kserve/releases/download/v0.8.0/kserve.yaml
```

#### Option 3: Workflow Orchestration with Argo
```bash
kubectl create namespace argo
kubectl apply -n argo -f https://github.com/argoproj/argo-workflows/releases/download/v3.4.4/install.yaml
```

#### Option 4: AI-Native Cluster Management with MCP
```bash
npx kubernetes-mcp-server@latest
```

## ? Useful Resources

### Documentation & Guides
- [CNCF AI/ML Working Group](https://github.com/cncf/tag-app-delivery/tree/main/wg-ai-ml)
- [Kubernetes AI/ML Best Practices](https://kubernetes.io/docs/concepts/extend-kubernetes/compute-storage-net/device-plugins/)
- [MLOps Principles](https://ml-ops.org/)
- [Model Context Protocol Documentation](https://modelcontextprotocol.io/)
- [Quick Start Guide](QUICKSTART.md)

### Community & Events
- [KubeCon + CloudNativeCon](https://events.linuxfoundation.org/kubecon-cloudnativecon/)
- [MLOps World](https://mlopsworld.com/)
- [Kubeflow Community](https://www.kubeflow.org/docs/about/community/)

## ? Contributing

We welcome contributions! Please read our [Contributing Guide](CONTRIBUTING.md) for details.

### Quick Contribution Steps
1. Fork the repository
2. Create a feature branch (`git checkout -b feature/add-new-tool`)
3. Add your changes in the appropriate category table
4. Commit your changes (`git commit -am 'Add new ML tool'`)
5. Push to the branch (`git push origin feature/add-new-tool`)
6. Create a Pull Request

## ? Community

Join our community to discuss Kubernetes AI/ML topics:

- **Slack**: [Collabnix Community](http://collabnix.com/slack)
- **Twitter**: [@collabnix](https://twitter.com/collabnix)
- **Blog**: [Collabnix.com](https://collabnix.com)
- **YouTube**: [Collabnix Channel](https://youtube.com/c/collabnix)

## ? License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## ? Acknowledgments

- Thanks to all the open-source contributors in the Kubernetes and AI/ML communities
- Special recognition to CNCF projects that power cloud-native AI/ML
- Inspired by the Cloud Native Landscape project
- MCP servers community for advancing AI-infrastructure integration

---

**Maintained by**: [Collabnix Community](https://collabnix.com)
**Last Updated**: May 2025

? **Star this repository** if you find it helpful!

