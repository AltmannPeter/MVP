# Digital Identity Wallet MVP – Technical Questions and Considerations

TLDR; Look at the MVP Valid Configuration examples and see if they match the user requirements that emerge during the discussion; it not, try finding another configuration that is minimally complex using the two DSMs and trade-off table.

## Introduction

This document outlines core technical questions and answers shaping the Minimum Viable Product (MVP), with a focus on technical feasibility. Determining what is technically possible is challenging given the evolving regulatory landscape, limited real-world trials, and a shifting final design target. The goal here is to identify key design choices and examine their implications and trade-offs.

The MVP is viewed as a configuration of multiple solution component options across distinct solution categories. The challenge is to identify configurations likely to become the dominant EUDIW solution design. This analysis complements legal and user experience perspectives by providing a structured assessment of technical feasibility and complexity. Technically, the MVP should be implemented in the simplest practical form that meets requirements and enables incremental enhancement as the foundation and technology mature.

To illustrate complexity drivers, the next section presents challenging problems with example implementation approaches. The document then identifies core root design properties and examines their dependencies. This mapping supports the identification of technically feasible configurations from which legally compliant and user-friendly solutions can be selected. The results are summarized in a Design Structure Matrix and a trade-off table. To further support solution development, the core properties and trade-off table are used to derive two valid MVP configurations. These can then guide  frequently asked design questions that shape the EUDIW solution.

## Complexity Drivers and Propagation

This section illustrates key complexity drivers and and how complexity can propagate.

### Architecture and Hardware (platform-level complexity)

* **Example 1: Smartphone-only EUDIW solution**  
  Moving all LoA H functions to a BYO smartphone is complex due to certification requirements. This also complicates other areas, e.g., recovery. Certifying an HSM based solution is simpler.

* **Example 2: Rely on PKCS#11-compatible HSMs**  
  Use standard HSM interfaces to avoid low-level integration and custom firmware requirements.

### Features and Scope (functional and operational complexity)

* **Example 1: Online-only operation**  
  Offline presentation proposals lack standardization and broad agreement; limit offline support to what the reference implementation provides.

* **Example 2: Recovery and backup**  
  Custom recovery mechanisms, like secret sharing, are possible but too complex for an MVP. Easiest option is to use re-onboarding. Optionally offer backup of minimal metadata (e.g., identity subject identifier and list of verifier services consumed) for smoother recovery.
  
* **Example 3: Usage data**  
  Rely on device-reported usage data. If possible to organize data aggregators, we can use private sum-based approaches. If data aggregators are not possible, devices can report usage data to wallet providers using a single-show PID without attributes.

### Cryptographic Profile (protocol and privacy-layer complexity)

* **Example 1: Simple privacy solutions**  
  Avoid advanced signature schemes and ZKP "layering". Focus on issuance using attestation format native solutions until standards mature.

* **Example 2: Avoid privacy threats by design**  
  Avoid correlation handles where possible. For example, use short-lived attestations instead of ZKP of non-revocation.

* **Example 3: Predicate support**  
  Boolean predicates are simple, e.g., `"age_over_18": True`, but require short-lived attestations.


Note how design choices in one domain often affect complexity in others. For example, using short-lived attestations eliminates revocation complexity and makes advanced predicates (e.g., ZKPs, hash-based proofs) largely unnecessary since static attributes (like age) remain valid for the attestation’s lifespan. Avoiding complex predicates further reduces issuer and verifier complexity. 

For the MVP, it’s critical to identify *symmetric couplings*—where complexity increases or decreases across domains simultaneously—and to watch for *asymmetric couplings*, where reducing complexity in one area increases it elsewhere. Tools like Design Structure Matrix (DSM) and trade-off tables can help visualize how root design properties (such as attestation lifespan) shape system-wide complexity patterns. To this end, we first have to identify root design properties. The DSM and trade-off table can then be used to analyze dependencies and help converge on a coherent MVP design. The following sections are structured to support this process.

## Root design properties

Root design properties define key solution decisions and are often the source of cascading dependencies. Once set, they constrain the solution space and shape design choices across multiple domains. An EUDIW solution can be seen as a specific configuration of these root properties. Some configurations introduce unnecessary complexity, while others may be invalid or impractical.

The root technical properties identified so far include:

