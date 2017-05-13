# MultisensoryDevice 

## Description

This model is built based on the FIWARE's Device & DeviceModel entities [DEVICE](../Device), however, unlike the aforementioned models, this entity aims to provide a detailed description of a device by splitting it into respective sensors.

## Example of use

```
{
  "id": "device-9845A",
  "type": "MultisensoryDevice",
  "category": "smartphone",
  "controlledProperty": "accelerometer",
  "osVersion": "Android 4.0",
  "softwareVersion": "MA-Test 1.6",
  "hardwareVersion": "GP-P9872",
  "firmwareVersion": "SM-A310F",
  "refDeviceModel": "mySensor-sensor-345",
  "refSensor":[
    "sensor-9845A",
    "sensor-9845B",
    "sensor-9845C"
  ]
  "dateCreated": "2016-08-22T10:18:16Z"
}
```