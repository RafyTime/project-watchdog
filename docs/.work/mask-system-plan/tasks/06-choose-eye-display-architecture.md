# Choose the Eye Display technology and architecture

Type: grilling
Status: claimed
Blocked by: 02, 04

## Question

Which Eye Display technology, panel arrangement, optical layers, and electrical architecture can produce the required Expressions within the captured mask geometry, budget, and power criteria while preserving wearer sightlines and glasses clearance? What candidate components and physical fit, visibility, reflection, and heat checks must pass before that choice is final?

## Context

- [Capture the existing mask constraints](01-capture-existing-mask-constraints.md)
- [Define the Eye Display experience](02-define-eye-display-experience.md)
- [Define power, reliability, and safety criteria](04-define-power-reliability-and-safety-criteria.md)

## Comments

### Design discussion, 2026-10-23

- Leo wants distinct points of light rather than continuous glowing strokes.
- Prefer ready-made display modules where available. The fastest workable approach takes priority.
- Leo reports about one week remaining. This is a planning constraint, not an agreed replacement event date; confirm the exact deadline in [Confirm the build deadline and minimum milestone](07-confirm-build-deadline-and-minimum-milestone.md).
- Source components for delivery to Germany. Leo has no microcontroller or LED modules available, so the parts selection must include both.
- Leo accepts placing Expressions slightly above or below his actual eyes to preserve a viewing gap.
- Leo accepts investigating the glasses panel but prefers a suitable flexible panel or separate modules for each eye. Prioritize a first working prototype within the roughly one-week window and minimize validation time. Physical fit and operating criteria remain unverified.
- Candidate comparison is in progress. Display technology, layout, and electrical architecture remain undecided.
- [Eye Display module candidates](../../../research/eye-display-candidates.md) records the manufacturer specifications, German sourcing leads, alternatives, and required fit and operating checks.
- The Adafruit LED Glasses Front Panel with its matching controller is a candidate for a quick first build, pending a rigid-panel fit check, usable sightlines, Expression shape checks, and power validation. Its documented 147 x 63 x 4.5 mm dimensions do not establish fit inside the curved insert. Manufacturer documentation: [panel](https://www.adafruit.com/product/5210). German sourcing leads: [panel](https://www.berrybase.de/adafruit-led-brille-frontplatte-116-rgb-leds-mit-i2c-treiber), [controller](https://www.berrybase.de/adafruit-led-brillen-treiber-nrf52840-sensorplatine). Seller listings advertise availability and 1-3 days; delivery and stock must be confirmed before ordering.
- The updated research recommends two separate Waveshare ESP32-S3-Matrix boards as the next MVP candidate. Each integrates an 8 x 8 RGB matrix and microcontroller with USB-C, reducing assembly. The German seller lists a 25 x 25 mm board footprint, EUR 10.90 each and 1-3 days; thickness, connector clearance, symbol size suitability, heat, runtime and actual delivery remain to be checked. This supersedes the full-width glasses panel as the leading candidate, but is not an agreed architecture. [Manufacturer documentation](https://docs.waveshare.com/ESP32-S3-Matrix), [German listing](https://www.berrybase.de/waveshare-esp32-s3-matrix-entwicklungsboard-wi-fi-bluetooth-5-le-8-8-matrix-512kb-sram-usb-c).

### Broader candidate comparison, 2026-10-23

- Leo agrees that buying two complete alternatives for a short comparison is reasonable. Cap the two alternative setups together at EUR 100, preferably less, and prioritize the easiest, fastest assembly. No purchase is authorized by this research request.
- Leo explicitly requested parallel research of alternatives, including adapting ready-made LED glasses. The separate research notes cover [donor glasses](../../../research/led-glasses-donors.md), [independent eye modules](../../../research/separate-eye-modules.md), and [flexible panels](../../../research/flexible-eye-panels.md).
- Delivery is to 53604 Bad Honnef. Leo has no power bank and wants to buy one through Amazon for general use as well. The comparison shows totals with and without the shared bank; whether it belongs inside the EUR 100 cap remains to be confirmed.
- The [combined comparison](../../../research/eye-display-candidates.md) now includes thin Adafruit 3138 white modules, integrated Waveshare modules, inexpensive donor glasses, and a flexible wired-pixel fallback. It distinguishes documented specifications, observed seller availability, cost allowances and unresolved fit or operating behavior.
- No compact flexible matrix with documented suitable geometry and dependable German stock qualified. Donor glasses remain experimental because teardown, bare-board fit and pocket restart are not verified. Independent module options provide controllable startup firmware but still need physical fit, vision, warmth and runtime checks.
- The leading documented pair is the thin white module setup plus the integrated Waveshare setup, approximately EUR 79 before the shared bank or EUR 106 including it. A donor-plus-Waveshare pair is approximately EUR 95 including the bank, with more unknowns. These are planning estimates with allowances, not final worst-case quotes. Candidate selection and architecture resolution remain pending Leo's comparison.

### Size and donor follow-up, 2026-10-24

- Leo's paper-template test establishes approximately 35 mm as the minimum desired Expression height, ideally 35 x 35 mm per eye. The earlier small-module recommendations are superseded; the photo does not establish usable inward sightlines.
- Leo excludes the general-use power bank from the EUR 100 cap for two display alternatives and rejects the wired NeoPixel strand for assembly effort.
- Leo requested research of Amazon alternatives to CHEMION rather than supplying favorite listings. Live checks for 53604 Bad Honnef found KBIBCK B0FFSQH8G2 at EUR 22.89 and Lixada B09L85YL7B at EUR 41.99, both showing 28 October delivery with a faster 27 October option. Their EUR 64.88 combined price excludes shipping and mounting/wiring. These are estimates, not purchases or guarantees.
- The current research preference is two different donor designs, conditional on active size, mask fit, inward vision, custom-X startup and control relocation. No exact-model teardown or 35 mm active-height specification was established. A 39 mm standalone board remains conditional because illuminated span and timely arrival are unverified. See the updated [comparison](../../../research/eye-display-candidates.md) and [donor evidence](../../../research/led-glasses-donors.md).
- No architecture selection has been agreed and this ticket remains unresolved.
