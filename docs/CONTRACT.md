# Patcher contract

Do not implement against folklore. Implement against this file.

## Identity

- Product: **Patcher**
- Repo: `computerpets-patcher`
- Category: Utility Tools
- Idea: Auto-Updater
- Port / surface: `8742`

## Must

- Stay canon with 210 species. No illegal hybrids. No swapped voices.
- Treat the desktop overlay as the main quest. This organ is optional until wired.
- Fail soft: the overlay keeps walking if this service is down, unless this *is* the overlay.
- No PII in public artifacts (Steam id, wallet, home path, webcam frames).

## Data

Channel(stable|beta) · Release(semver, sha256, sig) · Delta(from, to, size)

## Surface

- GET /v1/latest?channel=stable — version + urls + signatures
- GET /v1/delta?from=&to= — patch blob
- POST /v1/health — daemon ping

## Neighbors

- computerpets desktop
- computerpets-steamgate
- computerpets-forensics

## Failure doctrine

Bad signature → refuse, tray warning. Partial download → resume. Overlay running → apply on next quit, never mid-walk.

## Stack

Go or Java daemon · delta patches · SteamPipe optional · code-signed Windows/macOS/Linux
