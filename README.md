# Windows Service Analysis

<h2>Description</h2>
In this task, I used my reverse tcp in Ubuntu to create a BackupService auto start service in my windows vm then found the servie properties in services.msc and queried the properties in command prompt and powershell.  


<h2>Languages and Utilities Used</h2>

- <b>Windows cmd</b>
- <b>Windows powershell</b>
- <b>linux CLI</b>


<h2>Environments Used </h2>

- <b>Unbuntu</b>
- <b>Windows 10 Enterprise</b> 

<br />
<br />
Running the command promopt as admin to execute notmalware.exe.

![1) run as admin cmd notmalware exe](https://github.com/user-attachments/assets/293b45d1-b737-402e-9bd4-7acdc5f56741)

<br />
<br />
In my Ubuntu windows shell, I created a service named "BackupService" using the file path to notmalware with an auto start. Full command: sc create BackupService binPath= "C:\Users\albert\Downloads\notmalware.exe" start= auto. This did not work at first because I ran the malware without admin privileges. 

![2) create service in shell called BackupService](https://github.com/user-attachments/assets/d39fabe4-c182-4f1f-bad0-2b9c8be2318c)

<br />
<br />  
On my windows vm, I ran services.msc as admin and found the BackupService. I opened service properties to show the path to the notmalware.exe.

![3) Use services to find backupservices](https://github.com/user-attachments/assets/de18639d-1357-438e-8008-c7500ee0105d)

<br />
<br />
The command "sc qc Backupservice" queries the configuration information for a service named "Backupservice" on the local computer.

![4) sc qc to query the configuration of a suspicious service in cmd](https://github.com/user-attachments/assets/36674cb4-42d7-4a37-9e09-ca82312cd254)

<br />
<br />
In powershell, the command "get-service -name "BackupService" | select-object *" retrieves detailed information about the "BackupService" service and displays all available properties.

![5) get service name is not as verbose as sc qc in cmd](https://github.com/user-attachments/assets/14114138-b50b-4000-b493-3264f0dfacec)

<br />
<br />
The command get-wmiobject -class win32_service -filter "name = 'BackupService' " | select-object * retrieves detailed information about the "BackupService" using Windows Management Instrumentation (WMI).

![6)get-wmiobject to query windows managment intrumentation directly ](https://github.com/user-attachments/assets/38f95a69-93f6-4cd3-b32e-bc6b24abe33d)

<br />
<br />
