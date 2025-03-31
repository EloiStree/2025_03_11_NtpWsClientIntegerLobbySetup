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
- http://raspberrypi.local:8080:/reboot

Make sure that the service is enable and restable:
https://youtu.be/JWaKbI9fHVI?t=1937

There is a markdown option on the flask for documentation:
[![image](https://github.com/user-attachments/assets/1fe1b0f1-a593-4e64-b024-11e925183265)](https://youtu.be/JWaKbI9fHVI?t=1993
)
https://youtu.be/JWaKbI9fHVI?t=1993

















-------------

## Generate a SSH key and Git

Install Git Bash from git default tool:

[![image](https://github.com/user-attachments/assets/3614da4b-5efe-474b-930e-1b952e311d55)](https://git-scm.com)
https://git-scm.com

![image](https://github.com/user-attachments/assets/29c91293-6ad1-4dfe-a481-9d6f1b8919d9)
![image](https://github.com/user-attachments/assets/89e41427-a8c9-44e5-a0c9-c08216902681)

Setup your git account on the your computer if not already done.
```
git config --global pull.rebase false 
git config --global user.name "Hello World"  
git config --global user.email "helloworl@gmail.com"  
```


Put the SD car on your Pi and prepare a keyboard and mouse (if you use UI Desktop version)
Configure all what is ask to you in the PI configuration.
Not that you can skip the wifi setup and the update part.
- Wifi is already setup
- Update can be done during the reste of the tutorial.


Now you need to generate a SSH key on Window and push it to the PI

Launch `Git Bash`

- Type: `cd ~/.ssh`
- Type: `ssh-keygen``
- Give it a name: `pikey` (for example)
- Skip the password
- Next Next
![image](https://github.com/user-attachments/assets/9d1a92fe-e164-40c0-9d08-f6ee61251c7b)

Now you have a public and private key on the folder User/.ssh/



# Fetch Imager 
[![image](https://github.com/user-attachments/assets/bf72e778-328f-4660-9121-8da3b3cb3fee)](https://www.raspberrypi.com/software/)
https://www.raspberrypi.com/software/

Select the PI you have:
![image](https://github.com/user-attachments/assets/5e004b9d-7d4c-4856-88e5-46090cfae617)

You want the UI Desktop 64 Bit version for less performence but more easy debug:
![image](https://github.com/user-attachments/assets/09c92d65-d965-4109-935b-866b29dcdb45)

Edit the image:
![image](https://github.com/user-attachments/assets/a7b27a64-baa6-4f00-88bb-28ef9fcec0c4)


Give him the name raspberrypi.local
 ![image](https://github.com/user-attachments/assets/17772edf-4548-45b7-9e14-ff9203d61ae3)

Set the admin/password to user, `root`:
![image](https://github.com/user-attachments/assets/9fd333f2-382b-4d28-8619-7e2f7f9fbf3f)

Set the Wifi if you have it, I use a specific wifi for it to be able to take it with me when I move and use it offline.
My Wifi router name is raspberrypi.local and raspberrypi.local_5G
If you use zero, use the 2G

![image](https://github.com/user-attachments/assets/41367cf8-571a-43d4-bf49-2e6db791db06)

Key the password the time to install what you need:
![image](https://github.com/user-attachments/assets/9203a5f4-87da-4660-b311-8f5899f222b5)


Copy your ssh key in the ssh form
![image](https://github.com/user-attachments/assets/b40c8934-ce62-41f5-9047-cc184b0e38b7)


Install and wait the SD card to be ready:
![image](https://github.com/user-attachments/assets/2d36fc36-2224-44b9-85dd-5af4950c36bb)


Connect to your root user of the pi in Git Bash:  
![image](https://github.com/user-attachments/assets/50ca1bb7-947d-4e07-966a-c8504291c0ef)


if pi don't connect directly to Wifi:
su root
sudo raspi-config
![image](https://github.com/user-attachments/assets/2cf078b1-795c-4873-9c7a-024e431f55c4)
![image](https://github.com/user-attachments/assets/f6d4d489-ea3e-4220-a6a6-0dc09f246cfd)
![image](https://github.com/user-attachments/assets/32fa6363-d8f6-4a7e-a422-6f7da374ac60)
![image](https://github.com/user-attachments/assets/7f31bda5-e72b-435c-b0bb-b5e39366e09a)

Check that the pi exists:
 ping raspberrypi


sudo rpi
sudo apt install rpi-connect-lite
https://connect.raspberrypi.com/verify/8SF4-TYBZ


Add your key:

`sudo nano ~/.ssh/authorized_keys`
Ou 
```
ssh-copy-id -i ~/.ssh/pikey.pub root@raspberrypi
ssh-copy-id -i ~/.ssh/eloistree_all_pi.pub root@raspberrypi
```

Restart SSH:
```
sudo systemctl status ssh
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


