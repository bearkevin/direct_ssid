# TODO - Surge Panel R2 YAML

## Plan
- [x] Clarify target: use Surge Panel script to fetch Cloudflare R2 YAML and show remaining traffic for `Nexitally` and `WCloud`.
- [x] Confirm implementation approach: convert static `panel.sgmodule` into `Panel + Script(type=generic)` dynamic panel.
- [x] Implement parser script with network/parse fallback and light cache.
- [x] Update module entries to bind panel items to script.
- [x] Validate syntax and run a static quality check.
- [x] Add review notes and usage instructions.

## Review
- Validation done:
  - `node --check panel_provider_usage.js`
  - Local VM stub test for two providers (`Nexitally`, `WCloud`) with sample YAML, output content verified.
- Behavior diff vs previous module:
  - Before: static panel text hardcoded in `panel.sgmodule`.
  - After: dynamic panel fetched from YAML URL with provider-specific parsing and cache fallback.
- Risk notes:
  - YAML schema in production may differ; script already includes fuzzy key matching and fallback window parsing, but if your key names are very custom, synonym list may need one extra mapping.
