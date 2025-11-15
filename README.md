### Windows Team Notes

#### Check List

- [ ] Make sure the alpine router is not allowing outside traffic

- [ ] Change the passwords to the machines and get a limit for brute force attacks **Dont know how to do this look at the commands below**
	- ```net user administrator <new password>``` (This was use to change the password as quickly as possible)
		- example: net user administrator "Password" - this will change the password to Password if you want to change the default.
	<!-- - ```net accounts /lockoutduration:15``` - This will set a lockout time for 30 min -->
	<!-- - ```net accounts /lockoutthreshold:3``` - You will have three trys to log in if you fail you will have to wait the lockoutduration -->
- [ ] Help whoever has Active directory to get it running
- [ ] While the network is down double check services running - **What is really being scored?**
- [ ] Update windows offline - **Fuck if i know how**
- [ ] Windows devices check open ports - **If you are going to turn anything off take pictures**
	- ```netstat -ano``` (This displays active network connections and listening ports)
	- ```taskkill /F /PID <pid>``` (This was used to force terminate the process but **WILL NOT PERMANENTLY STOP THIS IS A QUICK FIX**)
- [ ] Windows devices check services running - **If you are going to remove a service take a picture of all service and the ones left**
- [ ] Check Windows updates to install anything you need that is critical
	- ```sfc /scannow``` (System file checker built-in utility that scans and repairs corrupted or missing system files)
---

### What I used last competition and why

- ```netstat -ano``` (This displays active network connections and listening ports)
- ```taskkill /F /PID <pid>``` (This was used to force terminate the process but **WILL NOT PERMANENTLY STOP**)
- ```net user administrator <new password>``` (This was use to change the password as quickly as possible)
- ```findstr /S "some string" *.*``` (This was using to locate a orange team memeber information but didnt see anything on the machine to help)
- ```sfc /scannow``` (System file checker built-in utility that scans and repairs corrupted or missing system files)
- review the updates and if you see a K<some number> see if you can download it by looking up the K<number> catalog
	- Example: KB5068861 catalog in browser (*you want the **Microsoft update catalog***)

---




### Useful commands and what they do


1. Local User & Group Enumeration
- ``` systeminfo``` - displays the systems info 
- ```net user``` - list all the users. 
- ```net accounts``` - Will display the min, max , and password length. As well as seeing if you have a lockout threshold,and duration of the lockout.
- ```net user administrator``` - will display the same information but for that user.
- ```net user administrator "Password"``` - this will change the password to Password if you want to change the default.   
	- ```net accounts /lockoutduration:15``` - This will set a lockout time for 30 min
	- ```net accounts /lockoutthreshold:3``` - You will have three trys to log in if you fail you will have to wait the *lockoutduration*  
- ```net localgroup administrator``` - look at the groups of a certain user. 

---

- ```whoami /priv``` - displays the privilage you have access to on the system.
- ```whoami /groups``` - displays all the groups the user is apart of.
- ```whoami /all``` - list all the users.

---

- ```Get-LocalUser | ft Name,Enabled,LastLogon``` - displays a list of Local Users on the device and if they are enabled and the time of the last time they logged on. 
- ```Get-ChildItem C:\Users -Force | Select Name``` - This will go into the "C" drive and select the name of the folders there.
	- ```Get-LocalGroupMember administrator``` - This will display the object class (group, or user) , the name, and principal source (Active Directory ,or local account)


2. Network Enumeration

- ```ipconfig /all``` - Displays all network information on the device
- ```nslookup <ip>``` - will display the host name
- ```netstat -ano```  - Will display all active connects 
- ```arp -a``` 		  - Will display devices you can contact
- ```netsh advfirewall show allprofiles``` - Show Windows Firewall status


3. Antivirus and Detections
- ```Get-MpComputerStatus``` - Check if Defender is running and up to date
- ```netsh advfirewall show domain``` - shows the firewall domain profile settings, you can check the other profiles by replacing domain with public/ private
- **Press Win + R, type mrt, press Enter** MSRT – Malicious Software Removal Tool A standalone Microsoft tool that removes prevalent malware.





 
