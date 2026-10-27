# Project Watchdog mask-system plan

## Destination

A build-ready specification for a serviceable wearable Mask System, prioritizing a working Eye Display as quickly as possible. On-demand Expression switching, the Pocket Controller, Phone Controller, Custom Visuals, and Voice System are optional additions that must not delay the minimum working result. Leo requires the Mask System to be usable and wearable by Friday 2026-10-30 at 18:00 Europe/Berlin, with extra tweaks allowed between 30 and 31 October. See [Confirm the build deadline and minimum milestone](tasks/07-confirm-build-deadline-and-minimum-milestone.md) for the agreed minimum and optional-feature cutoff.

## Notes

- This map plans the work; it does not implement the Mask System.
- The Halloween minimum is a milestone, not a permanent limit: after 31 October, Leo may revise it and continue building without deadlines or complexity limitations. See [Confirm the build deadline and minimum milestone](tasks/07-confirm-build-deadline-and-minimum-milestone.md).
- Use `wayfinder`, `grilling`, and `domain-modeling` while resolving design decisions. Use `research` for external technical facts and `prototype` when a rough artifact is needed to make a choice.
- Use the vocabulary in [`GLOSSARY.md`](../../../GLOSSARY.md).
- Preserve the existing mask exterior. Small concealed cuts, holes, or permanent mounts are acceptable.
- Choose optional control by ease and speed of implementation. Neither a Pocket Controller nor a Phone Controller is required for the minimum working result. See [Define control and event operation](tasks/03-define-control-and-event-operation.md).
- Plan for four hours of active use. Prefer a pocket-carried USB-C power bank, subject to electrical validation.
- Provide a concealed restart path that does not require opening the Mask System.
- Target a component budget below EUR 200, with a hard ceiling near EUR 350 when added cost clearly improves durability or serviceability. Reusable tools are excluded.
- Assume soldering and basic hand fabrication are available. Treat 3D printing as optional or outsourced.
- Favor recognizable Wrench-style Expressions and visibility at event distance over fine pixel detail.
- Favor repairable modules where failures or upgrades are plausible, but accept simpler permanent construction where modularity would threaten schedule, comfort, or budget.

## Decisions so far

- [Define the Eye Display experience](tasks/02-define-eye-display-experience.md): Agreed on tweakable character-like Expressions, X eyes at startup, static operation, instant switching, and manual brightness; white is sufficient, with blinking, glitches, and other animation optional.
- [Capture the existing mask constraints](tasks/01-capture-existing-mask-constraints.md): Recorded approximate geometry, construction, wear experience, replaceable insert, and candidate cable access, with component fit and mounting checks reserved for the chosen layout.
- **Voice System feasibility:** Treat live voice processing as an optional, removable embedded-audio module with wired microphone/speaker paths, independent mute and failure isolation, and reserved power/control interfaces; build it only after the Eye Display is stable and a bench prototype passes latency, feedback, intelligibility, power, and safety gates ([research note](../../research/voice-system-feasibility.md)).
- [Define control and event operation](tasks/03-define-control-and-event-operation.md): Prioritize a working Eye Display; controls are optional, with direct selection preferred, agreed disconnect/restart behavior, and accessible power operation near the battery.
- [Define power, reliability, and safety criteria](tasks/04-define-power-reliability-and-safety-criteria.md): Require four hours at intended brightness, X eyes within 10 seconds of a pocket restart, verified wearability, indoor use with sweat exposure, and preserved removal for repairs.
- [Choose the Eye Display technology and architecture](tasks/06-choose-eye-display-architecture.md): Adapt premade LED glasses for the MVP; compare KBIBCK and Lixada donors, with final donor selection and integration dependent on arrival tests.
- [Confirm the build deadline and minimum milestone](tasks/07-confirm-build-deadline-and-minimum-milestone.md): Verified wearable static X eyes by Friday 30 October at 18:00; optional feature work stops Thursday 29 October at noon, with unrestricted deadline-free development possible after 31 October.

## Not yet specified

- Physical placement, viewing arrangement, ventilation, cable routing, and mounting, pending the mask constraints and display architecture.
- Expression library, animation representation, and authoring pipeline beyond the visible behavior requirements.
- Custom Visual authoring and transfer workflow beyond the optional control interface.
- Power distribution, connectors, battery sizing, fault protection, and runtime validation.
- Voice System inclusion and integration, pending feasibility research and the core system architecture.
- Detailed integration, fallback, assembly, and verification sequence within the agreed milestone and optional-feature cutoff, pending donor-test findings.
- Portfolio documentation and repository structure for the eventual implementation.

## Out of scope

- The remainder of the Wrench costume outside modifications required to integrate the Mask System.
- Autonomous, AI-generated, camera-driven, or emotion-detection behavior.
- A polished general-purpose graphics or animation editor.
- Cloud services required for normal mask operation.
