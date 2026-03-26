---
name: pop-pr
description: >
  Create a PR from the current branch and start a loop to check for review
  feedback every 5 minutes. Use when the user says "pop pr", "pop a pr",
  "ship it and watch", or wants to create a PR and monitor it.
argument-hint: "[optional: base branch or PR URL]"
---

# Pop PR

Create a pull request from the current branch, then start a feedback loop that checks for review comments and CI status every 5 minutes.

## Step 1 — Create the PR

1. Run `git status` and `git log` to understand the current branch state
2. Determine the base branch (use the argument if provided, otherwise default to `main`)
3. Push the current branch to origin if not already pushed
4. Create the PR using `gh pr create`:
   - Write a concise title (under 70 chars)
   - Write a summary body with a `## Summary` section (bullet points) and a `## Test plan` section
   - If the branch only has one commit, use its message as the basis for the title
5. Print the PR URL so the user can see it

## Step 2 — Start the feedback loop

After the PR is created (or if the user provided an existing PR URL), invoke the `/loop` skill with a 5-minute interval to monitor the PR.

The loop prompt should be:

```
Check PR <PR_URL> for new activity:

1. Run `gh pr view <PR_URL> --json reviews,comments,statusCheckRollup,state`
2. If the PR has been **merged** or **closed**, report it and stop the loop.
3. If there are **new review comments or reviews** since the last check, summarize them and suggest how to address each piece of feedback.
4. If **CI checks failed**, fetch the failed check logs with `gh pr checks <PR_URL>` and summarize what broke.
5. If nothing new, just say "No new feedback on <PR_URL>".
```

## Notes

- If the user provides a PR URL instead of creating a new one, skip Step 1 and go straight to the loop.
- When addressing review feedback, make the code changes, commit, and push — then let the next loop iteration verify.
