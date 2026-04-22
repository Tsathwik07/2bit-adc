# 2-Bit Flash ADC Using Comparators

## Overview
A 2-bit Flash ADC built using ideal OP07 op-amps as comparators
with inverted logic and a resistor divider reference network.

## Resolution
```
Resolution = Vref / 2^n = 5V / 4 = 1.25V per step
```

## Architecture
- 3 comparators (OP07 in open-loop)
- Resistor divider: 4 × 1.25kΩ → taps at 1.25V, 2.5V, 3.75V
- Inverted logic: Vin at (−) input, Vref at (+) input

## Truth Table
| Vin Range    | B1 | B0 | Decimal |
|--------------|----|----|---------|
| 0 – 1.25V    | 0  | 0  | 0       |
| 1.25 – 2.5V  | 0  | 1  | 1       |
| 2.5 – 3.75V  | 1  | 0  | 2       |
| 3.75 – 5V    | 1  | 1  | 3       |

## Boolean Encoding
```
B1 = NOT(C2)
B0 = (C2 XOR C1) OR (NOT(C3) AND NOT(C2))
```

## Files
- `1bit_adc.asc` — Given 1-bit comparator ADC
- `2bit_adc.asc` — 2-bit Flash ADC design
