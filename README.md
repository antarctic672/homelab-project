# homelab-project
My homelab project
Network Architecture

Ubuntu Server - - - - Windows 10 | <-------- Kali
<img width="399" height="278" alt="image" src="https://github.com/user-attachments/assets/1e8b877f-8750-46d3-aed7-767f3980107a" />

I started with creating a secure and useful setup for Ubuntu Server. I needed to open the SSH securely, to operate via Windows10. I could not get the guest additions done on the ubuntu server for some reason (ctrl+c, ctr+v), but could on Windows10. The screenshot shows the successful creation of an SSH key pair on an Ubuntu system using the ssh-keygen command with the Ed25519 algorithm. <img width="1024" height="768" alt="VirtualBox_Windows_03_05_2026_23_48_34" src="https://github.com/user-attachments/assets/9c9f9c35-bd78-4ac0-8789-1eb0a4d8dcd2" /> 
The next stage involved configuring key-based authentication between the Windows client and the remote Ubuntu server. <img width="1024" height="768" alt="VirtualBox_Windows_04_05_2026_00_20_28" src="https://github.com/user-attachments/assets/161e2454-01e8-43ea-bc3d-64c305088f11" /> 
Here I am logged in with the passphrase<img width="1024" height="861" alt="VirtualBox_Windows_04_05_2026_00_24_10" src="https://github.com/user-attachments/assets/acafe90d-e5cb-4eff-94eb-a282e121b024" />

I also played a bit with the firewall. Probably forgot to take a screenshot, but I changed the ssh port from 22 to 2222 for security reasons. I used the sshd config file and edited the settings there.<img width="1920" height="974" alt="VirtualBox_Windows_06_05_2026_21_23_50" src="https://github.com/user-attachments/assets/5d3d0872-da51-47f9-a1d9-c8628c71fc31" />

Here you can see the current firewall rules as for the finish of this lab. Setting up VM's sometimes gets intense in terms of hardware/software issues and therefore I forget to document this lab (i fight to solve them and forget about documentation xD). The 1514, 1515, and 55000 ports are used for the Wazuh services, so I added them during implementing Wazuh. And I also opened the 443, but forgot to delete the IPv6 version (not critical). <img width="1024" height="768" alt="VirtualBox_Ubuntu Server_28_05_2026_22_46_53" src="https://github.com/user-attachments/assets/15efd387-9f0b-4603-89b1-a7e3fc2c2220" />

# (And coming back to the "issues". I did spend some time playing/setting up the VM's and learning information about how to do things. I only documented when I've accomplished something. I did not document everything. There was a ton things which I did "off the camera". During the whole lab I had a time where I both have the exams in my uni and the work, so there is inconsistency in my lab progress)

Wazuh implementation process. It is pretty boring overall, but there were some funny/hard moments which I had to solve, therefore it took some time.<img width="1920" height="974" alt="VirtualBox_Windows_06_05_2026_22_07_18" src="https://github.com/user-attachments/assets/44707930-cde5-445b-977e-e1e00318b667" />
<img width="1023" height="860" alt="VirtualBox_Windows_08_05_2026_14_42_42" src="https://github.com/user-attachments/assets/8ca65edf-3299-4b62-9c8e-459747a30b2e" />
<img width="1023" height="860" alt="VirtualBox_Windows_08_05_2026_14_44_29" src="https://github.com/user-attachments/assets/9224854b-26bd-41af-bdd5-a7d60d156305" />
<img width="1023" height="860" alt="VirtualBox_Windows_08_05_2026_15_01_36" src="https://github.com/user-attachments/assets/5d32e3c7-f32a-4fd3-babe-7ff56ea24b99" />
<img width="981" height="816" alt="wazuh dashboard" src="https://github.com/user-attachments/assets/7a40b2b4-0adb-4cc5-804f-242c87cd0c19" />

Finally accessed Wazuh. Used the windows10 to access it.<img width="1203" height="829" alt="wazuh accessed" src="https://github.com/user-attachments/assets/cf7af53d-d610-40d4-93a0-37f3f82b0eee" />

Added the windows10 as a wazuh node.<img width="1203" height="829" alt="wazuh accessed" src="https://github.com/user-attachments/assets/089e1ff5-8366-4ca2-9f57-3f174d3f8067" />
I wanted to create architecture, where there is a vulnerable metasploitable, which can access windows10. And windows10 can access ubuntu server. But it turns out that metasploitable is so vulnerable that I could not install wazuh node without properly updating it. What is the sense of a properly updated metasploitable? xD If it is supposed to be vulnerable. So I backed up with that idea, even though I spent some time configuring it. So I just left the architecture where there is the attacker (kali), vulnerable windows(firewall disabled), ubuntu server (accessible by the windows. because i configured the firewall in ubuntu server only to allow ssh connection from windows)
