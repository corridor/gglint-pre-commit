# gglint-pre-commit

[gglint](https://github.com/corridor/gglint)'s hooks for [pre-commit](https://pre-commit.com)
and [prek](https://github.com/j178/prek). They stop a commit that writes a secret into the
config or instruction files of a coding agent, such as `.mcp.json`, `.cursor/mcp.json` or
`CLAUDE.md`, and can check that every agent in the repository gets the same MCP servers.

```yaml
# .pre-commit-config.yaml
repos:
  - repo: https://github.com/corridor/gglint-pre-commit
    rev: v0.5.0
    hooks:
      - id: gglint-secrets
      # Also check that every agent gets the same MCP servers:
      # - id: gglint-mcp
```

pre-commit installs gglint from PyPI, as a program built for the machine, so nothing else is
needed: not uv, Node or Rust. It runs on Linux, macOS and Windows.

| Hook             | Runs                        | When a commit changes                       |
| ---------------- | --------------------------- | ------------------------------------------- |
| `gglint-secrets` | `gglint secrets FILE...`    | an agent's config or instruction file       |
| `gglint-mcp`     | `gglint mcp --format lines` | an agent's MCP config file                  |

Each gglint release is published here within the hour, tagged with its version, and
`pre-commit autoupdate` moves to the newest. The files are written from gglint's own
repository: send issues and changes to [corridor/gglint](https://github.com/corridor/gglint),
and see [the documentation](https://corridor.github.io/gglint/guides/pre-commit/).
