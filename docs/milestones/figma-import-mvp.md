# Milestone: Figma JSON Import MVP

**Origin:** [Nexus-Forge-Ai issue #1](https://github.com/christoy92/Nexus-Forge-Ai/issues/1)  
**Status:** Planned; no implementation exists yet.  
**Priority:** First bounded Forge feature after the application foundation.

## Outcome

Import a supported Figma REST-style JSON document, convert one selected frame into a deterministic Next.js/Tailwind page, show a safe preview and let the user download the source.

This is a JSON-document import, not a live Figma integration and not a .fig binary parser.

## Why this comes before the Agent Loop

The original Forge issue chose Figma Import because it can produce a focused, inspectable result with a relatively small dependency surface. An Agent Loop would require reliable code generation, isolated execution, tests, deployment credentials, retries and rollback controls.

Keep the first milestone as a compiler-like pipeline:

**parse → validate → normalize → render preview → generate source → export**

## MVP scope

- One /forge/import page with a bundled, clearly labelled demo fixture and optional upload of matching Figma REST-style JSON.
- Accept a documented document root; list supported frames and let the user select one.
- Support a bounded subset: FRAME, TEXT and RECTANGLE nodes; horizontal and vertical auto-layout; spacing and padding; fixed/hug sizing; solid fills and corner radius; basic text size, weight and alignment.
- Normalize input into a small typed UI tree.
- Generate deterministic React TSX and Tailwind-compatible styles.
- Use escaped literal values or static styles for arbitrary values; do not rely on runtime class discovery.
- Preview only the normalized tree through an allowlisted renderer.
- Export a minimal runnable Next.js/Tailwind project ZIP and an import diagnostics file.
- Keep state session-only for the MVP.

## Explicit exclusions

No live Figma URL/API/OAuth import; arbitrary Figma fidelity; .fig binary parsing; images, fonts, components/instances, vectors, effects, interactions or absolute-positioned layouts; prompt generation or linked-thread infrastructure as a dependency; Supabase, video/audio generation or an AI provider as a dependency; Agent Loop or automatic Vercel deployment.

Unsupported nodes or properties must produce visible diagnostics. They must never silently imply a faithful import.

## User flow

1. Open Forge → Import.
2. Load the demo JSON or upload a supported JSON document.
3. Validate the input and choose one eligible frame.
4. Generate and inspect preview, source files and warnings.
5. Correct the input or choose another frame if needed.
6. Download the source ZIP and follow its README to install/build locally.

## Input limits

Carry forward the original issue's proposed guardrails, subject to implementation review: maximum input size 1 MiB; maximum node count 1,000; maximum tree depth 30. Reject malformed or over-limit input with actionable errors.

## Security requirements

Never execute uploaded or generated code in the trusted app server or preview. Treat uploaded text and node properties as untrusted data. Escape text and validate style values. Use fixed, allowlisted export paths; prevent path traversal. Do not allow uploaded content to initiate network requests. Preview from a trusted renderer over the normalized tree. No credentials or unrelated user data in exported files.

## Acceptance criteria

- A fresh checkout installs and opens the import page using documented commands without secrets.
- Demo loading and valid JSON upload work.
- Users can select one supported frame and inspect preview, source and diagnostics.
- A nested auto-layout fixture preserves supported hierarchy, text, direction, spacing, padding, solid colors, radius and basic typography.
- Malformed JSON, invalid schema, oversized/deep/node-heavy input and missing eligible frames fail safely.
- Unsupported layout semantics block that frame; unsupported decorative properties produce visible warnings.
- HTML/script-like text renders as text and cannot execute.
- Repeating the same import produces identical source files.
- Downloaded fixture projects install and pass a production build.
- Browser tests cover load/upload → select → generate → inspect → download.
- Parser, normalizer, code generation and escaping have automated tests.
- All CI checks pass.

## Completion rule

Do not mark this milestone complete until the acceptance criteria are demonstrated in a linked implementation pull request. The feature remains planned until then.
