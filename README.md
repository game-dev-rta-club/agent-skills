# Rubber Ducking Skill

[![CI](https://github.com/game-dev-rta-club/rubber-ducking-skill/actions/workflows/ci.yml/badge.svg)](https://github.com/game-dev-rta-club/rubber-ducking-skill/actions/workflows/ci.yml)
[![Release](https://img.shields.io/github/v/release/game-dev-rta-club/rubber-ducking-skill)](https://github.com/game-dev-rta-club/rubber-ducking-skill/releases/latest)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

Independent second-pass review for Codex and Claude Code.

The package pairs a caller that opens and continues a focused review with a
partner that challenges plans, decisions, implementations, and final drafts.

## Install

### Codex

```sh
codex plugin marketplace add game-dev-rta-club/rubber-ducking-skill
codex plugin add rubber-ducking-skill@game-dev-rta-club
```

### Claude Code

```sh
claude plugin marketplace add game-dev-rta-club/rubber-ducking-skill
claude plugin install rubber-ducking-skill@game-dev-rta-club
```

### Upgrade from `agent-skills`

Version 2.0.0 renamed the plugin as well as the repository. Remove the old
plugin before refreshing the marketplace so that both identities are not left
installed.

Codex:

```sh
codex plugin remove agent-skills@game-dev-rta-club
codex plugin marketplace upgrade game-dev-rta-club
codex plugin add rubber-ducking-skill@game-dev-rta-club
```

Claude Code:

```sh
claude plugin uninstall agent-skills@game-dev-rta-club
claude plugin marketplace update game-dev-rta-club
claude plugin install rubber-ducking-skill@game-dev-rta-club
```

## How it works

| Skill | Role |
| --- | --- |
| [`rubber-duck-caller`](skills/rubber-duck-caller/SKILL.md) | Opens a review before non-trivial work and checks again as evidence or decisions change. |
| [`rubber-duck-partner`](skills/rubber-duck-partner/SKILL.md) | Challenges the caller's current plan, evidence, implementation, or draft without taking over the task. |

Use `rubber-duck-caller` in normal work. It invokes `rubber-duck-partner` as
the internal second role.

Try it with:

```text
Use rubber-duck-caller to pressure-test this migration plan before changing production.
```

## Safety

These skills contain instructions and have no runtime dependencies. Review the
source before installing and review proposed tool actions before approving
them. Report vulnerabilities through [SECURITY.md](SECURITY.md).

## Community

Use [GitHub Issues](https://github.com/game-dev-rta-club/rubber-ducking-skill/issues)
for bugs and ideas. Contributions and forks are welcome; see
[CONTRIBUTING.md](CONTRIBUTING.md). Participation is governed by the
[Code of Conduct](CODE_OF_CONDUCT.md).

This volunteer-maintained project does not guarantee response times, releases,
fixes, or long-term maintenance. General contact is available through the
[Game Dev RTA Club Google Group](https://groups.google.com/g/game-dev-rta-club).

## License

[MIT](LICENSE) © 2026 Game Dev RTA Club.
