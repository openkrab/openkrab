---
summary: "CLI reference for `openkrab reset` (reset local state/config)"
read_when:
  - You want to wipe local state while keeping the CLI installed
  - You want a dry-run of what would be removed
title: "reset"
---

# `openkrab reset`

Reset local config/state (keeps the CLI installed).

```bash
openkrab reset
openkrab reset --dry-run
openkrab reset --scope config+creds+sessions --yes --non-interactive
```
