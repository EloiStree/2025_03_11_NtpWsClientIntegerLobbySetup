## Video tutorial on **Bookworm** Pi OS

[![image](https://github.com/user-attachments/assets/1e726a16-0b0e-4b21-9607-1f2b3c17ea57)](https://youtu.be/uS1lP0U1d1M?t=63)


[![image](https://github.com/user-attachments/assets/803e6135-c155-4f07-8ff4-5a0ff6eabb83)](https://www.youtube.com/watch?v=mn3I5Xw9chY)  
  
- Latest: https://www.youtube.com/watch?v=mn3I5Xw9chY
- Draft:
  - https://www.youtube.com/watch?v=OHMu-tviMPI
  - https://youtu.be/I5--TX_WUnc


## 0. Install Raspberry Pi Imager

[![image](https://github.com/user-attachments/assets/fe16d5f1-0783-4e7e-82e2-226ef312eb73)](https://www.raspberrypi.com/software/)  
https://www.raspberrypi.com/software/  

## 1. Create an Image on a Disk

- **You can use**:
  - USB 1 or USB 2, but it is very slow.
  - USB 3, which is faster but still not ideal.
  - An SD card, but you will need a USB 3 adapter.
  - The SD card slot on the Dev Kit (if available).  
    - *(Ping me if you want to teach me how to enable it.)*
  - [Raspberry Pi - M.2 NVMe SSD](https://www.raspberrypi.com/products/ssd/) [📦](https://amzn.to/3BZp6ej).  
    - If you choose this, you will need an M.2 NVMe reader:  [📦](https://amzn.to/40ekJFF) .


1. Plug the drive into your computer.
2. Launch the **Raspberry Pi Imager** app.
3. Choose the target device: **Raspberry Pi 5**.
4. Select the operating system:
   - **Raspberry Pi OS 64-bit** (recommended if you plan to use the UI at any point).  
   - **Raspberry Pi OS Lite** (if you only need terminal access).  
5. Select the disk to write the image to (minimum size: 8 GB).
6. Press **Next**.
7. Pre-configure the system:
   - Add a user named `"root"` with your password.
   - Configure the Wi-Fi network and password.
   - Set a hostname (ensure it’s unique to avoid conflicts with other Raspberry Pi devices).
   - Optionally, add an SSH key to the software.  
     - *(Ping me if you want to teach me how to enable it.)*
8. Continue and overwrite the selected disk.

--- 

Let me know if there’s anything else you'd like clarified or expanded!



## 2. **Install Git**  


You can go here: https://git-scm.com
![image](https://github.com/user-attachments/assets/841b7f52-dd0a-48b6-8122-d0b23c0f9fb8)

Choose 64 bit for Windows setup
![image](https://github.com/user-attachments/assets/58d3ec75-61f7-4ead-89a2-ce277d1c7127)

Processed on the Git installation (Next next next)
Git Bash should be installed:
![image](https://github.com/user-attachments/assets/c8491156-b290-4de7-8c84-a3150d003ce0)


## 3. **Generate SSH Key**  
   - Navigate to your SSH folder:  
     ```bash
     mkdir ~/.ssh
     cd ~/.ssh
     ```  
   - Run:  
     ```bash
     ssh-keygen
     ```  
   - Provide a filename for your key (e.g., `eloistree_all_pi`).  
   - Press **Enter** twice to skip the passphrase (if not needed).  
   - Open the directory to check the files:  
     ```bash
     start "" .
     ```  
   - Open `eloistree_all_pi.pub` to copy its contents for later use.  
   - Optionally, view the private key (`eloistree_all_pi`) to understand its structure.  

5. **Sample Public Key Format**  
   ```
   ssh-ed25519 AAAAC3NzaC1lZDI1NTE5AAAAIJ0CEY70lUDsDTNLx+ijwmgbWvjwOSIl67jLn1R29Vkm elois@MSI
   ```

---

### The Pi:  
2. **Install Raspberry Pi OS**  
   - Download the Raspberry Pi Imager: [[Raspberry Pi Software](https://www.raspberrypi.com/software/)](https://www.raspberrypi.com/software/).  
   - Choose your hardware and the **Bookworm OS** (use Desktop if you need a GUI).  
   - Prepare your storage (SD/USB for older Pi models, NVMe for Pi 5 Dev Kit):  
     - Use a USB3 or NVMe card reader if required.  

3. **Configure the OS**  
   - During setup:  
     - Enter the hostname.  
     - Set the default user (`root`) and password (`your_password`).  
     - Configure Wi-Fi.  
     - Ensure SSH is enabled.  
     - Format and write the OS to the storage device.  
   - Insert the storage into the Pi.  
   - Connect a screen and keyboard to finalize configuration.  

4. **Optional: Pi Connect UI Setup**  
   - Follow the official guide if you prefer using a UI, but this document focuses on the console method.  

---

### Quick Checks:  
1. Update and Upgrade:  
   ```bash
   sudo apt update
   sudo apt upgrade
   ```  
3. Verify Python:  
   ```bash
   python --version
   ```  
   - If not installed:  
     ```bash
     sudo apt install python3
     ```  
4. Verify pip:  
   ```bash
   pip --version
   ```  
   - If not installed:  
     ```bash
     sudo apt install python3-pip
     ```  
6. Verify Git:  
   ```bash
   git --version
   ```  
   - If not installed:  
     ```bash
     sudo apt install git-all
     ```  

---

### Pi Connect Setup:  

Full Guide: https://www.raspberrypi.com/documentation/services/connect.html

1. **Install Pi Connect**  
   - Install the tool:  
     ```bash
     sudo apt install rpi-connect
     ```  
     - For console-only use:  
       ```bash
       sudo apt install rpi-connect-lite
       ```  
   - Start the service:  
     ```bash
     systemctl --user start rpi-connect
     loginctl enable-linger
     rpi-connect on
     rpi-connect reload
     ```  

> [Enable user-lingering](https://www.raspberrypi.com/documentation/services/connect.html#enable-remote-shell-at-all-times) to make your device accessible even when your user account isn’t logged in.

2. **Sign In to Pi Connect**  
   - Run:  
     ```bash
     rpi-connect signin
     ```  
   - Visit the provided link ([[Pi Connect Verify](https://connect.raspberrypi.com/verify)](https://connect.raspberrypi.com/verify)) and complete the sign-in process.  
   - If you see **✓ Signed in**, the setup is successful.  

---

### Add Your SSH Key:  
1. On the Pi, switch to the root user:  
   ```bash
   su root
   ```  
2. Open the `authorized_keys` file:  
   ```bash
   sudo nano ~/.ssh/authorized_keys
   ```  
3. Paste your public key (e.g., `ssh-ed25519 AAAAC3NzaC1lZDI1NTE5...`).  
5. Save and exit.  
7. Reopen the file to ensure it was saved correctly:  
   ```bash
   sudo nano ~/.ssh/authorized_keys
   ```  
8. Restart the SSH service:  
   ```bash
   sudo service ssh restart
   ```  

---

### Verify the SSH Connection:  
1. On Windows, open Git Bash and navigate to your `.ssh` folder:  
   ```bash
   cd ~/.ssh
   start "" .
   ```  
2. Edit the SSH config file to include:  
   ```
   Host raspberrypi2.local
     HostName raspberrypi2.local
     User root
     IdentityFile C:\Users\USER_NAME\.ssh\eloistree_all_pi

   Host raspberrypi3.local
     HostName raspberrypi3.local
     User root
     IdentityFile C:\Users\USER_NAME\.ssh\eloistree_all_pi
   ```  
   - This setup specifies that connections to `raspberrypi2.local` and `raspberrypi3.local` should use the specified private key.  

---

### Success!  
You now have a secure SSH connection to your Raspberry Pi with double authentication, ensuring reliable access. 🎉




Check that your removed the password acces
Allow SSH connection:
`sudo nano /etc/ssh/sshd_config`


Change:
```
PermitRootLogin no
PubkeyAuthentication yes
```
Check if it works
`ssh root@raspberrypi2`

Add your key: 
`ssh-copy-id -i ~/.ssh/eloistree_all_pi.pub root@raspberrypi2`

Check:

`ssh -i ~/.ssh/eloistree_all_pi.pub root@raspberrypi2`

