# MCP Servers for Kubernetes ???

Model Context Protocol (MCP) servers enable AI assistants to interact with Kubernetes clusters through standardized interfaces, providing natural language access to cluster management capabilities.

## What is MCP?

Model Context Protocol (MCP) is an open standard that allows AI applications to connect securely with external tools and data sources. Think of it as "USB for AI integrations" - providing a standardized way for AI assistants like Claude to interact with your infrastructure.

## Kubernetes MCP Servers

| Tool | Description | Language | License | GitHub Stars | Key Features |
|------|-------------|----------|---------|--------------|--------------|
| [kubernetes-mcp-server](https://github.com/manusa/kubernetes-mcp-server) | Native Kubernetes/OpenShift MCP server with direct API integration | Go | Apache 2.0 | 100+ | Native Go implementation, Cross-platform binaries, Auto-config detection, Helm support |
| [mcp-k8s-go](https://github.com/strowk/mcp-k8s-go) | Golang-based extensible Kubernetes MCP server | Go | MIT | 50+ | Lightweight, Pod logs, Events, Namespaces, Extensible architecture |
| [mcp-server-kubernetes](https://github.com/Flux159/mcp-server-kubernetes) | Node.js Kubernetes management server with Helm v3 support | TypeScript | MIT | 80+ | kubectl operations, Helm charts, Port forwarding, Non-destructive mode |
| [mcp-k8s](https://github.com/silenceper/mcp-k8s) | Fine-grained Kubernetes operations with RBAC and security controls | Go | MIT | 30+ | CRUD operations, Helm management, Security-focused, stdio/SSE transport |
| [k8s-multicluster-mcp](https://github.com/razvanmacovei/k8s-multicluster-mcp) | Multi-cluster Kubernetes operations with multiple kubeconfig support | Python | MIT | 25+ | Multi-cluster support, Context switching, Unified interface |
| [multicluster-mcp-server](https://github.com/yanmxa/multicluster-mcp-server) | GenAI gateway for multi-cluster Kubernetes environments | TypeScript | MIT | 20+ | Hub cluster approach, CRD support, Interactive observability |

## Features Comparison Matrix

| Feature | kubernetes-mcp-server | mcp-k8s-go | mcp-server-kubernetes | mcp-k8s | k8s-multicluster-mcp | multicluster-mcp-server |
|---------|----------------------|-------------|----------------------|---------|---------------------|------------------------|
| **Language** | Go | Go | TypeScript | Go | Python | TypeScript |
| **Multi-cluster** | ? | ? | ? | ? | ? | ? |
| **Native Binaries** | ? | ? | ? | ? | ? | ? |
| **Helm Support** | ? | ? | ? | ? | ? | ? |
| **OpenShift Support** | ? | ? | ? | ? | ? | ? |
| **Security Controls** | ? | ? | ? | ? | ? | ? |
| **Transport** | stdio/SSE | stdio | stdio/SSE | stdio/SSE | stdio | stdio |
| **Pod Logs** | ? | ? | ? | ? | ? | ? |
| **Port Forwarding** | ? | ? | ? | ? | ? | ? |
| **Read-only Mode** | ? | ? | ? | ? | ? | ? |
| **CRD Support** | ? | ? | ? | ? | ? | ? |
| **Docker Support** | ? | ? | ? | ? | ? | ? |

## Quick Start Guide

### 1. Install kubernetes-mcp-server (Recommended)

The most comprehensive and actively maintained MCP server for Kubernetes:

```bash
# Using npm (fastest method)
npx kubernetes-mcp-server@latest

# Using Python with uv
uvx kubernetes-mcp-server@latest

# Download native binary (Linux)
wget https://github.com/manusa/kubernetes-mcp-server/releases/latest/download/kubernetes-mcp-server-linux-amd64
chmod +x kubernetes-mcp-server-linux-amd64
./kubernetes-mcp-server-linux-amd64

# Download native binary (macOS)
wget https://github.com/manusa/kubernetes-mcp-server/releases/latest/download/kubernetes-mcp-server-darwin-amd64
chmod +x kubernetes-mcp-server-darwin-amd64
./kubernetes-mcp-server-darwin-amd64

# Using Docker
docker run -v ~/.kube/config:/root/.kube/config:ro ghcr.io/manusa/kubernetes-mcp-server:latest
```

### 2. Claude Desktop Configuration

Add to your `claude_desktop_config.json`:

**Basic Configuration:**
```json
{
  "mcpServers": {
    "kubernetes": {
      "command": "npx",
      "args": ["kubernetes-mcp-server@latest"]
    }
  }
}
```

**With Custom Kubeconfig:**
```json
{
  "mcpServers": {
    "kubernetes": {
      "command": "npx",
      "args": ["kubernetes-mcp-server@latest"],
      "env": {
        "KUBECONFIG": "/path/to/your/kubeconfig"
      }
    }
  }
}
```

**Read-only Mode (Safe for Production):**
```json
{
  "mcpServers": {
    "kubernetes-readonly": {
      "command": "npx",
      "args": ["kubernetes-mcp-server@latest", "--read-only"]
    }
  }
}
```

### 3. Multi-cluster Setup

For managing multiple Kubernetes clusters simultaneously:

```json
{
  "mcpServers": {
    "k8s-multicluster": {
      "command": "python3",
      "args": ["/path/to/k8s-multicluster-mcp/app.py"],
      "env": {
        "KUBECONFIG_DIR": "/path/to/kubeconfigs"
      }
    }
  }
}
```

## Installation Methods

### Method 1: Native Binaries (Fastest)

**Advantages:**
- No dependencies on Node.js or Python
- Fastest startup time
- Smallest resource footprint

```bash
# Download for your platform
curl -L https://github.com/manusa/kubernetes-mcp-server/releases/latest/download/kubernetes-mcp-server-$(uname -s | tr '[:upper:]' '[:lower:]')-$(uname -m) -o kubernetes-mcp-server
chmod +x kubernetes-mcp-server
```

### Method 2: npm Package

**Advantages:**
- Easy updates
- Cross-platform compatibility

```bash
npm install -g kubernetes-mcp-server
```

### Method 3: Docker Container

**Advantages:**
- Isolated environment
- Consistent runtime

```bash
docker run -v ~/.kube/config:/root/.kube/config:ro \
  -p 3000:3000 \
  ghcr.io/manusa/kubernetes-mcp-server:latest
```

### Method 4: Python Package (uv)

**Advantages:**
- Python ecosystem integration
- Easy dependency management

```bash
uvx kubernetes-mcp-server@latest
```

## Configuration Options

### Environment Variables

| Variable | Description | Default |
|----------|-------------|---------|
| `KUBECONFIG` | Path to kubeconfig file | `~/.kube/config` |
| `MCP_TRANSPORT` | Transport type (stdio/sse) | `stdio` |
| `MCP_PORT` | Port for SSE transport | `3000` |
| `MCP_HOST` | Host for SSE transport | `localhost` |
| `LOG_LEVEL` | Logging level | `info` |

### Command Line Arguments

```bash
kubernetes-mcp-server --help

Options:
  --read-only          Enable read-only mode (safe for production)
  --namespace <ns>     Default namespace for operations
  --context <ctx>      Kubernetes context to use
  --port <port>        Port for SSE transport
  --host <host>        Host for SSE transport
  --transport <type>   Transport type (stdio|sse)
  --version           Show version information
  --help              Show help
```

## Use Cases and Examples

### 1. Cluster Health Monitoring

**Prompt:** "Show me the health status of all nodes in my cluster"

**What the MCP server does:**
- Retrieves node information via Kubernetes API
- Checks node conditions and resource usage
- Provides formatted health report

### 2. Troubleshooting Failed Pods

**Prompt:** "Find all pods that are failing and show me their logs"

**What the MCP server does:**
- Lists pods with non-running states
- Fetches logs for failing pods
- Provides diagnostic information

### 3. Resource Management

**Prompt:** "List all deployments using more than 2GB of memory"

**What the MCP server does:**
- Queries deployment resource specifications
- Filters based on memory requirements
- Shows resource utilization

### 4. Security Auditing

**Prompt:** "Find all pods running as root across all namespaces"

**What the MCP server does:**
- Scans pod security contexts
- Identifies privilege escalation risks
- Provides security recommendations

### 5. Multi-cluster Operations

**Prompt:** "Compare the number of running pods between prod and staging clusters"

**What the MCP server does:**
- Switches between cluster contexts
- Counts running pods in each cluster
- Provides comparative analysis

## Security Considerations

### 1. RBAC Configuration

Create a service account with minimal required permissions:

```yaml
apiVersion: v1
kind: ServiceAccount
metadata:
  name: mcp-server
  namespace: default
---
apiVersion: rbac.authorization.k8s.io/v1
kind: ClusterRole
metadata:
  name: mcp-server-reader
rules:
- apiGroups: [""]
  resources: ["pods", "services", "nodes", "namespaces"]
  verbs: ["get", "list", "watch"]
- apiGroups: ["apps"]
  resources: ["deployments", "replicasets"]
  verbs: ["get", "list", "watch"]
---
apiVersion: rbac.authorization.k8s.io/v1
kind: ClusterRoleBinding
metadata:
  name: mcp-server-binding
roleRef:
  apiGroup: rbac.authorization.k8s.io
  kind: ClusterRole
  name: mcp-server-reader
subjects:
- kind: ServiceAccount
  name: mcp-server
  namespace: default
```

### 2. Network Policies

Restrict network access for MCP server pods:

```yaml
apiVersion: networking.k8s.io/v1
kind: NetworkPolicy
metadata:
  name: mcp-server-netpol
spec:
  podSelector:
    matchLabels:
      app: mcp-server
  policyTypes:
  - Ingress
  - Egress
  egress:
  - to:
    - namespaceSelector: {}
    ports:
    - protocol: TCP
      port: 443  # Kubernetes API server
```

### 3. Pod Security Standards

Use restricted pod security standards:

```yaml
apiVersion: v1
kind: Pod
metadata:
  name: mcp-server
  labels:
    app: mcp-server
spec:
  securityContext:
    runAsNonRoot: true
    runAsUser: 1000
    fsGroup: 2000
    seccompProfile:
      type: RuntimeDefault
  containers:
  - name: mcp-server
    image: ghcr.io/manusa/kubernetes-mcp-server:latest
    securityContext:
      allowPrivilegeEscalation: false
      readOnlyRootFilesystem: true
      capabilities:
        drop:
        - ALL
```

## Performance Optimization

### 1. Resource Limits

Configure appropriate resource limits:

```yaml
resources:
  requests:
    memory: "64Mi"
    cpu: "100m"
  limits:
    memory: "128Mi"
    cpu: "200m"
```

### 2. Caching

Some MCP servers support caching to improve performance:

```json
{
  "mcpServers": {
    "kubernetes": {
      "command": "kubernetes-mcp-server",
      "args": ["--cache-ttl", "300"]
    }
  }
}
```

### 3. Connection Pooling

Configure connection pooling for better resource utilization:

```bash
kubernetes-mcp-server --max-connections 10 --connection-timeout 30s
```

## Troubleshooting

### Common Issues

**1. Connection Refused**
```bash
# Check if kubeconfig is valid
kubectl cluster-info

# Verify MCP server is running
ps aux | grep kubernetes-mcp-server
```

**2. Permission Denied**
```bash
# Check RBAC permissions
kubectl auth can-i get pods --as=system:serviceaccount:default:mcp-server

# Verify service account exists
kubectl get serviceaccount mcp-server
```

**3. Memory Issues**
```bash
# Monitor resource usage
kubectl top pods -l app=mcp-server

# Check pod logs
kubectl logs -l app=mcp-server
```

### Debug Mode

Enable debug logging:

```json
{
  "mcpServers": {
    "kubernetes": {
      "command": "kubernetes-mcp-server",
      "args": ["--log-level", "debug"]
    }
  }
}
```

## Advanced Configuration

### Custom Resource Definitions (CRDs)

Support for custom resources:

```bash
kubernetes-mcp-server --enable-crds --crd-groups="argoproj.io,tekton.dev"
```

### Webhook Integration

Set up webhooks for real-time notifications:

```yaml
apiVersion: admissionregistration.k8s.io/v1
kind: MutatingAdmissionWebhook
metadata:
  name: mcp-server-webhook
webhooks:
- name: mcp.example.com
  clientConfig:
    service:
      name: mcp-server-webhook
      namespace: default
      path: "/webhook"
  rules:
  - operations: ["CREATE", "UPDATE"]
    apiGroups: [""]
    apiVersions: ["v1"]
    resources: ["pods"]
```

### Metrics and Monitoring

Enable Prometheus metrics:

```bash
kubernetes-mcp-server --enable-metrics --metrics-port 9090
```

## Best Practices

### 1. Security
- Always use read-only mode in production
- Implement proper RBAC controls
- Use service accounts with minimal permissions
- Enable audit logging

### 2. Performance
- Set appropriate resource limits
- Use caching when available
- Monitor memory and CPU usage
- Configure connection timeouts

### 3. Reliability
- Use health checks and readiness probes
- Implement graceful shutdown
- Set up proper logging and monitoring
- Use deployment strategies for updates

### 4. Multi-cluster Management
- Use separate MCP servers for different environments
- Implement cluster-specific naming conventions
- Set up proper network isolation
- Use GitOps for configuration management

## Contributing

To contribute to Kubernetes MCP servers:

1. **Choose a server** that matches your use case
2. **Fork the repository** and create a feature branch
3. **Add tests** for new functionality
4. **Update documentation** with examples
5. **Submit a pull request** with detailed description

## Related Projects

- [awesome-mcp-lists](https://github.com/collabnix/awesome-mcp-lists) - Comprehensive list of MCP servers
- [Model Context Protocol](https://modelcontextprotocol.io/) - Official MCP documentation
- [Claude Desktop](https://claude.ai/download) - AI assistant that supports MCP

---

**Need Help?**

- ? Check the [MCP Documentation](https://modelcontextprotocol.io/)
- ? Report issues in the respective GitHub repositories
- ? Join the [MCP Discord Community](https://discord.gg/modelcontextprotocol)
- ? Contribute to the [awesome-mcp-lists](https://github.com/collabnix/awesome-mcp-lists)

**Last Updated:** May 2025
