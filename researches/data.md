---
layout: page
title: Data Synthesis for Cybersecurity
permalink: /researches/data/
---

## Data Synthesis for Cybersecurity

Machine learning has become an important component of network monitoring and cyberattack detection. Its performance, however, depends heavily on the quality and diversity of the data used for training. In operational networks, normal traffic is abundant, while samples of attacks—especially new, rare, or targeted attacks—are difficult to collect. Security datasets are therefore often highly imbalanced, incomplete, and affected by differences between the environment in which they were collected and the environment in which a model is deployed.

Our research develops **synthetic-data generation, refinement, and augmentation methods for cybersecurity**. The objective is not simply to increase the number of training records. We aim to preserve the characteristics of real network traffic, represent minority attack classes faithfully, and improve the ability of detection models to recognize previously unseen attacks.

---

### Goal and Vision

The goal of this project is to establish a dependable data foundation for AI-based cybersecurity. We study methods that make security data:

- **Balanced:** rare but important attacks are sufficiently represented during training.
- **Faithful:** synthetic records preserve the statistical and structural properties of real traffic.
- **Diverse:** generated data cover variations that are difficult to observe in a limited real dataset.
- **Controllable:** researchers can understand and adjust where synthetic samples are generated.
- **Useful:** data quality is evaluated by its contribution to downstream intrusion-detection performance.
- **Privacy-conscious:** useful training data can be developed while reducing unnecessary dependence on raw operational data.


### Why Cybersecurity Needs Synthetic Data

Collecting comprehensive attack data from real networks is inherently difficult. Successful attacks are uncommon, zero-day attacks have few or no labeled examples, and sensitive traffic cannot always be shared among organizations. Even when public intrusion-detection datasets are available, their class distributions, protocols, devices, and attack patterns may differ from those of a deployment environment.

Simple duplication of minority samples does not create new information. At the same time, unconstrained generative models may produce records that look statistically plausible but violate relationships among network features or blur the boundaries between attack classes. Synthetic security data must therefore be evaluated from both a **data-fidelity perspective** and a **detection-utility perspective**.


### Core Research Principles

#### Generation for Imbalanced Security Data

We apply oversampling, autoencoders, diffusion models, and other generative techniques to tabular network-flow data. These methods learn representations of network behavior and generate additional samples for attack classes that are underrepresented in the original dataset.

#### Preservation of Multiple Attack Classes

A practical intrusion-detection dataset contains several attack categories with different feature distributions. Our research investigates generation methods that preserve class-specific characteristics instead of treating all malicious traffic as a single category. This is particularly important for distinguishing rare attacks from both normal traffic and other attacks.

#### Post-Processing and Quality Refinement

Generation alone does not guarantee useful data. Synthetic records may contain unrealistic feature combinations, excessive overlap between classes, or samples that provide little value to a classifier. We therefore develop post-processing methods that refine generated tabular data after synthesis and improve its contribution to network intrusion detection.

#### Controllable and Explainable Augmentation

For security-critical applications, researchers and operators need to understand how synthetic samples are created. We study geometric and model-based controls that determine the location and diversity of generated samples. This approach helps avoid opaque augmentation and enables systematic analysis of the relationship between synthetic data and detection boundaries.

#### Evaluation by Downstream Detection

Synthetic data are evaluated not only with statistical similarity metrics but also through the performance of models trained with the augmented datasets. Detection rate, false positives, class-level performance, robustness to distribution shifts, and the ability to identify unseen attacks are central evaluation criteria.


### Evolution of the Research

#### 2021: Representation Learning and SMOTE

The first stage combined a convolutional autoencoder with the Synthetic Minority Oversampling Technique (SMOTE). The autoencoder learned a compact representation of network traffic, while SMOTE augmented minority attack samples in the learned feature space. This work demonstrated that representation learning and data augmentation can be combined to address class imbalance in cyber intrusion detection.

The results were published as **A Convolutional Autoencoder Based Method with SMOTE for Cyber Intrusion Detection** at the 2021 IEEE International Conference on Big Data.

#### 2025: Diffusion-Based Multi-Class IDS Data Generation

The next stage investigated diffusion models for generating multi-class intrusion-detection datasets. Diffusion-based generation provides a flexible way to model complex tabular distributions and generate samples for multiple attack classes. The research examined whether the generated records preserve the characteristics required for training multi-class IDS models.

