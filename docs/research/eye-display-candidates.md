# Eye Display alternatives and procurement comparison

## Current recommendation, 2026-10-24

Leo's paper-template check sets a minimum Expression height of approximately 35 mm, ideally 35 x 35 mm per eye. This supersedes the 23 mm CharlieWing and 25 mm Waveshare recommendations below. The wired NeoPixel strand is rejected for assembly effort. The EUR 100 budget covers both alternative display setups; the general-use power bank is explicitly separate.

For the one-week MVP, investigate two different donor designs: [KBIBCK B0FFSQH8G2](https://www.amazon.de/dp/B0FFSQH8G2), EUR 22.89, and [Lixada B09L85YL7B](https://www.amazon.de/dp/B09L85YL7B), EUR 41.99. Together they cost EUR 64.88 before shipping and mounting/wiring supplies. Reserving EUR 15-25 for those supplies gives EUR 79.88-89.88 before shipping. These are planning allowances, not two validated complete builds. Both live Amazon pages for 53604 Bad Honnef showed stock, standard delivery Wednesday 28 October and a faster Tuesday 27 October option. Prices, arrival estimates and delivery charges must be checked at checkout.

Lixada explicitly supports RGB custom drawings through Shining Glasses. KBIBCK advertises custom drawing through Funky Glasses, but white/RGB capability and exact Android application compatibility remain unverified. Different mechanics and named apps provide some diversity, but both routes still share donor-fit and firmware uncertainty. Neither listing establishes a 35 mm illuminated X, the bare-board dimensions, saved-X startup, four-hour runtime or accessible pocket restart. No exact-model teardown was found. Preserve the original electronics for an intact custom-X, reboot and mask sightline check before disassembly; required arm electronics may need relocation rather than removal.

The standalone lead is a [KT-Elektronic 5 x 5 RGB panel](https://leds-and-more.de/RGB-SMD-Pixel-Matrix-LED-Panel-5x5-WS2812B-SK6812-39-x-395-mm), EUR 3.79 each, with a 39 x 39.5 x 3.2 mm board. Board height does not establish 35 mm illuminated height. It also needs a controller, power wiring and soldering; advertised German delivery is 2-6 working days. It remains a conditional alternative, not a qualified backup. Buying one of each architecture is useful only if the standalone option passes size and arrival constraints.

See the [live donor findings](led-glasses-donors.md) and [larger standalone investigation](separate-eye-modules.md). No hardware has been selected or purchased; the architecture ticket remains unresolved.

## Historical comparison, 2026-10-23 — superseded where noted above

Researched 2026-10-23 for [Choose the Eye Display technology and architecture](../.work/mask-system-plan/tasks/06-choose-eye-display-architecture.md). This comparison supersedes the earlier shortlist in this file. No hardware has been selected or purchased.

## Recommendation

The best documented pair to compare is two Adafruit 3138 CharlieWings with one QT Py controller, alongside two integrated Waveshare ESP32-S3-Matrix modules. The first offers thin, independently positioned white eyes; the second minimizes assembly. They share USB power and have firmware we can control, including startup X eyes. The pair is approximately EUR 79 before a power bank, or EUR 106 with the Amazon bank below, including the stated accessory allowances and standard shipping.

If EUR 100 must include the new power bank, the more affordable and mechanically different pair is the Waveshare setup plus white DIGI donor glasses, approximately EUR 95 including the bank and standard shipping. The donor is an experiment with unresolved teardown, application, fit and restart behavior. It must not be described as meeting every requirement on published evidence. Buying it protects against some visual-size risks, but does not guarantee a second passing assembly.

Leo's EUR 100 ceiling applies to both alternative setups together. Because he separately said he needs an Amazon power bank for general use, the totals below show it both separately and included. Do not assume permission to exceed EUR 100 or to exclude the bank from the cap. Exact checkout totals and the final pair remain a human decision.

## Requirements used

- Delivery to Germany, 53604 Bad Honnef, within roughly one week. An exact event date has not been agreed. Aim for arrival early in that window to leave assembly time.
- Distinct visible light points, white sufficient, recognizable Wrench-style Expressions. Startup X eyes are the minimum; live selection and animation are optional.
- Independent mounting is preferred; Expressions may sit above or below the physical eyes to preserve a clear viewing gap.
- Existing exposed insert area is at most approximately 160 x 75 mm with a nose cutout and substantial curvature. Those are not rectangular mounting dimensions. Preserve glasses clearance and ventilation.
- Four-hour runtime, usable vision in dim lighting, and X eyes within ten seconds after an accessible pocket restart remain acceptance criteria.
- Soldering tools are available; no microcontroller, LED modules or power bank are on hand. Prioritize finished modules and available software over custom fabrication.

See the [map](../.work/mask-system-plan/map.md) and the resolved requirements linked from the architecture ticket.

## Practical shortlist

Electronics prices below exclude the shared power bank, shipping and minor accessories. Seller pages showed stock during research; this is not a reservation or guaranteed delivery date.

| Route | Electronics for both eyes | Assembly and fit | Main unresolved issue | Assessment |
| --- | ---: | --- | --- | --- |
| Two [Adafruit 3138 cool-white CharlieWings](https://www.berrybase.de/adafruit-15x7-charlieplex-led-matrix-featherwing-kaltweiss) plus [QT Py RP2040](https://www.berrybase.de/adafruit-qt-py-rp2040) | EUR 28.50 + 10.95 = **39.45** | Finished 15 x 7 LED boards, each 51 x 23 x 3 mm. Solder four connections per display and an address bridge. Controller mounts elsewhere. | Actual illuminated size, mounting clearance, viewing gap and recognition through tint. | Best documented thin, independent eye layout; some soldering. |
| Two [Waveshare ESP32-S3-Matrix boards](https://www.berrybase.de/waveshare-esp32-s3-matrix-entwicklungsboard-wi-fi-bluetooth-5-le-8-8-matrix-512kb-sram-usb-c) | 2 x EUR 10.90 = **21.80** | Each integrates an 8 x 8 RGB matrix, controller and USB-C. Independent static X firmware; no display soldering. | Small symbols, complete installed depth and plug space. Manufacturer warns about heat at high brightness. | Fastest assembly and cheapest documented backup. |
| White [DIGI Bluetooth donor glasses](https://www.leds-blink.de/de/Bluetooth-LED-Brille-DIGI-Leuchtbrille-19-Programme-AKKU-USB-Handy-APP-Steuerung.html), article 2019010901 | **EUR 24.99**, included USB cable and internal battery | Existing drawing software and static mode. Inspect intact before removing mechanical parts. | Bare-board size, disassembly, phone compatibility, brightness, saved-X startup and pocket restart are unverified. | Cheapest donor experiment; higher integration uncertainty than modules. |
| [Adafruit 4560 flexible NeoPixel strand](https://www.berrybase.de/adafruit-neopixel-faden-mit-biegsamen-draht-50-neopixel) plus [5 V Nano clone](https://www.berrybase.de/kompatibler-arduino-nano-mit-atmel-mega-328p-prozessor-ch340g-usb-chipsatz) | EUR 19.50 + 6.90 = **26.40** | Position eighteen wired pixels as two nine-point X eyes on a removable carrier. Requires soldering, light shields and securing considerable wire slack. | More hand assembly; fixed pixel positions cannot reproduce arbitrary matrix Expressions. | Genuinely shapeable fallback, slower to mount. |
| [Adafruit EyeLights 5210 panel](https://www.berrybase.de/adafruit-led-brille-frontplatte-116-rgb-leds-mit-i2c-treiber) and [5217 controller](https://www.berrybase.de/adafruit-led-brillen-treiber-nrf52840-sensorplatine) | EUR 22.90 + 27.45 = **50.35** | Sparse 147 x 63 x 4.5 mm full-width rigid panel, documented libraries and cable interface. | Full-width flat board inside the bowed insert; sparse pixel map must support acceptable X eyes. | Better documented than a party-glasses teardown, but less attractive for fit and budget. |

The [3138 manufacturer specifications](https://www.adafruit.com/product/3138) establish its assembled module dimensions. The [pinout guide](https://learn.adafruit.com/adafruit-15x7-7x15-charlieplex-led-matrix-charliewing-featherwing/pinouts) specifies 3.3 V power and logic, addresses 0x74 and 0x77 and roughly 40 mA typical per board. Do not power this proposed arrangement from 5 V. That typical current is not a worst-case rating.

The [Waveshare manufacturer documentation](https://docs.waveshare.com/ESP32-S3-Matrix) establishes the integrated matrix and controller and warns about rapid temperature rise at excessive brightness. The [manufacturer outline](https://docs.waveshare.com/assets/images/ESP32-S3-Matrix_entity_4-f2ff12438008f6d521261f087156d46a.webp), inspected visually during research, confirms a 25 x 25 mm footprint. The 2.54 mm annotation marks GPIO pad spacing, not verified LED pitch. The drawing does not establish complete depth or USB plug projection.

## Donor glasses versus DIY

Donor glasses save firmware and pixel-wiring work only if we can preserve their working electronics. Removing arms might also disconnect a battery, button or controller. No exact donor teardown was found that proves removal is simple, and a foldable frame is not evidence of a flexible circuit board.

The white DIGI variant was selected in the retailer's browser interface during research. The price remained EUR 24.99 and Add to basket was enabled, with a displayed 1-2-day lead. This establishes a selectable order lead, not a counted white stock quantity, successful order or verified dimensions. The page links an Android APK, so exact current phone/application compatibility must be checked before counting its drawing software as usable. No software was downloaded or installed.

Retain the original electronics and battery for the initial check. Draw X eyes, close the phone interface, switch off/on and verify retention and brightness before dismantling anything. If that fails, use the documented module option rather than spending the remaining time reverse-engineering the donor. Keeping its original internal battery does not prove an accessible pocket restart.

The other RGB DIGI donor is EUR 29.99 but has an advertised 175 mm overall width. CHEMION has better official documentation and saved patterns, but approximately EUR 59 before unresolved delivery costs leaves less room for a second setup. Neither has proven bare-board fit or pocket restart. See [donor research](led-glasses-donors.md).

## Delivery evidence

Browser checks of BerryBase showed nine cool-white 3138 boards at EUR 14.25 each, six QT Py controllers at EUR 10.95, and over 100 Waveshare modules at EUR 10.90. All three product pages advertised 1-3 days. Counts and prices can change before checkout.

[BerryBase shipping terms](https://www.berrybase.de/versand-und-zahlungsbedingungen) list EUR 4.95 DHL shipping within Germany under EUR 200, or EUR 9.90 UPS Saver Express. Express is advertised as next business day, Monday to Friday, when ordered and paid by 15:00 using supported immediate-payment methods. The site banner separately mentions a 14:00 dispatch cutoff. Use checkout's actual estimate and order early rather than relying on either cutoff at its limit.

[leds-blink shipping terms](https://www.leds-blink.de/de/popup/Versand----Zahlungsbedingungen.html) list EUR 5 within Germany, generally 1-2 working days dispatch readiness and about two working days in transit. Its product's shorter 1-2-day headline must not be treated as guaranteed arrival. This makes it a plausible following-week lead, with weaker date certainty than the Amazon bank.

Amazon was checked with the visible delivery location Bad Honnef 53604. The new black [Anker Zolo A1688, 10,000 mAh, ASIN B0CZ9M6X8Q](https://www.amazon.de/dp/B0CZ9M6X8Q) showed EUR 26.99, in stock, standard delivery Tuesday 27 October and a fastest option Saturday 24 October. Free delivery was conditional on an eligible first order; account/Prime status and any expedited delivery fee remain checkout questions. A used offer had a later date and was not used in the budget.

## Power bank and shared accessories

The Anker A1688 is a reasonable general-use Amazon candidate, not yet a validated Mask System supply. Its [manufacturer guide](https://support.anker.com/s/article/Anker-Zolo-Power-Bank-10K-30W-Built-In-USB-C-Cable-User-Guide-A1688) specifies USB-A, USB-C and a short integrated USB-C cable, with 5 V / 3 A combined output when multiple outputs operate. Its 13.7 cm built-in cable cannot reach from a pocket to the mask.

Use one USB-A-to-C and one USB-C-to-C cable for the two USB-powered Waveshare boards. One must carry data for programming. Do not use a passive USB-C splitter or join two power-bank outputs. The CharlieWing controller can reuse the USB-A-to-C cable when comparing setups.

BerryBase lists a [1 m USB-A-to-C data cable](https://www.berrybase.de/blackcotton-usb-a-usb-c-kabel-usb-2.0-schwarz-1-0m) at EUR 1.60. Reserve EUR 6 total for suitable pocket-length power/programming cables; the exact second cable and its plug envelope remain to be selected. The budget is an allowance, not a finished basket.

Sparse dim patterns can be low-current loads. The A1688 guide documents a USB-A trickle mode, but does not prove four-hour uninterrupted output for this assembly. [Anker's general explanation](https://service.anker.com/fr/article-description/What-is-Trickle-Charging-Mode) describes automatic shutoff behavior and a two-hour low-current mode limit. Verify actual operation; do not substitute a trickle-mode feature claim for the four-hour test. The pocket restart can use unplugging the appropriate power cable or cables; the bank button is not established as a hard off switch.

## Combined budgets for two complete alternatives

These totals use observed electronics prices plus stated allowances. They are not guaranteed checkout quotes. Reuse one bank and the USB programming cable across alternatives. Both alternatives do not need to run simultaneously.

| Cost | Thin white modules plus Waveshare backup | White donor plus Waveshare backup |
| --- | ---: | ---: |
| Two Waveshare boards | EUR 21.80 | EUR 21.80 |
| Other complete display electronics | EUR 39.45, two 3138 plus QT Py | EUR 24.99, donor with battery/controller |
| USB cables allowance | EUR 6.00 | EUR 6.00 |
| Wire, insulation and mounting allowance | EUR 7.00 | EUR 5.00 |
| BerryBase DHL shipping | EUR 4.95 | EUR 4.95 |
| Donor seller shipping | Not needed | EUR 5.00 |
| **Both alternatives before bank** | **EUR 79.20** | **EUR 67.74** |
| Shared Amazon Anker bank | EUR 26.99 | EUR 26.99 |
| **Including bank** | **EUR 106.19** | **EUR 94.73** |

BerryBase Express adds EUR 4.95 to either column. Amazon delivery fees, higher accessory prices or additional materials would add to these totals. The donor pair has only EUR 5.27 buffer including the bank and standard shipping. Do not call either a worst-case guaranteed total or proceed with an order above the agreed cap.

The flexible strand plus Waveshare would be approximately EUR 98-104 including the same bank, standard combined shipping and the two notes' accessory allowances. Its individual pixel mounting is slower than either module route. It does not offer as strong a speed advantage as its low electronics price suggests.

## Rejected and conditional routes

No compact flexible matrix with dependable German stock qualified. Common 80 x 80 mm flexible matrices and 320 x 80 mm panels are too large and opaque; the selected manufacturers do not support cutting them to shape. Narrow 153 x 32 mm flexible wearable panels exist but lacked a sufficiently documented local delivery source. See [flexible-panel research](flexible-eye-panels.md).

LED name badges can provide stored static drawings in a thin assembly, but current white stock was uncertain and their internal batteries complicate pocket restart. M5Stack Atom Matrix is compact but the checked German source had a multi-week lead. Grove's matrix assembly is deep and still requires a controller. Older white matrix kits add depth and soldering without a clear advantage over the CharlieWing. See [separate-module research](separate-eye-modules.md).

## Decision still needed

Choose the two candidates and clarify whether the separately useful power bank belongs inside the EUR 100 ceiling. Buying two candidates is a valid way to reduce procurement risk, but neither can be called a validated assembly before arrival. Keep the physical checks short: fit and viewing gap, X recognition/glare through the insert, bench warmth at working brightness, then runtime and pocket restart. These checks preserve the agreed requirements without starting a long prototype program.
