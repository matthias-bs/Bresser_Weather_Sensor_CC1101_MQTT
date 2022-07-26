> :warning: This repository is deprecated and no longer maintained. 
> The recommended alternative is [BresserWeatherSensorReceiver](https://github.com/matthias-bs/BresserWeatherSensorReceiver)
> which provides a much cleaner design and allows to use an SX1276 or RFM95W radio receiver as an alternative to the CC1101.
> Please refer to the [BresserWeatherSensorMQTT](https://github.com/matthias-bs/BresserWeatherSensorReceiver/tree/main/examples/BresserWeatherSensorMQTT) example.

# Bresser_Weather_Sensor_CC1101_MQTT

**Bresser 5-in-1/6-in-1 868 MHz Weather Sensor Radio Receiver based on CC1101 and ESP32/ESP8266 - provides data via secure MQTT**

Based on:
- [Bresser5in1-CC1101](https://github.com/seaniefs/Bresser5in1-CC1101) by [Sean Siford](https://github.com/seaniefs)
- [RadioLib](https://github.com/jgromes/RadioLib) by [Jan Gromeš](https://github.com/jgromes)
- [arduino-mqtt](https://github.com/256dpi/arduino-mqtt) by [Joël Gähwiler (256dpi)](https://github.com/256dpi)
- [ArduinoJson](https://arduinojson.org) by [Benoit Blanchon](https://github.com/bblanchon) 

## Weather Stations

* [BRESSER Weather Center 5-in-1](https://www.bresser.de/en/Weather-Time/Weather-Center/BRESSER-Weather-Center-5-in-1-black.html)
* [BRESSER Professional WIFI colour Weather Center 5-in-1 V](https://www.bresser.de/en/Weather-Time/WLAN-Weather-Stations-Centers/BRESSER-Professional-WIFI-colour-Weather-Center-5-in-1-V.html)

The Bresser 5-in-1 Weather Stations seem to use two different protocols. Select the appropriate decoder by (un-)commenting `#define BRESSER_6_IN_1` in the source code.

| Model         | Decoder Function                |
| ------------- | ------------------------------- |
| 7002510..12   | decodeBresser**5In1**Payload()  |
| 7002585       | decodeBresser**6In1**Payload()  |

## MQTT Topics

MQTT publications:

`<base_topic>/data`    sensor data as JSON string - see `publishWeatherdata()`
     
`<base_topic>/radio`   CC1101 radio transceiver info as JSON string - see `publishRadio()`
     
`<base_topic>/status`  "online"|"offline"|"dead"$

$ via LWT

`<base_topic>` is set by `#define HOSTNAME ...`

`<base_topic>/data` JSON Example:
```
{"sensor_id":12345678,"ch":0,"battery_ok":true,"humidity":44,"wind_gust":1.2,"wind_avg":1.2,"wind_dir":150,"rain":146}
```

## Hardware 

(ESP8266 D1-Mini)
![Bresser5in1_CC1101_D1-Mini](https://user-images.githubusercontent.com/83612361/158458191-b5cabad3-3515-45d0-98e3-94b0fa13b8ef.jpg)

### CC1101

[Texas Instruments CC1101 Product Page](https://www.ti.com/product/CC1101)

**Note: CC1101 Module Connector Pitch is 2.0mm!!!**

Unlike most modules/breakout boards, most (if not all) CC1101 modules sold on common e-commerce platforms have a pitch (distance between pins) of 2.0mm. To connect it to breadboards or jumper wires with 2.54mm/100mil pitch (standard), the following options exist:

* solder wires directly to the module
* use a 2.0mm pin header and make/buy jumper wires with 2.54mm at one end and 2.0mm at the other (e.g. [Adafruit Female-Female 2.54 to 2.0mm Jumper Wires](https://www.adafruit.com/product/1919))
* use a [2.0mm to 2.54 adapter PCB](https://www.amazon.de/Lazmin-1-27MM-2-54MM-Adapter-Platten-Brett-drahtlose-default/dp/B07V873N52)

**Note 2: Make sure to use the 868MHz version!**

## Dashboard with [IoT MQTT Panel](https://snrlab.in/iot/iot-mqtt-panel-user-guide) (Example)
![IoTMQTTPanel_Bresser_5-in-1](https://user-images.githubusercontent.com/83612361/158457786-516467f9-2eec-4726-a9bd-36e9dc9eec5c.png)

