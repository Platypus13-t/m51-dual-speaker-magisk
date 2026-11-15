# Galaxy M51 Dual-Speaker Magisk Module

A reversible Magisk test module that routes built-in media to both the Galaxy M51 bottom speaker and receiver earpiece.

## Current tested build

- **v0.9**, confirmed working by the phone owner
- Samsung Galaxy M51 **SM-M515F** (SM6150), tested on LineageOS 23.2 / Android 16
- Receiver level 84 with `EAR PA Gain=G_6_DB`
- Ordinary media played through both the bottom speaker and earpiece

## Files

- [Flashable v0.9 module](M51_Dual_Speaker_Stereo_Test_v0.9.zip)
- [Source archive](M51_Dual_Speaker_Magisk_Source_v0.9.zip), with module source and investigation notes
- [Investigation notes](INVESTIGATION.md)

## Install and rollback

Install the flashable ZIP from Magisk's Modules screen, then reboot. Use only on the listed model. To roll back, disable or remove `m51_dual_speaker_test` in Magisk and reboot; this restores the original vendor audio XML through Magisk's overlay mechanism.

## Verification limits

Built-in media stereo routing was confirmed by listening. Calls were not changed. Wired-headphone-specific routes were left as supplied by the phone, but a physical headphone test has not been done.
