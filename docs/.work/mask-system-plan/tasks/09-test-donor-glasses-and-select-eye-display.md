# Test donor glasses and select the Eye Display

Type: task
Status: open
Blocked by: 06

## Question

Which of the KBIBCK and Lixada donor glasses can provide the minimum Eye Display inside the existing mask, and what measured facts must the mounting, optical and power decisions use?

## Context

- Parent plan: [Project Watchdog mask-system plan](../map.md).
- [Choose the Eye Display technology and architecture](06-choose-eye-display-architecture.md) selects the donor route and the two candidates.
- Leo intends to order both and reports estimated delivery Tuesday 27 October 2026. Receipt is a physical prerequisite; order completion is not yet confirmed.
- The Mask System must be usable and wearable by Friday 30 October. Prioritize a decisive fit and function check before modifying either donor.
- This is human-assisted physical testing that unblocks final donor selection and integration planning, not implementation of the completed Mask System.

## What it delivers

A comparison of both intact donors, a selected donor or a documented rejection of both, and measured evidence for the remaining integration decisions. Use the existing mask and Leo's normal glasses during the fit check. Preserve donor operation until initial checks pass.

## Acceptance criteria

- [ ] Record the received models and whether their phone software connects and uploads a static pair of X eyes. Confirm the display continues after disconnecting the phone.
- [ ] Switch each donor off and on. Record whether the X eyes persist and the startup time. Distinguish its original switch from the still-unverified pocket restart mechanism.
- [ ] Measure the illuminated X height and width, the usable panel outline and installed depth including required housings/connectors. Compare with the approximately 35 mm minimum desired Expression height per eye.
- [ ] Hold each working donor behind the mask insert without cutting or bending its PCB. Record outward recognition, inward sightlines in dim light, glare, glasses clearance, ventilation and pressure/contact points. Photograph the candidate placement where useful.
- [ ] Locate visible battery, controller, charging port, switches and wiring. Record what is known and what remains concealed. Inspect the housing further only after intact checks pass; do not assume arm removal is harmless.
- [ ] Record initial warmth at intended brightness and whether the layout is promising for wear. Record any runtime evidence without treating the advertised battery duration or a brief test as proof of four hours.
- [ ] Select the donor with the least remaining fit and integration work, or reject both and reopen the architecture decision. List outstanding mounting, optical shielding, power, accessible restart and assembled runtime checks. Do not mark the Mask System validated on the basis of these donor checks alone.

## Blockers and handoff

The architecture decision is resolved. Physical work waits for delivery and Leo's participation. Final mounting and electrical planning must use these findings. [Choose the optional control interface](08-choose-optional-control-interface.md) waits for the selected donor's capabilities.
