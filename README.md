# Disciplined Development

A reusable Codex skill for scoped software changes, explicit authorization, minimal diffs, and evidence-based verification.

## Install

Copy this directory into your Codex skills directory:

```sh
mkdir -p ~/.codex/skills
cp -R disciplined-development ~/.codex/skills/
```

Then start a new Codex conversation and invoke `$disciplined-development`, or let Codex select it automatically for a relevant development task.

To update an existing install after pulling changes:

```sh
cp -R disciplined-development ~/.codex/skills/
```

Restart the conversation after installing or updating so the skill is rediscovered.

## Contents

- `SKILL.md`: core authorization, implementation, and verification workflow.
- `references/ios.md`: conditional SwiftUI/iOS guidance.
- `references/media.md`: visual and media QA guidance.
- `references/security.md`: secrets, privacy, and external operations.
- `references/savario-keepify.md`: historical, project-specific notes; use only in that project.

Project instructions and the user's latest request take precedence over this skill. The skill itself does not grant authorization for code changes or external actions.
