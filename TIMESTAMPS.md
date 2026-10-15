# Cryptographic timestamps

This repository makes claims whose ORDER matters: the model, its parameters and its predictions are fixed
in a pre-registration before the code that tests them exists. Three independent dates back that up:

1. **The push.** GitHub's repository activity records when each commit arrived.
2. **RFC 3161.** A manifest of every tracked file and its SHA-256, signed by three independent trust
   authorities (one eIDAS-qualified) and stamped to Bitcoin: weekly, AND on every push that touches a
   `PREREGISTRATION*.md` or `results/`, so a pre-registration is dated within minutes of its push.
   `timestamps/`, `./tsa-verify.sh`, and `timestamps/README.md` for why two legs.
3. **OpenTimestamps.** Frozen files carry a `<name>.ots` proof beside them, committing the file's SHA-256
   to the Bitcoin blockchain, checkable without trusting this repository, GitHub or the authors:
   `ots verify PREREGISTRATION.md.ots`.

## What is stamped, and what is not

| Stamped (frozen once written) | Not stamped (living; history is in git, every version in the weekly manifest) |
|---|---|
| `PREREGISTRATION*.md` | `README.md`, `PLAN.md`, `MODEL.md`, `EMPIRICAL.md`, this file |
| everything under `results/` | `timestamps/` (it holds the proofs) |

`ots stamp` overwrites an existing proof, so a stamped file is never edited. A correction is a new file
(`PREREGISTRATION-<date>.md`). If a stamped file ever must change, rotate its proof to `<name>.rN.ots`
first and log it here.

## Log

- 2026-10-15: both legs installed (weekly OpenTimestamps upgrade, Sundays 04:17 UTC; RFC 3161 manifest,
  Sundays 06:17 UTC and on pushes touching the frozen paths). Nothing frozen yet.
