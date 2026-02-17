# Claude Code Permissions Reference

Documentation for `.claude/settings.local.json` permission rules.

## Allow Rules

| Rule | Description |
|------|-------------|
| `Bash(npm run *)` | Run any npm script (dev, build, lint, etc.) |
| `Bash(npm install *)` | Install packages |
| `Bash(npm test *)` | Run tests |
| `Bash(git status)` | Check repo status |
| `Bash(git add *)` | Stage files for commit |
| `Bash(git commit *)` | Create commits |
| `Bash(git log *)` | View commit history |
| `Bash(git diff *)` | View file changes |
| `Read` | Read any file (except denied ones) |
| `Edit(./src/**)` | Edit source code files |
| `WebFetch(domain:github.com)` | Fetch from GitHub |

## Deny Rules

| Rule | Description |
|------|-------------|
| `Bash(rm -rf *)` | Prevent recursive force delete (dangerous) |
| `Bash(git push *)` | Prevent pushing without review |
| `Bash(git reset --hard *)` | Prevent losing uncommitted changes |
| `Bash(npm publish *)` | Prevent accidental package publishing |
| `Read(./.env)` | Protect environment secrets |
| `Read(./.env.*)` | Protect all env file variants |
| `Read(./secrets/**)` | Protect secrets directory |
| `Edit(./package-lock.json)` | Prevent lockfile corruption |
| `Bash(sudo *)` | Prevent privilege escalation |
| `Bash(chmod 777 *)` | Prevent overly permissive file permissions |
| `Bash(rm -r *)` | Prevent recursive delete |
| `Bash(> *)` | Prevent file truncation |
| `Bash(curl * \| bash)` | Prevent piping scripts to shell |
| `Read(./**/credentials*)` | Protect credential files |
| `Read(./**/*.pem)` | Protect certificates |
| `Read(./**/*.key)` | Protect private keys |
| `Edit(./.github/**)` | Protect CI/CD workflows |

## Notes

- Deny rules always take precedence over allow rules
- `*` matches within a single directory
- `**` matches recursively across directories
- Use `/permissions` command in Claude Code to view active rules
