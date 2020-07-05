## Cracking WEP

## Perform the following steps prior to step 1, if you're wireless card is giving you issues.

* When putting a card into monitor mode, it will automatically check for interfering processes. It can also be done manually by running the following command:
````
airmon-ng check
````

* Kill interferring processes
````
airmon-ng check kill
````

* Kill the network manager(s) before putting card into monitor mode
````
airmon-ng check kill PID
````

* If started already...disable Monitor Mode
````
airmon-ng stop wlan0mon
````

* Restart Network Manager(s)
````
service network-manager start
````

**1) List All Available Wireless Interace Cards**

* You can do this with two commands: iwconfig or airmon-ng

![](https://github.com/azul-007/Pentesting/blob/master/Wireless/images/list_interfaces.png)

**2) Enable monitor mode on the interace found in step 1**

![](https://github.com/azul-007/Pentesting/blob/master/Wireless/images/monitor_mode.png)

**3) Identify the channel your WEP network is operating on**

* execute iwconfig or airmon-ng to get your wireless interface
* use either BSSID or ESSID.
* The channel number will be listed under the "CH" column.
````
airodump-ng wlan0mon
````
![](https://github.com/azul-007/Pentesting/blob/master/Wireless/images/identify_channel.png)

* Take not of the the MAC, channel and network name of the target AP.
* Test wireless device packet injection.
* If you receive "Injection is working! proceed, else, ensure you're using a compatible wireless card.

**4) Packet Injection**
````
aireplay-ng -c 3 -9 -e <network name> -a <target MAC> <interface>
````

