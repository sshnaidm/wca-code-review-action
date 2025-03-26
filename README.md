# Watson AI Code Review Action

A GitHub Action that automatically performs code reviews on pull requests using IBM Watson Code Assistant AI. The action analyzes code changes and provides feedback as a comment on the pull request.

## Features

- Automated code review on pull requests
- Customizable review prompts
- Support for including context from additional files
- Configurable context lines for better diff understanding
- Error handling with optional error reporting

## Usage

Add the following workflow to your repository at `.github/workflows/code-review.yml`:

```yaml
name: Code Review

on: [pull_request]

jobs:
  review:
    runs-on: ubuntu-latest
    permissions:
      contents: read
      pull-requests: write
    steps:
      - uses: actions/checkout@v4
      - uses: sshnaidm/wca-code-review-action@v1
        with:
          wca-key: ${{ secrets.IAM_APIKEY }}
```

## Prerequisites

1. IBM Watson Code Assistant API key
   - Add the API key to your GitHub repository secrets as `IAM_APIKEY`

## Configuration Options

| Input | Description | Required | Default |
|-------|-------------|----------|---------|
| `wca-key` | IBM Watson Code Assistant API key | Yes | - |
| `github-token` | GitHub token for API authentication | No | `${{ github.token }}` |
| `prompt` | Custom prompt for the AI review | No | Default review prompt |
| `post-if-error` | Post comment even if review fails | No | `true` |
| `context-lines` | Number of context lines in diff | No | `10` |
| `add-files` | Include all changed files in review | No | `false` |

## Advanced Usage Examples

### Custom Review Prompt

```yaml
- uses: sshnaidm/wca-code-review-action@v1
  with:
    wca-key: ${{ secrets.IAM_APIKEY }}
    prompt: |
      Please review this code with focus on:
      - Security issues
      - Performance optimizations
      - Best practices
```

### Include Additional Context

```yaml
- uses: sshnaidm/wca-code-review-action@v1
  with:
    wca-key: ${{ secrets.IAM_APIKEY }}
    add-files: 'true'
    context-lines: '20'
```

## Outputs

The action provides the following outputs:

- `results`: The complete results of the code review

## Error Handling

By default, the action will post a comment even if the review process encounters an error. This behavior can be disabled by setting `post-if-error: 'false'`.

## License

This project is licensed under the Apache License 2.0 - see the [LICENSE](LICENSE) file for details.

## Contributing

Contributions are welcome! Please feel free to submit a Pull Request.

## Support

For issues and feature requests, please open an issue in the GitHub repository.
