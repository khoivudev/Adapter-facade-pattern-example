### Adapter facade pattern concepts
* The client makes a request to the adapter by calling a method on it using the [target interface].
* The adapter translates the request into one or more calls on the adaptee using the [adaptee interface].
* The client receives the results of the call and never knows there is an adapter doing the translation.

#### Object Adapter
* [client] -> [target interface][translate](adaptee adapter)-> [adaptee interface]
* [client] -> [Duck interface][translate](Turkey adapter) -> [Turkey interface]
* [client] -> [Vehicle interface][translate](PX4 adapter) -> [PX4 Interface]


##### Code

```java
class PX4FAdapter implement Vehicle {
    PX4Firmware px4Firmware;

    takeOff() {
        px4Firmware.takeOff()
    }
    returnHome() {
        px4Firmware.returnHome()
    }
    arm() {
        px4Firmware.arm()
    }
    disarm() {
        px4Firmware.disarm()
    }
}

PX4Firmware px4Firmware = new PX4Firmware();
Vehicle px4Vehicle = new PX4FAdapter(px4Firmware);
```

##### Class Diagram
![alt_image](/design/object_adapter_diagram.png)

#### Class Adapter
* class adapter we subclass the Target(Vehicle) and the Adaptee(PX4Firmware), while with 
* object adapter we use composition to pass requests to an Adaptee.
* Note: the class adapter uses multiple inheritance, so you can’t do it in Java...
##### Code

```java
class PX4FAdapter extends PX4Firmware, Vehicle {
}

PX4Firmware px4Firmware = new PX4Firmware();
Vehicle px4Vehicle = new PX4FAdapter();
```

##### Class Diagram
![alt_image](/design/class_adapter_diagram.png)


### Home Sweet Home Theater 
