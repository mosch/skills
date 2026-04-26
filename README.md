# Agent Skills

A collection of agent skills for Claude Code and other coding agents.

## Planning & Design

- **to-prd** — Turn the current conversation context into a PRD and submit it as a GitHub issue. No interview — just synthesizes what you've already discussed.

  ```
  npx skills@latest add mosch/skills/to-prd
  ```

- **to-issues** — Break any plan, spec, or PRD into independently-grabbable GitHub issues using vertical slices.

  ```
  npx skills@latest add mosch/skills/to-issues
  ```

- **grill-me** — Get relentlessly interviewed about a plan or design until every branch of the decision tree is resolved.

  ```
  npx skills@latest add mosch/skills/grill-me
  ```

## Pull Requests

- **pop-pr** — Create a PR from the current branch, then start a loop that checks for review comments and CI status every 5 minutes.

  ```
  npx skills@latest add mosch/skills/pop-pr
  ```

- **pr-loop** — Go through PR review feedback one by one, prioritizing human comments over bots. Discuss each item, make changes, then push.

  ```
  npx skills@latest add mosch/skills/pr-loop
  ```

## Manual installation

```bash
git clone https://github.com/mosch/skills.git
```

Then point your agent at the cloned directory.

## License

MIT — see [LICENSE](LICENSE).
