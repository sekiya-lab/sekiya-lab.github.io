---
layout: page
title: Security DX
permalink: /researches/securitydx/
---

## Security DX

Digital communication has made social interaction faster and more convenient, but it has also created new opportunities for manipulation. Fraudulent investment offers, recruitment into criminal activity, misleading communities, and other harmful messages can exploit a person's desire for recognition, loneliness, peer pressure, or information overload. Short and fragmented messages may also conceal the wider context, legal implications, and risks needed for a calm decision.

The **Security DX** project studies these emerging **digital threats** through an interdisciplinary combination of cybersecurity, artificial intelligence, data analysis, and social psychology. Our goal is to understand how harmful communication affects human judgment, automatically assess its risks, and deliver timely, understandable warnings on the devices people use every day.

---

### Goal and Vision

Security DX aims to create a human-centered security mechanism that protects users across social media, messaging services, and web applications. The project has five goals:

- collect and organize real-world examples of malicious and misleading digital communication;
- identify the social and situational factors that make users susceptible to manipulation;
- develop AI models that assess harmful communication, misinformation, and contextual risk;
- implement an application-independent protection mechanism for smartphones and web browsers; and
- use research findings to strengthen cybersecurity literacy and security-by-design education.

The project connects technical detection with an understanding of human behavior. Rather than judging a message only by suspicious words or URLs, we investigate the relationship among message content, communication context, application characteristics, and the recipient's situation.


### What We Mean by Digital Threats

In this project, a digital threat is communication that exploits psychological conditions amplified by digital media and attempts to influence a person in a harmful direction. Such threats may not contain malware or an immediately verifiable falsehood. Their danger can emerge gradually through repeated interaction, social pressure, isolation, or a carefully constructed sense of trust and urgency.

Representative cases include:

- investment and financial fraud;
- recruitment for illegal or high-risk work;
- invitations to suspicious groups or communities;
- misinformation designed to provoke an unsafe decision; and
- manipulative exchanges that impair a user's ability to evaluate risk calmly.

This definition broadens cybersecurity beyond the protection of devices and accounts. It treats human judgment and well-being as essential parts of the security boundary.


### Research Architecture

#### Digital-Threat Intelligence Database

The first research component collects examples of harmful communication from social media, messaging applications, and documented fraud or solicitation cases. The database is designed to preserve the context in which an exchange occurred, not only the isolated message text.

Research data may include anonymized message content, application information, communication metadata, contextual descriptions, and labels indicating credibility or risk. These data provide a foundation for analyzing manipulation patterns and evaluating detection methods. Privacy protection, anonymization, access control, and responsible data governance are central design requirements.

#### Social and Behavioral Risk Analysis

Cybersecurity signals alone cannot fully explain why the same message may be harmless in one situation and dangerous in another. Security DX incorporates social-psychological analysis to investigate factors such as loneliness, recognition seeking, peer pressure, information overload, and the loss of contextual cues in online interaction.

This work supports a model of **situational risk**: an assessment of how message characteristics, interaction history, platform conditions, and human factors combine to increase the likelihood of manipulation. The objective is not to profile or blame users, but to recognize situations in which additional support may help them make an informed decision.

#### LLM- and SLM-Based Threat Assessment

The project initially uses large language models (LLMs) to analyze communication, infer missing context, and complement specialized threat indicators with broad linguistic and commonsense reasoning. The resulting prototype will help identify the minimum capabilities required for reliable risk assessment.

We then investigate how those capabilities can be transferred to a compact small language model (SLM). A lightweight model can execute locally or close to the user, reduce dependence on a remote service, limit unnecessary disclosure of private communication, and operate across different applications. Research challenges include accuracy, false alarms, explanation quality, model bias, adversarial manipulation, and changes in language and fraud tactics.

#### Digital Omamori: Application-Independent Protection

The primary system outcome is **Digital Omamori**, a digital guardian that combines the project's threat-assessment model with relevant knowledge from generative AI. It is envisioned as a smartphone security application or browser extension that monitors user-authorized digital communication, evaluates potential risk, and warns the user when an exchange may be suspicious.

Digital Omamori is designed to operate independently of a particular social network or messaging service. Instead of blocking communication automatically, it should present timely and understandable evidence that helps the user pause, reconsider the situation, and seek additional confirmation. User consent, privacy-preserving processing, explainable warnings, and human control are therefore fundamental to the design.


### Research Workflow

The project integrates its technical and human-centered research in the following cycle:

1. Collect and anonymize examples of malicious or misleading communication together with their context.
2. Analyze manipulation techniques and the social conditions associated with increased risk.
3. Construct a threat-intelligence database with credibility, risk, and contextual annotations.
4. Develop an LLM-based prototype for contextual threat assessment and explanation.
5. Distill the required capabilities into a lightweight SLM suitable for smartphones and browsers.
6. Implement Digital Omamori and evaluate its accuracy, usability, privacy, and effectiveness.
7. Feed the resulting cases and lessons into cybersecurity and professional education.


### Interdisciplinary Collaboration

Security DX brings together researchers and practitioners in cybersecurity, artificial intelligence, data collection and analysis, social psychology, and digital-service development. This collaboration enables the project to address the complete path from real-world observation to behavioral analysis, model development, system deployment, and education.

The research organization is intended to connect expertise across information science, information infrastructure, AI, secure information and communication technology, and the humanities and social sciences. Collaboration with industry contributes practical knowledge in security operations, AI engineering, and service deployment.


### Education and Social Implementation

Collected cases and research findings will support cross-disciplinary cybersecurity education. Students will learn not only how attacks work technically, but also how malicious communication exploits human behavior and how secure services should communicate risk to their users.

The project also envisions recurrent and reskilling education for working IT engineers in collaboration with external training organizations. The emphasis is on cultivating **security-native** professionals who can incorporate threat modeling, privacy, human factors, and security-by-design principles from the beginning of system development.


### Expected Contributions

Security DX is expected to produce:

1. a curated threat-intelligence database of malicious digital communication and its context;
2. an AI model for assessing manipulation, misinformation, and situational risk;
3. Digital Omamori, an application-independent protection mechanism for smartphones and browsers;
4. methods for explaining risk without removing user agency or generating excessive alarm;
5. interdisciplinary educational material based on real digital-threat cases; and
6. a framework for training security-native students and practicing engineers.


### Toward Human-Centered Digital Security

Digital transformation must be accompanied by safeguards that protect both information systems and the people who use them. Security DX therefore treats cybersecurity, AI, and social psychology as complementary disciplines. By converting real-world threat observations into data, models, protective tools, and education, the project seeks to prevent digital communication from being used to isolate, deceive, or manipulate individuals.

The long-term objective is a digital environment in which people can benefit from online communication while receiving trustworthy support at the moment a harmful interaction begins to influence their judgment.
