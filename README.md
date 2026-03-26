# Agent Skills

A collection of agent skills for Claude Code and other coding agents.

## Installation

```bash
npx skills add mosch/skills
```

## Included skills

### pop-pr

Create a PR from the current branch, then start a feedback loop that checks for review comments and CI status every 5 minutes. Handles the full lifecycle: push, create PR, monitor for reviews, address feedback, and verify CI.

**Usage:** Say "pop pr", "pop a pr", or "ship it and watch"

### pr-loop

Go through PR review feedback one by one, prioritizing human comments over bots. Discuss each item, make changes together, then push.

**Usage:** Say "pr loop", "go through PR comments", or "review feedback"

## Manual installation

```bash
git clone https://github.com/mosch/skills.git
```

Then configure your agent to load skills from the cloned directory.

## Contributing

Contributions welcome!

1. Fork the repository
2. Add or improve skills in the `skills/` directory
3. Test with actual development workflows
4. Submit a pull request

## License

MIT - See [LICENSE](LICENSE) for details
