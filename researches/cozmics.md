---
layout: page
title: Zero Trust Security for Container Environment
permalink: /researches/cozmics/
---

## Zero Trust Security for Container Environment

Cloud-native applications increasingly combine multiple containers inside a single Kubernetes Pod. Application containers may run alongside sidecars for logging, monitoring, service-mesh functions, or security. Although these containers can be developed and maintained by different teams or vendors, Kubernetes places them in the same network namespace and traditionally treats the Pod as a single trust boundary.

The **CoZMicS** project—Container Zero-Trust Micro-Segmentation—reconsiders this assumption. We develop a mechanism that applies zero-trust principles inside a Pod: communication between containers is denied by default and only explicitly authorized container–port pairs are permitted. The objective is to contain a compromised container and prevent lateral movement without changing the Kubernetes control plane, container runtime, or application architecture.

---

### Goal and Vision

CoZMicS aims to make the individual container, rather than the Pod, the unit of network trust. The project is designed around the following goals:

- **Deny by default:** intra-Pod communication is blocked unless explicitly authorized.
- **Least privilege:** each container can communicate only through the ports required for its role.
- **Declarative policy:** communication requirements are described together with the Kubernetes workload manifest.
- **Compatibility:** existing Pods, sidecars, container runtimes, and Kubernetes control-plane components do not require modification.
- **Dynamic enforcement:** policies can follow Pod creation, deletion, scaling, and rolling updates.
- **Operational visibility:** permitted communication is explicit, reviewable, and auditable.
- **Scalability:** enforcement should remain practical as the number of Pods, containers, and allowed ports grows.


### Why Intra-Pod Micro-Segmentation Is Necessary

Kubernetes network policies commonly control communication between Pods. Containers in the same Pod, however, share a network namespace and can communicate through the loopback interface. This behavior is useful for tightly coupled applications, but it also means that compromise of one container can expose the other containers in the Pod.

The risk is especially important for sidecars obtained from third parties or maintained under a different software lifecycle. A vulnerable monitoring or logging container may become a path to the main application. Existing controls such as Pod Security Standards, SecurityContext, SELinux, and AppArmor help restrict privileges and host access, but they do not by themselves provide a simple, declarative allowlist for every container-to-container connection inside a shared Pod network namespace.

CoZMicS introduces an additional internal boundary while preserving the operational advantages of the sidecar pattern.


### Architecture

The initial CoZMicS prototype is integrated with Cilium and Kubernetes workload lifecycle processing. Communication policy is written as metadata in the Pod manifest. At Pod startup, a helper component interprets the metadata and installs filtering rules in the Pod network namespace.

<figure style="text-align: center; margin: 2rem 0;">
  <a href="{{ '/assets/images/cozmics-design-overview.png' | relative_url }}">
    <img src="{{ '/assets/images/cozmics-design-overview.png' | relative_url }}" alt="Design overview of the CoZMicS container micro-segmentation mechanism" style="max-width: 760px; width: 100%; height: auto;">
  </a>
  <figcaption><em>Figure 1. Design overview of the proposed container micro-segmentation mechanism. Manifest metadata is processed through Cilium integration and a helper command to configure packet filtering inside each Pod. Reproduced from Figure 1 of the CoZMicS paper.</em></figcaption>
</figure>

The original implementation uses Netfilter and iptables. It first establishes a deny-all policy for intra-Pod traffic and then adds allow rules for the container–port pairs declared in the manifest. Policy generation is automated, so application developers describe the intended connectivity rather than manually operating firewall rules.


### Policy Model

CoZMicS expresses communication requirements using Kubernetes manifest annotations. Each rule identifies a container and the port through which communication should be allowed. The design keeps security intent close to the workload definition and makes it possible to review communication privileges through the same deployment workflow used for application configuration.

This model provides several operational benefits:

1. Security policy can be version-controlled with the application manifest.
2. A missing rule results in denied communication rather than implicit trust.
3. Policy changes can be applied as part of ordinary Kubernetes deployment operations.
4. Different containers within the same Pod can receive different communication privileges.
5. The intended communication surface can be inspected before deployment.


### Prototype and Evaluation

