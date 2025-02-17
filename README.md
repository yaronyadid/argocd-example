# ArgoCD Multi-Cluster Example

This repository demonstrates a GitOps approach to managing multiple Kubernetes clusters using ArgoCD and Helm.

## Repository Structure

```
.
├── apps/                   # Application Helm charts
│   ├── Chart.yaml         # Umbrella chart definition
│   ├── values.yaml        # Default values
│   └── charts/
│       └── nginx/         # Nginx application
│           ├── Chart.yaml
│           ├── values.yaml
│           └── templates/
├── clusters/              # Cluster-specific configurations
│   ├── cluster1/
│   ├── cluster2/
│   └── cluster3/
├── common/               # Shared configurations
└── cluster-config/       # ArgoCD and cluster bootstrap
    ├── applications/    # ApplicationSets
        └── bootstrap/       # Initial cluster setup
	```

	## Best Practices

	1. **Directory Structure**
	   - Separate application code from deployment configurations
   - Keep cluster-specific configurations isolated
   - Group related ApplicationSets together

2. **Configuration Management**
   - Use Helm for templating and value management
   - Maintain common configurations in `common/`
   - Override values at cluster level when needed

3. **GitOps Workflow**
   - All changes should be made through Git
   - Use Pull Requests for changes
   - Maintain clear separation between app and infrastructure code

4. **ArgoCD Setup**
   - ApplicationSets for managing multiple clusters
   - Clear project definitions with appropriate RBAC
   - Automated sync policies with proper retry mechanisms

## Usage

1. **Bootstrap ArgoCD**
```bash
kubectl apply -f cluster-config/bootstrap/project.yaml
```

2. **Deploy Applications**
```bash
kubectl apply -f cluster-config/applications/nginx-appset.yaml
```

3. **Add New Cluster**
   - Add new cluster configuration in `clusters/`
   - Update ApplicationSet generator in `cluster-config/applications/`
   - Add cluster details to ArgoCD

## Maintenance

1. **Adding New Applications**
   - Create new chart in `apps/charts/`
   - Add configurations to cluster values files
   - Create new ApplicationSet if needed

2. **Updating Applications**
   - Update values in appropriate files
   - Commit and push changes
   - ArgoCD will automatically sync

3. **Troubleshooting**
   - Check ArgoCD UI for sync status
   - Review application logs
   - Verify cluster-specific values
