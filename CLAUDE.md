# OpenWolf

This project uses OpenWolf for context management. The always-on rules live in `.claude/rules/openwolf.md`; the hooks handle bookkeeping (anatomy index, memory log, read tracking) automatically.

For the full operating protocol (session handoff, memory discipline, bug logging), load the `openwolf` skill, or read `.wolf/OPENWOLF.md`. Regenerate the session handoff with `/handoff`.


# Claude project context

Use `.ai-context/` as the canonical shared project context when analyzing or changing this repository. Read the relevant feature, removal, risk, and architecture guidance, then verify all conclusions against the source manifests and the selected upstream chart.

This file is only a provider adapter; it is not a substitute for source code or explicit project rules.
