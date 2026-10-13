# AfyaPlus AI Security Executive Brief

### Risks
The deployment of our AI Triage Path and Logistics Model Context Protocol (MCP) server introduces specific operational risks:
*   Data Interception Transit Leakage: Cleartext connection routing across medical hubs risks exposing protected diagnostics over open networks.
*   Context Model Injection and Tool Misuse: Malicious prompts feeding into model parameters could override system bounds, tricking the platform into leaking system parameters or dumping entire country supply inventories.
*   Unredacted Audit Logging Over-retention: Storing plaintext records, access tokens, or identity fields within log servers breaches statutory regulations.

### Mitigations
We have engineered automated defense layers directly embedded in the system execution workflow:
*   Strict Transit Guardrails: The deployment architecture uses `security_controls.py` to continuously assert active TLS layers on all non-local connections, dropping unencrypted text configurations.
*   Fail-Closed Environment Bootstrapping: System startup sequences strictly require parameters mapped via `security_controls.py` alongside configuration files like `secret_refs.yaml`. Missing configurations abort boot sequences immediately.
*   Pre-Execution Injection Block: The system intercepts queries using `security_controls.py` to match malicious instructions *before* they interface with an underlying AI model, dropping invalid commands with a clean HTTP 400 error.
*  Minimalist Logistics Mapping: The logistics MCP layer limits data surfaces to abstract metrics using an enforced lookup dictionary derived from `clinics_allowlist.json`, rejecting unmapped queries.
*   Redacted-then-Hashed Logs: Operational audit log scripts inside `security_controls.py` actively isolate inbound query data, substituting diagnostic text strings with one-way cryptographic hashes before committing values to storage files.

### Kenya DPA alignment
To ensure operational compliance with the Kenya Data Protection Act (KDPA) 2019, the architecture enforces systemic privacy pillars:
*   Structured Identity Inventories: The catalog defined in `data_inventory.json` systematically classifies every internal data tier.
*   Automated Lifecycle Erasure Sweeps: The system uses `compliance_engine.py` to consistently cycle older medical text records past standard windows while logging immutable deletion receipts to prove regular maintenance.
*  Statutory Basis Definitions: Every operational database mapping clearly flags regulatory context parameters under transparent labels, designating elements as "Legal Review Pending" to maintain standard operating boundaries.

### What we will not claim
*   We do not claim that this system is absolute. Security is a continuous operational practice rather than a static product baseline. The word unhackable does not apply to this architecture.
*   We do not claim to hold formal Kenyan Data Protection Office structural certification approvals; all regulatory configuration settings remain designated strictly as teaching fields while formal data officer assessments are pending.
*   We do not claim our automated scripts intercept advanced vector-space attacks; our platform targets structural patterns at the processing boundary.

### Financial Credit and Logistics Limits
The logistics tool strictly handles supply chain queries and provides contextual resource recommendations. The AI path does not hold operational permissions to authorize, distribute, or finalize financial credit lines, clinical transfers, or monetary commitments. It acts solely as an informational advisor to clinical personnel, leaving all resource spending authorizations to human operations management teams.
