# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Repository Purpose

This is a test repository used for testing commit workflows and path-to-production tools across both GitHub and GitLab platforms. It maintains synchronized mirrors:
- GitHub: https://github.com/darkin100/commit-changes-testing
- GitLab: https://gitlab.com/darkin1001/commit-changes-testing

## Core Workflow

The repository centers around a simple counter increment workflow in `dummycommit.txt`. The file contains a single integer that gets incremented to test PR/MR automation across both platforms.

### Git Remotes

- `origin`: GitHub (https://github.com/darkin100/commit-changes-testing.git)
- `gitlab`: GitLab (https://gitlab.com/darkin1001/commit-changes-testing.git)

### Custom Slash Commands

Three custom slash commands automate the counter increment workflow:

- `/push-pr`: Increments counter, commits, pushes to both GitHub and GitLab, and creates PR/MR on both platforms
- `/pr-github`: Same workflow but only for GitHub
- `/pr-gitlab`: Same workflow but only for GitLab

All commands follow this pattern:
1. Read current number from `dummycommit.txt`
2. Increment by 1
3. Write back to file
4. Commit with message "Increment counter to [new_number]"
5. Push to branch "increment-[new_number]"
6. Create PR/MR with consistent title and body

## CI/CD Pipelines

### GitHub Actions (`.github/workflows/github-actions-demo.yml`)

Runs on pull requests and executes a code review using the `darkin100/i-am-reviewed@v1.0` action. Requires these secrets:
- `GOOGLE_CLOUD_PROJECT`
- `GOOGLE_CLOUD_LOCATION`
- `GOOGLE_CLOUD_CREDENTIALS`

### GitLab CI (`.gitlab-ci.yml`)

Runs on merge request events using Docker-in-Docker to execute a PR review agent. Environment variables include:
- GitLab CI variables (auto-provided)
- Google Cloud credentials (must be set as CI/CD variables)

Uses the image: `europe-west2-docker.pkg.dev/iamreleased/docker-images/pr-review-agent-gitlab:latest`

## Claude Code Permissions

The `.claude/settings.local.json` pre-authorizes common git operations:
- Git add, commit, checkout, push, fetch
- GitHub PR creation via `gh` CLI
- GitLab MR creation and viewing via `glab` CLI
- Homebrew installations

These commands won't require additional user approval when executed by Claude Code.
