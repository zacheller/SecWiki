# Chapter 3: Kubernetes

**Introduction**

In this chapter, we will explain what Kubernetes is, its features, and the reasons why you should use it. We will explore the evolution of Kubernetes from Borg, which is a cluster manager created by Google. We will also talk about the Cloud Native Computing Foundation \(CNCF\), which currently hosts the Kubernetes project, along with other cloud-native projects, like Prometheus, Fluentd, rkt, containerd, etc.

**What is Kubernetes?**

* Kubernetes is an open-source system for automating deployment, scaling, and management of containerized applications.

**Why use K8s?**

* Deployable in nearly every environment \(eventually hybrid/multi-cloud\). Portable, extensible, modular, pluggable.

**What are the features of K8s?**

* Automatic bin packing
  * Kubernetes automatically schedules containers based on resource needs and constraints, to maximize utilization without sacrificing availability.
* Self-healing
  * Kubernetes automatically replaces and reschedules containers from failed nodes. It kills and restarts containers unresponsive to health checks, based on existing rules/policy. It also prevents traffic from being routed to unresponsive containers.
* Horizontal scaling
  * With Kubernetes applications are scaled manually or automatically based on CPU or custom metrics utilization.
* Service discovery and Load balancing
  * Containers receive their own IP addresses from Kubernetes, white it assigns a single Domain Name System \(DNS\) name to a set of containers to aid in load-balancing requests across the containers of the set.
* Automated rollouts and rollbacks
  * Kubernetes seamlessly rolls out and rolls back application updates and configuration changes, constantly monitoring the application's health to prevent any downtime.
* Secret and configuration management
  * Kubernetes manages secrets and configuration details for an application separately from the container image, in order to avoid a re-build of the respective image. Secrets consist of confidential information passed to the application without revealing the sensitive content to the stack configuration, like on GitHub.
* Storage orchestration
  * Kubernetes automatically mounts software-defined storage \(SDS\) solutions to containers from local storage, external cloud providers, or network storage systems.
* Batch execution
  * Kubernetes supports batch execution, long-running jobs, and replaces failed containers.

**K8s evolved from Borg. What features can be traced to Borg?**

* API servers
* Pods
* IP-per-Pod
* Services
* Labels

**What does the Cloud Native Computing Foundation \(CNCF\) do?**

* The Cloud Native Computing Foundation \(CNCF\) is one of the projects hosted by the Linux Foundation. CNCF aims to accelerate the adoption of containers, microservices, and cloud-native applications.

