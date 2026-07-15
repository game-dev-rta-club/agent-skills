# Agent Skills

[![CI](https://github.com/game-dev-rta-club/agent-skills/actions/workflows/ci.yml/badge.svg)](https://github.com/game-dev-rta-club/agent-skills/actions/workflows/ci.yml)
[![Release](https://img.shields.io/github/v/release/game-dev-rta-club/agent-skills)](https://github.com/game-dev-rta-club/agent-skills/releases/latest)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

A repository for small, reusable Agent Skills that add focused workflows to
Codex and Claude Code.

Each skill is kept independently understandable. Related skills may cooperate,
but the repository itself is a collection rather than a single framework or
methodology.

## Install

Installing the plugin makes every skill in the repository available to the
agent.

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

## Currently available

### Rubber-ducking

The first included workflow gives the working agent an independent reviewer.
It can challenge plans, decisions, drafts, code, and proposed answers while the
original agent remains responsible for the work.

| Skill | Role |
| --- | --- |
| [`rubber-duck-caller`](skills/rubber-duck-caller/SKILL.md) | Opens and continues an independent review dialogue during non-trivial work. This is the skill users normally invoke. |
| [`rubber-duck-partner`](skills/rubber-duck-partner/SKILL.md) | Acts as the focused reviewer inside that dialogue. The caller invokes it internally. |

Try it with:

```text
Use rubber-duck-caller to pressure-test this migration plan before changing production.
```

For a trivial question or a direct answer that needs no second opinion, skip
the dialogue.

## Project-local install

To review and commit the exact skill files with a project, use
[`gh-linked-skills`](https://github.com/game-dev-rta-club/gh-linked-skills):

```sh
gh linked-skills install game-dev-rta-club/agent-skills --all --tag v1.0.0
git add .agents/skills .gh-linked-skills.json
git commit -m "chore: install agent skills"
```

This writes every currently published skill to `.agents/skills/` and records
the source tag and revision in `.gh-linked-skills.json`.

## Repository structure

Each skill lives directly under `skills/` and starts with a `SKILL.md` file.
A skill may also include its own references, scripts, or assets when needed.

```text
skills/
├── rubber-duck-caller/
│   └── SKILL.md
└── rubber-duck-partner/
    └── SKILL.md
```

Related skills use a shared name prefix instead of nested skill directories.
New skills do not need to participate in the rubber-ducking workflow.

## Trust and scope

- The currently included skills are instruction-only and have no runtime
  dependencies.
- Skill source remains in this repository so it can be reviewed before use.
- CI validates skill layout, known cross-skill relationships, and Codex and
  Claude Code plugin metadata.
- Releases provide stable points to review and install.

Agent instructions are trusted input. Read a skill before installing it, and
review proposed tool actions just as you would without the skill. Report
vulnerabilities privately as described in [SECURITY.md](SECURITY.md).

## Development

Requirements: Node.js 20 or later.

```sh
npm ci
npm test
claude plugin validate .
```

The Claude validation command is only required when changing Claude plugin or
marketplace metadata.

To propose another reusable workflow, add a self-contained skill under
`skills/` and describe its user-visible purpose in this catalog.

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
