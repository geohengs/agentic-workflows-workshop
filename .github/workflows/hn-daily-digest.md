---
name: HN Daily Digest
on:
  schedule: daily on weekdays
  workflow_dispatch:
permissions:
  issues: read
  contents: read
  pull-requests: read
network:
  allowed:
    - hacker-news.firebaseio.com
tools:
  github: null
safe-outputs:
  create-issue:
    max: 1
model: gpt-4o-mini
---

Create a daily digest workflow for professional developers, referencing relevant top Hacker News stories on technology that can be used today by large companies. Every weekday, fetch the top 30 stories from the Hacker News API (https://hacker-news.firebaseio.com/v0/topstories.json), filter to stories with a score above 100 that are about software engineering, cloud infrastructure, AI/ML, developer tooling, or distributed systems. For each qualifying story include: the title, the URL, the score, the number of comments, and a one-sentence summary of why it is relevant to enterprise developers. Create a GitHub issue titled "HN Digest – <date>" with the results formatted as a Markdown table.