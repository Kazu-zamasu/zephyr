.. _disco_l475_iot1_board:

ST Disco L475 IOT01
###################

Overview
********

The B-L475E-IOT01A Discovery kit for IoT node allows users to develop
applications with direct connection to cloud servers.
The Discovery kit enables a wide diversity of applications by exploiting
low-power communication, multiway sensing and ARM |reg| Cortex |reg|-M4 core-based
STM32L4 Series features.

This kit provides:

- 64-Mbit Quad-SPI (Macronix) Flash memory
- Bluetooth |reg| V4.1 module (SPBTLE-RF)
- Sub-GHz (868 or 915 MHz) low-power-programmable RF module (SPSGRF-868 or SPSGRF-915)
- Wi-Fi |reg| module Inventek ISM43362-M3G-L44 (802.11 b/g/n compliant)
- Dynamic NFC tag based on M24SR with its printed NFC antenna
- 2 digital omni-directional microphones (MP34DT01)
- Capacitive digital sensor for relative humidity and temperature (HTS221)
- High-performance 3-axis magnetometer (LIS3MDL)
- 3D accelerometer and 3D gyroscope (LSM6DSL)
- 260-1260 hPa absolute digital output barometer (LPS22HB)
- Time-of-Flight and gesture-detection sensor (VL53L0X)
- 2 push-buttons (user and reset)
- USB OTG FS with Micro-AB connector
- Expansion connectors:
        - Arduino |trade| Uno V3
        - PMOD
- Flexible power-supply options:
        - ST LINK USB VBUS or external sources
- On-board ST-LINK/V2-1 debugger/programmer with USB re-enumeration capability:
        - mass storage, virtual COM port and debug port


.. image:: img/disco_l475_iot1.jpg
     :width: 531px
     :align: center
     :height: 354px
     :alt: Disco L475 IoT1

More information about the board can be found at the `Disco L475 IoT1 website`_.

Hardware
********

The STM32L475RG SoC provides the following hardware IPs:

- Ultra-low-power with FlexPowerControl (down to 130 nA Standby mode and 100 uA/MHz run mode)
- Core: ARM |reg| 32-bit Cortex |reg|-M4 CPU with FPU, frequency up to 80 MHz, 100DMIPS/1.25DMIPS/MHz (Dhrystone 2.1)
- Clock Sources:
        - 4 to 48 MHz crystal oscillator
        - 32 kHz crystal oscillator for RTC (LSE)
        - Internal 16 MHz factory-trimmed RC (±1%)
        - Internal low-power 32 kHz RC (±5%)
        - Internal multispeed 100 kHz to 48 MHz oscillator, auto-trimmed by
          LSE (better than ±0.25 % accuracy)
        - 3 PLLs for system clock, USB, audio, ADC
- RTC with HW calendar, alarms and calibration
- Up to 24 capacitive sensing channels: support touchkey, linear and rotary touch sensors
- 16x timers:
        - 2x 16-bit advanced motor-control
        - 2x 32-bit and 5x 16-bit general purpose
        - 2x 16-bit basic
        - 2x low-power 16-bit timers (available in Stop mode)
        - 2x watchdogs
        - SysTick timer
- Up to 114 fast I/Os, most 5 V-tolerant, up to 14 I/Os with independent supply down to 1.08 V
- Memories
        - Up to 1 MB Flash, 2 banks read-while-write, proprietary code readout protection
        - Up to 128 KB of SRAM including 32 KB with hardware parity check
        - External memory interface for static memories supporting SRAM, PSRAM, NOR and NAND memories
        - Quad SPI memory interface
- 4x digital filters for sigma delta modulator
- Rich analog peripherals (independent supply)
        - 3x 12-bit ADC 5 MSPS, up to 16-bit with hardware oversampling, 200 uA/MSPS
        - 2x 12-bit DAC, low-power sample and hold
        - 2x operational amplifiers with built-in PGA
        - 2x ultra-low-power comparators
- 18x communication interfaces
        - USB OTG 2.0 full-speed, LPM and BCD
        - 2x SAIs (serial audio interface)
        - 3x I2C FM+(1 Mbit/s), SMBus/PMBus
        - 6x USARTs (ISO 7816, LIN, IrDA, modem)
        - 3x SPIs (4x SPIs with the Quad SPI)
        - CAN (2.0B Active) and SDMMC interface
        - SWPMI single wire protocol master I/F
- 14-channel DMA controller
- True random number generator
- CRC calculation unit, 96-bit unique ID
- Development support: serial wire debug (SWD), JTAG, Embedded Trace Macrocell |trade|


