# Hermes-Lite 2 (Beta 5+) AK4951 v3 + Yaesu Band Voltage

AK4951 v3 audio codec variant with Yaesu-compatible band voltage output for controlling external amplifiers/tuners.

## Differences from hl2b5up_ak4951v3

| Parameter | hl2b5up_ak4951v3 | hl2b5up_ak4951v3_yaesu |
|---|---|---|
| `HL2_UART` | 1 | 0 |
| `HL2_BANDV_YAESU` | not defined | 1 |

## Differences from hl2b5up_main

| Parameter | hl2b5up_main | hl2b5up_ak4951v3_yaesu |
|---|---|---|
| `HL2_AK4951` | 0 | 1 |
| `AK4951` | not defined | 1 |
| `HL2_CW` | 1 | 2 (iambic) |
| `HL2_ATU` | 1 | 0 |
| `HL2_UART` | 1 | 0 |
| `HL2_HL2LINK` | 1 | 0 |
| `HL2_BANDV_YAESU` | not defined | 1 |

## Parameters

| Parameter | Value |
|---|---|
| `HL2_NR` | 4 (receivers) |
| `HL2_NT` | 1 (transmitter) |
| `HL2_CW` | 2 (iambic keyer) |
| `HL2_ATU` | 0 |
| `HL2_UART` | 0 |
| `HL2_FAN` | 1 |
| `HL2_HL2LINK` | 0 |
| `HL2_AK4951` | 1 |
| `HL2_EXTENDED_DEBUG_RESP` | 0 |
| `HL2_BYPASS_VERSA` | 0 |
| `HL2_BANDV_YAESU` | 1 |
| `CW_ENV_ROM` | 1 |

## DB1 Connector

DB1 is the 20-pin expansion connector. Pins 1-6 operate at 2.5V (Vlvds), remaining signal pins at 3.3V. Pins 10 and 12 are input-only. Full pinout: [docs/hl2_build9_connectors_signals_fpga_pins.md](../../docs/hl2_build9_connectors_signals_fpga_pins.md).

The `AK4951=1` macro repurposes DB1 pins for the I2S audio codec interface. The `HL2_BANDV_YAESU=1` macro further repurposes DB1-3 from UART TX to fan PWM, freeing the UART TX line. UART is fully disabled.

| DB1 Pin | FPGA | Signal | Dir | Function |
|---------|------|--------|-----|----------|
| 1 | PIN_72 | io_db1_1 | out | TX envelope PWM (Versa clock) |
| 2 | PIN_76 | io_db1_2 | **out** | I2S MOSI (data to AK4951 codec) |
| 3 | PIN_77 | io_db1_3 | out | Fan PWM (Yaesu: UART TX repurposed) |
| 4 | PIN_80 | io_db1_4 | **in** | External PTT input (weak pull-up) |
| 5 | PIN_83 | io_db1_5 | in | External TR clone (weak pull-up) |
| 6 | PIN_85 | io_db1_6 | out | AK4951 codec power down (i2s_pdn) |
| 9 | PIN_98 | io_led_d2 | out | Run LED (via R71) |
| 10 | PIN_90 | io_phone_ring | in | Iambic dash paddle (input only) |
| 11 | PIN_99 | io_led_d3 | out | TX LED (via R72) |
| 12 | PIN_91 | io_phone_tip | in | Iambic dot paddle (input only) |
| 13 | PIN_100 | io_led_d4 | out | ADC 75% LED (via R73) |
| 14 | PIN_101 | io_led_d5 | out | ADC 100% LED (via R74) |
| 15 | PIN_103 | clk_scl1 | inout | I2C bus 1 SCL (Versa clock) |
| 16 | PIN_104 | clk_sda1 | inout | I2C bus 1 SDA (Versa data) |
| 17 | PIN_31 | io_scl2 | inout | I2C bus 2 SCL |
| 18 | PIN_30 | io_sda2 | inout | I2C bus 2 SDA |

Additional I2S signals (not on DB1): `io_link_tx[0]` = I2S BCK, `io_link_tx[1]` = I2S LRCK, `io_link_rx[0]` = I2S MISO (from codec).

## Features

- AK4951 audio codec with I2S interface
- Iambic CW keyer
- Yaesu band voltage output (HL2_BANDV_YAESU=1)
- No UART (pin used for Yaesu band voltage)
- Uses `timing_ak4951.sdc`

## Building

```
cd variants/hl2b5up_ak4951v3_yaesu
make
```

Requires Quartus Prime Lite 23.1 or later. Output: `build/hermeslite.rbf`, `build/hermeslite.jic`.
