# Voice System feasibility

Research date: 2026-09-03

## Conclusion

A portable, customizable, real-time Voice System is technically realistic within the Project Watchdog budget, but it should remain an optional module rather than part of the Halloween-critical Eye Display path.

The most credible first architecture is a dedicated embedded-audio processor with a wired microphone and wired speaker. The microphone belongs close to the wearer's mouth, while the speaker should face away from the microphone and sit below the chin or on the upper chest/shoulder rather than beside the wearer's ear. The processor and amplifier can live in a small body-worn enclosure. Only power, low-rate control messages, and a hardware mute signal need to connect this module to the core Mask System.

This separation matters more than the processor brand. It keeps audio timing deterministic, prevents speaker-amplifier noise or a Voice System crash from disturbing the Eye Display, and lets the entire Voice System be removed if feedback, comfort, or schedule tests fail.

For a first build, use modest, speech-preserving effects rather than making dramatic pitch shifting mandatory. A close microphone, noise gate, filtering, compression/limiting, and a blend of clean voice with ring modulation, bit reduction, overdrive, or a short modulation effect can sound clearly synthetic without sacrificing every consonant. Pitch shift can be added, but its buffering must be measured because it can dominate end-to-end latency.

## Recommended architecture

```text
close microphone
    -> microphone bias / preamplifier
    -> embedded audio codec + real-time DSP
    -> high-pass / gate / compression
    -> selectable character effect + dry blend
    -> EQ + hard output limiter
    -> small class-D amplifier
    -> outward-facing body-worn speaker

Mask System controller
    -> preset / parameter / volume commands over a wired control link
    -> independent hardware mute
```

The audio path should be wired end to end. Wireless control of presets is fine; wireless transport of live audio is not recommended for this version.

### Why this is feasible

