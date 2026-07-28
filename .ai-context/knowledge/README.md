# Project knowledge

`.ai-context/` contains generated, evidence-based context for agents. The `knowledge/` tree contains compact lifecycle guidance that is useful when extending or removing a subsystem.

- Generated facts are marked by their source paths and should be rechecked against source.
- Inferred relationships are explicitly labeled `inferred`.
- Human-authored decisions or rules must be preserved during refreshes; none were found during this initial analysis.
- Secret values are never copied into this knowledge base. Secret-bearing paths are named only when their existence affects safe maintenance.
