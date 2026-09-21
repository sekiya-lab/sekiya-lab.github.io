---
layout: page
title: Next Architecture of Mobile Core Network
permalink: /researches/mobile/
---

## Next Architecture of Mobile Core Network

Mobile networks have become critical infrastructure for communication, industry, transportation, and public services. The 5G Core Network (5GC) has adopted a Service-Based Architecture (SBA), but its operational model still inherits important assumptions from conventional telecommunications systems. Multiple stateful Network Functions (NFs) retain and exchange User Equipment (UE) context, creating complex dependencies. A failure, software update, or scaling operation in one NF can therefore affect many users and may propagate across the control plane.

Our research reconsiders the architecture of the mobile core itself. Instead of treating each NF as a long-running stateful service, we investigate a **procedure-based, stateless, and per-UE architecture** designed for cloud platforms. The goal is not merely to run an existing 5GC implementation on virtual machines or containers, but to redesign its processing model so that mobile-core functions can benefit from elasticity, fault isolation, event-driven execution, and managed cloud services.

---

### Goal and Vision

The goal of this project is to develop a next-generation mobile core that is:

- **Scalable:** resources can be allocated in response to the number of procedures and active UEs.
- **Stateless:** persistent UE context is separated from short-lived processing functions.
- **Fault-isolated:** a problem affecting one UE or procedure does not unnecessarily affect other users.
- **Cloud-native:** control-plane processing can use event-driven execution and managed cloud services.
- **Operationally simple:** software updates, recovery, and capacity expansion can be performed with a smaller impact radius.
- **Extensible toward 6G:** the architecture can support increasingly distributed, heterogeneous, and software-defined mobile systems.


### Why the Mobile Core Needs a New Architecture

In a conventional 5GC, each NF serves many UEs and retains context associated with them. A control-plane procedure, such as registration or session establishment, traverses several NFs through multiple service-based interfaces. This design follows the standardized functional model, but it also introduces tightly coupled state, inter-NF signaling, and broad failure domains.

Cloud platforms offer rapid scaling, serverless execution, distributed storage, and messaging services. These capabilities cannot be fully exploited if the mobile core remains a set of continuously running, stateful NF processes. Our research therefore separates the standardized external behavior of 5GC from its internal implementation architecture and reorganizes processing around the procedures initiated by each UE.


### Core Architectural Principles

#### Procedure-Based Processing

Mobile-core behavior is decomposed according to 3GPP procedures rather than only according to conventional NF boundaries. The functions required for a procedure are invoked as an event-driven processing flow. This reduces unnecessary dependencies among long-running services and makes the execution path of each procedure explicit.

![mobile-proc5gc-architecture]({{ "mobile-proc5gc-architecture.png" | relative_url }})

#### Stateless Functions and External Context

UE context is stored outside the processing functions. A function retrieves the context required for an event, performs its processing, updates the external state when necessary, and then terminates. This model allows processing instances to be replaced or scaled without depending on local in-memory state.

#### Per-UE Fault Isolation

Processing and context are logically separated for each UE. A software failure or abnormal state can therefore be contained within a smaller scope. The architecture aims to avoid large-scale failures in which a single NF problem simultaneously disconnects many UEs.

#### Event-Driven Cloud Execution

Messages received from the radio access network or other mobile-core components are converted into events and delivered to the appropriate functions. Message queues and managed cloud services decouple message reception from procedure execution, enabling elastic processing and recovery.

#### Separation of Control and User Planes

The research began with control-plane procedures and was later extended to include the user plane. Supporting both planes is essential for completing real PDU session establishment and for evaluating an end-to-end mobile-core architecture on a public cloud.


### Evolution of the Research

#### 2023: Proc5GC - Stateless Procedural Processing

The first stage proposed **Proc5GC**, a stateless 5G core architecture based on procedural processing. It reorganized mobile-core control-plane behavior around individual procedures and UEs, while storing context externally. A prototype demonstrated that standardized 5GC behavior could be implemented without requiring every NF process to retain long-lived UE state.

