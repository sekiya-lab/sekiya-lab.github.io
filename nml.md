---
layout: page
title: NML
permalink: /nml/
---

NML (Network Machine **Muscle** Learning) Project
{: .display-6 }

![NML]({{ "assets/images/NML.png" | relative_url }}) NML means Network Muscle Learning, not Machine Learning!

**For more information, please refer to [https://nml.ai/](https://nml.ai/)**

### Goal and Background

The goal of this project is to make proactive cyber defenses in real-time using various and massive log datasets from network infrastructure and social information. In this research, we analyze cyber security big data in order to prevent facilities from cyber threats. This research is characterized by employing both a reactive and proactive approach to cyber security. The former can be defined as an analysis of cyber threats with online learning algorithms, and the latter is the prediction of future attacks. The key feature of our reactive approach is to extract knowledge from cyber security big data with a convolutional neural network. In our prior work, we have construct cybersecurity big data, which is comprised of sampled network traffic, DNS queries, a content of malware and malicious websites, and so much on. We have also attempted to extract knowledge from the big data with some heuristics. For example, our collected data were compared with the discrimination threshold which was given by our empirical network operations. Herein, we will adopt deep learning technologies to extract knowledge automatically. In addressing to mitigate cyber threats and risks, a proactive approach is also necessary as well as a reactive approach, due to that cyber security needs to be handled in a very short time period. If we could predict future cyber threats targeted to us and/or our organization, we would earn time for incident handling; it will helpful for providing better cyber security against the threats. The key feature of our proactive approach is to analyze social data with natural language processing and machine learning algorithms. The motivation of the attacks explicitly exists and is along with social trends. Text information extracted by SNS such as Twitter, Facebook, blogs, and news articles can be regarded as the context of the message was reflected by this motivation.

### Member

This project is joint research of The University of Tokyo, Nara Institute of Science and Technology (NAIST), Tokyo Institute of Technology (TITECH), and IIJ Innovation Institute.

### Significance of this Research

Cybersecurity, which aims at protecting cyber spaces from cyber threats, becomes one of the most important research agenda for the Internet. Enterprise organizations must be aware of devices that connect to an enterprise network and should collect information for detecting network anomaly. However, due to the rapid increase in the numbers of connected devices, organizations are required to analyze the large amount and diverse kinds of data in real-time; the analysis results should be outputted with small latency. Our work aims at solving this issue by the reactive and proactive approach. The former is needs to be automated, and artificial intelligence has begun to garner attention. However, due to the limited computational resources, it is really hard to analyze cyber threat big data in short time period. Our research aims at solving this issue by employing JHPCN’s analysis nodes. The latter, a proactive approach is necessary for each time for preparing against cyber attacks. Our social analysis will reveal the attacker’s motivation and future generated threats.

### Example Idea

In this collaborative research, The University of Tokyo (U-TOKYO) team has experience in constructing cyber security big data. The Nara Institute of Science and Technology (NAIST) team is the expert in extracting trends from SNS (Twitter) data. In this collaborative research, all members utilized a partner’s experience, analyze cyber security big data, and develop both reactive and proactive algorithms. As a prototype of the analysis, Figure 1 shows the procedure of this analysis. In this figure, the data collection is performed at NAIST and the data is transferred and stored in U-TOKYO storage. In U-TOKYO we try to analyze the relationship with the SNS data and traffic data, then try to make predictions of attacks.

![Figure SNS]({{ "assets/images/nml_figure-SNS.png" | relative_url }})

A method for data mining is a key issue for extracting knowledge from datasets. We try to run the convolutional neural network (CNN) to solve this issue as shown figure below. For example, we would like to analyze with deep learning for network traffic and time series prediction. A packet itself is a variable length, however, each packet can be interpreted as 5 tuples information, e.g., source address, destination address, source port number, destination port number, and time. It means, we can generate a high-dimensional matrix. We will recognize outliers, tendency, and predominant patterns in order to predict potential cyber attacks from cyber threat big data.

![Figure CNN]({{ "assets/images/nml_figure1-1.png" | relative_url }})

### Implementation

As a first our achievement, we publish a simple and fast full-text search engine for massive system datasets. The name is “Hayabusa”. You can get and try the software from [this site](https://github.com/hirolovesbeer/hayabusa). In this software, we provide the base infrastructure for analysis of massive datasets.

