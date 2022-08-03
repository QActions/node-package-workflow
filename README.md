# Node Package Workflow

Used as the GitHub workflow by the services team for Node.js package.

Example of how the build and publish workflow can be used in a package repository:  
```yaml
# .github/workflows/buildAndPublish.yaml
name: Build and Publish Node Package

on:
  workflow_dispatch:
  push:
    branches:
      - master
      - dev

jobs:
  buildAndPublish:
    uses: QActions/node-package-workflow/.github/workflows/buildAndPublish.yaml@1.0.0
    secrets:
      NPM_TOKEN: ${{ secrets.NPM_PACKAGES_FULL_READ_ACCESS_TOKEN }}
      GITHUB_PACKAGES_TOKEN: ${{ secrets.GITHUB_TOKEN }}
    with:
      nodeVersion: 16.x
```

Example of how the build workflow can be used in a package repository:
```yaml
# .github/workflows/build.yaml
name: Build Node Package

on:
  workflow_dispatch:

  push:
    branches-ignore:
      - master
      - dev

jobs:
  build:
    uses: QActions/node-package-workflow/.github/workflows/build.yaml@1.0.0
    secrets:
      NPM_TOKEN: ${{ secrets.NPM_PACKAGES_FULL_READ_ACCESS_TOKEN }}
      GITHUB_PACKAGES_TOKEN: ${{ secrets.GITHUB_TOKEN }}
    with:
      nodeVersion: 16.x
```
