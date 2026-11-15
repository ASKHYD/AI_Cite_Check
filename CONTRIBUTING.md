# Contributing / commit rules (CiteCheck)

This repo is built by one owner with an AI builder (Antigravity) and an
auditor (Milo). The rules below are ratified project decisions, not advice.

## Roles (D-04)
- The builder runs no git and no network.
- The owner (Abdul) runs all git himself and pastes outputs for verification.
- A phase advances only on the owner's explicit approval of its artefact.

## Never commit
- Credentials, API keys, tokens, or `.env` / secrets files of any kind.
- Semantic Scholar data (its licence is not open; no S2 data in this repo,
  the corpus, or any report).
- Any real unpublished manuscript (including the owner's own papers, which
  are private prototype test inputs only and are never distributed here).
- Third-party or publisher material whose redistribution terms have not been
  checked (including publisher abstracts).

## May commit
- Code, tests, and documentation.
- The seeded evaluation corpus, together with its generation/mutation logs
  and freeze hash, once the owner has approved the freeze.
- Public registry metadata (Crossref / OpenAlex bibliographic facts) as used
  by the corpus and reports — never abstracts.

## Evidence rule (D-07)
- Tests: pytest. Lint/format gate: ruff. GitHub Actions runs the suite on push.
- Every phase return reports exact pass/fail counts and the command that
  produced them. Assertions without output are not evidence.
- Versions are pinned (D-11); an upgrade is a deliberate mini-phase with a
  full test run, never a silent bump.
