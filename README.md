
# NTP WebSocket Client Integer Lobby Setup  

This tool enables integer-based multiplayer functionality using an APInt IO server.  

### Requirements (Raspberry Pi 5)  
To set up the integer multiplayer system, you need the following:  
- **Integer Server:** [GitHub Repository](https://github.com/EloiStree/2025_01_01_HelloMetaMaskPushToIID)  
- **NTP Server:** [GitHub Repository](https://github.com/EloiStree/2025_01_01_HelloPiOsNtpServer)  
- **Client (Python/JavaScript):** [GitHub Repository](https://github.com/EloiStree/2025_03_14_WsNtpIntRaspberryPiClientPyJS)  

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
    "be.elab.wsmetamaskauth": "https://github.com/EloiStree/OpenUPM_WsMetaMaskAuth.git"
```

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
  - [`be.elab.wsmetamaskauth`](https://github.com/EloiStree/OpenUPM_WsMetaMaskAuth.git)  
