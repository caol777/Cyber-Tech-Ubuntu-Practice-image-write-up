# Cyber-Tech-Ubuntu-Practice-image-write-up

## The Scenario

 This company's security policies require that all user accounts be password protected. Employees are required to choose secure passwords, however this policy may not be currently enforced on this computer. The presence of any non-work related media files and "hacking tools" on any computers is strictly prohibited. This company currently does not use any centralized maintenance or polling tools to manage their IT equipment. This computer is for official business use only by authorized users. This is a critical computer in a production environment. Please do NOT attempt to upgrade the operating system on this machine.
 
It is company policy to use only Ubuntu 24.04 on this computer. It is also company policy to use only the latest, official, stable Ubuntu 24.04 packages available for required software and services on this computer. Management has decided that the default web browser for all users on this computer should be the latest stable version of Firefox. Company policy is to never let users log in as root. If administrators need to run commands as root, they are required to use the "sudo" command.

Every year, CyberTech, a technology company, changes files, users, audits, passwords, application configurations, and security settings to maintain their server. However, this new year, a hacker compromised the maintenance technician's computer and made insecure changes! Your mission is to locate these issues and secure CyberTech's server once again.

Make sure to adhere to the correct users and set good security practices. This includes removing malware, enabling firewalls, deleting unneeded software/files, and securing passwords. 

# Forensics

## Forensic Questions 1
There is an image file named located on the *Downloads* of one of the users on this computer. Your task is to compute the SHA-256 hash of this file. Provide the hash as your answer.

Example Answer: fa690b82061edfd2852629aeba8a8977b57e40fcb77d1a7a28b26cba62591204

To get the Answer we would have to use the find command and look for a .jpg file.
I did find /home/*/ -type f -iname "*.jpg" to find the file. The "*" made the command look through all of users files and let me to find my answer. 

Two files should pop up so keep note of both 

Answer: 
