# DTFS Context

Last updated: 2026-06-15 13:59 UTC

## Project identity

DTFS is the Sligo Labs private project channel/repository initialized from Reserve Protocol's `reserve-index-dtf` codebase.

- Sligo GitHub repository: `https://github.com/sligo-labs/dtfs`
- Upstream repository: `https://github.com/reserve-protocol/reserve-index-dtf`
- Notion project page: `https://app.notion.com/p/DTFS-3806381fd20281f6be7dfae873afcb09`
- Canonical local checkout: `/home/droid/.hermes/workspace/dtfs`
- Discord channel: `#dtfs`

This Sligo repository is a private mirror rather than a public GitHub fork. GitHub forks of public repositories are public by default; Sligo client/project repositories are private unless a human explicitly changes visibility.

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
- Keep Sligo-local operating docs (`AGENTS.md`, `docs/context.md`, `docs/project-state.md`) current and compact.
- Use `origin` for the private Sligo repo and `upstream` for Reserve Protocol's source repo.
- Review upstream syncs carefully so Sligo-local docs are not removed accidentally.
