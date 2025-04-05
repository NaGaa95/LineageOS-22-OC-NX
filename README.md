# LineageOS 22.2 OC for Mariko ONLY (nx_tab)

DISCLAIMER: USE AT YOUR OWN RISK!

This Kernel is very dangerous and can possibly damage your console. Therefore I do not recommend using it. If you decide to use it, USE AT YOUR OWN RISK. THE SOFTWARE IS PROVIDED “AS IS”, WITHOUT WARRANTY OF ANY KIND.

Overclocking in general will shorten the lifespan of some hardware components. YOU ARE RESPONSIBLE for any problem or potential damage by using unsafe frequencies.

# Features 

* Based on latest Lineage OS 22.2
* CPU Overclock up to 2601 MHz
  * EOS CPU UV 4
  * High-Frequency vMin reduced to 800mV
  * Limited to 2499 MHz on lower CPU Speedo
* CPU LUT Table increased to 63
  * Allow finer voltage steps
* GPU Overclock up to 1267 MHz
  * GPU Volt Offset -10 / -20 for High Freq
* Increased Power Profile limits
  * CPU Frequency limited to 2397 Mhz in Handheld
  * GPU Frequency increased to 1075 Mhz in Handheld
  * Max CPU/GPU Clocks for Docked
* Increased CPU/GPU vMin & SoC Voltage
  * May help achieve higher RAM Frequencies for Hynix NEE / Micron WTB users (3000+ MHz) 
* Vdd2 Overvoltage up to 1212mV
* Fix for Nyxi Hyperion Series Joy-con
  * May also apply to other 3rd party Joycon with poor handshake implementation

## How to Install : 
1. Download latest [release](https://github.com/NaGaa95/LineageOS-22-OC-NX/releases).
2. Copy LineageOS .zip file on your SD Card and replace `boot.scr` in `/switchroot/android/` on your SD Card
3. Boot into recovery and flash the Lineage OS zip file (No need to wipe if you are already on Lineage OS 22)
4. set `dvfsb=1` / `gpu_dvfsc=1` / `oc=1` in your Android boot config `(Bootloader/ini/Android.ini)`
5. Enable Performance Mode in Switch Configuration app
<br /> /!\ UV Kernel only is recommended for low speedo (-1600) and Switch Lite /!\

### 1212mV vdd2 Overvoltage
* Use the modded Hekate-OC provided

## Useful Commands
Use ADB or app like DevInfoOverlay (Need ROOT)

CPU Voltage :
- `cat /sys/kernel/debug/tegra_dfll_fcpu/output_mv`

CPU Frequency :
- `cat /sys/kernel/debug/tegra_dfll_fcpu/rate`

GPU Voltage :
- `cat /sys/kernel/debug/57000000.gpu/voltage`

GPU Frequency (Min/Max/Current): 
- `cat /sys/devices/57000000.gpu/devfreq/57000000.gpu/min_freq`
- `cat /sys/devices/57000000.gpu/devfreq/57000000.gpu/max_freq`
- `/sys/devices/57000000.gpu/devfreq/57000000.gpu/cur_freq`

Override GPU Frequency (Min/Max)
- `echo <gpu_freq> > /sys/devices/57000000.gpu/devfreq/57000000.gpu/min_freq`
- `echo <gpu_freq> > /sys/devices/57000000.gpu/devfreq/57000000.gpu/max_freq`
<br /> Where `<gpu_freq>` is a value available in :
<br /> `cat /sys/devices/57000000.gpu/devfreq/57000000.gpu/available_frequencies`
  
RAM Vdd2 & Vddq Voltages :
- `cat /sys/kernel/debug/regulator/vdd-ddr/regulator/microvolts`
- `cat /sys/kernel/debug/regulator/vddio-ddr/regulator/microvolts`

RAM Frequency :
- `cat /sys/kernel/debug/tegra_bwmgr/emc_rate`

- ## Acknowledgement 
- CTCaer
- Meha
