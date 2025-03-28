

# How to use ?
[![image](https://github.com/user-attachments/assets/e4ce2614-0e97-470b-b7ff-e9b656a9809f)](https://youtu.be/7vQYGOoEILQ)  
https://youtu.be/7vQYGOoEILQ  


If you like the tool, you can send me a beer:
- https://buymeacoffee.com/apintio
  
Or buy some Raspberry PI equipement on Amazon:   
- https://github.com/EloiStree/HelloInput/issues?q=hardware  
- https://github.com/EloiStree/HelloRaspberryPiDevKitCM5
  
The code is under ["Pizza License"🍕](https://github.com/EloiStree/License)  

----------------

# NTP WebSocket Client Integer Lobby Setup  

This tool enables integer-based multiplayer functionality using an APInt IO server.  

### Requirements (Raspberry Pi 4/5)  
To set up the integer multiplayer system, you need the following:  
- **NTP Server:** [GitHub Repository](https://github.com/EloiStree/2025_01_01_HelloPiOsNtpServer)  
- **Integer Server:** [GitHub Repository](https://github.com/EloiStree/2025_01_01_HelloMetaMaskPushToIID)  
- **Client (Python/JavaScript/flask):** [GitHub Repository](https://github.com/EloiStree/2025_03_14_WsNtpIntRaspberryPiClientPyJS)  

> Note: To setup your Raspberry PI, you want a SSH and Pi Connect access.
> Find here a tutorial on the topic: [https://github.com/EloiStree/HelloRaspberryPiDevKitCM5/issues/13](https://github.com/EloiStree/HelloRaspberryPiDevKitCM5/issues/13)

### **Client Int Lobby Setup**  
Drag and drop the `Client Int Lobby` prefab into your scene.  

- Use `StaticIntLobbyMono_ListenLobby` to **listen** for integers sent by other players.  
- Use `StaticIntLobbyMono_PushToLobby` to **send** integers to other players in the lobby.  

### **Understanding the Index Integer Date (IID) Concept**  
The lobby system is based on the **Index Integer Date (IID)** model:  

- **Index** – A unique identifier used as an asymmetric key for authentication on the WebSocket server.  
- **Integer** – The numerical values shared between computers/games in the shared lobby.  
- **Date** – If all players use the same NTP server, game actions can be synchronized **without needing network communication**.  

### **Default Project Configuration**  
By default, the project is set up to use:  
- **NTP Server:** `raspberrypi.local`  
- **IID APInt Server:** `ws://raspberrypi.local:4615/`  

If you're using the **default image configuration**, the server address is **`raspberrypi.local`**.  
For the **online default server**, use **`apint.ddns.net`**.

### **Security and Authentication**  
This tool is designed to eliminate the need for a database with emails and passwords. To enable a lobby, you must **add a public key** to the APInt server.  

There are **two types of authentication**:  

1. **RSA Only (`pBit4096B58Pkcs1SHA256` format)**  
   - Works well but is **not suitable for eSports** because losing the key means **it cannot be recovered**.  

2. **ETH-backed RSA (using MetaMask for Letter Mark authentication)**  
   - Uses MetaMask as a **backup solution**, allowing an RSA key to perform actions on its behalf.  
   - If your RSA key is stolen, you can still **prove ownership** of the `Index` to the admin via MetaMask.  



### Included Tools  
This setup integrates multiple packages:  

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

```

DNS Fail Safe: Apparently Quest don't handle mDNS.   
Meaning that if you are working with DNS of a LAN Raspberry PI.  
What we don in this projet for those who host they own home server.  
You need to scan for LAN IP.  
https://github.com/EloiStree/2025_03_26_ScanForRaspberryPi  


### Features  
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
  - Maintains an active connection and handles reconnections automatically.  
  - [`be.elab.wsasymauth`](https://github.com/EloiStree/OpenUPM_WsAsymAuth)  



####  `package.json` Example for a Lobby 

```
    "be.elab.basicactioniid": "https://github.com/EloiStree/OpenUPM_BasicActionIID.git",
    "be.elab.iid": "https://github.com/EloiStree/OpenUPM_IID.git",
    "be.elab.intlobby": "https://github.com/EloiStree/2025_03_11_IntegerLobbyFacade.git",
    "be.elab.intlobbysampleship": "https://github.com/EloiStree/2025_03_18_IntLobbySampleSpaceship.git",
    "be.elab.developernote": "https://github.com/EloiStree/2024_08_09_DeveloperNote.git",

```
- Enables associating integers with actions:  
  - [OpenUPM Basic Action IID](https://github.com/EloiStree/OpenUPM_BasicActionIID)  
  - Requires IID to function:  
    - [OpenUPM IID](https://github.com/EloiStree/OpenUPM_IID.git)  

- A sample demonstrating how to create an integer-based lobby game:  
  - [Integer Lobby Sample Spaceship](https://github.com/EloiStree/2025_03_18_IntLobbySampleSpaceship)  
  - Requires the Integer Lobby Facade:  
    - [Integer Lobby Facade](https://github.com/EloiStree/2025_03_11_IntegerLobbyFacade.git)  

- A toolbox for exporting integers with compressed data:  
  - [OpenUPM Push Generic IID](https://github.com/EloiStree/OpenUPM_PushGenericIID.git)




----------------

# Also

## Control a Meross Switch with Unity3D

- https://github.com/EloiStree/2024_12_13_IntegerToMerossFromPython

## Control a Govee Light with Unity3D
 
- https://github.com/EloiStree/2025_03_19_IntegerToGoveeFromPython


Don't forget the Git:
```
git config --global pull.rebase false 
git config --global user.name "Ano Nymous"  
git config --global user.email AnoNymous@gamil.com  
```


Find service:

```
cd /etc/systemd/system
ls apint*
```

