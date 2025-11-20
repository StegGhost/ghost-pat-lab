# Ghost Credential / Phantom Trust Threat Model

This document describes the "Ghost Credential" threat pattern that inspired the
StegGhost sandbox.

## Threat Pattern: Ghost Credential / Phantom Trust Break

**Definition:**

A long-lived or legacy credential, token, machine account, or trust object
whose state no longer aligns with its surrounding auth policy, causing opaque
failures that appear benign but can mask deeper issues.

### Symptoms

- Authentication succeeds (`200` responses, valid identity).
- Authorization fails or behaves unexpectedly (`403`, `404`, missing resources).
- Operational teams may attribute issues to:
  - "Time/clock problems"
  - "Old configuration"
  - "Just reimage / reset it"
- Pressure to repair deeply (e.g., AD buckets, token lineage) is low.
- Reimaging or rotation is used as a blunt instrument, erasing evidence.

### Risks

- Forensic blind spots in large organizations.
- Potential for malicious use of legacy auth objects.
- Misattribution of behavior ("it's just a glitch" instead of "this is a pattern").
- Difficulty correlating events across time and organizational changes.

### Defensive Principles

1. **Short-lived credentials and required rotation.**
2. **Explicit ownership for every token and machine account.**
3. **Independent forensic access paths** that do not depend on the same trust
   mechanism under investigation.
4. **Treat time/clock anomalies as security events**, not just noise.
5. **Strong logging** around token use, trust breaks, and domain membership.
6. **Policy that rejects ambiguous ghost states**, forcing explicit re-issuance.

The StegGhost sandbox exists to study this pattern in a controlled way and help
design systems that **detect and prevent** such ghost auth objects.
