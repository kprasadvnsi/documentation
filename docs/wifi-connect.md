# Add a WIFI Connection

Their are several ways to add  a WIFI Connection, depending on your preference. These ways are listed below:
All of these methods  assume that your board has WiFI, and/or a USB wifi adapter
#

## Method 1: `nmtui`
The `nmtui` tool, or `NetworkManager Text User Interface`, is a component of NetworkManager, and can be used (in a TUI style) to add and select a WIFi network.
Nmtui is, however, also capable of managing other types of networks, and depending on your circumstances may not be the best option. This leads is to...

## Method 2: `nmcli `
`nmcli`, like `nmtui`, is a component of networkmanager, and has the same features.

To connect to a wireless network, follow these instructions:

### 1: list wireless networks
To show a list of wi-fi networks, at a sudo-enabled terminal, enter:

```sudo nmcli device wifi list```

The output should look like this:

```

*  SSID               MODE     CHAN     RATE          SIGNAL      BARS      SECURITY
*  Orange-Pi-wifi     Infra     11       54 Mbit/s      100         ▂▄▆█     --
   A13-Wifi           Infra      6       54 Mbit/s       30          ▂___    WPA1 WPA2
   2WIRE533           Infra     10       54 Mbit/s       44          ▂▄__    WPA1 WPA2


```

### Connect to network (without password)
If your network does *not* require a password (I.E. is not secure), you can connect to it with the following command:


``` sudo nmcli device wifi connect 'WiFINetworkName' ifname wlan0 ```

Give it a few seconds to connect, then verify your connectivity with:

``` ip -br address show dev wlan0 ```

### Connect to network (with password)
However, if your network does require a password (as most should), you may connect to it with the following command, replacing `WiFiNetworkName` and `WiFiNetworkPass` with your network name and password, respectively:



``` sudo nmcli device wifi connect 'WiFiNetworkName' password 'WifiPass' ifname wlan0 ```

Please do keep in mind that you will *not* receive feedback while typing the *password* component of the above command, for security reasons.

Once again, verify your connectivity with:

``` ip -br address show dev wlan0 ```

## Tips and Tricks

* When using `nmcli` and connecting to a wi-fi network who's eSSID (name) is not broadcast (I.E. hidden) you will need to add `hidden yes` to your `connect` command.
* If a `wlan0` interface does *not* exist on the system, please verify that your board *has* wifi (either via an internal adapter or over USB), that firmware is loaded (if necesary), that your kernel supports wifi, and that it does not have another name (such as wlp3s0). For more info on firmware, please see [wifi troubleshooting](wifi-troubleshooting.md)

* If the `ip -br address show dev wlan0` command does *not* show an IPV4 address, please verify that a DHCP server is present on your network. If not, please refer to [static network configuration](static-network.md) for more information.

