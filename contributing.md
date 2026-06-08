# Contributing to Awesome LLM Attacks

Thanks for helping build a vendor-neutral catalog of LLM/GenAI attack techniques.

## How to contribute
- **Add a technique:** append a row to the relevant `## Group` table with: a new `LLM-ATTK-NNN` ID
  (next free number), the technique name, framework mappings (OWASP LLM/ASI, MITRE ATLAS, MCP…), a one-line
  description, mitigations, and at least one reference.
- **Improve an entry:** tighten descriptions, add framework mappings, add primary-source references, fix errors.
- **Propose a new group** only for a genuinely new class of attack.

## Ground rules
- **Vendor-neutral.** No product pitches or coverage claims for specific tools.
- **Citation-backed.** Prefer primary sources (papers, advisories, framework docs). Verify the mapping IDs.
- **Defensive framing.** Describe the technique class and its mitigations — this is not an exploit repo.
- **One technique per row.** Keep IDs stable; never renumber existing entries.

Open a PR with a clear title. Maintainers review for accuracy, neutrality, and citations.
