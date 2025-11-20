# StegGhost Sandbox: ghost-pat-lab

This repository is a **sandbox** for studying the behavior of a legacy GitHub
Personal Access Token (PAT) in a safe, isolated environment.

It is designed **only for research and defense-building**, not for production use.

---

## Purpose

- Observe how an older PAT (e.g., created before org migrations) behaves today.
- Understand the differences between **authentication** (who you are) and
  **authorization** (what you can do).
- Generate reports and notes that help design **stronger, safer auth systems**
  for StegVerse and StegVerse-Labs.

All experiments should be **read-only** with respect to external resources.
Write operations are limited to this repo (reports, logs, documentation).

---

## Required secret

In this repo's settings, add a GitHub Actions secret:

- **Name:** `GH_GHOST_PAT`
- **Value:** the legacy PAT you want to study.

This PAT will be used only for:
- calling GitHub's public API endpoints (e.g., `/user`, `/user/repos`)
- reading identity and capability information
- mapping how GitHub responds to the token today

No write operations are performed with `GH_GHOST_PAT`.

---

## Workflows included

- `.github/workflows/ghost_identity.yml`
  - Shows basic identity information for the PAT (from `/user`).

- `.github/workflows/ghost_capabilities_heatmap.yml`
  - Collects a "heatmap" of what the PAT can see (e.g., `/user/repos`, `/rate_limit`).

- `.github/workflows/ghost_boundaries.yml`
  - Tests how the PAT behaves when calling specific repos or org endpoints you choose.

- `.github/workflows/ghost_logbook.yml`
  - Appends summarized findings into `.github/reports/ghost_activity.md`.

---

## How to use (quick start)

1. Create the repo `StegGhost/ghost-pat-lab`.
2. Add the secret `GH_GHOST_PAT` with your legacy PAT.
3. Upload this bundle into the root of the repo (keeping the folder structure).
4. Commit to `main`.
5. Go to the **Actions** tab and run:
   - **"Ghost PAT: Identity"** first,
   - then **"Ghost PAT: Capabilities Heatmap"**,
   - optionally **"Ghost PAT: Boundaries"** with a repo name,
   - and finally **"Ghost PAT: Logbook"** to capture notes.

---

## Philosophy

This sandbox exists to help **understand and defend against** strange,
legacy-auth behaviors that might appear in large systems — including real-world
environments like VA infrastructure and complex org migrations.

It is a **defensive research lab**, not a mechanism for untraceable or
unaccountable access.
Generated: 2025-11-20T20:47:33.843749Z
