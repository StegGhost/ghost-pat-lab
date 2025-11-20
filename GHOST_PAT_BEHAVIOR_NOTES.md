# Ghost PAT Behavior Notes

Use this file to record observations from running the workflows in this repo.

Suggested sections to maintain over time:

## 1. Identity Observations

- Output from `GET /user` when using the ghost PAT.
- Whether the `login` is a user or org.
- Any fields that seem surprising or legacy (e.g., old plan info, stale metadata).

## 2. Repository Visibility

- Which repos (if any) are listed by `/user/repos`.
- Whether sandbox repos appear or not.
- Any differences after adding/removing the PAT's user to orgs or repos.

## 3. Boundary Behavior

- How the PAT behaves when calling:
  - Repos it clearly should not see.
  - Repos in StegGhost.
  - Repos in StegVerse-Labs (read-only tests only).
- Noting HTTP statuses: `200`, `401`, `403`, `404`, etc.

## 4. Rate Limits and Headers

- Differences in rate limits vs newer tokens (if any).
- Interesting headers returned by the API.

## 5. Security and Defense Insights

- How systems might detect similar ghost tokens.
- What logging is needed to see these behaviors clearly.
- Policy / governance patterns that would prevent this type of drift.

---

These notes are meant to inform future StegVerse and StegVerse-Labs security
documentation, not to guide offensive or untraceable behavior.
