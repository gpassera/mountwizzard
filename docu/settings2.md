## Settings for ASCOM / Mount Drivers environment drivers and remote access

<img src="pics/tab_settings_ascommountdriver.png"/>

### Area 1: Mount Connection
The connection to the mount could be done either via an ASCOM driver (original 10micron or Per's driver) or via a direct IP connection.
In most cases it is simpler to use the direct connection (IP connection), because driver settings may cause interference with MountWizzard.
If you are using direct moutn connection, please enter the ip address of the mount. The port is set by MountWizzard automatically.
So if you are using Per's driver, please turn the update refraction parameter off. In addition, if you set the slewing speed in the driver,
it overwrites the settings you have done in MountWizzard. As the communication only used native mount commands, no functionality of any
driver is used. The ASCOM driver just passes the command through to the mount.
For simulation purposes it makes sense also to simulate the telescope. In that case you can choose the ASCOM telescope .NET simulation as
telescope. The functionality of MountWizzard with a simulated mount in naturally limited.

### Area 2: Relay Box
If you are using a KVM IP 8 port relay switch, you have to set the correct IP for the switch.

### Area 3: Setup Devices
Beside camera and telescope you could have several devices connected. MountWizzard supports some types:
- ASCOM Domes (Azimuth only)
- Observing Conditions(ObsCond) at the mount: Stickstation or MBox
- Observing Conditions on Open Weather
- Observing conditions for SQR metering: Unihedron SQR Device

The support of Dom is limited to slew a connected Dome to the right azimuth before moving on doing the next image. It's not a fully
supported Dome remote.

The ObsCond is the important device, where MountWizzard takes the information for update the refraction parameters. Normally you would use
a Stickstation or a MBox solution. But basically all devices, which deliver that data (temperature, humidity, pressure, dew point) could
be used. If you don't own one of them, you still can use Open Weather.

The Open Weather service gives you more information. You have to obtain an API key. Please check their website http://openweathermap.org/api
for further informations.

Last, but not least, you can have a sky quality meter from Unihedron attached. You have to use a USB type and you have to connect it via
ASCOM. There is a driver written by animaal (SGPro Forum under http://forum.mainsequencesoftware.com/t/environment-device-values/5051/16)
you find the driver on http://www.dizzy.eu/downloads.html. It does a great job!

### Area 4: ASCOM Camera PlateSolver

Still experimental, you might run into troubles. I let you know, when it works!

### Area 5: Remote Access for MW.

A first shot enabling backyard automation. When checked, MountWizzard will listen on port 3495 for commands send over via TCP. Actually
the only command is
<pre>shutdown</pre>
You could send the command on a windows pc by tool, which allows you to send a string via TCP. Here an example: Google for "NCAT Portable"
and download that tool. You can move the exe file in a directory which is available from your scripting environment (SGPro etc.) The command
for shutting down MountWizzard woudl be from the command line (or batch file):

<pre>echo shutdown | ncat --send-only localhost 3495</pre>

Still experimental, you might run into troubles. I let you know, when it works!

### Hints for configuration:
I'm using SGPro as my imaging setup. To make the best out of it, I choose the ASCOM Observation Conditions Hub as my environment device:

<img src="pics/observationconditions_sgpro.png"/>

if you configure that hub with data from open waether, stickstation (or MBox) and unihedron driver, SGPro puts all this data in you FITS
image files. With that information you can later check the conditions of you night ! Here my setup in the ASCOM hub:

<img src="pics/observationconditionshub.png"/>

[Back to settings](settings.md)

[Back to first steps](firststeps.md)

[Back to Home](home.md)