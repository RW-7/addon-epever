# Home Assistant Add-on: Epever solar client

_Simple add-on for Epever solar client._

![Supports aarch64 Architecture][aarch64-shield]
![Supports amd64 Architecture][amd64-shield]
![Supports armhf Architecture][armhf-shield]
![Supports armv7 Architecture][armv7-shield]
![Supports i386 Architecture][i386-shield]

[aarch64-shield]: https://img.shields.io/badge/aarch64-yes-green.svg
[amd64-shield]: https://img.shields.io/badge/amd64-yes-green.svg
[armhf-shield]: https://img.shields.io/badge/armhf-yes-green.svg
[armv7-shield]: https://img.shields.io/badge/armv7-yes-green.svg
[i386-shield]: https://img.shields.io/badge/i386-yes-green.svg

add this in Homeassistant configuration.yaml
```yaml
mqtt:
    sensor:
      - name: "input voltage"
        unique_id: input_voltage
        state_topic: "home/epever-solar2/epever/data"
        value_template: '{{ value_json["chargingInputVoltage"] }}'
        unit_of_measurement: "V"
        device:
           identifiers: Tracer2210AN
           manufacturer: "Epever"
           name: ReRuBabs_solar 
           model: "V01.02"
    
      - name: "input current"
        unique_id: station_input_current
        state_topic: "home/epever-solar2/epever/data"
        value_template: '{{ value_json["chargingInputCurrent"] }}'
        unit_of_measurement: "A"
        device:
           identifiers: Tracer2210AN
           manufacturer: "Epever"
           name: ReRuBabs_solar 
           model: "V01.02"
    
      - name: "input power"
        unique_id: station_input_power
        state_topic: "home/epever-solar2/epever/data"
        value_template: '{{ value_json["chargingInputPower"] }}'
        #last_reset_value_template: "{{value_json.lastUpdate | int | timestamp_custom('%d.%m.%Y %H:%M'}}"
        unit_of_measurement: "W"
        device:
           identifiers: Tracer2210AN
           manufacturer: "Epever"
           name: ReRuBabs_solar 
           model: "V01.02"
    
      - name: "battery charging voltage"
        state_topic: "home/epever-solar2/epever/data"
        unique_id: station_battery_charging_voltage
        value_template: '{{value_json["chargingOutputVoltage"] }}'
        unit_of_measurement: "V"
        device_class: voltage
        device:
           identifiers: Tracer2210AN
           manufacturer: "Epever"
           name: ReRuBabs_solar 
           model: "V01.02"

      - name: "battery charging current"
        state_topic: "home/epever-solar2/epever/data"
        unique_id: station_battery_charging_current
        value_template: '{{value_json["chargingOutputCurrent"] }}'
        unit_of_measurement: "A"
        device_class: current
        device:
           identifiers: Tracer2210AN
           manufacturer: "Epever"
           name: ReRuBabs_solar 
           model: "V01.02"
           
      - name: "battery charge level"
        state_topic: "home/epever-solar2/epever/data"
        unique_id: station_battery_charge_level
        value_template: '{{value_json["batterySoC"] }}'
        unit_of_measurement: "%"
        device_class: battery
        device:
           identifiers: Tracer2210AN
           manufacturer: "Epever"
           name: ReRuBabs_solar 
           model: "V01.02"
           
      - name: "charging status"
        state_topic: "home/epever-solar2/epever/status"
        unique_id: station_charging_status
        value_template: '{{value_json["equipmentStatus"]["battery"] }}'
        device:
           identifiers: Tracer2210AN
           manufacturer: "Epever"
           name: ReRuBabs_solar 
           model: "V01.02"

```