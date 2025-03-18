# ORCA_AFOIL
Autonomous electric hydrofoil for marine mapping.

## Hardware
* mRo Pixracer - https://docs.px4.io/main/en/flight_controller/pixracer.html
  * CPU: 180 MHz ARM Cortex
  * Invensense® ICM-20608 Accel / Gyro (4 KHz) / MPU9250 Accel / Gyro / Mag (4 KHz)
  * HMC5983 magnetometer with temperature compensation
  * Measurement Specialties MS5611 barometer
  * ESP8266 Wifi
* Matek AP_Periph CAN Magnetometer RM3100
  * Board Size: 36mm*25mm*10mm.
  * 6g
  * Interface:
    * CAN, DroneCAN Protocol
    * UART2, MSP output (MatekL431-Periph fw)
    * UART3, for external GNSS module
    * ST debug, SWCLK & SWDIO
  * LED
    * Blue, Fast blinking,  Booting
    * Blue, Slow blinking, working
    * Red, 3.3V indicator
* SD25MG  180 degree stainless stell high torque steros
  * Operation Voltage Range: 4.8V -7.4V
  * Operation Travel: 60°±1
  * Limit angle : 180°± 1
  * Direction: Re-clock wise/ Pulse Travel 500→2500 μsec
  * Waterproof performance: IP67
  * Dimensions:40x20x40.50mm
  * Weight:80g (without servo horn)
  * SD25MG：
    * Test Voltage: 6V / 7.4V / 8.4V
    * Idle current(at stopped): 270mA@6V / 320mA@7.4V / 360mA@8.4V
    * Operating speed (at no load):0.13 sec/60°@6V; 0.1sec/60°@7.4V; 0.08sec/60°@8.4V
    * Stall torque (at locked): 18kg-cm@6V; 23kg-cm@7.4V; 25kg-cm@8.4V
    * Running Current: 2.2A@6V; 2.8A@7.4V; 3.2A@8.4V

## Software

### QGroundControl Setup

1. On the command prompt enter:

```sh
sudo usermod -a -G dialout $USER
sudo apt-get remove modemmanager -y
sudo apt install gstreamer1.0-plugins-bad gstreamer1.0-libav gstreamer1.0-gl -y
sudo apt install libfuse2 -y
sudo apt install libxcb-xinerama0 libxkbcommon-x11-0 libxcb-cursor-dev -y
```


### PXR setup for the Pixracer

```sh
mkdir px4_source
cd px4_source
git clone git@github.com:PX4/PX4-Autopilot.git
cd PX4-Autopilot
./Tools/setup/ubuntu.sh
make make px4_fmu-v4_default boardconfig
```

This will bring up the board config for PX4. Navigate to the RC drivers: 

drivers -> RC

Enable crossfire by toggling crsf_rc (e.g. [*] crst_rc) and then save.






  
