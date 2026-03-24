<div align="center">

# refhub

### structured research memory for humans, tools, and agents

![frontend](https://img.shields.io/badge/frontend-refhub.io-7c3aed?style=for-the-badge)
![backend](https://img.shields.io/badge/backend-.netlify-22c55e?style=for-the-badge)
![integration](https://img.shields.io/badge/integration-refhub--skill-ec4899?style=for-the-badge)
![status](https://img.shields.io/badge/status-building-06b6d4?style=for-the-badge)

</div>

---

refhub is being built as a **reference manager + knowledge substrate** for serious research workflows.
it is not just a prettier paper list.
it is meant to support:

- organizing publications into vaults
- tagging and structuring research collections
- building relation graphs between papers and ideas
- exporting and syncing cleanly
- powering automation, agents, and future cli / mcp workflows

our bias is toward **explicit structure, usable interfaces, and APIs that are safe for automation**.

---

## ✦ what we are building

refhub is evolving into a small system, not a single repo.

### today
- a frontend for working with vaults, publications, tags, and profiles
- a backend/api layer for external integrations and api-key workflows
- supporting docs and specs for future skill / cli / agent workflows

### direction
we want refhub to become a solid foundation for:
- personal research knowledge management
- collaborative literature organization
- programmable reference workflows
- agentic ingestion / curation / export pipelines

in plain english: **something you can use directly in the browser, but also plug into tools without regretting it later.**

---

## ⚙ organization shape

the org is split by responsibility, not by accident.

| repo | role | focus |
|---|---|---|
| `refhub-io/refhub.io` | frontend product | vault browsing, editing, profile/settings, api-key management ui, search, workflow ergonomics |
| `refhub-io/.netlify` | backend api | versioned `/api/v1`, key auth, scoped access, import/export, backend hardening |
| `refhub-io/refhub-skill` | integration layer | skill workflows, api alignment, future cli / mcp path |

---

## ⟡ engineering stance

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

## ⇢ current repo map

```text
refhub-io/
├── refhub.io      # frontend product
├── .netlify       # backend api / serverless functions
└── refhub-skill   # skill/integration layer (emerging)
```

---

## ◇ near-term goals

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

## ✺ design sensibility

refhub is for researchers and builders who are comfortable with dense interfaces, keyboards, and actual structure.

the style is:
- dark-first
- technical
- data-dense
- low on marketing glaze
- closer to a good terminal tool than a lifestyle app

if something feels vague, ornamental, or overexplained, it is probably wrong.

---

## ☰ contributing

if you are contributing, keep the split clean:

- frontend concerns belong in `refhub.io`
- backend/api concerns belong in `.netlify`
- integration abstractions should follow the real backend, not outrun it

good contributions usually make one of these better:
- data structure
- permission clarity
- workflow efficiency
- integration safety
- research usability

---

## ↗ roadmap

v2 planning now exists in both main repos:

- frontend roadmap: `refhub.io/docs/V2_ROADMAP.md`
- backend roadmap: `.netlify/docs/V2_ROADMAP.md`

those documents outline the next serious layer:
- expanded scopes and permissions
- vault lifecycle
- first-class tags and relations
- search/filter/query surfaces
- import/sync
- audit/provenance
- better agent/workflow support

---

<div align="center">

## principle

**refhub should be pleasant for humans, legible for developers, and safe for agents.**

that is the bar.

</div>
