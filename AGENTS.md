# DTFS Worker Instructions

This repository is the Sligo Labs private DTFS project copy initialized from `reserve-protocol/reserve-index-dtf`.

## Source of truth

- Canonical Sligo repository: `git@github.com:sligo-labs/dtfs.git`
- Upstream source repository: `https://github.com/reserve-protocol/reserve-index-dtf.git`
- Repo state: `docs/project-state.md`
- Product/architecture context: `docs/context.md`
- Notion project page: `https://app.notion.com/p/DTFS-3806381fd20281f6be7dfae873afcb09`

## Git workflow

- Treat `/home/droid/.hermes/workspace/dtfs` as the canonical clean checkout for inspection and default-branch sync only.
- Do implementation work in dedicated worktrees under `/home/droid/workspaces/`.
- Use branches and PRs for changes after initial import; merge only after relevant checks pass or blockers are explicitly documented.
- Keep `origin` pointed at `sligo-labs/dtfs` and `upstream` pointed at `reserve-protocol/reserve-index-dtf`.
- Do not make this repository public. The upstream repository is public; this Sligo copy is private by policy.

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
- For upstream sync work, fetch `upstream`, review incoming diffs, and reconcile deliberately instead of blindly overwriting Sligo-local project docs.
