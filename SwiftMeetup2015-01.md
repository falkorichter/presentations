# Simple Bike Computer[^1]
### doing something useful with BLTE as a geek
##### git clone https://github.com/deadfalkon/simple-bike-computer-presentation.git
##### pull requests are welcome!

[^1]: Presentation made with [DecksetApp](http://decksetapp.com/) ![inline 8 %](http://cdn3.brettterpstra.com/uploads/2014/03/DecksetIcon.png)

---
#about me
@volkersfreunde
github.com/falkorichter
mobile software Ingenieur
work@sensorberg
[about.me/falkorichter](http://about.me/falkorichter)

---

#Content
* What is BTLE
* Simple Bike Computer
	* Hardware/setup - bike
	* Hardware - phone
* Swift iOS/MacOSX
* optional: Android

---
#BTLE
Bluetooth Low Energy®, a.k.a. Bluetooth Smart®
* simple low energy data transfer
* send simple bits of data fast
* don´t sent alot of data
* easy binding

---
#BTLE
> ​​​To help consumers identify compatibility and ensure connectivity with products and applications incorporating Bluetooth®​​ Core Specification version 4.0 (or higher), the Bluetooth SIG has developed the Bluetooth Smart and Bluetooth Smart Ready trademarks.[^5]

[^5]: [bluetooth.org/en-us/bluetooth-brand/how-to-use-smart-marks](https://www.bluetooth.org/en-us/bluetooth-brand/how-to-use-smart-marks)

---

#BTLE basics
[Services](https://developer.bluetooth.org/gatt/services/Pages/ServicesHome.aspx)
> Services are collections of characteristics and relationships to other services that encapsulate the behavior of part of a device.[^2]

[^2]: [developer.bluetooth.org/gatt/services/Pages/ServicesHome.aspx](https://developer.bluetooth.org/gatt/services/Pages/ServicesHome.aspx)

---
#BTLE basics

[Characteristics](https://developer.bluetooth.org/gatt/characteristics/Pages/CharacteristicsHome.aspx)
> Characteristics are defined attribute types that contain a single logical value.[^3]

[^3]: [developer.bluetooth.org/gatt/characteristics/Pages/CharacteristicsHome.aspx)[https://developer.bluetooth.org/gatt/characteristics/Pages/CharacteristicsHome.aspx]


---
#BTLE basics

[Descriptors](https://developer.bluetooth.org/gatt/descriptors/Pages/DescriptorsHomePage.aspx)
> "Descriptors are defined attributes that describe a characteristic value."[^4]

[^4]: [developer.bluetooth.org/gatt/descriptors/Pages/DescriptorsHomePage.aspx](https://developer.bluetooth.org/gatt/descriptors/Pages/DescriptorsHomePage.aspx)

---
#Why a bike computer?

##I ride my bike
##It´s not too expensive
##I want to know how far I go each week/month/year
##health foo #ftw

---
#Ingredients
Speed and Cadence Sensor

![inline fill](http://ecx.images-amazon.com/images/I/31f58c%2BTnUL.jpg)![inline fill](http://ecx.images-amazon.com/images/I/61Vb-HydLPL._SL1000_.jpg) ![inline fill](http://ecx.images-amazon.com/images/I/61sDR2xHfaL._SL1000_.jpg)

---
#Ingredients
![inline 33%](http://ecx.images-amazon.com/images/I/7191wWpGSfL._SL1500_.jpg)![inline 33%](http://ecx.images-amazon.com/images/I/815nGc7aReL._SL1500_.jpg)

---
#Ingedients
Amazon: "Geschwindigkeit und Trittfrequenz"

Any Mac / iPhone > 4S

Remove the label o the device with nail polish remover

---
#Speed and Cadence

* official Profile [all](https://developer.bluetooth.org/gatt/profiles/Pages/ProfilesHome.aspx)
* Cycling Speed and Cadence
	* [org.bluetooth.service.cycling_speed_and_cadence](https://developer.bluetooth.org/gatt/services/Pages/ServiceViewer.aspx?u=org.bluetooth.service.cycling_speed_and_cadence.xml) mandatory
	* [org.bluetooth.service.device_information](https://developer.bluetooth.org/gatt/services/Pages/ServiceViewer.aspx?u=org.bluetooth.service.device_information.xml) optional
	
It´s all nicely documented.

---
#Swift
everything is a pretty easy
stack (almost) identical on iOS & MacOSX (I had a compilation error on the same code)
characteristic.value() vs characteristic.value

---
#Hello world of BTLE: heartRate
[org.bluetooth.service.heart_rate](https://developer.bluetooth.org/gatt/services/Pages/ServiceViewer.aspx?u=org.bluetooth.service.heart_rate.xml)
1 Service
1 Value (the heart rate)
-> simulate beeing a heart rate sensor
-> simulate connecting to a heart rate sensor
[github.com/falkorichter/swift-simple-bike-computer](https://github.com/falkorichter/swift-simple-bike-computer)

---

#Swift become a peripheral:[^6][^7]
```swift
func startBroadcasting(){
    heartRateService.characteristics = [hearRateChracteristic]
    infoService.characteristics = [infoNameCharacteristics]
    
    peripheralManager.addService(infoService)
    peripheralManager.addService(heartRateService)
    var advertisementData = [
        CBAdvertisementDataServiceUUIDsKey:[infoService.UUID, heartRateService.UUID],
        CBAdvertisementDataLocalNameKey : "mac of falko"
    ]
    peripheralManager.startAdvertising(advertisementData)   
}
[...]
```

[^6]: done: [github.com/deadfalkon/swift-simple-bike-computer/blob/master/Shared/HeartBeatPeripheral.swift](https://github.com/deadfalkon/swift-simple-bike-computer/blob/master/Shared/HeartBeatPeripheral.swift)

[^7]: needed: [github.com/deadfalkon/swift-simple-bike-computer/blob/master/Shared/SpeedAndCadencePeripheral.swift](https://github.com/deadfalkon/swift-simple-bike-computer/blob/master/Shared/HeartBeatPeripheral.swift)

---
#Swift get notified :1 [^8]


```swift
let CSC_SERVICE = CBUUID(string: "1816")
let CSC_MEASUREMENT  = CBUUID(string: "2A5B")

func centralManagerDidUpdateState(central: CBCentralManager!){
    switch (central.state){
    case .PoweredOn:
        central.scanForPeripheralsWithServices([CSC_SERVICE], options: nil)
    default:
        println("not powered on")
    }
}
```
[^8]: https://github.com/deadfalkon/swift-simple-bike-computer/blob/master/Shared/CadenceConnector.swift

---
#Swift get notified :2

```swift
func centralManager(central: CBCentralManager!, didConnectPeripheral peripheral: CBPeripheral!){
    peripheral.discoverServices([CSC_SERVICE])
}
```

---
#Swift get notified :3

```swift
func peripheral(peripheral: CBPeripheral!, didDiscoverServices error: NSError!){
    if(error != nil) {
        for service in peripheral.services {
            if service.UUID == CSC_SERVICE {
                peripheral.discoverCharacteristics([CSC_MEASUREMENT], forService: service as CBService)
            }
        }
    }
}
```

---
#Swift get notified :4

```swift
func peripheral(peripheral: CBPeripheral!, didDiscoverCharacteristicsForService service: CBService!, error: NSError!) {
    if(error != nil){
        if service.UUID == CSC_SERVICE {
            for characteristic in service.characteristics{
                if (characteristic as CBCharacteristic).UUID == CSC_MEASUREMENT {
                    peripheral.setNotifyValue(true, forCharacteristic: characteristic as CBCharacteristic);
                }
            }
        }
    }
}
```
---
#Swift get notified :5

```swift
func peripheral(peripheral: CBPeripheral!, didUpdateValueForCharacteristic characteristic: CBCharacteristic!, error: NSError!) {
	//do your thing
}
```
