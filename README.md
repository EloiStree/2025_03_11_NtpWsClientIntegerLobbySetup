# 🤗 Welcome, Adventurer! 🧙‍♂️  

I'm working on a tool for building multiplayer games and network applications using only integers and time.  

There are two types of servers:  
- **Trusted**: No security concerns.  
- **Asymmetrical**: Users authenticate themselves.  

The server is designed to run on a Raspberry Pi.  

If this sounds interesting to you, you're in the right place!  
Feel free to reach out 🐿️ anytime on [Discord](https://discord.gg/uKwNN2ECJH).



----------------

# Trusted version: NTP WebSocket Client

This tool enables integer-based multiplayer lobby using an `APInt.IO` server.   

### **Understanding the Index Integer Date (IID) Concept**  

The lobby system is based on the **Index Integer Date (IID)** model:  

- **Index** – A unique identifier used as an asymmetric key for authentication on the WebSocket server.  
- **Integer** – The numerical values exchanged between computers/games in the shared lobby.  
- **Date** – All players use UTC time in milliseconds, synchronized with a time protocol server.  

Learn more: [Index Integer Date (IID)](https://github.com/EloiStree/IID)


### **Default Project Configuration**  

The project comes pre-configured with the following setup:  

- **NTP Server:** `raspberrypi.local`  
- **IID APInt Server:** `ws://raspberrypi.local:4625/`  

- **Ports:**  
  - **22** – SSH access to your Raspberry Pi  
  - **123** – Network Time Protocol (NTP)  
  - **4625** – Trusted server for lobby management  
  - **8080** – Flask server for debugging and IP discovery  

- **Optional Ports:**  
  - _**4615** – Asymmetrical server (for authentication, if needed)_  
  - _**3615** – UDP Trusted relay (for pushing UDP data to the WebSocket server)_  
  - _**7000** – UDP Broadcaster (for sending integers to other applications on the device)_  

### **Requirements (Raspberry Pi 4/5)**  

To set up the integer-based multiplayer system, you'll need the following:  

- **PI Connection & SSH**: [Setup Guide](https://github.com/EloiStree/HelloRaspberryPiDevKitCM5/issues/13)  
  - Configure your Raspberry Pi for remote debugging.  
  - Add a public key for SSH-based debugging.  

- **NTP Server**: [Setup Guide](https://github.com/EloiStree/2025_01_01_HelloPiOsNtpServer)  
  - Synchronize the Pi's clock to ensure all players/users have the same time reference.  

- **Flask Debug Server**: [Installation Guide](https://github.com/EloiStree/2025_01_01_FlaskServerAPIntIID/)  
  - Set up a lightweight web server for debugging the Pi’s state.  
  - Add a page at `8080/hostname` to retrieve the Pi’s name (useful when mDNS fails).  
  - Add a page at `8080/unique-id` to return the Pi’s hardware ID.  

- **Trusted Integer Server**: [Setup Guide](https://github.com/EloiStree/2025_01_01_TrustedServerAPIntIID)  
  - Install a WebSocket server that processes compact (≤16 bytes) data packets and broadcasts them to all connected players/users.  

- **Optional: Asymmetrical Integer Server**: [Installation Guide](https://github.com/EloiStree/2025_01_01_AsymmetricServerAPIntIID)  
  - Required if you need an authenticated, shared integer-based lobby for online multiplayer.  
  - More details in the [README](https://github.com/EloiStree/2025_01_01_AsymmetricServerAPIntIID/blob/main/README.md).  


### **Unity3D**  

> From the start, I've designed the Unity3D client around RSA (ECC) asymmetric keys 😅.  
> Even if you don’t use them, my code still relies on an understanding of RSA asymmetric keys.  
> Some packages are unnecessary for the `Trusted Server` but still required.

You can copy the following code into your `package.json` file within your Unity3D project folder.

#### `package.json` Dependencies  
```json
    "be.elab.asymsigner": "https://github.com/EloiStree/OpenUPM_AsymmetricalClipboardCoaster.git",
    "be.elab.intlobby": "https://github.com/EloiStree/2025_03_11_IntegerLobbyFacade.git",
    "be.elab.intlobbysetup": "https://github.com/EloiStree/2025_03_11_NtpWsClientIntegerLobbySetup.git",
    "be.elab.intmapping": "https://github.com/EloiStree/2025_03_16_IntegerMapping.git",
    "be.elab.pbit4096b58pkcs1sha256": "https://github.com/EloiStree/OpenUPM_pBit4096B58Pkcs1SHA256.git",
    "be.elab.tickcollection": "https://github.com/EloiStree/OpenUMP_TickCollection.git",
    "be.elab.unityfetchoffsetntp": "https://github.com/EloiStree/OpenUPM_UnityFetchOffsetNTP.git",
    "be.elab.wsclientiid": "https://github.com/EloiStree/OpenUPM_NtpWsClientIID.git",
    "be.elab.wsasymauth": "https://github.com/EloiStree/OpenUPM_WsAsymAuth.git",
    "be.elab.developernote": "https://github.com/EloiStree/2024_08_09_DeveloperNote.git",
    "be.elab.scanpioffline": "https://github.com/EloiStree/2025_03_26_ScanForRaspberryPi.git",
```

**mDNS Fail Safe**: Apparently Quest don't handle mDNS of the Rasbpberry PI
So I install Flask Server on Pi then scan for LAN IP `$"http://{ipv4}:8080/hostame"` when DNS failed


### **Client Integer Lobby Setup**  

Simply drag and drop the **"Client Int Lobby DNS Fail Safe Trusted"** prefab into your scene.  

This prefab includes an NTP client that connects to a server without authentication, forwarding received and sent integers to a static class accessible in Unity3D.  

- If DNS resolution fails, it scans `http://{ipv4}:8080/hostname` to verify if the device is a `raspberrypi`.  
- If multiple Raspberry Pis are in use (e.g., in a classroom setting), you can scans `http://{ipv4}:8080/unique-id` instead to identify the correct device.  
- Uses port `4625` to communicate with an unencrypted, trusted WebSocket server that relays received integers (≤16 bytes).  

I use IID instead of text for a reason: **to prevent hacks, crashes, KISS concept, and bandwidth issues—text are "slow."**  

#### Usage:  
- **Receiving Integers:** Use `StaticIntMono_ListenIntegerReceivedFromServer` to get integers from other players.  
- **Sending Integers:** Use `StaticIntMono_PushUnityToServer` to send integers to other players in the lobby.  

#### Custom Connection Support (UDP, WebTransport, RAM Tunneling, UNET, etc.):  
- Use `StaticIntMono_PushServerToUnity` to send integers to players.  
- Use `StaticIntMono_ListenIntegerSendToServer` to listen for outgoing integers from players and relay them.


### Test your code with the Flask project
- On Flask code call : http://raspberrypi.local:8080/trusted-client  
  - Page code: https://github.com/EloiStree/2025_01_01_FlaskServerAPIntIID/blob/main/www/trusted/RunClient.html  
  - Host on GitHub:  https://eloistree.github.io/2025_01_01_FlaskServerAPIntIID/www/trusted/RunClient.html  

_(Note you need to disable secure page on the browser)_

### Package explained
- **Lobby System with Drag-and-Drop Sample & Prefab**  
  - [`be.elab.intlobbysetup`](https://github.com/EloiStree/2025_03_11_NtpWsClientIntegerLobbySetup.git)  
- **Asymmetrical Authentication & Signing**  
  - Enables login via an asymmetrical cryptographic key that can be copied and pasted.  
  - [`be.elab.asymsigner`](https://github.com/EloiStree/OpenUPM_AsymmetricalClipboardCoaster.git)  
- **Integer Lobby Multiplayer Abstraction**  
  - Simplifies the creation of integer-based multiplayer games.  
  - [`be.elab.intlobby`](https://github.com/EloiStree/2025_03_11_IntegerLobbyFacade.git)  
- **Integer Mapping Documentation Storage (Optional)**  
  - Helps manage integer-based data structures within the project.  
  - [`be.elab.intmapping`](https://github.com/EloiStree/2025_03_16_IntegerMapping.git)  
- **RSA 4096 Authentication for Unity3D**  
  - Required for secure authentication.  
  - [`be.elab.pbit4096b58pkcs1sha256`](https://github.com/EloiStree/OpenUPM_pBit4096B58Pkcs1SHA256.git)  
- **Rapid Prototyping Toolkit**  
  - Used for quick execution of actions on `Awake`, `Enable`, and `Input` events.  
  - [`be.elab.tickcollection`](https://github.com/EloiStree/OpenUMP_TickCollection.git)  
- **NTP-Based Time Synchronization**  
  - Ensures game time is synced across players.  
  - [`be.elab.unityfetchoffsetntp`](https://github.com/EloiStree/OpenUPM_UnityFetchOffsetNTP.git)  
- **NTP & WebSocket RSA Setup for APInt**
  - Handles WebSocket and RSA authentication with APInt.  
  - [`be.elab.wsclientiid`](https://github.com/EloiStree/OpenUPM_NtpWsClientIID.git)  
- **WebSocket Connection Management with Asymmetrical Keys**  
  - Maintains an active connection and handless reconnections automatically.  
  - [`be.elab.wsasymauth`](https://github.com/EloiStree/OpenUPM_WsAsymAuth)  
- **Scan Raspberry Pi Offline
  - Allows to find Raspberry Pi when the lobby is offline on LAN on Quest3
  - [`be.elab.scanpioffline`](https://github.com/EloiStree/2025_03_26_ScanForRaspberryPi.git)


## **`package.json` Examples**  

### **Example for a Lobby System**  

If you want to create an integer-based multiplayer game, you can add the following packages to your `package.json`. Then, use the **"Int Lobby Sample Space Ship"** scene as a starting point.  

```json
    "be.elab.basicactioniid": "https://github.com/EloiStree/OpenUPM_BasicActionIID.git",
    "be.elab.iid": "https://github.com/EloiStree/OpenUPM_IID.git",
    "be.elab.intlobby": "https://github.com/EloiStree/2025_03_11_IntegerLobbyFacade.git",
    "be.elab.intlobbysampleship": "https://github.com/EloiStree/2025_03_18_IntLobbySampleSpaceship.git",
    "be.elab.developernote": "https://github.com/EloiStree/2024_08_09_DeveloperNote.git",
    "be.elab.intmapping": "https://github.com/EloiStree/2025_03_16_IntegerMapping.git"
```

### **Package Breakdown**  
- **Associating integers with actions:**  
  - [OpenUPM Basic Action IID](https://github.com/EloiStree/OpenUPM_BasicActionIID)  
  - Requires the IID system:  
    - [OpenUPM IID](https://github.com/EloiStree/OpenUPM_IID.git)  

- **Creating an integer-based lobby game:**  
  - Sample: [Integer Lobby Sample Spaceship](https://github.com/EloiStree/2025_03_18_IntLobbySampleSpaceship)  
  - Requires: [Integer Lobby Facade](https://github.com/EloiStree/2025_03_11_IntegerLobbyFacade.git)  

- **Additional utilities:**  
  - **Exporting integers with compressed data:** [OpenUPM Push Generic IID](https://github.com/EloiStree/OpenUPM_PushGenericIID.git)  
  - **Mapping integers to their functions in the app/game:** [Integer Mapping](https://github.com/EloiStree/2025_03_16_IntegerMapping.git)  

---

### **Example for an Outer Wilds-Style Game**  

If you want to create a time-based system similar to *Outer Wilds*, consider these packages:  

- **[Time Percent Interface](https://github.com/EloiStree/2025_02_17_TimePercentInterface)**  
  - Includes a Solar System Demo (requires manual time offset adjustment).  

- **[Time Percent Interface Bezier](https://github.com/EloiStree/2025_02_22_TimePercentInterfaceBezier)**  
  - Allows objects to follow a Bezier curve based on time progression (synchronized with an NTP server).  

- **[Unity Macro SRT](https://github.com/EloiStree/2025_02_17_UnityMacroSRT.git)**  
  - Enables scheduling events at precise times using **SRT format** (commonly used for subtitles in videos).  

If you prefer a simpler approach, you can trigger Unity3D **Timelines** based on NTP events _(not coded yet)_.


----------------

### OTHER NOTE

#### Control a Meross Switch with Unity3D

- https://github.com/EloiStree/2024_12_13_IntegerToMerossFromPython

#### Control a Govee Light with Unity3D
 
- https://github.com/EloiStree/2025_03_19_IntegerToGoveeFromPython

#### Discord and Twitch Chat

I have a code that allows to use Bot on Twitch and Discord:
More about it on [https://apint.io](https://apint.io)

Don't forget to set your user and mail on the Pi Git 😉:
```
git config --global pull.rebase false 
git config --global user.name "Ano Nymous"  
git config --global user.email AnoNymous@gamil.com  
```

Find APInt services install on the Pi:
```
cd /etc/systemd/system
ls apint*
```



-------------

Note for PI Zero: 
- dont use Zero on USB of your computer, it don't provide enought current.


---------------------------------

Log without the `config` file
```
ssh -i ~/.ssh/eloistree_all_pi root@raspberrypi5dk1.local
```
