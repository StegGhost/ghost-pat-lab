# StrangeAuth Origin Notes

These notes capture the origin of the "StrangeAuth" concept and why this
sandbox exists.

## Trigger

- A legacy GitHub Personal Access Token (PAT) was discovered which:
  - Was created **before** the current StegVerse-Labs org existed.
  - Authenticates successfully (`200` on `GET /user`).
  - Fails or behaves oddly when interacting with repos in the new org.

This mismatch between **successful identity auth** and **limited or blocked
capabilities** highlighted a "ghost credential" behavior:
a token that is valid as an identity, but no longer aligned with the modern
authorization world around it.

## Parallel to VA Experience

This pattern rhymed with earlier observations from VA infrastructure work:

- Windows machines were periodically removed from the network / domain due to
  time or clock issues.
- Local login was disabled by policy, making disconnected machines effectively
  opaque to on-site IT staff.
- Tier 3 discouraged deeper AD repair and recommended reimage instead.
- This created a potential **forensic blind spot** where anomalous behavior
  could occur on a machine and vanish when it was reimaged.

The conceptual bridge:

> "Ghost credentials" and "phantom trust breaks" can exist wherever legacy or
> misaligned auth objects are allowed to persist without clear ownership,
> rotation, or strong observability.

## Why This Sandbox

StegGhost / ghost-pat-lab is designed to:

- Hold a legacy PAT safely.
- Observe how GitHub treats it today.
- Document behavior that could inform **defensive designs** for future systems.
- Preserve this line of reasoning as part of StegVerse's broader security
  philosophy and memoir-like reflections.
