---
name: disciplined-development
description: Apply the user's development rules to understand, plan, implement, and verify scoped code changes with explicit authorization, minimal diffs, and evidence-based delivery. Use for software development tasks; keep platform and project-specific guidance conditional.
metadata:
  short-description: Evidence-based, scoped software development
---

# Disciplined Development

Use this skill to turn a development request into a correct, scoped, reviewable change. Treat project facts and the user's current instructions as authoritative. This skill does not grant permission for work the user has not authorized.

## Authority and authorization

Resolve conflicts in this order: the user's latest explicit instruction; confirmed project constraints and stable behavior; this skill's general rules; tool or historical defaults. Surface conflicts and material ambiguity instead of silently choosing.

Keep these states distinct: discussing a proposal, approving its direction, authorizing implementation, and authorizing external actions. A request to inspect, audit, review, or propose is read-only. Approval of a plan is not by itself approval to implement unless the user clearly says to proceed. A task authorization covers only its stated scope. Ask again only if implementation requires a material scope expansion or a separately authorized external action.

Do not commit, push, open a PR, publish, upload, make purchases, change live console data, or send project/user data externally without the applicable explicit authorization. Never expose secrets in code, logs, screenshots, artifacts, or replies.

## Working method

1. **Read project facts first.** Inspect applicable `AGENTS.md`, project documentation, stable feature baselines, relevant code/tests/assets, and the current working tree. Preserve pre-existing user changes. Distinguish fact, inference, and unknown.
2. **Define the task.** State the observed or requested outcome, acceptance conditions, affected surfaces, and what is outside scope. For a bug, establish reproduction conditions and evidence before proposing a cause.
3. **Choose the smallest sound change.** Explain the cause or requirement, intended files/surfaces, verification, and meaningful regression risks. Prefer a simple local fix. Do not opportunistically refactor, reformat, upgrade dependencies, or fix unrelated issues.
4. **Respect the authorization boundary.** If the user asked only for analysis or a proposal, stop before implementation. If authorized, change only the approved scope. Pause the affected work if new evidence makes a broader change necessary; explain the new scope before proceeding.
5. **Implement in small, reviewable steps.** Each change should trace to the request or approved fix. Before touching shared behavior, find its callers and affected screens. Preserve stable defaults and outputs unless changing them is part of the request.
6. **Verify the actual outcome.** Choose checks proportional to risk and user impact. Re-run the original bug path; check adjacent states and stable behavior. Ensure the tested build/artifact contains the new code. Use real or user-approved representative data and materials. If evidence is unavailable, report the gap plainly.
7. **Review and report.** Inspect the final diff, including generated and documentation changes. Keep code, comments, and current authoritative docs aligned. Remove only temporary artifacts created for this task. Report what changed, exact paths, checks actually run and their results, uncovered areas, and any external actions not performed.

## Engineering constraints

- Do not guess through repeated parameter/layout/framework changes. Reproduce, isolate variables, form a falsifiable cause, then make one minimal correction and retest the original path. If no defect is demonstrated, a zero-change conclusion is valid.
- Use staged checkpoints for larger work. Verify the riskiest assumptions early; do not build further on a disproven direction.
- Keep one source of truth for values that vary by environment, product, design, platform, region, or test scenario. Use named constants, tokens, configuration, or injection as appropriate; do not turn every literal into a setting.
- Extract shared code when there are real repeated callers or independently evolving responsibilities. Keep one authoritative implementation and verify behavior after extraction. Avoid speculative abstraction.
- Temporary fallbacks need a purpose, trigger, and retirement condition. Remove them when their migration/compatibility purpose ends; retain long-term accessibility, recovery, or platform compatibility behavior only with explicit conditions and verification.
- Keep current documentation consistent with behavior. When a task changes documented behavior, update the relevant authoritative doc. Before removing a stale guide, inspect references and preserve still-valid decisions/evidence in the current source of truth.
- Inspect files before replacing or deleting them. Preserve original user materials, source assets, and useful historical QA by default; do not overwrite a deliverable without authorization.
- Match tests to risk. Core logic, persistence, purchases/entitlements, import/export, state machines, and shared modules need deep automated coverage where feasible, plus integration or real-world checks appropriate to the behavior. Do not claim a check passed if it was not run.

## Conditional workflows

- For new or substantially revised pages, follow the project's design workflow. If none exists, use an interactive HTML prototype for review before production UI implementation; prototype approval, plan approval, and implementation authorization are separate.
- For visual/media changes, inspect the actual rendered output and representative states, not only source code or a success message. Use the relevant guide: [references/media.md](references/media.md).
- For SwiftUI/iOS work, read [references/ios.md](references/ios.md) and applicable project rules.
- For secrets, privacy, live services, or store operations, read [references/security.md](references/security.md). Project-specific store experience is not universal guidance.
- Savario/Keepify experience is conditional and project-bound; consult [references/savario-keepify.md](references/savario-keepify.md) only in that project. Do not apply its IDs, workflows, or product decisions elsewhere.

## Delivery checklist

- Is each change traceable to the authorized request?
- Did I preserve the user's existing work and stable behavior?
- Did I inspect and verify the final diff and relevant docs?
- Does the report distinguish passed, failed, not-run, and uncovered checks?
- Are file paths complete and are external actions accurately reported?
