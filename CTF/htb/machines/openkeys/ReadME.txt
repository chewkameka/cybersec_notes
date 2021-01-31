 Wednesday 16 December 2020 12:42:47 PM 
 
 Enumeration:
 	Port Scan:
 		sudo nmap -sC -sV -oA scans 10.10.10.199
 	
 	Dir Scan:
 		gobuster -w $DIR -x php -o gobuster_scan -u http://10.10.10.199/
 	
 	SQL Map:
 		sqlmap -r login.request --batch
 			{ -r : path to request file
 			  --batch : non interactive session, uses default answers for 						questions }
 
 Found a auth.php.swp file in includes dir found in dir enumeration.
 It is a vim swp file.
 Open vim. Type :recover [filename] and press q to read the file.
