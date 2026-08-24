---
{}
---

# Architecture Council runbook

> Use the Council only for an explicit on-demand decision. This is a manual Group kickoff runbook, not an automatic or scheduled runner. Create one current `architecture-review/v1` kickoff packet containing the configured input fields, then provide the same packet independently to all four reviewers. Conversation memory is not input authority.

# Architecture Council runbook

Use the Council only for an explicit on-demand decision. This is a manual Group kickoff runbook, not an automatic or scheduled runner. Create one current `architecture-review/v1` kickoff packet containing the configured input fields, then provide the same packet independently to all four reviewers. Conversation memory is not input authority.

Collect reviewer outputs without editing them into consensus. The synthesizer must retain dissent, uncertainty, conditions, unresolved risks, and the smallest reversible next step while returning one allowed outcome: `KEEP`, `MODIFY`, `EXPERIMENT`, or `ABANDON`.

The Council does not schedule work, write externally, change runtime, or persist decisions automatically. Any requested runtime or SoT change stops for explicit human approval.

The Registry Manager is read-only control-plane support: validate, diff, plan, and verify Git desired state against observed runtime evidence. It cannot operate local UI, auto-apply/delete, or derive desired state from runtime observations.
