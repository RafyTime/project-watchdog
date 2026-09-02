# Project Watchdog mask-system plan

## Destination

A build-ready specification for a serviceable wearable Mask System that can reliably present preset Expressions on its Eye Display through a wireless Pocket Controller, with a target of reaching verified operation no later than 2026-10-17. The specification must also preserve practical expansion paths for the Phone Controller, Custom Visuals, and the Voice System without making those features prerequisites for the Halloween build.

## Notes

- This map plans the work; it does not implement the Mask System.
- Use `wayfinder`, `grilling`, and `domain-modeling` while resolving design decisions. Use `research` for external technical facts and `prototype` when a rough artifact is needed to make a choice.
- Use the vocabulary in [`CONTEXT.md`](../../../CONTEXT.md).
- Preserve the existing mask exterior. Small concealed cuts, holes, or permanent mounts are acceptable.
- The Pocket Controller is the dependable primary control. The Phone Controller adds configuration and optional features.
- Plan for four hours of active use. Prefer a pocket-carried USB-C power bank, subject to electrical validation.
- Provide a concealed restart path that does not require opening the Mask System.
- Target a component budget below EUR 200, with a hard ceiling near EUR 350 when added cost clearly improves durability or serviceability. Reusable tools are excluded.
- Assume soldering and basic hand fabrication are available. Treat 3D printing as optional or outsourced.
- Favor recognizable Wrench-style Expressions and visibility at event distance over fine pixel detail.
- Favor repairable modules where failures or upgrades are plausible, but accept simpler permanent construction where modularity would threaten schedule, comfort, or budget.

## Decisions so far

- **Voice System feasibility:** Treat live voice processing as an optional, removable embedded-audio module with wired microphone/speaker paths, independent mute and failure isolation, and reserved power/control interfaces; build it only after the Eye Display is stable and a bench prototype passes latency, feedback, intelligibility, power, and safety gates ([research note](../../research/voice-system-feasibility.md)).

## Not yet specified

- Eye Display technology and electrical architecture, pending the mask constraints and visual requirements.
- Physical placement, viewing arrangement, ventilation, cable routing, and mounting, pending the mask constraints and display architecture.
- Expression library, animation representation, and authoring pipeline beyond the visible behavior requirements.
- Pocket Controller hardware and interaction layout beyond its role as the primary control.
- Phone Controller transport, platform shape, and Custom Visual workflow.
- Power distribution, connectors, battery sizing, fault protection, and runtime validation.
- Voice System inclusion and integration, pending feasibility research and the core system architecture.
- Procurement, prototype, fallback, assembly, and verification milestones needed to reach the target date.
- Portfolio documentation and repository structure for the eventual implementation.

## Out of scope

- The remainder of the Wrench costume outside modifications required to integrate the Mask System.
- Autonomous, AI-generated, camera-driven, or emotion-detection behavior.
- A polished general-purpose graphics or animation editor.
- Cloud services required for normal mask operation.
