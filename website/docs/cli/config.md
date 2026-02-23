---
summary: "CLI reference for `openkrab config` (get/set/unset config values)"
read_when:
  - You want to read or edit config non-interactively
title: "config"
---

# `openkrab config`

Config helpers: get/set/unset values by path. Run without a subcommand to open
the configure wizard (same as `openkrab configure`).

## Examples

```bash
openkrab config get browser.executablePath
openkrab config set browser.executablePath "/usr/bin/google-chrome"
openkrab config set agents.defaults.heartbeat.every "2h"
openkrab config set agents.list[0].tools.exec.node "node-id-or-name"
openkrab config unset tools.web.search.apiKey
```

## Paths

Paths use dot or bracket notation:

```bash
openkrab config get agents.defaults.workspace
openkrab config get agents.list[0].id
```

Use the agent list index to target a specific agent:

```bash
openkrab config get agents.list
openkrab config set agents.list[1].tools.exec.node "node-id-or-name"
```

## Values

Values are parsed as JSON5 when possible; otherwise they are treated as strings.
Use `--strict-json` to require JSON5 parsing. `--json` remains supported as a legacy alias.

```bash
openkrab config set agents.defaults.heartbeat.every "0m"
openkrab config set gateway.port 19001 --strict-json
openkrab config set channels.whatsapp.groups '["*"]' --strict-json
```

Restart the gateway after edits.
