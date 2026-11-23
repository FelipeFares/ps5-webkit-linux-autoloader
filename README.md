<p align="center">
  <img src="./assets/icon.svg" width="128" />
</p>
<h1 align="center">PS5 WebKit Linux Loader</h1>
&nbsp;
<p align="center">Dedicated PS5 WebKit launcher for Linux (Bazzite Bootc Loader).<br>Installs as an independent homescreen application (Title ID: <b>WKLX00001</b>) without overwriting the original WebKit Autoloader.<br>Supports firmwares <b>3.00&ndash;13.60</b>.</p>

---

## Features

- **Coexists with WebKit Autoloader**: Uses Title ID `WKLX00001` and port `18182` so both apps can be installed side-by-side on your PS5 home screen.
- **Cold Boot & Warm Boot**: Works on an unjailbroken console (runs kernel exploit first) OR on an already-jailbroken console (skips kernel exploit and directly launches Linux).
- **Dedicated Config (`autoload-linux`)**: Uses `autoload-linux` (or `autoload-linux.txt`), completely ignoring `autoload.txt` so there are zero conflicts with other loaders.
- **Out-of-the-Box Bazzite Fallback**: If no `autoload-linux` config file is present, it automatically launches:
  `/data/pldmgr/payloads/local/bazzite-bootc-loader/bazzite-bootc-loader-v3.0.1.elf`

---

## Setup Instructions

### If already jailbroken:
1. Download `webkit-linux-loader-installer_vX.Y.Z.elf` from Releases.
2. Send it to your PS5 with `elfldr` (port 9021) or launch it from Payload Manager.
3. The installer caches the offline page, creates the **WebKit Linux Loader** homescreen app, and exits.
4. **Reboot once** (or refresh homescreen), then launch **WebKit Linux Loader** whenever you want to boot Linux.

### If not jailbroken yet:
1. Run `webkit-linux-loader-host_vX.Y.Z.exe` on your PC.
2. Set your PS5 DNS to your PC IP.
3. Open User's Guide to install to homescreen.

---

## Configuration (`autoload-linux`)

If you want to customize what is loaded, create an `autoload-linux` file (or `autoload-linux.txt`) in:
- Root of a USB drive: `/mnt/usb0/autoload-linux` (or `/mnt/usb0/autoload-linux.txt` or `/mnt/usb0/autoload-linux/autoload-linux.txt`)
- Internal storage: `/data/autoload-linux` (or `/data/autoload-linux.txt` or `/data/autoload-linux/autoload-linux.txt`)

Example content:
```text
# Boot Bazzite Linux
/data/pldmgr/payloads/local/bazzite-bootc-loader/bazzite-bootc-loader-v3.0.1.elf
```

If neither file is found, it automatically boots the default path above!
