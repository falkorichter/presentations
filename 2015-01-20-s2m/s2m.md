# sensorberg & blte[^1]

[^1]: Presentation made with [DecksetApp](http://decksetapp.com/) ![inline 8 %](http://cdn3.brettterpstra.com/uploads/2014/03/DecksetIcon.png)


---
##questions?
#ask them right away!

---
#about me
falko@sensorberg.com
https://github.com/falkorichter
mobile software 
[about.me/falkorichter](http://about.me/falkorichter)

---
#about me
iOS / Android / anything
connect smart phone to my world


---
#sensorberg
* we sell beacons
	* USB stick, TI based, Nordic based
	* German QA
* planning beacon installations
    * subways, fairs, showcases
* software integration support
* complete software stack...

---
#software-stack
###iOS SDK
###Android SDK
###Backend with REST API
###Management Console[^2]
###Tools (Showcase Apps[^3], MacBeacon[^4], MacScanner, Technical Scanner, Beacon Configuration Tool, Fully automated Beacon Configuration Tool)
  
[^2]: [manage.sensorberg.com](https://manage.sensorberg.com)

[^4]: [BeaconOSX](https://github.com/sensorberg-dev/BeaconOSX)

[^3]: [GooglePlay](https://play.google.com/store/apps/developer?id=Sensorberg+GmbH)
--
#SDKs
easy integration
flexibility
hello world

--
#Android SDK
* scan in background
* stay awake in all neccesary conditions
* put process to sleep as long as possible
* resolve beacon events with backend and trigger presentation/reaction
* Service implementation

--
#iOS SDK
* tweak CoreLocation to enable background and foreground detection of any beacon
* resolve beacon events with backend and trigger presentation/reaction

--
#Android Architecture
* close as possible to the system
* android.app.AlarmManager, separate process Service, Intent RPC
* separate modules.
* Components:
	* Scanner
	* Resolver
	* Presenter
* test driven as much as possible 
	
--
#SDK coming soon
* offline capabilities
* caching of actions
* persistence of event in case of no connectivity
* Volley with Diskbased Cache + OKHttp

--






