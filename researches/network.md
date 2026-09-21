---
layout: page
title: Network Architecture, Operation, and Management
permalink: /researches/network/
---

## Network Architecture, Operation, and Management

Communication networks are critical infrastructure. They must remain available under failures and traffic changes, support new services without disrupting existing users, and remain understandable to the engineers who operate them. Achieving these requirements demands more than high-performance equipment. Network architecture, control mechanisms, measurement, security, and operational processes must work together.

Our research combines the design of network technologies with experience from production networks and large-scale testbeds. We develop architectures and operational methods, implement working prototypes, evaluate them with real traffic and equipment, and return the results to the research community, network operators, vendors, and standards activities.

---

### Goal and Vision

The goal of this research is to make networks dependable, programmable, observable, and practical to operate. We focus on the following principles:

- **Resilience:** services should continue when devices, links, software, or external systems fail.
- **Operational visibility:** engineers should be able to understand topology, traffic, performance, and abnormal behavior from measurable evidence.
- **Programmability:** network behavior should be controlled through explicit policies and software rather than repetitive device-by-device configuration.
- **Interoperability:** new technologies must work across implementations and coexist with deployed protocols and equipment.
- **Incremental deployment:** operators should be able to introduce a new architecture without replacing an entire network at once.
- **Security by design:** monitoring, isolation, authentication, and incident response should form part of the architecture from the beginning.


### Internet Architecture and IPv6

Our early work contributed to the design and implementation of the Internet protocol infrastructure itself. Through the **USAGI Project**, we worked on the IPv6 protocol stack for Linux and studied scalable implementation techniques for the transition to IPv6. Related research examined address allocation, protocol processing, and the operation of IPv6 networks.

This work later expanded to IPv6-only cloud infrastructure. We designed and operated an IPv6-only IaaS environment with IPv4/IPv6 translation, demonstrating how a data center can adopt IPv6 internally while retaining connectivity with existing IPv4 services. These studies established a continuing research approach: implement protocols in real systems, observe their operational behavior, and identify the changes required for dependable deployment.


### DNS Measurement and Secure Name Resolution

DNS is a distributed control infrastructure on which almost every Internet service depends. Our DNS research has covered both global observation and local operation. We measured root and country-code top-level-domain servers from multiple locations, analyzed DNS traffic at Internet service providers, and developed methods for evaluating server placement, reachability, response behavior, and performance.

We also investigated cache coordination, authentication-information management, and the security of name resolution. The **DNSSEC Simulator** allows operators to estimate the traffic and operational impact of DNSSEC before deploying it in a production environment. It uses real DNS implementations to reproduce realistic resolver and authoritative-server behavior, helping bridge the gap between protocol design and operational planning.

More recent work applies data analysis and machine learning to DNS operation, including server classification from response-message patterns and graph analysis of cache-server logs for detecting infected hosts.


### Internet Exchanges and Large-Scale Testbeds

Internet Exchanges provide a meeting point for many independently operated networks. Our work on **NSPIXP-3 / DIX-IE** treated the IX as both production infrastructure and a large-scale research testbed. It contributed knowledge about scalable switching, route exchange, traffic measurement, and the operational coordination required among multiple organizations.

The research later evolved into **PIX-IE**, a programmable Internet Exchange that investigated how Software-Defined Networking (SDN) could support flexible path control and new services at an IX. Recent work on **HolistIX** extended this direction toward zero-touch operation, using automation to reduce manual configuration and coordinate network services across an exchange.

We also participate in the design and operation of **Interop Tokyo ShowNet**. ShowNet provides a rare environment in which new protocols, high-speed links, routing systems, security mechanisms, telemetry tools, and multivendor equipment can be integrated at scale. Interoperability testing reveals operational problems that are difficult to reproduce in a small laboratory and turns practical experience into research questions.

<figure style="text-align: center; margin: 2rem 0;">
  <a href="{{ '/assets/images/shownet_topology.jpg' | relative_url }}">
    <img src="{{ '/assets/images/shownet_topology.jpg' | relative_url }}" alt="Example topology of the Interop Tokyo ShowNet" style="max-width: 780px; width: 100%; height: auto;">
  </a>
  <figcaption><em>Figure 1. An example ShowNet topology. A large multivendor testbed allows new network technologies to be evaluated under realistic design and operational constraints.</em></figcaption>