- Purpose-built microcontroller audio platforms already process input and output concurrently in small blocks. Daisy's official example uses a 48-sample block at 48 kHz, giving the processing callback 1 ms before an underrun; the block size is configurable down to small values ([Daisy audio guide](https://docs.daisy.audio/tutorials/_a3_Getting-Started-Audio/)). Teensy's audio engine uses 128-sample blocks representing about 2.9 ms at 44.1 kHz ([PJRC audio memory documentation](https://www.pjrc.com/teensy/td_libs_AudioConnection.html)). These figures are buffer intervals, not complete microphone-to-speaker latency, but they demonstrate that the core compute path can operate well below the project's proposed 20 ms acceptance ceiling.
- The required effects are already represented in maintained first-party libraries. DaisySP includes limiters, filters, phasers, wave folding, decimation, overdrive, and a time-domain pitch shifter ([Electrosmith DaisySP repository](https://github.com/electro-smith/DaisySP), [DaisySP pitch-shifter source](https://electro-smith.github.io/DaisySP/pitchshifter_8h_source.html)). PJRC's library provides streaming filters, mixing, and effects, and its granular effect explicitly supports real-time pitch shifting over a configurable grain buffer ([PJRC Audio Library](https://www.pjrc.com/teensy/td_libs_Audio.html), [PJRC granular effect](https://www.pjrc.com/teensy/gui/?info=AudioEffectGranular)).
- The power and cost are modest compared with the full Mask System budget. A Teensy 4.0 draws approximately 100 mA at 600 MHz and measures 35.6 x 17.8 mm; its current US retail listing is USD 23.80 ([PJRC Teensy 4.0 specifications](https://www.pjrc.com/store/teensy40.html), [SparkFun Teensy 4.0 listing](https://www.sparkfun.com/teensy-4-0.html)). The original Daisy Seed is listed at USD 21 and integrates 24-bit stereo audio hardware, a 480 MHz Cortex-M7, and 64 MB SDRAM ([Electrosmith Daisy Seed](https://electro-smith.com/daisy/daisy)). Neither price includes the microphone, speaker, amplifier, connectors, enclosure, tax, or shipping.
- A small 5 V class-D amplifier fits the expected power system. The PAM8302 is a representative part, not a selection. It accepts 2.0-5.5 V, drives a 4-8 ohm speaker, provides up to 2.5 W, and includes thermal and over-current protection. Its board vendor charges USD 3.95 ([Adafruit PAM8302 product documentation](https://www.adafruit.com/product/2130), [Diodes Incorporated PAM8302A datasheet](https://cdn-shop.adafruit.com/datasheets/PAM8302A.pdf)). At maximum output, amplifier and processor together fit inside a deliberately reserved 5 V / 1 A continuous branch, though the actual shared power budget must be measured with the selected Eye Display.

## Processor options

### 1. Dedicated embedded-audio board: recommended

Use a board designed around synchronous audio callbacks and a codec, with the character effects compiled into its firmware.

**Daisy Seed family.** The currently documented original Seed supplies stereo 24-bit audio hardware, a 480 MHz Cortex-M7, SDRAM, and an open C++ audio framework ([Electrosmith Daisy Seed](https://electro-smith.com/daisy/daisy)). Its audio pins are line-level, so a bare microphone needs bias and a preamplifier; the official audio guide describes the input as typically line level or requiring a level-conversion circuit ([Daisy audio guide](https://docs.daisy.audio/tutorials/_a3_Getting-Started-Audio/)). It also needs a speaker amplifier. Daisy is the strongest starting point if a current, supported Seed-family board is available from an EU supplier when procurement begins.

**Teensy 4.x plus Audio Adapter.** Teensy has the friendliest documented effect graph for a beginner. Its SGTL5000 adapter supports a mono microphone input, simultaneous input/output, configurable microphone gain, line output, and codec-side limiting/EQ functions ([PJRC Audio Adapter](https://www.pjrc.com/store/teensy3_audio.html), [PJRC SGTL5000 control reference](https://www.pjrc.com/teensy/gui/?info=AudioControlSGTL5000)). However, SparkFun currently marks the Rev D2 adapter retired and unavailable, despite listing its former price as USD 14.95 ([SparkFun Audio Shield listing](https://www.sparkfun.com/teensy-4-audio-shield-rev-d2.html)). That procurement risk prevents making the Teensy stack the default without first locating genuine EU stock or choosing another supported codec board.

Either platform has ample compute for a deliberately simple mono effects chain. The Halloween decision should be based on local availability, complete audio I/O hardware, and which toolchain can produce a stable pass-through prototype fastest. Sample-rate marketing should not decide it.

### 2. Dedicated ESP32-S3 audio module: feasible, more integration work

ESP32-S3 has two I2S peripherals, and Espressif publishes an official DSP library with FFT, FIR, and IIR primitives ([ESP-IDF I2S documentation](https://docs.espressif.com/projects/esp-idf/en/stable/esp32s3/api-reference/peripherals/i2s.html), [ESP-DSP repository](https://github.com/espressif/esp-dsp)). Espressif also publishes speech front-end components for noise suppression, voice activity detection, AGC, and acoustic echo cancellation ([ESP-SR Audio Front End](https://docs.espressif.com/projects/esp-sr/en/latest/esp32/audio_front_end/README.html), [ESP-SR AEC](https://docs.espressif.com/projects/esp-sr/en/latest/esp32/acoustic_echo_cancellation/README.html)).

This makes a dedicated ESP32-S3 audio board credible, particularly if acoustic echo cancellation becomes necessary. It is not the shortest route to a customizable character voice: codec selection, full-duplex audio plumbing, effects, and AEC reference routing still have to be integrated. Running the Eye Display, wireless control, and live DSP on one ESP32-S3 is therefore a later optimization, not the recommended initial architecture.

### 3. Phone-based live processing: prototype only

A phone can supply far more sophisticated effects, but latency and audio routing vary by hardware and operating system. Android defines its `audio.pro` feature as continuous round-trip latency of 20 ms or less, notes that musicians generally need about 10 ms, and states there is no runtime API that determines latency over every path ([Android audio latency guidance](https://developer.android.com/ndk/guides/audio/audio-latency)). Apple exposes route latency, but warns that high-quality Bluetooth recording can increase input latency and is not recommended for real-time communication; that feature is also unavailable in the EU ([Apple Bluetooth recording guidance](https://developer.apple.com/documentation/avfaudio/avaudiosession/categoryoptions-swift.struct/bluetoothhighqualityrecording)).

A wired USB audio interface can improve predictability, but adds adapters, cable routing, operating-system interruptions, and phone battery dependence. The Phone Controller remains a good editor for preset parameters; it should not sit in the live audio path for the Halloween build.

### 4. Raspberry Pi Zero 2 W: capable but disproportionate

The Zero 2 W offers a 1 GHz quad-core CPU, 512 MB memory, Wi-Fi/Bluetooth, and a 65 x 30 mm board, but expects a 5 V / 2.5 A supply and has no headphone/speaker audio socket ([Raspberry Pi Zero 2 W product brief](https://datasheets.raspberrypi.com/rpizero2/raspberry-pi-zero-2-w-product-brief.pdf)). A complete build therefore needs Linux storage, an audio interface or codec, an amplifier, and a controlled startup/shutdown strategy. It is useful only if later effects require software that cannot reasonably run on an embedded audio board. It adds no necessary capability to the first speech-effects chain.

## Latency and intelligibility

Use **20 ms microphone-to-speaker latency as the maximum acceptance threshold and target 10 ms or less for the normal effects preset**. This is a project target derived from Android's published professional-audio thresholds, not a guarantee from any candidate board. Measure it after the microphone preamp, codec, chosen effects, output codec, and amplifier are assembled; summing block sizes is not sufficient.

Effects that require longer look-ahead, grains, or spectral windows can violate the target even when the base platform is fast. PJRC's granular pitch shifter, for example, records and replays grains from a user-sized memory buffer ([PJRC granular effect](https://www.pjrc.com/teensy/gui/?info=AudioEffectGranular)). It is reasonable to infer that larger grains trade responsiveness for smoother pitch shifting, but the documentation does not specify end-to-end delay. Pitch shifting must therefore have a bypass, and the project should not count on it until measured.

Intelligibility should drive the effect chain:

1. high-pass/DC filtering to remove breath and handling rumble;
2. a conservative noise gate or expander;
3. gentle compression;
4. a parallel character effect blended with some clean speech;
5. narrow corrective EQ where testing shows a need;
6. a final limiter followed by a physical gain setting.

This ordering is a proposed design, not a claim that one set of parameters works in every mask. Presets should expose only a few safe parameters: effect depth, modulation or pitch amount, tone, and output level. Keep limiter and absolute gain limits outside normal Phone Controller editing.

## Feedback is the main engineering risk

Feedback happens when amplified speaker output re-enters the microphone and is amplified repeatedly. Shure's engineering guidance identifies excessive gain, microphone distance from the desired source, loudspeaker proximity, frequency response, and room acoustics as interacting causes; its first remedies are moving the microphone closer to the mouth, moving the loudspeaker farther away, and using a directional microphone where appropriate ([Shure feedback guidance](https://service.shure.com/articles/en_US/Knowledge/how-do-i-fix-my-feedback-problem), [Shure live-sound microphone techniques](https://www.shure.com/damfiles/default/global/documents/publications/en/performance-production/microphone_techniques_for_live_sound_reinforcement_english.pdf-3df433145fca686a736beeb5da588efa.pdf)). No microphone or DSP algorithm can guarantee immunity.

For the Mask System this leads to concrete constraints:

- Put a small microphone within a few centimetres of the mouth, use a foam windscreen, and mechanically isolate it from the mask shell. Test both directional and omnidirectional capsules; the shell may alter the expected polar pattern.
- Do not mount the main loudspeaker beside the microphone or next to an ear. Prefer an outward-facing chest, shoulder, or below-chin speaker, and use the mask shell itself as part of the acoustic separation only after testing confirms it helps.
- Provide a physical mute or push-to-talk control that works without software. Start every boot muted and ramp gain up without clicks.
- Set maximum analog gain during a controlled test. A software limiter protects against signal peaks, but it cannot by itself prevent a feedback loop.
- Treat AEC as an optional second-stage experiment. Espressif's AEC requires both microphone input and a playback-reference channel and offers more aggressive modes that may damage near-end speech quality ([ESP-SR AEC](https://docs.espressif.com/projects/esp-sr/en/latest/esp32/acoustic_echo_cancellation/README.html)). Good geometry and sane gain remain prerequisites.

## Power, placement, and safety

A pocket USB-C power bank supplying a regulated 5 V bus is compatible with this class of Voice System. Reserve **5 V at 1 A continuous** for the optional branch and rate its connector for at least 2 A to tolerate transients and future amplifier changes. This is a design allowance, not a predicted constant draw. The eventual power ticket must measure the whole Mask System at idle, typical speech, and worst-case Eye Display brightness before selecting a bank.

The processor, preamp, and amplifier should be a removable module. Keeping the higher-current speaker wiring and amplifier off the face reduces heat and weight and makes troubleshooting safer. The microphone lead should be shielded or differential where the selected hardware supports it; keep it away from Eye Display and class-D speaker wiring. Provide strain relief and a quick-disconnect in any cable that runs from mask to clothing.

The loudspeaker must never compromise awareness of announcements, people, or hazards. NIOSH's occupational benchmark is 85 dBA over eight hours, with allowable duration halving for every 3 dB increase; 88 dBA corresponds to four hours ([NIOSH noise exposure guidance](https://www.cdc.gov/niosh/bulletin/2016/noise.html)). This is not a consumer-event legal limit, but it is a useful conservative check: measure combined event and Voice System level at the wearer's ear, prefer well below 88 dBA for the four-hour target, and never solve poor audience audibility by placing a louder speaker near the ear.

Use an amplifier with thermal and over-current protection and keep a hardware output mute accessible. If a bridge-tied class-D amplifier such as the PAM8302 is selected, neither speaker terminal may be tied to ground; the vendor explicitly identifies the output as bridge-tied ([Adafruit PAM8302 product documentation](https://www.adafruit.com/product/2130)). Connector and wiring documentation must preserve that constraint.

## Cost and schedule assessment

A realistic parts allowance is **EUR 50-100** for the Voice System module before contingency: approximately EUR 20-35 for the processor, EUR 5-20 for codec or microphone conditioning, EUR 4-15 for an amplifier, and the remainder for a microphone, speaker, controls, connectors, enclosure, and mounting. This is an order-of-magnitude planning estimate based on the cited board prices, not a procurement quote. It fits the overall EUR 200 target only if the Eye Display leaves sufficient room.

The Voice System should remain a stretch deliverable for 2026-10-17. Do not purchase it until the Eye Display architecture and power budget are known. If capacity remains, run one early bench experiment with the exact proposed microphone and speaker positions. Continue only if clean pass-through meets the latency, feedback, and intelligibility gates below; otherwise preserve the interfaces and defer the module without redesigning the Mask System.

Event rules may also restrict use even when the module works. The gamescom 2026 cosplay-contest FAQ says microphones are not permitted during the stage performance and requires spoken material to be prerecorded in the submitted MP3 ([gamescom contest FAQ](https://cosplaycontest.gamescom.global/faqs)). This is a contest-stage rule, not evidence of a general ban on a muteable wearable speaker elsewhere at the event. The Voice System therefore needs an obvious mute/bypass and should never be assumed usable at every venue; current event rules must be checked before each outing.

## Minimum interfaces to reserve now

The core Mask System specification should reserve the following without selecting the Voice System hardware yet:

1. **Power branch.** Reserve switched 5 V and ground, capable of 1 A continuous, on a polarized locking connector rated for at least 2 A. Include branch protection and enough total power-bank margin. Do not power the speaker amplifier from a 3.3 V logic rail.
2. **Control link.** Reserve 3.3 V UART TX/RX plus signal ground. The message contract needs commands for mute, preset selection, safe parameter updates, output level, status, and fault reporting. The Eye Display must boot and operate normally when no Voice System responds.
3. **Hardware mute.** Provide one independent active-low line or physical series control that forces the amplifier into shutdown regardless of firmware state. Power-up should default to mute.
4. **Serviceable audio harnesses.** Use separate keyed connectors for the mask microphone and body-worn speaker. Do not carry raw microphone or speaker signals through the general Eye Display harness. Document any bridge-tied speaker wiring.
5. **Physical path.** Provide strain-relieved routing from the mouth-area microphone to a quick-disconnect at the mask edge, plus a mounting location on clothing for the processor/amplifier and outward-facing speaker. No exact module bay needs to be reserved inside the mask.
6. **Control affordance.** Reserve one reachable Pocket Controller action for mute or push-to-talk. Phone loss must not prevent muting the output.

These interfaces keep Daisy, Teensy, ESP32-S3, and future processors viable while avoiding a commitment to any one codec or board.

## Prototype acceptance gates

Before the Voice System becomes part of an event build, verify all of the following with the intended mask, clothing, speaker position, and power source:

- **Latency.** Every enabled event preset stays at or below 20 ms microphone-to-speaker. Target 10 ms or less for the default preset. Measure from a recorded impulse on separate input/output channels.
- **Stability.** The system has no buffer underruns, resets, or audible digital artifacts during a 30-minute continuous speech and silence test while the Eye Display and wireless controls are active.
- **Feedback margin.** At the chosen event volume, movement through expected head and body poses does not produce ringing or sustained feedback. The system mutes immediately when the physical control is used.
- **Intelligibility.** Unfamiliar listeners at the intended distance can repeat at least 8 of 10 short test phrases in representative ambient noise. Compare transformed and bypassed speech.
- **Power and thermal.** The complete Mask System reaches the four-hour target, connectors stay within their ratings, and no skin-facing part becomes uncomfortably warm.
- **Hearing.** Measured level at the wearer's ear remains below the project's exposure ceiling in representative event noise. Lower the speaker or move it farther from the ear if it does not.
- **Failure isolation.** Disconnecting, muting, resetting, or crashing the Voice System does not interrupt the Eye Display or Pocket Controller.

Passing these gates makes the Voice System an installable module. Failing them leaves the core Halloween build intact and the reserved interface available for a later iteration.
