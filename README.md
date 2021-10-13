# Jina AI GitHub Workflow Templates

Call these workflows remotely from your Executor's repo

1. Add your secret as `EXECUTOR_SECRET`
2. CD:

```yaml
name: CD

on:
  push:
    branches:
      - main
  release:
    types:
      - created
  workflow_dispatch:
  # pull_request:

jobs:
  call-external:
    uses: jina-ai/.github/.github/workflows/cd.yml@refactor-make-callable
    with:
      event_name: ${{ github.event_name }}
    secrets:
      secret: ${{ secrets.EXECUTOR_SECRET }}
```

3. CI

```yaml
name: CI

on: [pull_request]

jobs:
  call-external:
    uses: jina-ai/.github/.github/workflows/ci.yml@refactor-make-callable
```
