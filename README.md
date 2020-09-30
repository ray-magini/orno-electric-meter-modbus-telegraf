# Orno Electric Meter Modbus Telegraf
The Telegraf configuration enables Telegraf to read the Modbus RS485 registers of a ORNO OR-WE-517 electric meter (https://www.orno.pl/en/category/productData/4827/3-phase-multi-tariff-energy-meter-with-RS-485--80A)
This will probably work with any other ORNO electic meter holding the same Modbus registers.

## My Setup ##
* ORNO OR-WE-517 (https://www.orno.pl/en/category/productData/4827/3-phase-multi-tariff-energy-meter-with-RS-485--80A)
* RS485 USB converter stick (https://www.amazon.de/gp/product/B016IG6X7I/ref=ppx_yo_dt_b_asin_title_o08_s00?ie=UTF8&psc=1)
* Raspberry Pi with Raspian
* Telegraf (https://www.influxdata.com/time-series-platform/telegraf/)


## Further processing of the data ##
As per default Telegraf provides many options to output the data in many ways

### Telegraf output to influxdb ###
I am using this data for Grafana  
```
[[outputs.influxdb]]
   urls = ["http://influxdb.example.com:8086"]  
   database = "telegraf"  
```

### Telegraf output to mqtt ###
I am using this data for OpenHAB  
```
[[outputs.mqtt]]  
   servers = ["mqtt.example.com:1883"]  
   topic_prefix = "telegraf_modbus_common"  
   qos = 1  
   data_format = "json"  
```

