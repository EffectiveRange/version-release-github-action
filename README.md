# version-release-github-action

Create release of uploaded artifacts with version tagging

## Features

- Create release of previously uploaded artifacts
- Move the version tag to the latest commit (useful if the release pipeline pushed any changes e.g. version strings, changelogs etc.)
- Optionally create a `latest` tag and release with the same artifacts (useful when need a dynamic reference to the latest release like `git+https://github.com/<owner>/<repo>.git@latest`)

## Inputs

- `download-name`: Name of the uploaded artifact (default: `${{ github.event.repository.name }}`)
- `create-latest`: Create an additional 'latest' tag and release (default: `true`)

## Example usage

```yaml
jobs:
  release:
    runs-on: ubuntu-latest
    steps:
      - name: Release
        uses: EffectiveRange/version-release-github-action@v1
        with:
          download-name: 'uploaded-artifacts-name'
          create-latest: 'true'
```
