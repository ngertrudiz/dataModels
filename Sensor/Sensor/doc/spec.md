# Sensor

This model is built based on the Device & DeviceModel entities [DEVICE](./Device). The motivation for developing this model relies on the need of describe attributes values from each sensor embebed into a device. Thus rather than considering a device as a whole entity, Sensor & SensorModel split an apparatus (i.e., device) into separated elements (i.e., sensors) taking into account a more descriptive information.

## Description

It represents a physical sensor (i.e., hardware + software + firmware) intended to accomplish a particular task (e.g., to sense acceleration, gyroscope, temperature, an so on).

A Sensor is a tangible object which contains some logic and is producer and/or consumer of data. It can be considered as a single object capable of communicating electronically via a network, or as a part of a collection of sensors connected to a single communication mechanism, such as Smartphones or Smartwatches.


## Data Model

+ `id` : Unique identifier. 

+ `type` : Entity type. It must be equal to `Sensor`.

+ `category` : See attribute `category` from [SensorModel](../../SensorModel/doc/spec.md). Optional but recommended to optimize queries.
        
+ `controlledProperty` : See attribute `controlledProperty` from [SensorModel](../../SensorModel/doc/spec.md). Optional but recommended to optimize queries.

+ `controlledAsset` : The asset(s) (building, object, etc.) controlled by the sensor.
    + Attribute type: List of [Text](https://schema.org) or Reference(s) to another entity.
    + Optional

+ `mnc` : This property identifies the Mobile Network Code (MNC) of the network the sensor is attached to.
The MNC is used in combination with a Mobile Country Code (MCC) (also known as a "MCC / MNC tuple")
to uniquely identify a mobile phone operator/carrier using the GSM, CDMA, iDEN, TETRA
and 3G / 4G public land mobile networks and some satellite mobile networks.
    + Attribute type: [Text](https://schema.org/Text)
    + Optional

+ `mcc` : Mobile Country Code - This property identifies univoquely the country of the mobile network the sensor is attached to.
    + Attribute type: [Text](https://schema.org/Text)
    + Optional
    
+ `macAddress` : The MAC address of the sensor.
    + Attribute type: [Text](https://schema.org/Text)
    + Optional
    
+ `ipAddress` : The IP address of the sensor. It can be a comma separated list of values if the sensor has more than one IP address. 
    + Attribute type: [Text](https://schema.org/Text)
    + Optional

+ `supportedProtocol` : See attribute `supportedProtocol` from [SensorModel](../../SensorModel/doc/spec.md). Needed if due to a software update new protocols are supported. Otherwise it is better to convey it at `SensorModel` level. 

+ `configuration` : Sensor's technical configuration. This attribute is intended to be a dictionary of properties which capture
parameters which have to do with the configuration of a sensor (timeouts, reporting periods, etc.)
and which are not currently covered by the standard attributes defined by this model. 
    + Attribute type: [StructuredValue](https://schema.org/StructuredValue)
    + Attribute metadata:
        + `dateModified` :  It captures the last modification timestamp of this attribute.
            + Type: [DateTime](https://schema.org/DateTime) 
    + Optional
    
+ `location` : Location of this sensor represented by a GeoJSON geometry of type point. 
    + Attribute type: `geo:json`.
    + Normative References: [https://tools.ietf.org/html/rfc7946](https://tools.ietf.org/html/rfc7946)
    + Optional.
    
+ `name` : A mnemonic name given to the sensor.
    + Normative References: [name](https://schema.org/name)
    + Optional

+ `description` : Sensor's description.
    + Normative References: [description](https://schema.org/description)
    + Optional

+ `dateInstalled` : A timestamp which denotes when the sensor was installed (if it requires installation).
    + Attribute type: [DateTime](https://schema.org/DateTime)
    + Optional

+ `dateFirstUsed` : A timestamp which denotes when the sensor was first used.
    + Attribute type: [DateTime](https://schema.org/DateTime)
    + Optional

+ `dateManufactured` : A timestamp which denotes when the sensor was manufactured.
    + Attribute type: [DateTime](https://schema.org/DateTime)
    + Optional

+ `hardwareVersion` : The hardware version of this sensor.
    + Attribute type: [Text](https://schema.org/Text)
    + Optional

+ `softwareVersion` : The software version of this sensor.
    + Attribute type: [Text](https://schema.org/Text)
    + Optional

+ `firmwareVersion` : The firmware version of this sensor.
    + Attribute type: [Text](https://schema.org/Text)
    + Optional

+ `osVersion` : The version of the host operating system sensor.
    + Attribute type: [Text](https://schema.org/Text)
    + Optional

+ `dateLastCalibration` : A timestamp which denotes when the last calibration of the sensor happened.
    + Attribute type: [DateTime](https://schema.org/DateTime)
    + Optional
    
+ `serialNumber` : The serial number assigned by the manufacturer.
    + Normative References: [https://schema.org/serialNumber](https://schema.org/serialNumber)
    + Mandatory
    
+ `provider` : The provider of the sensor.
    + Normative References: [https://schema.org/provider](https://schema.org/provider)
    + Optional

+ `refSensorModel` : The sensor's model.
    + Attribute type: Reference to an entity of type [SensorModel](../../SensorModel/doc/spec.md).
    + Optional

+ `batteryLevel` : Sensor's battery level. It must be equal to `1.0` when battery is full. `0.0` when battery ìs empty.
`null` when cannot be determined. 
    + Type: [Number](https://schema.org/Number)
    + Allowed values: Interval [0,1]
    + Attribute metadata:
        + `timestamp`: Timestamp when the last update of the attribute happened.
        This value can also appear as a FIWARE [TimeInstant](https://github.com/telefonicaid/iotagent-node-lib#TimeInstant)
            + Type: [DateTime](http://schema.org/DateTime)
    + Optional
    
+ `sensorState` : State of this sensor from an operational point of view. Its value can be vendor dependent.  
    + Type: [Text](https://schema.org/Text)
    + Attribute metadata:
        + `timestamp`: Timestamp when the last update of the attribute happened.
        This value can also appear as a FIWARE [TimeInstant](https://github.com/telefonicaid/iotagent-node-lib#TimeInstant)
            + Type: [DateTime](http://schema.org/DateTime)
    + Optional

+ `dateLastValueReported` : A timestamp which denotes the last time when the sensor successfully reported data to the cloud.
    + Attribute type: [DateTime](https://schema.org/)
    + Optional

+ `value` : A observed or reported value. For actuator sensors, it is an attribute that allows
a controlling application to change the actuation setting. For instance, a switch sensor which is currently *on* can report a value `"on"`of type `Text`.
Obviously, in order to toggle the referred switch, this attribute value will have to be changed to `"off"`.
    + Attribute type: Any type, depending on the sensor. Usually [Text](https://schema.org/Text) or [QuantitativeValue](https://schema.org/QuantitativeValue).
    + Attribute metadata:
        + `timestamp`: Timestamp when the last update of the attribute happened.
        This value can also appear as a FIWARE [TimeInstant](https://github.com/telefonicaid/iotagent-node-lib#TimeInstant)
            + Type: [DateTime](http://schema.org/DateTime)
    + Optional
    
+ `dateModified` : Last update timestamp of this entity.
    + Attribute type: [DateTime](https://schema.org/DateTime)
    + Optional

+ `dateCreated` : Entity's creation timestamp.
    + Attribute type: [DateTime](https://schema.org/DateTime)
    + Optional    

## Examples

    {
      "id": "sensor-9845A",
      "type": "Sensor",
      "category": ["motion"],
      "controlledProperty": ["acceleration"],
      "controlledAsset": ["wastecontainer-Osuna-100"],
      "ipAddress": "192.14.56.78",
      "mcc": "214",
      "mnc": "07",
      "batteryLevel": 0.75,
      "serialNumer": "9845A",
      "refSensorModel": "myDevice-wastecontainer-sensor-345",
      "value": "-69.895,72.0493,4.90137,2017-01-18T20:45:43.765Z-0800 -69.844,72.0726,4.85817,2017-01-18T20:45:43.799Z-0800...",
      "deviceState": "ok",
      "dateFirstUsed": "2014-09-11",
    }


## Test it with a real service

T.B.D.

## Issues

T.B.D.