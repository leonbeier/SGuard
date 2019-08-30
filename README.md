# SGuard
This is an example project designed with the VHDPlus IDE. With your fingerprint you can secure an object and if somebody tries to steal it, you get a notification and the SGuard drives around the room to escape the thief.

It uses an FPGA, HX711, load cell, fingerprint reader, buzzer, RGB led, ESP8266, ultrasonic sensors and motors with encoders. 

## Software
- Download the VHDPlus IDE from VHDPlus.com and follow the instructions from Get Started.
- Clone this Project and open the SGuard.vhdpproj file with the IDE. 
- Press the run button, select your FPGA, connect the signals with the I/Os you want to connect your hardware with and click on Compile
- Press the program button and load the created programming file on your FPGA

## Hardware
### Pressure
To check if somebody tries to steal the secured object, I use a HX711 ADC together with a 5kg loadcell. With this you can see minimal changes in the pressure so it should even be impossible to replace the object with one of similar weight.
SCK_O has to be connected to SCK of the HX711 and DOUT_I with DT. The HX711 works with 3.3V, so no level shifter needed.

### Fingerprint
To secure and unlock the SGuard I used an AS608 fingerprint sensor, but I first used the FPGA as arduino (with NIOSDuino) to save my fingerprint on it. See https://github.com/adafruit/Adafruit-Fingerprint-Sensor-Library/blob/master/examples/enroll/enroll.ino.
If you want to use a normal arduino,  keep in mind that the fingerprint sensor runs with 3.3V and you need a level shifter to convert the 5V signals.
Finger_RX has to be connected to TX of the sensor and Finger_TX with RX.

### Buzzer and LED
If somebody tries to steal the object an alarm starts with the buzzer and LED. I used an active buzzer and an RGB LED with 220ohm resistors. Connect LED_R/G/B with the led and Buzzer with the buzzer.

### Notification
