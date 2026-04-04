![GitHub Release](https://img.shields.io/github/v/release/hexbyt3/Cfw4sysbots)
![GitHub Downloads (all assets, all releases)](https://img.shields.io/github/downloads/hexbyt3/Cfw4sysbots/total?color=violet)


# CFW4SysBots - Nintendo Switch SysBot Setup

Everything you need to run SysBot.NET on a modded Nintendo Switch. Releases are built automatically with the latest upstream components — no manual assembly required.

![Discord Banner 2](https://discord.com/api/guilds/1369342739581505536/widget.png?style=banner2)

## What's Included

Every release automatically pulls the latest versions of:

| Component | Source | Purpose |
|-----------|--------|---------|
| **Atmosphere** | [Atmosphere-NX/Atmosphere](https://github.com/Atmosphere-NX/Atmosphere) | Custom firmware |
| **Hekate** | [CTCaer/hekate](https://github.com/CTCaer/hekate) | Bootloader (mod-chipped only) |
| **AetherBlock** | [hexbyt3/AetherBlock](https://github.com/hexbyt3/AetherBlock) | DNS blocker, firmware manager, CFW updater |
| **sys-botbase** | [olliz0r/sys-botbase](https://github.com/olliz0r/sys-botbase) | SysBot.NET system module |
| **ldn_mitm** | [Lusamine/ldn_mitm](https://github.com/Lusamine/ldn_mitm/tree/for_sbnet) | Local wireless proxy for Sword/Shield |
| **JKSV** | [J-D-K/JKSV](https://github.com/J-D-K/JKSV) | Save file manager |
| **ftpd** | [mtheall/ftpd](https://github.com/mtheall/ftpd) | FTP server |
| **Daybreak** | Bundled with Atmosphere | Firmware installer |

## Download

Grab the latest release for your console type:

- **[CFW4SysBots-mod-chipped.zip](https://github.com/hexbyt3/CFW4SysBots/releases/latest)** — For Mariko/patched Switches with mod chips
- **[CFW4SysBots-unpatched.zip](https://github.com/hexbyt3/CFW4SysBots/releases/latest)** — For unpatched Switches (RCM exploit)

## Setup Guide

### Mod-Chipped Switches

1. Format your SD card to FAT32 using the included `tools/fat32Formater.exe`
2. Extract the ZIP contents to the root of your SD card (the `tools/` folder is fine to include — the Switch ignores it)
3. Power on — the mod chip boots into Hekate automatically
4. Select "Payloads" → "fusee.bin" to boot Atmosphere

### Unpatched Switches

1. Format your SD card to FAT32
2. Extract the ZIP contents to the root of your SD card
3. Power off, insert RCM jig, hold VOL+ and press POWER
4. Connect to PC, run `tools/TegraRCM/TegraRcmGUI.exe`
5. Inject `fusee.bin` payload

## Updating

### Update Order

**Always update CFW before firmware.** Atmosphere must support the firmware version you're running. Updating firmware first without updating Atmosphere will prevent your Switch from booting into CFW.

### Using AetherBlock (recommended — no PC needed)

**Step 1: Update CFW**
1. Open AetherBlock from the Homebrew Menu
2. Press **ZR** → CFW Package Updater
3. Press **A** to check for updates, then **A** again to download and install
4. **Don't reboot yet** — the new files are on your SD card and take effect on the next boot

**Step 2: Update Nintendo Firmware (if needed)**
1. Press **B** to go back, then **ZL** → Firmware Manager
2. Select the firmware version you want and press **A** to download
3. Press **A** to launch Daybreak when extraction completes
4. Confirm the install in Daybreak and **reboot once** — both updates take effect

No PC, no jig, no RCM, no payload injection. One reboot and you're done.

### Manual Update (from PC)

1. Download the latest release ZIP for your console type from this repo
2. Extract everything to the root of your SD card, overwriting when prompted
3. Reboot into the updated Atmosphere
4. If you also need to update Nintendo firmware, use Daybreak (`switch/daybreak.nro`) with firmware files placed in `/firmware/`

Your save data in the `Nintendo/` folder is never touched by either method.

## How Releases Are Built

This repo contains only configuration files and a CI workflow. When a release is tagged, GitHub Actions:

1. Pulls the latest releases of all components from their upstream repos
2. Assembles the SD card structure with our custom configs overlaid
3. Packages both mod-chipped and unpatched variants
4. Publishes the release with both ZIPs

No binaries are stored in git — everything is always fresh from upstream.

## Repository Structure

```
configs/
  common/          Shared configs (system_settings.ini, hosts, themes)
  mod-chipped/     Hekate boot config, warmboot binaries
  unpatched/       (minimal)
tools/
  mod-chipped/     FAT32 formatter
  unpatched/       FAT32 formatter + TegraRCM suite
manifests/
  firmware.json    Firmware download manifest for AetherBlock
```

## Disclaimer

This setup is intended for personal use only. Please respect game developers and do not use these tools for cheating in online play or distribution of unauthorized content.
