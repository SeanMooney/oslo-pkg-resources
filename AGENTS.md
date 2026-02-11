# AGENTS.md

## What is this repo?

`oslo-pkg-resources` is a **temporary** standalone redistribution of
`pkg_resources` from setuptools v81.0.0. It exists as a **migration bridge**
for OpenStack projects (and their dependencies) that were broken when
setuptools v82 removed the `pkg_resources` module.

## Expected lifetime

This package is intentional stop-gap. Projects that depend on it should
migrate to the modern standard-library and PyPA replacements:

- `importlib.resources` (resource access)
- `importlib.metadata` (package metadata / entry points)
- `packaging` (version parsing, specifiers, markers)

Once downstream consumers have migrated, this package will be retired.

## Working in this repo

The Python code under `oslo_pkg_resources/` is **vendored from setuptools** —
do not rewrite or refactor it. Changes should be minimal and focused on:

- Packaging and distribution (`pyproject.toml`, `setup.cfg`)
- CI / linting configuration (`tox.ini`, `.pre-commit-config.yaml`)
- Documentation and metadata


## Commit messages

Follow this format exactly:

```
Subject line in imperative mood, <50 chars, no period

Body explaining WHY and WHAT. Wrap at 72 characters.

Generated-By: claude-code
Signed-off-by: Your Name <your@email.com>
Change-Id: I<hash>
```

Rules:
- Subject line must be imperative ("Add feature", not "Added feature"),
  under 50 characters, with no trailing period.
- Body wraps at 72 characters and explains the motivation and approach.
- `Signed-off-by` (DCO) is **required** — use `git commit -s` to add it
  automatically. Every commit must have this line.
- `Change-Id` is required for Gerrit-based repos. If the commit-msg hook
  is installed it is added automatically; do not fabricate one.

## AI policy

- If the commit was **generated** by an AI tool, add a `Generated-By:`
  trailer with the tool name (e.g. `Generated-By: claude-code`).
- If AI was used only for **assistance** (suggestions, review), use
  `Assisted-By:` instead.
- Document what the AI produced and note any manual modifications.
- Always review AI-generated code for correctness and security before
  committing.

## Verification

If `tox` is not installed, run it via `uvx`:

```bash
uvx tox -e pep8                      # lint / style check
uvx tox -e py3                       # unit tests
uvx pre-commit run --all-files       # run all pre-commit hooks
git commit -s                        # auto-add DCO sign-off
```
