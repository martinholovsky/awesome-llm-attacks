# Contributing to Awesome LLM Attacks

Thanks for helping build a vendor-neutral catalog of LLM/GenAI attack techniques.

## How to contribute

- **Don't want to touch Markdown?** Open a [New attack technique issue](https://github.com/martinholovsky/awesome-llm-attacks/issues/new?template=new-attack-technique.yml)
  and fill in the form — a maintainer will turn it into a table row.
- **Add a technique via PR:** append a row to the relevant `## Group` table with: a new `LLM-ATTK-GGNN` ID
  (`GG` = group, `NN` = next free number in that group), the technique name, framework mappings (OWASP LLM/ASI,
  MITRE ATLAS, MCP…), a one-line description, mitigations, and at least one reference.
- **Improve an entry:** tighten descriptions, add framework mappings, add primary-source references, fix errors.
- **Propose a new group** only for a genuinely new class of attack.

### Row template (copy, fill, paste into the right group table)

```
| LLM-ATTK-GGNN | <technique name> | <OWASP LLMxx; ATLAS AML.Txxxx; ASIxx; MCP> | <one-line mechanism> | <mitigations; semicolon-separated> | <Name: [arXiv 25XX.XXXXX](https://arxiv.org/abs/25XX.XXXXX)> |
```

Column order is **ID | Technique | Framework | Description | Mitigation | References**. If a reference URL is
already cited elsewhere in the README, write the repeat as plain text (no link) — the catalog avoids duplicate links.

## Ground rules

- **Vendor-neutral.** No product pitches or coverage claims for specific tools.
- **Citation-backed.** Prefer primary sources (papers, advisories, framework docs). Verify the mapping IDs.
- **Defensive framing.** Describe the technique class and its mitigations — this is not an exploit repo.
- **One technique per row.** Keep IDs stable; never renumber existing entries.
- **Retired IDs are not free.** `LLM-ATTK-0611` and `LLM-ATTK-1004` were published,
  then removed as duplicates of `0603` and `0808`. Their numbers are unused but must
  **not** be reassigned — a released ID should never change meaning. Take the next
  number above the group's current highest.
- **Framework cells feed the crosswalk.** The group ↔ framework table near the top of
  the README is the union of the per-row Framework cells. If your row introduces a
  framework ID that its group doesn't already list, update that row of the crosswalk too.

## Before you open a PR

Run these from the repo root and make sure both are clean:

```sh
npx --yes prettier@latest --write README.md   # align table pipes
npx --yes awesome-lint                          # must exit 0
```

A few formatting rules the linter won't always flag but reviewers enforce: no
hard-wrapping (one line per paragraph), and no duplicate links — if a URL is
already cited in the README, write the repeat as plain text (no link).

Open a PR with a clear title. Maintainers review for accuracy, neutrality, and citations.
