# Flux Deployment Documentation

## Introduction

This repository contains configurations and documentation for deploying Flux, a GitOps tool, to a Google Cloud Kubernetes cluster. Flux automates the deployment and lifecycle management of applications through Git repositories.

## Prerequisites

To initiate an manual deployment all you need to do is create a commit in this repo with the new deployments. Preferbly helmrelease linked to the source code repo, where it would have helm charts.

## Flux Configuration

### Flux monitors the specified Docker Hub repository for new images based on the following criteria:

- Development Environment:
    Flux checks for new images with tags in the format `master-{runner_ID}`.

- Production Environment:
    Flux checks for images based on tags `x.x.x`.

### Deployment

Deployment is automatic. The Flux custom controller in the Google Cloud cluster continuously monitors this repository for changes. If any modifications occur, Flux automatically reapplies the configurations.

Additionally, when new images adhering to the defined dev and prod standards are pushed to the Docker repository, Flux automatically commits the newest image tag to this repository and triggers the deployments automatically.

# Conclusion

With Flux deployed to your Google Cloud Kubernetes cluster, the specified configurations for development and production environments will be applied automatically, ensuring a GitOps-driven continuous deployment workflow.