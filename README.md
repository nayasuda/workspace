# Google Workspace Extension for Gemini CLI (WSL-Ready Fork)

[日本語版 / Japanese README](./README.ja.md)

> This repository is an **unofficial fork** of [gemini-cli-extensions/workspace](https://github.com/gemini-cli-extensions/workspace), focused on improving usability in WSL environments.

The Google Workspace extension for Gemini CLI brings the power of Google Workspace apps to your command line. Manage documents, spreadsheets, presentations, emails, chat, and calendar events without leaving your terminal.

## Why this fork exists

This fork adds practical improvements for WSL authentication flow, especially around browser launch behavior during OAuth.

## What is changed

- WSL-aware browser launch fallback
  - `wslview` first
  - fallback to `cmd.exe /c start`
- Optional manual authentication mode
  - `WORKSPACE_OAUTH_MANUAL=1` prints auth URL for copy/paste
- Minor reliability improvements for WSL authentication flow

## Prerequisites

Before using the extension, you need to be logged into your Google account.

## Installation

`gemini extensions install https://github.com/nayasuda/gemini-workspace-wsl`

## Recommended for team usage

Use a **fixed release tag** instead of tracking `main` for stability and reproducibility.

Example tag:
- `v0.0.5-wsl1`

## Usage on WSL

This fork includes WSL-specific support. During authentication, it attempts to launch your Windows browser via:

1. `wslview`
2. `cmd.exe` fallback

### Requirements

Install `wslu`:

```bash
sudo apt install wslu
```

### Manual Authentication Mode

If browser launch fails, or if you prefer copy/paste auth:

```bash
export WORKSPACE_OAUTH_MANUAL=1
```

When enabled, the extension prints the authentication URL to the console instead of launching a browser.

## Commands

Examples:

### Get Schedule
Command: `/calendar:get-schedule [date]`  
Shows your schedule for today or a specified date.

### Search Drive
Command: `/drive:search <query>`  
Searches your Google Drive for files matching the query.

## Deployment

If you want to host your own infrastructure, see the [GCP Recreation Guide](./docs/GCP-RECREATION.md).

## Resources

- [Documentation](./docs/index.md): Detailed docs for available tools
- [GitHub Issues](https://github.com/nayasuda/gemini-workspace-wsl/issues): Bugs and feature requests

## Important Security Consideration: Indirect Prompt Injection

When exposing any language model to untrusted data, there is a risk of indirect prompt injection.  
This MCP server can read/modify/delete data in your Google account and shared resources.

- Never use this with untrusted tools
- Never include untrusted inputs into model context
- Review all agent actions carefully before relying on results

## Contributing

Contributions are welcome. Please read [CONTRIBUTING.md](./CONTRIBUTING.md).

## Legal

- License: [Apache License 2.0](./LICENSE)
- Terms of Service: https://policies.google.com/terms
- Privacy Policy: https://policies.google.com/privacy
- Security Policy: [SECURITY.md](./SECURITY.md)

## Upstream

Original repository: [gemini-cli-extensions/workspace](https://github.com/gemini-cli-extensions/workspace)
