---
name: update-github-info
description: Keep the GitHub Info page current with concise developer-focused updates.
on:
  schedule:
    - cron: "0 9 * * *"
  workflow_dispatch:
permissions:
  contents: read
  pull-requests: read
engine: copilot
tools:
  edit:
  web-fetch:
network:
  allowed:
    - github.blog
    - github.com
safe-outputs:
  create-pull-request:
    title-prefix: "[github-info] "
    labels:
      - documentation
    draft: true
    max: 1
---

Read `notes/mona-notes.md` before making any changes.

Fetch and review the latest public GitHub updates from:

- https://github.blog/latest/
- https://github.blog/changelog/

Use the fetched material to update `site/content/github-info.md` with short, practical summaries that help developers learn GitHub faster. Mention the source URL whenever an update comes from the GitHub Blog or GitHub Changelog. Preserve the existing format and make only relevant, focused changes. Do not modify any other files.

After reviewing the resulting diff, create exactly one draft pull request with the `create_pull_request` safe output for Mona to review. Use a concise title and explain which GitHub updates were added, including their source links. Do not push changes manually or write directly to `main`.