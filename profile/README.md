<div align="center">

<img src="https://refhub.io/og-image.png" alt="refhub" width="100%" />

# refhub

> // structured_research_memory for humans, tools, and agents

![frontend](https://img.shields.io/badge/frontend-refhub.io-7c3aed?style=for-the-badge)
![backend](https://img.shields.io/badge/backend-.netlify-22c55e?style=for-the-badge)
![skill](https://img.shields.io/badge/skill-refhub--skill-ec4899?style=for-the-badge)
![status](https://img.shields.io/badge/status-building-06b6d4?style=for-the-badge)

</div>

---

refhub is being built as a **reference manager + knowledge substrate** for serious research workflows. it is not just a prettier paper list. it is meant to support:

- organizing publications into vaults
- tagging and structuring research collections
- building relation graphs between papers and ideas
- exporting and syncing cleanly
- powering automation, agents, and future cli / mcp workflows

our bias is toward **explicit structure, usable interfaces, and apis that are safe for automation**.

---

## // what we are building

refhub is evolving into a small system, not a single repo.

### today
- a frontend for working with vaults, publications, tags, and profiles
- a backend/api layer for external integrations and api-key workflows
- a browser extension for saving papers from any tab
- agent skills and integration layer for claude code, gemini cli, opencode, codex, cursor, windsurf

### direction
we want refhub to become a solid foundation for:
- personal research knowledge management
- collaborative literature organization
- programmable reference workflows
- agentic ingestion / curation / export pipelines

in plain english: **something you can use directly in the browser, but also plug into tools without regretting it later.**

---

## // organization shape

the org is split by responsibility, not by accident.

| repo | role | focus |
|---|---|---|
| `refhub-io/refhub.io` | frontend product | vault browsing, editing, profile/settings, api-key management ui, search, workflow ergonomics |
| `refhub-io/.netlify` | backend api | versioned `/api/v1`, key auth, scoped access, import/export, backend hardening |
| `refhub-io/refhub-extensions` | browser extension | save papers from any tab — chrome + firefox, mv3, shared source tree |
| `refhub-io/refhub-skill` | integration layer | agent skill for the full v2 api surface — claude code, gemini cli, opencode, codex, cursor, windsurf |
| `refhub-io/refhub-cli` | cli | command-line client for the refhub api — used by agents and humans alike |
| `refhub-io/refhub-marketplace` | plugin registry | claude code marketplace for first-party refhub plugins |

---

## // agent support

install the refhub skill once — works across tools.

**claude code**
```sh
claude plugin marketplace add refhub-io/refhub-marketplace
claude plugin install refhub-skill@refhub-marketplace
```

**gemini cli · opencode · codex cli**
```sh
# gemini
mkdir -p ~/.gemini/skills/refhub-skill && curl -o ~/.gemini/skills/refhub-skill/SKILL.md \
  https://raw.githubusercontent.com/refhub-io/refhub-skill/main/SKILL.md

# opencode
mkdir -p ~/.config/opencode/skills/refhub-skill && curl -o ~/.config/opencode/skills/refhub-skill/SKILL.md \
  https://raw.githubusercontent.com/refhub-io/refhub-skill/main/SKILL.md

# codex
mkdir -p ~/.codex/skills/refhub-skill && curl -o ~/.codex/skills/refhub-skill/SKILL.md \
  https://raw.githubusercontent.com/refhub-io/refhub-skill/main/SKILL.md
```

**cursor · windsurf · others**
```sh
curl -O https://raw.githubusercontent.com/refhub-io/refhub-skill/main/AGENTS.md
```

---

## // engineering stance

we care about a few things quite a lot:

### 1. structure over vibes
if a concept matters, it should exist explicitly in the model and api.
that means tags, relations, permissions, vault roles, and scopes should be real things — not hidden conventions.

### 2. safe automation
if agents or scripts touch data, the system should make that sane:
- narrow api keys
- explicit scopes
- vault restrictions
- honest error handling
- auditability
- eventually dry-runs / safer bulk operations / sync surfaces

### 3. product clarity
frontend and backend should not blur responsibilities.
- normal user auth stays normal user auth
- api keys are for automation/runtime access
- settings should explain what a key can actually do

### 4. incremental seriousness
we are fine with v1 being small.
but the shape should support a credible v2 instead of painting us into a corner.

---

## // repo map

```
refhub-io/
├── refhub.io           # frontend product
├── .netlify            # backend api / serverless functions
├── refhub-cli          # cli client
├── refhub-extensions   # browser extension
├── refhub-skill        # skill / integration layer
└── refhub-marketplace  # claude code plugin registry
```

---

## // near-term goals

<table>
<tr>
<td valign="top" width="33%">

### backend
- strengthen api key management
- expand scope model cleanly
- add vault lifecycle support
- make tags / relations more first-class
- improve search, import, export, and sync surfaces

</td>
<td valign="top" width="33%">

### frontend
- make api-key management understandable and safe
- improve mobile responsiveness and settings ergonomics
- expose permission shape clearly
- support richer vault / tag / relation workflows

</td>
<td valign="top" width="33%">

### platform direction
- support agentic workflows without making the api sloppy
- keep the contract explicit enough for skill / cli / mcp layers later
- preserve a clean boundary between auth, data, and automation

</td>
</tr>
</table>

---

## // design sensibility

refhub is for researchers and builders who are comfortable with dense interfaces, keyboards, and actual structure.

the style is:
- dark-first
- technical
- data-dense
- low on marketing glaze
- closer to a good terminal tool than a lifestyle app

if something feels vague, ornamental, or overexplained, it is probably wrong.

---

## // contributing

if you are contributing, keep the split clean:

- frontend concerns belong in `refhub.io`
- backend/api concerns belong in `.netlify`
- extension concerns belong in `refhub-extensions`
- integration abstractions should follow the real backend, not outrun it

good contributions usually make one of these better:
- data structure
- permission clarity
- workflow efficiency
- integration safety
- research usability

---

<div align="center">

// refhub should be pleasant for humans, legible for developers, and safe for agents.

that is the bar.

</div>