The design was presented in **[A Design of Stateless 5G Core Network with Procedural Processing](https://doi.org/10.1109/BlackSeaCom58138.2023.10299772){: target="_blank" }** at IEEE BlackSeaCom 2023. Related implementations examined the external data structures required for UE context, a monolithic per-UE SMNF, and the realization of procedure-based processing using existing NF-oriented 5GC software.

#### 2024: Cloud5GC - Serverless Control Plane on a Public Cloud

The second stage implemented the proposed architecture as **Cloud5GC** on a public cloud. Control-plane functions were decomposed into independently executable functions and connected through cloud messaging and storage services. The implementation demonstrated that a 5GC control plane could be constructed using a scalable and stateless execution model while preserving the behavior expected by mobile-network components.

The results were published as **[Cloud5GC: Design and Implementation of Scalable and Stateless Mobile Core System on Public Cloud](https://doi.org/10.1109/ICOIN59985.2024.10572149){: target="_blank" }** at IEEE ICOIN 2024. The evaluation demonstrated the feasibility, flexibility, resilience, and fault-tolerance of the architecture on a public-cloud platform.

#### 2025: P-Cloud5GC - Extending the Architecture to the User Plane

The third stage extended Cloud5GC beyond control-plane signaling. **P-Cloud5GC** introduced user-plane support and validated the processing required for PDU session establishment. This step connected procedure-based control-plane functions with the data path needed to provide actual UE connectivity.

The work was presented in **[P-Cloud5GC: Innovative 5G Core Architecture on Public Cloud with Scalability and Fault Tolerance](https://doi.org/10.1109/NetSoft64993.2025.11080619){: target="_blank" }** at IEEE NetSoft 2025. The results show how the architecture can combine public-cloud elasticity with fault isolation across both control- and user-plane processing.


### Research Contributions

Across Proc5GC, Cloud5GC, and P-Cloud5GC, this project has produced the following contributions:

1. A redesign of 5GC processing around procedures and individual UEs.
2. Separation of persistent UE context from short-lived processing functions.
3. An event-driven execution model suitable for serverless and managed cloud platforms.
4. Reduction of the failure impact radius through per-UE processing and context isolation.
5. A public-cloud implementation of scalable and stateless control-plane functions.
6. Extension of the architecture to user-plane processing and PDU session establishment.


### Toward 6G and AI-Native Mobile Networks

Future mobile networks will combine communication services, edge computing, AI workloads, and highly distributed infrastructure. The mobile core will need to adapt its resource allocation and placement according to traffic, latency, resilience, and application requirements.

Our next research steps include portable implementations that reduce dependence on a specific cloud provider, orchestration across public cloud and edge environments, dynamic placement of procedure functions, stronger security and observability, and coordinated resource management between the mobile core, RAN, and AI computing infrastructure.

The long-term objective is an autonomous and dependable mobile-core platform in which each procedure can be deployed, scaled, monitored, updated, and recovered independently while maintaining interoperability with standardized mobile-network interfaces.


### Publications

- H. Watanabe, K. Akashi, K. Shima, Y. Sekiya, and K. Horiba, “A Design of Stateless 5G Core Network with Procedural Processing,” IEEE BlackSeaCom 2023, pp. 199--204, 2023.
- K. Akashi, S. Yamamoto, H. Sakurai, K. Ito, T. Ishihara, T. Iimura, H. Watanabe, K. Shima, K. Horiba, and Y. Sekiya, “Cloud5GC: Design and Implementation of Scalable and Stateless Mobile Core System on Public Cloud,” IEEE ICOIN 2024, pp. 310--315, 2024.
- K. Akashi, H. Watanabe, S. Yamamoto, T. Ishihara, T. Iimura, and Y. Sekiya, “P-Cloud5GC: Innovative 5G Core Architecture on Public Cloud with Scalability and Fault Tolerance,” IEEE NetSoft 2025, pp. 518--522, 2025.

Please refer to the [Publications & Activities]({{ "/publications/" | relative_url }}) page for complete bibliographic information.
