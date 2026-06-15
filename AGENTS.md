# DTFS Worker Instructions

This branch carries Sligo-local project instructions for the Discord channel named `dtfs`.

Important: these files are **not** intended for upstream Reserve Protocol PRs. Keep Sligo-only files on `sligo/project-docs` or in local worker context; keep contribution branches based on `upstream/main` / `origin/main` clean of `AGENTS.md` and `docs/` unless the upstream change explicitly needs documentation files that already exist upstream.

## Source of truth

- Public fork / origin: `git@github.com:sligo-droid/reserve-index-dtf.git`
- Upstream source repository: `https://github.com/reserve-protocol/reserve-index-dtf.git`
- Canonical local checkout: `/home/droid/.hermes/workspace/dtfs`
- Sligo project docs branch: `sligo/project-docs`
- Repo state on that branch: `docs/project-state.md`
- Product/architecture context on that branch: `docs/context.md`
- Notion project page: `https://app.notion.com/p/DTFS-3806381fd20281f6be7dfae873afcb09`

## Git workflow

- Treat `/home/droid/.hermes/workspace/dtfs` as the canonical clean checkout for inspection and default-branch sync only.
- Do implementation work in dedicated worktrees under `/home/droid/workspaces/`.
- Keep `origin` pointed at `sligo-droid/reserve-index-dtf` and `upstream` pointed at `reserve-protocol/reserve-index-dtf`.
- For upstream PRs, create a branch from `upstream/main` or the fork's `main`, make only the intended upstream code/docs change, push to `origin`, and open the PR against `reserve-protocol/reserve-index-dtf`.
- Do not merge `sligo/project-docs` into `main` or into upstream contribution branches.
- If Sligo docs accidentally appear in an upstream PR diff, stop and repair by rebasing/cherry-picking the intended commits onto a fresh branch from `upstream/main`.

## Development commands

This is a Solidity/Foundry + pnpm project.

- Install dependencies: `pnpm install --frozen-lockfile`
- Format check: `pnpm format:check`
- Compile: `pnpm compile`
- Core tests: `pnpm test`
- Extreme tests: `pnpm test:extreme`
- Full tests: `pnpm test:all`
- Size report: `pnpm size`
- Artifact export: `pnpm export`

## Environment / secrets

Do not commit secrets or RPC credentials. Required runtime/config names observed from `.env.example` and workflows:

- `FORK_RPC_MAINNET`
- `FORK_RPC_ARBITRUM`
- `FORK_RPC_BASE`
- GitHub Actions secrets: `ALCHEMY_MAINNET_KEY`, `ALCHEMY_BASE_KEY`
- Deploy/export-related key used by workflow/scripts: `ETHERSCAN_KEY`

Use provider/platform secret stores for values. Never store secret values in Git, Notion, Obsidian, memory, or Discord summaries.

## Project posture

- Preserve upstream architecture unless a task explicitly asks for a Sligo-specific change.
- Before edits, inspect immediate callers, tests, workflows, and deployment scripts relevant to the change.
- Keep Sligo operating context in this docs branch, Notion, Discord thread context, or local worker prompts — not in upstream contribution diffs.
