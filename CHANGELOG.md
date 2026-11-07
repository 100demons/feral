# Changelog

## 9.0 — first public version

- Nine models on one added machine: NYB (bytebeat), GND (Gendy), BNJ (Benjolin), RYT (Rhythmicon resonators),
  FRS (Fourses), RNG (HAVOC rungler), PLS (pulsar), SCN (scanned synthesis) and KOS (logistic map).
- COLOR and SWEEP are the model's two macros; CONTOUR is the tone envelope (a third control on BNJ and RNG);
  PUNCH is FREE.
- Tested on a real Model:Cycles on 2026-10-22, standalone.
- Packaged for the cycles-engines flasher at slot 7 (OS machine 6), with the custom SHAPE names through the
  registrar runtime.

## Source fix after 9.0

- `CUSTOM[]` is indexed by engine id, and SCN's engine id is 9, so the old nine-entry table read one byte past its
  end. It is now `CUSTOM[10]`, with 0 for SCN. SCN sounds exactly as before; only the out-of-bounds read is gone.
  The fix is in the committed source and object here. The source tree records it as 9.0.1; the flasher label
  remains 9.0.
