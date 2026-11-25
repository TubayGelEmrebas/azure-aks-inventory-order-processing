# Azure AKS Inventory & Order Processing Challenge

An eight-week solo engineering project to design and build an Azure prototype for inventory updates and order processing in a fictional retail scenario.

**This is a working prototype, not a production-ready system.** All project data will be synthetic. The design and implementation are my own work; external references will be credited in this repository.

## The challenge

Stores, warehouses, and online shops send inventory updates that may arrive late or more than once. When several customers try to order the last available item at the same time, the system must prevent overselling and keep stock records accurate.

This project explores how to handle these challenges through architecture design, implementation, and failure testing on Azure.

## Project goals

- Design an event-processing flow that handles duplicate, delayed, and failed messages.
- Compare optimistic and pessimistic concurrency approaches for stock reservations in Azure SQL.
- Provision Azure infrastructure with Terraform.
- Scale event consumers based on backlog and application services based on resource usage.
- Monitor service health, processing delays, errors, and stock exceptions.
- Test how the prototype responds to failures and document recovery results.
- Document architecture decisions, test results, migration considerations, and estimated Azure costs.
- Explore an AI-assisted feature that summarizes stock exceptions and suggests investigation steps.

## Planned architecture

The prototype is planned to use:

- **Azure Kubernetes Service (AKS)** to run application services and event consumers.
- **Azure Event Hubs** to receive inventory and order events.
- **An application-managed quarantine flow** to store messages that repeatedly fail processing. Event Hubs does not provide a native dead-letter queue.
- **Azure SQL** to store inventory, orders, and reservation data.
- **Azure Container Registry (ACR)** to store container images.
- **KEDA** to scale event consumers based on the Event Hubs backlog.
- **HPA** to scale application services based on resource usage.
- **Azure Monitor, Managed Prometheus, and Grafana** for observability.
- **Key Vault, Workload Identity, OIDC, RBAC, and NetworkPolicy** for secrets management, identity, access control, and network traffic rules.

Microsoft’s Cloud Adoption Framework and Well-Architected Framework will inform the design. Architecture decisions will be documented as Architecture Decision Records (ADRs).

## Infrastructure and CI/CD

Terraform will define the Azure network, AKS, and ACR.

GitHub Actions is planned to run checks and create Terraform plans for pull requests. Infrastructure changes will be applied only after approval. Helm will be used to package and deploy the application to AKS.

## Failure testing and AI-assisted review

The prototype will simulate delayed and duplicate events, repeated message failures, and service interruptions. Results and recovery behavior will be documented.

An AI-assisted feature will summarize stock exceptions, highlight patterns, and suggest possible causes or investigation steps. I will review its output; it will not make operational decisions or take automated actions.

## Eight-week plan

The plan may change as the project progresses.

1. Define requirements, architecture, and initial ADRs.
2. Create the application and event-processing prototype.
3. Implement inventory updates and order reservations.
4. Compare concurrency approaches in Azure SQL.
5. Provision Azure infrastructure with Terraform.
6. Add CI checks, identity, access controls, and network policies.
7. Add scaling, monitoring, and failure simulations.
8. Review results, document costs, and publish findings.

## Repository contents

This repository will include source code, Terraform configuration, architecture diagrams, ADRs, test results, project notes, and references as they are created.

## Progress updates

I plan to share progress every Wednesday, covering completed work, challenges, decisions, and next steps.

## Data and security

All project data is synthetic. Do not commit passwords, access tokens, private keys, or other secrets to this repository.

## References

External documentation, tools, and other references used during the project will be listed here or linked from the relevant project documents.

## Status

**In progress.** Planned components and technologies may change as the project develops.
