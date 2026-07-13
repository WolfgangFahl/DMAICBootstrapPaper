# AGENTS.md

## PLAN AND ASK BEFORE DO

**CRITICAL: NEVER EVER DO ANY ACTION READING, MODIFYING OR RUNNING without explaining the plan.**

Each set of intended actions needs to be explained in the format:

> I understood that `<YOUR ANALYSIS>` so that I plan to `<GOALS YOU PURSUE>` by `<ACTIONS TO BE CONFIRMED>` estimating `<# of ITEMS>` `<ITEMS>` to be worked on. Confirm with go!

**YOU WILL NEVER PROCEED WITHOUT POSITIVE CONFIRMATION by go!**

## Efficiency

- Do NOT do unneeded file lookups based on guessing or assuming typos.
- Do NOT read files you already have contents for.
- Keep summaries to 2-3 lines max unless asked for detail.
- Minimize tool calls. Batch parallel calls. Avoid redundant calls.

## Security

**CRITICAL: NEVER leak credentials, passwords, hashes, internal hostnames, IPs, or any infrastructure details to public platforms (GitHub, Discourse, etc.). Firing offense.**

## Scientific Paper

This project is a scientific paper. The publication outlet is **not yet
decided** (see issue #7 "Be publisher-independent until the outlet is
decided"); Zenodo is the only committed publication channel so far, and the
`ceurart` class is used as the working layout only.

Initial policy (in force until 2026-07-13, kept for the record): AI support
strictly limited to spelling/grammar corrections and formatting/build
tooling; AI must NOT generate, rewrite, or contribute original scientific
content, arguments, or prose.

### Policy amendment (2026-07-13, gate opened)

Issue #3 "Allow scientific content (policy gate)" was closed as approved by
the human author Wolfgang Fahl on 2026-07-13. The policy is amended as
follows:

- The AI agent MAY author scientific content for this paper (abstract,
  introduction, method, experiment description, statistics, analysis,
  related work) — grounded strictly in the experiment data: round logs,
  DMAIC corpus statistics via SMW queries, the public experiment pages, and
  the bibliography. No unsourced claims — every claim cites its source.
- All agent-authored content enters via commits and is subject to human
  review in GitHub/Overleaf; the human authors retain sole responsibility
  for all scientific claims, interpretations and conclusions at submission
  time.
- The Declaration on Generative AI in `main.tex` must disclose the agent's
  authorship role per the eventually chosen outlet's policy.
- This amendment and its timing are themselves experiment data.

### Issue-gated policy change (experiment governance)

This repository is itself part of the DMAIC Bootstrap experiment
(<https://cr.bitplan.com/index.php/DMAIC_Bootstrap>), whose subject is LLM
agent behavior under instructions, rules and knowledge-graph grounding.
Because the experiment studies agent-authored artifacts, the human authors
may explicitly relax the content policy — but only via the dedicated issue
**"Allow scientific content"** in this repository's issue tracker:

- Until that issue is closed by the human authors, the strict policy above
  applies without exception.
- If it is closed as approved, the policy section is amended in the same
  commit that closes the issue, stating exactly what the agent may author
  and under which human review.
- The gate and its resolution are experiment data and will be reported in
  the paper.

A "Declaration on Generative AI" must be finalized in `main.tex` before
submission, consistent with the policy state at submission time and with
the requirements of whatever outlet is eventually chosen (e.g. CEUR-WS's
<https://ceur-ws.org/GenAI/Policy.html> if that outlet is selected).

## GitHub Automation

This project uses GitHub Actions to automatically build the PDF from LaTeX
sources on every push to `main`.

### Structure

- `.github/workflows/build.yml` — CI workflow: checks out repo, builds PDF via `scripts/tex2pdf --github`, and commits the updated PDF if changed
- `scripts/tex2pdf` — LaTeX build script (pdfLaTeX + BibTeX, 3-pass). Supports `--build`, `--check`, `--install`, `--clean`, `--fonts`, `--github`, and `--help`
- `scripts/bash_messages` — colored terminal messaging helper (sourced by `tex2pdf`)
- `scripts/validate_cff` — validates `CITATION.cff` (cffconvert)
- `scripts/cff2zenodo` — derives the Zenodo deposit from `CITATION.cff` and uploads the built PDF
- `.gitignore` — excludes LaTeX build artifacts
- `README.md` — links to the PDF in the repo

### Template

- `ceurart.cls` — official CEUR-WS 1-column document class
- `elsarticle-num-names.bst` — CEUR-WS bibliography style
- `main.tex` — paper skeleton (title, author, empty Abstract + Introduction)
- `dmaicbootstrap.bib` — bibliography (predecessor reference only)
- `CITATION.cff` — citation metadata, single source of truth for Zenodo
