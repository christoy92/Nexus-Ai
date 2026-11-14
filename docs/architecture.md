# Nexus AI — Architecture

**Status:** Proposed architecture; not implemented  
**Last reviewed:** 14 November 2026

## Architectural goal

Build one application with modular capabilities and a shared orchestration core. Avoid separate apps, accounts, memories and provider integrations for Chat, Research and Forge.

Model providers must be replaceable without rewriting product workflows. Deterministic business logic, permissions and execution boundaries remain outside the language model.

## Proposed system layers

### Experience layer
- Next.js App Router web application (candidate based on the Forge proposal).
- Shared responsive design system.
- Workspace navigation and linked conversation threads.
- Chat, Research, Forge and Create surfaces.
- Accessible loading, error, approval and usage states.

### Product/domain layer
Typed concepts: User, Workspace, Membership, Conversation, Message, ThreadLink, ProjectFile, KnowledgeItem, MemoryItem, Task, TaskStep, ToolRun, Artifact, GeneratedProject, MediaAsset, Provider, ModelCapability, UsageRecord, ApprovalRequest and AuditEvent.

UI components call domain services, not provider APIs or database queries directly.

### Orchestration layer
A server-side orchestrator:
1. classifies the request and identifies workspace context;
2. decides whether deterministic code, a model or a tool is appropriate;
3. builds a minimal context package from authorized sources;
4. creates a bounded plan for multi-step work;
5. checks permissions, quota and cost limits;
6. requests approval when required;
7. executes allowed model/tool calls;
8. validates outputs and records provenance;
9. returns the result and updates task history.

The orchestrator must not invent capabilities, provider availability, prices or task completion.

### Model and tool adapters
Use stable internal interfaces for text/reasoning models, embeddings/retrieval, image generation/understanding, video generation/editing, audio transcription/generation, web/document retrieval, and code generation/validation.

Each adapter declares supported modalities, context limits, streaming support, regional availability, cost metadata and failure behavior. Provider selection uses a capability registry rather than hard-coded model names throughout the UI.

### Persistence layer
Supabase is a candidate because it appeared in the original Forge stack proposal. If selected, use it for authentication, relational project data and object storage. Add vector retrieval only when a concrete memory/research use case justifies it.

All database access passes through repository/service boundaries. Enforce tenant and workspace isolation with server-side authorization and database row-level security where applicable.

### Execution layer
Code execution, project builds, browser automation and agent tools run in isolated workers or sandboxes:
- no execution of uploaded code in the trusted web server;
- no production secrets in the sandbox by default;
- filesystem and network access allowlists;
- CPU, memory, time and output limits;
- disposable environments and auditable artifacts;
- explicit approval for deployment or external side effects.

The Figma Import MVP does not need arbitrary code execution: it previews a trusted normalized UI tree and exports source files.

### Observability and governance
Record task IDs and stage outcomes, provider/model and latency, usage and cost where available, tool permissions and approval decisions, validation failures and retries.

Do not log full private prompts, uploaded content or secrets by default. Define retention, access and deletion controls before production analytics.

## Core logical services

| Service | Responsibility |
| --- | --- |
| Request Router | Identify task type and candidate capability |
| Context Assembler | Retrieve only authorized workspace context |
| Model Router | Select provider/model by capability, quality, latency and budget |
| Tool Registry | Expose approved tools with schemas and permissions |
| Policy Engine | Enforce access, safety, quota and approval rules |
| Task Orchestrator | Coordinate bounded multi-step workflows |
| Memory Service | Manage user-controlled and workspace-scoped memory |
| Artifact Service | Store and version generated outputs |
| Usage Service | Track limits and cost |
| Evaluation Service | Check output quality and workflow acceptance criteria |

These are logical boundaries, not a requirement to create separate microservices. Start as a modular monolith.

## Model routing

Do not call a large model for every action:
- deterministic task → ordinary application code;
- simple text task → economical supported model;
- complex reasoning/research → stronger model when needed;
- media generation → relevant image/video/audio adapter;
- code task → code-capable model plus deterministic checks.

Routing may consider user preference, task capability, latency, privacy, region, availability and remaining quota. Never silently switch to a paid provider when a free/selected provider fails. Ask or follow a user-approved fallback policy.

## Memory and linked threads

Personal memory and workspace memory are separate scopes. A linked thread references shared context; it does not automatically grant access to every private conversation. Context assembly includes only material selected by the user or allowed by workspace permissions. Memory entries need provenance, timestamps and user controls. Define deletion and retention behavior before promising full erasure.

## Permissions and autonomy

| Level | Allowed behavior |
| --- | --- |
| 0 — Read | Read authorized context and produce analysis |
| 1 — Draft | Create drafts, plans, code or proposed changes |
| 2 — Isolated execution | Run tests or builds in a disposable sandbox |
| 3 — External/production action | Only after explicit, action-specific user approval |

Always require approval before spending money, sending external messages, publishing, purchasing, changing account permissions, accessing unrelated private data, deleting user data or deploying to production.

## Suggested initial stack (not locked)

The source repository proposed Next.js App Router and React, TypeScript, Tailwind CSS, Supabase, Vercel, and OpenAI/Replicate as initial AI/media examples.

The unified product should retain provider independence. Before implementation, verify current SDK support, runtime compatibility, free-tier limits, data regions and pricing. No provider, paid plan or deployment platform is approved by this document.

## Initial repository shape

    src/
      app/
        (workspace)/
          chat/
          research/
          forge/
          create/
          settings/
        api/
      components/
      features/
        chat/
        research/
        forge/
        create/
        memory/
        agents/
      domain/
        models/
        services/
        policies/
      server/
        orchestration/
        providers/
        tools/
        repositories/
        usage/
        security/
      shared/
        schemas/
        utils/
    docs/
      decisions/
      milestones/
      security/

Keep the first deployment as a modular monolith. Split services only when scale, security boundaries or independent release needs justify it.
