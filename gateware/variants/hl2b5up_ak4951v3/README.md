# hl2b5up_ak4951v3

HL2 beta5+ gateware variant with AK4951 audio codec (v3), no ATU.

## Parameters

| Parameter | Value |
|-----------|-------|
| HL2_NR | 4 |
| HL2_NT | 1 |
| HL2_UART | 1 |
| HL2_ATU | 0 |
| HL2_FAN | 1 |
| HL2_CW | 2 |
| HL2_HL2LINK | 0 |
| HL2_AK4951 | 1 |
| HL2_EXTENDED_DEBUG_RESP | 0 |
| HL2_BYPASS_VERSA | 0 |
| BETA5 | 1 |
| USE_ALTSYNCRAM | 1 |
| CW_ENV_ROM | 1 |
| AK4951 | 1 |

## Extra Files

- SDC: `timing_ak4951.sdc`
- QIP: `sin1k9r.qip`, `mult_s9_s8_s16.qip`, `mult_s16_s8_s16.qip`
