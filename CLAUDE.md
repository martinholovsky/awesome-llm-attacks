# CLAUDE.md — awesome-llm-attacks

Framework-mapped catalog of LLM/GenAI attack techniques, rendered as Markdown
tables in `README.md` (not the usual bullet-list awesome format). Submitted to
[sindresorhus/awesome](https://github.com/sindresorhus/awesome) — so the README
must satisfy that project's rules, several of which `awesome-lint` does **not**
enforce (see traps below).

## Layout

- `README.md` — the catalog. 11 `## Group` sections, each a table.
  Columns: **ID | Technique | Framework | Description | Mitigation | References**.
- IDs are `LLM-ATTK-GGNN` (GG = group 01–11, NN = number within the group).
  Never renumber existing IDs; append a new row at the **bottom of its group**.
- **Retired IDs — never reuse:** `0611`, `1004`. Both shipped in v1.2.2, were
  later found to duplicate `0603` / `0808`, and were deleted rather than left as
  `_Duplicate — merged into …._` stubs because they were the last row of their
  group. Their numbers are therefore free again — do **not** assign them to a new
  technique, or a published ID would silently change meaning. Duplicates that are
  **not** last in their group stay as stub rows (`0219`, `0220`, `0222`, `0312`,
  `0407`), since deleting those would renumber nothing but leave a confusing hole.
- `contributing.md` — contributor guide. `LICENSE` — CC-BY-4.0 (a Creative
  Commons license; a code license would be rejected by awesome).

## After any README edit (required)

```sh
npx --yes prettier@latest --write README.md   # aligns table pipes; preserves prose
npx --yes awesome-lint                          # MUST exit 0 — this is the gate
```

Do **not** run `prettier --prose-wrap never` in the normal flow — it de-aligns
the tables and awesome-lint then fails. It's only for a one-off prose unwrap,
and must be followed by a plain `prettier --write` to re-align.

## Traps awesome-lint won't catch (a human reviewer will)

- **No hard-wrapping** — one line per paragraph/blockquote.
- **No duplicate links** — if a URL is already linked once, write later
  citations as plain text (no `[]()`), or the double-link rule fails.
- **No License section in the README** — GitHub surfaces the license from
  `LICENSE`. Attribution/BibTeX lives under `## Footnotes`.
- **Banner goes inside the `<h1>`** (linked to the repo), Awesome badge
  centered below. Never have both a text `# Awesome LLM Attacks` heading and a
  banner wordmark of the same name.
- Citation style: `[Short Name (arXiv:XXXX.XXXXX)](https://arxiv.org/abs/XXXX.XXXXX)`.
  Prefer primary sources and **verify** mapping IDs and arXiv abstracts before
  adding — accuracy is the point of this repo.
- **The crosswalk table is the union of the per-row Framework cells** — it says so
  in its own preamble. Adding a row with a framework ID new to its group means
  updating that group's crosswalk cell too; merging or deleting a row can strand
  an ID there. Audit with a script rather than by eye; a stale `ASI08` survived in
  the Group 9 and 10 cells this way. Note the audit must expand range shorthand
  (`ASI01-08`, `LLM02-05`, `MCP01-07`) — a naive regex only reads the first atom.
- `atlas.mitre.org/techniques/AML.TXXXX` links are **soft-404s**: ATLAS is a Vue
  SPA that returns HTTP 404 while serving the app shell, so the pages render fine
  in a browser but any link checker flags them. Verify ATLAS technique IDs and
  names against `dist/ATLAS.yaml` in the `mitre-atlas/atlas-data` repo instead of
  the website.

## Releases

GitHub Releases are the canonical changelog (no `CHANGELOG.md`, to avoid drift):

```sh
git tag -a vX.Y.Z -m "..." && git push origin vX.Y.Z
gh release create vX.Y.Z --title "..." --notes "..."
```

Latest tag: **v1.3.1** (2026-08-27). Cut a release when a batch of technique
rows lands, and describe it in the release notes rather than a changelog file.
Bump this line in the same commit that precedes the tag, so the tagged tree
does not claim an older release as latest.

Commits carry a `Co-Authored-By:` trailer naming **the model that actually did
the work** (`Claude Opus 5 (1M context)`, `Claude Fable 5`, …) — do not copy a
previous commit's trailer, and do not omit it. AI assistance on this repo is
disclosed honestly, which matters because the awesome submission turns on it.
