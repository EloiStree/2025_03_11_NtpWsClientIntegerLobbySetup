- SSH and Connect PI tutorials:
  - https://github.com/EloiStree/HelloRaspberryPiDevKitCM5/issues/11
  - https://github.com/EloiStree/HelloRaspberryPiDevKitCM5/issues/13 



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
![image](https://github.com/user-attachments/assets/41367cf8-571a-43d4-bf49-2e6db791db06)

Key the password the time to install what you need:
![image](https://github.com/user-attachments/assets/9203a5f4-87da-4660-b311-8f5899f222b5)


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

Connect to your root user of the pi in Git Bash:
![image](https://github.com/user-attachments/assets/50ca1bb7-947d-4e07-966a-c8504291c0ef)

Add your key:
ssh-copy-id -i ~/.ssh/pikey.pub pi@raspberrypi

Allows root login:
sudo nano /etc/ssh/sshd_config
PermitRootLogin yes

Restart SSH:
sudo systemctl status ssh


Check if you succeed to connnect
ssh -i ~/.ssh/pikey root@raspberrypi
