# DTFS Context

Last updated: 2026-06-15 14:20 UTC

## Project identity

DTFS is the Discord channel/project name for Sligo's working fork of Reserve Protocol's `reserve-index-dtf` codebase.

- Public fork / origin: `https://github.com/sligo-droid/reserve-index-dtf`
- Upstream repository: `https://github.com/reserve-protocol/reserve-index-dtf`
- Notion project page: `https://app.notion.com/p/DTFS-3806381fd20281f6be7dfae873afcb09`
- Canonical local checkout: `/home/droid/.hermes/workspace/dtfs`
- Discord channel: `#dtfs`
- Sligo-only docs branch: `sligo/project-docs`

The fork's `main` branch should stay clean for upstream contribution work. Sligo-local operating docs (`AGENTS.md`, this file, and `docs/project-state.md`) live on `sligo/project-docs` and should not be merged into `main` or included in upstream PRs.

## Upstream product summary

Reserve Folio is an onchain protocol for creating and managing portfolios of ERC20 assets. Folios hold baskets of assets and rebalance through dutch auctions controlled by governance and delegated operational roles.

Core components from the upstream README/code layout:

- `contracts/Folio.sol`: primary portfolio contract with auction/rebalance logic.
- `contracts/deployer/FolioDeployer.sol`: deployment path for new Folio instances.
- `contracts/folio/FolioProxy.sol`: proxy for Folio implementations checked through a version registry.
- `contracts/governance/FolioGovernor.sol`: time-based governor.
- `contracts/staking/StakingVault.sol`: staking/voting/rewards vault.
- DAO-level registries include `FolioDAOFeeRegistry` and `FolioVersionRegistry`.

Primary operational roles:

- `DEFAULT_ADMIN_ROLE`: expected to be the slow Folio Governor timelock; owns broad Folio administration.
- `REBALANCE_MANAGER`: expected to be the fast Folio Governor timelock; starts/ends rebalances and auctions.
- `AUCTION_LAUNCHER`: expected to be an EOA or multisig; opens/ends auctions within governance-approved bounds.

## Stack

- Solidity smart contracts.
- Foundry for compile/test/deploy scripting.
- pnpm package management.
- TypeScript export script at `script/export.ts`.
- GitHub Actions workflows for formatting/linting, build/compile/artifacts, deployment smoke, and tests.

Package scripts observed in `package.json`:

- `pnpm format:check`
- `pnpm compile`
- `pnpm test`
- `pnpm test:extreme`
- `pnpm test:all`
- `pnpm size`
- `pnpm export`
- `pnpm deploy`

## External configuration

Do not store secret values in this repo or project notes.

Observed config/secret names:

- Local `.env.example`: `FORK_RPC_MAINNET`, `FORK_RPC_ARBITRUM`, `FORK_RPC_BASE`.
- GitHub Actions test workflow: `ALCHEMY_MAINNET_KEY`, `ALCHEMY_BASE_KEY`.
- Deploy workflow/scripts use `ETHERSCAN_KEY` in the environment.

## Current Sligo-local convention

- Keep upstream code behavior intact unless there is an explicit Sligo task.
- Use `origin` for the public Sligo Droid fork and `upstream` for Reserve Protocol's source repo.
- Keep Sligo project docs on `sligo/project-docs`, not on fork `main`.
- For upstream PRs, branch from `upstream/main`, push only intended upstream changes to `origin`, and verify the upstream compare does not include Sligo-only files.
