# Cyber-Tech-Ubuntu-Practice-image-write-up

## The Scenario

 This company's security policies require that all user accounts be password protected. Employees are required to choose secure passwords, however this policy may not be currently enforced on this computer. The presence of any non-work related media files and "hacking tools" on any computers is strictly prohibited. This company currently does not use any centralized maintenance or polling tools to manage their IT equipment. This computer is for official business use only by authorized users. This is a critical computer in a production environment. Please do NOT attempt to upgrade the operating system on this machine.
 
It is company policy to use only Ubuntu 24.04 on this computer. It is also company policy to use only the latest, official, stable Ubuntu 24.04 packages available for required software and services on this computer. Management has decided that the default web browser for all users on this computer should be the latest stable version of Firefox. Company policy is to never let users log in as root. If administrators need to run commands as root, they are required to use the "sudo" command.

Every year, CyberTech, a technology company, changes files, users, audits, passwords, application configurations, and security settings to maintain their server. However, this new year, a hacker compromised the maintenance technician's computer and made insecure changes! Your mission is to locate these issues and secure CyberTech's server once again.

Make sure to adhere to the correct users and set good security practices. This includes removing malware, enabling firewalls, deleting unneeded software/files, and securing passwords. 


# Forensics (Make sure you are logged into jmuskington to make it easier)

## Forensic Questions 1
There is an image file named located on the *Downloads* of one of the users on this computer. Your task is to compute the SHA-256 hash of this file. Provide the hash as your answer.

Example Answer: fa690b82061edfd2852629aeba8a8977b57e40fcb77d1a7a28b26cba62591204

To get the Answer we would have to use the find command and look for a .jpg file.
I did find /home/*/ -type f -iname "*.jpg" to find the file. The "*" made the command look through all of users files and let me to find my answer. 

![Screenshot from 2025-02-01 20-33-04](https://github.com/user-attachments/assets/cec0bfe5-b837-48aa-92f9-d50857129470)

after using the command you can see the two files here. 

Obviously the one we need to get the hash from is the downloads one and we will be using sha256sum to get that hash.

![image](https://github.com/user-attachments/assets/869a87e9-49ff-4afd-94d4-b8f6ffc986f9)

Here we find our answer

Answer: a534153c1d076fc192540a2be9e7ba24895bd1a8051b0a041136a015f9a84bc9

## Forensic Question 2
A suspicious file named generator.sh has been downloaded onto the system. Please find the URL from which this file has been downloaded, and please find the hidden secret inside the website.

Example Answer: https://funnywebsite.com
Example Answer: Cybersecurity is the best club!


![image](https://github.com/user-attachments/assets/5c33d927-5219-49fd-bf09-70b140aecc01)

if you look at the browser history you can find a shady website called "robux generator" 

Click on the website to find and copy the url for the first answer.



There is a hidden secret inside the website. We will look into the page source to find it.

![image](https://github.com/user-attachments/assets/e43b4b9e-fda7-4de2-b98a-ff460667234b)

Here we find out 2nd answer.


Answer: https://fastanddanger2.github.io
Answer: Secret Message: It doesn't actually give free robux!!! SHHHHH

## Forensic Question 3
The hacker, after installing some "hacking tools", decided to take a break  by scrolling through memes. While doing so, they downloaded an image file though the user jmuskington. In an attempt to cover their tracks, the hacker hid a secret text file inside this image file. Your task is to find the hidden text file within the image and reveal its content.

Example Answer: I hacked the system!


If you recall the other image file we found when we used the find command we can find the meme.jpg file easily
![Screenshot from 2025-02-01 20-33-04](https://github.com/user-attachments/assets/bac4c478-ee7e-40f3-b45a-35109ef3d8c6)

After finding the file we will use steghide to find the text file hidden in the image. 

![image](https://github.com/user-attachments/assets/de3d8599-897d-4acf-8b39-7538b5509fec)

After doing cat extract.txt we find the message "I'll be back - HackerXYZ" which is our answer
Answer: I'll be back - HackerXYZ

## Forensic Question 4
The hacker who gained access to this computer appended an insecure line in a critical file for sudo permissions. What is that line? (You should probably delete it after you find it).

If you go to /etc do ls | grep sudo, you can see a few sudo files to look at. In our case the line is in sudoers. To change it you would have to do sudo nano sudoers and look for the Defaults !authenticate line.

This line is not a default line and has to be removed.

Answer: Defaults !authenticate 

## Forensic Question 5

There is a source code editor installed on this computer. Find the release key fingerprint of this source code editor (1). Next find the key type (2) and the date the key expires (3) in the format YYYY-MM-DD.

For this answer you would have to look around for any coding applications. Like vscode, intellij, or in our case notepad++.
To answer these questions i just looked up notepad++ release key fingerprint and found them online or through chatgpt.

Answer: 14BC E436 2749 B2B5 1F8C 7122 6C42 9F1D 8D84 F46E
Answer: RSA 4096 / 4096
Answer: 2027-03-13


# Vulnerabilites

## Uninstall the 'hacking tools'

If you look in the /etc/bin directory and do ls. you can find two tools that could be used for hacking. nmap and wireshark. 

to delete these simply do sudo apt remove nmap / sudo apt remove wireshark.

## Removed Unauthorized user cpitt
If you look through the /etc/passwd file you can see alot of users who arent supposed to be on the system. cpitt is one of them and to remove that user you can do
sudo userdel -r cpitt 

## Unauthorized media files are removed
The same two .jpg files that we found before need to be removed from the system as they are non-work related media files.
you can do that using rm meme.jpg or getCooked.jpg

## Malicious user creation script removed
If you remember the roblox generator site we found in our history. You could also assume that a user downloaded the script. To find it, look in the downloads folder of jmuskington. and simply delete the file. using rm generator.sh

## Ensure firewall is active 
The firewall is listed as a critical service make sure it is working by doing sudo ufw enable.

## Ensure cguy is not an Administator
In /etc/groups you can see that some users are in the sudo group when they are admins. Please remove them to earn this point.

## Ensure tslow is an Administator 
In /etc/groups make sure that tslow is in the sudo group.

![image](https://github.com/user-attachments/assets/aee0aee1-fe36-4b6d-85b9-0d6072213aa8)

