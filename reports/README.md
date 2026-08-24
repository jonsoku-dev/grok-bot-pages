---
{}
---

# Reports

> `reports/current/results.md` is the current user-facing summary. `reports/daily/` and
`reports/weekly/` are dated pointers to source-bound archive reports; they do not maintain
independent fact copies.

# Reports

`reports/current/results.md` is the current user-facing summary. `reports/daily/` and
`reports/weekly/` are dated pointers to source-bound archive reports; they do not maintain
independent fact copies.

Long-term reports are stored under
`reports/archive/YYYY/MM/DD/<type>.md`. The path date must match frontmatter,
and approved reports preserve Git history. Only reader-facing intelligence outputs belong in
`reports/**`. System state, rollout receipts, runtime snapshots, and audit events belong under
`docs/**`, `runtime/**`, and `audit/**` and are never report types.

Every approved intelligence article must reference validated records under
`intelligence/signals/YYYY/MM/DD/<kind>/<region>/<id>.yaml`. Run
`npm run validate:intelligence` and `npm run validate:reports` before publishing.

Delivery routines reject missing, stale, or unapproved source material instead of substituting
conversation summaries. `npm run report:render -- --type <type> --date YYYY-MM-DD` renders a
deterministic draft; it cannot overwrite an existing archive report.
