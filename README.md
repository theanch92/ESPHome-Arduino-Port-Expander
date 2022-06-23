# ESPHome-Arduino-Port-Expander
An Arduino Port Expander for ESPHome with added Arduino Mega 2560 support  
See the <a href='https://esphome.io/cookbook/arduino_port_extender.html'>Esphome</a> page for documentation.

## Additional Updates

In addition to the binary and analog sensors, support for text sensors has been added. This makes it a little easier to send arbitrary data or precalculated text. The example sketch has been updated to demonstrate sending precalculated data from a DHT22 temperature / humidity sensor.

### Yaml Example
```
text_sensor:
  - platform: custom
    text_sensors:
    - name: "Temperature"
      id: text_1
      filters:
      - append: "F"
    - name: "Humidity"
      id: text_2
      filters:
      - append: "%"
    - name: "Heat Index"
      id: text_3
      filters:
      - append: "F"
    lambda: |-
      return {ape_text_sensor(expander1, 1, "Temperature"),
            ape_text_sensor(expander1, 2, "Humidity"),
            ape_text_sensor(expander1, 3, "Heat Index")};
```

