# Agent Skills — Independent Review for Codex & Claude Code

[![CI](https://github.com/game-dev-rta-club/agent-skills/actions/workflows/ci.yml/badge.svg)](https://github.com/game-dev-rta-club/agent-skills/actions/workflows/ci.yml)
[![Release](https://img.shields.io/github/v/release/game-dev-rta-club/agent-skills)](https://github.com/game-dev-rta-club/agent-skills/releases/latest)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

Give your coding agent a second reviewer before an important plan, decision,
patch, or answer ships.

These two small Agent Skills help Codex and Claude Code open an independent
review dialogue, respond to objections, and check the work again when the
evidence changes. The original agent stays responsible for the work and the
final answer.

## Try it in 30 seconds

Install the plugin for your agent:

### Codex

```sh
codex plugin marketplace add game-dev-rta-club/agent-skills
codex plugin add agent-skills@game-dev-rta-club
```

### Claude Code

```sh
claude plugin marketplace add game-dev-rta-club/agent-skills
claude plugin install agent-skills@game-dev-rta-club
```

Then ask:

```text
Use rubber-duck-caller to pressure-test this migration plan before changing production.
```

The caller asks an independent partner to challenge the current direction,
uses the feedback to improve the work, and checks again when new evidence or a
new decision appears.

```text
your task → caller → independent partner → objections or gaps → revised work
                   ↑                                      │
                   └──────────── check again ──────────────┘
```

## When it helps

- Before committing to an architecture or migration plan
- While debugging when the first explanation feels plausible but unproven
- Before presenting code review findings or a user-facing recommendation
- During research or writing when new evidence changes the conclusion

For a trivial question or a direct answer that needs no second opinion, skip
the dialogue.

## Included skills

| Skill | Use it when |
| --- | --- |
| [`rubber-duck-caller`](skills/rubber-duck-caller/SKILL.md) | You are doing non-trivial work and want an independent review throughout the task. This is the skill users normally invoke. |
| [`rubber-duck-partner`](skills/rubber-duck-partner/SKILL.md) | Another agent asks you to act as its focused reviewer. The caller invokes this internally. |

Every skill lives directly under `skills/`. Related skills share a name prefix
instead of using nested directories.

## Project-local install

To review and commit the exact skill files with a project, use
[`gh-linked-skills`](https://github.com/game-dev-rta-club/gh-linked-skills):

```sh
gh linked-skills install game-dev-rta-club/agent-skills --all --tag v1.0.0
git add .agents/skills .gh-linked-skills.json
git commit -m "chore: install agent skills"
```

This writes the skills to `.agents/skills/` and records the source tag and
revision in `.gh-linked-skills.json`.

## Trust and scope

- The skills are instruction-only: this repository contains no skill scripts
  or runtime dependencies.
- The source is intentionally small enough to read before installation.
- CI validates the skill layout, the caller-to-partner reference, and Codex and
  Claude Code plugin metadata.
- Releases provide stable points to review and install.

Agent instructions are trusted input. Read the skill source before installing
it, and review proposed tool actions just as you would without these skills.
Report vulnerabilities privately as described in [SECURITY.md](SECURITY.md).

## Development

Requirements: Node.js 20 or later.

```sh
npm ci
npm test
claude plugin validate .
```

The Claude validation command is only required when changing Claude plugin or
marketplace metadata.

## Support and maintenance

Use [GitHub Issues](https://github.com/game-dev-rta-club/agent-skills/issues)
for reproducible bugs and proposed improvements. General contact is available
through the [Game Dev RTA Club Google Group](https://groups.google.com/g/game-dev-rta-club).

This is a volunteer-maintained project. Response times, releases, fixes, and
long-term maintenance are not guaranteed.

## Contributing

Contributions and forks are welcome. See [CONTRIBUTING.md](CONTRIBUTING.md) for
the development and pull-request process.

## License

[MIT](LICENSE) © 2026 Game Dev RTA Club.
