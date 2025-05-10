# SysBot.NET Nintendo Switch Setup Guide

This package contains all the essential files needed to set up SysBot.NET on an unpatched Nintendo Switch for Pokémon games automation.

## Package Contents

### Files Included:
- **SysBot Base** - Core system for running bots on Nintendo Switch ([source](https://github.com/olliz0r/sys-botbase))
- **Atmosphère** - Custom firmware for Nintendo Switch ([source](https://github.com/Atmosphere-NX/Atmosphere))
- **JKSV** - Save file management tool ([source](https://github.com/J-D-K/JKSV))
- **ldn_mitm** - Required for Sword/Shield SysBot ([source](https://github.com/Lusamine/ldn_mitm/tree/for_sbnet))
- **ftpd pro** - FTP server for remote file management ([source](https://github.com/mtheall/ftpd))

## Prerequisites

- An **unpatched** Nintendo Switch (vulnerable to RCM exploit)
- A USB-C cable to connect your Switch to your PC
- A microSD card (minimum 16GB, recommended 32GB+)
- An RCM jig or alternative method to enter RCM mode

## Installation Guide

### Step 1: Format Your SD Card

1. Insert your microSD card into your computer
2. Navigate to the `tools` folder from the zip package
3. Run `fat32formatter.exe` to format your card to FAT32
   - **IMPORTANT**: This will erase all data on the card!
4. Follow the prompts to complete formatting

### Step 2: Copy Files to SD Card

1. After formatting, copy all contents from the `sd` folder in the zip directly to the root of your SD card
2. Do not change any folder structures or rename files
3. Safely eject the SD card from your computer

### Step 3: Enter RCM Mode

1. Power off your Nintendo Switch completely
2. Insert your microSD card into your Switch
3. Insert the RCM jig into the right Joy-Con rail
4. Hold VOL+ and press the POWER button simultaneously
   - The screen will remain black if done correctly

### Step 4: Inject Payload

1. Connect your Switch to your PC using the USB-C cable
2. Navigate to the `tools\TegraRCM` folder from the zip package
3. Run `TegraRcmGUI.exe` as Administrator
4. In the TegraRCM application:
   - Ensure your Switch is detected (shown in the bottom right)
   - Click on "Install Driver" if your device is not recognized
   - Navigate to the "Payload" tab
   - Select the included `fusee.bin` file
   - Click "Inject Payload"

### Step 5: Initial Atmosphère Setup

1. The Switch will boot into Atmosphère custom firmware
2. Follow any on-screen prompts to complete initial setup
3. Atmosphère will automatically load sys-botbase and other required modules

### Step 6: Connect to SysBot.NET

1. Launch your Pokémon game
2. Connect your Switch to the same network as your PC (via WiFi settings)
3. Note your Switch's IP address (found in System Settings → Internet → Connection Status)
4. Use this IP address to connect SysBot.NET from your PC

## Upgrading Existing Setup

When upgrading to a newer version of this package:

1. **IMPORTANT**: Do NOT delete the `Nintendo` folder on your SD card - it contains all your save data!
2. Copy the contents of the new `sd` folder to your SD card, overwriting existing files when prompted
3. Re-inject the payload using the updated `fusee.bin` if provided in the new package
4. Your saved data, configurations, and personal settings will remain intact

## Using JKSV (Save Manager)

JKSV lets you backup and restore game save files.

### Backing Up Saves:

1. Launch JKSV from the Homebrew Menu
2. Select the game you want to backup from the list
3. Press the + button or select "Backup" option
4. Enter a name for your backup (or use the default)
5. Wait for the backup to complete

### Restoring Saves:

1. Launch JKSV from the Homebrew Menu
2. Select the game you want to restore
3. Press Y to view your save backups
4. Select the backup you want to restore
5. Choose "Restore" and confirm
6. Restart your game to use the restored save

## Using FTPD Pro (File Transfer)

FTPD allows wireless file transfer between your PC and Switch.

### On Your Switch:

1. Launch FTPD Pro from the Homebrew Menu
2. The screen will display your Switch's IP address and port (usually 5000)
3. Leave FTPD Pro running during the entire transfer process

### On Your PC:

1. Download and install an FTP client like FileZilla
2. Open your FTP client and enter the connection details:
   - Host: Your Switch's IP address (shown on the FTPD screen)
   - Port: 5000 (or whatever is shown on the FTPD screen)
   - Username: (leave blank or try "anonymous")
   - Password: (leave blank)
3. Click "Connect" or "Quick Connect"
4. Once connected, you'll see your Switch's file system
5. You can now drag and drop files between your PC and Switch
6. When finished, disconnect from your FTP client before closing FTPD

Tips:
- Use FTP to add/update games and homebrew applications
- Navigate to `/atmosphere/contents/` to modify game mods
- You can transfer screenshots from `/Nintendo/Album/`

## Troubleshooting

- **Switch won't enter RCM**: Ensure your Switch is unpatched and the RCM jig is properly inserted
- **Payload injection fails**: Try reinstalling drivers or using a different USB cable
- **SysBot won't connect**: Verify your IP address and ensure your game is running
- **Black screen after injection**: Ensure you're using the correct fusee.bin file for your setup

## Additional Resources

- [SysBot.NET Wiki](https://github.com/kwsch/SysBot.NET/wiki)
- [Atmosphère Documentation](https://github.com/Atmosphere-NX/Atmosphere/wiki)

## Disclaimer

This setup is intended for personal use only. Please respect game developers and do not use these tools for cheating in online play or distribution of unauthorized content.
