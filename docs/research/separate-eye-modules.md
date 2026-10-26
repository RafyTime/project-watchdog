# Separate ready-made Eye Display modules

## Update on 2026-10-24: at least 35 mm of visible pattern height

Leo's 35 x 35 mm paper test establishes a new minimum visible Expression height of approximately 35 mm. **The earlier 25 mm Waveshare and horizontal 23 mm CharlieWing recommendations below are superseded for the primary build.** Their board sizes cannot produce a 35 mm tall luminous pattern. The revised EUR 100 combined hardware budget excludes the power bank and must leave room for the separate donor setup.

This focused follow-up did not establish a ready-made thin module with all three of the required facts: at least 35 mm visible pattern height, suitable board outline, and fast German stock. The closest lead is the KT-Elektronic 5 x 5 panel below. It remains conditional because its active LED span is unspecified. Do not silently substitute PCB height for Expression height.

### Closest lead: KT-Elektronic 39 x 39.5 mm 5 x 5 panel

LEDs-and-more lists this panel as article 7381055 at EUR 3.79 each, immediately available with **2-6 working days** for Germany. It is a complete rigid FR4 board, 39 x 39.5 x 3.2 mm, using 25 addressable 5050 RGB LEDs. The seller identifies KT-Elektronic as manufacturer. It needs an external controller, 4-5 V power and a data signal; the data starts top-right in a zigzag layout. The seller lists approximately 1.5 A at full white per panel and M2 mounting. [Product specification and stock lead](https://leds-and-more.de/RGB-SMD-Pixel-Matrix-LED-Panel-5x5-WS2812B-SK6812-39-x-395-mm)

Two boards cost EUR 7.58. The PCB footprint fits the desired size class far better than a conventional 65 mm square matrix. A five-row X uses nine pixels and is plausible for distinct light points. However, there is no dimensioned pitch or active-area drawing on the returned page. If pitch were 7.5 mm, outer LED centres would span only 30 mm; adding a nominal 5 mm LED package gives 35 mm of package envelope, but the actual emitting aperture is smaller than its package. That arithmetic is a conditional illustration, **not evidence that this board meets the 35 mm visual requirement**. Exact grid span needs a readable scaled drawing or a seller measurement. The page's claim that boards tile seamlessly is insufficient to prove pitch.

A simple controller arrangement is one 5 V Arduino-compatible Nano or similar board elsewhere in the mask, a shared regulated 5 V feed to both panels, common ground, one data line through a series resistor into the first panel, and the first panel's output into the second. Use a buffer/level shifter if choosing a 3.3 V controller instead. Keep LED power off GPIO pins and do not route full LED current through the controller regulator. The [Adafruit NeoPixel guide](https://learn.adafruit.com/adafruit-neopixel-uberguide/best-practices) documents the series resistor, power capacitor and 5 V logic-level practice. A controller, USB programming lead, power breakout, wire, capacitor/resistor and mounting need a further EUR 20-30 planning allowance, plus shipping. Thus the conditional standalone pair is roughly EUR 28-38 before shipping and bank, not a confirmed complete cart.

On Saturday 24 October, 2-6 working days can extend beyond the following weekend. The generic shipping statement is not a delivery commitment to 53604. Obtain a checkout estimate and active grid span before treating this as the selected first build.

### Leads rejected or left unresolved

- SparkFun LuMini 8 x 8 was investigated as a compact alternative, but the manufacturer marks it retired and unavailable. An EU distributor also marks it retired and out of stock. [Manufacturer](https://www.sparkfun.com/sparkfun-lumini-led-matrix-8x8-64-x-apa102-2020.html), [EU distributor](https://kamami.pl/en/retired-products/574454-lumini-led-matrix-8x8-rgb-led-matrix-com-15047-5906623420094.html)
- Rotating a 3138 CharlieWing gives a 51 mm tall board, but only a 23 mm wide board. Its actual active height still needs a pitch drawing, and its narrow seven-column X differs materially from the 35 x 35 mm mockup. It is a possible visual compromise requiring Leo's decision, not a proven substitute.
- Conventional WS2812 8 x 8 panels are commonly 65-66 mm square. LaskaKit documents a 66 x 66 x 3 mm stocked module. Such a board has ample light span but its opaque footprint can occupy most of the mask's maximum 75 mm eye aperture. It is not a verified viewing-gap layout and is not recommended merely because it is thin. [Own-brand module](https://www.laskakit.cz/en/8x8-inteligentni-rgb-led-neopixel-ctverec--ws2812--5050--5v/)
- Generic FC-16/MAX7219 tiles of approximately 32 mm cannot meet 35 mm visible height. Larger bare 37.9-48 mm matrix packages require separate drivers and often substantial depth. No assembled thin white module with a verified fast German supply was established in this pass.

The unresolved active span on the KT panel is the immediate decision blocker. Buying a small board because its outside dimensions are 39 mm would repeat the earlier mismatch between module size and visible Expression size.

## Earlier research, before the 35 mm minimum

Research date: 2026-10-23. Scope: two independent eye modules for the existing curved mask, approximately one week to a working result, no controller or LED stock on hand. Soldering tools are available. Leo subsequently confirmed that a power bank must be bought, with delivery to 53604 Bad Honnef. The parent research handles that purchase candidate separately. Leo accepts moving the Expressions above or below his pupils to preserve a viewing gap. These are component proposals, not purchases or validated assemblies.

## Finding

Two options justify further consideration. Two Waveshare ESP32-S3-Matrix boards require the least assembly and cost approximately EUR 22 before cables. Two Adafruit 3138 cool-white CharlieWings plus one QT Py RP2040 cost EUR 39.45 before wiring and provide a much better documented thin, wide eye module. The latter is the strongest new alternative to the earlier HT16K33 kits. The larger LED grid and 3 mm documented board thickness may justify a little soldering.

All these boards are opaque. They must leave an actual clear viewing gap, regardless of whether the LEDs themselves appear as distinct points. No candidate proves dim-light navigation or across-room recognition through this mask's insert. Physical width, illuminated width and shape recognition are separate questions.

## 1. Waveshare ESP32-S3-Matrix pair

The manufacturer documents an 8 x 8 RGB matrix, ESP32-S3, USB-C, GPIO breakout and reset/boot buttons. Its explicit warning says excessive brightness causes rapid temperature rise and can damage the board. [Manufacturer overview](https://docs.waveshare.com/ESP32-S3-Matrix) The official Arduino guide assigns the LED data to GPIO 14 and documents NeoPixel, NeoMatrix, GFX and FastLED examples. [Manufacturer Arduino guide](https://docs.waveshare.com/ESP32-S3-Matrix/Arduino)

Flash each board with its own static white X on startup. Eight rows support the core X and other simple shapes without a text renderer. Keep Wi-Fi and Bluetooth disabled for this minimum version. Configure brightness in firmware before the event; optional live adjustment and coordinated switching can follow. Two controllers are acceptable because static eyes do not need synchronized animation. This is a proposed implementation, not ready-to-flash project firmware.

BerryBase's direct German listing returned EUR 10.90 including VAT, 100+ units and 1-3 days. Its seller datasheet gives 25 x 25 mm. [German stock lead](https://www.berrybase.de/waveshare-esp32-s3-matrix-entwicklungsboard-wi-fi-bluetooth-5-le-8-8-matrix-512kb-sram-usb-c), [seller datasheet](https://www.berrybase.de/en/product-datasheet/019234a64c5c734d82d0c5015ec4f409/create)

The [manufacturer's outline image](https://docs.waveshare.com/assets/images/ESP32-S3-Matrix_entity_4-f2ff12438008f6d521261f087156d46a.webp) exists, but the available research tools did not expose readable dimensions. The [hardware resource page](https://docs.waveshare.com/ESP32-S3-Matrix/Resources-And-Documents) links a schematic and examples, with no mechanical model listed. **Assembled depth, actual LED pitch and USB plug projection remain unresolved.** Searches, the image viewer and a direct image retrieval did not resolve them. Do not advertise this as a verified 25 x 25 x N mm assembly or assume a generic USB plug fits. Its compact illuminated area may look small across a room.

Complete two-eye hardware needs two boards and two USB power leads compatible with the chosen bank. One lead must support data for sequential programming and may serve as a power lead afterward. No separate microcontroller, logic conversion or soldered display harness is needed when powering through USB. Use thin insulated mounts, rear insulation, and cable strain relief. Keep USB plugs pointed into an actual free cable route rather than toward the glasses.

There is no verified current at the intended X brightness. Set a low maximum brightness in the program, avoid an all-white startup test, then measure input current and temperature. Do not derive the LED power allowance from the onboard 800 mA regulator label. The schematic separates USB 5 V LED power from the processor regulator. [Manufacturer schematic](https://files.waveshare.com/wiki/ESP32-S3-Matrix/ESP32-S3-Matrix-Sch.pdf)

## 2. Adafruit 3138 CharlieWing pair and QT Py RP2040

The 3138 is a finished 15 x 7 grid of 105 cool-white LEDs with an IS31FL3731 driver. Adafruit specifies **51 x 23 x 3 mm**, 3.8 g, 256 brightness levels per LED and I2C addresses 0x74 or 0x77. The manufacturer no longer stocks it, but that does not rule out remaining German stock. [Manufacturer specifications](https://www.adafruit.com/product/3138) Unlike an HT16K33 matrix kit, the LEDs and driver are already mounted; only the harness needs soldering.

The pinout guide specifies 3.3 V for both power and logic, about 40 mA for most uses per board, and an address solder bridge to select 0x77. [Manufacturer pinout guide](https://learn.adafruit.com/adafruit-15x7-7x15-charlieplex-led-matrix-charliewing-featherwing/pinouts) These are typical figures, not worst-case guarantees. Two modules at roughly 80 mA typical plus the controller appear manageable for a small regulator, but measure the chosen pattern and brightness.

Use one QT Py RP2040 outside the eye/glasses clearance zone. Solder 3V, GND, SDA and SCL to both displays in parallel. Leave the first at 0x74 and bridge the second to 0x77. There is no need for Feather stacking headers, a controller behind each eye, 5 V logic conversion, or a separate LED supply in this proposed 3.3 V arrangement. Keep leads short within the mask and add strain relief. This remote mounting arrangement follows the documented four-wire interface; it is an engineering proposal.

Use the QT Py's labeled SDA/SCL pads and `busio.I2C(board.SCL, board.SDA)` in CircuitPython. The QT connector is a separate bus; if using that connector instead, select `board.STEMMA_I2C()` and a suitable breakout lead. Its regulator is specified as 600 mA peak, which is not a continuous-current thermal guarantee. [QT Py pinouts](https://learn.adafruit.com/adafruit-qt-py-2040/pinouts) The correct display class is `adafruit_is31fl3731.charlie_wing.CharlieWing`; the official guide provides the library and bitmap examples. [CharlieWing programming guide](https://learn.adafruit.com/adafruit-15x7-7x15-charlieplex-led-matrix-charliewing-featherwing/python-circuitpython)

BerryBase's direct 3138 page returned EUR 14.25, nine units and 1-3 days. Its direct QT Py page returned EUR 10.95, six units and 1-3 days. [Display stock lead](https://www.berrybase.de/adafruit-15x7-charlieplex-led-matrix-featherwing-kaltweiss), [controller stock lead](https://www.berrybase.de/adafruit-qt-py-rp2040) Counts varied between cached pages, so checkout remains the source for an actual order. Warm-white 3163 has the same 51 x 23 x 3 mm specification and EUR 14.25 listing, but only two units appeared in the newer search result. [Warm-white manufacturer](https://www.adafruit.com/product/3163), [warm-white seller](https://www.berrybase.de/adafruit-15x7-charlieplex-led-matrix-featherwing-warmweiss)

The wider 15-column grid offers more room for asymmetric shapes than the Waveshare's small square. Seven rows suffice to design X, chevron, exclamation and question-mark shapes, but this is a rendering assessment, not a readability test. Exact LED centre spacing was not established from a fabrication drawing. The LEDs occupy part of the board; 51 mm is the board width, not a verified luminous X width. The quoted 3 mm excludes any added headers, wiring loops, adhesive and insulation. Directly soldered wires can preserve a low profile.

## Other modules checked

| Candidate | Evidence and decision |
| --- | --- |
| Adafruit 3149 white HT16K33 16 x 8 | Board 51 x 23 x 5 mm and two separate 20 x 20 x 6 mm LED bodies. Complete installed depth is not stated. Each kit needs matrix soldering; manufacturer documents 3.3 V operation and roughly 120 mA typical. BerryBase lists EUR 17.90 with stock, but its direct page was an older crawl. Retain only if 3138 stock fails or square matrix pixels are preferred. [Specifications](https://www.adafruit.com/product/3149), [power guide](https://learn.adafruit.com/adafruit-8x16-led-matrix-featherwing/pinouts), [German lead](https://www.berrybase.de/adafruit-0.8-8x16-led-matrix-featherwing-display-kit-weiss) |
| M5Stack Atom Matrix | Official assembled case is 24 x 24 x 13.8 mm, with 5 x 5 RGB LEDs, USB-C and an M2 mounting hole. FastLED brightness 20 is recommended, with a heat/enclosure-damage warning. A five-row X is easy, detailed shapes are limited. Eckstein lists EUR 29.95 and approximately three weeks, so it misses the target. [Manufacturer](https://docs.m5stack.com/en/core/Atom-Matrix), [German seller](https://eckstein-shop.de/M5Stack-Marken__RGB) |
| M5Stack AtomS3-Lite | One programmable RGB LED, not a matrix. It would still need a separate display and adds no shortcut. [Manufacturer](https://docs.m5stack.com/en/core/AtomS3-Lite) |
| Grove RGB matrix with driver | Official 40 x 40 x 21 mm assembly, I2C at 0x65, 3.3/5 V. Still needs an external controller and addressing/wiring planning for two. The 21 mm depth is a poor starting point near the glasses; no fast German stock was established. [Manufacturer](https://wiki.seeedstudio.com/Grove-RGB_LED_Matrix_w-Driver/) |
| Adafruit 1080 / 1857 white 8 x 8 | Good simple interfaces, but a stocked pair in Germany was not established. The 1080's 4 mm is the backpack alone; the 1857's 7 mm is its matrix body. Neither proves complete assembly depth. DigiKey's 1857 listing returned zero stock and an 18-week lead. [1080](https://www.adafruit.com/product/1080), [1857](https://www.adafruit.com/product/1857), [German distributor](https://www.digikey.de/en/products/detail/adafruit-industries-llc/1857/7942431) |

## Complete setup budgets

These are per-setup allowances from the branch investigation. The [combined comparison](eye-display-candidates.md) counts shipping and the shared bank once and checks the EUR 100 ceiling for two alternatives together. It supersedes these preliminary bank allowances. Follow-up browser inspection confirmed the Waveshare manufacturer's 25 x 25 mm outline; depth and USB plug clearance remain unresolved.

Choose one setup. These are planning totals, not carts or guaranteed quotes. Shared cable and bank selection is being researched separately; the allowances below prevent those costs disappearing from the comparison. A bank with suitable simultaneous outputs is required for the solder-free Waveshare pair. Since Leo has no bank, use the totals including the EUR 20 bank allowance until the parent supplies a specific quote.

| Item | Waveshare pair | CharlieWing pair |
| --- | ---: | ---: |
| Two displays with integrated controllers | EUR 21.80 confirmed listing | EUR 28.50 confirmed listing |
| Separate QT Py RP2040 | Included | EUR 10.95 confirmed listing |
| USB lead or leads | EUR 6 allowance for two | EUR 3 allowance for one |
| Wire, insulation and small mounting materials | EUR 5 allowance | EUR 7 allowance |
| German shipping | EUR 4.95 parent-verified allowance | EUR 4.95 parent-verified allowance |
| Total with a suitable existing bank | **EUR 37.75** | **EUR 54.40** |
| If a bank must be bought, reserve EUR 20 | **EUR 57.75** | **EUR 74.40** |

Both proposals fit EUR 100 individually with these allowances. Faster shipping or unfamiliar bank requirements may change the total. A spare integrated Waveshare board adds EUR 10.90 and can still fit the budget. No spare is required to establish the comparison.

## Name-badge shortcut checked

A single programmable badge might show both eyes. The Sertronics datasheet documents a 93 x 30 x 6 mm badge, 85 x 23 mm active area, 44 x 11 LEDs at 1.93 mm pitch, static mode, eight memory banks and four brightness settings. It includes a 200 mAh battery, with claimed runtime of 12-24 hours. [Manufacturer-branded datasheet](https://cdn-reichelt.de/documents/datenblatt/A500/125904.pdf) The USB-C generation also has a [first-party programming manual](https://www.lednametags.de/wp-content/uploads/dlm_uploads/2025/08/Anleitung-LED-Name-Tag-Deutsch-1.3-1.pdf).

German white stock was inconclusive. Reichelt's direct white silver-frame result said in stock in one cache, while newer results said 1 December. Black-frame white results alternated between 3-5 working days and unavailable. [Silver-frame listing](https://www.reichelt.de/de/de/shop/produkt/led_name_tag_11x44_pixel_usb_rahmen_silber_led_weiss-249400), [black-frame listing](https://www.reichelt.de/de/de/shop/produkt/led_name_tag_11x44_pixel_usb_rahmen_schwarz_led_weiss-249404) BerryBase's smaller 70 x 22 x 7 mm white badge returned unavailable. [Mini badge](https://www.berrybase.de/mini-led-name-tag-11x44-pixel-usb-c-unifarben/farbe-weiss)

The internal battery creates another issue: interrupting pocket USB power does not establish a restart of the running display. Its own power button must remain accessible, or the pocket-restart requirement must change. Stored static-X startup, custom-image workflow and the flat 93 mm board's fit also need verification. This is a possible fallback if white stock and behavior are confirmed, not a better-supported replacement for the two shortlisted setups.

## Minimum evidence before final selection

Make one pair of module-shaped blocks at the actual mounting positions and thickness allowance, preserving space for plugs or wires. Wear glasses and the insert together, then check downward and forward navigation in dim lighting. The approximately 160 x 75 mm aperture and curved outline do not prove fit.

Then run the chosen low-brightness X behind the actual insert. Check recognition at intended room distance, distinct points, internal reflections, heat and fogging. Finally verify four hours with the selected bank and that accessible pocket power interruption returns both X eyes within ten seconds. Test automatic bank shutoff at the lowest selected brightness. These are targeted acceptance checks for the existing requirements; software library support does not establish any of them.

For speed choose the Waveshare pair if its small visual size and unresolved installed depth pass. Choose the CharlieWing pair when thin mounting and wider eye shapes matter more than avoiding a short soldering job. Avoid adding radios, a phone UI or live animation until the static result works.
