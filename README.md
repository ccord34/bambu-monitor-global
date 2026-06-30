# Bambu Monitor DualEye - Global Firmware Flasher

This repository hosts the English web flasher and binary firmware package for
**Bambu Monitor DualEye** on the Waveshare **ESP32-S3-DualEye-LCD-1.28** board.

It is intended for overseas users who want to install the `20260630-global-login`
firmware build, which adds the global Bambu Cloud email/password login path while
keeping the existing token and verification-code flows.

## Online flashing

Open the GitHub Pages site for this repository in desktop Chrome or Edge, connect
the ESP32-S3 board by USB, then click **Install Firmware**.

The web flasher writes the same segmented layout used by the locally verified
PlatformIO build:

```text
0x0000  firmware/bootloader.bin
0x8000  firmware/partitions.bin
0xe000  firmware/boot_app0.bin
0x10000 firmware/firmware.bin
```

## Offline flashing

If you prefer not to use Web Serial, download:

[BambuMonitor-ESP32S3-DualEye-20260630-global-login.zip](downloads/BambuMonitor-ESP32S3-DualEye-20260630-global-login.zip)

After extracting the package, flash from a terminal with:

```powershell
python -m esptool --chip esp32s3 --port COM13 --baud 460800 write_flash -z `
  0x0000 bootloader.bin `
  0x8000 partitions.bin `
  0xe000 boot_app0.bin `
  0x10000 firmware.bin
```

Replace `COM13` with your board's serial port.

## First run

After flashing:

1. Power on the device.
2. If Wi-Fi is not configured, connect to the device AP.
3. Open `http://192.168.4.1/` and configure Wi-Fi.
4. Reconnect to your home Wi-Fi.
5. Open the local configuration page shown on the screen.

## License

The web flasher and firmware binaries in this repository are provided for
personal, evaluation, repair, and non-commercial deployment only.

Commercial use is not permitted. See [LICENSE](LICENSE).