1. Attestation format: mDL, and SD-JWT VC. No linked-data attestations.
2. Attestation lifespan: real-time (<10 minutes), short-lived (<24h), long-lived.
3. Binding model: bound to user, bound to device, both; bound to multiple devices.
4. Key management model: device-held, cloud-held, or hybrid.
5. Key lifecycle: static, rotating, interaction-bound, usage-bound.
6. Predicates and proof model: boolean claims, non-ZKP range-proofs, IZKP-based.
7. Validity status checks: none, list-based, OCSP-like, (ZKP) accumulators.
8. Recovery model: re-onboarding, multi-party recovery.
9. Hardware root of trust: eSIM, HSM, smartphone secure area, or combination.
10. Unlinkability guarantee: per-verifier, per-presentation.
11. Disclosure model: issue requested attributes only, static salted attribute digests, dynamic predicates. All-or-nothing, a subset, or progressive.
12. Online-only vs offline support: always-online, online verifier, locally cached, fully offline.

There are of course additional non-technical properties, such as:

13. Issuer trust model: trusted list, federation, or mixture of both.
14. Verifier trust model: trusted list, federation, or mixture of both.
15. Metadata and schema trust model: static schema references, or dynamic discovery.
16. Usage data: none, opt-in/out, single aggregator, multiple aggregators.
17. Consent model: implicit, explicit per use, transaction specific, global.
18. Audit logs and wallet content: user visible, provider visible, third party visible.
19. Performance targets: latency, throughput, resource constraints, scalability, concurrent users etc.
20. Resilience model: soft/hard-failure, degraded operations, HSM unavailability
21. Protocol and transport stack: OID4VC, 18013-5/7. HTTPS, BLE, NFC.
22. Extensibility: plugin support, modularity, update channels.
23. Interoperability: none, core only, full. Conformance tests, interoperability.
24. Certification: smart-phone, HSM, hardware component (e.g., eSIM).

## Design Structure Matrix (DSM)

The DSM maps interactions between core properties to highlight key drivers and dependencies. It focuses on properties with meaningful interdependencies and cascading effects on system complexity. Properties like attestation type, or certification scope act largely as independent or regulatory choices and may only be mentioned briefly here to then be further addressed in the trade-off analysis. Consequently, not all properties will be treated below. Those that are omitted are either 1) externally fixed or mandated (e.g., certification and interoperability), 2) part of the MVP but have limited interdependencies (e.g., usage data, audit logs), or 3) are performance metrics.

Three DSMs are shown to illustrate various drivers and dependencies. Splitting the DSM reduces the cognitive load and avoids bloat due to "weak" or "none" dependencies. But splitting may also hide some dependencies. Consequently, the DSMs should be viewed as a part of a larger analysis. Herein, the DSMs are designed to illustrate *strong drivers* (rows with many strong labels), and *heavy dependents* (columns with many moderate/strong).

Note that a DSM does not provide an accurate picture of direction or dependencies in cases where both properties are downstream of another property not listed in the DSM. And in the case of a highly regulated context like the EUDIW, most dependencies are driven by external factors.

### DSM 1

| Driver ↓ / Affected →        | Lifespan (2) | Disclosure (11)  | Validity status (7) | Key mgmt / lifecycle (4,5) |
|------------------------------|--------------|---------------------|----------------------|------------------------------|
| Lifespan (2)                 | —            | strong              | strong               | moderate                     |
| Disclosure (11)           | moderate     | —                   | moderate             | weak                         |
| Validity status (7)         | strong       | moderate            | —                    | moderate                     |
| Key mgmt + lifecycle (4,5) | none         | weak                | moderate             | —                            |



**Lifespan** determines whether you need complex proofs or simpler boolean claims or even just the attributes requested by the verifier. Relatedly it impacts the cryptograhic requirements on unlinkability. Lifespan determines what kind of validity status mechanism you need. It also plays a role in key lifecycles as short lived attestations make key retirement easier but requires more keys. Lifespan reduces or amplifies recovery complexity but does not determine it solely. Finally, lifespan has limited impact on offline support; with real-time issuance not being possible to cache.

**Key management and lifecycle** partially constrains disclosure but does not determine it. It strongly impacts the hardware root of trust, and certification. It also strongly impacts the recovery model. The key lifecycle  impacts the requirements for validity status checks but is not its sole driver.

**Disclosure** can slightly relax the requirement of having short-lived attestations when cryptography can guarantee unlinkability. The unlinkability properties are strongly impacted by the disclosure approach, which also impacts the unlinkability guarantees of the validity status. Certain disclosure schemes require signature schemes that natively support them, which strongly impacts the hardware root of trust certification, and interoperability.

**Validity status** strongly impacts lifespan; without revocation, lifespan with explicit and short validity periods is required. The validity status check has certain unlinkability properties, which then determines the unlinkability property other components, like disclosure, maximally have to have. Advanced validity status checks impacts key management through the status check object, but is not its driver. It has a strong impact on online/offline support, and interoperability.

