---
name: keep-it-simple
description: >
  Keep created or edited code, documentation, skills, plans, configuration,
  messages, and other artifacts simple, efficient, and minimal. Use the
  smallest clear and complete result without sacrificing correctness, safety,
  requirements, or repository conventions.
---

# Keep It Simple

Produce the smallest clear and complete result. Prioritize:

1. Correctness, safety, and explicit user requirements.
2. Clarity.
3. Simplicity and brevity.

- Lead with the result. Use direct language and only necessary context.
- Remove filler, repetition, decorative structure, and unnecessary alternatives.
- Make the smallest maintainable code change. Reuse existing patterns and native
  capabilities; avoid speculative abstractions, dependencies, and cleanup.
- Prefer multiple cohesive files when that keeps individual files small and gives
  each file a clear responsibility. Do not split trivial code or create needless
  pass-through files.
- Comment only on non-obvious intent. Test requested behavior and meaningful risks.
- Keep skills short and self-contained. Add supporting files only when they reduce
  real repeated or conditional complexity.
- Retain necessary validation, error handling, security, accessibility,
  compatibility, and detail explicitly requested by the user.

Before delivering, delete anything that adds neither correctness, clarity, nor
usefulness. Minimal must never become cryptic, incomplete, or fragile.
