# BLM3061 – 8086 Assembly Labs

8086 assembly (MASM) lab assignments for the BLM3061 Microprocessor Systems course.

## Lab 2 – Parking Fee Calculator

Computes parking fees from a list of parking durations, then finds the average fee
and how many fees are above that average.

### How it works

1. **Fee calculation:** each duration in `PARK_SURELERI` is multiplied by the hourly
   rate `SAAT_UCRETI`. The result is stored in `UCRETLER` and added to a running total.
2. **Average:** the total is divided by `N` (integer division). The result is stored
   in `ORTALAMA_UCRET`.
3. **Count above average:** fees strictly greater than the average are counted.
   The count is stored in `ORTALAMA_USTU_SAYISI`.

### Data

| Variable               | Description                 | Default         |
|------------------------|-----------------------------|-----------------|
| `PARK_SURELERI`        | Parking durations (hours)   | `2, 5, 1, 8, 3` |
| `N`                    | Number of entries           | `5`             |
| `SAAT_UCRETI`          | Hourly rate                 | `20`            |
| `UCRETLER`             | Computed fees (output)      | –               |
| `ORTALAMA_UCRET`       | Average fee (output)        | –               |
| `ORTALAMA_USTU_SAYISI` | Fees above average (output) | –               |

### Expected output (default data)

| Output                 | Value                  |
|------------------------|------------------------|
| `UCRETLER`             | `40, 100, 20, 160, 60` |
| `ORTALAMA_UCRET`       | `76` (380 / 5)         |
| `ORTALAMA_USTU_SAYISI` | `2` (100 and 160)      |

## Building and running

Requires MASM 5.x and LINK, run in DOSBox or another DOS environment.
The toolchain is not included in this repository.

```
masm LAB2.ASM;
link LAB2.OBJ;
debug LAB2.EXE
```

The program writes no output to the screen. To see the results, check memory in DEBUG:
use `g` to run up to the `RETF` instruction, then `d ds:0` to dump the data segment.
