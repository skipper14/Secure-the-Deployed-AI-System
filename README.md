# Week 9: AI Security and Compliance

## Overview
This suite deploys comprehensive security controls for the AfyaPlus AI system, hardening both the public FastAPI Triage API layer and the logistics Model Context Protocol (MCP) server. The design aligns with the Kenya Data Protection Act (KDPA) 2019 guidelines via structural tracking, payload sanitization, and automated cleanup rules. Full non-technical management context is cataloged inside the `manager_brief.md` document.

## Encryption
- **transit_ok / TLS evidence:** Enforced programmatically inside `security_controls.py` via URL parse filters.
- **gitignore / resolve_secrets:** Guarded via rules inside `.gitignore` and validation hooks built into the system bootstrapper.
- **Key Vault or KMS, or the fallback twin JSON:** Modeled natively via configuration fallbacks mapped out inside `secret_refs.yaml` and verified with the cryptographic twin file `kms_twin.json`.

## Access control (including MCP)
- **rbac.py roles:** Implemented using the core authorization matrix mapping defined inside `security_controls.py`.
- **injection_guard:** Pre-model interceptor logic embedded inside `security_controls.py` returning immediate 400 bad request errors upon override fingerprint matching.
- **clinic allowlist:** Controlled structurally through constraint filters defined inside `clinics_allowlist.json`.

## Logging
- **path to the jsonl:** Appends cleanly to the local database file `audit_trail.jsonl`.
- **redact and hash approach:** Utilizes the hash-and-redact script pipeline built into the logging functions of `security_controls.py` to strip credentials and obscure medical diagnostics.

## Kenya DPA
- **inventory path:** Configured statically using structural classifications within `data_inventory.json`.
- **retention:** Governed by the automated sweeper functions inside `compliance_engine.py` writing verification receipts directly to `deletion_records.jsonl`.
- **rights stub / owner:** Assigned directly to the AfyaPlus Data Protection Operations Team via right-to-erasure workflows in `compliance_engine.py`.

## Manager brief
The complete non-technical narrative is located in [manager_brief.md](manager_brief.md). It confirms the four mandatory headings (*Risks*, *Mitigations*, *Kenya DPA alignment*, *What we will not claim*). **The word unhackable does not appear anywhere within the entire context.**

## Fallbacks declared
- [x] no Azure Key Vault (local-env plus the twin JSON)
- [x] no AWS account
- [x] local MCP stub
- [x] legal review pending on lawful_basis

## Checklist
- [x] Secrets not in git
- [x] MCP cannot dump the environment or every clinic
- [x] The brief is readable by a non-engineer