**Recovery** strongly impacts key management as different recovery options require very different key management approaches. It also has a major impact on interoperability and certification.

### DSM 2

| Driver ↓ / Affected →        | Binding model (3) | Hardware root of trust (9)  | Recovery (8)  | Key mgmt / lifecycle (4,5) |
|------------------------------|-------------------|-----------------------------|---------------|------------------------------|
| Binding model (3)           | —                | strong                     | strong        | strong                     |
| Hardware root of trust (9) | strong           | —                          | strong        | strong                     |
| Recovery (8)               | none            | none                      | —               | moderate                   |
| Key mgmt / lifecycle (4,5)| none            | none                      | strong          | —                          |

**Binding model** determines the requirement of a hardware root of trust. It also strongly impacts recovery and shapes how complex it must be, and fundamentally impacts the key management approach.

**Hardware root of trust** strongly determines with binding models are possible and fundamentally constrains recovery. Hardware also sets what key operations are possible.

**Recovery** can shape key management complexity if more advanced recovery options, like secret sharing, are required.

**Key management and lifecycle** constrain what recovery options are possible.

With dependencies mapped, we can better understand a trade-off table that illustrates simple and complex options.

### Trade-off Table

| Cluster / Driver               | Simple Option                                | Complex Option                                              |
|---------------------------------|---------------------------------------------|------------------------------------------------------------|
| Attestation lifespan (2)        | Short-lived (<24h)                          | Long-lived                   |
| Disclosure model (11)           | Boolean (e.g., `age_over_18`: `True`)       | Dynamic predicates |
| Validity status (7)             | No revocation, re-issuance                  | Lists, ZKP accumulators             |
| Key mgmt + lifecycle (4,5)      | Single-show HSM-protected key               | Fully unlinkable keys          |
| Binding model (3)               | Single HSM to which devices authenticate    | Cross-device key mgmt using multi-party computation                    |
| Hardware root of trust (9)      | Certified HSM                               | Certified devices / eSIM etc.                 |
| Recovery model (8)              | Re-onboarding, minimal metadata backup      | Multi-party recovery, secret sharing   |
| Unlinkability guarantee (10)    | Verifier single-show unlinkable             | Fully multi-show unlinkable |
| Online/offline support (12)     | Always-online                               | Verifier online   |

## Valid configurations

Valid configurations for the MVP can be identified using the DSMs and tradeoff table. Most properties should be selected from the "Simple Option" column. Where strong reason exist for including alternatives from the "Complex Option" column, it is helpful to consider the DSMs to understand the broader implication of those choices. Ideally, complex options should be limited to properties that have at most a moderate impact on few other properties (i.e., disclosure and recovery, optionally also key management as it only strongly determines recovery).

### MVP Configuration Example 1

* Attestation lifespan: short-lived
* Disclosure model: Boolean
* Validity status: explicit validity periods included in attestation with daily re-issuance
* Key management: HSM protected EUDIW keys, the user authenticates to HSM with a BYO mobile device
* Key lifecycle: freshly derived daily key
* Binding model: HSM PoP key with second factor from user device
* Hardware root of trust: HSM
* Recovery model: re-onboarding with optional verifier service metadata backup
* Unlinkability: single-show verifier unlinkable keys
* Offline support: online for daily refresh
* Usage data: report to wallet provider using anonymous PID

### MVP Configuration Example 2

Same as Configuration 1 but with the following changes:

* Disclosure model: Layer ZKP ontop of the attestation or as computational inputs
* Key lifecycle: key derivation with single-show keys

## Frequently Asked Questions

The DSMs and the trade-off table, together with the two valid configurations, can now guide answers to more general questions that can impact the user experience of the MVP. Possible questions to ask (or decide if they are blocking, mere design options, or even post-MVP considertion) for the MVP are grouped and listed below:

### Architecture and Platform

1. What is the core architecture?
3. How do we manage multi-tenancy at the HSM?
4. What secure hardware do we accept in the mobile devices?
5. How will the mobile device authenticate to the HSM?
6. Is it possible to rely solely on a standard HSM interface like PKCS#11 to avoid custom code? 
7. What local data will the mobile device store?
8. What does key management look like for single-use PoP keys?
9. Will the mobile device always require internet access?
10. Will we support multi-device usage? How?

### Credential and Key Lifecycle

10. What is the intended lifetime of keys? Will some keys be long term and others single-use?
11. How will validity status be managed?
12. How does the wallet automatically refresh attestations and credentials?
13. Will credential delegation be supported (e.g., from a parent to a child or business assistant)?
14. How will key compromise or device compromise be detected and handled?

