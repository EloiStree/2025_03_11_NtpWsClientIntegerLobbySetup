

### SSH and Connect Pi Tutorials:
- [GitHub Issue #11](https://github.com/EloiStree/HelloRaspberryPiDevKitCM5/issues/11)
- [GitHub Issue #13](https://github.com/EloiStree/HelloRaspberryPiDevKitCM5/issues/13)

### Video Tutorial:
A step-by-step video showing the installation on Raspberry Pi and basic usage.  
[![Watch the Video](https://github.com/user-attachments/assets/7ba64cb5-93da-4ace-b9fc-ec67e8184b7b)](https://youtu.be/JWaKbI9fHVI)  
🔗 [YouTube Link](https://youtu.be/JWaKbI9fHVI)

### Raspberry Pi Links:
- **Raspberry Pi 5:** [Amazon Link](https://www.amazon.com.be/-/en/SC1112-Raspberry-Pi-5-8Gb/dp/B0CK2FCG1K/)
- **Raspberry Pi Zero:** [Amazon Search](https://www.amazon.com.be/s?k=zero+raspberry+pi&i=electronics)

### Required Software:
- **Raspberry Pi Imager:**  
  ![Image](https://github.com/user-attachments/assets/e268fdc2-625a-457f-9991-b06330ffd8ed)  
  🔗 [Download Here](https://www.raspberrypi.com/software/)  
  🔗 [Installation Guide](https://youtu.be/JWaKbI9fHVI?t=189)

---

### Setting Up Raspberry Pi:
1. **Select the Pi:** [Guide](https://youtu.be/JWaKbI9fHVI?t=213)
2. **Select the OS:** [Guide](https://youtu.be/JWaKbI9fHVI?t=221)
3. **Edit Settings:** [Guide](https://youtu.be/JWaKbI9fHVI?t=232)  
   - `raspberrypi.local`
   - Admin: `root`
   - WiFi: `raspberrypi.local`
   - Enable SSH (password mode)

4. **Generate SSH Key:**
   - **In Windows PowerShell:**  
     ```
     cd ~/.ssh/
     ssh-keygen
     ```
   - Name it `pikey` or any custom name.  
   - You now have a **private and public key**.

5. **Check Raspberry Pi Status:** [Guide](https://youtu.be/JWaKbI9fHVI?t=382)

---

### Connecting to Raspberry Pi:
- **Ping the device:**  
  ```
  ping raspberrypi.local
  ```
  🔗 [Ping Guide](https://youtu.be/JWaKbI9fHVI?t=443)

- **SSH into Raspberry Pi:**  
  ```
  ssh -i ~/.ssh/pikey root@raspberrypi
  ```
  🔗 [Connection Guide](https://youtu.be/JWaKbI9fHVI?t=466)

- **Install Remote Control:**  
  ```
  sudo apt install rpi-connect-lite
  ```
  🔗 [Setup Guide](https://youtu.be/JWaKbI9fHVI?t=504)

- **Enable Remote Login:**  
  ```
  loginctl enable-linger
  rpi-connect on
  rpi-connect signin
  ```
  🔗 [Sign-in Guide](https://youtu.be/JWaKbI9fHVI?t=562)

- **Verify Device:**  
  🔗 [Create a Pi Connect Account](https://connect.raspberrypi.com/sign-in)  
  🔗 [Verify Your Device](https://connect.raspberrypi.com/verify/COPYIDHERE)

- **Add SSH Public Key to Raspberry Pi:**  
  ```
  cd ~/.ssh/
  ssh-keygen
  start .
  start pikey.pub
  ```
  Copy the public key into:  
  ```
  sudo nano ~/.ssh/authorized_keys
  sudo service ssh restart
  ```
  🔗 [SSH Key Guide](https://youtu.be/JWaKbI9fHVI?t=652)

---

### Installing Essential Software:
- **Visual Studio Code:** [Download Here](https://code.visualstudio.com)  
  🔗 [Setup Guide](https://youtu.be/JWaKbI9fHVI?t=766)

- **Remote SSH Extension:**  
  🔗 [Installation Guide](https://youtu.be/JWaKbI9fHVI?t=787)

- **Create SSH Config File:**  
  ```
  ~/.ssh/config
  ```
  ```
  Host raspberrypi
    Hostname raspberrypi.local
    User root
    IdentityFile C:\...\.ssh\pikey
  ```
  🔗 [Config Guide](https://youtu.be/JWaKbI9fHVI?t=794)

---

### Updating and Configuring Raspberry Pi:
- **Update & Upgrade:**  
  ```
  sudo apt update
  sudo apt upgrade -y
  ```
  🔗 [Update Guide](https://youtu.be/JWaKbI9fHVI?t=959)

- **Open Required Ports:**  
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
  🔗 [Firewall Guide](https://youtu.be/JWaKbI9fHVI?t=1148)

- **Install Git & Python:**  
  ```
  sudo apt install git-all
  sudo apt install python3
  sudo apt install python3-pip
  ```
  🔗 [Git Install](https://youtu.be/JWaKbI9fHVI?t=1197)  
  🔗 [Python Install](https://youtu.be/JWaKbI9fHVI?t=1289)

---

### Setting Up an NTP Server:
- **Clone the Documentation:**  
  ```
  git clone https://github.com/EloiStree/2025_01_01_HelloPiOsNtpServer.git /git/ntp_server/
  sudo apt install ntp -y
  sudo nano /etc/ntp.conf
  ```
  🔗 [NTP Guide](https://youtu.be/JWaKbI9fHVI?t=1357)

- **Configure `ntp.conf`:**  
  ```
  server 0.be.pool.ntp.org iburst
  server 1.be.pool.ntp.org iburst
  server 2.be.pool.ntp.org iburst
  server 3.be.pool.ntp.org iburst
  restrict 0.0.0.0 mask 0.0.0.0 nomodify notrap
  ```
  🔗 [NTP Config Guide](https://youtu.be/JWaKbI9fHVI?t=1427)

- **Finalize Installation:**  
  ```
  sudo timedatectl set-timezone Europe/Brussels
  ntpq -p
  sudo systemctl enable ntp
  sudo systemctl restart ntp
  sudo apt install ufw -y
  sudo ufw allow 123/udp
  pip install ntplib
  ```
  🔗 [Final Steps](https://youtu.be/JWaKbI9fHVI?t=1461)

---

### Installing Flask & WebSocket Server:
- **Install Flask Server:**  
  🔗 [GitHub Repo](https://github.com/EloiStree/2025_01_01_FlaskServerAPIntIID)  
  🔗 [Setup Guide](https://youtu.be/JWaKbI9fHVI?t=1585)

- **Install Required Python Modules:**  
  ```
  pip install ntplib flask markdown --break-system-packages
  ```
  🔗 [Module Install Guide](https://youtu.be/JWaKbI9fHVI?t=1835)

- **Install WebSocket Server:**  
  🔗 [GitHub Repo](https://github.com/EloiStree/2025_01_01_TrustedServerAPIntIID)  
  ```
  pip install tornado requests --break-system-packages
  ```
  🔗 [Setup Guide](https://youtu.be/JWaKbI9fHVI?t=2163)

---

### Unity3D Integration:
- **Clone Unity Packages:**  
  🔗 [GitHub Repo](https://github.com/EloiStree/2025_03_11_NtpWsClientIntegerLobbySetup)  
  🔗 [Setup Guide](https://youtu.be/JWaKbI9fHVI?t=2513)

- **Import Prefabs & Test Multiplayer Lobby:**  
  🔗 [Guide](https://youtu.be/JWaKbI9fHVI?t=2553)

-









**Ok, ready for Unity3D?**  

Let's copy all the necessary packages, core, and sample:  
🔗 [GitHub Repository](https://github.com/EloiStree/2025_03_11_NtpWsClientIntegerLobbySetup)  

```json
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
   "com.unity.inputsystem": "1.13.0"
```

### Steps to set up:

1. **Copy the package list** into `manifest.json`  
   🎥 [Video](https://youtu.be/JWaKbI9fHVI?t=2513)

2. **Import the demo prefab**  
   🎥 [Video](https://youtu.be/JWaKbI9fHVI?t=2553)

3. **Check that the Time Percent Interface is in the project**  
   🎥 [Video](https://youtu.be/JWaKbI9fHVI?t=2598)

4. **Listen to `ToOnlyOnceOffset` to sync time with Raspberry Pi**  
   🎥 [Video](https://youtu.be/JWaKbI9fHVI?t=2647)

5. **Ensure port 8080 is allowed** for Raspberry Pi discovery  
   🎥 [Video](https://youtu.be/JWaKbI9fHVI?t=2697)

6. **DNS Fail-Safe**: Find the Pi's hostname with Flask  
   🎥 [Video](https://youtu.be/JWaKbI9fHVI?t=2753)

7. **IPv4 to Ports**: Generate URLs for NTP, WS, and HTTP  
   🎥 [Video](https://youtu.be/JWaKbI9fHVI?t=2786)

8. **Pass URLs to the facade for WS & NTP clients**  
   🎥 [Video](https://youtu.be/JWaKbI9fHVI?t=2801)

### Key Scripts:

- `NtpOffsetOnlyOnceMono`
- `WsConnectToAsymServerMono`  
  🎥 [Check they work](https://youtu.be/JWaKbI9fHVI?t=2855)

Now, you can **sync objects in-game with the NTP server**, aligning them with the Raspberry Pi and other players.  
🎥 [Video](https://youtu.be/JWaKbI9fHVI?t=2896)

But we want to send and receive **integers**, not just time sync!  
🎥 [Video](https://youtu.be/JWaKbI9fHVI?t=2948)

### Debugging Integer Exchange:

- Observe **received** values:  
  📌 `StaticIntMono_ListenIntegerReceivedFromServer`  
  🎥 [Video](https://youtu.be/JWaKbI9fHVI?t=3182)

- Observe **sent** values:  
  📌 `StaticIntMono_ListenIntegerSentToServer`  
  🎥 [Video](https://youtu.be/JWaKbI9fHVI?t=3185)

9. **Import the SpaceShip Multiplayer Sample**  
   🎥 [Video](https://youtu.be/JWaKbI9fHVI?t=3254)

10. **If `package.json` has issues, push update**  
    🎥 [Video](https://youtu.be/JWaKbI9fHVI?t=3283)

11. **Use Static C# classes to link the facade and client effortlessly**  
    🎥 [Video](https://youtu.be/JWaKbI9fHVI?t=3353)

### Possible Applications:

- **Bug-killing game concept**  
  🎥 [Video](https://youtu.be/JWaKbI9fHVI?t=3384)

- **Change light colors dynamically**  
  🎥 [Video](https://youtu.be/JWaKbI9fHVI?t=3449)

- **Integer input/output with a static facade**  
  🎥 [Video](https://youtu.be/JWaKbI9fHVI?t=3468)

12. **Why not use an HTML/JavaScript page for easier sending/receiving?**  
    🎥 [Video](https://youtu.be/JWaKbI9fHVI?t=3477)

13. **Control time, color, shields, or start the scene via HTTP**  
    🔗 [http://raspberrypi.local:8080/trusted-client](http://raspberrypi.local:8080/trusted-client)  
    🎥 [Video](https://youtu.be/JWaKbI9fHVI?t=3610)

14. **Load game, lobby, and other scenes using integers**  
    🎥 [Video](https://youtu.be/JWaKbI9fHVI?t=3638)

---

🎉 **And that's it!** Now you know the basics of setting up and using a **Trusted IID APInt Server**! 🧙‍♂️🚀  
🎥 [Final Overview](https://youtu.be/JWaKbI9fHVI?t=3712)



 



-------------

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


