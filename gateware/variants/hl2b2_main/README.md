# hl2b2_main

Hermes-Lite 2 board revision 2 (beta 2) main gateware variant.

## Parameters

| Parameter | Value | Description |
|-----------|-------|-------------|
| BETA2     | 1     | Board revision 2 |
| HL2_NR    | 4     | Number of receivers |
| HL2_NT    | 1     | Number of transmitters |
| HL2_UART  | 1     | UART enabled |
| HL2_ATU   | 0     | ATU disabled |
| HL2_FAN   | 1     | Fan control enabled |
| HL2_CW    | 1     | CW mode enabled |
| HL2_HL2LINK | 1   | HL2Link enabled |
| HL2_AK4951 | 0    | AK4951 codec disabled |
| HL2_EXTENDED_DEBUG_RESP | 0 | Extended debug disabled |
| HL2_BYPASS_VERSA | 0  | Versa bypass disabled |

## Expansion Connector Pin Usage

BETA2 boards use different connector names and physical wiring than B5+ (which uses DB1). The same FPGA pins are used but with different signal assignments and connector names.

| FPGA Pin | Signal | Dir | Connector | Function |
|----------|--------|-----|-----------|----------|
| PIN_72 | io_cl1 | out | CL1 | TX envelope PWM output |
| PIN_76 | io_db24_1 | out | DB24 | UART TX |
| PIN_77 | io_phone_tip | in | Phone | CW/PTT tip |
| PIN_80 | io_phone_ring | in | Phone | CW/PTT ring |
| PIN_83 | io_cn4_6 | out | CN4 | Fan PWM |
| PIN_85 | io_cn4_7 | out | CN4 | Unused (assigned, no core connection) |
| PIN_90 | io_db22_3 | in | DB22 | Unused |
| PIN_91 | io_db22_2 | in | DB22 | Unused |
| PIN_98 | io_led_d2 | out | LED | Run LED |
| PIN_99 | io_led_d4 | out | LED | ADC 75% LED |
| PIN_100 | io_led_d3 | out | LED | TX LED |
| PIN_101 | io_led_d5 | out | LED | ADC 100% LED |
| PIN_103 | clk_sda1 | inout | I2C1 | I2C bus 1 SDA (swapped vs B5+) |
| PIN_104 | clk_scl1 | inout | I2C1 | I2C bus 1 SCL (swapped vs B5+) |
| PIN_31 | io_scl2 | inout | I2C2 | I2C bus 2 SCL |
| PIN_30 | io_sda2 | inout | I2C2 | I2C bus 2 SDA |

Note: LED D3/D4 pins (99/100) and I2C1 SCL/SDA pins (103/104) are physically swapped compared to B5+.
