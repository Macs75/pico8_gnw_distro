# PICO-8 Engine for Game & Watch Retro-Go SD

Binary releases of the PICO-8 engine for [Game & Watch Retro-Go SD](https://github.com/Macs75/game-and-watch-retro-go-sd) firmware.

This engine runs PICO-8 `.p8` and `.p8.png` cartridges on Nintendo Game & Watch hardware (STM32H7B0).

## Installation

1. Download the latest release archive
2. Copy the files to your SD card:
   ```
   SD:/cores/pico8.bin
   SD:/cores/pico8.ro
   SD:/cores/pico8_itcm.bin
   ```
3. Place your PICO-8 cartridges (`.p8` or `.p8.png`) in:
   ```
   SD:/roms/pico8/
   ```

That's it. Select a cart from the Retro-Go menu and it will launch with the engine.

## Requirements

- Game & Watch (Mario or Zelda edition) with Retro-Go SD firmware installed and SD card harware mod.
- The GPL firmware already includes a stub that shows an install message if the engine binaries are missing

## Files

| File | Description |
|------|-------------|
| `pico8.bin` | Engine data (loaded to RAM) |
| `pico8.ro` | Engine code (cached to flash, executed in place) |
| `pico8_itcm.bin` | Engine code (loaded in ITCM RAM for faster execution) |

## Multicart Support

Carts that load other carts via `load("#id")` will search:
- `SD:/roms/pico8/`
- `SD:/roms/pico8/.multicarts/`

Place the required sub-carts in either folder. use the ".multicart" folder to keep them hidden and show only the main cart in "roms/pico8"

## Save state support

The p8-engine provide savestate functionality ( 10 slots ), savestates will be saved in :
```
SD:/data/pico8/
```

## Cart Data Persistence

Carts that use `cartdata()`/`dset()`/`dget()` save their data to:
```
SD:/data/pico8/cdata/
```

## Compatibility

This engine aims for high compatibility with PICO-8 0.2.7 cartridges. Most carts work out of the box. Performance-heavy carts may run slower than 30fps on the G&W hardware.
Due to limited memory available on the G&W several carts are known to fail with "out of memory" errors of different flawors. 
Please check this page in case of problems to see if it's one of the carts known already for having issues: [Link](https://docs.google.com/spreadsheets/d/e/2PACX-1vQNI6r0leMszzNdeeKP-FVt0293E84rckfE7MAFvA8XNg6kN-lEK6wfkMXCnMAnP8cVEj59EO33zW01/pubhtml)

In case the game is not present please report it [here](https://github.com/Macs75/pico8_gnw_distro/issues) , It will be added to the list or if possible fixed.

## License

The engine binary is a software reimplementation of the pico8 api. It uses z8lua as a base, heavily modified for optimization/compatibility for STM32. The firmware that loads it ([game-and-watch-retro-go-sd](https://github.com/Macs75/game-and-watch-retro-go-sd)) is GPL-licensed and can be built and flashed independently. The firmware works without this engine — it simply shows an install prompt when a PICO-8 cart is selected.

## Links

- [Retro-Go SD Firmware (GPL)](https://github.com/Macs75/game-and-watch-retro-go-sd)
- [PICO-8 Fantasy Console](https://www.lexaloffle.com/pico-8.php) by Lexaloffle
- [Z8lua](https://github.com/samhocevar/z8lua)