The prototype was implemented in Go and evaluated on Kubernetes with Cilium. The experiments verified that the mechanism correctly blocks unauthorized intra-Pod communication while allowing explicitly declared container–port combinations.

The evaluation measured two forms of overhead:

- TCP session-establishment time as the number of containers and rules increases.
- Time required to generate and apply iptables allow rules as the numbers of Pods and containers increase.

<figure style="text-align: center; margin: 2rem 0;">
  <a href="{{ '/assets/images/cozmics-iptables-rule-time.png' | relative_url }}">
    <img src="{{ '/assets/images/cozmics-iptables-rule-time.png' | relative_url }}" alt="Time required to apply CoZMicS iptables rules" style="max-width: 680px; width: 100%; height: auto;">
  </a>
  <figcaption><em>Figure 2. Time required to apply iptables allow rules as the numbers of containers and Pods increase. Rule installation becomes impractical in the largest configuration. Reproduced from Figure 7 of the CoZMicS paper.</em></figcaption>
</figure>

The experiments revealed a fundamental scalability limitation. TCP session latency grows as more rules must be examined, reflecting the linear lookup behavior of iptables. Rule-application time also rises rapidly because the number of container–port rules grows with workload size. In the experiment with 50 Pods and 50 containers per Pod, policy propagation required approximately five hours.

Distributing containers across more Pods does not eliminate this problem. Each Pod has an independent network namespace and rule set, while the total amount of policy configuration continues to grow. The evaluation therefore shows that iptables is useful for demonstrating the feasibility of intra-Pod micro-segmentation but is not suitable as the final enforcement mechanism for large-scale deployments.


### Evolution Toward eBPF

Based on the evaluation, CoZMicS is evolving from an iptables prototype toward eBPF-based enforcement. eBPF enables policy lookup through efficient kernel data structures and allows filtering logic to be attached closer to the network-processing path. This can avoid long sequential rule chains and reduce both packet-processing and policy-update overhead.

The next implementation stage integrates container isolation with an eBPF data plane while retaining the declarative manifest model. The research focuses on:

- mapping containers and ports to efficient eBPF policy entries;
- preserving deny-by-default behavior during Pod startup and policy updates;
- supporting dynamic container lifecycle events without temporary policy gaps;
- measuring latency, throughput, memory consumption, and policy-update time;
- monitoring denied and permitted flows for incident investigation;
- maintaining compatibility with existing Kubernetes manifests and CNI operation.


### Security Contributions

CoZMicS contributes a container-oriented security model for cloud-native environments:

1. It identifies the shared Pod network namespace as an important remaining trust boundary.
2. It applies zero-trust and least-privilege principles to communication inside the Pod.
3. It provides a declarative container–port policy model integrated with Kubernetes manifests.
4. It demonstrates enforcement without modifying the Kubernetes control plane or container runtime.
5. It experimentally characterizes the latency and policy-management limits of iptables.
6. It establishes the design requirements for scalable eBPF-based intra-Pod isolation.


### Toward Zero-Trust Cloud-Native Infrastructure

Container micro-segmentation is one layer of a broader zero-trust architecture. Future work will combine network enforcement with workload identity, software supply-chain information, runtime behavior monitoring, and automated incident response. Policies should eventually be generated and updated using both declared application requirements and observed behavior, while every change remains explainable and auditable.

The long-term objective of CoZMicS is to provide lightweight and scalable containment for heterogeneous cloud-native workloads. Even when a sidecar or application container is compromised, the architecture should restrict the attacker's reachable services and prevent the compromise from spreading across containers, Pods, and clusters.


### Publication

- Shoya Nakamura, Kunio Akashi, and Yuji Sekiya, **[“Proposal and Evaluation of a Method for Container Micro-segmentation”](https://doi.org/10.1007/978-3-032-17443-7_15){: target="_blank" }**, *Innovative Security Solutions for Information Technology and Communications (SecITC 2025)*, Lecture Notes in Computer Science, Vol. 16443, pp. 249--261, Springer, 2026.

Please refer to the [Publications & Activities]({{ "/publications/" | relative_url }}) page for complete bibliographic information.
