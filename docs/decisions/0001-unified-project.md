# Decision 0001 — One Nexus AI project

**Date:** 14 November 2026  
**Status:** Proposed consolidation, implemented as a documentation branch only.

## Context

Two public repositories exist under the same owner:

- christoy92/Nexus-Ai: one README describing an all-in-one intelligence engine; no application source files.
- christoy92/Nexus-Forge-Ai: README, MIT license and .gitignore; no application source files. Its README describes a creative platform for app, video and audio generation, and it has an open issue defining a Figma JSON import MVP.

Neither repository contains a runnable app scaffold at the time of review.

## Decision

Use **Nexus-Ai** as the proposed canonical repository and umbrella product. Position **Nexus Forge** as the creative-building workspace inside Nexus AI, not a separate product with its own account, memory, model routing or orchestration system.

The unified product should share identity and workspaces, conversations and linked threads, memory and project context, model/provider routing, tool permissions and approvals, usage controls and artifact storage.

## Why

Nexus-Ai describes the wider intelligence engine. Nexus Forge contributes a concrete creative workflow and a bounded first milestone. Treating Forge as a module preserves that work while avoiding two competing products.

## Repository handling

- This branch contains the proposed consolidation.
- The original Nexus-Forge-Ai repository is preserved as a reference.
- Do not delete, archive or rename either original repository as part of this change.
- Do not merge this branch into main until the consolidation is reviewed.
- The existing open Figma Import issue remains open in the source repository until a deliberate issue migration/closure decision is made.

## Important corrections

The Forge README's “Always Free” claim is not carried forward as a promise of unlimited inference. Hosted model, video, audio and compute usage has real costs. The product direction is free-first with transparent limits and cost controls.

The source README's proposed stack and provider names are candidates, not verified implementation choices. The unified architecture remains provider-agnostic.

## Open decisions

1. Confirm Nexus-Ai as the canonical repository and Nexus Forge as a module.
2. Confirm final brand naming and visual identity.
3. Choose the initial application stack and hosting after checking runtime compatibility and cost.
4. Choose the initial model provider and decide whether bring-your-own-key/local models are supported.
5. Confirm the unified repository license. Nexus-Forge-Ai has an MIT license; Nexus-Ai had no license file. No license is applied by this consolidation branch.
6. Define free-tier quotas and any paid usage model before enabling paid APIs.

## Consequences

The roadmap prioritizes a reliable app foundation and one end-to-end workflow over a broad but unimplemented feature list. The Figma JSON Import MVP is retained as the first bounded Forge feature. Agent automation and deployment remain later phases.
