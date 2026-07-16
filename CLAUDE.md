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

## Releases

GitHub Releases are the canonical changelog (no `CHANGELOG.md`, to avoid drift):

```sh
git tag -a vX.Y.Z -m "..." && git push origin vX.Y.Z
gh release create vX.Y.Z --title "..." --notes "..."
```

Latest: **v1.2.2**. Commit trailer: `Co-Authored-By: Claude Fable 5 <noreply@anthropic.com>`.
