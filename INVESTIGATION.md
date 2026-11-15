# Investigation and test notes

## Findings

- **v0.1:** changed the backend suffix to `speaker-and-receiver` but did not define the matching usecase-prefixed mixer paths. The Qualcomm HAL composes a route name from the usecase and backend suffix, so it could not find the standalone path.
- **v0.2:** restored the `speaker` backend but put receiver controls in a standalone path instead of the active usecase paths.
- **v0.3:** nested a forward-referenced `rcv-media` path and enabled an RX backend link before PCM open; route parsing skipped the missing nested path and the early link was a plausible reason audio failed.
- **v0.4/v0.4.1:** runtime mixer controls did not open the receiver hardware interface because the HAL still used the WSA-only interface.
- **v0.5/v0.6:** retained the HAL `speaker` suffix, changed the speaker interface to WSA+RX, and added receiver controls directly to the eight active media usecase paths. Android logs confirmed the route was applied and receiver controls were active.
- **v0.7:** RX-only test confirmed media could be heard through the earpiece alone, but it was faint.
- **v0.8:** matched the stock handset route with receiver digital level 80 and `EAR PA Gain=G_6_DB`; the owner reported it was close to the remembered original earpiece loudness.
- **v0.9:** set the earpiece to 84 and restored both WSA and RX links. The owner confirmed the stereo route worked.

## Current v0.9 route

`SND_DEVICE_OUT_SPEAKER` retains the `speaker` backend suffix and uses `WSA_CDC_DMA_RX_0-and-RX_CDC_DMA_RX_0`. The eight tested speaker media paths link both front ends. Receiver digital level is 84; `EAR PA Gain` remains `G_6_DB`. Headphone-specific and call paths were not edited.

## Rollback

Disable or uninstall the Magisk module and reboot. No vendor file is overwritten outside the Magisk overlay.
