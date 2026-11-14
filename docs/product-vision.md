# Nexus AI — Product Vision

**Status:** Draft product direction  
**Last reviewed:** 14 November 2026

## What Nexus is

Nexus is a personal AI workspace connecting conversation, reasoning, research, creation and task execution. A user should be able to start with an idea, research it, create assets, build a product and refine it in the same project. Relevant context travels with the project, with clear controls over what is remembered and which tools may act.

Nexus is an application and orchestration system built around existing models. It is not a plan to train a foundation model from scratch.

## Product promise

**One place to move from thought to finished work.**

Nexus understands the request and project context, selects an appropriate model or deterministic tool, coordinates specialist capabilities, creates useful outputs, preserves relevant context across linked threads, and makes sources, progress, usage and approval requests visible.

## Product modules

### Nexus Chat
The main conversational interface for multi-turn work, file context, multimodal inputs when available, and handoff to specialist capabilities.

### Nexus Research
A research workspace for web and document research, source comparison, evidence extraction, summaries and research artifacts. Important claims should be traceable to sources.

### Nexus Forge
The creative and software-building workspace inherited from Nexus-Forge-Ai:
- turn a brief into a structured app or website plan;
- import supported Figma JSON and generate a bounded Next.js/Tailwind page;
- inspect generated source and diagnostics;
- preview safely and export source;
- later connect code generation, testing and deployment through isolated, permissioned workflows.

### Nexus Create
A shared creative surface for image, video, audio and other media tasks. Provider adapters make capabilities, latency, quality and cost comparable without rewriting the product.

### Nexus Memory
User-controlled personal and project context. Personal memory and workspace knowledge remain separate. Users can view, edit, export and delete memory. Not every conversation or file becomes permanent memory by default.

### Nexus Agents
Specialist task workflows coordinated by an orchestrator. A specialist is a bounded capability, not an unrestricted autonomous employee.

### Nexus Connect
Connectors to external services, tools and model providers. Each connector declares its permissions and supported actions.

## Connected workspace

A workspace is the organizing unit. It can contain conversations and linked threads, goals and decisions, reference files, research notes and citations, generated code/design/media, tasks, approvals and activity history.

Users can move from Chat to Research to Forge without manually reconstructing project context. They still choose which project materials are available to a task.

## Differentiation

Do not compete by claiming every model or feature on day one. The credible product hypothesis is:
1. one project context across chat, research and creation;
2. model/tool routing based on task fit rather than vendor lock-in;
3. specialist workflows with transparent permissions and approval gates;
4. durable, user-controlled memory and project history;
5. exportable outputs and a path from idea to usable artifact.

This is a hypothesis to validate, not a proven competitive advantage.

## Cost and access model

The original Forge README used the phrase “Always Free.” That promise is not supportable for unlimited hosted model inference, video/audio generation, storage and compute.

Recommended direction:
- keep the application free to access where feasible;
- use deterministic code instead of model calls for predictable operations;
- route simple tasks to lower-cost models and reserve stronger models for tasks that need them;
- cache reusable results and batch background work;
- set hard usage limits and alerts;
- consider local-model or bring-your-own-key options only where experience and security are sound;
- show users when a task may consume a quota or incur a charge;
- never add a paid provider, subscription or billing commitment without explicit approval.

Pricing and the free-tier policy are not decided.

## Trust, privacy and safety

Keep provider API keys on the server. Use least-privilege tools and scoped credentials. Ask before publishing, sending, purchasing, deploying or deleting. Run generated code in an isolated environment with resource limits and no default access to production secrets. Validate uploads, generated paths and tool arguments. Make memory and retention understandable and controllable. Avoid collecting sensitive information not required for the task.

## Non-goals for the first release

- Training a foundation model from scratch.
- Claiming access to every AI model or platform.
- Unrestricted autonomous agents.
- Automatically deploying or publishing generated work.
- Unlimited free media generation.
- Arbitrary Figma fidelity or unsupported binary-file import.
- Collecting all user activity to train or profile users by default.

## Success measures

Focus on successful task completion, time to usable output, correction/regeneration rate, research source quality, generated-project build success, cost per completed task, tool failure rate, user understanding of memory/permissions/costs and privacy/security incidents.
