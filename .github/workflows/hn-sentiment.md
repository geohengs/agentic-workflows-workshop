---
name: HN Sentiment Analysis
on:
  issue_comment:
    types: [created]
permissions:
  issues: write
  contents: read
network:
  allowed:
    - hacker-news.firebaseio.com
tools:
  - web-fetch
safe-outputs:
  add-comment:
    max: 1
model: gpt-4o-mini
---

Create a ChatOps slash command called /hn-sentiment. When a user posts a comment on a GitHub issue that starts with "/hn-sentiment <url>", where <url> is a Hacker News story URL (e.g. https://news.ycombinator.com/item?id=12345), do the following:
1) Extract the Hacker News item ID from the URL.
2) Fetch up to 50 top-level comments for that story from the Hacker News API.
3) Perform sentiment analysis on the comment text, classifying each comment as Positive, Negative, or Neutral.
4) Produce a summary that shows: the overall sentiment (with percentage breakdown), the top 3 most positive comments (with excerpt), and the top 3 most negative comments (with excerpt).
5) Reply to the original issue comment with the analysis formatted in Markdown.
If no URL is provided or the URL is not a valid Hacker News item, reply with a helpful error message.