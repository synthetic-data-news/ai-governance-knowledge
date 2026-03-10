# Synthetic Data vs. Real Data — Regulatory Compliance Comparison

One of the most common questions in AI compliance programs is whether synthetic data can replace real personal data for training purposes — and what governance obligations survive or change when it does.

The short answer: **synthetic data reduces but does not eliminate compliance obligations.**

---

## Side-by-Side Comparison

| Dimension | Real Personal Data | Synthetic Data |
|-----------|-------------------|----------------|
| Personal data under GDPR | Yes, by definition | Generally no — if properly generated |
| Re-identification risk | Present | Reduced — but not zero |
| Data subject rights apply | Yes (access, erasure, portability) | Generally not — no real subjects |
| Lawful basis required | Yes (consent, contract, legitimate interest) | Not required for synthetic records themselves |
| Source data governance | Required | Required for the source data used to train the synthesizer |
| EU AI Act Article 10 documentation | Required | Required — synthetic data does not exempt from governance |
| Representativeness obligation | Required | Required — validation is more complex |
| Bias documentation | Required | Required — synthetic data can inherit and amplify source bias |
| Certification records | Recommended | Recommended — especially for high-risk AI |
| Audit trail | Required (high-risk AI) | Required (high-risk AI) — same obligation |

---

## What Synthetic Data Reduces

### 1. GDPR Exposure

Real personal data training sets are subject to full GDPR requirements:
- lawful basis for processing
- data minimisation
- subject access requests
- right to erasure (including from training sets)
- international transfer restrictions

Properly generated synthetic data contains no real personal records. This eliminates most GDPR obligations for the synthetic dataset itself — though the **source data used to train the synthesizer** remains subject to GDPR.

### 2. Re-identification Risk

Real data can expose individuals even in anonymised form. Synthetic data generated with proper privacy mechanisms (differential privacy, k-anonymity) significantly reduces this risk.

**However:** synthetic datasets can still leak information about their source data through:
- membership inference attacks
- attribute inference attacks
- nearest-neighbour distance ratio (NNDR) vulnerabilities

Quality validation should include membership inference resistance testing.

### 3. Data Subject Rights Complexity

With real data, organisations must implement processes to locate and remove a specific individual's records from training sets — technically complex and operationally costly.

Synthetic data has no individual subjects to locate or remove.

---

## What Synthetic Data Does NOT Eliminate

### EU AI Act Article 10 — Data Governance Still Applies

Article 10 requires documentation and governance for **all** training data used in high-risk AI systems, regardless of whether it is real or synthetic. The obligations include:

- dataset provenance documentation
- representativeness validation
- bias analysis and mitigation documentation
- error minimisation procedures

A synthetic dataset used in a high-risk AI system must satisfy all Article 10 requirements. The documentation burden may be simpler (no subject rights, no data sharing agreements), but the governance obligation remains.

### Representativeness — Harder, Not Easier

Article 10 requires that training data be *representative* of the real-world population the system will encounter. For synthetic data, this requires:

- validation that the synthetic distribution matches the target distribution
- distributional fidelity metrics (KL divergence, Wasserstein distance, TSTR/TRTS)
- explicit documentation of rare events and edge case coverage

In some cases, synthetic data is *harder* to validate for representativeness than real data, because the synthesis process may smooth out or miss important distribution tails.

### Decision Logging — No Change

Article 12 logging requirements apply to the AI system's **operation**, not its training data. Whether a model was trained on real or synthetic data, all high-risk AI decisions must be automatically logged.

---

## Synthetic Data Certification and Article 10

Certification creates the immutable provenance record Article 10 implicitly requires. A certified synthetic dataset provides:

- cryptographic proof of the dataset's content (SHA-256 hash)
- generation metadata (algorithm, parameters, privacy mechanism)
- issuance timestamp
- verifiable signature

This is the closest equivalent to a data lineage record for synthetic training data.

See: [schemas/artifact-certificate.schema.json](../schemas/artifact-certificate.schema.json)

---

## Common Misconceptions

| Misconception | Reality |
|---------------|---------|
| "Synthetic data is GDPR-exempt" | Source data processing still requires lawful basis |
| "Synthetic data removes Article 10 obligations" | Governance documentation still required |
| "Synthetic data can't be biased" | Bias in source data transfers to synthetic data |
| "Differential privacy makes synthetic data safe" | DP reduces leakage; validation still required |
| "Certification replaces governance" | Certification attests to integrity; governance is the process |

---

## Decision Framework

```
Using synthetic data for high-risk AI training?

→ Source data (used to train synthesizer):
   Apply full GDPR and data governance controls

→ Synthetic dataset (used to train AI model):
   No individual subjects — reduced GDPR burden
   Article 10 documentation still required
   Certification recommended for audit trail
   Representativeness validation required
   Bias analysis required

→ AI system operation:
   Article 12 logging required (regardless of training data type)
   Article 19 retention required
```

---

## Summary

Synthetic data is a powerful tool for reducing GDPR exposure and simplifying data access for AI development. It is not a compliance bypass. The EU AI Act's governance, documentation, and logging requirements apply to high-risk AI systems regardless of whether training data is real or synthetic.

Used correctly — with proper validation, bias analysis, and certification — synthetic data can make EU AI Act compliance *more tractable*, not less.

---

*Source: [SyntheticDataNews](https://syntheticdatanews.com)*

*Related reading: [Synthetic Data Governance](https://syntheticdatanews.com/synthetic-data/governance) | [Synthetic Data Certification](https://syntheticdatanews.com/synthetic-data/certification) | [EU AI Act Article 10](https://syntheticdatanews.com/eu-ai-act/compliance-guide)*
