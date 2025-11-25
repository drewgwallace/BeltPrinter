# Benefits of Using DFU on the SKR Mini E3 V3

Using DFU mode with the **SKR Mini E3 V3** allows reliable and convenient firmware flashing without requiring an ST-Link or USB mass-storage interface.  

By installing the **Katapult bootloader**, you can simply **double-click the RESET button** to enter bootloader mode and flash firmware over a serial connection.

---
## Flashing Firmware Over Serial
For detailed instructions on putting the SKR Mini E3 V3 into DFU mode and overwriting the bootloader with Katapult, see the following repository:

- [3dApothecary-xyz / SKR_Mini_E3_V3_DFU](https://github.com/3dApothecary-xyz/SKR_Mini_E3_V3_DFU)

---
## Flashing Firmware Over Serial

Once Katapult is installed, and after entering bootloader mode, flash (or update) Klipper firmware using:

```bash
python3 ~/katapult/scripts/flashtool.py \
    -f ~/klipper/out/klipper.bin \
    -d /dev/serial0
