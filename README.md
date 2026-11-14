# Nexus AI

**One personal AI workspace for thinking, researching, creating and building.**

Nexus AI brings conversations, model access, memory, research and creative tools into one coherent product. Its creative workspace is **Nexus Forge**: the place where users turn ideas into apps, designs, video and audio.

Nexus is an application and orchestration layer around existing AI models and tools. The goal is not to train a new foundation model. Users should be able to move between capabilities without losing the context of their project.

> **Product status:** consolidation and planning baseline. Neither source repository currently contains a runnable application. Features below are product direction or planned work unless explicitly marked implemented.

## One product, connected capabilities

- **Nexus Chat** — conversations, reasoning, planning and everyday tasks.
- **Nexus Research** — structured research, source-backed answers and project knowledge.
- **Nexus Forge** — creative studio for building apps and websites, importing supported designs, and creating video and audio.
- **Nexus Create** — image, video, audio and other creative generation.
- **Nexus Memory** — user-controlled context and memory, scoped to the user and their projects.
- **Nexus Agents** — specialist workflows using approved tools to complete bounded tasks.
- **Nexus Connect** — integrations with external apps, services and model providers.

These are modules in one product, not separate apps with separate accounts, memories or orchestration systems.

## Product principles

1. **One context, many capabilities.** A project can connect conversations, research, files, generated assets and build tasks.
2. **Provider-independent.** Keep model and media providers behind adapters.
3. **Honest capability labels.** Never advertise a feature or integration as available until implemented and tested.
4. **User-controlled memory.** Make memory visible, scoped, editable and deletable.
5. **Human control.** Publishing, spending, sending messages, deleting data, deploying code and changing external systems require explicit authorization.
6. **Safe execution.** Generated code and uploaded content must not execute inside the trusted application server.
7. **Free-first, not fake-free.** Keep the core product accessible, use quotas and efficient routing, and explain limits. Unlimited hosted AI, video and audio generation cannot honestly be promised as free.

## Consolidation

This repository is the proposed canonical home:

- [Nexus-Ai](https://github.com/christoy92/Nexus-Ai) — umbrella product and primary repository.
- [Nexus-Forge-Ai](https://github.com/christoy92/Nexus-Forge-Ai) — source of the Forge creative-studio concept and its Figma-import milestone.

Nexus Forge becomes a workspace/module inside Nexus AI. The original repository is being preserved as a reference; it is not being deleted or archived as part of this preparation.

## Proposed technical direction

The Forge repository proposed Next.js App Router, React, Tailwind CSS, Supabase and Vercel. Its Figma-import milestone specifies a deterministic TypeScript pipeline. These are candidate foundations, not an implemented stack.

The unified architecture will use a web application, a server-side orchestration layer, provider adapters for language and media models, a permissioned tool registry, persistent project data and isolated execution for code-generation workflows.

See [Product Vision](docs/product-vision.md), [Architecture](docs/architecture.md) and [Roadmap](docs/roadmap.md).

## Current status

| Area | Status |
| --- | --- |
| Two-repository review | Complete |
| Unified product direction | Drafted on this branch |
| Nexus Forge module definition | Drafted |
| Figma JSON import MVP specification | Carried forward from the open Forge issue |
| Runnable app scaffold | Not started |
| Authentication and persistence | Not implemented |
| Model/API integration | Not implemented |
| Image, video or audio generation | Not implemented |
| Agent execution | Not implemented |
| Deployment | Not configured |

## Source repositories

- [Nexus-Ai](https://github.com/christoy92/Nexus-Ai)
- [Nexus-Forge-Ai](https://github.com/christoy92/Nexus-Forge-Ai)
- [Original Figma Import MVP issue](https://github.com/christoy92/Nexus-Forge-Ai/issues/1)

## License

Nexus-Forge-Ai contains an MIT license. Nexus-Ai did not contain a license file when reviewed. The unified repository's license is intentionally undecided until confirmed; this branch does not apply the MIT license to the whole project.
