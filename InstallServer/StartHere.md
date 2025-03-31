- SSH and Connect PI tutorials:
  - https://github.com/EloiStree/HelloRaspberryPiDevKitCM5/issues/11
  - https://github.com/EloiStree/HelloRaspberryPiDevKitCM5/issues/13 


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