</figure>


### Programmable Networks: SDN and NFV

SDN separates network control from packet forwarding and makes network behavior programmable. Network Functions Virtualization (NFV) implements middleboxes and network services as software. Our research has examined how these concepts can improve carrier, campus, cloud, and data-center networks while remaining manageable in actual operation.

**GINEW** (General Integrated Network Engineering Workbox) proposed an operational architecture for controlling VPLS paths across multiple routers. It provided a graphical interface through which operators and users could change service paths while preventing configuration conflicts. The project demonstrated that network programmability must include configuration consistency, access control, and operational workflows, not only a centralized controller.

Related work proposed new SDN/NFV service architectures, process-based software middleboxes, and practical service chaining. **FlowFall** implemented service chaining with commodity technologies, while later operational studies evaluated NFV service chains in real environments. We also applied OpenFlow to area-limited multicast, monitoring networks, information-leak prevention, wireless access-point firewalling, and mobility management.

<figure style="text-align: center; margin: 2rem 0;">
  <a href="{{ '/assets/images/ginew1.jpg' | relative_url }}">
    <img src="{{ '/assets/images/ginew1.jpg' | relative_url }}" alt="GINEW interface for programmable network operation" style="max-width: 680px; width: 100%; height: auto;">
  </a>
  <figcaption><em>Figure 2. GINEW connected programmable path control with an operational interface, enabling VPLS services to be configured and managed across multiple network devices.</em></figcaption>
</figure>


### Cloud, Overlay, and Data-Center Networks

Virtualized infrastructure requires network services that can follow workloads across hosts, data centers, and administrative domains. Our research developed user-defined networks for IaaS clouds and studied the combination of LISP and VXLAN for route optimization across geographically distributed cloud platforms.

The **ovstack** architecture provided a common data plane for multiple overlay protocols. Related work investigated protocol-independent forwarding tables, NIC offloading, high-speed packet I/O, container networking, and Layer 3 multipathing with commodity equipment. These results reduce dependence on specialized hardware while preserving the performance and flexibility required by cloud infrastructure.

Our work has also addressed campus SD-WAN and network design across multiple sites. More recent results include an extension of Equal-Cost Multi-Path routing for hardware load balancing. Together, these studies connect forwarding mechanisms with deployment constraints such as hardware capabilities, failure handling, migration, and operational simplicity.


### Measurement, Monitoring, and Automation

Operators need continuous evidence about network state. We study the collection and analysis of traffic, routing, DNS, wireless, security, and system logs to identify failures and abnormal behavior before they affect many users.

Research outcomes include scalable time-oriented log search with **Hayabusa**, continuous collection and visualization of wireless base-station and client statistics, and behavioral methods for detecting scans and low-rate denial-of-service attacks. We also investigate how telemetry and machine learning can support diagnosis while keeping the reasoning available to human operators.

Automation in this project aims to shorten the path from observation to action. A dependable system must validate intended changes, deploy them with a limited impact radius, observe their effects, and provide a safe rollback path. This operational feedback loop connects network management research with our work on cybersecurity, cloud-native infrastructure, and AI-assisted operations.


### Research Through Real-World Operation

Our methodology treats deployment and operation as part of the research process:

1. Identify a limitation or recurring operational problem in a production network or testbed.
2. Define an architecture that separates policy, control, forwarding, and observable state.
3. Build a working implementation using standard protocols and deployable software.
4. Evaluate performance, fault behavior, interoperability, and operational workload.
5. Test the design with realistic traffic, equipment, and organizational constraints.
6. Feed the findings back to implementations, operators, vendors, and standards communities.

This cycle prevents an architecture from being evaluated only under ideal laboratory conditions. It also allows operational experience to generate new research questions in automation, observability, resilience, and security.


### Research Contributions

This research has produced contributions across several layers of network infrastructure:

