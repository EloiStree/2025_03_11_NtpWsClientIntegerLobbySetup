- SSH and Connect PI tutorials:
  - https://github.com/EloiStree/HelloRaspberryPiDevKitCM5/issues/11
  - https://github.com/EloiStree/HelloRaspberryPiDevKitCM5/issues/13 


Video showing every step of the install on the Raspberry Pi and a bit how to use it.
[![image](https://github.com/user-attachments/assets/7ba64cb5-93da-4ace-b9fc-ec67e8184b7b)](https://youtu.be/JWaKbI9fHVI)
https://youtu.be/JWaKbI9fHVI

Pi5 : https://www.amazon.com.be/-/en/SC1112-Raspberry-Pi-5-8Gb/dp/B0CK2FCG1K/ref=pd_ci_mcx_mh_mcx_views_0_image?pd_rd_w=cajIc&content-id=amzn1.sym.68af92c7-3d62-4bb8-8b86-c0819078d251%3Aamzn1.symc.ca948091-a64d-450e-86d7-c161ca33337b&pf_rd_p=68af92c7-3d62-4bb8-8b86-c0819078d251&pf_rd_r=GAX033J1CZ0RF9104BS7&pd_rd_wg=yjJjc&pd_rd_r=63e29968-2db7-41d5-8b50-6ee7d207297c&pd_rd_i=B0CK2FCG1K

Zero: https://www.amazon.com.be/s?k=zero+raspberry+pi&i=electronics&crid=23HNVLRLDGRPO&sprefix=zero+raspberry+pi%2Celectronics%2C74&ref=nb_sb_noss_2

What do We need: https://youtu.be/JWaKbI9fHVI?t=134

`raspberrypi.local:123`
`ws://raspberrypi.local:4625`
`http://raspberrypi.local:8080/hostname`


We need to install Raspberry Pi Imager:
![image](https://github.com/user-attachments/assets/e268fdc2-625a-457f-9991-b06330ffd8ed)
https://www.raspberrypi.com/software/
https://youtu.be/JWaKbI9fHVI?t=189

Select the PI: https://youtu.be/JWaKbI9fHVI?t=213
Select the OS: https://youtu.be/JWaKbI9fHVI?t=221
Edit the Setting: https://youtu.be/JWaKbI9fHVI?t=232
raspberrypi.local
Admin:root and Wifi:raspberrypi.local
Services SSH in password mode

While it intalls: let's generate the key:
https://youtu.be/JWaKbI9fHVI?t=288

In window power shell generate the key
https://youtu.be/JWaKbI9fHVI?t=344
```
cd ~/.ssh/
ssh-keygen
```
Give it the name you want pikey or name_all_pi

Now you have private and public key.

Let go on the pi check what he is doing:
[![image](https://github.com/user-attachments/assets/8e382345-605b-4720-94aa-f8568162b9fe)](https://youtu.be/JWaKbI9fHVI?t=382)
https://youtu.be/JWaKbI9fHVI?t=382


Let's ping him: https://youtu.be/JWaKbI9fHVI?t=443
`ping raspberrypi.local`


Let's try to connect to it;https://youtu.be/JWaKbI9fHVI?t=466
[![image](https://github.com/user-attachments/assets/c73939fa-2ced-4a2a-9632-5d4dddec2d57)](https://youtu.be/JWaKbI9fHVI?t=466)
https://youtu.be/JWaKbI9fHVI?t=466

We need to set the RPI Conenct to remote control the device.
https://youtu.be/JWaKbI9fHVI?t=504
Set root and password

https://youtu.be/JWaKbI9fHVI?t=532
`sudo apt install rpi-conenct-lite``   

https://youtu.be/JWaKbI9fHVI?t=562
```  
loginctl enable-linger
rpi-connect on
rpi-conenct signin
```  
Create a account on pi connect and add the verify device
[![image](https://github.com/user-attachments/assets/d242d0a1-fbac-49c7-9817-32589c94bb1f)](https://youtu.be/JWaKbI9fHVI?t=635)
https://connect.raspberrypi.com/sign-in
https://connect.raspberrypi.com/verify/COPYIDHERE

Connect to the PI to add the SSH public key:
https://youtu.be/JWaKbI9fHVI?t=652
```
cd ~/.ssh/
ssh-keygen
start .
start pikey.pub 
```

copy the public key in 
```
sudo nano ~/.ssh/authorized_keys
sudo service ssh restart

```


Essayons de nous connecté:  
https://youtu.be/JWaKbI9fHVI?t=747  
```
ssh -i ~/.ssh/pikey root@raspberrypi
```

Installons visual studio code:
https://code.visualstudio.com
https://youtu.be/JWaKbI9fHVI?t=766



Install Remote SSH:
[![image](https://github.com/user-attachments/assets/0d9f622e-6525-4199-8056-b8b5b1590388)](https://youtu.be/JWaKbI9fHVI?t=787)

https://youtu.be/JWaKbI9fHVI?t=787

Créer un fichier config:
https://youtu.be/JWaKbI9fHVI?t=794
```

~/.ssh/config
```
```
Host raspberrypi
  Hostname raspberrypi.local
  user Root
  IdentityFile C:\...\.ssh\pikey
```

Connect to the pi with Remote ssh:
https://youtu.be/JWaKbI9fHVI?t=865


Press F1 and ask to connect ssh to raspberrypi.local
[![image](https://github.com/user-attachments/assets/2e580f7c-1b1a-446c-b155-eb31484970b4)](https://youtu.be/JWaKbI9fHVI?t=918)
https://youtu.be/JWaKbI9fHVI?t=918



Open terminal:  
[![image](https://github.com/user-attachments/assets/a3fd4642-451c-42e1-91fb-fe77264190a4)](https://youtu.be/JWaKbI9fHVI?t=959)
https://youtu.be/JWaKbI9fHVI?t=959


Let's udate the PI:
```
sudo apt update
sudo apt upgrade -y
```

Let's open the port of the PI app we are going to use:
https://youtu.be/JWaKbI9fHVI?t=1148
```
sudo apt install ufw -y
sudo ufw allow 22/tcp
sudo ufw allow 8080/tcp
sudo ufw allow 4625/tcp
sudo ufw allow 4615/tcp
sudo ufw allow 123/udp
sudo ufw allow 123/tcp
sudo ufw allow 3615/udp
```

We need git to work.

https://git-scm.com
```
sudo apt install git-all
```
https://youtu.be/JWaKbI9fHVI?t=1197

https://youtu.be/JWaKbI9fHVI?t=1258
```
sudo apt install python3
```

https://youtu.be/JWaKbI9fHVI?t=1289
```
sudo apt install python3-pip
```

GitHub of NTP: https://github.com/EloiStree/2025_01_01_HelloPiOsNtpServer

Let's check for the NTP server now :)
We clone the documentation:
https://youtu.be/JWaKbI9fHVI?t=1312

https://youtu.be/JWaKbI9fHVI?t=1357
```
git clone https://github.com/EloiStree/2025_01_01_HelloPiOsNtpServer.git /git/ntp_server/
sudo apt install ntp -y
sudo nano /etc/ntp.conf
```
Copy in the `ntp.conf`
https://youtu.be/JWaKbI9fHVI?t=1427
```
server 0.be.pool.ntp.org iburst
server 1.be.pool.ntp.org iburst
server 2.be.pool.ntp.org iburst
server 3.be.pool.ntp.org iburst
restrict 0.0.0.0 mask 0.0.0.0 nomodify notrap
```


Let's set time and finish the install:
https://youtu.be/JWaKbI9fHVI?t=1461
```
sudo timedatectl set-timezone Europe/Brussels
ntpq -p
sudo systemctl enable ntp
sudo systemctl restart ntp
sudo apt install ufw -y
sudo ufw allow 123/udp
```

Don't forget a small  `pip install ntplib --` for later

Test on the computer if you can access the NTP server:
[![image](https://github.com/user-attachments/assets/0fcb63ec-bff5-4c9a-b4b2-b92973f64f9b)](https://youtu.be/JWaKbI9fHVI?t=1542)
Code: https://github.com/EloiStree/2025_01_01_HelloPiOsNtpServer/blob/main/CheckNtp.py
https://youtu.be/JWaKbI9fHVI?t=1542


Let's install the Flask server
https://youtu.be/JWaKbI9fHVI?t=1585
https://github.com/EloiStree/2025_01_01_FlaskServerAPIntIID/

Let's copy past to create server and timer:
![image](https://github.com/user-attachments/assets/3c7af0aa-f2b0-40f2-8e75-9d9b66403665)
https://youtu.be/JWaKbI9fHVI?t=1627

Then reload service and deamon:
[![image](https://github.com/user-attachments/assets/5067614c-2696-4ec2-a49b-3232ff073f85)](https://youtu.be/JWaKbI9fHVI?t=1697
)
https://youtu.be/JWaKbI9fHVI?t=1697



You will need some python module:
https://youtu.be/JWaKbI9fHVI?t=1835
```
pip install ntplib flask markdown --break-system-packages
```

Let check that it works: https://youtu.be/JWaKbI9fHVI?t=1856
[![image](https://github.com/user-attachments/assets/628e87af-959b-47c1-909a-abcaeffc2b90)](http://raspberrypi.local:8080:/services)  
- http://raspberrypi.local:8080:/services  
- http://raspberrypi.local:8080:/ipv4  
- http://raspberrypi.local:8080:/hostname  
- http://raspberrypi.local:8080:/unique-id  
- http://raspberrypi.local:8080:/push-iid  
  - https://youtu.be/JWaKbI9fHVI?t=2041 
- http://raspberrypi.local:8080:/reboot

Make sure that the service is enable and restable:
https://youtu.be/JWaKbI9fHVI?t=1937

There is a markdown option on the flask for documentation:
[![image](https://github.com/user-attachments/assets/1fe1b0f1-a593-4e64-b024-11e925183265)](https://youtu.be/JWaKbI9fHVI?t=1993
)
https://youtu.be/JWaKbI9fHVI?t=1993



We have pi NTP Flask, let's install the websocket server for integer.

Let's clone and copy past:
GitHub: 
[![image](https://github.com/user-attachments/assets/c36894cb-a235-4f80-96c2-3589fb5d4675)](https://youtu.be/JWaKbI9fHVI?t=2136)
https://youtu.be/JWaKbI9fHVI?t=2136
https://github.com/EloiStree/2025_01_01_TrustedServerAPIntIID

Install the Python Module required:
https://youtu.be/JWaKbI9fHVI?t=2163
```
pip install tornado requests --break-system-packages
```

When the server and module are install it should be runnable:
https://youtu.be/JWaKbI9fHVI?t=2362

Let's check that it run:
https://youtu.be/JWaKbI9fHVI?t=2460


Ok ready for Unity3D ?

Let's copy all the package needed, core and sample:
https://github.com/EloiStree/2025_03_11_NtpWsClientIntegerLobbySetup
```
   "be.elab.asymsigner": "https://github.com/EloiStree/OpenUPM_AsymmetricalClipboardCoaster.git",
    "be.elab.developernote": "https://github.com/EloiStree/2024_08_09_DeveloperNote.git",
    "be.elab.intlobby": "https://github.com/EloiStree/2025_03_11_IntegerLobbyFacade.git",
    "be.elab.intlobbysetup": "https://github.com/EloiStree/2025_03_11_NtpWsClientIntegerLobbySetup.git",
    "be.elab.intmapping": "https://github.com/EloiStree/2025_03_16_IntegerMapping.git",
    "be.elab.pbit4096b58pkcs1sha256": "https://github.com/EloiStree/OpenUPM_pBit4096B58Pkcs1SHA256.git",
    "be.elab.scanpioffline": "https://github.com/EloiStree/2025_03_26_ScanForRaspberryPi.git",
    "be.elab.tickcollection": "https://github.com/EloiStree/OpenUMP_TickCollection.git",
    "be.elab.timepercent": "https://github.com/EloiStree/2025_02_17_TimePercentInterface.git",
    "be.elab.unityfetchoffsetntp": "https://github.com/EloiStree/OpenUPM_UnityFetchOffsetNTP.git",
    "be.elab.wsasymauth": "https://github.com/EloiStree/OpenUPM_WsAsymAuth.git",
    "be.elab.wsclientiid": "https://github.com/EloiStree/OpenUPM_NtpWsClientIID.git",

    "be.elab.basicactioniid": "https://github.com/EloiStree/OpenUPM_BasicActionIID.git",
    "be.elab.iid": "https://github.com/EloiStree/OpenUPM_IID.git",
    "be.elab.intlobbysampleship": "https://github.com/EloiStree/2025_03_18_IntLobbySampleSpaceship.git",    
"com.unity.inputsystem": "1.13.0",
```

Let's copy the package to manifest.json
[![image](https://github.com/user-attachments/assets/729625ae-c3b9-4b29-842f-cb53daa38b1b)](https://youtu.be/JWaKbI9fHVI?t=2513)
https://youtu.be/JWaKbI9fHVI?t=2513

Let's import the demo of the prefab to use:
[![image](https://github.com/user-attachments/assets/e7080023-46c0-4c27-8837-9724cc28c043)](https://youtu.be/JWaKbI9fHVI?t=2553)
https://youtu.be/JWaKbI9fHVI?t=2553


Check that time percent interface is in the project if you want to sync action with time in game:
https://youtu.be/JWaKbI9fHVI?t=2598


Listen ToOnlyOnceOffset will allows to push the offset between your computer and the PI from the singleton in the scene that will load the difference.
[![image](https://github.com/user-attachments/assets/74f617c9-9884-47db-9d80-831ec5249430)](https://youtu.be/JWaKbI9fHVI?t=2647)
https://youtu.be/JWaKbI9fHVI?t=2647

But to find the raspberrypi we ened to check the 8080 and so we need to allows it.
[![image](https://github.com/user-attachments/assets/f5200aad-dfea-4697-9811-2479fb9a062e)](https://youtu.be/JWaKbI9fHVI?t=2695)
https://youtu.be/JWaKbI9fHVI?t=2697


DNS Fail Safe that allow to look for hostname of the pi with Flask:
[![image](https://github.com/user-attachments/assets/073b9a39-e250-4bbe-99bc-e260f79899c0)](https://youtu.be/JWaKbI9fHVI?t=2753)
https://youtu.be/JWaKbI9fHVI?t=2753


IPV4 To Ports will generate the url of the NPT, WS and HTTP from the find IP (given by DNS or Scan IP)
[![image](https://github.com/user-attachments/assets/d929afcc-e4a9-4e1d-afe2-73cdae634d54)](https://youtu.be/JWaKbI9fHVI?t=2786)  
https://youtu.be/JWaKbI9fHVI?t=2786


Give he url to the face for the WS and NPT client that know the hard code behind it:
[![image](https://github.com/user-attachments/assets/1451b46e-f3d1-431f-8f2b-1a729f29a107)](https://youtu.be/JWaKbI9fHVI?t=2801)
https://youtu.be/JWaKbI9fHVI?t=2801

The two most important script is 
`NtpOffsetOnlyOnceMono` and `WsConnectToAsymServerMono`

Check that both works:
https://youtu.be/JWaKbI9fHVI?t=2855

We can for example now set object with offset of the NPT server to element in game to sync them with the pi and so other player:
https://youtu.be/JWaKbI9fHVI?t=2896


But we want to send integer and received not just sync time:
[![image](https://github.com/user-attachments/assets/af94e011-bbe8-454b-8b88-5d17b6163362)](https://youtu.be/JWaKbI9fHVI?t=2948)
https://youtu.be/JWaKbI9fHVI?t=2948


Let's show you the connection between the hardcode of sending and receiving the integer and give it to a static integer face ^^... This part of the video is a bit messy. I will do a better video on the topic focusing on using and not explaining.

"He hide part of the code"
https://youtu.be/JWaKbI9fHVI?t=3009

If you just want to observer what is send and what is received you can use:
[StaticIntMono_ListenIntegerReceivedFromServer](https://youtu.be/JWaKbI9fHVI?t=3182)
[StaticIntMono_ListenIntegerSentToServer](https://youtu.be/JWaKbI9fHVI?t=3185)
![image](https://github.com/user-attachments/assets/09ae6fe3-edc5-4dde-8eff-7fba35bb676d)


Let's import the SpaceShip Sample of an integer multiplayer lobby. https://youtu.be/JWaKbI9fHVI?t=3254

(If package.json bug, just push update:)
[![image](https://github.com/user-attachments/assets/fa761420-d754-4fc9-a048-40cb254baa2e)](https://youtu.be/JWaKbI9fHVI?t=3283)
https://youtu.be/JWaKbI9fHVI?t=3283


When you copy the sample in your scene with the client.
The facade code that use a Static C# class wil allow to link them without effort:
[![image](https://github.com/user-attachments/assets/fc5a055d-54e9-4f4c-9a9f-0a65f0696213)](https://youtu.be/JWaKbI9fHVI?t=3353)
https://youtu.be/JWaKbI9fHVI?t=3353


What would look like a game where you need to kills bugs:
[![image](https://github.com/user-attachments/assets/2d62a149-90be-4a07-900f-fce0c7a3e1db)](https://youtu.be/JWaKbI9fHVI?t=3384)
https://youtu.be/JWaKbI9fHVI?t=3384


Change color of the light:
[![image](https://github.com/user-attachments/assets/4ceaa343-ace3-4420-aadb-3a858c37e055)](https://youtu.be/JWaKbI9fHVI?t=3438)
https://youtu.be/JWaKbI9fHVI?t=3449

Int Int with listen to integer to static facade
Int Out will push integer to static facade
[![image](https://github.com/user-attachments/assets/2de9d2cb-7cfd-43e8-9e18-ff7da1832fac)](https://youtu.be/JWaKbI9fHVI?t=3468)
https://youtu.be/JWaKbI9fHVI?t=3468


Send and received in Unity is not supper face and praticle.
That could be nice if we could just make a HTML Javascript page ?
[![image](https://github.com/user-attachments/assets/9387ea43-92e2-4587-824b-96047ed7d1eb)
](https://youtu.be/JWaKbI9fHVI?t=3477)
https://youtu.be/JWaKbI9fHVI?t=3477

[![image](https://github.com/user-attachments/assets/6d2796f6-1696-4ee2-a76a-73c2efb28e1f)](https://youtu.be/JWaKbI9fHVI?t=3504)
https://youtu.be/JWaKbI9fHVI?t=3504
[http://raspberrypi.local:8080/trusted-client](http://raspberrypi.local:8080/trusted-client)

Change the time , color, shield, start scene..  
[![image](https://github.com/user-attachments/assets/43abe24d-7bf7-4c2e-ac21-aa51e5821664)](https://youtu.be/JWaKbI9fHVI?t=3610)  
https://youtu.be/JWaKbI9fHVI?t=3610  

Load a Game, Lobby and other scene with integer for example:
[![image](https://github.com/user-attachments/assets/cfdd25a9-9fa9-4052-86e7-e046e42ea37a)](https://youtu.be/JWaKbI9fHVI?t=3638)
https://youtu.be/JWaKbI9fHVI?t=3638


And tada 😅 !!!

Now you know the basic of how to install and use a Trusted IID APInt server 🧙‍♂️🤗

[![image](https://github.com/user-attachments/assets/a144e7ab-f58a-484d-aeb9-95e02acf3a39)](https://youtu.be/JWaKbI9fHVI?t=3712)
https://youtu.be/JWaKbI9fHVI?t=3712








 




-------------


Setup your git account on the your computer if not already done.
```
git config --global pull.rebase false 
git config --global user.name "Hello World"  
git config --global user.email "helloworl@gmail.com"  
```

sudo raspi-config
ping raspberrypi


sudo rpi
sudo apt install rpi-connect-lite
https://connect.raspberrypi.com/verify/8SF4-TYBZ

`sudo nano ~/.ssh/authorized_keys`
Ou 
```
ssh-copy-id -i ~/.ssh/pikey.pub root@raspberrypi
ssh-copy-id -i ~/.ssh/eloistree_all_pi.pub root@raspberrypi
```

```
sudo apt update 
sudo apt upgrade -y 
```

Command to push the key if you did not do it during the install:
```
ssh -i ~/.ssh/pikey root@raspberrypi
ssh -i ~/.ssh/eloistree_all_pi.pub root@raspberrypi
```


