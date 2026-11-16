# Test plugin marketplace

A basic GitHub Copilot plugin marketplace with two independent, dependency-free
test plugins. Neither plugin needs credentials, MCP servers, hooks, or scripts.

| Plugin | Skill | Expected response |
| --- | --- | --- |
| `test-hello-2` | `test-hello-2` | `Hello from test-hello-2!` |
| `test-checklist-2` | `test-checklist-2` | A four-item unchecked smoke-test checklist |

## Install

```sh
copilot plugin marketplace add taylorreis/plugin-marketplace-2
copilot plugin marketplace browse test-marketplace-2
copilot plugin install test-hello-2@test-marketplace-2
copilot plugin install test-checklist-2@test-marketplace-2
copilot plugin list
```

Start a new Copilot session after installation. Ask it to `run test-hello-2`, then
`run test-checklist-2`. Each skill should produce the response described above
without using tools or modifying files.

## Try a local checkout

From the repository root:

```sh
copilot --plugin-dir ./plugins/test-hello-2 --plugin-dir ./plugins/test-checklist-2
```

## Layout

The marketplace catalog is in `.claude-plugin/marketplace.json`. Each entry points
to a directory under `plugins/` containing its own `.claude-plugin/plugin.json`
manifest and a skill under `skills/<skill-name>/SKILL.md`.

The catalog uses the relative-source layout demonstrated by
[GitHub's Copilot marketplace](https://github.com/github/copilot-plugins/blob/main/.claude-plugin/marketplace.json).

## Remove

```sh
copilot plugin uninstall test-hello-2@test-marketplace-2
copilot plugin uninstall test-checklist-2@test-marketplace-2
```