1. implementation and operational validation of IPv6 technologies for hosts, clouds, and transition environments;
2. global and ISP-level DNS measurement, secure name-resolution mechanisms, and realistic DNSSEC deployment simulation;
3. design and operation of large Internet Exchange testbeds and programmable IX architectures;
4. SDN and NFV architectures for path control, service chaining, monitoring, and security;
5. overlay, multipath, and high-speed packet-processing mechanisms for cloud and data-center networks;
6. scalable collection, search, visualization, and analysis of operational telemetry; and
7. an engineering methodology that connects prototypes with multivendor interoperability and production operation.


### Toward Autonomous and Dependable Networks

Networks are becoming more distributed as cloud services, edge computing, mobile systems, and AI workloads interact. At the same time, encryption, software supply chains, and increasingly autonomous systems make failures and attacks harder to diagnose. Future network management must coordinate intent, identity, telemetry, and security policies across heterogeneous infrastructure.

Our next steps combine programmable data planes, streaming telemetry, digital twins, machine learning, and carefully controlled AI agents. The objective is an autonomous network that can recognize changes, explain their operational impact, recommend or execute bounded actions, and verify recovery without removing accountability from human operators.


### Selected Publications

- R. Nakamura, T. Okuzawa, K. Ebisawa, Y. Sekiya, and C.-H. Lee, “A Proposal of Hardware Load Balancer by Extending Equal-Cost Multi-Path,” *Journal of Information Processing*, Vol. 65, No. 3, pp. 635--645, 2024.
- C. Visser, S. Yamamoto, T. Tomine, Y. Sekiya, and M. Bruyere, “[HolistIX: A Zero-Touch Approach for IXPs](https://doi.org/10.23919/CNSM52442.2021.9615540){: target="_blank" },” *IEEE CNSM*, pp. 1--7, 2021.
- Y. Kuga, R. Nakamura, T. Matsuya, and Y. Sekiya, “NetTLP: A Development Platform for PCIe Devices in Software Interacting with Hardware,” *USENIX NSDI*, pp. 141--155, 2020.
- R. Nakamura, Y. Kuga, and Y. Sekiya, “[An Alternative Fast Packet I/O with Native System Calls](https://doi.org/10.1145/3341188.3341193){: target="_blank" },” *ACM CFI*, 2019.
- R. Nakamura, Y. Sekiya, and H. Tazaki, “[Grafting Sockets for Fast Container Networking](https://doi.org/10.1145/3230718.3230723){: target="_blank" },” *ACM ANCS*, pp. 15--27, 2018.
- K. Horiba, R. Nakamura, S. Suzuki, Y. Sekiya, and J. Murai, “Design and Operation of Service Chaining Using NFV,” *Information Processing Society of Japan Digital Practice*, Vol. 9, No. 4, 2018.
- R. Nakamura, K. Okada, Y. Sekiya, and H. Esaki, “[A Common Data Plane for Multiple Overlay Networks](https://doi.org/10.1016/j.comnet.2015.09.031){: target="_blank" },” *Computer Networks*, 2015.
- S. Yamamoto, R. Nakamura, Y. Ueno, K. Horiba, and Y. Sekiya, “[GINEW: A Novel Network Operation and Management Architecture](https://doi.org/10.11309/jssst.32.3_46){: target="_blank" },” *Computer Software*, Vol. 32, No. 3, pp. 46--57, 2015.
- Y. Sekiya, T. Ishihara, and H. Tazaki, “[DNSSEC Simulator for Realistic Estimation of Deployment Impacts](https://doi.org/10.1587/comex.3.305){: target="_blank" },” *IEICE Communications Express*, Vol. 3, No. 10, pp. 305--310, 2014.
- O. Nakamura, A. Kato, K. Hasebe, N. Morishima, Y. Sekiya, and N. Shigechika, “NSPIXP: A Large-Scale IX Testbed,” *IEICE Transactions on Communications*, Vol. J88-B, No. 10, pp. 1900--1909, 2005.
- H. Yoshifuji, K. Miyazawa, M. Nakamura, Y. Sekiya, H. Esaki, and J. Murai, “Linux IPv6 Stack Implementation Based on Serialized Data State Processing,” *IEICE Transactions on Communications*, Vol. E87-B, No. 3, 2004.

Please refer to the [Publications & Activities]({{ "/publications/" | relative_url }}) page for complete bibliographic information.
