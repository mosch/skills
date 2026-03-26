---
name: pr-loop
description: >
  Go through PR review feedback one by one, prioritizing human comments over
  bot/CI comments. Use when the user says "pr loop", "review feedback",
  "go through PR comments", or wants to address PR feedback iteratively.
argument-hint: "<PR URL or number>"
---

# PR Loop

Go through the feedback on a pull request one by one together with the user. Prioritize human feedback over robots.

## Steps

1. Fetch all review comments, reviews, and check results for the PR using `gh pr view <PR> --json reviews,comments,reviewThreads,statusCheckRollup`
2. Sort feedback into two groups:
   - **Human feedback**: comments and reviews from real people
   - **Bot feedback**: comments from bots, CI check failures, and automated reviews
3. Present human feedback first, then bot feedback. For each piece of feedback:
   - Show who left it, on which file/line, and what they said
   - Discuss with the user how to address it
   - Make the agreed-upon changes, commit, and move to the next item
4. After all feedback is addressed, push the changes and summarize what was done.
