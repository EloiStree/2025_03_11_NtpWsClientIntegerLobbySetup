# 🤗 Welcome 🧙‍♂️

I am designing some tool to make multiplayer game and network application using only integer and time.

I have two type of server:
- Trusted: We don't care of security
- Asymmertical: You user to authentify.

Server is design to be hosted on Raspberry Pi. 

If you like the concept, you are in the right place.  
Feel free to ping me 🐿️ at anytime on [Discord](https://discord.gg/uKwNN2ECJH).  

----------------

# Trusted version: NTP WebSocket Client Integer Lobby Setup 

This tool enables integer-based multiplayer lobby using an APInt IO server.   
_(Trusted is a version that don't use password and/or authentification.)_  



### **Understanding the Index Integer Date (IID) Concept**  
The lobby system is based on the **Index Integer Date (IID)** model:  

- **Index** – A unique identifier used as an asymmetric key for authentication on the WebSocket server.  
- **Integer** – The numerical values shared between computers/games in the shared lobby.  
- **Date** – If all players use the same NTP server, game actions can be synchronized **without needing network communication**.  
More about: [Index Integer Date (IID)](https://github.com/EloiStree/IID)  


### **Default Project Configuration**  

By default, the project is set up to use:  
- **NTP Server:** `raspberrypi.local`  
- **IID APInt Server:** `ws://raspberrypi.local:4625/`
- **Ports**:
  - **22**: SSH connection to your PI  
  - **123**: Network Time Protocole
  - **4625**: Trusted server to make the lobby
  - **8080**: Flask server to debug and be found by Ip scan
  - **4615**: Assymetrical server (if you want authentification server)
  - **3615**: UDP Trusted relay (if you need UDP relay)


### Requirements (Raspberry Pi 4/5)  

To set up the integer multiplayer system, you need the following:  
- **PI Connect and SSH**: https://github.com/EloiStree/HelloRaspberryPiDevKitCM5/issues/13
  - Let's configure your PI connection to debug online
  - Let's add public key to debug from SSH connection 
- **NTP Server:** https://github.com/EloiStree/2025_01_01_HelloPiOsNtpServer
  - Let's give a time protocole to the PI for player/user to have the same clock 
- **Flask:** https://github.com/EloiStree/2025_01_01_FlaskServerAPIntIID/
  - Let's install a small website to debug the PI state
  - Let's add a page 8080/hostname that return the current name of the PI for when mDNS don't work
  - Let's add a page 8080/unique-id that return the current hardware id of the PI when you want `that PI` 
- **Trusted Integer Server:** https://github.com/EloiStree/2025_01_01_TrustedServerAPIntIID 
  - Let's intall a websocket that only do one thing, take less that 16 bytes packages and broadcast it to all connected player/user. 
- Optional: **Assymetrical Integer Server:** https://github.com/EloiStree/2025_01_01_AsymmetricServerAPIntIID
  - This server is when you want to make mutualized with authentification Integer Lobby on a PI Online
  - More about it in the [ReadMe.md](https://github.com/EloiStree/2025_01_01_AsymmetricServerAPIntIID/blob/main/README.md)


### Untiy3D

I designed the Unity3D Client around RSA assymetrical key.
So if you don't use them, my code still need those understanding of what is RSA and Asym key.
You can copy those code in your `package.json` in the Unity3D project folder.

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


### **Client Int Lobby Setup**  

Drag and drop the `Client Int Lobby DNS Fail Safe Trusted` prefab into your scene.  

This prefab includes an NTP client that connects to a server without authentication, relaying sent and received integers to a static class accessible in Unity3D.  
- If the DNS fails, it scans for `$"http://{ipv4}:8080/hostname"` to check if the device is a `raspberrypi`.  
- It utilizes port `4625` for an unencrypted, trusted WebSocket server that simply relays received integers (≤16 bytes).    
I use IID instead of text for a reason: **prevent hacks, crashes, bandwidth bottlenecks, text is "slow"**.      

#### Usage:  
- **Receiving Integers:** Use `StaticIntMono_ListenIntegerReceivedFromServer` to get integers from other players.  
- **Sending Integers:** Use `StaticIntMono_PushUnityToServer` to send integers to other players in the lobby.  

#### Custom Connection Support (UDP, WebTransport, RAM Tunneling, UNET, etc.):  
- Use `StaticIntMono_PushServerToUnity` to send integers to players.  
- Use `StaticIntMono_ListenIntegerSendToServer` to listen for outgoing integers from players and relay them.



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


####  `package.json` Example for a Lobby 

If you want ane example of how you can use the tools to make a intger multiplayer game.
You can add those package and add the sample scene of "Int Lobby Sample space Ship"

```
    "be.elab.basicactioniid": "https://github.com/EloiStree/OpenUPM_BasicActionIID.git",
    "be.elab.iid": "https://github.com/EloiStree/OpenUPM_IID.git",
    "be.elab.intlobby": "https://github.com/EloiStree/2025_03_11_IntegerLobbyFacade.git",
    "be.elab.intlobbysampleship": "https://github.com/EloiStree/2025_03_18_IntLobbySampleSpaceship.git",
    "be.elab.developernote": "https://github.com/EloiStree/2024_08_09_DeveloperNote.git",
    "be.elab.intmapping": "https://github.com/EloiStree/2025_03_16_IntegerMapping.git",

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
- A tool that allows to create documentation on what integer do what in the app/game in Unity3D
  - [Integer Mapping](https://github.com/EloiStree/2025_03_16_IntegerMapping.git) 


####  `package.json` Example for a Outer Wild style game

- https://github.com/EloiStree/2025_02_17_TimePercentInterface
  - Look at the Solar System Demo (you need to add the offset yourself)
- https://github.com/EloiStree/2025_02_22_TimePercentInterfaceBezier
  - Allows to make object follow Bezier curve base on the time going on as percent with NTP server
- https://github.com/EloiStree/2025_02_17_UnityMacroSRT.git
  - Allows to store event that need to happens at a precise timing in a SRT format (used for subtitle in video).
     
If you don't want to make complicated code, trigger from NTP event some Unity3D Timeline.
(Not code yet)

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
