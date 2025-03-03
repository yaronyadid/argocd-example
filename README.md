# ArgoCD Example Repository

This repository contains applications to be deployed across multiple clusters using ArgoCD ApplicationSets.

## Structure

- `apps/`: Contains individual application charts (nginx, redis)
- `clusters/`: Contains cluster-specific values and ApplicationSet configurations
- `common/`: Contains shared values across all clusters
- `bootstrap/`: Contains bootstrap resources for initial ArgoCD setup
