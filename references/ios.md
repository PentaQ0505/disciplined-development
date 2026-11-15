# SwiftUI and iOS

Use these checks only for Swift/iOS work, alongside the active project's `AGENTS.md`, deployment target, and established architecture.

- Confirm the deployment target before choosing APIs. Gate newer APIs with availability checks and provide an appropriate fallback when the project supports older systems.
- Prefer the project's existing SwiftUI, persistence, and system capabilities. Do not add a third-party dependency or rewrite stable implementation without authorization.
- When adding source files, follow the project's Xcode project-generation method; filesystem presence alone may not include a file in the target.
- For shared layout, typography, color, navigation, or animation changes, inspect every consumer.
- Verify relevant Dynamic Type, VoiceOver, Reduce Motion, and safe-area behavior. Simulator checks do not establish real-device performance, permission, cache, or interaction behavior; use a device when the requirement depends on it.
- Do not simulate a real purchase by changing local state. Test purchase and entitlement flows with the project's authorized sandbox procedures.

Savario/Keepify has additional project-specific practices in [savario-keepify.md](savario-keepify.md); do not apply them to other projects.
