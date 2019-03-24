# Magnetic Triangular LED Lights Home assistant controller
(Initial project : https://github.com/bruhautomation/ESP-MQTT-JSON-Digital-LEDs )

This project control my DIY 3d printed nanoleaf [thingiverse](https://www.thingiverse.com/thing:3372353) with Home assistant

#### Supported Features Include
- RGB Color Selection
- Brightness 
- Flash
- Fade
- Transitions
- Effects with Animation Speed
- Over-the-Air (OTA) Upload from the ArduinoIDE!

Some of the effects incorporate the currrently selected color (sinelon, confetti, juggle, etc) while other effects use pre-defined colors. You can also select custom transition speeds between colors. The transition variable in Home Assistant (HA) also functions to control the animation speed of the currently running animation. The input_slider and automation in the HA configuration example allow you to easily set a transition speed from HA's user interface without needing to use the Services tool. 

The default speed for the effects is hard coded and is set when the light is first turned on. When changing between effects, the previously used transition speed will take over. If the effects don't look great, play around with the slider to adjust the transition speed (AKA the effect's animation speed). 

#### OTA Uploading
This code also supports remote uploading to the ESP8266 using Arduino's OTA library. To utilize this, you'll need to first upload the sketch using the traditional USB method. However, if you need to update your code after that, your WIFI-connected ESP chip should show up as an option under Tools -> Port -> Porch at your.ip.address.xxx. More information on OTA uploading can be found [here](http://esp8266.github.io/Arduino/versions/2.0.0/doc/ota_updates/ota_updates.html). Note: You cannot access the serial monitor over WIFI at this point.  

#### Parts List
- [Digital RGB Leds](http://geni.us/8mBml)
- [NodeMCU](http://geni.us/4pVoT)
- [Aluminum Mounting Channel/Diffuser](http://geni.us/JBDhv7)
- [12v to 5v Step Down](http://geni.us/PghhV9)
- [12V 15amp Power Supply](http://geni.us/8rKC)
- [Strip Connector](http://geni.us/OL7tHv)
- [Logic Level Shifter](http://geni.us/4hJAyy)
- [20 Gauge Wire](http://geni.us/2MBYAXF)
- [Cable Chase](http://geni.us/lFqD)
- [Project Box](http://geni.us/kZRgaj)
- [Header Wires](http://geni.us/GniKAX)
- [Power Jacks](http://geni.us/7Ywdut)


#### Wiring Diagram
![alt text](https://github.com/bruhautomation/ESP-MQTT-Digital-LEDs/blob/master/ESP%20MQTT%20Digital%20LEDs%20Wiring%20Diagram.png?raw=true "Wiring Diagram")


#### Home Assistant Service Examples
Besides using the card in Home Assistant's user interface, you can also use the Services tool to control the light using the light.turn_on and light.turn_off services. This will let you play with the parameters you can call later in automations or scripts. 

Fade the Light On Over 5 Seconds - light.turn_on
```
{"entity_id":"light.porch_strip",
"brightness":150,
"color_name":"blue",
"transition":"5"
}
```

Flash The Light - light.turn_on
```
{"entity_id":"light.porch_strip",
"color_name":"green",
"brightness":255,
"flash":"short"
}
```

Call Rainbow Effect with Slow Animation Speed - light.turn_on
```
{"entity_id":"light.porch_strip",
"transition":"50",
"brightness":255,
"effect":"rainbow"
}
```

Fade the Light Off Over 5 Seconds - light.turn_off
```
{"entity_id":"light.porch_strip",
"transition":"50"
}
```
