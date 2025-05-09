---
title: European Digital Identity Wallet
subtitle: Architecture and Reference Framework
...

# Architecture and Reference Framework

## 1 Introduction

### 1.1 Context

On 3 June 2021, the European Commission adopted a Recommendation ([COMMISSION
RECOMMENDATION (EU) 2021/946 of 3 June 2021 on a
[Common Union Toolbox](https://digital-strategy.ec.europa.eu/en/policies/eudi-wallet-toolbox)
for a coordinated approach towards a [European Digital Identity Framework](https://eur-lex.europa.eu/eli/reco/2021/946),
 [OJ L 210/51, 14.6.2021](https://eur-lex.europa.eu/legal-content/EN/TXT/HTML/?uri=OJ%3AL%3A2021%3A210%3AFULL))
calling on Member States to work closely together with the Commission towards
the development of a Toolbox including a technical Architecture and Reference
Framework (hereinafter the ARF), a set of common standards and technical
specifications and a set of common guidelines and best practices.

The Recommendation specifies that these outcomes will serve as a basis for the
implementation of the [European Digital Identity Regulation],
without the process of developing the Toolbox interfering with, or prejudging
the legislative process.

The Recommendation establishes a structured framework for cooperation between
Member States, the Commission, and, where relevant, private sector operators to
develop the Toolbox. The European Digital Identity Cooperation Group (EDICG),
formerly known as the eIDAS Expert Group, is responsible for:

- exchange best practices and cooperate with the Commission on emerging
policy initiatives in the field of digital identity wallets, electronic
identification means and trust services;
- advising the Commission in the preparation of draft implementing and delegated
acts;
- supporting Supervisory Bodies in the implementation of the [European Digital
Identity Regulation];
- organising peer reviews of electronic identification schemes;
- engaging with the Commission and other relevant stakeholders to develop a
[Common Union Toolbox](https://digital-strategy.ec.europa.eu/en/policies/eudi-wallet-toolbox);

The European Digital Identity Cooperation Group's page can be found [at the
official page](https://digital-strategy.ec.europa.eu/en/policies/european-digital-identity-cooperation-group).

The European Digital Identity Cooperation Group has since further developed the
concepts and specifications for the European Digital Identity Framework. The
current ARF version is based on the legal text adopted by the
co-legislators, including the adopted Commission Implementing Regulations:

- [CIR 2024/2977](https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=CELEX:32024R2977)
regarding PID and EAA,
- [CIR 2024/2979](https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=OJ:L_202402979)
regarding integrity and core functionalities,
- [CIR 2024/2980](https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=OJ:L_202402980)
regarding ecosystem notifications,
- [CIR 2024/2981](https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=OJ:L_202402981)
regarding certification of Wallet Solutions,
- [CIR 2024/2982](https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=OJ:L_202402982)
regarding protocols and interfaces.

### 1.2 Purpose of this document

The purpose of this document is to explain the architecture of the EUDI Wallet
ecosystem and all of its components, as well as how these components will interact
to ensure the security of the ecosystem and the privacy of its Users. Also, it
serves as background information to allow a better understanding of the the
high-level requirements established in Annex 2.

Additionally, this document forms a reference to create uniform conditions for
the implementation of the [European Digital Identity Regulation] and to define
the technical specifications, standards and procedures that the Commission will
develop for the purpose of implementing this Regulation.

Finally, this document is used to develop the Wallet Solution [reference implementation](https://github.com/eu-digital-identity-wallet/.github/blob/main/profile/reference-implementation.md).

The document presents a state-of-play of ongoing work of the European Digital
Identity Cooperation Group and does not imply any formal agreement regarding its
content. This document will be complemented and updated over time through the
process of establishing the toolbox, as described in [Chapter 8](#8-document-development).

This document holds no legal value and does not prejudge the final mandatory
legal requirements for the EUDI Wallet ecosystem. Only the adopted [European
Digital Identity Regulation], and the implementing and delegated acts adopted
under that Regulation, are mandatory. This document serves as a foundation for
regularly updating the implementing acts, ensuring alignment with technological
and standards developments.

### 1.3 Relation to the Large-Scale Pilots (LSP)

To support the development of a reference implementation of a Wallet Solution
and to pilot its usage across different priority use cases, the Commission
launched a call for proposals on 22 February 2022 under the Digital Europe
Programme to pilot use cases for the EUDI Wallet ecosystem at a large scale.

The objective of the Large-Scale Pilots (LSP) call is to support the piloting of
the EUDI Wallet ecosystem around a range of use cases involving both public and
private sector stakeholders. The LSPs will test the EUDI Wallet ecosystem in
both national and cross-borders contexts and integrate with the iterative
development of the reference application.

The works of the LSPs will be aligned with the ARF, which will guide pilot
system design and architecture development together with the release of the
reference implementation.

The LSPs are expected to provide feedback on the ARF as they develop and
interact with Relying Party services, Qualified or non-qualified Electronic
Attestations of Attributes (Q)EAA Providers, Person Identification Data (PID)
Providers, Qualified and non-qualified Trust Service Providers and Users in
meaningful interactions under the proposed use cases.

### 1.4 Definitions

The definitions used in this document can be found in Annex 1 of this document.

### 1.5 Scope

The **EUDI Wallet Architecture and Reference Framework (ARF)** document defines
the structural and functional aspects of the EUDI Wallet ecosystem, detailing
its key components and their interactions. It provides a technical foundation to
ensure **interoperability, security, and privacy**, aligning with the high-level
requirements specified in **Annex 2**. The ARF serves as a reference for the
**harmonised implementation of the [European Digital Identity Regulation]**,
guiding the development of **technical specifications, standards, and operational
procedures**.

This document **only applies to EUDI Wallet ecosystems compliant with the
[European Digital Identity Regulation]**, ensuring consistency in architecture
and implementation. It is designed to support the development of the Wallet
Solution reference implementation while remaining adaptable to technological and
regulatory advancements.

### 1.6 Change log

In this version of the ARF,

- relevant text from the [Discussion Paper for Topic D](./discussion-topics/d-embedded-disclosure-policies.md)
(Embedded disclosure policies) was included in [Sections 6.6.2.7](#6627-provisioning-embedded-disclosure-policies)
and [6.6.3.4](#6634-wallet-unit-evaluates-embedded-disclosure-policy-if-present). The High-Level Requirements introduced in this discussion paper were included in Annex 2 in [Topic 43](./annexes/annex-2/annex-2-high-level-requirements.md#a2343-topic-43---embedded-disclosure-policies).
- relevant text from the [Discussion Paper for Topic C](./discussion-topics/c-wallet-unit-attestation.md)
(Wallet Unit Attestation) was included in [Section 6.5.3.4](#6534-wallet-provider-issues-one-or-more-wallet-unit-attestations-to-the-wallet-unit), as well as other sections. However, only limited changes were made. The High-Level Requirements introduced and changed in this discussion paper were included in Annex 2 in [Topic 9](./annexes/annex-2/annex-2-high-level-requirements.md#a239-topic-9---wallet-unit-attestation). Other High-Level Requirements that used to be in Topic 9 were moved elsewhere, mainly to [Topic 40](./annexes/annex-2/annex-2-high-level-requirements.md#a2340-topic-40---wallet-instance-installation-and-wallet-unit-activation-and-management).
- relevant text from the [Discussion Paper for Topic G](./discussion-topics/g-zero-knowledge-proof.md) (Zero-Knowledge Proofs) was included in [Section 7.4.3.5.3](#74353-zero-knowledge-proofs). The High-Level Requirements introduced in this discussion paper were included in Annex 2 in [Topic 53](./annexes/annex-2/annex-2-high-level-requirements.md#a2353-topic-53-zero-knowledge-proofs).
- relevant text from the [Discussion Paper for Topic V](./discussion-topics/v-pid-rulebook.md) (PID Rulebook) was included in [Section 5.3](#53-attestation-formats-and-proof-mechanisms). Furthermore, high-level requirements and a specification of the encoding and format of [SD-JTW VC]-based PIDs were added to the [PID Rulebook](./annexes/annex-3/annex-3.01-pid-rulebook.md).

Apart from these changes, a limited number of editorial mistakes were corrected.

### 1.7 Additional topics

In this version of the ARF, several key areas still require further
exploration and refinement. These topics will be discussed in collaboration with
Member States, the European Digital Identity Cooperation Group, civil society,
industry representatives, and professionals, ensuring comprehensive feedback
from all relevant stakeholders. The outcomes of these discussions will be
incorporated into future versions of this ARF. The document will be iteratively
updated to improve its content and address emerging topics, with the process for
providing feedback and details on how updates will be managed outlined in
[Chapter 8](#8-document-development).

Among the areas identified for further discussion are:

- Relying Party registration.

Other topics that will be developed include:

- transaction logs maintained by the Wallet Unit,
- scenarios involving a natural person representing another natural person,
- Wallet-to-Wallet interactions,
- combined presentations of attestations,
- User requests for data deletion by Relying Parties,
- mechanisms for Users to report unlawful or suspicious data requests to data
protection authorities (DPAs),
- data portability.

Further discussions will explore the following topics:

- the development of catalogues for attestations,
- secure cryptographic interfaces between the Wallet Instance and the WSCA,
- User interfaces with Wallet Instances,
- authentication mechanisms for Users to access their devices,
- certificate transparency,
- support and maintenance responsibilities of Wallet Providers,
- the EUDI Wallet Trust Mark,
- transactional data needed by Wallet Units in payments and other use cases.

A detailed list of these topics and the progress of their development is
available on [GitHub](https://github.com/orgs/eu-digital-identity-wallet/projects/36).

## 2 EUDI Wallet functionalities

### 2.1 Introduction

The EUDI Wallet ecosystem is designed as a secure, User-controlled digital
environment that enables Users to use their Wallet Unit to manage and present
their person identification data (PID) and attestations across both public and
private services in the EU. Its functionalities are built around security,
privacy, and User control, ensuring seamless interactions with Relying Parties
and other entities, while adhering to data
protection principles.

This chapter outlines the core functionalities of Wallet Solutions, as defined
by the [European Digital Identity Regulation], and examines how the requirements
for its implementation align with real-world use cases where Users will use
their Wallet Unit.

The functionalities of a Wallet Unit can be grouped into the following
categories:

- **Secure identification and authentication**, ensuring that Users can present
person identification data in a trusted environment.
- **Exchanging qualified and non-qualified User attributes** through secure and
verifiable electronic attestations of attributes.
- **Electronic signing of documents or data**, allowing Users to create
legally recognised qualified electronic signatures and seals.
- **Generate and use pseudonyms** for authentication, to enhance privacy and
prevent tracking.

These functionalities are discussed in the next four sections.

### 2.2 Identification and authentication

Using their Wallet Units, Users are able to:

- **Identify and authenticate** to online and offline services, while using
**selective disclosure** of attributes as well as **User approval**. This
*ensures that only necessary and User-approved attributes are presented to
*Relying Parties, which minimises exposure of personal information.
- **Securely authenticate Relying Parties or other Wallet Units**, making sure
that attributes are only presented to trusted entities.
- **Onboard seamlessly with PID Providers or attestation Providers** by
leveraging existing electronic identification schemes, for a smooth and secure
registration process.
- **Be informed** whether a Relying Party is authorised or registered to receive
the requested attributes.
- **Access a transaction log via a dashboard**, allowing Users to:
    - **Review past interactions** with Relying Parties and Wallet Units.
    - **Request data erasure** under the GDPR Article 17 to maintain privacy.
    - **Report suspicious Relying Parties** to the relevant national data
    protection authority.

### 2.3 Attribute exchange mechanism using attestations

Using their Wallet Units, Users are able to:

- **Request, store, and present** personal identification data and electronic
attestations of attributes under their sole
control, ensuring secure usage in both online and offline scenarios.
- **Backup a list of their attributes, attestations, and configurations**,
guaranteeing compliance with data portability rights.
- **Prevent tracking by Relying Parties** when using attestations,
ensuring privacy-preserving interactions.

### 2.4 Qualified electronic signatures

Using their Wallet Units, Users are able to:

- **Create qualified electronic signatures and seals** for legally binding
digital transactions.
- **Sign documents using qualified electronic signatures**, which are provided
by default and free of charge within the Wallet Unit, ensuring universal
accessibility and compliance with legal standards.

These functionalities are implemented by using the authentication and signing
capabilities of the Wallet Unit as a part of a local QSCD, or a remote QSCD
managed by a QTSP. See [Topic 16](./annexes/annex-2/annex-2-high-level-requirements.md#a2316-topic-16---signing-documents-with-a-wallet-unit)
and [Topic 37](./annexes/annex-2/annex-2-high-level-requirements.md#a2337-topic-37---qes----remote-signing---technical-requirements).

### 2.5 Pseudonyms

Pseudonyms can be used to authenticate a User when it is not necessary for a
Relying Party to learn the identity of the User. As specified in [CIR
2024/2979], [W3C WebAuthn] defines the technical specification for pseudonyms.
Passkeys are a widely used type of credential which are created and asserted
using the WebAuthn API. [Section 4.7](#47-pseudonyms) gives more information on
the architecture and message flows of Passkeys.

A User uses a pseudonym when they wish to create an account at a Relying Party
without identifying themselves. The Relying Party associates the pseudonym with
the account, such that it can be used for subsequent authentication in later
interactions with that Relying Party. The User may additionally present
attributes from a PID or attestation to the Relying Party, either during
registration of the pseudonym or at a later interaction.

See also [Topic 11](./annexes/annex-2/annex-2-high-level-requirements.md#a2311-topic-11---pseudonyms)
and the [Discussion Paper on Topic E](./discussion-topics/e-pseudonyms-including-user-authentication-mechanism.md).

### 2.6 The role of use cases in the development of the Architecture and Reference Framework

#### 2.6.1 Overview

The development of the Architecture and Reference Framework (ARF) is strategically
driven by real-world use cases, ensuring that the User experience, value
proposition, and requirements of the EUDI Wallet ecosystem are
effectively addressed. To achieve this, the European Digital Identity
Cooperation Group initially created service blueprints for each use case, which
detail service touch points, components, and processes.

These blueprints serve a dual purpose: they play a crucial role in service
design, enhancing both User experience and operational efficiency, while also
identifying areas for improvement. As a foundational element, these blueprints
shape the development of common specifications, providing comprehensive yet
flexible solutions that can accommodate alternative approaches and optional
steps.

It is important to note that User journeys may vary based on the specific
implementation approach, influencing aspects such as data retrieval and User
approval processes. The Annexes contain detailed descriptions of these
blueprints, ensuring transparency and adaptability.

The European Digital Identity Cooperation Group has outlined service blueprints
for the following key use cases:

- Identification and authentication to access online services, see [Section 2.6.2](#262-identification-and-authentication-to-access-online-services-using-pid),
- Qualified Electronic Signature, see [Section 2.4](#24-qualified-electronic-signatures),
- Mobile Driving Licence, see [Section 2.6.3](#263-mobile-driving-licence),
- Additional use cases that will be introduced in the future, see [Section 2.6.4](#264-other-use-cases).

These blueprints, along with all relevant information on use cases
implementation, will be compiled in a standardised format within a dedicated
document titled the "Use Cases Manual", and distributed together with this document.

#### 2.6.2 Identification and authentication to access online services using PID

One of the main use cases of the EUDI Wallet ecosystem is secure User
identification and authentication. A User presents data from their PID, which is
issued and managed at Level of Assurance (LoA) High, to various online services,
both public and private.. This capability is crucial, as it allows Relying
Parties to confidently verify the identity of Users they interact with.

In this use case, a User utilises their Wallet Unit to present specific
attributes from a PID to a Relying Party in order to access online services.
Before doing so, the Wallet Unit first authenticates the User. The User is
particularly mindful of the privacy and security implications of presenting data
when accessing online services. Their primary objective is to securely and
reliably access online services that require authentication, while maintaining
full control over how their personal data is presented.

#### 2.6.3 Mobile Driving Licence

A significant use case for the Wallet Unit involves allowing Users to request,
store, and present a mobile Driving Licence (mDL) as an attestation in their
Wallet Unit, allowing them mainly to prove their driving privileges. In this use
case, the User employs a Wallet Unit to present an mDL to a Relying Party, for
instance a police officer.

The use case description concentrates on proximity supervised and unsupervised
flows, which involve scenarios where the User is physically near a Relying
Party, and the mDL attribute exchange occurs using proximity technologies (e.g.,
NFC, Bluetooth). The two proximity flows have one significant difference: in the
supervised flow, the Wallet Unit presents mDL attributes to a human Relying
Party or under their supervision, whereas in the unsupervised flow, the Wallet
Unit presents mDL attributes to a machine without human oversight.

In addition, like any other attestation type, an mDL can be presented online,
over the internet.

#### 2.6.4 Other use cases

##### 2.6.4.1 Health data

Easy access to health data is crucial in both national and cross-border
contexts. A Wallet Unit may enable access to patient summary, ePrescriptions,
etc.

##### 2.6.4.2 Educational attestations and professional qualifications

Providing credentials for qualification recognition procedures can be costly and
time-consuming for Users, Relying Parties (such as companies and employers), and
Attestation Providers (such as education and training providers or academic
institutions). A Wallet Unit may be a repository for educational credentials and
a means for presenting them by the User to relevant Relying Parties.

##### 2.6.4.3 Digital finance

A Wallet Unit may facilitate complying with strong customer authentication
requirements, using the user authentication capabilities described in
[Section 2.6.2](#262-identification-and-authentication-to-access-online-services-using-pid).
In line with the Commission's Retail Payments Strategy, this use case would be
developed in close coordination with Member States' advisory groups on retail
payments and the finance industry.

##### 2.6.4.4 Digital Travel Credential

Digital Travel Credential (DTC) Providers may issue DTCs to Wallet Units in a
supported format, to enable Relying Parties to identify Users, thus facilitating
a smooth travel experience and User journey. Relying Parties for a DTC may
include governments, transportation providers, hospitality agents, or any other
actors operating in a regulated environment which requires the use of a DTC.

##### 2.6.4.5 Social Security

Documents related to social security are important for many EU citizens to prove
their rights and obligations under social security legislation in the EU.
Examples include:

- **Portable Document (“PDA1”)** This is a statement of applicable legislation
which is useful to prove that a person pays social contributions in another EU
country, for example if they are a posted worker or work in several countries at
the same time.
- **Electronic Health Insurance Card ("EHIC")** This is a free card that provides
every citizen with access to medically necessary government-provided healthcare
during a temporary stay in one of the 27 EU countries, Iceland, Liechtenstein,
Norway, and Switzerland, under the same conditions and at the same cost (free in
some countries) as persons insured in that country. This includes, for example,
services related to chronic or existing illnesses, as well as in connection with
pregnancy and childbirth.

## 3. EUDI Wallet ecosystem

### 3.1 Introduction

This chapter describes the EUDI Wallet ecosystem as it is foreseen in the [European
Digital Identity Regulation]. The different roles in the EUDI Wallet ecosystem
are described in Figure 1 and detailed in the following sections.

![Figure 1: Overview of the EUDI Wallet ecosystem roles](media/Figure_1_Overview_of_EUDI_Wallet_roles.jpeg)
*Figure 1: Overview of the EUDI Wallet ecosystem roles*

1. Users of Wallet Units, see [Section 3.2](#32-users-of-wallet-units),
2. Wallet Providers, see [Section 3.3](#33-wallet-providers),
3. Person Identification Data (PID) Providers, see [Section 3.4](#34-person-identification-data-pid-providers),
4. Trusted List Providers, see [Section 3.5](#35-trusted-list-provider),
5. Qualified Electronic Attestation of Attributes (QEAA) Providers,
see [Section 3.6](#36-qualified-electronic-attestation-of-attributes-qeaa-providers),
6. Electronic Attestation of Attributes issued by or on behalf of a public
sector body responsible for an authentic source (PuB-EAA) Providers, see
[Section 3.7](#37-eaa-issued-by-or-on-behalf-of-a-public-sector-body-responsible-for-an-authentic-source-pub-eaa-providers),
7. Electronic Attestation of Attributes (EAA) Providers, see [Section 3.8](#38-non-qualified-electronic-attestation-of-attributes-eaa-providers),
8. Qualified Electronic Signature Remote Creation Providers, see [Section 3.9](#39-qualified-electronic-signature-remote-creation-qesrc-providers),
9. Authentic Sources, see [Section 3.10](#310-authentic-sources),
10. Relying Parties, see [Section 3.11](#311-relying-parties-and-intermediaries),
11. Conformity Assessment Bodies (CAB), see [Section 3.12](#312-conformity-assessment-bodies-cab),
12. Supervisory Bodies, see [Section 3.13](#313-supervisory-bodies),
13. Device Manufacturers and Related Subsystems Providers, see [Section 3.14](#314-device-manufacturers-and-related-subsystems-providers),
14. Attribute Schema Providers, see [Section 3.15](#315-attribute-schema-providers-for-qeaa-pub-eaa-and-eaa),
15. National Accreditation Bodies, see [Section 3.16](#316-national-accreditation-bodies),
16. Access Certificate Authorities, see [Section 3.17](#317-access-certificate-authorities).

### 3.2 Users of Wallet Units

Users of Wallet Units use the Wallet Unit to receive, store, and present PID,
QEAA, PuB-EAA, or non-qualified EAA to Relying Parties. Users can also create
qualified electronic signatures and seals (QES) and create and present
pseudonyms.

[CIR 2024/2982](https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=OJ:L_202402982)
(among others) defines 'wallet user' as 'a user who is in control of the wallet
unit'. Being in control of the Wallet Unit implies being able to present a PID
or attestation to a Relying Party. Within the use cases described in the current
version of the ARF, the User is the subject of the PID(s) in the Wallet Unit.
The User is also the subject of most of the attestations in the Wallet Unit, but
there could be attestations that have no subject, such as vouchers, or that
relate to objects owned or used by the User, such as a vehicle registration card.

Please note that this ARF assumes that a User device is a personal device, meaning that the User will not share it with other people, and that only the User can access and control the Wallet Unit.

Next versions of the ARF may include use cases for representation and
delegation, for example a parent representing their children or a CEO having the
right to sign contracts on behalf of their company. Conceivably, such use cases
may lead to situations where a Wallet Unit holds the natural-person PIDs of
multiple persons, or holds one or more legal-person PIDs in addition to a
natural-person PID. However, other solutions are possible as well. The topics of
representation and delegation will be further discussed with Member States in
the future.

The use of a Wallet Unit by citizens is not mandatory under the [European
Digital Identity Regulation]. However, each Member State will provide at least
one European Digital Identity Wallet within 24 months after the entry into force
of the implementing acts referred to in the [European Digital Identity
Regulation].

### 3.3 Wallet Providers

Wallet Providers are Member States or organisations either mandated or
recognised by Member States making a Wallet Solution available to Users. All
Wallet Solutions must be certified as described in [Chapter 7](#7-certification-and-risk-management).

A Wallet Provider makes a combination of several products and Trust Services
available to a User, which give the User sole control over the use of their
Person Identification Data (PID) and Electronic Attestations of Attributes
(QEAA, PuB-EAA or EAA), and any other personal data within their Wallet Unit.
This also implies guaranteeing a User sole control over sensitive cryptographic
material (e.g., private keys) related to their Wallet Unit.

Wallet Providers are responsible for ensuring compliance with the requirements
for Wallet Solutions.

From the viewpoint of the other actors in the EUDI Wallet ecosystem, the Wallet
Provider is responsible for all components of the Wallet Unit. These components
are described in [Section 4.3.2](#432-components-of-a-wallet-unit). In
particular, the Wallet Provider is responsible for ensuring that the Wallet
Instance can access a Wallet Secure Cryptographic Device (WSCD) that has a level
of security sufficient to ensure that the Wallet Unit can achieve Level of
Assurance High, as required in the [European Digital Identity Regulation].
This is true even if the WSCD is not delivered by the Wallet Provider but
is integrated into the User device.
For more information, see [Section 4.5](#45-wscd-architecture-types). Other actors
in the ecosystem do not need to interact with or explicitly trust a WSCD
supplier. As explained in [Section 6.5.3](#653-wallet-unit-activation), Wallet
Providers provide Wallet Unit Attestations (WUA) to the Wallet Unit. The WUA
attests that the Wallet Unit and all of its components, including the WSCD,
comply with the relevant requirements.

### 3.4 Person Identification Data (PID) Providers

PID Providers are trusted entities responsible for:

- verifying the identity of the User in compliance with LoA high requirements,
- issuing a PID to the Wallet Unit, and
- making available, in a privacy-preserving way, information for Relying Parties
to verify the validity of the PID.

The terms and conditions of these services are for each Member State to determine.

PID Providers may be the same organisations that today issue official identity
documents, electronic identity means, etc. PID Providers may be the same
organisations as Wallet Providers. In case an organisation acts as both a PID
Provider and a Wallet Provider, it complies with all requirements for both PID
Providers and Wallet Providers.

### 3.5 Trusted List Provider

A Trusted List Provider (TLP) is a body responsible for maintaining, managing,
and publishing a Trusted List. Within the EUDI
Wallet ecosystem, Trusted Lists exist for the following entities:

- Wallet Providers,
- PID Providers,
- QEAA Providers,
- PuB-EAA Providers,
- Access Certificate Authorities,
- Qualified Electronic Signature Remote Creation (QESRC) Providers.

Notes:

- Wallet Providers, PID Providers, and Access Certificate Authorities are not trust service providers in the sense of the [European Digital Identity Regulation]. Therefore, the Trusted Lists for these entities are -legally speaking- not trusted lists in the sense of [Article 22](https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=uriserv%3AOJ.L_.2014.257.01.0073.01.ENG#d1e2162-73-1). However, the technical requirements for all Trusted Lists and Trusted List Providers are the same. For that reason, the ARF does not distinguish between Trusted Lists for these entities and those for QEAA Providers and PuB-EAA Providers, who are trust service providers in the sense of the Regulation.
- Non-qualified EAA Providers are trust service providers in the sense of the [European Digital Identity Regulation]. Therefore, Trusted Lists and Trusted List Providers may also exist for non-qualified EAA Providers. However, this is out of scope of the ARF.

These Trusted Lists are described in more detail in [Sections 6.2.2](#622-wallet-provider-registration-and-notification),
[6.3.2](#632-pid-provider-or-attestation-provider-registration-and-notification)
and [6.4.2](#642-relying-party-registration). Some
Trusted Lists contain the trust anchors of the relevant entities. A trust anchor
is a combination of a public key and the identifier of the associated entity and
may be used to verify signatures created by that entity.

An entity's status as a trusted entity can be verified by checking whether they
are present on the relevant Trusted List. Trusted List Providers provide a
registration service for the relevant entities. The terms and conditions for
entities to become registered are for each Trusted List Provider to determine.

For more information, please refer to [Topic 27](./annexes/annex-2/annex-2-high-level-requirements.md#a2327-topic-27---registration-of-pid-providers-providers-of-qeaas-pub-eaas-and-non-qualified-eaas-and-relying-parties)
and to [Topic 31](./annexes/annex-2/annex-2-high-level-requirements.md#a2331-topic-31---pid-provider-wallet-provider-attestation-provider-and-access-certificate-authority-notification-and-publication).

### 3.6 Qualified Electronic Attestation of Attributes (QEAA) Providers

Qualified EAAs are provided by Qualified Trust Service Providers (QTSPs). The
general trust framework for QTSPs (see Chapter III, Section 3 of the [European
Digital Identity Regulation] applies also to QEAA Providers, but specific rules
for the Trust Service of issuing QEAAs may be defined as well.

QEAA Providers maintain an interface to Wallet Units to provide QEAAs upon
request. Potentially, they also maintain an
interface towards Authentic Sources to verify attributes, as specified in
[Topic 42](./annexes/annex-2/annex-2-high-level-requirements.md#a2342-topic-42---requirements-for-qtsps-to-access-authentic-sources).

It is likely that for most QEAAs, a QEAA Provider will need to verify the
identity of a User when issuing a QEAA. It is up to each QEAA Provider to
implement the necessary User authentication processes, in compliance with all
applicable national and Union legislation. Note that, when User identity
verification is necessary, it is likely that the User requesting a QEAA already
possesses a PID. This would enable the QEAA Provider to carry out User
identification and authentication at LoA high, by requesting and verifying
User attributes from the PID in the Wallet Unit.

The terms and conditions of these services are for each QEAA Provider to
determine, beyond what is specified in the [European Digital Identity Regulation].

### 3.7 EAA issued by or on behalf of a public sector body responsible for an authentic source (PuB-EAA) Providers

As specified in the [European Digital Identity Regulation], an attestation may
be issued by or on behalf of a public sector body responsible for an Authentic
Source. This ARF calls such an attestation a PuB-EAA. For a description of
Authentic Sources, see [Section 3.10](#310-authentic-sources). A public sector
body primarily is a state, regional or local authority, or a body governed by
public law.

A PuB-EAA Provider, meaning a public sector body issuing PuB-EAAs, is not a
QTSP. However, a PuB-EAA Provider has a qualified certificate, issued by a QTSP,
that allows it to sign PuB-EAAs. A Relying Party verifies a PuB-EAA by first
verifying the signature over the PuB-EAA, and subsequently verifying the
signature of the qualified PuB-EAA Provider certificate. For more details, refer
to [Section 6.6.3.6](#6636-relying-party-instance-verifies-the-authenticity-of-the-pid-or-attestation).
The [European Digital Identity Regulation] stipulates that PuB-EAAs, like QEAAs,
have the same legal effect as attestations in paper form. It is up to the Member
States to define terms and conditions for the provisioning of PuB-EAAs, but
PuB-EAA Providers will comply with the same technical specifications and
standards as Providers of PIDs and other attestations.

For the precise and legally binding definitions and obligations regarding the
issuance of PuB-EAAs, please refer to the [European Digital Identity Regulation].

### 3.8 Non-Qualified Electronic Attestation of Attributes (EAA) Providers

Non-qualified EAAs can be provided by any (non-qualified) Trust Service
Provider. While they will be supervised under the [European Digital Identity
Regulation], it can be assumed that other legal or contractual frameworks will
mostly govern the rules for provision, use and recognition of EAAs. Those other
frameworks may cover policy areas such as educational credentials, digital
payments, although they may also rely on Qualified Electronic Attestation of
Attributes Providers. For non-qualified EAAs to be used, EAA Providers offer
Users a way to request and obtain these EAAs. This implies that these
non-qualified EAA Providers comply with the Wallet Unit interface
specifications. The terms and conditions of issuing EAAs and related services
are subject to sectoral rules.

### 3.9 Qualified Electronic Signature Remote Creation (QESRC) Providers

The Wallet Unit will allow the User to create qualified electronic signatures or
seals over any data. This will also enhance the use of the Wallet Unit for
signing, in a natural and convenient way. The creation of a qualified electronic
signature or seal by means of the Wallet Unit can be achieved in several ways:

- the Wallet Unit itself could be certified as a qualified signature or seal
creation device (QSCD), or
- the Wallet Unit could implement secure authentication into an electronic
signature or electronic seal invocation capability, as part of a local QSCD or
a remote QSCD managed by a QTSP.

As part of the ecosystem, the use of common interfaces and protocols for
provisioning qualified electronic signatures and seals will create a unified
European market for QTSPs offering remote signature services. European citizens
will be able to choose any QTSP, without worrying about technical
interoperability, and this will enhance competition.

Besides providers of qualified electronic signatures and seals, also providers
of non-qualified electronic signatures or seals may exist. However, such
providers are out of scope of this ARF.

### 3.10 Authentic Sources

Authentic Sources are public or private repositories or systems, recognised or
required by law, containing attributes about natural or legal persons. Authentic
Sources are sources for attributes on, for instance, address, age, gender, civil
status, family composition, nationality, education and training qualifications
titles and licences, professional qualifications titles and licences, public
permits and licences, or financial and company data.

Authentic Sources are required to provide an interface to QEAA Providers to
verify the authenticity of the above attributes, either directly or via
designated intermediaries recognised at national level. Authentic Sources may
act as PuB-EAA Providers if they meet the requirements of the [European Digital Identity]
Regulation, see [Section 3.7](#37-eaa-issued-by-or-on-behalf-of-a-public-sector-body-responsible-for-an-authentic-source-pub-eaa-providers).
In Figure 1 this is indicated by the arrow 'provides qualified data'.

### 3.11 Relying Parties and intermediaries

Within the scope of this ARF, a Relying Party is a service provider requesting attributes contained
within a PID, QEAA, PuB-EAA or EAA from the Wallet Unit, subject to the approval
of the User and within the limits of applicable legislation and rules.

Note: As specified in the [European Digital Identity Regulation], legally speaking, the term 'Relying Party' includes Attestation Providers (i,e, QEAA Providers, PuB-EAA Providers,
and non-qualified EAA Providers), as well as service providers. However, technically speaking the responsibilities of Attestation Providers are quite different from those of service providers, as is the way they interact with Wallet Units. Therefore, for clarity the term 'Relying Party' is used in all parts of the ARF exclusively to mean a service provider interacting with a Wallet Unit to request and receive attributes from an attestation.

The reason for a Relying Party to rely on the Wallet Unit may be a legal requirement, a
contractual agreement, or their own decision. In particular, the [European
Digital Identity Regulation] requires that providers of very large online
platforms must accept the EUDI Wallet for their user authentication processes.

Relying Parties maintain an interface with Wallet Units to request PIDs and
attestations, using Relying Party authentication, as described in [Section 6.6.3.2](#6632-wallet-unit-authenticates-the-relying-party-instance).
If a Wallet Unit presents attributes from a PID or attestation to a Relying Party,
the Relying Party can verify the authenticity of these attributes.

To rely on Wallet Units for the purpose of providing a service, Relying Parties
inform the Member State where they are established about their intention for
doing so, and register the attributes that they intend to request. See [Section 6.4.2](#642-relying-party-registration)
for more information on Relying Party registration. During a transaction, a
Wallet Unit will verify that the Relying Party only requests attributes that it
registered. It will warn the User if this is not the case.
This is explained in [Section 6.6.3.3](#6633-wallet-unit-allows-user-to-verify-that-relying-party-does-not-request-more-attributes-than-it-registered).

In addition, an Attestation Provider may embed a disclosure policy in an
attestation. Such a policy indicates to which Relying Parties a Wallet Unit
should (or should not) present specific attributes from that attestation. During
a transaction, the Wallet Unit evaluates the policy based on data provided by
the Relying Party, and warns the User if the outcome of that evaluation is
negative. Please refer to [Section 6.6.3.4](#6634-wallet-unit-evaluates-embedded-disclosure-policy-if-present)
for more information.

So-called intermediaries form a special class of Relying Party. Article 5b (10)
of the [European Digital Identity Regulation] states "Intermediaries acting on
behalf of relying parties shall be deemed to be relying parties and shall not
store data about the content of the transaction.". Such an intermediary is a
party that offers services to Relying Parties to, on their behalf, connect to
Wallet Units and request the User attributes that these Relying Parties need.
The intermediary then sends the presented attributes to the 'end' Relying Party.
This implies that an intermediary performs all tasks assigned to a Relying Party
in this ARF on behalf of the 'end' Relying Party. In particular:

1. The intermediary registers once as a Relying Party and obtains an access
certificate (see [Section 6.6.3.2](#6632-wallet-unit-authenticates-the-relying-party-instance))
bearing its own name and Relying Party identifier. This access certificate is not
different from an access certificate issued to a 'normal' Relying Party, since
an intermediary is, as a matter of legal fact, a Relying Party.
Note: In addition, the intermediary may receive a registration certificate, if issued (see [Section 6.6.3.3](#6633-Wallet-Unit-allows-User-to-verify-that-Relying-Party-does-not-request-more-attributes-than-it-registered)). However this certificate is not used in intermediated transactions.
2. Next, the intermediary will separately register each of the 'end' Relying
Parties that uses its services, including registering the attributes the 'end'
Relying Party wants to request. The intermediary obtains a registration
certificate (see [Section 6.6.3.3](#6633-wallet-unit-allows-user-to-verify-that-relying-party-does-not-request-more-attributes-than-it-registered))
showing the name of the 'end' Relying Party. The Registrar verifies, in a manner
to be decided by a Member State, that the 'end' Relying Party is indeed using
the services of the intermediary. If all is correct, the Registrar will issue a
registration certificate containing an additional attribute stating that the
'end' Relying Party is using the services of the intermediary.
3. When asked by an 'end' Relying Party, the intermediary will request the
presentation of attributes from Wallet Units, using one or more of the flows
described in [Section 4.4](#44-data-presentation-flows). For this, the
intermediary will use their own access certificate (point 1. above) and the
registration certificate of the 'end' Relying Party (point 2. above).

4. If a Wallet Unit during a transaction, obtains information that the Relying Party uses the services of an intermediary, it
verifies that the name and the identifier of the intermediary in the
registration certificate are identical to the name and identifier in the access
certificate. If this verification fails, the Wallet Unit treats this as a
Relying Party authentication failure. If this verification succeeds, the Wallet
Unit displays to the User the name of the intermediary next to the name of the 'end' Relying Party when asking for User
approval to present the requested attributes.

    The Wallet Unit obtains information whether the Relying Party uses the services of an intermediary, along with the name of the 'end' Relying Party, from:
    + the registration certificate - if provided in the presentation request, or
    + the information contained in the presentation request (note: this will need an extension of [ISO/IEC 18013-5] and [OpenID4VP])

5. When a Wallet Unit presents a PID or attestation to the intermediary, the
intermediary verifies the authenticity of the PID or attestation, its revocation
status, device binding, and User binding, as well as any combined presentation
of attributes, if applicable, if it has agreed to do so with the Relying Party.
Also, the intermediary may need to verify the authenticity of the Wallet Unit
and its revocation status. (Note that a Relying Party is not obliged to carry
out all of these verifications. Therefore, the intermediary and any Relying
Party using its services must agree on what verifications the intermediary will
carry out.)
6. If these verifications are successful, the intermediary forwards the User
attributes it obtained from the Wallet Unit to the 'end' Relying Party. There
must be an interface between an intermediary and a Relying Party, over which the
'end' Relying Party can request the intermediary to request some User attributes
from a Wallet Unit and that the intermediary uses to send back the attribute
values presented by the Wallet Unit. However, specifying this interface or the
(security) requirements with which it needs to comply, is out of scope of the
ARF. In particular, it is not required that the User attributes are end-to-end
encrypted between the Wallet Unit and the 'end' Relying Party, such that an
intermediary would not be able to see them.
7. The intermediary deletes any PIDs, attestations, or WUAs it obtained from the
Wallet Unit, including any User attributes, immediately after it has sent the
User attributes to the Relying Party. If the intermediary does not send any User
attributes to the Relying Party, for example because one of the verifications in
the previous step failed, the intermediary deletes the PIDs, attestations, or
WUAs immediately after it has completed all necessary verifications.

Note that this approach implies that an intermediary (if it is acting only as an
intermediary, and never as an 'end' Relying Party in its own right) will not
need a registration certificate (despite it might be issued by a Registrar, according to rules set out by a given Member State). Conversely, an 'end' Relying Party using the services of an intermediary will not need an access certificate.

As discussed in [Section 6.6.3.5](#6635-wallet-unit-obtains-user-approval-for-presenting-selected-attributes),
during a transaction, a Wallet Unit requests the User for their approval to
present any User attributes to the Relying Party. In this process, the Wallet
Unit informs the User about the authenticated identity of the intermediary (from
the access certificate), and also about the identity of the 'end' Relying Party
and the fact that this Relying Party is using the services of the intermediary
(from the registration certificate).

For high-level requirements on this topic, see [Topic 52](./annexes/annex-2/annex-2-high-level-requirements.md#a2352-topic-52-relying-party-intermediaries).

In addition, before approval, the User may want to verify the 'end' Relying Party registration information and the scope of attributes requested, as described in [Section 6.6.3.3](#6633-wallet-unit-allows-user-to-verify-that-relying-party-does-not-request-more-attributes-than-it-registered)).



### 3.12 Conformity Assessment Bodies (CAB)

Conformity Assessment Bodies (CAB) are public or private bodies that are
accredited by a national accreditation body, which itself is designated by
Member States according to [Regulation 765/2008](https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=celex:32008R0765)
Article 6c (3). In particular, CABs are accredited to carry out assessments on
which Member States will rely before issuing a Wallet Solution or providing the
'qualified' status to a Trust Service Provider.

Wallet Solutions will be certified by CABs. QTSPs will be audited regularly by CABs.

The standards and schemes used by CABs to fulfil their tasks to certify Wallet
Solutions are discussed in [Chapter 7](#7-certification-and-risk-management).

### 3.13 Supervisory Bodies

Supervisory Bodies review the proper functioning of Wallet Providers and other
actors in the EUDI Wallet ecosystem. Supervisory Bodies will be created and
appointed by the Member States. The Supervisory Bodies will be notified to the
Commission by the Member States.

### 3.14 Device Manufacturers and Related Subsystems Providers

In the EUDI Wallet ecosystem, commercial actors such as device manufacturers and
related subsystems providers fulfil an important role to enable a Wallet Unit to
work smoothly and securely. Device manufacturers and related subsystem providers
provide a platform on which a Wallet Unit can be built. Wallet Providers ensure
that their Wallet Units use that platform to ensure usability, security,
stability and connectivity. The components provided by device manufacturers and
providers of related subsystems may include, among others, hardware, operating
systems, secure cryptographic hardware, libraries, and app stores.

### 3.15 Attribute Schema Providers for QEAA, PuB-EAA and EAA

Attribute Schema Providers publish attribute schemas describing the structure
of QEAAs, PuB-EAAs and EAAs, including the identifier, semantics, and encoding
of all attributes. These attribute schemas are published in Attestation
Rulebooks, see [Section 5.4](#54-attribute-schemas-and-attestation-rulebooks). For PIDs and mDLs, the
applicable Rulebooks are published by the Commission.

A catalogue of published Attestation Rulebooks will enable other entities such
as Relying Parties to discover which attestations exist within the EUDI Wallet
ecosystem, and how attributes from these attestations can be requested and
validated. The Commission sets out the technical specifications, standards, and
procedures for this purpose. Common schemas, including by sector-specific
organisations, are critical for widespread adoption of attestations.

### 3.16 National Accreditation Bodies

National Accreditation Bodies (NAB), under [Regulation (EC) No 765/2008](https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=celex:32008R0765),
are the bodies in Member States that perform accreditation with authority
derived from the Member State. NABs accredit CABs ([Section 3.12](#312-conformity-assessment-bodies-cab))
as competent, independent, and supervised professional certification bodies in
charge of certifying Wallet Solutions against normative document(s) establishing
the relevant requirements. NABs monitor the CABs to which they have issued an
accreditation certificate.

### 3.17 Access Certificate Authorities

Access Certificate Authorities issue access certificate to all PID Providers,
QEAA Providers, PuB-EAA Providers, non-qualified EAA Providers and Relying
Parties in the EUDI Wallet ecosystem. When these entities interact with a Wallet
Unit to issue or request a PID or attestation, they will present an access
certificate to prove their authenticity and validity.

Access Certificate Authorities must be notified by a Member State to the
Commission. As part of the notification process, the trust anchors of the Access
CA must be included in a Trusted List. A trust anchor is the combination of a
public key and an identifier for the associated entity. Wallet Units need these
trust anchors to verify the signatures over the access certificates presented
to them when a new PID or attestation is issued or when they receive an
attribute presentation request from a Relying Party.

## 4 High level architecture

### 4.1 Introduction

This chapter provides a broad overview of the EUDI Wallet ecosystem's core
components, their interfaces, and the overall design principles. This chapter is
structured as follows:

- [Section 4.2](#42-design-principles) discusses the design principles that
guided the design of the EUDI Wallet ecosystem, as described in this ARF.
- [Section 4.3](#43-reference-architecture) presents an overview of the
ecosystem's architecture, focussing on the components that make up a Wallet Unit
and on the interfaces between a Wallet Unit and other entities, as well as the
protocols used on these interfaces.
- [Section 4.4](#44-data-presentation-flows) discusses the different attestation
presentation flows enabled by this architecture, and in particular the
mechanisms foreseen to enable and secure remote presentation flows in which the
Wallet Unit and the Relying Party interact over the internet.
- [Section 4.5](#45-wscd-architecture-types) briefly discusses the different
architecture types a Wallet Providers may use for implementing one or more Wallet
Secure Cryptographic Device(s) into their Wallet Solutions.
- [Section 4.6](#46-state-diagrams) presents state diagrams for all of the main
entities and components in the EUDI Wallet ecosystem, discussing all of the
states a particular component can be in, as well as the conditions triggering
state transitions.
- [Section 4.7](#47-pseudonyms) discusses how pseudonyms will be implemented and used within a Wallet Unit.

### 4.2 Design principles

To effectively translate the [European Digital Identity Regulation] into a
User-friendly, privacy-focused, and secure technical architecture, establishing
design principles is crucial. These principles, rooted in the regulatory
framework and enriched by industry best practices, will serve as fundamental
guidelines. This approach ensures compliance with requirements emphasising
User-centricity, privacy, security, and cross-border interoperability. It
demonstrates a commitment to both regulatory alignment and excellence in the
EUDI Wallet architecture's design.

#### 4.2.1 User-centricity

The EUDI Wallet ecosystem prioritises User-centricity as a core design
principle. This means placing User needs and experience at the forefront of
every design decision. The Wallet Unit should be intuitive and easy to use, with
seamless integration into existing use cases. Users should have full control
over their attributes and privacy, with transparent information about what
attributes are being presented and to whom. Additionally, the Wallet Unit should
be accessible and inclusive, catering to Users with varying technical
backgrounds and abilities. By prioritising User-centricity, the EUDI Wallet
ecosystem fosters trust and encourages widespread adoption, ultimately achieving
its goal of empowering Users with secure and convenient digital identity
management.

#### 4.2.2 Interoperability

The EUDI Wallet ecosystem prioritises interoperability as a core design
principle. This ensures a Wallet Unit functions seamlessly across borders within
the EU. Users can travel freely and confidently utilise their digital identity
wallets for various services, from e-government platforms to private online
interactions. Interoperability fosters secure data exchange through standardised
protocols, allowing trusted entities to verify credentials effortlessly. This
not only simplifies the User experience but also strengthens overall security
within the system. Moreover, interoperability prevents market fragmentation by
creating a level playing field for different Wallet Solutions. It fosters
competition and collaboration, ultimately driving innovation in the EUDI Wallet
ecosystem. By prioritising interoperability, the EUDI Wallet architecture lays
the foundation for a trusted and universally accepted EUDI Wallet ecosystem
across the EU.

#### 4.2.3 Privacy by design

The EUDI Wallet architecture embodies the principle of privacy by design. This
means that the protection of User data is a fundamental pillar of the
architecture's design. The principle of data minimisation guides the collection
of personal information, ensuring that Relying Parties gather only the
attributes they need and have registered for. By enabling selective disclosure
of attributes, the Wallet Unit empowers Users with granular control over what
data is presented and to whom. Transparency is built into the system, with clear
explanations of how data is used and protected. By making privacy a cornerstone
from the beginning, the EUDI Wallet ecosystem aims to foster trust and protect
the fundamental rights of its Users. Finally, measures are taken to prevent
Users from being tracked by Relying Parties, PID Providers, or Attestation
Providers.

For more information, please refer to [Sections 7.4.3.4](#7434-risks-and-mitigation-measures-related-to-authorisation)
and [7.4.3.5](#7435-risks-and-mitigation-measures-related-to-user-privacy).

#### 4.2.4 Security by design

The EUDI Wallet architecture embraces the principle of security by design. This
means security considerations are woven into the very fabric of the
architecture's design. Throughout the design process, potential vulnerabilities
are identified and mitigated. Secure coding practices are mandated, and the
architecture itself minimises attack surfaces by compartmentalising sensitive
data and access controls. By prioritising security from the outset, the EUDI
Wallet architecture aims to be inherently resistant to cyberattacks and data
breaches, fostering trust and User confidence in this EUDI Wallet ecosystem.

For more information, please refer to [Sections 7.4.3.2](#7432-risks-and-mitigation-measures-related-to-confidentiality-integrity-and-authenticity)
and [7.4.3.3](#7433-risks-and-mitigation-measures-related-to-tampering-of-cryptographic-keys-and-sensitive-data).

### 4.3 Reference architecture

#### 4.3.1 Overview

The figure below gives an overview of the architecture of the EUDI Wallet
ecosystem and its components. In comparison to Figure 1, this figure presents
more detail on the composition of a Wallet Unit and its interfaces to other
entities. The depicted components of a Wallet Unit are described in [Section 4.3.2](#432-components-of-a-wallet-unit),
while the interfaces are described in [Section 4.3.3](#433-wallet-unit-interfaces-and-protocols).
The other entities shown in the figure were already described in [Chapter 3](#3-eudi-wallet-ecosystem).

![Figure 2](media/Figure_2_High-Level_Architecture.jpeg)
*Figure 2: EUDI Wallet ecosystem reference architecture*

Note that a User device can host more than one Wallet Unit, either provided by
multiple Wallet Providers or by the same one, if supported by that Wallet
Provider. If a User device hosts more than one Wallet Unit, all statements in
this ARF regarding a Wallet Unit and its components hold for each Wallet Unit
independently.

#### 4.3.2 Components of a Wallet Unit

The following have been identified as the core components of a Wallet Unit:

- **User device (UD)**: A User Device comprises the hardware, operating system,
and software environment required to host and execute the Wallet Instance. The
minimum hardware and software requirements for the User device will be
determined by the Wallet Provider.
- **Wallet Instance (WI)**: The app or application installed on a User device,
which is an instance of a Wallet Solution and belongs to and is controlled by a
User. This component implements the core business logic and interfaces as
depicted in Figure 2. It directly interacts with the WSCA/WSCD (see bullets
hereafter) to securely manage cryptographic assets and execute cryptographic
functions, ensuring a high level of assurance for authentication.
- **Wallet Secure Cryptographic Device (WSCD):** tamper-resistant device that
provides an environment that is linked to and used by the wallet secure
cryptographic application to protect critical assets and to securely execute
cryptographic functions. This includes a keystore, but
also the environment where the security-critical functions are executed. The
WSCD is tamper-proof and duplication-proof. One WSCD may be a part of multiple
Wallet Units, e.g. in case of a remote HSM. The WSCD consists of two parts: the
WSCD hardware covers the hardware issued by the WSCD vendor and the WSCD
firmware covers security-related software, such as an operating system and
cryptographic libraries provided by the WSCD vendor. Figure 2 shows four
different possible security architectures for the WSCD (for more details see
[Section 4.5](#45-wscd-architecture-types)):
    - a remote WSCD, which is a remote device, such as a Hardware Security Module (HSM),
    accessed over a network.
    - a local external WSCD, which is an external device, such as a smart card issued
    to the User specifically for this purpose,
    - a local internal WSCD, which is a component within the User device, such as a SIM,
    e-SIM, or embedded Secure Element,
    - a local native WSCD, which is a component embedded in the User device and accessed via
    an API provided by the operating system.

- **Wallet Secure Cryptographic Application (WSCA):** an application that
manages critical assets by being linked to and using the cryptographic and
non-cryptographic functions provided by the Wallet Secure Cryptographic Device.
The WSCA interfaces directly with the Wallet Instance. For more details see
[Section 4.5](#45-wscd-architecture-types).
- **Wallet Provider backend (WPB**): The Wallet Provider backend offers Users
support with their Wallet Units, performs essential maintenance, and issues
Wallet Unit Attestations through the Wallet Provider Interface (WPI).

#### 4.3.3 Wallet Unit interfaces and protocols

Figure 2 shows the following interfaces between components of a Wallet Unit, or
between the Wallet Unit and other entities in the EUDI Wallet ecosystem:

- The **Wallet Provider Interface (WPI)** is used by the Wallet Instance to
communicate with the Wallet Provider to request and issue the Wallet Unit
Attestation, as well as to provide support to the User and collect aggregated
and User-consented information in a privacy-preserving manner to provision the
Wallet Unit, in compliance with applicable legislation. Because the Wallet
Provider is responsible for both sides of this interface, it will not be
standardised in the scope of the EUDI Wallet ecosystem.
- The **User Interface (UI)** is the point of interaction and communication
between the User and the Wallet Instance. This interface will not be
standardised in the scope of the EUDI Wallet ecosystem.
- The **Presentation Interface (PI)** enables Relying Party Instances to securely
request and receive PIDs, QEAAs, PuB-EAAs and EAAs from Wallet Units. This
interface accommodates both remote and proximity interactions. For remote
presentation flows, as detailed in [Section 4.4.3](#443-remote-presentation-flows),
the Wallet Instance implements the OpenID for Verifiable Presentation protocol
[OpenID4VP] in combination with the [W3C Digital Credentials API]. In contrast,
for the proximity presentation flow, this interface adheres to the [ISO/IEC 18013-5]
standard, see [Section 4.4.2](#442-proximity-presentation-flows).
The same interface can also be used by another Wallet Unit to request User attributes,
see [Section 6.6.4](#664-pid-or-attestation-presentation-to-another-wallet-unit).
- The **Secure Cryptographic Interface (SCI)** enables the Wallet Instance to
communicate with the Wallet Secure Cryptographic Application (WSCA). This
interface is specifically designed for managing critical assets and
executing cryptographic functions. To be able to support different types of
WSCA/WSCD, Wallet Instances may need to be able to handle multiple flavours of
this interface.

- The **PID Issuance Interface (PII)** complies with the [OpenID4VCI] standard
and is used when the Wallet Unit communicates with a PID Provider to request and
receive PIDs to be stored within the Wallet Unit.
- The **Attestation Issuance Interface** **(AII)** complies with the
[OpenID4VCI] standard and is used by the Wallet Unit to request various
attestations that the User wants to include in their Wallet Unit.
- The **Remote Signing or Sealing Interface (RSI)** facilitates communication
between the Wallet Unit and a Qualified Electronic Signature Remote
Creation (QESRC) Provider. This interface is used by the Wallet Unit to generate
a qualified electronic signature or seal.

*Note that the "Attribute Deletion Request to Relying Party Interface" and the
"Reporting Relying Party to DPA Interface", which are mentioned in the
Regulation, are not depicted as interfaces in Figure 2. Functionality enabling a
User to request a Relying Party to delete personal data (i.e., User attributes)
obtained from the User's Wallet Unit is seen as a feature of the Wallet
Solution. The same applies to functionalities enabling the User to report a
Relying Party to a Data Protection Authority.

### 4.4 Data presentation flows

#### 4.4.1 Overview

This section defines four distinct communication flows that can be used when a
Wallet Unit presents a PID or attestation to a Relying Party Instance:

- **Proximity Supervised Flow**: In this flow, the User and their User
Device are physically near the Relying Part Instance. PIDs and attestations
are exchanged using proximity technology (e.g., NFC, Bluetooth) between the
Wallet Unit and the Relying Party Instance. Both devices may be with or without
internet connectivity. A human representative of the Relying Party supervises
the process.
- **Proximity Unsupervised Flow**: This flow is like the supervised flow, but
the Wallet Unit presents attestations to a machine, without human supervision.
The interfaces and protocols used in this flow are the same as for the proximity
supervised flow, and are described in [Section 4.4.2](#442-proximity-presentation-flows).
- **Remote Same-Device Flow**: In this flow, the User utilises a web browser or
another application on their User device to access a Relying Party's a service.
If consuming the service requires the Relying Party to obtain specific
attributes from the User's Wallet Unit, the Relying Party sends a presentation
request to the Wallet Unit. As explained in [Section 4.4.3.2](#4432-same-device-remote-presentation-flows),
this request is managed by the web browser on the User's device, utilising a
solution like the [W3C Digital Credentials API].
- **Remote Cross-Device Flow**: In this flow, the User uses a web browser on a
device other than the User device on which their Wallet Unit is installed to
access the Relying Party's service. This other device could be for instance a desktop, laptop, or another mobile device. If the Relying Party needs to send a
presentation request to the User's Wallet Unit, it presents this request to the
web browser on the other device. Again using the [W3C Digital Credentials API],
this web browser sets up a secure communication channel between the other device
and the User's device. [Section 4.4.3.3](#4433-cross-device-remote-presentation-flows)
explains this in more detail.

Specific use cases integrate one or more of these flows. Each of these flows is
described in more detail in one of the next sections.

#### 4.4.2 Proximity presentation flows

Figure 3 shows how attestation presentation works when the User and their User
Device are physically near the Relying Part Instance. In this case, the
[ISO/IEC 18013-5] standard specifies how a communication channel is set up and
how a presentation request and the corresponding response are exchanged.

![Figure 3](media/Figure_3_Proximity_Flow.png)
*Figure 3: Proximity presentations*

The attribute presentation flow begins when the User opens the Wallet Instance
and instructs it to display a QR code or present an NFC tag. This QR code or
NFC tag contains the information necessary to establish an NFC, BLE, or
Wi-Fi Aware connection. The Relying Party Instance scans the QR code or the NFC
tag and set ups the connection. The QR code or NFC tag also contains the
information necessary to create an authenticated and encrypted secure channel
between both entities.

#### 4.4.3 Remote presentation flows

##### 4.4.3.1 Introduction

Remote transaction flows are use cases in which the Relying Party Instance is
remote from the User and the User device. The Relying Party Instance requests
data from the Wallet Unit over the internet, using a browser. These use cases can
be further distinguished as same-device flows, in which the browser is running
on the same device as the Wallet Unit, and cross-device flows, where the browser
is on a different device.

Remote presentation flows come with a number of challenges that are not present
for proximity flows:

1. **Secure Cross-Device Flows**: Cross-device flows are vulnerable to phishing
and relay attacks, necessitating enhanced security measures. Proximity checks,
managed by the operating system of the User device, can mitigate the risks
derived from these vulnerabilities by leveraging built-in security features to
verify the authenticity of interactions, ensuring they are both secure and
reliable.
1. **Wallet Unit Selection**: In remote flows, where interactions
do not originate from the Wallet Unit, Users may encounter difficulties in
selecting the appropriate Wallet Unit to fulfil a specific
presentation request, particularly when multiple Wallet Units are present on the
device. A unified interface provided by the web browser and the device operating
system can streamline this process, offering a seamless and intuitive User
experience.
1. **Invocation Mechanism**: Establishing a communication channel between the
Wallet Unit and the remote Relying Party Instance presents challenges due to
inconsistent invocation methods. One approach considered by standardisation
bodies involves using custom URI schemes, such as "mdoc://" or "openid4vp://".
In this approach, the device operating system would trigger the Wallet Unit when
the Relying Party Instance requests a connection via a custom URI. Another
approach is the use of domain-bound universal links (a.k.a. app links). However,
relying on custom URI schemes or universal links introduces variability in User
experiences across different browsers and operating systems, resulting in
operational inefficiencies and potential security risks. An interface provided by
the web browser and the device OS does not need custom URL schemes or universal links
for invoking a Wallet Unit.
1. **Clear Origin Verification**: Protecting against relay attacks requires precise
identification of the Relying Party Instance's origin. Including the origin
information, such as the website domain or app package name, within the
presentation request ensures the authenticity of the request and enhances trust
for both Wallet Units and Users.
1. **Session binding**: When presenting a PID or attestation to a remote Relying
Party Instance, Users have to switch contexts. Existing protocols may enable
attacks where the contexts are not bound to each other, resulting in session
hijacking. Using an interface provided by the web browser and the device OS
allows information about a session to be embedded in a presentation request. At
the same time, the browser and the operating system handle proper context
switching, preventing session hijacking.

The next sections describe how these challenges might be solved for both
same-device and cross-device remote presentation flows, by using the [W3C
Digital Credentials API]. This API is expected to establish a consistent method for invoking Wallet Units, addressing these challenges.

The current version of the [W3C Digital Credentials API] extends the Credential Management
Level 1 API (the same API used by WebAuthn / Passkeys, see [Section 4.7](#47-pseudonyms))
to allow websites to request an attestation. This is achieved by providing a
sequence of "presentation requests", where each presentation request includes an
"exchange protocol" and "request data". The format of the request data are
specific to the exchange protocol. The Digital Credentials API specifications
will include a registry of supported protocols. For more information see the
[Topic F: Digital Credentials API](./discussion-topics/f-digital-credential-api.md)
discussion paper.

However, the [W3C Digital Credentials API] is still under development and has
not yet been standardised. For the [W3C Digital Credentials API] to be mandated
by this ARF in the future, it will have to align with the principles and
expectations outlined in
[Chapter 3](./discussion-topics/f-digital-credential-api.md#3) of the Topic F
discussion paper. Moreover, the API has not been implemented yet by all
browsers and operating systems.

Until these three conditions (standardisation, compliance with expectations, and
broad support) are fulfilled, the use of this API by Wallet Units and Relying
Parties is optional, and custom URL schemes may be used as well. If
a Wallet Unit implements a custom URL scheme, it will need to implement
mitigations for the challenges described in this section.

##### 4.4.3.2 Same-device remote presentation flows

![Figure 4](media/Figure_4_Remote_Same-Device_Flow.png)
*Figure 4: Remote same-device presentations*

Compared to Figure 2, Figure 4 shows additional detail. In particular, it shows
the browser on the User device and the relevant interfaces of this browser:

- The **Remote same-device presentation** interface establishes communication
between the web browser and a remote Relying Party Instance, which may operate
on a server managed by the Relying Party. This interface may comply with the
[Digital Credentials API], which is a browser API that is currently being
standardised within the W3C.
- The **WI-platform API** interface is a mechanism provided by the device's operating system that may implement the
Digital Credentials API mechanism at OS level. There are however no current plans
to standardise this interface on the level of the API calls. These calls will be
specified in the developer documentation for the respective OS. One of the key
elements of this API is that Wallet Unit receives reliable information regarding
the origin of the presentation request.

Obviously, the browser also has a User interface allowing the User to interact
with it. This interface will not be standardised in the context of the EUDI
Wallet ecosystem.

A remote same-device attribute presentation flow begins when the User accesses
the Relying Party's website using a browser on their device. The website may
provide an option for the User to present attributes from their Wallet Unit,
typically via a button or similar interface. When the User selects this option,
the browser may ask the User for permission to initiate the presentation flow. Upon
granting permission, the Relying Party Instance sends a presentation request
compliant with the OpenID4VP specification to the browser via the Digital
Credentials API. The browser, working in tandem with the device's operating
system (OS), forwards the request to the Wallet Unit using the WI-platform API.
If the device hosts multiple Wallet Units, the browser and OS will determine
which Wallet Unit should handle the request. This decision may involve
consulting the User.

The selected Wallet Unit processes the presentation request and seeks the
User's approval before returning the requested attributes in an encrypted format
to the browser. The browser then forwards this encrypted response to the remote
Relying Party Instance.

Figure 4 also illustrates an inter-app attribute presentation flow. In this
scenario, an application on the User's device, such as a banking or shopping
app, interacts with the Wallet Unit over the WI-platform API. This app acts as the Relying Party Instance, possibly in cooperation with a remote server of the entity that provisioned the app. The app can use the User attributes retrieved from the Wallet Unit itself, for example for
User authentication or to automatically fill in data fields like User name and address. Alternatively, the app can send these User attributes to the remote server. All requirements on Relying Parties in this ARF, such as those regarding Relying Party registration and authentication, User consent, and other aspects, obviously are applicable in this use case as well.

In this use case, the attribute presentation flow begins when the User opens the
app and initiates a request for attributes from the Wallet Unit via the
WI-platform API. Notably, this is the same API used in remote same-device
presentation flow involving a browser. The primary difference lies in the origin
information included in the presentation request, which may vary.

##### 4.4.3.3 Cross-device remote presentation flows

![Figure 5](media/Figure_5_Remote_Cross-Device_Flow.jpeg)
Figure 5: Remote cross-device presentations

A remote cross-device attribute presentation flow begins when the User uses a
browser on a device different from their User device to visit the website of the
Relying Party. The website may offer the User the possibility to present
attributes from their Wallet Unit, for example by clicking a button. If the User
does so, the browser may ask the User for permission to initiate the presentation flow. If the User allows this, the Relying Party Instance sends a presentation
request to the browser over the Digital Credentials API. The browser then
establishes a tunnel towards the User device, using the FIDO CTAP 2.2 hybrid
flow, see section 11.5 of [CTAP]. Note that this flow is also used for FIDO
Passkeys. This is done as follows:

 1. The browser presents a QR code that includes information about the tunnel
 endpoint, as well as keys that will be used for establishing a secure channel
 over this tunnel.
 2. The User scans the QR code using the camera on the User device.
 3. The User device emits a BLE advertisement, which is received by the browser.
 The advertisement includes, in an encrypted form, information required for
 establishing the secure tunnel. This advertisement is used as a proximity
 check: the tunnel cannot be established if the User device and the device on
 which the browser runs are not close to each other.
 4. A tunnel is established between the two devices.

The browser then sends the OpenID4VP-compliant presentation request to the User
device. If there are multiple Wallet Instances present on the User device, the
device OS will determine to which of these the request will be forwarded,
possibly after consulting the User. The selected Wallet Unit will process the
presentation request and, after requesting approval from the User, will return
the requested attributes in encrypted format to the browser, using the
established tunnel. The browser will forward the response to the remote Relying
Party Instance.

Note that the Wallet Instance does not see any difference between the
cross-device flow and the same-device flow. In both cases, it receives an
OpenID4VP-compliant presentation request over the WI-platform API described in
the previous section.

##### 4.4.3.4 Profiling the use of [OpenID4VP] in remote presentation flows

As mentioned above, for both same-device and cross-device remote presentation
flows, the messages used to request and present attestations comply with
[OpenID4VP]. The OpenID Foundation is standardising a profile for the W3C
Digital Credentials API, that will define how OpenID4VP will be used over this
API.

In addition, there are two other profiles that will be used by Wallet Units and
remote Relying Parties:

- [ISO/IEC 18013-7] Annex B contains a profile for OpenID4VP. Relying Parties
and Wallet Unit will comply with the requirements in this profile when the
format of the attestation complies with [ISO/IEC 18013-5].
- Otherwise, i.e. when the format of the attestation complies with [SD-JWT VC],
Relying Parties and Wallet Unit will comply with the requirements in the profile for SD-JWT VCs
specified in [HAIP].

### 4.5 WSCD architecture types

#### 4.5.1 Introduction

Figure 2 showed four different types of architecture for the WSCD, which are:

- Remote WSCD
- Local external WSCD
- Local internal WSCD
- Local native WSCD

In addition, this section also describes a hybrid architecture. Within the EUDI
Wallet ecosystem, a Wallet Provider is allowed to use any of these architectures.

Notes:

- Regardless of the architecture used, the Wallet Provider is
responsible for ensuring that the Wallet Instance can access a WSCD that has a
level of security sufficient to ensure that the Wallet Unit can achieve Level of
Assurance High, as required in the [European Digital Identity Regulation]. The
Wallet Provider remains responsible for managing cryptographic keys on the WSCD
(through the WSCA) throughout the lifetime of the Wallet Unit. The Wallet
Provider is also responsible for attesting the properties of the WSCD (including
relevant certifications) in the Wallet Unit Attestation, see [Section
6.5.3](#653-wallet-unit-activation).
- Again regardless of the architecture used, User access to the WSCD always involves two authentication factors: physical access to the User device and a knowledge-based authentication factor verified by the WSCA. If the WSCA/WSCD is local, the second authentication factor is directly verified by the WSCA. If it is remote, the Wallet Unit must contain an access token (or similar mechanism) to authenticate the Wallet Unit towards the WSCA and set up a secure communication channel. Over that channel, the PIN entered by the User is transferred to the WSCA and verified by it. See the requirements on User authentication in the section on Wallet Unit management in [Topic 40](./annexes/annex-2/annex-2-high-level-requirements.md#a2340-topic-40---wallet-instance-installation-and-wallet-unit-activation-and-management).

#### 4.5.2 Remote WSCD

In this architecture, the Wallet Secure Cryptographic Device is situated
remotely from the User device. Typically, it will be implemented by the Wallet
Provider using an HSM running on a secure server. The Wallet Provider will also
provide the WSCA with which the Wallet Unit interacts.

This architecture is typically used if the User device lacks sufficiently secure
hardware, or if the Wallet Provider does not want to have a dependency on such
hardware.

#### 4.5.3 Local external WSCD

If the User device lacks sufficiently secure hardware, another option is to use
a local external hardware component as the WSCD. This local external WSCD is
typically a smart card or a secure token. It is connected to the User device via
NFC or another short-range connection, and is able to perform all of the
cryptographic operations required from a WSCD / WSCA in the ARF. Note that many
existing smart cards, such as identity cards, will not be able to do this.

The WSCA typically takes the form of a Java Card applet. The WSCA is installed
prior to issuance of the smart card or secure token to the User. The issuer of
the WSCD and of the WSCA is the Wallet Provider or another entity acting on
behalf of or in cooperation with the Wallet Provider.

#### 4.5.4 Local internal WSCD

In this architecture, the Wallet Secure Cryptographic Device is integrated
directly within the User's device. This includes solutions like UICCs,
e-SIM/SAMs, or embedded Secure Elements. Such solutions typically are compliant
with the GlobalPlatform Card Specifications [GP CS] or with the GSMA Secured
Applications for Mobile [GSMA SAM] specification.

The WSCA will typically be a Java Card applet, and it is remotely issued to the
WSCD by the Wallet Provider, at the moment the Wallet Unit is activated; see
[Section 6.5.3](#653-wallet-unit-activation). In order to do this, the Wallet
Provider may need to connect to and collaborate with other entities, such as a
Trusted Service Manager employed by the owner of the WSCD.

The Wallet Provider is responsible for verifying that the local internal WSCD is
compliant with all applicable requirements, prior to activating a Wallet Unit
using such a WSCD.

#### 4.5.5 Local native WSCD

A local native WSCD is integrated into the User device. However, the API to
access the WSCD is included in the operating system of the User device.
Therefore, no separate WSCA is necessary. Alternatively, the API offered by the
OS may be viewed as the WSCA.

The Wallet Provider is responsible for verifying that the local native WSCD is
compliant with all applicable requirements, prior to activating a Wallet Unit
using such a WSCD.

#### 4.5.6 Hybrid architecture

In this architecture, two or more of the different types of WSCD described above
are combined. For example, a remote HSM may manage the cryptographic keys of the
Wallet Unit and of PIDs and attestations present in the Wallet Unit, while an
embedded Secure Element is used to manage the access to the remote HSM.

### 4.6 State diagrams

#### 4.6.1 Introduction

In this section, state diagrams are presented for Wallet Solutions, Wallet
Units, PID Providers and Attestation Providers, PIDs and attestations, and
Relying Parties.

#### 4.6.2 Wallet Solution

A Wallet Solution has a state diagram of its own. The state of a Wallet Solution
affects the state of all Wallet Units of that Wallet Solution. Figure 6 below
shows the states of the Wallet Solution:

![Figure 6](media/Figure_6_Statechart_Wallet_Solution.png)

Figure 6: State diagram of Wallet Solution

The **Candidate** state is the first state of a Wallet Solution. This means it
is fully implemented and the Wallet Provider requests the solution to be
certified as a Wallet Solution as part of an EUDI Wallet eID scheme.

If all the legal and technical criteria have been met, a Member State may decide
to allow a Wallet Provider to start providing the Wallet Solution to Users. The
state of the Wallet Solution becomes **Valid**. This means the Wallet Solution
can be officially launched, and can be provided to Users. The issuing Member
State informs the Commission of each change in the certification status of their
EUDI Wallet eID schemes and the Wallet Solutions provided under that scheme.

The issuing Member State can temporarily suspend a Wallet Solution. This would
for example be the result of a critical security issue. This leads to the
**Suspended** state. The issuing Member State can unsuspend the Wallet Solution,
bringing the Solution back to the **Valid** state. The issuing Member State can
also decide to completely withdraw the Wallet Solution, which brings the Wallet
Solution in the **Withdrawn** state.

A Wallet Unit that is part of a suspended or withdrawn Wallet Solution Provider
cannot request the issuance of a PID or attestation. Nor will a PID or
attestation presented by such a Wallet Unit be accepted by a Relying Party.

#### 4.6.3 Wallet Unit

Figure 7 below shows the states of a Wallet Unit.

![Figure 7](media/Figure_7_Statechart_Wallet_Unit.png)

Figure 7: State diagram of Wallet Unit

A Wallet Unit lifecycle begins when the User installs a Wallet Instance on their
User device, see [Section 6.5.2](#652-wallet-instance-installation). The Wallet
Unit's state is then **Installed**. In this state, the User and the Wallet
Provider can perform only one action, namely activating the Wallet Unit, as
described in [Section 6.5.3](#653-wallet-unit-activation). As part of the
activation process, the Wallet Provider issues one or more Wallet Unit Attestations (WUA)
to the Wallet Unit.

Once a Wallet Unit is activated, it is in the **Operational** state. In this
state, the User and the Wallet Provider manage the Wallet Unit and can perform
the same actions as in the **Valid** state, see below. However, obviously, the
User cannot identify nor authenticate themselves by presenting a PID to a
Relying Party, nor can any other action with a PID be performed, because by
definition no valid PID is present in this state.

If, in the **Operational** state, a PID Provider issues a PID to a Wallet Unit,
it transitions to the **Valid** state. If, in either of these two states, the
Wallet Provider revokes the WUA or the WUA expires, the Wallet Unit moves back
to **Installed**.

The following actions can be performed in the **Valid** state:

- The Wallet Provider updates the Wallet Unit to a new version,
- The Wallet Provider revokes the Wallet Unit, for instance at the User's
request or if the security of the Wallet Instance is broken. Revocation of the
Wallet Unit is accomplished by revoking the Wallet Unit Attestation (see
[Topic 9](./annexes/annex-2/annex-2-high-level-requirements.md#a239-topic-9---wallet-unit-attestation)
and [Topic 38](./annexes/annex-2/annex-2-high-level-requirements.md#a2338-topic-38---wallet-unit-revocation)).
- The User requests issuance of a PID, a QEAA, a PuB-EAA, or an EAA.
- The User presents attributes from a PID, a QEAA, a PuB-EAA, or an EAA to a
Relying Party.
- The User deletes a PID, a QEAA, a PuB-EAA, or an EAA.
- A PID, a QEAA, a PuB-EAA, or an EAA is revoked by its Provider (if it is valid
for more than 24 hours).
- The User uninstalls the Wallet Instance.

If the last or only PID in the Wallet Unit expires, is revoked, or is deleted,
the Wallet Unit's state is moved back to **Operational**. Note that if there are
multiple PIDs in the Wallet Unit, it does not move to the **Operational** state
as long as at least one of them is valid.

#### 4.6.4 PID Provider or Attestation Provider

Figure 8 shows the possible states of a PID Provider or Attestation Provider.

![Figure 8](media/Figure_8_Statechart_PID_Provider_Attestation_Provider.png)

Figure 8: State diagram of PID Provider or Attestation Provider

The **Valid** state is the first state of a PID Provider or Attestation
Provider. This means it is registered by the corresponding Trusted List Provider (Registrar)
and notified to the Commission, as described in [Section 6.3.2](#632-pid-provider-or-attestation-provider-registration-and-notification).

The Trusted List Provider can temporarily suspend a PID Provider or Attestation
Provider. This leads to the **Suspended** state. The Trusted List Provider can
unsuspend the PID Provider or Attestation Provider, bringing it back to the
**Valid** state. The Trusted List Provider can also decide to completely
cancel registration of the PID Provider or Attestation Provider, which brings it in the
**Cancelled** state. For more information about suspension or cancellation, please
refer to [Section 6.3.3](#633-pid-provider-or-attestation-provider-suspension-or-cancellation).
A PID Provider or Attestation Provider with suspended or cancelled registration cannot issue PIDs or
attestations to Wallet Units, nor will a PID or attestation issued by such a PID
Provider or Attestation Provider be accepted by Relying Parties.

#### 4.6.5 PID or attestation

Figure 9 shows the possible states of a PID or attestation.

In the context of the EUDI Wallet ecosystem, a PID or attestation begins its
lifecycle when being issued to a Wallet Unit. Please note that this means that
the management of attributes in the Authentic Source (adhering to national
structures and attribute definitions) is outside the scope of the ARF.

For certain use cases, a PID or attestation may be pre-provisioned, meaning it
is not yet valid when issued. In that case, its state is **Issued**, and it will
transition to **Valid** when it reaches the beginning of its validity period.
However, if a PID or attestation is issued on or after the validity start date,
its state directly changes to **Valid**.

![Figure 9](media/Figure_9_Statechart_PID.png)

Figure 9: State diagram of PID or attestation

There are two possible transitions for a valid PID or attestation: it expires by
passing through the validity end date and transitions to the **Expired** state,
or it is revoked by its PID Provider or Attestation Provider, ending up in the
**Revoked** state. Expiration and revocation are independent transitions. Once a
PID or attestation is expired or revoked, it cannot transition back to
**Valid**.

#### 4.6.6 Relying Party

Figure 10 shows the possible states of a Relying Party.

![Figure 10](media/Figure_10_Statechart_Relying_Party.png)

Figure 10: State diagram of Relying Party

The **Valid** state is the first state of a Relying Party. This means it has
been registered by a Relying Party Registrar, as described in [Section 6.4.2](#642-relying-party-registration).

The Registrar can suspend or cancel registration of a Relying Party.
This leads to the **Suspended** state. The Registrar can
unsuspend the Relying Party, bringing it back to the
**Valid** state. The Registrar can also decide to completely
cancel registration of the PID Provider or Attestation Provider, which brings it in the
**Cancelled** state. For more information about suspension or cancellation, please
refer to [Section 6.4.3](#643-relying-party-de-registration).
A Wallet Unit will not present a PID or attestation to a Relying Party that its registration is suspended or cancelled.


### 4.7 Pseudonyms

#### 4.7.1 Introduction to Passkeys

As specified in [CIR 2024/2979], [W3C WebAuthn] defines the technical
specification for pseudonyms. Passkeys are a widely used type of credential
which are created and asserted using the WebAuthn API.

Passkeys are to be seen as an alternative to passwords. The idea is that a User,
when registering a user account at a service, uses a secure device to generate a
public-private key pair, registers the public key at the service, and can then
subsequently use the private key to authenticate towards the service at later
points in time.

In a bit more detail, the flow for using Passkeys is as follows:

**Registration:**

1. The User generates a public-private key pair and stores both the public and
the private key at their secure device (referred to as an Authenticator).
2. The User registers the public key at the desired Relying Party service.

**Authentication:**

1. When the User wishes to authenticate towards a service, the service will send
them a challenge consisting of a random value.
2. The User uses the private key stored on their Authenticator to sign the
challenge and sends this back to the service.
3. The service verifies that the signature on the challenge can be verified
using the registered public key. If the signature verifies and the origin
matches the expected origin, the User is considered authenticated and thereby
granted access to the service.

For high-level requirements on the use of WebAuthn and Passkeys, see [Topic 11](./annexes/annex-2/annex-2-high-level-requirements.md#a2311-topic-11---pseudonyms). Note that the Commission will create or reference a technical specification containing all details necessary for Wallet Units and Relying Parties to generate, register, and use Pseudonyms.

#### 4.7.2 Introduction to [W3C WebAuthn]

##### 4.7.2.1 Overview

[W3C WebAuthn] defines an API for the creation and use of Passkeys.
Conceptually, in addition to the User, there are four different logical
components in this specification:

- **Relying Party Server:** The Relying Party that wishes to offer a service
based on authentication using Passkeys.
- **Relying Party Client:** The program provided by the Relying Party that runs
in the Client of the User and communicates with the Relying Party Server. The
Relying Party Client is typically some JavaScript code, provided by the Relying
Party, that runs on the Client (i.e., browser).
- **Client:** The client that the User uses to interact with the Relying Party's
server and with the User's authenticator. The Client can be thought of as the
browser that the User uses to access the Relying Party's service.
- **Authenticator:** The device controlled by the User to create, store, and use
the Passkeys. In the context of the EUDI Wallet, the Wallet Unit is the
Authenticator.

Note that the Relying Party Client and the Client are two programs that are
executed on the same physical machine.

[W3C WebAuthn] defines a model dividing the responsibilities between these
different entities and defines an interface between the Relying Party Client and
the Client. Additionally, it defines a challenge/response protocol to
authenticate with Passkeys. The interface is referred to as the *WebAuthn API*.

However, [W3C WebAuthn] does not specify how the Authenticator and the Client
must communicate.

[W3C WebAuthn] relies on several different types of identifiers, including:

- **Relying Party ID:** An identifier unique to the Relying Party, which must be
a valid domain string. This what the User will identify the Relying Party by and
let the Authenticator learn which Relying Party is asking for
registration/authentication.
- **Credential ID:** A unique identifier chosen by the Authenticator for each
Passkey.
- **User ID:** An identifier unique to each User, which is assigned by the
Relying Party. This will be provided to the Authenticator when registering a new
Passkey. Subsequently, it will be provided by the Authenticator when
authenticating towards the Relying Party. The Authenticator will keep track of
which Passkeys are available for which User IDs and Relying Party IDs. The
Relying Party keeps track of a User Name for each User ID.
- **User Name:** An alias that may be chosen by the User or the Relying Party
and assigned to a specific Passkey on the Authenticator. This allows the User to
easily distinguish and select which Passkey they want to authenticate with, if
several are present in the Authenticator for the given Relying Party.

The next sections elaborate on how the different components work together to
allow the registration and subsequent authentication using Passkeys.

##### 4.7.2.2 Registration

The flow for registering a Passkey in [W3C WebAuthn] is the following:

0. The User requests (out of band of WebAuthn) the Relying Party to create a new
Pseudonym.
1. The Relying Party Server creates a challenge and sends this along with the
User ID, the Relying Party ID, and the User Name to the Relying Party Client.
2. The Relying Party Client forwards the information to the Client using the WebAuthnAPI.
3. The Client checks that the Relying Party ID is consistent with the caller's
origin and forwards the information to the Authenticator along with other
contextual data.
4. The Authenticator authenticates the User (for example using a PIN or via
biometrics). It then generates a new key pair with a new Credential ID and set
the scope of this to the specific Relying Party ID and User ID. Finally, the
Authenticator may generate an attestation (explained in [Section
4.7.2.3](#4723-pseudonym-attestation)) and send this, as well as the public key
and its Credential ID, to the Client.
5. The Client then forwards the information to the Relying Party Client that
again forwards it to the Relying Party Server.
6. The Relying Party Server verifies the attestation (if present) and registers
the received public key for this User ID.

Note that the Authenticator stores the public key in a way such that it is
scoped uniquely to a specific Relying Party, aligning with the requirements of
[CIR 2024/2979], Article 14 (2), which states that the pseudonyms must be unique
to each Relying Party.

##### 4.7.2.3 Pseudonym attestation

The term 'attestation' is here used differently than elsewhere in the ARF. In
this context, the attestation is not about attributes of the User, but rather
about attributes of the Authenticator. The attestation serves to ensure the
Relying Party that they are talking with an Authenticator with certain
attributes. The attestation often takes the form of a signature on the challenge
as well as some other contextual data.

In [W3C WebAuthn], five different types of attestations are mentioned:

- **Basic Attestation:** The Authenticator stores a single master public and
private key. The private key is used to sign all attestations and a certificate
on the public key is included in the attestation data to allow the Relying Party
to verify the signature.

- **Attestation CA:** Similar to the above, in the sense that the Authenticator
stores a single master public and private key. However, instead of using
this to attest Passkeys, the Authenticator uses this to authenticate towards a
Certificate Authority (CA), which is configured to issue certificates to
the Authenticator on multiple attestation key pairs. The Authenticator then uses these attestation private keys to sign attestations.

- **Anonymisation CA:** Similar to the second bullet above, except that it is
explicit that the Authenticator requests a certificate for a new attestation key
pair per generated Passkey.

- **Self Attestation:** The attestation is signed with the private key of the
newly generated key pair in the Passkey. Note that this does not give any
guarantees for the Relying Party about the Authenticator they are interacting
with.

- **No Attestation Statement:** No attestation is given. Note that this does not
give any guarantees for the Relying Party about the Authenticator they are
interacting with.

Please note that Article 5a (5) a) viii) of the [European Digital Identity
Regulation] states "*European Digital Identity Wallets shall, in particular
support common protocols and interfaces: ... for relying parties to verify the
authenticity and validity of European Digital Identity Wallets;...*". The latter
two forms of attestation do not align with this requirement.
[Section 5.1 of the Discussion Paper for Topic E](./discussion-topics/e-pseudonyms-including-user-authentication-mechanism.md#51-topic-a-privacy-risks-and-mitigations)
discusses how the other three possibilities relate to privacy risks about User
surveillance identified in [Section
7.4.3.5](#7435-risks-and-mitigation-measures-related-to-user-privacy).

#### 4.7.2.4 Authentication

The flow for authentication using a Passkey following [W3C WebAuthn] is:

1. The Relying Party Server creates a challenge and sends this along with its
Relying Party ID to the Relying Party Client.
2. The Relying Party Client forwards the information to the Client using the
WebAuthn API.
3. The Client checks that the Relying Party ID is consistent with the caller's
origin and forwards the information to the Authenticator along with other
contextual data.
4. The Authenticator authenticates the User (for example using a PIN or via
biometrics). It then prompts the User to select one of the Passkeys scoped to
this Relying Party ID, if there are multiple. For this step the User Name can be
presented to the User. Finally, the Authenticator uses the private key of the
chosen key pair (= Passkey) to sign the challenge as well as some contextual
data including the User ID, Credential ID, and the Relying Party ID. The
Authenticator then sends this to the Client.
5. The Client forwards the information to the Relying Party Client, which again
forwards it to the Relying Party Server.
6. The Relying Party Server verifies the signature with the stored public key
for this User ID and Credential ID, and, depending on the outcome of this
verification, considers the User to be authenticated.

## 5 Data model and data exchange protocols

### 5.1 Attestation elements

Within the EUDI Wallet ecosystem, data is exchanged in the form of Electronic
Attestations of Attributes (EAA), hereafter referred to as "attestations." Apart
from EAA, the [European Digital Identity Regulation] explicitly defines another
category of data, called Person Identification Data (PID), see [Section 5.2](#52-attestation-categories).

Each PID and attestation consists of the following key elements:

- A set of **attributes**, which provide information about the subject of the
attestation. The subject of the PID or attestation may be a natural person or a
legal person. A Relying Party will request one or more of these attributes to
get the reliable information they need to provide some service to the User. The
set of attributes that an attestation may contain is defined in an attribute
schema, see below.

- A set of **metadata**, meaning information about the attestation itself, such
as its attestation type (PID, mDL, diploma, etc.), its Attestation Provider, and
its administrative validity period, if applicable. This kind of metadata is also
defined in an attribute schema. In addition, metadata also includes information
that is necessary to ensure the security of the attestation. This includes at
least its technical validity period. It also includes a public key of the
attestation, which a Relying Party will use to verify that the attestation was
not copied, see [Section 6.6.3.8](#6638-relying-party-instance-verifies-device-binding).
It may also include information allowing the Relying Party to verify that the attestation
was not revoked, see [Section 6.6.3.7](#6637-relying-party-verifies-that-the-pid-or-attestation-is-not-revoked).

- A **proof**, which ensures the integrity, authenticity, and support of
selective disclosure of the attestation. The format of the proof complies with
the proof mechanism specified for this type of attestation, see below. The proof
includes information that enables a Relying Party to verify the proof, for
example a Attestation Provider certificate and a reference to a trust anchor
that can be used to verify that certificate.

An **attribute schema** defines the logical organisation of all mandatory and
optional attributes within an attestation, as well as the format of each
attribute, meaning its unique identifier, encoding, allowed values, and
serialisation. In addition, an attribute schema specifies some of the
attestation metadata, such as its attestation type and information about its
Attestation Provider, validity period, etc. Within the EUDI Wallet ecosystem,
the attribute schema for each attestation type is specified by an Attribute
Schema Provider in an Attestation Rulebook according to [Section 5.4](#54-attribute-schemas-and-attestation-rulebooks).

A **proof mechanism** defines the method used to create the attestation proof.
For example, a 'standard' digital signature is a proof ensuring integrity and
authenticity, but not allowing selective disclosure. Proof mechanisms are
specified in standards or technical specifications. The attestation formats
listed in [Section 5.3](#53-attestation-formats-and-proof-mechanisms) either specify a
proof mechanism that allows for selective disclosure, or leave it to other
technical specifications to do so.

### 5.2 Attestation categories

#### 5.2.1 Overview

Within the European Digital Identity Wallet ecosystem, the [European Digital
Identity Regulation] distinguishes four legal categories of attestations:

- Person Identification Data (PID),
- Qualified Electronic Attestation of Attributes (QEAA),
- Electronic attestation of attributes issued by or on behalf of a public sector body responsible for an authentic source (PuB-EAA),
- Non-Qualified EAA.

The next subsections give more information about each of these categories.
Please note that the differences between them are purely legal. For example, a
diploma may be a QEAA or a non-qualified EAA, depending on whether it is issued
by a qualified trust service provider (QTSP) or by an unqualified one.
Similarly, an mDL may be issued as a PuB-EAA, a QEAA, or a non-qualified EAA,
depending on the legal status of the party issuing mobile driving licences in
each Member State. From a technical point of view, all PIDs, QEAAs, PuB-EAAs,
and EAAs comply with one of the attestation formats listed in [Section 5.3](#53-attestation-formats-and-proof-mechanisms).

#### 5.2.2 Person Identification Data (PID)

A PID is a set of data that is issued in
accordance with Union or national law and that enables the establishment of the
identity of a natural or legal person, or of a natural person representing
another natural person or a legal person.

Besides the fact that the Regulation defines the PID as a category of data that
is legally distinct from Electronic Attestations of Attributes (EAA), another
difference between PID and EAA is that the presence or absence of a valid PID
determines whether a Wallet Unit is in the Operational or the Valid state, as
discussed in [Section 4.6.3](#463-wallet-unit).

As implied in that section, it is possible for a Wallet Unit to contain multiple
PIDs. If the User has multiple nationalities, they may be able to
receive a PID from multiple PID Providers in a single Wallet Unit. However,
please note that a Wallet Provider is free to decide that its Wallet Unit does
not support all PID Providers, and that, conversely, a PID Provider may decide
that it does not support all Wallet Solutions; see [Section 6.5.2.3](#6523-user-validates-that-wallet-solution-is-usable-with-relevant-pid).
Note that the subject of all PIDs in the Wallet Unit will be
the same person, namely the User of the Wallet Unit.

For more information, please refer to [Section 3.4](#34-person-identification-data-pid-providers).

#### 5.2.3 Qualified Electronic Attestation of Attributes (QEAA)

A QEAA is an electronic attestation of attributes which is issued by a qualified
trust service provider (QTSP) and meets the requirements laid down in Annex V of
the Regulation. For more information, please refer to [Section 3.6](#36-qualified-electronic-attestation-of-attributes-qeaa-providers).

#### 5.2.4  Electronic attestation of attributes issued by or on behalf of a public sector body responsible for an authentic source (PuB-EAA)

A PuB-EAA is an electronic attestation of attributes issued by a public sector
body that is responsible for an authentic source or by a public sector body that
is designated by the Member State to issue such attestations of attributes on
behalf of the public sector bodies responsible for authentic sources in
accordance with Article 45f and with Annex VII of the Regulation.

For more information, please refer to [Section 3.7](#37-eaa-issued-by-or-on-behalf-of-a-public-sector-body-responsible-for-an-authentic-source-pub-eaa-providers).

#### 5.2.5 Non-Qualified EAA

A non-qualified EAA is an EAA which is not a QEAA or a PuB-EAA. For more
information, please refer to [Section 3.8](#38-non-qualified-electronic-attestation-of-attributes-eaa-providers).

### 5.3 Attestation formats and proof mechanisms

#### 5.3.1 Overview

[Section 5.1](#51-attestation-elements) listed a proof mechanism as one of the
key elements needed to define a type of attestation. The proof mechanism for an
attestation is closely related to the format of that attestation. Within the
EUDI Wallet ecosystem, the following standardised formats for electronic
attestations of attributes can be used:

- The format specified in [ISO/IEC 18013-5] and generalised in [ISO/IEC 23220-2],
- The format specified in 'SD-JWT-based Verifiable Credentials' [SD-JWT VC],
- The format specified in 'W3C Verifiable Credentials Data Model v2.0'[W3C VCDM 2.0].

The next subsections give more information about each of these formats and
specifications, and explain where the different elements of an attestation, as
explained in [Section 5.1](#51-attestation-elements) are defined for that
attestation format.

Within the EUDI Wallet ecosystem, Wallet Units will support the first two
formats above. Support for the third format is optional and meant for
non-qualified EAAs only. [Topic 12](./annexes/annex-2/annex-2-high-level-requirements.md#a2312-topic-12---attestation-rulebooks)
states the detailed requirements regarding support by Wallet Units, PID
Providers, and Attestation Providers for these formats and specifications.

#### 5.3.2 ISO/IEC 18013-5 and ISO/IEC 23220-2

The ISO/IEC 18013-5 standard was originally developed as a standard for mobile
driving licenses (mDL) and mDL readers. In terms of this ARF, an mDL is a Wallet
Unit containing an mDL attestation (as defined in the [mDL Rulebook](./annexes/annex-3/annex-3.02-mDL-rulebook.md)), while an mDL reader is
a Relying Party requesting such an attestation.

ISO/IEC 18013-5 specifies:

- An attribute schema containing all attributes and metadata for an mDL. The
schema specifies the semantics of these, as well as their encoding in Concise
Binary Object Representation (CBOR), see [RFC 8949]. The standard also specifies
the use of namespaces to avoid collision of attribute identifiers.
- A proof mechanism ensuring the authenticity and integrity of a PID or
attestation, while allowing selective disclosure of attributes.
- A security mechanism enabling device binding of PIDs and attestations, see
[Section 6.6.3.8](#6638-relying-party-instance-verifies-device-binding),
- All other aspects necessary to securely request, present, and verify an mDL
attestation in proximity flows, see [Section 5.6.2](#562-secure-data-exchange-using-isoiec-18013-5-and-isoiec-18013-7).

Point to note about ISO/IEC 18013-5:
- the mDL attribute schema (see
first bullet above) is the only aspect of ISO/IEC 18013-5 that is specific for mDLs.
All other aspects are generic and can be used for any other attestation type,
including PIDs. This means that another ISO/IEC 18013-5-compliant attestation
type can be created simply by specifying an appropriate attribute schema using
CBOR, and referring to ISO/IEC 18013-5 for all other details. Please refer to
[Chapter 4 of the PID Rulebook](./annexes/annex-3/annex-3.01-pid-rulebook.md#4-isoiec-18013-5-compliant-encoding-of-pid)
for an example. Within the EUDI Wallet ecosystem, such an attribute schema is
specified in an Attestation Rulebook, see [Section 5.4](#54-attribute-schemas-and-attestation-rulebooks). ISO/IEC 23220-2 specifies a generic set of attributes for use in different attestation types, and also specifies how these can be encoded in CBOR.
- An ISO/IEC standard for mobile documents in general (not mDLs specifically) is
in preparation and will become ISO/IEC 23220-4. This standard will generalise
ISO/IEC 18013-5, in the sense that it will allow more options and communication
flows. Once that standard is published, all references in this ARF to ISO/IEC
18013-5 may be replaced by appropriate references to ISO/IEC 23220-4. However,
at the moment ISO/IEC 23220-4 is not finished yet and therefore cannot be
referenced.

#### 5.3.3 SD-JWT VC

'SD-JWT-based Verifiable Credentials' [SD-JWT VC] specifies a data format and
processing rules to express verifiable credentials (i.e., attestations).
"SD-JWT" here stands for 'Selectively Disclosable JSON Web Token'. As that name
suggests, SD-JWTs are a special form of JWTs [RFC 7519] that are selectively
disclosable. The mechanisms used to make them selectively disclosable is often
described as using 'salted hashes', and is conceptually identical to the
mechanism used for the same purpose in [ISO/IEC 18013-5].

[SD-JWT VC] specifies the following aspects:

- The encoding to be used for attributes and metadata, namely JSON, as well as
rules to prevent collisions of claim names,
- A proof mechanisms ensuring the authenticity and integrity of a PID or
attestation, while allowing selective disclosure of attributes, see above.
- A security mechanism enabling device binding of PIDs and attestations, see
[Section 6.6.3.8](#6638-relying-party-instance-verifies-device-binding).

In addition to these aspects, within the EUDI Wallet ecosystem,

- attribute schemas for specific SD-JWT VC-compliant attestation types will be
specified in Attestation Rulebooks, see [Section 5.4](#54-attribute-schemas-and-attestation-rulebooks).
Please refer to [Chapter 5 of the PID Rulebook](./annexes/annex-3/annex-3.01-pid-rulebook.md#5-sd-jwt-vc-based-encoding-of-pid)
for an example.
- SD-JWT VC-compliant attestations will be requested and presented using
[OpenID4VP], see [Section 5.6.3](#563-secure-data-exchange-using-openid4vp).

Since [SD-JWT VC] contains a number of options, the use of the profile for
SD-JWT VCs specified in [HAIP] is necessary to ensure interoperability between
Wallet Units and Relying Parties.

#### 5.3.4 W3C Verifiable Credentials

The W3C Verifiable Credentials Data Model [W3C VCDM 2.0] defines a general data model,
offering a high-level structure but leaving many technical aspects open for further
definition, including:

- Security mechanisms
- Signature formats
- Transport protocols

Key features of W3C VCDM are:

- JSON-LD (Linked Data)-based: The use of JSON-LD ensures structured and
interoperable data exchange, but introduces complexity.
- Extensible Framework: Allows different implementations but requires
additional specifications.
- Security and Signature Formats: Not inherently defined — must be specified separately.

To implement W3C VCDM-based attestations, separate specifications are needed for
security mechanisms and signatures, such as:

1. 'Securing Verifiable Credentials using JOSE and COSE' [W3C VC-JOSE-COSE]:
Defines how to use one of the following to secure attestations in the VCDM
model:
    - a JWT (see [RFC 7519]),
    - a SD-JWT (see the [previous section](#533-sd-jwt-vc)), or
    - a CBOR Web Token (CWT, see [RFC 8392]).
1. 'Verifiable Credential Data Integrity' [W3C VC Data Integrity]: Provides a
cryptographic proof format independent of JWT or CWT, relying on detached proofs
(not embedded signatures) for better flexibility.

These mechanisms offer different trade-offs, allowing PID Providers or
Attestation Providers and Relying Parties to choose the appropriate security
model based on their privacy, interoperability, and trust requirements. In order
to achieve interoperability, the specification of a profile standard making
specific choices will be necessary.

In addition to these aspects, within the EUDI Wallet ecosystem,

- attribute schemas for specific W3C VCDM-compliant attestation types (if any)
will be specified in Attestation Rulebooks, see [Section 5.4](#54-attribute-schemas-and-attestation-rulebooks).
- W3C VCDM-compliant attestations may be requested and presented using
[OpenID4VP], see [Section 5.6.3](#563-secure-data-exchange-using-openid4vp).
However, this ARF does not require this, and for any W3C VCDM-compliant
attestation, the applicable transport protocol must be defined in the
corresponding Rulebook.

See [chapters 3 and 4 of the Discussion Paper for Topic V](./discussion-topics/v-pid-rulebook.md#3-attestation-formats)
for more considerations regarding the SD-JWT VC and W3C Verifiable Credential
formats and their interoperability within the EUDI Wallet ecosystem.

### 5.4 Attribute schemas and Attestation Rulebooks

[Section 5.1](#51-attestation-elements) listed an attribute schema as one of the
key elements needed to define a type of attestation. This section specifies the
concept of an Attestation Rulebook. For each type of attestation, such as a PID,
an mDL, a diploma, or an e-prescription, an Attestation Rulebook specifies the
attribute schema and proof mechanisms of that attestation, and, when required,
the trust mechanisms for authentication and authorisation. Each attestation has
an attestation type. The attribute schema specified in the Attestation Rulebook
defines the unique identifier, syntax, and semantics of all attributes that can
be part of that attestation.

An Attestation Rulebook also makes some choices regarding the protocol(s) for
presentation that must be supported by the relevant attestations. [Topic 12](./annexes/annex-2/annex-2-high-level-requirements.md#a2312-topic-12---attestation-rulebooks)
contains the requirements for Attestation Rulebooks.

Attestation Rulebooks are defined by Attribute Schema Providers, see [Section 3.15](#315-attribute-schema-providers-for-qeaa-pub-eaa-and-eaa).
This role can be assumed by different types of organisation:

- Some Rulebooks already have been defined by the European Commission, in
consultation with the European Digital Identity Cooperation Group (EDICG).
This concerns the [PID Rulebook](./annexes/annex-3/annex-3.01-pid-rulebook.md)
and the [mDL Rulebook](./annexes/annex-3/annex-3.02-mDL-rulebook.md)
in Annex 3 of the ARF.
- The Rulebook for an attestation intended to be used across organisations
and/or across borders can be defined by an organisation in which, insofar
possible, all stakeholders are represented. This will prevent multiple
Attestation Rulebooks being defined for the same type of attestation, such as
diplomas. It will also prevent unnecessary differences in the syntax and
semantics between similar attestations. The decision on which organisation will
be responsible for a given Attestation Rulebook is out of scope for this
document. As explained in [Topic 12](./annexes/annex-2/annex-2-high-level-requirements.md#a2312-topic-12---attestation-rulebooks),
it is possible that an individual Attestation Provider needs to include
attributes in an attestation that have not been specified in the relevant
sectoral or EU-wide Rulebook. An example of this are attributes that only have a
meaning within the Member State in which the Attestation Provider resides. To
allow such domestic attributes, an Attestation Provider can define a custom
Rulebook to specify attributes that are specific to this Provider and are not
included in the EU-wide or sectoral Rulebook.
- The Rulebook for an attestation intended to be used only within an
organisation will be defined by that organisation.

### 5.5 Catalogues

Section 2 in [Article 45e](https://eur-lex.europa.eu/legal-content/EN/ALL/?uri=CELEX:32024R1183#d1e3883-1-1)
of the Regulation, sets up the direct legal basis for the Commission to "where
necessary, establish specifications and procedures for the catalogue of
attributes and schemes for the attestation of attributes and verification
procedures for qualified electronic attestations of attributes".

One of the main rationales for the ARF is to reach a high level of
interoperability. This interoperability can be achieved on different layers. On
the technical level, interoperability can be achieved by using common standards,
protocols and technical specifications, ensuring common language for Attestation
Providers, Wallet Providers and Relying Parties, enabling issuance, presentation
and processing of attestations, based on agreed common protocols interfaces and
syntax.

The other layer is the semantic one and relates to semantic schemes of
attributes. The risk is that an uncontrolled manner of implementation and usage
will create barriers and complicate the implementation, thus making the
ecosystem much more costly to create and maintain, complex, and error-sensitive,
affecting the quality of the overall system.

For the development and success of the EUDI Wallet ecosystem, re-using the
building blocks of attributes and attestations is therefore essential. Creating
and maintaining controlled vocabularies, a catalogue of attributes, and
Attestation Rulebooks enables shorter 'time-to-market' and efficient
implementation.

Building on the requirements of [Topic 12](./annexes/annex-2/annex-2-high-level-requirements.md#a2312-topic-12---attestation-rulebooks),
having in mind both the need for interoperability on the one hand and the varied
nature of attestations and organisations specifying those attestations on the
other hand, the following principles were defined:

- Attestation Rulebooks for QEAAs and PuB-EAAs used within the EUDI Wallet
ecosystem may be registered and published in a publicly accessible catalogue.
The Attestation Rulebook catalogue may also include Attestation Rulebooks for
non-qualified EAAs.
- The Commission will take measures to establish and maintain the Attestation
Rulebooks catalogue.
- The Attestation Rulebooks catalogue will enable Attestation Providers, Relying
Parties and other actors in the EUDI Wallet ecosystem to know which attestation
types exist, and what are the identifiers, syntax, and semantics of all
attributes that are part of the attestation.

Also, the following points are emphasised, to facilitate creation and adoption:

- Registration of an Attestation Rulebook in the Attestation Rulebook catalogue
is not mandatory.
- Registration does not create any obligation or automatic acceptance by any
third party, or automatically imply cross-border recognition of the type of
attestation described in the Rulebook.
- The Attestation Rulebooks catalogue can be in the same environment as the
catalogue of attributes.

Implementation of these principles will be discussed further in detail. The
ambition is to use existing efforts and tools created by the Member States, the
Commission and cross-border organisations, to connect and interact with the
stakeholders, to utilise existing data assets for updating them when needed and
add new data sets to support new use cases that will be implemented in the EUDI
Wallet ecosystem.

[Topic 25](./annexes/annex-2/annex-2-high-level-requirements.md#a2325-topic-25---unified-definition-and-controlled-vocabularies-for-attributes)
and [Topic 26](./annexes/annex-2/annex-2-high-level-requirements.md#a2326-topic-26---catalogue-of-attestations),
present the current and foreseen status of the catalogues, their creation,
distribution, discovery, management and maintenance, that will allow simple
update procedures, not burdening the process on the one hand, while ensuring
consistent and on-going mechanisms to keep the catalogues updated and accessible
to the relevant actors, both those that create the content and those that use,
consume and process the attributes and the attestations, and - last but not
least - for the general public.

### 5.6 Protocols for secure data exchange between Wallet Units and Relying Parties

#### 5.6.1 Introduction

Within the EUDI Wallet ecosystem, the protocol specified in ISO/IEC 18013-5 is
used for proximity transaction flows, while the protocol specified in OpenID4VP
is used for remote transaction flows. This section briefly describes both of
these protocols.

#### 5.6.2 Secure data exchange using ISO/IEC 18013-5 and ISO/IEC 18013-7

ISO/IEC 18013-5 specifies the following aspects related to secure data exchange:

1. Message structures and transaction flows allowing a Wallet Unit and a Relying
Party to request and present attestations.
2. Proximity interface specifications, allowing a Wallet Unit and a Relying
Party to set up a communication channel using QR code or NFC, and to
subsequently communicate over BLE, NFC, or Wi-Fi Aware.
3. Security mechanisms ensuring
    - the confidentiality and authenticity of all data exchanged between a
    Wallet Unit and a Relying Party,
    - Relying Party authentication, see [Section 6.6.3.2](#6632-wallet-unit-authenticates-the-relying-party-instance).

As already explained in [Section 5.3.2](#532-isoiec-18013-5), although ISO/IEC
18013-5 nominally specified the mobile driving licence, all of the above aspects
are generic and can be used for any type of attestation.

Whereas ISO/IEC 18013-5 specifies proximity transaction flows only, ISO/IEC
18013-7 specifies how to request and present ISO/IEC 18013-5-compliant
attestations in remote transaction flows. This standard specifies three options:

- Using the messages and transaction flows specified in ISO/IEC 18103-5 over an
HTTP-based interface.
- Using [OpenID4VP], see [Section
5.6.3](#563-secure-data-exchange-using-openid4vp). [ISO/IEC 18013-7] specifies a
profile for this standard,
- Using the Digital Credential API, see [Section 4.4.3](#443-remote-presentation-flows).
[ISO/IEC 18013-7] specifies a profile for the use of this API.

Within the EUDI Wallet ecosystem, the second option above will be used for
requesting and presenting ISO/IEC 18013-5-compliant attestations in remote
transaction flows.

#### 5.6.3 Secure data exchange using [OpenID4VP]

The [OpenID4VP] standard defines message structures, transaction flows, and an
HTTP-based interface specification between Wallet Units and Relying Parties.
[OpenID4VP] also specifies security mechanisms ensuring:
    - the confidentiality and authenticity of all data exchanged between a
    Wallet Unit and a Relying,
    - Relying Party authentication.

[OpenID4VP] is suitable only for remote transaction flows.

[OpenID4VP] can be used for transporting attestations in different formats,
including especially the formats used within the EUDI Wallet ecosystem. Within
this ecosystem, [SD-JWT VC]-compliant attestations are always requested and
presented using [OpenID4VP], while [ISO/IEC 18013-5]-compliant attestations are
requested and presented using [OpenID4VP] in remote transaction flows.

Since [OpenID4VP] contains a number of options, the use of the profile for
'OpenID for Verifiable Presentations for IETF SD-JWT VC' specified in [HAIP] is
necessary to ensure interoperability between Wallet Units and Relying Parties.

## 6 Trust model

### 6.1 Scope

The trust model presented in this chapter defines how trust is established,
maintained, validated, and managed among entities within the EUDI Wallet
ecosystem. It outlines the underlying rules, assumptions, and mechanisms that
govern trust relationships, determining whether an entity (such as a Wallet
Unit, User Device, or Relying Party) can be considered trustworthy.

![Figure 11](media/Figure_11_Trust_Model.jpeg)

Figure 11 illustrates the key entities and the relationships in the trust model
of the EUDI Wallet ecosystem.

At its core is the **Wallet Unit** (top middle, blue), which interacts with
various entities throughout its lifecycle. The Wallet Unit lifecycle is detailed in [Section 6.5](#65-trust-throughout-a-wallet-unit-lifecycle) and consists of installation,
activation, management, and uninstallation.
Each Wallet Unit is a configuration of a **Wallet Solution**, comprising a
**Wallet Instance** and one or more WSCA/WSCDs, provided by a **Wallet
Provider**. The Wallet Provider oversees these components and manages their
registration, withdrawal, or suspension (see [Section 6.2](#62-trust-throughout-a-wallet-solution-lifecycle)).
The Wallet Provider ensures that a valid Wallet Unit is in possession of at least one **Wallet Unit Attestation (WUA)**, to enable other entities to
authenticate the Wallet Unit. The Wallet Provider can revoke the WUAs if needed.

The Wallet Unit handles **User PIDs** and **attestations** (QEAAs, PuB-EAAs, and
non-qualified EAAs). PIDs are issued by **PID Providers** and attestations by
**Attestation Providers**, both positioned to the left of the Wallet Unit in
[Figure 11](#61-scope). Before interacting with a Wallet Unit these providers must be
registered with a **PID Provider Registrar** or **Attestation
Provider Registrar**. Upon registration, they receive an **access certificate** (from a
**PID Provider Access CA** or **Attestation Provider Access CA**) and may optain one or more **registration certificates** ( from a **PID Provider Registration CA** or **Attestation Provider Registration CA**).
See [Section 6.3](#63-trust-throughout-a-pid-provider-or-an-attestation-provider-lifecycle).

Once a Wallet Unit receives a PID or attestation, it can present **User
attributes** to **Relying Party Instances** (right side of [Figure 11](#61-scope)). These
instances are hardware/software setups enabling **Relying Parties** to interact
with Wallet Units. Relying Parties register with a **Relying Party Registrar**,
receiving an **access certificate** for each Relying Party Instance, as well as
may obtain one or more **Relying Party Registration Certificates**.
This is discussed in [Section 6.4](#64-trust-throughout-a-relying-party-lifecycle).

[Section 6.6](#66-trust-throughout-a-pid-or-an-attestation-lifecycle) further
details the lifecycle of PIDs and attestations, including issuance,
presentation, management, and deletion.

Notes:

- This conceptual trust model may be implemented with slight variations across
Member States, such as adopting one or multiple Certification Authorities or
leveraging existing entities that already fulfil this role.
- For Access Certificates, PIDs, qualified EAAs, and PuB-EAAs, interoperability
is essential ([Section 4.2.2](#422-interoperability)) and is achieved by using
a PKI following X.509 certificate standards
([RFC5280](https://datatracker.ietf.org/doc/html/rfc5280),
[RFC3647](https://datatracker.ietf.org/doc/html/rfc3647)). Non-qualified EAAs
may adopt alternative trust models and verification mechanisms.
- The model supports both remote and proximity use cases, though technical
measures and authentication mechanisms may vary.
- This version of the ARF does not yet include trust interactions for
**qualified electronic signatures or seals**
(see [Topic 16](./annexes/annex-2/annex-2-high-level-requirements.md#a2316-topic-16---signing-documents-with-a-wallet-unit)
and [Topic 37](./annexes/annex-2/annex-2-high-level-requirements.md#a2337-topic-37---qes----remote-signing---technical-requirements)
in Annex 2).
- Besides the trust relationships described in this chapter, other trust
relations are established as well. For instance, Users, PID Providers,
Attestation Providers, and Relying Parties trust certification bodies and
Trusted List Providers. This trust is primarily rooted in authority and in
procedural measures, such as public oversight, published security and
operational policies, and audits, rather than in technical measures. To verify
that entities are indeed interacting with a trusted authority, standard
technical measures suitable for the context will be used.

### 6.2 Trust throughout a Wallet Solution lifecycle

#### 6.2.1 Wallet Solution lifecycle

[Section 4.6.2](#462-wallet-solution) presented the lifecycle of a Wallet Solution:

1. The Wallet Provider responsible for the Wallet Solution is registered by a
Trusted List Provider. As a result, the Wallet Solution enters the Valid state.
This is discussed in [Section 6.2.2](#622-wallet-provider-registration-and-notification).
2. Under specific conditions, a Trusted List Provider may decide to suspend or
withdraw a registered Wallet Provider. This is discussed in [Section 6.2.3](#623-wallet-provider-suspension-or-withdrawal).

#### 6.2.2 Wallet Provider registration and notification

[Figure 11](#61-scope) depicts the Wallet Provider to the top of the Wallet Unit. To the left
and below of this, the figure also shows that a Wallet Provider registers itself
and its Wallet Solution with a Wallet Provider Trusted List Provider in its
Member State. Subsequently, the Member State notifies the Wallet Provider to the
European Commission.

The Wallet Solution provided by the Wallet Provider is certified as described in
[Chapter 7](#7-certification-and-risk-management).

If the registration and notification processes are successful, the trust anchors
of the Wallet Provider are included in a Wallet Provider Trusted List. During
issuance of a PID or an attestation, the PID Provider or the Attestation
Provider can use these trust anchors to verify the authenticity of a Wallet Unit
Attestation signed by the Wallet Provider, so they can be sure they are dealing
with an authentic Wallet Unit from a trusted Wallet Provider.
See [Section 6.6.2.3](#6623-pid-provider-or-attestation-provider-validates-the-wallet-unit),
[Topic 9](./annexes/annex-2/annex-2-high-level-requirements.md#a239-topic-9---wallet-unit-attestation)
and [Topic 38](./annexes/annex-2/annex-2-high-level-requirements.md#a2338-topic-38---wallet-unit-revocation).
Similarly, when the Wallet Unit presents a PID or an attestation to a Relying
Party, the Relying Party can use the Wallet Provider trust anchors to verify the
authenticity of a Wallet Unit Attestation signed by the Wallet
Provider; see [Section 6.6.3.11](#66311-relying-party-instance-authenticates-the-wallet-unit-and-the-wallet-provider),
[Topic 9](./annexes/annex-2/annex-2-high-level-requirements.md#a239-topic-9---wallet-unit-attestation)
and [Topic 38](./annexes/annex-2/annex-2-high-level-requirements.md#a2338-topic-38---wallet-unit-revocation).

If a certain entity offers multiple Wallet Solutions, they will register as a
separate Wallet Provider for each of these Wallet Solutions. This implies that
such an entity will register different trust anchors for each of their Wallet
Solutions.

More details on the Wallet Provider notification process can be found in [Topic 31](./annexes/annex-2/annex-2-high-level-requirements.md#a2331-topic-31---pid-provider-wallet-provider-attestation-provider-and-access-certificate-authority-notification-and-publication).

#### 6.2.3 Wallet Provider suspension or withdrawal

Under specific conditions, a Trusted List Provider may decide to suspend or
withdraw a Wallet Provider. This implies that the Wallet Provider's status in
the respective Trusted List will be changed to Invalid. The conditions for this
will be specified by each Trusted List Provider. As a result of this status change,
PID Providers, Attestation Providers and Relying Parties will no longer trust
the trust anchors of the Wallet Provider and will therefore refuse to interact
with any Wallet Unit provided by that Wallet Provider.

When a Trusted List Provider withdraws a Wallet Provider, the Wallet Provider
revokes all valid WUAs for all Wallet Units, as described in [Section 6.6.3.12](#66312-relying-party-verifies-that-wua-is-not-revoked).

If an entity has registered multiple Wallet Providers, each offering a different
Wallet Solution, and one of these Wallet Providers is suspended or withdrawn,
only the applicable Wallet Solution will be impacted. It may happen that the
reason for suspension or withdrawal is applicable to all Wallet Solutions
offered, in which case all of the Wallet Providers registered by that entity
will be withdrawn or suspended separately.

### 6.3 Trust throughout a PID Provider or an Attestation Provider lifecycle

#### 6.3.1 PID Provider or Attestation Provider lifecycle

[Section 4.6.4](#464-pid-provider-or-attestation-provider) presented the
lifecycle of a PID Provider or Attestation Provider:

1. A PID Provider or an Attestation Provider is registered by a Trusted List Provider in its Member State. This is discussed in [Section 6.3.2](#632-pid-provider-or-attestation-provider-registration-and-notification).
2. Under specific conditions, a Trusted List Provider may decide to suspend or
cancel registration of a registered PID Provider or Attestation Provider. This is discussed in
[Section 6.3.3](#633-pid-provider-or-attestation-provider-suspension-or-withdrawal).

#### 6.3.2 PID Provider or Attestation Provider registration and notification

##### 6.3.2.1 Introduction

[Figure 11](#61-scope) depicts the PID Providers and Attestation Providers to the left of the
Wallet Unit. To the left and below of this, the figure also shows that each PID
Provider and Attestation Provider will register itself with a PID Provider
Registrar or an Attestation Provider Registrar in its Member State. The Member State notifies the PID Provider or Attestation Provider to the European Commission.

If the registration and notification processes are successful, at least the following happens:

- Data about the PID Provider or Attestation Provider is included in the registry of the relevant Registrar.
- The PID Provider or Attestation Provider receives an access certificate, and optionally one or more registration certificates.
- The trust anchors of the PID Provider or Attestation Provider are included in
a Trusted List.

These processes are discussed in the next subsections.

#### 6.3.2.2 Data about the PID Provider or Attestation Provider is included in the registry

When a PID Provider or Attestation Provider is registered, the Trusted List Provider registers a set of data about the PID Provider or Attestation Provider in its register. The Trusted List Provider makes the contents of the register available to the general public, both in machine-readable and human-readable format.

The data to be registered about a PID Provider or Attestation Provider includes the attestation type(s) that the PID Provider or Attestation Provider intends to issue to Wallet Units. This will enable Wallet Units and Relying to verify the entitlement of a given PID Provider or Attestation Provider to issue a specific attestation type. For example, a PuB-EAA Provider may be entitled to issue mDLs in a specific Member State, but may not be entitled to issue diplomas.

Note that the need to verify this entitlement depends on the legal status of the Provider:

- For PID Providers, their entitlement to issue PIDs follows already from the fact that their trust anchors are included in the PID Provider Trusted List; see [Section 6.3.2.4](#6324-pid-provider-or-attestation-provider-trust-anchors-are-included-in-a-trusted-list).
- For QEAA Providers, no checking of entitlement (apart from the fact that they are a QEAA) is necessary, since QEAA Providers are trusted by other actors in the EUDI Wallet
ecosystem to not fraudulently issue attestations that they are not legally
entitlement to issue. This trust is warranted since QEAA Providers operate
within a regulated framework and are regularly audited.
- For PuB-EAA Providers, checking of entitlement may be necessary, since the legal and regulatory framework within which they operate is different from that of QEAAs. To verify the entitlements of an PuB-EAA Provider it is interacting with, a Wallet Unit or Relying Party can query the registry of the Registrar mentioned in the access certificate of the PuB-EAA Provider.
- For non-qualified EAA Providers, checking of entitlement is necessary, since they are unregulated
and may not be completely trustworthy. Without additional measures, a fraudulent
EAA Provider may be able to issue types of QEAAs, PuB-EAAs or EAAs
that it is not legally entitled to issue. To prevent this, a Wallet Unit or Relying Party may query the applicable register, as described in the previous bullet. In addition, the applicable
Rulebook (see [Topic 12](./annexes/annex-2/annex-2-high-level-requirements.md#a2312-topic-12---attestation-rulebooks))
may define alternative mechanisms allowing a Wallet Unit or Relying Party to
verify an EAA Provider's entitlements.

##### 6.3.2.3 PID Provider or Attestation Provider receives an access certificate

When a PID Provider or Attestation Provider is registered by a Member State, a
PID Provider Access Certificate Authority (CA) or Attestation Provider Access
Certificate Authority issues one or more access certificates to the PID Provider
or to the Attestation Provider. A PID Provider or an Attestation Provider needs
such a certificate to authenticate itself towards a Wallet Unit when issuing a
PID or an attestation to it, as described in [Section 6.6.2.2](#6622-wallet-unit-authenticates-the-pid-provider-or-attestation-provider).


Subsequently, the Access Certificate Authority is included in a PID Provider
Access CA Trusted List or Attestation Provider Access CA Trusted List. This
Trusted List contains at least the trust anchor(s) of the CA. A Wallet Unit can
use these trust anchors to verify the authenticity of a PID Provider or an
Attestation Provider access certificate during the issuance of a PID or an
attestation. For more information, see [Topic 31](./annexes/annex-2/annex-2-high-level-requirements.md#a2331-topic-31---pid-provider-wallet-provider-attestation-provider-and-access-certificate-authority-notification-and-publication).

A PID Provider access certificate does not indicate that its subject is a PID Provider.
Similarly, an Attestation Provider access certificate does not indicate that its subject
is a QEAA Provider, a PuB-EAA Provider, or a non-qualified EAA Provider. Such information is included
in the registration certificates (if issued), or available in the Registrar's on-line service.
Furthermore, the access certificate of a PID Provider or Attestation Provider does not contain the
Provider's entitlements, e.g. to issue attestations of a specific type, for instance an
mDL or diploma ("intended use"). Such information is included in the Relying Party's registration certificate (if issued) and available in the Registrar's on-line service.

See [Section 6.6.3.3](https://github.com/eu-digital-identity-wallet/eudi-doc-architecture-and-reference-framework-private/blob/feature/1.10.0/docs/architecture-and-reference-framework-main.md#6633-wallet-unit-allows-user-to-verify-that-relying-party-does-not-request-more-attributes-than-it-registered) to learn more about the registration certificate content.

A Wallet Unit can use this information to verify that a Provider it is contacting to issue a specific type of attestation, is entitled to do so (verification of the type of the Provider and the "intended use").

If the registration certificate is not available, the Wallet Unit can always obtain this
information from the Registrar's on-line service (see
[Section 6.3.2.2](#6322-data-about-the-pid-provider-or-attestation-provider-is-included-in-the-registry)).

To manage both flows - with use of the registration certificate and without - the access certificates contains
+ information (a flag) to indicate whether the registration certificate was issued or not,
+ URL to the the Registrar's on-line service providing information on the Relying Parties registrations.
In case the intermediary is acting on behalf of an 'end' Relying Party, the information if the registration certificate is available is contained in the presentation request. (Note: this needs an extension of [ISO/IEC 18013-5] and [OpenID4VP]).



##### 6.3.2.4 PID Provider or Attestation Provider trust anchors are included in a Trusted List

For a PID Provider, a QEAA Provider, or a PuB-EAA Provider, successful
registration and notification also means that the Provider is notified to the
European Commission and that its trust anchors are included in a Trusted List.
Relying Parties can use these trust anchors to verify the authenticity of PIDs,
QEAAs, and PuB-EAAs they obtain from Wallet Units.

Non-qualified EAA Providers are not included in a Trusted List by a Member
State. However, if a Relying Party requests a non-qualified EAA from a Wallet
Instance, it must know how to obtain the domain-specific trust anchor it needs
to verify the signature over that EAA. To help with this, [Topic 12](./annexes/annex-2/annex-2-high-level-requirements.md#a2312-topic-12---attestation-rulebooks)
recommends that the applicable Rulebook specifies the mechanisms enabling this.
This mechanism may be similar to the one for QEAAs, namely that the relevant
non-qualified EAA Providers and their trust anchors are included in a trusted
list. However, other methods may be used as well, and even if such a trusted
list exists, it does not have to comply with the requirements in [Topic 31](./annexes/annex-2/annex-2-high-level-requirements.md#a2331-topic-31---pid-provider-wallet-provider-attestation-provider-and-access-certificate-authority-notification-and-publication).

More details on the PID Provider or Attestation Provider notification process,
as well as on the information registered and published in the PID Provider
Trusted List or Attestation Provider Trusted List, can be found in [Topic 31](./annexes/annex-2/annex-2-high-level-requirements.md#a2331-topic-31---pid-provider-wallet-provider-attestation-provider-and-access-certificate-authority-notification-and-publication).

#### 6.3.3 PID Provider's or Attestation Provider's registration suspension or cancellation

Under specific conditions, a Registrar may decide to suspend or
cancel registration of a PID Provider or Attestation Provider. The conditions for
this will be specified by each Registrar.

Suspension or cancellation implies that the PID Provider or Attestation Provider
access certificates are revoked. As a result, the PID Provider or Attestation
Provider will no longer be able to issue PIDs or attestations to Wallet Units.

For a PID Provider, QEAA Provider or PuB-EAA Provider, suspension or cancellation
also implies that its status in the respective Trusted List will be changed to
Invalid. As a result, Relying Parties will no longer trust PIDs or attestations
issued by the Provider with suspended or cancelled registration. For non-qualified EAA Providers,
the applicable Rulebook (see [Topic 12](./annexes/annex-2/annex-2-high-level-requirements.md#a2312-topic-12---attestation-rulebooks))
may define additional mechanisms ensuring that Relying Parties will no longer
trust the trust anchors of EAA Providers of which registration was suspended or cancelled.

When a Registrar suspends or cancels registration of a PID Provider or Attestation
Provider, the PID Provider or Attestation Provider revokes all of their PIDs or
attestations as described in [Section 6.6.3.7](#6637-relying-party-verifies-that-the-pid-or-attestation-is-not-revoked).

### 6.4 Trust throughout a Relying Party lifecycle

#### 6.4.1 Relying Party lifecycle

[Section 4.6.6](#466-relying-party) presented the lifecycle of a Relying Party:

1. A Relying Party is registered by a Registrar in the Member State where it
resides. Relying Party registration is discussed in [Section 6.4.2](#642-relying-party-registration).
2. Under specific conditions, a Registrar may decide to suspend or cancel registation of a
Relying Party. This is discussed in [Section 6.4.3](#643-relying-party-de-registration).

#### 6.4.2 Relying Party registration

[Figure 11](#61-scope) depicts the Relying Party Instance to the right of the Wallet Unit. A
Relying Party Instance is a combination of hardware and software used by a
Relying Party to interact with a Wallet Unit. A Relying Party can use multiple
Relying Party Instances, especially in case the interactions with the Wallet
Unit take place in proximity, for instance, a border control agency at an airport
employing multiple lines where arriving passengers can present their PID.

[Figure 11](#61-scope) also shows the Relying Party. Below that, it shows that each Relying
Party will register itself with a Relying Party Registrar in its Member State.
If the registration process is successful, the Registrar includes the Relying
Party in its public registry.

A Relying Party may register in the context of its several services, one per each intended use and requiring a specific attributes to be obtained from a Wallet Unit. In result, a single Relying Party may register multiple times and may be issued more than one registration certificate.

As a result of successful registration,

- the Relying Party Registration Certificate Authority (CA) may issue a registration certificate to the Relying Party. The purpose of the registration certificate is described in [Section 6.6.3.3](#6633-wallet-unit-allows-user-to-verify-that-relying-party-does-not-request-more-attributes-than-it-registered).
- a Relying Party Instance Access Certificate Authority (CA) associated with the
Registrar issues an access certificate to each Relying Party Instance of the
Relying Party. A Relying Party Instance needs such a certificate to authenticate
itself towards Wallet Units when requesting the presentation of attributes, as
described in [Section 6.6.3.2](#6632-wallet-unit-authenticates-the-relying-party-instance).

Subsequently, a Relying Party Registrar (or a Trusted List Provider acting on its behalf) in each Member State creates a Relying
Party Instance Access CA Trusted List containing the trust anchor(s) of all
associated Relying Party Instance Access CA(s). A Wallet Unit can use these
trust anchors to verify the authenticity of Relying Party Instance access
certificates. The Trusted List Provider signs and publishes the Relying Party
Instance Access CA Trusted List and makes the URL of the Trusted List available
to a common trust infrastructure maintained by the Commission, the so-called
List of Trusted Lists. Using the common infrastructure, any entity in the EUDI
Wallet ecosystem will be able to find all Trusted Lists in the ecosystem.

More details on the Relying Party registration process can be found in [Topic 27](./annexes/annex-2/annex-2-high-level-requirements.md#a2327-topic-27---registration-of-pid-providers-providers-of-qeaas-pub-eaas-and-non-qualified-eaas-and-relying-parties).

#### 6.4.3 Relying Party de-registration

Under specific conditions, a Registrar may decide to suspend or cancel registration of a registered
Relying Party. The conditions for this will be specified by each Registrar.

Suspension or cancellation involves revocation of all valid Relying Party Instance access
certificates by the relevant Access CA, such that the Relying Party is no longer
able to interact with Wallet Units.

### 6.5 Trust throughout a Wallet Unit lifecycle

#### 6.5.1 Wallet Unit lifecycle

[Section 4.6.3](#463-wallet-unit) above presented the lifecycle of a Wallet Unit:

1. The Wallet Instance that is part of the Wallet Unit is installed on a device
by a User. The required trust relationships for installation are discussed in
[Section 6.5.2](#652-wallet-instance-installation) below.
2. Next, the Wallet Unit is activated by the Wallet Provider and the User and
becomes operational. The goals and required trust relationships for activation
are discussed in [Section 6.5.3](#653-wallet-unit-activation).
3. Once in the **Operational** or **Valid** state, the Wallet Unit is managed by
the User and the Wallet Provider. This management includes at least revoking the
Wallet Unit when necessary. This is discussed in [Section
6.5.4](#654-wallet-unit-management). Management will also include regular
updates of the Wallet Instance application to ensure its continued security and
functionality. However, this is not further defined in this chapter.
4. The User may uninstall the Wallet Instance; see [Section 6.5.5](#655-wallet-instance-uninstallation).

#### 6.5.2 Wallet Instance installation

##### 6.5.2.1 Required trust relationships

The lifecycle of a Wallet Unit starts when a User decides to install a Wallet
Instance application on their device. This application in an instance of a
Wallet Solution, which is provided to the User by a Wallet Provider.

When downloading and installing the Wallet Instance, the following trust
relationships are established:

1. On behalf of the User, the OS of the User's device and the relevant app store
verify that the Wallet Instance (i.e., the application the User is installing)
is genuine and authentic and does not contain any malware or other threats.
2. The User verifies that they can obtain the PID(s) they need in an instance of
this Wallet Solution. If the relevant PID Provider does not support the Wallet
Solution, the User will not be able to use the Wallet Unit for obtaining those
PID(s).

The next two sections discuss these trust relationships.

##### 6.5.2.2 Wallet Solution authenticity is verified

To ensure that the User can trust the Wallet Solution, Wallet Providers
preferably make their certified Wallet Solutions available for installation via
the official app store of the relevant operating system (e.g., Android, iOS).
This allows the operating system of the device to perform relevant checks
regarding the authenticity of the app. It also allows Users to use the same
well-known channel for obtaining a Wallet Instance as they use for obtaining
other apps. Finally, it avoids a situation where a User must allow side-loading
of apps, which would increase the risk of unintentionally installing malicious
apps.

If a Wallet Provider makes its Wallet Solution available for installation
through other means than the official OS app store, it implements a mechanism
allowing the User to verify the authenticity of the Wallet Unit. Moreover, the
Wallet Provider provides clear instructions to the User on how to install the
Wallet Unit, including:

- instructions on how to verify the authenticity of the Wallet Instance to be
installed. This can be done, for example, by comparing the hash value of the
application downloaded by the User with a hash value published by the Wallet
Provider.
- instructions on bypassing of any operating system limitations on side-loading
of apps, if applicable, and ensuring that these limitations are restored after
the Wallet Instance has been installed.

Note: The [European Digital Identity Regulation] does not exclude the
possibility that a Wallet Instance may be installed on a non-mobile device, for
example a server. The requirements above also apply for the installation of a
Wallet Unit on a User device that is not a mobile device, and for which no
official operating system app store may exist.

##### 6.5.2.3 User validates that Wallet Solution is usable with relevant PID

A User installs a Wallet Unit because they want to obtain and use one or more
PIDs. However, PID Providers are not required to support all Wallet Solutions in
the EUDI Wallet ecosystem. 'Support' here means that the PID Provider is willing
to issue a PID to an instance of a given Wallet Solution on request of the User.
Instead, a PID Provider may choose to support only a single Wallet Solution or a
limited number of Wallet Solutions. Therefore, each PID Provider will publish a
list of Wallet Solutions that they support, such that a User that wants to
request a PID from that PID Provider knows which Wallet Unit they should
install. This list could be published, for example, on the PID Provider's
website.

Conversely, a Wallet Solution is not required to support all PID Providers,
where 'support' means that it is able to request the issuance of a PID from a
PID Provider. Each Wallet Provider will, prior to or during installation of a
Wallet Instance, let the User know which PID Providers are supported by this
Wallet Solution.

For QEAAs, PuB-EAAs, and non-qualified EAAs, the situation is different.
Providers of such attestations will support all Wallet Solutions and are not
allowed to discriminate between them when processing a request for the issuance
of an attestation. Conversely, a Wallet Solution supports all Attestation
Providers, and cannot discriminate between different Attestation Providers when
requesting the issuance of an attestation at the User's request.

#### 6.5.3 Wallet Unit activation

##### 6.5.3.1 Introduction

After installation of the Wallet Instance, the new Wallet Unit (which includes
that Wallet Instance) will contact the Wallet Provider to start the activation
process. For successful EUDI Wallet Instance activation, the following trust
relations are established:

1. The EUDI Wallet Instance authenticates the EUDI Wallet Provider, meaning that
the instance is sure that it is dealing with the genuine Wallet Provider who
provided it to the User.
2. The EUDI Wallet Provider authenticates the EUDI Wallet Instance. This means
that the EUDI Wallet Provider is sure that the instance is indeed a true
instance of their EUDI Wallet Solution, and not a fake app.

Both of these trust relationships are the responsibility of the Wallet Provider.
The ARF does not specify how these trust relationships can be satisfied.

During the activation process, at least the following steps happen:

1. The Wallet Provider requests data about the User's device from the Wallet
Instance.
2. The Wallet Provider requests the User to set up at least one User
authentication mechanism.
3. The Wallet Provider issues one or more Wallet Unit Attestations to the Wallet
Unit.
4. The Wallet Provider sets up a User account for the User.

These steps are described in the sections below.

##### 6.5.3.2 Wallet Provider requests data about the User's device from the Wallet Instance

The Wallet Instance connects to the Wallet Provider to be activated. Then, the
Wallet Provider requests data about the User's device from the Wallet Instance.
This data may include the communication technologies supported by the device and
the characteristics of the WSCD(s) available to the device for securely storing
cryptographic keys and data associated with the Wallet Unit itself and with the
attestations in that Wallet Unit.

Notes:

- As discussed in [Section 4.5](#45-wscd-architecture-types), a WSCD may be
integrated directly within the User's device. Examples of this include an e-SIM,
a UICC, an embedded Secure Element, or native secure hardware accessible via the
device's OS. If so, the Wallet Instance will discover the presence of such a
WSCD during activation and will communicate the characteristics of the WSCD to
the Wallet Provider. In some cases, the Wallet Provider will subsequently deploy
a WSCA to the WSCD to facilitate communication between the Wallet Instance and
the WSCD.
- Sometimes, the User's device does not contain a local WSCD, or the local WSCD does not
have the security posture necessary to enable the Wallet Unit to be an identity
means at LoA High, or the Wallet Provider does not want to use a local WSCD. In such a case, the Wallet Provider ensures the Wallet Unit
gets access to a remote HSM operated by the Wallet Provider.

##### 6.5.3.3 Wallet Provider requests User to set up at least one User authentication mechanism

User authentication will take place at several moments when a User uses their
Wallet Unit:

1. When the User opens the Wallet Instance. This is necessary to prevent anyone
except the User from accessing the Wallet Unit and inspecting the User's
attestations and attribute values. This data is personal and might be sensitive.
2. When (or before) the Wallet Unit must perform any cryptographic operation involving private or secret keys in the WSCD. This will happen at least when
    - The User instructs the Wallet Unit to request the issuance of a new PID or attestation, see [Section 6.6.2](#662-pid-or-attestation-issuance),
    - The Wallet Unit asks the User for approval to present some
attributes to a Relying Party, see [Section
6.6.3.5](#6635-wallet-unit-obtains-user-approval-for-presenting-selected-attributes),
    - The User deletes a PID or attestation in their Wallet Unit, see [Section 6.6](#666-pid-or-attestation-deletion)

User authentication for opening the Wallet Instance above can be done either by
the Wallet Instance or by a WSCD. In the latter case, it is the same mechanism
employed before the presentation of any attributes, see below. In the former
case, the mechanism used is preferably a general User authentication mechanism used by the User device, such as a lock screen.

User authentication before presenting attributes is always done by the WSCA. It
means that the User gives the WSCA permission to use the cryptographic keys
belonging to the Wallet Unit and to the PID or attestation for performing the
cryptographic operations necessary for presenting that PID or attestation. For
that reason, it is always the WSCD that performs User authentication in this
case.

During activation of the Wallet Unit, depending on the choice made by the Wallet
Provider to combine the two User authentication mechanisms or not, the Wallet
Provider will ask the User to set up one or two authentication mechanisms.

Note that, as discussed in the first bullet in [Section 6.6.3.9](#6639-relying-party-instance-verifies-or-trusts-user-binding),
the User authentication mechanisms implemented in the WSCD may also play a role
in ensuring User binding. User binding allows a Relying Party to trust that the
person presenting a PID or attestation is in fact the subject of that PID or
attestation.

##### 6.5.3.4 Wallet Provider issues one or more Wallet Unit Attestations to the Wallet Unit

During the activation of a Wallet Unit, the Wallet Provider issues one or more
Wallet Unit Attestations to the Wallet Unit. The Wallet Unit Attestation (WUA)
is described in [Topic 9](./annexes/annex-2/annex-2-high-level-requirements.md#a239-topic-9---wallet-unit-attestation). More information on the WUA can also be found in the [Discussion Paper for topic C](./discussion-topics/c-wallet-unit-attestation.md).

A WUA has three main purposes:

- It describes the capabilities and properties of the Wallet Unit, including the
Wallet Instance, the User device, and the WSCD(s). This allows a PID Provider or
an Attestation Provider to verify that the Wallet Unit complies with the
Provider's requirements and therefore is fit to receive a PID or an attestation
from the Provider. To ensure User privacy, the Wallet Unit presents its
capabilities and properties only to PID Providers and Attestation Providers, but
not to Relying Parties. This is because PID Providers and Attestation Providers
have a valid business reason to know these properties, whereas Relying Parties
do not. The [Discussion Paper for topic C](./discussion-topics/c-wallet-unit-attestation.md)
refers to these as 'Use case 1' (Relying Parties) and 'Use case 2'
(PID Providers and Attestation Providers).
- Moreover, the WUA contains a WUA public key. During the issuance of a PID or
an attestation (see [Section 6.6.2.3](#6623-pid-provider-or-attestation-provider-validates-the-wallet-unit)),
a PID Provider or Attestation Provider can use this public key to verify that
the Wallet Unit is in possession of the corresponding private key. Moreover, at
that time, the Wallet Unit will send another public key to the PID Provider or
Attestation Provider. The Provider will include this public key in the issued
PID or attestation. The PID Provider or Attestation Provider can optionally
verify that the private key belonging to this public key is protected by the
same WSCD as the private key belonging to the WUA public key, if this is
supported by the WSCD. Thus, the PID Provider or Attestation Provider can trust
this new public key. Note that support for such a proof is not mandatory in this
version of the ARF, since no mechanism has been specified yet, let alone that
this is widely supported by available WSCDs.
- Lastly, if a WUA is valid for 24 hours or longer, it contains information
allowing a PID Provider, an Attestation Provider, or a Relying Party to verify
that the Wallet Provider did not revoke the Wallet Unit Attestation, and hence
the Wallet Unit itself. The WUA and the revocation mechanisms for Wallet Units
are described in [Topic 38](./annexes/annex-2/annex-2-high-level-requirements.md#a2338-topic-38---wallet-unit-revocation).

The detailed format of the WUA will be specified in a technical specification.
There may be differences in the format for the WUAs suitable for Use case 1 and
those for Use case 2. Specifically, WUAs intended for Relying Parties will
probably comply with either [ISO/IEC 18013-5] or [SD-JWT VC], to avoid
additional requirements on Relying Parties and Wallet Units. For WUAs intended
for PID Providers or Attestation Providers, there is no such limitation, and the
format of these can be simpler.

Regarding the WUA validity period, an important requirement in [CIR 2024/2977],
Article 5, is that a PID Provider must revoke a PID when the Wallet Unit to
which that PID was issued is revoked. This implies that a PID Provider, during
the entire validity period of the PID, must be able to regularly check whether
the Wallet Provider revoked the WUA the PID Provider obtained from the Wallet
Unit during PID issuance. To be able to do so, the validity period of WUAs
intended for PID Providers will be long, perhaps as long as the expected
lifetime of the Wallet Unit. Moreover, the validity period of a PID cannot
exceed the end of validity of the WUA received by the PID Provider during
issuance.

The responsibilities of the Wallet Provider regarding issuance of a WUA are
similar to those of a PID Provider or Attestation Provider regarding the
issuance of a PID or an attestation. This means that after the initial issuance
of a WUA during activation, the Wallet Provider will manage the WUA and will
issue new WUAs to the Wallet Unit as needed, during the lifetime of the Wallet
Unit.  In particular, the Wallet Provider will ensure that the risk of malicious
Relying Parties linking multiple presentations of the same WUA, with the goal of
tracking the User, is minimised. For example, the Wallet Provider may set up the
Wallet Unit in such a way that each Wallet Unit Attestation is presented to at
most one PID Provider, Attestation Provider, or Relying Party. Such a WUA is
called a 'once-only' attestation, see [Section 7.4.3.5](#7435-risks-and-mitigation-measures-related-to-user-privacy).

##### 6.5.3.5 Wallet Provider sets up a User account for User

The User needs a User account at the Wallet Provider to ensure that they can
request the revocation of their Wallet Unit in case of theft or loss. The Wallet
Provider associates the Wallet Unit with the User account. The Wallet Provider
registers one or more backend-based User authentication methods that the Wallet
Provider will use to authenticate the User. Note that:

- The Wallet Provider does not need to know any real-world attributes of the
User. The User can use a pseudonym to register, for example an e-mail address.
If the Wallet Provider wants to request additional User attributes, for instance
to be able to provide additional services, they are free to do so if the User
consents.
- In any case, User details registered by the Wallet Provider will not be
included in the WUA. They are strictly for use by the Wallet Provider only.

#### 6.5.4 Wallet Unit management

Starting from Wallet Unit activation and until the Wallet Instance is
uninstalled by the User, a Wallet Unit is managed by the User and the Wallet
Provider. The Wallet Provider is responsible at least to:

- perform installation of a new version of the Wallet Solution as necessary.
- update the WUAs as necessary; see [Topic 9](./annexes/annex-2/annex-2-high-level-requirements.md#a239-topic-9---wallet-unit-attestation).
- revoke the Wallet Unit in case its security is compromised; see [Topic 38](./annexes/annex-2/annex-2-high-level-requirements.md#a2338-topic-38---wallet-unit-revocation).

The User will be able to request the Wallet Provider to revoke the Wallet Unit
at least in case of loss or theft of the User's device. See [Topic 38](./annexes/annex-2/annex-2-high-level-requirements.md#a2338-topic-38---wallet-unit-revocation).

If the Wallet Unit contains a PID, the PID Provider may request the Wallet
Provider to revoke the Wallet Unit in case the natural person using the Wallet
Unit has died or the legal person using the Wallet Unit has ceased operations.
See [Topic 38](./annexes/annex-2/annex-2-high-level-requirements.md#a2338-topic-38---wallet-unit-revocation).

Lastly, the Wallet Unit supports procedures for backing up and restoring the
attestations it contains, or for migrating these attestations to a different
Wallet Solution. See [Topic 33](./annexes/annex-2/annex-2-high-level-requirements.md#a2333-topic-33---wallet-unit-backup-and-restore)
and [Topic 34](./annexes/annex-2/annex-2-high-level-requirements.md#a2334-topic-34---migrate-to-a-different-wallet-solution)
respectively.

To allow Wallet Unit management, the following trust relations are established:

1. When contacting the Wallet Provider, for instance to request the revocation
of the Wallet Unit, the User authenticates the Wallet Provider. This means the
User is sure that they are visiting the website or the User portal of the
genuine Wallet Provider who is responsible for the User's Wallet Unit, and not a
spoofed website or portal. This risk can be partly mitigated by using standard
mechanisms such as TLS server authentication. However, in addition the User will
need to be vigilant as well, just as with any website on the internet.
2. When contacted by a User, the Wallet Provider authenticates the User. This
means that the Wallet Provider is sure that the User is indeed the User that was
associated with the Wallet Unit during activation. For this, the Wallet Provider
uses the authentication methods established in the User's account during
activation, see [Section 6.5.3](#653-wallet-unit-activation).
3. When the Wallet Unit and the Wallet Provider set up a communication channel,
the Wallet Unit authenticates the Wallet Provider, meaning that the Wallet Unit
is sure that it is dealing with the genuine Wallet Provider. Similarly, the
Wallet Provider authenticates the Wallet Unit. This means that the Wallet
Provider is sure that the EUDI Wallet Instance is indeed a true instance of
their Wallet Solution, and not a fake app. This will be ensured by the Wallet
Provider. The ARF does not specify how these trust relationships can be
satisfied.
4. When contacted by a PID Provider to request Wallet Unit revocation, the
Wallet Provider authenticates the PID Provider. [Section 6.6.2.2](#6622-wallet-unit-authenticates-the-pid-provider-or-attestation-provider)
below describes how a Wallet Unit can do this during PID issuance; a Wallet
Provider can use the same mechanism.
5. To identify the Wallet Unit that is to be revoked, the PID Provider uses a
Wallet Unit identifier provided by the Wallet Unit in the WUA during PID
issuance; see [Topic 9](./annexes/annex-2/annex-2-high-level-requirements.md#a239-topic-9---wallet-unit-attestation).

#### 6.5.5 Wallet Instance uninstallation

No trust relationships are required for Wallet Instance uninstallation; anybody
able to access the device of the User will be able to do this.

If the User uninstalls the Wallet Instance, the Wallet Instance ensures that the
associated WSCA(s) delete all sensitive data and cryptographic keys related to
the Wallet Unit and to all PIDs and attestations on the Wallet Unit.

If it supports the Digital Credentials API, see [Section 4.4.3](#443-remote-presentation-flows),
the Wallet Instance also discloses the fact that it is uninstalled to
the Digital Credentials API framework.

### 6.6 Trust throughout a PID or an attestation lifecycle

#### 6.6.1 PID or attestation lifecycle

[Section 4.6.5](#465-pid-or-attestation) above presented the lifecycle of a PID
or attestation within a Wallet Unit:

1. Using their Wallet Unit, the User requests the issuance of a PID or an
attestation from a PID Provider or an Attestation Provider. The required trust
relationships for issuance are discussed in [Section 6.6.2](#662-pid-or-attestation-issuance)
below.
2. Once the PID or attestation is issued into the Wallet Unit, the User can
present attributes from it to a Relying Party Instance, according to the User's
decision and depending on successful authentication of the Relying Party. The
required trust relationships for presenting PIDs and attestations, including
User approval and Relying Party authentication, are discussed in [Section 6.6.3](#663-pid-or-attestation-presentation-to-relying-party).
3. Instead of presenting attributes to a Relying Party, a User can also present
them to another User, meaning that their Wallet Unit is interacting with another
Wallet Unit. This is briefly discussed in [Section 6.6.4](#664-pid-or-attestation-presentation-to-another-wallet-unit).
4. The PID Provider or the Attestation Provider remains responsible for managing
the PID or attestation over its lifetime. Management may include re-issuing the
PID or attestation with the same or with different attribute values. The
Provider can also revoke the PID or the attestation, possibly based on a request
of the User. The management of PIDs and attestations is discussed in [Section 6.6.5](#665-pid-or-attestation-management).
5. Finally, [Section 6.6.6](#666-pid-or-attestation-deletion) discusses what
happens if a User decides to delete a PID or an attestation from their Wallet
Unit.

#### 6.6.2 PID or attestation issuance

##### 6.6.2.1 Required trust relationships

The lifecycle of a PID or an attestation starts when a User, using their Wallet
Unit, requests a PID Provider or an Attestation Provider to issue the PID or an
attestation to their Wallet Unit. The following trust relationships are
established during issuance:

1. The Wallet Unit authenticates the PID Provider or Attestation Provider using
the access certificate referred to in [Section 6.3](#63-trust-throughout-a-pid-provider-or-an-attestation-provider-lifecycle).
This ensures that the User can trust that the PID or attestation they are about
to receive, is issued by an authenticated PID Provider or Attestation Provider
respectively. See [Section 6.6.2.2](#6622-wallet-unit-authenticates-the-pid-provider-or-attestation-provider)
below describing how this will be done.
2. The PID Provider or Attestation Provider authenticates the User, meaning that
the Provider is sure about the identity of the User. This is necessary to enable
determination of the values of the attributes that the Provider will attest to.
For instance, a PID Provider needs to authenticate the User to ensure it
provides a PID containing the correct family name and date of birth. The method
by which the PID Provider or Attestation Provider performs User identification
and authentication is out of scope of the ARF, as these processes are specific
to each PID Provider or Attestation Provider. However, they will satisfy the
requirements for the Level of Assurance required for the PID or attestation
issued.
3. The PID Provider or Attestation Provider authenticates and validates the
Wallet Unit, see [Section 6.6.2.3](#6623-pid-provider-or-attestation-provider-validates-the-wallet-unit)
below.
4. The PID Provider or Attestation Provider verifies that the Wallet Provider
did not revoke the Wallet Unit. This is described in [Section 6.6.2.4](#6624-pid-provider-or-attestation-provider-verifies-that-wua-is-not-revoked).
5. After the PID or attestation is issued to the Wallet Unit, the Wallet Unit
verifies the authenticity of the PID or attestation; see [Section 6.6.2.5](#6625-wallet-unit-verifies-pid-or-attestation).
6. The User will activate a PID before they can use it; see [Section 6.6.2.6](#6626-user-activates-the-pid).
7. If an attestation contains an embedded disclosure policy, the Wallet Unit retrieves the policy and stores it locally, so that it can apply the policy in case a Relying Party requests attributes from the attestation. See [Section 6.6.2.7](#6627-provisioning-embedded-disclosure-policies).

More detailed requirements for the issuance process of PIDs and attestations,
for instance regarding the issuance protocol, are included in [Topic 10/23](./annexes/annex-2/annex-2-high-level-requirements.md#a2310-topic-10---issuing-a-pid-or-attestation-to-a-wallet-unit).

##### 6.6.2.2 Wallet Unit authenticates the PID Provider or Attestation Provider

As shown in [Figure 11](#61-scope), a Wallet Unit downloads the PID Provider Access CA
Trusted List(s) it needs from the relevant Trusted List Provider(s), possibly
after having located them via the Commission common trust infrastructure. It
also downloads all Attestation Provider Access CA Trusted List(s). See [Section 6.3.2](#632-pid-provider-or-attestation-provider-registration-and-notification)
for more information on these Trusted Lists.

Note: It is not mandatory for each Wallet Unit to possess all PID Provider CA
Trusted Lists, if there are multiple. Wallet Providers will choose which Trusted
Lists they need to subscribe to, for example depending on the Member State(s)
they are operating in. It is however mandatory to possess all Attestation
Provider Access CA Trusted Lists, as Wallet Units must support all QEAA
Providers and PuB-EAA Providers in the EUDI Wallet ecosystem.

To start the process of requesting a PID or an attestation, the User directs the
Wallet Unit to contact the PID Provider or Attestation Provider. The User may
for example use the Wallet Unit to scan a QR code or tap an NFC tag to do so.
Note that no centralised service discovery mechanism for PID or attestation
issuance is foreseen.


Before requesting the issuance of a PID or an attestation, the Wallet Unit
authenticates the PID Provider or the Attestation Provider. To do so, the Wallet
Unit verifies the access certificate presented to it by the PID Provider or
Attestation Provider in its Issuer metadata according to [OpenID4VCI].
To verify the role and the entitlements of the requesting entity (whether it is an
PID Provider or an Attestation Provider and what type of attestation provider), the Wallet unit checks the registration information contained in the registration certificate
(if available) or the Registrar's on-line service.


The Wallet Unit also verifies that the access certificate and registration certificate (if provided)
are authentic, that they are valid at the time of validation, and that the issuers of the certificates
are in the PID Provider or Attestation Provider Access CA Trusted List.



##### 6.6.2.3 PID Provider or Attestation Provider validates the Wallet Unit

###### 6.6.2.3.1 Verifies the authenticity of the Wallet Unit

As shown in [Figure 11](#61-scope), a PID Provider or an Attestation Provider downloads the
Wallet Provider Trusted List(s) it needs from the relevant Trusted List
Provider(s), possibly after having located them via the Commission common trust
infrastructure.

Note that for PID Providers it is not mandatory to possess all Wallet Provider
Trusted Lists, if there are multiple. This is because it is not mandatory for a
PID Provider to accept all certified Wallet Solutions in the EUDI Wallet
ecosystem. Each PID Provider will choose which Trusted Lists they need to
subscribe to. This is different for Attestation Providers: they must accept all
Wallet Solutions and hence must possess all Wallet Provider Trusted Lists.

[Section 6.5.3](#653-wallet-unit-activation) above described that a Wallet
Provider, during activation of a Wallet Unit, issues one or more Wallet Unit Attestations
(WUA) to the Wallet Unit. When the Wallet Unit sends a request for a PID or an
attestation to a PID Provider or to an Attestation Provider, it includes the WUA
in the request. The PID Provider or Attestation Provider verifies the signature
over the WUA, using the Wallet Provider trust anchor obtained from the Trusted
List. Next, the PID Provider or Attestation Provider verifies that the Wallet
Unit possesses the private key belonging to the public key in the WUA. This
proves that the Wallet Unit is authentic and is provided by a trusted Wallet
Provider. For more details see [Topic 9](./annexes/annex-2/annex-2-high-level-requirements.md#a239-topic-9---wallet-unit-attestation).

###### 6.6.2.3.2 Optionally, verifies that the User's Wallet Unit supports all required features

The WUA describes relevant features of the Wallet Unit, as well as the device it
is installed on. Depending on their needs, PID Providers or Attestation
Providers optionally verify that the User's Wallet Instance supports all
features they require. For example, for some PID Providers or Attestation
Providers it may be relevant to know whether the Wallet Unit supports presenting
the attestation in proximity flows using NFC.

###### 6.6.2.3.3 Optionally, validates the properties of the WSCD

The WUA describes the certifications and the other relevant properties of the
WSCD, i.e., the secure cryptographic device included in the Wallet Unit to store
and manage cryptographic keys. The security level of the WSCD is a key
determinant for the overall Level of Assurance (LoA) of the Wallet Unit. For
obtaining a PID, the Wallet Unit and the WSCD will comply with the requirements
for LoA High. For other attestations, LoA High or Substantial will be needed,
depending on the requirements of the Attestation Provider.

###### 6.6.2.3.4 Verifies that the PID key or the attestation key is protected by the WSCD

Knowing the properties of the WSCD is not very useful if the PID Provider or
Attestation Provider cannot be sure that the private key for their new PID or
attestation is indeed protected by that WSCD. [Topic 9](./annexes/annex-2/annex-2-high-level-requirements.md#a239-topic-9---wallet-unit-attestation)
describes how the PID Provider or Attestation Provider may be able obtain a proof that the WSCD described in the WUA protects both the WUA private key and the private key
of the new PID or attestation.

##### 6.6.2.4 PID Provider or Attestation Provider verifies that WUA is not revoked

[Section 6.5.3](#653-wallet-unit-activation) above described that a Wallet
Provider, during activation of a Wallet Unit, issues one or more Wallet Unit Attestation
(WUA) to the Wallet Unit. If a WUA is valid for longer than 24 hours, it
contains revocation information. During the lifetime of the Wallet Unit, the
Wallet Provider regularly verifies that the security of the Wallet Unit is not
breached or compromised. If the Wallet Unit is no longer secure, the Wallet
Provider revokes any of its WUAs that has a remaining validity period of 24
hours or longer. If the Wallet Provider uses WUAs with a validity period of less
than 24 hours, it stops issuing new WUAs to a Wallet Unit that is no longer
secure. The WUA thus allows PID Providers, Attestation Providers and Relying
Parties to verify that the Wallet Unit is not revoked.

[Topic 38](./annexes/annex-2/annex-2-high-level-requirements.md#a2338-topic-38---wallet-unit-revocation)
describes Wallet Unit revocation in more detail.

Once it has done all verifications, the PID Provider or Attestation Provider
will issue the PID or attestation to the Wallet Unit.

##### 6.6.2.5 Wallet Unit verifies PID or attestation

After the Wallet Unit receives the PID or attestation, it will

- verify that the PID or attestation it received matches the request.
- verify the signature of the PID or attestation, using the appropriate trust
anchor, in the same way as described for a Relying Party Instance in [Section 6.6.3.6](#6636-relying-party-instance-verifies-the-authenticity-of-the-pid-or-attestation).
- show the contents (i.e., attribute values) of the new PID or attestation to
the User and request the User's approval for storing the new PID or attestation.
When requesting approval, the Wallet Unit shows the contents of the PID or
attestation to the User. The Wallet Unit also informs the User about the
identity of the PID Provider or Attestation Provider, using the subject
information from the PID Provider or Attestation Provider access certificate.

If one these verifications fail, the Wallet Unit will delete the PID or
attestation, and will inform the User that issuance was not successful. Otherwise, the Wallet Unit will store the PID or attestation and will inform the User that issuance was successful. If it supports the Digital Credentials API, see [Section 4.4.3](#443-remote-presentation-flows), the Wallet Unit will also disclose the fact that it contains the new PID or attestation to the Digital Credentials API framework.

##### 6.6.2.6 User activates the PID

As documented in [Topic 9](./annexes/annex-2/annex-2-high-level-requirements.md#a239-topic-9---wallet-unit-attestation),
to achieve Level of Assurance (LoA) High,
[Commission Implementing Regulation (EU) 2015/1502](https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=CELEX:32015R1502)
requires that an activation process will be implemented to verify that a PID was
in fact delivered into the possession of the person to whom it belongs.

However, in fact no additional step is needed in the issuance process to ensure
this. This is because the User always starts the issuance process from the
Wallet Unit into which they want the PID Provider to issue the new PID. The PID
Provider sets up a secure communication channel towards this Wallet Unit, using
the flow specified in [OpenID4VCI]. Additionally, the User uses an eID means on
LoA High to authenticate towards the PID Provider. This process ensures that the
new PID can only end up on the device used by the subject of the PID.

Note that activation is required only for PIDs, since the [European
Digital Identity Regulation] only requires PIDs to be issued at LoA High.

##### 6.6.2.7 Provisioning embedded disclosure policies

##### 6.6.2.7.1 Introduction

During attestation issuance, an Attestation Provider can optionally create an embedded
disclosure policy for the attestation, and provide it to Wallet Units during attestation issuance. Such an embedded disclosure policy contains rules determining which (types of) Relying Parties are allowed by the Attestation Provider to receive the attestation.

Note that the [European Digital Identity Regulation] does not contain a requirement
for PIDs to be able to contain an embedded disclosure policy, but only for QEAAs
and PuB-EAAs.

For more information regarding embedded disclosure policies, please refer to the [Discussion Paper for Topic D](./discussion-topics/d-embedded-disclosure-policies.md).

###### 6.6.2.7.2 Types of embedded disclosure policies

Annex III of [CIR 2024/2979] defines the following common embedded
disclosure policies that must be supported:

>1. 'No policy' indicating that no policy applies to the electronic attestations
of attributes.
>2. 'Authorised relying parties only policy', indicating that wallet users may only
disclose electronic attestations of attributes to authenticated relying parties
which are explicitly listed in the disclosure policies.
>3. 'Specific root of trust' indicating that wallet users should only disclose
the specific electronic attestation of attributes to authenticated wallet-relying
parties with wallet-relying party access certificates derived from a specific
root (or list of specific roots) or intermediate certificate(s).

The first of these policies is the default and will be applied if the Attestation Provider does not provide an embedded disclosure policy for an attestation.

For expressing conditions on Relying Parties, an embedded disclosure policy will refer to information included in the access certificate provided to the Wallet Unit by the Relying Party. Note that access certificates are signed and hence the information they contain is authenticated.

Wallet Units, as well as the mechanisms used for defining and evaluating policies, will provide support for at least policies 2. and 3. above. The Commission will ensure a technical specification is created that specifies how these policies will be formatted.

###### 6.6.2.7.3 Distributing embedded disclosure policies

An Attestation Provider will provide an embedded disclosure policy in the Issuer metadata specified in [OpenID4VCI]. This does not require modifications to the attestation format. The Commission will ensure that a technical specification for issuing embedded disclosure policies is created.

Moreover, policies will be integrated directly into the metadata, rather than being "linked" using a URL and stored by the Attestation Provider. The approach does not require the Wallet Unit to communicate with the Attestation Provider in order to be able to obtain and evaluate a policy for an attestation requested by a Relying Party. Instead, during issuance of an attestation, the Wallet Unit retrieves any relevant disclosure policy from the metadata and stores it locally. A consequence of this approach is that an Attestation Provider will revoke an attestation if a relevant embedded disclosure policy must be updated.

##### 6.6.2.8 Batch issuance

Batch issuance means that instead of issuing a single PID or attestation to a
Wallet Unit, a PID Provider or Attestation Provider issues a batch of them. All
PIDs or attestations in a batch have the same attestation type, attribute values
and technical validity period. Apart from that, all of the descriptions in this section
6.6.2 apply regardless of the number of attestations issued (single or batch).

Batch issuance is discussed in more detail in the [Discussion Paper for Topic B](././discussion-topics/b-re-issuance-and-batch-issuance-of-pids-and-attestations.md).

#### 6.6.3 PID or attestation presentation to Relying Party

##### 6.6.3.1 Required trust relationships

A Relying Party can request a User to present some attributes from a PID or from
an attestation in their Wallet Unit. [Figure 11](#61-scope) shows that a Relying Party uses a
Relying Party Instance to interact with the Wallet Unit of the User. The
relationship between the Relying Party and their Relying Party Instance is
similar to the relationship between the User and their Wallet Unit.

When processing the request, the following trust relationships are established:

1. The Wallet Unit authenticates the Relying Party Instance, ensuring the User
about the Relying Party's identity. [Section
6.6.3.2](#6632-wallet-unit-authenticates-the-relying-party-instance) explains
how this will be done.
2. The Wallet Unit verifies that the Relying Party does not request more
attributes than it has registered for, and informs the User about the outcome of
this verification. See [Section 6.6.3.3](#6633-wallet-unit-allows-user-to-verify-that-relying-party-does-not-request-more-attributes-than-it-registered)
for more information.
3. The Attestation Provider, during issuance, may optionally embedded a
disclosure policy in the attestation. If such a policy is present for the
requested attestation, the Wallet Unit evaluates the disclosure policy and
informs the User about the outcome of this evaluation. See [Section 6.6.3.4](#6634-wallet-unit-evaluates-embedded-disclosure-policy-if-present).
4. The User approves or rejects the presentation of the requested attributes.
User approval and selective disclosure are described in [Section 6.6.3.5](#6635-wallet-unit-obtains-user-approval-for-presenting-selected-attributes).
Subsequently, after the Wallet Unit presents the selected attributes from the
PID or attestation to the Relying Party Instance by sending a response to the
request, the Relying Party validates the response. The following trust
relationships are established:
5. The Relying Party Instance verifies the signature of the PID or attestation.
This ensures that the Relying Party can trust that the PID or attestation it
receives is issued by an authentic Provider and has not been changed. This is
described in [Section 6.6.3.6](#6636-relying-party-instance-verifies-the-authenticity-of-the-pid-or-attestation).
6. The Relying Party verifies that the PID Provider or Attestation Provider did
not revoke the PID or attestation. This is described in [Section 6.6.3.7](#6637-relying-party-verifies-that-the-pid-or-attestation-is-not-revoked).
7. The Relying Party verifies that the PID Provider or Attestation Provider
issued this PID or attestation to the same Wallet Unit that presented it to the
Relying Party. In other words, it checks that the PID or attestation was not
copied or replayed. This is generally called device binding, and it is discussed
in [Section 6.6.3.8](#6638-relying-party-instance-verifies-device-binding)
8. In some use cases, the Relying Party verifies that the person presenting the
PID or attestation is the subject of the PID or attestation. This is called User
binding. In other use cases, the Relying Party trusts that Wallet Unit and the
WSCD have done this. User binding is discussed in [Section 6.6.3.9](#6639-relying-party-instance-verifies-or-trusts-user-binding).
9. The Relying Party can request attributes from two or more attestations in the
same interaction. This is called a **combined presentation of attributes**. If
so, the Relying Party verifies that these attestations belong to the same User.
This is discussed in [Section 6.6.3.10](#66310-relying-party-instance-verifies-combined-presentation-of-attributes).

Either before or after validating the PID or attestation per steps 5 - 9,

1. The Relying Party Instance authenticates the Wallet Unit and the Wallet
Provider; see [Section 6.6.3.11](#66311-relying-party-instance-authenticates-the-wallet-unit-and-the-wallet-provider).
2. The Relying Party Instance verifies that the Wallet Provider did not revoke
the Wallet Unit, see [Section 6.6.3.12](#66312-relying-party-verifies-that-wua-is-not-revoked)

Finally, after the interaction with the Relying Party Instance is over,

1. The Wallet Unit enables the User to report unlawful or suspicious requests
for personal data by a Relying Party, based on information logged by the Wallet
Unit. Similarly, the Wallet Unit enables the User to request a Relying Party to
delete personal data (i.e., User attributes) obtained from the Wallet Unit. This
is discussed in [Section 6.6.3.13](#66313-wallet-unit-enables-the-user-to-report-suspicious-requests-by-a-relying-party-and-to-request-a-relying-party-to-erase-personal-data).

##### 6.6.3.2 Wallet Unit authenticates the Relying Party Instance

Relying Party authentication is a process whereby a Relying Party proves its
identity to a Wallet Unit, in the context of an interaction in which the Relying
Party requests the Wallet Unit to present some attributes. Relying Party
authentication is discussed in [Topic 6](./annexes/annex-2/annex-2-high-level-requirements.md#a236-topic-6---relying-party-authentication-and-user-approval).

Relying Party authentication is included in the protocol used by a Wallet Unit
and a Relying Party Instance to communicate. As documented in [Topic 12](./annexes/annex-2/annex-2-high-level-requirements.md#a2312-topic-12---attestation-rulebooks),
at least two different protocols can be used within the EUDI Wallet ecosystem,
namely the ones specified in [ISO/IEC 18013-5] and [OpenID4VP]. Both protocols
include functionality allowing the Wallet Unit to authenticate the Relying Party
Instance. Although these protocols differ in the details, on a high level, they
both implement Relying Party authentication as shown in Figure 12 below.

![Figure 12](media/Figure_12_Relying_Party_Authentication.png)

Figure 12 High-level overview of Relying Party authentication process

The figure shows the following:

First, there are two preconditions that need to be fulfilled before the Relying
Party authentication process can begin. Note that these actions are not carried
out for every presentation, but only once (excluding possible updates):

A) The Relying Party registered itself as described in
[Section 6.4.2](#642-relying-party-registration)
and obtained a Relying Party Instance access certificate.

B) The Wallet Unit obtained the trust anchor of the Relying Party Instance
Access Certificate Authority.

Subsequently, during each presentation of attributes:

1. The Relying Party Instance prepares a request for some attributes to the
Wallet Unit and includes its Relying Party Instance access certificate in the
request, plus all intermediate certificates up to (but excluding) the trust anchor.
2. The Relying Party Instance signs some data in the attribute request using its
private key.
3. The Relying Party Instance sends the request to the Wallet Unit.
4. The Wallet Unit checks the authenticity of the request by verifying the
signature over the request using the public key in the Relying Party Instance
access certificate.
5. The Wallet Unit checks the authenticity of the Relying Party by validating
the Relying Party Instance access certificate and all intermediate certificates
included in the request. For validating the last intermediate certificate, the
Wallet Unit uses the trust anchor it obtained from the Trusted List.
6. The Wallet Unit validates that none of the certificates in the trust chain
have been revoked. This includes the Relying Party Instance access certificate
as well as all other certificates in the trust chain, including the trust anchor
itself if applicable.
7. The Wallet Unit continues by requesting the User for approval.
8. The User approves the attributes that will be presented.
9. The Wallet Unit sends a response containing only the approved attributes to
the Relying Party Instance.

##### 6.6.3.3 Wallet Unit allows User to verify that Relying Party does not request more attributes than it registered

During registration, the Relying Party registered which attributes it intends to
request from Wallet Units.
If the registration certificate had been issued for this Relying Party,
+ the Registrar listed these attributes in this certificate and sent it to the Relying Party,
+ the Relying Party may distribute it to all of its Relying Party Instances,
+ the Relying Party Instance may send this registration certificate to the Wallet Unit in each presentation request.


During a transaction, the Wallet Unit offers to the User an option to perform verification of the
Relying Party registration information. If the User choses to do so, the Wallet Unit
displays the contents of the registration certificate to the User when asking
the User for approval, see
[Section 6.6.3.5](#6635-wallet-unit-obtains-user-approval-for-presenting-selected-attributes),
at least in case one or more of the requested attributes is not included in the
list of attributes in the registration certificate.

The format of the registration certificate, as well as the way in which the
Wallet Unit can verify that the registration certificate belongs to the
authenticated Relying Party, will be specified in a technical specification. For
more information, see [Topic 44](./annexes/annex-2/annex-2-high-level-requirements.md#a2344-topic-44---relying-party-registration-certificates).

In case the registration certificate was not issued or not provided in the presentation
request, the Wallet Unit offers to the User an alternative option to perform verification of the
Relying Party information, through an on-line check instead.

If the User choses to perform such a check, the Wallet Unit retrieves a URL of the Registrar's on-line service from:
+ the Relying Party Access Certificate, or
+ the information contained in the presentation request - in case of requestor being an intermediary (note: this needs an extension of [ISO/IEC 18013-5] and [OpenID4VP]).

Next, the Wallet Unit makes a verification request via this URL, using the unique ID of the Relying Party (retrieved from the Relaying Party access certificate or from the presentation request in case the requestor is an intermediary).
The Wallet Unit notifies the User about the outcome of the verification in case the Relying Party requested attributes that it had not registered at Registrar before.
The Wallet Unit also notifies the User in case the Wallet Unit is not able to retrieve the Relying Party registration information (otherwise the notification is optional).



##### 6.6.3.4 Wallet Unit evaluates embedded disclosure policy, if present

During attestation issuance, an Attestation Provider optionally created an embedded
disclosure policy for the attestation, see [Section 6.6.2.7](#6627-provisioning-embedded-disclosure-policies).
If such a policy is present for the requested attestation, the Wallet Unit evaluates the policy, together with information in the access certificate, to determine whether the Attestation Provider allows this Relying Party to receive the requested attestation. Note that the Wallet Unit verifies the authenticity of these certificates before using any data contained in them.

The Wallet Unit presents the outcome of the disclosure policy evaluation to the
User in the form of an advice, when requesting User approval. For example, "The
issuer of your medical data does not want you to present data from \<attestation name\> to
\<Relying Party name\>. Do you want to continue?" Note that the User can
overrule the disclosure policy evaluation outcome.

For more details on the embedded disclosure policy, see [Topic 43](./annexes/annex-2/annex-2-high-level-requirements.md#a2343-topic-43---embedded-disclosure-policies).

##### 6.6.3.5 Wallet Unit obtains User approval for presenting selected attributes

**Note: In this document the term 'User approval' exclusively refers to a User's
decision to present an attribute to a Relying Party. Under no circumstances
User approval to present data from their Wallet Unit should be construed as
lawful grounds for the processing of personal data by the Relying Party or any
other entity. A Relying Party requesting or processing personal data from a
Wallet Unit must ensure that it has grounds for lawful processing of that data,
according to Article 6 of the GDPR.**

Before presenting any attribute to a Relying Party, the Wallet Unit requests the
User for their approval. This is critical for ensuring that the User remains in
control of their attributes.

A Wallet Unit requests User approval in all use cases, both in proximity flow
and remote flow, and including:

- Use cases where the Relying Party could be assumed to be trusted, for example,
when the Relying Party is part of law enforcement or another government agency.
- Use cases where the requested attributes are critical for the Relying Party to
grant access to the User or deliver the requested services.
- Use cases where there is, according to the GDPR or other legislation, no legal
need to ask for the User's approval because another legal basis exists for
requesting the attributes.

A prerequisite for requesting User approval is that the Wallet Unit is sure that
the person using the Wallet Unit is in fact the User. Therefore, the WSCA
authenticates the User prior to or during requesting User approval, on request
of the Wallet Unit. To do so, the Wallet Unit uses the User authentication
mechanisms set up during Wallet Unit activation, see
[Section 6.5.3](#653-wallet-unit-activation). More detailed requirements
regarding User approval can be found in [Topic 6](./annexes/annex-2/annex-2-high-level-requirements.md#a236-topic-6---relying-party-authentication-and-user-approval).

Another prerequisite for effective User approval is that the Wallet Unit allows
the selective disclosure of attributes. Selective disclosure implies mainly two
things. First, it enables a Relying Party to specify which of the attributes in
an attestation it wishes to receive (and which ones not). A Relying Party may
have different purposes for the requested attributes. For example, an online
liquor shop may need an age attestation to comply with its legal obligations,
and in addition would like to receive address information to be able to send the
ordered liquor to the User's home. Therefore, the Relying Party indicates the
goal of each (group of) requested attributes.

Secondly, selective disclosure implies that the Wallet Unit enables the User to
approve or deny the presentation of each (group of) attributes separately. The
User takes a decision based on at least the following information:

- The authenticated identity of the Relying Party,
- The information in the Relying Party's registration certificate or the information
received from the Registrar's on-line service regarding the
attributes that the Relying Party has registered during registration ("intended use")- at least
in case one or more of the requested attributes is not included in the list of
registered attributes,
- The information in the Relying Party's registration certificate or the information
received from the Registrar's on-line service regarding an
intermediary used by the Relying Party, if any - see [Section 3.11](#311-relying-parties-and-intermediaries).
- The outcome of the evaluation of the embedded disclosure policy, if any.

After the User gives their approval, the Wallet Unit will present the approved
User attributes to the Relying Party Instance.

##### 6.6.3.6 Relying Party Instance verifies the authenticity of the PID or attestation

The Relying Party Instance receives a PID or attestation, including some
attributes, from the Wallet Unit. Subsequently, it verifies the signature over
the PID or attestation. To do this for PIDs and QEAAs, the Relying Party
Instance uses a trust anchor of the Provider obtained from a Trusted List. Note
that the PID Provider or QEAA Provider may use an intermediate signing
certificate to sign the PID or attestation, and use the trust anchor to sign the
signing certificate, instead of signing the PID or attestation directly with the
trust anchor.

For PuB-EAAs, the Relying Party Instance verifies a PuB-EAA by first verifying
the signature of the PuB-EAA Provider over the PuB-EAA, using the PuB-EAA
Provider certificate issued by a QTSP. Subsequently, the Relying Party Instance
verifies the signature over this certificate, using the corresponding trust
anchor from the QTSP Trusted List. Note that both the PuB-EAA Provider and the
QTSP may use an intermediate signing certificate. All other things being equal,
the verification of a PuB-EAA will therefore involve one or more extra
certificates, compared to the verification of a PID or QEAA.

Finally, for non-qualified EAAs, the applicable Rulebook may describe how the
Relying Party Instance obtains the relevant trust anchor.

The above implies that a Relying Party Instance is aware whether the attestation
it is requesting from a Wallet Instance is a PID, a QEAA, a PuB-EAA, or a
non-qualified EAA. Also, the Relying Party Instance stores trust anchors in such
a way that, at the time of verification, it is able to distinguish between trust
anchors usable either for PIDs, for QEAAs, for PuB-EAAs, or for non-qualified
EAAs.

The technical implementation of the signature verification process depends on
which of the standards mentioned in [Topic 12](./annexes/annex-2/annex-2-high-level-requirements.md#a2312-topic-12---attestation-rulebooks)
is supported by the Wallet Unit. Each of these standards specifies in detail
how to carry out signature verification.

In addition, the Relying Party may want to verify that the Attestation Provider
can legally issue the type of attestation in question. As described in
[Section 6.3.2.3](#6323-pid-provider-or-attestation-provider-receives-an-access-certificate),
this is only needed for non-qualified EAA Providers, as the Relying Party trusts
a PID Provider, QEAA Provider or PuB-EAA Provider. For EAA Providers, the
applicable Rulebook may define methods that the Relying Party can use to verify
that the EAA Provider is allowed to issue this type of attestation.

Notes:

- All PIDs and attestations in the EUDI Wallet ecosystem are digitally signed by
the respective PID Provider or Attestation Provider, or by a WSCD that is part
of the Wallet Unit. If an attestation is digitally signed by a WSCD, it is
called a device-signed or self-issued attestation. Device-signed or self-issued
PIDs or attestations are allowed only if it can be shown that the WSCD signs
them at the required Level of Assurance (LoA). This implies that the level of
security offered by the WSCD is at least equivalent to the security level of the
secure infrastructure used by the PID Provider or Attestation Provider for
signing PIDs or attestations.

- The signature over the PID or attestation may or may not include the value of
the presented attributes. If the attribute values are not included in the
signature creation, the Relying Party trusts these attributes because they are
presented over an authenticated channel set up between the secure environment
(i.e., the WSCD or the secure infrastructure used by the PID Provider or
Attestation Provider, see previous bullet) and the Relying Party. One possible
way to set up such an authenticated channel is by ensuring the authenticity and
integrity (but not the non-repudiation) of the attributes by means of a Message
Authentication Code (MAC). The MAC is created by the secure environment over the
presented attribute values. The MAC key is generated from an ephemeral key of
the Relying Party (sent to the secure environment by the Wallet Instance) in
combination with an ephemeral key created by the secure environment. The latter
ephemeral key is sent to the Relying Party in such a way that the Relying Party
can verify the authenticity of this key. Such a solution, or similar ones, can
be used provided that:
    - the solution is fully compliant with the relevant standards, i.e.,
    [ISO/IEC 18013-5] or [OpenID4VP] and [SD-JWT VC].
    - the solution can be certified for security at LoA High according to
    [Chapter 7](#7-certification-and-risk-management)

##### 6.6.3.7 Relying Party verifies that the PID or attestation is not revoked

To allow revocation checking of a PID or attestation, the PID Provider or
Attestation Provider includes revocation information in the PID or attestation,
if it is valid for longer than 24 hours. This revocation information includes a
URL indicating the location where a Relying Party can obtain a status list or
revocation list, and an identifier or index for this specific certificate or
attestation within that list.

Notes:

- For attestations with a validity period of less than 24 hours, including
revocation information is not necessary.
- A status list is a bit string or byte string in which each bit or group of
bits denotes the current revocation status (valid or revoked) of one
attestation. To get the status of the attestation it has received from the
Wallet Unit, the Relying Party obtains the status list from the URL specified in
the attestation and verifies the value encoded at the bit position given by the
index value in the attestation.
- A revocation list is a list of PID identifiers or attestation identifiers
revoked by the PID Provider or Attestation Provider. To get the status of the
PID or attestation it has received from the Wallet Unit, the Relying Party
obtains the revocation list from the URL specified in the attestation and
verifies whether the identifier included in the attestation is on the list or
not.

For more details and requirements on revocation, see [Topic 7](./annexes/annex-2/annex-2-high-level-requirements.md#a237-topic-7---attestation-revocation-and-revocation-checking).

##### 6.6.3.8 Relying Party Instance verifies device binding

Device binding is the property that a PID or an attestation is bound to a
specific device (in fact, a WSCD) and cannot be used independent from that
device. Device binding protects the attestation against copying or cloning,
which enhances its security.

A PID Provider or an Attestation Provider implements device binding by including
a cryptographic public key in the PID or attestation and signing it. The
corresponding private key is protected by a certified WSCD in the Wallet Unit.

[Topic 9](./annexes/annex-2/annex-2-high-level-requirements.md#a239-topic-9---wallet-unit-attestation)
explains that a WSCD generates a public-private key pair for each attestation
upon request of the Wallet Unit, and that the Wallet Unit sends the public key
to the PID Provider or Attestation Provider. Furthermore, it discusses how the
PID or Attestation Provider can verify that the corresponding private key is
really protected by the WSCD.

During an interaction, the Relying Party verifies that the PID or attestation it
received from a Wallet Unit is indeed bound to the WSCD included in the Wallet
Unit. The Relying Party does so by requesting the Wallet Unit to sign some data
using the private key corresponding to the public key in the PID or attestation.
For this reason, device binding is also called 'proof of possession'. In
[ISO/IEC 18013-5] it is called 'mdoc authentication'. In [SD-JWT VC] it is
called 'key binding'.

The technical implementation of this verification depends on which of the
standards mentioned in [Topic 12](./annexes/annex-2/annex-2-high-level-requirements.md#a2312-topic-12---attestation-rulebooks)
is supported by the Wallet Unit. Each of these standards specifies in detail how
to carry out this verification.

##### 6.6.3.9 Relying Party Instance verifies or trusts User binding

User binding (sometimes also called 'holder binding') is the property that the
subject of the PID or attestation, meaning the natural or legal person described
in it, is in fact the person that presents the PID or attestation to the Relying
Party. User binding prevents an attacker from successfully presenting a PID or
an attestation that they are not legally allowed to use.

The mechanism(s) available for User binding depend on the presentation flow type
(proximity or remote, supervised or unsupervised, see also [Section
4.4](#44-data-presentation-flows)), and on the attributes issued to the User by
the PID Provider or Attestation Provider:

1. In the first place, the Relying Party can always decide to trust the User
authentication mechanisms implemented by the WSCD (see [Topic 9](./annexes/annex-2/annex-2-high-level-requirements.md#a239-topic-9---wallet-unit-attestation)).
This means that the Relying Party trusts that the the WSCD has properly
authenticated the User before allowing the User to present the attributes. Note
that:

- This trust is not based on the outcome of any verification by the Relying
 Party but on a a-priori trust in (in particular) the certified WSCD that is
 part of the Wallet Unit.
- Using this method implies that Relying Parties also trust device binding,
 as described in [Section 6.6.3.8](#6638-relying-party-instance-verifies-device-binding).
 The Relying Party Instance in fact first verifies that the PID or
 attestation is bound to a WSCD trusted by the PID Provider or Attestation
 Provider, and then trusts that the WSCD has properly authenticated the User.
- As a matter of fact, this User binding method will always be carried out,
 since the WSCD must authenticate its User when asking for User approval for
 presenting any attributes, and since device binding is also mandatory.

2. In addition, in some cases, if a Relying Party does not want to only trust
the above mechanism, it may be able to use User attributes to carry out an
additional User binding process. For example, if the PID or attestation contains
a User portrait, the Relying Party may be able to visually or biometrically
compare that portrait to the face of the person presenting the attestation or by
a photo taken of it by an automated machine or as a "selfie". This will
generally be possible in supervised proximity presentations by human inspection,
or in an unsupervised proximity flow if equipped with the appropriate equipment.
It may also be possible to do this in unsupervised remote presentations by using
face recognition technology, possibly even remotely. However, to generate
trustworthy outcomes in such situations, special conditions and dedicated
security measures are required, such as good lighting, clear instructions for
the User for positioning their face and an approved liveness detection mechanism
supporting Presentation Attacks Detection
([PAD](https://www.enisa.europa.eu/publications/remote-identity-proofing-attacks-countermeasures)),
as well as mechanisms for injection attack detection, in particular deepfake
detection.
3. Lastly, if the person presenting the PID or attestation is able to present an
identity document, the Relying Party may be able to verify User binding by
comparing attributes from the PID or attestation, such as first and last name,
to those in the identity document. However, this requires that the Relying Party
can verify that the identity document is authentic and really belongs to the
person presenting it. In practice this will often mean that the identity
document is a photo ID, and the presentation must consequently be done in
proximity and be supervised, or done remotely and supported by PAD.

Finally, note that in a combined presentation of attributes according to the
next section, if User binding is proven for one of the presented attestations,
it is proven for all of them.

##### 6.6.3.10 Relying Party Instance verifies combined presentation of attributes

According to the [European Digital Identity Regulation], a combined presentation
of attributes is a request for attributes from two or more attestations in the
same action. In this case, the Relying Party will verify that these attestations
belong to the same User, to prevent a hacked or fraudulent Wallet Unit from
presenting attributes from different Users.

A Relying Party can verify this by comparing attributes from the different
attestations. For example, the Relying Party may request the first and last name
of the User in all of the attestations, and compare the names. If they match,
the Relying Party concludes that the attestations belong to the same User.
However, this method implies that the Relying Party must request identifying
information from the User. In some use cases, requiring that information may not
be strictly necessary, and so this method may be seen as a threat to User
privacy. Moreover, this method may not be conclusive, for instance if multiple
people share the same name.

To solve these drawbacks, [Topic 18](./annexes/annex-2/annex-2-high-level-requirements.md#a2318-topic-18---combined-presentations-of-attributes)
describes how the Relying Party Instance can verify this cryptographically by
checking that the private keys paired with the public keys in the attestations are protected by the same WSCD. This is further described in [Topic 9](./annexes/annex-2/annex-2-high-level-requirements.md#a239-topic-9---wallet-unit-attestation).

##### 6.6.3.11 Relying Party Instance authenticates the Wallet Unit and the Wallet Provider

[Section 6.5.3](#653-wallet-unit-activation) above describes that a Wallet
Provider, during the lifetime of a Wallet Unit, ensures that the Wallet Unit is
always in possession of one or more valid Wallet Unit Attestations (WUAs).
Either before or after requesting one or more PIDs or attestations from a Wallet
Unit, a Relying Party Instance can:

- request a WUA from the Wallet Unit.
- verify the signature over the WUA using the Wallet Provider trust anchor
obtained from the Wallet Provider Trusted List.
- verify that the Wallet Unit is in possession of the private key belonging to
the public key in the WUA. This proves that the Wallet Unit is authentic and is
provided by the trusted Wallet Provider.

Note that requesting and verifying the WUA is not mandatory.

##### 6.6.3.12 Relying Party verifies that WUA is not revoked

[Section 6.6.2.4](#6624-pid-provider-or-attestation-provider-verifies-that-wua-is-not-revoked)
explained how a PID Provider or an Attestation Provider can verify that a WUA
(and thus the Wallet Unit) is not revoked. The same mechanism can be used by
Relying Party Instances as well.

##### 6.6.3.13 Wallet Unit enables the User to report suspicious requests by a Relying Party and to request a Relying Party to erase personal data

A Wallet Unit enables the User to report unlawful or suspicious requests for
personal data by a Relying Party to a Data Protection Authority (DPA). To allow
this, a Wallet Unit provides a dashboard allowing the User to lodge a complaint
about a suspicious Relying Party presentation request to the DPA of the Member
State that provided their Wallet Unit. For more information and requirements,
see [Topic 50](./annexes/annex-2/annex-2-high-level-requirements.md#a2350-topic-50---blueprint-to-report-unlawful-or-suspicious-request-of-data).
The User can make such a report regardless of whether any attributes were
actually presented to the Relying Party. Even if the Wallet Instance prevented
the presentation of any attributes because Relying Party authentication failed,
or if the User did not approve the presentation of any attributes, the User can
still lodge a complaint about the request with the relevant Data Protection
Authority.

The dashboard also enables the User to request a Relying Party to erase personal
data. For more information and requirements, see [Topic 48](./annexes/annex-2/annex-2-high-level-requirements.md#a2348-topic-48---blueprint-for-requesting-data-deletion-to-relying-parties).

To be able to substantiate a complaint, or to list data that must be deleted,
the User needs to be informed about which attributes were requested by which
Relying Parties. To enable this, a Wallet Unit maintains a log of all transactions that are performed. For presentation transactions, this log includes the attributes
that were requested and presented. The aforementioned dashboard also enables the
User to view the log and lodge a complaint for any transaction in the log. More
details about the logging functionality can be found in [Topic 19](./annexes/annex-2/annex-2-high-level-requirements.md#a2319-topic-19---user-navigation-requirements-dashboard-logs-for-transparency).

#### 6.6.4 PID or attestation presentation to another Wallet Unit

[Section 6.6.3](#663-pid-or-attestation-presentation-to-relying-party) discussed
the trust relationships necessary when a Wallet Unit receives a request from a
Relying Party Instance and presents attributes to that Relying Party Instance.

However, the [European Digital Identity Regulation] requires that a Wallet Unit
is also able to receive such a request from another Wallet Unit, and present
attributes to that requesting Wallet Unit. For more information and
requirements, please refer to [Topic 30](./annexes/annex-2/annex-2-high-level-requirements.md#a2330-topic-30---interaction-between-wallet-units).

#### 6.6.5 PID or attestation management

##### 6.6.5.1 Overview

Starting from the issuance of a PID or attestation, the PID or attestation is
managed by the User and the Wallet Provider. Management is performed until the
PID, or attestation, is deleted or the Wallet Instance is uninstalled by the
User. Management includes at least the following processes:

1. Re-issuance of the PID or attestation when necessary.
2. Revocation of the PID or attestation when necessary.

These processes are discussed in the next subsections.

##### 6.6.5.2 PID or attestation re-issuance

###### 6.6.5.2.1 Introduction

Re-issuance means the replacement of a PID or attestation that already exists in
a Wallet Unit by a PID or attestation having the same attestation type. Re-issuance
is always performed by the same PID Provider or Attestation Provider that issued
the existing PID or attestation, and it is initiated by the Wallet Unit. The
value of the attributes in the new attestation will typically be the same as in
the original attestation. However, this is not required; the PID Provider or
Attestation Provider may change one or more attribute values. Re-issuance is
only applied within the administrative validity period of a document. As an
example, a mobile driving licence (mDL) will typically be issued in the form of
attestations which have a technical validity period shorter than the
administrative validity period of the licence itself. Re-issuance is used for
obtaining fresh attestations as needed during the administrative validity
period, to ensure that the User can always present a valid mDL. When the
administrative validity period ends, there will be an administrative process for obtaining a new
driving license, which is however out of scope of this document.

Note that, in general, if the original PID or attestation was issued in a batch,
then the PID Provider or Attestation Provider will re-issue that PID or
attestation in a batch as well.

There may be different reasons for re-issuing a PID or attestation, for example:

- The current PID(s) or attestation(s) are near the end of their
 technical validity period, or the Wallet Unit is running out of once-only
 attestations. This is done to mitigate the risk of Relying Party linkability. For more information, see [Section 7.4.3.5](#7435-risks-and-mitigation-measures-related-to-user-privacy).
- The value of one or more of the attributes in the PID or attestation
 has changed.
- The security architecture of the Wallet Solution may use PIDs and/or
 attestations that are issued just-in-time, at the moment that PID or
 attestation is being requested by a Relying Party. This is sometimes
 called synchronous issuing.

These reasons are discussed in the next subsections. Re-issuance is discussed in
more detail in the [Discussion Paper for Topic B](././discussion-topics/b-re-issuance-and-batch-issuance-of-pids-and-attestations.md).

###### 6.6.5.2.2 Re-issuance to limit Relying Party linkability

As specified in [ISO/IEC 18013-5] or [SD-JWT VC], each PID or
attestation contains metadata indicating its technical validity period.
Determining the length of the technical validity period is the responsibility of
the PID Provider or the Attestation Provider. The
technical validity period chosen by the PID Provider or Attestation Provider will
depend on several factors, primarily the security architecture of the
Wallet Solution and the strategy chosen to mitigate Relying Party
linkability, see [Section 7.4.3.5](#7435-risks-and-mitigation-measures-related-to-user-privacy).

Given the above factors, it can generally be assumed that the technical validity
period of a PID or attestations will be much shorter than their lifetime,
meaning the period of time that a User wants to keep that PID or attestation in
their Wallet Unit. That implies that new PIDs and attestations will need to be
re-issued periodically, to replace the ones that are reaching end of their
technical validity.

A similar reason for re-issuing PIDs and attestations occurs when the
PID Provider or Attestation Provider uses once-only attestations (see [Section 7.4.3.5](#7435-risks-and-mitigation-measures-related-to-user-privacy)),
which can be presented only once to a Relying Party. In that case, the Wallet
Unit, or rather the User, will regularly need new PIDs or attestations to avoid
running out.

Re-issuance of PIDs or attestations for these reasons is a purely technical
matter. To the maximum extent possible, the User does not notice that a PID or
attestation has been re-issued, nor do they have to take any action to ensure
that re-issuance happens in time. These conditions are very different from a
first-time issuance of a PID or attestation, where the User must take the
initiative to request the PID or attestation, and is potentially involved in the
process in other ways as well.

This implies, among other, that no User authentication can take place during
re-issuance of an existing attestation. Nevertheless, a Wallet Unit may offer
the User the option to receive a notification of re-issuance.

In the absence of User authentication, and to prevent that a re-issued PID or
attestation ends up at the wrong User, the PID Provider or Attestation Provider
ensures that the re-issued PID or attestation is bound to the same WSCD as the
PID or attestation it replaces.

Finally, since the User is not involved, it is the Wallet Unit that triggers the
re-issuance of PIDs and attestation when necessary.

###### 6.6.5.2.3 Re-issuance because of a change of attribute values

During the lifetime of a PID or attestation, the value of some of the attributes
may change. For example, at the date of birth of the User, an age attestation
attribute (i.e., an attribute indicating whether the User has reached a certain
age) may have to be changed from value False to value True. In another example,
the User of a mobile driving licence may have passed the examination for a
different vehicle category. In this case, the PID Provider or Attestation
Provider shall re-issue the PID or attestation with the correct attribute
values, and shall revoke the existing attestation.

Re-issuance of a PID or attestation for this reason will have an impact on the
User, because they will notice that their attribute values have been changed.
Therefore, in this case Users will be informed when re-issuance happens.
Additionally, an Attestation Provider may state in their terms of conditions
that re-issuance of an attestation may be used.

###### 6.6.5.2.4 Re-issuance when using synchronous issuing

A third reason for re-issuing a PID or attestation is where the PID Provider or
Attestation Provider uses synchronous issuing in their security architecture. In
such an architecture, the Wallet Unit requests the re-issuance of a new PID or
attestation after it has received a request for that PID or attestation from a
Relying Party. Such a PID or attestation is very short-lived and is used only
once.

The conditions on User awareness and authentication discussed in [Section 6.6.5.2.2](#66522-re-issuance-to-limit-relying-party-linkability) are also valid for a synchronous re-issuance process.

###### 6.6.5.3 PID or attestation revocation

PID or attestation management includes ensuring that PIDs and attestations can
be revoked if necessary. Revocation is discussed in [Topic 7](./annexes/annex-2/annex-2-high-level-requirements.md#a237-topic-7---attestation-revocation-and-revocation-checking).
The User can request the PID Provider or Attestation Provider to revoke the PID
or attestation at least in case of loss or theft. In addition, a PID Provider or
Attestation Provider could regularly verify, for each of its valid PIDs or
attestations, whether the Wallet Provider revoked the Wallet Unit on which that
PID or attestation is residing. If it turns out that the Wallet Unit is revoked,
the PID Provider or Attestation Provider could revoke the respective PID or
attestation. Currently, no mechanism has been specified yet to enable a PID
Provider or Attestation Provider to verify whether a Wallet Unit is revoked.
This will be discussed for ARF 2.0.

#### 6.6.6 PID or attestation deletion

In case the User no longer wants to retain a specific PID or attestation in
their Wallet Unit, the User can delete it. If the PID Provider or Attestation
Provider issued a batch of multiple PIDs or attestations that have the same
content and are valid, the Wallet Unit deletes them all. Deleting a PID or an
attestation also means that the WSCD destroys the cryptographic key material
associated with that PID or attestation. Before deleting the PID or attestation
and the cryptographic keys, the WSCA included in the Wallet Unit will
authenticate the User.

If it supports the Digital Credentials API, see [Section 4.4.3](#443-remote-presentation-flows), the Wallet Unit also discloses the fact that it no longer contains the PID or attestation to the Digital Credentials API framework.

For high-level requirements on this topic, see [Topic 51](./annexes/annex-2/annex-2-high-level-requirements.md#a2351-topic-51---pid-or-attestation-deletion).

## 7 Certification and Risk Management

### 7.1 Introduction

This chapter briefly describes the certification of Wallet Solutions and the eID
schemes under which they are provided, covering the overall certification
approach, design principles, and key requirements outlined in the [European
Digital Identity Regulation](https://eur-lex.europa.eu/legal-content/EN/ALL/?uri=CELEX:32024R1183)
and Commission Implementing Regulation (CIR) laying down rules for on the
certification of Wallet Solution (2024/2981), or simply the [CIR 2024/2981](https://eur-lex.europa.eu/legal-content/EN/TXT/HTML/?uri=OJ:L_202402981).
Furthermore, references are made to the Annex I of the CIR, the [Risk
Register](https://eur-lex.europa.eu/legal-content/EN/TXT/HTML/?uri=OJ:L_202402981#anx_I,),
supporting the risk-based approach of the Wallet Solutions. For more detailed
requirements, please refer to the
[CIR 2024/2981](https://eur-lex.europa.eu/legal-content/EN/TXT/HTML/?uri=OJ:L_202402981)
itself.

The [European Digital Identity Regulation](https://eur-lex.europa.eu/legal-content/EN/ALL/?uri=CELEX:32024R1183)
requires certification of Wallet Solutions to ensure conformity of the Wallet
Solutions with functional, security, and privacy related requirements, to
achieve a high level of interoperability, security and trustworthiness.
Certification applies to the Wallet Solutions and the eID schemes under which
they are provided; for ease of reading this chapter only refers to Wallet
Solutions. Furthermore, the object of certification includes software
components, hardware components (in cases where they are provided directly or
indirectly by the Wallet Provider) and the processes that support the provision
and operation of a Wallet Solution, such as Wallet Unit activation, see
[Section 6.5.3](#653-wallet-unit-activation).

The aim is to harmonise the implementation of the requirements laid down by the
[European Digital Identity Regulation] and avoid divergent approaches to the
maximum extent possible. For this reason, the Commission requested ENISA to
prepare a candidate European certification scheme under the Cybersecurity Act,
the [CSA](https://eur-lex.europa.eu/eli/reg/2019/881/oj). As defining and
adopting a dedicated, harmonised certification scheme for Wallet Solutions
depends on agreements between Member States on detailed security requirements,
on the availability of underlying certification schemes, and on established good
practices in the Member States themselves, a transitory approach is foreseen by
means of national certification schemes.

In other words, the certification approach for Wallet Solutions follows two
phases. In the short-term, Member States provide national (transitory)
certification schemes. In the medium term, a harmonised CSA scheme will be
established. When the CSA-based scheme becomes available, it replaces the
national schemes as for cybersecurity requirements. The schemes may continue to
exist for functional requirements.

### 7.2. Certification of Wallet Solutions against national certification schemes

Until a dedicated Wallet Solution cybersecurity certification scheme under the
CSA is available, the [European Digital Identity Regulation] requires Member
States to establish national certification schemes. This will be done in time to
make available the Wallet Solutions before the end of 2026. The Commission has
adopted the [CIR 2024/2981](https://eur-lex.europa.eu/legal-content/EN/TXT/HTML/?uri=OJ:L_202402981)
to provide the main requirements on Member States for creation of national
certification schemes. The [CIR 2024/2981](https://eur-lex.europa.eu/legal-content/EN/TXT/HTML/?uri=OJ:L_202402981)
and resulting national certification schemes are defined around a number
of guiding principles:

First, the goal is to harmonise requirements to the extent possible. Member
States are also encouraged to work together in the design and implementation of
national schemes. Additionally, national schemes will leverage the use of
relevant and existing certification schemes and standards for Wallet Solution
certification and evaluation. Where available, relevant European CSA schemes
must be used. Currently, only the Common Criteria based European candidate
cybersecurity certification
[EUCC](https://certification.enisa.europa.eu/about-eu-certification/developing-certification-schemes_en)
scheme is available for the cybersecurity certification of ICT products, parts,
or components for products. Upcoming CSA-based schemes include
[EUCS](https://certification.enisa.europa.eu/about-eu-certification/developing-certification-schemes_en)
&
[EU5G](https://certification.enisa.europa.eu/about-eu-certification/developing-certification-schemes_en).
Additionally, other existing or upcoming schemes​ include schemes based on
FITCEM (EN 17640)​, national schemes such as on remote identity verification, or
other private schemes (e.g. for mobile devices and apps)​. For harmonisation of
functional requirements, the Commission Implementing Regulations (CIRs) adopted
under the [European Digital Identity Regulation](https://eur-lex.europa.eu/legal-content/EN/ALL/?uri=CELEX:32024R1183)
article 5(a) are referenced. For harmonisation of certification requirements,
the ISO/IEC 17065 framework under Regulation [765/2008] is used, complemented by
ISO/IEC 17067 on the definition of schemes.

Next, the [CIR 2024/2981](https://eur-lex.europa.eu/legal-content/EN/TXT/HTML/?uri=OJ:L_202402981)
refers to the composite nature of the Wallet Solutions as well as the potential
different architectures in Member States, considering that the
[European Digital Identity Regulation](https://eur-lex.europa.eu/legal-content/EN/ALL/?uri=CELEX:32024R1183)
is technology (and architecture) neutral. This means that a final ('top-level')
certification of the Wallet Solution will yield a composite certificate, built
on certification of separate components, such as EUCC certification. Wallet
Solutions are always to be certified against assurance level High, as set out
in the [European Digital Identity Regulation](https://eur-lex.europa.eu/legal-content/EN/ALL/?uri=CELEX:32024R1183)
as well as [CIR (EU) 2015/1502](https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=OJ%3AJOL_2015_235_R_0002).
That assurance level has to be reached by the overall Wallet Solution. Under
this Regulation, some components of the Wallet Solution may be certified at a
lower assurance level, provided this is duly justified and without prejudice to
the assurance level High reached by the overall Wallet Solution. For the use
of assurance information from other certification schemes or sources, a
dependency analysis will be performed.

Finally, in order to ensure a harmonised approach to cybersecurity and the
assessment of the most critical risks that might affect the provision and
operation of Wallet Units, a register of risks and threats is defined, see
[7.4 Risk-based approach and risk register](#74-risk-based-approach-and-risk-register).
The [Risk Register](https://eur-lex.europa.eu/legal-content/EN/TXT/HTML/?uri=OJ:L_202402981#anx_I)
contains high level risks and threats in relation to Wallet Solutions and the
ecosystem, as well as detailed threat scenarios that will be taken into
consideration when designing Wallet Solutions, independent of their specific
architecture.

As a first step towards certification of Wallet Solutions under national
schemes, Member States will assign a scheme owner, and design and roll out the
scheme. As part of this process, Certification Bodies (CBs) will be accredited
to carry out conformity assessments of Wallet Solutions against the requirements
of the [CIR 2024/2981](https://eur-lex.europa.eu/legal-content/EN/TXT/HTML/?uri=OJ:L_202402981)
and the national scheme. Wallet Providers then request one or more designated
CABs to assess and certify the conformity of their Wallet Solution. The CAB
evaluates and certifies the conformity of the Wallet Solution if they meet the
requirements.

The European Commission and ENISA support Member States in designing and
implementing national certification schemes in the Cooperation Group.

### 7.3 Certification of Wallet Solutions against a dedicated CSA-based scheme

In parallel to the work described above, ENISA is requested to draft a dedicated
European cybersecurity certification scheme for the Wallet Solutions under the
[CSA](https://eur-lex.europa.eu/eli/reg/2019/881/oj). Once available, this
CSA-based scheme will replace the national transitory schemes mentioned above
for the cybersecurity requirement it covers. This scheme will be based on
available national schemes, harmonised requirements, and identify any additional
requirements relevant for cybersecurity. The scheme will further detail the
cybersecurity requirements, identify and set normative standards and define the
target level of assurance or security for the relevant Wallet Solution
components.

The work to develop the CSA-based scheme follows the milestones set out by the
[CSA](https://eur-lex.europa.eu/eli/reg/2019/881/oj) and is supported by the Ad
Hoc Working Group or '[AHWG](https://www.enisa.europa.eu/news/call-for-experts-join-the-enisa-ad-hoc-working-group-on-eu-digital-identity-wallets-cybersecurity-certification)'.
This group is composed of selected experts from private organisations and
industry, with extensive knowledge and experience in the areas of cybersecurity
certification, digital wallets, electronic identification and trust services.
The first step is to have a candidate scheme ready for public consultation and
submitted for feedback of the European Cybersecurity Certification Group or
[ECCG](https://digital-strategy.ec.europa.eu/en/policies/cybersecurity-certification-group).
The ECCG’s opinion serves as advisory input to ensure the candidate scheme
aligns to EU cybersecurity objectives, standards and regulatory requirements.
Although the ECCG’s opinion is not binding, it will hold significant influence,
as it reflects the collective expertise of national cybersecurity authorities,
aiming to harmonise cybersecurity certification practices across Member States.
Based on this input, the candidate scheme might be updated further. After
finalisation of the ECCG opinion, the scheme will be transformed into a new
Implementing Regulation and adopted by comitology procedure.

Finally, ENISA is also asked to facilitate the transition from national
certification schemes to the dedicated cybersecurity certification scheme under
the CSA.

### 7.4 Risk-based approach and risk register

#### 7.4.1 Introduction

This section details the approach to develop harmonised guidelines for the
development of the transitory national certification schemes. In addition to the
requirements set out in the [European Digital Identity Regulation](https://eur-lex.europa.eu/legal-content/EN/ALL/?uri=CELEX:32024R1183)
article 5c, cybersecurity risks and threats associated with the Wallet Solutions
will be identified. Here, a risk-based approach is envisioned as the basis for
certification by Member States, ensuring that the Wallet Solutions uphold
confidentiality, availability and strong safeguards for User privacy and data
protection. This is inspired by known processes, such as for the General Data
Protection Regulation ([GDPR](https://eur-lex.europa.eu/eli/reg/2016/679/oj))
and related Data Protection Impact Assessments (DPIA).

The risk-based approach sets out a common [Risk Register](https://eur-lex.europa.eu/legal-content/EN/TXT/HTML/?uri=OJ:L_202402981#anx_I)
that contains a comprehensive but non-exhaustive list of risks and threats
related to the Wallet Solution. These risks and threats are
architecture-agnostic and provide a benchmark overview of the most critical
risks and threats to Wallet Solutions. By adopting this common set of risks and
threats, national transitory certification schemes will achieve a baseline level
of harmonisation.

The risk register will be applied by scheme owners, Wallet Providers, and
Certification Bodies (CBs). When establishing their certification schemes,
scheme owners will perform a risk assessment to refine and complement the risks
and threats listed in the register with those specific to their architecture,
and consider how the applicable risks and threats can be appropriately treated.
Wallet Providers will complement the scheme’s risk assessment to identify any
risks and threats specific to their implementation and propose appropriate
mitigation measures for evaluation by the certification body.

#### 7.4.2 High-level risks and threats

The following is an excerpt from [Risk Register]. To keep in line with the
continuously evolving threat landscape, the risk register will be maintained and
regularly updated in collaboration with the Cooperation Group.

High-level risks and threats

 R1 Creation or use of an existing electronic identity
 R2 Creation or use of a fake electronic identity
 R3 Creation or use of fake attributes
 R4 Identify theft
 R5 Data theft
 R6 Data disclosure
 R7 Data manipulation
 R8 Data loss
 R9 Unauthorised transaction
 R10 Transaction manipulation
 R11 Repudiation
 R12 Transaction data disclosure
 R13 Service disruption
 R14 Surveillance

System-related risks

 SR1 Wholesale surveillance
 SR2 Reputational damage
 SR3 Legal non-compliance

Technical threats

 TT1 Physical attacks

 1.1 Theft
 1.2 Information leakage
 1.3 Tampering

 TT2 Errors and misconfigurations

 2.1 Errors made when managing an IT system
 2.2 Application-level errors or usage errors
 2.3 Development-time errors and system misconfigurations

 TT3 Use of unreliable sources

 3.1 Erroneous use or configuration of wallet components

 TT4 Failure and outages

 4.1 Failure or dysfunction of equipment, devices or systems
 4.2 Loss of resources
 4.3 Loss of support services

 TT5 Malicious actions

 5.1 Interception of information
 5.2 Phishing and spoofing
 5.3 Replay of messages
 5.4 Brute-force attack
 5.5 Software vulnerabilities
 5.6 Supply chain attacks
 5.7 Malware
 5.8 Random number prediction

#### 7.4.3 Risks and mitigation measures discussed in Chapter 6 of this ARF

##### 7.4.3.1 Introduction

This section briefly discusses some of the risks that were considered when the
trust model in [Chapter 6](#6-trust-model) was created, together with the
mitigations for these risks and the residual risks that remain after these
mitigations. This section is not intended to be a comprehensive risk register
for the EUDI Wallet ecosystem as a whole; for that register, see [Risk Register]
and [Section 7.4.2](#742-high-level-risks-and-threats) above.
This section is limited to the scope of the ARF, namely, the Wallet Unit and its
interactions with other entities in the ecosystem, as depicted in [Figure 11](#61-scope) in
Chapter 6.

##### 7.4.3.2 Risks and mitigation measures related to confidentiality, integrity, and authenticity

Within the EUDI Wallet ecosystem, many interactions take place between entities
in which one entity requests another entity to perform a task. For example, a
User may ask a PID Provider or an Attestation Provider to provide a PID or an
attestation to a Wallet Unit, or a Relying Party may ask a User to present
attributes from an attestation in their Wallet Unit.
For any of these interactions, the following risks apply:

- An attacker could impersonate one of the interacting entities. Therefore, the
receiver of a message must be able to verify the identity of the sender, and
vice versa. In other words, mutual authentication is needed. This authentication
can be performed because valid entities in the EUDI Wallet ecosystem are put on
a Trusted List by Member States. By verifying the signature over a message and
verifying the associated public key certificates with a trust anchor included in
a Trusted List, the receiver of a message can be sure about the identity of the
message's sender.
- Messages between entities could be intercepted, meaning that they could be read
by an attacker. To mitigate this risk, messages must be encrypted to ensure
confidentiality.
- Intercepted messages could be changed by an attacker. To mitigate this risk,
messages must be authenticated, so that the receiver can verify that originate
from the authenticated sender and were not changed.

##### 7.4.3.3 Risks and mitigation measures related to tampering of cryptographic keys and sensitive data

The mechanisms for authentication and confidentiality described in the previous
section rely on the security of cryptographic keys, especially private and
secret keys. If an attacker can obtain, use, or tamper with these keys, these
security mechanisms would break down. Therefore, all cryptographic keys are
managed by dedicated secure applications (WSCAs), running on secure hardware
(WSCDs), as described in [Section 4.3](#43-reference-architecture). The security
of WSCDs and WSCAs is ensured by means of an appropriate certification process.

These mitigation measures apply for all entities in the EUDI Wallet ecosystem
that use cryptographic keys, including Wallet Units, Wallet Providers, PID
Providers and Attestation Providers, Trusted List Providers, and Certificate
Authorities. For Relying Parties and Relying Party Instances, such measures are
formally not required.

WSCDs and WSCAs in a Wallet Unit may also be used to store other sensitive data
except cryptographic keys. In particular, they could be used to store User
attributes, in such a way that attackers, including malicious applications
residing on the same User device as the Wallet Instance, cannot retrieve these
attributes. This is beneficial for User privacy.

##### 7.4.3.4 Risks and mitigation measures related to authorisation

In certain cases, there is a risk that a legitimate entity within the EUDI Wallet
ecosystem may attempt to perform actions beyond its authorised scope. This risk
primarily affects two types of entities.

First, a non-qualified EAA Provider may attempt to issue attestations for which
it lacks the necessary authorisation. For example, an Attestation Provider that
has not been officially designated by a Member State or another relevant
authority to issue diplomas may still attempt to generate an attestation of the
diploma type. Within the EUDI Wallet ecosystem, this risk is limited to
non-qualified EAA Providers, as PID Providers, QEAA Providers, and PuB-EAA
Providers are assumed to be inherently trustworthy in this context.
For more information, see [Section 6.3.2.3](#6323-pid-provider-or-attestation-provider-receives-an-access-certificate).

This risk is mitigated by querying the Relying Party registry via an API. This
registry, maintained by the Member State, contains comprehensive information
about each Relying Party, allowing the system to verify the legitimacy of the
issuer and ensure compliance with regulatory requirements.

In the context of the [European Digital Identity Regulation] Regulation, the
term Relying Party encompasses both Attestation Providers and entities that
provide services relying on attestations, ensuring a broad and consistent
approach to trust and verification within the EUDI Wallet ecosystem.

Second, a Relying Party in the EUDI Wallet ecosystem may attempt to request
attributes from a Wallet Unit without being registered or authorised to
do so. This risk is mitigated mainly by three measures:

1. **Selective Disclosure and User Control** – The attestation formats and
protocols specified in [ISO/IEC 18013-5] and [SD-JWT VC] + [OpenID4VP] enable
selective disclosure of attributes. This allows a Relying Party to specify which
attributes within an attestation it wishes to receive while excluding others, a
feature known as *collection limitation*. Additionally, selective disclosure
ensures that the User retains control over their data, as they can approve or
deny the presentation of requested attributes. More details on selective
disclosure and User approval can be found in [Section 6.6.3.5](#6635-wallet-unit-obtains-user-approval-for-presenting-selected-attributes).
2. **Mandatory Relying Party Registration of Requested Attributes** – The
[European Digital Identity Regulation] mandates that each Relying Party register
the attributes it intends to request from Users. According to [CIR 2024/2982](https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=OJ:L_202402982),
these registered attributes must be included in a Relying Party registration
certificate, which the Wallet Unit uses to verify the legitimacy of the request
and inform the User accordingly. This transparency ensures that Users can make
an informed decision about whether to approve or deny the presentation of the
requested attributes.
More details on this requirement can be found in [Section 6.6.3.3](#6633-wallet-unit-allows-user-to-verify-that-relying-party-does-not-request-more-attributes-than-it-registered).
3. **Attestation Provider Disclosure Policy Enforcement** – The [European
Digital Identity Regulation] also mandates that Attestation Providers can embed
a disclosure policy within their attestations. This policy may include rules
governing whether the Attestation Provider approves the presentation of this attestation to an authenticated Relying Party. The Wallet Unit evaluates this
policy —if present— alongside authenticated data from the Relying Party, and
informs the User of the outcome. This mechanism further supports the User in
making a well-informed decision on whether to approve or deny attribute
presentation. More information on disclosure
policy enforcement can be found in [Sections 6.6.2.7](#6627-provisioning-embedded-disclosure-policies) and [6.6.3.4](#6634-wallet-unit-evaluates-embedded-disclosure-policy-if-present).

##### 7.4.3.5 Risks and mitigation measures related to User privacy

###### 7.4.3.5.1 Linkability

User privacy is a key consideration in the design and implementation of the EUDI
Wallet ecosystem. An important aspect of privacy is unlinkability. Unlinkability
implies that, if a User presents attributes from an attestation multiple times,
the receiving Relying Parties cannot link these separate presentations to
conclude that they concern the same User.

Within the EUDI Wallet ecosystem, attributes are presented in electronic
attestations containing unique, fixed elements such as hash values, salts,
public keys, and signatures. Malicious Relying Parties could exploit these
values to track Users by storing and comparing them across multiple
transactions, identifying recurring patterns. This privacy threat, known as
**Relying Party linkability**, can occur within a single Relying Party or among
colluding entities.

A similar privacy threat arises when colluding Relying Parties share the unique
values they obtained from an attestation with a malicious PID Provider or
Attestation Provider. This allow the PID Provider or Attestation Provider to
track User activity across multiple services. In this case, it's called
**Attestation Provider linkability**.

This topic is discussed in more detail in the [Discussion Paper for Topic A](../../discussion-topics/a-privacy-risks-and-mitigations.md).

###### 7.4.3.5.2 Mitigating Relying Party linkability

Regarding the mitigation of Relying Party linkability: A trustworthy PID
Provider or Attestation Provider can mitigate Relying Party linkability fully by
issuing multiple PIDs or attestations to the same User. Wallet Units can use
these attestations as disposable (single-use) attestations, which ensures
attestations can never be linked by Relying Parties. [Topic 10/23 in Annex 2](./annexes/annex-2/annex-2-high-level-requirements.md#a2310-topic-10---issuing-a-pid-or-attestation-to-a-wallet-unit)
calls this 'once-only attestations', and requires Wallet Solutions to support
this method. It also specifies how a PID Provider or Attestation Provider can
indicate that they want a Wallet Unit to treat their PIDs or attestations in
this way.

However, the 'once-only' approach increases issuance complexity and management
overhead. Therefore, [Topic 10/23](./annexes/annex-2/annex-2-high-level-requirements.md#a2310-topic-10---issuing-a-pid-or-attestation-to-a-wallet-unit)
also mandates support for another solution, where PIDs and attestations are
valid for a limited time only. This limits the amount of PIDs and attestations
to be issued, but only partially mitigates Relying Party linkability. Topic
10/23 calls this 'limited-time attestations'.

Furthermore, Topic 10/23 describes two other approaches, which are optionally
supported by Wallet Solutions, namely:

- the Attestation Provider issues attestations in batches to the Wallet Unit.
The Wallet Unit then uses the attestations from a batch in a random order, until
it has presented all attestations in the batch once. Then it 'resets' the batch
and starts using them again in a random order. Topic 10/23 calls this
'rotating-batch attestations'.
- the Wallet Unit will present different attestations to different Relying
Parties. However, in case a Relying Party requests attributes from this
attestation multiple times, the Wallet Unit will present the same attestation to
this Relying Party each time. Topic 10/23 calls this 'Per-Relying Party
attestations'.

Additionally, organisational and enforcement measures can help deter Relying
Parties from colluding and tracking Users. In particular, Relying Parties found
in violation will have their access certificates revoked, preventing them from
further interactions with Wallet Units.

###### 7.4.3.5.3 Zero-Knowledge Proofs

Attestation Provider linkability cannot be fully eliminated when using
attestation formats based on salted hashes. The only viable mitigation is to
adopt Zero-Knowledge Proofs (ZKPs) as a verification mechanism instead of
relying on salted-attribute hashes. However, the integration of ZKPs in the EUDI
Wallet ecosystem is still under discussion and development due to the complexity
of implementing ZKP solutions in secure hardware and the lack of support in
currently available secure hardware (WSCDs). As with Relying Party
linkability, organisational and enforcement measures can help deter Attestation
Providers from colluding and tracking Users. Additionally, many Attestation
Providers are subject to regular audits, making it easier to detect collusion
and tracking compared to Relying Parties.

Zero-Knowledge Proof (ZKP) mechanisms for verifying personal information are
highly promising and essential for ensuring privacy in various use cases. They enable Users to prove statements such as "I am over 18" without
disclosing any personal data, offering a robust solution for privacy-preserving
authentication and verification.

One key area of development is age verification, where the European Commission
is actively exploring and testing ZKP-based solutions. The outcomes of this
initiative could pave the way for the adoption of ZKPs within the EUDI Wallet
ecosystem, further strengthening privacy protections in future implementations.

The [Discussion Paper for Topic G](./discussion-topics/g-zero-knowledge-proof.md) (Zero-Knowledge Proofs) presents the (desired) privacy properties of Zero-Knowledge Proof schemes. It introduces the main families of Zero-Knowledge Proof schemes and gives an overview of representative solutions. Finally, it discusses topics related to the integration of Zero-Knowledge Proof schemes into the EUDI Wallet ecosystem.

## 8 Document development

### 8.1 Publication

This document is made publicly available at
<https://github.com/eu-digital-identity-wallet/eudi-doc-architecture-and-reference-framework>
(GitHub repository) where it will be regularly updated.

### 8.2 Contributing

We value your feedback and encourage you to share any thoughts, suggestions, or
concerns you may have regarding this document.

#### 8.2.1 Providing Feedback

To provide feedback on this document, please visit our GitHub repository. You
can do so by navigating to the "Issues" tab and submitting a new issue or
commenting on existing ones. Whether you've spotted a typo, have a suggestion
for clarifying a section, or want to propose a new topic for inclusion, we
welcome your feedback.

##### 8.2.1.1 Guidelines for adding issues to the Github repository

When adding issues to the Github repository, please follow these general guidelines:

- Use **clear and descriptive titles** for your issues to provide a concise
summary of the problem or task. This helps others quickly understand the issue
at a glance.
- Provide a **detailed description of the issue**, including any relevant
context, background information. The description should be comprehensive enough
for others to understand the issue and take appropriate action.
- Use one or more of the following **labels** to categorise issues. Labels help
organise and prioritise issues, making it easier to manage the repository.

| **Label** | **Description** |
|-----------------------|-------------------|
| Content Clarifications| Raise issues seeking clarification on specific content within the document. This could include explanations of concepts, definitions of terms, or examples to illustrate certain points. |
| Suggestions for Improvements | Propose suggestions to enhance the clarity, completeness, or accuracy of the document. This could involve restructuring sections, adding examples, or providing additional information. |
| Errors and Corrections | Identify errors such as typos, grammatical mistakes, or factual inaccuracies within the document and suggest corrections. |
| Compatibility and Integration | Issues related to how the document integrates with other systems or technologies, ensuring compatibility with different platforms or frameworks. |
| Enhancement Requests | Request new features, sections, or content to be added to the document to improve its usefulness or relevance. |
| Formatting and Styling | Feedback regarding the visual appearance, organisation, and consistency of formatting within the document. |
| Documentation Standards | Discussions around adhering to documentation standards, conventions, or guidelines. |
| Licence and Legal Concerns | Questions or concerns related to the licensing of the document, usage rights, attribution requirements, or legal implications for contributors and Users. |
| Technical Clarification | Raise issues seeking clarification on specific technical content within the document. |

- **Attach** relevant files, screenshots, or links to additional resources that
provide context or assist in resolving the issue. This can include
**references** to related documentation or discussions.
- **Follow issue etiquette** by conducting a search to see if the issue has
already been reported before creating a new one. This helps avoid duplicate
issues.

##### 8.2.1.2 Guidelines for discussing existing issues in the GitHub repository

When discussing existing issues in the Github repository, please follow these
general guidelines:

- **Communicate with respect and courtesy** towards other contributors, maintain
a professional tone, and avoid using language that could be interpreted as
confrontational or inflammatory.
- Provide **context and background information** to help others understand your
perspective. Explain the reasoning behind your comments.
- Communicate your intentions and motivations behind your comments or
suggestions to **avoid misunderstandings**.
- Keep **discussions focused on the technical aspects of the issue** at hand.
- Provide **constructive feedback and suggestions** in a helpful and supportive
manner. Instead of simply pointing out problems, offer solutions or alternative
approaches to address the issue positively.
- Approach discussions with a **mindset of collaboration and problem-solving**.
- Be **open to different perspectives**, as contributors may have different
viewpoints, experiences, and expertise levels.
- Contribute to a **positive and welcoming community atmosphere**.

#### 8.2.2 Managing Issues and Pull Requests

Our team is committed to managing issues and pull requests related to this
document in a transparent and efficient manner to ensure that all feedback is
addressed promptly and effectively. Here's how we manage issues and pull
requests to set the right expectations:

- Issue Management: When an issue is submitted, our team will review and
prioritise it based on its relevance and impact. We'll keep you informed of the
status of your issue and provide updates as it progresses. Once resolved, we'll
close the issue and incorporate any necessary changes into the document.
- Pull Request Management: If you submit a pull request with proposed changes or
improvements to the document, our team will review it carefully and provide
feedback and suggestions for refinement. We'll work collaboratively with you to
ensure that your contribution aligns with our document's objectives and
maintains consistency and quality. Once approved, we'll merge your changes into
the document and acknowledge your contribution.

Your feedback and contributions are essential in helping us maintain the quality
and relevance of this document. We value your participation and strive to create
a collaborative environment where everyone's contributions are valued and
recognised.

### 8.3 Document Versioning

To avoid interoperability issues and changes to the ARF going unnoticed, a
version control system and the following semantic versioning scheme
(<https://semver.org>) will be used for the ARF.

The ARF document will be published under a standardised release versioning
format, *MAJOR.MINOR.PATCH*, where:

**MAJOR** version is incremented (i.e., new version), when the ARF document has
*undergone significant changes, for example introducing some breaking changes in
*the architecture,

**MINOR** version is incremented when new information has been added to the
*document or information has been removed from the document, and

**PATCH** version is incremented when minor changes have been made (e.g., fixing
*typos).

## 9 References

For undated references, the latest version available applies.

| **Item Reference** | **Standard name/details**|
|--------------------|---------------------------|
| [2015/1505] | [COMMISSION IMPLEMENTING DECISION (EU) 2015/1505](https://eur-lex.europa.eu/legal-content/EN/TXT/HTML/?uri=CELEX:32015D1505) of 8 September 2015 laying down technical specifications and formats relating to trusted lists pursuant to Article 22(5) of Regulation (EU) No 910/2014 of the European Parliament and of the Council on electronic identification and trust services for electronic transactions in the internal market. |
| [European Digital Identity Regulation] | [Regulation (EU) 2024/1183](https://eur-lex.europa.eu/legal-content/EN/TXT/HTML/?uri=OJ:L_202401183) of the European Parliament and of the Council of 11 April 2024 amending Regulation (EU) No 910/2014 as regards establishing the European Digital Identity Framework |
| [Risk Register] | [Regulation (EU) 2024/2981, Annex I](https://eur-lex.europa.eu/legal-content/EN/TXT/HTML/?uri=OJ:L_202402981#anx_I) of 28 November 2024 laying down rules for the application of Regulation (EU) No 910/2014 of the European Parliament and the Council as regards the certification of European Digital Identity Wallets |
| [CIR 2024/2977] | [Commission Implementing Regulation 2024/2977](https://eur-lex.europa.eu/legal-content/EN/TXT/HTML/?uri=OJ:L_202402977) of 28 November 2024 laying down rules for the application of Regulation (EU) No 910/2014 of the European Parliament and of the Council as regards person identification data and electronic attestations of attributes issued to European Digital Identity Wallets |
| [CIR 2024/2979] | [Commission Implementing Regulation 2024/2979](https://eur-lex.europa.eu/legal-content/EN/TXT/HTML/?uri=OJ:L_202402979) of 28 November 2024 laying down rules for the application of Regulation (EU) No 910/2014 of the European Parliament and of the Council as regards the integrity and core functionalities of European Digital Identity Wallets |
| [CIR 2024/2980] | [Commission Implementing Regulation 2024/2980](https://eur-lex.europa.eu/legal-content/EN/TXT/HTML/?uri=OJ:L_202402980) of 28 November 2024 laying down rules for the application of Regulation (EU) No 910/2014 of the European Parliament and of the Council as regards notifications to the Commission concerning the European Digital Identity Wallet ecosystem |
| [CIR 2024/2981] | [Commission Implementing Regulation (EU) 2024/2981](https://eur-lex.europa.eu/legal-content/EN/TXT/HTML/?uri=OJ:L_202402981) of 28 November 2024 laying down rules for the application of Regulation (EU) No 910/2014 of the European Parliament and the Council as regards the certification of European Digital Identity Wallets |
| [CIR 2024/2982] | [Commission Implementing Regulation 2024/2982](https://eur-lex.europa.eu/legal-content/EN/TXT/HTML/?uri=OJ:L_202402982) of 28 November 2024 laying down rules for the application of Regulation (EU) No 910/2014 of the European Parliament and of the Council as regards protocols and interfaces to be supported by the European Digital Identity Framework |
| [ISO/IEC 18013-5] | [ISO/IEC 18013-5](https://github.com/eu-digital-identity-wallet/eudi-doc-standards-and-technical-specifications/issues/84), Personal identification --- ISO-compliant driving licence - Part 5: Mobile driving licence (mDL) application |
| [ISO/IEC 18013-7] | [ISO/IEC 18013-7](https://github.com/eu-digital-identity-wallet/eudi-doc-standards-and-technical-specifications/issues/1), Personal identification --- ISO-compliant driving licence - Part 7: Mobile driving licence (mDL) add-on functions |
| [ISO/IEC 23220-2] |  [ISO/IEC 23220-2](https://www.iso.org/standard/86782.html), --- Cards and security devices for personal identification — Building blocks for identity management via mobile devices - Part 2: Data objects and encoding rules for generic eID systems |
| [ISO 3166-1] | [ISO 3166-1](https://github.com/eu-digital-identity-wallet/eudi-doc-standards-and-technical-specifications/issues/39): Codes for the representation of names of countries and their subdivisions -- Part 1: Country codes: alpha-2 country |
| [ISO 3166-2] | [ISO 3166-2:2020](https://github.com/eu-digital-identity-wallet/eudi-doc-standards-and-technical-specifications/issues/40): Codes for the representation of names of countries and their subdivisions --- Part 2: Country subdivision code |
| [ETSI TS 119 612]| [ETSI TS 119 612](https://github.com/eu-digital-identity-wallet/eudi-doc-standards-and-technical-specifications/issues/41): Electronic Signatures and Infrastructures (ESI); Trusted Lists |
| [ETSI TS 119 431-1]| [ETSI TS 119 431-1](https://github.com/eu-digital-identity-wallet/eudi-doc-standards-and-technical-specifications/issues/66) - Electronic Signatures and Infrastructures (ESI); Policy and security requirements for trust service providers; Part 1: TSP service components operating a remote QSCD / SCDev. |
| [ETSI TS 119 431-2]| [ETSI TS 119 431-2](https://github.com/eu-digital-identity-wallet/eudi-doc-standards-and-technical-specifications/issues/67) - Electronic Signatures and Infrastructures (ESI); Policy and security requirements for trust service providers; Part 2: TSP service components supporting AdES digital signature creation |
| [ETSI TS 119 432]| [ETSI TS 119 432](https://github.com/eu-digital-identity-wallet/eudi-doc-standards-and-technical-specifications/issues/68) - Electronic Signatures and Infrastructures (ESI); Protocols for remote digital signature creation |
| [ETSI EN 319 132-1]| [ETSI EN 319 132-1](https://github.com/eu-digital-identity-wallet/eudi-doc-standards-and-technical-specifications/issues/70) - Electronic Signatures and Infrastructures (ESI); XAdES digital signatures; Part 1: Building blocks and XAdES baseline signatures (XAdES) |
| [ETSI TS 119 182-1]| [ETSI TS 119 182-1](https://github.com/eu-digital-identity-wallet/eudi-doc-standards-and-technical-specifications/issues/71) - Electronic Signatures and Infrastructures (ESI); JAdES digital signatures; Part 1: Building blocks and JAdES baseline signatures |
| [ETSI EN 319 122-1]| [ETSI EN 319 122-1](https://github.com/eu-digital-identity-wallet/eudi-doc-standards-and-technical-specifications/issues/72) - Electronic Signatures and Infrastructures (ESI); CAdES digital signatures; Part 1: Building blocks and CAdES baseline signatures |
| [ETSI EN 319 162-1]| [ETSI EN 319 162-1](https://github.com/eu-digital-identity-wallet/eudi-doc-standards-and-technical-specifications/issues/73) - Electronic Signatures and Infrastructures (ESI); Associated Signature Containers (ASiC); Part 1: Building blocks and ASiC baseline containers |
| [ETSI EN 319 142] | [ETSI EN 319 142-1](https://github.com/eu-digital-identity-wallet/eudi-doc-standards-and-technical-specifications/issues/69) - Electronic Signatures and Infrastructures (ESI); PAdES digital signatures; Part 1: Building blocks and PAdES baseline signatures |
| [CEN EN 419 241-1]| [CEN EN 419 241-1](https://github.com/eu-digital-identity-wallet/eudi-doc-standards-and-technical-specifications/issues/101) -- Trustworthy Systems Supporting Server Signing - Part 1: General System Security Requirements |
| [SD-JWT VC] | [SD-JWT-based Verifiable Credentials](https://github.com/eu-digital-identity-wallet/eudi-doc-standards-and-technical-specifications/issues/9) (SD-JWT VC). Retrievable from: <https://datatracker.ietf.org/doc/draft-ietf-oauth-sd-jwt-vc/> |
| [RFC 2119] | [RFC 2119](https://github.com/eu-digital-identity-wallet/eudi-doc-standards-and-technical-specifications/issues/74) - Key words for use in RFCs to Indicate Requirement Levels. S. Bradner, March 1997. |
| [RFC 3339] | [RFC 3339](https://github.com/eu-digital-identity-wallet/eudi-doc-standards-and-technical-specifications/issues/75) - Date and Time on the Internet: Timestamps, G. Klyne et al., July 2002 |
| [RFC 4122] | [RFC 9562](https://github.com/eu-digital-identity-wallet/eudi-doc-standards-and-technical-specifications/issues/324) - Universally Unique IDentifiers (UUIDs), P. Leach et al., May 2024 |
| [RFC 5280] | [RFC 5280](https://github.com/eu-digital-identity-wallet/eudi-doc-standards-and-technical-specifications/issues/77) - Internet X.509 Public Key Infrastructure Certificate and Certificate Revocation List (CRL) Profile, D. Kooper et al., May 2008 |
| [RFC 3647] | [RFC 3647](https://github.com/eu-digital-identity-wallet/eudi-doc-standards-and-technical-specifications/issues/78) - Internet X.509 Public Key Infrastructure Certificate Policy and Certification Practices Framework, S. Chokhani et al., November 2003 |
| [RFC 7519] | [RFC 7519](https://github.com/eu-digital-identity-wallet/eudi-doc-standards-and-technical-specifications/issues/312) - JSON Web Token (JWT), M. Jones et al., May 2015 |
| [RFC 8259] | [RFC 8259](https://github.com/eu-digital-identity-wallet/eudi-doc-standards-and-technical-specifications/issues/79) - The JavaScript Object Notation (JSON) Data Interchange Format, T. Bray, Ed., December 2017 |
| [RFC 8610] | [RFC 8610](https://github.com/eu-digital-identity-wallet/eudi-doc-standards-and-technical-specifications/issues/80) - Concise Data Definition Language (CDDL): A Notational Convention to Express Concise Binary Object Representation (CBOR) and JSON Data Structures, H. Birkholz et al., June 2019 |
| [RFC 8943] | [RFC 8943](https://github.com/eu-digital-identity-wallet/eudi-doc-standards-and-technical-specifications/issues/81) - Concise Binary Object Representation (CBOR) Tags for Date, M. Jones et al., November 2020 |
| [RFC 8949] | [RFC 8949](https://github.com/eu-digital-identity-wallet/eudi-doc-standards-and-technical-specifications/issues/82) - Concise Binary Object Representation (CBOR), C. Bormann et al., December 2020 |
| [CSC API] | [Cloud Signature Consortium API Specification v2.0](https://github.com/eu-digital-identity-wallet/eudi-doc-standards-and-technical-specifications/issues/29), 20 April 2023 |
| [GP OMAPI] | GPD_SPE_075 [Open Mobile API Specification](https://github.com/eu-digital-identity-wallet/eudi-doc-standards-and-technical-specifications/issues/248), v3.3, July 2018, GlobalPlatform |
| [GP CS] | GPC_SPE_034 [Card Specification](https://github.com/eu-digital-identity-wallet/eudi-doc-standards-and-technical-specifications/issues/243), v2.3.1, March 2018, GlobalPlatform |
| [GSMA SAM] | [GSMA Secured Applications for Mobile](https://github.com/eu-digital-identity-wallet/eudi-doc-standards-and-technical-specifications/issues/241), v1.1, 03 November 2023, GSM Association |
| [W3C VCDM v2.0] | Sporny, M. *et al,* [Verifiable Credentials Data Model v2.0](https://github.com/eu-digital-identity-wallet/eudi-doc-standards-and-technical-specifications/issues/115), W3C Proposed Recommendation |
| [W3C VC-JOSE-COSE] | Jones, M. *et al,* "[Securing Verifiable Credentials using JOSE and COSE](https://www.w3.org/TR/vc-jose-cose/)", W3C Proposed Recommendation |
| [W3C VC Data Integrity] | Sporny, M. *et al,* [Verifiable Credential Data Integrity 1.0](https://www.w3.org/TR/vc-data-integrity/), W3C Proposed Recommendation |
| [W3C Digital Credentials API] | Caceres, M., Cappalli, T., Goto, S. *et al,* "[Digital Credentials API](https://github.com/eu-digital-identity-wallet/eudi-doc-standards-and-technical-specifications/issues/10)", Draft Community Group Report |
| [W3C WebAuthn] | Jeff Hodges *et al,* [Web Authentication](https://github.com/eu-digital-identity-wallet/eudi-doc-standards-and-technical-specifications/issues/314), An API for accessing Public Key Credentials Level 2, W3C Recommendation |
| [CTAP] | Client to Authenticator Protocol (CTAP) Review Draft, March 21, 2023. Available: <https://github.com/eu-digital-identity-wallet/eudi-doc-standards-and-technical-specifications/issues/365> |
| [OpenID4VCI]| Lodderstedt, T. et al., "[OpenID for Verifiable Credential Issuance](https://github.com/eu-digital-identity-wallet/eudi-doc-standards-and-technical-specifications/issues/3)", OpenID Foundation. |
| [OpenID4VP] | Terbu, O. et al., "[OpenID Connect for Verifiable Presentations](https://github.com/eu-digital-identity-wallet/eudi-doc-standards-and-technical-specifications/issues/2)", OpenID Foundation.  |
| [OIDC] | Sakimura, N. et al., "OpenID Connect Core 1.0", OpenID Foundation. Available: <https://openid.net/specs/openid-connect-core-1_0.html> |
| [EKYC] | Lodderstedt, T. et al., "OpenID Connect for Identity Assurance Claims Registration 1.0", OpenID Foundation. Available: <https://openid.net/specs/openid-connect-4-ida-claims-1_0-final.html> |
| [EKYC Schema] | Lodderstedt, T. et al., "OpenID Identity Assurance Schema Definition 1.0", OpenID Foundation. Available: <https://openid.net/specs/openid-ida-verified-claims-1_0-final.html> |
| [HAIP] | Yasuda, K. et al, "[OpenID4VC High Assurance Interoperability Profile](https://github.com/eu-digital-identity-wallet/eudi-doc-standards-and-technical-specifications/issues/4)", OpenId Foundation. |
| [IANA-JWT-Claims] | IANA JSON Web Token Claims Registry. Available: <https://www.iana.org/assignments/jwt/jwt.xhtml> |
| [[Topic 6](annexes/annex-2/annex-2-high-level-requirements.md#a236-topic-6---relying-party-authentication-and-user-approval)]| Annex 2 - Relying Party authentication and User approval |
| [[Topic 7](annexes/annex-2/annex-2-high-level-requirements.md#a237-topic-7---attestation-revocation-and-revocation-checking)] | Annex 2 - Attestation revocation and revocation checking |
| [[Topic 9](annexes/annex-2/annex-2-high-level-requirements.md#a239-topic-9---wallet-unit-attestation)] | Annex 2 - Wallet Unit Attestation |
| [[Topic 10](annexes/annex-2/annex-2-high-level-requirements.md#a2310-topic-10---issuing-a-pid-or-attestation-to-a-wallet-unit)] | Annex 2 -Issuing a PID or attestation to a Wallet Unit |
| [[Topic 11](annexes/annex-2/annex-2-high-level-requirements.md#a2311-topic-11---pseudonyms)] | Annex 2 - Pseudonyms |
| [[Topic 12](annexes/annex-2/annex-2-high-level-requirements.md#a2312-topic-12---attestation-rulebooks)] | Annex 2 - Attestation Rulebooks |
| [[Topic 16](annexes/annex-2/annex-2-high-level-requirements.md#a2316-topic-16---signing-documents-with-a-wallet-unit)] | Annex 2 - Signing documents with a Wallet Unit |
| [[Topic 18](annexes/annex-2/annex-2-high-level-requirements.md#a2318-topic-18---combined-presentations-of-attributes)] | Annex 2 - Combined presentations of attributes |
| [[Topic 19](annexes/annex-2/annex-2-high-level-requirements.md#a2319-topic-19---user-navigation-requirements-dashboard-logs-for-transparency)] | Annex 2 - User Navigation requirements (Dashboard logs for transparency) |
| [[Topic 23](annexes/annex-2/annex-2-high-level-requirements.md#a2323-topic-23---pid-issuance-and-qeaa-issuance)] | Annex 2 - PID issuance and (Q)EAA issuance |
| [[Topic 25](annexes/annex-2/annex-2-high-level-requirements.md#a2325-topic-25---unified-definition-and-controlled-vocabularies-for-attributes)] | Annex 2 - Unified definition and controlled vocabularies for attributes |
| [[Topic 26](annexes/annex-2/annex-2-high-level-requirements.md#a2326-topic-26---catalogue-of-attestations)] | Annex 2 - Catalogue of attestations |
| [[Topic 27](annexes/annex-2/annex-2-high-level-requirements.md#a2327-topic-27---registration-of-pid-providers-providers-of-qeaas-pub-eaas-and-non-qualified-eaas-and-relying-parties)] | Annex 2 - Registration of PID Providers, Providers of QEAAs, PuB-EAAs, and (non-qualified) EAAs, and Relying Parties |
| [[Topic 30](annexes/annex-2/annex-2-high-level-requirements.md#a2330-topic-30---interaction-between-wallet-units)] | Annex 2 - Interaction between Wallet Units |
| [[Topic 31](annexes/annex-2/annex-2-high-level-requirements.md#a2331-topic-31---pid-provider-wallet-provider-attestation-provider-and-access-certificate-authority-notification-and-publication)] | Annex 2 - PID Provider, Wallet Provider, Attestation Provider, and Access Certificate Authority notification and publication |
| [[Topic 33](annexes/annex-2/annex-2-high-level-requirements.md#a2333-topic-33---wallet-unit-backup-and-restore)] | Annex 2 - Wallet Unit backup and restore |
| [[Topic 34](annexes/annex-2/annex-2-high-level-requirements.md#a2334-topic-34---migrate-to-a-different-wallet-solution)] | Annex 2 - Migrate to a different Wallet solution |
| [[Topic 37](annexes/annex-2/annex-2-high-level-requirements.md#a2337-topic-37---qes----remote-signing---technical-requirements)] | Annex 2 - QES -- Remote Signing - Technical Requirements |
| [[Topic 38](annexes/annex-2/annex-2-high-level-requirements.md#a2338-topic-38---wallet-unit-revocation)] | Annex 2 - Wallet Unit revocation |
| [[Topic 42](annexes/annex-2/annex-2-high-level-requirements.md#a2342-topic-42---requirements-for-qtsps-to-access-authentic-sources)] | Annex 2 - Requirements for QTSPs to access Authentic Sources |
| [[Topic 43](annexes/annex-2/annex-2-high-level-requirements.md#a2343-topic-43---embedded-disclosure-policies)] | Annex 2 - Embedded disclosure policies |
| [[Topic 44](annexes/annex-2/annex-2-high-level-requirements.md#a2344-topic-44---relying-party-registration-certificates)] | Annex 2 - Relying Party registration certificates |
| [[Topic 48](annexes/annex-2/annex-2-high-level-requirements.md#a2348-topic-48---blueprint-for-requesting-data-deletion-to-relying-parties)] | Annex 2 - Blueprint for requesting data deletion to Relying Parties |
| [[Topic 50](annexes/annex-2/annex-2-high-level-requirements.md#a2350-topic-50---blueprint-to-report-unlawful-or-suspicious-request-of-data)] | Annex 2 - Blueprint to report unlawful or suspicious request of data |
| [[Topic 51](annexes/annex-2/annex-2-high-level-requirements.md#a2351-topic-51---pid-or-attestation-deletion)] | Annex 2 - PID or attestation deletion |
| [[Topic 52](annexes/annex-2/annex-2-high-level-requirements.md#a2352-topic-52-relying-party-intermediaries)] | Annex 2 - Relying Party intermediaries |

## 10 Annexes

- Definitions - [Annex 1](./annexes/annex-1/annex-1-definitions.md)
- High Level Technical Requirements - [Annex 2](./annexes/annex-2/annex-2-high-level-requirements.md)
- Rulebooks - Annex 3:
    - PID Rulebook - [Annex 3.1](./annexes/annex-3/annex-3.01-pid-rulebook.md)
    - mDL Rulebook - [Annex 3.2](./annexes/annex-3/annex-3.02-mDL-rulebook.md)
- Service Blueprints - Annex 4:
    - Blueprint Initialisation and activation - [Annex 4.1](./annexes/annex-4/annex-4.01-eudi-wallet-initialisation-and-activation.pdf)
    - Blueprint Online identification and authentication - [Annex 4.2](./annexes/annex-4/annex-4.02-eudi-wallet-online-identification-and-authentication.pdf)
    - Blueprint Issuing mDL - [Annex 4.3](./annexes/annex-4/annex-4.03-eudi-wallet-issuing-mdl.pdf)
    - Blueprint Presenting mDL (proximity-supervised) - [Annex 4.4](./annexes/annex-4/annex-4.04-eudi-wallet-presenting-mdl-proximity-supervised.pdf)
    - Blueprint Presenting mDL (proximity-unsupervised) - [Annex 4.5](./annexes/annex-4/annex-4.05-eudi-wallet-presenting-mdl-proximity-unsupervised.pdf)
    - Blueprint Remote QES -- Creating a signature for authentication /
    authorisation - [Annex 4.6](./annexes/annex-4/annex-4.06-Remote-qes-creating-a-signature-eudi-wallet-used-for-authentication-authorisation.pdf)
    - Blueprint Remote QES - Enrolment - [Annex 4.7](./annexes/annex-4/annex-4.07-remote-qes-enrolment.pdf)
    - Blueprint Remote QES - Creating a signature channelled by a Wallet Unit -
    [Annex 4.8](./annexes/annex-4/annex-4.08-remote-qes-creating-a-signature-channeled-by-eudi-wallet.pdf)
    - Blueprint Remote QES - Creating a signature channelled by Relying Party -
    [Annex 4.9](./annexes/annex-4/annex-4.09-remote-qes-creating-a-signature-channeled-by-relying-party.pdf)
    - Blueprint QES -- View history of signatures - [Annex 4.10](./annexes/annex-4/annex-4.10-qes-view-history-of-signatures.pdf)
    - Blueprint Local QES - Enrolment - [Annex 4.11](./annexes/annex-4/annex-4.11-local-qes-enrolment.pdf)
    - Blueprint Local QES -- Creating a signature - [Annex 4.12](./annexes/annex-4/annex-4.12-local-qes-creating-a-signature.pdf)
- Design Guides - Annex 5:
    - Wallet Unit design guide - [Annex 5.1](./annexes/annex-5/annex-5.01-design-guide.pdf)
    - Wallet Unit design guide -- data sharing scenarios - [Annex 5.2](./annexes/annex-5/annex-5.02-design-guide-data-sharing-scenarios.pdf)

    ---
    title: "European Digital Identity Wallet"
    subtitle: "ARF Annex 1 - Definitions"
    ...

    # ANNEX 1 - Definitions

    ## A.1 Introduction

    In the Architecture Reference Framework (ARF) many terms are used that need a
    precise definition. This Annex contains the definitions of these terms.

    In fact, there are three sources for these definitions:

    - In the first place, the [European Digital Identity Regulation] defines several
    of these terms. For convenience, these definitions are listed in [Section A.2](#a2-definitions-from-the-european-digital-identity-regulation).
    - Secondly, the adopted Commission Implementing Regulations [CIR
    2024/2977](https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=CELEX:32024R2977),
    [CIR 2024/2979](https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=OJ:L_202402979),
    [CIR 2024/2980](https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=OJ:L_202402980),
    [CIR 2024/2981](https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=OJ:L_202402981),
    and [CIR 2024/2982](https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=OJ:L_202402982)
    also contain a list of definitions. Again for convenience, these definitions are
    included in [Section A.3](#a3-definitions-from-the-adopted-commission-implementing-regulations)
    - Thirdly, in writing the ARF, additional technical terms and corresponding
    definitions are used. These are listed in [Section A.4](#a4-additional-definitions-used-in-the-arf).

    ## A.2 Definitions from the [European Digital Identity Regulation]

    The following terms are defined in the [European Digital Identity Regulation]
    and used in the ARF.

    | **Term** | **Definition in [European Digital Identity Regulation]** |
    |-----------|-----------|
    | **Electronic attestation of attributes (EAA)** | An attestation in electronic form that allows attributes to be authenticated. |
    | **Attribute** | A characteristic, quality, right or permission of a natural or legal person or of an object. |
    | **Authentic Source** | A repository or system, held under the responsibility of a public sector body or private entity, that contains and provides attributes about a natural or legal person or object and that is considered to be a primary source of that information or recognised as authentic in accordance with Union law or national law, including administrative practice. |
    | **Authentication** | An electronic process that enables the confirmation of the electronic identification of a natural or legal person or the confirmation of the origin and integrity of data in electronic form. |
    | **Conformity Assessment Body (CAB)** | A conformity assessment body as defined in [Article 2, point 13, of Regulation (EC) No 765/2008](https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=celex:32008R0765#d1e497-30-1), which is accredited in accordance with that Regulation as competent to carry out conformity assessment of a qualified trust service provider and the qualified trust services it provides, or as competent to carry out certification of European Digital Identity Wallets or electronic identification means. |
    | **Electronic attestation of attributes issued by or on behalf of a public sector body (PuB-EAA)** | An electronic attestation of attributes issued by a public sector body that is responsible for an authentic source or by a public sector body that is designated by the Member State to issue such attestations of attributes on behalf of the public sector bodies responsible for authentic sources in accordance with [Article 45f](https://eur-lex.europa.eu/legal-content/EN/ALL/?uri=CELEX:32024R1183#d1e3902-1-1) and with [Annex VII](https://eur-lex.europa.eu/legal-content/EN/ALL/?uri=CELEX:32024R1183#d1e40-56-1). |
    | **Electronic identification scheme** | A system for electronic identification under which electronic identification means are issued to natural or legal persons or natural persons representing other natural persons or legal persons. |
    | **(Electronic) signature** | Data in electronic form which is attached to or logically associated with other data in electronic form and which is used by the signatory to sign. |
    | **(Electronic) seal** | Data in electronic form which is attached to or logically associated with other data in electronic form to ensure the latter’s origin and integrity |
    | **User** | A natural or legal person, or a natural person representing another natural person or a legal person, that uses trust services or electronic identification means provided in accordance with the [European Digital Identity Regulation]. |
    | **Person Identification Data (PID)** | A set of data that is issued in accordance with Union or national law and that enables the establishment of the identity of a natural or legal person, or of a natural person representing another natural person or a legal person. |
    | **Qualified Electronic Attestation of Attributes (QEAA)** | An electronic attestation of attributes which is issued by a qualified trust service provider and meets the requirements laid down in [Annex V](https://eur-lex.europa.eu/legal-content/EN/ALL/?uri=CELEX:32024R1183#d1e46-54-1). |
    | **Qualified Electronic Signature (QES)** | An advanced electronic signature that is created by a qualified electronic signature creation device, and which is based on a qualified certificate for electronic signatures. |
    | **Qualified Electronic Signature Creation Device (QSCD)** | Configured software or hardware used to create an electronic signature that meets the requirements laid down in [Annex II](https://eur-lex.europa.eu/legal-content/EN/ALL/?uri=CELEX:32024R1183#d1e38-51-1) of the [European Digital Identity Regulation]. |
    | **Qualified Trust Service Provider (QTSP)** | Qualified Trust Service Provider means a trust service provider who provides one or more qualified trust services and is granted the qualified status by the supervisory body. |
    |**Relying Party** | A natural or legal person that relies upon electronic identification, European Digital Identity Wallets or other electronic identification means, or upon a trust service |
    | **Public Sector Body** | A state, regional or local authority, a body governed by public law or an association formed by one or several such authorities or one or several such bodies governed by public law, or a private entity mandated by at least one of those authorities, bodies or associations to provide public services, when acting under such a mandate. |

    **Table 1: Definition of terms used in the ARF originating from
    the [European Digital Identity Regulation]**

    ## A.3 Definitions from the adopted Commission Implementing Regulations

    The following terms are defined in the adopted Commission Implementing
    Regulations and used in the ARF. Note that small differences exist in the way in
    which terms are written, for example regarding capitalisation. The table
    contains the term as used in the ARF.

    | **Term** | **Definition** |
    |-----------|-----------|
    | (Wallet) User | A user who is in control of the Wallet Unit |
    | Wallet Unit | A unique configuration of a Wallet Solution that includes Wallet instances, Wallet Secure Cryptographic Applications and Wallet Secure Cryptographic Devices provided by a Wallet Provider to an individual Wallet User |
    | Wallet Solution | A combination of software, hardware, services, settings, and configurations, including Wallet Instances, one or more Wallet Secure Cryptographic Applications and one or more Wallet Secure Cryptographic Devices |
    | Provider of person identification data (PID Provider) | A natural or legal person responsible for issuing and revoking the person identification data and ensuring that the person identification data of a user is cryptographically bound to a Wallet Unit |
    | Wallet Unit Attestation (WUA) | A data object that describes the components of the Wallet Unit or allows authentication and validation of those components; |
    | Embedded disclosure policy | A set of rules, embedded in an electronic attestation of attributes by its provider, that indicates the conditions that a wallet-relying party has to meet to access the electronic attestation of attributes |
    | Registrar (of wallet-relying parties) | The body responsible for establishing and maintaining the list of registered wallet-relying parties established in their territory who has been designated by a Member State |
    | Wallet Instance | The application installed and configured on a Wallet User’s device or environment, which is part of a Wallet Unit, and that the Wallet User uses to interact with the Wallet Unit |
    | Wallet Secure Cryptographic Application (WSCA) | An application that manages critical assets by being linked to and using the cryptographic and non-cryptographic functions provided by the Wallet Secure Cryptographic Device |
    | Wallet Secure Cryptographic Device (WSCD) | A tamper-resistant device that provides an environment that is linked to and used by the Wallet Secure Cryptographic Application to protect critical assets and provide cryptographic functions for the secure execution of critical operations |
    | Wallet Provider | A natural or legal person who provides Wallet Solutions |
    | critical assets | Assets within or in relation to a Wallet Unit of such extraordinary importance that where their availability, confidentiality or integrity are compromised, this would have a very serious, debilitating effect on the ability to rely on the Wallet Unit |
    | (Wallet-) Relying Party | A Relying Party that intends to rely upon Wallet Units for the provision of public or private services by means of digital interaction |
    | (Wallet-relying party) access certificate | A certificate for electronic seals or signatures authenticating and validating the (Wallet-) Relying Party, issued by a provider of wallet-relying party access certificates |
    | Provider of wallet-relying party access certificates (Access Certificate Authority, Access CA) | A natural or legal person mandated by a Member State to issue Relying Party access certificates to (Wallet-) Relying Parties registered in that Member State. |
    | (Wallet-relying party) registration certificate | A data object that indicates the attributes the Relying Party has registered to intend to request from Users |

    ## A.4 Additional definitions used in the ARF

    Note: The technical terms and definitions in Table 3 below are intended to be
    defined in such a way that they are aligned with the definitions used in the
    [European Digital Identity Regulation] and the Commission Implementing
    Regulations in Tables 1 and 2, and should be interpreted as such. In case any
    definition in Table 3 contradicts a definition from the [European Digital
    Identity Regulation] or the Commission Implementing Regulations, the latter take
    precedence.

    In some cases, a term has its origin in the context of
    a specific Topic in [Annex 2](../annex-2/annex-2-high-level-requirements.md). In
    such a case, the topic number appears in brackets following the definition. If
    the definition relies on an external source, such as a
    standard or a formal publication, that source is mentioned.

    | **Term** | **Definition** |
    |-----------|-----------|
    | Administrative validity period (of a PID or attestation) | The date(s) from and/or up to which the attributes in the attestation are valid, which are represented as attribute(s) in the attestation. *Note: Some attestations, for instance diplomas, do not have an administrative validity period* |
    | Attestation | When not further qualified, a collective term for a QEAA, PuB-EAA, or (non-qualified) EAA. |
    | Attestation Provider | When not further qualified, a collective term for QEAA Provider, PuB-EAA Provider, or (non-qualified) EAA Provider. |
    | Attestation Revocation List | A mechanism provided by a PID Provider or an Attestation Provider (or a trusted party acting on its behalf) for communicating the revocation status of PIDs and attestations, by publishing a list of identifiers of revoked PIDs or attestations. [Topic 7] |
    | Attestation Rulebook | A document describing the attestation type, namespace(s), and other features for a specific attestation type. [Topic 12] |
    | Attestation Status List | A mechanism provided by a PID Provider or an Attestation Provider (or a trusted party acting on its behalf) for communicating the revocation status of PIDs and attestations, by publishing status information (Valid or Invalid) for all relevant PIDs or attestations. [Topic 7] *Note: Which PIDs or attestations are relevant is determined by the entity publishing the status list. For example, a status list may contain all PIDs or attestations whose validity period is not over yet at the time of publication of the list.* |
    | Attestation type | An identifier for a type of attestation, unique within the context of the EUDI Wallet ecosystem [Topic 12] |
    | Certificate Authority (CA) | An entity which is trusted by one or more parties in the EUDI Wallet ecosystem to create and seal certificates. |
    | Certificate Policy (CP) | A named set of rules that indicates the applicability of a certificate to a particular community and/or class of application with common security requirements. |
    | Namespace | A specification of the attribute identifier, syntax and semantics of attributes that can be used in an attestation, having an identifier that is unique within the context of the EUDI Wallet ecosystem. [Topic 12] |
    | National Accreditation Bodies (NAB) | A body that performs accreditation with authority derived from a Member State under [Regulation (EC) No 765/2008](https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=celex:32008R0765). |
    | Notification | The act of transferring information to the European Commission. [Topics 31] |
    | Pseudonym | Data uniquely representing a user which in itself does not allow to infer any user's attribute or person identification data, without the use of additional information that is kept separately by the issuer of the data uniquely representing the user. |
    | Public Key Infrastructure (PKI) | Systems, software, and communication protocols that are used by EUDI Wallet ecosystem components to distribute, manage, and control public keys. A PKI publishes public keys and establishes trust within an environment by validating and verifying the public keys mapping to an entity. |
    | Qualified Electronic Signature Remote Creation Provider | A natural or a legal person that offers services related to the remote creation, validation, and management of qualified electronic signatures that meet legal requirements and standards in the [European Digital Identity Regulation] to be considered as legally equivalent to handwritten signatures. |
    | Relying Party Instance | A software and/or hardware module with the capability to interact with a Wallet Unit and to perform Relying Party authentication, that is controlled by a Relying Party. |
    | Selective Disclosure | The capability enabling the User to present a subset of the attributes included in a PID or attestation. |
    | Technical validity period (of a PID or attestation) | The dates (and possibly times) from and up to which the attestation is valid, which are represented as metadata of the attestation. *Note: All PIDs and attestations have a technical validity period, which is typically much shorter than its administrative validity period (if existent). The technical validity period is chosen based on a risk analysis, e.g. with regard to User privacy.* |
    | Trust Anchor | An authoritative entity represented by a public key and associated data. *Note: based on RFC 5914.* |
    | Trusted List | Repository of information about authoritative entities in a particular legal or contractual context which provides information about their current and historical status. |

    ---
title: "European Digital Identity Wallet"
subtitle: "Architecture and Reference Framework"
...

# ANNEX 2 - High-Level Requirements <!-- omit from toc -->

## A.2 High-level requirements

### A.2.1 Introduction

#### A.2.1.1 Overview

This annex to the [ARF main document](../../architecture-and-reference-framework-main.md)
includes high-level requirements (HLRs) related to the EUDI Wallet ecosystem.
The requirements define the responsible actor that should implement each
requirement. There are no requirements imposed on the Users.

All requirements in this Annex only apply in the context of the EUDI Wallet
ecosystem. Attestations that are not bound to Wallet Units, as described in
[Section 6.6.3.8 of the ARF main document](../../architecture-and-reference-framework-main.md#6638-relying-party-instance-verifies-device-binding), are not included in the scope of this Annex.

#### A.2.1.2 Key words

This Annex uses the capitalised key words 'SHALL', 'SHOULD' and 'MAY' as
specified in [RFC 2119](https://datatracker.ietf.org/doc/html/rfc2119), i.e., to
indicate requirements, recommendations and options specified in this annex.

In addition, 'must' (non-capitalised) is used to indicate an external
constraint, i.e., a requirement that is not mandated by this document,
but, for instance, by an external standard or specification. The word
'can' indicates a capability, whereas other words, such as 'will', and
'is' or 'are', are intended as statements of fact.

### A.2.2 Structure and order of presentation of the HLRs

Topics presented in [Section A.2.3](#a23-high-level-requirements) are ordered by
a Topic number.

Each Topic includes a short description, followed by the High-Level
Requirements (HLRs), identified by a unique identifier. The identifier
includes a prefix which signifies the context of the HLRs (e.g. ISSU
for issuance), an underscore and a numerator, e.g. ISSU_10.

### A.2.3 High-Level Requirements

#### A.2.3.1 Topic 1 - Accessing Online Services with a Wallet Unit

##### Description <!-- omit from toc -->

One of the main use cases of the EUDI Wallet ecosystem is to enable Users to access
online services and to enable Relying Parties offering such services to, where needed, identify
and authenticate Users with a high level of assurance. This essential
functionality ensures that Relying Parties can confidently verify that they are
interacting with the correct User.

Note: As specified in the [European Digital Identity Regulation], legally speaking, the term 'Relying Party' also include QEAA Providers, PuB-EAA Providers,
and non-qualified EAA Providers. However, for clarity this Annex uses the term 'Relying Party' exclusively in the meaning of a service provider interacting with a Wallet Unit to request and receive attributes from an attestation.

In this use case, a User is using their Wallet Unit to present attributes in order to access online services offered by Relying Parties. The User is concerned about presenting such attributes during online interactions. Their objectives include maintaining control
over the presentation of personal attributes from PIDs and attestations.

##### HLRs <!-- omit from toc -->

| **Index** | **Requirement specification** |
| -- | -- |
| OIA_01 | A Wallet Unit SHALL support technical specifications to respond to person identification data (PID) and attestation presentation requests by Relying Parties. |
| OIA_02 | A Wallet Unit SHALL support proving cryptographic binding between a WSCA included in the Wallet Unit and a PID or attestation, in accordance with [SD-JWT VC] or [ISO/IEC 18013-5]. *Note: Such a mechanism is called device binding in [ISO/IEC 18013-5] and key binding in [SD-JWT VC].* |
| OIA_03 | The Commission SHALL adopt the technical specifications for the PID or attestation presentation request-response protocol and for the device binding mechanism, according to the protocols and interfaces specified in [OpenID4VP] for remote flows, and [ISO 18013-5] for proximity flows. |
| OIA_03a | Wallet Providers SHALL ensure that their Wallet Solution supports the protocol specified in 'OpenID for Verifiable Presentations', see [OpenID4VP], with additions and changes as documented in this Annex and in future technical specifications created by or on behalf of the Commission. |
| OIA_03b | For remote presentation flows, when the format of the requested attestation complies with [ISO/IEC 18013-5], Relying Parties and Wallet Units SHALL comply with the requirements in the profile for OpenID4VP specified in [ISO/IEC 18013-7] Annex B. |
| OIA_03c | For remote presentation flows, when the format of the requested attestation complies with [SD-JWT VC], Relying Parties and Wallet Units SHALL comply with the requirements in the 'OpenID for Verifiable Presentations for IETF SD-JWT VC' profile specified in [HAIP]. |
| OIA_04 | A Wallet Unit SHALL verify and process PID or attestation presentation requests from Relying Parties in accordance with the protocols and interfaces specified in [OpenID4VP] for remote flows. |
| OIA_05 | After verifying and processing a PID or attestation request, the Wallet Unit SHALL display to the User the identity of the requesting Relying Party and the requested attributes. |
| OIA_06 | A Wallet Unit SHALL present the requested attributes only after having received the User's authorisation. See also OIA_07. |
| OIA_07 | A Wallet Unit SHALL support selective disclosure of attributes from PIDs and attestations to be released to the requesting Relying Parties. |
| OIA_08 | Wallet Units and Relying Party Instances SHALL support the [W3C Digital Credentials API]](<https://wicg.github.io/digital-credentials/>) for remote presentation flows, provided that a) this API is fully standardised, b) this API complies with the expectations outlined in [Chapter 3](../../discussion-topics/f-digital-credential-api.md#3) of the Topic F discussion paper, and c) this API is broadly supported by relevant browsers and operating systems. |
| OIA_08a | If Wallet Units and Relying Party Instances do not support the [W3C Digital Credentials API], they SHALL implement adequate mitigations for the challenges described in [Section 4.4.3.1](../../architecture-and-reference-framework-main.md#4431-introduction) of the ARF main document. |
| OIA_08b | If a Wallet Unit supports the [W3C Digital Credentials API], it SHALL disclose the presence of all stored attestations and attributes to the Digital Credentials API framework, but it SHALL NOT disclose the value of the attributes in these attestations. *Note: The latter restriction applies even if such disclosure would enhance the services provided by the operating system to the Wallet Unit, for example, attestation selection in the context of the Digital Credentials API.* |
| OIA_08c | If a Relying Party supports the [W3C Digital Credentials API], the Relying Party's presentation request MAY be processed by the browser for searching available attestations, for preventing fraud targeting the user, or for troubleshooting purposes. Moreover, the request SHOULD be processed by the browser for User security purposes. However, the request SHALL NOT be processed by the browser for market analysis purposes (including as a secondary purpose) or for the browser’s own purposes. |
| OIA_09 | For remote presentation flows the Wallet Unit SHALL ensure that the attributes included in the presented attestation are accessible only to the Relying Party Instance, by encrypting the presentation response. The technical specification meant in OIA_03a SHALL specify mechanisms preventing decryption of the presentation response via Man-in-the-Middle attacks by the browser, the operating system, or other components between the Wallet Unit and the Relying Party. |
| OIA_10 | For both proximity and remote presentation flows, if a Wallet Unit contains two PIDs having the same encoding (e.g. ISO/IEC 18013-5 or SD-JWT VC-compliant) and a Relying Party requests a PID, the Wallet Unit SHALL ask the User which of these PIDs they want to release, unless the Wallet Unit can decide from context. |
| OIA_11 | For both proximity and remote presentation flows, if a Wallet Unit contains two attestations having the same encoding (e.g. ISO/IEC 18013-5 or SD-JWT VC-compliant) and the same attestation type, and a Relying Party requests an attestation of that type and encoding, the Wallet Unit SHALL ask the User which of these attestations they want to release, unless the Wallet Unit can decide from context. *Note: Attestation types are explained in [[Topic 12](#a2312-topic-12---attestation-rulebooks)].* |
| OIA_12 | For both proximity and remote presentation flows, a Relying Party SHALL validate the signature of a PID using a trust anchor provided in a PID Provider Trusted List made available in accordance with [[Topic 31](#a2331-topic-31---pid-provider-wallet-provider-attestation-provider-and-access-certificate-authority-notification-and-publication)]. |
| OIA_13 | For both proximity and remote presentation flows, a Relying Party SHALL validate the qualified signature of a QEAA in accordance with Art.32 of the [European Digital Identity Regulation]. For the verification, the Relying Party SHALL use a trust anchor provided in a QEAA Provider Trusted List made available in accordance with [Art. 22](https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=uriserv%3AOJ.L_.2014.257.01.0073.01.ENG#d1e2162-73-1) of the [European Digital Identity Regulation]. |
| OIA_14 | For both proximity and remote presentation flows, a Relying Party SHALL validate the qualified signature of a PuB-EAA in accordance with [Art.32](https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=uriserv%3AOJ.L_.2014.257.01.0073.01.ENG#d1e2594-73-1) of the [European Digital Identity Regulation]. For that verification, the Relying Party SHALL use the public key provided in the qualified certificate of the QTSP supporting the qualified signature. The Relying Party SHALL also validate the qualified certificate of the QTSP using a trust anchor provided in a Trusted List made available in accordance with [Art. 22](https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=uriserv%3AOJ.L_.2014.257.01.0073.01.ENG#d1e2162-73-1) of the [European Digital Identity Regulation]. The Relying Party SHALL also verify the certified attributes of the qualified certificate, as specified in [Article 45f](https://eur-lex.europa.eu/legal-content/EN/ALL/?uri=CELEX:32024R1183#d1e3902-1-1). |
| OIA_15 | For both proximity and remote presentation flows, a Relying Party SHALL validate the signature of a non-qualified EAA using a trust anchor provided according to the mechanism(s) specified in the applicable Rulebook, see [[Topic 12](#a2312-topic-12---attestation-rulebooks)]. *Notes: - OIA_12 – OIA_15 imply that a Relying Party Instance must know if the attestation it is requesting from a Wallet Instance is a PID, a QEAA, a PuB-EAA, or a non-qualified EAA. These requirements also imply that the Relying Party Instance must store trust anchors in such a way that, at the time of verification, it is able to distinguish between trust anchors usable either for PIDs, for QEAAs, for PuB-EAAs, or for non-qualified EAAs. - PID Providers, QEAA Providers, and PuB-EAA Providers are trusted by other actors in the EUDI Wallet ecosystem to not fraudulently issue attestations (or PIDs) that they are not legally allowed to issue. This trust is warranted since these kinds of providers operate within a regulated framework and are regularly audited. However, non-qualified EAA Providers are unregulated and may not be completely trustworthy. Therefore, when it receives an non-qualified attestation, a Relying Party Instance may have to verify that the non-qualified EAA Provider is authorised or registered to issue this type of attestation, in addition to verifying the signature over the attestation using the EAA Provider's trust anchor. Mechanisms allowing to do this should be defined in the applicable Rulebook, see ARB_26.* |
| OIA_16 | When receiving a PID, attestation, or WUA, a Relying Party Instance SHALL discard the values of all unique elements, including at least the ones mentioned in requirement ISSU_35 in [Topic 10/23](#a2310-topic-10---issuing-a-pid-or-attestation-to-a-wallet-unit), as well as any timestamps, as soon as they are no longer needed. The Relying Party Instance SHALL NOT communicate these values to the Relying Party or to any other party inside or outside the EUDI Wallet ecosystem. |

#### A.2.3.2 Topic 2 - Mobile Driving Licence within the EUDI Wallet ecosystem

##### Description <!-- omit from toc -->

A User can obtain their mobile Driving Licence (mDL) from an mDL Provider and
store it in an Wallet Unit. The User can then present the mDL to a Relying Party
upon request to prove their driving rights conveniently, securely, and in
compliance with the Driving Licences Directive, once it is adopted.

This Topic contains high-level requirements related to a User presenting a
mobile Driving Licence (mDL) to a Relying Party in a supervised or unsupervised
scenario, and also in an unsupervised scenario, in proximity mode.

##### HLRs <!-- omit from toc -->

No high-level requirements are identified for this Topic, as the mDL is an
attestation that must comply with all relevant requirements in other Topics.

#### A.2.3.3 Topic 3 - PID Rulebook

##### Description <!-- omit from toc -->

The Person Identification Data (PID) Rulebook contains requirements specific to
the PID within the EUDI Wallet ecosystem.

The PID Rule Book contains the PID attribute schema, which describes the structure, the type, the identifiers, and the logical organisation of the mandatory and optional
attributes and metadata of the PID, as specified in Commission Implementing
Regulation (EU) 2024/2977. It also describes how Member States can specify any
possible national attributes. Two encodings for these attributes are specified,
one compliant with [ISO/IEC 18013-5], the other compliant with [SD-JWT VC].

For more information, see Annex 3 - [PID Rulebook].

##### A. Generic HLRs <!-- omit from toc -->

The requirements in the table below are valid for all PIDs in the EUDI Wallet
ecosystem, regardless of the encoding used.

| **Index** | **Requirement specification** |
|-----------|--------------|
| PID_01 | PIDs and PID Providers SHALL comply with all requirements in [PID Rulebook]. |
| PID_02 | A PID Provider SHALL issue any PID in both the format specified in ISO/IEC 18013-5 [ISO/IEC 18013-5] and the format specified in [SD-JWT VC]. *Note: CIR 2024/2977 mentions the W3C Verifiable Credentials Data Model v1.1 instead of [SD-JWT VC]. The latest stable version of this standard is [W3C VCDM 2.0].  However, W3C VCDM is not a complete specification of an attestation format. In particular, it does not specify a specific proof method to be used. Without additional specification, such as those in [W3C VC-JOSE-COSE] or [W3C VC Data Integrity], and making further choices, it is impossible to implement a PID based on W3C VCDM. This Rulebook considers [SD-JWT VC] to essentially be such an additional specification. See also [Section 5.3.4](../../architecture-and-reference-framework-main.md#534-w3c-verifiable-credentials) of the ARF main document.* |
| PID_03 | The portrait in a PID SHALL consist of a single portrait image in JPEG format. The portrait image SHALL comply with the quality requirements for a Full Frontal Image Type in ISO/IEC 19794-5 clauses 8.2, 8.3, and 8.4. However, the attribute portrait SHALL NOT comply with the format requirements in ISO/IEC 19794-5 clauses 8.1 and 8.5, meaning it SHALL NOT contain any of the headers or blocks specified in clause 5 except for the image data itself (a JPEG). |

##### B. HLRs for ISO/IEC 18013-5-compliant PIDs <!-- omit from toc -->

The requirements in the table below are valid for PIDs in the EUDI Wallet
ecosystem that are compliant with [ISO/IEC 18013-5].

| **Index** | **Requirement specification** |
|-----------|--------------|
| PID_04 | PID Providers SHALL use “eu.europa.ec.eudi.pid.1” as the attestation type for ISO/IEC 18013-5-compliant PIDs. *Notes: - This identifier uses the general format [Reverse Domain].[Domain Specific Extension]. Since the European Commission controls the domain ec.europa.eu, this attestation type identifier will not collide with any attestation type identifiers defined by other organisations in other Attestation Rulebooks. - The Commission may use the version number “1” in this identifier to distinguish between the first version of the PID, defined in the [PID Rulebook](../annex-3/annex-3.01-pid-rulebook.md), and any future version, which will then have an incremented version number.* |
| PID_05 | When issuing a PID compliant with [ISO/IEC 18013-5], a PID Provider SHALL use the value “eu.europa.ec.eudi.pid.1” for the identifier of the namespace for the PID attributes specified in [Section 4.2 of the PID Rulebook](../annex-3/annex-3.01-pid-rulebook.md#42-encoding-of-pid-attributes-and-metadata). *Notes: - The version number “1” allows for future extension(s) or change(s) of the ISO/IEC 18013-5-compliant PID attributes. - This namespace has the same value as the attestation type specified in requirement PID_04. This is allowed according to ISO/IEC 18013-5.* |
| PID_06 | When issuing a PID compliant with [ISO/IEC 18013-5], a PID Provider MAY include attributes that are not defined in the [PID Rulebook](../annex-3/annex-3.01-pid-rulebook.md). If so, these attributes SHALL be defined within a domestic PID namespace as meant in requirement ARB_10 in [Topic 12](#a2312-topic-12---attestation-rulebooks). The PID Provider SHALL generate the identifier for this domestic PID namespace by appending the applicable ISO 3166-1 alpha-2 country code or the ISO 3166-2 region code, separated by a period, to the PID namespace identifier specified in PID_05, excluding the version number. The PID Provider MAY include a version number in the domestic PID namespace identifier. *Note: For example, the identifier of the first domestic PID namespace for Germany could be “eu.europa.ec.eudi.pid.de.1”.* |
| PID_07 | A PID Provider that defines a domestic namespace SHALL publish the namespace, including all attribute identifiers, their definition, presence and encoding format, in an Attestation Rulebook complying with all applicable requirements in [Topic 12](#a2312-topic-12---attestation-rulebooks). |
| PID_08 | When issuing a PID compliant with [ISO/IEC 18013-5], a PID Provider SHALL include both the attributes and the metadata specified in CIR 2024/2977 in the PID as (issuer-signed or device-signed) data elements. *Note: This implies that technically speaking, there is no difference between these attributes and metadata.* |
| PID_09 | When issuing a PID compliant with [ISO/IEC 18013-5], a PID Provider SHALL encode each attribute or metadata in the PID as specified in the third column of the tables in [Section 4.2.1 of the PID Rulebook](../annex-3/annex-3.01-pid-rulebook.md#421-overview). |
| PID_10 | When issuing a PID compliant with [ISO/IEC 18013-5], a PID Provider SHALL encode each attribute or metadata in the PID in Concise Binary Object Representation (CBOR) according to [RFC 8949]. |
| PID_11 | When issuing a PID compliant with [ISO/IEC 18013-5], a PID Provider SHALL ensure that each PID contains at most one attribute with the same attribute identifier. |
| PID_12 | When issuing a PID compliant with [ISO/IEC 18013-5], a PID Provider SHALL ensure that the value of all attributes and metadata in the PID is valid at the value of the timestamp in the validFrom element in the MSO, see [ISO/IEC 18013-5] clause 9.1.2.4. *Note: The value of the age_over_18, age_over_NN, or age_in_years attributes, if present, changes whenever the User to whom the person identification data relates has a relevant birthday. The value of many other attributes will also change over time.* |
| PID_13 | When issuing a PID compliant with [ISO/IEC 18013-5], a PID Provider SHALL ensure that the issuance_date attribute, if present, is not later than the validFrom element in the MSO, see [ISO/IEC 18013-5] clause 9.1.2.4. |

##### C. HLRs for SD-JWT VC-compliant PIDs <!-- omit from toc -->

The requirements in the table below are valid for PIDs in the EUDI Wallet
ecosystem that are compliant with [SD-JWT VC].

| **Index** | **Requirement specification** |
|-----------|-------------------------------|
| PID_14 | A PID Provider issuing [SD-JWT VC]-compliant PIDs SHALL include the vct claim in their PIDs, where the vct claim SHALL be a URN within the `urn:eudi:pid:` namespace. The type indicated by the vct claim SHALL be `urn:eudi:pid:1` for the type defined in this document or a domestic type that extends it. |
| PID_15 | A catalog linked in the PID Rulebook SHALL associate all SD-JWT VC types for PIDs with SD-JWT VC type metadata which will include the same information as the PID Rulebook applicable to the type.  |
| PID_16 | A PID Provider that defines a domestic type SHALL publish information about the type, including all claim identifiers, their definition, presence and encoding format, in an Attestation Rulebook complying with all applicable requirements in [Topic 12](#a2312-topic-12---attestation-rulebooks). |
| PID_17 | When issuing a PID compliant with [SD-JWT VC], a PID Provider SHALL include both the attributes and the metadata specified in CIR 2024/2977 in the PID as claims. *Note: This implies that technically speaking, there is no difference between these attributes and metadata.* |
| PID_18 | When issuing a PID compliant with [SD-JWT VC], a PID Provider SHALL encode each attribute or metadata in the PID as specified in the tables in [Section 5.2 of the PID Rulebook](../annex-3/annex-3.01-pid-rulebook.md#52-encoding-of-pid-attributes). |
| PID_19 | When issuing a PID compliant with [SD-JWT VC], a PID Provider SHALL ensure that the value of all attributes and metadata in the PID is valid at the value of the timestamp in the nbf claim, if present. *Note: The value of the age-related claims, if present, changes whenever the User to whom the person identification data relates has a relevant birthday. The value of many other attributes will also change over time.* |
| PID_20 | When issuing a PID compliant with [SD-JWT VC], a PID Provider SHALL ensure that the date_of_issuance claim, if present, is not later than the value of the timestamp in the nbf claim, if present. |
| PID_21 | When issuing a PID compliant with [SD-JWT VC], a PID Provider SHALL make all claims (i.e., all top-level properties, all nested properties, and all array entries) selectively disclosable individually, except those claims defined as non-selectively disclosable in [SD-JWT VC]. |

#### A.2.3.4 Topic 4 - mDL Rulebook

##### Description <!-- omit from toc -->

The mobile driving licence (mDL) Rulebook contains requirements specific
to the mDL use case within the EUDI Wallet ecosystem.

Mobile driving licences are legally specified in the proposed EC
Regulation 2023_127 (4th Driving Licence Regulation). This Regulation
specifies that mDLs must comply with the ISO/IEC 18013-5 standard. It
does not mention any other standards, in particular not [SD-JWT VC].
Consequently, mDLs issued to a Wallet Unit will not be implemented
as [SD JWT VC]- compliant documents. The mDL Rulebook therefore specifies
only an ISO/IEC 18013-5 compliant encoding.

For more information, see Annex 3 - [mDL Rulebook].

##### HLRs <!-- omit from toc -->

| **Index** | **Requirement specification** |
|-----------|--------------|
| mDL_01 | mDLs and mDL Providers SHALL comply with all requirements in [mDL Rulebook]. |

#### A.2.3.5 Topic 5 - Wallet Unit Design Guide

There are no HLRs for this Topic.

#### A.2.3.6 Topic 6 - Relying Party authentication and User approval

##### Description <!-- omit from toc -->

Relying Party authentication is a process whereby a Relying Party proves
its identity to a Wallet Unit, in the context of a transaction in
which the Relying Party requests the Wallet Unit to release some
attributes.

To perform Relying Party authentication, the Wallet Unit verifies a
Relying Party Instance access certificate offered by the entity with which it
communicates, which is called a "Relying Party Instance". Note that
there could be multiple Relying Party Instances for each Relying Party.

The Wallet Unit communicates the outcome of Relying Party authentication to the
User when it requests the User for approval to present the requested attributes.
High-level requirements for User approval are also included in this Topic. The
Wallet Unit also communicates the outcome of the verification of the Relying
Party registration certificate, see
[Topic 44](#a2344-topic-44---relying-party-registration-certificates), and the outcome
of the evaluation of an embedded disclosure policy, if present, see
[Topic 43](#a2343-topic-43---embedded-disclosure-policies).

##### HLRs <!-- omit from toc -->

A. Relying Party authentication

| **Index** | **Requirement specification** |
|-----------|--------------|
| RPA_01 | The Wallet Unit used by a User, as well as the Relying Party Instance used by the Relying Party, SHALL implement a mechanism for Relying Party authentication. This mechanism SHALL: - enable the Wallet Unit to identify and authenticate the Relying Party, - enable the Wallet Unit to verify that the request from the Relying Party was not copied and replayed, - use Relying Party Instance access certificates issued in accordance with [[Topic 27](#a2327-topic-27---registration-of-pid-providers-providers-of-qeaas-pub-eaas-and-non-qualified-eaas-and-relying-parties)]. |
| RPA_01a | If a Wallet Unit supports the [W3C Digital Credentials API] for remote presentation flows, it SHALL retain full authority over the process meant in RPA_01. In particular, this process SHALL NOT be handled by a third party, including the browser and the operating system. |
| RPA_02 | The Commission SHALL ensure that technical specifications for the Relying Party authentication mechanism mentioned in RPA_01 are created both for Wallet Units complying with [ISO/IEC 18013-5] and for Wallet Units complying with [OpenID4VP]. These specifications SHALL comply with applicable requirements in these standards. |
| RPA_02a | The technical specifications mentioned in RPA_02 SHALL ensure that a Relying Party Instance includes its access certificates in the presentation request by value, not by reference. *Note: This ensures that no external requests are necessary to carry out Relying Party authentication, and that transactions are atomic and self-contained.* |
| RPA_03 | A Wallet Unit and a Relying Party Instance SHALL perform Relying Party authentication in all use cases, whether proximity or remote, using a Relying Party Instance access certificate. *Note: The actions both entities perform differ. For example, while the Relying Party creates a signature over some data in the request, the Wallet Unit validates that signature.* |
| RPA_04 | For the verification of Relying Party Instance access certificates, a Wallet Unit SHALL accept the trust anchors in the Trusted List(s) of Relying Party Access Certificate Authorities of all Member States. *Note: For more information about Relying Party Access Certificate Authorities, please see [[Topic 31](#a2331-topic-31---pid-provider-wallet-provider-attestation-provider-and-access-certificate-authority-notification-and-publication)].* |
| RPA_05 | If Relying Party authentication fails for any reason, the Wallet Instance SHALL inform the User that the identity of the Relying Party could not be verified and that therefore the request is not trustworthy. |
| RPA_06 | If Relying Party authentication succeeds, the Wallet Instance SHALL display to the User the name of the Relying Party as included in the Relying Party registration certificate (see [Topic 44](#a2344-topic-44---relying-party-registration-certificates)), if available, together with the attributes requested by the Relying Party, as well as the warning in case any of the requested attributes is not included in the list of attributes in the registration certificate (registered "intended use"). The Wallet Instance SHALL do so when asking the User for approval according to RPA_07. _Note: If the Relying Party registration certificate is not available, see RPA_06c._ |
| RPA_06a | If the registration certificate indicates that an intermediary is acting on behalf of the 'end' Relying Party, as described in [Topic 52](#a2352-topic-52-relying-party-intermediaries), the Wallet Unit SHALL verify that the name and the unique identifier of the intermediary included in the registration certificate are identical to the name and unique identifier included in the Relying Party Instance access certificate. If this verification fails, the Wallet Unit SHALL treat this as a Relying Party authentication failure. If this verification succeeds, the Wallet Instance SHALL display to the User the names of the intermediary and the intermediated End-Relying Party. _Note: If the Relying Party registration certificate is not available, see RPA_06d._|
| RPA_06b | If Relying Party authentication fails for any reason, the Wallet Unit SHALL either not present the requested attributes to the Relying Party, or give the User the choice to present the requested attributes or not. *Note: It is up to the Wallet Provider to make a choice for one of the two options above.* |
| RPA_06c | If the Relying Party registration certificate is not available, the name of the Relying party is retrieved from the access certificate. The User SHALL be offered on option to perform an on-line verification of the Relying Party information and the registered intended use, meaning to obtain the list of registered attributes ("intended use"). If the User chooses to do so, the Wallet Unit retrieves a URL of the Registrar's on-line service (or Trusted List, if applicable) to fetch such information and run comparison and display the warning as defined in RPA_06.     |
| RPA_06d | If a transaction is performed by an intermediary and the Relying Party registration certificate is not available, the Wallet Unit SHALL retrieve the name and the unique identifier of the 'end' Relying Party from the presentation request and use them to obtain information from the Registrar's on-line service on the 'end' Relying Party and an intermediary it is linked to (to check if it is the same entity as in the access certificate).      |


B. User approval

| **Index** | **Requirement specification** |
|-----------|--------------|
| RPA_07 | A Wallet Unit SHALL ensure the User approved the release of any attribute(s) in the Wallet Unit to a Relying Party, prior to releasing these attributes. A Wallet Unit SHALL always allow the User to refuse releasing an attribute requested by the Relying Party. |
| RPA_07a | If a Wallet Unit supports the [W3C Digital Credentials API] for remote presentation flows, it SHALL retain full authority over the process meant in RPA_07. In particular, this process SHALL NOT be handled by a third party, including the browser and the operating system. |
| RPA_08 | A Wallet Unit SHALL ensure that (one of) its WSCA(s) has authenticated the User before allowing the User to give or refuse approval for releasing any attributes. *Note: See [[Topic 09](#a239-topic-9---wallet-unit-attestation)] for information about the WSCA.* |
| RPA_09 | A Relying Party SHOULD communicate in the request which attributes are needed for which purpose (use case, service), if this is supported by the protocol used for communication with the Wallet Unit. *Notes: - This could be done, for instance, by grouping the attributes and describing the use case, service, or purpose of each group. - The purpose of this recommendation is that a Relying Party makes clear to the User what the intended use, the service being accessed, or the specific purpose is of each requested attribute. For example, a service may legally require attributes for age verification (e.g., birthdate), but the Relying Party may additionally want a User address (e.g., street, location, PObox, country) in order to offer added-value services. Age verification attributes and address attributes should be grouped separately, and the purposes should be clearly distinguished. This allows the User to be better informed about the request, and also allows them to approve one purpose but deny the other; see RPA_10.* |
| RPA_10 | If a Wallet Unit receives a request indicating one or more purposes (use cases, services) for requesting attributes, the Wallet Instance SHOULD show these to the User when asking for User approval. Moreover, the Wallet Unit SHOULD ensure that for each purpose, the User gives approval either to release all attributes requested for that purpose, or none of them. *Note: This means that a User should either approve the release of all attributes in a given group or to deny the entire group. The Wallet Unit should not allow partial approval within a group. Partial approval would mean that the Relying Party cannot deliver the service, but nevertheless receives some User attributes. This would be a violation of the User's privacy.* |
| RPA_11 | When the presentation of an attestation is denied by the User, the Wallet Unit SHALL behave towards the Relying Party as if the attestation did not exist. |

#### A.2.3.7 Topic 7 - Attestation revocation and revocation checking

##### Description <!-- omit from toc -->

This Topic contains the high-level requirements (HLRs) relating to the
(possible) revocation of PIDs, QEAAs, PuB-EAAs, non-qualified EAAs and WUAs by
their providers. It also contains HLRs relating to the (possible) checking of
the revocations status of a PID or attestation by a Relying Party.

Note: This Topic does not pertain to access certificates for Relying Parties,
PID Providers or Attestation Providers as discussed in
[[Topic 31](#a2331-topic-31---pid-provider-wallet-provider-attestation-provider-and-access-certificate-authority-notification-and-publication)].
Neither does it apply to any intermediate certificates establishing trust
between these certificates and the respective trust anchors. These access
certificates are part of a Public Key Infrastructure, and rules for revoking
these certificates will be established within the respective PKI.

##### HLRs <!-- omit from toc -->

| **Index** | **Requirement specification** |
|-----------|--------------|
| VCR_01 | A PID Provider, QEAA Provider, PuB-EAA Provider, or Wallet Provider SHALL use one of the following methods for revocation of a PID, QEAA, PuB-EAA, or WUA: - Only issue short-lived attestations having a validity period of 24 hours or less, such that revocation will never be necessary, - Use an Attestation Status List mechanism specified per VCR_11, or - Use an Attestation Revocation List mechanism specified per VCR_11. *Note: The 24-hour period originates from ETSI EN 319 411-1 V1.4.1, requirement REV-6.2.4-03A. This requires that the process of revocation must take at most 24 hours. Consequently, revocation may make no sense if the attestation is valid for less than 24 hours, because it may reach the end of its validity period before it is revoked.* |
| VCR_02 | For non-qualified EAAs, the relevant Rulebook SHALL specify whether that type of EAA must be revocable. If a non-qualified EAA type must be revocable, the relevant Rulebook SHALL determine which of the methods mentioned in VCR_01 must be implemented by the relevant EAA Providers for the revocation of such an EAA. |
| VCR_03 | If a PID or attestation is revocable, the PID Provider of a given PID, or the Attestation Provider of a given attestation, SHALL be the only party in the EUDI Wallet ecosystem responsible for executing the revocation of that PID or attestation. Similarly, if a WUA is revocable, the Wallet Provider of a given WUA SHALL be the only party in the EUDI Wallet ecosystem responsible for executing the revocation of that WUA. *Note: A PID Provider, Attestation Provider or Wallet Provider MAY outsource the operation of the revocation process to a third party.* |
| VCR_04 | A PID Provider, Attestation Provider or Wallet Provider that revoked a PID or attestation SHALL NOT reverse the revocation. |
| VCR_05 | If a PID, attestation, or WUA is revocable, the PID Provider, Attestation Provider, or Wallet Provider SHALL have a policy specifying under which conditions a PID, attestation, or WUA it issued will be revoked. |
| VCR_06 | If a PID, attestation, or WUA is revocable, the PID Provider, Attestation Provider, or Wallet Provider SHALL revoke a PID, attestation, or WUA when its security has been compromised. |
| VCR_07 | If a WUA is revocable, the Wallet Provider SHALL revoke that WUA upon the explicit request of the User to revoke their Wallet Unit. |
| VCR_07a | If a PID or attestation is revocable, the PID Provider or Attestation Provider SHOULD revoke that PID or attestation upon the explicit request of the subject of the PID or the attestation. |
| VCR_07b | If a PID or attestation is revocable, the PID Provider or Attestation Provider SHOULD revoke that PID if the Wallet Unit on which it resides is revoked, in compliance with requirement WU_Revocation 18 in [Topic 38](#a2338-topic-38---wallet-unit-revocation). |
| VCR_08 | If a PID is revocable, the PID Provider SHALL revoke a PID upon the death of the natural person who is the subject of the PID, or the cease of activity of the legal person who is the subject of the PID. |
| VCR_09 | If a PID, attestation, or WUA is revocable, the PID Provider, Attestation Provider or Wallet Provider SHALL revoke a PID, attestation, or WUA if the value of one or more attributes in the PID, attestation, or WUA was changed (including attributes being added or deleted) and it is still valid for at least 24 hours. Subsequently, if the User's contact details are known, the PID Provider SHOULD, via an out-of-band manner, notify the User about the revocation and ask the User to request re-issuance of the PID, attestation, or WUA using their Wallet Unit. *Note: If the value of the attributes is determined by a party different from the Provider, such as an Authentic Source, the Provider is responsible for ensuring that this third party notifies them about such changes.* |
| VCR_10 | Wallet Providers SHALL implement the attestation revocation mechanisms specified per VCR_11 in their Wallet Solutions. |
| VCR_11 | The Commission SHALL create or reference technical specifications providing all necessary details for PID Providers, Attestation Providers, and Wallet Providers to implement an Attestation Status List mechanism or an Attestation Revocation List mechanism for the PIDs, attestations, and WUAs they issue. These technical specifications SHALL also contain all details necessary for Relying Party Instances, Relying Parties and Wallet Units interacting with other Wallet Units to use these mechanisms to verify the revocation status of PIDs, attestations, and WUAs. *Note: 'Attestation Status List' and 'Attestation Revocation List' are specific mechanisms, defined in Annex 1. Attestation Revocation Lists are sometimes referred to as 'Identifier Lists'.* |
| VCR_12 | If a Relying Party decides it needs to verify the revocation status of a PID, attestation or WUA, it SHALL support both the Attestation Status List mechanism and the Attestation Revocation List mechanism specified per VCR_11. *Note: Per VCR_13, it is recommended but not mandatory for a Relying Party to verify whether a PID, attestation or WUA is revoked.* |
| VCR_13 | A Relying Party Instance SHOULD verify the revocation status of a PID, attestation, or WUA upon obtaining it from a Wallet Unit, following the steps specified per VCR_11. |
| VCR_14 | When no reliable information regarding the revocation status of a PID, attestation or WUA is available, a Relying Party SHOULD perform a risk analysis considering all relevant factors for the use case, before taking a decision to accept or refuse the PID, attestation or WUA. |
| VCR_15 | A Relying Party Instance SHOULD NOT request the relevant Attestation Status List or Attestation Revocation List each time an attestation is presented to it by a Wallet Unit. Rather, the Relying Party operating the Relying Party Instance SHOULD download each new version of the list once, at a time and from a location unrelated to the presentation of a PID or attestation by a User. The Relying Party SHOULD then distribute the list to all of its Relying Party Instances, using an Relying Party-internal distribution mechanism. |
| VCR_16 | A PID Provider, Attestation Provider or Wallet Provider SHALL NOT require the Relying Party or Relying Party Instance to authenticate itself before downloading an Attestation Status List or Attestation Revocation List. |
| VCR_17 | When using an Attestation Status List for revocation, the PID Provider, Attestation Provider or Wallet Provider SHALL randomly assign the index for each PID or attestation, to prevent this index from becoming a correlator. *Note: Randomly assigning indices within a bitstring or byte array is more complicated than creating random identifiers (e.g. serial numbers) for attestations, as is needed for an Attestation Revocation List. This is because duplicate indices and unnecessarily long bitstrings or byte arrays must be prevented.* |
| VCR_18 | When using an Attestation Status List for revocation, the PID Provider, Attestation Provider or Wallet Provider SHALL represent a sufficiently large number of PIDs, attestations, or WUAs on each Attestation Status List to ensure herd privacy. *Note: In this context, herd privacy means that if a Relying Party requests a particular status list, the PID Provider, Attestation Provider or Wallet Provider is not able to deduce which PID or attestation (likely) was presented to that Relying Party. *Note: Complying with this requirement may be difficult in case the number of PIDs, attestations, or WUAs to be represented on the list is small. In such a case, decoy entries can be added to the list to obfuscate the real number of referenced PIDs, attestations, or WUAs.* |
| VCR_19 | A Wallet Unit SHOULD regularly check the revocation status of its PIDs, attestations, and WUAs, and notify the User if a PID or attestation, or a WUA (i.e, the Wallet Unit itself), is revoked. |

#### A.2.3.8 Topic 8 - Design Solutions on Data Sharing scenarios

There are no HLRs for this Topic.

#### A.2.3.9 Topic 9 - Wallet Unit Attestation

Note to this Topic: The Commission received many comments on
the ideas described in this Topic, particularly relating to revocation and
the differing needs of Relying Parties on one side and
PID Providers and Attestation Providers on the other.
Further details on these subjects will be provided in a technical specification
and the high level requirements in Topic 9 intentionally do not go into these technical details. To support the varying needs of the actors, the technical specification may specify two types of WUA, containing
different information, and having different validity periods and different formats.

##### Description <!-- omit from toc -->

When a User's Wallet Unit interacts with other actors
in the EUDI Wallet ecosystem, e.g., PID Providers, Attestation Providers
or Relying Parties, that actor may want to verify if the Wallet Unit is trustworthy,
i.e., the Wallet Unit is authentic and has not been revoked.
*This scenario will be referred to as Use Case 1.*

Furthermore, when a PID Provider or Attestation Provider receives a request from a
User to issue a PID or attestation to the User's Wallet Unit,
the PID Provider or Attestation Provider needs to decide whether it can
comply with this request. To determine this, the PID Provider or
Attestation Provider needs to know (among other things) if the Wallet
Unit offers the functional capabilities required by the PID Provider
or Attestation Provider in its PID or attestation issuing policy. In
addition, the PID Provider or Attestation Provider needs to know if the
Wallet Secure Cryptographic Application(s) (WSCA) and the corresponding
Wallet Secure Cryptographic Device(s) (WSCD) that are part of the Wallet Unit
offer the required level of security. Therefore, the PID Provider or
Attestation Provider needs to receive trustworthy information about
these capabilities and security posture.
*This scenario will be referred to as Use Case 2.*

This Topic introduces an information object that contains the necessary
information to achieve the two use cases. This object is called the Wallet Unit
Attestation (WUA). The WUA also contains a public key. By including this public
key in the WUA, the Wallet Provider attests that the corresponding private key is
protected by a certified WSCA/WSCD that has the properties and security posture
described in the WUA.
Note that the information about the Wallet Unit and the WSCA(s) should only be
released in relation to Use Case 2, meaning that to accommodate both use cases, the Wallet Unit must be able to release a WUA either with or without this information.

The PID Provider or Attestation Provider then asks the Wallet Unit to create a key
pair for its new PID or attestation, and to prove that both this new private key and the
private key corresponding to public key in the WUA are in possession of the Wallet Unit.

A topic related to the WUA is the following. It would be useful for the Wallet Unit to be able to provide a proof that the PID or attestation private key is protected by the same WSCA as the WUA private
key. Because if that is the case, the PID Provider or Attestation Provider can be sure that the
security level of the new PID or attestation key is the same as the security
level of the WUA key. Moreover, such a proof could also be useful in case of a combined presentation of attributes as discussed in [Topic 18](#a2318-topic-18---combined-presentations-of-attributes), to give assurance to the Relying Party that all of these attestations originate from the same WSCA/WSCD and thus are related to the same User.

However, at the moment of writing this version of the ARF, no commonly agreed technical specification of such a proof is available. Moreover, even if such a specification were available, it is
not fully clear how many WSCAs/WSCDs available to Wallet Units will support the cryptographic functionalities
necessary to generate such a proof. Therefore, creating such a proof is recommended (SHOULD), not required (SHALL). In this way, once a Wallet Unit includes a WSCD/WSCA that supports the required cryptographic functionalities, such a proof can be used as described in this Topic.

Notes:

- The Commission will ensure a technical specification for such a proof is created in the future.
- In earlier versions of the ARF, this proof was called a 'proof of association'. However, this is also the name commonly used for one of the proposals for implementing such a proof. To avoid confusion, this version of the ARF does not use this term.

Please note that the scope of this Topic is limited to the question
of how the WUA is issued during Wallet Unit activation and how it is
used during attestation issuance. The role played by the WUA during the
release of an attestation to a Relying Party is discussed in [[Topic 18](#a2318-topic-18---combined-presentations-of-attributes)]
(Combined presentation of attributes).

##### HLRs <!-- omit from toc -->

###### A.  Support for WUA Use Cases <!-- omit from toc -->

| **Index** | **Requirement specification**   |
|-----------|----------------------------------------------|
| WUA_01  | The WUA SHALL provide a PID Provider or Attestation Provider with information about the capabilities of the WSCA and WSCD of the Wallet Unit, such that they are able to take a well-grounded decision on whether to issue an attestation or PID to the Wallet Unit. |
| WUA_02  | The WUA SHALL enable Relying Parties, PID Providers, and Attestation Providers to verify the authenticity and revocation status of the Wallet Unit. |
| WUA_03  | Wallet Providers SHALL ensure that a non-revoked Wallet Unit at all times can present a WUA, when requested by a Relying Party, PID Provider, or Attestation Provider. |
| WUA_04  | During PID or attestation issuance, a Wallet Unit SHALL provide the PID Provider or Attestation Provider with information on all WSCAs it is able to use for private key management, so that the PID Provider or Attestation Provider can make a choice about the WSCA it wants to use for its new PID or attestation. Notes: - This information is not in the form of a WUA. As specified in WUA_05, the Wallet Unit must provide only the WUA for the WSCA that is actually used, not for all WSCAs it can potentially use. - See also WUA_15.  |
| WUA_05  | During PID or attestation issuance, a Wallet Unit SHALL provide the PID Provider or Attestation Provider with the WUA describing the properties of the WSCA that generated the new PID or attestation private key and protects it. |
| WUA_06  | If a Wallet Unit contains multiple WSCAs, it SHALL, internally and securely, keep track of which PIDs and attestations are bound to which WSCA. |
| WUA_07  | A Wallet Unit SHALL present a WUA only as part of either the issuance of a PID or an attestation, or in conjunction with the presentation of a PID or an attestation to a Relying Party. *Note: the WUA presented during issuance has different information content and may have a different format than the WUA presented in conjunction with a PID or an attestation.*  |
| WUA_08  | The WUA SHALL enable PID Providers to request a Wallet Provider to revoke a Wallet Unit, in accordance with requirement WURevocation_11. |

###### B.  WUA in relation Cryptographic Keys <!-- omit from toc -->

| **Index** | **Requirement specification**  |
|-----------|----------------------|
| WUA_09 | A WUA SHALL contain a public key, and the corresponding private key SHALL be generated by the WSCA described in the WUA presented by the Wallet Unit, if the WUA contains information about a WSCA. |
| WUA_10 | The WSCA SHOULD be able to prove that two or more private keys, paired with two or more public keys, are stored in it. *Notes: -These public keys may be included in WUAs, PIDs, attestations, or pseudonyms. -The proof may be transitive, so a proof that two keys are stored/managed in the same WSCA may be done by proving keys relate to each other via a third key (also stored in the WSCA).* |
| WUA_11 | During PID or attestation issuance, the PID Provider or Attestation Provider SHALL verify that the WSCA described in the WUA received from the Wallet Unit has proven possession of the private key corresponding to the public key in the WUA. |
| WUA_11a | During PID or attestation issuance, the PID Provider or Attestation Provider SHALL verify that a WSCA has proven possession of the new PID or attestation private key.|
| WUA_11b | During PID or attestation issuance, the PID Provider or Attestation Provider SHOULD verify the proof generated by the WSCA per requirement WUA_10, if present, to verify that the new PID or attestation private key is stored in the same WSCA as the WUA private key. *Note: The three proofs mentioned in WUA_11, WUA_11a and WUA_11b MAY be implemented as a single cryptographic proof.* |
| WUA_12 |  The Wallet Unit SHALL be able to prove that it possesses the private key corresponding to the public key in the WUA. |
| WUA_13 | A Relying Party requesting the creation of a pseudonym according to [W3C WebAuthn] SHOULD verify that the private key belonging to the public key it receives as a pseudonym, is stored in the same WSCA as the WUA private key. |
| WUA_14 | The common OpenID4VCI protocol referenced in requirement ISSU_01, or an EUDI Wallet-specific extension or profile thereof, SHALL enable a PID Provider or Attestation Provider to verify that the WUA private key and the PID or attestation private key are stored in the same WSCA. |
| WUA_15 | The common OpenID4VCI protocol referenced in requirement ISSU_01, or an EUDI Wallet-specific extension or profile thereof, SHALL enable a PID Provider or Attestation Provider to indicate in the Token Response the WSCA to which the new PID or attestation key must be bound. |
| WUA_16 | If a WSCA is able to export a private key, the Wallet Provider SHALL specify this capability as an attribute in the WUA. |

###### C.  Requirements regarding privacy <!-- omit from toc -->

| **Index** | **Requirement specification**  |
|-----------|------|
| WUA_17   | A Wallet Provider SHALL consider all relevant factors, including offline usage, interoperability, and the risk of a WUA becoming a vector to track the User, when deciding on the validity period of a WUA. A Wallet Provider MAY use short-lived WUAs to mitigate such risks. *Note: The requirements for the validity period of WUAs presented to Relying Parties in the technical specification (see WUA_19) may be different from the validity period of WUAs presented to PID Providers and Attestation Providers.* |
| WUA_18   | A Wallet Unit SHALL release data related to the User device in a WUA only to a PID Provider or Attestation Provider, and not to a Relying Party or any other party. *Note: Use case 2 (data related to the User device), must not be supported for Relying Parties.* |

###### D.  Miscellaneous requirements <!-- omit from toc -->

| **Index** | **Requirement specification** |
|-----------|------------------------|
| WUA_19  | The Commission SHALL create or reference technical specification for the WUA, compliant with the HLRs in this topic. |
| WUA_20  | The Wallet Provider SHALL ensure that Wallet Units conform to all requirements specified in the technical specification mentioned in WUA_19. |
| WUA_21  | The common OpenID4VCI protocol referenced in requirement ISSU_01, or an EUDI Wallet-specific extension or profile thereof, SHALL enable a Wallet Unit to transfer a WUA to a PID Provider or Attestation Provider.  |

#### A.2.3.10 Topic 10 - Issuing a PID or attestation to a Wallet Unit

##### Description <!-- omit from toc -->

PID Providers and Attestation Providers issue PIDs and attestations to
Wallet Units. This Topic lists the high-level technical
requirements related to PID and attestation issuance.

This Topic also contains the high-level requirements for [Topic 23](#a2323-topic-23---pid-issuance-and-qeaa-issuance).

##### HLRs <!-- omit from toc -->

###### A - Generic HLRs <!-- omit from toc -->

| **Index** | **Requirement specification** |
|-----------|--------------|
| ISSU_01 | Wallet Providers SHALL ensure that their Wallet Solution supports the OpenID4VCI protocol specified in [OpenID4VCI], as profiled by the 'OpenID for Verifiable Credential Issuance' profile specified in [HAIP], and with additions and changes as documented in this Annex (see e.g. this Topic and [[Topic 9](#a239-topic-9---wallet-unit-attestation)]) and in future technical specifications created by or on behalf of the Commission. |
| ISSU_01a | PID Providers and Attestation Providers SHALL support the OpenID4VCI protocol specified in [OpenID4VCI], as profiled by the 'OpenID for Verifiable Credential Issuance' profile specified in [HAIP], and with additions and changes as documented in this Annex (see e.g. this Topic and [[Topic 9](#a239-topic-9---wallet-unit-attestation)]) and in future technical specifications created by or on behalf of the Commission. |
| ISSU_02 | Wallet Providers SHALL ensure that their Wallet Solution supports the attestation formats specified in ISO/IEC 18013-5, see [ISO18013-5], and in "SD-JWT-based Verifiable Credentials (SD-JWT VC)", see [SD-JWT-VC], with additions and changes as documented in this Annex and in future technical specifications created by or on behalf of the Commission. |
| ISSU_03 | Wallet Units, PID Providers, and Attestation Providers SHALL support the [W3C Digital Credentials API]](<https://wicg.github.io/digital-credentials/>) for issuance of PIDs and attestations, provided that a) this API is fully standardised, b) this API complies with the expectations outlined in [Chapter 3](../../discussion-topics/f-digital-credential-api.md#3) of the Topic F discussion paper, and c) this API is broadly supported by relevant browsers and operating systems. |
| ISSU_04 | The OpenID4VCI protocol referenced in requirement ISSU_01, or an EUDI Wallet-specific extension or profile thereof, SHALL enable PID Providers and Attestation Provider to issue to a Wallet Unit a batch of multiple PIDs or attestations that are simultaneously valid and contain the same attributes. |
| ISSU_05 | A Wallet Unit SHALL support a process to activate a newly issued PID, in accordance with the requirements for LoA High in [Commission Implementing Regulation (EU) 2015/1502](https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=CELEX%3A32015R1502) Section 2.2.2. The Wallet Unit SHALL NOT allow a User to use a non-activated PID. *Notes: - The goal of the activation process is to verify that the PID was delivered into the Wallet Unit and WSCA of the User who is the subject of the PID. - This requirement is not applicable for QEAAs, PuB-EAAs or non-qualified EAAs, since these are not identity means in the sense of Commission Implementing Regulation (EU) 2015/1502.* |
| ISSU_06 | After a Wallet Unit receives a PID or an attestation from a PID Provider or Attestation Provider, it SHALL verify that the PID or attestation it received matches the PID or attestation requested by the Wallet Unit. |
| ISSU_07 | After a Wallet Unit receives a PID from a PID Provider, it SHALL validate the signature of the PID using a trust anchor provided in a PID Provider Trusted List made available in accordance with [[Topic 31](#a2331-topic-31---pid-provider-wallet-provider-attestation-provider-and-access-certificate-authority-notification-and-publication)]. *Note: This signature validation may not be useful in architectures where the Wallet Provider is also the PID Provider and the validation of the PID signature would be done by the same component (namely, a remote HSM) that created the signature. However, in such a situation, additional measures SHALL be taken to ensure that any errors in the PID issuance process will be detected.* |
| ISSU_08 | After a Wallet Unit receives a QEAA from a QEAA Provider, it SHALL validate the qualified signature of the QEAA in accordance with Art.32 of the [European Digital Identity Regulation]. For the verification, the Wallet Unit SHALL use a trust anchor provided in a QEAA Provider Trusted List made available in accordance with [Art. 22](https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=uriserv%3AOJ.L_.2014.257.01.0073.01.ENG#d1e2162-73-1) of the [European Digital Identity Regulation]. |
| ISSU_09 | After a Wallet Unit receives a PuB-EAA from a PUB-EAA Provider, it SHALL validate the qualified signature of the PuB-EAA in accordance with Art.32 of the [European Digital Identity Regulation]. For that verification, the Wallet Unit SHALL use the public key provided in the qualified certificate of the QTSP supporting the qualified signature. The Wallet Unit SHALL also validate the qualified certificate of the QTSP using a trust anchor provided in a Trusted List made available in accordance with [Art. 22](https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=uriserv%3AOJ.L_.2014.257.01.0073.01.ENG#d1e2162-73-1) of the [European Digital Identity Regulation]. Finally, the Wallet Unit SHALL also verify the certified attributes of the qualified certificate, as specified in [Article 45f](https://eur-lex.europa.eu/legal-content/EN/ALL/?uri=CELEX:32024R1183#d1e3902-1-1). |
| ISSU_10 | After a Wallet Unit receives a non-qualified EAA from an EAA Provider, it SHALL validate the signature of the EAA using a trust anchor provided according to the mechanism(s) specified in the applicable Rulebook, see [[Topic 12](#a2312-topic-12---attestation-rulebooks)]. *Notes: - Requirements ISSU_07 to ISSU_10 are equivalent to requirements OIA_12 to OIA_15 in [Topic 1](#a231-topic-1---accessing-online-services-with-a-wallet-unit). These requirements imply that a Wallet Instance must be aware whether the attestation it is requesting from an issuer is a PID, a QEAA, a PuB-EAA, or a non-qualified EAA. These requirements also imply that the Wallet Unit must store trust anchors in such a way that, when it receives an issued attestation, it is able to distinguish between trust anchors usable either for PIDs, for QEAAs, for PuB-EAAs, or for non-qualified EAAs. - PID Providers, QEAA Providers, and PuB-EAA Providers are trusted by other actors in the EUDI Wallet ecosystem to not fraudulently issue attestations (or PIDs) that they are not legally allowed to issue. This trust is warranted since these kinds of providers operate within a regulated framework and are regularly audited. However, non-qualified EAA Providers are unregulated and may not be completely trustworthy. Therefore, before requesting an non-qualified attestation, a Wallet Unit may need to verify that the non-qualified EAA Provider is authorised or registered to issue this type of attestation. Mechanisms allowing to do this may be defined in the applicable Rulebook, see ARB_26.* |
| ISSU_11 | A Wallet Unit SHALL request the User's approval before storing a PID or attestation obtained from a PID Provider or Attestation Provider. When requesting approval, the Wallet Instance SHALL display the contents of the PID or attestation to the User. The Wallet Instance SHALL also inform the User about the identity of the PID Provider or Attestation Provider, using the subject information in the PID Provider's or Attestation Provider's access certificate. |
| ISSU_11b | In case one or more of the verifications in ISSU_06 – ISSU_11 fail, the Wallet Unit SHALL immediately delete the PID or attestation it received. The Wallet Instance SHALL notify the User about the fact that issuance of the PID or attestation was not successful, including the reason for this failure. |
| ISSU_12 | A PID Provider or Attestation Provider SHALL offer its PIDs or attestations in all formats required in the PID Rulebook or the applicable Attestation Rulebook, see [[Topic 12](#a2312-topic-12---attestation-rulebooks)]. *Note: Examples include the mdoc format specified in [ISO/IEC 18013-5] and the SD-JWT VC-format specified in [SD-JWT VC].* |
| ISSU_12a | A Wallet Provider SHALL ensure that, when a User instructs their Wallet Unit to request a PID or attestation from a PID Provider or Attestation Provider, the Wallet Unit requests that PID or attestation in all formats offered by the PID Provider or Attestation Provider. *Note: Examples include the mdoc format specified in [ISO/IEC 18013-5] and the SD-JWT VC-format specified in [SD-JWT VC].* |
| ISSU_12b  | During PID or attestation issuance, a WSCA SHALL generate a new key pair for a new PID or attestation, on request of the PID Provider or Attestation Provider via the Wallet Instance. *Note: In case of synchronous issuing in a remote HSM architecture, re-use of an existing key pair for the new PID or attestation may be acceptable and it may not be necessary to generate a new key pair for each new PID or attestation.* |
| ISSU_12c  | The expiration date of the issued PID or Attestation SHALL be no later than the expiration date of the WUA presented as part of the issuance process. |

###### B - HLRs for PID issuance <!-- omit from toc -->

| **Index** | **Requirement specification** |
|-----------|--------------|
| ISSU_13 | A Wallet Provider SHALL ensure that at least one PID Provider is willing to issue a PID complying with [PID Rulebook] to Users of the Wallet Units it provides. |
| ISSU_14 | A PID Provider SHALL ensure that all PIDs it issues to Wallet Units comply with the requirements specified in [PID Rulebook]. |
| ISSU_15 | A PID Provider SHALL support the OpenID4VCI protocol referenced in ISSU_01 for issuing PIDs. |
| ISSU_16 | Empty |
| ISSU_17 | A PID Provider SHALL implement device binding for all PIDs it issues, meaning it SHALL ensure that a PID is cryptographically bound to a WSCA included in the Wallet Unit, as specified in requirement WUA_11 in [[Topic 09](#a239-topic-9---wallet-unit-attestation)]. *Note: Device binding is called 'mdoc authentication' in [ISO/IEC 18013-5] and 'key binding' in [SD-JWT-VC].* |
| ISSU_18 | A PID Provider SHALL verify the identity of the subject of the PID in compliance with Level of Assurance (LoA) High requirements. *Notes: - These requirements will be determined by the relevant eID scheme. - In most cases, the subject of the PID is the same person as the User. However, it has not yet been ruled out that a Wallet Unit may contain multiple PIDs, for example in the case of a parent having their children's PIDs in their Wallet Unit. Another example is a natural person representing a legal person, who may hold a legal-person PID in their Wallet Unit next to their own natural-person PID. These topics will be further discussed with Member States.* |
| ISSU_18a | A PID Provider SHALL ensure that the attributes attested in the PID issued are valid for the identified PID subject at any point of time of PID validity. |
| ISSU_19 | For the verification of a WUA, a PID Provider SHALL accept the trust anchors in the Wallet Provider Trusted List it needs. *Notes: - The Wallet Provider Trusted List is explained in [[Topic 31](#a2331-topic-31---pid-provider-wallet-provider-attestation-provider-and-access-certificate-authority-notification-and-publication)]. - It is not mandatory for a PID Provider to accept all Wallet Provider Trusted Lists, if there are multiple. This is because it is not mandatory for a PID Provider to accept all certified Wallet Solutions in the EUDI Wallet ecosystem. Each PID Provider will choose which Trusted Lists they need to subscribe to.* |
| ISSU_19a | A PID Provider SHALL support at least one Wallet Solution, meaning that it is willing and able to issue a PID to a Wallet Unit on request of the User. |
| ISSU_20 | To inform its potential PID subjects about the Wallet Solution(s) they can use for requesting a PID, a PID Provider SHALL publish a list of supported Wallet Solutions in such a way that it can be easily found, for example on the PID Provider's website. |
| ISSU_21 | Before issuing a PID, a PID Provider SHALL verify that the Wallet Provider mentioned in the Wallet Unit's WUA is present in a Wallet Provider Trusted List. The PID Provider SHALL also authenticate and validate the WUA using the trust anchor(s) registered for the Wallet Provider in the Wallet Provider Trusted List. Moreover, it SHALL verify that the Wallet Units's WUA is not revoked. *Notes: - For the WUA, see [[Topic 9](#a239-topic-9---wallet-unit-attestation)] and [[Topic 38](#a2338-topic-38---wallet-unit-revocation)]. - [CIR 2024/2977](https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=CELEX:32024R2977), Article 3 (9), also allows "another authentication mechanism in accordance with an electronic identity scheme notified at assurance level high." However, the ARF does not further specify such other authentication mechanisms, which means that in general they will not be interoperable.* |
| ISSU_22 | A PID Provider SHALL include its PID Provider access certificate in its Issuer metadata used in the common OpenID4VCI protocol referenced in ISSU_01. |
| ISSU_22a | A PID Provider SHALL sign its metadata (as defined in OpenID4VCI) using the private key corresponding to its PID Provider access certificate. |
| ISSU_22b | The common OpenID4VCI protocol referenced in requirement ISSU_01, or an EUDI Wallet-specific extension or profile thereof, SHALL enable a PID Provider or Attestation Provider to include its access certificate in its Issuer metadata, according to requirement ISSU_22. |
| ISSU_23 | For the verification of PID Provider access certificates, a Wallet Unit SHALL accept the trust anchors in the Trusted List(s) of PID Provider Access Certificate Authorities it needs. *Notes: - PID Provider Access Certificate Authority Trusted Lists are explained in [[Topic 27](#a2327-topic-27---registration-of-pid-providers-providers-of-qeaas-pub-eaas-and-non-qualified-eaas-and-relying-parties)]. -It is not mandatory for a Wallet Unit to accept all PID Provider Access Certificate Authority Trusted Lists, if there are multiple. Wallet Providers will choose which Trusted Lists they need to subscribe to, for example depending on the Member State(s) they are operating in.* |
| ISSU_23a | A Wallet Provider SHALL support at least one PID Provider, meaning that its Wallet Units SHALL be capable of requesting the issuance of a PID from these PID Provider(s), and that the Wallet Provider has agreed with the PID Provider(s) that the PID Provider(s) will process such a request according to the agreed rules and procedures. |
| ISSU_23b | Prior to or during installation of a Wallet Instance, the Wallet Provider SHALL notify the User about the PID Provider(s) that are supported by the Wallet Unit. |
| ISSU_24 | A Wallet Unit SHALL authenticate and validate the PID Provider access certificate before requesting the issuance of a PID. The Wallet Unit SHALL verify that the access certificate is authentic and is valid at the time of validation, and that the issuer of the access certificate is a CA that is in a PID Provider Access Certificate Authority Trusted List. *Note: The PID Provider Access Certificate Authority Trusted List is not the same as the PID Provider Trusted List mentioned in [[Topic 31](#a2331-topic-31---pid-provider-wallet-provider-attestation-provider-and-access-certificate-authority-notification-and-publication)].* |
| ISSU_24a | Before the issuance of a PID, the Wallet Unit SHALL verify that the PID issuer is a registered PID Provider and its entitlements. This can be done with use of information contained in PID Provider registration certificate, if available. If the registration certificate is not available, the Wallet Unit SHALL use the URL of the Registrar's on-line service, contained in the PID Provider access certificate, to obtain such information. In case the result of the verification is negative or indicates differences in the entitlements (eg. issuance concerns PID type that was not registered before by this PID Provider), the Wallet Unit SHALL display a warning to the user, and the User may accept or reject the issuance.  |


###### C - HLRs for Attestation Issuance <!-- omit from toc -->

| **Index** | **Requirement specification** |
|-----------|--------------|
| ISSU_25 | An Attestation Provider SHALL ensure all attestations issued to Wallet Units comply with the requirements specified in the applicable Rulebook, as described in [[Topic 12](#a2312-topic-12---attestation-rulebooks)]. |
| ISSU_26 | An Attestation Provider SHALL support the OpenID4VCI protocol referenced in ISSU_01 for issuing attestations. |
| ISSU_27 | An Attestation Provider SHALL implement device binding for all attestations it issues, meaning it SHALL ensure that an attestation is cryptographically bound to a WSCA included in the Wallet Unit, as specified in requirement WUA_11 in [[Topic 9](#a239-topic-9---wallet-unit-attestation)]. *Note: device binding is called 'mdoc authentication'  in [ISO/IEC 18013-5] and 'key binding' in [SD-JWT-VC].* |
| ISSU_27a | If applicable, an Attestation Provider SHALL verify the identity of the subject of the attestation in compliance with applicable requirements, in accordance with relevant standards or Implementing Regulations. *Note: Not every attestation has a subject. For example, a holiday voucher may be valid for any User that can present it to a Relying Party. This is comparable to the concept of a 'bearer token'.* |
| ISSU_27b | If applicable, an Attestation Provider SHALL ensure that the attributes attested in the attestation issued are valid for the identified attestation subject. |
| ISSU_28 | For the verification of a WUA, an Attestation Provider SHALL accept the trust anchors in the Wallet Provider Trusted List. *Note: The Wallet Provider Trusted List is explained in [[Topic 31](#a2331-topic-31---pid-provider-wallet-provider-attestation-provider-and-access-certificate-authority-notification-and-publication)].* |
| ISSU_29 | An Attestation Provider SHALL support all Wallet Solutions, meaning that they SHALL NOT discriminate between Wallet Solutions when processing a request for the issuance of an attestation. |
| ISSU_30 | Before issuing an attestation, an Attestation Provider SHALL: - verify that the Wallet Provider mentioned in the Wallet Unit's WUA is present in the Wallet Provider Trusted List. - authenticate and validate the WUA using the trust anchor(s) registered for the Wallet Provider in the Wallet Provider Trusted List. - verify that the Wallet Unit's WUA is not revoked. *Note: For the WUA, see [[Topic 9](#a239-topic-9---wallet-unit-attestation)] and [[Topic 38](#a2338-topic-38---wallet-unit-revocation)].* |
| ISSU_31 | Empty |
| ISSU_32 | An Attestation Provider SHALL include its Attestation Provider access certificate in its Issuer metadata used in the common OpenID4VCI protocol referenced in ISSU_01. |
| ISSU_32a | An Attestation Provider SHALL sign its metadata (as defined in OpenID4VCI) using the private key corresponding to its Attestation Provider access certificate. |
| ISSU_33 | For the verification of Attestation Provider access certificates, a Wallet Unit SHALL accept the trust anchors in all Attestation Provider Access Certificate Authority Trusted List(s). *Note: Attestation Provider Access Certificate Authority Trusted Lists are explained in [[Topic 27](#a2327-topic-27---registration-of-pid-providers-providers-of-qeaas-pub-eaas-and-non-qualified-eaas-and-relying-parties)]. There may be separate Access Certificate Authority Trusted Lists for QEAA Providers, PuB-EAA Providers, and EAA Providers.* |
| ISSU_33a | A Wallet Provider SHALL support all Attestation Providers, meaning that its Wallet Units SHALL be capable of requesting the issuance of a QEAA, PuB-EAA, or non-qualified EAA from these Providers at the User's request. |
| ISSU_34 | A Wallet Unit SHALL authenticate and validate the Attestation Provider access certificate before requesting the issuance of an attestation. The Wallet Unit SHALL verify that the access certificate is authentic and is valid at the time of validation, and that the issuer of the access certificate is a CA that is in the Attestation Provider Access Certificate Authority Trusted List, as documented in [[Topic 27](#a2327-topic-27---registration-of-pid-providers-providers-of-qeaas-pub-eaas-and-non-qualified-eaas-and-relying-parties)]. *Note: PID Providers, QEAA Providers, and PuB-EAA Providers are trusted by other actors in the EUDI Wallet ecosystem to not fraudulently issue attestations (or PIDs) that they are not legally allowed to issue. This trust is warranted since these kinds of providers operate within a regulated framework and are regularly audited. However, non-qualified EAA Providers are unregulated and may not be completely trustworthy. Therefore, before requesting an EAA from a non-qualified EAA Provider, a Wallet Unit may need to verify that that EAA Provider is authorised or registered to issue the type of EAA the Wallet Unit is requesting. Such verification requirements, as well as the mechanisms allowing to do this, may be defined in the applicable Rulebook.* |
| ISSU_34a | Before the issuance of a an Attestation, the Wallet Unit SHALL verify that the EAA issuer (Attestation Provider) is a registered QEAA Provider or PuB-EAA Provider or EAA Provider and its entitlements. This can be done with use of information contained in the Attestation Provider registration certificate, if available. If the registration certificate is not available, the Wallet Unit SHALL use the URL of the Registrar's on-line service, contained in the Attestation Provider access certificate, to obtain such information. In case the result of the verification is negative or indicates differences in the entitlements (eg. issuance concerns EAA type that was not registered before by this EAA Provider), the Wallet Unit SHALL display a warning to the user, and the User may accept or reject the issuance.  |

###### D - HLRs for Privacy Risks and Mitigation <!-- omit from toc -->

These HLRs were added as a result of the discussions of Topic A,
Privacy risks and mitigation. For more background information on these
requirements, please refer to
[Section 7.4.3.5 of the ARF main document](../../architecture-and-reference-framework-main.md#7435-risks-and-mitigation-measures-related-to-user-privacy) and to the [Discussion Paper for Topic A](../../discussion-topics/a-privacy-risks-and-mitigations.md).

Note: These requirements mention the WUA and the Wallet Provider. This is
because it is assumed that the format of the WUA complies with either [ISO/IEC
18013-5] or [SD-JWT VC], like for PIDs and attestations. However, this
assumption will be further discussed with Member States. If it turns out to be
wrong, then these requirements will be adapted accordingly.*

| **Index** | **Requirement specification** |
|-----------|--------------|
| ISSU_35 | A PID Provider, Attestation Provider, or Wallet Provider SHALL ensure that all unique elements in a PID, attestation or WUA, including at least a) the salt used for hashing every attribute, b) the hash values of all attributes, c) the attestation identifier or index used for revocation purposes (if applicable), d) the attestation public key used for device binding, and e) the value of the Attestation Provider signature, have values that are unique across all PIDs, attestations, or WUAs issued by that Provider. *Note: This can be achieved, for example, by ensuring that salt values and attestation identifiers are pseudo-random numbers generated by a cryptographically secure pseudo-random number generator (CSPRNG).* |
| ISSU_35a | After issuing a PID, attestation, or WUA, a PID Provider, Attestation Provider or Wallet Provider SHALL discard the values of all unique elements, including at least the ones mentioned in requirement ISSU_35 above, as well as any timestamps, as soon as they are no longer needed. The Provider SHALL NOT communicate these values to any other party inside or outside the EUDI Wallet ecosystem. |
| ISSU_36 | When issuing PIDs, attestations, or WUAs in a batch to a Wallet Unit, a PID Provider, Attestation Provider, or Wallet Provider SHALL ensure that the timestamps in these PIDs, attestations, or WUAs do not enable Relying Parties to conclude that they are part of the same batch (and therefore belong to the same User). *Note: This can be done, for example, by making timestamps sufficiently imprecise that a high number of batches, each issued to a different Wallet Unit, share the same timestamp values (herd privacy).* |
| ISSU_37 | A Wallet Provider SHALL ensure that its Wallet Solution supports the following methods for limiting the number of times a User can present the same attestation to Relying Parties: Method A (Once-only attestations, as specified in requirement ISSU_43 - ISSU_47) and Method B (Limited-time attestations, as specified in requirement ISSU_48 - ISSU_50). In addition, a Wallet Provider MAY ensure that its Wallet Solution supports Method C (Rotating-batch attestations, as specified in requirement ISSU_51 - ISSU_54) or Method D (Per-Relying Party attestations, as specified in requirement ISSU_55 - ISSU_57). *Note: Wallet Solutions, PID Providers, Attestation Providers, and Wallet Providers are free to define and use other methods as well. However, such other methods are out of scope of the ARF.* |
| ISSU_38 | A PID Provider, Attestation Provider or Wallet Provider SHALL have a policy describing which of the methods A, B, C, or D it will use to limit the number of times a Wallet Unit may present a single PID, attestation, or WUA to relying Parties. For each supported method, the policy SHALL also specify how the values for respective parameters for that method, such as technical validity period and batch size, will be chosen. The goal of the policy SHALL be to ensure that the risk of Relying Party linkability is mitigated to an acceptable level, given the (expected) usage of the PID, attestation, or WUA by the User. To determine what an acceptable level of risk is, the PID Provider, Attestation Provider, or Wallet Provider SHALL carry out a risk analysis regarding Relying Party linkability. *Note: If a PID Provider, Attestation Provider, or Wallet Provider issues multiple attestation types, these requirements apply for each type of attestation separately.* |
| ISSU_39 | The Commission SHALL create or reference a profile or extension of the OpenID4VCI specification enabling a PID Provider, Attestation Provider, or Wallet Provider to indicate in their OpenID4VCI Issuer metadata which of the methods A, B, C, or D the Wallet Unit must use for the PID, attestation, or WUA issued. Indicated methods SHALL be ordered by preference. This profile or extension SHALL also enable the PID Provider, Attestation Provider, or Wallet Provider to set the value of parameters to be used by the Wallet Unit for each method (if applicable). *Note: For example, the parameters to be set for method A include the lower limit for unused attestations and the batch size to be requested.* |
| ISSU_40 | PID Providers, Attestation Providers and Wallet Providers SHALL indicate in their OpenID4VCI Issuer metadata at least that either method A or method B must be used for a given type of PID, attestation, or WUA. PID Providers, Attestation Providers, and Wallet Providers MAY additionally indicate that it prefers using method C and/or method D over method A or method B. In such a case, a Wallet Unit supporting method C and/or method D SHALL use that method, while a Wallet Unit not supporting these methods SHALL use method A or method B, as applicable. *Example: An Attestation Provider indicates methods {D, C, A} in their metadata, in that order. A Wallet Unit that supports methods C and D (as well as A and B) then uses method D for this type of attestation. A Wallet Unit supporting methods A, B and C uses method C. A Wallet Unit supporting only methods A and B uses method A.* |
| ISSU_41 | To the maximum extent possible, Wallet Providers, PID Providers, and Attestation Providers SHALL ensure that Users do not notice which of the methods A, B, C, or D is used for their PIDs, attestations, or WUAs.|
| ISSU_42 | To the maximum extent possible, Wallet Providers, PID Providers, and Attestation Providers SHALL ensure that no User action is needed for the re-issuance of PIDs or attestations. *Note: For the topic of re-issuance, see also the [Discussion Paper for Topic B](../../discussion-topics/b-re-issuance-and-batch-issuance-of-pids-and-attestations.md).* |

###### Method A: Once-only attestations <!-- omit from toc -->

The requirements in this subsection specify the Wallet Unit's behaviour when it
is using Method A for a given type of PID, attestation, or WUA. For more
information on this method, please refer to
[Section 3.2 of the Discussion Paper for Topic A](../../discussion-topics/a-privacy-risks-and-mitigations.md#32-method-a-once-only-attestations).

| **Index** | **Requirement specification** |
|-----------|--------------|
| ISSU_43 | The Wallet Unit SHALL request the PID Provider, Attestation Provider, or Wallet Provider to issue PIDs, attestations, or WUAs in batches to the Wallet Unit. All PIDs, attestations, or WUAs in a batch SHALL have the same attribute values and the same technical validity period. |
| ISSU_44 | The Wallet Unit SHALL present each PID, attestation, or WUA only once to a Relying Party, except when it has fallen back to Method B as specified below, or to another available method. |
| ISSU_45 | The Wallet Unit SHALL have a lower limit for the number of unused PIDs, attestations, or WUAs it holds, and SHALL request the issuance of a new batch when this limit is reached. During the first issuance of a new PID, attestation, or WUA, see requirement ISSU_39, the PID Provider, Attestation Provider or Wallet Provider SHALL inform the Wallet Unit about the value of the lower limit and the size of the batch to be requested. |
| ISSU_46 | If the Wallet Unit must request a new batch of PIDs, attestations, or WUAs, but is not able to do so because it is offline, the Wallet Unit SHALL warn the User that they are about to lose the possibility to present this PID or attestation to a Relying Party (or any PID or attestation, in case of the WUA) and request them to connect their device to the internet. |
| ISSU_47 | If the Wallet Unit has run out of unused PIDs, attestations, or WUAs, but is not able to request a new batch because it is offline, it SHALL fall back to method B (see requirement 6), or another available method. This means that, when requested by a Relying Party, the Wallet Unit SHALL again present one of the already used PIDs, attestations or WUAs. The Wallet Unit SHALL return to using method A as soon as it is able to go online and request a new batch of PIDs, attestations or WUAs. |

###### Method B: Limited-time attestations <!-- omit from toc -->

The requirements in this subsection specify the Wallet Unit's behaviour when it
is using Method B for a given type of PID, attestation, or WUA.
[Section 3.2 of the Discussion Paper for Topic A](../../discussion-topics/a-privacy-risks-and-mitigations.md#32).

| **Index** | **Requirement specification** |
|-----------|--------------|
| ISSU_48 | The Wallet Unit SHALL request the PID Provider, Attestation Provider, or Wallet Provider to issue a single PID, attestation, or WUA to the Wallet Unit.|
| ISSU_49 | The Wallet Unit SHALL present that PID, attestation or WUA multiple times to the same Relying Party, or to different Relying Parties, when requested to do so. |
| ISSU_50 | The Wallet Unit SHALL request the PID Provider, Attestation Provider, or Wallet Provider to re-issue a PID, attestation, or WUA some time before the one existing in the Wallet Unit expires. The PID Provider, Attestation Provider, or Wallet Provider SHALL inform the Wallet Unit about the moment at which the Wallet Unit must request the re-issuance of a PID, attestation, or WUA, relative to the expiration date of the existing one. *Note: It is the responsibility of Relying Parties to validate whether a presented PID, attestation, or WUA is temporally valid. A Wallet Unit is allowed to present a PID, attestation, or WUA even if its expiration date is in the past.* |

###### Method C: Rotating-batch attestations <!-- omit from toc -->

The requirements in this subsection specify the Wallet Unit's behaviour when it
is using Method C for a given type of PID, attestation, or WUA.

| **Index** | **Requirement specification** |
|-----------|--------------|
| ISSU_51 | The Wallet Unit SHALL request the PID Provider, Attestation Provider, or Wallet Provider to issue PIDs, attestations, or WUAs in batches to the Wallet Unit. All PIDs, attestations, or WUAs in a batch SHALL have the same attribute values and the same technical validity period. |
| ISSU_52 | When a presentation of attributes is requested by multiple Relying Parties, the Wallet Unit SHALL present each PID, attestation, or WUA in a batch once, in a random order.|
| ISSU_53 | When all PIDs, attestations, or WUAs in a batch have been presented once, the Wallet Unit SHALL reset the batch, and start presenting each PID, attestation, or WUA in the batch again in a random order. |
| ISSU_54 | The Wallet Unit SHALL request the PID Provider, Attestation Provider, or Wallet Provider to re-issue a batch of PIDs, attestations, or WUAs, some time before the batch in the Wallet Unit expires. The PID Provider, Attestation Provider, or Wallet Provider SHALL inform the Wallet Unit about the size of the batch and about the moment at which the Wallet Unit must request the re-issuance of a batch, relative to the expiration date of the existing one. |

###### Method D: Per-Relying Party attestations <!-- omit from toc -->

The requirements in this subsection specify the Wallet Unit's behaviour when it
is using Method D for a given type of PID, attestation, or WUA.

| **Index** | **Requirement specification** |
|-----------|--------------|
| ISSU_55 | The Wallet Unit SHALL present a different PID, attestation, or WUA to each different Relying Party upon their request. This means that it SHALL comply with Method A for such Relying Parties. |
| ISSU_56 | In case a given Relying Party requests attributes from a given type of PID, attestation, or WUA multiple times, the Wallet Unit MAY present the same PID, attestation or WUA to this Relying Party each time. If it does, it SHALL comply with Method B or Method C for such a Relying Party. |
| ISSU_57 | The Wallet Unit SHALL keep track of which PID, attestation, or WUA it has presented to which Relying Party, using the unique Relying Party identifier from the Relying Party access certificate. |

###### E - HLRs for re-issuance and batch issuance of PIDs, attestations and WUAs <!-- omit from toc -->

These HLRs were added as a result of the discussions of Topic B,
re-issuance and batch issuance of PIDs, attestations and WUAs. For more background
information on these requirements, please refer to [Sections 6.6.2.7](../../architecture-and-reference-framework-main.md#6627-batch-issuance)
and
[6.6.5.2](../../architecture-and-reference-framework-main.md#6652-pid-or-attestation-re-issuance) of the ARF main document, and to the [Discussion Paper for Topic B](../../discussion-topics/b-re-issuance-and-batch-issuance-of-pids-and-attestations.md).

| **Index** | **Requirement specification** |
|-----------|--------------|
| ISSU_58 | A Wallet Unit SHALL give its User the option to manually initiate a re-issuance process for any of the PIDs or attestations in their Wallet Unit. *Note: This requirement does not apply for WUAs, since Users must not be involved in the management of WUAs.* |
| ISSU_59 | After a successful re-issuance, a Wallet Unit SHALL compare the attribute values of the re-issued PID or attestation with those of the existing PID or attestation, and SHALL notify the User in case of any differences. *Note: This requirement does not apply for WUAs, since Users must not be involved in the management of WUAs.* |
| ISSU_60 | A Wallet Unit SHALL gracefully handle situations in which re-issuance of a PID,  attestation, or WUA is refused by the PID Provider, Attestation Provider, or Wallet Provider,for example by attempting a retry after an appropriate delay. |
| ISSU_61 | A Wallet Unit SHALL support PID or attestation first-time batch issuance with a single User authentication, regardless of the size of the batch. *Notes: - See also requirement WIAM_14. - This requirement does not apply for WUAs, since Users must not be involved in the management of WUAs.* |
| ISSU_62 | If a PID, attestation, or WUA was successfully re-issued because the value of one or more of its attributes was changed (including attributes being added or deleted), a Wallet Unit SHOULD delete the correct pre-existing PID, attestation, or WUA. *Notes: - It is up to the Wallet Unit, possibly using metadata provided by the PID Provider, Attestation Provider, or Wallet Provider using the [OpenID4VCI] protocol, to determine the PID, attestation, or WUA to be deleted. - Additionally, per requirement VCR_09, the PID Provider, Attestation Provider, or Wallet Provider revokes the pre-existing PID, attestation, or WUA.* |
| ISSU_63 | PID Providers, Attestation Providers, Wallet Providers, and Wallet Units SHALL support the features of [OpenID4VCI] enabling the re-issuance of all PIDs, attestations, and WUAs. |
| ISSU_64 | PID Providers, Attestation Providers, Wallet Providers, and Wallet Units SHALL support the features of [OpenID4VCI] enabling the batch issuance of all PIDs, attestations, and WUAs. |
| ISSU_65 | The common OpenID4VCI protocol referenced in requirement ISSU_01, or an EUDI Wallet-specific extension or profile thereof, SHALL enable a PID Provider, Attestation Provider or Wallet Provider to verify that a re-issued PID, attestation, or WUA is bound to the same WSCD to which the existing PID, attestation, or WUA is bound. *Note: This can be done, for instance, by requiring that OAuth 2.0 Demonstrating Proof of Possession (DPoP) [RFC 9449] is used for each Refresh Token, and that the public key in the DPoP proof is identical to the public key in the existing PID, attestation, or WUA issued to the Wallet Unit previously.* |

#### A.2.3.11 Topic 11 - Pseudonyms

##### Description <!-- omit from toc -->

Wallet Units will support generating pseudonyms for Users in compliance with the
W3C WebAuthn API specification, [W3C WebAuthn](https://www.w3.org/TR/2021/REC-webauthn-2-20210408/). On a high level, this means that
the WSCD in the Wallet Unit will be able to create key pairs. The public keys of
these pairs function as pseudonyms for the User. Only the User can use these
pseudonyms, since the WSCD authenticates the User before allowing a pseudonym to
be used, see requirement WIAM_14. The Wallet Unit will keep an internal structure
to associate each pseudonym (public key) with a specific Relying Party, based on
the Relying Party unique identifier in the Relying Party Instance access
certificate mentioned in requirement Reg_32.

Pseudonyms were discussed with Member States in Topic E. These
discussions included the use cases for which Wallet Units must support
pseudonyms and the HLRs for the technical specification of how it must be
implemented. The below HRLs are the result of this discussion. For more
background information on these requirements, please refer to the [Discussion
Paper for Topic E](../../discussion-topics/e-pseudonyms-including-user-authentication-mechanism.md).

Note: As specified in requirement PA_21, the Commission will create or reference a technical specification containing a profile or extension of the [W3C WebAuthn] specification. The HLRs below are in fact requirements to be fulfilled by this technical specification.

###### A. HLRs related to Use Cases <!-- omit from toc -->

| **Index** | **Requirement specification** |
|-----------|---------------------------------------|
| PA_01 | A Wallet Unit SHALL enable a User to generate a Pseudonym and register it at a Relying Party.|
| PA_02 | A Wallet Unit SHALL enable a User to authenticate with a Pseudonym towards a Relying Party if the Wallet Unit was used previously to register the Pseudonym for the same Relying Party. |
| PA_03 | A Wallet Unit SHALL be able to perform the actions specified in the above two requirements independently of whether the interaction with the Relying Party is initiated on the same device hosting the Wallet Instance or on a device different from the one hosting the Wallet Instance. |
| PA_04 | A Wallet Unit SHALL enable the User to use multiple different Pseudonyms at a given Relying Party. |
| PA_05 | A Wallet Unit SHOULD enable a User to freely choose a User alias for each Pseudonym registered at a Relying Party. Setting an alias SHOULD be optional for the User. The User SHOULD be able to change the alias for any Pseudonym. |
| PA_06 | A Wallet Unit SHALL enable a User to choose which Pseudonym to authenticate with towards a Relying Party, if multiple Pseudonyms are registered for this Relying Party. The Wallet Unit SHOULD present the User with the aliases of the applicable Pseudonyms, if assigned, when making this choice. |
| PA_07 | A Wallet Unit SHOULD enable a User to delete a Pseudonym. |
| PA_08 | A Wallet Unit SHOULD enable to the User to manage pseudonyms within the Wallet Unit in a user-friendly and transparent manner. Users SHOULD be informed about when and with which Relying Party their pseudonyms were used and be able to view a complete transaction log (including canceled or unsuccessful transactions). |
| PA_09 | A Wallet Unit SHOULD enable the User to see all existing pseudonyms, including the associated Relying Party. |

###### B. HLRs related to Relying Parties <!-- omit from toc -->

| **Index** | **Requirement specification** |
|-----------|---------------------------------------|
| PA_10 | A Relying Party SHALL be able to verify that a User is registering a Pseudonym using a non-revoked Wallet Unit. |
| PA_11 | A Relying Party SHALL be able to verify that a User is authenticating with a Pseudonym using a non-revoked Wallet Unit. |
| PA_12 | If Wallet Unit is used to register a Pseudonym at a Relying Party in combination with a PID, attestation or WUA being presented to the same Relying Party, then this Relying Party SHALL be able to verify that the same User performed both actions. |
| PA_13 | The Relying Party SHALL be able to validate that the pseudonym presented to them belongs to the User presenting it. |

###### C. HLRs related to privacy <!-- omit from toc -->

| **Index** | **Requirement specification** |
|-----------|---------------------------------------|
| PA_14 | A Wallet Unit SHALL store the information necessary for authenticating with a Pseudonym in its WSCA/WSCD. |
| PA_15 | A Relying Party SHALL NOT be able to derive the User’s true identity, or any data identifying the User, from the Pseudonym value received by the Relying Party. |
| PA_16 | A Wallet Unit SHALL NOT reveal the same Pseudonym to different Relying Parties unless the User explicitly chooses otherwise. |
| PA_17 | It SHALL NOT be possible to correlate Pseudonyms based on their values nor on other metadata sent by the Wallet Unit during registration and authentication, meaning that colluding Relying Parties SHALL NOT able to conclude that different Pseudonyms belong to the same User. |
| PA_18 | The Wallet Unit SHALL ensure that Pseudonyms contain sufficient entropy to make the chance of colliding Pseudonyms (meaning two Users having the same Pseudonym value for the same Relying Party) negligible. |
| PA_19 | A Wallet Unit SHALL NOT share the User's optionally assigned Pseudonym aliases with any Relying Party. |
| PA_20 | The Wallet Unit SHOULD be able to verify the identity of a Relying Party when a User registers a Pseudonym or authenticates with a Pseudonym. |

###### D. HLRs related to interoperability <!-- omit from toc -->

| **Index** | **Requirement specification** |
|-----------|---------------------------------------|
| PA_21 | The Commission SHALL create or reference a technical specification containing a profile or extension of the [W3C WebAuthn] specification compliant with the HLRs specified in this Topic. This specification SHALL contain all details necessary for Wallet Units and Relying Parties to generate, register, and use Pseudonyms. |
| PA_22 | Wallet Providers SHALL ensure that their Wallet Solution supports the [W3C WebAuthn] specification and the technical specification meant in requirement PA_21. |

#### A.2.3.12 Topic 12 - Attestation Rulebooks

##### Description <!-- omit from toc -->

Article 45e of the [European Digital Identity Regulation] sets up the legal
basis for the Commission to "where necessary, establish specifications and
procedures for the catalogue of attributes and schemes for the attestation of
attributes and verification procedures for qualified electronic attestations of
attributes". As described in [Section 5.6 of the ARF main document](../../architecture-and-reference-framework-main.md#56-catalogues), these 'schemes for the
attestation of attributes' will be described in so-called Attestation Rulebooks.
A separate Rulebook will be created for each type of attestation. This Topic
describes the high-level requirements for the Attestation Rulebooks that will
specify the details of new types of attestations.

Attestation Rulebooks will be written by Attribute Schema Providers, a role
which can be assumed by different types of organisation. The goal of this Topic
is to ensure that all Rulebooks that will be written in the future will contain
the same type of information and the same level of detail, such that all
attestations are interoperable.

Attestation Rulebooks may be registered and published in a publicly accessible
catalogue, as described in [Topic 25](#a2325-topic-25---unified-definition-and-controlled-vocabularies-for-attributes).

##### HLRs <!-- omit from toc -->

###### A. Requirements regarding attestation formats <!-- omit from toc -->

| **Index** | **Requirement specification** |
|-----------|--------------|
| ARB_01 | The Schema Provider for an Attestation Rulebook describing a type of attestation that is a QEAA or a PuB-EAA SHALL specify that one or more of the following two common format(s) must be used for these attestations: - The format specified in ISO/IEC 18013-5, see [ISO18013-5]. - The format specified in "SD-JWT-based Verifiable Credentials (SD-JWT VC)", see [SD-JWT-VC]. |
| ARB_01a | The Schema Provider for an Attestation Rulebook describing a type of attestation that is a non-qualified EAA SHALL specify that one or more of the following three common format(s) must be used for these attestations: - The format specified in ISO/IEC 18013-5, see [ISO18013-5]. - The format specified in "SD-JWT-based Verifiable Credentials (SD-JWT VC)", see [SD-JWT-VC]. - The format specified in “W3C Verifiable Credentials Data Model”, see [W3C VCDM v2.0]. |
| ARB_01b | The Schema Provider for an Attestation Rulebook describing attestations using the format specified in [SD-JWT VC] SHALL ensure that these attestations comply with the 'SD-JWT VCs' profile specified in [HAIP]. |
| ARB_02 | The Schema Provider for an Attestation Rulebook SHALL analyse whether it must be possible for a User to present that type of attestation when the Wallet Unit and the Relying Party are in proximity and attestations are presented without using the internet. If so, the Attestation Rulebook SHALL specify that the attestations must be issued in the ISO/IEC 18013-5-compliant mdoc format. *Note: In theory, it is possible to use SD-JWT VC-compliant attestations in proximity use cases. In practice, however, the only protocol available to request and release SD-JWT VC-compliant attestations between a Wallet Unit and a Relying Party Instance is OpenID4VP. That protocol cannot be used without internet connectivity.* |
| ARB_03 | The Schema Provider for an Attestation Rulebook MAY specify in the Attestation Rulebook that that type of attestation must be issued in the [SD-JWT VC]-compliant format, provided the [SD-JWT VC] specification has been approved by an EU standardisation body or by the European Digital Identity Cooperation Group established pursuant to [Article 46e](https://eur-lex.europa.eu/legal-content/EN/ALL/?uri=CELEX:32024R1183#d1e4536-1-1)(1) of the [European Digital Identity Regulation].|
| ARB_04 | If an Attestation Rulebook specifies that a type of attestation can be issued in a format compliant with [W3C VCDM v2.0], the Schema Provider for that Attestation Rulebook SHALL ensure the Rulebook references one or more documents specifying in detail how a Relying Party can request attributes from a such an attestation, and how a User can selectively disclose attributes from such an attestation. Moreover, these referenced documents SHALL be approved by an EU standardisation body or by the European Digital Identity Cooperation Group established pursuant to [Article 46e](https://eur-lex.europa.eu/legal-content/EN/ALL/?uri=CELEX:32024R1183#d1e4536-1-1)(1) of the [European Digital Identity Regulation]. |

###### B. Requirements regarding attestation types <!-- omit from toc -->

| **Index** | **Requirement specification** |
|-----------|--------------|
| ARB_05 | The Schema Provider for an Attestation Rulebook SHALL specify a value for the attestation type, which SHALL be unique within the scope of the EUDI Wallet ecosystem. *Notes: - In ISO/IEC 18013-5, the attestation type is called 'document type' and is included as a "docType" key-value pair in both the mdoc request and the mdoc response. Also, a method for generating unique attestation type values is recommended. - In OpenID4VP, the attestation type is included in the "id" property of an Input Descriptor in a Presentation Request. - In [SD-JWT VC], the attestation type is called 'SD-JWT VC type' and is included as a 'vct' claim in the SD-JWT VC.* |

###### C. Requirements regarding attestation attribute schemas <!-- omit from toc -->

| **Index** | **Requirement specification** |
| -----| --------|
| ARB_06 | The Schema Provider for an Attestation Rulebook SHALL define all attributes that an attestation of that type may contain. This definition SHALL first describe the semantics of each attribute in an encoding-independent manner and SHALL subsequently for each attribute specify an ISO/IEC 18013-5-compliant format, an SD-JWT VC-compliant format, or both, as needed given the choices made according to ARB_01 - ARB_04. |
| ARB_06a | For ISO/IEC 1803-5-compliant attestations, the Attestation Rulebook SHALL define each attribute within an attribute namespace. An attribute namespace SHALL fully define the identifier, the syntax, and the semantics of each attribute within that namespace. An attribute namespace SHALL have an identifier that is unique within the scope of the EUDI Wallet ecosystem, and each attribute identifier SHALL be unique within that namespace. *Note: In ISO/IEC 18013-5, namespaces are discussed and a method for generating unique namespace identifiers is recommended.*|
| ARB_06b | For [SD-JWT VC]-compliant attestations, the Schema Provider for the Attestation Rulebook SHALL ensure that each claim name is either included in the IANA registry for JWT claims, or is a Public Name as defined in [RFC 7519]. *Note: [SD-JWT VC] does not discuss how to avoid conflicting claim names. Since SD-JWTs are a special kind of JWTs, the methods specified in RFC 7519 are applicable.*|
| ARB_07 | When determining the attributes to be included in a new attestation type, the Schema Provider for the applicable Attestation Rulebook SHOULD consider referring to attributes that are already included in the catalogue specified in [Topic 25](#a2325-topic-25---unified-definition-and-controlled-vocabularies-for-attributes) + [26](#a2326-topic-26---catalogue-of-attestations), rather than unnecessarily re-defining all attributes within a new namespace.|
| ARB_08 | The Schema Provider for an Attestation Rulebook SHOULD, when specifying a new attribute, take into consideration existing conventions for attribute identifier values and attribute syntaxes. *Note: These conventions may depend on the format of the attestation, i.e., CBOR for ISO/IEC 18013-5-compliant attestations or JSON for SD-JWT VC-compliant attestations.* |
| ARB_09 | The Schema Provider for an Attestation Rulebook SHALL specify, for each attribute in the attestation, whether the presence of that attribute is mandatory, optional, or conditional. |
| ARB_10 | The Schema Provider for an Attestation Rulebook for an ISO/IEC 18013-5 compliant attestation MAY define a domestic namespace to specify attributes that are specific to that Rulebook and are not included in the applicable EU-wide or sectoral namespace. All requirements for namespaces in this Topic also apply for domestic namespaces. |
| ARB_11 | The Schema Provider for an Attestation Rulebook describing a type of attestation that is a QEAA or a PuB-EAA SHALL include in the Rulebook an attribute as meant in [Annex V](https://eur-lex.europa.eu/legal-content/EN/ALL/?uri=CELEX:32024R1183#d1e40-54-1) point a) and [Annex VII](https://eur-lex.europa.eu/legal-content/EN/ALL/?uri=CELEX:32024R1183#d1e40-56-1) point a) of the [European Digital Identity Regulation]. This attribute SHALL reference the technical specification meant in ARB_25. |
| ARB_12 | The Schema Provider for an Attestation Rulebook describing a type of attestation that is a non-qualified EAA SHOULD include an attribute in the Rulebook indicating that the attestation is an EAA. This attribute SHALL reference the technical specification meant in ARB_25. |
| ARB_13 | The Schema Provider for an Attestation Rulebook describing a type of attestation that is a QEAA SHALL include in the Rulebook one or more attributes or metadata representing the set of data meant in [Annex V](https://eur-lex.europa.eu/legal-content/EN/ALL/?uri=CELEX:32024R1183#d1e40-54-1) point b) of the [European Digital Identity Regulation]. |
| ARB_14 | The Schema Provider for an attestation Rulebook describing a type of attestation that is a PuB-EAA SHALL include in the Rulebook one or more attributes or metadata representing the set of data meant in [Annex VII](https://eur-lex.europa.eu/legal-content/EN/ALL/?uri=CELEX:32024R1183#d1e40-56-1) point b) of the [European Digital Identity Regulation]. |
| ARB_15 | The Schema Provider for an Attestation Rulebook describing a type of attestation that is a non-qualified EAA SHOULD include in the Rulebook one or more attributes or metadata representing the set of data meant in [Annex V](https://eur-lex.europa.eu/legal-content/EN/ALL/?uri=CELEX:32024R1183#d1e40-54-1) point b) of the [European Digital Identity Regulation]. |
| ARB_16 | The Schema Provider for an Attestation Rulebook describing a type of attestation that is a QEAA or a PuB-EAA SHALL include in the Rulebook one or more attributes representing the set of data meant in [Annex V](https://eur-lex.europa.eu/legal-content/EN/ALL/?uri=CELEX:32024R1183#d1e40-54-1) point c) or [Annex VII](https://eur-lex.europa.eu/legal-content/EN/ALL/?uri=CELEX:32024R1183#d1e46-55-1) point c) of the [European Digital Identity Regulation]. |
| ARB_17 | The Schema Provider for an Attestation Rulebook describing a type of attestation that is a non-qualified EAA SHOULD include in the Rulebook one or more attributes representing the set of data meant in [Annex V](https://eur-lex.europa.eu/legal-content/EN/ALL/?uri=CELEX:32024R1183#d1e40-54-1) point c) of the [European Digital Identity Regulation]. |
| ARB_18 | The Schema Provider for an Attestation Rulebook describing a type of attestation that is a QEAA or a PuB-EAA SHALL include in the Rulebook one or more attributes or metadata representing the set of data meant in [Annex V](https://eur-lex.europa.eu/legal-content/EN/ALL/?uri=CELEX:32024R1183#d1e40-54-1) point e) or [Annex VII](https://eur-lex.europa.eu/legal-content/EN/ALL/?uri=CELEX:32024R1183#d1e40-56-1) point e) of the [European Digital Identity Regulation]. |
| ARB_19 | The Schema Provider for an Attestation Rulebook describing a type of attestation that is a non-qualified EAA SHOULD include in the Rulebook one or more attributes representing the set of data meant in [Annex V](https://eur-lex.europa.eu/legal-content/EN/ALL/?uri=CELEX:32024R1183#d1e40-54-1) point e) of the [European Digital Identity Regulation]. |
| ARB_20 | The Schema Provider for an Attestation Rulebook describing a type of attestation that is a QEAA or a PuB-EAA SHALL include in the Rulebook one or more attributes or metadata representing the location meant in [Annex V](https://eur-lex.europa.eu/legal-content/EN/ALL/?uri=CELEX:32024R1183#d1e40-54-1) point h) or [Annex VII](https://eur-lex.europa.eu/legal-content/EN/ALL/?uri=CELEX:32024R1183#d1e40-56-1) point h) of the [European Digital Identity Regulation]. For a QEAA, this location SHALL indicate at least the URL at which a machine-readable version of the trust anchor to be used for verifying the QEAA can be found or looked up. For a PuB-EAA, this location SHALL indicate at least the URL at which a machine-readable version of the qualified certificate that signed the PuB-EAA can be found or looked up. |
| ARB_21 | The Schema Provider for an Attestation Rulebook describing a type of attestation that is a non-qualified EAA SHOULD include in the Rulebook one or more attributes or metadata representing the location at which a machine-readable version of the trust anchor to be used for verifying the EAA can be found or looked up.*Note: What this location indicates precisely is dependent on the nature of the mechanism used for distributing trust anchors; see requirement ARB_26.* |

###### D. Miscellaneous requirements <!-- omit from toc -->

| **Index** | **Requirement specification** |
|-----------|--------------------|
| ARB_22 | The Schema Provider for an Attestation Rulebook SHALL specify all technical details necessary to ensure interoperability, security, and privacy of that attestation. *Note: An Attestation Rulebook may also specify requirements regarding how the Wallet Unit must display the attestation and the attributes in it to the User.* |
| ARB_23 | The Schema Provider for an Attestation Rulebook describing a type of attestation that is a QEAA or a PuB-EAA SHALL specify which of the revocation mechanisms specified in [Topic 7](#a237-topic-7---attestation-revocation-and-revocation-checking) SHALL be supported by that attestation. |
| ARB_24 | The Schema Provider for an Attestation Rulebook describing a type of attestation that is a non-qualified EAA SHALL specify whether that type of EAA must be revocable. If an EAA type must be revocable, the relevant Rulebook SHALL determine which of the revocation mechanisms specified in [Topic 7](#a237-topic-7---attestation-revocation-and-revocation-checking) SHALL be supported by that attestation. |
| ARB_25 | The Commission SHALL take measures to ensure that the following information is included in a technical specification: - The identifier of the attribute containing the indication meant in [Annex V](https://eur-lex.europa.eu/legal-content/EN/ALL/?uri=CELEX:32024R1183#d1e40-54-1) point a) and [Annex VII](https://eur-lex.europa.eu/legal-content/EN/ALL/?uri=CELEX:32024R1183#d1e40-56-1) point a). - The syntax and semantics of this attribute in case the attestation is a QEAA, in case it is PuB-EAA, and in case it is a non-qualified EAA. |
| ARB_26 | The Schema Provider for an Attestation Rulebook describing a type of attestation that is a non-qualified EAA SHOULD define in the Rulebook: - mechanisms allowing a Wallet Unit to verify that the EAA Provider is authorised or registered to issue this type of EAA. - mechanisms allowing a Relying Party to obtain, in a trustworthy manner, the trust anchor(s) of the EAA Providers issuing this type of EAA. |
| ARB_27 | The Schema Provider for an Attestation Rulebook describing a type of attestation that is a QEAA, PuB-EAA, or non-qualified EAA SHOULD specify in the Rulebook whether a Relying Party receiving the attestation must request and verify a PID. *Note: Relying Parties can only do so in a trustworthy manner if Wallet Units are able to provide a proof that the private keys of the attestation and the PID are stored in the same WSCD, in accordance with the requirements in Topic 18.* |

#### A.2.3.13 Topic 13 - Developing a Wallet Unit architecture based on Secure Element

There are no HLRs for this Topic.

#### A.2.3.14 Topic 14 - Developing a Wallet Unit architecture based on External Token

There are no HLRs for this Topic.

#### A.2.3.15 Topic 15 - Developing a Wallet Unit architecture based on Remote HSM

There are no HLRs for this Topic.

#### A.2.3.16 Topic 16 - Signing documents with a Wallet Unit

##### Description <!-- omit from toc -->

A Wallet Unit SHALL enable its User to create qualified electronic
signatures or seals. This goal can be reached by using signature or seal
creation capabilities of the Wallet Unit as a part of a local QSCD,
or by using a remote QSCD managed by a QTSP.

This Topic contains high-level requirements related to the creation of
Qualified Electronic Signatures using a Wallet Unit.

##### HLRs <!-- omit from toc -->

###### A. Requirement for Wallet Providers <!-- omit from toc -->

| **Index** | **Requirement specification** |
|-----------|------------|
| QES_01 | Wallet Providers SHALL ensure that each User has the possibility to receive a qualified certificate for Qualified Electronic Signatures, bound to a QSCD, that is either local, external, or remotely managed in relation to the Wallet Instance. |
| QES_02 | Wallet Providers SHALL ensure that each User who is a natural person has, at least for non-professional purposes, free-of-charge access to a Signature Creation Application which allows the creation of free-of-charge Qualified Electronic Signatures using the certificates referred to in QES_01. Wallet Providers SHALL ensure that: - The Signature Creation Application SHALL, as a minimum, be capable of signing or sealing User-provided data and Relying Party-provided data. - The Signature Creation Application SHALL be implemented as part of a Wallet Solution or external to it (by providers of trust services or by Relying Parties). - The Signature Creation Application SHALL be able to generate signatures or seals in formats compliant with at least the mandatory formats referred to in QES_08. *Notes: - Signature Creation Application (SCA): see definition in the ETSI TS 119 432 standard. - If the SCA is external to the Wallet Solution, it may be for example a separate mobile application, or be hosted remotely, for instance by the QTSP or by a Relying Party.* |
| QES_03 | For the use of the qualified certificate referred to in QES_01, Wallet Providers SHALL ensure that a Wallet Unit implements secure authentication of the User, as well as signature or seal invocation capabilities, as a part of a local, external or remote QSCD. |
| QES_04 | Wallet Providers SHALL enable their Wallet Units to interface with QSCDs using protocols and interfaces necessary for the implementation of secure User authentication and signature or seal functionality. *Note: In a Relying Party-centric flow, the remote QTSP will likely be selected by the Relying Party, which implies the QSCD is managed by the remote QTSP. In a Wallet Unit-driven flow, the User should be able to choose the QSCD.* |
| QES_05 | Wallet Providers SHALL enable their Wallet Units to be used for User enrolment to a remote QES Provider (i.e., a QTSP offering remote QES), except where the Wallet Unit interfaces with local or external QSCDs. |
| QES_06 | Wallet Providers SHALL ensure that their Wallet Solution supports at least one of the following options for remote QES signature creation: - remote QES creation through secure authentication to a QTSP signature web portal, - remote QES creation channelled by the Wallet Unit, - remote QES creation channelled by a Relying Party. |
| QES_07 | Wallet Providers SHALL ensure that, where a Signature Creation Application relies on a remote Qualified Signature Creation Device and where it is integrated into a Wallet Instance, it supports the Cloud Signature Consortium API Specification 2.0 [CSC API]. |
| QES_08 | Wallet Providers SHALL ensure that their Wallet Units are able to create signatures or seals in accordance with the mandatory PAdES format as specified in ETSI EN 319 142-1 V1.1.1 (2016-04). In addition, Wallet Providers SHOULD ensure that their Wallet Units are able to create signatures or seals in accordance with the following formats: - XAdES as specified in ETSI EN 319 132-1 V1.2.1 (2022-02), - JAdES as specified in ETSI TS 119 182-1 V1.2.1 (2024-07), - CAdES as specified in ETSI EN 3191 22-1 V1.3.1 (2023-06), and - ASiC as specified in ETSI EN 319 162-1 V1.1.1 (2016-04) and ETSI EN 319 162-2 V1.1.1 (2016-04). |
| QES_09 | Empty |
| QES_10 | Wallet Providers SHALL ensure that, where the Signature Creation Application is implemented as part of the Wallet Unit and is used to generate signatures or seals of the representation of the document or data to be signed or sealed, the Wallet Unit presents the representation of the document or data to be signed or sealed to the User. |
| QES_11 | Wallet Providers SHALL ensure that, where the Signature Creation Application is implemented as part of the Wallet Unit, a Wallet Unit computes the hash or digest of the document or data to be signed through a Signature Create Application component. |
| QES_12 | Wallet Providers SHALL ensure that a Wallet Unit is able to create the signature value of the document or data to be signed either using a local or a remote signing application. *Note: a local signing application is on-device. It may either be embedded in the Wallet Unit or be an external application.* |
| QES_13 | Wallet Providers SHALL ensure that a Wallet Unit provides a log of transactions related to qualified electronic signatures generated by or through the Wallet Unit, allowing the User to view the history of previously signed data or documents, according to the requirements in [Topic 19](#a2319-topic-19---user-navigation-requirements-dashboard-logs-for-transparency). *Note: If the signature is generated by a remote Signature Creation Application, the Wallet is at minimum used to authenticate the User to the remote QTSP and to obtain the User's consent for the usage of the private signing key. The logs then record information about these processes.* |
| QES_14 | Wallet Providers SHALL ensure that the User will be able to explicitly authorise the creation of a qualified electronic signature or seal through their Wallet Unit. |
| QES_15 | Wallet Providers SHALL ensure that a Wallet Unit can verify, in remote signature creation scenarios, that the qualified electronic signature or seal creation device is part of a qualified service, which is carried out by a qualified trust service provider.  |
| QES_16 | Wallet Providers SHOULD ensure that a Wallet Unit supports multiple-signing scenarios where multiple signatories are required to sign the same document or data. |
| QES_17 | Wallet Providers SHALL ensure that Wallet Units provide a signature creation confirmation upon the creation of a qualified electronic signature, informing the User about the outcome of the signature creation process. *Note: See also QES_17a.* |
| QES_17a | If the Signature Creation Application is external to the Wallet Unit, after the User authorises the usage of the private signing key, the Signature Creation Application SHALL return the outcome of the signature creation process to the Wallet Unit. |
| QES_18 | Wallet Providers SHALL configure at least one default qualified signing service in the Wallet Unit. |
| QES_19 | Wallet Providers SHALL ensure that, where the Signature Creation Application is implemented as part of the Wallet Unit, a Wallet Unit supports ETSI TS 119 101 (Electronic Signatures and Infrastructures (ESI); Policy and security requirements for applications for signature creation and signature validation) when using signing keys managed by the QSCD, whether locally, externally, or remotely in relation to the Wallet Instance. |
| QES_20 | Empty |
| QES_21 | Empty |
| QES_22 | Empty |

###### B. Requirements for QTSPs <!-- omit from toc -->

| **Index** | **Requirement specification** |
|-----------|--------------|
| QES_23 | QTSPs providing the remote QES part of a Wallet Solution SHALL support: 1. ETSI TS 119 431-1 (Electronic Signatures and Infrastructures (ESI); Policy and security requirements for trust service providers; Part 1: TSP service components operating a remote QSCD / SCDev), 2. ETSI TS 119 431-2 (Electronic Signatures and Infrastructures (ESI); Policy and security requirements for trust service providers; Part 2: TSP service components supporting AdES digital signature creation), 3. ETSI TS 119 432 (Electronic Signatures and Infrastructures (ESI); Protocols for remote digital signature creation). Wallet Providers and QTSPs providing the remote QES part of a Wallet Solution SHALL comply with Sole Control Assurance Level (SCAL) 2 as defined in CEN EN 419 241-1 (Trustworthy Systems Supporting Server Signing - Part 1: General System Security Requirements). |
| QES_24 | QTSPs providing the Signature Creation Application as part of the remote QES part of a Wallet Solution SHALL support ETSI TS 119 101 (Electronic Signatures and Infrastructures (ESI); Policy and security requirements for applications for signature creation and signature validation). |

###### C. Requirements for Relying Parties <!-- omit from toc -->

| **Index** | **Requirement specification** |
|-----------|--------------|
| QES_24a | Relying Parties providing the Signature Creation Application in a Relying Party-centric flow SHALL support ETSI TS 119 101 (Electronic Signatures and Infrastructures (ESI); Policy and security requirements for applications for signature creation and signature validation). |

###### D. Requirements for the Commission <!-- omit from toc -->

| **Index** | **Requirement specification** |
|-----------|------------|
| QES_25 | Empty |
| QES_26 | Empty |

#### A.2.3.17 Topic 17 - Identity matching

##### Description <!-- omit from toc -->

Users would like to use their PID in their Wallet Unit to access their existing
online account(s), even if their PID attribute values are not exactly the same
as those in their account(s). Users regularly need to log in to cross-border
services offered by public sector bodies. Identity matching enables them to use
their Wallet Unit to do so.

##### HLRs <!-- omit from toc -->

There are no HLRs for this Topic.

#### A.2.3.18 Topic 18 - Combined presentations of attributes

##### Description <!-- omit from toc -->

This Topic discusses the combined presentation of attributes by a Wallet
Instance to a Relying Party. 'Combined presentation' here refers to a
transaction in which the Relying Party requests attributes of the same User from
multiple attestations (PID and/or (Q)EAAs) in a single request and receives
those attributes in a single response. These attestations can have been provided
to the Wallet Unit by one or by multiple PID Providers or Attestation Providers.

This Topic answers the following questions:

- How can a Relying Party request for a combined presentation of attributes?
- How can a Wallet Unit receiving such a request present the attributes in a
combined manner?
- How can the Relying Party verify the authenticity of all released attributes
in a combined response?
- How can the Relying Party verify whether all released attributes were issued
to the same User?

Regarding the last question:

- The subject may be either a natural person or a legal person.
- However, use cases such as delegation or legal representation, where
 the Relying Party may request attributes that are originally part of
 multiple distinct attestations that were not issued to the same User,
 are not combined presentations and are out of scope of this Topic.

##### HLRs <!-- omit from toc -->

###### A. Functional requirements for ecosystem components <!-- omit from toc -->

| **Index** | **Requirement specification** |
|-----------|-----------------|
| ACP_01 | Wallet Units SHALL support the features in [ISO18013-5] and/or [OpenID4VP] (as applicable) that allow requesting and releasing attributes from multiple attestations in a single request and response. |
| ACP_02 | Relying Parties SHOULD support the features in [ISO18013-5] and/or [OpenID4VP] (as applicable) that allow requesting and releasing attributes from multiple attestations in a single request and response. |
| ACP_03 | Empty |
| ACP_04 | If a Wallet Unit determines it must release multiple attestations to a Relying Party in a combined presentation of attributes, it SHOULD request a proof from the WSCA that the WSCA manages all of the private keys of these attestations. |
| ACP_05 | If, as a result of ACP_04, the Wallet Unit receives such a proof from the WSCA, it SHALL include this proof in the response message containing the combined presentation of attributes and send it to the Relying Party. |
| ACP_06 | If a Relying Party receives a combined presentation of attributes including a proof as meant in ACP_04, it SHOULD verify this proof to validate that the attestations in this presentation were issued to the same User. |

###### B. Process requirements <!-- omit from toc -->

| **Index** | **Requirement specification** |
|-----------|----------------|
| ACP_07 | During issuance of an attestation, an Attestation Provider SHOULD be able to request that the private key for the new attestation is managed by the same WSCD as the private key of a PID or another attestation already existing on the Wallet Unit, provided that the Attestation Provider has verified during the issuance process that the new attestation indeed belongs to the User of that existing PID or attestation. *Note: Also see requirement WUA_10 in [Topic 09](#a239-topic-9---wallet-unit-attestation).* |
| ACP_08 | When receiving a combined presentation of attributes, a Relying Party SHOULD NOT refuse the attestations solely because a proof as meant in ACP_04 is absent. |

###### C. Miscellaneous <!-- omit from toc -->

| **Index** | **Requirement specification** |
|-----------|-----------------|
| ACP_09 | The common [ISO18013-5] and [OpenID4VP] protocols, or an EUDI Wallet-specific extension or profile thereof, SHALL enable a Wallet Unit to transfer a proof as meant in ACP_04 to a Relying Party. The Commission SHALL take measures to ensure that this is the case. |

#### A.2.3.19 Topic 19 - User navigation requirements (Dashboard logs for transparency)

##### Description <!-- omit from toc -->

In this use case, the User is accessing a dashboard of the
Wallet Unit, which provides a record of all transactions executed through the
Wallet Unit. The User is concerned about data privacy, and thus the
function of a dashboard ensures a higher degree of transparency, privacy
and control of the User over their personal data.

This Topic lists high-level requirements related to the functions
of such a dashboard.  

##### HLRs <!-- omit from toc -->

| **Index** | **Requirement specification** |
|-----------|-----------------|
| DASH_01 | A Wallet Provider SHALL enable a User to access a dashboard functionality in their Wallet Unit. |
| DASH_02 | The Wallet Unit SHALL log all transactions executed through the Wallet Unit, including any transactions that were not completed successfully. This log SHALL include all types of transaction executed through the Wallet Unit: issuance and re-issuance transactions, presentation transactions, signature creation transactions (see [Topic 16](#a2316-topic-16---signing-documents-with-a-wallet-unit)), attribute deletion requests sent to a Relying Party (see [Topic 48](#a2348-topic-48---blueprint-for-requesting-data-deletion-to-relying-parties)), and complaints lodged with a Data Protection Authority (see [Topic 50](#a2350-topic-50---blueprint-to-report-unlawful-or-suspicious-request-of-data)). *Note: For the data to be logged for an attribute deletion request or a complaint, see Topic 48 and Topic 50, respectively.* |
| DASH_02a | The Wallet Unit SHALL retain transactions in the log at least for the time period specified in applicable legislation. If the Wallet Unit must delete transactions from the log, for instance because of size limitations, the Wallet Unit SHALL notify the User via the dashboard before doing so and SHALL instruct the User how to export the transactions that are about to be deleted; see DASH_07. |
| DASH_02b | The dashboard SHALL include a functionality to display to the User an overview of all transactions in the log. |
| DASH_03 | For a presentation transaction executed through the Wallet Unit, the log SHALL contain at least: a) the date and time of the transaction, b) the name, contact details (if the registration certificate was available), and unique identifier of the corresponding Relying Party, and the Member State in which that Relying Party is established, or relevant information from the WUA of the Requestor Wallet Unit (see [Topic 30](#a2330-topic-30---interaction-between-wallet-units)), c) the name, contact details (if a registration certificate was available), and unique identifier of the intermediary, if an intermediary is involved in the transaction, d) the attestation type(s) and the identifier(s) of the attribute(s) that were requested, as well as those that were presented, e) in the case of non-completed transactions, the reason for such non-completion, f) URL address of the Registrar's on-line service.  _Note: the URL address can be retrieved from the access certificate_. |
| DASH_04 | For a signature creation transaction executed through the Wallet Unit, the log SHALL contain at least: a) the date and time of the transaction, b) the document or data signed (where possible), c) in the case of non-completed transactions, the reason for such non-completion. |
| DASH_05 | For an issuance or re-issuance transaction executed through the Wallet Unit, the log SHALL contain at least: a) the date and time of the transaction, b) the name, contact details (if the registration certificate was available), and unique identifier of the corresponding PID Provider or Attestation Provider, c) the attestation type requested, as well as the attestation type issued, d) the number of attestations requested and/or issued (i.e., the size of the batch in case of batch issuance). d) in the case of non-completed transactions, the reason for such non-completion. e) for a re-issuance transaction, whether it was triggered by the User or by the Wallet Unit without involvement of the User, f) URL address of the Registrar's on-line service. _Note: the URL address can be retrieved from the access certificate_. |
| DASH_06 | The Wallet Provider SHALL ensure the confidentiality, integrity, and authenticity of all transactions included in the log. |
| DASH_06a | Via the dashboard, the Wallet Unit SHALL enable the User to delete any transaction in the log. The Wallet Unit SHALL ensure that no other entity can delete transactions from the log, except possibly for the reason mentioned in DASH_02a. |
| DASH_07 | The dashboard SHALL allow the User to export the details of one or more transactions in the log to a file, while ensuring their confidentiality, authenticity and integrity. |
| DASH_08 | For a natural-person User, a Wallet Instance SHALL provide a User interface. |
| DASH_09 | The User interface referred to in DASH_08 SHALL display an EU Digital Identity Wallet Trust Mark complying with technical specifications. *Note: The Commission will develop technical specifications for this Trust Mark.* |
| DASH_10 | The Wallet Unit SHALL make the logs accessible to the Wallet Provider if this is necessary for the provisioning of the Wallet Unit, and only after obtaining explicit consent from the User via the dashboard. |
| DASH_11 | A Wallet Unit issued to a legal person SHALL allow the legal person to interact with the Wallet Unit in the appropriate interface provided by the Wallet Provider. |
| DASH_12 | The User interface referred to in DASH_08 SHALL enable the User, for each presentation transaction in the dashboard, to easily request the Relying Party to delete any or all attributes presented to it in that transaction, or to lodge a complaint about that particular transaction to a DPA. |

#### A.2.3.20 Topic 20 - Strong User authentication for electronic payments

##### Description <!-- omit from toc -->

This topic deals with the requirement for Strong User (Customer) Authentication
(SCA) in the context of authenticating a User as part of electronic payments.  

Users would like to be able to authenticate themselves during online
payments securely and conveniently using their Wallet Units, so that
they can enjoy a seamless and protected shopping/ payment experience.  

The goal is to implement Strong Customer Authentication (SCA) for electronic
payments, ensuring a high level of security and compliance with
[Article 97 of the PSD2](https://eur-lex.europa.eu/eli/dir/2015/2366/oj#d1e5540-35-1)
(and with the future PSD3/PSR).

[Commission Delegated Regulation (EU) 2018/389](https://eur-lex.europa.eu/eli/reg_del/2018/389/oj)
lays down the requirements for strong customer authentication (SCA), which needs
to be complied with when accessing a payment account online and for initiating
electronic payments, or carrying out any action through a remote channel which
may imply a risk of payment fraud or other abuses. The use of the wallet for SCA
will be in full compliance with those requirements.  

In the future, a Wallet Unit could also be used for payments with Central Bank
Digital Currencies.  

##### HLRs <!-- omit from toc -->

There are no HLRs for this Topic.

#### A.2.3.21 Topic 21 - Diplomas within the EUDI Wallet ecosystem

There are no HLRs for this Topic.

#### A.2.3.22 Topic 22 - Digital Travel Credentials within the EUDI Wallet ecosystem

There are no HLRs for this Topic.

#### A.2.3.23 Topic 23 - PID issuance and (Q)EAA issuance

##### Description <!-- omit from toc -->

See [Topic 10](#a2310-topic-10---issuing-a-pid-or-attestation-to-a-wallet-unit).

##### HLRs <!-- omit from toc -->

See [Topic 10](#a2310-topic-10---issuing-a-pid-or-attestation-to-a-wallet-unit).

#### A.2.3.24 Topic 24 - User identification in proximity scenarios

##### Description <!-- omit from toc -->

In this use case, the User is using their Wallet Unit for identification
purposes in proximity scenarios. As explained in [Section 4.4.2 of the ARF main document](../../architecture-and-reference-framework-main.md#442-proximity-presentation-flows), in a
proximity flow, the User and their Wallet Instance are physically near the
Relying Part Instance. PIDs and attestations are exchanged using proximity
technology (e.g., NFC, Bluetooth) between the Wallet Unit and the Relying Party
Instance. Note that this definition does not imply that a Wallet Unit and a
Relying Party have to use proximity technologies if they are close together.
They are free to use a remote flow (according to [Topic 1](#a231-topic-1---accessing-online-services-with-a-wallet-unit)).
However, there may be situations where either the Wallet Unit or the Relying
Party Instance does not have an internet connection. In such cases, they must be
able to use a proximity flow, if they are close together.

The User is concerned
about sharing personal data in proximity, while the User's objectives
include identifying themselves to services requiring User identification
and maintaining control over their personal data sharing.

This topic lists high-level requirements related to User
identification in proximity use cases where Users utilise their Wallet Units.

##### HLRs <!-- omit from toc -->

| **Index** | **Requirement specification** |
|-----------|----------------|
| ProxId_01 | To enable identification using proximity flows, Wallet Units SHALL support device retrieval as specified in ISO/IEC 18013-5 for presenting PID, attestation, or WUA attributes. Wallet Units SHALL comply with the requirements for mDLs in clause 6 and for mdocs in clauses 8 and 9 of ISO/IEC 18013-5. *Note: Nominally, ISO/IEC 18013-5 is intended only for mDLs and mDL readers. The corresponding standard for mobile documents in general (including Wallet Units with the EUDI Wallet ecosystem) will be ISO/IEC 23220-4, which is based on ISO/IEC 18013-5. However, the latter standard is not finished yet and therefore cannot be referenced at the moment. To guarantee interoperability between Wallet Units and Relying Party Instances in proximity scenarios, it is necessary to make choices from among the possibilities specified in ISO/IEC 18013-5. Making the same choices as for mDLs ensure this.* |
| ProxId_01a | If a Relying Party supports using proximity flows, its Relying Party Instances SHALL support device retrieval as specified in ISO/IEC 18013-5 for presenting PID, attestation, or WUA attributes. Such Relying Party Instances SHALL comply with the requirements for mDL readers in clause 6 and for mdoc readers in clauses 8 and 9. *Note: See note to ProxId_01. Support for proximity flows by Relying Parties is not mandatory.* |
| ProxId_02 | Wallet Solutions, PID Providers, Attestation Providers, Wallet Providers, and Relying Parties SHALL NOT support server retrieval as specified in ISO/IEC 18013-5 for requesting and presenting PID, attestation, or WUA attributes. *Note: Using server retrieval, a Relying Party would request User attributes directly from a PID Provider or Attestation Provider, after having received an authentication and/or authorisation token from the User's Wallet Unit.* |
| ProxId_03 | A Wallet Unit SHALL present the presentation request and the identity of the Relying Party to the User when processing the request. |
| ProxId_04 | A Wallet Unit SHALL request its User to approve the presentation of attributes from their Wallet Unit for proximity identification before presenting them to the Relying Party. |
| ProxId_05 | A Wallet Unit SHALL transmit the requested User attributes to the requesting Relying Party Instance securely in accordance with ISO/IEC 18013-5 for proximity flows. |
| ProxId_06 | Empty |

#### A.2.3.25 Topic 25 - Unified definition and controlled vocabularies for attributes

##### Description <!-- omit from toc -->

[Topic 12](#a2312-topic-12---attestation-rulebooks) describes the
high-level requirements (HLR) for the Rulebooks that will
specify the details of new types of attestations, including QEAAs, PuB-EAAs, and
non-qualified EAAs. This Topic already touched and defined high-level requirements
regarding the catalogue for Attestation Rulebooks.

The following main concepts were defined in
[Topic 12](#a2312-topic-12---attestation-rulebooks)
and developed in the current version of this Topic:

- Attestation Rulebooks for QEAAs and PuB-EAAs used within the EUDI Wallet
ecosystem may be registered and published in a publicly accessible catalogue.
- The Attestation Rulebook catalogue may also include Attestation Rulebooks for
non-qualified EAAs.
- The Commission will take measures to establish and maintain the Attestation
Rulebooks catalogue.
- The Attestation Rulebooks catalogue will enable mainly Relying Parties, but
also other actors in the EUDI Wallet ecosystem, to know which attestation types
exist, and what is the identifier, syntax, and semantics of each attribute in a
type of attestation.

The following points are emphasised:

- Registration of an Attestation Rulebook in the attestation catalogue is not mandatory.
- Registration in the Attestation Rulebook catalogue does not create any
obligation of acceptance of the attestation by any Relying Party, nor does it
necessarily imply cross-border recognition of that attestation.
- The Attestation Rulebooks catalogue can be hosted in the same environment as
the catalogue of attributes.

##### HLRs <!-- omit from toc -->

| **Index** | **Requirement specification** |
|-----------|-------------------|
| CAT_01 | The Commission SHALL establish a catalogue of attributes used within the EUDI Wallet ecosystem. *Note: The catalogue of attributes does not need to be a separate catalogue, but could be combined with the Attestation Rulebooks catalogue mentioned in CAT_05.* |
| CAT_01a | The Commission SHALL enable any entity to request the registration in the catalogue of one or more attribute(s) of an attestation used within the EUDI Wallet ecosystem. |
| CAT_01b | The Schema Provider for an Attestation Rulebook that is a QEAA or PuB-EAA SHOULD request the registration of all attributes in that QEAA or PuB-EAA in the catalogue of attributes. The Schema Provider for an Attestation Rulebook that is a non-qualified EAA MAY request the registration of the attributes in that EAA in the catalogue. |
| CAT_02 | Empty |
| CAT_03 | The Commission SHALL make the catalogue of attributes publicly available and machine-readable. *Note: The requirement for availability implies setting up the required means for high availability and avoiding a single point of failure.* |
| CAT_03b | The Commission SHALL consider the following semantic artifacts for inclusion in the catalogue of attributes: - [Representation Powers and Mandates (RPaM) Ontology](https://joinup.ec.europa.eu/collection/isa-action-201612-semantic-interoperability-representation-powers-and-mandates-0/solution/representation-powers-and-mandates-ontology#:~:text=The%20ultimate%20objective%20of%20the,structured%20and%20machine%2Dreadable%20format) - [SEMPER \| DE4A](https://www.de4a.eu/semper) - [SEMIC Core Vocabularies](https://interoperable-europe.ec.europa.eu/collection/semic-support-centre/core-vocabularies#What%20are%20the%20Core%20Vocabularies) - [IANA Registry for JSON Web Token Claims](https://www.iana.org/assignments/jwt/jwt.xhtml) (for JSON-based attributes only) - [ISO/IEC 23220-2](https://www.iso.org/standard/86782.html) (for CBOR-based attributes only) |
| CAT_04 | The Commission SHALL make publicly available the existence and maintenance of the catalogue of attributes mentioned in CAT_01, including processes to propose the registration to public and private parties, allowing to register attributes, and conditions for updating and/or removing attributes. These processes SHALL include archiving and logging changes of the history of the catalogue of attributes in an appropriate way, including versioning. *Note: There are layers on top of the attributes that need maintenance as well. So, maintenance in this case is more generic and encompasses more than just the attribute itself.* |

#### A.2.3.26 Topic 26 - Catalogue of attestations

##### Description <!-- omit from toc -->

See [Topic 25](#a2325-topic-25---unified-definition-and-controlled-vocabularies-for-attributes).

##### HLRs <!-- omit from toc -->

| **Index** | **Requirement specification** |
|-----------|---------------|
| CAT_05 | The Commission SHALL establish a catalogue of Attestation Rulebooks used within the EUDI Wallet ecosystem. *Note: For Attestation Rulebooks, see Topic 12.* |
| CAT_05a | The Commission SHALL enable any entity to register an Attestation Rulebook used within the EUDI Wallet ecosystem. |
| CAT_05b | The Schema Provider for an Attestation Rulebook that is a QEAA or PuB-EAA SHOULD register its Rulebook in the catalogue of Attestation Rulebooks. The Schema Provider for an Attestation Rulebook that is a non-qualified EAA MAY register its Rulebook. |
| CAT_06 | The Commission SHALL make the catalogue publicly available and machine-readable, by hosting the catalogue, or parts of it, including an e-discovery mechanism and/or by referencing to other catalogues. *Note: The requirement for availability implies setting up the required means for high availability and avoiding a single point of failure.* |
| CAT_07 | The Commission SHALL enable a self-registration process of Attestation Rulebooks, without pre-approval by the registry, for both public and private entities. |
| CAT_08 | Empty |
| CAT_09 | The Commission SHALL make publicly available the existence and maintenance of the Attestation Rulebooks catalogue mentioned in CAT_01, including processes to propose the registration to public and private parties, allowing to register an Attestation Rulebook, and conditions for updating and/or removing Attestation Rulebooks. These processes SHALL include archiving and logging changes of the history of the Attestation Rulebooks catalogue in an appropriate way, including versioning. |
| CAT_10 | The body registering an Attestation Rulebook SHALL include a unique reference to this body and the way to contact it, or how to find information for doing so. *Notes: - Topic 12 describes an option for Member State-specific (i.e., domestic) Rulebooks, extending a EU-wide Rulebook. - Rulebooks may also be shared between interested parties in an out-of-band manner.* |
| CAT_11 | Empty |

#### A.2.3.27 Topic 27 - Registration of PID Providers, Providers of QEAAs, PuB-EAAs, and non-qualified EAAs, and Relying Parties

##### Description <!-- omit from toc -->

PID Providers, QEAA Providers, PuB-EAA Providers, non-qualified EAA Providers
and Relying Parties SHALL register with a Registrar in their Member State. The
main goal of the registration process is for the entity to receive an access
certificate that Wallet Units can use to authenticate them.

This Topic specifies high-level requirements related to the registration of the
above mentioned entities.

##### HLRs <!-- omit from toc -->

A. *General requirements for Member State registration processes*

| **Index** | **Requirement specification** |
|-----------|----------------|
| Reg_01 | Member States SHALL provide processes and mechanisms for PID Providers, QEAA Providers, PuB-EAA Providers, non-qualified EAA Providers, and Relying Parties to register in a registry. *Note: Member States may choose to implement a single registry for all these roles, or a separate registry for each of these roles.* |
| Reg_01a | The Commission SHALL provide specifications for a common set of data to be registered about a) PID Providers, b) QEAA Providers, c) PuB-EAA Providers, d) non-qualified EAA Providers. and e) Relying Parties. |
| Reg_01b | For PID Providers, QEAA Providers, PuB-EAA Providers, and non-qualified EAA Providers, the common set of data meant in Reg_01a SHALL include the attestation type(s) that the provider intends to issue to Wallet Units. |
| Reg_02 | Member States SHALL make publicly available all necessary details and documentation about the registration processes for their registry. |
| Reg_03 | Member States SHALL publish the registry entries online, in a sealed or signed machine-readable common format suitable for automated processing, according to the [European Digital Identity Regulation] Article 5b 5, for the purpose of transparency to Users and other stakeholders. |
| Reg_04 | Member States SHALL make the registry available online, in a common human-readable format. |
| Reg_05 | The Commission SHALL establish a technical specification for the common formats mentioned in Reg_03 and Reg_04. |
| Reg_06 | The Commission SHALL provide specifications for a common API for retrieving registry entries from the Member States registries per Reg_03, defining the minimum requirements for interoperability. *Note: Requirements for this API are defined in Reg_08 and Reg_09.* |
| Reg_07 | The Commission SHALL provide specifications for a common user interface for accessing the Member State registries per Reg_04. *Note: Requirements for this user interface are defined in Reg_08 and Reg_09.* |
| Reg_08 | The API mentioned in Reg_06 and the user interface mentioned in Reg_07 SHALL use a secure channel protecting the authenticity and integrity of the information in the registry during transport. |
| Reg_09 | The API mentioned in Reg_06 and the user interface mentioned in Reg_07 SHALL NOT require authentication or prior registration and authorisation of any entity wishing to retrieve the information in the registry. |

B. *General requirements for the issuance of access certificates*

| **Index** | **Requirement specification** |
|-----------|-----------------|
| Reg_10 | A Member State SHALL ensure that an Access Certificate Authority notified according to [[Topic 31](#a2331-topic-31---pid-provider-wallet-provider-attestation-provider-and-access-certificate-authority-notification-and-publication)] issues an access certificate to all PID Providers, QEAA Providers, PuB-EAA Providers, non-qualified EAA Providers, and Relying Parties registered in one of the Member State's registries. |
| Reg_11 | A Member State SHALL ensure that the issuance process of access certificates by their notified Access Certificate Authority(s) complies with a common Certificate Policy for Access Certificate Authority. |
| Reg_12 | The Commission SHALL provide technical specifications establishing the common Access Certificate Authority Certificate Policy mentioned in Reg_11. |
| Reg_13 | The common Certificate Policy mentioned in Reg_12 SHALL require that an Access Certificate Authority logs all issued certificates for Certificate Transparency (CT). *Note: This requirement is still under discussion and might be changed or removed in a future version of this ARF.* |
| Reg_14 | The common Certificate Policy mentioned in Reg_12 SHALL require that an Access Certificate Authority provides one or more method(s) to revoke the access certificates it issued. |
| Reg_15 | The common Certificate Policy mentioned in Reg_12 SHALL include a policy for revocation, which SHALL require that an Access Certificate Authority revokes an access certificate at least when: - the certificate subject which is a Relying Party is de-registered by the respective Registrar, - the certificate subject which is a PID Provider, QEAA Provider, PuB-EAA Provider, or non-qualified EAA Provider is withdrawn or suspended by the respective Registrar, - on request of the certificate subject, or - on request of a competent national authority. |
| Reg_16 | The common Certificate Policy mentioned in Reg_12 SHALL specify the profile of access certificates in detail. |
| Reg_17 | The common Certificate Policy mentioned in Reg_12 SHALL require that an access certificate indicates whether its subject is a PID Provider, a QEAA Provider, a PuB-EAA Provider, a non-qualified EAA Provider, or a Relying Party Instance. |
| Reg_18 | The common Certificate Policy mentioned in Reg_12 SHALL define the minimum change history information to be stored for resolving possible disputes regarding registration. |

C. *Requirements for the registration of PID Providers*

| **Index** | **Requirement specification** |
|-----------|---------------------|
| Reg_19 | A Member State SHALL approve a PID Provider according to a well-defined policy before including it in its PID Provider Registry. To that end, a Member State SHALL define specific vetting processes and rules of acceptance for inclusion of PID Providers in its Registry. |
| Reg_20 | A Member State SHALL identify PID Providers at a level of confidence proportionate to the risk arising from the potential harm a fraudulent PID Provider could cause to Users and other stakeholders in the EUDI Wallet ecosystem. |
| Reg_20a | A Registrar SHALL provide a method to suspend or withdraw a registered PID Provider. |
| Reg_20b | A Registrar SHALL have a policy for the suspension or withdrawal of a registered PID Provider, which SHALL specify that a PID Provider is suspended or withdrawn at least on request of the PID Provider or of a competent national authority. |

D. *Requirements for the registration of Attestation Providers*

| **Index** | **Requirement specification** |
|-----------|-------------------|
| Reg_21 | A Member State SHALL approve an Attestation Provider according to a well-defined policy before including it in its Attestation Provider Registry. To that end, a Member State SHALL define specific vetting processes and rules of acceptance for inclusion of Attestation Providers in its Registry. These processes and rules SHOULD consider any relevant differences between QEAA Providers, PuB-EAA Providers, and non-qualified EAA Providers. |
| Reg_22 | A Member State SHALL identify Attestation Providers (i.e., QEAA Providers, PuB-EAA Providers and non-qualified EAA Providers) at a level of confidence proportionate to the risk arising from the potential harm a fraudulent Attestation Provider could cause to Users and other stakeholders in the EUDI Wallet ecosystem. |
| Reg_22a | A Registrar SHALL provide a method to suspend or withdraw a registered Attestation Provider. |
| Reg_22b | A Registrar SHALL have a policy for the suspension or withdrawal of a registered Attestation Provider, which SHALL specify that an Attestation Provider is suspended or withdrawn at least on request of the PID Provider or of a competent national authority. |

E. *Requirements for the registration of Relying Parties*

| **Index** | **Requirement specification** |
|-----------|------------------|
| Reg_23 | The Commission SHALL establish a technical specification for a common set of Relying Party information to be registered in Member State registries. This set SHALL include at least the information defined in [European Digital Identity Regulation] [article 5b](https://eur-lex.europa.eu/legal-content/EN/ALL/?uri=CELEX:32024R1183#d1e1776-1-1) 2 (c). |
| Reg_24 | A Member State SHALL enable a Relying Party to register remotely, using an API or user interface. |
| Reg_25 | A Member State SHALL identify a Relying Party at a level of confidence proportionate to the risk arising from the potential harm a fraudulent Relying Party could cause to Users and other stakeholders in the EUDI Wallet ecosystem. |
| Reg_26 | A Member State SHALL enable a Relying Party to update the information registered on it using a process comparable to the original registration process, and using the API or user interface mentioned in Reg_24. |
| Reg_27 | Relying Parties SHALL make any updates necessary to ensure the continued correctness of the registered information without undue delay. |
| Reg_28 | A Member State's Registry SHALL log all changes made on the information regarding a Relying Party, including at least initial registration, updates, deletion of information, and suspension or withdrawal. |
| Reg_29 | A Registrar SHALL have a policy for the withdrawal of a registered Relying Party, which SHALL specify that a Relying Party is withdrawn at least on request of the Relying Party or of a competent national authority. |
| Reg_30 | Empty |

F. *Requirements for the issuance of Relying Party Instance access certificates*

| **Index** | **Requirement specification** |
|-----------|---------------------|
| Reg_31 | The common Certificate Policy mentioned in Reg_12 SHALL require that a Relying Party Instance access certificate contains a name for the Relying Party, in a format suitable for presenting to a User. *Note: A Wallet Unit needs such a name when requesting User approval according to [[Topic 6](#a236-topic-6---relying-party-authentication-and-user-approval)].* |
| Reg_32 | The common Certificate Policy mentioned in Reg_12 SHALL require that a Relying Party Instance access certificate contains an EU-wide unique identifier for the Relying Party, and SHALL specify a method for deriving such identifiers. *Notes: - The Wallet Instance needs such an identifier at least to lodge a complaint of suspicious Relying Party presentation requests to a data protection authority according to [Topic 50](#a2350-topic-50---blueprint-to-report-unlawful-or-suspicious-request-of-data). - The EU-wide unique identifier could, for example, be a composition of a unique identifier of the registrar, defined in the policy, and a unique identifier for the Relying Party allocated by this registrar. - This Relying Party identifier is identical in all Relying Party Instance access certificates issued to a given Relying Party.* |

#### A.2.3.28 Topic 28 - Wallet Unit for legal persons

Note to this Topic: Legal-person PIDs and Wallet Units for legal persons were
added to the list of topics to be discussed with Member States in the future.

##### Description <!-- omit from toc -->

This topic is focused on identifying high-level requirements for a legal-person
Wallet Unit. All core capabilities of a Wallet Unit for a natural person are
available for a legal person. There are some differences between a natural and
legal person that accordingly leads to different requirements for issuing
legal-person PIDs and the Wallet Units containing legal-person PIDs.

Notes:

- A legal-person PID is issued under an eID scheme.
- A legal-person PID is described in a legal-person PID Rulebook,
 which is different from the natural-person PID Rulebook in [PID
 Rulebook]. A legal-person PID has a different attestation type than
 a natural-person PID, and also contains different attributes. For
 example, date of birth or age are not relevant information for legal
 persons. Specifying a different Rulebook for legal-person PIDs
 allows Relying Parties and other Wallet Units to request
 these attributes.  
- A legal-person Wallet Solution may be implemented in the same
 manner as a natural-person Wallet Solution, meaning chiefly that it
 is implemented on a mobile device operated by a single User, who is
 a natural person. However, a legal-person Wallet Solution may
 also be implemented as a server-based (web-based) application. In
 the latter case, a Wallet Unit can be used either by one or more
 natural persons appointed by the legal person, or by information
 systems of the legal persons that give an Wallet Unit
 commands in accordance with rules defined by the legal person.

##### HLRs <!-- omit from toc -->

| **Index** | **Requirement specification** |
|-----------|------------------|
| LP_01 | The Commission SHALL develop a Legal-person PID Rulebook to specify the attribute scheme and other technical details applicable for legal-person PIDs. |
| LP_02 | The attestation type of a legal-person PID SHALL be different from the attestation type of a natural person PID. *Note: See [[Topic 12](#a2312-topic-12---attestation-rulebooks)] for an explanation of the concept of attestation type.* |
| LP_03 | A legal-person PID SHALL comply with all requirements in the Legal-person PID Rulebook mentioned in LP_02. |

#### A.2.3.29 Topic 29 - Delegation paradigm

##### Description <!-- omit from toc -->

[Topic 3](#a233-topic-3---pid-rulebook) describes requirements for a rulebook of
natural-person PIDs. [Topic 28](#a2328-topic-28---wallet-unit-for-legal-persons)
does the same for legal-persons PIDs.

[Article 5a](https://eur-lex.europa.eu/legal-content/EN/ALL/?uri=CELEX:32024R1183#d1e1347-1-1).5.(f)
of the [European Digital Identity Regulation] also mentions the possibility of
issuing eIDs that also could attest a natural person representing the natural or
legal person.  At current time, this Topic proposes to not describe any
requirements for such eID schemes without further Member State input for such
eID schemes. The main reason is that there is no cross-border legal framework
for mutual recognition of powers and mandates. Powers and mandates are generally
legal system-specific and administrative system-specific.

Another use case for delegation is where the recognition of the power
for a person to represent another person occurs on an *ad hoc* basis,
based on a decision by the represented User and in the context of a
specific Relying Party. The basis for such decisions is outside the
scope of eIDAS. Various scenarios can be considered:

1. Natural person to natural person, based on the will of the
 represented person: One individual authorises another individual to
 represent them, for example:
   - Picking up a prescription from the pharmacy or a package from
 the post office for a family member.
   - Empowering a person to vote on your behalf.
   - Empowering a notary to sell your house on your behalf to a
 certain party for a certain amount.
   - Empowering your employer to apply for a residence permit on your
 behalf.
2. Natural person to natural person, based on some decision by an
 authority, or also as a consequence of national, EU or international
 law.
3. Legal guardian being able to take decisions on behalf of child,
 disabled person, or elderly person.
4. Natural person to legal person: An individual authorising a legal
 entity to represent them.
5. A person empowering a law firm to be the executor of the trust upon their
 death.
6. A person empowering a bank to invest on their behalf.

##### HLRs <!-- omit from toc -->

There are no specific requirements in this Topic.

#### A.2.3.30 Topic 30 - Interaction between Wallet Units

##### Description <!-- omit from toc -->

A User can request another User to release an attestation of attributes, where
both Users use their Wallet Unit. This can be done when their devices are close
together (that is, in physical proximity) with internet connectivity for both
devices (online), or without internet connectivity for either or both devices
(offline).

This Topic lists the high-level requirements related to the interaction between
two Wallet Units. This topic will be further discussed with Member States.

##### HLRs <!-- omit from toc -->

| **Index** | **Requirement specification** |
|-----------|-----------------|
| W2W_01 | A Wallet Unit SHALL support an interface and protocol for: - Establishing a connection with another Wallet Unit, - Receiving PID and (Q)EAA presentation requests from another Wallet Unit, - Validating such requests, - Responding to such requests in accordance with the technical specifications as defined by [OpenID4VP] and [ISO/IEC 18013-5]. |
| W2W_01a | In addition to W2W_01, a Wallet Unit SHALL support an interface and protocol for: - Sending PID and (Q)EAA presentation requests to another Wallet Unit, - Receiving and validating the corresponding presentation response, in accordance with the technical specifications as defined by [OpenID4VP] and [ISO/IEC 18013-5]. |
| W2W_02 | The Commission SHALL develop technical specifications for exchanging PIDs and attestations between two Wallet Units in accordance with the technical specifications as defined by [OpenID4VP] and [ISO/IEC 18013-5]. |
| W2W_03 | The Requestor Wallet Unit SHALL authenticate its User prior to requesting attestations presentation from another Wallet Unit. |
| W2W_04 | The Requestee Wallet Unit SHALL request User approval, as specified in [[Topic 6](#a236-topic-6---relying-party-authentication-and-user-approval)], before presenting requested attestations or attributes to another Wallet Unit. The Wallet Unit SHALL inform the User about the attributes that are being requested, and of the outcome of authentication and validation checks of the request and the requestor. |
| W2W_05 | The Requestor Wallet Unit SHOULD have pre-defined a list of attributes of PID or attestations that can be requested from the Requestee Wallet Unit. |
| W2W_06 | The Requestee Wallet Unit SHALL authenticate and validate the Requestor Wallet Unit, ensuring the validity of the Requestor Wallet Unit and the attribute request. |
| W2W_07 | The Requestor Wallet Unit SHALL display the received attributes to its User. |

#### A.2.3.31 Topic 31 - PID Provider, Wallet Provider, Attestation Provider, and Access Certificate Authority notification and publication

##### Description <!-- omit from toc -->

PID Providers, PuB-EAA Providers, Wallet Providers and Access Certificate
Authorities must be notified by a Member State to the Commission. As part of the
notification process, the trust anchors of these parties must be included in a
Trusted List. A trust anchor is the combination of a public key and an
identifier for the associated entity. Trust anchors are required for the
verification of the signatures of PIDs, attestations, WUAs, and access
certificates that are issued by these parties.

This Topic contains High-Level Requirements for the notification of these
parties by Member States, and for the publication of the notified information by
the Commission.

##### HLRs <!-- omit from toc -->

A. Generic requirements for notification

| **Index** | **Requirement specification** |
|-----------|-----------------|
| GenNot_01 | The European Commission SHALL establish technical specifications for a common system enabling the notification of PID Providers, PuB-EAA Providers, Wallet Providers, Access Certificate Authorities and Registrars of Registration Certificates by Member States to the Commission. _Note: Notification does not apply to QEAA Providers and (non-qualified) EAA Providers, as explained in Sections D and F below, respectively._ |
| GenNot_02 | As part of the specifications referred to in GenNot_01, the European Commission SHALL establish standard operating procedures for the notification of a PID Provider, PuB-EAA Provider, Wallet Provider, Access Certificate Authorities or Registration Certificate Authorities to the Commission. _Note: The outcome of the notification procedure is the publication of the information notified by the Member State according to [Article 5a](https://eur-lex.europa.eu/legal-content/EN/ALL/?uri=CELEX:32024R1183#d1e1347-1-1) (18) in a machine and human readable manner using the common system mentioned in Section H, TLPub_01._ |
| GenNot_03 | The common system mentioned in GenNot_01 SHALL enable: - A secure notification channel between Member States and the Commission for all notifications. - A notification, verification, and publication process and associated validation steps (with follow-up and monitoring) at the Commission side. - Collected data to be processed, consolidated, signed or sealed, and published in both a machine-processable Trusted List and in a human-readable format, manually and/or automatically using e.g. a web service and/or API. |
| GenNot_04 | As regard to GenNot_03, second bullet, the Commission SHALL verify whether the notified data is complete and meets the technical specifications, while the Member States SHALL be responsible for the correctness of the notified information. |
| GenNot_05 | As part of the specifications referred to in GenNot_01, the European Commission SHALL establish standard operating procedures for the suspension or cancellation of a PID Provider, PuB-EAA Provider, Wallet Provider, Access Certificate Authority or Registration Certificate Authority. These operating procedures SHALL include unambiguous conditions for suspension or cancellation. As an outcome of the suspension or cancellation procedure, the status of the suspended or cancelled PID Provider, PuB-EAA Provider, Wallet Provider, Access Certificate Authority or Registration Certificate Authority in the Trusted List SHALL be changed to Invalid. |

B. Requirements for the notification of PID Providers

| **Index** | **Requirement specification** |
|-----------|-----------------|
| PPNot_01 | The European Commission SHALL establish technical specifications for the common set of information to be notified about PID Providers. |
| PPNot_02 | The common set of information to be notified about a PID Provider SHALL include at least: 1. Identification data: i. MS/Country of establishment, ii. Name as registered in an official record, iii. Where applicable: a. A business registration number from an official record, b. Identification data from that official record. 2. PID Provider trust anchors, i.e., public keys and name as per point 1) ii) above, supporting the authentication of PIDs issued by the PID Provider, 3. PID Provider Access Certificate Authority trust anchors, i.e., public keys and CA name, supporting the authentication of the PID Provider by Wallet Units at the service supply point(s) listed per point 4. below. 4. Service supply point(s), i.e., the URL(s) at which a Wallet Unit can start the process of requesting and obtaining a PID. _Notes: - Relating to point 3. above: PID Provider Access Certificate Authority trust anchors are notified separately from the Access Certificate Authority (see Section G below), since PID Providers are -legally speaking- not Relying Parties. - For the concept of an Access Certificate Authority, see also [[Topic 27](#a2327-topic-27---registration-of-pid-providers-providers-of-qeaas-pub-eaas-and-non-qualified-eaas-and-relying-parties)] and [Section 6.3.2 of the ARF main document](../../architecture-and-reference-framework-main.md#632-pid-provider-or-attestation-provider-registration-and-notification)._ |
| PPNot_03 | PID Providers SHALL ensure that all PIDs they issue can be authenticated using the PID Provider trust anchors notified to the Commission. |
| PPNot_04 | PID Providers SHALL ensure that their PID Provider access certificates can be authenticated using the PID Provider Access Certificate Authority trust anchors notified to the Commission. *Note: [[Topic 6](#a236-topic-6---relying-party-authentication-and-user-approval)] describes how access certificates will be used.*|
| PPNot_05 | PID Provider trust anchors SHALL be accepted because of their secure notification by the Member States to the Commission and by their publication in the corresponding Commission-compiled PID Provider Trusted List which is sealed by the Commission. |
| PPNot_06 | PID Provider Access Certificate Authority trust anchors SHALL be accepted because of their secure notification by the Member States to the Commission and by their publication in the corresponding Commission-compiled PID Provider Access Certificate Authority Trusted List which is signed or sealed by the Commission. |
| PPNot_07 | The format of the PID Provider Trusted List SHALL comply with ETSI TS 119 612 v2.1.1 or with a suitable profile similarly derived from ETSI TS 102 231. |

C. Requirements for the notification of Wallet Providers

| **Index** | **Requirement specification** |
|-----------|-----------------|
| WPNot_01 | The European Commission SHALL establish technical specifications for the common set of information to be notified about Wallet Providers. |
| WPNot_02 | The common set of information to be notified about a Wallet Provider SHALL include: 1. Identification data: i. MS/Country of establishment, ii. Name as registered in an official record, iii. Where applicable: a. Business registration number from an official record, and b. Identification data from the official record. 2. Wallet Provider trust anchors, i.e., public keys and name as per point 1. b. above, supporting the authentication of Wallet Unit Attestations issued by the Wallet Provider. *Notes: - See [[Topic 9](#a239-topic-9---wallet-unit-attestation)] and [[Topic 38](#a2338-topic-38---wallet-unit-revocation)] for the definition of the WUA. - A Wallet Provider does not need an access certificate to interact with Wallet Units.* |
| WPNot_03 | Wallet Providers SHALL ensure that all WUAs they issue can be authenticated using the trust anchors notified to the Commission. |
| WPNot_04 | Wallet Provider trust anchors SHALL be accepted because of their secure notification by the Member States to the Commission and by their publication in the corresponding Commission-compiled Wallet Provider Trusted List which is sealed by the Commission. |
| WPNot_05 | The format of the Wallet Provider Trusted List SHALL comply with ETSI TS 119 612 v2.1.1 or with a suitable profile similarly derived from ETSI TS 102 231. |
| WPNot_06 | If a Wallet Provider is withdrawn (see requirement GenNot_05 above), that Wallet Provider SHALL immediately revoke all of its valid WUAs, in accordance with the requirements in [Topic 38](#a2338-topic-38---wallet-unit-revocation). If a Wallet Provider is suspended, that Wallet Provider and the Member State SHALL agree on the necessary precautionary measures that need to be taken, which MAY include the immediate revocation of all or some of its valid WUAs.|

D. Requirements for the notification of QEAA Providers

There is no notification of QEAA Provider foreseen by the [European Digital
Identity Regulation], except for establishing the [Art. 22](https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=uriserv%3AOJ.L_.2014.257.01.0073.01.ENG#d1e2162-73-1)
Trusted List once a qualified status is granted. QTSPs issuing QEAAs to Wallet
Units SHALL abide by the Implementing Act to be adopted under [Art. 45d](https://eur-lex.europa.eu/legal-content/EN/ALL/?uri=CELEX:32024R1183#d1e3849-1-1)(5).

E. Requirements for the notification of PuB-EAA Providers

This notification is pursuant to
[Art.45f](https://eur-lex.europa.eu/legal-content/EN/ALL/?uri=CELEX:32024R1183#d1e3902-1-1)(3)
and to the implementing acts to be adopted pursuant to
[Art.45f](https://eur-lex.europa.eu/legal-content/EN/ALL/?uri=CELEX:32024R1183#d1e3902-1-1)(7).
It should be noted that the purpose of this notification is mainly to the
attention of QTSPs issuing qualified certificates for electronic signatures or
seals to those public sector bodies referred to in [Article
3](https://eur-lex.europa.eu/legal-content/EN/ALL/?uri=CELEX:32024R1183#d1e739-1-1),
point (46), and identified as the issuer in the PuB-EAA. The Trusted List
compiled by the Commission is deemed to be a constitutive list of such
[Art.3](https://eur-lex.europa.eu/legal-content/EN/ALL/?uri=CELEX:32024R1183#d1e739-1-1)(46)
bodies recognised for issuing PUB-EAAs. Consequently, QTSPs are expected to
verify such lists prior to issuing a qualified certificate to any entity
claiming to be a
[Art.3](https://eur-lex.europa.eu/legal-content/EN/ALL/?uri=CELEX:32024R1183#d1e739-1-1)(46)
body.

| **Index** | **Requirement specification** |
|------------|-----------------|
| PuBPNot_01 | The European Commission SHALL establish technical specifications for the common set of information to be notified about PuB-EAA Providers. |
| PuBPNot_02 | The common set of information to be notified by Member States about PuB-EAA Providers SHALL include at least: 1. Identification data: i. MS/Country of establishment, ii. Name as registered in an official record, iii. Where applicable: a. Registration number as in official record, and b. Official record identification data. iv. Identification data of the Union or national law under which a. Either the PuB-EAA Provider is established as the responsible body for the Authentic Source based on which the electronic attestation of attributes is issued, or b. The PuB-EAA Provider is the body designated to act on behalf of the responsible body referred to in point 1. iv. a. v.The conformity assessment report issued by a conformity assessment body, confirming that the requirements set out in paragraphs 1, 2 and 6 of [Article 45f](https://eur-lex.europa.eu/legal-content/EN/ALL/?uri=CELEX:32024R1183#d1e3902-1-1) are met. 2. Service supply point(s), i.e., the URL(s) at which a Wallet Unit can start the process of requesting and obtaining a PuB-EAA from the PuB-EAA Provider. |
| PuBPNot_03 | The format of the PuB-EAA Provider Trusted List SHALL comply with ETSI TS 119 612 v2.1.1 or with a suitable profile similarly derived from ETSI TS 102 231. |

F. Requirements for the notification of non-qualified EAA Providers

There is no notification of non-qualified EAA Providers foreseen by the
[European Digital Identity Regulation]. As stated in [[Topic 12](#a2312-topic-12---attestation-rulebooks)],
the Schema Provider for an Attestation Rulebook describing a type of attestation
that is an EAA defines in the Rulebook the mechanisms allowing a Relying Party
to obtain, in a trustworthy manner, the trust anchor(s) of EAA Providers issuing
this type of EAA.

G. Requirements for the notification of Access
 Certificate Authorities

Relying Party Access Certificate Authorities (CA) are responsible for
signing access certificates they issue to Relying Parties. Legally speaking,
Relying Parties in this context also include QEAA Providers, PuB-EAA Providers,
and non-qualified EAA Providers, but for clarity these roles are mentioned
separately in the requirements below. Where these requirements use the term
'Access Certificate Authorities' without further qualifications, this includes
Access Certificate Authorities for QEAA Providers, PuB-EAA Providers,
non-qualified EAA Providers, and Relying Parties.

For more information about Relying Party Access Certificate Authority,
see [[Topic 27](#a2327-topic-27---registration-of-pid-providers-providers-of-qeaas-pub-eaas-and-non-qualified-eaas-and-relying-parties)].

| **Index** | **Requirement specification** |
|------------|------------------|
| RPACANot_01 | The European Commission SHALL establish technical specifications for the common set of information to be notified about Access Certificate Authorities and Registrars of Registration Certificates. |
| RPACANot_02 | The common set of information to be notified about an Access Certificate Authority and Registrars of Registration Certificates SHALL include: 1. Identification data: i) MS/Country of establishment, ii) Name as registered in an official record, iii) Where applicable: - A business registration number from an official record, - Identification data from that official record. 2. Access Certificate Authority or Registration Certificate Authority trust anchors, i.e., public keys and name as per point 1) ii), supporting the authentication of Relying Parties by Wallet Units. |
| RPACANot_03 | Relying Parties, QEAA Providers, PuB-EAA Providers, and non-qualified EAA Providers SHALL ensure that their access certificates can be authenticated using the Access Certificate Authority trust anchors notified to the Commission. |
| RPACANot_04 | Access Certificate Authority and Registration Certificate Authority trust anchors SHALL be accepted because of their secure notification by the Member States to the Commission and by their publication in the corresponding Commission-compiled Access Certificate Authority and Registration Certificate Authority Trusted Lists which are signed or sealed by the Commission. _Note: The adopted version of the CIR for Relying Party registration will clarify how the Trusted List for Registrars of Registration Certificates are to be arranged, the certificates not being PKI/X.509 certificates as is the case with standard EU Trusted Lists. It is also to be clarified in the related technical specification if Access Certificate Authorities can sign other certificates than access certificates._ |
| RPACANot_05 | The format of an Access Certificate Authority Trusted List SHALL comply with ETSI TS 119 612 v2.1.1 or with a suitable profile similarly derived from ETSI TS 102 231. |
| RPACANot_06 | If an Access Certificate Authority is suspended or cancelled (see requirement GenNot_05 above), that Access Certificate Authority SHALL immediately revoke all of its valid access certificates. _Note: When the access certificates of an Intermediary that has its RPACs issued by said suspended or cancelled Access Certificate Authority are revoked, the End-Relying Parties depending on said Intermediary, while having valid registration certificates from a Registrar will have no access to transact with EUDI Wallet Users until the End-Relying Parties a) transit to another Intermediary that has RPAC issued by an active Access Certification Authority or b)the original Access Certificate Authority can continue its operations and re-issue earlier revoked certificates for the original Intermediary._ |
| RPACANot_07 | If a Registrar of Relying Party Registration Certificates is suspended or cancelled (see requirement GenNot_05 above), that Registrar of Relying Party Registration Certificates SHALL immediately revoke all of its valid registration certificates. |


H. Requirements for the publication of Trusted Lists compiled by the
 Commission

| **Index** | **Requirement specification** |
|------------|------------------|
| TLPub_01 | The European Commission SHALL establish technical specifications for the system enabling the publication by the Commission of the information notified by the Member States regarding PID Providers, Wallet Providers, PuB-EAA Providers, Access Certificate Authorities and Registrars of Registration Certificates. |
| TLPub_02 | The European Commission SHALL establish technical specifications for the set of information to be published about: PID Providers, Wallet Providers,PuB-EAA Providers, Access Certificate Authorities and Registrars of Registration Certificates based on the information notified by the Member States. _Note: The information to be published MAY be different from the information to be notified per requirements PPNot_01, WPNot_01, PuBPNot_01, and RPACANot_01 above, respectively._ |
| TLPub_03 | The publication of the information referred to in TLPub_01 SHALL take place over a secure channel protecting the authenticity and integrity of the published information. |
| TLPub_04 | The technical system mentioned in TLPub_01 SHALL NOT require authentication or prior registration and authorisation of any entity wishing to retrieve the published information. |
| TLPub_05 | The information referred to in TLPub_01 SHALL be published in an electronically signed or sealed form that is suitable for automated processing, and in a human-readable format, e.g., through introspection and display facilities, over an authenticated channel. |
| TLPub_06 | The Commission SHALL publish in the OJEU the locations of the Trusted Lists for PID Providers, Wallet Providers, PuB-EAA Providers, and Access Certificate Authorities. |
| TLPub_07 | The Commission SHALL publish in the OJEU the trust anchors to be used for verifying the signature or seal mentioned in TLPub_05. |
| TLPub_08 | 	As part of the specifications referred to in TLPub_01, the European Commission SHALL establish technical specifications for ensuring the availability and authenticity of the full history regarding the information notified about PID Providers, Wallet Providers, PuB EAA Providers, Access Certificate Authorities and Registrars of Registration Certificates. |

#### A.2.3.32 Topic 32 - PID interoperability

See [Topic 12](#a2312-topic-12---attestation-rulebooks).

#### A.2.3.33 Topic 33 - Wallet Unit backup and restore

##### Description <!-- omit from toc -->

Backup and restore functionality is needed in case the User has lost access to
their current Wallet Unit, for example in case of loss, theft, or breakdown. It
is also needed if the User wants to start using another Wallet Unit, for example
because they have bought a new device, need to factory-reset their existing
device, or want to migrate to another Wallet Solution. In all of these cases,
the User wants to restore the PIDs and attestations in their existing Wallet
Unit on their new Wallet Unit, with as minimal an effort as possible.

The [European Digital Identity Regulation] does not contain a requirement
mandating backup and restore functionality in the Wallet. However, Wallet
Providers should implement backup and restore functionality nevertheless,
because it will be expected by Users. In fact, the requirements in [Topic 34](#a2334-topic-34---migrate-to-a-different-wallet-solution)
also ensure the possibility of backup and restore.

##### HLRs <!-- omit from toc -->

There are no specific requirements in this Topic.

#### A.2.3.34 Topic 34 - Migrate to a different Wallet Solution

##### Description <!-- omit from toc -->

Article 5a 4 (g) of the [European Digital Identity Regulation] ensures the
User's rights to data portability. Data portability means that a User can
migrate to a different Wallet Solution. The User installs an instance of the new
Wallet Solution, and then wants to restore the PIDs and attestations in their
existing Wallet Unit to their new Wallet Unit. This should be possible with as
minimal an effort as possible, and independent of whether the User still has
access to their existing Wallet Unit.

The solution described in this Topic is to introduce a Migration Object in each
Wallet Unit. This object is a list of PIDs and attestations contained in the
Wallet Unit, together with the information needed to request (re-)issuance of
that PID or attestation. Note that the Migration Object does not contain any
private keys of PIDs or attestations. In most security
architectures for a Wallet Solution described in [Section 4.5 of the ARF main document](../../architecture-and-reference-framework-main.md#45-wscd-architecture-types), this is
impossible, since the WSCA/WSCD that contains these private keys does not allow
their extraction under any circumstances. An exception may be architectures in
which attestation private keys are managed in a remote HSM and the migration is
to a new Wallet Unit of the same Wallet Provider. However, in such cases,
restoring functionality of the PIDs and attestations in a new Wallet Unit does
not necessitate that private keys must be exported to another HSM. Rather, it
implies the User must be able to authenticate towards the existing HSM from the
new Wallet Unit, and be recognised as an existing User.

The fact that the Migration Object does not contain private keys means that PIDs
and attestations cannot be backed up and restored from the object in such a way
that they are usable in a new Wallet Unit without involvement of the PID
Provider or Attestation Provider. Instead, the User must ask the respective PID
Provider(s) or Attestation Provider(s) to re-issue the PID(s) or attestation(s)
to the new Wallet Unit. The only function of the Migration Object is to simplify
this process by listing the PIDs and attestations present in the existing Wallet
Unit, together with the information needed by the new Wallet Unit to start the
re-issuance process.

The Migration Object does not contain attribute values or attribute identifiers,
as that data is considered sensitive and is not useful anyway because of the
limitations explained above. Instead, the object only contains a list of
attestation types and the related Attestation Providers. However, even this
limited information may be considered sensitive in some cases. Therefore, the
Migration Object is stored in such a way that its confidentiality is ensured and
that it can be used only by the User.

##### HLRs <!-- omit from toc -->

A. Back-up requirements

| **Index** | **Requirement specification** |
|-----------|------------------|
| Mig_01 | A Wallet Unit SHALL include and keep up-to-date a Migration Object, containing the following information: - The contents of the log for all transactions executed through the Wallet Unit, as listed in requirement DASH_02. - A list of PIDs and attestations present in the Wallet Unit, according to the requirements in this Topic. |
| Mig_02 | The Commission SHALL define a technical specification of the Migration Object. |
| Mig_03 | For each PID or attestation that is issued to it, a Wallet Unit SHALL add all data that is necessary to request re-issuance of that PID or attestation to the Migration Object. This SHALL include at least the attestation type and the PID Provider or Attestation Provider that issued the PID or attestation, as well as their service supply points. However, the Migration Object SHALL NOT contain attribute identifiers or attribute values, and SHALL NOT contain any private keys of the PID or attestation. |
| Mig_03b | If the User deletes a PID or attestation from their Wallet Unit, the Wallet Unit SHALL delete the corresponding entry from the Migration Object. |
| Mig_04 | The Wallet Unit SHALL store the Migration Object in an external storage or remote location of the User's choice, in such a way that the User can still retrieve the object from a new Wallet Unit in case the existing Wallet Unit becomes unavailable. *Note: The new Wallet Unit may be either an instance of the same Wallet Solution as the old one, or an instance of a different Wallet Unit.* |
| Mig_05 | The Wallet Unit SHALL store the Migration Object in such a way that its confidentiality is protected and that it is protected against use by others than the User. *Note: This could be done, for example, by using password-based cryptography to encrypt the object.* |

B. Restore Requirements

| **Index** | **Requirement specification** |
|-----------|-----------------|
| Mig_06 | Directly after installation of a new Wallet Instance, the Wallet Instance SHALL enable the User to import a Migration Object from an external storage or remote location indicated by the User. |
| Mig_07 | For each PID and attestation listed in the Migration Object, the Wallet Unit SHALL enable the User to select that PID or attestation. When selected, the Wallet Unit SHALL request the respective PID Provider or Attestation Provider to re-issue that PID or attestation. If the Migration Object lists a PID, the PID SHALL be the first to be restored. |
| Mig_07a | The Wallet Unit SHALL ask the User whether they want to restore the log from the Migration Object. When the User agrees, the Wallet Unit SHALL restore the log, and SHALL append future transactions to this log according to the requirements in [Topic 19](#a2319-topic-19---user-navigation-requirements-dashboard-logs-for-transparency). |
| Mig_08 | Empty |
| Mig_09 | Empty |
| Mig_10 | Empty |
| Mig_11 | The processes and interfaces used for re-issuance of a PID or attestation (as part of a migration process) SHALL be the same as those used for their issuance, as specified in [Topic 10](#a2310-topic-10---issuing-a-pid-or-attestation-to-a-wallet-unit). |
| Mig_12 | Empty |
| Mig_13 | Empty |
| Mig_14 | Empty |
| Mig_15 | Empty |
| Mig_16 | Empty |

#### A.2.3.35 Topic 35 - PID issuance service blueprint

##### Description <!-- omit from toc -->

This Topic analyses the User journeys for PID issuance to a Wallet
Unit. This Topic focuses on natural persons only.

##### HLRs <!-- omit from toc -->

No HLRs are present for this Topic. Note that issuance of PID is discussed in [Topic 10](#a2310-topic-10---issuing-a-pid-or-attestation-to-a-wallet-unit); relevant HLRs can be found there.

#### A.2.3.36 Topic 36 - Risk Analysis of the Wallet usage

There are no HLRs for this Topic.

#### A.2.3.37 Topic 37 - QES -- Remote Signing - Technical Requirements

See [Topic 16](#a2316-topic-16---signing-documents-with-a-wallet-unit).

#### A.2.3.38 Topic 38 - Wallet Unit revocation

##### Description <!-- omit from toc -->

This Topic discusses Wallet Unit revocation. In particular, it answers the
following questions: - How can a Wallet Provider revoke a Wallet Unit? - During
issuance of an attestation, how can an Attestation Provider verify whether a
Wallet Unit has been revoked? - When requesting attributes from an attestation, how
can a Relying Party verify whether a Wallet Unit has been revoked?

In case of a security issue, Article 5e of the [European Digital Identity
Regulation] requires Wallet Providers to first suspend a Wallet Unit and to
revoke it only if the issue cannot be solved within three months. However, the
suspension of a Wallet Unit is an administrative process, which does not imply
that the WUAs of that Wallet Unit need to be suspended, as opposed to being
revoked. Instead, if the Wallet Provider administratively suspends a Wallet
Unit, it will immediate revoke all corresponding WUAs. If (within three months)
the situation is remedied and the Wallet Unit can be re-instated, the Wallet
Provider will issue one or more new WUAs to the Wallet Unit.

##### HLRs <!-- omit from toc -->

A. Issuing a Wallet Unit Attestation

| **Index** | **Requirement specification** |
|------------|-------------------|
| WURevocation_01 | To enable a Relying Party or an Attestation Provider to verify the authenticity and (if necessary, see requirement VCR_01) the revocation status of a Wallet Unit it is interacting with, a Wallet Provider SHALL issue one or more Wallet Unit Attestations to the Wallet Unit, as specified in Topic 9. *Note: The first of these WUAs will be issued during the activation phase of a Wallet Unit. During the lifetime of the Wallet Unit, the Wallet Provider will re-issue WUAs as needed.* |
| WURevocation_02 | During the lifetime of the Wallet Unit, the Wallet Provider SHALL ensure that the Wallet Unit at all times is able to respond with a valid WUA to a presentation request from a Relying Party. |
| WURevocation_03 | Empty |
| WURevocation_04 | Empty |
| WURevocation_05 | Empty |

A. Revoking a Wallet Unit

| **Index** | **Requirement specification** |
|------------|------------------|
| WURevocation_06 | Empty |
| WURevocation_07 | A Wallet Provider SHALL be able to revoke a Wallet Unit by revoking its WUA(s), as specified in [[Topic 7](#a237-topic-7---attestation-revocation-and-revocation-checking)]. *Note: Topic 7 also allows the use of short-lived (i.e., valid for less than 24 hours) WUAs that do no need to be revoked. In that case, the Wallet Provider revokes the Wallet Unit by no longer issuing WUAs to it.*|
| WURevocation_08 | Empty |
| WURevocation_09 | During the lifetime of a Wallet Unit, the Wallet Provider SHALL regularly verify that the security of the Wallet Unit is not breached or compromised. If the Wallet Provider detects a security breach or compromise, the Wallet Provider SHALL analyse its cause(s) and impact(s). If the breach or compromise affects the trustworthiness or reliability of the Wallet Unit, the Wallet Provider SHALL administratively revoke or suspend the Wallet Unit and SHALL immediately revoke the corresponding WUA(s) if they have a remaining validity period of 24 hours or longer. The Wallet Provider SHALL do so at least in the following circumstances: - If the security of the Wallet Unit, or the security of the mobile device and OS on which the corresponding Wallet Instance is installed, or the security of a WSCA it uses for managing cryptographic keys and sensitive data, is breached or compromised in a manner that affects its trustworthiness or reliability. - If the security of the Wallet Solution is breached or compromised in a manner that affects the trustworthiness or reliability of all corresponding Wallet Units. - If the security of the common authentication and data protection mechanisms used by the Wallet Unit is breached or compromised in a manner that affects their trustworthiness or reliability. - If the security of the electronic identification scheme under which the Wallet Unit is provided is breached or compromised in a manner that affects its trustworthiness or reliability. |
| WURevocation_9b | If within three months from an administrative suspension of a Wallet Unit the security breach or compromise is remedied, the Wallet Provider SHALL issue one or more WUAs to the Wallet Unit, such that the User can again use it. |
| WURevocation_10 | A Wallet Provider SHALL revoke a Wallet Unit upon the explicit request of the User registered during the Wallet Unit activation process, see [Topic 40](#a2340-topic-40---wallet-instance-installation-and-wallet-unit-activation-and-management). To do so, the Wallet Provider SHALL revoke all valid WUA(s) for that Wallet Unit, if they have a remaining validity period of 24 hours or longer. The Wallet Provider SHALL authenticate the User before accepting a request to revoke the Wallet Unit. |
| WURevocation_11 | A Wallet Provider SHALL revoke a Wallet Unit upon the explicit request of a PID Provider, in case the natural person using the Wallet Unit has died or the legal person using the Wallet Unit has ceased operations. To do so, the Wallet Provider SHALL revoke all valid WUA(s) for that Wallet Unit, if they have a remaining validity period of 24 hours or longer. To identify the Wallet Unit that is to be revoked, the PID Provider SHALL use the Wallet Unit identifier provided by the Wallet Provider in the WUA during PID issuance. |
| WURevocation_12 | Before revoking a Wallet Unit per WURevocation_11, the Wallet Provider SHALL verify that the party requesting revocation is indeed a valid PID Provider listed in the Trusted List of PID Providers. |
| WURevocation_13 | Before requesting a Wallet Provider to revoke a Wallet Unit per WURevocation_11, the PID Provider SHALL ensure that the revocation does not harm the interests of any of the stakeholders. The PID Provider SHALL have (and follow) a documented policy to ensure that this is the case. |

B. Informing the User

| **Index** | **Requirement specification** |
|-----------|-------------------|
| WURevocation_14 | A Wallet Provider SHALL inform a User without delay, and within 24 hours at most, in case the Wallet Provider decided to revoke the User's Wallet Unit. The Wallet Provider SHALL also inform the User about the reason(s) for the revocation. This information SHALL be understandable for the general public. It SHALL include (a reference to) technical details about any security breach if applicable. |
| WURevocation_15 | Empty |
| WURevocation_16 | To inform a User about the revocation of their Wallet Unit, the Wallet Provider SHALL use a communication channel that is independent of the Wallet Unit. In addition, the Wallet Provider MAY use the Wallet Unit itself to inform the User. |

C. Verifying the revocation status of a Wallet Unit

| **Index** | **Requirement specification** |
|-----------|------------------|
| WURevocation_17 | Empty |
| WURevocation_18 | A PID Provider or Attestation Provider SHOULD, for each of its valid PIDs or attestations, regularly verify whether the Wallet Provider revoked the Wallet Unit on which that PID or attestation is residing. If it turns out that the Wallet Unit is revoked, the PID Provider or Attestation Provider SHOULD immediately revoke the respective PID or attestation in accordance with all requirements in [[Topic 7](#a237-topic-7---attestation-revocation-and-revocation-checking)]. *Notes: - How the PID Provider or Attestation Provider can do this verification depends on the details of the WUA and on WUA management. This is a topic that will be further discussed. - The reverse is not true: When a PID is revoked, this does not imply that the Wallet Unit on which it is residing should also be revoked. Instead, the Wallet Unit moves to the Operational state. See [ARF main document Section 4.6.3](../../architecture-and-reference-framework-main.md#463-wallet-unit).* |
| WURevocation_19 | A Relying Party SHOULD verify the revocation status of the Wallet Unit by requesting and verifying a WUA and subsequently verifying the revocation status of the WUA following the steps specified per VCR_11. |
| WURevocation_19a | To safeguard User privacy, a Relying Party Instance SHOULD request only the data from the WUA that is necessary for carrying out a revocation check for the Wallet Unit. *Note: The format of the WUA will be further discussed with Member States. However, the WUA contains information about the Wallet Instance and the related WSCD(s) that are only relevant for PID Providers and Attestation Providers, and that a Relying Party should not know.* |
| WURevocation_19b | To safeguard User privacy, a Wallet Unit SHALL present to a Relying Party only the data in the WUA that is necessary for carrying out a revocation check for the Wallet Unit. *Note: See note to requirement WURevocation_19a. In addition, this requirement implies that the format of the WUA must enable the selective disclosure of attributes.* |
| WURevocation_20 | For the verification of WUAs, a Relying Party SHALL accept the trust anchors in the Wallet Provider Trusted List. *Note: The Wallet Provider Trusted List is explained in [[Topic 31](#a2331-topic-31---pid-provider-wallet-provider-attestation-provider-and-access-certificate-authority-notification-and-publication)].* |
| WURevocation_21 | When no reliable information regarding the revocation status of a WUA is available, a Relying Party SHOULD perform a risk analysis considering all relevant factors for the use case, before taking a decision to accept or refuse the Wallet Unit. |

#### A.2.3.39 Topic 39 - Wallet to wallet technical Topic

See [Topic 30](#a2330-topic-30---interaction-between-wallet-units).

#### A.2.3.40 Topic 40 - Wallet Instance installation and Wallet Unit activation and management

##### Description <!-- omit from toc -->

This Topic discusses requirements related to the installation of a Wallet
Instance by the User, the subsequent activation of the Wallet Unit by the User
and the Wallet Provider, and the management of the Wallet Unit throughout its
lifetime.

##### A - HLRs for Wallet Instance installation <!-- omit from toc -->

| **Index** | **Requirement specification** |
|-----------|------------------|
| WIAM_01 | To ensure that the User can trust the Wallet Solution, a Wallet Provider SHOULD make its certified Wallet Solution available for installation only via the official app store of the relevant operating system (e.g., Android, iOS). *Note: This allows the operating system of the device to perform relevant checks regarding the authenticity of the Wallet Unit.* |
| WIAM_02 | If a Wallet Provider makes its certified Wallet Solution available for installation through other means than the official OS app store, it SHALL implement a mechanism allowing the User to verify the authenticity of the Wallet Unit. Moreover, it SHALL provide clear instructions to the User on how to install the Wallet Instance, including at least: - instructions on the verification of the authenticity of the Wallet Instance to be installed, - instructions on bypassing of any operating system limitations on side-loading of apps, if applicable, and ensuring that these limitations are restored after the Wallet Instance has been installed. *Note: This requirement also applies for the installation of a Wallet Instance on a User device that is not a mobile device, and for which no official operating system app store may exist.* |

##### B - HLRs for Wallet Unit activation <!-- omit from toc -->

| **Index** | **Requirement specification** |
|-----------|------------------|
| WIAM_03 | A Wallet Provider SHALL ensure that a Wallet Instance starts a process to activate the new Wallet Unit with the Wallet Provider immediately after installation or when the User first opens the Wallet Instance. The Wallet Provider SHALL ensure that the Wallet Instance starts this process only with a secure backend of the Wallet Provider. |
| WIAM_04 | During the activation process of a new Wallet Unit, the Wallet Provider SHALL verify that the new Wallet Instance is a genuine instance of its Wallet Solution. |
| WIAM_05 | During the activation process of a new Wallet Unit, the Wallet Provider SHALL process information about the User device and the available WSCAs and WSCDs, as far as necessary to issue a Wallet Unit Attestation to the Wallet Unit conform all requirements in [Topic 9](#a239-topic-9---wallet-unit-attestation) section A. The Wallet Provider MAY process additional information necessary for managing the Wallet Unit, but it SHALL NOT process more information than it reasonably needs for legitimate purposes. The Wallet Provider SHALL request User consent (through the Wallet Instance) for all information and data it will process, both during activation and throughout the lifetime of the Wallet Unit. The Wallet Provider SHALL inform the User about the purposes of data processing, in accordance with the General Data Protection Regulation. |
| WIAM_06 | The Wallet Provider SHALL request the User, through the new Wallet Instance, to set up a User account at the Wallet Provider. The Wallet Provider SHALL explain to the User that this is necessary to enable the User to request revocation of the Wallet Unit in case of theft or loss. The Wallet Provider SHALL register one or more User authentication methods that the Wallet Provider will use to authenticate the User in the future. These methods SHALL be independent of the Wallet Unit and the User device. The Wallet Provider SHALL allow the User to register using an alias instead of true identity data. The Wallet Provider SHALL NOT use any registered User data for purposes other than User authentication, unless the User gives explicit consent to do so. The Wallet Provider SHALL register the relationship between the Wallet Unit and the corresponding User account. |
| WIAM_07 | A Wallet Provider SHALL activate a new Wallet Unit before a User can use it to have issued an PID or attestation. *Note: The WUA is issued as part of the activation.* |
| WIAM_08 | A Wallet Provider SHALL only activate a new Wallet Unit if it has verified that: - The Wallet Unit includes at least one WSCA that is certified to be compliant with applicable requirements in this Topic, for Level of Assurance High in [Commission Implementing Regulation (EU) 2015/1502](https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=CELEX%3A32015R1502) section 2.2.1. In addition, the Wallet Unit MAY include one or more other WSCAs, which SHALL be certified to be compliant with applicable requirements for Level of Assurance Substantial or High. - The private key corresponding to the public key in the WUA (see WUA_07) is protected by the respective WSCA under control of the User. |
| WIAM_09 | If a WSCA/WSCD contains cryptographic keys related to multiple Wallet Units, the Wallet Provider SHALL ensure that a Wallet Unit can only access keys that are related to that Wallet Unit. |
| WIAM_10 | During the activation of a new Wallet Unit, a Wallet Provider SHALL create and sign at least one Wallet Unit Attestation, and issue them to the Wallet Unit. |

##### C - HLRs for Wallet Unit management <!-- omit from toc -->

| **Index** | **Requirement specification** |
|-----------|------------------|
| WIAM_11 | During the lifetime of the Wallet Unit, the Wallet Provider SHALL update the Wallet Unit as necessary to ensure its continued security and functionality. |
| WIAM_12 | All communication between the Wallet Provider and the Wallet Unit SHALL be mutually authenticated and SHOULD be encrypted. |
| WIAM_13 | If the User uninstalls the Wallet Unit, the Wallet Unit SHALL ensure that all cryptographic key material in the WSCA(s) related to the Wallet Unit is securely destroyed. This includes all keys of the WUAs, PIDs and attestations stored in the Wallet Unit. *Note: Key deletion is a cryptographic key operation and requires User authentication, as specified in requirement WIAM_14.* |
| WIAM_13a | If a Wallet Unit supports the [W3C Digital Credentials API] and the User uninstalls the Wallet Unit, the Wallet Unit SHALL disclose the fact that it no longer stores any PID(s) or attestation(s) to the Digital Credentials API framework. |
| WIAM_14 | A WSCA SHALL authenticate the User before performing any cryptographic operation involving a private or secret key of a Wallet Unit (i.e., a WUA key) or of a PID or an attestation stored in a Wallet Unit. For a PID key (which is part of the EUDI Wallet eID means), this WSCA SHALL be certified to be compliant with applicable requirements for Level of Assurance High in [Commission Implementing Regulation (EU) 2015/1502](https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=CELEX%3A32015R1502) section 2.2.1. *Note: Many actions of the Wallet Unit, such as processing a Relying Party request and presenting an attestation, require multiple cryptographic operations, for example ephemeral key generation followed by key agreement and message encryption. This requirement does not imply that separate User authentication is necessary before each of these. Rather, a successful User authentication will be valid for all cryptographic operations necessary for a Wallet Unit action. It is up to the Wallet Provider to determine what constitutes a 'Wallet Unit action', finding a balance between security (more User authentications) and User convenience (fewer User authentications). During certification of the Wallet Solution, it will be verified that the solution provides an adequate level of security.* |
| WIAM_15 | A Wallet Unit SHALL authenticate the User before performing any operation. The Wallet Unit SHOULD rely on a WSCA to do so, per WIAM_14. If this is infeasible, the Wallet Unit SHOULD use a User authentication mechanism implemented on OS level, such as a lock screen, but, if this is infeasible, it MAY also use a separate User authentication mechanism implemented in the Wallet Instance. *Notes: - The goal of this requirement is to prevent any User interaction without User authentication. User interaction includes, for example, using the user interface to see which attestations are present in the Wallet Unit or what are the values of specific User attributes. - An example where using a WSCA for User authentication is not feasible is a Wallet Unit using a remote HSM as its WSCA and being without internet connection. - In general, using an OS-level User authentication mechanism instead of a separate mechanism implemented in the Wallet Instance is beneficial for security and User experience. Please note that this ARF assumes that a User device is a personal device, meaning that the User will not share it with other people. - An example where using an OS-level User authentication mechanism is not feasible is where the User has disabled such mechanisms (i.e., no lock screen is used). In that case, a Wallet Unit that is not able to use a WSCA for User authentication must use a separate authentication mechanism implemented in the Wallet Instance as a fallback.* |
| WIAM_16 | For User authentication according to WIAM_15, a Wallet Unit SHALL implement an idle timeout, after which User authentication SHALL again be required. The Wallet Unit SHOULD provide the User with the option to set the idle timeout to a duration shorter than the default timeout. |
| WIAM_17 | A WSCA SHALL be able to authenticate a User, in accordance with the requirements in [Commission Implementing Regulation (EU) 2015/1502](https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=CELEX%3A32015R1502) section 2.2.1. |
| WIAM_18 | A WSCA SHALL be able to generate a new key pair on request of the Wallet Provider via the Wallet Instance. |
| WIAM_19 | A WSCA SHALL be able to prove possession of the private key corresponding to a public key on request of a Wallet Instance, for example by signing a challenge with that private key. |
| WIAM_20 | A WSCA SHALL protect a private key it generated during the entire lifetime of the key. This protection SHALL at least imply that the WSCA prevents the private key from being extracted in the clear. If a WSCA is able to export a private key in encrypted format, the resulting level of protection SHALL be equivalent to the protection level of the private key when stored in the WSCA. |

#### A.2.3.41 Topic 41 - Minimum requirements on PuB-EAAs rulebooks

See [Topic 12](#a2312-topic-12---attestation-rulebooks).

#### A.2.3.42 Topic 42 - Requirements for QTSPs to access Authentic Sources

##### Description <!-- omit from toc -->

This Topic discusses the ability of QTSPs issuing electronic attestations of
attributes to verify those attributes by electronic means at the request
of the User, wherever those attributes rely on Authentic Sources within
the public sector.  

##### HLRs <!-- omit from toc -->

| **Index** | **Requirement specification** |
|-----------|------------------|
| QTSPAS_01 | In accordance with technical specifications referred to in QTSPAS_07, Member States SHALL define: - discovery mechanisms that enable QTSPs to request information about Authentic Sources or designated intermediaries recognised at the national level. This includes information regarding the attributes of a natural or legal person for which the Authentic Source or designated intermediary is considered a primary source, or for which it is recognised as authentic in accordance with Union law or national law, including administrative practices. - procedures for QTSPs to request the verification of attributes from Authentic Sources. |
| QTSPAS_02 | An Authentic Source in the public sector, or its designated intermediary, SHALL implement an interface complying with the technical specification mentioned in QTSPAS_07 for receiving verification requests and sending responses. For each received request, the Authentic Source SHALL - identify and authenticate the requestor in such a way that it can subsequently determine whether the requestor is a QTSP issuing qualified electronic attestation of attributes, for example by means of a lookup in the QTSP Trusted List. - authenticate the User and obtain their approval, if it is legally obliged to do so, in addition to the User authentication and approval already performed by the QTSP according to QTSPAS_08. - verify whether the attribute values claimed by the QTSP match the values held by the Authentic Source; and, finally, - respond with one of the following for each attribute: +'match', if the attribute value held for this User by the Authentic Source is identical to the value claimed by the QTSP, + 'no match', if the attribute value held for this User by the Authentic Source is not identical to the value claimed by the QTSP, including if the Authentic Source is the authentic source for this attribute but does not hold a value for this User, +'unknown', if the Authentic Source is not the authentic source for this attribute. |
| QTSPAS_03 | An Authentic Source or designated intermediary SHALL respond to a verification request for attributes by any QTSP issuing qualified electronic attestation of attributes.|
| QTSPAS_04 | An Authentic Source or designated intermediary SHALL implement the technical specifications mentioned in QTSPAS_01, so that the QTSP will receive the result of the verification of the requested attributes as described in QTSPAS_02. If the verification is deferred, the response to the QTSP SHALL include the maximum time that it will take to verify the requested attributes, and a unique identifier that the QTSP SHALL use to obtain the result of the verification. |
| QTSPAS_05 | A QTSP SHALL send an attribute verification request directly to the Authentic Source or designated intermediary recognised at national level, after discovering it using the mechanisms mentioned in QTSPAS_01. |
| QTSPAS_06 | Member States SHALL specify the processes and mechanisms to designate the Authentic Sources or intermediaries recognised at national level in accordance with Union or national law, allowing these Authentic Sources or intermediaries to verify the attributes presented to them by QTSPs. |
| QTSPAS_07 | The Commission SHALL publish, in cooperation with the European Digital Identity Cooperation Group, a technical specification, referring to applicable standards, specifications and procedures, that will cover at least the attributes specified in Annex VI, wherever those attributes rely on Authentic Sources within the public sector, for which Member States must ensure that measures are taken to allow qualified providers of electronic attestations of attributes to verify by electronic means, at the request of the User, their authenticity against the relevant authentic source. |
| QTSPAS_07a | The standards and procedures mentioned in QTSPAS_07 SHOULD, whenever possible, be aligned and compatible with those used for the platforms implementing the Once Only Technical System (OOTS). *Note: There is a clear synergy of both of these data exchange approaches. In fact, the national OOTS node would be a candidate for acting as an intermediary between QTSPs issuing QEAAs and the Authentic Sources.* |
| QTSPAS_08 | A QTSP SHALL obtain approval from the User to verify the authenticity of the attributes, before requesting the verification of those attributes by the relevant Authentic Source or designated intermediary. |

#### A.2.3.43 Topic 43 - Embedded disclosure policies

##### Description <!-- omit from toc -->

This topic is focused on identifying high-level requirements for disclosure
policies which may be embedded in an attestation. Such a policy may be created
by the Attestation Provider, and allows the Wallet Unit, using data obtained
from the Relying Party, to determine whether the Attestation Provider agrees
with releasing attributes from the attestation to the Relying Party. Note that
an embedded disclosure policy, if present, is applicable for any attribute in
the attestation.

Note that embedded disclosure policies do not apply to Wallet-to-Wallet interactions as described in [Topic 30](#a2330-topic-30---interaction-between-wallet-units).

##### HLRs <!-- omit from toc -->

| **Index** | **Requirement specification** |
|-----------|-----------------|
| EDP_01 | A Wallet Unit SHALL enable an Attestation Provider to optionally express an embedded disclosure policy for a QEAA, PuB-EAA, or non-qualified EAA. *Note: The [European Digital Identity Regulation] does not contain a requirement for PIDs to be able to contain an embedded disclosure policy.* |
| EDP_02 | A Wallet Unit SHALL support embedded disclosure policies implementing the 'Authorised relying parties only policy' described in Annex III of Implementing Regulation (EU) 2024/2979. Such an embedded disclosure policy SHALL contain a list of EU-wide unique identifiers of Relying Parties as specified in Reg_32. The Wallet Unit SHALL retrieve the identifier from the Relying Party access certificate presented by the Relying Party, and compare it to the list of authorised identifiers in the policy. _Note: If the Relying Party is an intermediary, see EDP_2a_  |
| EDP_2a | If the Relying Party is an intermediary, the Wallet Unit SHALL retrieve the name and the unique identifier of the 'end' Relying Party from the presentation request and use them to obtain information from the Registrar's on-line service on the 'end' Relying Party and an intermediary it is linked to (to check if it is the same entity as in the access certificate). |
| EDP_03 | A Wallet Unit SHALL support embedded disclosure policies implementing the 'Specific root of trust' policy described in Annex III of Implementing Regulation (EU) 2024/2979. Such an embedded disclosure policy SHALL contain a list of root or intermediate certificates used for signing Relying Party access certificates. The Wallet Unit SHALL compare the certificate chain that was used to sign the access certificate provided by the Relying Party to the list of authorised root or intermediate certificates in the policy. |
| EDP_04 | Empty |
| EDP_05 | An embedded disclosure policy SHOULD contain a link to a website of the Attestation Provider explaining the disclosure policy in layman's terms. If this is the case, the Wallet Unit SHALL display the link to the User and allow them to navigate to that website. |
| EDP_06 | The Wallet Unit SHALL evaluate an embedded disclosure policy in conjunction with the information received from the requesting Relying Party, in order to determine if the Relying Party has permission from the Attestation Provider to access the requested attestation. |
| EDP_07 | The Wallet Unit SHALL enable the User, based on the outcome of the evaluation of the applicable embedded disclosure policy(s), to deny or allow the presentation of the requested attestation to the Relying Party. |
| EDP_08 | The Commission SHALL take measures to ensure a technical specification is created establishing common mechanisms for the specification of embedded disclosure policies by Attestation Providers, and for the evaluation of such policies by Wallet Units. |
| EDP_09 | An Attestation Provider SHALL include an embedded disclosure policy (if any) by value in the Issuer metadata related to the attestation, in compliance with the [OpenID4VCI] issuance protocol or an extension thereof specified in the technical specification mentioned in EDP_08. |
| EDP_10 | During attestation issuance, a Wallet Unit SHALL retrieve and store locally the corresponding embedded disclosure policy, if any. |
| EDP_11 | An Attestation Provider SHALL revoke an attestation if a corresponding embedded disclosure policy is added, changed, or deleted. |

#### A.2.3.44 Topic 44 - Relying Party registration certificates

##### Description <!-- omit from toc -->

This topic identifies high-level requirements for Relying Party registration
certificates, which were introduced in Commission Implementing Regulation
2024/2982 [2024/2982]. A registration certificate may be is issued by a Relying Party
Registrar to a Relying Party during the registration process described in
[Topic 27](#a2327-topic-27---registration-of-pid-providers-providers-of-qeaas-pub-eaas-and-non-qualified-eaas-and-relying-parties).
It contains mainly the list of attributes registered by the Relying Party
according to Article 5b 2 (c) of the [European Digital Identity Regulation]. A
registration certificate is signed by the Registrar.
As a Relying Party is obliged to register for each purpose ("intended use") separately, a single Relying Party may possess multiple registration certificates.  

Commission Implementing Regulation 2024/2982 requires a Wallet Unit to
authenticate and validate the registration certificate (if available), and to display to the User the
information on the Relying Party as registered by the Registrar (information can be retrieved from the registration certificate or from the Registrar's on-line service). This enables Users
to verify that the attributes being requested by the Relying Party are within
the scope of their registered attributes ("intended use"), providing assurance that the request
is legitimate and trustworthy.

##### HLRs <!-- omit from toc -->

A. Issuance of Relying Party registration certificates

| **Index** | **Requirement specification** |
|-----------|-----------------|
| RPRC_01 | During the registration process for Relying Parties, as specified in [Topic 27](#a2327-topic-27---registration-of-pid-providers-providers-of-qeaas-pub-eaas-and-non-qualified-eaas-and-relying-parties), the Member State Registrar SHALL create and sign or seal a registration certificate and issue it to the Relying Party for each intended use requested to be registered by the Relying Party. The registration certificate SHALL comply with the applicable requirements in the technical specification mentioned in RPRC_02. *Note: See [Topic 52](#a2352-topic-52-relying-party-intermediaries).* |
| RPRC_02 | The Commission SHALL ensure that a technical specification is created, describing at least 1. the contents and format of registration certificates, 2. the signing method(s) used to ensure the authenticity of the registration certificates. 3. the trust infrastructure necessary for signing registration certificates and for verifying these signatures, including, if necessary, the use of Trusted Lists to establish trust in Member States Registrars and to distribute their trust anchors to Wallet Units. 4. the method used for binding each registration certificate to the Relying Party Instance access certificate that will be used during the same transaction. This binding method SHALL enable a Wallet Unit to verify that the registration certificate is bound to the Relying Party that authenticated itself using the access certificate. The binding method SHALL consider situations in which the Relying Party uses the services of an intermediary (see [Topic 52](#a2352-topic-52-relying-party-intermediaries)) to connect to the Wallet Unit. 5. whether or not a registration certificate must have a validity period. 6. the method to be used for revocation of registration certificates. Moreover, the technical specification SHALL describe the impact of revocation, especially compared to the impact of revocation of the Relying Party Instance access certificates. |
| RPRC_03 | The contents of a registration certificate issued per registered intended use of the Relying Party SHALL include at least information required in Annex V of the CIR for Relying Party Registration. If the Relying Party uses the services of an intermediary (see [Topic 52](#a2352-topic-52-relying-party-intermediaries)): the fact that this is the case, plus the user-friendly (common) name and unique identifier (as meant in RPRC_03a and RPRC_03b) of this intermediary. |
| RPRC_03a | The common Relying Party Registration Certificate Policy SHALL require that a Relying Party registration instance certificate contains a common name for the Relying Party instance, in a format suitable for presenting to a User. _Notes: - A Wallet Unit needs such a name when requesting User approval according to [[Topic 6](#a236-topic-6---relying-party-authentication-and-user-approval)] , - If Relying Party uses an Intermediary, both Intermediary and End-Relying Party common names need to be shown when requesting User approval and the User should be informed that the Intermediary is representing/acting on behalf of the End-Relying Party._ |
| RPRC_03b | The common Relying Party Registration Certificate Policy SHALL require that a Relying Party registration certificate contains an EU-wide unique identifier for the Relying Party, and SHALL specify a method for deriving such identifiers. _Notes: - The Wallet Instance needs such an identifier at least to lodge a complaint of suspicious Relying Party presentation requests to a data protection authority according to [Topic 50](#a2350-topic-50---blueprint-to-report-unlawful-or-suspicious-request-of-data). - The EU-wide unique identifier could, for example, be a concatenated list of one or more registered official wallet-relying party identifiers listed in Annex I(3) of the [Draft of the CIR for RP-Registration], expressed in semantic form defined in [ETSI EN319 412-1] sections 5.1.4 or 5.1.5 and used as the Distinguished Name (DN) of the certificate subject in both access and registration certificates of the Relying Party. Exact specification is left for the technical specifications to be developed by the European Commission._ |


B. Presentation and verification of Relying Party registration certificates

| **Index** | **Requirement specification** |
|-----------|-----------------|
| RPRC_04 | In both proximity and remote presentation flows, the Relying Party Instance SHALL transfer a Relying Party registration certificate to the Wallet Unit in the presentation request, according to the applicable standard's extension mentioned in RPRC_05. The registration certificate SHALL be included in the request by value, not by reference. *Note: This ensures that no external requests are necessary to validate the request, and that transactions are atomic and self-contained.* |
| RPRC_05 | The Commission SHALL ensure that extensions are specified for [ISO/IEC 18013-5] and for [OpenID4VP], allowing a Relying Party to transfer a Relying Party registration certificate to a Wallet Unit. These extensions SHALL comply with applicable requirements in these standards. |
| RPRC_06 | The Wallet Unit SHALL verify the authenticity and validity of the registration certificate according to the technical specification meant in RPRC_02. If the outcome of the verification is negative, the Wallet Unit SHALL, when asking for User approval according to RPA_07 and subject to the User preference set according to RPRC_08, notify the User that it could not verify whether the Relying Party registered the requested attributes with the competent authorities. |
| RPRC_07 | The Wallet Unit SHALL verify that all attributes requested in the presentation request are included in the list of attributes in the registration certificate (if available) or registered in the Relying Party registry (available through the Registrar's on-line service). If the outcome of the verification is negative, the Wallet Unit SHALL, when asking for User approval according to RPA_07 and subject to the User preference set according to RPRC_08, notify the User about the requested attributes that the Relying Party did not register. |
| RPRC_08 | A Wallet Unit SHOULD enable its User to set their preference for showing or hiding the notifications meant in RPRC_06 and RPRC_07. By default, the Wallet Unit SHALL show the notifications. |
| RPRC_09 | The EU-wide unique identifier SHALL be identical in all registration certificates issued for a given Relying Party. _Note: In case the registration certificates issued to an End-Relying Party are held and presented by an Intermediary (Relying Party), the given Relying Party meant in the text is the End-Relying Party. An Intermediary will obtain and hold registration certificates with non-identical unique identifiers._ |
| RPRC_10 | The Commission SHALL provide technical specifications establishing common Certificate Policy for registration certificates, covering at least management and selection of signing keys, revocation and lifecycle management of RPRCs on individual intended use level. _Note: The TS could set the provider of RPRCs to follow applicable parts of technical standards such as EN 319 401 (for General Policy Requirements for TSPs) and TS 119 461 (for identity proofing of Relying Party representatives)._ |
| PRRC 11 | There SHALL be only one valid registration certificate present in a presentation request for given intended use of a Relying Party. An error SHALL be reported (logged and shown for the User) by the Wallet Unit if it receives multiple registration certificates for the same intended use within same presentation request. |

#### A.2.3.45 Topic 45 - QEAA Rulebook

See [Topic 12](#a2312-topic-12---attestation-rulebooks).

#### A.2.3.46 Topic 46 - Protocols and interfaces for Presentation of PID and (Q)EAA with Relying Parties

See [Topic 1](#a231-topic-1---accessing-online-services-with-a-wallet-unit)
and [Topic 12](#a2312-topic-12---attestation-rulebooks).

#### A.2.3.47 Topic 47 - Protocols and interfaces for PID and (Q)EAA issuance, and (non-)qualified certificates issuance

See [Topic 10](#a2310-topic-10---issuing-a-pid-or-attestation-to-a-wallet-unit)/[23](#a2323-topic-23---pid-issuance-and-qeaa-issuance).

#### A.2.3.48 Topic 48 - Blueprint for requesting data deletion to Relying Parties

##### Description <!-- omit from toc -->

In this use case, a User requests the deletion of their personal attributes from
Relying Parties with which they have interacted through their Wallet Unit.

Users are concerned about having control over their personal data, thus
the function of requesting data deletion ensures a higher degree of
transparency, privacy and control of the Users over their personal
data.

This Topic lists high-level requirements related to the function
of Users requesting the deletion of their personal data from Relying
Parties through their Wallet Unit.

Note: A Relying Party may use the services of an intermediary to request data
from a Wallet Unit, see [Topic 52](#a2352-topic-52-relying-party-intermediaries).
However, such intermediaries are required to delete any data they obtain from a
Wallet Unit immediately after sending it to the Relying Party. Data deletion
requests are therefore always sent to the Relying Party, not the intermediary.

##### HLRs <!-- omit from toc -->

| **Index** | **Requirement specification** |
|-----------|------------------|
| DATA_DLT_01 | A Wallet Provider SHALL ensure that its Wallet Units support the technical specifications mentioned in DATA_DLT_02, allowing a User to request from a Relying Party the erasure of their attributes that were presented by that Wallet Unit to that Relying Party, in accordance with Regulation (EU) 2016/679. |
| DATA_DLT_02 | The Commission SHALL, in cooperation with the Member States, develop technical specifications for a Wallet Unit interface allowing a Wallet Unit to send attribute deletion requests to Relying Parties with whom it has interacted in the past. |
| DATA_DLT_03 | A Wallet Instance SHALL provide a function where the User may select one Relying Party or multiple Relying Parties for which an attribute deletion request must be submitted. |
| DATA_DLT_04 | A Wallet Instance SHALL be able to display the attribute deletion requests previously submitted through the Wallet Unit. |
| DATA_DLT_05 | A Wallet Unit SHALL include attribute deletion requests in a log so they can be presented to the User via the dashboard (as specified in [Topic 19](#a2319-topic-19---user-navigation-requirements-dashboard-logs-for-transparency)). |
| DATA_DLT_06 | The log SHALL include as a minimum: - Date of attribute deletion request, - Relying Party to which the request was made, - Attributes requested to be removed. |

#### A.2.3.49 Topic 49 - Protocol and interfaces for requesting data deletion to relying parties

Deleted.

#### A.2.3.50 Topic 50 - Blueprint to report unlawful or suspicious request of data

##### Description <!-- omit from toc -->

In this use case, a User reports a Relying Party to the competent national data
protection authority, because the User claims that this Relying Party sent an
unlawful or inappropriate request for attribute to the Wallet Unit. Users are
concerned about having control over their personal data, and specifically about
a Relying Party over-asking for personal information, thus the function of
reporting suspicious or inappropriate requests ensures a higher degree of
transparency, privacy and control of the Users over their personal data.

This topic lists high-level requirements related to the function of Users
reporting unlawful or inappropriate attribute requests from Relying Parties.

##### HLRs <!-- omit from toc -->

| **Index** | **Requirement specification** |
|-----------|--------------------|
| RPT_DPA_01 | A Wallet Unit SHALL provide an interface to lodge a complaint of suspicious Relying Party presentation requests to the DPA of the Member State that provided the Wallet Unit. |
| RPT_DPA_02 | The User interface enabling a User to start the process of lodging a complaint SHALL be accessible via the Wallet Instance. |
| RPT_DPA_03 | A Wallet Provider SHALL implement the interface in compliance with national procedural law and administrative practices. |
| RPT_DPA_04 | A Wallet Unit SHALL enable the lodged complaint to be substantiated, including information to identify the Relying Party, their presentation request, and the User's allegation. |
| RPT_DPA_05 | A Wallet Unit SHALL keep reports sent to the DPA in a log file so that it can be presented to the User in the dashboard (as specified in [Topic 19](#a2319-topic-19---user-navigation-requirements-dashboard-logs-for-transparency)). |

#### A.2.3.51 Topic 51 - PID or attestation deletion

##### Description <!-- omit from toc -->

This topic lists high-level requirements related to a User deleting a PID or
attestation from their Wallet Unit.

##### HLRs <!-- omit from toc -->

| **Index** | **Requirement specification** |
|-----------|--------------------|
| PAD_01 | A Wallet Unit SHALL at any time enable the User to delete any PID or attestation from their Wallet Unit. |
| PAD_02 | If the User indicates that a PID or attestation must be deleted, and the Wallet Unit contains multiple PIDs or attestation having the corresponding attestation type and Provider, a Wallet Unit SHALL delete all of these PIDs and attestations simultaneously. *Note: This situation may occur if the PID Provider or Attestation Provider issued a batch of attestations to the Wallet Unit, rather than a single one.* |
| PAD_03 | If the Wallet Unit deletes a PID or attestation on the User's request, the Wallet Unit SHALL NOT notify the respective PID Provider or Attestation Provider. *Note: This is a matter of User privacy.* |
| PAD_04 | If the Wallet Unit deletes a PID or attestation on the User's request, the Wallet Unit SHALL ensure that all cryptographic key material in the WSCA related to this PID or attestation is securely destroyed. *Note: Key deletion is a cryptographic key operation and requires User authentication, as specified in requirement WIAM_14.* |
| PAD_05 | If a Wallet Unit supports the [W3C Digital Credentials API] and it deletes a PID or attestation on the User's request, the Wallet Instance SHALL disclose the fact that it no longer stores this PID or attestation to the Digital Credentials API framework. |

#### A.2.3.52 Topic 52 Relying Party intermediaries

##### Description <!-- omit from toc -->

This topic lists high-level requirements regarding so-called intermediaries,
which form a special class of Relying Party. Article 5b (10) of the [European
Digital Identity Regulation] states "Intermediaries acting on behalf of relying
parties shall be deemed to be relying parties and shall not store data about the
content of the transaction". Such an intermediary is a party that offers
services to Relying Parties to, on their behalf, connect to Wallet Units and
request the User attributes that these Relying Parties need. The intermediary
then performs all necessary verifications, and, if successful, sends the
presented attributes to the intermediated Relying Party. This implies that an
intermediary performs all tasks assigned to a Relying Party in this ARF on
behalf of the intermediated Relying Party.

##### HLRs <!-- omit from toc -->

| **Index** | **Requirement specification** |
|-----------|--------------------|
| RPI_01 | An intermediary SHALL register as a Relying Party, in accordance with all requirements in [Topic 27](#a2327-topic-27---registration-of-pid-providers-providers-of-qeaas-pub-eaas-and-non-qualified-eaas-and-relying-parties). *Note: This implies that an intermediary obtains an access certificate containing its own name and unique Relying Party identifier.* |
| RPI_02 | An intermediary is acting only on behalf of another RP, but from the Registrar and the regulation's point of view is considered as a Relying Party and may obtain a registration certificate according to [Topic 44](#a2344-topic-44---relying-party-registration-certificates), containing its name and identifier. |
| RPI_03 | An intermediary SHALL register at the Registrar each Relying Party it is acting on behalf, as well as each intended use separately related to a given Relying Party. Depending on Registrar's policy, the intermediary may receive registration certificates related to each registration, according to the requirements in [Topic 44](#a2344-topic-44---relying-party-registration-certificates). The registration certificate SHALL contain intermediated Relying Party's name and unique identifier, as well as the list of attributes registered for that Relying Party's intended use. |
| RPI_04 | When issuing a registration certificate for a Relying Party via an intermediary, the Registrar SHALL verify, in a manner to be decided by Registrar's Member State, that the Relying Party will indeed use the services of the intermediary to interact with Wallet Units. |
| RPI_05 | When issuing a registration certificate for a Relying Party via an intermediary, the Registrar SHALL include in the registration certificate the attributes meant in RPRC_03a and RPRC_03b containing the name and unique identifier of the Relying Party, as well as of the intermediary. |
| RPI_06 | When requested by a Relying Party, an intermediary SHALL request presentation of attributes from a specific Wallet Unit, using the intermediary's access certificate meant in requirement RPI_01, and the registration certificate of the Relying Party, as meant in RPI_03. |
| RPI_07 | In case a Wallet Unit receives a presentation request from an intermediary on behalf of a Relying Party, during the Relying Party authentication it SHALL verify the name of the intermediary and display this name to the User when asking for User consent for the presentation, as described in the requirements RPA_06a and RPA_06d. |
| RPI_08 | When a Wallet Unit presents to an intermediary any User attributes from a PID or attestation, the intermediary SHALL, after successfully carrying out the verifications in RPI_09, forward these attributes (only) to the Relying Party on behalf of which the presentation request was made. If any of the verifications in RPI_09 fail, the intermediary SHALL NOT forward any attributes to the Relying Party. |
| RPI_09 | When a Wallet Unit presents to an intermediary any attributes from a PID or attestation, the intermediary SHALL verify the authenticity of the PID or attestation, its revocation status, device binding, and User binding, as well as any combined presentation of attributes, if applicable, as specified in this ARF and if agreed with the Relying Party. Furthermore, the intermediary SHALL verify the authenticity of the Wallet Unit and its revocation status, as specified in this ARF - if agreed with the Relying Party. *Note: This ARF does not mandate that a Relying Party must carry out all of these verifications. Therefore, the intermediary and any Relying Party using its services must agree on what verifications the intermediary will carry out.* |
| RPI_10 | The intermediary SHALL delete any PIDs, attestations, or WUAs it obtained from the Wallet Unit, including any User attributes, completely and immediately after it has sent the User attributes to the intermediated Relying Party. If the intermediary does not send any User attributes to the intermediated Relying Party, for example because one of the verifications in the previous step failed, the intermediary SHALL delete the PIDs, attestations, or WUAs completely and immediately as soon as it has completed all necessary verifications. |

#### A.2.3.53 Topic 53 Zero-Knowledge Proofs

##### Description <!-- omit from toc -->

This topic lists high-level requirements for a Zero-Knowledge Proof scheme to be used within the EUDI Wallet ecosystem as a proof mechanism for PIDs and attestations. A Zero-Knowledge Proof (ZKP) is a cryptographic protocol that allows one party
(the prover) to convince another party (the verifier) that a given statement is
true without revealing any additional information beyond the validity of the
statement itself. This ensures that the verifier gains no knowledge about how
the prover knows the statement to be true, preserving privacy while enabling trust.

The topic of ZKPs for the EUDI Wallet ecosystem was introduced in the [Discussion Paper for Topic G](../../discussion-topics/g-zero-knowledge-proof.md). The high-level requirements in this Topic were taken from that discussion paper.

##### HLRs <!-- omit from toc -->

| **Index** | **Requirement specification** |
|-----------|--------------------|
| ZKP_01 | A ZKP scheme SHALL provide support for the following generic functions, while hiding all attributes of PIDs or attestations: (i) generation of a proof that an (some) attribute(s) having a specific value is (are) included in a PID or attestation, (ii) generation of a proof that a PID or attestation is within its validity period, (iii) generation of a proof that a PID or attestation has not been revoked, and (iv) generation of a proof that a PID or attestation is bound to a key stored in the WSCD of the Wallet Unit. Additionally, a ZKP scheme SHOULD provide support for the following function, which SHOULD  be used only when hiding the PID Provider or Attestation Provider is necessary: (v) generation of a proof that a PID or attestation has been issued by a trusted PID Provider or Attestation Provider, without revealing the PID Provider or Attestation Provider. *Notes: - See section 4.1.1 of the Discussion Paper for Topic G.* |
| ZKP_02 | A ZKP scheme SHALL support proving possession of attestation of a given type. *Note: See section 4.1.2 and 4.1.3 of the Discussion Paper for Topic G.* |
| ZKP_03 | A ZKP scheme SHOULD support the privacy-preserving binding of an attestation to a PID. In addition to the generic functions defined in ZKP_01, for this use case, a ZKP scheme SHALL provide support for the following functions: (i) generation of a proof that the Wallet Unit stores an attestation and a PID and that the attestation includes a specific attribute, having a specific value, which is also present in the PID. *Note: See section 4.1.4 of the Discussion Paper for Topic G.* |
| ZKP_04 | A ZKP scheme SHOULD support the derivation of a verifiable User pseudonym, by combining an attribute value that is unique for the User with Relying Party-specific context (e.g., the Relying Party identifier) In addition to the generic functions defined in ZKP_01, for this use case, a ZKP scheme SHALL provide support for the following functions: (i) generation of a request for the issuance of an attestation that includes a secret attribute unique to the User, without revealing this attribute to the Attestation Provider, (ii) generation of an attestation presentation that includes a verifiable pseudonym derived from the secret attribute, a Relying Party identifier, and context-related information. *Note: See section 4.1.5 of the Discussion Paper for Topic G.* |
| ZKP_05 | A ZKP scheme SHALL be usable in both remote and proximity presentation flows. While the inclusion of ZKP will introduce computational and verification delays, these delays SHALL NOT critically undermine or defeat the purpose of the Relying Party service (e.g. because of a critical impact on the User experience of the Wallet Unit). |
| ZKP_06 | A ZKP scheme SHOULD be able to generate proofs for already issued PIDs and attestations in the formats specified in [ISO/IEC 18013-5] or [SD-JWT VC]. |
| ZKP_07 | A ZKP scheme SHALL NOT introduce any additional communication or information that could be used to track or link User activity during, before, or after proof generation. |
| ZKP_08 | A ZKP scheme SHALL rely solely on algorithms standardised by a standardisation organisation recognised by the Commission or in a standard recognised by the Commission. |
| ZKP_09 | Use of a ZKP scheme SHALL NOT prevent the Wallet Unit's ability to provide User authentication with Level of Assurance High. |



---
title: "European Digital Identity Wallet"
subtitle: "ARF Annex 3.01 - PID Rulebook"
...

# ANNEX 3.01 - PID Rulebook

## 1 Introduction

### 1.1 Document scope

This document is the natural-person Person Identification Data (PID) Rulebook
and is part of the Architecture Reference Framework (ARF). It specifies
how the mandatory and optional person identification data for the natural
person, as defined in Tables 1 and 2 in the Annex of the Commission Implementing
Regulation on PID and EAA [CIR 2024/2977], as well as the metadata specified in
Table 5 of that CIR, will be encoded within the EUDI Wallet ecosystem.
Additionally, this document specifies further optional PID attributes that are
not included in the CIR.

This document also specifies how a PID and all attributes in it are encoded if
the PID complies with [ISO/IEC 18013-5] and if it complies with [SD-JWT VC].

Person identification data for the legal person is out of scope of this document.

This PID Rulebook complies with all applicable requirements in Topic 12
(Attestation Rulebooks) in Annex 2 of the Architecture Reference Framework.

### 1.2 Document structure

This PID Rulebook is structured as follows:

- [Chapter 2](#2-pid-attributes-and-metadata) describes the PID attributes and
metadata on a generic level, regardless of the encoding used for the PID. Most
of the content of this chapter is a direct copy of the Annex of Commission
Implementing Regulation 2024/2977 on PID and EAA. However, a few additional
attributes are specified in this chapter.
- [Chapter 3](#3-isoiec-18013-5-compliant-encoding-of-pid) specifies how the PID
attributes and metadata are encoded in case the PID complies with [ISO/IEC
18013-5].
- [Chapter 4](#4-sd-jwt-vc-based-encoding-of-pid) specifies how the PID
attributes and metadata are encoded in case the PID complies with [SD-JWT VC].

### 1.3 Key words

This document uses the capitalised key words 'SHALL', 'SHOULD' and 'MAY' as
specified in [RFC 2119], i.e., to indicate requirements, recommendations and
options specified in this document.

In addition, 'must' (non-capitalised) is used to indicate an external
constraint, i.e., a requirement that is not mandated by this document, but, for
instance, by an external document. The word 'can' indicates a capability,
whereas other words, such as 'will', and 'is' or 'are' are intended as
statements of fact.

### 1.4 Terminology

This document uses the terminology specified in [Annex 1](../annex-1/annex-1-definitions.md) of the ARF.

## 2 PID attributes and metadata

### 2.1 Introduction

Sections [2.2](#22-mandatory-attributes-specified-in-cir-20242977), [2.3](#23-optional-attributes-specified-in-cir-20242977), [2.4](#24-mandatory-metadata-specified-in-cir-20242977) and [2.5](#26-additional-optional-attributes-specified-in-this-rulebook) of this chapter list the mandatory and optional
PID attributes and PID metadata defined in CIR 2024/2977. [Section 2.6](#26-additional-optional-attributes-specified-in-this-rulebook) lists the optional PID attributes additionally defined in this PID Rulebook.

Note that, when requesting PID attributes from a Wallet Unit, a Relying Party is not required to request all mandatory attributes. Also, a User is allowed to refuse to present a mandatory attribute, if it is requested by a Relying Party.

The data identifiers and definitions given in Sections 2.2, 2.3, 2.4, and 2.5
are identical to those in CIR 2024/2977, except where explicitly indicated that
some further explanations have been added in this Rulebook.

All data identifiers and definitions in this chapter are independent of any
encoding used. Consequently,

- the data identifiers in these tables are not necessarily the same as the
attribute identifiers used for PIDs complying with [ISO/IEC 18013-5]. [Chapter 3](#3-isoiec-18013-5-compliant-encoding-of-pid) specifies the data element
identifiers to be used for PIDs in [ISO/IEC 18013-5] format
- the data identifiers in these tables are not necessarily the same as the claim
names used for PIDs complying with [SD-JWT VC]. [Chapter 4](#4-sd-jwt-vc-based-encoding-of-pid) specifies the attribute identifiers to be
used for such PIDs.

### 2.2 Mandatory attributes specified in CIR 2024/2977

| **Data Identifier** | **Definition** |
|------------------------|--------------|
| family_name | Current last name(s) or surname(s) of the user to whom the person identification data relates. |
| given_name | Current first name(s), including middle name(s) where applicable, of the user to whom the person identification data relates. |
| birth_date | Day, month, and year on which the user to whom the person identification data relates was born. |
| birth_place | The country as an alpha-2 country code as specified in ISO 3166-1, or the state, province, district, or local area or the municipality, city, town, or village where the user to whom the person identification data relates was born. |
| nationality | One or more alpha-2 country codes as specified in ISO 3166-1, representing the nationality of the user to whom the person identification data relates. |

### 2.3 Optional attributes specified in CIR 2024/2977

| **Data Identifier** | **Definition** |
|------------------------|--------------|
| resident_address | The full address of the place where the user to whom the person identification data relates currently resides or can be contacted (street name, house number, city etc.). |
| resident_country | The country where the user to whom the person identification data relates currently resides, as an alpha-2 country code as specified in ISO 3166-1. |
| resident_state | The state, province, district, or local area where the user to whom the person identification data relates currently resides. |
| resident_city | The municipality, city, town, or village where the user to whom the person identification data relates currently resides. |
| resident_postal_code | The postal code of the place where the user to whom the person identification data relates currently resides. |
| resident_street | The name of the street where the user to whom the person identification data relates currently resides. |
| resident_house_number | The house number where the user to whom the person identification data relates currently resides, including any affix or suffix. |
| personal_administrative_number | A value assigned to the natural person that is unique among all personal administrative numbers issued by the provider of person identification data. Where Member States opt to include this attribute, they shall describe in their electronic identification schemes under which the person identification data is issued, the policy that they apply to the values of this attribute, including, where applicable, specific conditions for the processing of this value. |
| portrait | Facial image of the wallet user compliant with ISO 19794-5 or ISO 39794 specifications. **Further clarification added in this PID Rulebook:** The detailed format of the portrait is specified in requirement PID_03 in [Annex 2, Topic 3](../annex-2/annex-2-high-level-requirements.md#a233-topic-3---pid-rulebook). |
| family_name_birth | Last name(s) or surname(s) of the User to whom the person identification data relates at the time of birth. |
| given_name_birth | First name(s), including middle name(s), of the User to whom the person identification data relates at the time of birth. |
| sex | Values shall be one of the following: 0 = not known; 1 = male; 2 = female; 3 = other; 4 = inter; 5 = diverse; 6 = open; 9 = not applicable. For values 0, 1, 2 and 9, ISO/IEC 5218 applies. |
| email_address | Electronic mail address of the user to whom the person identification data relates, in conformance with [RFC 5322]. |
| mobile_phone_number | Mobile telephone number of the User to whom the person identification data relates, starting with the '+' symbol as the international code prefix and the country code, followed by numbers only. |

### 2.4 Mandatory metadata specified in CIR 2024/2977

| **Data Identifier** | **Definition** |
|------------------------|--------------|
| expiry_date | Date (and if possible time) when the person identification data will expire. **Further clarification added in this PID Rulebook:** This attribute, as well as the optional issuance_date attribute specified in [Section 2.6](#26-additional-optional-attributes-specified-in-this-rulebook), pertains to the administrative validity period of the PID. It is up to the PID Provider to decide whether a PID has an administrative validity period. However, if present, it in general is different from the technical validity period of a PID. The technical validity period is a mandatory element of all PIDs (and also attestations) in the EUDI Wallet ecosystem. It typically is short, a few days or weeks at most, if not shorter, to mitigate challenges regarding tracking of Users by malicious Relying Parties based on the repeated presentation of the same PID. On the other hand, the administrative validity period is typically at least a few years long. During the administrative validity period of a PID, the PID Provider will therefore provide multiple successive PIDs to a User, typically without any actions being expected from the User. However, when the administrative validity period of a PID ends, typically the User has to apply for an entirely new PID.|
| issuing_authority | Name of the administrative authority that issued the person identification data, or the ISO 3166 alpha-2 country code of the respective Member State if there is no separate authority entitled to issue person identification data. |
| issuing_country | Alpha-2 country code, as specified in ISO 3166-1, of the country or territory of the provider of the person identification data. |

### 2.5 Optional metadata specified in CIR 2024/2977

| **Data Identifier** | **Definition** |
|------------------------|--------------|
| document_number | A number for the person identification data, assigned by the provider of person identification data. |
| issuing_jurisdiction | Country subdivision code of the jurisdiction that issued the person identification data, as specified in ISO 3166-2:2020, Clause 8. The first part of the code shall be the same as the value for the issuing country. |
| location_status | The location of validity status information on the person identification data where the providers of person identification data revoke person identification data. |

### 2.6 Additional optional attributes specified in this Rulebook

| **Data Identifier** | **Definition** |
|------------------------|--------------|
| issuance_date | Date (and if possible time) when the person identification data was issued and/or the administrative validity period of the person identification data began. See also the clarification for expiry_date in [Section 2.4](#24-mandatory-metadata-specified-in-cir-20242977). |
| age_over_18 | Attesting whether the User to whom the person identification data relates is currently an adult (true) or a minor (false). If present, the requirements in clause 7.2.5 of ISO/IEC 18013-5 are applicable for this attribute. |
| age_over_NN | Attesting whether the User to whom the person identification data relates is at least NN years old. N <> 18. Multiple instances of this attribute may be present, provided the value of NN is different in each of them. If present, the requirements in clause 7.2.5 of ISO/IEC 18013-5 are applicable for these attributes. |
| age_in_years | The current age of the User to whom the person identification data relates in years. |
| age_birth_year | The year when the User to whom the person identification data relates was born. |
| trust_anchor | This attribute indicates at least the URL at which a machine-readable version of the trust anchor to be used for verifying the PID can be found or looked up. *Note: This attribute corresponds to the location meant in Annex V point h) or Annex VII point h) of the [European Digital Identity Regulation], which is mandatory for QEAAs. This PID Rulebook adds this as an optional attribute for PIDs as well, so PID Providers are able to ensure that PIDs can be validated by Relying Parties in the same manner as QEAAs.* |

## 3 ISO/IEC 18013-5-compliant encoding of PID

### 3.1 Encoding of PID attributes and metadata

#### 3.1.1 Overview

The ISO/IEC 18013-5-compliant encoding of PID attributes and metadata is
specified in the table below. The table contains the following information for
all attributes:

- The first column lists the data identifier specified in
[Chapter 2](#2-pid-attributes-and-metadata) above.
- The second column lists the corresponding attribute identifier to be used in
presentation requests and responses according to [ISO/IEC 18013-5].
- The third column indicates the encoding of each attribute. This column uses
CDDL representation types defined in [RFC 8610]. The following notes and
requirements apply:
    - tstr, uint, bstr, bool and tdate are CDDL representation types defined in
  [RFC 8610].
    - Regarding type tstr: this document confirms that, as specified in RFC
    8949, a tstr SHALL be encoded in UTF-8 and SHALL support the full Unicode
    range.
    - All attributes having encoding type tstr SHALL have a maximum length of
    150 characters.
    - This document specifies full-date as full-date = #6.1004(tstr), where tag
    1004 is specified in [RFC 8943].
    - In accordance with [RFC 8949], section 3.4.1, a tdate attribute SHALL
    contain a date-time string as specified in [RFC 3339]. In accordance with
    [RFC 8943], a full-date attribute SHALL contain a full-date string as
    specified in [RFC 3339].
    - The following requirements apply to the representation of dates in
    attributes, unless otherwise indicated:
        - Fractions of seconds SHALL NOT be used;
        - A local offset from UTC SHALL NOT be used; the time-offset defined in
        [RFC 3339] SHALL be to "Z".
    - RFC 8949, section 4.2, describes four rules for canonical CBOR. Three of
    those rules SHALL be implemented for all CBOR structures in PIDs, as
    follows:
        - integers (major types 0 and 1) SHALL be as small as possible;
        - the expression of the length in a bstr, tstr, array or map SHALL be as
        short as possible;
        - indefinite-length items SHALL be made into definite-length items.

| **Data Identifier** | **Attribute identifier** | **Encoding format** |
|------------------------|--------------|------------------|
| family_name | family_name | tstr |
| given_name | given_name | tstr |
| birth_date | birth_date | full-date, see [Section 3.1.4](#314-attribute-birth_date). |
| birth_place | place_of_birth | See [Section 3.1.5](#315-attribute-birth_place). |
| nationality | nationality | nationalities, see [Section 3.1.2](#312-attribute-nationality). |
| resident_address | resident_address | tstr |
| resident_country | resident_country | tstr |
| resident_state | resident_state | tstr |
| resident_city | resident_city | tstr |
| resident_postal_code | resident_postal_code | tstr |
| resident_street | resident_street | tstr |
| resident_house_number | resident_house_number | tstr |
| personal_administrative_number | personal_administrative_number | tstr |
| portrait | portrait | bstr |
| family_name_birth | family_name_birth | tstr |
| given_name_birth | given_name_birth | tstr |
| sex | sex | uint |
| email_address | email_address | tstr |
| mobile_phone_number | mobile_phone_number | tstr |
| expiry_date | expiry_date | tdate or full-date |
| issuing_authority | issuing_authority | tstr |
| issuing_country | issuing_country | tstr |
| document_number | document_number | tstr |
| issuing_jurisdiction | issuing_jurisdiction | tstr |
| location_status | - | See [Section 3.1.3](#313-attribute-location_status). |
| issuance_date | issuance_date | tdate or full-date |
| age_over_18 | age_over_18 | bool |
| age_over_NN | age_over_NN | bool |
| age_in_years | age_in_years | uint |
| age_birth_year | age_birth_year | uint |
| trust_anchor | trust_anchor | tstr |

#### 3.1.2 Attribute nationality

The attribute nationality takes as its value an array of Alpha-2 country codes
as specified in ISO 3166-1. Using CDDL notation as specified in RFC 8610, the
encoding of this data element is:

```
nationalities = [
  \+ CountryCode
]

CountryCode = tstr ; Alpha-2 country code specified in ISO 3166-1
```

Note: If the User to whom the person identification data relates has multiple
nationalities (and the PID Provider is willing to attest to these multiple
nationalities), the PID Provider can include all of the nationalities in the
nationalities array. A potential drawback of this solution is that the User
cannot selectively disclose only one of these nationalities, since for ISO/IEC
18013-5-compliant attestations, always the entire array will be presented if the
User approves the presentation of the nationality attribute. A potential
solution to this challenge is for the PID Provider to include only one
nationality in the nationality attribute, and for the remaining nationalities
use one or more domestic data attributes specified according to requirement
PID_06 in [Annex 2, Topic 3](../annex-2/annex-2-high-level-requirements.md#a233-topic-3---pid-rulebook).

#### 3.1.3 Attribute location_status

For ISO/IEC 18013-5-compliant PIDs, the attribute location_status is
absent, since the PID issuer will add revocation information, if needed, to the MSO as specified in [ISO/IEC 18013-5].

#### 3.1.4 Attribute birth_date

For PIDs compliant with ISO/IEC 18013-5, dates are encoded as specified in RFC
8943. This encoding does not contain provisions for encoding partial dates. This
may cause challenges in case the birth date of a User is not (fully) known. To
deal with such cases, a PID Provider could adopt a policy to choose appropriate
values for the unknown date elements. However, mandating such a policy is out of
scope of this document.

#### 3.1.5 Attribute place_of_birth

The attribute place_of_birth SHALL contain at least one of the following key-value pairs: country, region, locality.
Using CDDL notation as specified in RFC 8610, the encoding of this data element is:

```
place_of_birth =
{
  ? country: tstr ; a single alpha-2 country code as specified in ISO 3166-1
  ? region: tstr ; the name of a state, province, district, or local area
  ? locality: tstr ; the name of a municipality, city, town, or village
}
```


## 4 SD-JWT VC-based encoding of PID

### 4.1 Encoding of PID attributes and metadata

### 4.1.1 Overview

Following requirement ARB_06b, SD-JWT VC-encoded PIDs use claim names that are either registered in the JSON Web
Token Claims Registry [IANA-JWT-Claims], are Public Names as defined in [RFC 7519], or are Private Names specific
to the attestation type. The tables below map the data
identifiers defined above to the corresponding claim names and specify the encoding format of the claim value.

A JSON string used in an SD-JWT VC-encoded PID SHALL be encoded in UTF-8 and SHALL support the full Unicode range, unless explicitly specified otherwise in the tables below or the references therein.

Note that a hierarchical claim name structure can be used in SD-JWT VC encoded
PIDs as SD-JWT allows for individual selective disclosure of objects
and their properties. A hierarchical claim name structure is indicated by the
notation `parent.child` in the tables below.

The following IANA registered claim names are to be used for PIDs:

| **Data Identifier** | **Attribute identifier** | **Encoding format** |**Reference/Notes** |
|-------------------- |--------------------------|---------------------|--------------------|
| family_name | family_name | string | Section 5.1 of [OIDC] |
| given_name | given_name | string | Section 5.1 of [OIDC] |
| birth_date | birthdate | string, ISO 8601-1 [ISO8601‑1] YYYY-MM-DD format | Section 5.1 of [OIDC] |
| birth_place | place_of_birth | JSON structure | Section 4.1 of [EKYC];  At least one of the members (country, region or locality) SHALL be present in the JSON structure |
| nationality | nationalities | array of strings | Section 4.1 of [EKYC]; using alpha-2 country codes as defined in [Section 2.2](#22-mandatory-attributes-specified-in-cir-20242977) |
| resident_address | address.formatted | string | Section 5.1 of [OIDC] |
| resident_country | address.country | string | Section 5.1 of [OIDC] |
| resident_state | address.region | string | Section 5.1 of [OIDC] |
| resident_city | address.locality | string | Section 5.1 of [OIDC] |
| resident_postal_code | address.postal_code | string | Section 5.1 of [OIDC] |
| resident_street | address.street_address | string | Section 5.1 of [OIDC] |
| resident_house_number | address.house_number | string | Section 5.1 of [OIDC] |
| family_name_birth | birth_family_name | string | Section 4.1 of [EKYC] |
| given_name_birth | birth_given_name | string | Section 4.1 of [EKYC] |
| email_address | email | string | Section 5.1 of [OIDC] |
| mobile_phone_number | phone_number | string | Section 5.1 of [OIDC] |
| portrait | picture | string; data URL containing the base64-encoded portrait in JPEG format according to PID_03 in [Annex 2, Topic 3](../annex-2/annex-2-high-level-requirements.md#a233-topic-3---pid-rulebook)  | Section 5.1 of [OIDC] |

Note: The standard JWT claims nbf and exp are used to express the technical validity period of a SD-JWT VC-compliant PID.

The following Private Names specific to the attestation type defined in this document are to be used for PIDs:

| **Data Identifier** | **Attribute identifier** | **Encoding format** | **Notes** |
|---------------------|--------------------------|---------------------|-----------|
| expiry_date | date_of_expiry | string | ISO 8601-1 [ISO8601‑1] YYYY-MM-DD format, as defined in Section 5.4.4.2 of [EKYC Schema] |
| issuance_date | date_of_issuance | string | ISO 8601-1 [ISO8601‑1] YYYY-MM-DD format, as defined in Section 5.4.4.2 of [EKYC Schema] |
| personal_administrative_number | personal_administrative_number | string | |
| sex | sex | number | numeric encoding as described in [Section 2.3](#23-optional-attributes-specified-in-cir-20242977); gender from [OIDC] uses a different value range and is therefore not used |
| issuing_authority | issuing_authority | string | |
| issuing_country | issuing_country | string | |
| document_number | document_number | string | |
| issuing_jurisdiction | issuing_jurisdiction | string | |
| location_status | - | See [Section 4.2.2](#422-attribute-location_status) | |
| age_over_18 | age_equal_or_over.18 | boolean (see note below) | |
| age_over_NN | age_equal_or_over.NN | boolean (see note below) | |
| age_in_years | age_in_years | number | |
| age_birth_year | age_birth_year | number | |
| trust_anchor | trust_anchor | string | |

Note: Instead of separate claims for (for example) age_over_16, age_over_18, age_over_65, etc., a single claim age_equal_or_over is used. This claim is an object with properties for each age as follows:

```json
"age_equal_or_over": {
    "16": true,
    "18": true,
    "65": false
}
```


#### 4.2.2 Attribute location_status

For SD-JWT VC-compliant PIDs, the PID issuer will add validity status
information, if needed, as specified in [SD-JWT VC]. This PID Rulebook does not
specify a separate attribute for including the location of validity status
information.

### 4.2 Note on VCT

SD-JWT VC defines the Verifiable Credential Type (`vct`). A type comes
with associated metadata that, for instance, provides information about
the type itself, outlines a schema detailing the claims that are
optional or mandatory in the SD-JWT VC, and specifies their display
methods. Additionally, a type can extend another type, enabling
the creation of domestic types based on a common EU-wide type, while preserving
the mandatory claims from the base type. Domestic
types MAY however define additional claims and display information. Details
are defined in [SD-JWT VC].

This document defines the base type to be "urn:eudi:pid:1". As a convention, all
PIDs must use types in the namespace "urn:eudi:pid:".

SD-JWT VC specifies Type Metadata as a machine-readable format for information
regarding a type, including the information on claims such as what is contained
in this document. Requirement PID_15 in [Annex 2, Topic 3](../annex-2/annex-2-high-level-requirements.md#a233-topic-3---pid-rulebook) requires that the information on the
common EU-wide type as well as on any domestic types is published and
accessible in a catalog.

### 4.3 Example

EXAMPLE: The following example shows the payload of a PID in SD-JWT VC format before the encoding into the SD-JWT format.

```json
{
    "vct": "urn:eudi:pid:de:1",

    "given_name": "Jean",
    "family_name": "Dupont",
    "birthdate": "1980-05-23",

    "age_equal_or_over": {
        "12": true,
        "14": true,
        "16": true,
        "18": true,
        "21": true,
        "65": false
    },
    "age_in_years": 44,
    "age_birth_year": 1980,

    "address": {
        "street_address": "123 Via Appia",
        "locality": "Rome",
        "region": "Lazio",
        "postal_code": "00100",
        "country": "IT"
    },

    "nationalities": ["FR"],

    "sex": 5,

    "place_of_birth": {
        "country": "DD"
    },

    "cnf": {
        "jwk": {
            "kty": "EC",
            "crv": "P-256",
            "x": "52aDI_ur05n1f_p3jiYGUU82oKZr3m4LsAErM536crQ",
            "y": "ckhZ-KQ5aXNL91R8Eufg1aOf8Z5pZJnIvuCzNGfdnzo"
        }
    },

    "issuing_authority": "DE",
    "issuing_country": "DE"
}
```

Note: The `cnf` claim is used for expressing key binding in SD-JWT VCs.
The example above shows a public key in JWK format.

Note: Additional technical claims are not shown here, including
references to the issuer, validity status information, and more.

## 5 References

See [Chapter 9](../../architecture-and-reference-framework-main.md#9-references) of the ARF main document.

---
title: "European Digital Identity Wallet"
subtitle: "ARF Annex 3.02 - mDL Rulebook"
...

# ANNEX 3.02 - mDL Rulebook

*This is a working document that holds no legal value and does not
reflect any common agreement or position of the co-legislators. It
presents a state-of-play of ongoing work of the European Digital Identity Cooperation Group. This
document is being continuously updated and should not be considered
final.*

## 1 Introduction

This document is the mobile driving licence (mDL) Rulebook. It is part of the Architecture and Reference Framework for the EUDI Wallet ecosystem. It contains requirements specific to mDL attestations with the EUDI Wallet ecosystem.

This mDL Rulebook contains the following topics:

- [Chapter 2](#2-mdl-attribute-schema) specifies the mDL attribute schema. This
describes the structure, the type, the entity identifiers, and the logical
organisation of the mandatory and optional attributes of the mDL. It also
describes how Member States can specify any possible national attributes.

Further topics will be added if and when they are identified.

## 2 mDL attribute schema

## 2.1 Introduction

This document describes the structure, type, data element identifiers,
and logical organisation of the mandatory and optional attributes of the
mobile driving licence (mDL) attestation within the EUDI Wallet. It also
describes how Member States can specify any possible national
attributes.

Mobile driving licences are legally specified in the [proposed EC Regulation 2023_127](https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=celex%3A52023PC0127)
(4th Driving Licence Regulation). This Regulation specifies that mDLs shall
comply with the ISO/IEC 18013-5 standard. It does not mention any other
standards, in particular not [SD-JWT VC]. Consequently, mDLs issued to a Wallet
Unit SHALL NOT be implemented as [SD-JWT VC]-compliant attestations. This
document therefore specifies only an ISO/IEC 18013-5-compliant encoding.

### 2.2 ISO/IEC 18013-5 compliant encoding

The data model for ISO/IEC 18013-5-encoded mDLs is fully specified in
ISO/IEC 18013-5. No changes need to be made to this data model for an
mDL attestation within the EUDI Wallet ecosystem.

## 4 References

See [Chapter 9](../../architecture-and-reference-framework-main.md#9-references)
of the main ARF document.

<img align="right" height="50" src="https://raw.githubusercontent.com/eu-digital-identity-wallet/eudi-srv-web-issuing-eudiw-py/34015dc3c6f52529a99e673df1d4fa69d50f7ff5/app/static/ic-logo.svg"/><br/>

# Specification of EUDI Wallet Trust Mark

## Abstract

The present document specifies the technical specification and requirements for EUDI Wallet Trust Mark.

### [GitHub discussion](https://github.com/eu-digital-identity-wallet/eudi-doc-architecture-and-reference-framework/discussions/425)

## Versioning

| Version | Date       | Description                                                                |
|---------|------------|----------------------------------------------------------------------------|
| `0.1`   | 20.01.2025 | Initial version for discussion                                             |
| `0.2`   | 18.02.2025 | Version with first internal feedback and improved scoping                  |
| `0.3`   | 03.03.2025 | Version for public discussion with the Member States                       |
| `0.4`   | 03.04.2025 | Updated version based on discussions in 1st and 2nd focus group meetings   |
| `1.0`   | 25.04.2025 | Final version (v1.0)                                                       |

## 1 Introduction and Overview

The present document specifies technical and procedural aspects related to use of the **EU Digital Identity Wallet Trust Mark** (also referred as **EUDI Wallet Trust Mark** in this document) in the context of the EUDI Wallet, having regard to the [European Digital Identity Regulation], and in particular Articles 5a(5) and 3(50) thereof.

The purpose of a visible and recognisable trust mark is to add trust in the EUDI Wallet ecosystem and help the Users to recognise and validate the certification status of the EUDI Wallet Providers and their EUDI Wallet services.

### 1.1 Requirements in Regulation EU 2024/1183
 - According to Article 3 (50), the EUDI Wallet Trust Mark is defined as **"a verifiable, simple and recognisable indication which is communicated in a clear manner that a European Digital Identity Wallet has been provided in accordance with this Regulation.”**

 - According to Article 5a (5)(a) (iv), **the Trust Mark must be displayed to the User**.
 - According to Article 5a (8)(a), **the Member States shall provide validation mechanisms free-of-charge, in order to: (a) ensure that the authenticity and validity of European Digital Identity Wallets can be verified;**
- According to the Article 5d, the European Commission publishes the list of certified EUDI Wallets as an official list in the Official Journal of the European Union, thus acting as a reference for which Wallet Solutions are certified. **Removal from the list means certification is no longer valid**.

### 1.2 Scope for the Trust Mark Requirements and Design
The EUDI Wallet Trust Mark must be designed and copyright protected, as a kind of label, which is only allowed to be displayed if the EUDI Wallet of the User both complies to the requirements of EUDI Wallet Solutions (is a certified Wallet) while being recognised by at least one Member State. If either of the aforementioned base requirements become non-applicable, the Member States must inform the Commission and the Cooperation Group and state the reason for cancellation. Upon cancellation, the Wallet Provider must remove the visible trust mark from affected Wallet Solution, and any references to it.

The European Commission is responsible for the EUDI Wallet Trust Mark in terms of graphic design, ownership of the logo registration process and takes responsibility for drafting rules and usage guidelines, and distribution to the designated actors within the ecosystem.

As the Regulation does not specify what verifiable means, or where it shall be displayed, the realisation of the EUDI Wallet Trust Mark was conducted via collecting the business requirements, identifying any complexity limitations if any, and considering the priorities of the involved ecosystem stakeholders (Member States).

 > Note (to be removed before v1.0): Current version of the specificaiton reflexes the majority of opinions gathered from the Member States that attended the first meeting handling version 0.3, and those Member States' experts that provided review comments online after the meeting. The technical complexity of the solution was agreed to be minimised - as the ARF already defines technical solution ensuring the cryptographic trust of an individual Wallet Unit (the Wallet Unit Attestation).  

 The proposed mandatory high-level requirements define a solution that focuses on providing the EUDI Trust Mark logo only to valid Wallet Units ('EUDI Wallet Trust Mark'), and providing with it a direct link to the EU list of certified EUDI Wallets and/or the individual Wallet Solution page, located within the eIDAS Dashboard web site. The requirements are presented in the actor-oriented requirement format: **"As an *actor* I shall/should *verb* to achieve *my required goal*"**.

This document does not address the visual or user experience related design elements related to the trust mark; these are provided separately by the European Commission and may be derived from the final requirements listed in this specification.

 >NOTE 1: The presence and rendering of the EUDI Wallet Trust Mark in a Wallet Unit could also be bound to validity of the WUA. The third parties or European Commission MAY later decide to operate a wallet certification verification service based on presenting the WUA for this service, thus allowing on-demand verification of the Wallet Solution certification status for the User. The operating principle of this simple verification service is specified broadly in Section 2.2, and any requirements or components related to it marked as **OPTIONAL** in Sections 3 and 4 detailing exact technical solution.

>NOTE 2: Any possible requirements for trust indicators unrelated to the EUDI Wallet Solution are out of scope of this document. **The scope is the trust mark visible in the EUDI Wallet, not the Relying Party services and/or the Attestation Provider qualifications**. The Trust Mark analysis and solution may at a later stage be extended to other elements of the European Digital Identity ecosystem, so that the Users can be informed regarding the reliability and trustworthiness of the different Relying Parties they interact with.

### 1.3 Background: Existing European trust marks as a reference

To our knowledge, the European Commission has launched a few business-to-consumer type trust mark programmes related to EU Regulations: the earlier being the EU Trust Mark for Qualified Trust Services (launched as an Implementing Act for eIDAS Regulation) and the newer Ecommerce Europe Trustmark for safe and ethical cross-border ecommerce. These trust marks are both bound to EU regulation, but are probably facing very different types of end customers and their awareness among EU Member State citizens is probably not actively studied. These are included to provide a comparison/starting point for the EUDI Wallet Trust Mark specification.

#### 1.3.1 EU Trust Mark for Qualified Trust Services

[Commission Implementing Regulation (EU) 2015/806 of 22 May 2015 laying down specifications relating to the form of the EU trust mark for qualified trust services](http://data.europa.eu/eli/reg_impl/2015/806/oj) specifies a trust mark for QTSPs. Use of the trust mark is optional and it is not verifiable according to Article 23 (1) of Regulation 910/2014 (the eIDAS Regulation), therefore the way this trust mark is implemented may not meet the needs of EUDI Wallet Trust Mark.

Some visible uses of the QTSP trust mark for reference:

- [**TrustPro Web Page**](https://www.trustpro.eu/): Interactive logo, test this by browsing to the home page section just before the page footer area. Clicking on the EU Trust Mark links to the [EU/EEA Trusted List Browser](https://eidas.ec.europa.eu/efda/trust-services/browse/eidas/tls) page.
- [**Penneo QTSP page (blog)**](https://penneo.com/blog/qualified-trust-service-providers/): Passive use of the logo on the informative QTSP related blog page. The logo is in no way related to validation, the available validation means (checking from the EU LTL via the eIDAS Dashboard) are explained separately in the main text.

This overview of samples is in no way exhaustive as there may be well-hidden trust mark appearances among the EU QTSP web pages.

#### 1.3.2 Ecommerce Europe

The European Regulation on online dispute resolution for consumer disputes [EU 524/2013](http://data.europa.eu/eli/reg/2013/524/oj) states that "traders established within the European Union engaging in online sales or service contracts shall provide on their websites an electronic link to the European Online Dispute Resolution (ODR) platform". Consumers who have a problem with an online purchase can file complaints on the European ODR platform. Platform will close its operations by July 2025.

When present on an online shop, the Ecommerce Europe Trustmark shows that the online shop is nationally certified for safe e-commerce by the respective national e-commerce association, and that it complies with European laws and regulations. This is done via a visual trust mark which is available for online shops only via the Member State's associations that are formally affiliated to the Ecommerce Europe scheme. Most EU countries have joined it, but some are notably missing, whilst others are closing their safe e-commerce activities (e.g. Norway from 1 February 2025). National associations typically have defined their own national graphic trust mark logo, use of which happens ahead or in parallel with the Ecommerce Europe equivalent.

It seems that the Qualified Trust Service trust mark is just a logo specified by the Regulation 524/2013, whose usage is granted for QTSPs present on the EU list of trusted lists, whereas the Ecommerce Europe trust mark is usually accompanied with a Member State specific trusted e-shop certificate, which can in the best case be verified through simple user-familiar means, such as linking the trust mark icon to the national association's trust mark verification page which shows key information of the online shop provider. A good example is the Swedish trygg E-handel certificate; it is implemented as a web site script provided for the company by the association upon accomplishing the registration and checks.

National certificates are commercial and incur often both an onboarding fee and an annual maintenance fee. The "issuer" of the E-commerce certificate (the local member association) must check the applicant's compliance against safe e-commerce rules set by Regulation 524/2013, available via [The Ecommerce Europe Trustmark Code of Conduct](https://ecommercetrustmark.eu/the-code-of-conduct/), prior to certificate issuance.

Some examples of national associations and their trust mark onboarding processes and list of certified e-shops:

- **Trygg E-handel (Sweden Ecommerce)**: Onboarding page: [Om Trygg E-handel](https://tryggehandel.svenskhandel.se/om-trygg-e-handel/), member list page: [Certifierade e-handlare](https://tryggehandel.svenskhandel.se/certifierade-e-handlare/)
- **Shopping Secure trust mark (Thuiswinkel.org)**: Onboarding page: [Shopping Secure Trust Mark](https://www.thuiswinkel.org/en/trust/trustmarks/shopping-secure/), member list page: [Member Search Page](https://www.thuiswinkel.org/en/member-search/)


## 2 Functional description of EUDI Wallet Trust Mark

As a conclusion on the overview section, the approach for introducing the EUDI Wallet Trust Mark should be kept simple enough to ensure it can serve its intended (business) function without creating an overly complicated governance or technical framework for the Wallet Providers or other actors in the EUDI ecosystem to deploy in parallel to their main goal - provisioning and maintaining secure wallet solutions for the Member State citizens. The key is how the verifiability requirement of Art 3(50) is approached keeping the desired simplicity in mind, and therefore a solution that utilises already existing ecosystem components for trust, and provides human-centric verification of the User's EUDI Wallet is elaborated in this Section. Section 2.1 covers the mandatory part of the usage, and an optional EUDI Wallet verification service is described in Section 2.2. Mandatory requirements for realisation of the first solution are covered in Section 3.

### 2.1 Trust Mark UI view with links to trusted list of EUDI Wallets and Wallet certification information page
The proposed solution is to arrange any trust mark graphical elements (logo, image,...) and localised information about the wallet certification to the Wallet Unit by providing a set of necessary links to the data in a new (metadata-) object of the Wallet Unit Attestation (WUA).

The localised, human readable information, including the links to use for reviewing the certification status of the Wallet Solution of the User SHALL be rendered in user-friendly manner on Wallet Provider preferred UI view/views (all meeting the requirements set for the Wallet Users in section 2.1) combined with the presentation of EUDI Wallet Trust Mark graphical elements.

When a link shown on the UI view containing EUDI Wallet Trust Mark and provided information text is activated, User's device SHALL open up a new browser window, and depending on the link, bring the User either to the European Commission hosted page that contains full public listing of certified Wallet Solutions, or to the eIDAS dashboard sub-page that lists the information of the corresponding certified Wallet Solution. The sub-pages SHALL be queryable based on the Wallet Solution ID, the EU-wide unique identifier provided to the Wallet Solution after successful certification.

An UI view sample of this approach captured from the European Commission's design team working on UX and graphics for the Trust Mark is shown in Figure 1 - the User would click the 'EUDI Wallet Provider Trusted List' link and be transitioned through opening the device browser to EC's public web site listing all certified EUDI Wallets. The UI view contains also another link, 'Wallet information page', that would bring the User directly to the Wallet Solution specific sub-page on the eIDAS Dashboard site.

![Trust Mark with eIDAS dashboard links at Onboarding View](./img/ts1-eudiw-onboarding-with-trust-mark-fig1.png)

Figure 1. Welcome view of an EUDI Wallet with Trust Mark logo with text and informative links (concept image only)

### 2.2 EUDI Wallet verification tool (a service concept)

For a general technical note, the issuance of the WUA upon Wallet Unit activation allows creation of third party services that could function as on-demand Wallet verification services, issuing the Wallet Unit a suitable 'statement attestation' in exchange of the User presenting a valid WUA to this service. This attestation would work for the Users as a *visible* local cryptographic proof of the status of their Wallet Solution certification, aside of the user-invisible WUA.

This technical specification does not mandate provisioning of a separate EUDI Wallet verifier service by the European Commission or by any other ecosystem stakeholders. Functionality and requirements of services handling WUA verification in context of the EUDI Wallet Trust Mark (outside the WUA verification use cases already in the ARF) may be specified later. The concept is carried along in the specification architecture (Section 4) marked as OPTIONAL, and related requirements and components are marked with asterisk ('\*').

## 3 Actor-Oriented Requirements

The EUDI Wallet Trust Mark functionality related requirements are presented in this Section, separated per actor/role in the EUDI ecosystem.

### 3.1 (EUDI Wallet) User Requirements

**EWTM-U1**: As a future potential user of a EUDI Wallet, I want to have a clear understanding of how to distinguish real from fake EUDI Wallet Solutions.

> Note: This hints at the duty of the Commission to create clear documentation and guidance on distinguishing real EUDI Wallets from fake ones.

**EWTM-U2**: As a a potential User of a EUDI Wallet, I want to see if I’m about to install a Certified EUDI Wallet Solution issued, recognised or mandated by a Member State.

> Note: In lack of certification information at the official app downloading services this means providing such information as seen feasible - e.g. via the Wallet onboarding/download information pages hosted by the Member States and the European Commission.

**EWTM-U3**: As a potential User of a EUDI Wallet, I want to see which Member States support PID issuance to given Certified EUDI Wallet Solution.

> Note: Collecting this information to the list of certified EUDI Wallets at EC requires PID issuance support as information to be provided to the EC by notifying Member State.

**EWTM-U4**: As a user of a EUDI Wallet, after installation, I want a means to check that the EUDI Wallet Solution certification is legitimate as part of the EUDI Wallet Instance activation.

> Note: Certification related information is made available to the EUDI Wallet Unit via the WUA issuance.

**EWTM-U5**: As a User of a EUDI Wallet, I want a means to check on demand if the EUDI Wallet Unit that I am currently using is a Certified EUDI Wallet.

**EWTM-U6**: As a User of a EUDI Wallet, I want to be able to read fresh high-level information of the Certification status when I select (click or tap) a visual indicator (logo) of the EUDI Wallet Trust Mark in the EUDI Wallet Unit.

**EWTM-U7**: As a User of a EUDI Wallet, I want the EUDI Wallet Trust Mark to be always positioned in a standard location (such as UI view or menu item) in the EUDI Wallet Unit.

**EWTM-U8**: As a User of a EUDI Wallet, I want to get an out-of-band indication (e.g. push message or e-mail message) from the Wallet Provider if the certification status and thus the linked EUDI Wallet Trust Mark status of the EUDI Wallet Solution I use has been revoked.

> Note: The User is expected to have an arrangement (user account, with some authentication mechanism and user account) with the Wallet Provider. If the user has registered an email address for receiving news about the Wallet Solution, the revocation information could be part of the customer communications (and part of the terms of service agreed between the User and the Wallet Provider).

**EWTM-U9**: As a user of a EUDI Wallet, I want guidance on the EUDI Wallet on how to act if my EUDI Wallet Unit has been revoked.

> Note: Guidelines on how to deal with non-functioning app are easiest found from the app itself. The actual realisation may be part of the guidelines material to be created and provided by the European Commission.

**EWTM-U10**: As a physically impaired User of a EUDI Wallet, I want to have accessibility support within realisation of the requirements set in **EWTM-U4** - **EWTM-9**.

> Note: Accessibility considerations from [WCAG 2.1](https://www.w3.org/TR/WCAG21/) such as screen reader compatibility, color contrast, or keyboard navigation must to be addressed in the end-user implementation and guidelines to be provided. Users with visual impairments, cognitive disabilities, or low digital literacy may face challenges in:
> - perceiving the Trust Mark (e.g., reliance on visual-only indicators),
> - understanding certification status (e.g., clarity of meaning in B1-level local language) or
> - Reacting to certification changes (e.g., what actions should be taken if revoked?)


### 3.2 Wallet Provider Requirements

**EWTM-WP1**: As a Wallet Provider, I want  my right to use of the EUDI Wallet Trust Mark is handled as one outcome of the Wallet Solution certification process at the Member State level.

**EWTM-WP2**: As a Wallet Provider, I want a logo/logos with graphical guidelines for proper use of the EUDI Wallet Trust Mark in EUDI Wallet Solution implementation.

**EWTM-WP3**: As a Wallet Provider, I need early developer access to formal graphical element (with all of its potential variations, if they exist) of the EUDI Wallet Trust Mark for my development flow for embedding this element onto the well-defined user interface view in my EUDI Wallet Solution.

**EWTM-WP4**: As a Wallet Provider, I need EUDI Wallet Trust Mark deployment guidelines online (when allowed to show, where to show, how to deal with applicable mobile app store deployment and distribution rules if they impact the deployment of the Trust Mark) from the European Commission.

**EWTM-WP5**: As a Wallet Provider, I need online access to the EUDI Wallet Trust Mark logo and localised information texts about the Trust Mark and/or certification from the European Commission.

> Note: This online information data object is needed for the Wallet Unit to customise the UI view to the localisation language used by the User's mobile device. This data is accessible upon issuance of the issuance WUA to the Wallet Unit. See _TrustMarkResourceURL_.

**EWTM-WP6**: As a Wallet Provider I want to be able to link from the Wallet Unit's UI view with the EUDI Wallet Trust Mark graphics and information text to the European Commission-provided link to the eIDAS Dashboard page that shows the up-to-date list of official certified EUDI Wallets.

> Note: See _ListofCertifiedWalletsURL_.

**EWTM-WP7**: As a Wallet Provider I want to be able to link from the Wallet Unit's UI view with the EUDI Wallet Trust Mark logo and information text directly to my EUDI Wallet Solution specific link provided to me.

> Note: See _WalletSolutionInfoPageURL_.

**EWTM-WP8**: As a Wallet Provider I want an option to provide the User an UI view equipped with QR code versions of the links of **EWTM-WP5** and **EWTM-WP6**.

### 3.3 European Commission Requirements

**EWTN-EC1**: As the European Commission, I take the responsibility for the EUDI Wallet Trust Mark in terms of graphic design, ownership in the logo registration process, drafting necessary rules and usage guidelines and for distributing this information to the designated actors within the EUDI ecosystem.

**EWTM-EC2**: As the European Commission, I want a specific site path to the list of certified, EUDI Trust Mark-eligible (certified) Wallet Solutions on the eIDAS Dashboard as exists today for the existing Trust Services so that it can be provided to the Wallet Providers after I received Wallet notification from a Member State.

> Note: See _ListofCertifiedWalletsURL_.

**EWTM-EC3**: As the European Commission, I want a direct link to an individual, EUDI Trust Mark-eligible Wallet Solution listed on the eIDAS Dashboard, so that I can provide this link to the Wallet Provider after I received Wallet notification from the Member State.

> Note: See _WalletSolutionInfoPageURL_.

**EWTM-EC4**: As the European Commission, I want to allocate a new certified EUDI Wallet Solution a unique identifier, so that I can use it as part of the link of **EWTM-EC3** and enable online querying for this EUDI Wallet Solution's certification information via the eIDAS Dashboard.

**EWTM-EC5**: As European Commission, I want to deliver the unique identifier of **EWTM-EC4** to the Wallet Provider, so that Wallet Provider can use the identifier as the WalletSolutionID value in the (issuance) Wallet Unit Attestations it issues to individual Wallet Units of the certified Wallet Solution.

> Note: See WalletSolutionID in \[Issuance WUA Specification\].

**EWTM-EC6**: As European Commission, I want the Member States to inform me within 24 hours if a given Wallet Solution has been revoked, so that I can remove it from the official online list of certified EUDI Wallet Solutions.


### 3.4 Member State Requirements

**EWTM-MS1**: As a Member State, I want to have access to EUDI Wallet Trust Mark and wallet certification guidelines released and maintained by the European Commission, so that I can use those for informing my citizens about secure use of EUDI Wallets and where certification information can be looked for.

**EWTM-MS2**: As a Member State, I want to receive the Wallet Solution certification information from the CAB that has assessed and certified the Wallet Solution, so that I can forward this information as part of the notification process to the European Commission.

## 4 Data Format and Solution Architecture

### 4.1 Data format and structure for EUDI Wallet Trust Mark resources

The realisation of the EUDI Wallet Trust Mark as specified in Section 4.2 is dependent on providing the Wallet Solution (or individual Wallet Unit) access to necessary machine-readable information latest upon Wallet Unit activation. The EUDI Wallet Trust Mark itself will have graphical appearance and informatory texts as defined and released by the European Commission. Rendering of these assets on the Wallet Unit is  enabled through providing access to those as URLs, so that the Wallet Solution development team (or if UI view configuration is updated after the app compilation and delivery, each Wallet Unit individually) can receive the information.

A Wallet Unit that needs this information in activation stage (does not have the information provide in the compiled Wallet Solution asset) SHALL be able to download these resources by utilising WalletTrustMarkInformation data (see Table 1) provided to the Wallet Provider. This information SHALL be provided to the Wallet Unit by the Wallet Provider in parallel to its initial WUA issuance.

The data object _WalletTrustMarkInformation_ contents are defined in Table 1. The information SHALL be delivered for the Wallet Provider for Wallet Solution configurability purposes (either pre-distribution or on-demand) as described in Section 4.2.

**Table 1**: WalletTrustMarkInformation data object

| Name of data object          | Description        | Encoding                            |   Status  |
|------------------------------|--------------------|:-----------------------------------:| --------- |
| TrustMarkResourceURL         | URL of the official EUDI Wallet Trust Mark graphics and User Info resources for rendering in the Wallet user interface; contents provided and hosted by the EC. | URL | Mandatory |
| ListOfCerfifiedWalletsURL    |  URL of the public list of certified EUDI Wallet Solutions in EU; provided and hosted by the EC. | URL | Mandatory |
| ListOfCerfifiedWalletsQRCode |  QR Code containing the information of ListOfCertifiedWalletsURL | ISO-8859-1 Byte mode QR code | Optional |
| WalletSolutionInfoPageURL    | URL to the certified Wallet Solution's own information page under the list of certified EUDI Wallet Solutions page. Constructed from the ListOfCertifiedWalletsURL URL appended with a '?'+ the WalletSolutionID Identifier of the Wallet Solution. *Note: This allows, as necessary, a direct search query from the Wallet user interface to open the individual Wallet Solution page from the list behind the top level of certified Wallets list page*. | URL | Mandatory |
| WalletSolutionInfoPageQRCode |  QR Code containing the information of WalletSolutionInfoPageURL | ISO-8859-1 Byte mode QR code | Optional  |
| WalletVerifierToolURL* | URL pointing to the official EUDI Wallet Verification Tool's (an Attestation Provider Service) _/.well-known/openid-credential-issuer_ endpoint used for retrieval of the attestation provider metadata. | URL  | Optional |

#### 4.1.1. TrustMarkResource object

The official EUDI Wallet Trust Mark graphics and user information resources to be rendered on the Wallet Unit are served from the URL _TrustMarkResourceURL_ and SHALL be structured as a JSON data object according to the sample below. Note: Example has only three localisation strings for brevity, a full version SHALL contain all official EU languages.

**Table 2**: TrustMarkResource data object          

    {
      "TrustMarkResource": [
      {
        "type": "image",
        "name": "eudi-wallet-trustmark-logo.png",
        "url": "path/to/eudi-wallet-trustmark-logo.png"
      },
      {
        "type": "text",
        "name": "TrustMarkUserInfo",
        "localizations": {
          "en": "SampleText-for-Users",
          "fr": "TexteExemple-pour-Utilisateurs",
          "de": "Beispieltext-für-Benutzer"
        }
      }
     ]
    }

#### 4.1.2 ListOfCertifiedWalletsURL

_ListOfCertifiedWalletsURL_ is a URL to the public list of certified EUDI Wallet Solutions. URL SHALL be provided for the Wallet Provider to be included in the _WalletTrustMarkInformation_ data object.

#### 4.1.3 WalletSolutionInfoPageURL

the _WalletSolutionInfoPageURL_ SHALL point to the individual Wallet Solution's information page under the _ListofCertifiedWalletsURL_. URL SHALL be constructed from the ListOfCertifiedWalletsURL URL appended with a '?'+ the WalletSolutionID Identifier (see Appendix 1, Table 2 of \[Issuance WUA Specification\] of the certified Wallet Solution and SHALL be provided for the Wallet Provider to be included in the _WalletTrustMarkInformation_ data object.

#### 4.1.4 QR Code versions of page resources

_ListOfCerfifiedWalletsQRCode_ and _WalletSolutionInfoPageQRCode_ MAY be provided to the Wallet Unit by the Wallet Provider when issuing the Wallet Unit Attestation. If present, they SHALL be ISO 8859-1 byte mode QR code encoded representations of the original URLs.

#### 4.1.5 EUDI Wallet Verifier Tool Service* (OPTIONAL)

_WalletVerifierToolURL*_, if present in the WalletTrustMarkInformation object, SHALL point to the URL which provides the attestation provider information of the chosen EUDI Wallet Verifier Tool service (the [Credential Issuer Metadata](https://openid.net/specs/openid-4-verifiable-credential-issuance-1_0.html#credential-issuer-wellknown) of \[OpenID4VCI\]).

> Note 1: Attestation type to be issued by such service is TBA.

> Note 2: A Wallet Provider may choose freely among available 3rd party verification tool services. The European Commission MAY later at its convenience provide such as a public service.

### 4.2 Solution Architecture

The solution architecture describes the active entities, components and responsible parties necessary for the delivery of mandatory functional descriptions of Section 2.1 for the EUDI Wallet Users.

> Note: Provisioning of the verification tool service is optional and thus elements and flows related to it are marked with asterisks (\*) in the architecture diagram and component descriptions.

#### 4.2.1 System architecture

The actors and elements required for the functional flows are presented as a system diagram in Figure 2. Internal components of the actors are considered to be 'black boxes', that is the specification does not define internal behaviour or design of the individual actors' systems.

![Trust-Mark-Component-Architecture](./img/ts1-eudiw-trust-mark-components-fig2.png)

Figure 2. EUDI ecosystem components and data flows required in implementation of functionalities of Section 2.


#### 4.2.2. Actor and data flow descriptions

The functions, inputs and outputs of individual systems in the diagram of Figure 2 are (following the order of events in a 'happy flow' situation):

**Wallet Provider** - entity developing and distributing EUDI **Wallet Solutions**, instances of which are the **Wallet Units** the **Users** have installed to their devices. Wallet Provider requests certification of their Wallet Solution before it can provide it to the Users (1).

**Conformity Assessment Body** (CAB) assesses the Wallet Solution to be certified (2). If certification is passed, the CAB informs the applicable Member State, and provides as output the certification information produced in the assessment (3).

**Member State** receives information from the CAB, and notifies the European Commission, forwarding the certification information to the Commission (4).

**The European Commission**'s responsible unit for the Trust Mark information and listing of certified EUDI Wallets manages that
- (5) The EUDI Wallet Trust Mark materials are available online as required behind a web resource (TrustMarkResourceURL)
- (6) the certified Wallet Solution is given a WalletSolutionID, information of the Wallet Solution is added to the official list of certified wallets
- (7) a Wallet Solution specific information page is created and published online
- (8) OPTIONALLY, the entity (or any 3rd party whatsover) develops, registers and operates the EUDI Wallet Verifier Tool as a wallet-relying party service per description of Section 2.2.
- (9) The Wallet Provider is sent information required for configuring the certified Wallet Solution and issuing the Wallet Unit Attestation: the assigned _WalletSolutionID_, the _TrustMarkResourceURL_, the _ListOfCertifiedWalletsURL_, the _WalletSolutionInfoPageURL_, and (OPTIONALLY) the _WalletVerifierToolURL_.

After receiving the information, the Wallet Provider updates the Wallet Solution asset where needed (10) in order to (11) be able to render the Wallet Solution specific **EUDI Wallet UI view with expected graphics and other information of the Trust Mark** (material and user experience guidelines for which the European Commission is responsible according to requirement **EWTM-EC1**).

The WUA issuance (12) by the Wallet Provider happens at Wallet Unit activation as defined in the ARF and related technical specification (and happens irrespective of the requirements of this specification). It provides the basis for the optional verification tool services.

**The User** can at their discretion view (13) the official EUDI Trust Mark information from the UI view of the EUDI Wallet, and (14) access the EUDI Wallet listing and individual Wallet Solution pages (and OPTIONAL Verifier Tool service, if such are set available to verify the Wallet Solution's certification status against presenting the WUA for verification by the service).

> Note: The guidelines for situations if the Wallet Solution of the User proves to be non-certified for whatever reason (obvious fake, revoked at solution or at instance level) are equally important to showing a positive outcome with graphics and texts of the EUDI Wallet Trust Mark. These 'unhappy flow' scenarios and remedies should be covered in public EUDI Wallet communication materials, they are not subject of this technical specification.


## 5 References

| Reference      | Description |
|----------------------------------------|----------------------------------------------|
| [WCAG 2.1 ]                            | [Web Content Accessibility Guide\sion 2.1](https://www.w3.org/TR/WCAG21/) |
| [Issuance WUA Specification]           | [Specification of Wallet Unit Attestations (WUA) used in issuance of PID and Attestations](https://github.com/eu-digital-identity-wallet/eudi-doc-standards-and-technical-specifications/blob/main/docs/technical-specifications/ts3-wallet-unit-attestation.md)                                     |
|  [OpenID4VCI]                          | [OpenID For Verifiable Credential Issuance v1.0](https://github.com/eu-digital-identity-wallet/eudi-doc-standards-and-technical-specifications/issues/3)  |


<img align="right" height="50" src="https://raw.githubusercontent.com/eu-digital-identity-wallet/eudi-srv-web-issuing-eudiw-py/34015dc3c6f52529a99e673df1d4fa69d50f7ff5/app/static/ic-logo.svg"/><br/>

# Specification of systems enabling the notification and subsequent publication of Provider information

## Abstract

The present document specifies the data model and systems enabling the notification and subsequent publication of Provider information.

### [GitHub discussion](https://github.com/eu-digital-identity-wallet/eudi-doc-architecture-and-reference-framework/discussions/427)

## Versioning

| Version | Date       | Description                                                                                                                                                                                                                                                           |
|---------|------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `0.1`   | 16.01.2025 | Initial version for first discussions.                                                                                                                                                                                                                                |
| `0.2`   | 10.02.2025 | Version with first feedback integrated.                                                                                                                                                                                                                               |
| `0.3`   | 09.03.2025 | Version with more comments integrated.                                                                                                                                                                                                                                |
| `0.4`   | 09.04.2025 | Version with more comments integrated and separation of ``LegalEntity`` and ``Provider``. ``IntendedUse`` has been introduced and specification text has been closely aligned with class diagram.                                                                     |
| `0.9`  | 25.04.2025  | Version with slightly updated data model and specification of notification system. |


## 1. Introduction and Overview

The present document specifies selected technical and procedural aspects related to the **notification and
subsequent publication of Provider information** according to (EU) No 910/2014 and the Commission Implementation Regulation
(CIR) [(EU) 2024/2980](https://eur-lex.europa.eu/eli/reg_impl/2024/2980/oj) of 28 November 2024 laying down rules for the application of Regulation
(EU) No 910/2014 of the European Parliament and of the Council as regards **notifications to the Commission
concerning the European Digital Identity Wallet (EUDIW) ecosystem**.

This document also covers the notification of "Public Body Authentic Source
Electronic Attestation of Attributes (PuB-EAA) Providers" according to Article 45f Nr. 3 of (EU) No 910/2014 together with the
envisioned notification procedure according to the [Draft of the CIR for PuB-EAA](https://tinyurl.com/IA-45def-draft).

To this extent the present document addresses the following types of Providers and notifications:

1. **Registrars and Registers of Wallet-Relying Parties** (see Article 5a Nr. 18 (a) of (EU) No 910/2014 and
 Annex II 1. of CIR (EU) 2024/2980,
2. **Wallet Providers** and mechanism to validate authenticity and validity of Wallet Units (see Article 5a Nr. 18 (b)
 of No 910/2014 and Annex II 2. of CIR (EU) 2024/2980),
3. **Providers of Person Identification Data (PID)** and mechanisms enabling the authentication and validation of PID
 (see Article 5a Nr. 18 (c) of (EU) No 910/2014 and Annex II 3. of CIR (EU) 2024/2980),
4. **Providers of Wallet-Relying Party Access Certificates** (see Annex II 4. of CIR (EU) 2024/2980)
5. **Public Body Authentic Source Electronic Attestation of Attributes (PuB-EAA) Providers** (see Article 45f Nr. 3 of
 (EU) No 910/2014) and Annex III of [Draft of the CIR for PuB-EAA](https://tinyurl.com/IA-45def-draft)),

The following notification procedures are out of scope of the present document, as they are well
established already:

* Notification of **eID Schemes** according to Article 9 of (EU) No 910/2014
* Notification of **Conformity Assessment Bodies** according to Article 20 (b) 1b of the amended Regulation (EU) No 910/2014
* Notification of **Supervisory Bodies for the European Digital Identity Wallet Framework** according to Article 46a of (EU) No 910/2014
* Notification of **Supervisory Bodies for Trust Services according** to Article 46b of (EU) No 910/2014
* Notification of **Single Points of Contact** according to Article 46c of (EU) No 910/2014
* Notification of **Qualified Trust Service Providers** according to Article 21 of (EU) No 910/2014 to the national Supervisory
 Body and the related management of **Trusted lists** according to Article 22 of (EU) No 910/2014.

## 2. Data Model

The present data model has been created based on the existing implementing act CIR [(EU) 2024/2980](https://eur-lex.europa.eu/eli/reg_impl/2024/2980/oj) and
and the published drafts of the forthcoming implementing acts [Draft of the CIR for PuB-EAA](https://tinyurl.com/IA-45def-draft) and [Draft of the CIR for RP-Registration](https://tinyurl.com/IA-5b-draft),
while keeping the [SEMIC Style Guide](https://semiceu.github.io/style-guide/1.0.0/index.html) in mind and aligning it with the [Core Business Vocabulary](https://semiceu.github.io/Core-Business-Vocabulary/releases/2.2.0/) as much
as reasonable.

![ProviderDataModel](img/ts2-eudi-providers.svg)

As outlined in the above figure, it contains the following **main classes**:

* **LegalEntity**
* **Provider**
* **WRPRegistrar**
* **WalletProvider**
* **PIDProvider**
* **PubEEAProvider**
* **TrustServiceProvider** with its subclass **WRPAccCertProvider**
* **WalletRelyingParty**

These classes are defined using the following **auxiliary classes**

* **Document**
* **Identifier**
* **Law**
* **LegalPerson**
* **NaturalPerson**
* **Policy**
* **TrustService**
* **WalletSolution**

### 2.1 LegalEntity

The ``LegalEntity`` class provides the basis for the derivation of the ``Provider`` class, which the central class of the present data model.
Its design takes into account that all the involved legal entities may either be legal persons or natural persons and this class assembles the
generic attributes related to a legal entity, which are relevant here. It contains the attributes specified in the following table:


| Attribute          | Multiplicity | Type                                   | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                    |
|--------------------|--------------|----------------------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `legalPerson`      | [0..1]       | [*LegalPerson*](#294-legalperson)      | specifies the specific attributes of a **legal person**. This attribute is present, if and only if the legal entity is a private or public legal person.                                                                                                                                                                                                                                                                                                       |
| `naturalPerson`    | [0..1]       | [*NaturalPerson*](#295-naturalperson) | specifies the specific attributes of a **natural person**. This attribute is present, if and only if the legal entity is a natural person.                                                                                                                                                                                                                                                                                                                     |
| `identifier`     | [0..*]       | [*Identifier*](#292-identifier)        | may be present in order to specify one or more **identifiers** of the legal entity, as stated in an official record together with the identification data of that official record, if applicable.                                                                                                                                                                                                                                                              |
| `postalAddress` | [0..*]       | *string*                               | may be present in order to specify the **postal address** of the legal entity in line with clause 6.6.1 of recommendation [ITU-T X.520](https://www.itu.int/rec/T-REC-X.520/en).                                                                                                                                                                                                                                                                               |
| `country`        | [1..1]       | *string*                               | specifies the alpha-2 **country code** according to ISO 3166-1 of the country in which the legal entity is established, or the string "EU" for providers operating on a European level.                                                                                                                                                                                                                                                                |
| `email`          | [0..*]       | *string*                               | may be present in order to specify one or more **email addresses** according to [RFC5322](https://www.rfc-editor.org/rfc/rfc5322.html) of the legal entity.                                                                                                                                                                                                                                                                                                                 
| `phone`          | [0..*]       | *string*                               | may be present in order to specify one or more **phone numbers** of the legal entity starting with the ‘+’ symbol as the international code prefix and the country code, followed by numbers only as specified in [RFC2806](https://www.rfc-editor.org/rfc/rfc2806.html).                                                                                                                                                                                                  
| `infoURI`        | [0..*]       | *string*                               | may be present in order to specify one or more Unique Resource Identifiers (URIs) according to [RFC3986](https://www.rfc-editor.org/rfc/rfc3986.html) with **webpages for information** about the legal entity.                                                                                                                                                                                                                                                                                                                                                                

### 2.2 Provider

The ``Provider`` class inherits all attributes from the more general ``LegalEntity`` class specified above and is the central class of the
data model from which the other classes for the individual provider classes derive. It contains the attributes specified in the following table:

| Attribute           | Multiplicity | Type                    | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
|---------------------|--------------|-------------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `providerType` | [1..1]      | *string*                | specifies the **type** of the provider according to its sub-class, as it is necessary for the specification of the API in [clause 3.2](#3-2-components-and-interfaces), whereas the following values are defined in the present document: <ul><li>`WRPRegistrar`</li><li>`WalletProvider`</li><li>`PIDProvider`</li><li>`PubEEAProvider`</li>`WRPAccCertProvider`</li><li>`WalletRelyingParty`</li></ul>                                                                                                                                                                                     |
| `policy`          | [1..*]       | [*Policy*](#295-policy) | specifies the type and URL of a webpage where the relevant **service policy** (e.g. registration policy or trust service policy) or **privacy policy** or **terms and conditions statement** of the provider are located, where applicable.                                                                                                                                                                                                                                                                                                                                                  |
| `x5c`             | [0..*]       | *string*                | specifies a sequence of **X.509 certificate chains** according to [RFC 7515](https://www.rfc-editor.org/rfc/rfc7515.html), where each certificate chain is compliant to [RFC 3647](https://www.rfc-editor.org/rfc/rfc3647.html) and [RFC 5280](https://www.rfc-editor.org/rfc/rfc5280.html), if used by the provider for all its services. Specifying more than one certificate chain here allows to support key rollover procedures. In case of a ``TrustServiceProvider`` this element is not present, as the relevant certificate chains are assigned to the individual ``TrustService``. |

### 2.3 WRPRegistrar

According to Article 5a Nr. 18 (a) of (EU) No 910/2014, the Member States are required to notify the European Commission
about the **Registrars for Wallet-Relying Parties**, which are responsible for establishing and maintaining the lists of
relying parties (**Registries of Wallet-Relying Parties**), that rely on European Digital Identity Wallets in
accordance with Article 5b(5) of (EU) No 910/2014 and the location of that lists.

According to Annex II 1. of CIR (EU) 2024/2980, the EU Member States shall provide for each register and registrar the following information to
the European Commission:

* (a) the name of the register;
* (b) at least one URL where the register is available for access, which shall use state of the art transport layer encryption;
* (c) the name of the registrar that is responsible for that register;
* (d) where applicable, the registration number of the registrar;
* (e) the Member State in which the registrar is established;
* (f) the contact email and contact phone number of the registrar, for matters related to the register;
* (g) where applicable, the URL of a webpage for additional information about the registrar and the register;
* (h) the URL of the webpage where the registration policy that applies to the register and related information are located;
* (i) one or more certificates compliant with IETF RFC 3647 which can be used to verify the signature or seal created by the registrar on the register data and for which the certified identity data include the name of the registrar, and where applicable, the registration number of the registrar, as provided in points (c) and (d), respectively.

The ``WRPRegistrar`` class is used for this kind of notification and inherits all attributes from the ``Provider``
class. In addition to the attributes of the ``Provider`` class it contains the attributes specified in the following table:

| Attribute | Multiplicity | Type | Description |
|---------------|--------------|----------|-------------|
| `register` | [1..1] | *string* | specifies the **name of the register**. |
| `registerURI` | [1..*] | *string* | specifies the **URL where the register is available for access**. |

### 2.4 WalletProvider

According to Article 5a Nr. 18 (b) of (EU) No 910/2014, the Member States are required to notify to the European Commission
about the **Wallet Providers**, which are the bodies responsible for the provision of European Digital Identity Wallets in accordance with Article 5a(1).
In line with Article 5a Nr. 18 (e) the notified information shall also include information about the mechanism for the validation of the authenticity
and validity of European Digital Identity Wallets.

According to Annex II 2. of CIR (EU) 2024/2980, the EU Member States shall provide for each wallet provider the following information to
the European Commission:

* (a) the name of the wallet provider;
* (b) where applicable, the registration number of the wallet provider;
* (c) where applicable, the name of the body responsible for the provision of the wallet solution;
* (d) the Member State in which the wallet provider is established;
* (e) the contact email and contact phone number of the wallet provider, for matters related to the wallet solutions
 it provides;
* (f) where applicable, the URL of the webpage for additional information about the wallet provider and the wallet solution;
* (g) the URL of the webpage where the policies, terms and conditions of the wallet provider that apply to the provision
 and use of the wallet solution it provides are located;
* (h) one or more certificates compliant with IETF RFC 3647 that can be used to authenticate and validate the
 components of the wallet unit the wallet provides, and for which the certified identity data includes the name,
 and where applicable, the registration number of the wallet provider, as specified in points (a) and (b), respectively;
* (i) for each wallet solution provided by the wallet provider, the name and the reference number of the wallet solution
 it provides, as the Commission shall publish this information in the Official Journal of the European Union pursuant
 to Article 5d of Regulation (EU) No 910/2014.

The ``WalletProvider`` class is used for this kind of notification and inherits all attributes from the ``Provider``
class. In addition to the attributes of the ``Provider`` class it contains the attributes specified in the following table:

| Attribute       | Multiplicity | Type                                      | Description                                                            |
|-----------------|--------------|-------------------------------------------|------------------------------------------------------------------------|
| `walletSol` | [1..*]      | [*WalletSolution*](#297-walletsolution) | specifies details with respect to the **wallet solution**. |

### 2.5 PIDProvider

According to Article 5a Nr. 18 (c), the Member States are required to notify to the European Commission the
**Provider of Person Identification Data (PID)**, which are responsible for ensuring that the PID is associated with
the European Digital Identity Wallet in accordance with Article 5a(5), point (f). In line with Article 5a Nr. 18 (d) the
notified information shall contain information, which allows to validate the PID.

According to Annex II 3. of CIR (EU) 2024/2980, the EU Member States shall provide for each PID-Provider the
following information to the European Commission:

* (a) the name of the provider of person identification data;
* (b) where applicable, a registration number of the provider of person identification data;
* (c) where applicable, the name of the body responsible for ensuring that the person identification data is associated with the wallet unit;
* (d) the Member State in which the provider of person identification data is established;
* (e) the contact email and contact phone number of the provider of person identification data, for matters related to the person identification data it provides;
* (f) where applicable, the URL of the webpage that contains additional information about the person identification data provider;
* (g) the URL of the webpage that contains the policies, terms and conditions of the provider of person identification data that apply to the provision and use of the person identification data it provides;
* (h) one or more certificates compliant with IETF RFC 3647 that can be used to verify the signature or seal created by the provider of person identification data on the person identification data it provides, and for which the certified identity data include the name, and where applicable, the registration number of the person identification data provider, as specified in points (a) and (b), respectively.

The ``PIDProvider`` class is used for this kind of notification and inherits all attributes from the ``Provider``
class. In addition to the attributes of the ``Provider`` class it contains the attributes specified in the following table:

| Attribute | Multiplicity | Type | Description |
|--------------|--------------|----------|----|
| `PIDIssuer` | [0..1] | *string* | specifies the **name of the body responsible** for ensuring that the person identification data is associated with the wallet unit. |

### 2.6 PubEEAProvider

> **NOTE 1 (CIR for PuB-EEA-Provider-handling is still draft):**
> This section should be treated with some caution, as the implementing act according to the Articles 45d, 45e and 45f of
> (EU) No. 910/2014 is currently only available as [Draft of the CIR for PuB-EAA](https://tinyurl.com/IA-45def-draft)
> and may therefore change until final publication and endorsement.

According to Article 45f (3) of (EU) No 910/2014) the Member States shall notify **Public Sector Body Authentic Source Electronic Attestation of Attributes (PuB-EAA) Providers**
according to Article 3 (46) of (EU) No 910/2014) to the Commission. That notification shall include a conformity assessment report issued by a
conformity assessment body confirming that the requirements set out in Article 45f (1), (2) and (6) of (EU) No 910/2014) are met. The Commission shall
make available to the public, through a secure channel, the list of public sector bodies referred to in Article 3 (46) (EU) No 910/2014) in
electronically signed or sealed form suitable for automated processing. Further details are outlined in Annex III of [Draft of the CIR for PuB-EAA](https://tinyurl.com/IA-45def-draft)).

The ``PubEEAProvider`` class is used for this kind of notification and inherits all attributes from the ``Provider``
class, which in turn inherits all attributes from the ``LegalEntity`` class. Note, that a ``PubEEAProvider`` is always a public sector legal
entity, which is established by some public law and hence the element ``establishedByLaw`` in ``LegalPerson`` shall always be present.  
In addition to the attributes of the ``Provider`` class the ``PubEEAProvider`` class contains the attributes specified in the following table:

| Attribute | Multiplicity | Type                        | Description |
|-------------|--------------|-----------------------------|-----------------|
| `EEAIssuer` | [0..1] | [*Provider*](#22-provider)  | specifies the details of the *EEA issuer**, if it is not identical to the public sector body, which is responsible for the authentic source indicated in the ``Provider`` class. |
| `car` | [1..*] | [*Document*](#291-document) | contains the **conformity assessment report** mentioned in Article 45f (3) of (EU) No 910/2014 consisting of one or more ``Document`` elements. |

### 2.7 WRPAccCertProvider

The ``WRPAccCertProvider`` class is used for the notification of issuers of access certificates
for wallet-relying parties as required by Annex II 4. of CIR [(EU) 2024/2980](https://eur-lex.europa.eu/eli/reg_impl/2024/2980/oj).

It simply inherits the attributes from the ``TrustServiceProvider`` class, which in turn inherits
the attributes from the ``Provider`` class and ``LegalEntity`` class and adds one or more `trustSrv` attributes,
as specified in the following table:

| Attribute | Multiplicity | Type                                 | Description |
|-----------------------|--------------|--------------------------------------|---|
| `trustSrv` | [1..*] | [*TrustService*](#296-trustservice) | specifies the **details of the trust service**. |

According to Article 5a Nr. 18 (d) of (EU) No 910/2014 the EU Member States shall notify the European Commission about
the mechanism for the validation of the identity of the Wallet-Relying Parties. As stipulated by the implementing acts
according to Article 5a (23) (EU) 2024/1183, i.e. within [(EU) 2024/2977](http://data.europa.eu/eli/reg_impl/2024/2977/oj), [(EU) 2024/2979](http://data.europa.eu/eli/reg_impl/2024/2979/oj), [(EU) 2024/2980](http://data.europa.eu/eli/reg_impl/2024/2980/oj)
and [(EU) 2024/2982](http://data.europa.eu/eli/reg_impl/2024/2982/oj), the validation of the identity of the Wallet-Relying Parties is envisioned to take place using
so called "Wallet-Relying Party Access Certificates", which are defined to be certificates for electronic seals or signatures
authenticating and validating the wallet-relying party issued by specific providers, which are mandated by the EU Member
State.

According to Annex II 4. of CIR (EU) 2024/2980, the EU Member States shall notify the following information
for each Provider of Wallet-Relying Party Access Certificates to the European Commission:

* (a) the name of the provider of wallet-relying party access certificates;
* (b) where applicable, a registration number of the provider of wallet-relying party access certificates;
* (c) the Member State in which the provider of wallet-relying party access certificates is established;
* (d) the contact email and contact phone number of the provider of wallet-relying party access certificates,
 for matters related to the access certificates it provides to wallet-relying parties;
* (e) where applicable, the URL of the webpage of the provider of wallet-relying party access certificates that
 contains additional information about the provider and the access certificates it provides to wallet-relying parties;
* (f) the URL of the webpage that contains the policies, terms and conditions that apply to the provision and use of
 the access certificates it provides to wallet-relying parties;
* (g) one or more certificates compliant with IETF RFC 3647 that can be used to verify the signature or seal created
 by the provider of wallet-relying party access certificates on the access certificate it provides to wallet-relying
 parties, with, where applicable, the information required to distinguish wallet-relying party access certificates
 from other certificates.

### 2.8 WalletRelyingParty

As stipulated in Article 5b (1) of (EU) No. 910/2014, the **Wallet-Relying Parties** shall register in the
Member State where they are established.

Article 5b (2) of (EU) No. 910/2014 makes clear, that the "registration process shall be cost-effective
and proportionate-to-risk". According to Article 5b (5) of (EU) No. 910/2014 the "Member States
shall make the information referred to in paragraph 2 publicly available online in electronically signed
or sealed form suitable for automated processing" and Article 5b (7) of (EU) No. 910/2014 stipulates that
the "Member States shall provide a common mechanism for allowing the identification and
authentication of relying parties, as referred to in Article 5a (5), point (c)" of (EU) No. 910/2014.

As clarified by the already endorsed implementing acts according to Article 5a (23) (EU) 2024/1183, i.e.
within [(EU) 2024/2977](http://data.europa.eu/eli/reg_impl/2024/2977/oj), [(EU) 2024/2979](http://data.europa.eu/eli/reg_impl/2024/2979/oj), [(EU) 2024/2980](http://data.europa.eu/eli/reg_impl/2024/2980/oj) and [(EU) 2024/2982](http://data.europa.eu/eli/reg_impl/2024/2982/oj), the
"common mechanism allowing the identification and authentication of relying parties" is to use
X.509-based "Wallet-Relying Party Access Certificates" issued by a suitable Certification Authority
(cf. [``WRPAccCertProvider``](#27-wrpacccertprovider)).

>**NOTE 2: (Member States are invited to cooperate with respect to registration)**
> While Article 5b of (EU) No. 910/2014 has assigned the responsibility for the registration
> to the Member States, the stipulations in the paragraphs (2) ("cost-effective"), (5) ("suitable for
> automated processing") and (7) ("common mechanism") seem to suggest, that normalised data structures,
> a joint solution development and a close collaboration among the Member States and further EUDI
> stakeholders may be appropriate here. Therefore, the present document also outlines the data structure
> of the ``WalletRelyingParty`` class, even if there is no notification procedure, which directly involves
> Wallet-Relying Parties.

> **NOTE 3 (CIR for Registration of Wallet-Relying Parties is not yet formally published):**
> This section should be treated with caution, as the implementing act according to the Article 5b of
> (EU) No. 910/2014 is currently only available as [Draft of the CIR for RP-Registration](https://tinyurl.com/IA-5b-draft),
> and may therefore change until final publication and endorsement. The text below is based on the publicly
> available draft of the implementing act and already includes the concept of "intended use of attributes",
> which in turn corresponds to the concept of "purpose" according to Art. 5 1. (b) of [(EU) 2016/679](http://data.europa.eu/eli/reg/2016/679/oj).  
> The text below will be replaced with the published text as soon as it is available.

> **NOTE 4 (Data Model for Wallet-Relying Party will later be shifted to other document):**
> The part of the data model which addresses Wallet-Relying Parties is planned to be dropped as soon
> as it is available in [TS5](https://github.com/eu-digital-identity-wallet/eudi-doc-standards-and-technical-specifications/tree/main/docs/technical-specifications).

According to Article 3 and Annex I of [Draft of the CIR for RP-Registration](https://tinyurl.com/IA-5b-draft)
the registration of Wallet-Relying Parties captures the following information:

1. The name of the wallet-relying party as stated in an official record together with identification data of that official record.
2. Where applicable, one or more identifiers of the wallet-relying party, as stated in an official record together with identification
 data of that official record, expressed as:

 (a) an Economic Operators Registration and Identification (EORI) number as referred to in Commission Implementing Regulation (EU) No 1352/20131;

 (b) the registration number as registered in a national business register;

 (c) a Legal Entity Identifier (LEI) as referred to in Commission Implementing Regulation (EU) No 2022/18602;

 (d) a VAT registration number;

 (e) an excise number as specified in Article 2(12) of Council Regulation (EC) No 389/20123;

 (f) a tax reference number;

 (g) a European Unique Identifier (EUID) as referred to in Commission Implementing Regulation (EU) 2020/22444.

3. The physical address where the wallet-relying party is registered.

4. For the indication of the Member State in which the registering wallet-relying party is established, the ISO 3166-1 Alpha 2
 codes shall be used, with the following exception: the Country Code for Greece shall be ‘EL’.

5. Detailed contact information of the wallet-relying party, one or more, including:

 (a) a website for providing help desk and support;

 (b) a phone number where the wallet-relying party can be contacted for matters pertaining to its registration and intended use of the wallet units;

 (c) a digital address where the wallet-relying party can be contacted for matters pertaining to its registration and intended use of the wallet units;

 (d) an e-mail address where the wallet-relying party can be contacted for matters pertaining to its registration and intended use of the wallet units;

6. A description of the type of services provided.

7. A list of the attributes that the relying party intends to request, expressed as a friendly name and a technical name including the namespace that the attributes
 are grouped under in a machine-readable format for automated processing, with an indication if they are mandatory or optional.

8. A description of the intended use of the attributes to be requested by the wallet-relying party from wallet units, including an indication
 if the intended use of the attribute are for purposes to fulfil specific rules of the Union or National law requiring the relying party to identify users.

9. An indication whether the wallet-relying party is a public sector body.

10. Where applicable, every entitlement of the wallet-relying party, that shall be expressed as follows:

 (a) ‘Service_Provider’ to express the entitlement of the wallet-relying party as a provider of services;

 (b) ‘QEAA_Provider’ to express the entitlement of the wallet-relying party as a qualified trust service provider issuing qualified
 electronic attestations of attributes;

 (c) ‘Non_Q_EAA_Provider’ to express the entitlement of the wallet-relying party as a Trust service provider issuing non-qualified electronic attestations of attributes;

 (d) ‘PUB_EAA_Provider’ to express the entitlement of the wallet-relying party as a provider of electronic attestations of attributes issued by or on behalf of a
 public sector body responsible for an authentic source;

 (e) ‘PID_Provider’ to express the entitlement of the wallet-relying party as a provider of person identification data;

 (f) ‘QCert_for_ESeal_Provider’ to express the entitlement of the wallet-relying party as a qualified trust service provider
 issuing qualified certificates for electronic seals;

 (g) ‘QCert_for_ESig_Provider’ to express the entitlement of the wallet-relying party as a qualified trust service provider
 issuing qualified certificates for electronic signatures;

 (h) ‘rQSealCDs_Provider’ to express the entitlement of the wallet-relying party as a qualified trust service provider providing a
 qualified trust service for the management of a remote qualified electronic signature creation device;

 (i) ‘rQSigCDs_Provider’ to express the entitlement of the wallet-relying party as a qualified trust service provider providing a qualified trust
 service for the management of a remote qualified electronic seal creation device;

 (j) ‘ESig_ESeal_Creation_Provider’ to express the entitlement of the wallet-relying party as a (non-qualified) trust service provider of remote
 creation of electronic signatures or electronic seals as a non-qualified trust service;

The ``WalletRelyingParty`` class is used for this kind of notification and inherits all attributes from the ``Provider``
class. In addition to the attributes of the ``Provider`` class it contains the attributes specified in the following table:

| Attribute                              | Multiplicity | Type                              | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
|----------------------------------------|--------------|-----------------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `tradeName`                            | [0..1]       | *string*                          | may be present in order to specify the **trade name** of the Wallet-Relying Party, if applicable.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                     |
| `supportURI`                           | [0..1]       | *string*                          | specifies the **support URI** for the service provided by the Wallet-Relying Party, if applicable. Note, that Annex I of [Draft of the CIR for RP-Registration](https://tinyurl.com/IA-5b-draft) stipulates that the Wallet-relying Party shall provide detailed contact information in form of (a) a website for helpdesk and support, (b) a phone number or (c) an e-mail address pertaining to its registration and intended use of the wallet units.                                                                                                                                                                                                                                                                                                                                                                                                                                                                              |
| `srvDescription`                       | [1..1]       | *string*                          | contains a **description of the service** provided by the Wallet-Relying Party.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| `intendedUse`                          | [1..*]       | *IntendedUse* | may appear one or more times in order to specify intended use cases in which the Wallet-Relying Party intends to rely on attributes of a wallet user presented by a wallet unit.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |
| `isPSB`                                | [1..1]       | *boolean*                         | indicates, whether the Wallet-Relying Party **is a public sector body** or not.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                       |
| `entitlement`                          | [1..*]       | *string*                          | specifies the **set of entitlements** of the Wallet-Relying Party in form of a URI according to [RFC3986](https://www.rfc-editor.org/rfc/rfc3986.html), whereas the following URIs are defined in the present document: <ul><li> http://data.europa.eu/eudi/entitlement/Service_Provider</li> <li> http://data.europa.eu/eudi/entitlement/QEAA_Provider</li><li> http://data.europa.eu/eudi/entitlement/Non_Q_EAA_Provider</li><li> http://data.europa.eu/eudi/entitlement/PUB_EAA_Provider</li><li> http://data.europa.eu/eudi/entitlement/PID_Provider</li><li> http://data.europa.eu/eudi/entitlement/QCert_for_ESeal_Provider</li><li> http://data.europa.eu/eudi/entitlement/QCert_for_ESig_Provider</li><li> http://data.europa.eu/eudi/entitlement/rQSealCDs_Provider</li><li> http://data.europa.eu/eudi/entitlement/rQSigCDs_Provider</li><li> http://data.europa.eu/eudi/entitlement/ESig_ESeal_Creation_Provider</li></ul> |
| `providesAttestations`                 | [0..*]       | *string*                          | specifies the link to the [credential issuer metadata](https://openid.net/specs/openid-4-verifiable-credential-issuance-1_0.html#section-11.2.2) of the attestation provider.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                         |
| `usesIntermediary` | [0..1]      | [*Provider*](#22-provider)                 | indicates whether there is an intermediary according to [Article 5b (10) of (EU) No. 910/2014](https://www.eid.as/#article5b) and refers to it.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |
| `supervisoryAuthority`                 | [1..1]       | [*LegalEntity*](#21-legalentity)  | specifies the competent **data protection supervisory authority** according to Article 51 of [(EU) 2016/679](http://data.europa.eu/eli/reg/2016/679/oj), which is in charge of supervising the Wallet-Relying Party.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                  |

### 2.9 Auxiliary Classes

#### 2.9.1 Document

The ``Document`` class is used within the definition of the [``WalletRelyingParty``](#25-pubeeaprovider) class. It contains the attributes specified in the following table:

| Attribute | Multiplicity | Type | Description |
|-----------|--------------|----------|--------------|
| `type` | [1..1] | *string* | is the **MIME type** of the document according to IETF RFC 2046. |
| `content` | [1..1] | *string* | is the **content of the document** encoded as specified by its MIME type. |

#### 2.9.2 Identifier

The ``Identifier`` class is used within the definition of the [``LegalEntity``](#21-legalentity) class.
It contains the attributes specified in the following table:

| Attribute | Multiplicity | Type | Description                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                           |
|--------------|--------------|----------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `type` | [1..1] | *string* | is the **type** of the identifier specified by a URI according to [RFC3986](https://www.rfc-editor.org/rfc/rfc3986.html), whereas the following URIs are defined in the present document: <ul><li>http://data.europa.eu/eudi/id/EORI-No - Economic Operator Registration and Identification Number (**EORI-No**) according to [(EU) No 1352/2013](http://data.europa.eu/eli/reg_impl/2013/1352/oj)</li> <li>http://data.europa.eu/eudi/id/LEI - Legal Entity Identifier (**LEI**) according to [(EU) No 2022/1860](http://data.europa.eu/eli/reg_impl/2022/1860/oj) and ISO 17442</li><li>http://data.europa.eu/eudi/id/EUID - European Unique Identifier (**EUID**) according to [(EU) 2020/2244](http://data.europa.eu/eli/reg_impl/2020/2244/oj) and [(EU) 2021/1042](http://data.europa.eu/eli/reg_impl/2021/1042/oj)</li> <li>http://data.europa.eu/eudi/id/VATIN - Value Added Tax Identification Number (**VATIN**) according to the [Council Directive 2006/112/EC](http://data.europa.eu/eli/dir/2006/112/oj)</li> <li>http://data.europa.eu/eudi/id/TIN - [Taxpayer Identification Number (**TIN**)](https://taxation-customs.ec.europa.eu/online-services/online-services-and-databases-taxation/taxpayer-identification-number-tin_en)</li> <li><http://data.europa.eu/eudi/id/Excise> - **Excise Number** according to Art. 2 (12) of the Council Regulation [(EC) No. 389/2012](http://data.europa.eu/eli/reg/2012/389/oj) </li> </ul>. |
| `identifier` | [1..1] | *string* | is the **identifier**, which identifies the ``LegalEntity`` under consideration.                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                                      |

> **NOTE 5 (National business registration number is part of EUID):**
> Annex I Nr. 2 of [Draft of the CIR for RP-Registration](https://tinyurl.com/IA-5b-draft) also lists
> the identifier option "registration number as registered in a national business register". However, this option seems
> to be superfluous, as this is already covered by the EUID case, as this identifier is constructed to
> contain the mentioned national business registration number.

#### 2.9.3 Law

The ``Law`` class is used within the definition of the [``LegalPerson``](#294-legalperson)
class. It contains the attributes specified in the following table:

| Attribute | Multiplicity | Type | Description                                                                                                                                                                                                  |
|---------------|--------------|----------|--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `lang` | [1..1] | *string* | is the two-letter Alpha-2 **language code** according to ISO 639 (Set 1).                                                                                                                                    |
| `legalBasis` | [1..1] | *string* | specifies the **legal basis** according to which a [``LegalPerson``](#296-legalperson) is established as such or the access to a specific [``Claim``](#291-claim) is required or recommended. |

#### 2.9.4 LegalPerson

The ``LegalPerson`` class is used within the definition of the [``LegalEntity``](#21-legalentity)
class and allows to specify the attributes of a legal person. It contains the attributes specified in the following table:

| Attribute          | Multiplicity | Type               | Description                                                                                                                                                                                                                                                     |
|--------------------|--------------|--------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `legalName`        | [1..*]       | *string*           | specifies the **legal name** of the legal person, as specified in an official record.                                                                                                                                                                           |
| `establishedBylaw` | [0..*]      | [*Law*](#293-law) | specifies the **legal basis** on which the legal person is established. This information should in particular be present in case of a public sector body and it shall be present in case of a public sector body, which is responsible for an authentic source. |

#### 2.9.4 NaturalPerson

The ``NaturalPerson`` class is used within the definition of the [``LegalEntity``](#21-legalentity)
class and allows to specify the attributes of a natural person. It contains the attributes specified in the following table:

| Attribute          | Multiplicity | Type                | Description                                                                                                                                                                                                                                                                       |
|--------------------|--------------|---------------------|-----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `givenName`        | [1..1]       | *string*            | specifies the current **first name(s)** of the natural person including middle name(s) where applicable, as specified in official records and the set of person identification data according to the Annex of [(EU) 2024/2977]( http://data.europa.eu/eli/reg_impl/2024/2977/oj). |
| `familyName`       | [1..1]       | *string*            | specifies the current **last name(s)** or surnames of the natural person, as specified in official records and the set of person identification data according to the Annex of [(EU) 2024/2977]( http://data.europa.eu/eli/reg_impl/2024/2977/oj).                                |
| `dateOfBirth`      | [0..1]      | *string*            | specifies the **data of birth** of the natural person, as specified in official records and the set of person identification data according to the Annex of [(EU) 2024/2977]( http://data.europa.eu/eli/reg_impl/2024/2977/oj), if present.                                       |
| `placeOfBirth` | [0..1]      | *string*            | specifies the **place of birth** of the natural person, as specified in official records and the set of person identification data according to the Annex of [(EU) 2024/2977]( http://data.europa.eu/eli/reg_impl/2024/2977/oj), if present.                                      |

#### 2.9.5 Policy

The ``Policy`` class is used within the definition of the [``Provider``](#21-provider) class. It contains the attributes specified in the following table:

| Attribute | Multiplicity | Type | Description |
|-------------|--------------|----------|---------------|
| `type` | [1..1] | *string* | specifies the **type of the policy** in form of a URI according to [RFC3986](https://www.rfc-editor.org/rfc/rfc3986.html), whereas the following URIs are defined in the present document: <ul><li>http://data.europa.eu/eudi/policy/trust-service-practice-statement - is a **Trust Service Practice statement** according to clause 6.1 of [ETSI EN 319 401](https://www.etsi.org/deliver/etsi_en/319400_319499/319401/03.01.01_60/en_319401v030101p.pdf).</li><li>http://data.europa.eu/eudi/policy/terms-and-conditions - is a **Terms and Conditions** statement according to clause 6.2 of [ETSI EN 319 401](https://www.etsi.org/deliver/etsi_en/319400_319499/319401/03.01.01_60/en_319401v030101p.pdf).</li><li>http://data.europa.eu/eudi/policy/privacy-statement - is a **Privacy Statement** to fulfil the information requirements of Article 12 ff [(EU) 2016/679](http://data.europa.eu/eli/reg/2016/679/oj).</li><li>http://data.europa.eu/eudi/policy/privacy-policy - is a **Privacy Policy** according to the clauses 3.14 and 5.6 of ISO/IEC 29100.</li><li>http://data.europa.eu/eudi/policy/registration-policy - is a **Registration Policy** according to Article 4 of [Draft of the CIR for RP-Registration](https://tinyurl.com/IA-5b-draft).</li> </ul> |
| `policyURI` | [1..1] | *string* | specifies the **policy URI** in form of a URL according to [RFC1738](https://www.rfc-editor.org/rfc/rfc1738.html) where the policy is published. |

#### 2.9.6 TrustService

The **TrustService** class is used within the definition of the [TrustServiceProvider](#286-trustservice) class. It contains the attributes specified in the following table:

| Attribute | Multiplicity | Type | Description                                                                                                                                                                                                                                                                                                                           |
|------------------|--------------|----------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `type` | [1..1]       | *string* | specifies the **Service type identifier** of the Trust Service in Form of a URI according to [RFC3986](https://www.rfc-editor.org/rfc/rfc3986.html), whereas the set of admissible URIs is defined in clause 5.5.1 of [ETSI TS 119 612](https://www.etsi.org/deliver/etsi_ts/119600_119699/119612/02.03.01_60/ts_119612v020301p.pdf). |
| `srvName` | [1..1]       | *string* | specifies the **TSP trade name** of the Trust Service according to clause 5.4.2 of [ETSI TS 119 612](https://www.etsi.org/deliver/etsi_ts/119600_119699/119612/02.03.01_60/ts_119612v020301p.pdf).                                                                                                                                    |
| `x5c` | [1..*]      | *string* | specifies the set of **Service digital identities** of the Trust Service according to clause 5.5.3 of [ETSI TS 119 612](https://www.etsi.org/deliver/etsi_ts/119600_119699/119612/02.03.01_60/ts_119612v020301p.pdf) in form of X.509 certificate chains encoded in Base 64.                                                        |
| `status` | [1..1]       | *string* | specifies the **Service current status** of the Trust Service according to clause 5.5.4 point i) of [ETSI TS 119 612](https://www.etsi.org/deliver/etsi_ts/119600_119699/119612/02.03.01_60/ts_119612v020301p.pdf).                                                                                                                   |
| `statusDate` | [1..1]       | *string* | specifies the **Current status starting date and time** of the Trust Service according to clause 5.5.5 of [ETSI TS 119 612](https://www.etsi.org/deliver/etsi_ts/119600_119699/119612/02.03.01_60/ts_119612v020301p.pdf) using the format defined in ISO 8601-1.                                                                      |
| `srvURI` | [1..*]       | *string* | specifies the **Service supply points** of the Trust Service according to clause 5.5.7 of [ETSI TS 119 612](https://www.etsi.org/deliver/etsi_ts/119600_119699/119612/02.03.01_60/ts_119612v020301p.pdf).                                                                                                                             |
| `srvQualifier` | [0..*]       | *string* | specifies the **Service information extensions** of the Trust Service according to clause 5.5.9 of [ETSI TS 119 612](https://www.etsi.org/deliver/etsi_ts/119600_119699/119612/02.03.01_60/ts_119612v020301p.pdf).                                                                                                                    |


#### 2.9.7 WalletSolution

The **WalletSolution** class is used within the definition of the [WalletProvider](#24-walletprovider) class. It contains the attributes specified in the following table:

| Attribute | Multiplicity | Type | Description                                                                                                                                                                                                                                                                                                                           |
|------------------|--------------|----------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `solProvider` | [0..1] | *string* | specifies the **name of the body responsible** for the provision of the wallet solution, if applicable. |
| `walletName` | [1..1] | *string* | specifies the **name of the wallet solution**. |
| `refNum` | [1..1] | *string* | specifies the **reference number** of the wallet solution. |

## 3. Notification System

As defined in [Article 3 (1) of (EU) 2024/2980](http://data.europa.eu/eli/reg_impl/2024/2980/oj), the Commission
will make available to Member States a *Secure Electronic Notification System* enabling Member States to notify
the information on the bodies and mechanisms referred to in [Article 5a(18) of (EU) No 910/2014](https://www.eid.as/#article5a)
and specified in more detail in the [Annexes of (EU) 2024/2980](http://data.europa.eu/eli/reg_impl/2024/2980/oj) and the present document.

The Member States will submit the relevant information according to [Article 4 of (EU) 2024/2980](http://data.europa.eu/eli/reg_impl/2024/2980/oj) to the Commission and the
Commission will in turn publish the relevant information according to [Article 4 of (EU) 2024/2980](http://data.europa.eu/eli/reg_impl/2024/2980/oj)
in form of a suitable *Trusted List* according to [Article 5 of (EU) 2024/2980](http://data.europa.eu/eli/reg_impl/2024/2980/oj).

### 3.1 System Architecture

The envisioned system architecture for the Secure Electronic Notification System described in the present document is fairly simple and mainly consists of

* the *Secure Electronic Notification System* operated by the European Commission and
* decentral *Client Components* operated  by the Member States and other stakeholders within the EUDI ecosystem, which rely on the Trusted List(s) respectively,

as outlined in the following figure.

![NotificationSystem](img/ts2-eudi-notification-system.svg)

### 3.2 Components and Interfaces

The Secure Electronic Notification System has the following interfaces:

1. the *Application Programming Interface (API)* as defined by the [OpenAPI](https://spec.openapis.org/oas/latest.html)-specification provided in [Annex A.2](#a2-openapi-specifications-normative)
2. a suitable *Web Interface* which is at least accessible by the authorized member state representatives and
3. a web endpoint,  where the *Trusted List(s)* according to [Article 5 of (EU) 2024/2980](http://data.europa.eu/eli/reg_impl/2024/2980/oj) and related information is available.

## Annex A

### A.1 JSON-Schema (normative)

The file [``ts-2-eudi-provider.json``](api/ts2-eudi-provider.json) contains the JSON-Schema definitions corresponding to the Data Model specified in [clause 2](#2-data-model) above.

### A.2 OpenAPI-Specifications (normative)

The file [``ts2-openapi-eudi-provider.json``](api/ts2-openapi-eudi-provider.json) contains the JSON-based [OpenAPI](https://spec.openapis.org/oas/latest.html)-specification of the API specified in [clause 3](#3-notification-system) above.

### A.3 XML-Schema (informative)

The file [``ts2-eudi-provider.xsd``](api/ts2-eudi-provider.xsd) contains the XML-Schema definitions corresponding to the Data Model specified in [clause 2](#2-data-model) above.



<img align="right" height="50" src="https://raw.githubusercontent.com/eu-digital-identity-wallet/eudi-srv-web-issuing-eudiw-py/34015dc3c6f52529a99e673df1d4fa69d50f7ff5/app/static/ic-logo.svg"/><br/>

# Specification of Wallet Unit Attestations (WUA) used in issuance of PID and Attestations

## Abstract
The present document specifies how WUA is used in connection with PID Providers and Attestation Providers.

#### [GitHub discussion](https://github.com/eu-digital-identity-wallet/eudi-doc-architecture-and-reference-framework/discussions/450)

## Versioning

| Version | Date       | Description                                                                      |
|---------|------------|----------------------------------------------------------------------------------|
| `0.1`   | 28.03.2025 | Initial version for first discussions.                                           |
| `0.2`   | 14.04.2025 | Improvements after first round of feedback and improved scoping.                 |
| `0.3`   | 28.04.2025 | Addition of Wallet App Attestation, improvements after second round of feedback. |

## 1 Introduction and Overview
The WUA (Wallet Unit Attestation) topic has been discussed in the European Digital Identity Cooperation Group. As a result a number of High Level Requirements (HLRs) have been proposed. The present document is set to enable actors in the EUDIW ecosystem to follow the HLRs while ensuring the interoperability of the ecosystem. The HLRs are available in the [ARF ANNEX 2 Topic 9](https://eu-digital-identity-wallet.github.io/eudi-doc-architecture-and-reference-framework/latest/annexes/annex-2/annex-2-high-level-requirements/#a239-topic-9---wallet-unit-attestation).

This specification is designed to enable the high level requirements defined in the ARF. Additionally the specification strives to ensure that the WUA mechanism is compatible with the existing technical specifications for the EUDIW ecosystem. I.e., the mechanism must be compatible with ISO18013-5 as well as OID4VCI, OID4VP. The goal of the specification, is that the solution is technically simple and does not introduce unnecessary complexity.

[Section 2](#2-solution-description) of this document will serve as the contents of the technical specification and the appendix informally discusses the different solutions that have been proposed during development of this technical specification.

### 1.1 WUA Use Cases (from ARF HLRs)
The HLRs of the ARF mandates that the WUA functionality must support a certain set of information to be transferred from the Wallet Provider (via the Wallet Unit) to the Issuing entities (i.e., PID Provider or Attestation Provider) and another set of information to the Relying Parties. That is, the content of the WUA differs based upon which party receives the information. Additionally, the WUA functionality will be used as part of separate protocols for respective issuance and presentations. We therefore distinguish between these parts of the functionality by using the following terminology:

* *Issuance WUAs*: Wallet Unit Attestations which information will be transferred from a Wallet Provider to the Issuer via the Wallet during issuance. Issuance WUAs must allow Issuers to determine the security level of the wallet, authenticate the wallet and check that it has not been revoked for the lifetime of the attestation they are issuing.
* *Presentation WUAs*: Wallet Unit Attestations which information will be transferred from a Wallet Provider to a Relying Party via the Wallet during presentation. Presentation WUAs must enable a Relying Party to authenticate the wallet and check that it has not been revoked at the time of presentation.

**This technical specification will only address the Issuance WUA.**

### 1.2 Scope
This STS will specify the following:

* The *transfer* of Issuance WUAs between the wallet and the issuing party (i.e., either PID or Attestation Provider).
* The *format* of Issuance WUAs including its encoding and integrity protection mechanism.
* The *content* of Issuance WUAs.
* The *life cycle* of Issuance WUAs.
* The *revocation mechanism* for Issuance WUAs.

> Note that _how_ Wallet Providers issue WUAs to the wallet are out of scope for this technical specification, as this will only be done by the wallet providers themselves and does therefore not require any standard to achieve interoperability.

Below is a simple depiction of which parts of interactions involving WUAs between different actors in the EUDIW ecosystem are in scope of the WUA specifications:

<br/><img src="img/ts3-wua-scope.png"/><br/>

## 1.3 Requirements Notation
The key words "REQUIRED", "SHALL", "SHALL NOT", "SHOULD", "SHOULD NOT", "RECOMMENDED", "NOT RECOMMENDED", "MAY", and "OPTIONAL" in this document are to be interpreted as described in [RFC2119](https://datatracker.ietf.org/doc/html/rfc2119) [RFC8174](https://datatracker.ietf.org/doc/html/rfc8174) when, and only when, they are written in all capital letters.

# 2 Solution Description
EUDI Wallets shall use two types of attestations in relation to issuance: 1) A *Wallet App Attestation* (WAA) that attests *only* the integrity of the app and 2) a *Wallet Unit Attestation* (WUA) that attests the security of keys in the WSCD and that the Wallet Unit has not been revoked.

The WAA allows Attestation Providers to protect their endpoints by only communicating with Wallet Applications which integrity are ensured by the Wallet Providers. WUAs on the other hand allow Attestation Providers to ensure that they only issue attestations that are cryptographically bound to keys that are properly protected (i.e., in a WSCD with sufficiently high attack resistance), as well as to revoke their credentials in case a Wallet Provider revokes a Wallet Unit.

A high level overview of the current solution is given in the table below:

| **Conceptual Part** | **Solution**                                                                                                                                                                                                                                                                                                                                                                                                                     |
|---------------------|----------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Format              | Both WAA and WUA shall be JSON Web Tokens (JWTs) signed by the Wallet Provider. See [Section 2.1 Format](#21-format).                                                                                                                                                                                                                                                                                                            |
| Transport           | The WAA shall be a client attestation sent to token endpoint at  Authorization Server.  The WUA shall be a `key_attestation` element, as part of the `jwt` proof of possession within the `CredentialRequest` of OID4VCI. The `key_attestation` element is extended to include a `eudi_wallet_info` element, containing EUDI Wallet specific information.  See [Section 2.2 Transport](#22-transport).                           |
| Content             | The WAA shall contain only very basic information about the application. Certain WUA information will be transferred in existing elements of the OID4VCI protocol, e.g., revocation information and the public key corresponding to a private key stored in the WSCA/WSCD. Other WAA and WUA information will be a contained in a `eudi_wallet_info` element. The concrete contents are discussed in [Section 2.3 Content](#23-content). |
| Life Cycle          | The WAA shall be have a very short time-to-live. The WUA shall be issued by Wallet Providers that must maintain revocation status for the validity period of the WUA. See [Section 2.4 Life Cycle](#24-life-cycle).                                                                                                                                                                |
| Revocation          | WAA shall not, due to their short time-to-live, have any revocation mechanism associated. Revocation of WUAs shall be done using chunked Status List. See [Section 2.5 Revocation](#25-revocation).|

Below we present details of the technical specification for Issuance WUAs.

## 2.1 Format
A Wallet App Attestation SHALL be a JSON Web Token (JWT) as specified in [RFC7519](https://datatracker.ietf.org/doc/html/rfc7519).

A Wallet Unit Attestation SHALL be a JSON Web Token (JWT) as specified in [RFC7519](https://datatracker.ietf.org/doc/html/rfc7519).

## 2.2 Transport
The ARF specifies that [OIDF OpenID for Verifiable Credential Issuance - draft 15](https://github.com/eu-digital-identity-wallet/eudi-doc-standards-and-technical-specifications/issues/3) is to be  used for issuance, hence the transport of the WAA and WUA must be compatible with the options of the OID4VCI protocol.

### 2.2.1 Transport of WAA
The WAA SHALL be an OAuth Client Attestation as specified in [OAuth 2.0 Attestation-Based Client Authentication](https://datatracker.ietf.org/doc/html/draft-ietf-oauth-attestation-based-client-auth-04#name-client-attestation-pop-jwt) and sent to the Authorization Server in the Pushed Authorization Request and the Token Request.

The WAA SHALL be signed by the Wallet Provider.

The WAA SHALL either be sent along with a Proof-of-Possession (PoP) OR it SHALL contain the `nonce` value obtained from the nonce endpoint of the Credential Issuer. The former will be referred to as a key bound WAA and the latter as an ephemeral WAA.

> Note that ephemeral are considered to be slightly more secure as the time window for compromising the integrity of the app is reduced. However, the WAA is not a security critical mechanism, but merely a hardening mechanisms which PID and Attestation Providers can use to protect their end points.

If a key bound WAA is sent to the Wallet, then it SHALL have a time-to-live of less than 24 hours. I.e., the difference between expiration time `exp` and the time of issuance SHALL be less than 24 hours.

If an ephemeral WAA is sent to the Wallet, then it SHALL have a time-to-live of less than 30 seconds. I.e., the difference between expiration time `exp` and the time of issuance SHALL be less than 30 seconds.

#### 2.2.1.1 Wallet Providers Responsibilities for Transport of WAAs
A Wallet Provider SHALL verify the integrity of the Wallet Application before signing a WAA.

The Wallet Provider SHALL ensure that a Wallet Unit can either receive ephemeral WAAs on demand by the Wallet or ensure that the Wallet has key bound WAAs as needed for issuance.

Wallet Provider SHALL ensure that their Wallets only use a WAA once.

> This is to prevent issuer linkability.

#### 2.2.1.2 PID Providers and Attestation Providers Responsibilities for Transport of WAAs
When a PID Provider or Attestation Provider receives a WAA, then they SHALL check that the signature of the JWT verifies under the Wallet Provider's public key as found on the Trusted List of Wallet Providers.

When a PID Provider or Attestation Provider receives a WAA, then they SHALL check that it has not expired.

If a PID Provider or Attestation Provider receives a WAA with no PoP, then they SHALL check that included `nonce` is valid from their nonce endpoint.

If a PID Provider or Attestation Provider receives a WAA with a PoP, then they SHALL check the signature of the PoP verifies under the present in the `cnf`.

### 2.2.2 Transport of WUA
The WUA SHALL be a `key_attestation` as defined in [Appendix D of OpenID for Verifiable Credential Issuance - draft 15](https://openid.net/specs/openid-4-verifiable-credential-issuance-1_0-15.html#keyattestation) but extended with a  `eudi_wallet_info` as presented in [Section 2.3 Content](#23-content).

During issuance in OID4VCI, EUDI Wallets SHALL in the `proof` field include the WUA in a proof of type `jwt` with their *CredentialRequest* to the Credential Issuer.

> Note the `jwt` acts as a proof-of-possesion (PoP) of the keys.

#### 2.2.2.1 Wallet Providers Responsibilities for Transport of WUAs
The WUA (i.e., the `key_attestation` element) SHALL be generated and signed by the *Wallet Provider*.

The Wallet Provider SHALL verify that the keys attested to in the `key_attestation` are stored in secure hardware as described in the `key_attestation`.

Wallet Providers SHALL ensure that their Wallet generate a `jwt` element signed by the *Wallet Unit* with the key at index 0 of the `attested_keys` array within the `key_attestation` object.

> Requiring only one signature on the entire `jwt` may improve the user experience as some WSCDs may require a user gesture to sign. Note that this does not degrade the security as the signature of the Wallet Provider still binds all all the keys to the same WSCD.

Wallet Providers SHALL ensure that their Wallets use a WUA only once and each individual key is SHALL only be included in one WUA.

> This is to prevent verifier linkability.

#### 2.2.2.2 PID Providers and Attestation Providers Responsibilities for Transport of WUAs
PID and Attestation Providers SHALL verify that the signature of the WUA verifies under the Wallet Provider's public key as found on the Trusted List Wallet Providers.

PID and Attestation Providers SHALL verify that the signature of the `jwt` element matches the key at index 0 of the `attested_keys` array within the `key_attestation` object included in the `jwt`.

PID and Attestation Providers SHALL verify that the `jwt` element includes a valid `nonce` from their `nonce` endpoint.

## 2.3 Content
The high-level requirements of the ARF require a number of different attributes being transferred as part of the WAA and WUA. Some of these attributes are already defined by the OID4VCI specification, in which case OIDC4VCI will be used. Other attributes are specific for the EUDI Wallet ecosystem, these are placed in a `eudi_wallet_info` element in both the WAA and WUA.

The `eudi_wallet_info` object contains the following informational content:

| Attribute | Multiplicity | Type | Description |
|---------------|--------------|-----------------------------------|--------|
| `general_info` | REQUIRED in both WAA and WUA| [`general_info`](#231-generalinfo) | specifies generic information on the Wallet Unit. |
| `wscd_info` | REQUIRED in WUA | [`wscd_info`](#232-wscdinfo) | specifies information on the WSCD containing the attested keys. |

### 2.3.1 `general_info`
The `general_info` object has the following content:

| Attribute | Multiplicity | Type | Description |
|---------------|--------------|-----------------------------------|--------|
| `wallet_provider_name` | REQUIRED | *string* | **Name of Wallet Provider**, as listed on the Trusted List of Wallet Providers |
| `wallet_solution_id` | REQUIRED | *string* | **Identifier of the Wallet Solution**, as listed on the Trusted List of Wallet Providers. |
| `wallet_solution_version` | REQUIRED | *string* | **Version of the Wallet Solution** |
| `wallet_solution_certification_information` | REQUIRED | *JSON/string* | Object containing information on which conformity assessment body certified the Wallet Solution, the applicable certification number, etc. |

### 2.3.2 `wscd_info`
The `wscd_info` object has the following content:

| Attribute | Multiplicity | Type | Description |
|---------------|--------------|-----------------------------------|--------|
| `wscd_type` | RECOMMENDED | *string* | Technical implementation of the WSCD, for instance remote HSM or external smart card |
| `wscd_certification_information` | REQUIRED | *JSON / string* | Information about the certification achieved by the WSCD, such as under which scheme (for instance, Common Criteria, GlobalPlatform), the requirements that were evaluated (for example, the Protection Profile used), the evaluation level, and perhaps other applicable information. |
| `wscd_attack_resistance` | REQUIRED | *integer [1-3]* | Integer representing the level of Attack Resistance for all functions offered by the WSCD, corresponding to eIDAS LoA; 3 = High / 2 = Substantial / 1 = Low |

### 2.3.3 Content of WAA
The content of the WAA is given by the OAuth Client Attestation as specified in [OAuth 2.0 Attestation-Based Client Authentication](https://datatracker.ietf.org/doc/html/draft-ietf-oauth-attestation-based-client-auth-04#name-client-attestation-pop-jwt). In addition to the required attributes (e.g. ``iss``, ``exp`` and ``jti``), the WAA SHALL also include the `eudi_wallet_info` claim, containing `general_info` described in [*general_info*](#231-generalinfo).

### 2.3.4 Content of WUA
The content of the WUA is given by the `key_attestation` definition specified in [Appendix D of OpenID for Verifiable Credential Issuance - draft 15](https://openid.net/specs/openid-4-verifiable-credential-issuance-1_0-15.html#keyattestation)
In addition to the required attributes (e.g. ``iat`` and ``attested_keys``), the WUA SHALL also include the `eudi_wallet_info` claim, containing both `general_info` described in [*general_info*](#231-generalinfo) and `wscd_info` described in [*wscd_info*](#232-wscdinfo). The WUA SHALL also include the `status` object.

> OID4VCI natively supports revocation, hence the `status` object of the `key_attestation` element SHALL be used to handle revocation. In particular, the value of `idx`  is what allows the Wallet Provider to identify the Wallet Unit (i.e. the revocation identifier) and is therefore what is required by the PID provider to request a revocation of the Wallet Unit.

> Note that the `key_attestation` element contains the signed keys in `jwk` format. The `jwk` format specifies that each key must contain an algorithm type. Hence, this provides protection against downgrade attacks for attested keys.

> Also note that the `key_attestation` element contains an `iss` element, i.e. the issuer identifier, which also includes the Wallet Provider identity.

## 2.4 Life Cycle
WAAs are short-lived and to be consumed upon usage, hence this section only specifies the life cycle of the WUAs.

### 2.4.1 Wallet Provider responsibilities
A Wallet Provider SHALL choose the technical validity period of the WUA and SHALL maintain the revocation mechanism i.e., see [Section 2.5](#25-revocation) for until this period has passed.
The `key_attestation` JWT contains a field `exp` denoting the technical expiration period of the `key_attestation`.

When choosing the validity period, the Wallet Provider SHALL at least consider account security, user privacy and interoperability. Regarding interoperability, PID or Attestations SHALL NOT have an expiration date later than the expiration date of the WUA used during issuance, hence the validity period of the WUA SHOULD be at least 1 month.

> Note that the validity period has impact on the revocation mechanism. A longer validity period will require the revocation status list to be maintained for a longer period of time. A shorter validity period may result in more frequent issuance of WUAs.

A Wallet Provider SHALL keep track of which WUAs are associated with which Wallet Units.

In case a Wallet Unit is to be revoked, a Wallet Provider SHALL revoke all WUAs associated with this Wallet Unit.

### 2.4.2 PID Provider and Attestation Provider responsibilities
A PID Provider SHALL check the revocation status of the WUA received in relation to issuance once every 24 hours for the validity period of the PID. If the WUA is revoked, then PID Provider SHALL revoke the PID. If PID Providers issue PIDs with a validity period of less than 24 hours, they only need to verify the validity period of the WUA upon issuance.

Attestation Providers MAY check the revocation status of the WUA and revoke their attestations if the WUA is revoked.

The technical validity period of a PID or Attestation SHALL end before the technical validity period of the issuance WUA shown to the PID or Attestation Provider in the issuance process.

During re-issuance of a PID or Attestation (i.e., if for example the technical validity of a PID or Attestation expires before the administrative validity period expires), then the Wallet Unit (or Attestation Provider) SHALL send a new WUA (i.e., a WUA that has not been used in relation to issuance before) in the *Credential Request* to the PID or Attestation Provider.

> Note it is required to be a new WUA as the keys should be different from previous WUA in order to prevent linkability of keys upon presentation.

## 2.5 Revocation
Status lists, as defined in [I-D.ietf-oauth-status-list] SHALL be used as revocation mechanism as described in Appendix D and E of the OID4VCI specification, i.e. the `status` element of `key_attestation` SHALL be used.

To ease scalability, the Wallet Provider can use the following optimisations:
* The status list SHOULD be chunked by issuance date, i.e. a separate status list is generated for all WUAs issued each single day. The URI specified in the `status` element of the `key_attestation` SHOULD contain the issuance date, i.e. the URI will have a format similar to: `https://revocation_url/statuslists/2024/12/24/` for WUAs issued on Dec. 24, 2024.
* The status list SHOULD be compressed to reduce the size.

# 3 Appendix

## 3.1 Example JSON
A number of different data objects are sent in the OID4VCI protocol. Below we provide some non-normative examples:

Example of a key bound *Wallet App Attestation*:
```
{
  "typ": "oauth-client-attestation+jwt"
  "alg": "ES256",
  "kid": "11"
}
.
{
  "iss": "https://client.example.com",
  "sub": "https://client.example.com",
  "eudi_wallet_info": {JSON},
  "exp": 1300819380,
  "cnf": {
    "jwk": {
      "kty": "EC",
      "use": "sig",
      "crv": "P-256",
      "x": "18wHLeIgW9wVN6VD1Txgpqy2LszYkMf6J8njVAibvhM",
      "y": "-V4dS4UaLMgP_4fY4j8ir7cl1TXlFdAgcx55o7TkcSA"
    }
  }
}
```

Example of a *Credential Request*:
```
{
  "credential_configuration_id": "org.iso.18013.5.1.mDL",
  "proof": {
    "proof_type": "jwt",
    "jwt": "eyJraWQiOiJkaWQ6ZXhhbXBsZTplYmZlYjFmNzEyZWJjNmYxYzI3NmUxMmVjMjEva2V5cy8xIiwiYWxnIjoiRVMyNTYiLCJ0eXAiOiJKV1QifQ"
  }
}
```

Example of a `jwt` object (part of a *Credential Request*):
```
{
  "typ": "openid4vci-proof+jwt",
  "alg": "ES256",
  "kid": "0",
  "key_attestation":["eyJraWQiOiJkaWQ6ZXhhbXBsZTplYmZlYjFmNzEyZWJjNmYxYzI3NmUxMmVjMjEva2V5cy8xIiwiYWxnIjoiRVMyNTYiLCJ0eXAiOiJKV1QifQ"]
}.{
  "aud": "https://credential-issuer.example.com",
  "iat": 1701960444,
  "nonce": "LarRGSbmUPYtRYO6BQ4yn8"
}
```

Example of a `key_attestation` object:
```
{
  "typ": "keyattestation+jwt",
  "alg": "ES256",
  "x5c": ["MIIDQjCCA..."]
}
.
{
  "iss": "<identifier of the issuer of this key attestation - Corresponds to `wallet_provider_name` in `eudi_wallet_info`>",
  "iat": 1516247022,
  "exp": 1541493724,
  "eudi_wallet_info": {JSON},
  "status": {
    "status_list": {
        "idx": 412,
        "uri": "https://revocation_url/statuslists/1"
      }
  }
  "attested_keys": [
    {
      "kty": "EC",
      "crv": "P-256",
      "x": "TCAER19Zvu3OHF4j4W4vfSVoHIP1ILilDls7vCeGemc",
      "y": "ZxjiWWbZMQGHVWKVQ4hbSIirsVfuecCE6t4jT9F2HZQ"
    }
  ]
}
```

Example of the `eudi_wallet_info` object:
```
"eudi_wallet_info": {
  "general_info": {
     "wallet_provider_name": "WalletCorp",
     "wallet_solution_id": "SmartWallet-mobile",
     "wallet_solution_version": "1.0.1",
     "wallet_solution_certification_information": "https://example.org/certification/SmartWalletMobile/1-0-1/"
  },
  "wscd_info": {
     "wscd_type" : "REMOTE HSM",
     "wscd_certification_information" : "GlobalPlatform",
     "wscd_attack_resistance" : 2
  }
}
```

## 3.2 Revocation discussion

In this section, we list and discuss possible revocation methods that have been investigated during the writing of this STS.
We will use the following abbreviations when discussing the solutions.

*n*: number of WP users.
*n_iss*: number of Wallet Units using the issuer.
*m*: Avg. number of issuers of PID or Attestations used by each Wallet Unit.

| Name of method | Description        | Pro  |  Cons                        |   
|---------|-------------|----------------------------------|---------------------------|
| Status list  | Each attestation contains a random (unique pr. issuer) revocation identifier generated and stored by the WP. When the WP revokes a Wallet Unit, it will add the identifiers of that Wallet Unit to the public revocation list, which contains all revoked identifiers. | Conceptually easy to understand and generally well supported. The WP does not learn which wallet units access which issuers, only that a issuer has accessed the status list. The status list is fairly static and can be published using a CDN or similar technologies. | The WP needs to maintain the status for *n x m* identifiers. |
| Chunked status list | Instead of publishing all revocations on a single status list, the WP may opt to publish the revocations of a subset of the attestations on separate lists. This chunking could be based on the date of issuance, i.e. revocations related to attestations issued on 1/1/2026 can be found on URI A and revocations related to attestations issued on 2/1/2025 can be found on URI B, etc. | This will reduce the size of each status list. | All parties need to keep track of both the revocation identifier and additional information (date of issuance). |
| Secret seed PRNG status list | The WP stores a secret seed for each Wallet Unit. This seed is used to generate the revocation identifier. When the WP revokes a Wallet Unit, it will add the secret seed to the public revocation list, allowing the issuers to compute the revocation identifiers. Otherwise this functions as a status list. | The WP will only need to maintain the status for *n* seeds. | After revocation, the seed is published, making it possible to compute and thereby link the revocation identifiers.|  
| Online status protocol | Instead of the issuer downloading a complete status list, the issuer queries the WP for the status of each individual Wallet when doing a revocation check. Note that the Wallet identifier used in this approach can be generated by hashing the issuer identifier and a secret key shared between the Wallet Unit and Wallet Provider. | The WP only needs to maintain the status for the *n* Wallet Units. The Issuer only needs to process the relevant *n_iss* Wallet Units.| Each request will require the WP to do a lookup and cannot be distributed as static data. The WP also learns which issuers have been accessed by the Wallet Unit.|
| Wallet Type lookups | The 'Status list' and 'Online status protocol' methods can be modified to operate on "Wallet types" rather than individual wallets. Instead of a revocation id, the WUA will contain a "Wallet type" attribute, which can be used to revoke "classes" of Wallet Units.| As there will be a very small (compared to individual Wallet Units) number of wallet types, computational complexity and privacy issues are minimal. | The approach does not allow for revocation of individual Wallet Units, which is required for PID use cases. |
| Short lived attestations | As an alternative to revocation, the WUA can expire less than 24 hours after issuance, this would eliminate the need for revocation altogether. | WP does not need to maintain revocation status. | WP will often have to perform verifications of the integrity of the Wallet Unit. Short lived attestations will not accommodate the legal requirement for PID providers to check the revocation status of the Wallet Unit. |

#### 3.2.1 Revocation proposal

With the above solutions in mind, we propose to use the chunked status list, i.e. a separate status list is generated for all WUAs issued each single day. The URI will have a format similar to:
`https://revocation_url/statuslists/2024/12/24/` for WUAs issued on Dec. 24, 2024. We note that status lists encourage compression, which will reduce the size in general. It is also possible to do additional chunking to further reduce the status list sizes. A similar approach to revocation status list are used elsewhere in the ARF and it would be preferable if the same method could also be used for WUA. We note that revocation status lists are also natively supported by the *key_attestation* element in OID4VCI.

Regarding the scalability of the described proposal, a rough calculation of the complexity for a status list corresponding to one day is provided below:

The example is based on a Wallet Provider servicing 80 mio. Wallet Units, each having 10 WUAs issued per day, this will result in revocation information for one day for 8 * 10^8 WUAs.

> Note that each wallet having 10 WUAs issue each day probably is an exaggerated estimate by a factor of 5-10. The estimate can be further broken down to *avg. number of issuers for each wallet / lifetime of the WUA*, as it depends on the number of PID providers and Attestations providers each Wallet Unit interacts with and with the lifetime of the WUA: Using short-lived WUAs will limit the lifetime of the issued PIDs and attestation and thereby force more frequent re-issuance. As each re-issuance will also require a new WUA, this requires the Wallet Unit to more frequently request issuance of WUAs.

The (uncompressed) status list will therefore be around 8 * 10^8 bits or 100 MB per day. However, very high compression rates are expected due to the nature of the status lists, and the compressed lists are estimated to be around 1 MB if not smaller.

> Note that if this is deemed impractical, then the size of the chunks of the status list can be reduced further. For example it could be reduced to 10^5 which will give a compressed bit string status list in the range of hundreds of bytes.

The Wallet Provider will need to keep track of which revocation identifier (index of the status list) belongs to which Wallet Unit. Assuming 64 bits are allocated for the revocation identifier, the Wallet Provider will need to store revocation information will require roughly 6.4 GB of storage.


<img align="right" height="50" src="https://raw.githubusercontent.com/eu-digital-identity-wallet/eudi-srv-web-issuing-eudiw-py/34015dc3c6f52529a99e673df1d4fa69d50f7ff5/app/static/ic-logo.svg"/><br/>

# Specification for ZKP Implementation in EUDI Wallet

## Abstract

The present document specifies the technical specification and requirements for Zero-Knowledge Proof (ZKP) Implementation in EUDI Wallet.

### [GitHub discussion](https://github.com/eu-digital-identity-wallet/eudi-doc-architecture-and-reference-framework/discussions/485)

## Versioning

| Version | Date | Description |
|---------|------------|------------|
| `0.1` | 03.04.2025 | Initial version for discussion |
| `0.2` | 23.04.2025 | Updates based on first group meeting |
| `0.3` | 02.05.2025 | Updates based on second group meeting |

## 1 Introduction and Overview
This document provides a technical overview of existing Zero-Knowledge Proof (ZKP)
systems that could serve as potential candidates for inclusion in a **future** technical
specification for ZKP implementation within the EUDI  Wallet. At present, no existing
ZKP approach can be deemed fully suitable or mature enough for direct integration into
the EUDI Wallet. The objective of this document is therefore to examine current
ZKP technologies from a technical perspective, assess their applicability in the context
of the EUDI Wallet ARF, and identify existing gaps or limitations.

High Level Requirements (HLRs) of the ARF with respect to the use of ZKPs are presented
in the Annex 2 of the ARF under Topic 53.

## 2 Available Zero-Knowledge Proof schemes
Following the classification of ETSI TR 119 476 [ETSI_119476] and [Topic_G] we discuss
two categories of ZKP schemes: multi-message signature schemes and proofs for arithmetic circuits.

## 2.1 Multi-message signature schemes
From a high-level perspective, multi-message signature-based solutions are implemented as follows.
Initially, a PID Provider or Attestation Provider constructs an attestation that can be
represented in the form of a list of messages. Then it uses a multi-message signature algorithm
and generates a (short) signature over the set of messages. A Wallet Unit can now selectively hide
any of the messages and generate a ZKP which proves that "the Wallet Unit possesses a list of messages
that together with the revealed ones can verify the signature of the PID Provider or Attestation Provider".

### 2.1.1 BBS+
BBS+ is a digital signature protocol which is used for signing a set of
messages.  It was first envisioned by Boneh, Boyen, Shacham in [BBS2004] (from
where it takes its name), touched and re-visited by [Cam2016]. Currently under
standardisation by the IRTF Crypto Forum Research Group [Loo2025] based on the
improvements presented in [Tes2023], as well as by ISO/IEC in "ISO/IEC PWI 24843
Privacy-preserving attribute-based credentials". The description of BBS+ in the rest of this
section is based on [Tes2023].

#### 2.1.1.1 Issuance
The PID or Attestation Provider transforms a PID or attestation into a list of
messages (e.g., using a technique such as [Kal2022]). This list of messages is
then signed using the BBS+ signature scheme as described in [Tes2023], which relies
on pairing-friendly elliptic curves. The resulting signed attestation is subsequently
transmitted to the Wallet Unit.

#### 2.1.1.2 Presentation
A Wallet Unit can generate a presentation of an attestation that includes only a
subset of the messages from the list generated during issuance. It then creates a
zero-knowledge proof (ZKP), using the scheme described in [Tes2023], demonstrating
that the disclosed messages are indeed part of the original list of messages
signed by the Provider.

#### 2.1.1.3 Performance
BBS+ proof generation and verification is reported to be less than 2ms. The size
of the BBS+ proof is 272+32*i bytes, where i is the number of hidden messages.

#### 2.1.1.4 Discussion
BBS+ achieves high performance and its building blocks are well-researched. However.
pairing-based cryptographic algorithms and pairing friendly elliptic curves are not
standardized and they are not supported by existing Hardware Security Modules (HSMs),
Secure Elements, or SIM cards.
Similarly, algorithms for transforming attestation formats specified in [ISO/IEC 18013-5] or [SD-JWT VC]
into list of messages are missing. Finally, the BBS+ approach under standardization
does not consider binding of an attestation to a public key controlled by the Wallet Unit
of the User.

### 2.1.2 Pairing-free BBS schemes
Recent efforts (BBS# [Des2025] and SAAC [Api2025]) propose pairing-free variants
of BBS. These schemes leverage a construction known as Keyed-Verification Anonymous Credentials (KVAC),
which is a type of anonymous credential used in a special setting where the Provider and the
Relying Party are the same entity (i.e., they share a private key). KVACs are very
efficient, do not rely on pairings, and are widely adopted in the Signal messaging system [Cha2020].
The main building block of KVACs is a Message Authentication Code (MAC). Both approaches
build upon the solution presented in [Bar2016] which creates a MAC for a list of
messages using a paring free variant of BBS signatures [BBS2004]  and then allows a user
to reveal a subset of these messages, proving at the same time that it knows
a valid MAC over the complete list of messages; this proof can be verified using
the Provider's secret key.  
Additionally, BBS# proposes a solution for device-binding from ECDSA-signatures,
relying on re-randomization of ECDSA signatures and public keys. Furthermore,
a trust model for BBS# that covers revocation and proof of validity is defined
in [BBT2025].

#### 2.1.2.1 Issuance
The PID or Attestation Provider transforms a PID or attestation into a list of
messages. Then it produces a MAC *A* using its secret key and a random number *e*. Finally,
it transmits (A,e) to the Wallet Unit.

#### 2.1.2.2 Presentation
The Wallet Unit randomizes *A* and obtains a new *A'*. Furthermore using its attestation,
a random number, and  *e* it generates a new number *B'*. *B'* has the property that it equals to
*A'* raised to the secret key of the Provider. In the setting where the Provider and
the Relying Party are the same entity, the Relying Party has only to check if the
latter equality holds. However, in the general case the Relying Party does not
have access to the private key of the Provider. Therefore two approaches are proposed:

* The Relying Party asks the Provider to verify that *B'* equals to *A'* raised to
its secret key. Because both numbers are randomized, the Provider cannot linked them
back to User.
* The Wallet Unit asks the Relying Party to verify *B'* equals to *A'*. This can be done
in batch and at an earlier time. In order to preserve unlinkability, the Wallet Unit
"blinds" these two numbers and the provider generates a proof based on the blinded
values. This is achieved using Oblivious Issuance of Proofs [Orr2024].

Additionally, BBS# defines algorithms for public key randomization with the aid
of the WSCD, and for proving possession of the corresponding private key, which is
stored securely within the WSCD.

#### 2.1.2.3 Performance
[Des2025] reports for BBS# proof generation and verification times of less than 2.5ms in high-end
mobile devices. Similarly reports that the size of a BBS# presentation proof is 416+U*32
bytes, where U denotes the number of hidden messages.

#### 2.1.2.4 Discussion
BBS# and SAAC offer high performance but introduce additional communication between
the Relying Party or Wallet Unit and the Provider. This additional interaction is
comparable in  volume to batch issuance of attestations. Notably,
both schemes avoid the use of pairing-based cryptography, however, they
still require standardization. Furthermore, in both approaches the operations
required from the Provider side are not currently supported by existing Hardware
Security Modules (HSMs). Finally, BBS# supports binding an attestation to a public
key controlled by the Wallet Unit and stored securely within the associated WSCD.  

### 2.1.3 BBS with ECDSA proof of possession
Recent ZKP schemes enable the proof of possession of a secret key corresponding
to an ECDSA digital signature, along with a commitment to the associated public key.
These schemes can be constructed using either Sigma protocols [Cel2024] or zkSNARKs
[Woo2025]. By combining such a proof mechanism with BBS signatures, it
becomes possibly to bind an attestation to a private key stored in a WSCD.

#### 2.1.3.1 Issuance
The PID or Attestation Provider follows the same steps described in section 2.1.1.1
including however in the list of signed message an ECDSA public key.

#### 2.1.3.2 Presentation
The Wallet Unit performs the steps described in section 2.1.1.2 making sure that
the public key included in the list of messages is hidden. It then performs the
following additional steps: it creates a commitment of the public key, it generates
a proof that that the committed public key is the same as the (hidden) public
key included in the attestation, it generates an ECDSA digital signature
of a fresh nonce using the
device's WSCD, it generates a proof that signature can be verified using the
committed public key.

#### 2.1.3.3 Performance
This approach introduces some additional overhead related to  proofs.
[Cel2024] report proof size grater than 160kB, and proof generation and verification
times over 610ms and 450ms respectively in a Macbook M1 with 8 GB of memory. [Woo2025]
reports proof generation time 1.6msec. and proof verification time 1.7msec in a
AMD Ryzen Threadripper 5995WX 1.8GHz CPU, 256 GBs RAM server. Similarly, [Woo2025]
reports proof size equal to 406 bytes.

#### 2.1.3.4 Discussion
Both of these approaches support proof-of-possession of an ECDSA private key.
However, both solutions require support for paring cryptography and pairing-friendly
curves. Finally, these schemes still require standardization.   

## 2.2 Proofs for arithmetic circuits (programmable ZKPs)

These solutions are based on a program expressed in the form of an arithmetic
circuit. This circuit receives a secret input, referred to as the witness,
which can be for example an attestation, as well as a public statement. The
circuit performs a calculation and outputs true if certain conditions hold (e.g.,
“the attestation includes an age attribute with value > 18”). A Wallet Unit
can then generate a ZKP which proves that “the Wallet Unit knows a witness (e.g.,
an attestation), which when provided as input to a certain circuit using the
provided statement, the circuit outputs true”.

### 2.2.1 Anonymous credentials from ECDSA
Anonymous credentials based on ECDSA are presented in [Fri2024]. This approach
builds upon the Ligero protocol [Ame2017].

#### 2.2.1.1 Setup
This solution does not require a trusted setup phase. However, the arithmetic
circuits used to perform cryptographic computations within the Wallet Unit must
be carefully designed, implemented, and distributed.

#### 2.2.1.2 Issuance
PID Providers or Attestation Providers remain unaware of the use of this scheme;
therefore, no changes are required to the existing issuance process.

#### 2.2.1.3 Presentation
To generate a zero-knowledge proof for the presentation of an attestation, the Wallet Unit
first encodes the attestation as private inputs (i.e., witnesses) to a suitable arithmetic
circuit that represents the desired statement. The circuit also defines any public inputs,
such as the public key of the Provider. The Wallet Unit then runs the zkSNARK prover algorithm
over the circuit using the witness and public inputs, producing a succinct proof. This proof
can be verified by any third party using the public inputs.

#### 2.2.1.4 Performance
The solution in [Fri2024] is reported to generate a proof that an [ISO/IEC 18013-5]
attestation is valid and it includes an age_over_18 attribute in 1.2sec in a
Pixel 6 pro phone. The corresponding verification time is 0.6sec. The size of the proof
is approx 400KB.

#### 2.2.1.5 Discussion
The anonymous credentials from ECDSA approach introduces the highest computational and
communication overhead among the solutions discussed in this document. Additionally,
several components of the scheme are not yet standardized. This solution also requires
the design and deployment of separate arithmetic circuits for each type of proof
statement (e.g., depending on the format or structure of the attestation)

On the other hand, this solution does not require any change to the credential issuance
process and it can be used with the attestation formats specified in [ISO/IEC 18013-5] or [SD-JWT VC].
Similarly, it supports attestation binding to a public key controlled by the Wallet Unit
and stored securely within the associated WSCD.

### 2.2.2 Crescent
Crescent is presented in [Paq2024] and builds upon Groth16 [Gro2016] zkSNARK

#### 2.2.1.1 Setup
This solution requires a trusted setup during which a proving key and a verification key
for a specific arithmetic circuit are generated, which should be distributed to Wallet Units
and Relying Parties respectively. This process requires a one-time generation
of structured reference strings (SRS), which must be securely discarded afterward to prevent
compromise. The setup is circuit-specific, meaning a new setup must be performed for
each unique statement or circuit. Additionally, the arithmetic
circuits used to perform cryptographic computations within the Wallet Unit must
be carefully designed, implemented, and distributed.

#### 2.2.2.2 Issuance
PID Providers or Attestation Providers  are oblivious to the use of this scheme, therefore
no changes are required to the existing issuance process.

#### 2.2.2.3 Presentation
In Crescent, the proof generation process is split into two phases: an offline phase
and an online phase. In the offline phase, which is executed only once, the Wallet Unit
encodes the attestation as a witness for a pre-defined arithmetic circuit. Using this
witness the Wallet Unit computes a Groth16 proof. In the online phase, the Wallet Unit
re-randomizes the proof to ensure unlinkability between multiple presentations of the
same attestation. This re-randomized proof can then be safely shared with the Relying Party,
who verifies it using the corresponding verification key and the disclosed public inputs.

#### 2.2.2.4 Performance
When used in an Intel Xeon W-2133 CPU at 3.60GHz with 6 cores Crescent is reported
to achieve online proof generation in 29.2ms and proof verification in 11.7ms. These numbers
are increased to 315ms and 184ms respectively when device binding is used. The offline
proof generation requires 19sec. The size
of the setup parameters is 580MB and the size of a proof is 1019 bytes.

#### 2.2.2.5 Discussion
Crescent has better performance than Anonymous credentials from ECDSA solution however
the trusted setup parameters create significant storage overhead. Moreover, some components
of this solution are not standardized.

Similarly, to anonymous credentials from ECDSA, Crescent does not require any change to the credential issuance
process and it can be used with the attestation formats specified in [ISO/IEC 18013-5] or [SD-JWT VC].
Crescent also supports attestation binding to a public key controlled by the Wallet Unit
and stored securely within the associated WSCD.



## 3 References

| Reference | Description |
| --- | --- |
| [Ame2017] | Scott Ames, Carmit Hazay, Yuval Ishai,  Muthuramakrishnan Venkitasubramaniam, "Ligero: Lightweight Sublinear Arguments Without a Trusted Setup", in ACM CCS 2017
| [Api2025] | Rutchathon Chairattana-Apirom, Franklin Harding, Anna Lysyanskaya, and Stefano Tessaro, "Server-Aided Anonymous Credentials," available at <https://eprint.iacr.org/2025/513>, 2025
| [Bar2016] | Amira Barki, Solenn Brunet, Nicolas Desmoulins, and Jacques Traor´e, "Improved algebraic MACs and practical keyed-verification anonymous credentials," In Roberto Avanzi and Howard M. Heys, editors, SAC 2016, volume 10532 of LNCS, pages 360–380. Springer, Cham, August 2016
| [BBT2025] | Trust Model : Securing digital identity with advanced cryptographic algorithms, available at https://github.com/Orange-OpenSource/BBS-SHARP-doc-eudi-wallet ,  2025
| [Des2025] | Nicolas Desmoulins, Antoine Dumanois, Seyni Kane, and Jacques Traoré, “Making BBS Anonymous Credentials eIDAS 2.0 Compliant”, Cryptology ePrint Archive, Paper 2025/619, 2025, available at <https://eprint.iacr.org/2025/619> |
| [Topic_G] | Discussion Paper for the European Digital Identity Cooperation Group regarding Topic G: Zero Knowledge Proof, version 1.4 |
| [BBS2004] | Boneh, Dan, Xavier Boyen, and Hovav Shacham. "Short group signatures." In Annual international cryptology conference, pp. 41-55. Berlin, Heidelberg: Springer Berlin Heidelberg, 2004. |
| [Cel2024] | Sofia Celi, Shai Levin, and Joe Rowell, "CDLS: proving knowledge of committed discrete logarithms with soundness," Progress in Cryptology – AFRICACRYPT 2024 |
| [Cha2020] | M Chase, T Perrin, G Zaverucha "The Signal Private Group System and Anonymous Credentials Supporting Efficient Verifiable Encryption." In ACM CCS 2020 |
| [ETSI\_119476] | ETSI TR 119 476 V1.2.1, Electronic Signatures and Trust  Infrastructures (ESI); Analysis of selective disclosure and zero-knowledge proofs applied to Electronic Attestation of Attributes |
| [Fri2024] | Matteo Frigo and abhi shelat, Anonymous credentials from ECDSA, Cryptology ePrint Archive, Paper 2024/2010, 2024, available at <https://eprint.iacr.org/2024/2010> |
| [Gro2016] | Jens Groth, “On the Size of Pairing-Based Non-Interactive Arguments”, in EUROCRYPT 2016 |
| [Kal2022]| V Kalos, GC Polyzos, "Requirements and Secure Serialization for Selective Disclosure Verifiable Credentials", in IFIP SEC 2022
| [Loo2025] | Tobias Looker, Vasilis Kalos, Andrew Whitehead and  Mike Lodder, "The BBS Signature Scheme," available at <https://datatracker.ietf.org/doc/draft-irtf-cfrg-bbs-signatures/>, 2025
| [Orr2024] | Michele Orrù, Stefano Tessaro, Greg Zaverucha, Chenzhi Zhu, "Oblivious issuance of proofs", In Annual International Cryptology Conference, 2024 |
| [Paq2024] | Christian Paquin, Guru-Vamsi Policharla, and Greg Zaverucha, "Crescent: Stronger Privacy for Existing Credentials, Cryptology ePrint Archive, Paper 2024/2013, 2024, available at <https://eprint.iacr.org/2024/2013> |
| [Tes2023] |Tessaro, S. and C. Zhu, "Revisiting BBS Signatures", In EUROCRYPT, 2023|
| [Woo2025] | Anna P. Y. Woo, Alex Ozdemir, Chad Sharp, Thomas Pornin, and Paul Grubbs, "Efficient proofs of possession for legacy signature,". IEEE Security and Privacy, 2025 |



<img align="right" height="50" src="https://raw.githubusercontent.com/eu-digital-identity-wallet/eudi-srv-web-issuing-eudiw-py/34015dc3c6f52529a99e673df1d4fa69d50f7ff5/app/static/ic-logo.svg"/><br/>

# Specification of common formats and API for Relying Party Registration information

## Abstract

The present document specifies the data formats and application programming interface (API) for the machine-readable Relying Party Registration required by the [European Digital Identity Regulation (EU 910/2014)](https://eur-lex.europa.eu/eli/reg/2014/910/oj/eng).

### [GitHub discussion](https://github.com/eu-digital-identity-wallet/eudi-doc-standards-and-technical-specifications/discussions/357)

## Versioning

| Version | Date        | Description                                               |
|---------|-------------|-----------------------------------------------------------|
| `0.1`   | 25.04.2025  | Initial version for first discussion                      |
| `0.2`   | 30.04.2025  | Initial version - fixed data model figure                 |

## 1. Introduction and Overview

The present document specifies the common data formats and the application programming interface (API) related to **Relying Party Registration** according to [**European Digital Identity Regulation (EU 910/2014)**](https://eur-lex.europa.eu/eli/reg/2014/910/oj/eng) ("[Regulation]"). and the Commission Implementing Regulation
(CIR) [**EU 2025/TBA**](https://eur-lex.europa.eu/eli/reg_impl/2025/TBA/oj) of 21 May 2025 on laying down rules for the application of Regulation (EU) No 910/2014 of the European Parliament and of the Council as regards the registration of wallet-relying parties ("[CIR for Relying Party Registration]").

Relying Party Registration is addressed in Article 5b (11) of the Regulation and the [CIR for Relying Party Registration] lays down further details, which are in scope of present technical document.

Specifically on [**CIR for Relying Party Registration**]:

In the recitals, recital (3) states:
*To ensure broad access to the registers and to achieve interoperability, Member States should set up both human and machine-readable interfaces that meet the technical specifications set out in this Regulation. Providers of wallet-relying party access certificates and wallet-relying party registration certificates, where available, should, for the purpose of issuing those certificates, also be able to rely upon these interfaces.*

For the purposes of defining the technical specification, the [CIR for Relying Party Registration] sets specific ruling for:
1. The minimum common data set: The registration of a Relying Party to a registry shall include at least the information set out in Annex I of the [CIR for Relying Party Registration] - see Art. 3(2) and the technical specification [Common Set of Relying Party Information to be Registered](**TS6 public link TBA**)
2. Online access to the registry information: The data shall be made available online both in human-readable form and in a form suitable for automated processing - see Art. 3(4).
3. Information shall be available through a single common API - see Art. 3(5).
4. Common requirements of [CIR for Relying Party Registration] Annex II Section 2 shall be complied with - see Art 3(6).
5. Annex II Sections 1 and 2 define the data format, signing and API requirements:
    - a REST API published according to OpenAPI version 3,
    - serving data out in JSON format,
    - the output JSON data is signed according to IETF 7515 on JSON Web Signatures (JWS),
    - provide open access,
    - provide API methods for **search and request lists of wallet-relying parties** based on following query parameters: official or business registration number, company name, privacy policy URL, entitlements (including sub-entitlements if defined by a Member State), and wallet-relying party reliance on intermediary and by an associated intermediary where applicable.
    - where query results match at least one wallet-relying party, response shall provide statement information of these wallet relying parties, including information registered according to [CIR for Relying Party Registration] Annex I and full wallet-relying party access certificate (and registration certificate, if applicable) histories, but shall exclude physical address of the registration information of [CIR for Relying Party Registration] Annex I (4).

## 2. Data Model

The data model and common format for Relying Party Registration is derived from the [CIR for Relying Party Registration], the [Common Set of Relying Party Information to be Registered](**TS6 public link TBA**) technical specification and the [Provider information specification],
while keeping the [SEMIC Style Guide](https://semiceu.github.io/style-guide/1.0.0/index.html) in mind and aligning it with the [SEMIC Core Business Vocabulary](https://semiceu.github.io/Core-Business-Vocabulary/releases/2.2.0/) as much as reasonable.

> NOTE: The data model for Relying Party Registration data depends on the [Provider information specification] data model, to which it carries a few superclass dependencies as referenced in this section.

![WRP-Reg-DataModel](img/ts5-wrpreg-datamodel.svg)

As outlined in the figure, the data model contains the main class **WalletRelyingParty**, which has class dependencies to superclasses **LegalEntity** and **Provider** specified in [Provider information specification].

The main class of the data model is **WalletRelyingParty**, which
* contains the attributes listed in Section 2.1
* as a class inherits attributes of **Provider** and **LegalEntity** superclasses from the [Provider information specification].
* defines its own **auxiliary classes**:
  * **Claim**
  * **Credential**
  * **IntendedUse**
  * **TransactionData**
  * **Intermediary**

* depends on following auxiliary classes of the [Provider information specification]:
  *
  * **Identifier**
  * **Law**
  * **Policy**
  * **LegalPerson**


### 2.1 WalletRelyingParty

The ``WalletRelyingParty`` main class inherits all attributes from the ``Provider``
superclass specified in the [Provider information specification]. In addition to the attributes of the ``Provider`` class it contains the attributes specified in the following table:

| Attribute              | Multiplicity | Type                                   | Description     |
|------------------------|--------------|----------------------------------------|-----------------|
| `tradeName`            | [0..1]       | *string*                               | may be present in order to specify the **trade name** (common name, service name) of the Wallet-Relying Party, if applicable.           |
| `supportURI`           | [0..1]       | *string*                               | specifies the **support URI** for the service provided by the Wallet-Relying Party, if applicable. Note that Annex I (7) of [CIR for Relying Party Registration](https://TBA) stipulates that the Wallet-Relying Party shall provide detailed contact information in form of (a) a website for helpdesk and support, (b) a phone number or (c) an e-mail address pertaining to its registration and intended use of the Wallet Units. |
| `srvDescription`       | [1..1]       | *string*                               | contains a **description of the service** provided by the Wallet-Relying Party.                              |
| `intendedUse`          | [0..*]       | [*IntendedUse*](#243-intendeduse)      | may appear one or more times in order to specify intended use cases in which the Wallet-Relying Party intends to rely on attestations of attributes of a Wallet User presented by a Wallet Unit. `IntendedUse` is **not required** from Wallet-Relying Parties that register only to act as an Intermediary.                                    |
| `isPSB`                | [1..1]       | *boolean*                              | indicates whether the Wallet-Relying Party **is a public sector body** or not.                         |
| `entitlement`          | [1..*]       | *string*                               | specifies the **set of entitlements** of the Wallet-Relying Party in form of a URI according to [RFC3986](https://www.rfc-editor.org/rfc/rfc3986.html), whereas the following URIs are defined in the present document: <ul><li> http://data.europa.eu/eudi/entitlement/Service_Provider</li> <li> http://data.europa.eu/eudi/entitlement/QEAA_Provider</li><li> http://data.europa.eu/eudi/entitlement/Non_Q_EAA_Provider</li><li> http://data.europa.eu/eudi/entitlement/PUB_EAA_Provider</li><li> http://data.europa.eu/eudi/entitlement/PID_Provider</li><li> http://data.europa.eu/eudi/entitlement/QCert_for_ESeal_Provider</li><li> http://data.europa.eu/eudi/entitlement/QCert_for_ESig_Provider</li><li> http://data.europa.eu/eudi/entitlement/rQSealCDs_Provider</li><li> http://data.europa.eu/eudi/entitlement/rQSigCDs_Provider</li><li> http://data.europa.eu/eudi/entitlement/ESig_ESeal_Creation_Provider</li></ul>     |
| `providesAttestations` | [0..*]       | [*Credential*](#244-credential)        | specifies the **set of sub-entitlements** of the Wallet-Relying Party (See [CIR for Relying Party Registration] Annex I (13)). Shall be present only if any `entitlement` of the Wallet-Relying Party is of type QEAA_Provider, Non_Q_EAA_Provider, PUB_EAA_Provider or PID_Provider, listing the attestation type(s) (`Credential`) the Wallet-Relying Party intends to issue to Wallet Units.     |
| `supervisoryAuthority` | [1..1]       | [*LegalEntity*](**link in provider specification TBA**) | specifies the competent **data protection supervisory authority** according to Article 51 of [(EU) 2016/679](http://data.europa.eu/eli/reg/2016/679/oj) in charge of supervising the Wallet-Relying Party. It provides the necessary contact information towards the Data Protection Authority through its `email`, `phone` and/or `infoURI` attributes, of which at least one SHALL be provided for an DPA registered into a Member State Registry.         |
| `usesIntermediary`     | [0..*]       | [*Intermediary*](#245)                 | if present, indicates **whether the Wallet-Relying Party depends on use of at least one Intermediary** and lists the needed information (unique Identifier and trade name) of the **Intermediaries** the registered Wallet-Relying Party depends on.               |
| `isIntermediary`       | [1..1]       | *boolean*                              | indicates whether the Wallet-Relying Party is registered to act on-behalf of End-Relying Parties (is an **Intermediary**) or not. Attribute SHALL be set to FALSE if `usesIntermediary` attribute is present. |

> Note: Topic M (User reporting unlawful or suspicious request of data to Data Protection Authorities) of the ARF adds the contact information of intended-use responsible DPA to the set of data to be registered by the Wallet-Relying Party. This information is available as OneOf[supervisoryAuthority.email, supervisoryAuthority.phone, supervisoryAuthority.infoURI] if the same DPA is valid for all intended uses of the Wallet-Relying Party.

### 2.2 Provider

The ``Provider`` superclass inherits all attributes from the more general ``LegalEntity`` superclass specified in the [Provider information specification]. WalletRelyingParty class inherits all attributes of this class.

### 2.3 LegalEntity

The ``LegalEntity`` superclass contains the attributes specified in [Provider information specification]. WalletRelyingParty class inherits all attributes of this class.

### 2.4 Auxiliary Classes

The WalletRelyingParty class has attributes that depend on a set of its own auxiliary classes (in addition to ones defined in [Provider information specification] as listed in Section 2 above) as follows:

### 2.4.1 Claim
The ``Claim`` class is used within the definition of the [``Credential``](#244-credential) class to list required attributes within a requested attestation, and contains the following attributes:

| Attribute                 | Multiplicity | Type                   | Description                           |
|---------------------------|--------------|------------------------|---------------------------------------|
| `id`                      | [0..1]       | *string*               | Identifier of a particular claim. See [OpenID4VP] Section 6.3.            |
| `path`                    | [1..1]       | *string*               | a path pointer that specifies the path to a claim within the `Credential`. See [OpenID4VP] Sections 6.3. and 7. |
| `values`                  | [0..1]       | *string*               | An array of strings, integers or boolean values that specifies the expected values of the claim. See [OpenID4VP] Sections 6.3. and 6.4.1.                    |

### 2.4.2 Identifier
The ``Identifier`` class is used within the definition of the ``LegalEntity`` superclass and contains the attributes specified in the [Provider information specification].

#### 2.4.2.1 Unique Identifier for identification of Wallet-Relying Parties

The ARF Annex 2 high-level requirements on Relying Party Registration (**ToDo add final links**) require a Wallet Unit to be able to both identify the Wallet-Relying Party with an unique identifier and a trade name or service name of the said Relying Party, and in the optional case that Registrar issues Registration Certificates, allow association between the Access Certificate and the Registration Certificate of a Relying Party (or between an Intermediary and its End-Relying Party) based on this unique identifier.

The [CIR for Relying Party Registration] Annex I (2) lists seven alternative identifiers and a wild card option (3)(h) to be registrable for a Wallet-Relying Party, of which **at least one** should be provided when registering a Wallet-Relying Party to a Registrar.

For the purpose of standardising a single technical unique identifier available for use in the EUDI ecosystem, identifier of type **http://data.europa.eu/eudi/id/EUID - European unique identifier (EUID)** as defined in \[[CIR for BRIS\]](https://eur-lex.europa.eu/eli/reg_impl/2021/1042/oj) SHALL be used by default in registration of a Wallet-Relying Party to a Registrar.

The other alternate identifiers listed in [CIR for Relying Party Registration] Annex I (2) MAY be registered in addition to the default unique identifier.

> Note 1: The Annex I (3)(b) 'registration number as registered in national business register' is considered redundant with EUID (3)(g) - all Member State national business registries shall provide EUIDs for all registered legal entities in their registry for cross-border purposes.

> Note 2: The set of identifiers in [CIR for Relying Party Registration] Annex I indicates all Wallet-Relying Parties to be legal persons. Registration of natural persons as Wallet-Relying Parties (an option enabled in the [Regulation]) can be followed utilising the `LegalEntity` class of [Provider information specification].

#### 2.4.3 IntendedUse

The ``IntendedUse`` class is used within the definition of the [``WalletRelyingParty``](#21-walletrelyingparty) class to specify the required information when a Wallet-Relying Party is requesting data from a Wallet Unit - for legal reference see [CIR for Relying Party Registration] Annex I paragraphs (8), (9) and (10)).

The class contains the attributes specified in the following table:

| Attribute                 | Multiplicity | Type                   | Description                           |
|---------------------------|--------------|------------------------|---------------------------------------|
| `purpose`                 | [1..*]       | *string*               | specifies one or more **purposes** of the intended data processing according to Article 5 1. (b) of [(EU) 2016/679](https://eur-lex.europa.eu/eli/reg/2016/679/oj).            |
| `privacyPolicy`           | [1..1]       | [*Policy*](#247-policy) | specifies the privacy policy of the intended use. `Policy.type` SHALL be of type Privacy Statement.              |
| `scope`                   | [0..1]       | *string* | Wallet Units MAY support presentation requests from Wallet-Relying Parties using OAuth 2.0 scope values.        |
| `credential`              | [1..*]       | [*Credential*](#244-credential) | specifies the set of potentially **requestable attestations** which may be requested by the Wallet-Relying Party within the scope of the present intended use of data.      |
| `transactionData`         | [0..1]       | [*TransactionData*](#246-transactiondata) | if present, enables a binding between the Wallet User's authentication and the authorization to complete e.g. a payment transaction, or to sign document using QES (Qualified Electronic Signatures).       |


#### 2.4.4 Credential

The ``Credential`` class is used within the definition of the [``IntendedUse``](#243-intendeduse) class to specify the individual attestation specific information within a presentation request or upon issuance of the attestation.

| Attribute                 | Multiplicity | Type                   | Description                           |
|---------------------------|--------------|------------------------|---------------------------------------|
| `id`                      | [1..1]       | *string*               | Identifier of the attestation. See [OpenID4VP] Section 6.3.                |
| `format`                  | [1..1]       | *string*               | Specifies the format of the attestation. For valid values, see [OpenID4VP] Appendix B.  |
| `multiple`                | [0..1]       | *boolean*              | A boolean which indicates whether multiple Credentials can be returned for presentation request including this Credential. If omitted, the default value is false.  |
| `meta`                    | [0..1]       | *string*               | An object defining additional properties requested by the Verifier that apply to the metadata and validity data of the Credential. The properties of this object are defined per Credential Format.                    |
| `trusted_authorities`     | [0..1]       | *string*               | A non-empty array of objects that specifies expected authorities or trust frameworks that certify Attestation Providers, that the Wallet-Relying Party will accept. For structure and use of the object, see [OID4VP] Section 6.1.1. EUDI trust framework uses extensively Trusted Lists (TLs) as defined in ETSI 119 612, and objects of type 'etsi_tl' SHALL be used in objects when applicable Attestation Providers are managed via TLs.  |
| `require_cryptographic_holder_binding`   | [0..1] | *boolean*     | Indicates whether the Wallet-Relying Party requires a Cryptographic Holder Binding proof. See [OID4VP] Section 6.1.  |
| `claim`                   | [0..*]       | [*Claim*](#241-claim)  | A non-empty array of objects that specifies attributes in the requested attestation. See [OID4VP] Section 6.3   |
| `claim_sets`              | [0..*]       | *string* | A non-empty array containing arrays of identifiers for elements in claims that specifies which combinations of claims for the Credential are requested. The rules for selecting claims are defined in [OID4VP] Section 6.4.1.   |

> Note: In line with the data minimisation principle according to Article 5 1. (c) of [(EU) 2016/679](https://eur-lex.europa.eu/eli/reg/2016/679/oj) the Wallet-Relying Party may only request the minimum set of attestations (`Credentials`) and attributes (`Claims`) within those necessary for a specific intended use (described in `IntendedUse.purpose`).

#### 2.4.5 Intermediary

The ``Intermediary`` class is used within the definition of the [``WalletRelyingParty``](#21-walletrelyingparty) class. It allows to specify the attributes necessary to be able to associate an End-Relying Party with its Intermediaries it depends on, and show the trade name or service name of the Intermediary for a Wallet User upon a presentation request. See [ARF Topic 52](https://github.com/eu-digital-identity-wallet/eudi-doc-architecture-and-reference-framework/blob/main/docs/annexes/annex-2/annex-2-high-level-requirements.md#a2352-topic-52-relying-party-intermediaries), high-level requirements RPI_01 and RPI_07.

Intermediaries are Wallet-Relying Parties with the ``WalletRelyingParty.isIntermediary`` attribute set TRUE. Validation of the registering Wallet-Relying Parties willing to act as an Intermediary is not specified in this specification.

| Attribute          | Multiplicity | Type                | Description           |
|--------------------|--------------|---------------------|-----------------------|
| `intermediaryIdentifier`     | [1..1]       | [*Identifier*](#242-identifier)       | SHALL be present in order to specify the **unique identifier** (See [Identifier](#242-identifier)) of an intermediating Wallet-Relying Party. The value SHALL be of type EUID and match with the ``WalletRelyingParty.identifier.identifier`` value of the Intermediary in question.              |
| `IntermediaryTradeName`      | [1..1]       | *string*                          | SHALL be present in order to be able to show the **trade name** of the Intermediating Wallet-Relying Party to a Wallet User. This value SHALL match with the ``WalletRelyingParty.tradeName`` value of the Intermediary in question.           |

#### 2.4.6 TransactionData

The ``TransactionData`` class is used within the definition of the [``IntendedUse``](#243-intendeduse) class. The object defined by the class is an array of strings, where `type` is the string that identifies the type of transaction data. each `credential_id` string references an attestation requested by the Wallet-Relying Party that can be used to authorise this transaction. The `transaction_details` contains any other type-specific parameters of the transaction. See [OID4VP] Section 8.4 for details.

| Attribute          | Multiplicity | Type                | Description           |
|--------------------|--------------|---------------------|-----------------------|
| `type` | [1..1] | *string* | String that identifies the type of transaction data, determining the parameters that can be included in the class object. The specific values of the type are not defined in this specification.  |
| `credential_ids` | [1..*] | *String* |  Array of strings, each referencing an attestation ([`Credential`](#244-credential)) requested by the Wallet-Relying Party that can be used to authorise the transaction. |
| `transactionDetails` | [0..1] | *string* | parameters specific to the `type` of the transaction |

#### 2.4.7 Policy (external)

The ``Policy`` class is used within the definition of the  [``IntendedUse``](#243-intendeduse)class. It contains the attributes specified in the [Provider information specification].

#### 2.4.8 LegalPerson (external)

The ``LegalPerson`` class is used within the definition of the ``LegalEntity``
class and allows to specify the attributes of a legal person. It contains the attributes specified in the [Provider information specification].

#### 2.4.9 Law (external)

The ``Law`` class is used within the definition of the ``LegalPerson`` class and contains the attributes specified in the [Provider information specification].


## 3 Common Application Programming Interface

### 3.1 API methods on registration and updating of Wallet-Relying Party data

The common Registry API write methods are defined for purposes of managing the register information of Member State Registrars, and SHALL be accessible by authorised users only.

**To be added.**

> Note 1: This section will list the OpenAPI methods necessary to write or update information on a Registry. The methods will be only accessible for authenticated and authorised API clients. The national mechanisms to implement authentication and authorisation are left for the discretion of the Member States. Requirement to provide secure-by-design and high-availability API is especially valid for the methods listed here.

> Note 2: Write methods TBA after Section 3.2 is final.

### 3.2 API methods for registrar queries (open API)

The Registry API's read methods SHALL be open for public access. The public API SHALL provide methods for searching and querying complete data sets of registered Wallet-Relying Parties matching with provided query parameters, that can be any of:
  * **official or business registration number** (see `WalletRelyingParty.Identifier`) - will return data of list of matching Wallet-Relying Parties
  * **official company name or trade name** (see `WalletRelyingParty.legalName` and `WalletRelyingParty.tradeName`) - will return data of list of matching Wallet-Relying Parties.
  * **URL of the Wallet-Relying Party's privacy policy** (see `WalletRelyingParty.policy`) - will return data of list of matching Wallet-Relying Parties.
  * **type of entitlement** (see `WalletRelyingParty.entitlement`) - will return data of list of Wallet-Relying Parties matching with queried entitlement type.
  * **type of attestations provided** (see `WalletRelyingParty.providesAttestations`) - - will return data of list of matching Wallet-Relying Parties that provide the queried attestation type.
  * **reliance upon an Intermediary** (see `WalletRelyingParty.usesIntermediary`) - will return data of list of matching Wallet-Relying Parties that have the attribute `WalletRelyingParty.usesIntermediary` present.
  * **official company name or trade name of an Intermediary** (see `WalletRelyingParty.isIntermediary`) - will return all Wallet-Relying Parties associated with queried Intermediary information through their `WalletRelyingParty.usesIntermediary` information present in the Registy.

where query results match at least one wallet-relying party, the method response SHALL provide
* set of information registered to matching Wallet-Relying Party (the full contents of `WalletRelyingParty` class for given instance without `WalletRelyingParty.physicalAddress` attribute), and
* full wallet-relying party access certificate (and registration certificate, if applicable) histories, as set available by respective Certificate Authorities for Access (or Registration, where applicable) Certificates, if the Registrar is not itself acting as the respective Certificate Authority.

> Note 1: It needs to be discussed if certificate histories have an existing data model used by Certificate Authorities. Anything that closely resembles the requirement in [CIR for Relying Party Registration] is provided by Certificate Transparency registers, use of which remains open in the ARF and Cooperation Group. Specifying a **Certificate log FORMAT for X.509 or other certificate types (RPACs and RPRCs) is not in scope of the Common Format and API specification**.

> Note 2: It needs to be discussed if more narrow responses are necessary outside the minimum required by Regulation, for e.g. online verification of registered intended use contents of a known Wallet-Relying Party by Wallet Units, if a Member State does not provide Relying Party Registration Certificates for the Wallet-Relying Parties.

The OpenAPI 3.0 compatible REST API methods for above are provided in Annex A.2

### 4 References

| Reference      | Description |
|----------------------------------------|----------------------------------------------|
| [Regulation] | [European Digital Identity Regulation (EU 910/2014)](https://eur-lex.europa.eu/eli/reg/2014/910/oj/eng)  |
| [CIR for Relying Party Registration]      | **Link TBA after May 9 2025**[]()  |
| [CIR for BRIS]  | [CIR (EU) 2021/1042 on technical specifications and procedures for the system of interconnection of registers](https://eur-lex.europa.eu/eli/reg_impl/2021/1042/oj)      |
| [Common Set of Relying Party Information to be Registered]    |       [The European Commission Technical Specification on Common Set of Relying Party Information to be Registered](https://github.com/eu-digital-identity-wallet/eudi-doc-standards-and-technical-specifications/blob/main/docs/technical-specifications/ts6-common-set-of-rp-information-to-be-registered.md)         |
| [Provider information specification]                            | [The European Commission Technical Specification of systems enabling the notification and subsequent publication of Provider information](https://github.com/eu-digital-identity-wallet/eudi-doc-standards-and-technical-specifications/blob/main/docs/technical-specifications/ts2-notification-publication-provider-information.md) |
| [Ref TBA]           | []()                                     |

## Annex A

### A.1 JSON-Schema (normative)

The file [``json-of-common-rp-model.json``](api/ts5-json-of-common-rp-data-model.json) contains the JSON-Schema definitions corresponding to the Data Model specified in [Section 2](#2-data-model) above. It is a Wallet-Relying Party Registration -specific subset of the full data model defined in [Provider information specification].

### A.2 OpenAPI Specifications (normative)

> Note: The [OpenAPI](https://spec.openapis.org/oas/latest.html) specification of the JSON and REST based application programming interfaces described in [Section 3](#3-common-application-programming-interface) will follow in a future revision of the present document.

<img align="right" height="50" src="https://raw.githubusercontent.com/eu-digital-identity-wallet/eudi-srv-web-issuing-eudiw-py/34015dc3c6f52529a99e673df1d4fa69d50f7ff5/app/static/ic-logo.svg"/><br/>

# Common Set of Relying Party Information to be Registered

## Abstract

The present document specifies the common data set required for Relying Party Registration as required by the [European Digital Identity Regulation (EU 2024/1183)](https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=celex%3A32024R1183).

### [GitHub discussion](https://github.com/eu-digital-identity-wallet/eudi-doc-standards-and-technical-specifications/discussions/358)

## Versioning

| Version | Date        | Description               |
|---------|-------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| `0.1`   | 25.04.2025  | Initial version for first discussion                      |


## 1. Introduction and Overview

The present document specifies the minimum common data set required from the Wallet-Relying Parties in **Relying Party Registration** according to [**European Digital Identity Regulation (EU 2024/1183)**](https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=celex%3A32024R1183) ("[Regulation]") and the Commission Implementing Regulation
(CIR) [**EU 2025/TBA**](https://eur-lex.europa.eu/eli/reg_impl/2025/TBA/oj) of 21 May 2025 on laying down rules for the application of Regulation (EU) No 910/2014 of the European Parliament and of the Council as regards the registration of wallet-relying parties ("[CIR for Relying Party Registration]").

Relying Party Registration is addressed in Article 5b (11) of the Regulation and the [CIR for Relying Party Registration] lays down further details, which are in scope of present technical document: The registration of a Relying Party to a registry shall include at least the information set out in Annex I of the [CIR for Relying Party Registration] (see Art. 3(2)).

## 2 Common Data Set

### 2.1 Mandatory Data Set in Registration

This section provides a table of minimum set of attributes, that SHALL be provided in Wallet-Relying Party registration based on ruling of [CIR for Relying Party Registration] Annex I.

For guidance on the data format of each information attribute, the table rows contain a reference to the corresponding class and attribute [class.element] definition specified in [Common formats and API specification] and [Provider information specification], whichever applies.

The Description row in the table contains clarifications regarding use of mandatory attributes with various Wallet-Relying Party types (entitlements and provided attestations ('sub-entitlements' in ).

| Data Identifier             |  Description            | Class reference     |
|-----------------------------|-------------------------|---------------------|
| Legal Name        | Name of the Wallet-Relying Party in an official record.   | WalletRelyingParty.legalName |
| Trade Name | A user-friendly name (trade name or service name) of the Wallet-Relying Party. SHALL be used as name of the entity if Legal Name is not applicable.   |   WalletRelyingParty.tradeName |
| Identifier  | Official identifier of the entity. **If several are registered to the Registry, at least one Identifier SHALL be of type 'EUID'** (see \[[CIR for BRIS\]](https://eur-lex.europa.eu/eli/reg_impl/2021/1042/oj)) for availability of an unique identifier of the Wallet-Relying Party for technical purposes.   |    WalletRelyingParty.Identifier    |
| Physical Address  | The postal address where the Wallet-Relying Party is established SHALL be provided for the Registrar.  | WalletRelyingParty.postalAddress | WalletRelyingParty.postalAddress     |
|  Contact Information    | a Wallet-relying Party SHALL provide detailed contact information pertaining to its registration and intended use of the wallet units in form of **at least one of** (a) a website for helpdesk and support, (b) a phone number or (c) an e-mail address.    |   WalletRelyingParty.supportURI  WalletRelyingParty.phone  WalletRelyingParty.email   |
| Service Description   |    A description of the service the wallet-relying party provides.   |  WalletRelyingParty.srvDescription      |
| Public Sector Body    | An indication whether the Wallet-Relying Party is a public sector body.  | WalletRelyingParty.isPSB      |
| Entitlements  |  The entitlement(s) of the Wallet-Relying Party. Possible entitlement types are ‘Service_Provider’, ‘QEAA_Provider’, ‘Non_Q_EAA_Provider’, ‘PUB_EAA_Provider’, ‘PID_Provider’, ‘QCert_for_ESeal_Provider’, ‘QCert_for_ESig_Provider’, ‘rQSigCDs_Provider’, ‘rQSealCDs_Provider’ or ‘ESig_ESeal_Creation_Provider’.  | WalletRelyingParty.entitlement |
| Purpose | A description of intended use of the data that the wallet-relying party intends to request from wallet units. **Provided for each intended use.**    |    WalletRelyingParty.IntendedUse.purpose       |
| Data Requested    | Provided the Wallet-Relying Party intends to request data from the Wallet Unit for its intended use, the attestations and attributes intends to request. Provided from the registry in a machine readable format that provides the attestation and attribute names & types. **Provided for each intended use.**   |  WalletRelyingParty.IntendedUse.Credential    |
| Data Protection Authority | The competent data protection supervisory authority supervising the Wallet-Relying Party and its intended uses. The national Registry SHALL arrange access to the national DPA(s)s with their Contact Information in the mechanism offered for registering Wallet-Relying Parties. **Provided for each intended use of the Wallet-Relying Party.** | WalletRelyingParty.supervisoryAuthority |

## 2.2 Optional Data to be Provided in Registration

This section provides a table of attributes, that MAY be provided in wallet-relying party registration based on ruling of [CIR for Relying Party Registration] Annex I. For guidance on the data format of each information attribute, the table rows contain a pointer to the corresponding class and attribute [class.element] definition specified in [Common formats and API specification] and [Provider information specification].

The table contains clarifications regarding use of the data attributes when the End-Relying Parties have attestation provider entitlement(s) or are as service providers relying on the option of using an Intermediary (a Wallet-Relying Party registered to operate as an Intermediary) when transacting with the EUDI wallets.

| Data Identifier             |  Description            | Class reference     |
|-----------------------------|-------------------------|---------------------|
| infoURI  | At least one uniform resource identifier (‘URI’) belonging to the wallet-relying party with web page(s) for information about the entity, if applicable. | WalletRelyingParty.infoURI   |
| Identifier  | Alternate identifiers of the entity than the type 'EUID' Identifier (See [Mandatory Data Set in Registration](#21)).  |    WalletRelyingParty.Identifier    |
| Use of Intermediary   | List of Intermediaries the Wallet-Relying Party with entitlement type 'Service_provider' relies upon, if it is not transacting directly with the Wallet Units. When present,Intermediary-specific data object SHALL contain its unique identifier of type 'EUID' and its Trade name.   | WalletRelyingParty.usesIntermediary  |
| isIntermediary | An indicator flag that SHALL be present if the registering Wallet-Relying Party intends to act as an Intermediary for other (End-) Wallet-Relying Parties. *Note: If the same Wallet-Relying Party provides a service which requires presentation of attestations, it SHALL register this service as a separate registration instance, with appropriate data on its intended use(s).*    | WalletRelyingParty.isIntermediary
| providesAttestations | A list of attestations a Wallet-Relying Party intends to issue for Wallet Units. SHALL only be present if the entitlements of the Wallet-Relying Party are of type ‘QEAA_Provider’, ‘Non_Q_EAA_Provider’, ‘PUB_EAA_Provider’ or ‘PID_Provider’. | WalletRelyingParty.providesAttestations


## 4. References

| Reference      | Description |
|----------------------------------------|----------------------------------------------|
| [Regulation] | [European Digital Identity Regulation (EU 2024/1183)](https://eur-lex.europa.eu/legal-content/EN/TXT/?uri=celex%3A32024R1183)  |
| [CIR for Relying Party Registration]      | **Link TBA**[]()  |
| [CIR for BRIS]  | [CIR (EU) 2021/1042 on technical specifications and procedures for the system of interconnection of registers](https://eur-lex.europa.eu/eli/reg_impl/2021/1042/oj)      |
| [Provider information specification]      | [Specification of systems enabling the notification and subsequent publication of Provider information](https://github.com/eu-digital-identity-wallet/eudi-doc-standards-and-technical-specifications/blob/main/docs/technical-specifications/ts2-notification-publication-provider-information.md) |
| [Common formats and API specification]           | [Specification of common formats and API for Relying Party Registration information](https://github.com/eu-digital-identity-wallet/eudi-doc-standards-and-technical-specifications/blob/main/docs/technical-specifications/ts5-common-formats-and-api-for-rp-registration.md)                                     |
