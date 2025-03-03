# ArgoCD Example Repository

This repository contains a Helm-based structure for deploying applications across multiple clusters using ArgoCD.

## Structure

- `apps/`: Contains the umbrella chart and individual application charts
- `clusters/`: Contains cluster-specific values and application definitions
- `common/`: Contains shared values across all clusters
- `bootstrap/`: Contains bootstrap resources for ArgoCD setup

## Usage

Each cluster folder contains its own application set and values files for customizing deployments.
