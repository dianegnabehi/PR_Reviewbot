# PR Review Bot

A GitHub Actions-based bot that uses Blackbox API to automatically review Pull Requests with AI-powered analysis, bug detection, documentation linking, and summarization.

## Features

- **Out-of-the-box**: Works immediately after setup in any GitHub repository.
- **Robust & Scalable**: Handles multiple repositories without per-repo configuration.
- **Innovative Analysis**:
  - Code review with suggestions.
  - Bug detection.
  - Documentation linking.
  - Change summarization.
- **Clear Demo**: See below for testing instructions.

## Setup

1. **Fork or Clone this repository** to your GitHub account.

2. **Add Repository Secrets** (in Settings > Secrets and variables > Actions):
   - `BLACKBOX_API_KEY`: Your Blackbox API key.
   - `BLACKBOX_API_URL`: (Optional) Blackbox API endpoint URL. Defaults to `https://api.blackbox.ai/v1/completions`.

3. **Copy the workflow** to your target repository:
   - Copy `.github/workflows/pr-review.yml` to the target repo's `.github/workflows/` directory.
   - Copy `review_pr.py` to the root of the target repo.

4. **Install Dependencies** (if running locally):
   - `pip install requests PyGithub`

## How It Works

- Triggers on PR events: opened, synchronize, reopened.
- Fetches the PR diff using GitHub API.
- Sends the diff to Blackbox API with a structured prompt for analysis.
- Posts an AI-generated comment on the PR with review insights.

## Demo

### Local Testing

1. Set environment variables:
   ```bash
   export GITHUB_TOKEN=your_github_token
   export BLACKBOX_API_KEY=your_blackbox_key
   export BLACKBOX_API_URL=https://api.blackbox.ai/v1/completions
   export GITHUB_REPOSITORY=your/repo
   export GITHUB_EVENT_PATH=/path/to/mock/event.json  # Create a mock PR event JSON
   ```

2. Run the script:
   ```bash
   python review_pr.py
   ```

### GitHub Testing

1. Create a PR in the repository where the workflow is set up.
2. The bot will automatically post a review comment.

## Customization

- Modify the prompt in `review_pr.py` to adjust analysis focus.
- Add more API integrations or post-processing logic.

## Requirements

- Python 3.9+
- GitHub Actions enabled in the repository.
- Valid Blackbox API credentials.

## License

MIT
