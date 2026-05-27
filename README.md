# EA5IUE Gateware for Hermes-Lite 2

FPGA gateware for the [Hermes-Lite 2](https://hermeslite.com/) SDR transceiver, build 74.3.

## Origins

This is a minor fork of the [softerhardware/Hermes-Lite2](https://github.com/softerhardware/Hermes-Lite2) gateware, which itself incorporates contributions from multiple authors over the years:

- **Steve Haynal KF7O** — core architecture, AD9866 control, hermeslite_core (2014-2019)
- **Phil Harman VK6APH / VK6PH** — HPSDR radio, FIR filters, iambic keyer, CIC interpolator (2013-2014)
- **James Ahlstrom N2ADR** — original FIR filter and interpolator code (2011)
- **Alex Shovkoplyas VE3NEA** — original receiver design (2008)
- **Takashi Komatsumoto JI1UDD** — CW sidetone, CW envelope ROM, extamp, exttuner, AK4951 audio (2018-2021)

All original code is licensed under the GNU General Public License v2.

## What Changed

Minor tweaks and bug fixes. My experience in radio and retro FPGA systems makes it impossible for me to see an FPGA and not reprogram it. Changes from upstream 74.2 include:

- Unified `hermeslite.v` with `ifdef`-based parameterization via QSF `VERILOG_MACRO` definitions
- CW envelope ROM (`cw_env_rom.v`) for shaped CW keying
- CW sidetone generation with sigma-delta DAC for iambic mode (CW=2)
- Yaesu band voltage output variants
- Build fixes and warning cleanups

## Variants

| Variant | Board | Description |
|---------|-------|-------------|
| `hl2b2_main` | HL2 b2 | Main, 4 RX, 1 TX |
| `hl2b3to4_main` | HL2 b3/b4 | Main, 4 RX, 1 TX |
| `hl2b3to4_cicrx` | HL2 b3/b4 | CIC-only RX, 10 RX, no TX |
| `hl2b5up_main` | HL2 b5+ | Main, 4 RX, 1 TX, ATU, fan, HL2Link |
| `hl2b5up_main_iambic` | HL2 b5+ | Main with iambic keyer + sidetone DAC |
| `hl2b5up_6rx` | HL2 b5+ | 6 RX |
| `hl2b5up_cicrx` | HL2 b5+ | CIC-only RX, 10 RX |
| `hl2b5up_15ce` | HL2 b5+ | 15 CE region |
| `hl2b5up_ak4951v3` | HL2 b5+ | AK4951 companion board v3 |
| `hl2b5up_ak4951v3_yaesu` | HL2 b5+ | AK4951 v3 + Yaesu band voltage |
| `hl2b5up_ak4951v4_yaesu` | HL2 b5+ | AK4951 v4 + Yaesu band voltage |

## Building

Requires [Intel Quartus Prime Lite 23.1](https://www.intel.com/content/www/us/en/software/programmable/quartus-prime/download.html) for Cyclone IV E.

```bash
# Build a single variant
make -C gateware/variants/hl2b5up_main

# Build all variants
make -C gateware/variants
```

## License

GPLv2, same as the upstream project.
