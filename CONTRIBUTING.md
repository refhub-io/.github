# Contributing to the RefHub GitHub profile

This repo controls the public GitHub organization profile and related org-level docs.

## Brand, style, and identity

Before editing the org profile, compare wording with `refhub-style-guide/refhub-identity.md`. Keep it concise, lowercase where that is part of the RefHub voice, accurate about active/archived repos, and free of local-only operational detail.

Core rules:

- Prefer concise, practical wording over marketing copy.
- Preserve lowercase, `//` comment-style headings, snake_case labels, and monospace conventions where the repo surface already uses them.
- Keep examples concrete and operational: vaults, papers, tags, relations, PDFs, exports, agents, and API keys.
- Do not introduce a one-off visual, copy, naming, or interaction style for a single feature.

## Existing conventions

Before editing, read `profile/README.md` and compare wording with `refhub-style-guide/refhub-identity.md`.

Keep the org profile:

- concise;
- lowercase and `//`-styled where that is part of the RefHub voice;
- accurate about active repos and archived/deprecated repos;
- free of local-only operational details.

## Scope and branch discipline

Do the work that was asked for. Keep unrelated repo-map edits, marketing copy rewrites, and badge changes out of focused PRs unless required.

## Pull requests

Never commit directly to `main`.

Use a fresh branch from current `origin/main`:

- `fix/...` for corrections.
- `feature/...` for new org-profile sections.
- `docs/...` for documentation-only changes.
- `chore/...` for maintenance.

Open a PR for every change.

## Verification

Preview Markdown rendering before merging. Check links to repos, install instructions, badges, and archived/deprecated labels.

## Changelog and semver

This repo has no package release surface. PR descriptions are the change log. Keep them specific.

## Security and credentials

Never commit API keys, bearer tokens, local env files, private user data, or user-specific credentials. Examples must use placeholders only.
