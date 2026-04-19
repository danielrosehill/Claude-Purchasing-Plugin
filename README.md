# purchasing

Claude Code plugin for running purchasing decisions end-to-end — from intake and spec, through research and comparison, to a recommendation and (optionally) a PDF report. Covers three purchasing surfaces: general consumer/business purchasing, technical rig procurement, and vendor/content recommendations.

Part of the [danielrosehill Claude Code marketplace](https://github.com/danielrosehill/Claude-Code-Plugins).

## What you get

### Primitives (always available once the plugin is installed)

**General-purchasing commands** (`/purchasing:*`):
- `intake` — build the per-purchase spec (`spec.md`)
- `research` — evaluate candidates against the spec
- `compare` — side-by-side comparison of 2–4 shortlisted products
- `evaluate` — quick one-off evaluation of a single product
- `recommend` — generate the final PDF recommendation report
- `recompare` — re-run the shortlist against the current spec
- `extract` — pull product data from screenshots, PDFs, and catalogs
- `market-check` — local vs international price realism with import costs
- `load-preferences` / `save-preferences` — standing preferences to/from Mem0
- `apply-profile` — bias this purchase toward a named buyer archetype (BIFL, budget, minimalist, etc.)
- `update-spec` — targeted edit to `spec.md`

**Tech-procurement commands** (`/purchasing:rig-*`):
- `rig-setup` — initial hardware-planning interview
- `rig-profile` — document a specific machine's hardware
- `rig-analyze` — identify bottlenecks and upgrade opportunities
- `rig-compare` — compare specific components
- `rig-recommend` — generate upgrade recommendations
- `rig-estimate` — produce a formal cost estimate document

**Vendor-recommendations commands** (`/purchasing:rec-*`):
- `rec-onboard` — first-run preference capture (format + availability)
- `rec-more-like-this` — similar-item recommendations from a seed
- `rec-log-feedback` — record like / dislike on past recommendations and update the profile
- `rec-list` — surface recommendation history and feedback status
- `rec-opml-ingest` / `rec-reading-list-ingest` / `rec-watch-history-ingest` — bulk-seed preferences from exports

**Agents**:
- `manufacturer-research`, `price-comparison`, `product-extraction`, `review-aggregation`, `spec-verification` — research sub-agents for the general-purchasing flow
- `preference-curator`, `recommender` — recommendation-profile and suggestion sub-agents

### Provisioning skill

- `/purchasing:new-workspace <name> [--variant=general-purchasing|tech-procurement|vendor-recommendations] [--local-only] [--private]`

Scaffolds a new workspace from one of three templates, personalises `CLAUDE.md` from `~/.claude/CLAUDE.md`, and (by default) creates a public GitHub repo for it.

## Pattern

Primitives live in the plugin → globally available from any cwd.
Workspace scaffolds are provisioned as **data** → no `.claude/` tree inside provisioned workspaces.
Plugin updates never touch your workspace data.

See [PLAN.md in Claude-Workspace-Reshaping-190426](https://github.com/danielrosehill/Claude-Workspace-Reshaping-190426) for the full pattern spec this plugin follows.

## Variants

- `general-purchasing` (default) — one-purchase-per-repo workflow with spec, buyer profiles, research, and PDF report.
- `tech-procurement` — hardware rig planning: profile existing machines, analyse bottlenecks, recommend components, produce a formal cost estimate.
- `vendor-recommendations` — ongoing content/vendor recommendation workspace: learns preferences over time, generates similar-item suggestions, tracks feedback.

## Install

Via the danielrosehill marketplace:

```
/plugin marketplace add danielrosehill/Claude-Code-Plugins
/plugin install purchasing
```

## License

MIT.
