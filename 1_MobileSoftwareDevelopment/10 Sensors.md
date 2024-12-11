### <mark style="background: #AD21D9;">Introduction:</mark>

While smartphones may have less computation power than laptops/PCs and battery limitations, they have one significant advantage: 

They have sensors to measure aspects / properties of the current environment  

<mark style="background: #AD21D9;">In this lecture:</mark>  
- we will introduce the various sensor types, 
- coordinate systems and  
- the issues that surround sensors

![](https://i.imgur.com/DKdLdzB.png)

### <mark style="background: #AD21D9;">Sensors:</mark>  

Sensors permit a device to collect data about the current environment,  

While data is basic it can provide useful information about what a user is doing / state  

Examples in latest generation devices include heart rate monitors and step counters  

For tracking user health and fitness

![](https://i.imgur.com/Np8ts5T.png)

### <mark style="background: #AD21D9;">Scalar Sensors:</mark>  

<mark style="background: #AD21D9;">Sensors are divided into two types:</mark>  
- Scalar
- Vector  

A scalar sensor is a sensor that reads a single valued property about an environment  

That property has no directional component, e.g. ambient temperature

![](https://i.imgur.com/3e1q2zQ.png)

### <mark style="background: #AD21D9;">Light Sensors:</mark>  

The light sensor measures ambient light levels in an environment  

Unit of measurement = Lux  

0 represents complete darkness while increasing values represent increasing brightness.  

Well lit room will approximately be 300 to 500 lux  

One of the main uses of this sensor is automatic adjustment of screen brightness in response to room lighting level.

### <mark style="background: #AD21D9;">Temperature Sensor:</mark>

![](https://i.imgur.com/DmsjhFy.png)

### <mark style="background: #AD21D9;">Proximity Sensor:</mark> 

Proximity sensors measure how close an object is to the sensor  

Unit of measurement is centimetre  

Disable/enable a screen when user moves device to their ear for a phone call.  

Also used when a device is put face down to silence the device from accepting calls.

### <mark style="background: #AD21D9;">Barometric Sensors:</mark>

![](https://i.imgur.com/dg2LKqV.png)

### <mark style="background: #AD21D9;">Vector sensors:</mark> 

Vector sensors are sensors that measure data in more than one dimension  

All vector sensors in android will measure in three directions  

These sensors tend to be the most common in android devices  

As they provide much more information about the environment to the user

![](https://i.imgur.com/mmOuBqq.png)

### <mark style="background: #AD21D9;">Accelerometers:</mark>

An accelerometer is used to measure accelerations in all three directions 

<mark style="background: #AD21D9;">Acceleration</mark> = rate in change in velocity.  

Higher absolute values state that device is undergoing quicker changes in speed  

The SI unit here is metres per second squared ms<sup>−2</sup> but common to convert this is G-force units as well 1g = 9.81ms<sup>−2</sup>  

More commonly used sensors

### <mark style="background: #AD21D9;">Gyroscopes:</mark>  

Gyroscopes are used to measure the speed of rotation of device  

Unit of measurement is radians per second. 

Higher absolute values represent faster device rotation  

Another more commonly found sensor  

Used with an accelerometer to generate device orientation

### <mark style="background: #AD21D9;">Magnetic field sensors:</mark> 

Magnetic field = detect the magnetic field strength of the earth  

Unit of measurement here is the <mark style="background: #AD21D9;">micro-Tesla</mark> (μT).  

Higher values indicate a stronger magnetic field  

Generally used to get device orientation if gyroscope is not available  

More recent use is for magnetic covers to turn screens on and off automatically.

### <mark style="background: #AD21D9;">Virtual Sensors:</mark>  

Using sensors like the accelerometer may not be the best approach  

In the case of the accelerometer, will not always have a gravity component need in application  

Thus, Android provides a series of virtual sensors that will provide filtered versions of data and common combinations of sensors  

Here we look at a few of these virtual sensors.

### <mark style="background: #AD21D9;">Linear Accelerometer:</mark>

The linear accelerometer is a high pass filter applied to the values that come back from the accelerometer  

The high pass filter will remove the gravity component from the accelerometer as it is constant and has a frequency of zero  

This will only leave the accelerations on the device that are caused by the user  

Generally used in place of the raw accelerometer

### <mark style="background: #AD21D9;">Gravity Sensor:</mark> 

The gravity sensor is a low pass filter applied to the accelerometer  

Thus removing all of the user induced accelerations on the device  

Main use = determining orientation  

Generally more interested in removing the gravity component

### <mark style="background: #AD21D9;">Rotation Vector:</mark> 

The rotation vector is a combination of the accelerometer and gyroscope that is used to determine a three axis orientation of a device  

Has a different coordinate system to the other sensors  

Will produce a set of values that will enable the device to determine its compass bearing and the pitch and roll of the device

### <mark style="background: #AD21D9;">Sensors and uses - Summary:</mark>

![](https://i.imgur.com/Tue7RdT.png)

### <mark style="background: #AD21D9;">Location Sensors:</mark>

One of the more important sensors within the device

Used to locate the device on the surface of the planet

Mainly used for navigation and geotagging purposes.

Also used for anti-theft measures

### <mark style="background: #AD21D9;">GPS:</mark> 

This is the most accurate of the location sensors. Uses the Global Positioning System satellite signals  

Can provide accuracy to within a few metres  

Generally used for navigation but because it does not encode direction it is assisted by the rotation vector  

BUT ... does not work indoors

### <mark style="background: #AD21D9;">Network Location:</mark> 

“location system” that uses a database of network access points and their location  

Provides an approximation of the location of the device  

However, unlike GPS it works both indoors and outdoors  

Generally the two will be combined to provide a full location for the device indoor and outdoor.

### <mark style="background: #AD21D9;">Android Sensor Management:</mark> 

Sensors are managed through a series of sensor classes  

To hide the individual differences in how each sensor is managed.  

Provide a unified interface to the developer  

All applications must register interest in sensors directly with the Android OS  

To reduce battery usage, android will deliver updates at the rate required by each individual application rather than have multiple applications polling the sensor.

### <mark style="background: #AD21D9;">Permissions:</mark> 

Getting access to majority of sensors does not require any form of permissions  

Very difficult to do any kind of malicious activity just by reading gyroscopes and accelerometers  

However, for the location sensors , there is explicit permissions required  

As an application can track the user’s location and user may not want to disclose this information  

May cause privacy issues if sensor is being used for gait analysis to determine health.

### <mark style="background: #AD21D9;">Sensor Querying:</mark> 

No guarantee that a sensor will be on a device  

While variety of sensors appear on majority of devices, some rarely default on all (temperature and barometric )  

Expected to query the existence of a sensor before using it  

Generally ask for the default sensor of the type you are interested in.  

If a null value is returned then the device has no sensors of that type.

### <mark style="background: #AD21D9;">Sensor Manager Class:</mark> 

Class through which all access to sensors is handled and where sensor listeners registered  

You will query this service for all of the sensors you require in your application  

Register listeners for those sensors with this service  

It will then take responsibility for triggering your listeners whenever a new sensor value is obtained.

### <mark style="background: #AD21D9;">Sensor Class:</mark> 

Contains all the information about each sensor that a device has  

Includes all the constants that differentiate between the different sensor types  

You can use this to query the specification of the individual sensors  

For example if you are looking to compare the sensors of each individual type and are looking for the best one

### <mark style="background: #AD21D9;">Sensor Listeners:</mark> 

Small segments of code that provide a means of capturing new sensor values  

Values may then be used to update your application and UI  

Also includes information about the current accuracy of the sensor  

Gives you a chance to change another sensor if there is another one available or to change your UI to inform user of lower accuracy

### <mark style="background: #AD21D9;">Sensor Delay Types:</mark> 

There are three main default sensor update rates (possible to define custom rates as well provided they are greater than or equal to the first constant listed)  

<mark style="background: #AD21D9;">SENSOR DELAY FASTEST:</mark> get updates from sensor as fast as it can produce them  

<mark style="background: #AD21D9;">SENSOR DELAY GAME:</mark> get updates from the sensor at a rate that is appropriate for game loop processing  

<mark style="background: #AD21D9;">SENSOR DELAY UI:</mark> get updates from the sensor at a rate that is suitable for updating a UI

### <mark style="background: #AD21D9;">Where Sensors fit in with the Activity Life Cycle:</mark> 

Recommended that sensors should register when application is not in the stopped state  

Generally users are not interested in sensor values if not active  
- Deregister listeners in the ``onStop()`` method and  
- Reregister in the ``onStart()`` method as a way of conserving battery power

### <mark style="background: #AD21D9;">GPS and the activity lifecycle:</mark> 

The same advice applies to location sensors with a few minor exceptions  

The main exception is the navigation case  

This is because if a navigation app is interrupted and removes location listeners, upon reregistering it will take about 5 to 10 seconds to get a GPS fix.  

If you are constrained by this then keep the sensor active, otherwise deregister it.

### <mark style="background: #AD21D9;">Issues to consider with sensors:</mark> 

While sensors do provide a lot of information about the environment and your user there are issues to consider with their use  

These must be considered carefully  

As they will affect the level of trust of your users and also the amount of information you collect on them  

Also the performance of your application and associated battery drain

### <mark style="background: #AD21D9;">User Tracking:</mark> 

One of the most important issues is the use of location sensors to track user location  

Possible for this data to be abused - Track a user’s full movements throughout a long period of time  

If app is going to track user, must inform them initially and give a chance to opt out

### <mark style="background: #AD21D9;">Clarity on data use:</mark> 

Like permissions you should be fully clear on what data you use from sensors and what for  

Applications that do this generally are safe and more likely to be trusted by users  

If you collect such data from your user (particularly location) and store on a server somewhere, please secure it with encryption  

And also if you can anonymise and scrub as much identifying information as is possible

### <mark style="background: #AD21D9;">Battery Use:</mark>  

Delicate balancing act between  
- sensor accuracy  
- performance 
- battery power  

Higher poll rates on sensors produce quicker updates & will improve the accuracy of application  

But ... this will cause higher battery power consumption  

Inversely, save battery at the expense of timeliness & accuracy

### <mark style="background: #AD21D9;">Sensor Accuracy:</mark> 

Another issue to consider is that every sensor will have different accuracies and value ranges  

Devices with cheaper sensors may not provide many values and their accuracy may be questionable  

More expensive sensors will provide higher accuracy and values but will cost more  

You cannot assume any base level with regards to accuracy and value range with any sensor on any device

### <mark style="background: #AD21D9;">When to use multiple sensors of the same type:</mark> 

Some devices will provide more than one of the same sensor type  

It is possible to register interest in more than one sensor of the same type  

Only done if you need higher accuracy than you get from a single sensor  

Through the use of averaging or filtering both sensors

### <mark style="background: #AD21D9;">Sensor values are not absolute:</mark>  

Sensors may not represent values as a continuous range but as discrete steps with a gap in between  

While a sensor measure a continuous variable the sensor has to represent this as a discrete value  

Thus there will be a level of error associated between what the sensor reports and the actual value of that property in the environment  

Usually more expensive sensors will have more discrete levels leading to a larger set of values that can be represented

### <mark style="background: #AD21D9;">Rotation Coordinate System:</mark> 

Rotation vector uses the ground plane as reference instead of the device  

X axis is pointing right - represents <mark style="background: #AD21D9;">pitch</mark> axis of device  

Y axis pointing vertically up - represents <mark style="background: #AD21D9;">roll</mark> axis of device  

Z axis pointing towards user - represents the <mark style="background: #AD21D9;">compass</mark> direction

![](https://i.imgur.com/lsEFvei.png)

### <mark style="background: #AD21D9;">Location Coordinate System:</mark>

Takes advantage of world standard latitude and longitude

Takes the earth and maps the surface as a 2D plane

Latitude determines north/south range [-90,90]

Longitude determines east/west range of [-180,180]