### Attestation Types and Formats

15. Which formats will be supported?
16. Which selective disclosure mechanism will be supported?
17. How will we manage qualified electronic signatures (QES)?
18. Will the wallet support combined presentations?
19. What does WUA management look like?

### Protocols and Communication

20. Which issuance protocols will be implemented?
21. Which presentation protocols will be supported?
22. What transport mechanisms will be used?
23. Will verifier-initiated and holder-initiated flows both be supported?

### Privacy, User Control, and Threat Model

24. How will the system minimize correlatable identifiers across issuers and verifiers?
25. What data (if any) will the wallet provider or HSM operator be able to see or access?
26. How does the user control credential retention?
27. How does the solution show what data was shared and when?

### Usage Metrics and Statistics

28. How is usage statistics collected and aggregated?

### Failure and Recovery

29. What happens if the HSM is temporarily unavailable?
30. What recovery mechanisms will be supported if a user loses or replaces their mobile device?

### Security Controls

31. How will multi-factor authentication (MFA) be implemented on the mobile device with HSM, to satisfy LoA High, and what cryptographic mechanisms (e.g., threshold signatures, aPAKE) are under consideration?

### Software Updates and Storage

32. How will the wallet software be updated securely?
33. Will critical security patches be enforced or user-controlled?
34. Where will local metadata or non-cryptographic state be stored?

### Scalability and Testing

35. What is the expected number of concurrent users or transactions?
36. Are there load benchmarks or performance targets for the HSM and backend?

### General Scope and Priorities

37. What is explicitly out of scope for the MVP?
38. How will interoperability and compliance be tested before deployment?

### Roadmap and Process

39. What is the expected development and rollout timeline?
40. What is the plan for post-MVP iterations and feature expansion?


----


### Onboarding and first-use

41. What does discovery look like?
42. What setup guidance does the app provide?
43. How does the user know that the initial setup was correct?
44. What is the effort associated with the initial setup (e.g., scanning documents, PIN creation, enrolling biometrics, visiting physical service center)?
45. How does the user know that the wallet is legitimate?

### Daily use

46. How smoothly does the user expect to retrieve a specific attestation?
47. What constitutes an intuitive process?
48. What is the user involvement in selective disclosure?
49. What makes the user confident in that they shared exactly what they intended?
50. What makes the user confident in that they shared to whom they intended to share?

### Privacy and control

51. What details matter for event logs?
52. How is the event log presented (e.g., in app, downloaded report, external privacy dashboard)?
53. How is the right to be forgotten implemented?

### Recovery

54. If the user loses their mobile device, what is the ideal path to recover access?
55. What is an acceptable "loss" (metadata, attestation, contact list etc.) for the user?
56. What is an acceptable recovery effort?
57. What happens if the user changes their mobile device and wants to migrate?

### Authentication and MFA

58. What friction will the user tolerate (PIN, biometrics, one time code etc) for sensitive actions?
59. What error handling (e.g., retry option) exists to reduce user frustration?

### Accessibility

60. What offline features matter most (present existing attestation, prepare delegation of presentation request)?

### Multi-device use

61. How is the multi-device scenario managed?
62. How does the user access attestations from their desktop?


## FAQ answers table

Legend | E = Explicit answer | P = Partial / pending detail | N = No answer / out of scope