This work was presented as **[拡散モデルを用いた多クラスIDSデータセット生成手法の検討](https://ken.ieice.org/ken/program/index.php?tgid=IEICE-IN&tgs_regid=4d814b872960fd02e954bd500fdb3b49e11ec0f7a423aaa7f97ffb68a5e6af4b){: target="_blank" }** at the IEICE Network Systems Technical Committee in 2025.

#### 2025--2026: TabRefine—Improving Synthetic Tabular Data

Based on the observation that generative models can produce imperfect or ambiguous samples, we developed **TabRefine**, a post-processing framework for synthetic tabular data. TabRefine separates data generation from quality improvement and refines generated samples for their intended use in network intrusion detection.

The framework evaluates and improves synthetic data from the perspective of downstream IDS performance. This makes it possible to enhance generated datasets without redesigning each underlying generator and provides a reusable layer between data synthesis and classifier training.

The results were published as **[TabRefine: A Post-Processing Framework for Enhancing Synthetic Tabular Data in Network Intrusion Detection Systems](https://doi.org/10.1109/BigData66926.2025.11402086){: target="_blank" }** at the 2025 IEEE International Conference on Big Data. The research was further consolidated in a 2026 master's thesis on post-processing for synthetic tabular data quality improvement in network intrusion detection systems.

#### 2026: STSMOTE for Few-Shot Zero-Day Attack Detection

The latest stage addresses attack classes for which only a very small number of observations are available. **STSMOTE** is a controllable data-augmentation method for few-shot zero-day attack detection. Rather than relying exclusively on a black-box generator, the method uses geometric parameters to control the region in which synthetic samples are produced.

This design emphasizes reliability and interpretability. It allows researchers to examine how augmentation changes the decision boundary and to avoid generating samples in regions that may confuse normal and malicious traffic. The work extends our data-synthesis research from general class imbalance toward the more demanding problem of learning from scarce examples of previously unseen attacks.


### Research Contributions

Across these studies, the project has produced the following contributions:

1. Integration of learned traffic representations with minority-class oversampling for intrusion detection.
2. Application of diffusion models to multi-class network intrusion-detection data.
3. A generator-independent post-processing framework for improving synthetic tabular data.
4. Evaluation of synthetic data through both fidelity measures and downstream detection performance.
5. Controllable augmentation for few-shot and zero-day attack scenarios.
6. A research methodology that connects data generation, quality analysis, model training, and security evaluation.


### Toward Trustworthy Security Data Engineering

Future cybersecurity systems will need to learn continuously from distributed and rapidly changing environments. Our next research steps include generating realistic IoT and DDoS traffic from operational traces, adapting synthetic datasets to new network environments, preserving temporal and protocol relationships, measuring privacy leakage, and detecting low-quality or harmful synthetic samples automatically.

We also plan to investigate how generative AI and autonomous agents can assist with dataset construction while maintaining provenance, reproducibility, and human oversight. The long-term objective is a trustworthy security-data engineering platform that can collect, generate, refine, validate, and share data for AI-based defense without losing the operational meaning of network activity.


### Publications

- Xinyi She and Yuji Sekiya, “A Convolutional Autoencoder Based Method with SMOTE for Cyber Intrusion Detection,” 2021 IEEE International Conference on Big Data, pp. 2565--2573, 2021.
- 石井 悠人, 明石 邦夫, and 関谷 勇司, 「拡散モデルを用いた多クラスIDSデータセット生成手法の検討」, 電子情報通信学会技術研究報告, Vol. 124, No. 419, pp. 450--455, 2025.
- Haruto Ishii, Kunio Akashi, and Yuji Sekiya, “TabRefine: A Post-Processing Framework for Enhancing Synthetic Tabular Data in Network Intrusion Detection Systems,” 2025 IEEE International Conference on Big Data, pp. 7803--7813, 2025.
- 石井 悠人, 「ネットワーク侵入検知システムにおける合成表形式データ品質改善のための後処理フレームワーク」, 東京大学大学院情報理工学系研究科修士論文, 2026.

Please refer to the [Publications & Activities]({{ "/publications/" | relative_url }}) page for complete bibliographic information.
