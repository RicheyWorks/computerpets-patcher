# Patcher

**Auto-Updater** — Lightweight daemon that patches the desktop client silently and verifies signatures.

Part of the [ComputerPets](https://github.com/RicheyWorks/computerpets) ecosystem. Index: [computerpets-ecosystem](https://github.com/RicheyWorks/computerpets-ecosystem).

> Status: **design scaffold**. This repository ships the contract, README, and layout so implementation can start without renaming the organ later.

## Why it exists

Friends should not re-clone GitHub to get a walk-cycle fix. Patcher is the missing .exe path the flagship README still warns is not in a store.

The flagship overlay already puts a living sticker on the real desktop (Rui first, 210 kinds). Patcher does not replace that. It is one organ.

## Stack

Go or Java daemon · delta patches · SteamPipe optional · code-signed Windows/macOS/Linux

GroupId / namespace: `com.enterprisepet.patcher`  
Default listen: `8742`

## Talks to

- computerpets desktop
- computerpets-steamgate
- computerpets-forensics

## Contract

### Data

`Channel(stable|beta) · Release(semver, sha256, sig) · Delta(from, to, size)`

### Surface

- GET /v1/latest?channel=stable — version + urls + signatures
- GET /v1/delta?from=&to= — patch blob
- POST /v1/health — daemon ping

### Failure doctrine

Bad signature → refuse, tray warning. Partial download → resume. Overlay running → apply on next quit, never mid-walk.

## Layout

```
computerpets-patcher/
  README.md           this file
  LICENSE             MIT
  docs/CONTRACT.md    the same contract, frozen for implementers
  src/                implementation lands here
```

## Run (Windows)

PowerShell, from this folder, after the flagship helpers (Git, Node LTS 22+, JDK 21 as needed):

```powershell
go build -o patcher ./cmd/patcher  (Windows: patcher.exe as a user service)
```

You do not need this service to meet Rui. The [flagship start-here](https://github.com/RicheyWorks/computerpets/blob/main/docs/START-HERE.md) is still the first pet.

## Ecosystem

| Organ | Repo |
| --- | --- |
| Flagship desktop + Spring | [RicheyWorks/computerpets](https://github.com/RicheyWorks/computerpets) |
| This organ | [RicheyWorks/computerpets-patcher](https://github.com/RicheyWorks/computerpets-patcher) |
| Full map | [RicheyWorks/computerpets-ecosystem](https://github.com/RicheyWorks/computerpets-ecosystem) |

## License

MIT. See [LICENSE](LICENSE).

---

*Two hundred ten living kinds. Keep them so a line does not go quiet.*
