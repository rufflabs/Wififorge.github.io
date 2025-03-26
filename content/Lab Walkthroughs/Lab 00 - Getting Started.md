# Summary
In this lab we are just learning how to navigate the tool **Wifi Forge**. Wifi Forge is a framework built on top of the open source software mininet that provides *wireless* wifi labs! The labs in this course teach a variety of common wifi hacking concepts. 

# Navigating the Main Menu
Wifi Forge should already be launched on the machine. If it is, you should see the following menu: 

![[Pasted image 20250317233428.png]]

If this menu is not present on your machine, launch WifiForge with the following command. If the command does not work - ask for help.

```
sudo python3 /Wifi-Forge/Framework/WifiForge.py
```

Use the **UP** and **DOWN** arrow keys to navigate the menu. Press **ENTER** to select a lab. After selecting a lab, allow for up to 15 seconds for the network to build. When finished, your screen will appear similar to the following: 

![[2025-03-17_23-18.png]]
*Ignore any older commands that appear in the terminal - these are just for housekeeping*

This is the interface you will have to work with for the majority of labs. Note the name of the node (Attacker) in the upper left hand corner of the terminal window. This is the name of a simulated machine on the network. The attacking machine is always called "Attacker" and will normally be the only machine you interact with. However, a handful of labs may require you to simulate user behavior or have multiple CLIs on the same machine. In these cases, you will be provided with a multi-pane view similar to the one below: 

![[Pasted image 20250317233007.png]]
*pane borders are more clearly defined in the actual lab - they don't show up well in the screenshot tool.*

Note here that the screen allows access to two different hosts: your attacking machine "**Attacker**" and one victim "**host_machine**". You can access the terminals of each of these machines by clicking within the pane that represents the host you want to interact with. 

# Done with the Lab?
To exit a lab, simply type ```main_menu``` into any of the terminal panes to return to the main menu. 

NEXT LAB: [[Lab 01 - Bettercap Recon]]
