# Metasploit-for-reconnaissance
# Metasploit
Metasploit for reconnaissance in pentesting

# AIM:

To get introduced to Metasploit Framework and to  perform reconnaissance  in pentesting .

## DESIGN STEPS:

### Step 1:

Install kali linux either in partition or virtual box or in live mode

### Step 2:

Investigate on the various categories of tools as follows:

### Step 3:

Open terminal and try execute some kali linux commands

## EXECUTION STEPS AND ITS OUTPUT:

Find out the ip address of the attackers system
## OUTPUT:

<img width="1029" height="496" alt="image" src="https://github.com/user-attachments/assets/11445035-d006-4436-9daa-b1b109f9e5eb" />


Invoke msfconsole:
## OUTPUT:

<img width="1022" height="675" alt="image" src="https://github.com/user-attachments/assets/2cbcdd10-c94f-454e-90ed-8dcda320e9c5" />

Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.


<img width="1024" height="773" alt="image" src="https://github.com/user-attachments/assets/764b9052-7513-460c-ba4a-cea90c915360" />


Port Scanning:
Following command is executed for scanning the systems on our local area network with a TCP scan (-sT) looking for open ports between 1 and 1000 (-p1-1000).
msf >  nmap -sT 192.168.1810/24 -p1-1000  (Replace with appropriate IP Address)
## OUTPUT:

<img width="750" height="521" alt="image" src="https://github.com/user-attachments/assets/d00aa3f6-1249-45c0-8717-ab452a7f853b" />


step4:
use the db-nmap command to scan and save the results into Metasploit's postgresql attached database. In that way, you can use those results in the exploitation stage later.

scan the targets with the command db_nmap as follows.
msf > db_nmap 192.168.181.0/24
## OUTPUT:
<img width="741" height="310" alt="image" src="https://github.com/user-attachments/assets/6d41cf1a-c369-4db1-843b-b4222995c181" />



Metasploit has a multitude of scanning modules built in. If we open another terminal, we can navigate to Metasploit's auxiliary modules and list all the scanner modules.
cd /usr/share /metasploit-framework/modules/auxiliary
kali > ls -l
## OUTPUT:
<img width="555" height="335" alt="image" src="https://github.com/user-attachments/assets/a6223908-d478-47bd-bbdb-e70d564bfd77" />



Search is a powerful command in Metasploit that you can use to find what you want to locate. 
msf >search name:Microsoft type:exploit
## OUTPUT:

<img width="831" height="404" alt="image" src="https://github.com/user-attachments/assets/c8fe9121-c7ac-4913-bf05-1525e5702fad" />


The info command provides information regarding a module or platform,

Before beginning, set up the Metasploit database by starting the PostgreSQL server and initialize msfconsole database as follows:
systemctl start postgresql
msfdb init
## OUTPUT:




## MYSQL ENUMERATION
Find the IP address of the Metasploitable machine first. Then, use the db_nmap command in msfconsole with Nmap flags to scan the MySQL database at 3306 port.
db_nmap -sV -sC -p 3306 <metasploitable_ip_address>

## OUTPUT:

<img width="742" height="317" alt="image" src="https://github.com/user-attachments/assets/6d94f8d1-4370-4a19-b10e-eaf74553a3b2" />


Use the search option to look for an auxiliary module to scan and enumerate the MySQL database.
search type:auxiliary mysql
## OUTPUT:

<img width="822" height="271" alt="image" src="https://github.com/user-attachments/assets/398ad89f-c42c-487e-8174-07ab9e10d291" />


use the auxiliary/scanner/mysql/mysql_version module by typing the module name or associated number to scan MySQL version details.
use 11
Or:
use auxiliary/scanner/mysql/mysql_version
## OUTPUT:

<img width="808" height="172" alt="image" src="https://github.com/user-attachments/assets/f22adcb0-8f0f-4ba3-b174-2492b78c9e86" />



Use the set rhosts command to set the parameter and run the module, as follows:
## OUTPUT:

<img width="599" height="113" alt="image" src="https://github.com/user-attachments/assets/fb665f8b-fde9-4f3d-a8dd-47512303dc9b" />


After scanning, you can also brute force MySQL root account via Metasploit's auxiliary(scanner/mysql/mysql_login) module.
## OUTPUT:


<img width="823" height="324" alt="image" src="https://github.com/user-attachments/assets/0cc118e6-a1ef-40bf-9ebd-cc9ffe1ad0e6" />


set the PASS_FILE parameter to the wordlist path available inside /usr/share/wordlists:
set PASS_FILE /usr/share/wordlistss/rockyou.txt
Then, specify the IP address of the target machine with the RHOSTS command.
set RHOSTS <metasploitable-ip-address>
Set BLANK_PASSWORDS to true in case there is no password set for the root account.
set BLANK_PASSWORDS true
## OUTPUT:


<img width="816" height="232" alt="image" src="https://github.com/user-attachments/assets/e008ac53-d503-4845-be6a-3c40821f8afd" />



## RESULT:
The Metasploit framework for reconnaissance is  examined successfully
