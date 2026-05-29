# hl2b5up_4000

HL2 beta5+ gateware variant for HL2-4000 with 5 receivers and HL2LINK.

## Parameters

| Parameter | Value |
|-----------|-------|
| HL2_NR | 5 |
| HL2_NT | 0 |
| HL2_UART | 0 |
| HL2_ATU | 0 |
| HL2_FAN | 0 |
| HL2_CW | 0 |
| HL2_HL2LINK | 1 |
| HL2_AK4951 | 0 |
| HL2_EXTENDED_DEBUG_RESP | 0 |
| HL2_BYPASS_VERSA | 0 |
| BETA5 | 1 |
| USE_ALTSYNCRAM | 1 |
| CW_ENV_ROM | 1 |

## DB1 Connector

DB1 is the 20-pin expansion connector. Pins 1-6 operate at 2.5V (Vlvds), remaining signal pins at 3.3V. Pins 10 and 12 are input-only. Full pinout: [docs/hl2_build9_connectors_signals_fpga_pins.md](../../docs/hl2_build9_connectors_signals_fpga_pins.md).

This is a receive-only variant for HL2-4000 hardware. All DB1 signal pins are assigned but most are functionally idle (TX, UART, ATU, Fan, CW all disabled). Only io_db1_1 (TX envelope PWM signal still driven by core) and io_db1_5 (ATU ACK with pull-up) have active signals.

| DB1 Pin | FPGA | Signal | Dir | Function | Status |
|---------|------|--------|-----|----------|--------|
| 1 | PIN_72 | io_db1_1 | out | TX envelope PWM | Signal driven (no TX active) |
| 2 | PIN_76 | io_db1_2 | in | UART RX | Idle (UART disabled) |
| 3 | PIN_77 | io_db1_3 | out | UART TX | Idle (UART disabled) |
| 4 | PIN_80 | io_db1_4 | out | Fan PWM | Idle (Fan disabled) |
| 5 | PIN_83 | io_db1_5 | in | ATU acknowledge | Idle (ATU disabled, weak pull-up) |
| 6 | PIN_85 | io_db1_6 | out | ATU request | Idle (ATU disabled) |
| 9 | PIN_98 | io_led_d2 | out | Run LED | Active |
| 10 | PIN_90 | io_phone_ring | in | CW/PTT ring | Idle (CW disabled) |
| 11 | PIN_99 | io_led_d3 | out | TX LED | Active |
| 12 | PIN_91 | io_phone_tip | in | CW/PTT tip | Idle (CW disabled) |
| 13 | PIN_100 | io_led_d4 | out | ADC 75% LED | Active |
| 14 | PIN_101 | io_led_d5 | out | ADC 100% LED | Active |
| 15 | PIN_103 | clk_scl1 | inout | I2C bus 1 SCL | Active |
| 16 | PIN_104 | clk_sda1 | inout | I2C bus 1 SDA | Active |
| 17 | PIN_31 | io_scl2 | inout | I2C bus 2 SCL | Active |
| 18 | PIN_30 | io_sda2 | inout | I2C bus 2 SDA | Active |
