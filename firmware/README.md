# Firmware

## Benefits of Using DFU on the SKR Mini E3 V3

Using DFU mode with the **SKR Mini E3 V3** allows reliable and convenient firmware flashing without requiring an ST-Link or USB mass-storage interface.  

By installing the **Katapult bootloader**, you can simply **double-click the RESET button** to enter bootloader mode and flash firmware over a serial connection.

### Placing the SKR Mini E3 V3 into DFU Mode

For detailed instructions on putting the SKR Mini E3 V3 into DFU mode and overwriting the bootloader with Katapult, see the following repository:

- [3dApothecary-xyz / SKR_Mini_E3_V3_DFU](https://github.com/3dApothecary-xyz/SKR_Mini_E3_V3_DFU)

### Install Katapult

- [Install Katapult](https://github.com/Arksine/katapult)

```
Katapult Configuration v0.0.1-109-g902f335
    Micro-controller Architecture (STMicroelectronics STM32)  --->
    Processor model (STM32G0B1)  --->
    Build Katapult deployment application (8KiB bootloader)  --->
    Clock Reference (8 MHz crystal)  --->
    Communication interface (Serial (on USART2 PA3/PA2))  --->
    Application start offset (8KiB offset)  --->
(250000) Baud rate for serial port
()  GPIO pins to set on bootloader entry
[*] Support bootloader entry on rapid double click of reset button
[ ] Enable bootloader entry on button (or gpio) state
[ ] Enable Status LED
```
```sudo dfu-util -R -a 0 -s 0x08000000:mass-erase:force:leave -D ~/katapult/out/katapult.bin -d 0483:df11```

### Install Klipper

- [Install Klipper](https://www.klipper3d.org/Installation.html)

```
Klipper Firmware Configuration
[*] Enable extra low-level configuration options
    Micro-controller Architecture (STMicroelectronics STM32)  --->
    Processor model (STM32G0B1)  --->
    Bootloader offset (8KiB bootloader)  --->
    Clock Reference (8 MHz crystal)  --->
    Communication interface (Serial (on USART2 PA3/PA2))  --->
(250000) Baud rate for serial port
[*] Optimize stepper code for 'step on both edges'
()  GPIO pins to set at micro-controller startup
```

### Flashing Firmware Over Serial

Once Katapult is installed, and after entering bootloader mode, flash (or update) Klipper firmware using:

```bash
python3 ~/katapult/scripts/flashtool.py \
    -f ~/klipper/out/klipper.bin \
    -d /dev/serial0
```
