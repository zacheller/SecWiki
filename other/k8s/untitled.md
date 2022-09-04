# Chapter 2: Container Orchestration

**Introduction**

With container images, we confine the application code, its runtime, and all of its dependencies in a pre-defined format. And, with container runtimes like runC, containerd, or rkt we can use those pre-packaged images, to create one or more containers. All of these runtimes are good at running containers on a single host. But, in practice, we would like to have a fault-tolerant and scalable solution, which can be achieved by creating a single controller/management unit, after connecting multiple nodes together. This controller/management unit is generally referred to as a container orchestrator.\
\
**What are Containers?**

* portable, isolated virtual environments for applications to run without interference from other running applications.
* encapsulate microservices and their dependencies but do not run them directly. Containers run container images.

**What are Microservices?**

* lightweight applications with specific dependencies, libraries and environmental requirements

**What is a Container image?**

* bundles the application along with its runtime and dependencies, and a container is deployed from the container image

**What is Container Orchestration?**

* Container orchestrators are tools which group systems together to form clusters where containers' deployment and management is automated at scale while meeting the requirements of:
  * Fault-tolerance
  * On-demand scalability
  * Optimal resource usage
  * Auto-discovery to automatically discover and communicate with each other
  * Accessibility from the outside world
  * Seamless updates/rollbacks without any downtime.
* e.g. Amazon Elastic Container Service, Azure Container Instances, Azure Service Fabric, Kubernetes, Marathon, Nomad, Docker Swarm

**Explain the reasons for doing container orchestration.**

* so you don't have to manually maintain containers
* Most container orchestrators can:
  * Group hosts together while creating a cluster
  * Schedule containers to run on hosts in the cluster based on resources availability
  * Enable containers in a cluster to communicate with each other regardless of the host they are deployed to in the cluster
  * Bind containers and storage resources
  * Group sets of similar containers and bind them to load-balancing constructs to simplify access to containerized applications by creating a level of abstraction between the containers and the user
  * Manage and optimize resource usage
  * Allow for implementation of policies to secure access to applications running inside containers.

**Discuss different container orchestration options.**

* container orchestrators can be deployed on the infrastructure of our choice - on bare metal, Virtual Machines, on-premise, or the public cloud. Kubernetes can be deployed on a workstation, with or without a local hypervisor such as Oracle VirtualBox, inside a company's data center, in the cloud on AWS Elastic Compute Cloud (EC2) instances, Google Compute Engine (GCE) VMs, DigitalOcean Droplets, OpenStack, etc
* turnkey solutions which allow Kubernetes clusters to be installed, with only a few commands, on top of cloud Infrastructures-as-a-Service, such as GCE, AWS EC2, Docker Enterprise, IBM Cloud, **Rancher**, VMware, Pivotal, and multi-cloud solutions through IBM Cloud Private and StackPointCloud.

**Discuss different container orchestration deployment options.**

* Directly on infrastructure of your choice
* Turnkey solutions on top of cloud IaaS
* Kubernetes as-a-Service solution, offered and hosted by the major cloud providers, such as [Google Kubernetes Engine](https://cloud.google.com/kubernetes-engine/) (GKE), [Amazon Elastic Container Service for Kubernetes](https://aws.amazon.com/eks/) (Amazon EKS), [Azure Kubernetes Service](https://azure.microsoft.com/en-us/services/kubernetes-service/) (AKS), [IBM Cloud Kubernetes Service](https://www.ibm.com/cloud/container-service), [DigitalOcean Kubernetes](https://www.digitalocean.com/products/kubernetes/), [Oracle Container Engine for Kubernetes](https://cloud.oracle.com/containers/kubernetes-engine), etc

