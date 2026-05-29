# hl2b5up_main

Standard HL2 beta5+ gateware variant with full features.

## Parameters

| Parameter | Value |
|-----------|-------|
| HL2_NR | 4 |
| HL2_NT | 1 |
| HL2_UART | 1 |
| HL2_ATU | 1 |
| HL2_FAN | 1 |
| HL2_CW | 1 |
| HL2_HL2LINK | 1 |
| HL2_AK4951 | 0 |
| HL2_EXTENDED_DEBUG_RESP | 1 |
| HL2_BYPASS_VERSA | 0 |
| BETA5 | 1 |
| USE_ALTSYNCRAM | 1 |
| CW_ENV_ROM | 1 |

## DB1 Connector

DB1 is the 20-pin expansion connector. Pins 1-6 operate at 2.5V (Vlvds), remaining signal pins at 3.3V. Pins 10 and 12 are input-only. Full pinout: [docs/hl2_build9_connectors_signals_fpga_pins.md](../../docs/hl2_build9_connectors_signals_fpga_pins.md).

| DB1 Pin | FPGA | Signal | Dir | Function |
|---------|------|--------|-----|----------|
| 1 | PIN_72 | io_db1_1 | out | TX envelope PWM (Versa clock) |
| 2 | PIN_76 | io_db1_2 | in | UART RX |
| 3 | PIN_77 | io_db1_3 | out | UART TX |
| 4 | PIN_80 | io_db1_4 | out | Fan PWM |
| 5 | PIN_83 | io_db1_5 | in | ATU acknowledge (weak pull-up) |
| 6 | PIN_85 | io_db1_6 | out | ATU request |
| 9 | PIN_98 | io_led_d2 | out | Run LED (via R71) |
| 10 | PIN_90 | io_phone_ring | in | CW/PTT ring (input only) |
| 11 | PIN_99 | io_led_d3 | out | TX LED (via R72) |
| 12 | PIN_91 | io_phone_tip | in | CW/PTT tip (input only) |
| 13 | PIN_100 | io_led_d4 | out | ADC 75% LED (via R73) |
| 14 | PIN_101 | io_led_d5 | out | ADC 100% LED (via R74) |
| 15 | PIN_103 | clk_scl1 | inout | I2C bus 1 SCL (Versa clock) |
| 16 | PIN_104 | clk_sda1 | inout | I2C bus 1 SDA (Versa data) |
| 17 | PIN_31 | io_scl2 | inout | I2C bus 2 SCL |
| 18 | PIN_30 | io_sda2 | inout | I2C bus 2 SDA |
