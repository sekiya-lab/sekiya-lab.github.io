---
layout: page
title: Researches
permalink: /researches/
---

## Ongoing Projects

SEKIYA laboratory is now working on the following topics.

- NEDO 受託研究「[ポスト5G情報通信システム基盤強化研究開発事業／ポスト5G情報通信システムの開発（委託）／（f1）超分散コンピューティング技術の開発](https://www.nedo.go.jp/activities/ZZJP_100172.html){: target="_blank" }」
- 科研費「トラフィックの時空間特徴量に着目した DoS 耐性 IoT アーキテクチャの研究」
- ソフトバンク共同研究「ステートレスかつセキュアな次世代モバイルコア実現に向けた研究開発」
- 総務省受託研究「ISPにおけるネットワークセキュリティ技術の導入に関する調査」
- AITAC 共同研究「次世代 IT インフラエンジニア育成に向けたカリキュラムと演習環境の構築」
- 東京大学 SI センター「サイバーセキュリティ教育プログラム」

- [NML Project](/researches/nml/)

---

## Next Architecture of Mobile Core Network

(TBD)


---

## Network Cyber Security

Network Security is an essential keyword in the current Internet and mandatory for the Internet. We can observe DDoS attacks, spoofing attacks, and brute-force attacks every day. In these surrounding situations, [NECOMA Project](http://www.necoma-project.jp/){: target="_blank" } was started. It is a joint research project of EU and JP. We, SEKIYA lab, join the project from the Japanese side. The project was funded by the [Ministry of Internal Affairs and Communications](https://www.soumu.go.jp/english/){: target="_blank" }. The NECOMA Project was finished in 2017 and [NML Project](https://nml.ai/){: target="_blank" } was started, taking over NECOMA Project. NML Project was funded by [JST CREST](https://www.jst.go.jp/kisoken/crest/project/1111094/1111094_2017.html){: target="_blank" }.

NECOMA addresses the aspect of **data collection** , leveraging past and current work on the topic with the goal to expand these existing mechanisms and orient them towards threat data analysis.

Second, it addresses **threat data analysis** not only from the perspective of understanding attackers and vulnerabilities but also from the point of view of the target and victim, needing to protect itself in real-time and in the most efficient manner possible; this will be achieved through the development of metrics that allow measuring the impact of attacks on the protected infrastructure or endpoint.

Third, it aims to **develop and demonstrate new cyber defense mechanisms** that leverage these metrics for deployment and evaluation.

These three aspects will be analyzed both from an infrastructure perspective (networks and large computing infrastructures) and endpoints (smartphones and browsers). The results of the NECOMA project will be showcased in demonstrators that will highlight the innovations of the project and prepare exploitation.

[![necoma]({{ "assets/images/necoma.png" | relative_url }}){: class="thumb" }]({{ "assets/images/necoma.png" | relative_url }})


---

## Next Generation NSP Consortium (Finished)

[This consortium](http://www.next-nsp.org/){: target="_blank" } was established in 2014 and our laboratory is tightly involved in the activities. The goals of this consortium are

- designing the architecture for next generation network infrastructure,
- evaluating the technologies for software-defined infrastructure, and
- building the scalable architecture to support the network infrastructure.

Over 30 companies are joined the consortium and work for evaluating software-defined technologies and virtualization architecture for network services.

[![NSP Goals]({{ "assets/images/NSP6.jpg" | relative_url }}){: class="thumb" }]({{ "assets/images/NSP6.jpg" | relative_url }})
[![NSP Collaboration]({{ "assets/images/NSP11.jpg" | relative_url }}){: class="thumb" }]({{ "assets/images/NSP11.jpg" | relative_url }})
[![NSP Concepts]({{ "assets/images/NSP7.jpg" | relative_url }}){: class="thumb" }]({{ "assets/images/NSP7.jpg" | relative_url }})


---

## Distributed Cloud Computing

We are working on the fundamental and infrastructure technologies for Cloud Computing. Especially resource management, distributed filesystem, monitoring method, and network virtualization. Integrating these research, we construct and operate the real IaaS cloud, called "[WIDE Cloud](http://wcc.wide.ad.jp/){: target="_blank" })". The testbed is IaaS cloud and distributed IaaS cloud connected universities and research organizations. The cloud is a testbed for new technologies and ideas with the actual user. Over hundred users are joined in the cloud and operate over 400 VMs. The project was originally supported by [Ministry of Economy, Trade and Industry](https://www.meti.go.jp/){: target="_blank" }. The project is collaborated with [NICT](https://www.nict.go.jp/){: target="_blank" }/[JGN-X](https://testbed.nict.go.jp/){: target="_blank" }.

We have papers about resource management, distributed filesystem, and network virtualization.

[![closer-poster]({{ "assets/images/closer-poster.png" | relative_url }}){: class="thumb" }]({{ "assets/images/closer-poster.png" | relative_url }})
[![yanjue-poster]({{ "assets/images/yanjue-poster.png" | relative_url }}){: class="thumb" }]({{ "assets/images/yanjue-poster.png" | relative_url }})

[![WIDE Cloud overview]({{ "assets/images/widecolud_overview.jpg" | relative_url }}){: class="thumb" }]({{ "assets/images/widecolud_overview.jpg" | relative_url }})
[![WIDE Cloud tech]({{ "assets/images/widecolud_tech.jpg" | relative_url }}){: class="thumb" }]({{ "assets/images/widecolud_tech.jpg" | relative_url }})
[![WIDE Cloud challenges]({{ "assets/images/widecolud_challenges.jpg" | relative_url }}){: class="thumb" }]({{ "assets/images/widecolud_challenges.jpg" | relative_url }})
[![WIDE Cloud wcc]({{ "assets/images/widecolud_wcc.jpg" | relative_url }}){: class="thumb" }]({{ "assets/images/widecolud_wcc.jpg" | relative_url }})


---

## Software Defined Networking (SDN)

We are working on SDN for management of data center networks, cloud networks and carrier networks. One of the most effective usages of SDN is a path control of carrier networks and enterprise networks. The project called "[GINEW](http://wp.ginew.net/){: target="_blank" }" is an Open Source SDN implementation developed with [KEIO University](https://www.sfc.keio.ac.jp/){: target="_blank" } and [NICT](https://testbed.nict.go.jp/){: target="_blank" }. GINEW stands for “General Integrated Network Engineering Workbox”. The SDN framework can control VPLS path on several routers and provide GUI for users. Administrators and users can switch VPLS path easily and avoid conflictions of VPLS configs.

[![ginew1]({{ "assets/images/ginew1.jpg" | relative_url }}){: class="thumb" }]({{ "assets/images/ginew1.jpg" | relative_url }})
[![ginew2]({{ "assets/images/ginew2.jpg" | relative_url }}){: class="thumb" }]({{ "assets/images/ginew2.jpg" | relative_url }})

Also we are working on applying OpenFlow for GeoCasting. The proposed usage is a emergency notification of earthquake prediction. If the OpenFlow switch has the Geoinformation such as GPS, we can send an emergency notification with a range of latitude and longitude. The basic idea and elementary results of simulation was published as papers.

[![Area Limited Multicast with OpenFlow]({{ "assets/images/Area-Limited-Multicast-with-OpenFlow.png" | relative_url }}){: class="thumb" }]({{ "assets/images/Area-Limited-Multicast-with-OpenFlow.png" | relative_url }})


---

## DNSSEC Simulator

In order to protect DNS answers from spoofing and attacking DNSSEC is useful and important. However, DNSSEC is not easy to introduce into existing DNS environments. Operators should pay more costs for signing zones and managing keys. Moreover, the amount of traffic will grow when DNSSEC is introduced because the size of DNSSEC messages is bigger than no DNSSEC messages.

Before introducing and deploying DNSSEC into existing DNS servers, operators and administrators may want to evaluate the operational costs and estimate the growth of DNS traffic. On the other hand, there is no good tool and simulator to evaluate the effects of introducing DNSSEC into existing environments, so we would like to provide a DNSSEC simulation software for DNS operators and administrators. This is the motivation of starting this project. This project is funded by Grant-in-Aid for Scientific Research (C) by [Japan Society for the Promotion of Science (JSPS)](https://www.jsps.go.jp/){: target="_blank" }

The project has its [project page](https://dnssec.sekiya-lab.info/){: target="_blank" } and a demo movie uploaded on youtube.

<iframe width="560" height="315" src="https://www.youtube.com/embed/GUUurmUNdds?si=Jp-73vUM-35Y0tD5" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>


---

### Network Architecture, Operation, and Management

The network is an infrastructure for communications. It should be redundant and flexible for users. It also should be manageable and feasible for network administrators and operators. We are working on the automation of network management, monitoring, and troubleshooting. We positively join the events for testing interoperability of new network technologies such as [Interop Tokyo](https://www.interop.jp/){: target="_blank" }, and make feedback to network vendors and standards body such as [IETF](https://www.ietf.org/){: target="_blank" }. We intend both of theoretical and practical research.

We also join in the operation and research of Internet Exchanges, called [DIX-IE / NSPIXP-3](http://nspixp.wide.ad.jp/){: target="_blank" }. In these IXes, we try to collect real and practical statistical data and try to apply the data for research of DDoS mitigation.

![ShowNet Topology]({{ "assets/images/shownet_topology.jpg" | relative_url }}){: class="thumb" }
![Network Equipment]({{ "assets/images/network_equipment.jpg" | relative_url }}){: class="thumb" }
