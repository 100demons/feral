# FERAL — nine noisy, unpredictable synthesis models for the Model:Cycles

FERAL is one added machine for the **Elektron Model:Cycles**, OS 1.13: nine noisy, unpredictable synthesis models
on one machine, light on the processor. COLOR and SWEEP are the model's two macros; CONTOUR is the tone envelope
(or a third control on BNJ and RNG); PUNCH is FREE.

This repository is the machine's **source package**, published so that other projects can port it. It is not a
firmware and contains none.

**Hear it:** [FERAL on YouTube](https://www.youtube.com/watch?v=r4Z3FvKYv5k)  
**Flasher:** [100demons.github.io/cycles-engines/flasher](https://100demons.github.io/cycles-engines/flasher/) —
tick FERAL and bring your own official `model-cycles_OS1.13.syx`.

## The models

SHAPE picks the model. The names are shown on the machine's screen.

| SHAPE | Model | What it is |
|---:|---|---|
| 0 | NYB | Nyblcore: bytebeat formulas over an 8 kHz counter |
| 1 | GND | Gendy: per-period waveform from random-walk points |
| 2 | BNJ | Benjolin: two triangles plus an 8-bit rungler clocked by OSC2 |
| 3 | RYT | Rhythmicon: ten partials as 2-pole ping resonators |
| 4 | FRS | Fourses: four points reflecting between neighbors, averaged |
| 5 | RNG | Rungler: 8-bit register quantized to fifths/octaves |
| 6 | PLS | Pulsar: windowed sine pulses at COLOR × pitch |
| 7 | SCN | Scanned synthesis: 32-mass ring scanned at note pitch |
| 8 | KOS | Chaotic map: x → r·x(1−x), 16 iterations per period |

## The knobs

| Knob | What it does |
|---|---|
| PITCH / FINE | the note, as on every machine |
| COLOR | the model's first macro; the value window names the real control for that model |
| SHAPE | the model (the table above) |
| SWEEP | the model's second macro |
| CONTOUR | the tone envelope; a third control on BNJ and RNG |
| DECAY | the stock amp envelope |
| GATE | on, with extended note lengths, is recommended for all synthesis types |
| PUNCH | the FREE switch: off, each trig restarts the engine; on, it keeps running between trigs, so patterns drift. On BNJ it locks the random loop into a repeating cycle |

## Status

| | |
|---|---|
| Package | `cycles-mod/0.1`, the model27/cycles-engines package format |
| Slot in the flasher | 7 (the OS numbers it machine 6) |
| Committed object | `feral.o`; `core/build_engine.py feral --check` passes |
| Emulated | the source tree's nine-model voice-loop proof, 2026-10-22 |
| Tested on a real Model:Cycles | **yes** — 2026-10-22, standalone; the composed package build is new |
| Weight | the worst model is 4,801 instructions per 32-sample block, against 5,290 for TONE |
| License | MIT |

FERAL is the only one of the flasher engines that has been played on hardware. The hardware test covers the
standalone build; the package's own composed build has not been separately tested.

## Package layout

```
tools/machines/feral/
  manifest.json    the package: build recipe, symbols, claims, tests, compatibility
  card.json        the flasher card: label, description, status, video
  tiny2.c          the voice-loop bridge
  tiny2_dsp.h      the model dispatcher and shared DSP
  tiny2_eng_a.h … tiny2_eng_e.h   the nine models
  tiny2_tables.h   the generated tables
  feral_ui.S       the custom SHAPE names through the registrar runtime
  feral_icons.h    the machine-page splash
  feral.o          the committed relocatable object
  LICENSE          MIT
```

There is no firmware here: the package is applied to the user's own official OS file by a host such as
[cycles-engines](https://github.com/100demons/cycles-engines).

## Build and check the object

The package builds with the **cycles-engines** toolchain. Copy `tools/machines/feral/` into a cycles-engines
checkout as `engines/feral/`, then:

```sh
export M68K_CROSS=/path/to/bin/m68k-elf-        # or have m68k-elf-gcc on PATH
python3 core/build_engine.py feral --check
```

`--check` rebuilds `feral.o` from the sources and the manifest's recipe and compares it with the committed object.
The composer and the flasher never need the toolchain: they place the committed object.

## Install

Easiest: tick **FERAL** in the [flasher](https://100demons.github.io/cycles-engines/flasher/) and bring your own
official OS 1.13 file. Or download `feral-9.0.zip` from this repository's Releases and add the folder to your own
build.

## Credits

- Engine, tables and design: **100demons and Claude**, MIT.
- See [THIRD-PARTY-NOTICES.md](THIRD-PARTY-NOTICES.md).

## Changelog

See [CHANGELOG.md](CHANGELOG.md).
