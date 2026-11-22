# HANDOFF — lsd_decompiled

**Last updated: 2026-11-22 (America/New_York).**
**Repo:** `mhvnsnt/lsd_decompiled` (PUBLIC), default branch `master` (not `main` — use this branch as the PR base).
**Purpose of this file:** any agent that picks up work here reads this FIRST, then the linked docs. It states what we've done, where we're at, and what we're working toward — so the owner can say "go to this repo, pick up the work" and you just know. Update this file in the same PR whenever the state changes (add, don't delete).

## 1. What this repo is

A work-in-progress decompilation of LSD: Dream Emulator for the PlayStation 1 — mirrored into the owner's account 2026-11-20. This is the cawfee lineage: an early-stage decomp that aims to create a fully functional decompilation compilable back into a playable game matching the original. Many functions are still being identified and filenames are still a work in progress and are not yet final.

This is the EARLY one of the owner's LSD decomps — do not mistake it for a complete one. How they relate:
- `mhvnsnt/lsd-decomp` — the AI-written matching decomp, complete (1,447/1,447 functions read).
- `mhvnsnt/lsddecomp` — the brian-oblivion lineage complete matching decomp (CC0).
- `mhvnsnt/lsddecomp-1` — the FirecatFG first attempt from 2024.
- `mhvnsnt/LSDRevamped` — Figglewatts' Unity remake of the game (not a decomp).
- `mhvnsnt/libLSD` — Figglewatts' C# library for loading LSD data files.

## 2. Where we're at

### DONE
- **Early decomp work (2026-10-01 → 2026-10-03):** "memory specific functions in base_class, merge together" (`a51621d`), "fix base checks" (`8751977`), "slow clean" (`1632600`), "cleanup" (`16a3914`). Last push 2026-10-03.
- **Mirrored into this account 2026-11-20** (repo created here that day; history carried over).
- **Build setup documented:** `configure.py` + `tools/quiet_ninja.py` (split / check); needs the game executable `SLPS_015.56` in `rom/` (SHA1 `76322eeade5ebb22dca57fdeac7d68c30f06308d`).

### IN PROGRESS
- Nothing in progress in this mirror. No open PRs, no releases. Upstream (cawfee) work is early-stage by its own README — this mirror is a snapshot of that state, not an active fork.

### BLOCKED
- Nothing blocked here — but be honest about the state: this decomp is incomplete. If the owner needs LSD code that works, the complete repos (`lsd-decomp`, `lsddecomp`) are the ones to use. Do not build plans on this repo as if it were complete.

## 3. What we're working toward

Reference only, for now. This repo is kept so the early-stage cawfee approach stays available for comparison — different segmentation, different names, different tooling (splat/maspsx via `configure.py` rather than the other repos' setups). If anyone ever resumes this lineage, the work is identifying the remaining functions and finalizing filenames. That is upstream's work or the owner's call — not a lane's to start unasked.

## 4. Standing rules that apply here

- **Branch → PR → merge, always.** Never push to `master` directly. Add-only, zero-conflict PRs, no force pushes.
- **Checkpoint-and-save law:** CHECKPOINT.md first, update after every step; the repo is the save; resume, never restart.
- **No-temp-storage law:** nothing in /tmp or any wipeable location, ever. Everything goes straight into the repo or a durable folder the second it exists.
- **Real-source-only:** this whole repo IS real decomp work. Never substitute a guess for a function that hasn't been identified — the README is explicit that names and files are not final.
- **Licence/source logged honestly:** fan project, not affiliated with Asmik Ace, OutSide Directors Company, Osamu Sato, or Sony. You need your own copy of the game to build anything. Credit: FirecatFG's decompilation for the original toolchain and initial segments.
- **Never kill in-progress work.** Never delete game files or other lanes' work without the standing verification rules.

## 5. Key files and paths

| What | Where |
|---|---|
| Build setup | `configure.py`, `tools/quiet_ninja.py` (`split`, `check`), `requirements.txt` |
| Game code | `src/`, `include/`, `config/` |
| Game executable (yours, not in repo) | `rom/SLPS_015.56` |
| Related repos (NOT this one) | `mhvnsnt/lsd-decomp`, `mhvnsnt/lsddecomp`, `mhvnsnt/lsddecomp-1`, `mhvnsnt/LSDRevamped`, `mhvnsnt/libLSD` |

## 6. Open decisions needing the owner

- **Does this lineage get any more work?** The complete decomps exist. Whether the cawfee approach is worth resuming — or this mirror just stays as a reference snapshot — is his call.

## 7. How to pick up

1. Read this HANDOFF.md first, then `README.md`.
2. To build: Linux or WSL2, Python 3.8+, your own `SLPS_015.56` in `rom/`; `python3 configure.py setup`, then `python3 configure.py`, then `python3 tools/quiet_ninja.py split` and `check`. The built executable's hash must pass the check.
3. Never commit game data. Never push to `master` directly.
4. Land work branch → PR → merge, add-only, base branch `master`.
5. Update this HANDOFF.md in the same PR when the state changes.
