# Evaluate Voice System feasibility

Type: research
Status: resolved
Blocked by: none

## Question

Which portable real-time Voice System architectures are technically realistic for a wearable mask, considering intelligibility, processing latency, acoustic feedback, microphone and speaker placement, power, size, customization, safety, cost, and the October schedule? What minimum interfaces should the core Mask System reserve if voice processing remains an optional later module?

## Answer

A customizable embedded Voice System is feasible within budget, but it should remain an independently removable stretch module with a wired live-audio path, close microphone, outward-facing body-worn speaker, hardware mute, and measured latency/feedback/safety gates. The core Mask System should reserve a protected 5 V / 1 A branch, 3.3 V UART control, an independent mute line, serviceable microphone and speaker harnesses, and a Pocket Controller mute action without depending on the Voice System for normal operation. Platform options, evidence, integration constraints, and acceptance tests are documented in [the Voice System feasibility research note](../../../research/voice-system-feasibility.md).
