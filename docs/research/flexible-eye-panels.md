# Flexible Eye Display candidates

Researched on 2026-10-23 for [Choose the Eye Display technology and architecture](../.work/mask-system-plan/tasks/06-choose-eye-display-architecture.md). This is the flexible-panel branch of the comparison, not an agreed architecture or purchase list. Requirements come from that ticket's linked prerequisites, the plan map, and the glossary. The user now caps both alternative setups together at EUR 100 and prioritizes a working prototype in about one week, delivered to Germany. The [combined comparison](eye-display-candidates.md) supplies the shared bank price and paired-option budgets; it supersedes the preliminary bank allowance below.

## Finding

No compact, genuinely flexible matrix with verified German stock emerged as a purchase-ready recommendation. Small flexible wearable modules exist, but the narrow ones lacked credible short-delivery sourcing. Most ready-stock flexible hobby matrices are too large and opaque for this mask.

A prewired NeoPixel strand is a credible geometry fallback for fixed X eyes. It replaces the opaque matrix with individually positioned light points. It needs more mounting work and a few solder joints. It should compete against other candidates on assembly time, not automatically displace a complete donor or integrated module.

## Candidate comparison

| Candidate | Verified specification or listing | Fit and delivery judgment |
| --- | --- | --- |
| Adafruit flexible 8 x 8 NeoPixel, 2612 | Manufacturer specifies 80 x 80 x 2 mm, gentle forming only, no repeated flexing, no cutting into shapes. Manufacturer no longer stocks it. [Manufacturer](https://www.adafruit.com/product/2612) | Reject for this build. Each eye side has at most about 75 mm height, with a curved outline and nose cutout. Two opaque 80 mm squares consume almost the full window. |
| Generic WS2812 flexible 8 x 32 | German seller lists 320 x 80 x 3 mm, EUR 22.90, few available, 1-2 business days. [Seller](https://www.led-shop.com/8x32-Pixel-Panel-WS2812-LED-Matrix?btgsterne=5) | Reject. Rotating does not solve either dimension. No manufacturer-approved cutting evidence was found for this panel. |
| DFRobot flexible 8 x 8 | OpenELAB lists EUR 31.45 and zero stock. [German listing](https://openelab.de/products/dfrobot-gravity-flexible-8x8-rgb) | Reject as a deadline fallback. Its ordinary 80 mm class does not solve the geometry problem, and this source has no stock. |
| BTF-Lighting complete flexible 16 x 32 display | Manufacturer lists a 170 x 70 mm option, USB power, Bluetooth control, and USD 27.99. It advertises 93 available, but customer customs handling applies. [Manufacturer](https://www.btf-lighting.com/de/products/led-matrix-pixel-panel-bluetooth-app-usb-5v-flexible-addressable-rgb-pattern-graffiti-scrolling-text-animation-display) | Reject as an internal Eye Display. Curvature might reduce the straight width, but its opaque 70 mm height occupies almost the full exposed opening. No usable viewing gap or nose clearance is established. No German arrival promise. |
| WAS LMD17 complete flexible display | German shop lists 173 x 70 mm, EUR 13.77, USB, Phone Controller and handheld control. The page does not establish available quantity or dispatch time. [Seller](https://car-bulbs.de/8861-led-matrix-display-16x3270x173mm.html) | Same obstruction problem as BTF. Low product price does not make it a usable wearable fallback. Do not cut it. |
| Narrow BL1248 / 1248BL wearable flex panel | Search found nominal 153 x 32 mm, 12 x 48 pixel products, but only overseas marketplace evidence for this particular size. No primary specification plus credible German delivery source was verified. | Worth revisiting only if a donor cap or mask with the exact narrow panel is available locally. It could occupy an upper band, but remains unqualified. Do not order on an unverified generic product photo. |
| Adafruit 4560 soft-wire NeoPixel strand | German product page opened successfully and lists EUR 19.50, two available, 1-3 days. One strand can supply both eyes. [German seller](https://www.berrybase.de/adafruit-neopixel-faden-mit-biegsamen-draht-50-neopixel) | Keep as a secondary fixed-X fallback. It has no large opaque backing and can follow the insert curve. Individual mounting, wire slack, glare, and sweat isolation remain work. |

The mask's 160 x 75 mm exposed maximum is not a rectangle available for mounting. Full-height panels remain poor candidates even when they bend. No documented minimum bend radius was found for these selected products; a claim of flexibility is insufficient to guarantee the existing 40-45 mm estimated bow.

## Sparse prewired strand fallback

Adafruit 4560 is a string of addressable LEDs joined by flexible coated wire. The German seller specifies roughly 100 mm spacing and allows clipping the wire. The manufacturer specifies 5 V operation and warns against higher than 6 V. The current manufacturer revision, introduced in June 2024, has silicon-covered pixels and encased wires. A reseller's older description still says the strand has no weatherproof coating, so confirm the delivered revision and insulate it for sweat rather than assuming protection. [Manufacturer](https://www.adafruit.com/product/4560), [seller](https://www.berrybase.de/adafruit-neopixel-faden-mit-biegsamen-draht-50-neopixel).

An example fixed layout uses nine points per X: five points on each diagonal sharing one centre. Eighteen LEDs form both eyes. Position them on a thin removable carrier around the actual sightlines, with light shields behind the pixels. This is a proposed physical arrangement, not a manufacturer accessory or a measured fit.

The 100 mm electrical spacing is much wider than the desired visible spacing. Secure the excess wire in broad loops outside the viewing gap. Do not shorten and resolder all gaps; that would remove this approach's assembly advantage. Cut only the unwanted output tail after identifying the actual data direction. Bare cut ends need insulation. No large opaque backing is necessary, but the LEDs themselves still obstruct small areas and can reflect off the insert.

This layout provides startup X eyes and brightness adjustment in firmware. It cannot produce arbitrary grid Expressions without remounting pixels. Turning subsets off permits only shapes supported by their fixed locations. That is a real scope tradeoff, acceptable only if Leo chooses fixed X eyes as this fallback's minimum result.

### Complete estimate for both eyes

| Item | Quantity | Cost | Evidence or remaining check |
| --- | --- | --- | --- |
| Adafruit 4560 strand | 1 | EUR 19.50 | Opened German page lists two in stock and 1-3 days. See link above. |
| Nano-compatible ATmega328P / CH340G, CH-ANANO | 1 | EUR 6.90 | Opened seller page lists 100+ in stock, 1-3 days, 5 V operation and Mini USB. [Seller](https://www.berrybase.de/kompatibler-arduino-nano-mit-atmel-mega-328p-prozessor-ch340g-usb-chipsatz) |
| Mini USB data/power cable | 1 | EUR 2-4 allowance | Required for programming and pocket power. Exact stocked cable still needs selection. |
| 330-470 ohm data resistor, 500-1000 microfarad supply capacitor, insulated wire, connector/pigtail | 1 set | EUR 2-4 allowance | Exact parts still need selection. |
| Carrier, opaque backing behind individual pixels, insulation and strain relief | 1 set | EUR 3-5 allowance | Estimate, not a checkout quote. |
| German shipping | 1 order | EUR 4.95 allowance | Parent comparison verifies BerryBase shipping and exact basket grouping. |
| **Total before power bank** | | **EUR 38.35-44.35** | Both eyes and controller. Reusable soldering tools excluded. |
| Pocket 5 V USB power bank | 1 | **Add the shared verified bank price** | Parent comparison owns the bank choice. A EUR 10-15 planning allowance gives roughly EUR 48-59, not a firm complete checkout price. |

This is an indicative complete architecture with a few unselected accessories. It is not a verified purchase-ready basket. A shared power bank and combined shipping must be counted only once across two alternatives. The pair must stay under the user's EUR 100 total ceiling after the exact remaining items and shipping are selected.

Use a 5 V ATmega328P Nano for this estimate, not a Nano ESP32 or Nano 33. Arduino confirms that those radio-equipped variants use 3.3 V logic. The 5 V Nano avoids a separate data level shifter when both data and pixels use the matching 5 V supply. [Arduino voltage table](https://support.arduino.cc/hc/en-us/articles/11264980365468-Nano-family-overview).

Provide pixels with a suitable 5 V power path and common ground. Do not power them from a GPIO pin. Do not assume the clone's USB/5 V board trace or diode can supply unrestricted pixel current. Keep a small fixed pixel count and low brightness, and either verify that path's rated current or split regulated 5 V to board and strand with an insulated connection. Adafruit recommends the series resistor and input capacitor above. Measure actual current, warmth and four-hour runtime. [Adafruit connection guidance](https://learn.adafruit.com/adafruit-neopixel-uberguide/best-practices).

The firmware can use the existing Adafruit NeoPixel Arduino library. A short startup program can set all physically placed X pixels to dim white. This is simpler than building matrix rendering or wireless control. The CH340G USB interface may need its Windows driver, so include one successful upload in initial assembly work. This research has not verified that particular clone's bootloader or upload behaviour.

## Why ordinary flex strips are not the leading fallback

Four narrow LED-strip diagonals can form X eyes while leaving most of the insert clear. Cuttable WS2812 strips exist, but crossing two wide flexible circuits and wiring their data direction requires more joints and insulation than a prewired string. A ready-stock 50 cm, 30-pixel BerryBase strip is listed at EUR 5.50 on the strand product page, but its density is only 60 LEDs/m. That is about 16.7 mm between points. A 40 mm diagonal would contain only about three points. Denser strips improve that but raise cost and require small-pad soldering.

Do not substitute nOOds, EL wire, COB strip, or diffused neon. Those produce the continuous strokes that Leo explicitly does not want.

## Stock and delivery limits

The German strand and Nano pages were opened, rather than trusting search snippets alone. They list stock and 1-3 days. That is a seller estimate, not a date promised to the user's address. Friday 2026-10-23 ordering, cutoff times, weekend handling, payment and actual destination still matter.

This matters because the NeoPixel Driver BFF search snippet showed available stock at EUR 4.30, while opening its actual product page showed unavailable. Its QT Py alternative therefore cannot be treated as a stocked fallback without rechecking. [BFF product page](https://www.berrybase.de/en/adafruit-neopixel-driver-bff-for-qt-py-and-xiao-neopixel-jst-ph-3-pin-5v-level-converter).

No candidate here has proven fit, acceptable inward glare, glasses clearance, dim-light navigation, moisture isolation, restart within 10 seconds or four-hour runtime. A short assembled check remains necessary even when two candidates are purchased.
