# Savario / Keepify project notes

**Read only when working in Savario/Keepify. These rules and historical lessons must not be generalized to other projects.** First confirm current project documentation; these notes reflect decisions and experience recorded through 2026-11-15 and may have changed.

## Engineering conventions

- Localization uses the project-approved `L10n.s(...)` path for composed strings and direct `Text("...")` for view literals. The project source forbids `String(localized:)` due to observed in-app language switching behavior. Confirm current implementation before changing this convention.
- Design tokens have a single source of truth shared between `design/00_DESIGN_TOKENS.md` and `DesignSystem/DS.*`; synchronize both when tokens change. UI copy is English-first by product decision; HTML design drafts remain Chinese.
- Platform source icons use `SourceIcon`/`SourceChipIcon`; haptics use `Haptics.swift`. Avoid direct substitutes in views.
- Deployment target is iOS 17.0; guard iOS 26-only APIs and provide graceful degradation.
- Do not recreate the Xcode project; incrementally modify the user-created project.
- Project history says commit messages are Chinese with date and milestone number, and milestones are committed and pushed. Current global authorization still applies: no commit or push without explicit user authorization.
- Completion requires a successful build and relevant simulator or device verification with inspectable evidence; do not infer success.

## Rendering bug investigation

1. Reproduce, isolate variables, state a falsifiable root-cause hypothesis, make a minimal change, retest the original path, and record the evidence chain.
2. Narrow animation/rendering issues by checking whether position changes, whether it occurs without scrolling, what content triggers it, and which OS version is affected.
3. Confirm the affected OS/device early. Failure to reproduce on a newer simulator does not disprove an older-device report.
4. A discovered defect is not necessarily the reported defect. Verify each fix against the user's original symptom.
5. A one-line change may be the right fix; do not accumulate speculative mitigations.

## Debug hooks and documentation

- For hard-to-reproduce states, project history uses launch-argument hooks protected by `#if DEBUG`. Verify the hook itself and ensure it is unreachable in Release.
- Keep product numbers in a single source of truth and synchronize store copy, review notes, and screenshots when those numbers change.
- Keep a single current workbench document for cross-session operational work; explicitly record unresolved decisions rather than silently deciding them.
- Record bug evidence as symptom, diagnostic path, root cause, diff, and regression result.

## Historical App Store Connect checklist

Treat these as prompts to verify against current Apple tooling and current project state, not timeless platform facts:

- Verify targeted device families against required screenshots.
- Check free-app pricing schedules, version metadata, copyright, review contact details, content rights, age-rating overrides, and in-app purchase localization/pricing/review assets and submission state.
- Validate screenshot dimensions, encoding, and upload type against current requirements.
- Add the app version and related products to the same review submission batch as required by the current workflow.
- For a first submission rejected for missing information, project experience suggests a real-device walkthrough recording and a structured review note can address information gaps without code changes. Confirm the actual rejection reason first.
- Verify China storefront availability and filing requirements using current official guidance before changing territory settings or making compliance claims.
- After API changes, read back state and counts. Some review relationships, contact fields, and questionnaires have historically required the web UI.

## Historical paywall decision

Project experience records a Founder product as the only purchasable item and a Regular product as a non-sale strikethrough anchor. Ending the founder period involved repricing Founder and removing Regular from sale. This is a project product decision, not general advice: verify current product IDs, code, and store state before acting. Any live change requires explicit authorization.
