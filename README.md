# Radware Kubernetes Home Assessment

## Overview

This repository contains solutions for the Radware Kubernetes Home Assessment. The assignments demonstrate practical Kubernetes administration, resource management, networking, scheduling, troubleshooting, and deployment management concepts using Minikube.

---

## Environment

* Kubernetes: v1.35.1
* Minikube: Multi-Node Cluster
* Container Runtime: Docker
* CNI: Calico
* Operating System: Ubuntu (EC2)

---

## Repository Structure

```text
Radware-Assignment/
│
├── assignment1/
│   ├── README.md
│   ├── limitrange.yaml
│   ├── resourcequota.yaml
│   ├── good-pod.yaml
│   ├── oom-pod.yaml
│   └── screenshots/
│
├── assignment2/
│   ├── README.md
│   ├── deployment.yaml
│   ├── clusterip.yaml
│   ├── nodeport.yaml
│   └── screenshots/
│
├── assignment3/
│   ├── README.md
│   ├── frontend.yaml
│   ├── backend.yaml
│   ├── database.yaml
│   ├── default-deny.yaml
│   ├── allow-dns.yaml
│   ├── frontend-backend.yaml
│   ├── backend-database.yaml
│   └── screenshots/
│
├── assignment4/
│   ├── README.md
│   ├── batch-pod.yaml
│   ├── ops-pod-no-toleration.yaml
│   ├── ops-pod-toleration.yaml
│   ├── affinity-pod.yaml
│   └── screenshots/
│
└── assignment5/
    ├── README.md
    ├── deployment.yaml
    └── screenshots/
```

---

# Assignment 1: Resource Governance and Failure Modes

## Objective

Validate practical understanding of Kubernetes resource management and failure handling.

## Manifest Files

* limitrange.yaml
* resourcequota.yaml
* good-pod.yaml
* oom-pod.yaml

## Concepts Demonstrated

* Resource Requests
* Resource Limits
* LimitRange
* ResourceQuota
* OOMKilled Behavior
* Admission Control

## Validation Performed

* Created namespace-level LimitRange
* Applied ResourceQuota restrictions
* Verified successful pod creation
* Simulated OOMKilled scenario
* Verified quota enforcement and admission failures

---

# Assignment 2: Service Exposure and Endpoint Debugging

## Objective

Demonstrate internal and external service access and troubleshoot service-to-pod mappings.

## Manifest Files

* deployment.yaml
* clusterip.yaml
* nodeport.yaml

## Concepts Demonstrated

* Deployments
* ClusterIP Services
* NodePort Services
* Port Forwarding
* Endpoint Verification
* Service Troubleshooting

## Validation Performed

* Deployed Nginx with three replicas
* Exposed application using ClusterIP and NodePort
* Verified internal access from within the cluster
* Verified external access through NodePort
* Tested service port-forwarding
* Diagnosed and fixed broken service selectors

---

# Assignment 3: NetworkPolicy with DNS-Safe Zero Trust

## Objective

Implement a DNS-safe zero-trust networking model using Kubernetes NetworkPolicies.

## Manifest Files

* frontend.yaml
* backend.yaml
* database.yaml
* default-deny.yaml
* allow-dns.yaml
* frontend-backend.yaml
* backend-database.yaml

## Concepts Demonstrated

* Network Policies
* Default Deny Strategy
* DNS Access Control
* Ingress Rules
* Egress Rules
* Zero Trust Networking

## Validation Performed

* Applied default deny policy
* Restored DNS functionality using allow-dns policy
* Allowed Frontend → Backend communication
* Allowed Backend → Database communication
* Blocked Frontend → Database communication

### Connectivity Matrix

| Source   | Destination | Result  |
| -------- | ----------- | ------- |
| Frontend | Backend     | Allowed |
| Backend  | Database    | Allowed |
| Frontend | Database    | Blocked |

---

# Assignment 4: Scheduling Controls

## Objective

Demonstrate workload placement and scheduling using labels, selectors, taints, tolerations, and affinity.

## Manifest Files

* batch-pod.yaml
* ops-pod-no-toleration.yaml
* ops-pod-toleration.yaml
* affinity-pod.yaml

## Concepts Demonstrated

* Node Labels
* NodeSelector
* Taints
* Tolerations
* Node Affinity

## Validation Performed

* Added a second worker node
* Applied node labels
* Applied node taints
* Scheduled workloads using NodeSelector
* Verified scheduling failure without toleration
* Verified successful scheduling with toleration
* Scheduled workloads using Node Affinity

---

# Assignment 5: Controlled Production Change

## Objective

Perform safe deployment updates and recover from deployment failures.

## Manifest Files

* deployment.yaml

## Concepts Demonstrated

* Deployments
* Rolling Updates
* Readiness Probes
* Liveness Probes
* Rollout History
* Rollback Recovery

## Validation Performed

* Created Deployment with three replicas
* Configured readiness probes
* Configured liveness probes
* Performed rolling updates
* Verified rollout status and rollout history
* Simulated ImagePullBackOff failure
* Diagnosed deployment failure
* Successfully rolled back to a healthy revision

---

# Key Kubernetes Concepts Covered

* Resource Management
* Service Discovery
* Networking
* Network Security
* Scheduling
* High Availability
* Rolling Updates
* Health Checks
* Failure Recovery
* Troubleshooting
* Kubernetes Best Practices

---

# Author

**Sai Chowdary**

B.Tech Computer Science Engineering

Cloud & DevOps Enthusiast
