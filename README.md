# DFIR-Tips
Lets Rock !! Gather all our Weaponz

## Identify malicious macro was enabled & clicked

1. Look at this registery key
```
HKEY_LOCAL_MACHINE\USERDAT\Software\Microsoft\Office\<VERS>\<PROGRAM>\Security\Trusted Documents\TrustRecords 
```
**OR**
```
HKEY_CURRENT_USER\Software\Microsoft\Office\[office_version]\Word\Security\Trusted Documents\TrustRecords
```
Look ONLY for values where last four bytes are "FF FF FF 7F".

2. Check INetCache Outlook folder
```
C:\Users\<name>\AppData\Local\Microsoft\Windows\INetCache\Content.Outlook\<Folder>\
```
File wont exist if AV quarantined it.

3. Check the macro settings
```
NTUSERDAT\Software\Microsoft\Office\<vers>\<program>\Security
```
**OR**
```
Computer\HKEY_CURRENT_USER\SOFTWARE\Microsoft\Office\16.0\Word\Security
```

|VBA warning | Data Value|
| ------------- |:-------------:| 
|Disable all macros w/o notification | 2, 4|
|Disable all macros except signed macros| 3|
|Enable all macros| 1|

4. Check recent files viewed/visited
+ NTUSER.DAT artefacts
+ LNK / Jmplists
+ Microsoft Recent Files (C:\Users\<usr>\appdata\roaming\Microsoft\office\Recent)

5. Execution of word/excel
+ Prefetch
+ Shimcache
+ Amcache (Not relevant if using workstation) 
+ Security.evtx Event ID 4688

