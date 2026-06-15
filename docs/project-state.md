# DTFS Project State

Last updated: 2026-06-15 13:59 UTC
State owner: Sligo Labs

## Current focus

Initial channel/project setup from `reserve-protocol/reserve-index-dtf` into a private Sligo Labs repository.

## Snapshot

| Area                     | State    | Evidence                                                                                                                  |
| ------------------------ | -------- | ------------------------------------------------------------------------------------------------------------------------- |
| Sligo repository         | verified | `https://github.com/sligo-labs/dtfs`, private repository                                                                  |
| Upstream source          | verified | `https://github.com/reserve-protocol/reserve-index-dtf`, default branch `main`                                            |
| Local canonical checkout | verified | `/home/droid/.hermes/workspace/dtfs` at `ba1088f`, clean, `origin/main == upstream/main` at initialization                |
| Remotes                  | verified | `origin` = `git@github.com:sligo-labs/dtfs.git`; `upstream` = `https://github.com/reserve-protocol/reserve-index-dtf.git` |
| Notion project page      | verified | `https://app.notion.com/p/DTFS-3806381fd20281f6be7dfae873afcb09`                                                          |
| CI                       | blocked  | PR #1 Actions jobs did not start because GitHub reports account payment/spending-limit blocking runner start              |
| Discord channel topic    | blocked  | `#dtfs` topic PATCH returned Discord 403 Forbidden; current topic is `null`                                               |
| Production deploy        | planned  | No frontend/app production deployment configured during initial import                                                    |
| Secrets/config           | planned  | Required secret names identified; values not configured or stored in project docs                                         |

Allowed states: `planned`, `ready`, `in_progress`, `blocked`, `warning`, `implemented`, `merged`, `deployed`, `verified`, `superseded`.

## Done

- Created private Sligo Labs repository `sligo-labs/dtfs`.
- Imported upstream `reserve-protocol/reserve-index-dtf` default branch, tags, and upstream branches that GitHub accepted.
- Created canonical local checkout at `/home/droid/.hermes/workspace/dtfs`.
- Added `upstream` remote pointing at Reserve Protocol's repository.
- Created Notion project page under the Clients page.
- Added initial repo-local worker instructions and project context/state docs.

## In Progress

- Initial Sligo-local docs PR: `https://github.com/sligo-labs/dtfs/pull/1` (`chore/dtfs-initial-project-docs`).

## Blocked

- Merging PR #1 is blocked on GitHub Actions runner availability. Every PR workflow job failed before steps ran with: “The job was not started because recent account payments have failed or your spending limit needs to be increased.”
- Setting the Discord channel topic is blocked by bot permission: PATCH `/channels/1516078359677898932` returned HTTP 403. Desired topic when permission is fixed: zero-width-space line, blank line, `pending`, then `https://github.com/sligo-labs/dtfs`.

## Warnings / caveats

- This is a private mirror, not a GitHub-network fork. The upstream repository is public and Sligo policy keeps new client/project repos private unless a human explicitly changes visibility.
- The initial mirror push attempted to copy upstream pull-request refs; GitHub rejected hidden `refs/pull/*` refs as expected. Branches and tags were imported.
- GitHub Actions secrets are not configured yet. Tests that require fork RPC keys will fail or be incomplete until the needed secrets are added in GitHub/Vercel/provider secret stores.

## External Configuration

Do not store secret values here.

Required/observed config names:

- `FORK_RPC_MAINNET`
- `FORK_RPC_ARBITRUM`
- `FORK_RPC_BASE`
- `ALCHEMY_MAINNET_KEY`
- `ALCHEMY_BASE_KEY`
- `ETHERSCAN_KEY`

## Next Actions

1. Resolve the GitHub Actions billing/spending-limit blocker, then rerun PR #1 checks.
2. Grant the Sligo Labs bot permission to edit the `#dtfs` channel topic, then set it to the static creation metadata.
3. Merge PR #1 after checks can actually run, then fast-forward `/home/droid/.hermes/workspace/dtfs`.
4. Configure GitHub Actions secrets if CI/test parity is needed for forked-network tests.
5. Decide whether DTFS needs Vercel/frontend deployment, Supabase, or a contract-only workflow. No deployment was assumed during initialization.
6. For future upstream syncs, fetch `upstream/main`, review diffs, and preserve Sligo-local docs.

## Verification Checklist

- [x] GitHub repository exists under `sligo-labs` and is private.
- [x] Canonical checkout exists at `/home/droid/.hermes/workspace/dtfs`.
- [x] `origin/main` and `upstream/main` matched at initialization commit `ba1088f`.
- [x] Notion page was created under the configured Clients page.
- [ ] Initial docs PR merged and canonical checkout fast-forwarded afterward.
- [ ] Sligo GitHub Actions checks observed after first PR.
