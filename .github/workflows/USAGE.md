# Documentation

## Using the Auto Merge and Release Workflow

Call this workflow from another workflow file:

```yaml
name: Release Workflow

on:
  workflow_dispatch:
    inputs:
      release-branch:
        description: 'Target branch for release'
        required: false
        default: 'main'
        type: string

jobs:
  release:
    uses: tastyigniter/workflows/.github/workflows/auto-merge-release.yml@main
    with:
      release-branch: ${{ inputs.release-branch || 'main' }}
    secrets:
      ACCESS_TOKEN: ${{ secrets.ACCESS_TOKEN }}
```
