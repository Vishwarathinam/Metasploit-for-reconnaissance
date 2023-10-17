# Metasploit-for-reconnaissance
Metasploit for reconnaissance in pentesting

# AIM:

To get introduced to Metasploit Framework and to  perform reconnaissance  in pentesting .

## DESIGN STEPS:

1) Install kali linux either in partition or virtual box or in live mode
2) Investigate on the various categories of tools as follows
3) Open terminal and try execute some kali linux commands

## EXECUTION STEPS AND ITS OUTPUT:

Find out the ip address of the attackers system

![z1](https://github.com/Vishwarathinam/Metasploit-for-reconnaissance/assets/95266350/dd30262f-9c28-41c0-aac8-0b855481d83a)



Invoke msfconsole:

![z2](https://github.com/Vishwarathinam/Metasploit-for-reconnaissance/assets/95266350/596c3187-efab-4a13-961e-8b3650dc7a68)



Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.

![z3](https://github.com/Vishwarathinam/Metasploit-for-reconnaissance/assets/95266350/e828febf-21aa-470b-9632-22e8f5c707ae)



Port Scanning:

Following command is executed for scanning the systems on our local area network with a TCP scan (-sT) looking for open ports between 1 and 1000 (-p1-1000). msf > nmap -sT 192.168.1810/24 -p1-1000

## OUTPUT:

![z4](https://github.com/Vishwarathinam/Metasploit-for-reconnaissance/assets/95266350/e7d22d33-a2cb-4a4d-ae37-0bff2522aad7)



USE the db-nmap command to scan and save the results into Metasploit's postgresql attached database. In that way, you can use those results in the exploitation stage later.

scan the targets with the command db_nmap as follows. msf > db_nmap 192.168.181.0/24


## OUTPUT:

![z5](https://github.com/Vishwarathinam/Metasploit-for-reconnaissance/assets/95266350/5c9735c1-fc96-4fa3-bb38-93514ca4c2f1)



Metasploit has a multitude of scanning modules built in. If we open another terminal, we can navigate to Metasploit's auxiliary modules and list all the scanner modules. cd /usr/share /metasploit-framework/modules/auxiliary kali > ls -l

## OUTPUT:

![z6](https://github.com/Vishwarathinam/Metasploit-for-reconnaissance/assets/95266350/c401af61-207c-4796-8c7c-ed8558a64c7c)



Search is a powerful command in Metasploit that you can use to find what you want to locate. msf >search name:Microsoft type:exploit

The info command provides information regarding a module or platform,

## OUTPUT
![z7](https://github.com/Vishwarathinam/Metasploit-for-reconnaissance/assets/95266350/09d4c7f0-de3a-4f6a-a50b-d5dfb9199b32)



Before beginning, set up the Metasploit database by starting the PostgreSQL server and initialize msfconsole database as follows: systemctl start postgresql msfdb init

## MYSQL ENUMERATION

Find the IP address of the Metasploitable machine first. Then, use the db_nmap command in msfconsole with Nmap flags to scan the MySQL database at 3306 port. db_nmap -sV -sC -p 3306 <metasploitable_ip_address>

![z8](https://github.com/Vishwarathinam/Metasploit-for-reconnaissance/assets/95266350/52748a25-b02a-4280-adf5-622b961adddb)


Use the search option to look for an auxiliary module to scan and enumerate the MySQL database. search type:auxiliary mysql

![z9](https://github.com/Vishwarathinam/Metasploit-for-reconnaissance/assets/95266350/6aadb8d2-bad4-413b-a9d1-203e3b91a7e2)



use the auxiliary/scanner/mysql/mysql_version module by typing the module name or associated number to scan MySQL version details. use 11 Or: use auxiliary/scanner/mysql/mysql_version

![z10](https://github.com/Vishwarathinam/Metasploit-for-reconnaissance/assets/95266350/456398e2-703a-4afd-b956-eba53e1cb97d)



Use the set rhosts command to set the parameter and run the module, as follows:

![z11](https://github.com/Vishwarathinam/Metasploit-for-reconnaissance/assets/95266350/03faf607-3c54-413e-be80-a7472b3e0343)



After scanning, you can also brute force MySQL root account via Metasploit's auxiliary(scanner/mysql/mysql_login) module.

![z12](https://github.com/Vishwarathinam/Metasploit-for-reconnaissance/assets/95266350/945a74ae-b9d8-4200-8d7c-b295fe9d1ea9)



set the PASS_FILE parameter to the wordlist path available inside /usr/share/wordlists: set PASS_FILE /usr/share/wordlistss/rockyou.txt Then, specify the IP address of the target machine with the RHOSTS command. set RHOSTS Set BLANK_PASSWORDS to true in case there is no password set for the root account. set BLANK_PASSWORDS true

![z13](https://github.com/Vishwarathinam/Metasploit-for-reconnaissance/assets/95266350/1e8d4e61-3e07-42e4-b373-62e1e9d89b5c)




## RESULT:

The Metasploit framework for reconnaissance is  examined successfully
