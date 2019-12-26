# Add a WIFI Connection

Their are convenient ways on how u can add  WIFI Connection.

#

The first method is  via the Software `nmtui`
U just type `nmtui` into your Terminal, then u can easily add a new WIFI Connection via the Interface.

Another method is to use  `nmcli `
first u list the available WIFI Networks.

```nmcli device wifi list```

The output should look like this:

```

*  SSID               MODE     CHAN     RATE          SIGNAL      BARS      SECURITY
*  Orange-Pi-wifi     Infra     11       54 Mbit/s      100         ▂▄▆█     --
   A13-Wifi           Infra      6       54 Mbit/s       30          ▂___    WPA1 WPA2
   2WIRE533           Infra     10       54 Mbit/s       44          ▂▄__    WPA1 WPA2


```


Now u can connect to a  Wifi without Password via:

``` sudo nmcli device wifi connect '(your wifi network name/SSID)' ifname wlan0 ```

and to a Wifi with Password via:

``` udo nmcli device wifi connect '(your wifi network name/SSID)' password '(your wifi password)' ifname wlan0 ```

Keep in mind that u dont get any feedback while u type your Password.

If u have a Wifi with hidden SSID  u need to add `hidden yes ` to the end of the command.


Now u can Check your connection:

```  nmcli connection show --active ```

To test u can now ping Googles DNS Server

``` ping -c 5 8.8.8.8  ```

Congratulations u are now connected to a WIFI Network