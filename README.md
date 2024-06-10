# version-release-github-action

Create release of uploaded artifacts with version tagging

## Features

- Create release of previously uploaded artifacts (artifacts should be uploaded in a previous step or job)
- Move the version tag to the latest commit (useful if the release pipeline pushed any changes e.g. version strings, changelogs etc.)
- Optionally create a `latest` tag and release with the same artifacts (useful when need a dynamic reference to the latest release like `git+https://github.com/<owner>/<repo>.git@latest`)

## Inputs

- `release-version`: Version of the release (if not provided, will use the given git tag)
- `download-name`: Name of the uploaded artifact (default: `${{ github.event.repository.name }}`)
- `create-latest`: Create an additional 'latest' tag and release (default: `true`)

## Example usage

```yaml
jobs:
  release:
    runs-on: ubuntu-latest
    steps:
      - name: Checkout repository
        uses: actions/checkout@v4
      - name: Release
        uses: EffectiveRange/version-release-github-action@v1
        with:
          release-version: '1.0.0'
          download-name: 'uploaded-artifacts-name'
          create-latest: 'true'
```
