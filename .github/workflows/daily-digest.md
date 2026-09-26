---
name: Daily Digest
model: gpt-4o
on:
  schedule: daily on weekdays
  workflow_dispatch:
permissions:
  issues: read
  contents: read
safe-outputs:
  create-issue:
    max: 1
---
Every weekday, create a GitHub issue that summarises all open issues
and pull requests in this repository. Group them by label. Include the
total count, the title, the author, and how long each item has been
open. Title the issue "Daily Digest – <date>".