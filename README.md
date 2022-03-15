# Bresser_Weather_Sensor_CC1101_MQTT

**Bresser 5-in-1/6-in-1 868 MHz Weather Sensor Receiver based on CC1101 providing data via secure MQTT for ESP32/ESP8266**

Based on:
- [Bresser5in1-CC1101](https://github.com/seaniefs/Bresser5in1-CC1101) by [Sean Siford](https://github.com/seaniefs)
- [RadioLib](https://github.com/jgromes/RadioLib) by [Jan Gromeš](https://github.com/jgromes)
- [arduino-mqtt](https://github.com/256dpi/arduino-mqtt) Joël Gähwiler (256dpi)
- [ArduinoJson](https://arduinojson.org) by Benoit Blanchon 


## MQTT Topics

MQTT publications:

`<base_topic>/data`    sensor data as JSON string - see `publishWeatherdata()`
     
`<base_topic>/radio`   CC1101 radion transceiver info as JSON string - see `publishRadio()`
     
`<base_topic>/status`  "online"|"dead"$

$ via LWT

`<base_topic>` is set by `#define HOSTNAME ...`

## Hardware (ESP8266 D1-Mini)
![Bresser5in1_CC1101_D1-Mini](https://user-images.githubusercontent.com/83612361/158458191-b5cabad3-3515-45d0-98e3-94b0fa13b8ef.jpg)

## Dashboard with [IoT MQTT Panel](https://snrlab.in/iot/iot-mqtt-panel-user-guide) (Example)
![IoTMQTTPanel_Bresser_5-in-1](https://user-images.githubusercontent.com/83612361/158457786-516467f9-2eec-4726-a9bd-36e9dc9eec5c.png)

