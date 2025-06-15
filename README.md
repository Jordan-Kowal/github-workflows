# ✨ GitHub Workflows ✨

- [✨ GitHub Workflows ✨](#-github-workflows-)
  - [⚡ Available Workflows](#-available-workflows)
    - [🤖 Update UV Lockfile](#-update-uv-lockfile)
      - [Requirements](#requirements)
      - [Inputs](#inputs)
      - [Example](#example)

## ⚡ Available Workflows

### 🤖 Update UV Lockfile

This workflow automatically updates your Python dependencies using `uv` and creates a pull request with the changes.

#### Requirements

- Python project that uses `uv` as a project manager
- A `GITHUB_TOKEN` secret in the project secret variables

#### Inputs

| Input | Description | Required | Default |
|-------|-------------|----------|---------|
| `base_branch` | Branch to create PR against | No | `main` |
| `branch` | Branch to create the PR from | No | `update-uv` |
| `pr_title` | Title for the pull request | No | `[Deps] Update uv lockfile` |
| `working_directory` | Directory containing the Python project | No | `.` |

#### Example

```yaml
name: Update uv lockfile

on:
  workflow_dispatch:
  schedule:
    - cron: '0 0 * * 1'  # Run weekly on Monday

jobs:
  update-deps:
    uses: ./.github/workflows/update-uv-lockfile.yml
    # Optional parameters
    with:
      base_branch: main
      branch: update-deps
      pr_title: '[Deps] Update uv lockfile'
      working_directory: .
```
