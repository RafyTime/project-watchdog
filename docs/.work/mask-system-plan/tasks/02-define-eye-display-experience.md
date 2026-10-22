# Define the Eye Display experience

Type: grilling
Status: resolved
Blocked by: none

## Question

Which Expressions, animation behaviors, visual qualities, operating modes, transitions, and wearer-visible indications must the Eye Display support for the core Halloween result, and which belong only to later expansion?

## Answer

Agreed with Leo on 2026-10-23.

### Core behavior

- Present chunky, character-like Wrench-style Expressions recognizable across a room. The two eyes can show different shapes.
- Keep these as provisional options: `(0 0)`, `(^ ^)`, `(\ /)`, `(x x)`, `(> <)`, `(? ?)`, `(! !)`, and `(> o)`. The set and individual designs can be changed or tweaked; these examples are not a fixed required library.
- Start with X eyes, represented by `(x x)`.
- White is sufficient. Color is optional.
- Support static Expressions first. Keep the selected Expression until the wearer changes it, including if the controller disconnects.
- Switch immediately when a new Expression is selected. No transition effect is required.
- Provide manual brightness adjustment. Automatic brightness is deferred.
- Keep status symbols out of the outward-facing Eye Display. No internal display is required. Selection and connection feedback, if desired, belongs in the control and event operation decision.

### Optional additions

- Add subtle animation loops for personality, such as idle blinking or random glitches, while retaining the selected Expression's meaning.
- A quick glitch effect when switching Expressions is optional. It must not delay recognition of a new selection or prevent another selection from interrupting it immediately.
- Automatic Expression cycling is optional; holding one selected Expression is sufficient.
- Detailed images, text, and Custom Visual workflows are later expansion rather than core requirements.

### Implications for later decisions

The character-like examples simplify the visual requirements, but do not require a text renderer or settle the display technology. Choose hardware against recognizable shapes, asymmetric eye designs, manual brightness control, and static operation first. Animation and color must not become prerequisites for the core result.

The display architecture decision remains blocked by the power, reliability, and safety criteria. The final Expression library, animation representation, and authoring pipeline remain to be specified after the architecture is clearer.
