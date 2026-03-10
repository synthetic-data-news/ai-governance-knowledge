# EU AI Act — High-Risk AI Classification (Annex III)

The EU AI Act defines a specific category of **high-risk AI systems** subject to strict governance, documentation, logging, and monitoring requirements before they can be placed on the EU market or put into service.

Understanding whether a system qualifies as high-risk is the **first compliance decision** any organization must make.

---

## What Makes a System "High-Risk"?

An AI system is high-risk under Annex III if it is used in one of the **eight regulated domains** listed below, and the system poses a significant risk to health, safety, or fundamental rights.

Additionally, AI systems that are themselves a **safety component** of a regulated product (under EU product safety legislation such as the Machinery Regulation, Medical Device Regulation, etc.) are automatically high-risk.

> **Important:** General-purpose AI models (GPAIs) are subject to separate transparency obligations and do not automatically fall under Annex III — but systems *built using* GPAIs may still qualify if they are deployed in a high-risk use case.

---

## The Eight High-Risk Domains (Annex III)

### 1. Biometric Identification and Categorisation

| Use Case | Examples |
|----------|---------|
| Remote biometric identification | Facial recognition in public spaces |
| Biometric verification | Identity confirmation at borders, checkpoints |
| Biometric categorisation | Inferring protected characteristics from biometric data |

**Compliance note:** Real-time remote biometric identification in public spaces by law enforcement is subject to additional restrictions beyond standard high-risk requirements.

---

### 2. Critical Infrastructure Management

| Use Case | Examples |
|----------|---------|
| Energy grid management | AI managing electricity supply and demand |
| Water and waste systems | Automated control of water treatment |
| Transportation infrastructure | AI-assisted traffic management, rail safety systems |
| Digital infrastructure | Automated cybersecurity threat response |

**Compliance note:** Disruption of these systems may affect large populations. Logging and human oversight requirements are particularly stringent.

---

### 3. Education and Vocational Training

| Use Case | Examples |
|----------|---------|
| Access decisions | AI-based admissions screening |
| Assessment | Automated exam scoring, proctoring systems |
| Monitoring | Tracking student engagement and performance |
| Career guidance | AI-driven vocational routing tools |

**Compliance note:** These systems affect educational access and opportunity, which are considered fundamental rights considerations.

---

### 4. Employment and Workforce Management

| Use Case | Examples |
|----------|---------|
| Recruitment | CV screening, candidate ranking tools |
| Hiring decisions | Automated interview scoring |
| Promotion and task allocation | Workforce management systems |
| Performance monitoring | Productivity tracking tools |

**Compliance note:** This is one of the most commercially active categories. Most AI-based HR tools deployed at scale qualify as high-risk.

---

### 5. Access to Essential Private and Public Services

| Use Case | Examples |
|----------|---------|
| Credit scoring | Automated creditworthiness assessment |
| Insurance risk | AI-based underwriting and pricing |
| Public benefits | Eligibility determination for social services |
| Emergency response prioritisation | Resource allocation systems |

**Compliance note:** Systems that influence financial access, housing, or social services qualify. This includes consumer-facing fintech applications.

---

### 6. Law Enforcement

| Use Case | Examples |
|----------|---------|
| Risk assessment | Recidivism prediction, criminal profiling |
| Evidence analysis | AI polygraph tools, behavioural analysis |
| Predictive policing | Crime likelihood mapping |
| Deepfake detection | Evidence authenticity analysis |

**Compliance note:** Strong fundamental rights implications. Human oversight requirements are especially prominent for law enforcement systems.

---

### 7. Migration, Asylum, and Border Control

| Use Case | Examples |
|----------|---------|
| Asylum screening | Risk assessment for asylum applications |
| Visa processing | Automated application review |
| Border surveillance | Behavioural analytics at border crossings |
| Document verification | AI-based identity document analysis |

**Compliance note:** Migration decisions carry significant humanitarian implications. These systems face close scrutiny from European Data Protection Board guidance.

---

### 8. Administration of Justice and Democratic Processes

| Use Case | Examples |
|----------|---------|
| Judicial support | Decision support tools for courts |
| Dispute resolution | AI-assisted legal outcome prediction |
| Election systems | AI tools influencing democratic participation |

**Compliance note:** This category is narrow but carries the highest reputational and legal risk. Any AI influencing judicial or electoral processes is high-risk by definition.

---

## Compliance Requirements for High-Risk Systems

Once a system is classified as high-risk, it must satisfy requirements across six areas:

| Requirement | Key Article | Summary |
|-------------|-------------|---------|
| Data governance | Article 10 | Training data must be representative, documented, and traceable |
| Technical documentation | Article 11 | System capabilities, limitations, and design must be documented |
| Record-keeping | Article 12 | Automatic logging of system operation |
| Transparency | Article 13 | Users must be informed they are interacting with a high-risk AI |
| Human oversight | Article 14 | Effective oversight mechanisms must be built in |
| Accuracy and robustness | Article 15 | Performance must be validated and monitored continuously |

---

## Log Retention (Article 19)

Deployers of high-risk systems must retain automatically generated logs for a minimum period sufficient to support regulatory review. Six months is the general minimum; sector-specific regulations (finance, healthcare) may require longer.

See: [article-19-log-retention.md](article-19-log-retention.md)

---

## Infrastructure Typically Required

A compliant high-risk AI deployment requires:

- **Artifact certification** — cryptographic provenance records for training datasets
- **Decision logging** — tamper-evident records of system outputs with model and policy version
- **Audit trail** — complete chain from dataset → model → decision
- **Human oversight controls** — intervention hooks and override documentation
- **Post-market monitoring** — ongoing performance and bias tracking

See: [schemas/decision-record.schema.json](../schemas/decision-record.schema.json)
See: [reference/ai-audit-architecture.md](../reference/ai-audit-architecture.md)

---

## Quick Self-Assessment

```
1. Does the system operate in one of the eight Annex III domains?
   → No → Likely not high-risk under Annex III (check GPAI rules)
   → Yes → Proceed

2. Does it make or materially influence decisions affecting individuals?
   → No → May be out of scope
   → Yes → High-risk — full compliance obligations apply

3. Is it embedded in a safety-critical regulated product?
   → Yes → High-risk regardless of domain
```

---

## Related Articles

- [Article 10 — Data Governance](article-10-data-governance.md)
- [Article 12 — Logging Requirements](article-12-ai-logging.md)
- [Article 19 — Log Retention](article-19-log-retention.md)

---

*Source: [SyntheticDataNews](https://syntheticdatanews.com)*

*Related reading: [EU AI Act Compliance Guide](https://syntheticdatanews.com/eu-ai-act/compliance-guide) | [EU AI Act Compliance Checklist](https://syntheticdatanews.com/eu-ai-act/compliance-checklist)*
