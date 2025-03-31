
- SSH and Connect PI tutorials:
  - [Tutorial 1](https://github.com/EloiStree/HelloRaspberryPiDevKitCM5/issues/11)
  - [Tutorial 2](https://github.com/EloiStree/HelloRaspberryPiDevKitCM5/issues/13)

Video showing every step of the install on the Raspberry Pi and a bit how to use it.
[![image](https://github.com/user-attachments/assets/7ba64cb5-93da-4ace-b9fc-ec67e8184b7b)](https://youtu.be/JWaKbI9fHVI)
[Watch the video](https://youtu.be/JWaKbI9fHVI)

- [Pi5](https://www.amazon.com.be/-/en/SC1112-Raspberry-Pi-5-8Gb/dp/B0CK2FCG1K/ref=pd_ci_mcx_mh_mcx_views_0_image?pd_rd_w=cajIc&content-id=amzn1.sym.68af92c7-3d62-4bb8-8b86-c0819078d251%3Aamzn1.symc)
- [Zero](https://www.amazon.com.be/s?k=zero+raspberry+pi&i=electronics&crid=23HNVLRLDGRPO&sprefix=zero+raspberry+pi%2Celectronics%2C74&ref=nb_sb_noss_2)

What do we need: [Watch the video](https://youtu.be/JWaKbI9fHVI?t=134)

- `raspberrypi.local:123`
- `ws://raspberrypi.local:4625`
- `http://raspberrypi.local:8080/hostname`

We need to install Raspberry Pi Imager:
![image](https://github.com/user-attachments/assets/e268fdc2-625a-457f-9991-b06330ffd8ed)
[Raspberry Pi software](https://www.raspberrypi.com/software/)
[Watch the video](https://youtu.be/JWaKbI9fHVI?t=189)

- [Select the PI](https://youtu.be/JWaKbI9fHVI?t=213)
- [Select the OS](https://youtu.be/JWaKbI9fHVI?t=221)
- [Edit the Setting](https://youtu.be/JWaKbI9fHVI?t=232)
  - raspberrypi.local
  - Admin: root and WiFi: raspberrypi.local
  - Services SSH in password mode

While it installs, let's generate the key:
[Watch the video](https://youtu.be/JWaKbI9fHVI?t=288)

In Windows PowerShell, generate the key:
[Watch the video](https://youtu.be/JWaKbI9fHVI?t=344)
```sh
cd ~/.ssh/
ssh-keygen
```
Give it the name you want, e.g., pikey or name_all_pi

Now you have a private and public key.

Let's check what the Pi is doing:
[![image](https://github.com/user-attachments/assets/8e382345-605b-4720-94aa-f8568162b9fe)](https://youtu.be/JWaKbI9fHVI?t=382)
[Watch the video](https://youtu.be/JWaKbI9fHVI?t=382)

Let's ping it: [Watch the video](https://youtu.be/JWaKbI9fHVI?t=443)
```sh
ping raspberrypi.local
```

Let's try to connect to it: [Watch the video](https://youtu.be/JWaKbI9fHVI?t=466)
[![image](https://github.com/user-attachments/assets/c73939fa-2ced-4a2a-9632-5d4dddec2d57)](https://youtu.be/JWaKbI9fHVI?t=466)
[Watch the video](https://youtu.be/JWaKbI9fHVI?t=466)

We need to set up the RPI Connect to remote control the device.
[Watch the video](https://youtu.be/JWaKbI9fHVI?t=504)
- Set root and password
- [Watch the video](https://youtu.be/JWaKbI9fHVI?t=532)
  ```sh
  sudo apt install rpi-connect-lite
  ```

- [Watch the video](https://youtu.be/JWaKbI9fHVI?t=562)
  ```sh
  loginctl enable-linger
  rpi-connect on
  rpi-connect signin
  ```
- Create an account on Pi Connect and add the verified device
  [![image](https://github.com/user-attachments/assets/d242d0a1-fbac-49c7-9817-32589c94bb1f)](https://youtu.be/JWaKbI9fHVI?t=635)
  [Sign in](https://connect.raspberrypi.com/sign-in)
  [Verify](https://connect.raspberrypi.com/verify/COPYIDHERE)

Connect to the PI to add the SSH public key:
[Watch the video](https://youtu.be/JWaKbI9fHVI?t=652)
```sh
cd ~/.ssh/
ssh-keygen
start .
start pikey.pub
```

Copy the public key in:
```sh
sudo nano ~/.ssh/authorized_keys
sudo service ssh restart
```

Let's try to connect: [Watch the video](https://youtu.be/JWaKbI9fHVI?t=747)
```sh
ssh -i ~/.ssh/pikey root@raspberrypi
```

Install Visual Studio Code:
[Visual Studio Code](https://code.visualstudio.com)
[Watch the video](https://youtu.be/JWaKbI9fHVI?t=766)

Install Remote SSH:
[![image](https://github.com/user-attachments/assets/0d9f622e-6525-4199-8056-b8b5b1590388)](https://youtu.be/JWaKbI9fHVI?t=787)
[Watch the video](https://youtu.be/JWaKbI9fHVI?t=787)

Create a config file: [Watch the video](https://youtu.be/JWaKbI9fHVI?t=794)
```sh
~/.ssh/config
```
```sh
Host raspberrypi
  Hostname raspberrypi.local
  User root
  IdentityFile C:\...\.ssh\pikey
```

Connect to the Pi with Remote SSH:
[Watch the video](https://youtu.be/JWaKbI9fHVI?t=865)

Press F1 and ask to connect SSH to raspberrypi.local
[![image](https://github.com/user-attachments/assets/2e580f7c-1b1a-446c-b155-eb31484970b4)](https://youtu.be/JWaKbI9fHVI?t=918)
[Watch the video](https://youtu.be/JWaKbI9fHVI?t=918)

Open terminal:  
[![image](https://github.com/user-attachments/assets/a3fd4642-451c-42e1-91fb-fe77264190a4)](https://youtu.be/JWaKbI9fHVI?t=959)
[Watch the video](https://youtu.be/JWaKbI9fHVI?t=959)

Let's update the Pi:
```sh
sudo apt update
sudo apt upgrade -y
```

Let's open the ports for the PI app we are going to use:
[Watch the video](https://youtu.be/JWaKbI9fHVI?t=1148)
```sh
sudo apt install ufw -y
sudo ufw allow 22/tcp
sudo ufw allow 8080/tcp
sudo ufw allow 4625/tcp
sudo ufw allow 4615/tcp
sudo ufw allow 123/udp
sudo ufw allow 123/tcp
sudo ufw allow 3615/udp
```

We need Git to work.
[Git SCM](https://git-scm.com)
```sh
sudo apt install git-all
```
[Watch the video](https://youtu.be/JWaKbI9fHVI?t=1197)

[Watch the video](https://youtu.be/JWaKbI9fHVI?t=1258)
```sh
sudo apt install python3
```
[Watch the video](https://youtu.be/JWaKbI9fHVI?t=1289)
```sh
sudo apt install python3-pip
```

GitHub of NTP: [NTP GitHub](https://github.com/EloiStree/2025_01_01_HelloPiOsNtpServer)

Let's check for the NTP server now :)
We clone the documentation:
[Watch the video](https://youtu.be/JWaKbI9fHVI?t=1312)

[Watch the video](https://youtu.be/JWaKbI9fHVI?t=1357)
```sh
git clone https://github.com/EloiStree/2025_01_01_HelloPiOsNtpServer.git /git/ntp_server/
sudo apt install ntp -y
sudo nano /etc/ntp.conf
```
Copy in the `ntp.conf`
[Watch the video](https://youtu.be/JWaKbI9fHVI?t=1427)
```sh
server 0.be.pool.ntp.org iburst
server 1.be.pool.ntp.org iburst
server 2.be.pool.ntp.org iburst
server 3.be.pool.ntp.org iburst
restrict 0.0.0.0 mask 0.0.0.0 nomodify notrap
```

Let's set the time and finish the install:
[Watch the video](https://youtu.be/JWaKbI9fHVI?t=1461)
```sh
sudo timedatectl set-timezone Europe/Brussels
ntpq -p
sudo systemctl enable ntp
sudo systemctl restart ntp
sudo apt install ufw -y
sudo ufw allow 123/udp
```

Don't forget to run `pip install ntplib --` for later.

Test on the computer if you can access the NTP server:
[![image](https://github.com/user-attachments/assets/0fcb63ec-bff5-4c9a-b4b2-b92973f64f9b)](https://youtu.be/JWaKbI9fHVI?t=1542)
[Code](https://github.com/EloiStree/2025_01_01_HelloPiOsNtpServer/blob/main/CheckNtp.py)
[Watch the video](https://youtu.be/JWaKbI9fHVI?t=1542)

Let's install the Flask server:
[Watch the video](https://youtu.be/JWaKbI9fHVI?t=1585)
[Flask Server GitHub](https://github.com/EloiStree/2025_01_01_FlaskServerAPIntIID/)

Let's copy and paste to create the server and timer:
![image](https://github.com/user-attachments/assets/3c7af0aa-f2b0-40f2-8e75-9d9b66403665)
[Watch the video](https://youtu.be/JWaKbI9fHVI?t=1627)

Then reload the service and daemon:
[![image](https://github.com/user-attachments/assets/5067614c-2696-4ec2-a49b-3232ff073f85)](https://youtu.be/JWaKbI9fHVI?t=1697)
[Watch the video](https://youtu.be/JWaKbI9fHVI?t=1697)

You will need some Python modules:
[Watch the video](https://youtu.be/JWaKbI9fHVI?t=1835)
```sh
pip install ntplib flask markdown --break-system-packages
```
Let's check that it works: [Watch the video](https://youtu.be/JWaKbI9fHVI?t=1856)
[![image](https://github.com/user-attachments/assets/628e87af-959b-47c1-909a-abcaeffc2b90)](http://raspberrypi.local:8080:/services)
- [Services](http://raspberrypi.local:8080:/services)
- [IPv4](http://raspberrypi.local:8080:/ipv4)
- [Hostname](http://raspberrypi.local:8080:/hostname)
- [Unique ID](http://raspberrypi.local:8080:/unique-id)
- [Push IID](http://raspberrypi.local:8080:/push-iid)
- [Reboot](http://raspberrypi.local:8080:/reboot)

Make sure that the service is enabled and restartable:
[Watch the video](https://youtu.be/JWaKbI9fHVI?t=1937)

There is a Markdown option on the Flask for documentation:
[![image](https://github.com/user-attachments/assets/1fe1b0f1-a593-4e64-b024-11e925183265)](https://youtu.be/JWaKbI9fHVI?t=1993)
[Watch the video](https://youtu.be/JWaKbI9fHVI?t=1993)

## Generate an SSH Key and Git

Install Git Bash from the Git default tool:
[![image](https://github.com/user-attachments/assets/3614da4b-5efe-474b-930e-1b952e311d55)](https://git-scm.com)
[Git SCM](https://git-scm.com)

![image](https://github.com/user-attachments/assets/29c91293-6ad1-4dfe-a481-9d6f1b8919d9)
![image](https://github.com/user-attachments/assets/89e41427-a8c9-44e5-a0c9-c08216902681)

Set up your Git account on your computer if not already done.
```sh
git config --global pull.rebase false 
git config --global user.name "Hello World"  
git config --global user.email "helloworld@gmail.com"  
```

Put the SD card in your Pi and prepare a keyboard and mouse (if you use the UI Desktop version).
Configure all that is asked of you in the PI configuration.
Note that you can skip the WiFi setup and the update part.
- WiFi is already set up
- Update can be done during the rest of the tutorial

Now you need to generate an SSH key on Windows and push it to the PI.

Launch `Git Bash`
- Type: `cd ~/.ssh`
- Type: `ssh-keygen`
- Give it a name: `pikey` (for example)
- Skip the password
- Next, Next
![image](https://github.com/user-attachments/assets/9d1a92fe-e164-40c0-9d08-f6ee61251c7b)

Now you have a public and private key in the folder User/.ssh/

Fetch Imager 
![image](https://github.com/user-attachments/assets/bf72e778-328f-4660-9121-8da3b3cb3fee)
[Raspberry Pi software](https://www.raspberrypi.com/software/)

Select the PI you have:
![image](https://github.com/user-attachments/assets/5e004b9d-7d4c-4856-88e5-46090cfae617)

You want the UI Desktop 64 Bit version for less performance but easier debugging:
![image](https://github.com/user-attachments/assets/09c92d65-d965-4109-935b-866b29dcdb45)

Edit the image:
![image](https://github.com/user-attachments/assets/a7b27a64-baa6-4f00-88bb-28ef9fcec0c4)

Give it the name raspberrypi.local
![image](https://github.com/user-attachments/assets/17772edf-4548-45b7-9e14-ff9203d61ae3)

Set the admin/password to user, `root`:
![image](https://github.com/user-attachments/assets/9fd333f2-382b-4d28-8619-7e2f7f9fbf3f)

Set the WiFi if you have it. I use a specific WiFi for it to be able to take it with me when I move and use it offline.
My WiFi router name is raspberrypi.local and raspberrypi.local_5G
If you use zero, use the 2G
![image](https://github.com/user-attachments/assets/41367cf8-571a-43d4-bf49-2e6db791db06)

Keep the password the time to install what you need:
![image](https://github.com/user-attachments/assets/9203a5f4-87da-4660-b311-8f5899f222b5)

Copy your SSH key in the SSH form:
![image](https://github.com/user-attachments/assets/b40c8934-ce62-41f5-9047-cc184b0e38b7)

Install and wait for the SD card to be ready:
![image](https://github.com/user-attachments/assets/2d36fc36-2224-44b9-85dd-5af4950c36bb)

Connect to your root user of the PI in Git Bash:  
![image](https://github.com/user-attachments/assets/50ca1bb7-947d-4e07-966a-c8504291c0ef)

If the Pi doesn't connect directly to WiFi:
```sh
su root
sudo raspi-config
```
![image](https://github.com/user-attachments/assets/2cf078b1-795c-4873-9c7a-024e431f55c4)
![image](https://github.com/user-attachments/assets/f6d4d489-ea3e-4220-a6a6-0dc09f246cfd)
![image](https://github.com/user-attachments/assets/32fa6363-d8f6-4a7e-a422-6f7da374ac60)
![image](https://github.com/user-attachments/assets/7f31bda5-e72b-435c-b0bb-b5e39366e09a)

Check that the Pi exists:
```sh
ping raspberrypi
```

```sh
sudo rpi
sudo apt install rpi-connect-lite
```
[Verify](https://connect.raspberrypi.com/verify/8SF4-TYBZ)

Add your key:
```sh
sudo nano ~/.ssh/authorized_keys
```
or 
```sh
ssh-copy-id -i ~/.ssh/pikey.pub root@ras
