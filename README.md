# How-to-program-an-ESP03
How a quick guide to start booting/flashing/programming your ESP-03 or ESP8265 boards

<img src="https://content.instructables.com/FOS/AZGY/LDX41CHP/FOSAZGYLDX41CHP.jpg?auto=webp&width=800&height=450&fit=bounds&md=561c8c864ec27d790a1beaa67e884af3"></img>

This tutorial is for the younger me from 3 years back who bought an ESP-03 but never managed to make it work. The internet still does not seem to have enough good resources around it, so why not?

# Components - 
Alongside the ESP-03 module, we only need 1 additional board. That is -

1. USB to TTL/Serial converter. (or any board with 3.3V, GND, Rx and Tx)
2. ESP-03


# ESP03 Pinout

<img src ="https://content.instructables.com/FZZ/QQ3H/LDX41CRE/FZZQQ3HLDX41CRE.jpg?auto=webp&width=1600&height=900&fit=bounds&md=3c1c0a0cd5dbed4d371f163304bc1143"></img>


# Wiring

First of all, this is an ESP8285 and not 8266.

Second, before jumping into wiring, it is important that we understand the boot mode properly.

Third, there are three boot mode select pins along with the Chip_PD/enable pin which needs to be in a very specific voltage state for the chip to enter Boot Mode.

The best resource for that can be found in the Boot Mode Selection section of the official documentation: https://docs.espressif.com/projects/esptool/en/latest/esp8266/advanced-topics/boot-mode-selection.html


Full details can be found in the link above, but let me summarize everything.

<img src="https://content.instructables.com/F5G/I5VV/LDX41BXL/F5GI5VVLDX41BXL.png?auto=webp&frame=1&fit=bounds&md=085dbe398b63cd2887e8a1896c9f4d51"></img>



# Boot Mode:

ESP-03 <--------------> USB_to_TTL (or any other device that has VCC, GND, RX and TX pins)

GPIO0 -----------------> GND

GPIO2 -----------------> 3.3V

GPIO15 ---------------> GND

Chip_PD/Enable ----> 3.3V (same for normal operation)

RX ----------------------> TX

TX -----------------------> RX

GND --------------------> GND



# Arduino IDE Setup 
I am assuming that you already have the ESP8266 boards installed to your Arduino IDE.

So, simply go to boards options and select ESP8285 -

<img src="https://content.instructables.com/FTL/8CRS/LDX41C4O/FTL8CRSLDX41C4O.png?auto=webp&width=800&height=450&fit=bounds&md=48608ac0bf4bf1677957f631dec5e80e"></img>

Now, simply click write some simple code and click upload - 

```
int LED = 12;

void setup() {
  pinMode(LED, OUTPUT);
}

void loop() {
  digitalWrite(LED, HIGH); 
  delay(1000);                
  digitalWrite(LED, LOW);  
  delay(1000); 
}
```



If you did everything right, upon clicking upload, it will immediately start uploading without any delays - 

<img src="https://content.instructables.com/FXQ/XRWU/LDX41CD6/FXQXRWULDX41CD6.png?auto=webp&width=400&height=275&fit=bounds&md=9a174b1b7d74988a70cc4f2f847cd2d0"></img>



# YOU MUST CHANGE THE CIRCIT FOR NORMAL MODE TO TEST YOUR PROGRAM

Make sure you have wired it for **Normal Mode** as mentioned on above to make your flashed code work.
