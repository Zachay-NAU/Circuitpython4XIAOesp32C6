# CircuitPython for XIAO_ESP32C6

---
## Introduction
In this tutorial, we will provide a concise overview of utilizing the XIAO ESP32C6 with CircuitPython. 
It includes the basic usage of Wifi settings and pinout applications.

## Circuitpython


### Hardware

1. XIAO ESP32C6
<div class="get_one_now_container" style={{textAlign: 'center'}}>
    <a class="get_one_now_item" href="https://www.seeedstudio.com/Seeed-Studio-XIAO-ESP32C6-p-5884.html">
            <strong><span><font color={'FFFFFF'} size={"4"}> Get One Now 🖱️</font></span></strong>
    </a>
</div>

<img src="https://github.com/Zachay-NAU/Circuitpython4XIAOesp32C6/blob/main/XIAOESPC6/1.png" width="700">

### Software

1. Flash the Firmware with esptool
#### enter bootloader mode
```
Connected to computer, but no port number found for XIAO.
The computer is connected and the port number appears, but the upload program fails.
```

#### check the serial port in thr terminal
```
ls /dev/ttyACM*
```

#### install esptool

Note: You will need Python 3.7 or newer installed on your system
```
pip install esptool
```

#### erase flash
```
esptool.py --chip esp32c6 --port /dev/ttyACM0 erase_flash
```

#### download the firmware
<div class="download" style={{textAlign: 'center'}}>
    <a class="download the firmware here" href="https://github.com/Zachay-NAU/Circuitpython4XIAOesp32C6/blob/main/XIAOESPC6/seeed_xiao_esp32c6_firmware05032024.bin">
            <strong><span><font color={'FFFFFF'} size={"4"}> download the firmware here 🖱️</font></span></strong>
    </a>
</div>

Then, open the file floder in terminal.

#### flash the firmware
```
esptool.py --chip esp32c6 --port /dev/ttyACM0 write_flash -z 0x0 seeed_xiao_esp32c6_firmware05032024.bin
```

2. Set the software

#### open Thonny

#### click "stop" button

#### select interpreter

#### write code and click the green button to run

#### install liberaries

open the terminal
```
pip3 install adafruit-circuitpython-connectionmanager
```

3. Blink Test
```
"""Example for Seeed Studio XIAO ESP32C6. Blinks the built-in LED."""
import time
import board
import digitalio

led = digitalio.DigitalInOut(board.LED)
led.direction = digitalio.Direction.OUTPUT

while True:
    led.value = True
    time.sleep(0.5)
    print("LED on")
    led.value = False
    time.sleep(0.5)
    print("LED off")
```
4. Wifi COnnection
```
import time
import ipaddress
import wifi

print('Wifi Testing!')
print("joining network...")
print(wifi.radio.connect(ssid="UMASS fried chicken",password="Zacharyloveschicken"))
print("my IP addr:", wifi.radio.ipv4_address)
print("Connected!")
```

5. DIgital Output (PIR Motion Sensor)
```
import board
import time
import digitalio

PIR_PIN = board.D5

pir = digitalio.DigitalInOut(PIR_PIN)
pir.direction = digitalio.Direction.INPUT

led = digitalio.DigitalInOut(board.LED)
led.direction = digitalio.Direction.OUTPUT

while True:
    pir_value = pir.value
    if pir_value:
        led.value = True
        print('Detected!')
    else:
        led.value = False
        print('Not detected!')
    time.sleep(1)
```
6. Analog Reading (Analog Mic)
```
import time
import board
from analogio import AnalogIn

analog_in = AnalogIn(board.A0)


def get_voltage(pin):
    return (pin.value * 3.3) / 65536


while True:
    print((get_voltage(analog_in),))
    time.sleep(0.1)
```

7. IIC(Temperature Reading)
#### install sensor liberaries
```
```

8. UART(GPS)


















