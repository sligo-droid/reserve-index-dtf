# DTFS Project State

Last updated: 2026-06-15 14:26 UTC
State owner: Sligo Labs

## Current focus

DTFS is now a public GitHub fork intended for upstream Reserve Protocol contribution work. The Discord channel remains named `dtfs`; the canonical GitHub repository is `sligo-droid/reserve-index-dtf`.

## Snapshot

| Area                     | State    | Evidence                                                                                                          |
| ------------------------ | -------- | ----------------------------------------------------------------------------------------------------------------- |
| Public fork              | verified | `https://github.com/sligo-droid/reserve-index-dtf`; REST reports `fork=true`, parent/source = upstream            |
| Upstream source          | verified | `https://github.com/reserve-protocol/reserve-index-dtf`, default branch `main`                                    |
| Fork `main`              | verified | `upstream main...sligo-droid:main` compare is `identical` (`ahead_by=0`, `behind_by=0`)                           |
| Local canonical checkout | verified | `/home/droid/.hermes/workspace/dtfs`, clean, `origin/main == upstream/main` at setup                              |
| Remotes                  | verified | `origin` = `git@github.com:sligo-droid/reserve-index-dtf.git`; `upstream` = Reserve Protocol repo                 |
| Sligo docs branch        | verified | `sligo/project-docs` pushed to `origin`; upstream compare lists only `AGENTS.md` and `docs/` files                |
| Notion project page      | verified | `https://app.notion.com/p/DTFS-3806381fd20281f6be7dfae873afcb09`                                                  |
| GitHub Actions           | warning  | Org/account billing previously blocked Actions on the temporary import repo; true fork main has no new checks yet |
| Discord channel topic    | verified | Read back from Discord as zero-width-space line, blank line, `pending`, fork GitHub URL                           |
| Production deploy        | planned  | No frontend/app production deployment configured during initialization                                            |
| Secrets/config           | planned  | Required secret names identified; values not configured or stored in project docs                                 |

Allowed states: `planned`, `ready`, `in_progress`, `blocked`, `warning`, `implemented`, `merged`, `deployed`, `verified`, `superseded`.

## Done

- Made the repository public as requested.
- Moved the canonical repository target to `sligo-droid`.
- Renamed the canonical repository to `reserve-index-dtf`.
- Recreated the canonical repository as a real GitHub fork of `reserve-protocol/reserve-index-dtf` so upstream PRs work through GitHub's fork network.
- Preserved the earlier public mirror as `sligo-droid/reserve-index-dtf-import-backup-20260615` rather than deleting it.
- Updated local `origin` remotes in the canonical checkout and docs worktree.
- Installed Foundry/Forge on this host under the Hermes home environment.
- Created Notion project page under the Clients page.
- Added/updated Sligo-local worker instructions and project context/state docs on `sligo/project-docs`.

- Pushed/updated `sligo/project-docs` on the real fork.
- Retried Discord channel topic update after bot reinstall/permission change; Discord returned 200 and readback verified the topic.

## In Progress

None.

## Blocked

None for repository topology.

## Warnings / caveats

- Sligo-only docs should not live on fork `main` because `main` is the branch most likely to seed upstream PR branches. Keep `AGENTS.md` and `docs/` on `sligo/project-docs` or in local/agent context.
- The earlier `sligo-labs/dtfs` import became a public mirror during relocation and was then renamed to `sligo-droid/reserve-index-dtf-import-backup-20260615`. It exists only as a preserved backup; do not use it as canonical.
- GitHub Actions secrets are not configured yet. Tests that require fork RPC keys will fail or be incomplete until the needed secrets are added in GitHub/provider secret stores.

## External Configuration

Do not store secret values here.

Required/observed config names:

- `FORK_RPC_MAINNET`
- `FORK_RPC_ARBITRUM`
- `FORK_RPC_BASE`
- `ALCHEMY_MAINNET_KEY`
- `ALCHEMY_BASE_KEY`
- `ETHERSCAN_KEY`

## Upstream PR workflow

1. Start contribution work from `upstream/main` or `origin/main`, not from `sligo/project-docs`.
2. Create a focused branch under `/home/droid/workspaces/`.
3. Make only the intended upstream change.
4. Run focused checks locally; run RPC-backed tests only when the needed secrets are available.
5. Push the branch to `origin`.
6. Open the PR against `reserve-protocol/reserve-index-dtf`.
7. Before opening, verify `gh api repos/reserve-protocol/reserve-index-dtf/compare/main...sligo-droid:<branch>` does not list Sligo-only `AGENTS.md` or `docs/` changes.

## Next Actions

1. Decide whether to delete the preserved backup repo `sligo-droid/reserve-index-dtf-import-backup-20260615`; deletion should be explicit.
2. Configure GitHub Actions secrets if CI/test parity is needed for forked-network tests.
3. For future upstream syncs, fetch `upstream/main`, update fork `main`, and keep `sligo/project-docs` separate.

## Verification Checklist

- [x] GitHub repository exists under `sligo-droid/reserve-index-dtf` and is public.
- [x] GitHub REST reports the canonical repository is a real fork of `reserve-protocol/reserve-index-dtf`.
- [x] Upstream compare reports fork `main` is identical to upstream `main` at setup.
- [x] Canonical checkout exists at `/home/droid/.hermes/workspace/dtfs`.
- [x] `origin/main` and `upstream/main` match at setup commit `ba1088f`.
- [x] Notion page was created under the configured Clients page.
- [x] `sligo/project-docs` pushed to the real fork.
- [x] Discord channel topic updated and read back.
