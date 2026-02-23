---
summary: "CLI reference for `openkrab approvals` (exec approvals for gateway or node hosts)"
read_when:
  - You want to edit exec approvals from the CLI
  - You need to manage allowlists on gateway or node hosts
title: "approvals"
---

# `openkrab approvals`

Manage exec approvals for the **local host**, **gateway host**, or a **node host**.
By default, commands target the local approvals file on disk. Use `--gateway` to target the gateway, or `--node` to target a specific node.

Related:

- Exec approvals: [Exec approvals](/tools/exec-approvals)
- Nodes: [Nodes](/nodes)

## Common commands

```bash
openkrab approvals get
openkrab approvals get --node <id|name|ip>
openkrab approvals get --gateway
```

## Replace approvals from a file

```bash
openkrab approvals set --file ./exec-approvals.json
openkrab approvals set --node <id|name|ip> --file ./exec-approvals.json
openkrab approvals set --gateway --file ./exec-approvals.json
```

## Allowlist helpers

```bash
openkrab approvals allowlist add "~/Projects/**/bin/rg"
openkrab approvals allowlist add --agent main --node <id|name|ip> "/usr/bin/uptime"
openkrab approvals allowlist add --agent "*" "/usr/bin/uname"

openkrab approvals allowlist remove "~/Projects/**/bin/rg"
```

## Notes

- `--node` uses the same resolver as `openkrab nodes` (id, name, ip, or id prefix).
- `--agent` defaults to `"*"`, which applies to all agents.
- The node host must advertise `system.execApprovals.get/set` (macOS app or headless node host).
- Approvals files are stored per host at `~/.openkrab/exec-approvals.json`.
