# Furby-Connect-Mask-PCB
!!!!!!!!.THIS IS STILL A WORK IN PROGRESS.!!!!!!!
# Furby Sleep Mask PCB

A replacement for the small "sleep mask" ID board that plugs into a Furby, so you can choose which personality it reads. Changing the resistor values changes the personality.

## How it works

The Furby identifies the mask by measuring a voltage, not by talking to a chip. The board is a small resistor network:

- The host pulls **J5-7** low, then **J5-8** low, and reads the voltage on **J5-4** each time.
- **R62** (100k) pulls J5-4 up to 3V3 and **C68** (100 nF) filters it.
- **R41** sets the J5-7 reading and **R42** sets the J5-8 reading.

Reading = 3.3 V × R / (R + 100k). For example, 18k gives about 0.50 V and 110k gives about 1.73 V. Fit different resistors to pick a different personality.

## Board

- 2 layers, about 28.6 × 23.04 mm (1.126 × 0.907 in)
- Eight round contact pads on the back (W1–W8), the Furby's only contact
- Eight through-hole wire pads (J5-3 to J5-8, VDD, GND)
- Parts: R41, R42, R62 (0805, 1%), C68 (100 nF, 0805)
- Suggested order options: ENIG finish, 1.6 mm thickness

## Files

| File | Contents |
|---|---|
| `mask.kicad_sch` | Schematic |
| `mask.kicad_pcb` | PCB layout |
| `mask_trimmer_sweep_log.xlsx` | Log sheet for sweeping a trimmer to find resistor values |

## Status

Work in progress and **untested**.

- The circuit is inferred from measurements of the original board, not from Furby firmware.
- Board size, pad positions and passive sizes came from photos of the original, so check them against a real mask before ordering.
- The J5-3, J5-5 and J5-6 pads are not used in this resistor-only version.
- The EEPROM option on the original board footprint is not included.

## Finding resistor values

1. Replace R42 (or R41) with a multi-turn trimmer.
2. Step through values and record the Furby's response in the sweep log.
3. Fit fixed 1% resistors once you know which values work.
