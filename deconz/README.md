# Jvannoyx4 deCONZ

Installation
The installation of this add-on is straightforward and easy to do.

Navigate in your Home Assistant frontend to Hass.io -> Add-on Store.
Find the "deCONZ" add-on and click it.
Click on the "INSTALL" button.
How to use
Using a RaspBee
If your are using RaspBee, you may need to edit the config.txt file in the root
of your SD card in order for your RaspBee to be recognized and assigned a device name.

Add following to your config.txt:

enable_uart=1
dtoverlay=pi3-miniuart-bt
Configure the add-on
The add-on needs to know where your ConBee/RaspBee can be found, and therefore,
you'll need to configure the add-on to point to the right device.

If you're using Hass.io you may find the correct value for this on the
Hass.io -> System -> Host system -> Hardware page.

Replace null in the device option in the add-on configuration and specify
the device name in quotes: (e.g. "/dev/ttyUSB0", "/dev/ttyAMA0", or "/dev/ttyACM0").
Click on "SAVE" to save the add-on configuration.
Start the add-on.
After installing and starting this add-on, access the deCONZ WebUI ("Phoscon")
with "WEB UI" button.

Configuring the Home Assistant deCONZ Component
By default, Home Assistant has the discovery component enabled, which
automatically discovers this add-on.

Navigate to Configuration -> Integrations page after starting this
add-on to configure the deCONZ component.

In case you don't have discovery enabled on your Home Assistant instance,
follow these instructions to configure the deCONZ component:

https://home-assistant.io/components/deconz/

Migrating to this Add-on
To migrate deCONZ to Hass.io and this add-on, backup your deCONZ config via the
Phoscon WebUI, then restore that config after installing/reinstalling.

You must perform these steps or your Light, Group names and other data will be lost!

However, your ZigBee devices will remain paired to your ConBee or RaspBee hardware.

Accessing the deCONZ application and viewing the mesh via VNC
The add-on allows you to access the underlying deCONZ application running on
a remote desktop via VNC. It allows you to view the ZigBee mesh (which can
be really helpful when debugging network issues), but also gives you access
to tons of advanced features.

To enable it:

Set a port number for VNC in the "Network" configuration section of the
add-on and hit "SAVE". Advised is to use port 5900, but any other port above
5900 works as well.
Set a VNC password in the add-on configuration and hit "SAVE".
Restart the add-on.
To access it you need a VNC Viewer application.

If you are using macOS, you are in luck, since VNC is built-in. Open the
spotlight search and enter: vnc://hassio.local:5900

Upgrading RaspBee and ConBee firmware
This add-on allows you to upgrade your firmware straight from the Phoscon
web interface with ease.

Go to "Settings -> Gateway" and click the upgrade button.

However, some USB sticks (like the Aeotec Z-Wave sticks), can interfere with
the upgrade process, causing the firmware upgrade to fail silently. If you end
up with the same firmware version as before you started the upgrade, consider
unplugging the other sticks and try again.

If that is still not working, try upgrading the firmware manually.

Advanced debug output control
Hidden controls are added to the add-on to allow control over the debug
output of deCONZ. The following options are hidden, but can be added to
the add-on configuration:

dbg_info
dbg_aps
dbg_otau
dbg_zcl
dbg_zdp
These options require a number that represents the log level.

Example add-on config with dbg_aps enabled on log level 1:

{
  "device": "/dev/ttyUSB0",
  "vnc_password": "",
  "dbg_aps": 1
}
Configuration
Add-on configuration:

{
  "device": "/dev/ttyAMA0"
}
Option: device (required)
The device address of your ConBee/RaspBee.

If you're using Hass.io you may find the correct value for this on the
Hass.io -> System -> Host system -> Hardware page.

In most cases this is one of the following:

"/dev/ttyUSB0"
"/dev/ttyAMA0"
"/dev/ttyACM0"
Known issues and limitations
Use at least 2.5A power supply for your Raspberry Pi! This avoids strange behavior when using this add-on.
Support
Got questions?

You have several options to get them answered:

The Home Assistant Discord Chat Server.
The Home Assistant Community Forum.
Join the Reddit subreddit in /r/homeassistant
In case you've found an bug, please open an issue on our GitHub.
