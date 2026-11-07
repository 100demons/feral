# Third-party notices

## Synthesis models

FERAL's nine models follow published synthesis ideas — bytebeat, Gendy, Benjolin, the Rhythmicon, Fourses, a
rungler, pulsar, scanned synthesis and the logistic map. The code and tables were written for this machine; no
third-party code, table, sample or firmware is included.

## Elektron

No Elektron firmware is included in this repository, original or modified, nor anything extracted from one — no
section, no dump, no copied routine. The machine is source code and a relocatable object; it is applied to a user's
own official `model-cycles_OS1.13.syx` by the host project's build.

Model:Cycles and Model:Samples are trademarks of Elektron Music Machines MAV AB. This project is independent and
not affiliated with, endorsed by or supported by Elektron.

## Tools this package is built with

| Component | Licence | How it is used |
|---|---|---|
| GNU m68k GCC and binutils | GPL | compiles and links `feral.o`; not distributed here |
| cycles-engines | MIT | the package format, composer and build; not distributed here |