| # | FAQ topic (abridged) | Status (E / P / N) | Current coverage & residual gaps |
|---|----------------------|--------------------|----------------------------------|
| **Architecture & Platform** | | | |
| 1  | Core architecture (HSM‑centric) | **E** | All PoP & attestation keys on HSM; phone only authenticates via OPAQUE session. |
| 3  | HSM multi‑tenancy isolation | **N** | No policy for partitions, per‑tenant audit or key namespace. |
| 4  | Accepted phone secure hardware | **P** | Secure‑enclave assumed; certification level & OS baseline TBD. |
| 5  | Phone ↔ HSM authentication | **E** | OPAQUE with PIN‑hardened secret; server envelope counter for rate‑limit. Need transcript‑to‑PoP binding sketch. |
| 6  | PKCS#11‑only interface | **E** | Recommended to avoid custom firmware. |
| 7  | Local data storage & sync | **P** | User‑ID, local attestations, 1‑yr verifier list under HW‑backed key; sync model (device‑only vs. server‑assist) TBD; encryption & rollback counter unspecified. |
| 8  | Single‑use PoP key management | **P** | Daily‑derived keys; derivation tree & entropy source still open. |
| 9  | Always‑online requirement | **E** | Online daily refresh mandatory; offline postponed. |
| 10 | Multi‑device usage | **E** | Explicitly out of scope for MVP‑1. |
| **Credential & Key Lifecycle** | | | |
| 10L | Key lifetimes | **E** | Daily PoP rotation; 24 h attestation lifespan. |
| 11 | Validity‑status management | **E** | No revocation; freshness ≤ 24 h. Verifiers rely on secure‑time service; drift bound set per verifier. |
| 12 | Automated refresh scheduling | **N** | Job timing, retries, DoS handling not designed. |
| 13 | Delegation support | **N** | Absent. |
| 14 | Compromise detection & response | **N** | No telemetry, key‑revocation or anomaly triggers. |
| **Attestation Types & Formats** | | | |
| 15 | Supported formats | **E** | mDL and SD‑JWT VC; linked‑data VCs excluded. |
| 16 | Selective‑disclosure mechanism | **P** | Boolean claims (Cfg‑1) plus optional ZKP layer (Cfg‑2); SD‑JWT field layout pending. |
| 17 | Qualified electronic signatures | **N** | Not covered. |
| 18 | Combined presentations | **N** | Not defined. |
| 19 | WUA management | **N** | Term undefined. |
| **Protocols & Communication** | | | |
| 20 | Issuance protocol choice | **N** | Only candidate list. |
| 21 | Presentation protocols | **N** | Same. |
| 22 | Transport mechanisms | **N** | HTTPS/BLE/NFC listed, none selected. |
| 23 | Verifier‑ vs. holder‑initiated flows | **N** | Unspecified. |
| **Privacy & User Control** | | | |
| 24 | Minimising correlatable IDs | **P** | Single‑show keys; verifier list export leaks usage unless pseudonymised/encrypted. |
| 25 | Wallet‑provider / HSM visibility | **N** | Threat model for operator missing. |
| 26 | Credential retention control | **N** | Deletion & TTL policy absent. |
| 27 | User‑visible sharing proof | **N** | Event‑log UX not designed. |
| **Usage Metrics** | | | |
| 28 | Statistics collection pipeline | **P** | Device‑reported + optional aggregator concept; pipeline and consent flows not drafted. |
| **Failure & Recovery** | | | |
| 29 | HSM outage handling | **N** | No fail‑over or degraded‑mode plan. |
| 30 | Lost‑phone recovery | **E** | New device requires in‑person visit **or** remote LoA‑H (eID card). Flow & anti‑phishing pending. |
| 54 | Ideal recovery path | **E** | Same as #30. |
| 55 | Acceptable data loss | **N** | Undefined. |
| 56 | Acceptable recovery effort | **N** | Undefined. |
| 57 | Phone migration | **E** | Uses same process as lost‑phone recovery. |
| **Security Controls & MFA** | | | |
| 31 | MFA mechanism for LoA‑H | **P** | Possession (phone) + OPAQUE‑protected PIN; need second‑factor binding (biometric? OS unlock?) and LoA‑H evidence chain. |
| 58 | User‑acceptable friction | **N** | UX research not done. |
| 59 | Error handling / retries | **N** | Unspecified. |
| **Updates & Storage** | | | |
| 32 | Secure update channel | **N** | Not covered. |
| 33 | Patch‑enforcement policy | **N** | Not covered. |
| 34 | Local metadata storage rules | **N** | Encryption & tamper rules missing. |
| **Scalability & Testing** | | | |
| 35 | Concurrent‑user targets | **N** | Not defined. |
| 36 | HSM/backend benchmarks | **N** | Not defined. |
| **Scope & Priorities** | | | |
| 37 | Explicit out‑of‑scope list | **E** | Complex‑column items (offline predicates, multi‑party keys, multi‑device) excluded. |
| 38 | Interop & compliance testing | **N** | Not planned. |
| **Roadmap & Process** | | | |
| 39 | Development & rollout timeline | **N** | Absent. |
| 40 | Post‑MVP iteration plan | **N** | Absent. |
| **Onboarding & First‑Use** | | | |
| 41–45 | Discovery, setup flow, legitimacy checks | **N** | None drafted. |
| **Daily Use** | | | |
| 46–50 | Retrieval UX, disclosure UX, user assurance | **N** | None drafted. |
| **Privacy Event Logs** | | | |
| 51–53 | Log schema, presentation, right‑to‑erasure | **N** | Not covered. |
| **Accessibility & Offline Features** | | | |
| 60 | Offline features priority | **P** | Offline support deferred; specific accessibility features undefined. |
| **Multi‑device** | | | |
| 61 | Multi‑device scenario management | **E** | Declared out of scope. |
| 62 | Desktop access | **E** | Declared out of scope. |
