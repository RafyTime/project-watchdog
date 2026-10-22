# Define control and event operation

Type: grilling
Status: resolved
Blocked by: none

## Question

How should the wearer start, control, recover, and shut down the Mask System during an event, including the precise responsibilities of the Pocket Controller and Phone Controller, feedback to the wearer, connection-loss behavior, and operation with gloves or a locked phone?

## Answer

Agreed with Leo on 2026-10-23.

### Build priority

Get the Eye Display working as quickly as possible. On-demand Expression switching and all controller additions are welcome extras, not prerequisites for the minimum working Mask System. This supersedes the map's earlier requirement for a wireless Pocket Controller and qualifies the control-related requirements in [Define the Eye Display experience](02-define-eye-display-experience.md).

The minimum result can display the startup X eyes without on-demand switching. Preserve the agreed recognizable visual style. This priority does not waive power, reliability, or safety criteria, which remain a separate decision.

### Optional controls

- Choose whichever control is easiest and fastest to implement. A Pocket Controller or Phone Controller can provide on-demand selection; neither is mandatory.
- If control is included, prefer direct selection of several Expressions over cycling through the entire set. Choose the actual layout and available selections later.
- A Pocket Controller should allow Expression selection and manual brightness adjustment by feel, with gloves on and the phone locked. A Phone Controller alone naturally requires access to the phone.
- The Phone Controller may also provide configuration and later Custom Visuals. It must not be needed for normal operation or recovery of a Mask System that has a Pocket Controller.
- For a Pocket Controller, confirm that the mask received a command, preferably with a brief vibration if practical. Show connection status when the wearer inspects the controller. Keep status indications off the outward-facing Eye Display; no internal display is required.
- Controller features, including feedback and event-time brightness adjustment, must not delay the minimum working Eye Display. Their implementation belongs to the optional control decision.

### Event operation and recovery

- Start, shut down, or fully restart using an accessible switch or cable connection near the pocket-carried battery. The wearer must be able to reach it while wearing the mask, without opening the Mask System. Exact hardware and electrical suitability remain to be selected.
- Start the Eye Display with X eyes. After a mask restart, return to X eyes.
- When on-demand selection is available, switch immediately and hold the selected Expression until it is changed.
- On a controller disconnect, retain the selected Expression and reconnect automatically. Do not replay button presses missed while disconnected.
- Reconnect an included Pocket Controller after a mask restart without requiring the phone.

### Follow-up decisions

Choose optional control hardware and interaction details after the Eye Display architecture is known. The current map's 2026-10-17 target predates this agreement, so confirm the current deadline and minimum demonstration milestone separately. No replacement date was agreed in this session.
