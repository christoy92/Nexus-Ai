# Nexus AI — Roadmap

**Status:** Proposed; do not describe a feature as shipped unless separately verified.  
**Last reviewed:** 14 November 2026

## Phase 0 — Consolidate and define

- [x] Inspect both source repositories and their current contents.
- [x] Select Nexus-Ai as the proposed canonical repository.
- [x] Reframe Nexus Forge as the creative-building workspace inside Nexus.
- [x] Carry forward the Figma Import MVP scope and safety requirements.
- [x] Document product vision, architecture and roadmap.
- [ ] Confirm product name/branding and repository destination.
- [ ] Resolve the unified repository license.
- [ ] Confirm initial hosting, database and model-provider choices.

**Exit gate:** one agreed product direction, documented architecture and reviewed first implementation milestone.

## Phase 1 — Application foundation

Create a fresh Next.js App Router + TypeScript application scaffold, subject to stack confirmation. Establish shared layout, navigation, responsive design system and workspace shell. Add linting, type-checking, tests and CI. Define typed domain models and repository/service boundaries. Establish secure environment-variable handling and secret scanning.

**Exit gate:** clean checkout installs, tests and builds; no AI provider is required just to run the application.

## Phase 2 — Nexus Chat and first model adapter

Implement conversation UI and streaming response states. Add one server-side model-provider adapter. Keep provider keys server-side. Add request validation, quotas, timeout handling and usage tracking. Show the selected model/provider and meaningful fallback behavior. Do not silently move a user onto a paid provider.

**Exit gate:** one end-to-end text conversation works reliably with server-side secrets and a hard usage cap.

## Phase 3 — Workspaces, linked threads and memory

Create user workspaces and project context. Link related threads without exposing unrelated private conversations. Add user-controlled memory with view/edit/delete controls. Add project files and context selection. Define retention and export behavior.

**Exit gate:** users can continue a project across threads and understand what context is being reused.

## Phase 4 — Nexus Forge: Figma JSON Import MVP

Carry forward the open milestone from [Nexus-Forge-Ai issue #1](https://github.com/christoy92/Nexus-Forge-Ai/issues/1).

Upload supported Figma REST-style JSON or load a bundled demo; validate input and list eligible frames; select one frame; normalize supported nodes into a typed UI tree; render a safe preview from trusted components; generate deterministic React/Next.js and Tailwind-compatible source; show diagnostics; download a minimal project ZIP and diagnostics.

No live Figma API/OAuth, no .fig binary parsing, no uploaded-code execution, no AI provider and no automatic deployment in this milestone.

**Exit gate:** supported fixture passes parser, normalization, deterministic code generation, safe preview, export build and end-to-end browser tests.

## Phase 5 — Nexus Research and file intelligence

Add source-backed web/document research. Show citations and distinguish evidence from inference. Allow users to attach selected research to a workspace. Add document extraction and structured summaries. Add retrieval only after access controls and source provenance are in place.

## Phase 6 — Nexus Create: multimodal generation

Add image generation/understanding through a provider adapter, audio transcription/generation, and video generation/editing only after cost, latency and safety are evaluated. Provide provider capability comparison and transparent usage limits. Store generated artifacts in user-controlled workspaces.

## Phase 7 — Nexus Agents and safe build loop

Introduce bounded specialist workflows. Run tests/builds in isolated disposable environments. Show plans, tool calls, logs and artifacts. Add checkpoints, retries and resumability. Require approval for external actions, publishing and deployment. No unrestricted self-modification or autonomous production changes.

## Phase 8 — Model routing and integrations

Add multiple model providers and a capability registry. Route by task fit, latency, region, quality and budget. Add approved external integrations and user-configurable fallback policies. Evaluate local-model options where practical.

## Release gates

Before public release: authentication and workspace isolation reviewed; privacy notice, terms, retention and deletion behavior defined; security review and dependency audit completed; quotas and cost ceilings tested; generated-code isolation tested; accessibility and mobile UX reviewed; error handling and backup/recovery tested; all advertised capabilities verified in the deployed build.

## Explicitly deferred

Training a foundation model from scratch; “every model” or “every platform” claims; unlimited hosted AI/video/audio generation; autonomous production deployment; unrestricted agent access to user accounts or secrets; complex multi-agent orchestration before one reliable end-to-end workflow exists.
