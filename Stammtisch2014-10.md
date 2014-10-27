# Simple Bike Computer
### doing something useful BLTE as a geek

---

#Content
* What is BTLE
* How does it work on Android
* Simple Bike Computer
	* Hardware/setup - bike
	* Hardware - phone
* How does it work on *other* platforms?
	* Swift iOS/MacOSX

---

#BTLE
* simple low energy data transfer
* send simple bits of data fast
* don´t sent alot of data
* easy binding

---

#BTLE
* [Services](https://developer.bluetooth.org/gatt/services/Pages/ServicesHome.aspx)
	* "Services are collections of characteristics and relationships to other services that encapsulate the behavior of part of a device."
* [Characteristics](https://developer.bluetooth.org/gatt/characteristics/Pages/CharacteristicsHome.aspx)
	* "Characteristics are defined attribute types that contain a single logical value." 
* [Descriptors](https://developer.bluetooth.org/gatt/descriptors/Pages/DescriptorsHomePage.aspx)
	* "Descriptors are defined attributes that describe a characteristic value."	

---
#Why a bike computer?

##I ride my bike
##It´s not too expensive
##I want to know how far I go each week/month/year
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

---
#Speed and Cadence

* official Profile [all](https://developer.bluetooth.org/gatt/profiles/Pages/ProfilesHome.aspx)
* Cycling Speed and Cadence
	* [org.bluetooth.service.cycling_speed_and_cadence](https://developer.bluetooth.org/gatt/services/Pages/ServiceViewer.aspx?u=org.bluetooth.service.cycling_speed_and_cadence.xml) mandatory
	* [org.bluetooth.service.device_information](https://developer.bluetooth.org/gatt/services/Pages/ServiceViewer.aspx?u=org.bluetooth.service.device_information.xml) optional
	
It´s all nicely documented.

---
#BTLE on Android
* BluetoothManager
* BluetoothGattCallback
	* onConnectionStateChange
    * onReadRemoteRssi
    * onServicesDiscovered
    * onCharacteristicChanged 		
Connect.java

---
#BTLE on Android
1. Subscribe to **Notify** Characteristic *org.bluetooth.characteristic.csc_measurement*
2. extract values
3. display them

---
#Android: Scan and connect
```java
   final BluetoothAdapter adapter = bluetooth.getAdapter();
   UUID[] serviceUUIDs = new UUID[]{CSC_SERVICE_UUID};
   adapter.startLeScan(serviceUUIDs, new BluetoothAdapter.LeScanCallback() {
		@Override
		public void onLeScan(BluetoothDevice device, int rssi, byte[] scanRecord) {
			device.connectGatt(Connect.this, autoConnectCheckBox.isChecked(), bluetoothGattCallback);
		}
	}
```

---
#Android: Scan for Services
######BluetoothGattCallback:

```java
   @Override
   public void onConnectionStateChange(BluetoothGatt gatt, int status, int state) {
       super.onConnectionStateChange(gatt, status, state);
       switch (state) {
           	case BluetoothGatt.STATE_CONNECTED: {
               showText("STATE_CONNECTED", Style.INFO);
               setConnectedGatt(gatt);
               gatt.discoverServices();
               break;
			}
		}
	}
```

---
#Android: Register for Updates
######Register for Updates of the **org.bluetooth.characteristic.csc_measurement**
######BluetoothGattCallback:

```java
	@Override
    public void onServicesDiscovered(BluetoothGatt gatt, int status) {
    	super.onServicesDiscovered(gatt, status);
        BluetoothGattCharacteristic valueCharacteristic = gatt.getService(CSC_SERVICE_UUID).getCharacteristic(CSC_CHARACTERISTIC_UUID);
        boolean notificationSet = gatt.setCharacteristicNotification(valueCharacteristic, true);
        BluetoothGattDescriptor descriptor = valueCharacteristic.getDescriptor(BTLE_NOTIFICATION_DESCRIPTOR_UUID);
        descriptor.setValue(BluetoothGattDescriptor.ENABLE_NOTIFICATION_VALUE);
        boolean writeDescriptorSuccess = gatt.writeDescriptor(descriptor);
	}
```
---
#Android: Monitor the RSSI
######BluetoothGattCallback:
```java
	@Override
	public void onReadRemoteRssi(BluetoothGatt gatt, int rssi, int status) {
		super.onReadRemoteRssi(gatt, rssi, status);
		listener.updateRssiDisplay(rssi);
	}
	@Override
	public void onCharacteristicChanged(BluetoothGatt gatt, BluetoothGattCharacteristic characteristic) {
		super.onCharacteristicChanged(gatt, characteristic);
		gatt.readRemoteRssi();
	}
```
######Also when scanning:
```java
	final BluetoothAdapter adapter = bluetooth.getAdapter();
     UUID[] serviceUUIDs = new UUID[]{CSC_SERVICE_UUID};
     adapter.startLeScan(serviceUUIDs, new BluetoothAdapter.LeScanCallback() {
         @Override
         public void onLeScan(BluetoothDevice device, int rssi, byte[] scanRecord) {
			listener.updateRssiDisplay(rssi);
         }
     });
```

---

#Swift
### #wtf is swift?

---

#Swift
everything is a little easier
```swift
	
```




