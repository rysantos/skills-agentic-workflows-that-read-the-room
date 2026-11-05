---
name: update-github-info
description: Draft website updates for Mona's GitHub Info site from official GitHub sources.
on:
  workflow_dispatch:
  schedule:
    - cron: '17 9 * * *'
safe-outputs:
  create-pull-request:
    title-prefix: "[mona] "
    draft: true
    fallback-as-issue: false
    allowed-files:
      - site/content/github-info.md
tools:
  edit:
  web-fetch:
network:
  allowed:
    - github.com
    - github.blog
    - awesome-copilot.github.com
engine:
  id: copilot
  copilot-sdk: true
---

# Update Mona's GitHub Info website

Read `notes/mona-notes.md` before making changes.

Use these sources:
- `notes/mona-notes.md`
- GitHub Blog: https://github.blog/latest/
- GitHub Changelog: https://github.blog/changelog/
- Awesome Copilot workflows: https://awesome-copilot.github.com/workflows/

Web fetch the GitHub Blog, GitHub Changelog, and Awesome Copilot workflows pages. Update `site/content/github-info.md` with concise, practical updates for readers. Include source context when content comes from the GitHub Blog, GitHub Changelog, or Awesome Copilot workflows.

Create a pull request for Mona to review, using a title that mentions Mona or GitHub Info. Do not write directly to `main`; use the `safe-outputs` `create-pull-request` configuration.
