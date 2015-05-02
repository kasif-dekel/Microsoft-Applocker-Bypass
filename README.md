# Microsoft-Applocker-Bypass
A new technique to bypass microsoft's applocker. 

# What is AppLocker:
AppLocker is a new feature in Windows 7 and Windows Server 2008 R2 that allows you to specify which users or groups can run particular applications in your organization based on unique identities of files. If you use AppLocker, you can create rules to allow or deny applications from running.

# The Finding:
When AppLocker is configured to work in whitelist mode (e.g: only specified programs are allowed to run) it is possible to bypass to protection of 'AppLocker'.
If, for example only [mspaint.exe, notepad.exe, calc.exe] are signed and allowed to run - it is still possible to run other programs and even run code that uses the WindowsAPI.
The vulnerability occurs since it is not possible to block the EXE file 'rundll32.exe' since its required by windows to perform important tasks.
Everything that you need to do to bypass applocker is run the rundll32.exe binary file with the following arguments (can be done by creating a shortcut, windows+R, etc):

```
rundll32.exe javascript:"\..\mshtml,RunHTMLApplication ";alert(1);
```



Once you run this, an internet-explorer window will show up with the alert message (1). 
If the machine isnt a kiosk machine, and you can copy a special DLL into the machine - its even better =] But as you already understand by now, you can use this to run vbscripts to perform more advanced operations.

# Microsft's Response
![alt tag](http://oi57.tinypic.com/2ns1543.jpg)
