> **Experimental. We are just trying this.** [Disclaimer](../../DISCLAIMER.md) · Kaspa Testnet-10 only. No covenant id, key, address, host, or port in this folder.
>
> This folder is a tool. Reading it does not start a machine, arm a runner, or send.

# Sixteen-family hash path

This is the desk's path to [hashes/SIXTEEN.md](../../hashes/README.md) for pre-run 2. It is not the old desk publisher, which writes 8 or 32 families and is not used here.

| File | What it does |
|---|---|
| `sixteen-format.mjs` | The one shape of `SIXTEEN.md`: sixteen rows, family label, cohort, sha256 of the lowercase hex covenant id, a Fixed line, then an On origin line. Floor is families 1–13. Double is families 14–16. |
| `hash-sixteen.mjs` | Reads the family coins from the desk's own synced TN10 node, builds the sixteen genesis transactions in one reference builder, and writes the rows. It does not submit. It keeps the built transactions in a private bundle on the desk. The family submit uses that bundle, so each row is the hash of the covenant that is then submitted. |
| `publish-sixteen.mjs` | Reads the gates from origin, pushes the rows (`Publish the sixteen family-id hashes.`), reads that commit's time back from origin, and pushes the On origin line (`Record the origin time of the sixteen family-id hashes.`). |
| `sixteen.ps1` | The desk wrapper. PowerShell 7 only. `-Mode check` builds and verifies locally and pushes nothing. `-Mode publish` stops at the first closed gate, then builds, verifies, and publishes. |

The private config, the key file, the node address, and the bundle stay on the desk. They are not in this repo.

## Gates the publisher reads from origin

It writes nothing unless all of these hold on `origin/main` of this repo:

- `logs/PRE-RUN-OPEN.md` is there with `PRE_RUN_OPEN`.
- `logs/MINI-ARMED.md` is there with `MINI_ARMED`.
- `logs/BOT-HALT.md` and `logs/FAILED.md` are absent.
- `hashes/SIXTEEN.md` is absent. It is not republished.

The file must verify, every row must match the private bundle, and a format-check fixture is refused for a GitHub origin. Git is called by its full path. A failed push is tried once more after a rebase on origin, then the tool stops and says the git error.

## Builder launch path

The reference builder builds a genesis only when the launch path starts with `launch::storm-2026-10-`. Anything else is refused with `launch path not on the storm allow-list`. Pre-run 1's hash step used a `launch::prerun1-…` path, and that refusal was its `HASH_STOP build`. `hash-sixteen.mjs` checks the prefix before it reads the node.

## Checked on the desk, 11 Nov 2026

`-Mode check` on the desk, against its own synced TN10 node: gates held (`pre-run-open-absent`), sixteen genesis transactions built, sixteen rows written locally, the file verified, the rows matched the bundle, and two builds on the same coins gave the same rows. Nothing was pushed and nothing was submitted. The funding coins were not one size.
