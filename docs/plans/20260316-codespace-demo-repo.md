# GitHub Codespace Demo Repo for tx CLI

## Overview
Create a `texops/demo` GitHub repo that lets prospective users evaluate the `tx` CLI in a browser-based Codespace. The repo contains a sample LaTeX document (testmath from CTAN), a devcontainer that pre-installs Go and `tx`, and a README walking through the full workflow: login, init, build.

## Context (from brainstorm)
- Target audience: prospective users evaluating tx on their own
- Single document: testmath.tex from CTAN (amsmath test file)
- No `.texops.yaml` committed — users run `tx init` to experience the full flow
- Auth: assume users already have a TexOps account
- Repo: `texops/demo` on GitHub

## Development Approach
- No tests needed — this is a static demo repo (config + docs + sample tex file)
- Each task is a file to create
- Validate devcontainer.json syntax manually

## Implementation Steps

### Task 1: Create devcontainer.json

**Files:**
- Create: `.devcontainer/devcontainer.json`

- [x] Create `.devcontainer/devcontainer.json` using `mcr.microsoft.com/devcontainers/go:1.24` as base image
- [x] Add `postCreateCommand` to run `go install github.com/texops/tx@latest`
- [x] Validate JSON syntax

### Task 2: Add testmath.tex

**Files:**
- Create: `testmath.tex`

- [ ] Fetch testmath.tex from `https://raw.githubusercontent.com/latex3/latex2e/main/required/amsmath/testmath.tex`
- [ ] Place it at repo root as `testmath.tex`
- [ ] Verify it contains `\documentclass` (needed for `tx init` discovery)

### Task 3: Write README.md

**Files:**
- Create: `README.md`

- [ ] Add title and one-line description of what this repo is
- [ ] Add "Open in GitHub Codespaces" badge linking to `texops/demo`
- [ ] Write step-by-step instructions:
  1. Open in Codespace (click badge)
  2. `tx login` — authenticate with TexOps
  3. `tx init` — accept defaults (texlive:2021, pdflatex)
  4. `tx build` — compile, PDF appears in working directory
- [ ] Add brief "What happened?" section explaining the cloud build flow
- [ ] Add link to tx repo and TexOps for more info

### Task 4: Create the GitHub repo and push

- [ ] Create `texops/demo` repo on GitHub (public, no template)
- [ ] Push all files
- [ ] Verify Codespace launches and `tx` is available after container build

### Task 5: Move plan to completed

- [ ] Move this plan to `docs/plans/completed/`

## Technical Details

**devcontainer.json structure:**
```json
{
  "name": "TexOps Demo",
  "image": "mcr.microsoft.com/devcontainers/go:1.24",
  "postCreateCommand": "go install github.com/texops/tx@latest"
}
```

**testmath.tex source:** `https://raw.githubusercontent.com/latex3/latex2e/main/required/amsmath/testmath.tex`

**Codespace badge markdown:**
```markdown
[![Open in GitHub Codespaces](https://github.com/codespaces/badge.svg)](https://codespaces.new/texops/demo)
```

## Post-Completion

**Manual verification:**
- Launch a Codespace from the repo and walk through the full README flow
- Confirm `tx` binary is on PATH after container creation
- Confirm `tx init` discovers testmath.tex
- Confirm `tx build` produces testmath.pdf
