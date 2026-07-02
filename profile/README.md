<div align="center">

<img src="https://refhub.io/og-image.png" alt="refhub" width="100%" />

# refhub

> // structured_research_memory for humans, tools, and agents

![frontend](https://img.shields.io/badge/frontend-refhub.io-7c3aed?style=for-the-badge)
![backend](https://img.shields.io/badge/backend-.netlify-22c55e?style=for-the-badge)
![cli](https://img.shields.io/badge/cli-refhub--cli-0ea5e9?style=for-the-badge)
![skill](https://img.shields.io/badge/skill-refhub--skill-ec4899?style=for-the-badge)
![status](https://img.shields.io/badge/status-building-06b6d4?style=for-the-badge)

</div>

---

refhub is a **modern reference management platform** for organizing academic publications, building citation networks, and sharing research collections.

it is built for the command-line generation: browser-first, keyboard-friendly, dark by default, structured enough for agents and scripts, and blunt about the difference between user workflows and automation workflows.

---

## // current_state

refhub is now a multi-repo system with a clear split between product, api, cli, extension, and agent integration work.

- `refhub.io` is the frontend product: vaults, papers, profiles, settings, help, and api-key management
- `.netlify` is the backend/api layer: `/api/v1`, scoped keys, semantic scholar routes, pdf/item routes, import/export surfaces
- `refhub-cli` and `refhub-skill` are the automation layer for humans, scripts, and agents
- `refhub-extensions` handles browser capture
- `refhub-paper-drafter` is a specialized agent skill built on top of `refhub-skill`/`refhub-cli`, for drafting HCI and visualization research papers from a vault
- agent skills self-host their own Claude Code and Codex plugin marketplaces — no separate registry repo

near-term work is focused on cleaner vault workflows, stronger permission semantics, better import/export/search, and safer agentic operations.

---

## // what_we_are_building

refhub is not a prettier paper list. the target is a research memory system with explicit structure:

- vault-based publication management
- public and private research collections
- tags, metadata, relations, profiles, and settings
- pdf and google drive attachment workflows
- versioned api access for trusted automation
- cli, browser extension, and agent skill surfaces

in plain english: **usable in the browser, programmable without regret.**

---

## // repo_map

| repo | role | focus |
|---|---|---|
| [`refhub-io/refhub.io`](https://github.com/refhub-io/refhub.io) | frontend product | vaults, papers, profiles, settings, help, api-key ui |
| [`refhub-io/.netlify`](https://github.com/refhub-io/.netlify) | backend api | `/api/v1`, scoped auth, semantic scholar, pdf/item routes, import/export |
| [`refhub-io/refhub-cli`](https://github.com/refhub-io/refhub-cli) | cli | command-line workflows for humans, scripts, and agents |
| [`refhub-io/refhub-extensions`](https://github.com/refhub-io/refhub-extensions) | browser extension | save papers from the browser, chrome/firefox, mv3 |
| [`refhub-io/refhub-skill`](https://github.com/refhub-io/refhub-skill) | agent skill | operate the refhub api/cli — self-hosts its own claude code + codex plugin marketplaces |
| [`refhub-io/refhub-paper-drafter`](https://github.com/refhub-io/refhub-paper-drafter) | agent skill | draft hci/visualization research papers from a vault; builds on `refhub-skill`, works standalone |
| [`refhub-io/refhub-mcp`](https://github.com/refhub-io/refhub-mcp) | mcp experiments | earlier mcp integration work |
| [`refhub-io/refhub-style-guide`](https://github.com/refhub-io/refhub-style-guide) | internal style guide | identity, aesthetics, copy, and product conventions |
| [`refhub-io/refhub-ascii`](https://github.com/refhub-io/refhub-ascii) | assets | ascii logo assets |
| [`refhub-io/refhub-qr`](https://github.com/refhub-io/refhub-qr) | assets | qr/supporting assets |
| [`refhub-io/.github`](https://github.com/refhub-io/.github) | org profile | this readme and github organization profile |

---

## // agent_support

each agent skill repo is self-contained — no shared registry. install `refhub-skill` for general vault/api operation, `refhub-paper-drafter` for the paper-drafting workflow (works standalone, or layered on top of `refhub-skill`).

**claude code**
```sh
claude plugin marketplace add https://github.com/refhub-io/refhub-skill
claude plugin install refhub-skill@refhub-skill

claude plugin marketplace add https://github.com/refhub-io/refhub-paper-drafter
claude plugin install refhub-paper-drafter@refhub-paper-drafter
```

**codex**

add to your Codex plugin marketplace configuration (`~/.agents/plugins/marketplace.json` or project-local):
```json
{
  "name": "refhub-skill",
  "source": { "source": "github", "repo": "refhub-io/refhub-skill" },
  "policy": { "installation": "AVAILABLE", "authentication": "ON_INSTALL" },
  "category": "Productivity"
}
```
each repo also ships its own `.agents/plugins/marketplace.json`, so cloning locally and pointing Codex at the clone works too — see each repo's README.

**gemini cli · opencode**
```sh
# gemini
mkdir -p ~/.gemini/skills/refhub-skill && curl -o ~/.gemini/skills/refhub-skill/SKILL.md \
  https://raw.githubusercontent.com/refhub-io/refhub-skill/main/skills/refhub-skill/SKILL.md

# opencode
mkdir -p ~/.config/opencode/skills/refhub-skill && curl -o ~/.config/opencode/skills/refhub-skill/SKILL.md \
  https://raw.githubusercontent.com/refhub-io/refhub-skill/main/skills/refhub-skill/SKILL.md
```

**cursor · windsurf · pi · other generic harnesses**
```sh
curl -O https://raw.githubusercontent.com/refhub-io/refhub-skill/main/AGENTS.md
```
each skill repo's `AGENTS.md` is a full standalone copy of its skill instructions — no plugin system required.

---

## // engineering_stance

### structure_over_vibes
if a concept matters, it should exist explicitly in the model and api.

tags, relations, permissions, vault roles, scopes, and item metadata should be real things — not hidden conventions.

### safe_automation
agents and scripts should get narrow, inspectable access:

- scoped api keys
- vault restrictions
- honest errors
- auditability
- eventually dry-runs, safer bulk operations, and sync surfaces

### clean_boundaries
normal user auth is for people. api keys are for runtime automation. account setup and connected services stay in the web app.

---

## // design_sensibility

refhub is for researchers and builders who are comfortable with dense interfaces, keyboards, and actual structure.

- dark by default
- keyboard-first
- monospace where data matters
- `//` as the signature pattern
- low on marketing glaze
- closer to a good terminal tool than a lifestyle app

---

## // contributing

keep the split clean:

- frontend concerns belong in `refhub.io`
- backend/api concerns belong in `.netlify`
- cli ergonomics belong in `refhub-cli`
- extension concerns belong in `refhub-extensions`
- integration abstractions should follow the real backend, not outrun it

good contributions improve data structure, permission clarity, workflow efficiency, integration safety, or research usability.

---

<div align="center">

// pleasant for humans • legible for developers • safe for agents

</div>


<div align="center">
    // this software is free as in freedom.
</div>
<div align="center">
    •
</div>
<div align="center">
    // licensed under GPLv3. read more at <a href=https://www.gnu.org/licenses/gpl-3.0.en.html">https://www.gnu.org</a>
</div>

