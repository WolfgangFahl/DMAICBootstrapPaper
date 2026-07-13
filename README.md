# DMAIC Bootstrap — Paper (skeleton)

Paper repository for the **DMAIC Bootstrap** experiment: applying the Six
Sigma DMAIC cycle to LLM agent incidents recorded in a Semantic MediaWiki
knowledge graph — and bootstrapping the improvement system by its own method.
Follow-up to
[How We Created 6 AI Agents in No Time](https://wiki.bitplan.com/index.php/How_We_Created_6_AI_Agents_in_No_Time).

This repository currently contains only the build infrastructure and an
**empty** paper skeleton — **no scientific content**. Scientific content is
issue-gated: see the AI content policy below.

- Experiment page: [cr:DMAIC Bootstrap](https://cr.bitplan.com/index.php/DMAIC_Bootstrap)
- Plan: [cr:DMAIC Bootstrap/Plan](https://cr.bitplan.com/index.php/DMAIC_Bootstrap/Plan)
- Context model: [AgentTeamContext](https://contexts.bitplan.com/index.php/AgentTeamContext)
- [View PDF in browser](https://github.com/WolfgangFahl/DMAICBootstrapPaper/raw/main/main.pdf) (built by CI)

## Build

```bash
scripts/tex2pdf --build
```

The PDF is rebuilt automatically on every push to `main` via GitHub
Actions (`.github/workflows/build.yml`). `CITATION.cff` is the single source
of truth for citation metadata (`scripts/validate_cff`,
`scripts/cff2zenodo`).

## Template

The publication outlet is **not yet decided**
([issue #7](https://github.com/WolfgangFahl/DMAICBootstrapPaper/issues/7));
Zenodo is the only committed publication channel so far. The `ceurart`
1-column class is used as the working layout only. Do not use the
`twocolumn` / `hf` document-class options with this class.

## AI content policy

See [AGENTS.md](AGENTS.md): the repository started with AI assistance
limited to spelling/grammar and formatting/build tooling. On 2026-07-13 the
human authors opened the issue gate
([#3 "Allow scientific content"](https://github.com/WolfgangFahl/DMAICBootstrapPaper/issues/3)):
the AI agent may author scientific content grounded strictly in the
experiment data, with every claim citing its source, under human review;
the human authors retain sole responsibility for all scientific claims at
submission time. The policy gate and its resolution are themselves part of
the reported experiment.