More information about STM32L476RG can be found here:
       - `STM32L475RG on www.st.com`_
       - `STM32L475 reference manual`_

Supported Features
==================

The Zephyr Disco L475 IoT board configuration supports the following hardware features:

+-----------+------------+-------------------------------------+
| Interface | Controller | Driver/Component                    |
+===========+============+=====================================+
| NVIC      | on-chip    | nested vector interrupt controller  |
+-----------+------------+-------------------------------------+
| UART      | on-chip    | serial port-polling;                |
|           |            | serial port-interrupt               |
+-----------+------------+-------------------------------------+
| PINMUX    | on-chip    | pinmux                              |
+-----------+------------+-------------------------------------+
| GPIO      | on-chip    | gpio                                |
+-----------+------------+-------------------------------------+
| I2C       | on-chip    | i2c                                 |
+-----------+------------+-------------------------------------+
| PWM       | on-chip    | pwm                                 |
+-----------+------------+-------------------------------------+

Other hardware features are not yet supported on this Zephyr port.

The default configuration can be found in the defconfig file:

	``boards/arm/disco_l475_iot1/disco_l475_iot1_defconfig``


Connections and IOs
===================

Disco L475 IoT Board has 8 GPIO controllers. These controllers are responsible for pin muxing,
input/output, pull-up, etc.

Available pins:
---------------

For detailed information about available pins please refer to `STM32 Disco L475 IoT1 board User Manual`_.

Default Zephyr Peripheral Mapping:
----------------------------------

- UART_1_TX : PB6
- UART_1_RX : PB7
- UART_2_TX : PA2
- UART_2_RX : PA3
- I2C_1_SCL : PB8
- I2C_1_SDA : PB9
- I2C_2_SCL : PB10
- I2C_2_SDA : PB11
- SPI_1_SCK : PA5
- SPI_1_MISO : PA6
- SPI_1_MOSI : PA7
- PWM_2_CH1 : PA15
- USER_PB : PC13
- LD2 : PA5

System Clock
------------

Disco L475 IoT System Clock could be driven by internal or external oscillator,
as well as main PLL clock. By default System clock is driven by PLL clock at 80MHz,
driven by 16MHz high speed internal oscillator.

Serial Port
-----------

Disco L475 IoT board has 6 U(S)ARTs. The Zephyr console output is assigned to UART1.
Default settings are 115200 8N1.


Programming and Debugging
*************************

Flashing
========

Disco L475 IoT board includes an ST-LINK/V2-1 embedded debug tool interface.
This interface is not supported by the openocd version 0.9 included by the Zephyr SDK v0.9.
Until we update the Zephyr SDK, use openocd v0.10.0 from the openocd-stm32 project on GitHub
to get the minimum set of scripts needed to flash and debug STM32 development boards.

.. code-block:: console

   $ git clone  https://github.com/erwango/openocd-stm32.git

Then follow instructions in README.md


Flashing an application to Disco L475 IoT
-----------------------------------------

The sample application :ref:`hello_world` is being used in this tutorial:

To build the Zephyr kernel and application, enter:

.. code-block:: console

   $ cd <zephyr_root_path>
   $ source zephyr-env.sh
   $ cd $ZEPHYR_BASE/samples/hello_world/
   $ make BOARD=disco_l475_iot1

Connect the Disco L475 IoT to your host computer using the USB port.
Then, enter the following command:

.. code-block:: console

   $ cd <openocd-stm32_path>
   $ stm32_flsh l4 $ZEPHYR_BASE/samples/hello_world/outdir/disco_l475_iot1/zephyr.bin

Run a serial host program to connect with your Nucleo board.

.. code-block:: console

   $ minicom -D /dev/ttyACM0

You should see the following message:

.. code-block:: console

   $ Hello World! arm


Debugging
=========

Access gdb with the following make command:

.. code-block:: console

   $ cd <openocd-stm32_path>
   $ stm32_dbg l4 $ZEPHYR_BASE/samples/hello_world/outdir/disco_l475_iot1/zephyr.elf

.. _Disco L475 IoT1 website:
   http://www.st.com/content/st_com/en/products/evaluation-tools/product-evaluation-tools/mcu-eval-tools/stm32-mcu-eval-tools/stm32-mcu-discovery-kits/b-l475e-iot01a.html

.. _STM32 Disco L475 IoT1 board User Manual:
   http://www.st.com/resource/en/user_manual/dm00347848.pdf

.. _STM32L475RG on www.st.com:
   http://www.st.com/en/microcontrollers/stm32l475rg.html

.. _STM32L475 reference manual:
   http://www.st.com/resource/en/reference_manual/DM00031020.pdf
