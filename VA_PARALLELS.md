# VA Parallels (Context Notes)

These notes link the StegGhost work to earlier experiences in VA infrastructure
work that helped shape the "Ghost Credential" concept.

## Observed Pattern at VA

- Windows machines joined to a domain with PIV-based auth.
- Local login disabled by policy; all access required domain trust.
- Machines periodically fell off the network / domain, often attributed to
  time/clock mismatches.
- Once off-domain:
  - Local troubleshooting was constrained by policy.
  - AD repair was discouraged.
  - Reimaging and redeployment was the standard response.

## Why It Matters

- This created a blind spot: machines that were actively in use one day became
  effectively "dead" the next, with limited ability to inspect what had
  happened in between.
- The combination of:
  - strict central policy,
  - fragile trust conditions (time, domain membership),
  - and reimaging as the default resolution
  could, in theory, mask deeper misuse if someone understood how to trigger
  those conditions deliberately.

## Conceptual Connection

The StegGhost sandbox does not recreate VA systems, but it explores a conceptually
similar pattern in a different domain (GitHub tokens):

- Legacy PATs act like "ghost credentials": valid identities, misaligned with
  current orgs.
- They can authenticate but have unclear or restricted capabilities.
- Without careful logging and analysis, this behavior is easy to misinterpret.

Understanding and documenting this pattern in a safe, controlled environment
may help design better defenses for future systems, including those that
serve vulnerable populations.
