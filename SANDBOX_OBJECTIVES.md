# StegGhost Sandbox Objectives

This sandbox exists for **defensive research**, not production use.

## Primary Objectives

1. **Observe legacy PAT behavior safely.**
   - How does an older PAT behave against modern GitHub APIs?
   - What does it see?
   - Where is it blocked?

2. **Map authentication vs authorization clearly.**
   - Distinguish between "who are you?" and "what are you allowed to do?"
   - Document how GitHub expresses that difference via status codes and data.

3. **Inform better designs for StegVerse and StegVerse-Labs.**
   - Token vaults.
   - Short-lived capabilities.
   - Stronger logging and governance.
   - Safer AI entity permissions.

4. **Preserve context for memoir and long-term reflection.**
   - Link technical insights to lived experience and motivations.

## Non-Goals

- No production secrets.
- No write operations to external repos.
- No attempts to bypass GitHub's security model.
- No unlogged or unaccountable behavior.

Everything here should be traceable, explainable, and oriented toward
**protecting people** from the kinds of blind spots large systems can create.
