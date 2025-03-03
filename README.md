# ArgoCD Example Repository

This repository contains applications to be deployed across multiple clusters using ArgoCD ApplicationSets.

## Structure

- `apps/`: Contains individual application charts (nginx, redis)
- `clusters/`: Contains cluster-specific values and ApplicationSet configurations
- `common/`: Contains shared values across all clusters
- `bootstrap/`: Contains bootstrap resources for initial ArgoCD setup


├── apps/
│   ├── nginx/       # Nginx application chart
│   └── redis/       # Redis application chart 
├── clusters/
│   ├── cluster1/
│   │   ├── values.yaml              # Cluster-specific values
│   │   └── applicationset.yaml      # Single ApplicationSet for cluster1
│   ├── cluster2/
│   │   └── ...
│   └── cluster3/
│       └── ...
├── common/
│   └── values.yaml                  # Common values for all clusters
├── bootstrap/                       # Bootstrap resources (namespaces, RBAC, etc.)
│   ├── namespaces.yaml
│   ├── projects.yaml
│   └── rbac.yaml
└── root-application.yaml            # Root Application to deploy all cluster ApplicationSets