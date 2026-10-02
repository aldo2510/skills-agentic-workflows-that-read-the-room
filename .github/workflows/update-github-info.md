---
name: update-github-info
on:
  schedule:
    - cron: "0 9 * * *"
  workflow_dispatch:
permissions:
  contents: read
  pull-requests: read
engine: copilot
network:
  allowed:
    - defaults
    - github.blog
    - github.com
    - awesome-copilot.github.com
tools:
  github:
    toolsets: [repos]
  web-fetch:
  edit:
safe-outputs:
  create-pull-request:
---

# Update GitHub Info

Keep the GitHub Info website current with practical, source-backed updates for developers.

1. Read `notes/mona-notes.md` and `site/content/github-info.md` before making any changes.
2. Use the GitHub repository API tools to read repository guidance and reference files. Do not use terminal, CLI, or sandboxed commands for those reads.
3. Use the `web-fetch` tool to fetch and read:
   - https://github.blog/latest/
   - https://github.blog/changelog/
  - https://awesome-copilot.github.com/workflows/
4. Identify a small set of useful, recent updates that fit Mona's editorial angle, including relevant Awesome Copilot workflows. Keep the writing short and practical, and cite the relevant source for each update.
5. Use the `edit` tool to update only `site/content/github-info.md`. Preserve its existing structure and avoid unrelated formatting changes.
6. Review the resulting diff for accuracy, concise wording, and unintended changes.
7. Commit the change on a new branch and call the `create_pull_request` safe-output tool exactly once to open a pull request for Mona to review. Do not push directly to `main`.

If neither source has a meaningful update, do not change the content and do not open a pull request.