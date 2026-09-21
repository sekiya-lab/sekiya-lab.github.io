---
layout: page
title: NML
permalink: /researches/nml/
---

## NML (Network Machine **Muscle** Learning) Project

![NML]({{ "assets/images/NML.png" | relative_url }})

NML means **Network Machine Muscle Learning**. The project name reflects our goal of building cybersecurity technologies that do more than recognize known attack patterns: they must remain effective against evolving threats, limited observations, adversarial manipulation, and changes in real-world network environments.

**For more information, please refer to [https://nml.ai/](https://nml.ai/){: target="_blank" }.**

---

### Goal and Vision

The NML project studies the intersection of **machine learning, artificial intelligence, and cybersecurity**. Our goal is to develop practical methods for detecting, understanding, and mitigating cyber threats by learning from network traffic, DNS and URL data, security logs, threat intelligence, and observations from cyber-physical systems.

Machine-learning models for cybersecurity face challenges that differ from ordinary classification tasks. Attack data are scarce and highly imbalanced, new attacks may have only a few examples, network environments change over time, and attackers deliberately try to evade detection. A model that performs well on one benchmark dataset may therefore fail when deployed in another network or confronted with a previously unseen attack.

NML addresses these challenges throughout the AI security lifecycle: constructing and refining datasets, designing models with stronger generalization, explaining their decisions, evaluating adversarial weaknesses, and connecting detection results to deployable security controls.


### Research Themes

#### Generalizable Detection of Cyber Threats

We investigate models that learn the semantic and structural characteristics of malicious activity instead of relying only on manually selected indicators. Recent work on phishing detection combines a fine-tuned BERT model with external features obtained from public Internet resources. This multimodal design improves cross-dataset generalization and supports detection when phishing techniques and URL distributions change over time.

Our research also explores emerging learning paradigms, including quantum machine learning, to evaluate their applicability and limitations for phishing URL detection.

#### Data Quality, Synthetic Data, and Few-Shot Learning

Cybersecurity datasets often contain severe class imbalance: normal traffic is abundant, while important attacks may have very few samples. NML develops methods for producing reliable training data without obscuring the characteristics of rare attacks.

**TabRefine** is a post-processing framework that improves synthetic tabular data for network intrusion detection. Related work investigates diffusion-based generation of multi-class IDS datasets. In 2026, we proposed **STSMOTE**, a controllable data augmentation method for few-shot zero-day attack detection. Unlike black-box generation alone, STSMOTE uses geometric parameters to control where synthetic samples are generated, emphasizing reliability and interpretability in security-sensitive settings.

#### Explainable AI and Adversarial Robustness

AI-based security mechanisms must themselves be treated as attack targets. We study how explanations produced by XAI can reveal the features that influence a network intrusion detector and how an adversary can exploit this information to construct feasible evasive traffic. Our work has progressed from XAI-driven adversarial attacks to black-box settings that better reflect operational conditions.

We also evaluate physical adversarial attacks against industrial AI vision systems. This extends NML beyond conventional network traffic analysis and examines how small physical changes can mislead AI components used in factory automation and other cyber-physical systems.

#### Security Controls for AI-Enabled Infrastructure

Detection alone is not sufficient. NML also studies mechanisms that limit the impact of compromise. Our container micro-segmentation research applies a zero-trust policy inside Kubernetes Pods: communication is denied by default and allowed only for explicitly specified container-port pairs. This work connects AI-driven monitoring and analysis with enforceable controls for modern cloud-native infrastructure.


### Research Approach

NML combines data-driven analysis with knowledge of network protocols, system architecture, and attacker behavior. Our research cycle consists of the following activities:

1. Collect and curate network traffic, DNS, URL, log, malware, and cyber-physical observations.
2. Measure dataset bias, class imbalance, distribution shift, and the fidelity of synthetic data.
3. Develop machine-learning and deep-learning models for detection, classification, and prediction.
4. Use explainable AI to analyze model decisions and expose security weaknesses.
5. Evaluate models against evasion, black-box, physical, and zero-day attack scenarios.
6. Translate analytical results into practical controls for network and cloud-native systems.

This approach treats AI not only as a defensive tool, but also as a component whose reliability, explainability, and attack surface must be evaluated.


### Recent Research Outcomes (2024--2026)

- **[Few-shot zero-day attack detection (2026)](https://www.thinkmind.org/download_full.php?instance=ICIMP+2026){: target="_blank" }:** STSMOTE provides controllable data augmentation for highly imbalanced NIDS datasets and attack classes with very few observations.
- **[Container micro-segmentation (2026)](https://doi.org/10.1007/978-3-032-17443-7_15){: target="_blank" }:** a zero-trust mechanism enforces container-level communication policies inside Kubernetes Pods.
- **[Synthetic IDS data refinement (2025)](https://doi.org/10.1109/BigData66926.2025.11402086){: target="_blank" }:** TabRefine improves the usefulness of generated tabular data through post-processing tailored to network intrusion detection.
- **[Generalizable phishing detection (2025)](https://doi.org/10.1109/ACCESS.2025.3591843){: target="_blank" }:** a fine-tuned BERT-based multimodal model combines URL representations with external Internet features.
- **[Adversarial security for industrial AI (2025)](https://doi.org/10.1109/CCNCPS66785.2025.11135836){: target="_blank" }:** physical adversarial attacks demonstrate risks to AI vision systems used in factory automation.
- **Black-box attacks against AI-based NIDS (2025):** XAI-guided techniques are extended to more realistic black-box attack conditions.
- **Interpretable phishing URL detection (2024):** fine-tuned BERT is evaluated as an interpretable alternative to conventional feature engineering.
- **[XAI-driven attacks against NIDS (2024)](https://doi.org/10.1145/3655693.3655714){: target="_blank" }:** model explanations are used to identify influential features and generate feasible adversarial network traffic.

Please refer to the [Publications & Activities]({{ "/publications/" | relative_url }}) page for complete bibliographic information.


### From the Original NML Concept to the Current Project

The original NML project combined large-scale network and security datasets with social information to support reactive detection and proactive prediction of cyber threats. That vision remains important, but the project has expanded as AI has become a core part of operational security systems.

Today, NML focuses on the entire relationship between AI and cybersecurity: using AI to detect attacks, improving the data used to train security models, examining attacks against AI itself, and designing infrastructure that can contain threats when detection is imperfect. The project continues to pursue cybersecurity technologies that are accurate, explainable, robust, and deployable in real networks.

