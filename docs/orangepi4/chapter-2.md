# Control GPIO with python

## 1. Download OPi.GPIO

```bash
git clone https://github.com/baiywt/OPi.GPIO.git
```

## 2. Install

```bash
apt install python3-pip
cd OPi.GPIO
python3 setup.py install
```

## 3. Test

Create a new file:test_gpio.py

```python
import time
import sys
import OPi.GPIO as GPIO
import orangepi.pi4

BOARD = orangepi.pi4.BOARD
GPIO.setmode(BOARD)
pin=int(sys.argv[1])
GPIO.setup(pin, GPIO.OUT)
while True:
    GPIO.output(pin, GPIO.HIGH)
    time.sleep(1)
    GPIO.output(pin, GPIO.LOW)
    time.sleep(1)
```

```bash
python3 test_gpio.py 16 // Control physical pin 16 flip the level once a second
```
