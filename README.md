
# Trusted version: NTP WebSocket Client Integer Lobby Setup 

This tool enables integer-based multiplayer lobby using an APInt IO server.   
_(Trusted is a version that don't use password and/or authentification.)_  



### **Understanding the Index Integer Date (IID) Concept**  
The lobby system is based on the **Index Integer Date (IID)** model:  

- **Index** – A unique identifier used as an asymmetric key for authentication on the WebSocket server.  
- **Integer** – The numerical values shared between computers/games in the shared lobby.  
- **Date** – If all players use the same NTP server, game actions can be synchronized **without needing network communication**.  

### **Default Project Configuration**  
By default, the project is set up to use:  
- **NTP Server:** `raspberrypi.local`  
- **IID APInt Server:** `ws://raspberrypi.local:4625/`
_(4625: Trusted server - 4615: Assymetrical server - 3615: UDP Trusted relay)_


### Requirements (Raspberry Pi 4/5)  

To set up the integer multiplayer system, you need the following:  
- **PI Connect and SSH**: https://github.com/EloiStree/HelloRaspberryPiDevKitCM5/issues/13
- **NTP Server:** https://github.com/EloiStree/2025_01_01_HelloPiOsNtpServer
- **Flask:** https://github.com/EloiStree/2025_01_01_FlaskServerAPIntIID/  
- **Integer Server:** https://github.com/EloiStree/2025_01_01_TrustedServerAPIntIID




### **Client Int Lobby Setup**  

Drag and drop the `Client Int Lobby DNS Fail Safe Trusted` prefab into your scene.  

- Use `StaticIntMono_ListenIntegerReceivedFromServer` to **receive** integers from other players.  
- Use `StaticIntMono_PushUnityToServer` to **send** integers to other players in the lobby.  

If setting up a custom connection:  
- Forward received integers from other players to `StaticIntMono_PushServerToUnity`.  
- Forward integers sent by the current player from `StaticIntMono_ListenIntegerSendToServer` to your system.


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
    "be.elab.scanpioffline": "https://github.com/EloiStree/2025_03_26_ScanForRaspberryPi.git",

```

**DNS Fail Safe**: Apparently Quest don't handle mDNS.   
Meaning that if you are working with DNS of a LAN Raspberry PI.  
What we do for those who host they own home server.  
You need to scan for LAN IP `$"http://{ipv4}:8080/hostame"`  


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
  - Maintains an active connection and handless reconnections automatically.  
  - [`be.elab.wsasymauth`](https://github.com/EloiStree/OpenUPM_WsAsymAuth)  
- **Scan Raspberry Pi Offline
  - Allows to find Raspberry Pi when the lobby is offline on LAN on Quest3
  - [`be.elab.scanpioffline`](https://github.com/EloiStree/2025_03_26_ScanForRaspberryPi.git)


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




####  `package.json` Example for a Outer Wild style game

- https://github.com/EloiStree/2025_02_17_TimePercentInterface
  - Look at the Solar System Demo (you need to add the offset yourself)

If you don't want to make complicated code, trigger from NTP event some Unity3D Timeline.
(Code not done yet)

----------------

# OTHER NOTE

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

---------------------------------

# Old tutorrial on the Assymetrical version before reforge of the code to make ETH and MetaMask les focused in the project.

## If you want a server with assymetrical authentification

[![image](https://github.com/user-attachments/assets/e4ce2614-0e97-470b-b7ff-e9b656a9809f)](https://youtu.be/7vQYGOoEILQ)  
https://youtu.be/7vQYGOoEILQ  
