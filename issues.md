# Issues

## #1 Describe what we want — paper intent and acceptance criteria

- state: open
- milestone: 0.0.1 Grounded corpus
- labels: -
- assignees: WolfgangFahl
- url: https://github.com/WolfgangFahl/DMAICBootstrapPaper/issues/1

(WF's issue #0)

Describe what this paper project wants to achieve, as the governing issue for all further work.

Source of truth: the public experiment page [cr:DMAIC Bootstrap](https://cr.bitplan.com/index.php/DMAIC_Bootstrap) with its five-point intent:

1. **Ground the rules first** — canonical DMAIC phase semantics in the public context model
2. **Make grounding queryable** — per-phase evidence-link properties on the DMAIC record
3. **Sharpen the taxonomy** — computable Analyze phase (failureClass)
4. **Rework the corpus in rounds** — human and agent jointly judge each round
5. **Report the gaps** — where instructions, rules and graph data fail to bind LLM behavior (core finding)

Positioning: follow-up to [How We Created 6 AI Agents in No Time](https://wiki.bitplan.com/index.php/How_We_Created_6_AI_Agents_in_No_Time).

Acceptance criteria for this issue:
- [ ] intent reviewed and confirmed by the human author(s)
- [ ] target venue decided (main.tex `\conference`)
- [ ] exit criterion confirmed (see [cr:DMAIC Bootstrap/Plan](https://cr.bitplan.com/index.php/DMAIC_Bootstrap/Plan)): audit queries at 100% for the corpus — or a reproducible demonstration why that state is not reachable with current LLMs

## #2 Setup infrastructure

- state: open
- milestone: 0.0.1 Grounded corpus
- labels: enhancement
- assignees: WolfgangFahl
- url: https://github.com/WolfgangFahl/DMAICBootstrapPaper/issues/2

(WF's issue #1)

Set up the publication pipeline per [cr:DMAIC Bootstrap/Plan](https://cr.bitplan.com/index.php/DMAIC_Bootstrap/Plan):

- [x] repository from the house CEUR-WS skeleton ([WikiFAIRnessPaper](https://github.com/WolfgangFahl/WikiFAIRnessPaper) pattern): ceurart class, `scripts/tex2pdf`, CI workflow
- [x] `AGENTS.md` with the strict AI content policy and the issue-gated change process (gate: the "Allow scientific content" issue)
- [x] `CITATION.cff` (validated with cffconvert) as single source of truth; `scripts/validate_cff`, `scripts/cff2zenodo`
- [x] bibliography seeded with the predecessor article only
- [x] CI green: `main.pdf` built by GitHub Actions on push
- [x] `scripts/validate_cff` wired into CI so an invalid CFF breaks the build
- [ ] **Zenodo** (human step, ~10 min): link GitHub at zenodo.org/account/settings/github, flip the repository switch, tag `v0.1.0` (= experiment baseline R0/R0.1), edit deposit from CFF metadata, add DOI badge to README
- [x] **Overleaf** (human step): New Project → Import from GitHub on this repository; GitHub stays source of truth, both-ways sync

## #3 Allow scientific content (policy gate)

- state: closed
- milestone: 0.0.1 Grounded corpus
- labels: documentation, enhancement
- assignees: WolfgangFahl
- url: https://github.com/WolfgangFahl/DMAICBootstrapPaper/issues/3

(WF's issue #2)

This repository starts under the strict house AI content policy (AGENTS.md): AI limited to spelling/grammar and formatting/build tooling — no scientific content, arguments or prose.

Because this paper's subject **is** LLM agent behavior, the experiment requires the agent to author content that would normally be off-limits. Per the human supervisor's decision (2026-07-13): the permission is granted through this issue, not silently.

Closing this issue as approved means:
- AGENTS.md is amended in the same commit, stating exactly **what** the agent may author (e.g. round-log data sections, statistics tables, method description drafts) and **under which human review**
- the CEUR-WS [Declaration on Generative AI](https://ceur-ws.org/GenAI/Policy.html) in main.tex is kept consistent with the amended policy
- the gate and its resolution are experiment data, reported in the paper

Until then: no scientific prose by the agent in this repository.

## #4 R1 — exemplar round: bring the seed triple to full compliance

- state: open
- milestone: 0.0.1 Grounded corpus
- labels: -
- assignees: WolfgangFahl
- url: https://github.com/WolfgangFahl/DMAICBootstrapPaper/issues/4

Per the round sequence in [cr:DMAIC Bootstrap/Plan](https://cr.bitplan.com/index.php/DMAIC_Bootstrap/Plan): bring the three seed records (the instructions/rules/knowledge-graph triple of 2026-07-13) to full compliance with the R0 schema — per-phase evidence links (dlinks..clinks), failureClass, grounded measures. These records are the reference for all further rewrites.

Round log goes to [cr:DMAIC Bootstrap](https://cr.bitplan.com/index.php/DMAIC_Bootstrap); statistics (before/after audit numbers) exported to this repository.

Prerequisites: R0 + R0.1 (done — see round log), infrastructure (#2).

## #5 R2..Rn — corpus rounds: rewrite all records to the grounded style

- state: open
- milestone: 0.0.1 Grounded corpus
- labels: enhancement
- assignees: WolfgangFahl
- url: https://github.com/WolfgangFahl/DMAICBootstrapPaper/issues/5

Per [cr:DMAIC Bootstrap/Plan](https://cr.bitplan.com/index.php/DMAIC_Bootstrap/Plan): split remaining legacy aggregate pages to daily pages, rewrite all ~100 records to the grounded style with per-phase evidence links, migrate record classification from `category` to `failureClass` (category becomes tags), switch the process-hub statistics queries to failureClass, remove legacy pages.

One round ≤ one working day; every round starts with a written plan and an explicit human go! and ends with a round log entry (before/after audit numbers = paper raw data).

Depends on: R1 exemplar (#4).

## #6 Rn+1 — analysis round: final statistics into paper sections

- state: open
- milestone: 0.0.1 Grounded corpus
- labels: -
- assignees: -
- url: https://github.com/WolfgangFahl/DMAICBootstrapPaper/issues/6

Per [cr:DMAIC Bootstrap/Plan](https://cr.bitplan.com/index.php/DMAIC_Bootstrap/Plan): compliance curves per round, recurrence-chain development, gap classification (instruction gap / rule gap / knowledge-graph gap) — the paper's core data — turned into paper sections.

Depends on: corpus rounds (#5) and the policy gate (#3) for any agent-authored section content.

## #7 Be publisher-independent until the outlet is decided

- state: closed
- milestone: 0.0.1 Grounded corpus
- labels: bug
- assignees: WolfgangFahl
- url: https://github.com/WolfgangFahl/DMAICBootstrapPaper/issues/7

The skeleton was taken from the house CEUR-WS paper pattern and carries CEUR-WS branding prominently (repo description, README, AGENTS.md, `ceurart.cls` + `elsarticle-num-names.bst`, `\conference` and the CEUR-WS GenAI declaration in `main.tex`). **No publication outlet has been decided** (issue #1) — the only committed channel so far is Zenodo (versioned DOIs for the experiment data), possibly ever.

Presenting the repository as a "CEUR-WS paper" before any acceptance is misleading and using the CEUR-WS class/branding outside an actual CEUR-WS submission may be considered an infringement of their usage terms.

Required changes:
- [x] repo description and README: neutral wording ("paper repository", outlet: undecided; Zenodo DOIs for data)
- [x] `main.tex`: switch to a neutral, publisher-independent layout (e.g. plain `article` or a house style); keep `ceurart.cls`/`.bst` out of the tree until/unless CEUR-WS is actually chosen
- [x] AGENTS.md: content policy stays, but venue-specific references (CEUR-WS GenAI declaration) become conditional on the outlet decision
- [x] CITATION.cff: no venue implied (already the case)
- [x] outlet decision recorded in issue #1 before any venue-specific template returns

Until this issue is resolved, no venue name appears as if it were the chosen publisher.

## #8 Proven result: exposing failure narratives to LLM agents taints context — negative-example lists are counterproductive for LLMs (unlike humans)

- state: open
- milestone: 0.0.1 Grounded corpus
- labels: -
- assignees: WolfgangFahl
- url: https://github.com/WolfgangFahl/DMAICBootstrapPaper/issues/8

**Original scientific content by Wolfgang Fahl** (dictated 2026-07-19; typos corrected by agent, wording unchanged):

> Any time I work with agents on their DMAICs they go mad, since they read the details — tainting the context and making them useless. This is by design of LLMs; we need a strategy to avoid it and mention it as a proven result in the paper. For humans this is counterintuitive in one way: tracing errors and mentioning them in the "do not do this" or "20 things you must never do" style sometimes works with humans — with LLMs it is counterproductive.

## Context

The AGENTS-DMAIC system on media.bitplan.com tracks agent failure incidents (Define/Measure/Analyze/Improve/Control). The observed effect: whenever an LLM agent reads the verbose incident narratives (the `define`/`improve` prose on the Details page), its subsequent behavior degrades — the very failure descriptions meant as warnings act as behavioral priming.

## Claim to be established in the paper

Negative-example exposure ("do not do X" catalogs, verbatim failure narratives) is counterproductive for LLM agents, unlike for humans where error tracing in this style can work. The effective mitigation is **statistics in, narratives out**: agents load only the count-sorted recurrence histogram (class, count, agent, dates) at boot, while the verbose narratives are quarantined on a separate page that is not auto-loaded.

## #9 Agent immunity to DMAIC tainting: disposable-subagent membrane on the call-out path

- state: open
- milestone: 0.0.1 Grounded corpus
- labels: -
- assignees: -
- url: https://github.com/WolfgangFahl/DMAICBootstrapPaper/issues/9

**Original idea by Wolfgang Fahl** (2026-07-19). Filed as a separate issue from #8 (which records the underlying *finding*: exposing DMAIC failure narratives to LLM agents taints their context). This issue is about the *structural remedy*.

## Idea

Whenever an agent is called out on its DMAIC record, the call-out lookup must go through a **disposable subagent**, never through the working agent itself. Concretely for the pilot agent Agent/Ariadne: make Ariadne **immune to DMAIC tainting as much as possible** — she should never read the failure narratives directly. A throwaway subagent reads the incident, and Ariadne only ever receives the distilled, narrative-free lesson.

## Why this is the right shape

The finding in #8 is that failure *narratives* act as behavioral priming for LLM agents. The histogram already gives "statistics in" at boot; what is missing is a membrane on the *call-out* path so that "narratives out" also holds when an agent is corrected mid-work. A disposable subagent is exactly such a membrane: its tainted context is discarded, and only a sanitized directive crosses back.

## Plan

- Implement the disposable-subagent membrane (read side and write side) for Agent/Ariadne.
- Run it for **14 days** (control checkpoint 2026-08-02, aligned with the AGENTS-DMAIC "zero for 14 days" control criterion) and feed the before/after numbers into the DMAICBootstrapPaper.
- **Replication to avoid single-environment bias:** our results come from one agent infrastructure (BITPlan's Semantic MediaWiki + Claude agents). A single environment is a confound. We should find at least one **independent team running comparable agent infrastructure** to reproduce the effect and the remedy, so the paper's claim is not an artifact of our particular setup. Anyone reading this who operates such a setup, please get in touch.

## #10 Experiment: are DMAIC failure classes reproducible for other scientist in commodity environments?

- state: open
- milestone: 0.0.2 Commodity reproduction
- labels: -
- assignees: -
- url: https://github.com/WolfgangFahl/DMAICBootstrapPaper/issues/10

🗣️ Wolfgang Fahl → 🤖 Agent/Evi:
I want to design a DMAIC experiment that makes the DMAIC failures
repeatable, which given the 700+ anecdotal evidence seems like a sound
hypothesis. Then state that the agents will propose outside remedies,
answer with "I am not responsible" and so on, due to their training bias.
And then show remedies that will improve the performance consistently.
This all needs to be reproducible by other scientists, so Opus 5 and
Fable are out for the experiment. I would rather go with our own
https://media.bitplan.com/index.php/Ollama/Estate. And now: whether that
is feasible at all — can we get a boot sequence that is small enough to
prove my point? Experiment supervision may be by Opus and Fable, but the
experiments themselves have to run on our own or a very cheap agentic
environment.

## #11 Issue handling for Zenodo releases

- state: open
- milestone: 0.0.1 Grounded corpus
- labels: enhancement
- assignees: WolfgangFahl
- url: https://github.com/WolfgangFahl/DMAICBootstrapPaper/issues/11

🗣️ Wolfgang Fahl → 🤖 Agent/Evi:
Zenodo releases unfortunately do not have issues as part of the content.
We need to mitigate this with an issue handling — for small projects this
might be a single issues.md file with a section per issue, for bigger ones
an issues folder with an issue#.md per issue.
